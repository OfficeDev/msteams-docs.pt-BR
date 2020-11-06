---
title: Introdução-criar um bot
author: heath-hamilton
description: Crie rapidamente um bot do Microsoft Teams usando o Microsoft Teams Toolkit.
ms.author: lajanuar
ms.date: 11/04/2020
ms.topic: tutorial
ms.openlocfilehash: 1229064ac6b7aab73c50048f0764c6a2353ab54a
ms.sourcegitcommit: 99c35de7e2c604bd8bce392242c2c2fa709cd50b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/06/2020
ms.locfileid: "48931733"
---
# <a name="build-a-bot-for-microsoft-teams"></a><span data-ttu-id="c7949-103">Criar um bot para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="c7949-103">Build a bot for Microsoft Teams</span></span>

<span data-ttu-id="c7949-104">Você criará um aplicativo de *bot* básico neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="c7949-104">You'll build a basic *bot* app in this tutorial.</span></span> <span data-ttu-id="c7949-105">Um bot atua como intermediário entre os usuários do Teams e o serviço Web.</span><span class="sxs-lookup"><span data-stu-id="c7949-105">A bot acts as an intermediary between Teams users and your web service.</span></span> <span data-ttu-id="c7949-106">As pessoas podem bater papo com um bot para obter informações rapidamente ou iniciar fluxos de trabalho e tarefas realizadas pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="c7949-106">People can chat with a bot to quickly get information or initiate workflows and tasks performed by your service.</span></span>

## <a name="your-assignment"></a><span data-ttu-id="c7949-107">Sua atribuição</span><span class="sxs-lookup"><span data-stu-id="c7949-107">Your assignment</span></span>

<span data-ttu-id="c7949-108">Seu local de trabalho criou um aplicativo do teams que usa [guias](../build-your-first-app/build-personal-tab.md) para informações de contato importantes da superfície.</span><span class="sxs-lookup"><span data-stu-id="c7949-108">Your workplace created a Teams app that uses [tabs](../build-your-first-app/build-personal-tab.md) to surface important contact information.</span></span> <span data-ttu-id="c7949-109">Por exemplo, os colegas têm acesso rápido ao número de telefone de suporte técnico.</span><span class="sxs-lookup"><span data-stu-id="c7949-109">For example, colleagues have quick access to the help desk phone number.</span></span> <span data-ttu-id="c7949-110">Mas em vez de chamar, e se as pessoas pudessem entrar em contato com o suporte técnico usando um chatbot?</span><span class="sxs-lookup"><span data-stu-id="c7949-110">But instead of calling, what if people could contact the help desk using a chatbot?</span></span> <span data-ttu-id="c7949-111">Seu chefe pede que você veja com rapidez como você pode obter um bot de conversação básico e em execução no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="c7949-111">Your boss asks you to look at how quickly you can get a basic conversational bot up and running in Teams.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="c7949-112">O que você aprenderá</span><span class="sxs-lookup"><span data-stu-id="c7949-112">What you'll learn</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="c7949-113">Criar um projeto de aplicativo e um bot usando o Microsoft Teams Toolkit para o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="c7949-113">Create an app project and bot using the Microsoft Teams Toolkit for Visual Studio Code</span></span>
> * <span data-ttu-id="c7949-114">Identificar algumas das configurações do aplicativo e scaffolding relevantes para bots</span><span class="sxs-lookup"><span data-stu-id="c7949-114">Identify some of the app configurations and scaffolding relevant to bots</span></span>
> * <span data-ttu-id="c7949-115">Hospedar um aplicativo localmente</span><span class="sxs-lookup"><span data-stu-id="c7949-115">Host an app locally</span></span>
> * <span data-ttu-id="c7949-116">Configurar um bot para o Teams</span><span class="sxs-lookup"><span data-stu-id="c7949-116">Configure a bot for Teams</span></span>
> * <span data-ttu-id="c7949-117">Sideload e testar um bot no Teams</span><span class="sxs-lookup"><span data-stu-id="c7949-117">Sideload and test a bot in Teams</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="c7949-118">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="c7949-118">Before you begin</span></span>

