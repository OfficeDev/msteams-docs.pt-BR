---
title: Começar - Criar seu primeiro aplicativo Teams com SPFx
author: zhenyasav
description: Saiba como criar uma guia personalizada com a Estrutura do SharePoint
ms.author: zhenyasa
ms.date: 05/19/2021
ms.topic: quickstart
ms.openlocfilehash: 54886b47bbe70fed5dd1f010517e6c91d8d5a50d
ms.sourcegitcommit: 9cabeaed9baf96c8caeb1497f0bc37abdb787d22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/25/2021
ms.locfileid: "52646608"
---
# <a name="build-and-run-your-first-microsoft-teams-app-with-sharepoint-framework-spfx"></a><span data-ttu-id="c7137-103">Crie e execute seu primeiro aplicativo Microsoft Teams com Estrutura do SharePoint (SPFx)</span><span class="sxs-lookup"><span data-stu-id="c7137-103">Build and run your first Microsoft Teams app with SharePoint Framework (SPFx)</span></span>

<span data-ttu-id="c7137-104">Neste tutorial, você criará um novo aplicativo Microsoft Teams no Estrutura do SharePoint (SPFx) que implementa um aplicativo pessoal simples.</span><span class="sxs-lookup"><span data-stu-id="c7137-104">In this tutorial, you will create a new Microsoft Teams app in SharePoint Framework (SPFx) that implements a simple personal app.</span></span> <span data-ttu-id="c7137-105">(Um *aplicativo pessoal* inclui um conjunto de guias com escopo para uso individual.) Durante o tutorial, você aprenderá sobre a estrutura de um aplicativo Teams, como executar o aplicativo localmente e como implantar o aplicativo SharePoint.</span><span class="sxs-lookup"><span data-stu-id="c7137-105">(A *personal app* includes a set of tabs scoped for individual use.) During the tutorial, you will learn about the structure of a Teams app, how to run the app locally, and how to deploy the app to SharePoint.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="c7137-106">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="c7137-106">Before you begin</span></span>

<span data-ttu-id="c7137-107">Certifique-se de que seu ambiente de desenvolvimento está definido instalando os [pré-requisitos](prerequisites.md)</span><span class="sxs-lookup"><span data-stu-id="c7137-107">Make sure your development environment is set up by installing the [prerequisites](prerequisites.md)</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c7137-108">Pré-requisitos de instalação</span><span class="sxs-lookup"><span data-stu-id="c7137-108">Install prerequisites</span></span>](prerequisites.md)

## <a name="get-organized"></a><span data-ttu-id="c7137-109">Organizar-se</span><span class="sxs-lookup"><span data-stu-id="c7137-109">Get organized</span></span>

<span data-ttu-id="c7137-110">Além dos pré-requisitos, você também precisa ser administrador de um conjunto SharePoint Site.</span><span class="sxs-lookup"><span data-stu-id="c7137-110">In addition to the prerequisites, you also need to be an Administrator for a SharePoint Site Collection.</span></span>  <span data-ttu-id="c7137-111">É aqui que você implantará seu aplicativo para hospedagem.</span><span class="sxs-lookup"><span data-stu-id="c7137-111">This is where you will deploy your app for hosting.</span></span>  <span data-ttu-id="c7137-112">Se você estiver usando um locatário de programa de desenvolvedor do M365, use a conta de administrador configurada quando se registrou no programa.</span><span class="sxs-lookup"><span data-stu-id="c7137-112">If you are using an M365 developer program tenant, use the administrator account you set up when you registered for the program.</span></span>  

## <a name="create-your-project"></a><span data-ttu-id="c7137-113">Criar seu projeto</span><span class="sxs-lookup"><span data-stu-id="c7137-113">Create your project</span></span>

<span data-ttu-id="c7137-114">Use o Teams Toolkit para criar seu primeiro projeto:</span><span class="sxs-lookup"><span data-stu-id="c7137-114">Use the Teams Toolkit to create your first project:</span></span>

# <a name="visual-studio-code"></a>[<span data-ttu-id="c7137-115">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="c7137-115">Visual Studio Code</span></span>](#tab/vscode)

1. <span data-ttu-id="c7137-116">Abra Visual Studio código.</span><span class="sxs-lookup"><span data-stu-id="c7137-116">Open Visual Studio code.</span></span>
1. <span data-ttu-id="c7137-117">Abra o Teams Toolkit selecionando o ícone Teams na barra lateral:</span><span class="sxs-lookup"><span data-stu-id="c7137-117">Open the Teams Toolkit by selecting the Teams icon in the sidebar:</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="O Teams ícone na barra Visual Studio Code lateral.":::

