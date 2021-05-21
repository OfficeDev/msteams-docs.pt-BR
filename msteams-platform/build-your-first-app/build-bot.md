---
title: Começar - Criar um bot
author: girliemac
description: Crie rapidamente um Microsoft Teams usando o Microsoft Teams Toolkit.
ms.author: timura
ms.date: 04/14/2020
ms.topic: tutorial
ms.openlocfilehash: 2cbd90b293e8ac8343febc7b3d23278d5bb5bf82
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565883"
---
# <a name="create-your-first-bot-for-teams"></a><span data-ttu-id="7d3cc-103">Crie seu primeiro bot para Teams</span><span class="sxs-lookup"><span data-stu-id="7d3cc-103">Create your first bot for Teams</span></span>

<span data-ttu-id="7d3cc-104">Este tutorial ensina você a criar um aplicativo de bot básico.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-104">This tutorial teaches you to build a basic bot app.</span></span> <span data-ttu-id="7d3cc-105">Um bot age como um intermediário entre Teams usuários e seu aplicativo Web ou serviço com uma interface de conversa.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-105">A bot acts as an intermediary between Teams users and your web app or service with a conversational interface.</span></span> <span data-ttu-id="7d3cc-106">As pessoas podem conversar com um bot para obter informações rapidamente ou iniciar fluxos de trabalho e tarefas executadas pelo seu serviço.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-106">People can chat with a bot to quickly get information or initiate workflows and tasks performed by your service.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="7d3cc-107">O que você aprenderá</span><span class="sxs-lookup"><span data-stu-id="7d3cc-107">What you'll learn</span></span>

* <span data-ttu-id="7d3cc-108">Crie um projeto de aplicativo e um bot usando o Microsoft Teams Toolkit para Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-108">Create an app project and bot using the Microsoft Teams Toolkit for Visual Studio Code.</span></span>
* <span data-ttu-id="7d3cc-109">Entenda as Teams de aplicativos relevantes para bots.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-109">Understand the Teams app configurations relevant to bots.</span></span>
* <span data-ttu-id="7d3cc-110">Hospede e execute um aplicativo localmente usando uma solução de túnel localhost.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-110">Host and run an app locally using a localhost tunneling solution.</span></span>
* <span data-ttu-id="7d3cc-111">Fazer sideload e testar um bot Teams.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-111">Sideload and test a bot in Teams.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7d3cc-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="7d3cc-112">Prerequisites</span></span>

<span data-ttu-id="7d3cc-113">Certifique-se de entender como configurar e criar um aplicativo Teams simples.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-113">Ensure that you understand how to set up and build a simple Teams app.</span></span> <span data-ttu-id="7d3cc-114">Para obter mais informações, [consulte create your first Microsoft Teams aplicativo "Hello, World!".](../build-your-first-app/build-and-run.md)</span><span class="sxs-lookup"><span data-stu-id="7d3cc-114">For more information, see [create your first Microsoft Teams "Hello, World!" app](../build-your-first-app/build-and-run.md).</span></span> 

## <a name="1-create-your-app-project"></a><span data-ttu-id="7d3cc-115">1. Crie seu projeto de aplicativo</span><span class="sxs-lookup"><span data-stu-id="7d3cc-115">1. Create your app project</span></span>

<span data-ttu-id="7d3cc-116">A Microsoft Teams Toolkit ajuda a configurar os seguintes componentes para seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="7d3cc-116">The Microsoft Teams Toolkit helps you set up the following components for your app:</span></span> 

* <span data-ttu-id="7d3cc-117">**Configurações de aplicativo e scaffolding relevantes** para bots.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-117">**App configurations and scaffolding** relevant to bots.</span></span>
* <span data-ttu-id="7d3cc-118">**Bot** que é registrado automaticamente com o serviço Microsoft Azure Bot.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-118">**Bot** that's automatically registered with the Microsoft Azure Bot Service.</span></span>

<span data-ttu-id="7d3cc-119">**Para criar seu projeto de aplicativo**</span><span class="sxs-lookup"><span data-stu-id="7d3cc-119">**To create your app project**</span></span>

1. Em Visual Studio Code, selecione **Microsoft Teams** barra de atividades à esquerda e escolha Criar um novo Teams :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: **app**.

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-01.png" alt-text="Captura de tela mostrando como criar um aplicativo no Teams Toolkit.":::

