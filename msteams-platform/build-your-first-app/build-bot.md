---
title: Comece - Construa um bot
author: girliemac
description: Crie rapidamente um bot de Microsoft Teams usando o Microsoft Teams Toolkit.
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
# <a name="create-your-first-bot-for-teams"></a><span data-ttu-id="7a172-103">Crie seu primeiro bot para Teams</span><span class="sxs-lookup"><span data-stu-id="7a172-103">Create your first bot for Teams</span></span>

<span data-ttu-id="7a172-104">Este tutorial ensina você a construir um aplicativo básico de bot.</span><span class="sxs-lookup"><span data-stu-id="7a172-104">This tutorial teaches you to build a basic bot app.</span></span> <span data-ttu-id="7a172-105">Um bot atua como um intermediário entre Teams usuários e seu aplicativo ou serviço web com uma interface de conversação.</span><span class="sxs-lookup"><span data-stu-id="7a172-105">A bot acts as an intermediary between Teams users and your web app or service with a conversational interface.</span></span> <span data-ttu-id="7a172-106">As pessoas podem conversar com um bot para obter rapidamente informações ou iniciar fluxos de trabalho e tarefas executadas pelo seu serviço.</span><span class="sxs-lookup"><span data-stu-id="7a172-106">People can chat with a bot to quickly get information or initiate workflows and tasks performed by your service.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="7a172-107">O que você vai aprender</span><span class="sxs-lookup"><span data-stu-id="7a172-107">What you'll learn</span></span>

* <span data-ttu-id="7a172-108">Crie um projeto de aplicativo e bot usando o Microsoft Teams Toolkit para Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="7a172-108">Create an app project and bot using the Microsoft Teams Toolkit for Visual Studio Code.</span></span>
* <span data-ttu-id="7a172-109">Entenda as configurações de aplicativos Teams relevantes para os bots.</span><span class="sxs-lookup"><span data-stu-id="7a172-109">Understand the Teams app configurations relevant to bots.</span></span>
* <span data-ttu-id="7a172-110">Hospede e execute um aplicativo localmente usando uma solução de túnel local.</span><span class="sxs-lookup"><span data-stu-id="7a172-110">Host and run an app locally using a localhost tunneling solution.</span></span>
* <span data-ttu-id="7a172-111">Carga lateral e teste um bot em Teams.</span><span class="sxs-lookup"><span data-stu-id="7a172-111">Sideload and test a bot in Teams.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7a172-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="7a172-112">Prerequisites</span></span>

<span data-ttu-id="7a172-113">Certifique-se de entender como configurar e construir um aplicativo de Teams simples.</span><span class="sxs-lookup"><span data-stu-id="7a172-113">Ensure that you understand how to set up and build a simple Teams app.</span></span> <span data-ttu-id="7a172-114">Para obter mais informações, consulte [criar seu primeiro Microsoft Teams aplicativo "Hello, World!".](../build-your-first-app/build-and-run.md)</span><span class="sxs-lookup"><span data-stu-id="7a172-114">For more information, see [create your first Microsoft Teams "Hello, World!" app](../build-your-first-app/build-and-run.md).</span></span> 

## <a name="1-create-your-app-project"></a><span data-ttu-id="7a172-115">1. Crie seu projeto de aplicativo</span><span class="sxs-lookup"><span data-stu-id="7a172-115">1. Create your app project</span></span>

<span data-ttu-id="7a172-116">O Microsoft Teams Toolkit ajuda a configurar os seguintes componentes para o seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="7a172-116">The Microsoft Teams Toolkit helps you set up the following components for your app:</span></span> 

* <span data-ttu-id="7a172-117">**Configurações de aplicativos e andaimes** relevantes para bots.</span><span class="sxs-lookup"><span data-stu-id="7a172-117">**App configurations and scaffolding** relevant to bots.</span></span>
* <span data-ttu-id="7a172-118">**Bot** que é automaticamente registrado no serviço de Microsoft Azure Bot.</span><span class="sxs-lookup"><span data-stu-id="7a172-118">**Bot** that's automatically registered with the Microsoft Azure Bot Service.</span></span>

