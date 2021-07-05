---
title: 'Introdução: Crie sua primeira extensão de mensagens'
author: adrianhall
description: Crie uma extensão de mensagens para o Microsoft Teams usando o Kit de Ferramentas do Teams.
ms.author: adhal
ms.date: 05/20/2021
ms.topic: quickstart
ms.openlocfilehash: 3566bc55c9995a8407b1344fbdb7d1548e210046
ms.sourcegitcommit: 9d63611974ba8a7e7f19ceea35e50189a2e90434
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2021
ms.locfileid: "53254283"
---
# <a name="build-and-run-your-first-messaging-extension-for-microsoft-teams"></a><span data-ttu-id="dc9ad-103">Crie e execute sua primeira extensão de mensagens para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="dc9ad-103">Build and run your first messaging extension for Microsoft Teams</span></span>

<span data-ttu-id="dc9ad-104">Neste tutorial, você aprenderá *a* criar um comando de pesquisa para pesquisar dados externos e inserir os resultados em uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-104">In this tutorial, you will learn how to create a *search command* to search for external data and insert the results into a message.</span></span> 

<span data-ttu-id="dc9ad-105">Há dois tipos de **extensões de mensagens** do Teams:</span><span class="sxs-lookup"><span data-stu-id="dc9ad-105">There are two types of Teams **messaging extensions**:</span></span>

- <span data-ttu-id="dc9ad-106">[Comandos de pesquisa](../messaging-extensions/how-to/search-commands/define-search-command.md) permitem pesquisar sistemas externos e inserir os resultados dessa pesquisa em uma mensagem em forma de cartão.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-106">[Search commands](../messaging-extensions/how-to/search-commands/define-search-command.md) allow you to search external systems and insert the results of that search into a message in the form of a card.</span></span>
- <span data-ttu-id="dc9ad-107">[Comandos de ação](../messaging-extensions/how-to/action-commands/define-action-command.md) permitem que você apresente aos usuários um pop-up modal para coletar ou exibir informações e, em seguida, processar sua interação e enviar informações de volta para o Teams.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-107">[Action commands](../messaging-extensions/how-to/action-commands/define-action-command.md) allow you present your users with a modal popup to collect or display information, then process their interaction and send information back to Teams.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="dc9ad-108">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="dc9ad-108">Before you begin</span></span>

<span data-ttu-id="dc9ad-109">Certifique-se de que seu ambiente de desenvolvimento está definido instalando os Pré-requisitos.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-109">Make sure your development environment is set up by installing the Prerequisites.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dc9ad-110">Instalar Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="dc9ad-110">Install Prerequisites</span></span>](prerequisites.md)

## <a name="create-your-project"></a><span data-ttu-id="dc9ad-111">Criar o seu projeto</span><span class="sxs-lookup"><span data-stu-id="dc9ad-111">Create your project</span></span>

<span data-ttu-id="dc9ad-112">Use o Kit de ferramentas do Teams para criar o seu primeiro projeto:</span><span class="sxs-lookup"><span data-stu-id="dc9ad-112">Use the Teams Toolkit to create your first project:</span></span>

# <a name="visual-studio-code"></a>[<span data-ttu-id="dc9ad-113">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="dc9ad-113">Visual Studio Code</span></span>](#tab/vscode)

1. <span data-ttu-id="dc9ad-114">Abra o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-114">Open Visual Studio Code.</span></span>
1. <span data-ttu-id="dc9ad-115">Selecione o Teams na barra lateral para abrir o Teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-115">Select the Teams icon in the sidebar to open the Teams Toolkit.</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="O ícone do Teams na barra lateral do Visual Studio Code":::

1. <span data-ttu-id="dc9ad-117">Selecione **Criar Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-117">Select **Create New Project**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project.png" alt-text="Localização do link de Criação de Novo Projeto na barra lateral do Kit de ferramentas do Teams.":::

1. <span data-ttu-id="dc9ad-119">Selecione **Criar um novo aplicativo do Teams**.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-119">Select **Create a new Teams app**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-new-project-intro.png" alt-text="Início do assistente para Criar Novo Projeto":::

1. <span data-ttu-id="dc9ad-121">Na seção **Selecionar recursos,** selecione **Extensão de Mensagem**, desmarque **Tab** e selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-121">In the **Select capabilities** section, select **Message Extension**, deselect **Tab** and select **OK**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/msgextn-create-project-capabilities.png" alt-text="Captura de tela mostrando como adicionar capacidades ao seu novo aplicativo.":::

1. <span data-ttu-id="dc9ad-123">Na seção **Registro bot,** selecione **Criar um novo registro de bot**.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-123">In the **Bot registration** section, select **Create a new bot registration**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-bot-registration.png" alt-text="Selecione criar um novo registro de bot":::

   > [!NOTE]
   > <span data-ttu-id="dc9ad-125">As extensões de mensagens dependem dos bots para fornecer uma caixa de diálogo entre o usuário e seu código.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-125">Messaging extensions rely on bots to provide a dialog between the user and your code.</span></span>

1. <span data-ttu-id="dc9ad-126">Na seção **Linguagem de Programação,** selecione **JavaScript**.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-126">In the **Programming Language** section, select **JavaScript**.</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-programming-languages.png" alt-text="Captura de tela mostrando como selecionar a linguagem de programação.":::

1. <span data-ttu-id="dc9ad-128">Selecione uma pasta do espaço de trabalho.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-128">Select a workspace folder.</span></span>  <span data-ttu-id="dc9ad-129">Uma pasta será criada dentro de sua pasta do espaço de trabalho para o projeto que você está criando.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-129">A folder will be created within your workspace folder for the project you are creating.</span></span>

1. <span data-ttu-id="dc9ad-130">Insira um nome adequado para seu aplicativo, como `helloworld`.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-130">Enter a suitable name for your app, like `helloworld`.</span></span>  <span data-ttu-id="dc9ad-131">O nome do aplicativo deve consistir apenas de caracteres alfanuméricos.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-131">The name of the app must consist only of alphanumeric characters.</span></span>  <span data-ttu-id="dc9ad-132">Pressione **Inserir** para continuar.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-132">Press **Enter** to continue.</span></span>

   <span data-ttu-id="dc9ad-133">O seu aplicativo do Teams será criado em alguns segundos.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-133">Your Teams app will be created within a few seconds.</span></span>

# <a name="command-line"></a>[<span data-ttu-id="dc9ad-134">Linha de comando</span><span class="sxs-lookup"><span data-stu-id="dc9ad-134">Command line</span></span>](#tab/cli)

<span data-ttu-id="dc9ad-135">Use a CLI `teamsfx` para criar o seu primeiro projeto.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-135">Use the `teamsfx` CLI to create your first project.</span></span>  <span data-ttu-id="dc9ad-136">Inicie pela pasta onde deseja criar a pasta do projeto.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-136">Start from the folder where you want to create the project folder.</span></span>

``` bash
teamsfx new
```

<span data-ttu-id="dc9ad-137">A CLI lhe guiará através de algumas perguntas para criar o projeto.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-137">The CLI walks through some questions to create the project.</span></span>  <span data-ttu-id="dc9ad-138">Cada pergunta lhe dirá como respondê-la (por exemplo, usar as teclas de seta para selecionar uma opção).</span><span class="sxs-lookup"><span data-stu-id="dc9ad-138">Each question will tell you how to answer it (for example, to use arrow keys to select an option).</span></span>  <span data-ttu-id="dc9ad-139">Depois de responder à pergunta, confirme sua escolha pressionando **Inserir**.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-139">When you have answered the question, confirm your choice by pressing **Enter**.</span></span>

1. <span data-ttu-id="dc9ad-140">Selecione **Criar um novo aplicativo do Teams**.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-140">Select **Create a new Teams app**.</span></span>
1. <span data-ttu-id="dc9ad-141">Selecione a **Extensão da Mensagem** e desmarque a **Guia**.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-141">Select the **Message Extension** and deselect **Tab**.</span></span>
1. <span data-ttu-id="dc9ad-142">Selecione **Criar um novo registro de bot**.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-142">Select **Create a new bot registration**.</span></span>
1. <span data-ttu-id="dc9ad-143">Selecione **JavaScript** como linguagem de programação.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-143">Select **JavaScript** as the programming language.</span></span>
1. <span data-ttu-id="dc9ad-144">Pressione **Inserir** para selecionar a pasta padrão do espaço de trabalho.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-144">Press **Enter** to select the default workspace folder.</span></span>
1. <span data-ttu-id="dc9ad-145">Insira um nome adequado para seu aplicativo, como `helloworld`.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-145">Enter a suitable name for your app, like `helloworld`.</span></span>  <span data-ttu-id="dc9ad-146">O nome do aplicativo deve consistir apenas de caracteres alfanuméricos.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-146">The name of the app must consist only of alphanumeric characters.</span></span>

   <span data-ttu-id="dc9ad-147">Depois que todas as perguntas foram respondidas, seu projeto é criado.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-147">After all the questions have been answered, your project is created.</span></span>