1. <span data-ttu-id="7d3cc-122">Quando solicitado, entre com sua conta Microsoft 365 de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-122">When prompted, sign in with your Microsoft 365 development account.</span></span> 
1. <span data-ttu-id="7d3cc-123">Na tela Selecionar projeto, selecione Bots de conversa:</span><span class="sxs-lookup"><span data-stu-id="7d3cc-123">On the Select project screen, select Conversation bots:</span></span> 

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-02.png" alt-text="Captura de tela mostrando como criar um novo bot no Teams Toolkit.":::

1. <span data-ttu-id="7d3cc-125">Na tela **Configurar projeto,** insira um nome para seu bot.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-125">On the **Configure project** screen, enter a name for your bot.</span></span> <span data-ttu-id="7d3cc-126">Esse é o nome padrão para seu aplicativo e também o nome do diretório do projeto do aplicativo em sua máquina local.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-126">This is the default name for your app and also the name of the app project directory on your local machine.</span></span>
1. <span data-ttu-id="7d3cc-127">Selecione **Criar um novo Registro de** Bot Criar  >  **Bot,** conforme mostrado na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="7d3cc-127">Select **Create a new Bot** > **Create Bot Registration** as shown in the following image:</span></span>

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-03.png" alt-text="Captura de tela mostrando a nomeação de novo bot no Teams Toolkit.":::

    <span data-ttu-id="7d3cc-129">Se tiver êxito, seu novo bot terá um status **Registrado.**</span><span class="sxs-lookup"><span data-stu-id="7d3cc-129">If successful, your new bot will have a **Registered** status.</span></span> <span data-ttu-id="7d3cc-130">Agora, seu bot é registrado automaticamente com o serviço Microsoft Azure Bot.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-130">Now your bot is automatically registered with the Microsoft Azure Bot Service.</span></span> 

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-04.png" alt-text="Captura de tela mostrando o registro de novo bot no Teams Toolkit.":::

1. <span data-ttu-id="7d3cc-132">Selecione **Concluir** na parte inferior da tela e salve seu projeto em seu computador.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-132">Select **Finish** at the bottom of the screen and save your project on your machine.</span></span>  

## <a name="2-understand-your-app-project-components"></a><span data-ttu-id="7d3cc-133">2. Entenda os componentes do projeto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="7d3cc-133">2. Understand your app project components</span></span>

<span data-ttu-id="7d3cc-134">Grande parte das configurações e scaffolding do aplicativo são configuradas automaticamente quando você cria seu projeto com o Teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-134">Much of the app configurations and scaffolding are set up automatically when you create your project with the Teams Toolkit.</span></span> <span data-ttu-id="7d3cc-135">Vamos ver os principais componentes para a criação de um bot:</span><span class="sxs-lookup"><span data-stu-id="7d3cc-135">Let's look at the main components for building a bot:</span></span>

:::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-05.png" alt-text="Captura de tela mostrando um scaffold de projeto no Teams Toolkit.":::

<span data-ttu-id="7d3cc-137">Se você criou uma guia em outro tutorial, o scaffolding do aplicativo para o bot é diferente.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-137">If you created a tab in another tutorial, the app scaffolding for the bot is different.</span></span> <span data-ttu-id="7d3cc-138">Ao contrário das guias, o desenvolvimento de bots não exige que você crie nenhum componente web front-end ou use o SDK do cliente JavaScript Teams.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-138">Unlike tabs, bot development doesn't require you to build any front-end web components or use the Teams JavaScript client SDK.</span></span>  <span data-ttu-id="7d3cc-139">Em vez disso, o scaffolding usa o [Microsoft Bot Framework](https://dev.botframework.com/), que é um SDK de código aberto para criar bots inteligentes de nível empresarial que podem funcionar na Web, em dispositivos móveis e, claro, Teams!</span><span class="sxs-lookup"><span data-stu-id="7d3cc-139">Instead, the scaffolding uses the [Microsoft Bot Framework](https://dev.botframework.com/), which is an open-source SDK for building intelligent, enterprise-grade bots that can work on the web, mobile, and of course Teams!</span></span> 

