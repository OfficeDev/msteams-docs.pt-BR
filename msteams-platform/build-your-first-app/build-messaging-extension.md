---
title: Começar - Criar uma extensão de mensagens
author: girliemac
description: Crie rapidamente uma extensão Microsoft Teams de mensagens usando a Microsoft Teams Toolkit.
ms.author: timura
ms.date: 03/25/2021
ms.topic: tutorial
ms.openlocfilehash: 91a5a15697163ee9103607511047a6411a5acf1a
ms.sourcegitcommit: 303fc214aa04757779a171337f31a6539f47fd03
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2021
ms.locfileid: "52068756"
---
# <a name="build-your-first-messaging-extension-for-microsoft-teams"></a><span data-ttu-id="77a79-103">Crie sua primeira extensão de mensagens para Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="77a79-103">Build your first messaging extension for Microsoft Teams</span></span>

<span data-ttu-id="77a79-104">Há dois tipos de extensões Teams *de mensagens:* comandos [de pesquisa](../messaging-extensions/how-to/search-commands/define-search-command.md) e comandos [de ação.](../messaging-extensions/how-to/action-commands/define-action-command.md)</span><span class="sxs-lookup"><span data-stu-id="77a79-104">There are two types of Teams *messaging extensions*: [Search commands](../messaging-extensions/how-to/search-commands/define-search-command.md) and [action commands](../messaging-extensions/how-to/action-commands/define-action-command.md).</span></span>

<span data-ttu-id="77a79-105">Este tutorial ensina a criar um comando de pesquisa *(também* conhecido como extensão de mensagens baseada em pesquisa *),* que é um atalho para localizar conteúdo externo e compartilhamento no Teams.</span><span class="sxs-lookup"><span data-stu-id="77a79-105">This tutorial teaches you to create a *search command* (also known as a *search-based messaging extension*), which is a shortcut for finding external content and sharing it in Teams.</span></span> <span data-ttu-id="77a79-106">Os usuários podem acessar comandos de pesquisa Teams caixa de comando ou composição.</span><span class="sxs-lookup"><span data-stu-id="77a79-106">Users can access search commands from the Teams compose or command box.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="77a79-107">O que você aprenderá</span><span class="sxs-lookup"><span data-stu-id="77a79-107">What you'll learn</span></span>

* <span data-ttu-id="77a79-108">Crie um projeto de aplicativo e um bot de extensão de mensagens usando o Microsoft Teams Toolkit para Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="77a79-108">Create an app project and messaging extension bot using the Microsoft Teams Toolkit for Visual Studio Code.</span></span>
* <span data-ttu-id="77a79-109">Entenda as configurações do aplicativo e os scaffolding relevantes para extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="77a79-109">Understand the app configurations and the scaffolding relevant to messaging extensions.</span></span>
* <span data-ttu-id="77a79-110">Hospedar um aplicativo localmente.</span><span class="sxs-lookup"><span data-stu-id="77a79-110">Host an app locally.</span></span>
* <span data-ttu-id="77a79-111">Configure o bot para sua extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="77a79-111">Configure the bot for your messaging extension.</span></span>
* <span data-ttu-id="77a79-112">Fazer sideload e testar uma extensão de mensagens Teams.</span><span class="sxs-lookup"><span data-stu-id="77a79-112">Sideload and test a messaging extension in Teams.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="77a79-113">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="77a79-113">Prerequisites</span></span>

<span data-ttu-id="77a79-114">Certifique-se de entender como configurar e criar um aplicativo Teams simples.</span><span class="sxs-lookup"><span data-stu-id="77a79-114">Make sure that you understand how to set up and build a simple Teams app.</span></span> <span data-ttu-id="77a79-115">Para obter mais informações, [consulte create your first Microsoft Teams aplicativo "Hello, World!".](../build-your-first-app/build-and-run.md)</span><span class="sxs-lookup"><span data-stu-id="77a79-115">For more information, see [create your first Microsoft Teams "Hello, World!" app](../build-your-first-app/build-and-run.md).</span></span>

## <a name="1-create-your-app-project"></a><span data-ttu-id="77a79-116">1. Crie seu projeto de aplicativo</span><span class="sxs-lookup"><span data-stu-id="77a79-116">1. Create your app project</span></span>

<span data-ttu-id="77a79-117">A Microsoft Teams Toolkit ajuda a configurar os seguintes componentes para a extensão de mensagens:</span><span class="sxs-lookup"><span data-stu-id="77a79-117">The Microsoft Teams Toolkit helps you set up the following components for your messaging extension:</span></span>

* <span data-ttu-id="77a79-118">**Configurações de aplicativo e scaffolding relevantes** para extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="77a79-118">**App configurations and scaffolding** relevant to messaging extensions</span></span>
* <span data-ttu-id="77a79-119">**Bot** para sua extensão de mensagens que é registrada automaticamente com o serviço Microsoft Azure Bot</span><span class="sxs-lookup"><span data-stu-id="77a79-119">**Bot** for your messaging extension that's automatically registered with the Microsoft Azure Bot Service</span></span>

<span data-ttu-id="77a79-120">**Para criar seu projeto de aplicativo**</span><span class="sxs-lookup"><span data-stu-id="77a79-120">**To create your app project**</span></span>

1. Em Visual Studio Code, selecione **Microsoft Teams** barra de atividades à esquerda e escolha Criar um novo Teams :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: **app**.
1. <span data-ttu-id="77a79-122">Quando solicitado, entre com sua conta Microsoft 365 de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="77a79-122">When prompted, sign in with your Microsoft 365 development account.</span></span>
1. <span data-ttu-id="77a79-123">Na tela **Selecionar projeto,** em **Pesquisa de Extensões de**  >  **Mensagens,** clique em **JS (JavaScript)**.</span><span class="sxs-lookup"><span data-stu-id="77a79-123">On the **Select project** screen, at **Messaging Extensions** > **Search**, click **JS (JavaScript)**.</span></span> 
1. <span data-ttu-id="77a79-124">Insira um nome para seu Teams app.</span><span class="sxs-lookup"><span data-stu-id="77a79-124">Enter a name for your Teams app.</span></span> <span data-ttu-id="77a79-125">Esse é o nome padrão para seu aplicativo e também o nome do diretório do projeto do aplicativo em sua máquina local.</span><span class="sxs-lookup"><span data-stu-id="77a79-125">This is the default name for your app and also the name of the app project directory on your local machine.</span></span>
1. <span data-ttu-id="77a79-126">Selecione **Criar um novo Bot** e clique em Criar Registro **de** Bot.</span><span class="sxs-lookup"><span data-stu-id="77a79-126">Select **Create a new Bot** then click **Create Bot Registration** button.</span></span> <span data-ttu-id="77a79-127">Se tiver êxito, seu novo bot terá um status *Registrado.*</span><span class="sxs-lookup"><span data-stu-id="77a79-127">If successful, your new bot will have a *Registered* status.</span></span> <span data-ttu-id="77a79-128">Agora, seu bot é registrado automaticamente com o serviço Microsoft Azure Bot.</span><span class="sxs-lookup"><span data-stu-id="77a79-128">Now your bot is automatically registered with the Microsoft Azure Bot Service.</span></span> 
1. <span data-ttu-id="77a79-129">Selecione **Concluir** na parte inferior da tela para configurar seu projeto e salvar seu projeto em seu computador local.</span><span class="sxs-lookup"><span data-stu-id="77a79-129">Select **Finish** at the bottom of the screen to configure your project and save your project on your local machine.</span></span>

## <a name="2-understand-your-app-project-components"></a><span data-ttu-id="77a79-130">2. Entenda os componentes do projeto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="77a79-130">2. Understand your app project components</span></span>

<span data-ttu-id="77a79-131">Grande parte das configurações e scaffolding do aplicativo são configuradas automaticamente quando você cria seu projeto com o Teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="77a79-131">Much of the app configurations and scaffolding are set up automatically when you create your project with the Teams Toolkit.</span></span>

* <span data-ttu-id="77a79-132">Configurações do aplicativo: para exibir ou atualizar as configurações da extensão de mensagens, selecione **App Studio** no kit de ferramentas e acesse **Extensões de mensagens.**</span><span class="sxs-lookup"><span data-stu-id="77a79-132">App configurations: To view or update your messaging extension's configurations, select **App Studio** in the toolkit and go to **Messaging extensions**.</span></span>
* <span data-ttu-id="77a79-133">Estrutura de aplicativos: o scaffolding de aplicativo fornece um arquivo, localizado no diretório raiz do seu projeto, para manipular como sua extensão de mensagens (ou tecnicamente, o bot da extensão de mensagens ) responde às consultas de pesquisa no `botActivityHandler.js` Teams. [](#4-configure-the-bot-for-your-messaging-extension)</span><span class="sxs-lookup"><span data-stu-id="77a79-133">App scaffolding: The app scaffolding provides a `botActivityHandler.js` file, located in the root directory of your project, for handling how your messaging extension (or technically, the [messaging extension's bot](#4-configure-the-bot-for-your-messaging-extension)) responds to search queries in Teams.</span></span>

## <a name="3-set-up-a-secure-tunnel-to-your-app"></a><span data-ttu-id="77a79-134">3. Configurar um túnel seguro para seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="77a79-134">3. Set up a secure tunnel to your app</span></span>

<span data-ttu-id="77a79-135">Para fins de teste, vamos hospedar sua extensão de mensagens em um servidor Web local (porta 3978).</span><span class="sxs-lookup"><span data-stu-id="77a79-135">For testing purposes, let's host your messaging extension on a local web server (port 3978).</span></span> <span data-ttu-id="77a79-136">Você usará o [ngrok](https://ngrok.com/download) para configurar um túnel seguro para localhost.</span><span class="sxs-lookup"><span data-stu-id="77a79-136">You are going to use [ngrok](https://ngrok.com/download) to set up a secure tunnel to localhost.</span></span> <span data-ttu-id="77a79-137">Consulte [build your first bot for Microsoft Teams](../build-your-first-app/build-bot.md#3-securely-expose-your-localhost-to-the-internet) for details.</span><span class="sxs-lookup"><span data-stu-id="77a79-137">See [build your first bot for Microsoft Teams](../build-your-first-app/build-bot.md#3-securely-expose-your-localhost-to-the-internet) for details.</span></span> 

1. <span data-ttu-id="77a79-138">Caso ainda não tenha feito isso, instale [ngrok](https://ngrok.com/download).</span><span class="sxs-lookup"><span data-stu-id="77a79-138">If you haven't already, install [ngrok](https://ngrok.com/download).</span></span>
1. <span data-ttu-id="77a79-139">Em um terminal, execute `ngrok http -host-header=rewrite 3978` .</span><span class="sxs-lookup"><span data-stu-id="77a79-139">In a terminal, run `ngrok http -host-header=rewrite 3978`.</span></span>
1. <span data-ttu-id="77a79-140">Copie a URL HTTPS na saída (por exemplo, ) já que Teams `https://468b9ab725e9.ngrok.io` requer conexões HTTPS.</span><span class="sxs-lookup"><span data-stu-id="77a79-140">Copy the HTTPS URL in the output (for example, `https://468b9ab725e9.ngrok.io`) since Teams requires HTTPS connections.</span></span>

   <span data-ttu-id="77a79-141">Com essa URL, Teams (que requer conexões HTTPS) poderá túnel para onde você está hospedando seu aplicativo ( `localhost` na porta 3978).</span><span class="sxs-lookup"><span data-stu-id="77a79-141">With this URL, Teams (which requires HTTPS connections) will be able tunnel to where you're hosting your app (`localhost` on port 3978).</span></span>

## <a name="4-configure-the-bot-for-your-messaging-extension"></a><span data-ttu-id="77a79-142">4. Configure o bot para sua extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="77a79-142">4. Configure the bot for your messaging extension</span></span>

<span data-ttu-id="77a79-143">As extensões de mensagens dependem de bots para enviar e processar solicitações de usuários Teams para seu serviço hospedado.</span><span class="sxs-lookup"><span data-stu-id="77a79-143">Messaging extensions rely on bots to send and process user requests from Teams to your hosted service.</span></span> <span data-ttu-id="77a79-144">O bot deve ser registrado no Serviço bot do Azure, que foi feito quando você configura seu aplicativo usando o Teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="77a79-144">The bot must be registered with the Azure Bot Service, which was done when you set up your app using the Teams Toolkit.</span></span>

<span data-ttu-id="77a79-145">Você ainda deve especificar uma URL de ponto de extremidade de bot para receber e processar consultas de pesquisa em sua extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="77a79-145">You still must specify a bot endpoint URL to receive and process search queries in your messaging extension.</span></span> <span data-ttu-id="77a79-146">Normalmente, a URL se parece com `https://HOST_URL/api/messages` .</span><span class="sxs-lookup"><span data-stu-id="77a79-146">Typically, the URL looks like `https://HOST_URL/api/messages`.</span></span> <span data-ttu-id="77a79-147">Você pode configurar isso rapidamente no kit de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="77a79-147">You can configure this quickly in the toolkit.</span></span>

1. Em Visual Studio Code, selecione **Microsoft Teams** à esquerda da Barra de Atividades :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: e escolha Abrir **Microsoft Teams Toolkit**.
1. <span data-ttu-id="77a79-149">Vá para **Bots > registros de bot existentes** e selecione o bot que você criou durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="77a79-149">Go to **Bots > Existing bot registrations** and select the bot you created during setup.</span></span>
1. <span data-ttu-id="77a79-150">No campo **Endereço do ponto** de extremidade bot, insira a URL do ngrok (por exemplo, ) onde você está hospedando o bot e `https://468b9ab725e9.ngrok.io` adeque `/api/messages` a ele.</span><span class="sxs-lookup"><span data-stu-id="77a79-150">In the **Bot endpoint address** field, enter the ngrok URL (for example, `https://468b9ab725e9.ngrok.io`) where you're hosting the bot and append `/api/messages` to it.</span></span>

   <span data-ttu-id="77a79-151">Seu bot poderá lidar com consultas em sua extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="77a79-151">Your bot will be able to handle queries in your messaging extension.</span></span>

## <a name="5-build-and-run-your-app"></a><span data-ttu-id="77a79-152">5. Crie e execute seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="77a79-152">5. Build and run your app</span></span>

<span data-ttu-id="77a79-153">Você configurou uma URL para hospedar sua extensão de mensagens e configurá-la para lidar com pesquisas.</span><span class="sxs-lookup"><span data-stu-id="77a79-153">You've set up a URL to host your messaging extension and configured it to handle searches.</span></span> <span data-ttu-id="77a79-154">É hora de fazer o aplicativo funcionar.</span><span class="sxs-lookup"><span data-stu-id="77a79-154">It's time to get your app up and running.</span></span>

1. <span data-ttu-id="77a79-155">Abra o terminal e vá para o diretório raiz do seu projeto de aplicativo</span><span class="sxs-lookup"><span data-stu-id="77a79-155">Open terminal and go to the root directory of your app project</span></span>
1. <span data-ttu-id="77a79-156">Executar `npm install` .</span><span class="sxs-lookup"><span data-stu-id="77a79-156">Run `npm install`.</span></span>
1. <span data-ttu-id="77a79-157">Executar `npm start` .</span><span class="sxs-lookup"><span data-stu-id="77a79-157">Run `npm start`.</span></span>

   <span data-ttu-id="77a79-158">Se tiver êxito, você verá a seguinte mensagem indicando que seu serviço de extensão de mensagens está escutando atividades em seu `localhost` :</span><span class="sxs-lookup"><span data-stu-id="77a79-158">If successful, you see the following message indicating your messaging extension service is listening for activity at your `localhost`:</span></span>

   `Bot/ME service listening at http://localhost:3978`

## <a name="6-sideload-your-messaging-extension-in-teams"></a><span data-ttu-id="77a79-159">6. Fazer sideload da extensão de mensagens no Teams</span><span class="sxs-lookup"><span data-stu-id="77a79-159">6. Sideload your messaging extension in Teams</span></span>

<span data-ttu-id="77a79-160">Com a extensão de mensagens em execução, você pode instalá-la Teams.</span><span class="sxs-lookup"><span data-stu-id="77a79-160">With your messaging extension running, you can install it in Teams.</span></span>

> [!TIP]
> <span data-ttu-id="77a79-161">Se você não tiver sideloaded de um aplicativo Teams antes e tiver problemas, siga estas [instruções](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams).</span><span class="sxs-lookup"><span data-stu-id="77a79-161">If you haven't sideloaded a Teams app before and run into issues, follow these [instructions](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams).</span></span>

1. <span data-ttu-id="77a79-162">Em Visual Studio Code, selecione a **tecla F5** para iniciar um cliente Teams Web.</span><span class="sxs-lookup"><span data-stu-id="77a79-162">In Visual Studio Code, select the **F5** key to launch a Teams web client.</span></span>
1. <span data-ttu-id="77a79-163">Na caixa de diálogo de instalação do aplicativo, selecione **Adicionar para mim**.</span><span class="sxs-lookup"><span data-stu-id="77a79-163">In the app install dialog, select **Add for me**.</span></span>

## <a name="7-test-your-messaging-extension"></a><span data-ttu-id="77a79-164">7. Teste sua extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="77a79-164">7. Test your messaging extension</span></span>

<span data-ttu-id="77a79-165">Saiba como as extensões de mensagens funcionam em um Teams chat.</span><span class="sxs-lookup"><span data-stu-id="77a79-165">Learn how messaging extensions work in a Teams chat.</span></span>

1. <span data-ttu-id="77a79-166">Inicie um novo chat.</span><span class="sxs-lookup"><span data-stu-id="77a79-166">Start a new chat.</span></span> Na caixa de redação, selecione **Mais** e selecione o aplicativo de extensão de mensagens :::image type="icon" source="../assets/icons/teams-client-more.png"::: que você acabou de fazer sideload.
1. <span data-ttu-id="77a79-168">Tente pesquisar algo (por exemplo, **Tíquetes).**</span><span class="sxs-lookup"><span data-stu-id="77a79-168">Try searching for something (for example, **Tickets**).</span></span> <span data-ttu-id="77a79-169">Se seu aplicativo estiver funcionando, você verá resultados de pesquisa de exemplo (você pode adicionar seus próprios posteriormente).</span><span class="sxs-lookup"><span data-stu-id="77a79-169">If your app is working, you'll see sample search results (you can add your own later).</span></span>

   :::image type="content" source="../assets/images/build-your-first-app/me-teams-test.png" alt-text="Uma captura de tela mostrando como uma extensão de mensagens baseada em pesquisa é usada na caixa de Teams de composição.":::

## <a name="troubleshooting"></a><span data-ttu-id="77a79-171">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="77a79-171">Troubleshooting</span></span>

<span data-ttu-id="77a79-172">As informações a seguir podem ajudar se você tiver problemas ao concluir este tutorial.</span><span class="sxs-lookup"><span data-stu-id="77a79-172">The following information may help if you had issues completing this tutorial.</span></span>

<span data-ttu-id="77a79-173">**Bot não está conectado ao Teams**</span><span class="sxs-lookup"><span data-stu-id="77a79-173">**Bot isn't connected to Teams**</span></span>

<span data-ttu-id="77a79-174">Se você instalou seu aplicativo, mas ele não está funcionando, certifique-se de que o bot da extensão de mensagens esteja conectado ao canal de Teams do Serviço de Bot [do Azure. ](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="77a79-174">If you installed your app but it isn't working, make sure the messaging extension's bot is [connected to the Azure Bot Service's Teams *channel*](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true).</span></span>

<span data-ttu-id="77a79-175">É importante entender que isso não é o mesmo que um canal no Teams.</span><span class="sxs-lookup"><span data-stu-id="77a79-175">It's important to understand that this isn't the same as a channel in Teams.</span></span> <span data-ttu-id="77a79-176">Nesse caso, um canal é como o Serviço de Bot do Azure conecta seu bot ao Teams ou outro aplicativo de comunicações da Microsoft ou de terceiros com [suporte.](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="77a79-176">In this case, a channel is how the Azure Bot Service connects your bot to Teams or another [supported Microsoft or third-party communications app](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true).</span></span>

## <a name="see-also"></a><span data-ttu-id="77a79-177">Confira também</span><span class="sxs-lookup"><span data-stu-id="77a79-177">See also</span></span>

* [<span data-ttu-id="77a79-178">Teams caixa de comando ou composição</span><span class="sxs-lookup"><span data-stu-id="77a79-178">Teams compose or command box</span></span>](../messaging-extensions/what-are-messaging-extensions.md) 
* [<span data-ttu-id="77a79-179">Incluir um recurso de desfralização de link</span><span class="sxs-lookup"><span data-stu-id="77a79-179">Include a link unfurling feature</span></span>](../messaging-extensions/how-to/link-unfurling.md)
* [<span data-ttu-id="77a79-180">Diretrizes de design</span><span class="sxs-lookup"><span data-stu-id="77a79-180">Design guidelines</span></span>](../messaging-extensions/design/messaging-extension-design.md) 
* [<span data-ttu-id="77a79-181">Modelos de interface do usuário prontos para produção</span><span class="sxs-lookup"><span data-stu-id="77a79-181">Production-ready UI templates</span></span>](../concepts/design/design-teams-app-ui-templates.md) 
* [<span data-ttu-id="77a79-182">Adicionar autenticação</span><span class="sxs-lookup"><span data-stu-id="77a79-182">Add authentication</span></span>](../messaging-extensions/how-to/add-authentication.md)
* [<span data-ttu-id="77a79-183">Criar uma extensão de mensagens baseada em ação</span><span class="sxs-lookup"><span data-stu-id="77a79-183">Create an action-based messaging extension</span></span>](../messaging-extensions/how-to/action-commands/define-action-command.md)
* [<span data-ttu-id="77a79-184">Microsoft Bot Framework</span><span class="sxs-lookup"><span data-stu-id="77a79-184">Microsoft Bot Framework</span></span>](https://dev.botframework.com/)

## <a name="next-steps"></a><span data-ttu-id="77a79-185">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="77a79-185">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="77a79-186">Definir comandos de pesquisa</span><span class="sxs-lookup"><span data-stu-id="77a79-186">Define search commands</span></span>](../messaging-extensions/how-to/search-commands/define-search-command.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="77a79-187">Responder às pesquisas dos usuários</span><span class="sxs-lookup"><span data-stu-id="77a79-187">Respond to users' searches</span></span>](../messaging-extensions/how-to/search-commands/respond-to-search.md)