---

## <a name="take-a-tour-of-the-source-code"></a><span data-ttu-id="dc9ad-148">Faça um tour pelo código-fonte</span><span class="sxs-lookup"><span data-stu-id="dc9ad-148">Take a tour of the source code</span></span>

<span data-ttu-id="dc9ad-149">Se desejar pular esta seção por enquanto, você pode [executar seu aplicativo localmente](#run-your-app-locally).</span><span class="sxs-lookup"><span data-stu-id="dc9ad-149">If you wish to skip this section for now, you can [run your app locally](#run-your-app-locally).</span></span>

<span data-ttu-id="dc9ad-150">Uma extensão de mensagem usa o [Bot Framework](https://docs.botframework.com) para permitir que o usuário interaja com o seu serviço por meio de uma conversa.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-150">A messaging extension uses the [Bot Framework](https://docs.botframework.com) to allow the user to interact with your service via a conversation.</span></span>  <span data-ttu-id="dc9ad-151">Após o andaime, o seu projeto ficará assim:</span><span class="sxs-lookup"><span data-stu-id="dc9ad-151">After scaffolding, your project will look like this:</span></span>

:::image type="content" source="../assets/images/teams-toolkit-v2/msgextn-file-layout.png" alt-text="Layout de arquivo de um projeto de bot.":::

<span data-ttu-id="dc9ad-153">O código do bot é armazenado no diretório `bot`.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-153">The bot code is stored in the `bot` directory.</span></span>  <span data-ttu-id="dc9ad-154">O `bot/messageExtensionBot.js` é o ponto de entrada principal da extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-154">The `bot/messageExtensionBot.js` is the main entry point for the messaging extension.</span></span>

> [!Tip]
> <span data-ttu-id="dc9ad-155">Familiarize-se com bots fora do Teams antes de integrar seu primeiro bot no Teams.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-155">Familiarize yourself with bots outside of Teams before you integrate your first bot within Teams.</span></span>  <span data-ttu-id="dc9ad-156">Você pode localizar mais informações sobre os bots analisando os tutoriais do [Serviço de Bot do Azure](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="dc9ad-156">You can find more information about bots by reviewing the [Azure Bot Service](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true) tutorials.</span></span>

## <a name="run-your-app-locally"></a><span data-ttu-id="dc9ad-157">Executar o seu aplicativo localmente</span><span class="sxs-lookup"><span data-stu-id="dc9ad-157">Run your app locally</span></span>

<span data-ttu-id="dc9ad-158">O Kit de ferramentas do Teams permite hospedar o seu aplicativo localmente.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-158">Teams Toolkit allows you to host your app locally.</span></span>  <span data-ttu-id="dc9ad-159">Para fazer isso:</span><span class="sxs-lookup"><span data-stu-id="dc9ad-159">To do this:</span></span>

- <span data-ttu-id="dc9ad-160">Um Aplicativo Azure Active Directory é registrado no locatário do M365.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-160">An Azure Active Directory Application is registered within the M365 tenant.</span></span>
- <span data-ttu-id="dc9ad-161">Um manifesto do aplicativo é enviado ao Portal do Desenvolvedor para o Teams.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-161">An app manifest is submitted to the Developer Portal for Teams.</span></span>
- <span data-ttu-id="dc9ad-162">Uma API é executada localmente usando as Ferramentas Principais de Funções do Azure para dar suporte ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-162">An API is run locally using Azure Functions Core Tools to support your app.</span></span>
- <span data-ttu-id="dc9ad-163">[ngrok](https://ngrok.io) é instalado e usado para fornecer um túnel entre o Teams e sua extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-163">[ngrok](https://ngrok.io) is installed and used to provide a tunnel between Teams and your messaging extension.</span></span>

<span data-ttu-id="dc9ad-164">Para criar e executar o aplicativo localmente:</span><span class="sxs-lookup"><span data-stu-id="dc9ad-164">To build and run your app locally:</span></span>

1. <span data-ttu-id="dc9ad-165">Na Visual Studio Code, pressione a **tecla F5** para executar seu aplicativo no modo de depuração.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-165">From Visual Studio Code, press the **F5** key to run your application in debug mode.</span></span>

   > <span data-ttu-id="dc9ad-166">Quando você executa o aplicativo pela primeira vez, todas as dependências são baixadas e o aplicativo é compilado.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-166">When you run the app for the first time, all dependencies are downloaded and the app is built.</span></span>  <span data-ttu-id="dc9ad-167">Uma janela do navegador é aberta automaticamente quando a compilação é concluída.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-167">A browser window automatically opens when the build is complete.</span></span>  <span data-ttu-id="dc9ad-168">Isso pode levar de 3 a 5 minutos para ser concluído.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-168">This can take 3-5 minutes to complete.</span></span>

1. <span data-ttu-id="dc9ad-169">O Teams é carregado em um navegador da Web e você será solicitado a entrar.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-169">Teams will be loaded in a web browser, and you will be prompted to sign in.</span></span> <span data-ttu-id="dc9ad-170">Se for solicitado a abrir o Microsoft Teams, selecione Cancelar para permanecer no navegador.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-170">If prompted to open Microsoft Teams, select Cancel to remain within the browser.</span></span> <span data-ttu-id="dc9ad-171">Entre com sua conta do M365.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-171">Sign in with your M365 account.</span></span>

1. <span data-ttu-id="dc9ad-172">Selecione **Adicionar** para adicionar o aplicativo à sua conta.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-172">Select **Add** to add the app to your account.</span></span>

   <span data-ttu-id="dc9ad-173">Depois que o aplicativo for carregado, você será levado diretamente para uma caixa de diálogo de pesquisa:</span><span class="sxs-lookup"><span data-stu-id="dc9ad-173">After the app is loaded, you will be taken directly to a search dialog:</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/msgextn-completed-app.png" alt-text="Sua extensão de mensagens baseada em pesquisa em ação":::

   <span data-ttu-id="dc9ad-175">Digite algum texto na caixa de pesquisa e selecione uma das opções.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-175">Type some text in the search box, then select one of the options.</span></span>  <span data-ttu-id="dc9ad-176">Um cartão adaptativo será adicionado à sua caixa de entrada.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-176">An adaptive card will be added to your input box.</span></span>

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="dc9ad-177">Saiba o que acontece quando você executar seu aplicativo localmente no depurador.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-177">Learn what happens when you run your app locally in the debugger.</span></span></summary>

<span data-ttu-id="dc9ad-178">Quando você pressiona a **tecla F5,** o Teams Toolkit:</span><span class="sxs-lookup"><span data-stu-id="dc9ad-178">When you press the **F5** key, the Teams Toolkit:</span></span>

1. <span data-ttu-id="dc9ad-179">Registra seu aplicativo com Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-179">Registers your application with Azure Active Directory.</span></span>
1. <span data-ttu-id="dc9ad-180">Registra seu aplicativo para "side loading" no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-180">Registers your application for "side loading" in Microsoft Teams.</span></span>
1. <span data-ttu-id="dc9ad-181">Inicia o back-end do aplicativo em execução localmente usando as Ferramentas Principais da [Função do Azure.](/azure/azure-functions/functions-run-local?#start)</span><span class="sxs-lookup"><span data-stu-id="dc9ad-181">Starts your application backend running locally using [Azure Function Core Tools](/azure/azure-functions/functions-run-local?#start).</span></span>
1. <span data-ttu-id="dc9ad-182">Inicia um túnel ngrok para que Teams possa se comunicar com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-182">Starts an ngrok tunnel so Teams can communicate with your app.</span></span>
1. <span data-ttu-id="dc9ad-183">Inicia Microsoft Teams com um comando para instruir Teams fazer sideload do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-183">Starts Microsoft Teams with a command to instruct Teams to sideload the application.</span></span>

</details>

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="dc9ad-184">Saiba como solucionar problemas comuns ao executar seu aplicativo localmente.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-184">Learn how to troubleshoot common issues when running your app locally.</span></span></summary>

<span data-ttu-id="dc9ad-185">Para executar com êxito seu aplicativo no Teams, você deve ter uma conta de desenvolvimento do Microsoft 365 que permite o sideload do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-185">To successfully run your app in Teams, you must have a Microsoft 365 development account that allows app sideloading.</span></span> <span data-ttu-id="dc9ad-186">Para obter mais informações sobre abertura de conta, confira [Pré-requisitos](prerequisites.md#enable-sideloading).</span><span class="sxs-lookup"><span data-stu-id="dc9ad-186">For more information on account opening, see [Prerequisites](prerequisites.md#enable-sideloading).</span></span>

> [!TIP]
> <span data-ttu-id="dc9ad-187">Verifique se há problemas antes de fazer o sideload de seu aplicativo, usando a [ferramenta de validação de aplicativo](https://dev.teams.microsoft.com/appvalidation.html), que está incluída no kit de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-187">Check for issues before sideloading your app, using the [app validation tool](https://dev.teams.microsoft.com/appvalidation.html), which is included in the toolkit.</span></span> <span data-ttu-id="dc9ad-188">Corrija os erros para fazer o sideload do aplicativo com êxito.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-188">Fix the errors to successfully sideload the app.</span></span>
</details>

[!INCLUDE [Provision and Deploy your app on Azure](~/includes/get-started/azure-provisioning-instructions.md)]

<!-- markdownlint-disable MD033 -->

<details>
<summary><span data-ttu-id="dc9ad-189">Saber o que acontece quando você implanta o seu aplicativo no Azure</span><span class="sxs-lookup"><span data-stu-id="dc9ad-189">Learn what happens when you deployed your app to Azure</span></span></summary>

<span data-ttu-id="dc9ad-190">Antes da implantação, o aplicativo era executado localmente:</span><span class="sxs-lookup"><span data-stu-id="dc9ad-190">Before deployment, the application has been running locally:</span></span>

1. <span data-ttu-id="dc9ad-191">O back-end é executado usando o _Azure Functions Core Tools_.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-191">The backend runs using _Azure Functions Core Tools_.</span></span>
1. <span data-ttu-id="dc9ad-192">O ponto de extremidade HTTP do aplicativo, onde o Microsoft Teams carrega o aplicativo, é executado localmente.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-192">The application HTTP endpoint, where Microsoft Teams loads the application, runs locally.</span></span>

<span data-ttu-id="dc9ad-193">A implantação envolve o provisionamento de recursos em uma assinatura ativa do Azure e a implantação (upload) do código de back-end e front-end do aplicativo para o Azure.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-193">Deployment involves provisioning resources on an active Azure subscription and deploying (uploading) the backend and frontend code for the application to Azure.</span></span> <span data-ttu-id="dc9ad-194">O back-end usa uma variedade de serviços do Azure, incluindo o Serviço de Aplicativo do Azure e o Serviço de Bot do Azure.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-194">The backend uses a variety of Azure services, including Azure App Service and Azure Bot Service.</span></span>

</details>

## <a name="add-a-configuration-page-to-your-messaging-extension"></a><span data-ttu-id="dc9ad-195">Adicionar uma página de configuração à extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="dc9ad-195">Add a configuration page to your messaging extension</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

## <a name="code-sample"></a><span data-ttu-id="dc9ad-196">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="dc9ad-196">Code sample</span></span>

<span data-ttu-id="dc9ad-197">O Teams Config do Auth de Pesquisa para projetos de exemplo no GitHub, demonstre como criar extensões de mensagens que incluem uma página de configuração e a autenticação [do Serviço bot.](https://github.com/microsoft/BotBuilder-Samples#teams-samples)</span><span class="sxs-lookup"><span data-stu-id="dc9ad-197">The Teams Search Auth Config for sample projects on GitHub, demonstrate how to create messaging extensions that include a configuration page and [Bot Service authentication](https://github.com/microsoft/BotBuilder-Samples#teams-samples).</span></span> <span data-ttu-id="dc9ad-198">Os exemplos também demonstram como criar extensões de mensagem que aceitam solicitações de pesquisa e retornam os resultados depois que o usuário se inscreveu.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-198">The samples also demonstrate how to create message extensions that accept search requests and return the results after the user has signed in.</span></span>

| <span data-ttu-id="dc9ad-199">**Exemplo de nome**</span><span class="sxs-lookup"><span data-stu-id="dc9ad-199">**Sample name**</span></span> | <span data-ttu-id="dc9ad-200">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="dc9ad-200">**Description**</span></span> | <span data-ttu-id="dc9ad-201">**.NET**</span><span class="sxs-lookup"><span data-stu-id="dc9ad-201">**.NET**</span></span> | <span data-ttu-id="dc9ad-202">**Node.js**</span><span class="sxs-lookup"><span data-stu-id="dc9ad-202">**Node.js**</span></span> | <span data-ttu-id="dc9ad-203">**Python**</span><span class="sxs-lookup"><span data-stu-id="dc9ad-203">**Python**</span></span> |
|-----------------|-----------------|-------------|--------------|--------|
| <span data-ttu-id="dc9ad-204">Construtor de bots</span><span class="sxs-lookup"><span data-stu-id="dc9ad-204">Bot builder</span></span> | <span data-ttu-id="dc9ad-205">Para criar extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="dc9ad-205">To create messaging extensions.</span></span> | [<span data-ttu-id="dc9ad-206">View</span><span class="sxs-lookup"><span data-stu-id="dc9ad-206">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config) | [<span data-ttu-id="dc9ad-207">View</span><span class="sxs-lookup"><span data-stu-id="dc9ad-207">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/52.teams-messaging-extensions-search-auth-config) | [<span data-ttu-id="dc9ad-208">View</span><span class="sxs-lookup"><span data-stu-id="dc9ad-208">View</span></span>]( https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/50.teams-messaging-extension-search) |

## <a name="additional-code-sample"></a><span data-ttu-id="dc9ad-209">Exemplo de código adicional</span><span class="sxs-lookup"><span data-stu-id="dc9ad-209">Additional code sample</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dc9ad-210">Exibir mais Exemplos de Estrutura de Bots em GitHub</span><span class="sxs-lookup"><span data-stu-id="dc9ad-210">View more Bot Framework Samples on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-samples#messaging-extensions-samples-using-the-v4-sdk)

## <a name="see-also"></a><span data-ttu-id="dc9ad-211">Confira também</span><span class="sxs-lookup"><span data-stu-id="dc9ad-211">See also</span></span>

* [<span data-ttu-id="dc9ad-212">Visão geral dos tutoriais</span><span class="sxs-lookup"><span data-stu-id="dc9ad-212">Tutorials Overview</span></span>](code-samples.md) 
* [<span data-ttu-id="dc9ad-213">Criar um aplicativo usando React</span><span class="sxs-lookup"><span data-stu-id="dc9ad-213">Create an app using React</span></span>](first-app-react.md)
* [<span data-ttu-id="dc9ad-214">Criar um aplicativo usando o Blazor</span><span class="sxs-lookup"><span data-stu-id="dc9ad-214">Create an app using Blazor</span></span>](first-app-blazor.md)
* [<span data-ttu-id="dc9ad-215">Criar um aplicativo usando SPFx</span><span class="sxs-lookup"><span data-stu-id="dc9ad-215">Create an app using SPFx</span></span>](first-app-spfx.md)
* [<span data-ttu-id="dc9ad-216">Criar um aplicativo usando C# ou .NET</span><span class="sxs-lookup"><span data-stu-id="dc9ad-216">Create an app using C# or .NET</span></span>](get-started-dotnet-app-studio.md)
* [<span data-ttu-id="dc9ad-217">Criar um aplicativo usando o Node.js</span><span class="sxs-lookup"><span data-stu-id="dc9ad-217">Create an app using Node.js</span></span>](get-started-nodejs-app-studio.md)
* [<span data-ttu-id="dc9ad-218">Criar um aplicativo usando o gerador Yeoman</span><span class="sxs-lookup"><span data-stu-id="dc9ad-218">Create an app using Yeoman generator</span></span>](get-started-yeoman.md)
* [<span data-ttu-id="dc9ad-219">Criar um programa bot de conversação</span><span class="sxs-lookup"><span data-stu-id="dc9ad-219">Create a conversational bot app</span></span>](first-app-bot.md)
* [<span data-ttu-id="dc9ad-220">Exemplos de código</span><span class="sxs-lookup"><span data-stu-id="dc9ad-220">Code Samples</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples)