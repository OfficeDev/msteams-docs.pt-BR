---
title: Introdução - Construa o seu primeiro bot de conversação
author: adrianhall
description: Crie um bot de conversação para o Microsoft Teams usando o Kit de ferramentas do Teams.
ms.author: adhal
ms.date: 05/27/2021
ms.topic: quickstart
ms.openlocfilehash: 96bbddd99b6901a4b92e1e2f2dc98482c755dc66
ms.sourcegitcommit: 9d63611974ba8a7e7f19ceea35e50189a2e90434
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2021
ms.locfileid: "53254248"
---
# <a name="build-your-first-conversational-bot-for-microsoft-teams"></a><span data-ttu-id="beed1-103">Criar o seu primeiro bot de conversação para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="beed1-103">Build your first conversational bot for Microsoft Teams</span></span>

<span data-ttu-id="beed1-104">Neste tutorial, você aprenderá como construir, executar e implantar um aplicativo bot do Teams.</span><span class="sxs-lookup"><span data-stu-id="beed1-104">In this tutorial, you will learn how to build, run, and deploy a Teams bot app.</span></span> <span data-ttu-id="beed1-105">Um bot atua como um intermediário entre um usuário do Teams e um serviço Web.</span><span class="sxs-lookup"><span data-stu-id="beed1-105">A bot acts as an intermediary between a Teams user and a web service.</span></span>  <span data-ttu-id="beed1-106">Os usuários podem bater papo com um bot para obter informações rapidamente, iniciar fluxos de trabalho ou qualquer outra coisa que seu serviço Web possa fazer.</span><span class="sxs-lookup"><span data-stu-id="beed1-106">Users can chat with a bot to quickly get information, initiate workflows, or anything else your web service can do.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="beed1-107">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="beed1-107">Before you begin</span></span>

<span data-ttu-id="beed1-108">Certifique-se de que seu ambiente de desenvolvimento está definido instalando os Pré-requisitos.</span><span class="sxs-lookup"><span data-stu-id="beed1-108">Make sure your development environment is set up by installing the Prerequisites.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="beed1-109">Instalar Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="beed1-109">Install Prerequisites</span></span>](prerequisites.md)

## <a name="create-your-project"></a><span data-ttu-id="beed1-110">Criar o seu projeto</span><span class="sxs-lookup"><span data-stu-id="beed1-110">Create your project</span></span>

<span data-ttu-id="beed1-111">Use o Kit de ferramentas do Teams para criar o seu primeiro projeto:</span><span class="sxs-lookup"><span data-stu-id="beed1-111">Use the Teams Toolkit to create your first project:</span></span>

# <a name="visual-studio-code"></a>[<span data-ttu-id="beed1-112">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="beed1-112">Visual Studio Code</span></span>](#tab/vscode)

1. <span data-ttu-id="beed1-113">Abra o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="beed1-113">Open Visual Studio code.</span></span>
1. <span data-ttu-id="beed1-114">Selecione o Teams na barra lateral para abrir o Teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="beed1-114">Select the Teams icon in the sidebar to open the Teams Toolkit.</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="O ícone do Teams na barra lateral do Visual Studio Code":::

1. <span data-ttu-id="beed1-116">Selecione **Criar Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="beed1-116">Select **Create New Project**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project.png" alt-text="Localização do link de Criação de Novo Projeto na barra lateral do Kit de ferramentas do Teams.":::

1. <span data-ttu-id="beed1-118">Selecione **Criar um novo aplicativo do Teams**.</span><span class="sxs-lookup"><span data-stu-id="beed1-118">Select **Create a new Teams app**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-new-project-intro.png" alt-text="Início do assistente para Criar Novo Projeto":::

1. <span data-ttu-id="beed1-120">Na seção **Selecionar recursos,** selecione **Bot**, desmarque **Tab** e selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="beed1-120">In the **Select capabilities** section, select **Bot**, deselect **Tab** and select **OK**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-capabilities-bot.png" alt-text="Captura de tela mostrando como adicionar capacidades ao seu novo aplicativo.":::

1. <span data-ttu-id="beed1-122">Na seção **Registro bot,** selecione **Criar um novo registro de bot**.</span><span class="sxs-lookup"><span data-stu-id="beed1-122">In the **Bot registration** section, select **Create a new bot registration**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-bot-registration.png" alt-text="Selecione criar um novo registro de bot":::