1. <span data-ttu-id="c7137-119">Selecione **Criar Novo Project**.</span><span class="sxs-lookup"><span data-stu-id="c7137-119">Select **Create New Project**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project.png" alt-text="Local do link Criar novo Project na barra Teams Toolkit lado.":::

1. <span data-ttu-id="c7137-121">Selecione **Criar um novo Teams app**.</span><span class="sxs-lookup"><span data-stu-id="c7137-121">Select **Create a new Teams app**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-new-project-intro.png" alt-text="Início do assistente para Criar novo Project":::

1. <span data-ttu-id="c7137-123">Na etapa **Selecionar recursos,** o recurso **Tab** já estará selecionado.</span><span class="sxs-lookup"><span data-stu-id="c7137-123">On the **Select capabilities** step, the **Tab** capability will already be selected.</span></span>  <span data-ttu-id="c7137-124">Pressione **OK**.</span><span class="sxs-lookup"><span data-stu-id="c7137-124">Press **OK**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-capabilities.png" alt-text="Captura de tela mostrando como adicionar recursos ao seu novo aplicativo.":::

1. <span data-ttu-id="c7137-126">Na etapa **de tipo de hospedagem frontend,** selecione **Estrutura do SharePoint (SPFx)**.</span><span class="sxs-lookup"><span data-stu-id="c7137-126">On the **Frontend hosting type** step, select **SharePoint Framework (SPFx)**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-hosting.png" alt-text="Captura de tela mostrando como selecionar hospedagem para seu novo aplicativo.":::

1. <span data-ttu-id="c7137-128">Na etapa **Estrutura,** selecione **React**.</span><span class="sxs-lookup"><span data-stu-id="c7137-128">On the **Framework** step, select **React**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-which-framework.png" alt-text="Selecionar Estrutura":::

1. <span data-ttu-id="c7137-130">Quando solicitado a um **Nome da Webpart,** pressione **Enter** para aceitar o padrão.</span><span class="sxs-lookup"><span data-stu-id="c7137-130">When asked for a **Webpart Name**, press **Enter** to accept the default.</span></span>

1. <span data-ttu-id="c7137-131">Quando solicitado para a **Descrição da Webpart,** pressione **Enter** para aceitar o padrão.</span><span class="sxs-lookup"><span data-stu-id="c7137-131">When asked for the **Webpart Description**, press **Enter** to accept the default.</span></span>

1. <span data-ttu-id="c7137-132">Quando solicitado a linguagem **de programação,** pressione **Enter** para aceitar o padrão.</span><span class="sxs-lookup"><span data-stu-id="c7137-132">When asked for the **Programming Language**, press **Enter** to accept the default.</span></span>

1. <span data-ttu-id="c7137-133">Selecione uma pasta de espaço de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c7137-133">Select a workspace folder.</span></span>  <span data-ttu-id="c7137-134">Uma pasta será criada em sua pasta de espaço de trabalho para o projeto que você está criando.</span><span class="sxs-lookup"><span data-stu-id="c7137-134">A folder will be created within your workspace folder for the project you are creating.</span></span>

1. <span data-ttu-id="c7137-135">Insira um nome adequado para seu aplicativo, como `helloworld` .</span><span class="sxs-lookup"><span data-stu-id="c7137-135">Enter a suitable name for your app, like `helloworld`.</span></span>  <span data-ttu-id="c7137-136">O nome do aplicativo deve consistir apenas em caracteres alfanuméricos.</span><span class="sxs-lookup"><span data-stu-id="c7137-136">The name of the app must consist only of alphanumeric characters.</span></span>  <span data-ttu-id="c7137-137">Pressione **Enter** para continuar.</span><span class="sxs-lookup"><span data-stu-id="c7137-137">Press **Enter** to continue.</span></span>

<span data-ttu-id="c7137-138">Seu Teams aplicativo será criado em alguns segundos.</span><span class="sxs-lookup"><span data-stu-id="c7137-138">Your Teams app will be created within a few seconds.</span></span>

# <a name="command-line"></a>[<span data-ttu-id="c7137-139">Linha de comando</span><span class="sxs-lookup"><span data-stu-id="c7137-139">Command line</span></span>](#tab/cli)