<span data-ttu-id="7a172-119">**Para criar seu projeto de aplicativo**</span><span class="sxs-lookup"><span data-stu-id="7a172-119">**To create your app project**</span></span>

1. Em Visual Studio Code, selecione **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: na Barra de Atividades esquerda e escolha **Criar um novo aplicativo de Teams**.

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-01.png" alt-text="Captura de tela mostrando como criar um aplicativo no Teams Toolkit.":::

1. <span data-ttu-id="7a172-122">Quando solicitado, faça login com sua conta de desenvolvimento Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="7a172-122">When prompted, sign in with your Microsoft 365 development account.</span></span> 
1. <span data-ttu-id="7a172-123">Na tela do projeto Selecionar, selecione Chat bots:</span><span class="sxs-lookup"><span data-stu-id="7a172-123">On the Select project screen, select Conversation bots:</span></span> 

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-02.png" alt-text="Captura de tela mostrando como criar um novo bot no Teams Toolkit.":::

1. <span data-ttu-id="7a172-125">Na tela do **projeto Configurar, digite** um nome para o seu bot.</span><span class="sxs-lookup"><span data-stu-id="7a172-125">On the **Configure project** screen, enter a name for your bot.</span></span> <span data-ttu-id="7a172-126">Este é o nome padrão do seu aplicativo e também o nome do diretório de projetos do aplicativo em sua máquina local.</span><span class="sxs-lookup"><span data-stu-id="7a172-126">This is the default name for your app and also the name of the app project directory on your local machine.</span></span>
1. <span data-ttu-id="7a172-127">Selecione **Criar um novo registro de** bot create  >  **bot,** conforme mostrado na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="7a172-127">Select **Create a new Bot** > **Create Bot Registration** as shown in the following image:</span></span>

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-03.png" alt-text="Captura de tela mostrando nomear novo bot no Teams Toolkit.":::

    <span data-ttu-id="7a172-129">Se for bem sucedido, seu novo bot terá um **status registrado.**</span><span class="sxs-lookup"><span data-stu-id="7a172-129">If successful, your new bot will have a **Registered** status.</span></span> <span data-ttu-id="7a172-130">Agora, seu bot está automaticamente registrado no serviço de Microsoft Azure Bot.</span><span class="sxs-lookup"><span data-stu-id="7a172-130">Now your bot is automatically registered with the Microsoft Azure Bot Service.</span></span> 

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-04.png" alt-text="Captura de tela mostrando o registro de novo bot no Teams Toolkit.":::

1. <span data-ttu-id="7a172-132">Selecione **Terminar** na parte inferior da tela e salvar seu projeto em sua máquina.</span><span class="sxs-lookup"><span data-stu-id="7a172-132">Select **Finish** at the bottom of the screen and save your project on your machine.</span></span>  

## <a name="2-understand-your-app-project-components"></a><span data-ttu-id="7a172-133">2. Entenda os componentes do projeto do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="7a172-133">2. Understand your app project components</span></span>

<span data-ttu-id="7a172-134">Muitas das configurações e andaimes do aplicativo são configuradas automaticamente quando você cria seu projeto com o Teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="7a172-134">Much of the app configurations and scaffolding are set up automatically when you create your project with the Teams Toolkit.</span></span> <span data-ttu-id="7a172-135">Vejamos os principais componentes para a construção de um bot:</span><span class="sxs-lookup"><span data-stu-id="7a172-135">Let's look at the main components for building a bot:</span></span>

:::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-05.png" alt-text="Captura de tela mostrando um andaime de projeto no Teams Toolkit.":::

