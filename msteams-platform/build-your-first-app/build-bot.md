---
title: Começar - Criar um bot
author: heath-hamilton
description: Crie rapidamente um bot do Microsoft Teams usando o Kit de Ferramentas do Microsoft Teams.
ms.author: lajanuar
ms.date: 11/04/2020
ms.topic: tutorial
ms.openlocfilehash: 3e07c148e1b03431dc419a4e3679abac0229ff72
ms.sourcegitcommit: e08f309f62db2cf0f505f2aadfe728e5b46c17a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "50140465"
---
# <a name="build-a-bot-for-microsoft-teams"></a><span data-ttu-id="f1d05-103">Criar um bot para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="f1d05-103">Build a bot for Microsoft Teams</span></span>

<span data-ttu-id="f1d05-104">Você criará um aplicativo *de bot* básico neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="f1d05-104">You'll build a basic *bot* app in this tutorial.</span></span> <span data-ttu-id="f1d05-105">Um bot age como um intermediário entre os usuários do Teams e seu serviço Web.</span><span class="sxs-lookup"><span data-stu-id="f1d05-105">A bot acts as an intermediary between Teams users and your web service.</span></span> <span data-ttu-id="f1d05-106">As pessoas podem conversar com um bot para obter informações rapidamente ou iniciar fluxos de trabalho e tarefas executadas pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="f1d05-106">People can chat with a bot to quickly get information or initiate workflows and tasks performed by your service.</span></span>

## <a name="your-assignment"></a><span data-ttu-id="f1d05-107">Sua atribuição</span><span class="sxs-lookup"><span data-stu-id="f1d05-107">Your assignment</span></span>

<span data-ttu-id="f1d05-108">Seu local de trabalho criou um aplicativo do Teams que usa [guias para](../build-your-first-app/build-personal-tab.md) destacar informações importantes de contato.</span><span class="sxs-lookup"><span data-stu-id="f1d05-108">Your workplace created a Teams app that uses [tabs](../build-your-first-app/build-personal-tab.md) to surface important contact information.</span></span> <span data-ttu-id="f1d05-109">Por exemplo, colegas têm acesso rápido ao número de telefone do help desk.</span><span class="sxs-lookup"><span data-stu-id="f1d05-109">For example, colleagues have quick access to the help desk phone number.</span></span> <span data-ttu-id="f1d05-110">Mas, em vez de chamar, e se as pessoas pudessem entrar em contato com o help desk usando um chatbot?</span><span class="sxs-lookup"><span data-stu-id="f1d05-110">But instead of calling, what if people could contact the help desk using a chatbot?</span></span> <span data-ttu-id="f1d05-111">Seu chefe solicita que você veja com que rapidez você pode fazer com que um bot de conversa básica seja executado no Teams.</span><span class="sxs-lookup"><span data-stu-id="f1d05-111">Your boss asks you to look at how quickly you can get a basic conversational bot up and running in Teams.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="f1d05-112">O que você aprenderá</span><span class="sxs-lookup"><span data-stu-id="f1d05-112">What you'll learn</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="f1d05-113">Criar um projeto de aplicativo e um bot usando o Kit de Ferramentas do Microsoft Teams para Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="f1d05-113">Create an app project and bot using the Microsoft Teams Toolkit for Visual Studio Code</span></span>
> * <span data-ttu-id="f1d05-114">Identificar algumas das configurações do aplicativo e a scaffolding relevante para bots</span><span class="sxs-lookup"><span data-stu-id="f1d05-114">Identify some of the app configurations and scaffolding relevant to bots</span></span>
> * <span data-ttu-id="f1d05-115">Hospedar um aplicativo localmente</span><span class="sxs-lookup"><span data-stu-id="f1d05-115">Host an app locally</span></span>
> * <span data-ttu-id="f1d05-116">Configurar um bot para o Teams</span><span class="sxs-lookup"><span data-stu-id="f1d05-116">Configure a bot for Teams</span></span>
> * <span data-ttu-id="f1d05-117">Fazer sideload e testar um bot no Teams</span><span class="sxs-lookup"><span data-stu-id="f1d05-117">Sideload and test a bot in Teams</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="f1d05-118">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="f1d05-118">Before you begin</span></span>