<span data-ttu-id="c7137-140">Use a `teamsfx` CLI para criar seu primeiro projeto.</span><span class="sxs-lookup"><span data-stu-id="c7137-140">Use the `teamsfx` CLI to create your first project.</span></span>  <span data-ttu-id="c7137-141">Comece na pasta onde você deseja criar a pasta do projeto.</span><span class="sxs-lookup"><span data-stu-id="c7137-141">Start from the folder where you want to create the project folder.</span></span>

``` bash
teamsfx new
```

<span data-ttu-id="c7137-142">A CLI orienta algumas perguntas para criar o projeto.</span><span class="sxs-lookup"><span data-stu-id="c7137-142">The CLI walks through some questions to create the project.</span></span>  <span data-ttu-id="c7137-143">Cada pergunta lhe dirá como respondê-la (por exemplo, para usar teclas de seta para selecionar uma opção).</span><span class="sxs-lookup"><span data-stu-id="c7137-143">Each question will tell you how to answer it (for example, to use arrow keys to select an option).</span></span>  <span data-ttu-id="c7137-144">Quando tiver respondido à pergunta, confirme sua escolha pressionando **Enter**.</span><span class="sxs-lookup"><span data-stu-id="c7137-144">When you have answered the question, confirm your choice by pressing **Enter**.</span></span>

1. <span data-ttu-id="c7137-145">Selecione **Criar um novo Teams app**.</span><span class="sxs-lookup"><span data-stu-id="c7137-145">Select **Create a new Teams app**.</span></span>
1. <span data-ttu-id="c7137-146">Escolha o **recurso Tab.**</span><span class="sxs-lookup"><span data-stu-id="c7137-146">Choose the **Tab** capability.</span></span>
1. <span data-ttu-id="c7137-147">Selecione **Estrutura do SharePoint (SPFx)** de frontend.</span><span class="sxs-lookup"><span data-stu-id="c7137-147">Select **SharePoint Framework (SPFx)** frontend hosting.</span></span>
1. <span data-ttu-id="c7137-148">Selecione **React** estrutura.</span><span class="sxs-lookup"><span data-stu-id="c7137-148">Select **React** framework.</span></span>
1. <span data-ttu-id="c7137-149">Pressione **Enter** para o **Nome da Webpart**.</span><span class="sxs-lookup"><span data-stu-id="c7137-149">Press **Enter** for the **Webpart Name**.</span></span>
1. <span data-ttu-id="c7137-150">Pressione **Enter** para a **Descrição da Webpart**.</span><span class="sxs-lookup"><span data-stu-id="c7137-150">Press **Enter** for the **Webpart Description**.</span></span>
1. <span data-ttu-id="c7137-151">Pressione **Enter** para a **Linguagem de Programação**.</span><span class="sxs-lookup"><span data-stu-id="c7137-151">Press **Enter** for the **Programming Language**.</span></span>
1. <span data-ttu-id="c7137-152">Pressione **Enter** para selecionar a pasta de espaço de trabalho padrão.</span><span class="sxs-lookup"><span data-stu-id="c7137-152">Press **Enter** to select the default workspace folder.</span></span>
1. <span data-ttu-id="c7137-153">Insira um nome adequado para seu aplicativo, como `helloworld` .</span><span class="sxs-lookup"><span data-stu-id="c7137-153">Enter a suitable name for your app, like `helloworld`.</span></span>  <span data-ttu-id="c7137-154">O nome do aplicativo deve consistir apenas em caracteres alfanuméricos.</span><span class="sxs-lookup"><span data-stu-id="c7137-154">The name of the app must consist only of alphanumeric characters.</span></span>

<span data-ttu-id="c7137-155">Depois que todas as perguntas foram respondidas, seu projeto será criado.</span><span class="sxs-lookup"><span data-stu-id="c7137-155">Once all the questions have been answered, your project will be created.</span></span>

---

- [<span data-ttu-id="c7137-156">Saiba mais sobre o desenvolvimento para Estrutura do SharePoint</span><span class="sxs-lookup"><span data-stu-id="c7137-156">Learn more about developing for SharePoint Framework</span></span>](/sharepoint/dev/spfx/sharepoint-framework-overview)

## <a name="take-a-tour-of-the-source-code"></a><span data-ttu-id="c7137-157">Fazer um tour pelo código-fonte</span><span class="sxs-lookup"><span data-stu-id="c7137-157">Take a tour of the source code</span></span>