1. <span data-ttu-id="beed1-124">Na seção **Linguagem de Programação,** selecione **JavaScript**.</span><span class="sxs-lookup"><span data-stu-id="beed1-124">In the **Programming Language** section, select **JavaScript**.</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-programming-languages.png" alt-text="Captura de tela mostrando como selecionar a linguagem de programação.":::

1. <span data-ttu-id="beed1-126">Selecione uma pasta do espaço de trabalho.</span><span class="sxs-lookup"><span data-stu-id="beed1-126">Select a workspace folder.</span></span>  <span data-ttu-id="beed1-127">Uma pasta será criada dentro de sua pasta do espaço de trabalho para o projeto que você está criando.</span><span class="sxs-lookup"><span data-stu-id="beed1-127">A folder will be created within your workspace folder for the project you are creating.</span></span>

1. <span data-ttu-id="beed1-128">Insira um nome adequado para seu aplicativo, como `helloworld`.</span><span class="sxs-lookup"><span data-stu-id="beed1-128">Enter a suitable name for your app, like `helloworld`.</span></span>  <span data-ttu-id="beed1-129">O nome do aplicativo deve conter apenas caracteres alfanuméricos.</span><span class="sxs-lookup"><span data-stu-id="beed1-129">The name of the app must contain only alphanumeric characters.</span></span>  <span data-ttu-id="beed1-130">Pressione **Inserir** para continuar.</span><span class="sxs-lookup"><span data-stu-id="beed1-130">Press **Enter** to continue.</span></span>

<span data-ttu-id="beed1-131">O seu aplicativo do Teams será criado em alguns segundos.</span><span class="sxs-lookup"><span data-stu-id="beed1-131">Your Teams app will be created within a few seconds.</span></span>

# <a name="command-line"></a>[<span data-ttu-id="beed1-132">Linha de comando</span><span class="sxs-lookup"><span data-stu-id="beed1-132">Command line</span></span>](#tab/cli)

<span data-ttu-id="beed1-133">Use a CLI `teamsfx` para criar o seu primeiro projeto.</span><span class="sxs-lookup"><span data-stu-id="beed1-133">Use the `teamsfx` CLI to create your first project.</span></span>  <span data-ttu-id="beed1-134">Inicie pela pasta onde deseja criar a pasta do projeto.</span><span class="sxs-lookup"><span data-stu-id="beed1-134">Start from the folder where you want to create the project folder.</span></span>

``` bash
teamsfx new
```

<span data-ttu-id="beed1-135">A CLI lhe guiará através de algumas perguntas para criar o projeto.</span><span class="sxs-lookup"><span data-stu-id="beed1-135">The CLI walks through some questions to create the project.</span></span>  <span data-ttu-id="beed1-136">Cada pergunta lhe dirá como respondê-la (por exemplo, usar as teclas de seta para selecionar uma opção).</span><span class="sxs-lookup"><span data-stu-id="beed1-136">Each question will tell you how to answer it (for example, to use arrow keys to select an option).</span></span>  <span data-ttu-id="beed1-137">Depois de responder à pergunta, confirme sua escolha pressionando **Inserir**.</span><span class="sxs-lookup"><span data-stu-id="beed1-137">When you have answered the question, confirm your choice by pressing **Enter**.</span></span>

1. <span data-ttu-id="beed1-138">Selecione **Criar um novo aplicativo do Teams**.</span><span class="sxs-lookup"><span data-stu-id="beed1-138">Select **Create a new Teams app**.</span></span>
1. <span data-ttu-id="beed1-139">Selecione **Bot** e desmarque **Tab**.</span><span class="sxs-lookup"><span data-stu-id="beed1-139">Select **Bot** and deselect **Tab**.</span></span>
1. <span data-ttu-id="beed1-140">Selecione **Criar um novo registro de bot**.</span><span class="sxs-lookup"><span data-stu-id="beed1-140">Select **Create a new bot registration**.</span></span>
1. <span data-ttu-id="beed1-141">Selecione **JavaScript** como linguagem de programação.</span><span class="sxs-lookup"><span data-stu-id="beed1-141">Select **JavaScript** as the programming language.</span></span>
1. <span data-ttu-id="beed1-142">Pressione **Inserir** para selecionar a pasta padrão do espaço de trabalho.</span><span class="sxs-lookup"><span data-stu-id="beed1-142">Press **Enter** to select the default workspace folder.</span></span>
1. <span data-ttu-id="beed1-143">Insira um nome adequado para seu aplicativo, como `helloworld`.</span><span class="sxs-lookup"><span data-stu-id="beed1-143">Enter a suitable name for your app, like `helloworld`.</span></span>  <span data-ttu-id="beed1-144">O nome do aplicativo deve consistir apenas de caracteres alfanuméricos.</span><span class="sxs-lookup"><span data-stu-id="beed1-144">The name of the app must consist only of alphanumeric characters.</span></span>

