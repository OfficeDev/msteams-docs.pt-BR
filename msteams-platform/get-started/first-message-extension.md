---
title: 'Introdução: Crie sua primeira extensão de mensagens'
author: adrianhall
description: Crie uma extensão de mensagens para o Microsoft Teams usando o Kit de Ferramentas do Teams.
ms.author: adhal
ms.date: 05/20/2021
ms.topic: quickstart
ms.openlocfilehash: bf00897beec92c64fe9dd68ca76e35751b3c7aed
ms.sourcegitcommit: 14409950307b135265c8582408be5277b35131dd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2021
ms.locfileid: "52994200"
---
# <a name="build-and-run-your-first-messaging-extension-for-microsoft-teams"></a><span data-ttu-id="cfd2b-103">Crie e execute sua primeira extensão de mensagens para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="cfd2b-103">Build and run your first messaging extension for Microsoft Teams</span></span>

<span data-ttu-id="cfd2b-104">Há dois tipos de **extensões de mensagens** do Teams:</span><span class="sxs-lookup"><span data-stu-id="cfd2b-104">There are two types of Teams **messaging extensions**:</span></span>

- <span data-ttu-id="cfd2b-105">[Comandos de pesquisa](../messaging-extensions/how-to/search-commands/define-search-command.md) permitem pesquisar sistemas externos e inserir os resultados dessa pesquisa em uma mensagem em forma de cartão.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-105">[Search commands](../messaging-extensions/how-to/search-commands/define-search-command.md) allow you to search external systems and insert the results of that search into a message in the form of a card.</span></span>
- <span data-ttu-id="cfd2b-106">[Comandos de ação](../messaging-extensions/how-to/action-commands/define-action-command.md) permitem que você apresente aos usuários um pop-up modal para coletar ou exibir informações e, em seguida, processar sua interação e enviar informações de volta para o Teams.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-106">[Action commands](../messaging-extensions/how-to/action-commands/define-action-command.md) allow you present your users with a modal popup to collect or display information, then process their interaction and send information back to Teams.</span></span>

<span data-ttu-id="cfd2b-107">Neste tutorial, você criará um *comando de pesquisa* para pesquisar dados externos e inserir os resultados em uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-107">In this tutorial, you will create a *search command* to search for external data and insert the results into a message.</span></span>  

## <a name="before-you-begin"></a><span data-ttu-id="cfd2b-108">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="cfd2b-108">Before you begin</span></span>

<span data-ttu-id="cfd2b-109">Certificar-se de que o seu ambiente de desenvolvimento esteja configurado instalando os [Pré-requisitos](prerequisites.md)</span><span class="sxs-lookup"><span data-stu-id="cfd2b-109">Make sure your development environment is set up by installing the [Prerequisites](prerequisites.md)</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cfd2b-110">Instalar Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="cfd2b-110">Install Prerequisites</span></span>](prerequisites.md)

## <a name="create-your-project"></a><span data-ttu-id="cfd2b-111">Criar o seu projeto</span><span class="sxs-lookup"><span data-stu-id="cfd2b-111">Create your project</span></span>

<span data-ttu-id="cfd2b-112">Use o Kit de ferramentas do Teams para criar o seu primeiro projeto:</span><span class="sxs-lookup"><span data-stu-id="cfd2b-112">Use the Teams Toolkit to create your first project:</span></span>

# <a name="visual-studio-code"></a>[<span data-ttu-id="cfd2b-113">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="cfd2b-113">Visual Studio Code</span></span>](#tab/vscode)

1. <span data-ttu-id="cfd2b-114">Abra o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-114">Open Visual Studio Code.</span></span>
1. <span data-ttu-id="cfd2b-115">Abra o Kit de Ferramentas do Teams selecionando o ícone do Teams na barra lateral:</span><span class="sxs-lookup"><span data-stu-id="cfd2b-115">Open the Teams Toolkit by selecting the Teams icon in the sidebar:</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="O ícone do Teams na barra lateral do Visual Studio Code":::

1. <span data-ttu-id="cfd2b-117">Selecione **Criar Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-117">Select **Create New Project**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project.png" alt-text="Localização do link de Criação de Novo Projeto na barra lateral do Kit de ferramentas do Teams.":::

