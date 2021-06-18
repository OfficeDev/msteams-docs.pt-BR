---
title: 'Iniciar: Compilar seu primeiro aplicativo do Teams com React'
author: adrianhall
description: Crie rapidamente um aplicativo do Microsoft Teams que exibe uma mensagem "Olá, Mundo!" usando o Kit de ferramentas do Microsoft Teams e o React.
ms.author: adhal
ms.date: 05/27/2021
ms.topic: quickstart
ms.openlocfilehash: edd7cf8048dd89156b4b91afecb329d91baf3f53
ms.sourcegitcommit: 14409950307b135265c8582408be5277b35131dd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2021
ms.locfileid: "52994109"
---
# <a name="build-and-run-your-first-microsoft-teams-app-with-react"></a><span data-ttu-id="61962-104">Compilar e executar seu primeiro aplicativo do Microsoft Teams com React</span><span class="sxs-lookup"><span data-stu-id="61962-104">Build and run your first Microsoft Teams app with React</span></span>

<span data-ttu-id="61962-105">Neste tutorial, você criará um novo aplicativo Microsoft Teams no React que implementa um aplicativo pessoal simples para extrair informações do Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="61962-105">In this tutorial, you will create a new Microsoft Teams app in React that implements a simple personal app to pull information from the Microsoft Graph.</span></span> <span data-ttu-id="61962-106">Por exemplo, um *aplicativo pessoal* inclui um conjunto de guias com escopo para uso individual.</span><span class="sxs-lookup"><span data-stu-id="61962-106">For example, a *personal app* includes a set of tabs scoped for individual use.</span></span> <span data-ttu-id="61962-107">Durante o tutorial, você aprenderá sobre a estrutura de um aplicativo Teams, como executar um aplicativo localmente e como implantar o aplicativo no Azure.</span><span class="sxs-lookup"><span data-stu-id="61962-107">During the tutorial, you will learn about the structure of a Teams app, how to run an app locally, and how to deploy the app to Azure.</span></span>

<span data-ttu-id="61962-108">O aplicativo que é compilado exibe informações básicas para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="61962-108">The app that is built displays basic user information for the current user.</span></span> <span data-ttu-id="61962-109">Quando a permissão é concedida, o aplicativo se conectará ao Microsoft Graph como o usuário atual para obter o perfil completo.</span><span class="sxs-lookup"><span data-stu-id="61962-109">When permission is granted, the app will connect to the Microsoft Graph as the current user to get the complete profile.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="61962-110">Antes de você começar</span><span class="sxs-lookup"><span data-stu-id="61962-110">Before you begin</span></span>

<span data-ttu-id="61962-111">Certifique-se de que seu ambiente de desenvolvimento está definido instalando os [pré-requisitos](prerequisites.md).</span><span class="sxs-lookup"><span data-stu-id="61962-111">Make sure your development environment is set up by installing the [prerequisites](prerequisites.md).</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="61962-112">Instalar pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="61962-112">Install prerequisites</span></span>](prerequisites.md)

## <a name="create-your-project"></a><span data-ttu-id="61962-113">Criar seu projeto</span><span class="sxs-lookup"><span data-stu-id="61962-113">Create your project</span></span>

<span data-ttu-id="61962-114">Use o Kit de ferramentas do Teams para criar o seu primeiro projeto:</span><span class="sxs-lookup"><span data-stu-id="61962-114">Use the Teams Toolkit to create your first project:</span></span>

# <a name="visual-studio-code"></a>[<span data-ttu-id="61962-115">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="61962-115">Visual Studio Code</span></span>](#tab/vscode)

1. <span data-ttu-id="61962-116">Abra o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="61962-116">Open Visual Studio code.</span></span>
1. <span data-ttu-id="61962-117">Abra o Kit de ferramentas do Teams selecionando o ícone do Teams na barra lateral:</span><span class="sxs-lookup"><span data-stu-id="61962-117">Open the Teams Toolkit by selecting the Teams icon in the sidebar:</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="O ícone do Teams na barra lateral do Visual Studio Code":::

1. <span data-ttu-id="61962-119">Selecione **Criar Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="61962-119">Select **Create New Project**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project.png" alt-text="Localização do link de Criação de Novo Projeto na barra lateral do Kit de ferramentas do Teams.":::

1. <span data-ttu-id="61962-121">Selecione **Criar um novo aplicativo do Teams**.</span><span class="sxs-lookup"><span data-stu-id="61962-121">Select **Create a new Teams app**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-new-project-intro.png" alt-text="Início do assistente para Criar Novo Projeto":::

1. <span data-ttu-id="61962-123">Na etapa **Selecionar recursos,** o recurso **Tab** já está selecionado.</span><span class="sxs-lookup"><span data-stu-id="61962-123">On the **Select capabilities** step, the **Tab** capability is already selected.</span></span> <span data-ttu-id="61962-124">Pressione **OK**.</span><span class="sxs-lookup"><span data-stu-id="61962-124">Press **OK**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-capabilities.png" alt-text="Captura de tela mostrando como adicionar capacidades ao seu novo aplicativo.":::

1. <span data-ttu-id="61962-126">Na etapa **Tipo de hospedagem front-end**, selecione **Azure**.</span><span class="sxs-lookup"><span data-stu-id="61962-126">On the **Frontend hosting type** step, select **Azure**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-hosting.png" alt-text="Captura de tela mostrando como selecionar a hospedagem para seu novo aplicativo.":::

1. <span data-ttu-id="61962-128">Na etapa **Recursos em nuvem**, pressione **OK**.</span><span class="sxs-lookup"><span data-stu-id="61962-128">On the **Cloud resources** step, press **OK**.</span></span>  <span data-ttu-id="61962-129">Não precisamos de recursos adicionais em nuvem para este tutorial.</span><span class="sxs-lookup"><span data-stu-id="61962-129">We do not need additional cloud resources for this tutorial.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-cloud-resources.png" alt-text="Captura de tela mostrando como adicionar recursos em nuvem ao seu novo aplicativo.":::

1. <span data-ttu-id="61962-131">Na etapa **Linguagem de Programação**, selecione **JavaScript**.</span><span class="sxs-lookup"><span data-stu-id="61962-131">On the **Programming Language** step, select **JavaScript**.</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-programming-languages.png" alt-text="Captura de tela mostrando como selecionar a linguagem de programação.":::

1. <span data-ttu-id="61962-133">Selecione uma pasta do espaço de trabalho.</span><span class="sxs-lookup"><span data-stu-id="61962-133">Select a workspace folder.</span></span> <span data-ttu-id="61962-134">Uma pasta é criada em sua pasta de espaço de trabalho para o projeto que você está criando.</span><span class="sxs-lookup"><span data-stu-id="61962-134">A folder is created within your workspace folder for the project you are creating.</span></span>

1. <span data-ttu-id="61962-135">Insira um nome adequado para seu aplicativo, como `helloworld`.</span><span class="sxs-lookup"><span data-stu-id="61962-135">Enter a suitable name for your app, like `helloworld`.</span></span> <span data-ttu-id="61962-136">O nome do aplicativo deve consistir apenas de caracteres alfanuméricos.</span><span class="sxs-lookup"><span data-stu-id="61962-136">The name of the app must consist only of alphanumeric characters.</span></span>  <span data-ttu-id="61962-137">Pressione **Inserir** para continuar.</span><span class="sxs-lookup"><span data-stu-id="61962-137">Press **Enter** to continue.</span></span>

<span data-ttu-id="61962-138">Seu Teams app é criado em alguns segundos.</span><span class="sxs-lookup"><span data-stu-id="61962-138">Your Teams app is created within a few seconds.</span></span>

# <a name="command-line"></a>[<span data-ttu-id="61962-139">Linha de comando</span><span class="sxs-lookup"><span data-stu-id="61962-139">Command line</span></span>](#tab/cli)