<span data-ttu-id="beed1-145">Depois que todas as perguntas foram respondidas, seu projeto é criado.</span><span class="sxs-lookup"><span data-stu-id="beed1-145">After all the questions have been answered, your project is created.</span></span>

---

## <a name="take-a-tour-of-the-source-code"></a><span data-ttu-id="beed1-146">Faça um tour pelo código-fonte</span><span class="sxs-lookup"><span data-stu-id="beed1-146">Take a tour of the source code</span></span>

<span data-ttu-id="beed1-147">Se desejar pular esta seção por enquanto, você pode [executar seu aplicativo localmente](#run-your-app-locally).</span><span class="sxs-lookup"><span data-stu-id="beed1-147">If you wish to skip this section for now, you can [run your app locally](#run-your-app-locally).</span></span>

<span data-ttu-id="beed1-148">Uma extensão de mensagem usa o [Bot Framework](https://docs.botframework.com) para permitir que o usuário interaja com o seu serviço por meio de uma conversa.</span><span class="sxs-lookup"><span data-stu-id="beed1-148">A messaging extension uses the [Bot Framework](https://docs.botframework.com) to allow the user to interact with your service via a conversation.</span></span>  <span data-ttu-id="beed1-149">Após o andaime, o seu projeto ficará assim:</span><span class="sxs-lookup"><span data-stu-id="beed1-149">After scaffolding, your project will look like this:</span></span>

:::image type="content" source="../assets/images/teams-toolkit-v2/bot-file-layout.png" alt-text="Layout de arquivo de um projeto de bot.":::

<span data-ttu-id="beed1-151">O código do bot é armazenado no diretório `bot`.</span><span class="sxs-lookup"><span data-stu-id="beed1-151">The bot code is stored in the `bot` directory.</span></span>  <span data-ttu-id="beed1-152">O `bot/teamsBot.js` é o principal ponto de entrada para o bot e as caixas de diálogo são armazenadas no diretório `dialogs`.</span><span class="sxs-lookup"><span data-stu-id="beed1-152">The `bot/teamsBot.js` is the main entry point for the bot, and the dialogs are stored in the `dialogs` directory.</span></span>

> [!Tip]
> <span data-ttu-id="beed1-153">Familiarize-se com os bots fora do Teams antes de integrar o seu primeiro bot dentro do Teams.</span><span class="sxs-lookup"><span data-stu-id="beed1-153">Familiarize yourself with bots outside of Teams before you integrate your first bot within Teams.</span></span>  <span data-ttu-id="beed1-154">Você pode localizar mais informações sobre os bots analisando os tutoriais do [Serviço de Bot do Azure](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="beed1-154">You can find more information about bots by reviewing the [Azure Bot Service](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true) tutorials.</span></span>

## <a name="run-your-app-locally"></a><span data-ttu-id="beed1-155">Executar o seu aplicativo localmente</span><span class="sxs-lookup"><span data-stu-id="beed1-155">Run your app locally</span></span>

<span data-ttu-id="beed1-156">O Kit de ferramentas do Teams permite hospedar o seu aplicativo localmente.</span><span class="sxs-lookup"><span data-stu-id="beed1-156">Teams Toolkit allows you to host your app locally.</span></span>  <span data-ttu-id="beed1-157">Para fazer isso:</span><span class="sxs-lookup"><span data-stu-id="beed1-157">To do this:</span></span>

- <span data-ttu-id="beed1-158">Um Aplicativo do Azure Active Directory é registrado no locatário M365.</span><span class="sxs-lookup"><span data-stu-id="beed1-158">An Azure Active Directory Application is registered within the M365 tenant.</span></span>
- <span data-ttu-id="beed1-159">Um manifesto do aplicativo é enviado ao Centro de Desenvolvedor para o Teams.</span><span class="sxs-lookup"><span data-stu-id="beed1-159">An app manifest is submitted to the Developer Center for Teams.</span></span>
- <span data-ttu-id="beed1-160">Uma API é executada localmente usando o Azure Functions Core Tools para oferecer suporte ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="beed1-160">An API is run locally using Azure Functions Core Tools to support your app.</span></span>
- <span data-ttu-id="beed1-161">[ngrok](https://ngrok.io) é instalado e usado para fornecer um túnel entre o Teams e o código do seu bot.</span><span class="sxs-lookup"><span data-stu-id="beed1-161">[ngrok](https://ngrok.io) is installed and used to provide a tunnel between Teams and your bot code.</span></span>

<span data-ttu-id="beed1-162">Para compilar e executar o seu aplicativo localmente:</span><span class="sxs-lookup"><span data-stu-id="beed1-162">To build and run your app locally:</span></span>

1. <span data-ttu-id="beed1-163">Na Visual Studio Code, pressione a **tecla F5** para executar seu aplicativo no modo de depuração.</span><span class="sxs-lookup"><span data-stu-id="beed1-163">From Visual Studio Code, press the **F5** key to run your application in debug mode.</span></span>

   > <span data-ttu-id="beed1-164">Quando você executa o aplicativo pela primeira vez, todas as dependências são baixadas e o aplicativo é compilado.</span><span class="sxs-lookup"><span data-stu-id="beed1-164">When you run the app for the first time, all dependencies are downloaded and the app is built.</span></span>  <span data-ttu-id="beed1-165">Uma janela do navegador é aberta automaticamente quando a compilação é concluída.</span><span class="sxs-lookup"><span data-stu-id="beed1-165">A browser window automatically opens when the build is complete.</span></span>  <span data-ttu-id="beed1-166">Isto pode levar de 3 a 5 minutos para ser concluído.</span><span class="sxs-lookup"><span data-stu-id="beed1-166">This can take 3-5 minutes to complete.</span></span>

1. <span data-ttu-id="beed1-167">O navegador da Web começa a executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="beed1-167">Your web browser starts to run the app.</span></span> <span data-ttu-id="beed1-168">Se for solicitado a abrir Teams área de trabalho, selecione **Cancelar** para permanecer no navegador.</span><span class="sxs-lookup"><span data-stu-id="beed1-168">If prompted to open Teams desktop, select **Cancel** to remain in the browser.</span></span> <span data-ttu-id="beed1-169">Você também pode ser solicitado a alternar para a área de trabalho Teams outras vezes; selecione o Teams web quando isso acontecer.</span><span class="sxs-lookup"><span data-stu-id="beed1-169">You may also be prompted to switch to Teams desktop at other times; select the Teams web app when this happens.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/launch-web-browser-and-pick-webapp.png" alt-text="Captura de tela mostrando como escolher a versão da web das equipes quando lançadas":::

1. <span data-ttu-id="beed1-171">Você pode ser solicitado a entrar.</span><span class="sxs-lookup"><span data-stu-id="beed1-171">You may be prompted to sign in.</span></span>  <span data-ttu-id="beed1-172">Em caso afirmativo, entre com sua conta M365.</span><span class="sxs-lookup"><span data-stu-id="beed1-172">If so, sign in with your M365 account.</span></span>
1. <span data-ttu-id="beed1-173">Quando solicitado a instalar o aplicativo no Teams, selecione **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="beed1-173">When prompted to install the app onto Teams, select **Add**.</span></span>

   <span data-ttu-id="beed1-174">Depois que o aplicativo for carregado, você será levado diretamente para uma sessão de chat com o bot.</span><span class="sxs-lookup"><span data-stu-id="beed1-174">After the app is loaded, you will be taken directly to a chat session with the bot.</span></span>  <span data-ttu-id="beed1-175">Você pode digitar `intro` para mostrar um cartão de apresentação e `show` para mostrar seus detalhes do Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="beed1-175">You can type `intro` to show an introduction card, and `show` to show your details from Microsoft Graph.</span></span>  <span data-ttu-id="beed1-176">(Isso exigirá uma aprovação de permissões adicionais).</span><span class="sxs-lookup"><span data-stu-id="beed1-176">(This will require an additional permissions approval).</span></span>

   <span data-ttu-id="beed1-177">A depuração funciona normalmente - experimente você mesmo!</span><span class="sxs-lookup"><span data-stu-id="beed1-177">Debugging works as you normally would expect - try it yourself!</span></span> <span data-ttu-id="beed1-178">Abra o arquivo `bot/dialogs/rootDialog.js` e localize o método `triggerCommand(...)`.</span><span class="sxs-lookup"><span data-stu-id="beed1-178">Open the `bot/dialogs/rootDialog.js` file and locate the `triggerCommand(...)` method.</span></span>  <span data-ttu-id="beed1-179">Defina um ponto de interrupção no caso padrão.</span><span class="sxs-lookup"><span data-stu-id="beed1-179">Set a breakpoint on the default case.</span></span>  <span data-ttu-id="beed1-180">Em seguida, digite algum texto.</span><span class="sxs-lookup"><span data-stu-id="beed1-180">Then type some text.</span></span>

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="beed1-181">Saiba o que acontece quando você executa seu aplicativo localmente no depurador.</span><span class="sxs-lookup"><span data-stu-id="beed1-181">Learn what happens when you run your app locally in the debugger.</span></span></summary>

<span data-ttu-id="beed1-182">Quando você pressiona a **tecla F5,** o Teams Toolkit:</span><span class="sxs-lookup"><span data-stu-id="beed1-182">When you press the **F5** key, the Teams Toolkit:</span></span>

1. <span data-ttu-id="beed1-183">Registra seu aplicativo com Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="beed1-183">Registers your application with Azure Active Directory.</span></span>
1. <span data-ttu-id="beed1-184">Registra seu aplicativo para "side loading" no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="beed1-184">Registers your application for "side loading" in Microsoft Teams.</span></span>
1. <span data-ttu-id="beed1-185">Inicia o back-end do aplicativo em execução localmente usando as Ferramentas Principais da [Função do Azure.](/azure/azure-functions/functions-run-local?#start)</span><span class="sxs-lookup"><span data-stu-id="beed1-185">Starts your application backend running locally using [Azure Function Core Tools](/azure/azure-functions/functions-run-local?#start).</span></span>
1. <span data-ttu-id="beed1-186">Inicia um túnel ngrok para que Teams possa se comunicar com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="beed1-186">Starts an ngrok tunnel so Teams can communicate with your app.</span></span>
1. <span data-ttu-id="beed1-187">Inicia Microsoft Teams com um comando para instruir Teams fazer sideload do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="beed1-187">Starts Microsoft Teams with a command to instruct Teams to sideload the application.</span></span>

</details>

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="beed1-188">Saiba como solucionar problemas comuns ao executar seu aplicativo localmente.</span><span class="sxs-lookup"><span data-stu-id="beed1-188">Learn how to troubleshoot common issues when running your app locally.</span></span></summary>

<span data-ttu-id="beed1-189">Para executar com êxito seu aplicativo no Teams, você deve ter uma conta de desenvolvimento do Microsoft 365 que permite o sideload do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="beed1-189">To successfully run your app in Teams, you must have a Microsoft 365 development account that allows app sideloading.</span></span> <span data-ttu-id="beed1-190">Para obter mais informações sobre abertura de conta, confira [Pré-requisitos](prerequisites.md#enable-sideloading).</span><span class="sxs-lookup"><span data-stu-id="beed1-190">For more information on account opening, see [Prerequisites](prerequisites.md#enable-sideloading).</span></span>

> [!TIP]
> <span data-ttu-id="beed1-191">Verifique se há problemas antes de fazer o sideload de seu aplicativo, usando a [ferramenta de validação de aplicativo](https://dev.teams.microsoft.com/appvalidation.html), que está incluída no kit de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="beed1-191">Check for issues before sideloading your app, using the [app validation tool](https://dev.teams.microsoft.com/appvalidation.html), which is included in the toolkit.</span></span> <span data-ttu-id="beed1-192">Corrija os erros para fazer o sideload do aplicativo com êxito.</span><span class="sxs-lookup"><span data-stu-id="beed1-192">Fix the errors to successfully sideload the app.</span></span>
</details>

[!INCLUDE [Provision and Deploy your app on Azure](~/includes/get-started/azure-provisioning-instructions.md)]

<!-- markdownlint-disable MD033 -->

<details>
<summary><span data-ttu-id="beed1-193">Saber o que acontece quando você implanta o seu aplicativo no Azure</span><span class="sxs-lookup"><span data-stu-id="beed1-193">Learn what happens when you deployed your app to Azure</span></span></summary>

<span data-ttu-id="beed1-194">Antes da implantação, o aplicativo era executado localmente:</span><span class="sxs-lookup"><span data-stu-id="beed1-194">Before deployment, the application has been running locally:</span></span>

1. <span data-ttu-id="beed1-195">O back-end é executado usando o _Azure Functions Core Tools_.</span><span class="sxs-lookup"><span data-stu-id="beed1-195">The backend runs using _Azure Functions Core Tools_.</span></span>
1. <span data-ttu-id="beed1-196">O ponto de extremidade HTTP do aplicativo, onde o Microsoft Teams carrega o aplicativo, é executado localmente.</span><span class="sxs-lookup"><span data-stu-id="beed1-196">The application HTTP endpoint, where Microsoft Teams loads the application, runs locally.</span></span>

   <span data-ttu-id="beed1-197">A implantação envolve o provisionamento de recursos em uma assinatura ativa do Azure e a implantação (upload) do código de back-end e front-end do aplicativo para o Azure.</span><span class="sxs-lookup"><span data-stu-id="beed1-197">Deployment involves provisioning resources on an active Azure subscription and deploying (uploading) the backend and frontend code for the application to Azure.</span></span> <span data-ttu-id="beed1-198">O back-end usa uma variedade de serviços do Azure, incluindo o Serviço de Aplicativo do Azure e o Serviço de Bot do Azure.</span><span class="sxs-lookup"><span data-stu-id="beed1-198">The backend uses a variety of Azure services, including Azure App Service and Azure Bot Service.</span></span>

</details>

## <a name="see-also"></a><span data-ttu-id="beed1-199">Confira também</span><span class="sxs-lookup"><span data-stu-id="beed1-199">See also</span></span>

* [<span data-ttu-id="beed1-200">Visão geral dos tutoriais</span><span class="sxs-lookup"><span data-stu-id="beed1-200">Tutorials Overview</span></span>](code-samples.md) 
* [<span data-ttu-id="beed1-201">Criar um aplicativo usando React</span><span class="sxs-lookup"><span data-stu-id="beed1-201">Create an app using React</span></span>](first-app-react.md)
* [<span data-ttu-id="beed1-202">Criar um aplicativo usando o Blazor</span><span class="sxs-lookup"><span data-stu-id="beed1-202">Create an app using Blazor</span></span>](first-app-blazor.md)
* [<span data-ttu-id="beed1-203">Criar um aplicativo usando SPFx</span><span class="sxs-lookup"><span data-stu-id="beed1-203">Create an app using SPFx</span></span>](first-app-spfx.md)
* [<span data-ttu-id="beed1-204">Criar um aplicativo usando C# ou .NET</span><span class="sxs-lookup"><span data-stu-id="beed1-204">Create an app using C# or .NET</span></span>](get-started-dotnet-app-studio.md)
* [<span data-ttu-id="beed1-205">Criar um aplicativo usando o Node.js</span><span class="sxs-lookup"><span data-stu-id="beed1-205">Create an app using Node.js</span></span>](get-started-nodejs-app-studio.md)
* [<span data-ttu-id="beed1-206">Criar um aplicativo usando o gerador Yeoman</span><span class="sxs-lookup"><span data-stu-id="beed1-206">Create an app using Yeoman generator</span></span>](get-started-yeoman.md)
* [<span data-ttu-id="beed1-207">Criar uma extensão de mensagem</span><span class="sxs-lookup"><span data-stu-id="beed1-207">Create a messaging extension</span></span>](first-message-extension.md)
* [<span data-ttu-id="beed1-208">Exemplos de código</span><span class="sxs-lookup"><span data-stu-id="beed1-208">Code Samples</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples)