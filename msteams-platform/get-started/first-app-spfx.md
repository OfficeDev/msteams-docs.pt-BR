---
title: Começar - Criar seu primeiro aplicativo Teams com SPFx
author: zhenyasav
description: Saiba como criar uma guia personalizada com a Estrutura do SharePoint
ms.author: zhenyasa
ms.date: 05/19/2021
ms.topic: quickstart
ms.openlocfilehash: 4df2bb71837af520a2d2500a45b8605e5fae08b2
ms.sourcegitcommit: 9d63611974ba8a7e7f19ceea35e50189a2e90434
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2021
ms.locfileid: "53254220"
---
# <a name="build-and-run-your-first-microsoft-teams-app-with-sharepoint-framework-spfx"></a><span data-ttu-id="27f7a-103">Crie e execute seu primeiro aplicativo Microsoft Teams com Estrutura do SharePoint (SPFx)</span><span class="sxs-lookup"><span data-stu-id="27f7a-103">Build and run your first Microsoft Teams app with SharePoint Framework (SPFx)</span></span>

<span data-ttu-id="27f7a-104">Neste tutorial, você aprenderá a criar um novo aplicativo Microsoft Teams no Estrutura do SharePoint SPFx que implementa um aplicativo pessoal simples.</span><span class="sxs-lookup"><span data-stu-id="27f7a-104">In this tutorial, you will learn how to create a new Microsoft Teams app in SharePoint Framework SPFx that implements a simple personal app.</span></span> <span data-ttu-id="27f7a-105">Por exemplo, um *aplicativo pessoal* inclui um conjunto de guias para uso individual.</span><span class="sxs-lookup"><span data-stu-id="27f7a-105">For example, a *personal app* includes a set of tabs for individual use.</span></span> <span data-ttu-id="27f7a-106">Durante o tutorial, você aprenderá sobre a estrutura de um aplicativo Teams, como executar um aplicativo localmente e como implantar o aplicativo SharePoint.</span><span class="sxs-lookup"><span data-stu-id="27f7a-106">During the tutorial, you will learn about the structure of a Teams app, how to run an app locally, and how to deploy the app to SharePoint.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="27f7a-107">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="27f7a-107">Before you begin</span></span>

<span data-ttu-id="27f7a-108">Certifique-se de que seu ambiente de desenvolvimento está definido instalando os pré-requisitos.</span><span class="sxs-lookup"><span data-stu-id="27f7a-108">Make sure your development environment is set up by installing the prerequisites.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="27f7a-109">Instalar pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="27f7a-109">Install prerequisites</span></span>](prerequisites.md)

## <a name="get-organized"></a><span data-ttu-id="27f7a-110">Organizar-se</span><span class="sxs-lookup"><span data-stu-id="27f7a-110">Get organized</span></span>

<span data-ttu-id="27f7a-111">Além dos pré-requisitos, você também precisa ser administrador de um conjunto SharePoint Site.</span><span class="sxs-lookup"><span data-stu-id="27f7a-111">In addition to the prerequisites, you also need to be an Administrator for a SharePoint Site Collection.</span></span>  <span data-ttu-id="27f7a-112">É aqui que você implantará seu aplicativo para hospedagem.</span><span class="sxs-lookup"><span data-stu-id="27f7a-112">This is where you will deploy your app for hosting.</span></span>  <span data-ttu-id="27f7a-113">Se você estiver usando um locatário de programa de desenvolvedor do M365, use a conta de administrador configurada quando se registrou no programa.</span><span class="sxs-lookup"><span data-stu-id="27f7a-113">If you are using an M365 developer program tenant, use the administrator account you set up when you registered for the program.</span></span>  

## <a name="create-your-project"></a><span data-ttu-id="27f7a-114">Criar seu projeto</span><span class="sxs-lookup"><span data-stu-id="27f7a-114">Create your project</span></span>

<span data-ttu-id="27f7a-115">Use o Kit de ferramentas do Teams para criar o seu primeiro projeto:</span><span class="sxs-lookup"><span data-stu-id="27f7a-115">Use the Teams Toolkit to create your first project:</span></span>

# <a name="visual-studio-code"></a>[<span data-ttu-id="27f7a-116">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="27f7a-116">Visual Studio Code</span></span>](#tab/vscode)