<span data-ttu-id="61962-140">Use a CLI `teamsfx` para criar o seu primeiro projeto.</span><span class="sxs-lookup"><span data-stu-id="61962-140">Use the `teamsfx` CLI to create your first project.</span></span>  <span data-ttu-id="61962-141">Inicie pela pasta onde deseja criar a pasta do projeto.</span><span class="sxs-lookup"><span data-stu-id="61962-141">Start from the folder where you want to create the project folder.</span></span>

``` bash
teamsfx new
```

<span data-ttu-id="61962-142">A CLI lhe guiará através de algumas perguntas para criar o projeto.</span><span class="sxs-lookup"><span data-stu-id="61962-142">The CLI walks through some questions to create the project.</span></span> <span data-ttu-id="61962-143">Cada pergunta lhe dirá como respondê-la, por exemplo, use teclas de seta para selecionar uma opção.</span><span class="sxs-lookup"><span data-stu-id="61962-143">Each question will tell you how to answer it, for example, use arrow keys to select an option.</span></span> <span data-ttu-id="61962-144">Depois de responder à pergunta, confirme sua escolha pressionando **Inserir**.</span><span class="sxs-lookup"><span data-stu-id="61962-144">When you have answered the question, confirm your choice by pressing **Enter**.</span></span>

1. <span data-ttu-id="61962-145">Selecione **Criar um novo aplicativo do Teams**.</span><span class="sxs-lookup"><span data-stu-id="61962-145">Select **Create a new Teams app**.</span></span>
1. <span data-ttu-id="61962-146">Escolha a capacidade **Guia**.</span><span class="sxs-lookup"><span data-stu-id="61962-146">Choose the **Tab** capability.</span></span>
1. <span data-ttu-id="61962-147">Selecione **Azure** como hospedagem front-end.</span><span class="sxs-lookup"><span data-stu-id="61962-147">Select **Azure** frontend hosting.</span></span>
1. <span data-ttu-id="61962-148">Não selecione nenhum recurso em nuvem.</span><span class="sxs-lookup"><span data-stu-id="61962-148">Do not select any cloud resources.</span></span>
1. <span data-ttu-id="61962-149">Selecione **JavaScript** como linguagem de programação.</span><span class="sxs-lookup"><span data-stu-id="61962-149">Select **JavaScript** as the programming language.</span></span>
1. <span data-ttu-id="61962-150">Pressione **Inserir** para selecionar a pasta padrão do espaço de trabalho.</span><span class="sxs-lookup"><span data-stu-id="61962-150">Press **Enter** to select the default workspace folder.</span></span>
1. <span data-ttu-id="61962-151">Insira um nome adequado para seu aplicativo, como `helloworld`.</span><span class="sxs-lookup"><span data-stu-id="61962-151">Enter a suitable name for your app, like `helloworld`.</span></span>  <span data-ttu-id="61962-152">O nome do aplicativo deve consistir apenas de caracteres alfanuméricos.</span><span class="sxs-lookup"><span data-stu-id="61962-152">The name of the app must consist only of alphanumeric characters.</span></span>

<span data-ttu-id="61962-153">Depois que todas as perguntas foram respondidas, seu projeto é criado.</span><span class="sxs-lookup"><span data-stu-id="61962-153">Once all the questions have been answered, your project is created.</span></span>

---

## <a name="take-a-tour-of-the-source-code"></a><span data-ttu-id="61962-154">Faça um tour pelo código-fonte</span><span class="sxs-lookup"><span data-stu-id="61962-154">Take a tour of the source code</span></span>

<span data-ttu-id="61962-155">Se desejar pular esta seção por enquanto, você pode [executar seu aplicativo localmente](#run-your-app-locally).</span><span class="sxs-lookup"><span data-stu-id="61962-155">If you wish to skip this section for now, you can [run your app locally](#run-your-app-locally).</span></span>

<span data-ttu-id="61962-156">Uma vez que o Kit de ferramentas do Teams configura seu projeto, você tem os componentes para compilar um aplicativo pessoal básico para o Teams.</span><span class="sxs-lookup"><span data-stu-id="61962-156">Once the Teams Toolkit configures your project, you have the components to build a basic personal app for Teams.</span></span> <span data-ttu-id="61962-157">Os diretórios e arquivos do projeto são exibidos na área do Explorador do Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="61962-157">The project directories and files display in the Explorer area of Visual Studio Code.</span></span>

:::image type="content" source="../assets/images/teams-toolkit-v2/react-app-project.png" alt-text="Captura de tela mostrando arquivos de projeto do aplicativo para um aplicativo pessoal no Visual Studio Code.":::

<span data-ttu-id="61962-159">O Kit de ferramentas cria automaticamente scaffolding para você no diretório do projeto com base nas capacidades que você adicionou durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="61962-159">The Toolkit automatically creates scaffolding for you in the project directory based on the capabilities you added during setup.</span></span> <span data-ttu-id="61962-160">O Kit de ferramentas do Teams mantém o estado de seu aplicativo no diretório `.fx`.</span><span class="sxs-lookup"><span data-stu-id="61962-160">The Teams Toolkit maintains its state for your app in the `.fx` directory.</span></span>  <span data-ttu-id="61962-161">Entre outros itens deste diretório:</span><span class="sxs-lookup"><span data-stu-id="61962-161">Among other items in this directory:</span></span>

- <span data-ttu-id="61962-162">Os ícones do aplicativo são armazenados como arquivos PNG em `color.png` e `outline.png`.</span><span class="sxs-lookup"><span data-stu-id="61962-162">The app icons are stored as PNG files in `color.png` and `outline.png`.</span></span>
- <span data-ttu-id="61962-163">O manifesto do aplicativo para publicação no Portal do Desenvolvedor do Teams é armazenado em `manifest.source.json`.</span><span class="sxs-lookup"><span data-stu-id="61962-163">The app manifest for publishing to the Developer Portal for Teams is stored in `manifest.source.json`.</span></span>
- <span data-ttu-id="61962-164">As configurações que você escolheu ao criar o projeto são armazenadas em `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="61962-164">The settings you chose when creating the project are stored in `settings.json`.</span></span>

<span data-ttu-id="61962-165">Como você selecionou a capacidade de guias durante a instalação, o Kit de ferramentas do Teams reúne todo o código necessário para uma guia básica no diretório `tabs`.</span><span class="sxs-lookup"><span data-stu-id="61962-165">Since you selected the tab capability during setup, the Teams Toolkit scaffolds all the necessary code for a basic tab in the `tabs` directory.</span></span> <span data-ttu-id="61962-166">Dentro deste diretório há vários arquivos importantes:</span><span class="sxs-lookup"><span data-stu-id="61962-166">Within this directory there are several important files:</span></span>

- <span data-ttu-id="61962-167">`tabs/src/index.jsx` é o ponto de entrada do front-end do aplicativo, onde o componente principal `App` é renderizado com `ReactDOM.render()`.</span><span class="sxs-lookup"><span data-stu-id="61962-167">`tabs/src/index.jsx` is the front-end app's entry point, where the main `App` component is rendered with `ReactDOM.render()`.</span></span>
- <span data-ttu-id="61962-168">`tabs/src/components/App.jsx` lida com o roteamento de URLs em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="61962-168">`tabs/src/components/App.jsx` handles URL routing in your app.</span></span> <span data-ttu-id="61962-169">Ele chama o [Microsoft Teams JavaScript client SDK](../tabs/how-to/using-teams-client-sdk.md) para estabelecer a comunicação entre seu aplicativo e o Teams.</span><span class="sxs-lookup"><span data-stu-id="61962-169">It calls the [Microsoft Teams JavaScript client SDK](../tabs/how-to/using-teams-client-sdk.md) to establish communication between your app and Teams.</span></span>
- <span data-ttu-id="61962-170">`tabs/src/components/Tab.jsx` contém o código para implementar a IU do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="61962-170">`tabs/src/components/Tab.jsx` contains the code to implement the UI of your app.</span></span>
- <span data-ttu-id="61962-171">`tabs/src/components/TabConfig.jsx` contém o código para implementar a IU que configura seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="61962-171">`tabs/src/components/TabConfig.jsx` contains the code to implement the UI that configures your app.</span></span>

<span data-ttu-id="61962-172">Várias guias são exigidas pelo runtime do Teams, incluindo o aviso de privacidade, os termos de uso e as guias de configuração.</span><span class="sxs-lookup"><span data-stu-id="61962-172">Several tabs are required by the Teams runtime, including the privacy notice, terms of use, and configuration tabs.</span></span>  <span data-ttu-id="61962-173">O código para o aviso de privacidade e os termos de uso estão localizados no mesmo diretório.</span><span class="sxs-lookup"><span data-stu-id="61962-173">The code for the privacy notice and terms of use are located in the same directory.</span></span>

<span data-ttu-id="61962-174">Quando se adiciona a funcionalidade da nuvem, diretórios adicionais são adicionados ao projeto.</span><span class="sxs-lookup"><span data-stu-id="61962-174">When you add cloud functionality, additional directories are added to the project.</span></span>  <span data-ttu-id="61962-175">Principalmente, o diretório `api` retém o código para qualquer Azure Functions que você escreva.</span><span class="sxs-lookup"><span data-stu-id="61962-175">Most notably, the `api` directory holds the code to any Azure Functions you write.</span></span>

## <a name="run-your-app-locally"></a><span data-ttu-id="61962-176">Executar seu aplicativo localmente</span><span class="sxs-lookup"><span data-stu-id="61962-176">Run your app locally</span></span>

<span data-ttu-id="61962-177">O Kit de ferramentas do Teams permite que você execute seu aplicativo localmente.</span><span class="sxs-lookup"><span data-stu-id="61962-177">Teams Toolkit allows you to run your app locally.</span></span>  <span data-ttu-id="61962-178">Isto consiste de várias partes que são necessárias para fornecer a infraestrutura correta que o Teams espera:</span><span class="sxs-lookup"><span data-stu-id="61962-178">This consists of several parts that are necessary to provide the correct infrastructure that Teams expects:</span></span>

- <span data-ttu-id="61962-179">Um aplicativo está registrado no Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="61962-179">An application is registered with Azure Active Directory.</span></span>  <span data-ttu-id="61962-180">Este aplicativo tem permissões associadas ao local de onde o aplicativo é carregado e a quaisquer recursos de back-end que ele acesse.</span><span class="sxs-lookup"><span data-stu-id="61962-180">This application has permissions associated with the location that the app is loaded from and any backend resources it accesses.</span></span>
- <span data-ttu-id="61962-181">Uma API da Web é hospedada para auxiliar nas tarefas de autenticação, atuando como um proxy entre o aplicativo e o Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="61962-181">A web API is hosted to assist with authentication tasks, acting as a proxy between the app and Azure Active Directory.</span></span>  <span data-ttu-id="61962-182">Isto é executado pelo Azure Functions Core Tools.</span><span class="sxs-lookup"><span data-stu-id="61962-182">This is run by Azure Functions Core Tools.</span></span>  <span data-ttu-id="61962-183">Ele pode ser acessado na URL `https://localhost:5000`.</span><span class="sxs-lookup"><span data-stu-id="61962-183">It can be accessed at the URL `https://localhost:5000`.</span></span>
- <span data-ttu-id="61962-184">Os recursos HTML, CSS e JavaScript que compõem o front-end do aplicativo são hospedados em um serviço local.</span><span class="sxs-lookup"><span data-stu-id="61962-184">The HTML, CSS, and JavaScript resources that make up the front end of the app are hosted on a local service.</span></span> <span data-ttu-id="61962-185">Ele pode ser acessado em `https://localhost:3000`.</span><span class="sxs-lookup"><span data-stu-id="61962-185">It can be accessed at `https://localhost:3000`.</span></span>
- <span data-ttu-id="61962-186">Um manifesto de aplicativo é gerado e existe no Portal de Desenvolvedor do Teams.</span><span class="sxs-lookup"><span data-stu-id="61962-186">An app manifest is generated and exists in the Developer Portal for Teams.</span></span>  <span data-ttu-id="61962-187">O Teams usa o manifesto do aplicativo para dizer aos clientes conectados de onde carregar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="61962-187">Teams uses the app manifest to tell connected clients where to load the app from.</span></span>

<span data-ttu-id="61962-188">Depois de fazer isso, o aplicativo pode ser carregado dentro do cliente do Teams.</span><span class="sxs-lookup"><span data-stu-id="61962-188">Once this is done, the app can be loaded within the Teams client.</span></span>  <span data-ttu-id="61962-189">Usamos o cliente Web do Teams para que possamos ver o código HTML, CSS e JavaScript dentro de um ambiente de desenvolvimento web padrão.</span><span class="sxs-lookup"><span data-stu-id="61962-189">We use the Teams web client so that we can see the HTML, CSS, and JavaScript code within a standard web development environment.</span></span>

### <a name="build-and-run-your-app-locally-in-visual-studio-code"></a><span data-ttu-id="61962-190">Compilar e executar seu aplicativo localmente em Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="61962-190">Build and run your app locally in Visual Studio Code</span></span>

<span data-ttu-id="61962-191">Para compilar e executar seu aplicativo localmente:</span><span class="sxs-lookup"><span data-stu-id="61962-191">To build and run your app locally:</span></span>

1. <span data-ttu-id="61962-192">No Visual Studio Code, pressione **F5** para executar seu aplicativo no modo de depuração.</span><span class="sxs-lookup"><span data-stu-id="61962-192">From Visual Studio Code, press **F5** to run your application in debug mode.</span></span>

   > <span data-ttu-id="61962-193">Quando você executa o aplicativo pela primeira vez, todas as dependências são baixadas e o aplicativo é compilado.</span><span class="sxs-lookup"><span data-stu-id="61962-193">When you run the app for the first time, all dependencies are downloaded and the app is built.</span></span>  <span data-ttu-id="61962-194">Uma janela do navegador é aberta automaticamente quando a compilação é concluída.</span><span class="sxs-lookup"><span data-stu-id="61962-194">A browser window automatically opens when the build is complete.</span></span>  <span data-ttu-id="61962-195">Isto pode levar de 3 a 5 minutos para ser concluído.</span><span class="sxs-lookup"><span data-stu-id="61962-195">This can take 3-5 minutes to complete.</span></span>

   <span data-ttu-id="61962-196">A Toolkit solicita que você instale um certificado local, se necessário.</span><span class="sxs-lookup"><span data-stu-id="61962-196">The Toolkit prompts you to install a local certificate if required.</span></span> <span data-ttu-id="61962-197">Esse certificado permite que o Teams carregue seu aplicativo a partir de `https://localhost`.</span><span class="sxs-lookup"><span data-stu-id="61962-197">This certificate allows Teams to load your application from `https://localhost`.</span></span> <span data-ttu-id="61962-198">Selecione Sim quando aparecer a seguinte caixa de diálogo:</span><span class="sxs-lookup"><span data-stu-id="61962-198">Select yes when the following dialog appears:</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/ssl-prompt.png" alt-text="Captura de tela mostrando como a solicitação de instalação de um certificado SSL para permitir que o Teams carregue seu aplicativo a partir do localhost.":::

1. <span data-ttu-id="61962-200">O navegador da Web começa a executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="61962-200">Your web browser starts to run the app.</span></span> <span data-ttu-id="61962-201">Se for solicitado a abrir a área de trabalho do Teams, selecione **Cancelar** para permanecer no navegador.</span><span class="sxs-lookup"><span data-stu-id="61962-201">If prompted to open Teams desktop, select **Cancel** to remain in the browser.</span></span> <span data-ttu-id="61962-202">Você também pode ser solicitado a mudar para a área de trabalho do Teams em outras ocasiões; selecione o aplicativo Web do Teams quando isso acontecer.</span><span class="sxs-lookup"><span data-stu-id="61962-202">You may also be prompted to switch to Teams desktop at other times; select the Teams web app when this happens.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/launch-web-browser-and-pick-webapp.png" alt-text="Captura de tela mostrando como escolher a versão da web das equipes quando lançadas":::

1. <span data-ttu-id="61962-204">Você pode ser solicitado a entrar.</span><span class="sxs-lookup"><span data-stu-id="61962-204">You may be prompted to sign in.</span></span>  <span data-ttu-id="61962-205">Em caso afirmativo, entre com sua conta M365.</span><span class="sxs-lookup"><span data-stu-id="61962-205">If so, sign in with your M365 account.</span></span>
1. <span data-ttu-id="61962-206">Quando solicitado a instalar o aplicativo no Teams, pressione **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="61962-206">When prompted to install the app onto Teams, press **Add**.</span></span>

<span data-ttu-id="61962-207">Seu aplicativo agora é exibido:</span><span class="sxs-lookup"><span data-stu-id="61962-207">Your app is now displayed:</span></span>

:::image type="content" source="../assets/images/teams-toolkit-v2/react-finished-app.png" alt-text="Captura de tela do aplicativo concluído":::

<span data-ttu-id="61962-209">Você pode fazer atividades normais de depuração como se fosse qualquer outro aplicativo Web, como a configuração de pontos de interrupção.</span><span class="sxs-lookup"><span data-stu-id="61962-209">You can do normal debugging activities as if this were any other web application, such as setting breakpoints.</span></span> <span data-ttu-id="61962-210">O aplicativo dá suporte à recarga dinâmica.</span><span class="sxs-lookup"><span data-stu-id="61962-210">The app supports hot reloading.</span></span> <span data-ttu-id="61962-211">Se você alterar qualquer arquivo dentro do projeto, a página será recarregada.</span><span class="sxs-lookup"><span data-stu-id="61962-211">If you change any file within the project, the page will be reloaded.</span></span>

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="61962-212">Saiba o que acontece quando você executa seu aplicativo localmente no depurador.</span><span class="sxs-lookup"><span data-stu-id="61962-212">Learn what happens when you run your app locally in the debugger.</span></span></summary>

<span data-ttu-id="61962-213">Quando você pressionou F5, o Kit de ferramentas do Teams:</span><span class="sxs-lookup"><span data-stu-id="61962-213">When you pressed F5, the Teams Toolkit:</span></span>

1. <span data-ttu-id="61962-214">Registrou seu aplicativo no Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="61962-214">Registered your application with Azure Active Directory.</span></span>
1. <span data-ttu-id="61962-215">*Fez o sideload* de seu aplicativo no Teams.</span><span class="sxs-lookup"><span data-stu-id="61962-215">*Sideloaded* your app in Teams.</span></span>
1. <span data-ttu-id="61962-216">Iniciou a execução do back-end de seu aplicativo localmente usando o [Azure Functions Core Tools](/azure/azure-functions/functions-run-local?#start).</span><span class="sxs-lookup"><span data-stu-id="61962-216">Started your application backend running locally using [Azure Function Core Tools](/azure/azure-functions/functions-run-local?#start).</span></span>
1. <span data-ttu-id="61962-217">Iniciou a hospedagem local do front-end de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="61962-217">Started your application front-end hosted locally.</span></span>
1. <span data-ttu-id="61962-218">Iniciado o Microsoft Teams em um navegador da Web com um comando para instruir o Teams a carregar o aplicativo de lado de `https://localhost:3000/tab` .</span><span class="sxs-lookup"><span data-stu-id="61962-218">Started Microsoft Teams in a web browser with a command to instruct Teams to side load the application from `https://localhost:3000/tab`.</span></span> <span data-ttu-id="61962-219">Essa é a URL registrada no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="61962-219">This is the URL registered in the application manifest.</span></span>

</details>

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="61962-220">Saiba como solucionar problemas comuns ao executar seu aplicativo localmente.</span><span class="sxs-lookup"><span data-stu-id="61962-220">Learn how to troubleshoot common issues when running your app locally.</span></span></summary>

<span data-ttu-id="61962-221">Para executar com êxito seu aplicativo no Teams, você deve ter uma conta do Teams que permite o sideload de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="61962-221">To successfully run your app in Teams, you must have a Teams account that allows app sideloading.</span></span> <span data-ttu-id="61962-222">Para obter mais informações sobre abertura de conta, confira [pré-requisitos](prerequisites.md#enable-sideloading).</span><span class="sxs-lookup"><span data-stu-id="61962-222">For more information on account opening, see [prerequisites](prerequisites.md#enable-sideloading).</span></span>

</details>

[!INCLUDE [Provision and Deploy your app on Azure](~/includes/get-started/azure-provisioning-instructions.md)]

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="61962-223">Saiba o que acontece quando você implanta o seu aplicativo no Azure</span><span class="sxs-lookup"><span data-stu-id="61962-223">Learn what happens when you deployed your app to Azure</span></span></summary>

<span data-ttu-id="61962-224">Antes da implantação, o aplicativo era executado localmente:</span><span class="sxs-lookup"><span data-stu-id="61962-224">Before deployment, the application has been running locally:</span></span>

1. <span data-ttu-id="61962-225">O back-end é executado usando o **Azure Functions Core Tools**.</span><span class="sxs-lookup"><span data-stu-id="61962-225">The backend runs using **Azure Functions Core Tools**.</span></span>
1. <span data-ttu-id="61962-226">O ponto de extremidade HTTP do aplicativo, onde o Microsoft Teams carrega o aplicativo, é executado localmente.</span><span class="sxs-lookup"><span data-stu-id="61962-226">The application HTTP endpoint, where Microsoft Teams loads the application, runs locally.</span></span>

<span data-ttu-id="61962-227">A implantação envolve o provisionamento de recursos em uma assinatura ativa do Azure e a implantação ou carregamento do código back-end e front-end do aplicativo para o Azure.</span><span class="sxs-lookup"><span data-stu-id="61962-227">Deployment involves provisioning resources on an active Azure subscription and deploying or uploading the backend and frontend code for the application to Azure.</span></span>

1. <span data-ttu-id="61962-228">O back-end, se configurado, usa uma variedade de serviços do Azure, incluindo o Serviço de Aplicativo do Azure e o Armazenamento do Azure.</span><span class="sxs-lookup"><span data-stu-id="61962-228">The backend if configured uses a variety of Azure services, including Azure App Service and Azure Storage.</span></span>
1. <span data-ttu-id="61962-229">O front-end do aplicativo será implantado em uma conta de Armazenamento do Microsoft Azure configurada para hospedagem Web estática.</span><span class="sxs-lookup"><span data-stu-id="61962-229">The frontend application will be deployed to an Azure Storage account configured for static web hosting.</span></span>

</details>

## <a name="see-also"></a><span data-ttu-id="61962-230">Confira também</span><span class="sxs-lookup"><span data-stu-id="61962-230">See also</span></span>

- [<span data-ttu-id="61962-231">Criar um aplicativo do Teams com o Blazor</span><span class="sxs-lookup"><span data-stu-id="61962-231">Create a Teams app with Blazor</span></span>](first-app-blazor.md)
- <span data-ttu-id="61962-232">[Criar um aplicativo do Teams como uma Web Part do SharePoint](first-app-spfx.md) (Azure não é necessário)</span><span class="sxs-lookup"><span data-stu-id="61962-232">[Create a Teams app as a SharePoint Web Part](first-app-spfx.md) (Azure not required)</span></span>
- [<span data-ttu-id="61962-233">Criar um programa bot de conversação</span><span class="sxs-lookup"><span data-stu-id="61962-233">Create a conversational bot app</span></span>](first-app-bot.md)
- [<span data-ttu-id="61962-234">Criar uma extensão de mensagem</span><span class="sxs-lookup"><span data-stu-id="61962-234">Create a messaging extension</span></span>](first-message-extension.md)

## <a name="next-step"></a><span data-ttu-id="61962-235">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="61962-235">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="61962-236">Criar um aplicativo do Teams com o Blazor</span><span class="sxs-lookup"><span data-stu-id="61962-236">Create a Teams app with Blazor</span></span>](first-app-blazor.md)