<span data-ttu-id="f1d05-119">Se você ainda não o fez, entenda e instale os pré-requisitos de desenvolvimento [do Teams.](build-first-app-overview.md#get-prerequisites)</span><span class="sxs-lookup"><span data-stu-id="f1d05-119">If you haven't yet, make sure you [understand and install the Teams development prerequisites](build-first-app-overview.md#get-prerequisites).</span></span>

## <a name="1-create-your-app-project"></a><span data-ttu-id="f1d05-120">1. Crie seu projeto de aplicativo</span><span class="sxs-lookup"><span data-stu-id="f1d05-120">1. Create your app project</span></span>

<span data-ttu-id="f1d05-121">O Microsoft Teams Toolkit ajuda você a configurar os seguintes componentes para seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="f1d05-121">The Microsoft Teams Toolkit helps you set up the following components for your app:</span></span>

* <span data-ttu-id="f1d05-122">**Configurações de aplicativos e scaffolding** relevantes para bots</span><span class="sxs-lookup"><span data-stu-id="f1d05-122">**App configurations and scaffolding** relevant to bots</span></span>
* <span data-ttu-id="f1d05-123">**Bot** que é registrado automaticamente com o Serviço de Bot do Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="f1d05-123">**Bot** that's automatically registered with the Microsoft Azure Bot Service</span></span>

> [!TIP]
> <span data-ttu-id="f1d05-124">Se você ainda não criou um projeto de aplicativo do [](../build-your-first-app/build-and-run.md) Teams antes, talvez seja útil seguir estas instruções que explicam os projetos com mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="f1d05-124">If you haven't created a Teams app project before, you might find it helpful to follow [these instructions](../build-your-first-app/build-and-run.md) that explain projects in more detail.</span></span>

1. No Visual Studio Code, selecione **o Microsoft Teams** na Barra de Atividades à esquerda e escolha Criar um novo aplicativo do :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: **Teams.**
1. <span data-ttu-id="f1d05-126">Quando solicitado, entre com sua conta de desenvolvimento do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="f1d05-126">When prompted, sign in with your Microsoft 365 development account.</span></span>
1. <span data-ttu-id="f1d05-127">Na tela **Adicionar recursos,** selecione **Bot** e **Next.**</span><span class="sxs-lookup"><span data-stu-id="f1d05-127">On the **Add capabilities** screen, select **Bot** then **Next**.</span></span>
1. <span data-ttu-id="f1d05-128">Insira um nome para seu aplicativo do Teams.</span><span class="sxs-lookup"><span data-stu-id="f1d05-128">Enter a name for your Teams app.</span></span> <span data-ttu-id="f1d05-129">(Esse é o nome padrão para seu aplicativo e também o nome do diretório do projeto do aplicativo em seu computador local.)</span><span class="sxs-lookup"><span data-stu-id="f1d05-129">(This is the default name for your app and also the name of the app project directory on your local machine.)</span></span>
1. <span data-ttu-id="f1d05-130">Vá para **Configurar bot e** selecione Criar um novo **Bot** e Criar Registro **de Bot.**</span><span class="sxs-lookup"><span data-stu-id="f1d05-130">Go to **Configure bot** and select **Create a new Bot** then **Create Bot Registration**.</span></span> <span data-ttu-id="f1d05-131">Se bem-sucedido, seu novo bot terá um status **registrado.**</span><span class="sxs-lookup"><span data-stu-id="f1d05-131">If successful, your new bot will have a **Registered** status.</span></span>
1. <span data-ttu-id="f1d05-132">Selecione **Concluir** na parte inferior da tela e escolha um local para criar seu projeto.</span><span class="sxs-lookup"><span data-stu-id="f1d05-132">Select **Finish** at the bottom of the screen and choose a location to create your project.</span></span>

## <a name="2-identify-relevant-app-project-components"></a><span data-ttu-id="f1d05-133">2. Identifique componentes relevantes do projeto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="f1d05-133">2. Identify relevant app project components</span></span>

<span data-ttu-id="f1d05-134">Grande parte das configurações e da scaffolding do aplicativo é configurada automaticamente quando você cria seu projeto com o Kit de Ferramentas do Teams.</span><span class="sxs-lookup"><span data-stu-id="f1d05-134">Much of the app configurations and scaffolding are set up automatically when you create your project with the Teams Toolkit.</span></span> <span data-ttu-id="f1d05-135">Vejamos os componentes principais para a criação de um bot.</span><span class="sxs-lookup"><span data-stu-id="f1d05-135">Let's look at the main components for building a bot.</span></span>

### <a name="app-configurations"></a><span data-ttu-id="f1d05-136">Configurações do aplicativo</span><span class="sxs-lookup"><span data-stu-id="f1d05-136">App configurations</span></span>

<span data-ttu-id="f1d05-137">Para exibir ou atualizar as configurações do bot, selecione **App Studio** no kit de ferramentas e vá para **Bots.**</span><span class="sxs-lookup"><span data-stu-id="f1d05-137">To view or update your bot's configurations, select **App Studio** in the toolkit and go to **Bots**.</span></span>

### <a name="app-scaffolding"></a><span data-ttu-id="f1d05-138">Scaffolding de aplicativos</span><span class="sxs-lookup"><span data-stu-id="f1d05-138">App scaffolding</span></span>

<span data-ttu-id="f1d05-139">O scaffolding do aplicativo fornece um arquivo, localizado no diretório raiz do seu projeto, para manipular como o bot processa as atividades no Teams (por exemplo, como o bot responde a mensagens `botActivityHandler.js` específicas, como "Hello").</span><span class="sxs-lookup"><span data-stu-id="f1d05-139">The app scaffolding provides a `botActivityHandler.js` file, located in the root directory of your project, for handling how your bot processes activities in Teams (for example, how the bot responds to specific messages such as "Hello").</span></span>

## <a name="3-set-up-a-secure-tunnel-to-your-app"></a><span data-ttu-id="f1d05-140">3. Configurar um túnel seguro para seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="f1d05-140">3. Set up a secure tunnel to your app</span></span>

<span data-ttu-id="f1d05-141">Para fins de teste, vamos hospedar seu aplicativo em um servidor Web local (porta 3978).</span><span class="sxs-lookup"><span data-stu-id="f1d05-141">For testing purposes, let's host your app on a local web server (port 3978).</span></span>

1. <span data-ttu-id="f1d05-142">Caso ainda não tenha feito isso, instale [o ngrok.](https://ngrok.com/download)</span><span class="sxs-lookup"><span data-stu-id="f1d05-142">If you haven't already, install [ngrok](https://ngrok.com/download).</span></span>
1. <span data-ttu-id="f1d05-143">Em um terminal, execute `ngrok http -host-header=rewrite 3978` .</span><span class="sxs-lookup"><span data-stu-id="f1d05-143">In a terminal, run `ngrok http -host-header=rewrite 3978`.</span></span>
1. <span data-ttu-id="f1d05-144">Copie a URL HTTPS na saída (por exemplo, ) já que o `https://468b9ab725e9.ngrok.io` Teams requer conexões HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f1d05-144">Copy the HTTPS URL in the output (for example, `https://468b9ab725e9.ngrok.io`) since Teams requires HTTPS connections.</span></span>

<span data-ttu-id="f1d05-145">Com essa URL, o Teams (que requer conexões HTTPS) poderá usar o túnel para onde você está hospedando seu aplicativo `localhost` (na porta 3978).</span><span class="sxs-lookup"><span data-stu-id="f1d05-145">With this URL, Teams (which requires HTTPS connections) will be able tunnel to where you're hosting your app (`localhost` on port 3978).</span></span>

## <a name="4-configure-your-bot"></a><span data-ttu-id="f1d05-146">4. Configure seu bot</span><span class="sxs-lookup"><span data-stu-id="f1d05-146">4. Configure your bot</span></span>

<span data-ttu-id="f1d05-147">Para usar um bot no Teams, você deve registrá-lo com o Serviço de Bot do Azure.</span><span class="sxs-lookup"><span data-stu-id="f1d05-147">To use a bot in Teams, you must register it with the Azure Bot Service.</span></span> <span data-ttu-id="f1d05-148">Para você, isso é feito automaticamente quando você configura seu aplicativo usando o Kit de Ferramentas do Teams.</span><span class="sxs-lookup"><span data-stu-id="f1d05-148">Lucky for you, this is done automatically when you set up your app using the Teams Toolkit.</span></span>

<span data-ttu-id="f1d05-149">Você ainda deve especificar um endereço de ponto de extremidade para receber e processar mensagens do usuário (ou seja, solicitações) enviadas para o bot.</span><span class="sxs-lookup"><span data-stu-id="f1d05-149">You still must specify an endpoint address to receive and process user messages (i.e., requests) sent to the bot.</span></span> <span data-ttu-id="f1d05-150">Normalmente, a URL tem a `https://HOST_URL/api/messages` aparência.</span><span class="sxs-lookup"><span data-stu-id="f1d05-150">Typically, the URL looks like `https://HOST_URL/api/messages`.</span></span> <span data-ttu-id="f1d05-151">Você pode configurar isso rapidamente no kit de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="f1d05-151">You can configure this quickly in the toolkit.</span></span>

1. No Visual Studio Code, selecione **o Microsoft Teams na** Barra de Atividades à esquerda e escolha Abrir o Kit de Ferramentas do Microsoft :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: **Teams.**
1. <span data-ttu-id="f1d05-153">Vá para **Bots > registros de bot existentes** e selecione o bot que você criou durante a configuração.</span><span class="sxs-lookup"><span data-stu-id="f1d05-153">Go to **Bots > Existing bot registrations** and select the bot you created during setup.</span></span>
1. <span data-ttu-id="f1d05-154">No campo **de endereço do ponto** de extremidade bot, insira a URL ngrok (por exemplo, ) onde você está hospedando o bot e `https://468b9ab725e9.ngrok.io` `/api/messages` anexar a ele.</span><span class="sxs-lookup"><span data-stu-id="f1d05-154">In the **Bot endpoint address** field, enter the ngrok URL (for example, `https://468b9ab725e9.ngrok.io`) where you're hosting the bot and append `/api/messages` to it.</span></span><br/>
    :::image type="content" source="../assets/images/build-your-first-app/bot-config-endpoint-url.png" alt-text="Ilustração mostrando onde você pode configurar a URL do ponto de extremidade do bot no Kit de Ferramentas do Teams.":::

<span data-ttu-id="f1d05-156">Seu bot poderá responder a mensagens no Teams.</span><span class="sxs-lookup"><span data-stu-id="f1d05-156">Your bot will be able to respond to messages in Teams.</span></span>

## <a name="5-build-and-run-your-app"></a><span data-ttu-id="f1d05-157">5. Crie e execute seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="f1d05-157">5. Build and run your app</span></span>

<span data-ttu-id="f1d05-158">Você configurou uma URL para hospedar seu bot e configurou-a para manipular mensagens.</span><span class="sxs-lookup"><span data-stu-id="f1d05-158">You've set up a URL to host your bot and configured it to handle messages.</span></span> <span data-ttu-id="f1d05-159">É hora de começar a trabalhar com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f1d05-159">It's time to get your app up and running.</span></span>

1. <span data-ttu-id="f1d05-160">Em um terminal, vá para o diretório raiz do seu projeto de aplicativo e `npm install` execute.</span><span class="sxs-lookup"><span data-stu-id="f1d05-160">In a terminal, go to the root directory of your app project and run `npm install`.</span></span>
1. <span data-ttu-id="f1d05-161">Executar `npm start` .</span><span class="sxs-lookup"><span data-stu-id="f1d05-161">Run `npm start`.</span></span>

<span data-ttu-id="f1d05-162">Se bem-sucedido, você verá a seguinte mensagem indicando que seu bot está escutando atividades em `localhost` seu:</span><span class="sxs-lookup"><span data-stu-id="f1d05-162">If successful, you see the following message indicating your bot is listening for activity at your `localhost`:</span></span>

`Bot/ME service listening at http://localhost:3978`

## <a name="6-sideload-your-bot-in-teams"></a><span data-ttu-id="f1d05-163">6. Fazer sideload do seu bot no Teams</span><span class="sxs-lookup"><span data-stu-id="f1d05-163">6. Sideload your bot in Teams</span></span>

<span data-ttu-id="f1d05-164">Com o bot em execução, você pode instalá-lo no Teams.</span><span class="sxs-lookup"><span data-stu-id="f1d05-164">With your bot running, you can install it in Teams.</span></span>

> [!TIP]
> <span data-ttu-id="f1d05-165">Se você ainda não tiver sideloaded de um aplicativo do Teams antes e tiver problemas, siga estas [instruções.](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams)</span><span class="sxs-lookup"><span data-stu-id="f1d05-165">If you haven't sideloaded a Teams app before and run into issues, follow these [instructions](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams).</span></span>

1. <span data-ttu-id="f1d05-166">No Visual Studio Code, pressione a **tecla F5** para iniciar um cliente Web do Teams.</span><span class="sxs-lookup"><span data-stu-id="f1d05-166">In Visual Studio Code, press the **F5** key to launch a Teams web client.</span></span>
1. <span data-ttu-id="f1d05-167">Na caixa de diálogo de instalação do aplicativo, selecione **Adicionar para mim.**</span><span class="sxs-lookup"><span data-stu-id="f1d05-167">In the app install dialog, select **Add for me**.</span></span> <span data-ttu-id="f1d05-168">(Você pode adicionar o bot a um canal ou chat, mas é menos intrusivo para outras pessoas testar um bot em um chat um-para-um.)</span><span class="sxs-lookup"><span data-stu-id="f1d05-168">(You could add the bot to a channel or chat, but it's less intrusive to others to test a bot in a one-on-one chat.)</span></span>

## <a name="7-test-your-bot"></a><span data-ttu-id="f1d05-169">7. Teste seu bot</span><span class="sxs-lookup"><span data-stu-id="f1d05-169">7. Test your bot</span></span>

<span data-ttu-id="f1d05-170">Agora, para a parte divertida: vamos dizer "Hello" para seu bot.</span><span class="sxs-lookup"><span data-stu-id="f1d05-170">Now for the fun part: Let's say "Hello" to your bot.</span></span>

1. <span data-ttu-id="f1d05-171">Na caixa de redação, envie uma `Hello` mensagem.</span><span class="sxs-lookup"><span data-stu-id="f1d05-171">In the compose box, send a `Hello` message.</span></span>

<span data-ttu-id="f1d05-172">Seu bot responde com algo parecido com a seguinte mensagem.</span><span class="sxs-lookup"><span data-stu-id="f1d05-172">Your bot replies with something like the following message.</span></span>

:::image type="content" source="../assets/images/build-your-first-app/contoso-chatbot.png" alt-text="Uma captura de tela mostrando um usuário dizendo &quot;Hello&quot; para um bot do Teams e recebendo uma resposta.":::

## <a name="well-done"></a><span data-ttu-id="f1d05-174">Bem feito</span><span class="sxs-lookup"><span data-stu-id="f1d05-174">Well done</span></span>

<span data-ttu-id="f1d05-175">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="f1d05-175">Congratulations!</span></span> <span data-ttu-id="f1d05-176">Você tem um bot básico do Teams que pode se comunicar com usuários um a um ou em configurações de grupo (canais e chats).</span><span class="sxs-lookup"><span data-stu-id="f1d05-176">You have a basic Teams bot that can communicate with users one-on-one or in group settings (channels and chats).</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="f1d05-177">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="f1d05-177">Troubleshooting</span></span>

<span data-ttu-id="f1d05-178">As informações a seguir podem ajudar se você tiver problemas para concluir este tutorial.</span><span class="sxs-lookup"><span data-stu-id="f1d05-178">The following information may help if you had issues completing this tutorial.</span></span>

### <a name="bot-isnt-connected-to-teams"></a><span data-ttu-id="f1d05-179">O bot não está conectado ao Teams</span><span class="sxs-lookup"><span data-stu-id="f1d05-179">Bot isn't connected to Teams</span></span>

<span data-ttu-id="f1d05-180">Se você instalou seu aplicativo, mas o bot não está funcionando, certifique-se de que o bot está conectado ao canal do Teams do Serviço de Bot do [Azure. ](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="f1d05-180">If you installed your app but the bot isn't working, make sure the bot is [connected to the Azure Bot Service's Teams *channel*](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true).</span></span>

<span data-ttu-id="f1d05-181">É importante entender que isso não é o mesmo que um canal no Teams.</span><span class="sxs-lookup"><span data-stu-id="f1d05-181">It's important to understand that this isn't the same as a channel in Teams.</span></span> <span data-ttu-id="f1d05-182">Nesse caso, um canal é como o Serviço de Bot do Azure conecta seu bot ao Teams ou a outro aplicativo de comunicação com suporte da Microsoft ou de [terceiros.](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="f1d05-182">In this case, a channel is how the Azure Bot Service connects your bot to Teams or another [supported Microsoft or third-party communications app](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true).</span></span>

## <a name="learn-more"></a><span data-ttu-id="f1d05-183">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="f1d05-183">Learn more</span></span>

* [<span data-ttu-id="f1d05-184">Veja o que mais os bots do Teams podem fazer com um de nossos exemplos</span><span class="sxs-lookup"><span data-stu-id="f1d05-184">See what else Teams bots can do with one of our samples</span></span>](https://github.com/microsoft/BotBuilder-Samples#teams-samples)
* [<span data-ttu-id="f1d05-185">Princípios básicos de conversas</span><span class="sxs-lookup"><span data-stu-id="f1d05-185">Bot conversation basics</span></span>](../bots/how-to/conversations/conversation-basics.md)
* <span data-ttu-id="f1d05-186">Siga nossas [diretrizes de design](../bots/design/bots.md) e crie com modelos de interface do usuário prontos para [produção](../concepts/design/design-teams-app-ui-templates.md) para criar uma experiência perfeita.</span><span class="sxs-lookup"><span data-stu-id="f1d05-186">Follow our [design guidelines](../bots/design/bots.md) and build with [production-ready UI templates](../concepts/design/design-teams-app-ui-templates.md) to create a seamless experience.</span></span>
* [<span data-ttu-id="f1d05-187">Autenticação de bot no Teams</span><span class="sxs-lookup"><span data-stu-id="f1d05-187">Bot authentication in Teams</span></span>](../bots/how-to/authentication/auth-flow-bot.md)
* [<span data-ttu-id="f1d05-188">Microsoft Bot Framework</span><span class="sxs-lookup"><span data-stu-id="f1d05-188">Microsoft Bot Framework</span></span>](https://dev.botframework.com/)
* [<span data-ttu-id="f1d05-189">Criar um bot sem o kit de ferramentas</span><span class="sxs-lookup"><span data-stu-id="f1d05-189">Create a bot without the toolkit</span></span>](../resources/bot-v3/bots-create.md)