1. <span data-ttu-id="27f7a-117">Abra o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="27f7a-117">Open Visual Studio code.</span></span>
1. <span data-ttu-id="27f7a-118">Selecione o Teams na barra lateral para abrir o Teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="27f7a-118">Select the Teams icon in the sidebar to open the Teams Toolkit.</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="O ícone do Teams na barra lateral do Visual Studio Code":::

1. <span data-ttu-id="27f7a-120">Selecione **Criar Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="27f7a-120">Select **Create New Project**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project.png" alt-text="Localização do link de Criação de Novo Projeto na barra lateral do Kit de ferramentas do Teams.":::

1. <span data-ttu-id="27f7a-122">Selecione **Criar um novo aplicativo do Teams**.</span><span class="sxs-lookup"><span data-stu-id="27f7a-122">Select **Create a new Teams app**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-new-project-intro.png" alt-text="Início do assistente para Criar Novo Projeto":::

1. <span data-ttu-id="27f7a-124">Na seção **Selecionar recursos,** selecione **Guia** e selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="27f7a-124">In the **Select capabilities** section, select **Tab** and select **OK**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-capabilities.png" alt-text="Captura de tela mostrando como adicionar capacidades ao seu novo aplicativo.":::

1. <span data-ttu-id="27f7a-126">Na seção **Tipo de hospedagem frontend,** selecione **Estrutura do SharePoint (SPFx)**.</span><span class="sxs-lookup"><span data-stu-id="27f7a-126">In the **Frontend hosting type** section, select **SharePoint Framework (SPFx)**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-hosting.png" alt-text="Captura de tela mostrando como selecionar a hospedagem para seu novo aplicativo.":::

1. <span data-ttu-id="27f7a-128">Na seção **Estrutura,** selecione **React**.</span><span class="sxs-lookup"><span data-stu-id="27f7a-128">In the **Framework** section, select **React**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-which-framework.png" alt-text="Selecionar Estrutura":::

1. <span data-ttu-id="27f7a-130">Quando solicitado a um **Nome da Webpart,** pressione **Enter** para aceitar o padrão.</span><span class="sxs-lookup"><span data-stu-id="27f7a-130">When asked for a **Webpart Name**, press **Enter** to accept the default.</span></span>

1. <span data-ttu-id="27f7a-131">Quando solicitado para a **Descrição da Webpart,** pressione **Enter** para aceitar o padrão.</span><span class="sxs-lookup"><span data-stu-id="27f7a-131">When asked for the **Webpart Description**, press **Enter** to accept the default.</span></span>

1. <span data-ttu-id="27f7a-132">Quando solicitado a linguagem **de programação,** pressione **Enter** para aceitar o padrão.</span><span class="sxs-lookup"><span data-stu-id="27f7a-132">When asked for the **Programming Language**, press **Enter** to accept the default.</span></span>

1. <span data-ttu-id="27f7a-133">Selecione uma pasta do espaço de trabalho.</span><span class="sxs-lookup"><span data-stu-id="27f7a-133">Select a workspace folder.</span></span>  <span data-ttu-id="27f7a-134">Uma pasta será criada dentro de sua pasta do espaço de trabalho para o projeto que você está criando.</span><span class="sxs-lookup"><span data-stu-id="27f7a-134">A folder will be created within your workspace folder for the project you are creating.</span></span>

1. <span data-ttu-id="27f7a-135">Insira um nome adequado para seu aplicativo, como `helloworld`.</span><span class="sxs-lookup"><span data-stu-id="27f7a-135">Enter a suitable name for your app, like `helloworld`.</span></span>  <span data-ttu-id="27f7a-136">O nome do aplicativo deve consistir apenas de caracteres alfanuméricos.</span><span class="sxs-lookup"><span data-stu-id="27f7a-136">The name of the app must consist only of alphanumeric characters.</span></span>  <span data-ttu-id="27f7a-137">Pressione **Inserir** para continuar.</span><span class="sxs-lookup"><span data-stu-id="27f7a-137">Press **Enter** to continue.</span></span>

   <span data-ttu-id="27f7a-138">O seu aplicativo do Teams será criado em alguns segundos.</span><span class="sxs-lookup"><span data-stu-id="27f7a-138">Your Teams app will be created within a few seconds.</span></span>

# <a name="command-line"></a>[<span data-ttu-id="27f7a-139">Linha de comando</span><span class="sxs-lookup"><span data-stu-id="27f7a-139">Command line</span></span>](#tab/cli)