<span data-ttu-id="7a172-137">Se você criou uma guia em outro tutorial, o andaime do aplicativo para o bot é diferente.</span><span class="sxs-lookup"><span data-stu-id="7a172-137">If you created a tab in another tutorial, the app scaffolding for the bot is different.</span></span> <span data-ttu-id="7a172-138">Ao contrário das guias, o desenvolvimento de bots não exige que você construa nenhum componente web front-end ou use o Teams Cliente JavaScript SDK.</span><span class="sxs-lookup"><span data-stu-id="7a172-138">Unlike tabs, bot development doesn't require you to build any front-end web components or use the Teams JavaScript client SDK.</span></span>  <span data-ttu-id="7a172-139">Em vez disso, o andaime usa o [Microsoft Bot Framework](https://dev.botframework.com/), que é um SDK de código aberto para a construção de bots inteligentes de nível corporativo que podem funcionar na web, mobile e, claro, Teams!</span><span class="sxs-lookup"><span data-stu-id="7a172-139">Instead, the scaffolding uses the [Microsoft Bot Framework](https://dev.botframework.com/), which is an open-source SDK for building intelligent, enterprise-grade bots that can work on the web, mobile, and of course Teams!</span></span> 

<span data-ttu-id="7a172-140">O `botActivityHandler.js` arquivo, localizado no diretório raiz do seu projeto, é o manipulador específico de Teams que lida com as atividades do bot, como como o bot responde a mensagens específicas.</span><span class="sxs-lookup"><span data-stu-id="7a172-140">The `botActivityHandler.js` file, located in the root directory of your project, is the Teams-specific handler that handles bot activities, such as how the bot responds to specific messages.</span></span> <span data-ttu-id="7a172-141">O andaime do aplicativo fornece um `botActivityHandler.js` arquivo localizado no diretório raiz do seu projeto, é o manipulador específico Teams que lida com atividades de bot, como como o bot responde a mensagens específicas.</span><span class="sxs-lookup"><span data-stu-id="7a172-141">The app scaffolding provides a `botActivityHandler.js` file located in the root directory of your project, is the Teams specific handler that handles bot activities such as how the bot responds to specific messages.</span></span>

## <a name="3-securely-expose-your-localhost-to-the-internet"></a><span data-ttu-id="7a172-142">3. Exponha com segurança seu local à internet</span><span class="sxs-lookup"><span data-stu-id="7a172-142">3. Securely expose your localhost to the internet</span></span>

<span data-ttu-id="7a172-143">Dê uma olhada no `index.js` arquivo, que cria um servidor HTTP e lida com roteamento para ouvir as solicitações recebidas do seu bot.</span><span class="sxs-lookup"><span data-stu-id="7a172-143">Take a look at the `index.js` file, which creates an HTTP server and handles routing to listen for incoming requests to your bot.</span></span> <span data-ttu-id="7a172-144">O `/api/messages` URL de ponto final do seu aplicativo é para responder às solicitações do cliente:</span><span class="sxs-lookup"><span data-stu-id="7a172-144">The `/api/messages` is your app's endpoint URL to respond to client requests:</span></span> 

```JavaScript
server.post('/api/messages', (req, res) => { 
  adapter.processActivity(req, res, async (context) => { 
    await botActivityHandler.run(context); 
  }); 
}); 
```

<span data-ttu-id="7a172-145">Para encaminhar as solicitações à lógica do seu bot, você deve configurar uma URL acessível ao público, como `https://example.com/api/messages` , em vez de `https://localhost` .</span><span class="sxs-lookup"><span data-stu-id="7a172-145">To forward the requests to your bot's logic, you must set up a publicly accessible URL, such as `https://example.com/api/messages`, instead of `https://localhost`.</span></span> <span data-ttu-id="7a172-146">Como seu aplicativo está sendo executado a partir de seu localhost atualmente, você deve *túnel* da rede.</span><span class="sxs-lookup"><span data-stu-id="7a172-146">Because your app is running from your localhost currently, you must *tunnel* the network.</span></span>