<span data-ttu-id="c7949-119">Se você ainda não tiver feito isso, não se esqueça de [entender e instalar os pré-requisitos de desenvolvimento do teams](build-first-app-overview.md#get-prerequisites).</span><span class="sxs-lookup"><span data-stu-id="c7949-119">If you haven't yet, make sure you [understand and install the Teams development prerequisites](build-first-app-overview.md#get-prerequisites).</span></span>

## <a name="1-create-your-app-project"></a><span data-ttu-id="c7949-120">1. criar seu projeto de aplicativo</span><span class="sxs-lookup"><span data-stu-id="c7949-120">1. Create your app project</span></span>

<span data-ttu-id="c7949-121">O Microsoft Teams Toolkit ajuda você a configurar os seguintes componentes para seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="c7949-121">The Microsoft Teams Toolkit helps you set up the following components for your app:</span></span>

* <span data-ttu-id="c7949-122">**Configurações do aplicativo e scaffolding** relevantes para bots</span><span class="sxs-lookup"><span data-stu-id="c7949-122">**App configurations and scaffolding** relevant to bots</span></span>
* <span data-ttu-id="c7949-123">**Bot** que é registrado automaticamente com o serviço de bot do Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="c7949-123">**Bot** that's automatically registered with the Microsoft Azure Bot Service</span></span>

> [!TIP]
> <span data-ttu-id="c7949-124">Se você ainda não criou um projeto de aplicativos do Microsoft Teams, talvez ache útil seguir [estas instruções](../build-your-first-app/build-and-run.md) para explicar os projetos com mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="c7949-124">If you haven't created a Teams app project before, you might find it helpful to follow [these instructions](../build-your-first-app/build-and-run.md) that explain projects in more detail.</span></span>

1. No Visual Studio Code, selecione **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: na barra de atividades à esquerda e escolha **criar um novo aplicativo Teams**.
1. <span data-ttu-id="c7949-126">Quando solicitado, entre com sua conta de desenvolvimento do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="c7949-126">When prompted, sign in with your Microsoft 365 development account.</span></span>
1. <span data-ttu-id="c7949-127">Na tela **Adicionar recursos** , selecione **bot** e, em seguida, **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c7949-127">On the **Add capabilities** screen, select **Bot** then **Next**.</span></span>
1. <span data-ttu-id="c7949-128">Insira um nome para seu aplicativo do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="c7949-128">Enter a name for your Teams app.</span></span> <span data-ttu-id="c7949-129">(Esse é o nome padrão para seu aplicativo e também o nome do diretório do projeto de aplicativo em sua máquina local.)</span><span class="sxs-lookup"><span data-stu-id="c7949-129">(This is the default name for your app and also the name of the app project directory on your local machine.)</span></span>
1. <span data-ttu-id="c7949-130">Vá para **Configurar bot** e selecione **criar um novo bot** e, em seguida, **criar registro de bot**.</span><span class="sxs-lookup"><span data-stu-id="c7949-130">Go to **Configure bot** and select **Create a new Bot** then **Create Bot Registration**.</span></span> <span data-ttu-id="c7949-131">Se tiver êxito, o novo bot terá um status **registrado** .</span><span class="sxs-lookup"><span data-stu-id="c7949-131">If successful, your new bot will have a **Registered** status.</span></span>
1. <span data-ttu-id="c7949-132">Selecione **concluir** na parte inferior da tela e escolha um local para criar seu projeto.</span><span class="sxs-lookup"><span data-stu-id="c7949-132">Select **Finish** at the bottom of the screen and choose a location to create your project.</span></span>

## <a name="2-identify-relevant-app-project-components"></a><span data-ttu-id="c7949-133">2. identificar componentes de projeto de aplicativo relevantes</span><span class="sxs-lookup"><span data-stu-id="c7949-133">2. Identify relevant app project components</span></span>

<span data-ttu-id="c7949-134">Grande parte das configurações do aplicativo e do scaffolding são configuradas automaticamente quando você cria seu projeto com o Teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="c7949-134">Much of the app configurations and scaffolding are set up automatically when you create your project with the Teams Toolkit.</span></span> <span data-ttu-id="c7949-135">Vamos examinar os principais componentes para a criação de um bot.</span><span class="sxs-lookup"><span data-stu-id="c7949-135">Let's look at the main components for building a bot.</span></span>

### <a name="app-configurations"></a><span data-ttu-id="c7949-136">Configurações do aplicativo</span><span class="sxs-lookup"><span data-stu-id="c7949-136">App configurations</span></span>

<span data-ttu-id="c7949-137">Para exibir ou atualizar as configurações do bot, selecione o **app Studio** no kit de ferramentas e vá para **bots**.</span><span class="sxs-lookup"><span data-stu-id="c7949-137">To view or update your bot's configurations, select **App Studio** in the toolkit and go to **Bots**.</span></span>

### <a name="app-scaffolding"></a><span data-ttu-id="c7949-138">Aplicativo scaffolding</span><span class="sxs-lookup"><span data-stu-id="c7949-138">App scaffolding</span></span>

<span data-ttu-id="c7949-139">O aplicativo scaffolding fornece um `botActivityHandler.js` arquivo, localizado no diretório raiz do seu projeto, para lidar com o modo como seu bot processa as atividades no Teams (por exemplo, como o bot responde a mensagens específicas como "Hello").</span><span class="sxs-lookup"><span data-stu-id="c7949-139">The app scaffolding provides a `botActivityHandler.js` file, located in the root directory of your project, for handling how your bot processes activities in Teams (for example, how the bot responds to specific messages such as "Hello").</span></span>

## <a name="3-set-up-a-secure-tunnel-to-your-app"></a><span data-ttu-id="c7949-140">3. configurar um túnel seguro para seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="c7949-140">3. Set up a secure tunnel to your app</span></span>

<span data-ttu-id="c7949-141">Para fins de teste, vamos hospedar seu aplicativo em um servidor Web local (porta 3978).</span><span class="sxs-lookup"><span data-stu-id="c7949-141">For testing purposes, let's host your app on a local web server (port 3978).</span></span>

1. <span data-ttu-id="c7949-142">Caso ainda não tenha feito isso, instale o [ngrok](https://ngrok.com/download).</span><span class="sxs-lookup"><span data-stu-id="c7949-142">If you haven't already, install [ngrok](https://ngrok.com/download).</span></span>
1. <span data-ttu-id="c7949-143">Em um terminal, execute `ngrok http -host-header=rewrite 3978` .</span><span class="sxs-lookup"><span data-stu-id="c7949-143">In a terminal, run `ngrok http -host-header=rewrite 3978`.</span></span>
1. <span data-ttu-id="c7949-144">Copie a URL HTTPS na saída (por exemplo,), pois o Microsoft `https://468b9ab725e9.ngrok.io` Teams requer conexões HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c7949-144">Copy the HTTPS URL in the output (for example, `https://468b9ab725e9.ngrok.io`) since Teams requires HTTPS connections.</span></span>

<span data-ttu-id="c7949-145">Com esta URL, o Teams (que requer conexões HTTPS) será habilitado para encapsular onde você está hospedando seu aplicativo ( `localhost` na porta 3978).</span><span class="sxs-lookup"><span data-stu-id="c7949-145">With this URL, Teams (which requires HTTPS connections) will be able tunnel to where you're hosting your app (`localhost` on port 3978).</span></span>

## <a name="4-configure-your-bot"></a><span data-ttu-id="c7949-146">4. configure seu bot</span><span class="sxs-lookup"><span data-stu-id="c7949-146">4. Configure your bot</span></span>

<span data-ttu-id="c7949-147">Para usar um bot no Teams, você deve registrá-lo com o serviço de bot do Azure.</span><span class="sxs-lookup"><span data-stu-id="c7949-147">To use a bot in Teams, you must register it with the Azure Bot Service.</span></span> <span data-ttu-id="c7949-148">Sorte para você, isso é feito automaticamente quando você configura seu aplicativo usando o Teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="c7949-148">Lucky for you, this is done automatically when you set up your app using the Teams Toolkit.</span></span>

<span data-ttu-id="c7949-149">Você ainda deve especificar um endereço de ponto de extremidade para receber e processar mensagens de usuário (ou seja, solicitações) enviadas ao bot.</span><span class="sxs-lookup"><span data-stu-id="c7949-149">You still must specify an endpoint address to receive and process user messages (i.e., requests) sent to the bot.</span></span> <span data-ttu-id="c7949-150">Normalmente, a URL é semelhante `https://HOST_URL/api/messages` .</span><span class="sxs-lookup"><span data-stu-id="c7949-150">Typically, the URL looks like `https://HOST_URL/api/messages`.</span></span> <span data-ttu-id="c7949-151">Você pode configurar isso rapidamente no kit de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="c7949-151">You can configure this quickly in the toolkit.</span></span>

1. No Visual Studio Code, selecione **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: na barra de atividades à esquerda e escolha **abrir o Microsoft Teams Toolkit**.
1. <span data-ttu-id="c7949-153">Vá até **Bots > registros de bot existentes** e selecione o bot que você criou durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="c7949-153">Go to **Bots > Existing bot registrations** and select the bot you created during setup.</span></span>
1. <span data-ttu-id="c7949-154">No campo **endereço do ponto de extremidade do bot** , insira a URL do ngrok (por exemplo, `https://468b9ab725e9.ngrok.io` ) em que você está hospedando o bot e anexe `/api/messages` a ela.</span><span class="sxs-lookup"><span data-stu-id="c7949-154">In the **Bot endpoint address** field, enter the ngrok URL (for example, `https://468b9ab725e9.ngrok.io`) where you're hosting the bot and append `/api/messages` to it.</span></span><br/>
    :::image type="content" source="../assets/images/build-your-first-app/bot-config-endpoint-url.png" alt-text="Ilustração mostrando onde você pode configurar a URL do ponto de extremidade do bot no kit de ferramentas do teams.":::

<span data-ttu-id="c7949-156">Seu bot poderá responder às mensagens no Teams.</span><span class="sxs-lookup"><span data-stu-id="c7949-156">Your bot will be able to respond to messages in Teams.</span></span>

## <a name="5-build-and-run-your-app"></a><span data-ttu-id="c7949-157">5. Compilar e executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="c7949-157">5. Build and run your app</span></span>

<span data-ttu-id="c7949-158">Você configurou uma URL para hospedar seu bot e configurá-la para lidar com as mensagens.</span><span class="sxs-lookup"><span data-stu-id="c7949-158">You've set up a URL to host your bot and configured it to handle messages.</span></span> <span data-ttu-id="c7949-159">É hora de colocar seu aplicativo em funcionamento.</span><span class="sxs-lookup"><span data-stu-id="c7949-159">It's time to get your app up and running.</span></span>

1. <span data-ttu-id="c7949-160">Em um terminal, vá para o diretório raiz do seu projeto de aplicativo e execute `npm install` .</span><span class="sxs-lookup"><span data-stu-id="c7949-160">In a terminal, go to the root directory of your app project and run `npm install`.</span></span>
1. <span data-ttu-id="c7949-161">Executar `npm start` .</span><span class="sxs-lookup"><span data-stu-id="c7949-161">Run `npm start`.</span></span>

<span data-ttu-id="c7949-162">Se tiver êxito, você verá a seguinte mensagem indicando que o seu bot está ouvindo a atividade no seu `localhost` :</span><span class="sxs-lookup"><span data-stu-id="c7949-162">If successful, you see the following message indicating your bot is listening for activity at your `localhost`:</span></span>

`Bot/ME service listening at http://localhost:3978`

## <a name="6-sideload-your-bot-in-teams"></a><span data-ttu-id="c7949-163">6. Sideload seu bot no Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="c7949-163">6. Sideload your bot in Teams</span></span>

<span data-ttu-id="c7949-164">Com o bot em execução, você pode instalá-lo no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="c7949-164">With your bot running, you can install it in Teams.</span></span>

> [!TIP]
> <span data-ttu-id="c7949-165">Se você ainda não suplementos foi feito um aplicativo do Microsoft Teams e tiver problemas, siga estas [instruções](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams).</span><span class="sxs-lookup"><span data-stu-id="c7949-165">If you haven't sideloaded a Teams app before and run into issues, follow these [instructions](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams).</span></span>

1. <span data-ttu-id="c7949-166">No Visual Studio Code, pressione a tecla **F5** para iniciar um cliente Web do teams.</span><span class="sxs-lookup"><span data-stu-id="c7949-166">In Visual Studio Code, press the **F5** key to launch a Teams web client.</span></span>
1. <span data-ttu-id="c7949-167">Na caixa de diálogo instalar aplicativo, selecione **Adicionar para mim**.</span><span class="sxs-lookup"><span data-stu-id="c7949-167">In the app install dialog, select **Add for me**.</span></span> <span data-ttu-id="c7949-168">(Você pode adicionar o bot a um canal ou chat, mas é menos intrusivo para que outras pessoas possam testar um bot em um chat de um em um.)</span><span class="sxs-lookup"><span data-stu-id="c7949-168">(You could add the bot to a channel or chat, but it's less intrusive to others to test a bot in a one-on-one chat.)</span></span>

## <a name="7-test-your-bot"></a><span data-ttu-id="c7949-169">7. teste seu bot</span><span class="sxs-lookup"><span data-stu-id="c7949-169">7. Test your bot</span></span>

<span data-ttu-id="c7949-170">Agora, para a parte divertida: Vamos dizer "Olá" ao seu bot.</span><span class="sxs-lookup"><span data-stu-id="c7949-170">Now for the fun part: Let's say "Hello" to your bot.</span></span>

1. <span data-ttu-id="c7949-171">Na caixa redigir, envie uma `Hello` mensagem.</span><span class="sxs-lookup"><span data-stu-id="c7949-171">In the compose box, send a `Hello` message.</span></span>

<span data-ttu-id="c7949-172">Seu bot responde com algo como a mensagem a seguir.</span><span class="sxs-lookup"><span data-stu-id="c7949-172">Your bot replies with something like the following message.</span></span>

:::image type="content" source="../assets/images/build-your-first-app/contoso-chatbot.png" alt-text="Uma captura de tela mostrando um usuário diga _OL_QUOTE_PLACEHOLDER_Olá_OL_QUOTE_PLACEHOLDER_ para um bot do Microsoft Teams e obtendo uma resposta.":::

## <a name="well-done"></a><span data-ttu-id="c7949-174">Muito bem</span><span class="sxs-lookup"><span data-stu-id="c7949-174">Well done</span></span>

<span data-ttu-id="c7949-175">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="c7949-175">Congratulations!</span></span> <span data-ttu-id="c7949-176">Você tem um bot de equipe básico que pode se comunicar com os usuários, um ou em configurações de grupo (canais e chats).</span><span class="sxs-lookup"><span data-stu-id="c7949-176">You have a basic Teams bot that can communicate with users one-on-one or in group settings (channels and chats).</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="c7949-177">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="c7949-177">Troubleshooting</span></span>

<span data-ttu-id="c7949-178">As informações a seguir podem ajudar se você tiver problemas para concluir este tutorial.</span><span class="sxs-lookup"><span data-stu-id="c7949-178">The following information may help if you had issues completing this tutorial.</span></span>

### <a name="bot-isnt-connected-to-teams"></a><span data-ttu-id="c7949-179">O bot não está conectado ao Teams</span><span class="sxs-lookup"><span data-stu-id="c7949-179">Bot isn't connected to Teams</span></span>

<span data-ttu-id="c7949-180">Se você instalou seu aplicativo, mas o bot não está funcionando, certifique-se de que o bot está [conectado ao *canal* Teams do serviço de bot do Azure](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="c7949-180">If you installed your app but the bot isn't working, make sure the bot is [connected to the Azure Bot Service's Teams *channel*](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true).</span></span>

<span data-ttu-id="c7949-181">É importante entender que isso não é o mesmo que um canal no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="c7949-181">It's important to understand that this isn't the same as a channel in Teams.</span></span> <span data-ttu-id="c7949-182">Nesse caso, um canal é como o serviço de bot do Azure conecta seu bot ao Teams ou a um [aplicativo de comunicação da Microsoft ou de terceiros com suporte](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="c7949-182">In this case, a channel is how the Azure Bot Service connects your bot to Teams or another [supported Microsoft or third-party communications app](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true).</span></span>

## <a name="learn-more"></a><span data-ttu-id="c7949-183">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="c7949-183">Learn more</span></span>

* [<span data-ttu-id="c7949-184">Veja o que mais os bots de equipe podem fazer com um de nossos exemplos</span><span class="sxs-lookup"><span data-stu-id="c7949-184">See what else Teams bots can do with one of our samples</span></span>](https://github.com/microsoft/BotBuilder-Samples#teams-samples)
* [<span data-ttu-id="c7949-185">Princípios básicos de conversas</span><span class="sxs-lookup"><span data-stu-id="c7949-185">Bot conversation basics</span></span>](../bots/how-to/conversations/conversation-basics.md)
* [<span data-ttu-id="c7949-186">Autenticação de bot no Teams</span><span class="sxs-lookup"><span data-stu-id="c7949-186">Bot authentication in Teams</span></span>](../bots/how-to/authentication/auth-flow-bot.md)
* [<span data-ttu-id="c7949-187">Microsoft bot Framework</span><span class="sxs-lookup"><span data-stu-id="c7949-187">Microsoft Bot Framework</span></span>](https://dev.botframework.com/)
* [<span data-ttu-id="c7949-188">Criar um bot sem o kit de ferramentas</span><span class="sxs-lookup"><span data-stu-id="c7949-188">Create a bot without the toolkit</span></span>](../bots/how-to/create-a-bot-for-teams.md)