<span data-ttu-id="27f7a-140">Use a CLI `teamsfx` para criar o seu primeiro projeto.</span><span class="sxs-lookup"><span data-stu-id="27f7a-140">Use the `teamsfx` CLI to create your first project.</span></span>  <span data-ttu-id="27f7a-141">Inicie pela pasta onde deseja criar a pasta do projeto.</span><span class="sxs-lookup"><span data-stu-id="27f7a-141">Start from the folder where you want to create the project folder.</span></span>

``` bash
teamsfx new
```

<span data-ttu-id="27f7a-142">A CLI lhe guiará através de algumas perguntas para criar o projeto.</span><span class="sxs-lookup"><span data-stu-id="27f7a-142">The CLI walks through some questions to create the project.</span></span>  <span data-ttu-id="27f7a-143">Cada pergunta lhe dirá como respondê-la (por exemplo, usar as teclas de seta para selecionar uma opção).</span><span class="sxs-lookup"><span data-stu-id="27f7a-143">Each question will tell you how to answer it (for example, to use arrow keys to select an option).</span></span>  <span data-ttu-id="27f7a-144">Depois de responder à pergunta, confirme sua escolha pressionando **Inserir**.</span><span class="sxs-lookup"><span data-stu-id="27f7a-144">When you have answered the question, confirm your choice by pressing **Enter**.</span></span>

1. <span data-ttu-id="27f7a-145">Selecione **Criar um novo aplicativo do Teams**.</span><span class="sxs-lookup"><span data-stu-id="27f7a-145">Select **Create a new Teams app**.</span></span>
1. <span data-ttu-id="27f7a-146">Selecione **Guia**.</span><span class="sxs-lookup"><span data-stu-id="27f7a-146">Select **Tab**.</span></span>
1. <span data-ttu-id="27f7a-147">Selecione **Estrutura do SharePoint (SPFx)** de frontend.</span><span class="sxs-lookup"><span data-stu-id="27f7a-147">Select **SharePoint Framework (SPFx)** frontend hosting.</span></span>
1. <span data-ttu-id="27f7a-148">Selecione **React** estrutura.</span><span class="sxs-lookup"><span data-stu-id="27f7a-148">Select **React** framework.</span></span>
1. <span data-ttu-id="27f7a-149">Pressione **Enter** para o **Nome da Webpart**.</span><span class="sxs-lookup"><span data-stu-id="27f7a-149">Press **Enter** for the **Webpart Name**.</span></span>
1. <span data-ttu-id="27f7a-150">Pressione **Enter** para a **Descrição da Webpart**.</span><span class="sxs-lookup"><span data-stu-id="27f7a-150">Press **Enter** for the **Webpart Description**.</span></span>
1. <span data-ttu-id="27f7a-151">Pressione **Enter** para a **Linguagem de Programação**.</span><span class="sxs-lookup"><span data-stu-id="27f7a-151">Press **Enter** for the **Programming Language**.</span></span>
1. <span data-ttu-id="27f7a-152">Pressione **Inserir** para selecionar a pasta padrão do espaço de trabalho.</span><span class="sxs-lookup"><span data-stu-id="27f7a-152">Press **Enter** to select the default workspace folder.</span></span>
1. <span data-ttu-id="27f7a-153">Insira um nome adequado para seu aplicativo, como `helloworld`.</span><span class="sxs-lookup"><span data-stu-id="27f7a-153">Enter a suitable name for your app, like `helloworld`.</span></span>  <span data-ttu-id="27f7a-154">O nome do aplicativo deve consistir apenas de caracteres alfanuméricos.</span><span class="sxs-lookup"><span data-stu-id="27f7a-154">The name of the app must consist only of alphanumeric characters.</span></span>

   <span data-ttu-id="27f7a-155">Depois que todas as perguntas foram respondidas, seu projeto será criado.</span><span class="sxs-lookup"><span data-stu-id="27f7a-155">After all the questions have been answered, your project will be created.</span></span>

---

- [<span data-ttu-id="27f7a-156">Saiba mais sobre o desenvolvimento para Estrutura do SharePoint</span><span class="sxs-lookup"><span data-stu-id="27f7a-156">Learn more about developing for SharePoint Framework</span></span>](/sharepoint/dev/spfx/sharepoint-framework-overview)

## <a name="take-a-tour-of-the-source-code"></a><span data-ttu-id="27f7a-157">Faça um tour pelo código-fonte</span><span class="sxs-lookup"><span data-stu-id="27f7a-157">Take a tour of the source code</span></span>

<span data-ttu-id="27f7a-158">Se desejar pular esta seção por enquanto, você pode [executar seu aplicativo localmente](#run-your-app-locally).</span><span class="sxs-lookup"><span data-stu-id="27f7a-158">If you wish to skip this section for now, you can [run your app locally](#run-your-app-locally).</span></span>

<span data-ttu-id="27f7a-159">Após a Teams Toolkit configura seu projeto, você terá os componentes para criar um aplicativo pessoal básico para Teams que está hospedado no Estrutura do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="27f7a-159">After the Teams Toolkit configures your project, you have the components to build a basic personal app for Teams that is hosted within the SharePoint Framework.</span></span>  <span data-ttu-id="27f7a-160">Os diretórios e arquivos do projeto são exibidos na área do Explorador do Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="27f7a-160">The project directories and files display in the Explorer area of Visual Studio Code.</span></span>

:::image type="content" source="../assets/images/teams-toolkit-v2/app-project-files-spfx.png" alt-text="Captura de tela mostrando arquivos de projeto do aplicativo para um aplicativo pessoal no Visual Studio Code.":::

<span data-ttu-id="27f7a-162">O Kit de ferramentas cria automaticamente scaffolding para você no diretório do projeto com base nas capacidades que você adicionou durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="27f7a-162">The Toolkit automatically creates scaffolding for you in the project directory based on the capabilities you added during setup.</span></span> <span data-ttu-id="27f7a-163">O Kit de ferramentas do Teams mantém o estado de seu aplicativo no diretório `.fx`.</span><span class="sxs-lookup"><span data-stu-id="27f7a-163">The Teams Toolkit maintains its state for your app in the `.fx` directory.</span></span>  <span data-ttu-id="27f7a-164">Entre outros itens deste diretório:</span><span class="sxs-lookup"><span data-stu-id="27f7a-164">Among other items in this directory:</span></span>

- <span data-ttu-id="27f7a-165">Os ícones do aplicativo são armazenados como arquivos PNG em `color.png` e `outline.png`.</span><span class="sxs-lookup"><span data-stu-id="27f7a-165">The app icons are stored as PNG files in `color.png` and `outline.png`.</span></span>
- <span data-ttu-id="27f7a-166">O manifesto do aplicativo para publicação no Portal do Desenvolvedor para Teams é armazenado em `manifest.source.json` .</span><span class="sxs-lookup"><span data-stu-id="27f7a-166">The app manifest for publishing to Developer Portal for Teams is stored in `manifest.source.json`.</span></span>
- <span data-ttu-id="27f7a-167">As configurações que você escolheu ao criar o projeto são armazenadas em `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="27f7a-167">The settings you chose when creating the project are stored in `settings.json`.</span></span>

<span data-ttu-id="27f7a-168">Como você selecionou um SPFx webpart, os seguintes arquivos são relevantes para sua interface do usuário:</span><span class="sxs-lookup"><span data-stu-id="27f7a-168">Since you selected a SPFx Webpart project, the following files are relevant to your UI:</span></span>

- <span data-ttu-id="27f7a-169">A pasta `SPFx/src/webparts/{webpart}` contém sua SPFx webpart.</span><span class="sxs-lookup"><span data-stu-id="27f7a-169">The folder `SPFx/src/webparts/{webpart}` contains your SPFx webpart.</span></span>
- <span data-ttu-id="27f7a-170">O arquivo `.vscode/launch.json` descreve as configurações de depuração disponíveis na paleta de depuração.</span><span class="sxs-lookup"><span data-stu-id="27f7a-170">The file `.vscode/launch.json` describes the debugging configurations available in the debug palette.</span></span>

<span data-ttu-id="27f7a-171">Para obter mais informações sobre SharePoint Webparts para Teams, [consulte a documentação SharePoint.](/sharepoint/dev/spfx/build-for-teams-overview)</span><span class="sxs-lookup"><span data-stu-id="27f7a-171">For more information about SharePoint Webparts for Teams, [refer to the SharePoint documentation](/sharepoint/dev/spfx/build-for-teams-overview).</span></span>

## <a name="run-your-app-locally"></a><span data-ttu-id="27f7a-172">Executar seu aplicativo localmente</span><span class="sxs-lookup"><span data-stu-id="27f7a-172">Run your app locally</span></span>

<span data-ttu-id="27f7a-173">Teams Toolkit permite que você hospede seu aplicativo localmente e execute-o por meio do [Estrutura do SharePoint Workbench](/sharepoint/dev/spfx/debug-in-vscode).</span><span class="sxs-lookup"><span data-stu-id="27f7a-173">Teams Toolkit allows you to host your app locally and run it through the [SharePoint Framework Workbench](/sharepoint/dev/spfx/debug-in-vscode).</span></span>

### <a name="build-and-run-your-app-locally-in-visual-studio-code"></a><span data-ttu-id="27f7a-174">Compilar e executar seu aplicativo localmente em Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="27f7a-174">Build and run your app locally in Visual Studio Code</span></span>

<span data-ttu-id="27f7a-175">Para compilar e executar seu aplicativo localmente:</span><span class="sxs-lookup"><span data-stu-id="27f7a-175">To build and run your app locally:</span></span>

1. <span data-ttu-id="27f7a-176">Na Visual Studio Code, pressione a **tecla F5.**</span><span class="sxs-lookup"><span data-stu-id="27f7a-176">From Visual Studio Code, press the **F5** key.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-debug-local.png" alt-text="Captura de tela mostrando como iniciar um SPFx em um workbench local.":::

   > [!NOTE]
   > <span data-ttu-id="27f7a-178">Quando você executa o aplicativo pela primeira vez, todas as dependências são baixadas e o aplicativo é compilado.</span><span class="sxs-lookup"><span data-stu-id="27f7a-178">When you run the app for the first time, all dependencies are downloaded and the app is built.</span></span>  <span data-ttu-id="27f7a-179">Uma janela do navegador é aberta automaticamente e carrega o SharePoint Workbench quando a com build estiver concluída.</span><span class="sxs-lookup"><span data-stu-id="27f7a-179">A browser window automatically opens and loads the SharePoint Workbench when the build is complete.</span></span>  <span data-ttu-id="27f7a-180">Isto pode levar de 3 a 5 minutos para ser concluído.</span><span class="sxs-lookup"><span data-stu-id="27f7a-180">This can take 3-5 minutes to complete.</span></span>

   <span data-ttu-id="27f7a-181">Depois que o SharePoint Workbench for carregado.</span><span class="sxs-lookup"><span data-stu-id="27f7a-181">After the SharePoint Workbench is loaded.</span></span>

   >[!NOTE]
   > <span data-ttu-id="27f7a-182">O Kit de ferramentas lhe solicitará a instalação de um certificado local, se necessário.</span><span class="sxs-lookup"><span data-stu-id="27f7a-182">The Toolkit will prompt you to install a local certificate if needed.</span></span> <span data-ttu-id="27f7a-183">Esse certificado permite que o Teams carregue seu aplicativo a partir de `https://localhost`.</span><span class="sxs-lookup"><span data-stu-id="27f7a-183">This certificate allows Teams to load your application from `https://localhost`.</span></span> <span data-ttu-id="27f7a-184">Selecione Sim quando aparecer a seguinte caixa de diálogo:</span><span class="sxs-lookup"><span data-stu-id="27f7a-184">Select yes when the following dialog appears:</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/ssl-prompt.png" alt-text="Captura de tela mostrando como a solicitação de instalação de um certificado SSL para permitir que o Teams carregue seu aplicativo a partir do localhost.":::

1. <span data-ttu-id="27f7a-186">Selecione **Adicionar Webpart +** ícones para adicionar sua webpart.</span><span class="sxs-lookup"><span data-stu-id="27f7a-186">Select **Add Webpart +** icons to add your webpart.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-workbench-addpart.png" alt-text="Captura de tela mostrando o SPFx workbench em execução com o pop-up para adicionar uma webpart mostrando.":::

1. <span data-ttu-id="27f7a-188">Selecione sua webpart no menu.</span><span class="sxs-lookup"><span data-stu-id="27f7a-188">Select your webpart from the menu.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-workbench-addpart2.png" alt-text="Captura de tela mostrando o SPFx workbench em execução com o pop-up para adicionar uma seleção de webpart.":::

   <span data-ttu-id="27f7a-190">Seu aplicativo agora deve estar em execução.</span><span class="sxs-lookup"><span data-stu-id="27f7a-190">Your app should now be running.</span></span>  <span data-ttu-id="27f7a-191">Você pode fazer atividades normais de depuração como se fosse qualquer outra webpart SPFx (como definir pontos de interrupção).</span><span class="sxs-lookup"><span data-stu-id="27f7a-191">You can do normal debugging activities as if this were any other SPFx webpart (such as setting breakpoints).</span></span>

   > [!TIP]
   > <span data-ttu-id="27f7a-192">Tente colocar pontos de interrupção no método render de `SPFx/src/webparts/{webpart}/{webpart}.ts` e recarregar a janela do navegador.</span><span class="sxs-lookup"><span data-stu-id="27f7a-192">Try placing breakpoints in the render method of `SPFx/src/webparts/{webpart}/{webpart}.ts` and reloading the browser window.</span></span> <span data-ttu-id="27f7a-193">VS Code parar em pontos de interrupção em seu código.</span><span class="sxs-lookup"><span data-stu-id="27f7a-193">VS Code will stop on breakpoints in your code.</span></span>

## <a name="deploy-your-app-to-sharepoint"></a><span data-ttu-id="27f7a-194">Implantar seu aplicativo para SharePoint</span><span class="sxs-lookup"><span data-stu-id="27f7a-194">Deploy your app to SharePoint</span></span>

<span data-ttu-id="27f7a-195">Verifique se existe SharePoint catálogo de aplicativos em sua implantação.</span><span class="sxs-lookup"><span data-stu-id="27f7a-195">Ensure a SharePoint App Catalog exists in your deployment.</span></span>  <span data-ttu-id="27f7a-196">Se um não existir, [crie um](/sharepoint/use-app-catalog).</span><span class="sxs-lookup"><span data-stu-id="27f7a-196">If one does not exist, [create one](/sharepoint/use-app-catalog).</span></span>  <span data-ttu-id="27f7a-197">Pode levar até 15 minutos para que o catálogo de aplicativos seja totalmente criado.</span><span class="sxs-lookup"><span data-stu-id="27f7a-197">It may take up to 15 minutes for the app catalog to be fully created.</span></span>

# <a name="visual-studio-code"></a>[<span data-ttu-id="27f7a-198">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="27f7a-198">Visual Studio Code</span></span>](#tab/vscode)

1. <span data-ttu-id="27f7a-199">Abra o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="27f7a-199">Open Visual Studio Code.</span></span>
1. <span data-ttu-id="27f7a-200">Selecione a Teams Toolkit na barra lateral selecionando o ícone Teams.</span><span class="sxs-lookup"><span data-stu-id="27f7a-200">Select the Teams Toolkit from the sidebar by selecting the Teams icon.</span></span>
1. <span data-ttu-id="27f7a-201">Selecione **Provisionamento na Nuvem**.</span><span class="sxs-lookup"><span data-stu-id="27f7a-201">Select **Provision in the Cloud**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/provisioning-commands.png" alt-text="Captura de tela mostrando os comandos de provisionamento":::

   <span data-ttu-id="27f7a-203">Você pode monitorar o progresso observando as caixas de diálogo no canto inferior direito.</span><span class="sxs-lookup"><span data-stu-id="27f7a-203">You can monitor the progress by watching the dialogs in the bottom right corner.</span></span>  <span data-ttu-id="27f7a-204">Após alguns segundos, você verá o seguinte aviso:</span><span class="sxs-lookup"><span data-stu-id="27f7a-204">After a few seconds, you will see the following notice:</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/provision-complete.png" alt-text="Captura de tela mostrando a caixa de diálogo completa de provisionamento.":::

1. <span data-ttu-id="27f7a-206">Depois que o provisionamento for concluído, selecione **Implantar na nuvem**.</span><span class="sxs-lookup"><span data-stu-id="27f7a-206">After provisioning is complete, select **Deploy to the cloud**.</span></span>

1. <span data-ttu-id="27f7a-207">Atualmente, a implantação automatizada não está disponível.</span><span class="sxs-lookup"><span data-stu-id="27f7a-207">Currently, automated deployment is not available.</span></span>  <span data-ttu-id="27f7a-208">Uma caixa de diálogo será exibida solicitando que você crie e implante manualmente.</span><span class="sxs-lookup"><span data-stu-id="27f7a-208">A dialog will pop up prompting you to build and deploy manually.</span></span> <span data-ttu-id="27f7a-209">Selecione **Criar SharePoint Pacote**.</span><span class="sxs-lookup"><span data-stu-id="27f7a-209">Select **Build SharePoint Package**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/build-sharepoint-package.png" alt-text="Captura de tela para a caixa de diálogo Criar Pacote do Sharepoint":::

# <a name="command-line"></a>[<span data-ttu-id="27f7a-211">Linha de comando</span><span class="sxs-lookup"><span data-stu-id="27f7a-211">Command line</span></span>](#tab/cli)

<span data-ttu-id="27f7a-212">Em sua janela de terminal:</span><span class="sxs-lookup"><span data-stu-id="27f7a-212">In your terminal window:</span></span>

1. <span data-ttu-id="27f7a-213">Execute `teamsfx provision`.</span><span class="sxs-lookup"><span data-stu-id="27f7a-213">Run `teamsfx provision`.</span></span>

   ``` bash
   teamsfx provision
   ```

   <span data-ttu-id="27f7a-214">Você pode ser solicitado a fazer logoff na sua assinatura do Azure.</span><span class="sxs-lookup"><span data-stu-id="27f7a-214">You may be prompted to log in to your Azure subscription.</span></span>  <span data-ttu-id="27f7a-215">Se necessário, você será solicitado a selecionar uma assinatura do Azure a ser usada para os recursos do Azure.</span><span class="sxs-lookup"><span data-stu-id="27f7a-215">If required, you will be prompted to select an Azure subscription to use for the Azure resources.</span></span>

   > [!NOTE]
   > <span data-ttu-id="27f7a-216">Sempre há alguns recursos do Azure usados para hospedar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="27f7a-216">There are always some Azure resources used for hosting your app.</span></span>

1. <span data-ttu-id="27f7a-217">Execute `teamsfx deploy`.</span><span class="sxs-lookup"><span data-stu-id="27f7a-217">Run `teamsfx deploy`.</span></span>

   ``` bash
   teamsfx deploy
   ```

1. <span data-ttu-id="27f7a-218">Quando solicitado, selecione **Criar SharePoint Pacote**.</span><span class="sxs-lookup"><span data-stu-id="27f7a-218">When prompted, select **Build SharePoint Package**.</span></span>

---

<span data-ttu-id="27f7a-219">O SharePoint pacote está localizado `SPFx/sharepoint/solution` no seu projeto.</span><span class="sxs-lookup"><span data-stu-id="27f7a-219">The SharePoint package is located in `SPFx/sharepoint/solution` within your project.</span></span>  <span data-ttu-id="27f7a-220">Upload pacote para SharePoint:</span><span class="sxs-lookup"><span data-stu-id="27f7a-220">Upload the package to SharePoint:</span></span>

1. <span data-ttu-id="27f7a-221">Faça logon no Console de Administração do M365 e navegue até o SharePoint App Catalog.</span><span class="sxs-lookup"><span data-stu-id="27f7a-221">Log into the M365 Admin Console, then navigate to the SharePoint App Catalog.</span></span>

   1. <span data-ttu-id="27f7a-222">Abra `https://admin.microsoft.com/AdminPortal/Home` .</span><span class="sxs-lookup"><span data-stu-id="27f7a-222">Open `https://admin.microsoft.com/AdminPortal/Home`.</span></span>
   1. <span data-ttu-id="27f7a-223">Em **Centros de administração,** selecione o **SharePoint** de administração.</span><span class="sxs-lookup"><span data-stu-id="27f7a-223">Under **Admin centers**, select the **SharePoint** admin center.</span></span>
   1. <span data-ttu-id="27f7a-224">Selecione **Mais recursos** no menu barra lateral.</span><span class="sxs-lookup"><span data-stu-id="27f7a-224">Select **More features** from the sidebar menu.</span></span>
   1. <span data-ttu-id="27f7a-225">Pressione **Abrir** em **Aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="27f7a-225">Press **Open** under **Apps**.</span></span>
   1. <span data-ttu-id="27f7a-226">Selecione **Catálogo de Aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="27f7a-226">Select **App Catalog**.</span></span>

1. <span data-ttu-id="27f7a-227">Selecione **Distribuir aplicativos para SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="27f7a-227">Select **Distribute apps for SharePoint**.</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-distribute-apps.png" alt-text="Distribuir aplicativos para SharePoint.":::

1. <span data-ttu-id="27f7a-229">Selecione **Upload**.</span><span class="sxs-lookup"><span data-stu-id="27f7a-229">Select **Upload**.</span></span>

1. <span data-ttu-id="27f7a-230">Selecione **Escolher Arquivo**.</span><span class="sxs-lookup"><span data-stu-id="27f7a-230">Select **Choose File**.</span></span>

1. <span data-ttu-id="27f7a-231">Localize `{project}.sppkg` seu arquivo na pasta dentro do seu `SPFx/sharepoint/solution` projeto.</span><span class="sxs-lookup"><span data-stu-id="27f7a-231">Locate your `{project}.sppkg` file in the `SPFx/sharepoint/solution` folder within your project.</span></span> <span data-ttu-id="27f7a-232">Selecione **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="27f7a-232">Select **Open**.</span></span>

1. <span data-ttu-id="27f7a-233">Selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="27f7a-233">Select **OK**.</span></span>

1. <span data-ttu-id="27f7a-234">O SharePoint de implantação será automaticamente iniciar.</span><span class="sxs-lookup"><span data-stu-id="27f7a-234">The SharePoint deployment process will automatically start.</span></span> <span data-ttu-id="27f7a-235">Verifique se **Tornar essa solução disponível para todos os sites da organização** está selecionada.</span><span class="sxs-lookup"><span data-stu-id="27f7a-235">Verify that **Make this solution available to all sites in the organization** is selected.</span></span> <span data-ttu-id="27f7a-236">Em seguida, **selecione Implantar**.</span><span class="sxs-lookup"><span data-stu-id="27f7a-236">Then select **Deploy**.</span></span>

1. <span data-ttu-id="27f7a-237">Selecione a **guia ARQUIVOS.**</span><span class="sxs-lookup"><span data-stu-id="27f7a-237">Select the **FILES** tab.</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-appcatalog-filestab.png" alt-text="Selecione a guia arquivos no catálogo SharePoint App.":::

1. <span data-ttu-id="27f7a-239">selecione o pacote implantado e selecione **Sincronizar para Teams** no canto superior direito.</span><span class="sxs-lookup"><span data-stu-id="27f7a-239">select the package you deployed, then select **Sync to Teams** from the upper right corner.</span></span>

    > [!Note]
    > <span data-ttu-id="27f7a-240">O processo Sincronizar Teams pode levar alguns minutos.</span><span class="sxs-lookup"><span data-stu-id="27f7a-240">The Sync to Teams process can take a couple of minutes.</span></span>  <span data-ttu-id="27f7a-241">Você verá uma mensagem no lado direito do navegador indicando que o aplicativo foi sincronizado com êxito com Teams.</span><span class="sxs-lookup"><span data-stu-id="27f7a-241">You will see a message on the right-hand side of the browser indicating that the app has successfully synchronized to Teams.</span></span>

   <span data-ttu-id="27f7a-242">Abra o Teams aplicativo (ou entre `https://teams.microsoft.com` em ).</span><span class="sxs-lookup"><span data-stu-id="27f7a-242">Open the Teams application (or sign in at `https://teams.microsoft.com`).</span></span>  <span data-ttu-id="27f7a-243">Pressione o ponto triplo na barra lateral e selecione **Todos os aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="27f7a-243">Press the triple-dot on the sidebar, then select **All apps**.</span></span>  <span data-ttu-id="27f7a-244">O aplicativo será colocado nos **Aplicativos construídos para sua categoria organizacional.**</span><span class="sxs-lookup"><span data-stu-id="27f7a-244">The app will be placed in the **Apps built for your org** category.</span></span>  <span data-ttu-id="27f7a-245">Você pode adicionar o aplicativo a partir daí.</span><span class="sxs-lookup"><span data-stu-id="27f7a-245">You can add the app from there.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-app-in-teams.png" alt-text="Captura de tela mostrando o aplicativo dentro Teams":::

## <a name="see-also"></a><span data-ttu-id="27f7a-247">Confira também</span><span class="sxs-lookup"><span data-stu-id="27f7a-247">See also</span></span>

* [<span data-ttu-id="27f7a-248">Visão geral dos tutoriais</span><span class="sxs-lookup"><span data-stu-id="27f7a-248">Tutorials Overview</span></span>](code-samples.md)
* [<span data-ttu-id="27f7a-249">Criar um programa bot de conversação</span><span class="sxs-lookup"><span data-stu-id="27f7a-249">Create a conversational bot app</span></span>](first-app-bot.md)
* [<span data-ttu-id="27f7a-250">Criar uma extensão de mensagem</span><span class="sxs-lookup"><span data-stu-id="27f7a-250">Create a messaging extension</span></span>](first-message-extension.md)
* [<span data-ttu-id="27f7a-251">Exemplos de código</span><span class="sxs-lookup"><span data-stu-id="27f7a-251">Code Samples</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples)