<span data-ttu-id="7d3cc-140">O arquivo, localizado no diretório raiz do seu projeto, é o manipulador específico Teams que lida com atividades de bot, como como o bot responde a mensagens `botActivityHandler.js` específicas.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-140">The `botActivityHandler.js` file, located in the root directory of your project, is the Teams-specific handler that handles bot activities, such as how the bot responds to specific messages.</span></span> <span data-ttu-id="7d3cc-141">O scaffolding de aplicativo fornece um arquivo localizado no diretório raiz do seu projeto, é o manipulador Teams específico que lida com atividades de bot, como como o bot responde a mensagens `botActivityHandler.js` específicas.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-141">The app scaffolding provides a `botActivityHandler.js` file located in the root directory of your project, is the Teams specific handler that handles bot activities such as how the bot responds to specific messages.</span></span>

## <a name="3-securely-expose-your-localhost-to-the-internet"></a><span data-ttu-id="7d3cc-142">3. Expor seu localhost com segurança à Internet</span><span class="sxs-lookup"><span data-stu-id="7d3cc-142">3. Securely expose your localhost to the internet</span></span>

<span data-ttu-id="7d3cc-143">Dê uma olhada no arquivo, que cria um servidor HTTP e lida com o roteamento para ouvir solicitações `index.js` de entrada para seu bot.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-143">Take a look at the `index.js` file, which creates an HTTP server and handles routing to listen for incoming requests to your bot.</span></span> <span data-ttu-id="7d3cc-144">A URL do ponto de extremidade do seu `/api/messages` aplicativo é para responder às solicitações do cliente:</span><span class="sxs-lookup"><span data-stu-id="7d3cc-144">The `/api/messages` is your app's endpoint URL to respond to client requests:</span></span> 

```JavaScript
server.post('/api/messages', (req, res) => { 
  adapter.processActivity(req, res, async (context) => { 
    await botActivityHandler.run(context); 
  }); 
}); 
```

<span data-ttu-id="7d3cc-145">Para encaminhar as solicitações para a lógica do bot, você deve configurar uma URL publicamente acessível, como , em `https://example.com/api/messages` vez de `https://localhost` .</span><span class="sxs-lookup"><span data-stu-id="7d3cc-145">To forward the requests to your bot's logic, you must set up a publicly accessible URL, such as `https://example.com/api/messages`, instead of `https://localhost`.</span></span> <span data-ttu-id="7d3cc-146">Como seu aplicativo está em execução no momento do seu localhost, você deve *canalizando* a rede.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-146">Because your app is running from your localhost currently, you must *tunnel* the network.</span></span>

<span data-ttu-id="7d3cc-147">O túnel é um protocolo que permite que você transporte dados em uma rede.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-147">Tunneling is a protocol that allows you to transport data across a network.</span></span> <span data-ttu-id="7d3cc-148">E o túnel localhost fornece uma conexão entre o computador local e uma conexão remota.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-148">And localhost tunneling gives you a connection between your local machine and a remote connection.</span></span> <span data-ttu-id="7d3cc-149">Para expor seu localhost com segurança à Internet, recomendamos que você use a ferramenta de terceiros chamada, **ngrok**.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-149">To securely expose your localhost to the internet, we recommend you to use the 3rd party tool called, **ngrok**.</span></span> <span data-ttu-id="7d3cc-150">Isso lhe dará uma URL segura.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-150">This will give you a secure URL.</span></span> 

1. <span data-ttu-id="7d3cc-151">Vá para o [site ngrok.com](https://ngrok.com/download) e siga a instrução para instalar e configurar o ngrok em seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-151">Go to the [ngrok.com](https://ngrok.com/download) site and follow the instruction to install and set up ngrok in your environment.</span></span> 
    
    <span data-ttu-id="7d3cc-152">Adicione o caminho completo ao arquivo ngrok.exe que você instalou à variável de ambiente PATH do sistema.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-152">Add the full path to the ngrok.exe file that you installed to the system PATH environment variable.</span></span> <span data-ttu-id="7d3cc-153">As etapas exatas são específicas do shell que você está usando.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-153">The exact steps are specific to the shell that you are using.</span></span>

1.  <span data-ttu-id="7d3cc-154">Depois de terminar de defini-lo, abra um terminal e execute `ngrok http -host-header=rewrite 3978` .</span><span class="sxs-lookup"><span data-stu-id="7d3cc-154">After you have finished setting it up, open a terminal and run `ngrok http -host-header=rewrite 3978`.</span></span> 

    <span data-ttu-id="7d3cc-155">Agora o ngrok fornece uma URL pública e segura que encaminha para o seu localhost na porta 3978, portanto, copie a URL HTTPS, por exemplo, conforme mostrado na captura de tela abaixo, já que o Teams requer conexões `https://287a4f4223bc.ngrok.io` HTTPS:</span><span class="sxs-lookup"><span data-stu-id="7d3cc-155">Now ngrok provides you a public, secure URL that forwards to your localhost at port 3978, so copy the HTTPS URL, for example, `https://287a4f4223bc.ngrok.io` as shown in the screenshot below, since Teams requires HTTPS connections:</span></span> 

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-ngrok-06.png" alt-text="Captura de tela mostrando o tunelamento de localhost com ngrok.":::

1. <span data-ttu-id="7d3cc-157">Registre a URL no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-157">Register the URL in your app manifest.</span></span> 

## <a name="4-register-your-bot-endpoint"></a><span data-ttu-id="7d3cc-158">4. Registre seu ponto de extremidade de bot</span><span class="sxs-lookup"><span data-stu-id="7d3cc-158">4. Register your bot endpoint</span></span>

<span data-ttu-id="7d3cc-159">Para usar um bot no Teams, você deve registrá-lo com o Serviço bot do Azure.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-159">To use a bot in Teams, you must register it with the Azure Bot Service.</span></span> <span data-ttu-id="7d3cc-160">Isso é feito automaticamente quando você configura seu aplicativo usando o Teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-160">This is done automatically when you set up your app using the Teams Toolkit.</span></span>

<span data-ttu-id="7d3cc-161">Você ainda deve especificar um endereço de ponto de extremidade para receber e processar mensagens de usuário ou solicitações enviadas para o bot.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-161">You must still specify an endpoint address to receive and process user messages, or requests sent to the bot.</span></span> <span data-ttu-id="7d3cc-162">Normalmente, a URL se parece com `https://HOST_URL/api/messages` .</span><span class="sxs-lookup"><span data-stu-id="7d3cc-162">Typically, the URL looks like `https://HOST_URL/api/messages`.</span></span> <span data-ttu-id="7d3cc-163">Você pode configurar isso no kit de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-163">You can configure this in the toolkit.</span></span>

1. <span data-ttu-id="7d3cc-164">Em Visual Studio Code, abra **Microsoft Teams Toolkit**.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-164">In Visual Studio Code, open **Microsoft Teams Toolkit**.</span></span>
1. <span data-ttu-id="7d3cc-165">Selecione **Bots**  >  **Registros de bots existentes** e selecione o bot que você criou durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-165">Select **Bots** > **Existing bot registrations** and select the bot you created during setup.</span></span> 
1. <span data-ttu-id="7d3cc-166">No campo **endereço do ponto** de extremidade bot, insira a URL do ngrok, por exemplo, , onde você está hospedando o bot e `https://287a4f4223bc.ngrok.io` anexar a `/api/messages` ele:</span><span class="sxs-lookup"><span data-stu-id="7d3cc-166">In the **Bot endpoint address** field, enter the ngrok URL, for example, `https://287a4f4223bc.ngrok.io`, where you're hosting the bot and append `/api/messages` to it:</span></span>

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-07.png" alt-text="Captura de tela mostrando como túnel localhost com ngrok.":::

    <span data-ttu-id="7d3cc-168">Seu bot poderá responder a mensagens no Teams, depois de configurar o ponto de extremidade corretamente.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-168">Your bot will be able to respond to messages in Teams, after you set up the endpoint correctly.</span></span> 

## <a name="5-build-and-run-your-app"></a><span data-ttu-id="7d3cc-169">5. Crie e execute seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="7d3cc-169">5. Build and run your app</span></span>

<span data-ttu-id="7d3cc-170">Você configurou uma URL para hospedar seu bot e configurá-lo para manipular mensagens.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-170">You've set up a URL to host your bot and configured it to handle messages.</span></span> <span data-ttu-id="7d3cc-171">É hora de fazer o aplicativo funcionar.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-171">It's time to get your app up and running.</span></span>

1. <span data-ttu-id="7d3cc-172">Em um terminal, vá para o diretório raiz do seu projeto de aplicativo e execute `npm install` .</span><span class="sxs-lookup"><span data-stu-id="7d3cc-172">In a terminal, go to the root directory of your app project and run `npm install`.</span></span>
1. <span data-ttu-id="7d3cc-173">Executar `npm start` .</span><span class="sxs-lookup"><span data-stu-id="7d3cc-173">Run `npm start`.</span></span>

   <span data-ttu-id="7d3cc-174">Se tiver êxito, você verá a seguinte mensagem indicando que seu bot está escutando atividades em seu `localhost` :</span><span class="sxs-lookup"><span data-stu-id="7d3cc-174">If successful, you see the following message indicating your bot is listening for activity at your `localhost`:</span></span>

   `Bot/ME service listening at http://localhost:3978`

## <a name="6-sideload-your-bot-in-teams"></a><span data-ttu-id="7d3cc-175">6. Fazer sideload do bot no Teams</span><span class="sxs-lookup"><span data-stu-id="7d3cc-175">6. Sideload your bot in Teams</span></span>

<span data-ttu-id="7d3cc-176">Com o bot em execução, você pode instalá-lo Teams.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-176">With your bot running, you can install it in Teams.</span></span>

> [!TIP]
> <span data-ttu-id="7d3cc-177">Se você não tiver sideloaded de um aplicativo Teams antes e tiver problemas, siga estas [instruções](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams).</span><span class="sxs-lookup"><span data-stu-id="7d3cc-177">If you haven't sideloaded a Teams app before and run into issues, follow these [instructions](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams).</span></span>

1. <span data-ttu-id="7d3cc-178">Em Visual Studio Code, selecione a **tecla F5** para iniciar um cliente Teams Web.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-178">In Visual Studio Code, select the **F5** key to launch a Teams web client.</span></span>
1. <span data-ttu-id="7d3cc-179">Na caixa de diálogo de instalação do aplicativo, selecione **Adicionar para mim**.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-179">In the app install dialog, select **Add for me**.</span></span> 

   > [!Note]
   > <span data-ttu-id="7d3cc-180">Por padrão, o aplicativo é adicionado à sua mensagem de chat direta 1:1, no entanto, você pode optar por instalá-la a uma equipe ou chat clicando na pequena seta ao lado de **Adicionar para mim**.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-180">By default, the app is added to your 1:1 direct chat message, however you can choose to install it to a team or chat by clicking the little arrow beside **Add for me**.</span></span> <span data-ttu-id="7d3cc-181">Neste tutorial, vamos clicar em Adicionar.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-181">In this tutorial, let’s just click Add.</span></span>

   :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-install-08.png" alt-text="Captura de tela mostrando o localhost de tunelamento com ngrok.":::

## <a name="7-test-your-bot"></a><span data-ttu-id="7d3cc-183">7. Teste seu bot</span><span class="sxs-lookup"><span data-stu-id="7d3cc-183">7. Test your bot</span></span>

<span data-ttu-id="7d3cc-184">Vamos dizer "Olá" para seu bot.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-184">Let's say "Hello" to your bot.</span></span>

* <span data-ttu-id="7d3cc-185">Na caixa de redação, envie uma `Hello` mensagem.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-185">In the compose box, send a `Hello` message.</span></span>
    <span data-ttu-id="7d3cc-186">Seu bot responde a algo como a seguinte mensagem:</span><span class="sxs-lookup"><span data-stu-id="7d3cc-186">Your bot replies with something like the following message:</span></span>

    :::image type="content" source="../assets/images/build-your-first-app/teams-client-bot.png" alt-text="Uma captura de tela mostrando um usuário dizer &quot;Hello&quot; para um Teams e obter uma resposta.":::

    <span data-ttu-id="7d3cc-188">Agora você criou um bot de Teams básico que pode se comunicar com os usuários um-a-um ou em configurações de grupo (canais e chats) 🎉.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-188">You have now created a basic Teams bot that can communicate with users one-on-one or in group settings (channels and chats) 🎉.</span></span>

## <a name="troubleshoot-your-bot"></a><span data-ttu-id="7d3cc-189">Solucionar problemas de seu bot</span><span class="sxs-lookup"><span data-stu-id="7d3cc-189">Troubleshoot your bot</span></span>

<span data-ttu-id="7d3cc-190">As informações a seguir podem ajudar se você tiver problemas ao concluir este tutorial.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-190">The following information may help if you had issues completing this tutorial.</span></span>

### <a name="bot-isnt-connected-to-teams"></a><span data-ttu-id="7d3cc-191">Bot não está conectado ao Teams</span><span class="sxs-lookup"><span data-stu-id="7d3cc-191">Bot isn't connected to Teams</span></span>


<span data-ttu-id="7d3cc-192">Se você instalou seu aplicativo, mas o bot não está funcionando, certifique-se de que o bot está conectado ao canal de Teams do Serviço de Bot [do Azure. ](/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="7d3cc-192">If you installed your app but the bot isn't working, make sure the bot is [connected to the Azure Bot Service's Teams *channel*](/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true).</span></span>

<span data-ttu-id="7d3cc-193">É importante entender que isso não é o mesmo que um canal no Teams.</span><span class="sxs-lookup"><span data-stu-id="7d3cc-193">It's important to understand that this isn't the same as a channel in Teams.</span></span> <span data-ttu-id="7d3cc-194">Nesse caso, um canal é como o Serviço de Bot do Azure conecta seu bot ao Teams ou outro aplicativo de comunicações da Microsoft ou de terceiros com [suporte.](/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="7d3cc-194">In this case, a channel is how the Azure Bot Service connects your bot to Teams or another [supported Microsoft or third-party communications app](/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true).</span></span>

## <a name="see-also"></a><span data-ttu-id="7d3cc-195">Confira também</span><span class="sxs-lookup"><span data-stu-id="7d3cc-195">See also</span></span>

* [<span data-ttu-id="7d3cc-196">Noções básicas de bot</span><span class="sxs-lookup"><span data-stu-id="7d3cc-196">Bot basics</span></span>](../bots/bot-basics.md)
* [<span data-ttu-id="7d3cc-197">Crie uma guia pessoal para Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="7d3cc-197">Build a personal tab for Microsoft Teams</span></span>](../build-your-first-app/build-personal-tab.md)
* [<span data-ttu-id="7d3cc-198">Veja o que Teams bots podem fazer com um de nossos exemplos</span><span class="sxs-lookup"><span data-stu-id="7d3cc-198">See what else Teams bots can do with one of our samples</span></span>](https://github.com/microsoft/BotBuilder-Samples#teams-samples)
* [<span data-ttu-id="7d3cc-199">Princípios básicos de conversas</span><span class="sxs-lookup"><span data-stu-id="7d3cc-199">Bot conversation basics</span></span>](../bots/how-to/conversations/conversation-basics.md)
* [<span data-ttu-id="7d3cc-200">Diretrizes de design</span><span class="sxs-lookup"><span data-stu-id="7d3cc-200">Design guidelines</span></span>](../bots/design/bots.md) 
* [<span data-ttu-id="7d3cc-201">Modelos de interface do usuário prontos para produção</span><span class="sxs-lookup"><span data-stu-id="7d3cc-201">Production-ready UI templates</span></span>](../concepts/design/design-teams-app-ui-templates.md)
* [<span data-ttu-id="7d3cc-202">Autenticação bot no Teams</span><span class="sxs-lookup"><span data-stu-id="7d3cc-202">Bot authentication in Teams</span></span>](../bots/how-to/authentication/auth-flow-bot.md)
* [<span data-ttu-id="7d3cc-203">Microsoft Bot Framework</span><span class="sxs-lookup"><span data-stu-id="7d3cc-203">Microsoft Bot Framework</span></span>](https://dev.botframework.com/)
* [<span data-ttu-id="7d3cc-204">Criar um bot sem o kit de ferramentas</span><span class="sxs-lookup"><span data-stu-id="7d3cc-204">Create a bot without the toolkit</span></span>](../resources/bot-v3/bots-create.md)

## <a name="next-step"></a><span data-ttu-id="7d3cc-205">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="7d3cc-205">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7d3cc-206">Construir uma extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="7d3cc-206">Build a messaging extension</span></span>](../build-your-first-app/build-messaging-extension.md)