1. <span data-ttu-id="cfd2b-119">Selecione **Criar um novo aplicativo do Teams**.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-119">Select **Create a new Teams app**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-new-project-intro.png" alt-text="Início do Assistente para Criar Novo Projeto":::

1. <span data-ttu-id="cfd2b-121">Na etapa **Selecionar recursos**, selecione **Extensão de Mensagem** e desmarque **Guia**. Pressione **OK**.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-121">On the **Select capabilities** step, select **Message Extension** and deselect **Tab**.  Press **OK**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/msgextn-create-project-capabilities.png" alt-text="Captura de tela mostrando como adicionar recursos ao seu novo aplicativo.":::

1. <span data-ttu-id="cfd2b-123">Na etapa **Registro de bot**, selecione **Criar um novo registro de bot**.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-123">On the **Bot registration** step, select **Create a new bot registration**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-bot-registration.png" alt-text="Selecione criar um novo registro de bot":::

   > [!NOTE]
   > <span data-ttu-id="cfd2b-125">As extensões de mensagens dependem dos bots para fornecer uma caixa de diálogo entre o usuário e seu código.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-125">Messaging extensions rely on bots to provide a dialog between the user and your code.</span></span>

1. <span data-ttu-id="cfd2b-126">Na etapa **Linguagem de Programação**, selecione **JavaScript**.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-126">On the **Programming Language** step, select **JavaScript**.</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-programming-languages.png" alt-text="Captura de tela mostrando como selecionar a linguagem de programação.":::

1. <span data-ttu-id="cfd2b-128">Selecione uma pasta do espaço de trabalho.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-128">Select a workspace folder.</span></span>  <span data-ttu-id="cfd2b-129">Uma pasta será criada dentro de sua pasta do espaço de trabalho para o projeto que você está criando.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-129">A folder will be created within your workspace folder for the project you are creating.</span></span>

1. <span data-ttu-id="cfd2b-130">Insira um nome adequado para seu aplicativo, como `helloworld`.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-130">Enter a suitable name for your app, like `helloworld`.</span></span>  <span data-ttu-id="cfd2b-131">O nome do aplicativo deve consistir apenas de caracteres alfanuméricos.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-131">The name of the app must consist only of alphanumeric characters.</span></span>  <span data-ttu-id="cfd2b-132">Pressione **Inserir** para continuar.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-132">Press **Enter** to continue.</span></span>

<span data-ttu-id="cfd2b-133">O seu aplicativo do Teams será criado em alguns segundos.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-133">Your Teams app will be created within a few seconds.</span></span>

# <a name="command-line"></a>[<span data-ttu-id="cfd2b-134">Linha de comando</span><span class="sxs-lookup"><span data-stu-id="cfd2b-134">Command line</span></span>](#tab/cli)

<span data-ttu-id="cfd2b-135">Use a CLI `teamsfx` para criar o seu primeiro projeto.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-135">Use the `teamsfx` CLI to create your first project.</span></span>  <span data-ttu-id="cfd2b-136">Inicie pela pasta onde deseja criar a pasta do projeto.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-136">Start from the folder where you want to create the project folder.</span></span>

``` bash
teamsfx new
```

<span data-ttu-id="cfd2b-137">A CLI lhe guiará através de algumas perguntas para criar o projeto.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-137">The CLI walks through some questions to create the project.</span></span>  <span data-ttu-id="cfd2b-138">Cada pergunta lhe dirá como respondê-la (por exemplo, usar as teclas de seta para selecionar uma opção).</span><span class="sxs-lookup"><span data-stu-id="cfd2b-138">Each question will tell you how to answer it (for example, to use arrow keys to select an option).</span></span>  <span data-ttu-id="cfd2b-139">Depois de responder à pergunta, confirme sua escolha pressionando **Inserir**.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-139">When you have answered the question, confirm your choice by pressing **Enter**.</span></span>

1. <span data-ttu-id="cfd2b-140">Selecione **Criar um novo aplicativo do Teams**.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-140">Select **Create a new Teams app**.</span></span>
1. <span data-ttu-id="cfd2b-141">Selecione o **de Extensão de** mensagem e desmarque o **guia** recurso.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-141">Select the **Message Extension** capability and deselect the **Tab** capability.</span></span>
1. <span data-ttu-id="cfd2b-142">Selecione **Criar um novo registro de bot**.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-142">Select **Create a new bot registration**.</span></span>
1. <span data-ttu-id="cfd2b-143">Selecione **JavaScript** como linguagem de programação.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-143">Select **JavaScript** as the programming language.</span></span>
1. <span data-ttu-id="cfd2b-144">Pressione **Inserir** para selecionar a pasta padrão do espaço de trabalho.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-144">Press **Enter** to select the default workspace folder.</span></span>
1. <span data-ttu-id="cfd2b-145">Insira um nome adequado para seu aplicativo, como `helloworld`.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-145">Enter a suitable name for your app, like `helloworld`.</span></span>  <span data-ttu-id="cfd2b-146">O nome do aplicativo deve consistir apenas de caracteres alfanuméricos.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-146">The name of the app must consist only of alphanumeric characters.</span></span>

<span data-ttu-id="cfd2b-147">Assim que todas as perguntas forem respondidas, o seu projeto será criado.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-147">Once all the questions have been answered, your project will be created.</span></span>

---

## <a name="take-a-tour-of-the-source-code"></a><span data-ttu-id="cfd2b-148">Faça um tour pelo código-fonte</span><span class="sxs-lookup"><span data-stu-id="cfd2b-148">Take a tour of the source code</span></span>

<span data-ttu-id="cfd2b-149">Se desejar pular esta seção por enquanto, você pode [executar seu aplicativo localmente](#run-your-app-locally).</span><span class="sxs-lookup"><span data-stu-id="cfd2b-149">If you wish to skip this section for now, you can [run your app locally](#run-your-app-locally).</span></span>

<span data-ttu-id="cfd2b-150">Uma extensão de mensagem usa o [Bot Framework](https://docs.botframework.com) para permitir que o usuário interaja com o seu serviço por meio de uma conversa.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-150">A messaging extension uses the [Bot Framework](https://docs.botframework.com) to allow the user to interact with your service via a conversation.</span></span>  <span data-ttu-id="cfd2b-151">Após o andaime, o seu projeto ficará assim:</span><span class="sxs-lookup"><span data-stu-id="cfd2b-151">After scaffolding, your project will look like this:</span></span>

:::image type="content" source="../assets/images/teams-toolkit-v2/msgextn-file-layout.png" alt-text="Layout de arquivo de um projeto de bot.":::

<span data-ttu-id="cfd2b-153">O código do bot é armazenado no diretório `bot`.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-153">The bot code is stored in the `bot` directory.</span></span>  <span data-ttu-id="cfd2b-154">O `bots/messageExtensionBot.js` é o ponto de entrada principal da extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-154">The `bots/messageExtensionBot.js` is the main entry point for the messaging extension.</span></span>

> [!Tip]
> <span data-ttu-id="cfd2b-155">Familiarize-se com bots fora do Teams antes de integrar seu primeiro bot no Teams.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-155">Familiarize yourself with bots outside of Teams before you integrate your first bot within Teams.</span></span>  <span data-ttu-id="cfd2b-156">Você pode localizar mais informações sobre os bots analisando os tutoriais do [Serviço de Bot do Azure](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="cfd2b-156">You can find more information about bots by reviewing the [Azure Bot Service](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true) tutorials.</span></span>

## <a name="run-your-app-locally"></a><span data-ttu-id="cfd2b-157">Executar o seu aplicativo localmente</span><span class="sxs-lookup"><span data-stu-id="cfd2b-157">Run your app locally</span></span>

<span data-ttu-id="cfd2b-158">O Kit de ferramentas do Teams permite hospedar o seu aplicativo localmente.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-158">Teams Toolkit allows you to host your app locally.</span></span>  <span data-ttu-id="cfd2b-159">Para fazer isso:</span><span class="sxs-lookup"><span data-stu-id="cfd2b-159">To do this:</span></span>

- <span data-ttu-id="cfd2b-160">Um Aplicativo Azure Active Directory é registrado no locatário do M365.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-160">An Azure Active Directory Application is registered within the M365 tenant.</span></span>
- <span data-ttu-id="cfd2b-161">Um manifesto do aplicativo é enviado ao Portal do Desenvolvedor para o Teams.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-161">An app manifest is submitted to the Developer Portal for Teams.</span></span>
- <span data-ttu-id="cfd2b-162">Uma API é executada localmente usando as Ferramentas Principais de Funções do Azure para dar suporte ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-162">An API is run locally using Azure Functions Core Tools to support your app.</span></span>
- <span data-ttu-id="cfd2b-163">[ngrok](https://ngrok.io) é instalado e usado para fornecer um túnel entre o Teams e sua extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-163">[ngrok](https://ngrok.io) is installed and used to provide a tunnel between Teams and your messaging extension.</span></span>

<span data-ttu-id="cfd2b-164">Para criar e executar o aplicativo localmente:</span><span class="sxs-lookup"><span data-stu-id="cfd2b-164">To build and run your app locally:</span></span>

1. <span data-ttu-id="cfd2b-165">No Visual Studio Code, pressione **F5** para executar seu aplicativo no modo de depuração.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-165">From Visual Studio Code, press **F5** to run your application in debug mode.</span></span>

   > <span data-ttu-id="cfd2b-166">Quando você executa o aplicativo pela primeira vez, todas as dependências são baixadas e o aplicativo é compilado.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-166">When you run the app for the first time, all dependencies are downloaded and the app is built.</span></span>  <span data-ttu-id="cfd2b-167">Uma janela do navegador é aberta automaticamente quando a compilação é concluída.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-167">A browser window automatically opens when the build is complete.</span></span>  <span data-ttu-id="cfd2b-168">Isso pode levar de 3 a 5 minutos para ser concluído.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-168">This can take 3-5 minutes to complete.</span></span>

1. <span data-ttu-id="cfd2b-169">O Teams é carregado em um navegador da Web e você será solicitado a entrar.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-169">Teams will be loaded in a web browser, and you will be prompted to sign in.</span></span> <span data-ttu-id="cfd2b-170">Se for solicitado a abrir o Microsoft Teams, selecione Cancelar para permanecer no navegador.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-170">If prompted to open Microsoft Teams, select Cancel to remain within the browser.</span></span> <span data-ttu-id="cfd2b-171">Entre com sua conta do M365.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-171">Sign in with your M365 account.</span></span>

1. <span data-ttu-id="cfd2b-172">Pressione **Adicionar** para adicionar o aplicativo à sua conta.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-172">Press **Add** to add the app to your account.</span></span>

<span data-ttu-id="cfd2b-173">Depois que o aplicativo for carregado, você será levado diretamente para uma caixa de diálogo de pesquisa:</span><span class="sxs-lookup"><span data-stu-id="cfd2b-173">Once the app is loaded, you will be taken directly to a search dialog:</span></span>

:::image type="content" source="../assets/images/teams-toolkit-v2/msgextn-completed-app.png" alt-text="Sua extensão de mensagens baseada em pesquisa em ação":::

<span data-ttu-id="cfd2b-175">Digite algum texto na caixa de pesquisa e selecione uma das opções.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-175">Type some text in the search box, then select one of the options.</span></span>  <span data-ttu-id="cfd2b-176">Um cartão adaptativo será adicionado à sua caixa de entrada.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-176">An adaptive card will be added to your input box.</span></span>

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="cfd2b-177">Saiba o que acontece quando você executar seu aplicativo localmente no depurador.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-177">Learn what happens when you run your app locally in the debugger.</span></span></summary>

<span data-ttu-id="cfd2b-178">Quando você pressionou F5, o Kit de ferramentas do Teams:</span><span class="sxs-lookup"><span data-stu-id="cfd2b-178">When you pressed F5, the Teams Toolkit:</span></span>

1. <span data-ttu-id="cfd2b-179">Registrou seu aplicativo no Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-179">Registered your application with Azure Active Directory.</span></span>
1. <span data-ttu-id="cfd2b-180">Registrou seu aplicativo para "carregamento lateral" no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-180">Registered your application for "side loading" in Microsoft Teams.</span></span>
1. <span data-ttu-id="cfd2b-181">Iniciou o back-end do aplicativo em execução localmente usando as [Ferramentas do Azure Function Core](/azure/azure-functions/functions-run-local?#start).</span><span class="sxs-lookup"><span data-stu-id="cfd2b-181">Started your application backend running locally using [Azure Function Core Tools](/azure/azure-functions/functions-run-local?#start).</span></span>
1. <span data-ttu-id="cfd2b-182">Iniciou um túnel ngrok para que o Teams possa se comunicar com o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-182">Started an ngrok tunnel so Teams can communicate with your app.</span></span>
1. <span data-ttu-id="cfd2b-183">Iniciou o Microsoft Teams com um comando para instruir o Teams a fazer o sideload do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-183">Started Microsoft Teams with a command to instruct Teams to sideload the application.</span></span>

</details>

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="cfd2b-184">Saiba como solucionar problemas comuns ao executar seu aplicativo localmente.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-184">Learn how to troubleshoot common issues when running your app locally.</span></span></summary>

<span data-ttu-id="cfd2b-185">Para executar com êxito seu aplicativo no Teams, você deve ter uma conta de desenvolvimento do Microsoft 365 que permite o sideload do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-185">To successfully run your app in Teams, you must have a Microsoft 365 development account that allows app sideloading.</span></span> <span data-ttu-id="cfd2b-186">Para obter mais informações sobre abertura de conta, confira [Pré-requisitos](prerequisites.md#enable-sideloading).</span><span class="sxs-lookup"><span data-stu-id="cfd2b-186">For more information on account opening, see [Prerequisites](prerequisites.md#enable-sideloading).</span></span>

> [!TIP]
> <span data-ttu-id="cfd2b-187">Verifique se há problemas antes de fazer o sideload de seu aplicativo, usando a [ferramenta de validação de aplicativo](https://dev.teams.microsoft.com/appvalidation.html), que está incluída no kit de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-187">Check for issues before sideloading your app, using the [app validation tool](https://dev.teams.microsoft.com/appvalidation.html), which is included in the toolkit.</span></span> <span data-ttu-id="cfd2b-188">Corrija os erros para fazer o sideload do aplicativo com êxito.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-188">Fix the errors to successfully sideload the app.</span></span>
</details>

[!INCLUDE [Provision and Deploy your app on Azure](~/includes/get-started/azure-provisioning-instructions.md)]

<!-- markdownlint-disable MD033 -->

<details>
<summary><span data-ttu-id="cfd2b-189">Saber o que acontece quando você implanta o seu aplicativo no Azure</span><span class="sxs-lookup"><span data-stu-id="cfd2b-189">Learn what happens when you deployed your app to Azure</span></span></summary>

<span data-ttu-id="cfd2b-190">Antes da implantação, o aplicativo era executado localmente:</span><span class="sxs-lookup"><span data-stu-id="cfd2b-190">Before deployment, the application has been running locally:</span></span>

1. <span data-ttu-id="cfd2b-191">O back-end é executado usando o _Azure Functions Core Tools_.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-191">The backend runs using _Azure Functions Core Tools_.</span></span>
1. <span data-ttu-id="cfd2b-192">O ponto de extremidade HTTP do aplicativo, onde o Microsoft Teams carrega o aplicativo, é executado localmente.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-192">The application HTTP endpoint, where Microsoft Teams loads the application, runs locally.</span></span>

<span data-ttu-id="cfd2b-193">A implantação envolve o provisionamento de recursos em uma assinatura ativa do Azure e a implantação (upload) do código de back-end e front-end do aplicativo para o Azure.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-193">Deployment involves provisioning resources on an active Azure subscription and deploying (uploading) the backend and frontend code for the application to Azure.</span></span> <span data-ttu-id="cfd2b-194">O back-end usa uma variedade de serviços do Azure, incluindo o Serviço de Aplicativo do Azure e o Serviço de Bot do Azure.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-194">The backend uses a variety of Azure services, including Azure App Service and Azure Bot Service.</span></span>

</details>

## <a name="add-a-configuration-page-to-your-messaging-extension"></a><span data-ttu-id="cfd2b-195">Adicionar uma página de configuração à extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="cfd2b-195">Add a configuration page to your messaging extension</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

## <a name="code-sample"></a><span data-ttu-id="cfd2b-196">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="cfd2b-196">Code sample</span></span>

<span data-ttu-id="cfd2b-197">O Teams Config do Auth de Pesquisa para projetos de exemplo no GitHub, demonstre como criar extensões de mensagens que incluem uma página de configuração e a autenticação [do Serviço bot.](https://github.com/microsoft/BotBuilder-Samples#teams-samples)</span><span class="sxs-lookup"><span data-stu-id="cfd2b-197">The Teams Search Auth Config for sample projects on GitHub, demonstrate how to create messaging extensions that include a configuration page and [Bot Service authentication](https://github.com/microsoft/BotBuilder-Samples#teams-samples).</span></span> <span data-ttu-id="cfd2b-198">Os exemplos também demonstram como criar extensões de mensagem que aceitam solicitações de pesquisa e retornam os resultados depois que o usuário se inscreveu.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-198">The samples also demonstrate how to create message extensions that accept search requests and return the results after the user has signed in.</span></span>

| <span data-ttu-id="cfd2b-199">**Exemplo de nome**</span><span class="sxs-lookup"><span data-stu-id="cfd2b-199">**Sample name**</span></span> | <span data-ttu-id="cfd2b-200">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="cfd2b-200">**Description**</span></span> | <span data-ttu-id="cfd2b-201">**.NET**</span><span class="sxs-lookup"><span data-stu-id="cfd2b-201">**.NET**</span></span> | <span data-ttu-id="cfd2b-202">**Node.js**</span><span class="sxs-lookup"><span data-stu-id="cfd2b-202">**Node.js**</span></span> | <span data-ttu-id="cfd2b-203">**Python**</span><span class="sxs-lookup"><span data-stu-id="cfd2b-203">**Python**</span></span> |
|-----------------|-----------------|-------------|--------------|--------|
| <span data-ttu-id="cfd2b-204">Construtor de bots</span><span class="sxs-lookup"><span data-stu-id="cfd2b-204">Bot builder</span></span> | <span data-ttu-id="cfd2b-205">Para criar extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-205">To create messaging extensions.</span></span> | [<span data-ttu-id="cfd2b-206">View</span><span class="sxs-lookup"><span data-stu-id="cfd2b-206">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config) | [<span data-ttu-id="cfd2b-207">View</span><span class="sxs-lookup"><span data-stu-id="cfd2b-207">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/52.teams-messaging-extensions-search-auth-config) | [<span data-ttu-id="cfd2b-208">View</span><span class="sxs-lookup"><span data-stu-id="cfd2b-208">View</span></span>]( https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/50.teams-messaging-extension-search) |

## <a name="additional-code-sample"></a><span data-ttu-id="cfd2b-209">Exemplo de código adicional</span><span class="sxs-lookup"><span data-stu-id="cfd2b-209">Additional code sample</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cfd2b-210">Exibir mais Exemplos de Estrutura de Bots em GitHub</span><span class="sxs-lookup"><span data-stu-id="cfd2b-210">View more Bot Framework Samples on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-samples#messaging-extensions-samples-using-the-v4-sdk)

## <a name="see-also"></a><span data-ttu-id="cfd2b-211">Confira também</span><span class="sxs-lookup"><span data-stu-id="cfd2b-211">See also</span></span>

- [<span data-ttu-id="cfd2b-212">Criar um aplicativo do Teams com o React</span><span class="sxs-lookup"><span data-stu-id="cfd2b-212">Create a Teams app with React</span></span>](first-app-react.md)
- [<span data-ttu-id="cfd2b-213">Criar um aplicativo do Teams com o Blazor</span><span class="sxs-lookup"><span data-stu-id="cfd2b-213">Create a Teams app with Blazor</span></span>](first-app-blazor.md)
- <span data-ttu-id="cfd2b-214">[Criar um aplicativo do Teams como uma Web Part do Microsoft Office SharePoint Online](first-app-spfx.md) (Azure não necessário)</span><span class="sxs-lookup"><span data-stu-id="cfd2b-214">[Create a Teams app as a SharePoint Web Part](first-app-spfx.md) (Azure not required)</span></span>
- [<span data-ttu-id="cfd2b-215">Criar um bot de conversa</span><span class="sxs-lookup"><span data-stu-id="cfd2b-215">Create a conversation bot</span></span>](first-app-bot.md)