<span data-ttu-id="7a172-147">O tunelamento é um protocolo que permite transportar dados através de uma rede.</span><span class="sxs-lookup"><span data-stu-id="7a172-147">Tunneling is a protocol that allows you to transport data across a network.</span></span> <span data-ttu-id="7a172-148">E o túnel local lhe dá uma conexão entre sua máquina local e uma conexão remota.</span><span class="sxs-lookup"><span data-stu-id="7a172-148">And localhost tunneling gives you a connection between your local machine and a remote connection.</span></span> <span data-ttu-id="7a172-149">Para expor com segurança seu local à internet, recomendamos que você use a ferramenta de terceiros chamada **ngrok**.</span><span class="sxs-lookup"><span data-stu-id="7a172-149">To securely expose your localhost to the internet, we recommend you to use the 3rd party tool called, **ngrok**.</span></span> <span data-ttu-id="7a172-150">Isso lhe dará uma URL segura.</span><span class="sxs-lookup"><span data-stu-id="7a172-150">This will give you a secure URL.</span></span> 

1. <span data-ttu-id="7a172-151">Vá até o [site ngrok.com](https://ngrok.com/download) e siga as instruções para instalar e configurar ngrok em seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="7a172-151">Go to the [ngrok.com](https://ngrok.com/download) site and follow the instruction to install and set up ngrok in your environment.</span></span> 
    
    <span data-ttu-id="7a172-152">Adicione o caminho completo ao arquivo ngrok.exe que você instalou à variável de ambiente PATH do sistema.</span><span class="sxs-lookup"><span data-stu-id="7a172-152">Add the full path to the ngrok.exe file that you installed to the system PATH environment variable.</span></span> <span data-ttu-id="7a172-153">Os passos exatos são específicos para a concha que você está usando.</span><span class="sxs-lookup"><span data-stu-id="7a172-153">The exact steps are specific to the shell that you are using.</span></span>

1.  <span data-ttu-id="7a172-154">Depois de terminar de configurá-lo, abra um terminal e `ngrok http -host-header=rewrite 3978` corra.</span><span class="sxs-lookup"><span data-stu-id="7a172-154">After you have finished setting it up, open a terminal and run `ngrok http -host-header=rewrite 3978`.</span></span> 

    <span data-ttu-id="7a172-155">Agora, a ngrok fornece uma URL pública e segura que encaminha para o seu localhost na porta 3978, então copie a URL HTTPS, por exemplo, como mostrado na captura de tela abaixo, já que `https://287a4f4223bc.ngrok.io` Teams requer conexões HTTPS:</span><span class="sxs-lookup"><span data-stu-id="7a172-155">Now ngrok provides you a public, secure URL that forwards to your localhost at port 3978, so copy the HTTPS URL, for example, `https://287a4f4223bc.ngrok.io` as shown in the screenshot below, since Teams requires HTTPS connections:</span></span> 

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-ngrok-06.png" alt-text="Captura de tela mostrando o túnel do localhost com ngrok.":::

1. <span data-ttu-id="7a172-157">Registre a URL no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7a172-157">Register the URL in your app manifest.</span></span> 

## <a name="4-register-your-bot-endpoint"></a><span data-ttu-id="7a172-158">4. Registre seu ponto final do bot</span><span class="sxs-lookup"><span data-stu-id="7a172-158">4. Register your bot endpoint</span></span>

<span data-ttu-id="7a172-159">Para usar um bot em Teams, você deve registrá-lo no Serviço Azure Bot.</span><span class="sxs-lookup"><span data-stu-id="7a172-159">To use a bot in Teams, you must register it with the Azure Bot Service.</span></span> <span data-ttu-id="7a172-160">Isso é feito automaticamente quando você configura seu aplicativo usando o Teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="7a172-160">This is done automatically when you set up your app using the Teams Toolkit.</span></span>

<span data-ttu-id="7a172-161">Você ainda deve especificar um endereço de ponto final para receber e processar mensagens do usuário ou solicitações enviadas ao bot.</span><span class="sxs-lookup"><span data-stu-id="7a172-161">You must still specify an endpoint address to receive and process user messages, or requests sent to the bot.</span></span> <span data-ttu-id="7a172-162">Normalmente, a URL se parece `https://HOST_URL/api/messages` com .</span><span class="sxs-lookup"><span data-stu-id="7a172-162">Typically, the URL looks like `https://HOST_URL/api/messages`.</span></span> <span data-ttu-id="7a172-163">Você pode configurar isso no kit de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="7a172-163">You can configure this in the toolkit.</span></span>

1. <span data-ttu-id="7a172-164">Em Visual Studio Code, **Microsoft Teams Toolkit** aberto.</span><span class="sxs-lookup"><span data-stu-id="7a172-164">In Visual Studio Code, open **Microsoft Teams Toolkit**.</span></span>
1. <span data-ttu-id="7a172-165">Selecione **bots**  >  **Registros de bots existentes** e selecione o bot criado durante a configuração.</span><span class="sxs-lookup"><span data-stu-id="7a172-165">Select **Bots** > **Existing bot registrations** and select the bot you created during setup.</span></span> 
1. <span data-ttu-id="7a172-166">No campo de **endereços do ponto final do Bot,** digite a URL ngrok, por `https://287a4f4223bc.ngrok.io` exemplo, onde você está hospedando o bot e `/api/messages` anexar a ele:</span><span class="sxs-lookup"><span data-stu-id="7a172-166">In the **Bot endpoint address** field, enter the ngrok URL, for example, `https://287a4f4223bc.ngrok.io`, where you're hosting the bot and append `/api/messages` to it:</span></span>

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-07.png" alt-text="Captura de tela mostrando como túnel localhost com ngrok.":::

    <span data-ttu-id="7a172-168">Seu bot será capaz de responder às mensagens em Teams, depois de configurar o ponto final corretamente.</span><span class="sxs-lookup"><span data-stu-id="7a172-168">Your bot will be able to respond to messages in Teams, after you set up the endpoint correctly.</span></span> 

## <a name="5-build-and-run-your-app"></a><span data-ttu-id="7a172-169">5. Construa e execute seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="7a172-169">5. Build and run your app</span></span>

<span data-ttu-id="7a172-170">Você configurou uma URL para hospedar seu bot e configurou-o para lidar com mensagens.</span><span class="sxs-lookup"><span data-stu-id="7a172-170">You've set up a URL to host your bot and configured it to handle messages.</span></span> <span data-ttu-id="7a172-171">É hora de colocar seu aplicativo em funcionamento.</span><span class="sxs-lookup"><span data-stu-id="7a172-171">It's time to get your app up and running.</span></span>

1. <span data-ttu-id="7a172-172">Em um terminal, vá para o diretório raiz do seu projeto de aplicativo e execute `npm install` .</span><span class="sxs-lookup"><span data-stu-id="7a172-172">In a terminal, go to the root directory of your app project and run `npm install`.</span></span>
1. <span data-ttu-id="7a172-173">`npm start`Corra.</span><span class="sxs-lookup"><span data-stu-id="7a172-173">Run `npm start`.</span></span>

   <span data-ttu-id="7a172-174">Se for bem-sucedido, você verá a seguinte mensagem indicando que seu bot está ouvindo a atividade em seu `localhost` :</span><span class="sxs-lookup"><span data-stu-id="7a172-174">If successful, you see the following message indicating your bot is listening for activity at your `localhost`:</span></span>

   `Bot/ME service listening at http://localhost:3978`

## <a name="6-sideload-your-bot-in-teams"></a><span data-ttu-id="7a172-175">6. Carregar lateralmente seu bot em Teams</span><span class="sxs-lookup"><span data-stu-id="7a172-175">6. Sideload your bot in Teams</span></span>

<span data-ttu-id="7a172-176">Com o bot funcionando, você pode instalá-lo em Teams.</span><span class="sxs-lookup"><span data-stu-id="7a172-176">With your bot running, you can install it in Teams.</span></span>

> [!TIP]
> <span data-ttu-id="7a172-177">Se você nunca mais regou um aplicativo de Teams antes e se deparar com problemas, siga estas [instruções](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams).</span><span class="sxs-lookup"><span data-stu-id="7a172-177">If you haven't sideloaded a Teams app before and run into issues, follow these [instructions](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams).</span></span>

1. <span data-ttu-id="7a172-178">Em Visual Studio Code, selecione a tecla **F5** para lançar um Teams cliente web.</span><span class="sxs-lookup"><span data-stu-id="7a172-178">In Visual Studio Code, select the **F5** key to launch a Teams web client.</span></span>
1. <span data-ttu-id="7a172-179">No aplicativo instalar a caixa de diálogo, selecione **Adicionar para mim**.</span><span class="sxs-lookup"><span data-stu-id="7a172-179">In the app install dialog, select **Add for me**.</span></span> 

   > [!Note]
   > <span data-ttu-id="7a172-180">Por padrão, o aplicativo é adicionado à sua mensagem de bate-papo direto 1:1, no entanto você pode optar por instalá-lo em uma equipe ou chat clicando na pequena seta ao lado **de Add para mim**.</span><span class="sxs-lookup"><span data-stu-id="7a172-180">By default, the app is added to your 1:1 direct chat message, however you can choose to install it to a team or chat by clicking the little arrow beside **Add for me**.</span></span> <span data-ttu-id="7a172-181">Neste tutorial, vamos clicar em Adicionar.</span><span class="sxs-lookup"><span data-stu-id="7a172-181">In this tutorial, let’s just click Add.</span></span>

   :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-install-08.png" alt-text="Captura de tela mostrando túnel localhost com ngrok.":::

## <a name="7-test-your-bot"></a><span data-ttu-id="7a172-183">7. Teste seu bot</span><span class="sxs-lookup"><span data-stu-id="7a172-183">7. Test your bot</span></span>

<span data-ttu-id="7a172-184">Vamos dizer "Olá" para o seu robô.</span><span class="sxs-lookup"><span data-stu-id="7a172-184">Let's say "Hello" to your bot.</span></span>

* <span data-ttu-id="7a172-185">Na caixa de composição, envie uma `Hello` mensagem.</span><span class="sxs-lookup"><span data-stu-id="7a172-185">In the compose box, send a `Hello` message.</span></span>
    <span data-ttu-id="7a172-186">Seu bot responde com algo como a seguinte mensagem:</span><span class="sxs-lookup"><span data-stu-id="7a172-186">Your bot replies with something like the following message:</span></span>

    :::image type="content" source="../assets/images/build-your-first-app/teams-client-bot.png" alt-text="Uma captura de tela mostrando um usuário dizer 'Olá' para um bot Teams e recebendo uma resposta.":::

    <span data-ttu-id="7a172-188">Agora você criou um bot básico de Teams que pode se comunicar com os usuários um a um ou em configurações de grupo (canais e chats) 🎉.</span><span class="sxs-lookup"><span data-stu-id="7a172-188">You have now created a basic Teams bot that can communicate with users one-on-one or in group settings (channels and chats) 🎉.</span></span>

## <a name="troubleshoot-your-bot"></a><span data-ttu-id="7a172-189">Solucionar problemas do seu bot</span><span class="sxs-lookup"><span data-stu-id="7a172-189">Troubleshoot your bot</span></span>

<span data-ttu-id="7a172-190">As informações a seguir podem ajudar se você tiver problemas para completar este tutorial.</span><span class="sxs-lookup"><span data-stu-id="7a172-190">The following information may help if you had issues completing this tutorial.</span></span>

### <a name="bot-isnt-connected-to-teams"></a><span data-ttu-id="7a172-191">Bot não está conectado a Teams</span><span class="sxs-lookup"><span data-stu-id="7a172-191">Bot isn't connected to Teams</span></span>


<span data-ttu-id="7a172-192">Se você instalou seu aplicativo, mas o bot não está funcionando, certifique-se de que o bot esteja [conectado ao *canal* Teams do Azure Bot Service](/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="7a172-192">If you installed your app but the bot isn't working, make sure the bot is [connected to the Azure Bot Service's Teams *channel*](/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true).</span></span>

<span data-ttu-id="7a172-193">É importante entender que isso não é o mesmo que um canal em Teams.</span><span class="sxs-lookup"><span data-stu-id="7a172-193">It's important to understand that this isn't the same as a channel in Teams.</span></span> <span data-ttu-id="7a172-194">Neste caso, um canal é como o Azure Bot Service conecta seu bot a Teams ou outro [aplicativo de comunicação suportado da Microsoft ou de terceiros.](/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="7a172-194">In this case, a channel is how the Azure Bot Service connects your bot to Teams or another [supported Microsoft or third-party communications app](/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true).</span></span>

## <a name="see-also"></a><span data-ttu-id="7a172-195">Confira também</span><span class="sxs-lookup"><span data-stu-id="7a172-195">See also</span></span>

* [<span data-ttu-id="7a172-196">Noções básicas de bot</span><span class="sxs-lookup"><span data-stu-id="7a172-196">Bot basics</span></span>](../bots/bot-basics.md)
* [<span data-ttu-id="7a172-197">Crie uma guia pessoal para Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="7a172-197">Build a personal tab for Microsoft Teams</span></span>](../build-your-first-app/build-personal-tab.md)
* [<span data-ttu-id="7a172-198">Veja o que mais Teams bots podem fazer com uma de nossas amostras</span><span class="sxs-lookup"><span data-stu-id="7a172-198">See what else Teams bots can do with one of our samples</span></span>](https://github.com/microsoft/BotBuilder-Samples#teams-samples)
* [<span data-ttu-id="7a172-199">Princípios básicos de conversas</span><span class="sxs-lookup"><span data-stu-id="7a172-199">Bot conversation basics</span></span>](../bots/how-to/conversations/conversation-basics.md)
* [<span data-ttu-id="7a172-200">Diretrizes de design</span><span class="sxs-lookup"><span data-stu-id="7a172-200">Design guidelines</span></span>](../bots/design/bots.md) 
* [<span data-ttu-id="7a172-201">Modelos de interface do usuário prontos para produção</span><span class="sxs-lookup"><span data-stu-id="7a172-201">Production-ready UI templates</span></span>](../concepts/design/design-teams-app-ui-templates.md)
* [<span data-ttu-id="7a172-202">Autenticação de bot em Teams</span><span class="sxs-lookup"><span data-stu-id="7a172-202">Bot authentication in Teams</span></span>](../bots/how-to/authentication/auth-flow-bot.md)
* [<span data-ttu-id="7a172-203">Microsoft Bot Framework</span><span class="sxs-lookup"><span data-stu-id="7a172-203">Microsoft Bot Framework</span></span>](https://dev.botframework.com/)
* [<span data-ttu-id="7a172-204">Crie um bot sem o kit de ferramentas</span><span class="sxs-lookup"><span data-stu-id="7a172-204">Create a bot without the toolkit</span></span>](../resources/bot-v3/bots-create.md)

## <a name="next-step"></a><span data-ttu-id="7a172-205">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="7a172-205">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7a172-206">Construir uma extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="7a172-206">Build a messaging extension</span></span>](../build-your-first-app/build-messaging-extension.md)