<span data-ttu-id="c7137-158">Se quiser ignorar essa seção por enquanto, você pode [executar seu aplicativo localmente.](#run-your-app-locally)</span><span class="sxs-lookup"><span data-stu-id="c7137-158">If you wish to skip this section for now, you can [run your app locally](#run-your-app-locally).</span></span>

<span data-ttu-id="c7137-159">Depois que Teams Toolkit configura seu projeto, você tem os componentes para criar um aplicativo pessoal básico para Teams que está hospedado no Estrutura do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="c7137-159">Once the Teams Toolkit configures your project, you have the components to build a basic personal app for Teams that is hosted within the SharePoint Framework.</span></span>  <span data-ttu-id="c7137-160">Os diretórios e arquivos do projeto são exibidos na área Explorer do Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="c7137-160">The project directories and files display in the Explorer area of Visual Studio Code.</span></span>

:::image type="content" source="../assets/images/teams-toolkit-v2/app-project-files-spfx.png" alt-text="Captura de tela mostrando arquivos de projeto de aplicativo para um aplicativo pessoal Visual Studio Code.":::

<span data-ttu-id="c7137-162">O Toolkit cria automaticamente o scaffolding para você no diretório do projeto com base nos recursos adicionados durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="c7137-162">The Toolkit automatically creates scaffolding for you in the project directory based on the capabilities you added during setup.</span></span> <span data-ttu-id="c7137-163">O Teams Toolkit mantém seu estado para seu aplicativo no `.fx` diretório.</span><span class="sxs-lookup"><span data-stu-id="c7137-163">The Teams Toolkit maintains its state for your app in the `.fx` directory.</span></span>  <span data-ttu-id="c7137-164">Entre outros itens neste diretório:</span><span class="sxs-lookup"><span data-stu-id="c7137-164">Among other items in this directory:</span></span>

- <span data-ttu-id="c7137-165">Os ícones do aplicativo são armazenados como arquivos PNG `color.png` em `outline.png` e .</span><span class="sxs-lookup"><span data-stu-id="c7137-165">The app icons are stored as PNG files in `color.png` and `outline.png`.</span></span>
- <span data-ttu-id="c7137-166">O manifesto do aplicativo para publicação no Portal do Desenvolvedor para Teams é armazenado em `manifest.source.json` .</span><span class="sxs-lookup"><span data-stu-id="c7137-166">The app manifest for publishing to Developer Portal for Teams is stored in `manifest.source.json`.</span></span>
- <span data-ttu-id="c7137-167">As configurações escolhidas ao criar o projeto são armazenadas em `settings.json` .</span><span class="sxs-lookup"><span data-stu-id="c7137-167">The settings you chose when creating the project are stored in `settings.json`.</span></span>

<span data-ttu-id="c7137-168">Como você selecionou um SPFx webpart, os seguintes arquivos são relevantes para sua interface do usuário:</span><span class="sxs-lookup"><span data-stu-id="c7137-168">Since you selected an SPFx Webpart project, the following files are relevant to your UI:</span></span>

- <span data-ttu-id="c7137-169">A pasta `SPFx/src/webparts/{webpart}` contém sua SPFx webpart.</span><span class="sxs-lookup"><span data-stu-id="c7137-169">The folder `SPFx/src/webparts/{webpart}` contains your SPFx webpart.</span></span>
- <span data-ttu-id="c7137-170">O arquivo `.vscode/launch.json` descreve as configurações de depuração disponíveis na paleta de depuração.</span><span class="sxs-lookup"><span data-stu-id="c7137-170">The file `.vscode/launch.json` describes the debugging configurations available in the debug palette.</span></span>

<span data-ttu-id="c7137-171">Para obter mais informações sobre SharePoint Webparts para Teams, [consulte a documentação SharePoint.](/sharepoint/dev/spfx/build-for-teams-overview)</span><span class="sxs-lookup"><span data-stu-id="c7137-171">For more information about SharePoint Webparts for Teams, [refer to the SharePoint documentation](/sharepoint/dev/spfx/build-for-teams-overview).</span></span>

## <a name="run-your-app-locally"></a><span data-ttu-id="c7137-172">Executar seu aplicativo localmente</span><span class="sxs-lookup"><span data-stu-id="c7137-172">Run your app locally</span></span>

<span data-ttu-id="c7137-173">Teams Toolkit permite que você hospede seu aplicativo localmente e execute-o por meio do [Estrutura do SharePoint Workbench](/sharepoint/dev/spfx/debug-in-vscode).</span><span class="sxs-lookup"><span data-stu-id="c7137-173">Teams Toolkit allows you to host your app locally and run it through the [SharePoint Framework Workbench](/sharepoint/dev/spfx/debug-in-vscode).</span></span>

### <a name="build-and-run-your-app-locally-in-visual-studio-code"></a><span data-ttu-id="c7137-174">Criar e executar seu aplicativo localmente Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="c7137-174">Build and run your app locally in Visual Studio Code</span></span>

<span data-ttu-id="c7137-175">Para criar e executar seu aplicativo localmente:</span><span class="sxs-lookup"><span data-stu-id="c7137-175">To build and run your app locally:</span></span>

1. <span data-ttu-id="c7137-176">De Visual Studio Code, pressione **F5**.</span><span class="sxs-lookup"><span data-stu-id="c7137-176">From Visual Studio Code, press **F5**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-debug-local.png" alt-text="Captura de tela mostrando como iniciar um SPFx em um workbench local.":::

   > [!NOTE]
   > <span data-ttu-id="c7137-178">Quando você executar o aplicativo pela primeira vez, todas as dependências serão baixadas e o aplicativo será criado.</span><span class="sxs-lookup"><span data-stu-id="c7137-178">When you run the app for the first time, all dependencies are downloaded and the app is built.</span></span>  <span data-ttu-id="c7137-179">Uma janela do navegador é aberta automaticamente e carrega o SharePoint Workbench quando a com build estiver concluída.</span><span class="sxs-lookup"><span data-stu-id="c7137-179">A browser window automatically opens and loads the SharePoint Workbench when the build is complete.</span></span>  <span data-ttu-id="c7137-180">Isso pode levar de 3 a 5 minutos para ser concluído.</span><span class="sxs-lookup"><span data-stu-id="c7137-180">This can take 3-5 minutes to complete.</span></span>

   <span data-ttu-id="c7137-181">Depois que o SharePoint Workbench for carregado.</span><span class="sxs-lookup"><span data-stu-id="c7137-181">Once the SharePoint Workbench is loaded.</span></span>

   >[!NOTE]
   > <span data-ttu-id="c7137-182">A Toolkit solicitará que você instale um certificado local, se necessário.</span><span class="sxs-lookup"><span data-stu-id="c7137-182">The Toolkit will prompt you to install a local certificate if needed.</span></span> <span data-ttu-id="c7137-183">Esse certificado permite Teams carregar seu aplicativo de `https://localhost` .</span><span class="sxs-lookup"><span data-stu-id="c7137-183">This certificate allows Teams to load your application from `https://localhost`.</span></span> <span data-ttu-id="c7137-184">Selecione sim quando a caixa de diálogo a seguir for exibida:</span><span class="sxs-lookup"><span data-stu-id="c7137-184">Select yes when the following dialog appears:</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/ssl-prompt.png" alt-text="Captura de tela mostrando como o prompt para instalar um certificado SSL para permitir Teams carregar seu aplicativo do localhost.":::

1. <span data-ttu-id="c7137-186">Pressione um dos ícones **Adicionar Webpart** (+) para adicionar sua webpart.</span><span class="sxs-lookup"><span data-stu-id="c7137-186">Press one of the **Add Webpart** (+) icons to add your webpart.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-workbench-addpart.png" alt-text="Captura de tela mostrando o SPFx workbench em execução com o pop-up para adicionar uma webpart mostrando.":::

1. <span data-ttu-id="c7137-188">Escolha sua webpart no menu.</span><span class="sxs-lookup"><span data-stu-id="c7137-188">Choose your webpart from the menu.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-workbench-addpart2.png" alt-text="Captura de tela mostrando o SPFx workbench em execução com o pop-up para adicionar uma seleção de webpart.":::

<span data-ttu-id="c7137-190">Seu aplicativo agora deve estar em execução.</span><span class="sxs-lookup"><span data-stu-id="c7137-190">Your app should now be running.</span></span>  <span data-ttu-id="c7137-191">Você pode fazer atividades normais de depuração como se fosse qualquer outra webpart SPFx (como definir pontos de interrupção).</span><span class="sxs-lookup"><span data-stu-id="c7137-191">You can do normal debugging activities as if this were any other SPFx webpart (such as setting breakpoints).</span></span>

> [!TIP]
> <span data-ttu-id="c7137-192">Tente colocar pontos de interrupção no método render de `SPFx/src/webparts/{webpart}/{webpart}.ts` e recarregar a janela do navegador.</span><span class="sxs-lookup"><span data-stu-id="c7137-192">Try placing breakpoints in the render method of `SPFx/src/webparts/{webpart}/{webpart}.ts` and reloading the browser window.</span></span> <span data-ttu-id="c7137-193">VS Code parar em pontos de interrupção em seu código.</span><span class="sxs-lookup"><span data-stu-id="c7137-193">VS Code will stop on breakpoints in your code.</span></span>

## <a name="deploy-your-app-to-sharepoint"></a><span data-ttu-id="c7137-194">Implantar seu aplicativo para SharePoint</span><span class="sxs-lookup"><span data-stu-id="c7137-194">Deploy your app to SharePoint</span></span>

<span data-ttu-id="c7137-195">Verifique se existe SharePoint catálogo de aplicativos em sua implantação.</span><span class="sxs-lookup"><span data-stu-id="c7137-195">Ensure a SharePoint App Catalog exists in your deployment.</span></span>  <span data-ttu-id="c7137-196">Se um não existir, [crie um](/sharepoint/use-app-catalog).</span><span class="sxs-lookup"><span data-stu-id="c7137-196">If one does not exist, [create one](/sharepoint/use-app-catalog).</span></span>  <span data-ttu-id="c7137-197">Pode levar até 15 minutos para que o catálogo de aplicativos seja totalmente criado.</span><span class="sxs-lookup"><span data-stu-id="c7137-197">It may take up to 15 minutes for the app catalog to be fully created.</span></span>

# <a name="visual-studio-code"></a>[<span data-ttu-id="c7137-198">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="c7137-198">Visual Studio Code</span></span>](#tab/vscode)

1. <span data-ttu-id="c7137-199">Abra Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="c7137-199">Open Visual Studio Code.</span></span>
1. <span data-ttu-id="c7137-200">Selecione a Teams Toolkit na barra lateral selecionando o ícone Teams.</span><span class="sxs-lookup"><span data-stu-id="c7137-200">Select the Teams Toolkit from the sidebar by selecting the Teams icon.</span></span>
1. <span data-ttu-id="c7137-201">Selecione **Provisionamento na Nuvem**.</span><span class="sxs-lookup"><span data-stu-id="c7137-201">Select **Provision in the Cloud**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/provisioning-commands.png" alt-text="Captura de tela mostrando os comandos de provisionamento":::

1. <span data-ttu-id="c7137-203">Você pode monitorar o progresso observando as caixas de diálogo no canto inferior direito.</span><span class="sxs-lookup"><span data-stu-id="c7137-203">You can monitor the progress by watching the dialogs in the bottom right corner.</span></span>  <span data-ttu-id="c7137-204">Após alguns segundos, você verá o seguinte aviso:</span><span class="sxs-lookup"><span data-stu-id="c7137-204">After a few seconds, you will see the following notice:</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/provision-complete.png" alt-text="Captura de tela mostrando a caixa de diálogo completa de provisionamento.":::

1. <span data-ttu-id="c7137-206">Depois que o provisionamento for concluído, selecione **Implantar na nuvem**.</span><span class="sxs-lookup"><span data-stu-id="c7137-206">Once provisioning is complete, select **Deploy to the cloud**.</span></span>

1. <span data-ttu-id="c7137-207">Atualmente, a implantação automatizada não está disponível.</span><span class="sxs-lookup"><span data-stu-id="c7137-207">Currently, automated deployment is not available.</span></span>  <span data-ttu-id="c7137-208">Uma caixa de diálogo será exibida solicitando que você crie e implante manualmente.</span><span class="sxs-lookup"><span data-stu-id="c7137-208">A dialog will pop up prompting you to build and deploy manually.</span></span> <span data-ttu-id="c7137-209">Pressione **Build SharePoint Package**.</span><span class="sxs-lookup"><span data-stu-id="c7137-209">Press **Build SharePoint Package**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/build-sharepoint-package.png" alt-text="Captura de tela para a caixa de diálogo Criar Pacote do Sharepoint":::

# <a name="command-line"></a>[<span data-ttu-id="c7137-211">Linha de comando</span><span class="sxs-lookup"><span data-stu-id="c7137-211">Command line</span></span>](#tab/cli)

<span data-ttu-id="c7137-212">Em sua janela de terminal:</span><span class="sxs-lookup"><span data-stu-id="c7137-212">In your terminal window:</span></span>

1. <span data-ttu-id="c7137-213">Executar `teamsfx provision` .</span><span class="sxs-lookup"><span data-stu-id="c7137-213">Run `teamsfx provision`.</span></span>

   ``` bash
   teamsfx provision
   ```

   <span data-ttu-id="c7137-214">Você pode ser solicitado a fazer logoff na sua assinatura do Azure.</span><span class="sxs-lookup"><span data-stu-id="c7137-214">You may be prompted to log in to your Azure subscription.</span></span>  <span data-ttu-id="c7137-215">Se necessário, você será solicitado a selecionar uma assinatura do Azure a ser usada para os recursos do Azure.</span><span class="sxs-lookup"><span data-stu-id="c7137-215">If required, you will be prompted to select an Azure subscription to use for the Azure resources.</span></span>

   > [!NOTE]
   > <span data-ttu-id="c7137-216">Sempre há alguns recursos do Azure usados para hospedar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c7137-216">There are always some Azure resources used for hosting your app.</span></span>

1. <span data-ttu-id="c7137-217">Executar `teamsfx deploy` .</span><span class="sxs-lookup"><span data-stu-id="c7137-217">Run `teamsfx deploy`.</span></span>

   ``` bash
   teamsfx deploy
   ```

1. <span data-ttu-id="c7137-218">Quando solicitado, selecione **Criar SharePoint Pacote**.</span><span class="sxs-lookup"><span data-stu-id="c7137-218">When prompted, select **Build SharePoint Package**.</span></span>

---

<span data-ttu-id="c7137-219">O SharePoint pacote está localizado `SPFx/sharepoint/solution` no seu projeto.</span><span class="sxs-lookup"><span data-stu-id="c7137-219">The SharePoint package is located in `SPFx/sharepoint/solution` within your project.</span></span>  <span data-ttu-id="c7137-220">Upload pacote para SharePoint:</span><span class="sxs-lookup"><span data-stu-id="c7137-220">Upload the package to SharePoint:</span></span>

1. <span data-ttu-id="c7137-221">Faça logon no Console de Administração do M365 e navegue até o SharePoint App Catalog.</span><span class="sxs-lookup"><span data-stu-id="c7137-221">Log into the M365 Admin Console, then navigate to the SharePoint App Catalog.</span></span>

   - <span data-ttu-id="c7137-222">Abra `https://admin.microsoft.com/AdminPortal/Home` .</span><span class="sxs-lookup"><span data-stu-id="c7137-222">Open `https://admin.microsoft.com/AdminPortal/Home`.</span></span>
   - <span data-ttu-id="c7137-223">Em **Centros de administração,** selecione o **SharePoint** de administração.</span><span class="sxs-lookup"><span data-stu-id="c7137-223">Under **Admin centers**, select the **SharePoint** admin center.</span></span>
   - <span data-ttu-id="c7137-224">Selecione **Mais recursos** no menu barra lateral.</span><span class="sxs-lookup"><span data-stu-id="c7137-224">Select **More features** from the sidebar menu.</span></span>
   - <span data-ttu-id="c7137-225">Pressione **Abrir** em **Aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="c7137-225">Press **Open** under **Apps**.</span></span>
   - <span data-ttu-id="c7137-226">Selecione **Catálogo de Aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="c7137-226">Select **App Catalog**.</span></span>

1. <span data-ttu-id="c7137-227">Selecione **Distribuir aplicativos para SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="c7137-227">Select **Distribute apps for SharePoint**.</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-distribute-apps.png" alt-text="Distribuir aplicativos para SharePoint.":::

1. <span data-ttu-id="c7137-229">Selecione **Upload**.</span><span class="sxs-lookup"><span data-stu-id="c7137-229">Select **Upload**.</span></span>

1. <span data-ttu-id="c7137-230">Pressione **Escolher Arquivo**.</span><span class="sxs-lookup"><span data-stu-id="c7137-230">Press **Choose File**.</span></span>

1. <span data-ttu-id="c7137-231">Localize `{project}.sppkg` seu arquivo, localizado na `SPFx/sharepoint/solution` pasta dentro do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="c7137-231">Locate your `{project}.sppkg` file, located in the `SPFx/sharepoint/solution` folder within your project.</span></span>  <span data-ttu-id="c7137-232">Pressione **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="c7137-232">Press **Open**.</span></span>

1. <span data-ttu-id="c7137-233">Pressione **OK**.</span><span class="sxs-lookup"><span data-stu-id="c7137-233">Press **OK**.</span></span>

1. <span data-ttu-id="c7137-234">O SharePoint de implantação será automaticamente iniciar.</span><span class="sxs-lookup"><span data-stu-id="c7137-234">The SharePoint deployment process will automatically start.</span></span>  <span data-ttu-id="c7137-235">**Certifique-se de tornar essa solução disponível para todos os sites na** organização está marcada e pressione **Implantar**.</span><span class="sxs-lookup"><span data-stu-id="c7137-235">Ensure **Make this solution available to all sites in the organization** is checked, then press **Deploy**.</span></span>

1. <span data-ttu-id="c7137-236">Selecione a **guia ARQUIVOS.**</span><span class="sxs-lookup"><span data-stu-id="c7137-236">Select the **FILES** tab.</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-appcatalog-filestab.png" alt-text="Selecione a guia arquivos no catálogo SharePoint App.":::

1. <span data-ttu-id="c7137-238">selecione o pacote implantado e pressione **Sincronizar para Teams** na faixa de opções.</span><span class="sxs-lookup"><span data-stu-id="c7137-238">select the package you deployed, then press **Sync to Teams** in the ribbon.</span></span>

    > [!Note]
    > <span data-ttu-id="c7137-239">O processo Sincronizar Teams pode levar alguns minutos.</span><span class="sxs-lookup"><span data-stu-id="c7137-239">The Sync to Teams process can take a couple of minutes.</span></span>  <span data-ttu-id="c7137-240">Você verá uma mensagem no lado direito do navegador indicando que o aplicativo foi sincronizado com êxito com Teams.</span><span class="sxs-lookup"><span data-stu-id="c7137-240">You will see a message on the right-hand side of the browser indicating that the app has successfully synchronized to Teams.</span></span>

<span data-ttu-id="c7137-241">Abra o Teams aplicativo (ou entre `https://teams.microsoft.com` em ).</span><span class="sxs-lookup"><span data-stu-id="c7137-241">Open the Teams application (or sign in at `https://teams.microsoft.com`).</span></span>  <span data-ttu-id="c7137-242">Pressione o ponto triplo na barra lateral e selecione **Todos os aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="c7137-242">Press the triple-dot on the sidebar, then select **All apps**.</span></span>  <span data-ttu-id="c7137-243">O aplicativo será colocado nos **Aplicativos construídos para sua categoria organizacional.**</span><span class="sxs-lookup"><span data-stu-id="c7137-243">The app will be placed in the **Apps built for your org** category.</span></span>  <span data-ttu-id="c7137-244">Você pode adicionar o aplicativo a partir daí.</span><span class="sxs-lookup"><span data-stu-id="c7137-244">You can add the app from there.</span></span>

:::image type="content" source="../assets/images/teams-toolkit-v2/spfx-app-in-teams.png" alt-text="Captura de tela mostrando o aplicativo dentro Teams":::

## <a name="next-steps"></a><span data-ttu-id="c7137-246">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="c7137-246">Next steps</span></span>

<span data-ttu-id="c7137-247">Saiba mais sobre outros métodos para criar Teams aplicativos:</span><span class="sxs-lookup"><span data-stu-id="c7137-247">Learn about other methods for creating Teams apps:</span></span>

- [<span data-ttu-id="c7137-248">Criar um Teams com React</span><span class="sxs-lookup"><span data-stu-id="c7137-248">Create a Teams app with React</span></span>](first-app-react.md)
- [<span data-ttu-id="c7137-249">Criar um Teams com o Blazor</span><span class="sxs-lookup"><span data-stu-id="c7137-249">Create a Teams app with Blazor</span></span>](first-app-blazor.md)
- [<span data-ttu-id="c7137-250">Criar um aplicativo bot de conversação</span><span class="sxs-lookup"><span data-stu-id="c7137-250">Create a conversational bot app</span></span>](first-app-bot.md)
- [<span data-ttu-id="c7137-251">Criar uma extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="c7137-251">Create a messaging extension</span></span>](first-message-extension.md)