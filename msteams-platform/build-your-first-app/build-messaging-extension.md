---
title: Comece - Construa uma extensão de mensagens
author: girliemac
description: Crie rapidamente uma extensão de mensagens Microsoft Teams usando o Microsoft Teams Toolkit.
ms.author: timura
ms.date: 03/25/2021
ms.topic: tutorial
ms.openlocfilehash: c120a5b5d878c549cde008c3e1ccc71743a4e24f
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566058"
---
# <a name="build-your-first-messaging-extension-for-microsoft-teams"></a><span data-ttu-id="ac934-103">Construa sua primeira extensão de mensagens para Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="ac934-103">Build your first messaging extension for Microsoft Teams</span></span>

<span data-ttu-id="ac934-104">Existem dois tipos de *extensões* de mensagens Teams: [comandos de pesquisa](../messaging-extensions/how-to/search-commands/define-search-command.md) e [comandos de ação](../messaging-extensions/how-to/action-commands/define-action-command.md).</span><span class="sxs-lookup"><span data-stu-id="ac934-104">There are two types of Teams *messaging extensions*: [Search commands](../messaging-extensions/how-to/search-commands/define-search-command.md) and [action commands](../messaging-extensions/how-to/action-commands/define-action-command.md).</span></span>

<span data-ttu-id="ac934-105">Este tutorial ensina você a criar um *comando de pesquisa* (também conhecido como *extensão de mensagens baseada em pesquisa),* que é um atalho para encontrar conteúdo externo e compartilhá-lo em Teams.</span><span class="sxs-lookup"><span data-stu-id="ac934-105">This tutorial teaches you to create a *search command* (also known as a *search-based messaging extension*), which is a shortcut for finding external content and sharing it in Teams.</span></span> <span data-ttu-id="ac934-106">Os usuários podem acessar comandos de pesquisa da Teams compor ou caixa de comando.</span><span class="sxs-lookup"><span data-stu-id="ac934-106">Users can access search commands from the Teams compose or command box.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="ac934-107">O que você vai aprender</span><span class="sxs-lookup"><span data-stu-id="ac934-107">What you'll learn</span></span>

* <span data-ttu-id="ac934-108">Crie um robô de extensão de projeto de aplicativo e de gerenciamento de mensagens usando o Microsoft Teams Toolkit para Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="ac934-108">Create an app project and messaging extension bot using the Microsoft Teams Toolkit for Visual Studio Code.</span></span>
* <span data-ttu-id="ac934-109">Entenda as configurações do aplicativo e os andaimes relevantes para as extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="ac934-109">Understand the app configurations and the scaffolding relevant to messaging extensions.</span></span>
* <span data-ttu-id="ac934-110">Hospede um aplicativo localmente.</span><span class="sxs-lookup"><span data-stu-id="ac934-110">Host an app locally.</span></span>
* <span data-ttu-id="ac934-111">Configure o bot para sua extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="ac934-111">Configure the bot for your messaging extension.</span></span>
* <span data-ttu-id="ac934-112">Sideload e teste uma extensão de mensagens em Teams.</span><span class="sxs-lookup"><span data-stu-id="ac934-112">Sideload and test a messaging extension in Teams.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ac934-113">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="ac934-113">Prerequisites</span></span>

<span data-ttu-id="ac934-114">Certifique-se de entender como configurar e construir um aplicativo de Teams simples.</span><span class="sxs-lookup"><span data-stu-id="ac934-114">Make sure that you understand how to set up and build a simple Teams app.</span></span> <span data-ttu-id="ac934-115">Para obter mais informações, consulte [criar seu primeiro Microsoft Teams aplicativo "Hello, World!".](../build-your-first-app/build-and-run.md)</span><span class="sxs-lookup"><span data-stu-id="ac934-115">For more information, see [create your first Microsoft Teams "Hello, World!" app](../build-your-first-app/build-and-run.md).</span></span>

## <a name="1-create-your-app-project"></a><span data-ttu-id="ac934-116">1. Crie seu projeto de aplicativo</span><span class="sxs-lookup"><span data-stu-id="ac934-116">1. Create your app project</span></span>

<span data-ttu-id="ac934-117">O Microsoft Teams Toolkit ajuda a configurar os seguintes componentes para sua extensão de mensagens:</span><span class="sxs-lookup"><span data-stu-id="ac934-117">The Microsoft Teams Toolkit helps you set up the following components for your messaging extension:</span></span>

* <span data-ttu-id="ac934-118">**Configurações de aplicativos e andaimes** relevantes para extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="ac934-118">**App configurations and scaffolding** relevant to messaging extensions.</span></span>
* <span data-ttu-id="ac934-119">**Bot** para sua extensão de mensagens que é automaticamente registrado no serviço de Microsoft Azure Bot.</span><span class="sxs-lookup"><span data-stu-id="ac934-119">**Bot** for your messaging extension that's automatically registered with the Microsoft Azure Bot Service.</span></span>

<span data-ttu-id="ac934-120">**Para criar seu projeto de aplicativo**</span><span class="sxs-lookup"><span data-stu-id="ac934-120">**To create your app project**</span></span>

1. Em Visual Studio Code, selecione **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: na Barra de Atividades esquerda e escolha **Criar um novo aplicativo de Teams**.
1. <span data-ttu-id="ac934-122">Quando solicitado, faça login com sua conta de desenvolvimento Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="ac934-122">When prompted, sign in with your Microsoft 365 development account.</span></span>
1. <span data-ttu-id="ac934-123">Na tela do **projeto Select,** na Pesquisa **de Extensões de Mensagens,** clique em  >   **JS (JavaScript)**.</span><span class="sxs-lookup"><span data-stu-id="ac934-123">On the **Select project** screen, at **Messaging Extensions** > **Search**, click **JS (JavaScript)**.</span></span> 
1. <span data-ttu-id="ac934-124">Digite um nome para o aplicativo Teams.</span><span class="sxs-lookup"><span data-stu-id="ac934-124">Enter a name for your Teams app.</span></span> <span data-ttu-id="ac934-125">Este é o nome padrão do seu aplicativo e também o nome do diretório de projetos do aplicativo em sua máquina local.</span><span class="sxs-lookup"><span data-stu-id="ac934-125">This is the default name for your app and also the name of the app project directory on your local machine.</span></span>
1. <span data-ttu-id="ac934-126">Selecione **Criar um novo Bot** e clique em Criar registro de **bot.**</span><span class="sxs-lookup"><span data-stu-id="ac934-126">Select **Create a new Bot** then click **Create Bot Registration** button.</span></span> <span data-ttu-id="ac934-127">Se for bem sucedido, seu novo bot terá um *status registrado.*</span><span class="sxs-lookup"><span data-stu-id="ac934-127">If successful, your new bot will have a *Registered* status.</span></span> <span data-ttu-id="ac934-128">Agora, seu bot está automaticamente registrado no serviço de Microsoft Azure Bot.</span><span class="sxs-lookup"><span data-stu-id="ac934-128">Now your bot is automatically registered with the Microsoft Azure Bot Service.</span></span> 
1. <span data-ttu-id="ac934-129">Selecione **Concluir** na parte inferior da tela para configurar seu projeto e salvar seu projeto em sua máquina local.</span><span class="sxs-lookup"><span data-stu-id="ac934-129">Select **Finish** at the bottom of the screen to configure your project and save your project on your local machine.</span></span>

## <a name="2-understand-your-app-project-components"></a><span data-ttu-id="ac934-130">2. Entenda os componentes do projeto do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="ac934-130">2. Understand your app project components</span></span>

<span data-ttu-id="ac934-131">Muitas das configurações e andaimes do aplicativo são configuradas automaticamente quando você cria seu projeto com o Teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="ac934-131">Much of the app configurations and scaffolding are set up automatically when you create your project with the Teams Toolkit.</span></span>

* <span data-ttu-id="ac934-132">Configurações do aplicativo: Para visualizar ou atualizar as configurações da extensão de mensagens, selecione **App Studio** no kit de ferramentas e vá para **extensões de mensagens**.</span><span class="sxs-lookup"><span data-stu-id="ac934-132">App configurations: To view or update your messaging extension's configurations, select **App Studio** in the toolkit and go to **Messaging extensions**.</span></span>
* <span data-ttu-id="ac934-133">Andaimes de aplicativos: O andaime do aplicativo fornece um `botActivityHandler.js` arquivo, localizado no diretório raiz do seu projeto, para lidar com como sua extensão de mensagens (ou tecnicamente, o [bot da extensão de mensagens](#4-configure-the-bot-for-your-messaging-extension)) responde a consultas de pesquisa em Teams.</span><span class="sxs-lookup"><span data-stu-id="ac934-133">App scaffolding: The app scaffolding provides a `botActivityHandler.js` file, located in the root directory of your project, for handling how your messaging extension (or technically, the [messaging extension's bot](#4-configure-the-bot-for-your-messaging-extension)) responds to search queries in Teams.</span></span>

## <a name="3-set-up-a-secure-tunnel-to-your-app"></a><span data-ttu-id="ac934-134">3. Configure um túnel seguro para o seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="ac934-134">3. Set up a secure tunnel to your app</span></span>

<span data-ttu-id="ac934-135">Para fins de teste, vamos hospedar sua extensão de mensagens em um servidor web local (porta 3978).</span><span class="sxs-lookup"><span data-stu-id="ac934-135">For testing purposes, let's host your messaging extension on a local web server (port 3978).</span></span> <span data-ttu-id="ac934-136">Você vai usar [ngrok](https://ngrok.com/download) para montar um túnel seguro para o localhost.</span><span class="sxs-lookup"><span data-stu-id="ac934-136">You are going to use [ngrok](https://ngrok.com/download) to set up a secure tunnel to localhost.</span></span> <span data-ttu-id="ac934-137">Consulte [construir seu primeiro bot para Microsoft Teams](../build-your-first-app/build-bot.md#3-securely-expose-your-localhost-to-the-internet) para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="ac934-137">See [build your first bot for Microsoft Teams](../build-your-first-app/build-bot.md#3-securely-expose-your-localhost-to-the-internet) for details.</span></span> 

1. <span data-ttu-id="ac934-138">Se você ainda não fez isso, instale [ngrok](https://ngrok.com/download).</span><span class="sxs-lookup"><span data-stu-id="ac934-138">If you haven't already, install [ngrok](https://ngrok.com/download).</span></span>
1. <span data-ttu-id="ac934-139">Em um terminal, `ngrok http -host-header=rewrite 3978` corra.</span><span class="sxs-lookup"><span data-stu-id="ac934-139">In a terminal, run `ngrok http -host-header=rewrite 3978`.</span></span>
1. <span data-ttu-id="ac934-140">Copie a URL HTTPS na saída (por `https://468b9ab725e9.ngrok.io` exemplo), já que Teams requer conexões HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ac934-140">Copy the HTTPS URL in the output (for example, `https://468b9ab725e9.ngrok.io`) since Teams requires HTTPS connections.</span></span>

   <span data-ttu-id="ac934-141">Com esta URL, Teams (que requer conexões HTTPS) será capaz de túnel para onde você está hospedando seu aplicativo ( `localhost` na porta 3978).</span><span class="sxs-lookup"><span data-stu-id="ac934-141">With this URL, Teams (which requires HTTPS connections) will be able tunnel to where you're hosting your app (`localhost` on port 3978).</span></span>

## <a name="4-configure-the-bot-for-your-messaging-extension"></a><span data-ttu-id="ac934-142">4. Configure o bot para sua extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="ac934-142">4. Configure the bot for your messaging extension</span></span>

<span data-ttu-id="ac934-143">As extensões de mensagens dependem de bots para enviar e processar solicitações de usuários de Teams para o seu serviço hospedado.</span><span class="sxs-lookup"><span data-stu-id="ac934-143">Messaging extensions rely on bots to send and process user requests from Teams to your hosted service.</span></span> <span data-ttu-id="ac934-144">O bot deve ser registrado no Azure Bot Service, que foi feito quando você configurar seu aplicativo usando o Teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="ac934-144">The bot must be registered with the Azure Bot Service, which was done when you set up your app using the Teams Toolkit.</span></span>

<span data-ttu-id="ac934-145">Você ainda deve especificar uma URL de ponto final do bot para receber e processar consultas de pesquisa na extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="ac934-145">You still must specify a bot endpoint URL to receive and process search queries in your messaging extension.</span></span> <span data-ttu-id="ac934-146">Normalmente, a URL se parece `https://HOST_URL/api/messages` com .</span><span class="sxs-lookup"><span data-stu-id="ac934-146">Typically, the URL looks like `https://HOST_URL/api/messages`.</span></span> <span data-ttu-id="ac934-147">Você pode configurar isso rapidamente no kit de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="ac934-147">You can configure this quickly in the toolkit.</span></span>

1. Em Visual Studio Code, selecione **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: na Barra de Atividades esquerda e escolha Open **Microsoft Teams Toolkit**.
1. <span data-ttu-id="ac934-149">Vá para **Bots > registros de bot existentes** e selecione o bot que você criou durante a configuração.</span><span class="sxs-lookup"><span data-stu-id="ac934-149">Go to **Bots > Existing bot registrations** and select the bot you created during setup.</span></span>
1. <span data-ttu-id="ac934-150">No campo **de endereços de ponto final do Bot,** digite a URL ngrok (por `https://468b9ab725e9.ngrok.io` exemplo, ) onde você está hospedando o bot e `/api/messages` anexar a ele.</span><span class="sxs-lookup"><span data-stu-id="ac934-150">In the **Bot endpoint address** field, enter the ngrok URL (for example, `https://468b9ab725e9.ngrok.io`) where you're hosting the bot and append `/api/messages` to it.</span></span>

   <span data-ttu-id="ac934-151">Seu bot será capaz de lidar com consultas na sua extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="ac934-151">Your bot will be able to handle queries in your messaging extension.</span></span>

## <a name="5-build-and-run-your-app"></a><span data-ttu-id="ac934-152">5. Construa e execute seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="ac934-152">5. Build and run your app</span></span>

<span data-ttu-id="ac934-153">Você configurou uma URL para hospedar sua extensão de mensagens e configurou-a para lidar com pesquisas.</span><span class="sxs-lookup"><span data-stu-id="ac934-153">You've set up a URL to host your messaging extension and configured it to handle searches.</span></span> <span data-ttu-id="ac934-154">É hora de colocar seu aplicativo em funcionamento.</span><span class="sxs-lookup"><span data-stu-id="ac934-154">It's time to get your app up and running.</span></span>

1. <span data-ttu-id="ac934-155">Abra o terminal e vá para o diretório raiz do seu projeto de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ac934-155">Open terminal and go to the root directory of your app project.</span></span>
1. <span data-ttu-id="ac934-156">`npm install`Corra.</span><span class="sxs-lookup"><span data-stu-id="ac934-156">Run `npm install`.</span></span>
1. <span data-ttu-id="ac934-157">`npm start`Corra.</span><span class="sxs-lookup"><span data-stu-id="ac934-157">Run `npm start`.</span></span>

   <span data-ttu-id="ac934-158">Se for bem-sucedido, você verá a seguinte mensagem indicando que seu serviço de extensão de mensagens está ouvindo a atividade em seu `localhost` :</span><span class="sxs-lookup"><span data-stu-id="ac934-158">If successful, you see the following message indicating your messaging extension service is listening for activity at your `localhost`:</span></span>

   `Bot/ME service listening at http://localhost:3978`

## <a name="6-sideload-your-messaging-extension-in-teams"></a><span data-ttu-id="ac934-159">6. Acarregue a extensão de mensagens em Teams</span><span class="sxs-lookup"><span data-stu-id="ac934-159">6. Sideload your messaging extension in Teams</span></span>

<span data-ttu-id="ac934-160">Com a extensão de mensagens em execução, você pode instalá-la em Teams.</span><span class="sxs-lookup"><span data-stu-id="ac934-160">With your messaging extension running, you can install it in Teams.</span></span>

> [!TIP]
> <span data-ttu-id="ac934-161">Se você nunca mais regou um aplicativo de Teams antes e se deparar com problemas, siga estas [instruções](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams).</span><span class="sxs-lookup"><span data-stu-id="ac934-161">If you haven't sideloaded a Teams app before and run into issues, follow these [instructions](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams).</span></span>

1. <span data-ttu-id="ac934-162">Em Visual Studio Code, selecione a tecla **F5** para lançar um Teams cliente web.</span><span class="sxs-lookup"><span data-stu-id="ac934-162">In Visual Studio Code, select the **F5** key to launch a Teams web client.</span></span>
1. <span data-ttu-id="ac934-163">No aplicativo instalar a caixa de diálogo, selecione **Adicionar para mim**.</span><span class="sxs-lookup"><span data-stu-id="ac934-163">In the app install dialog, select **Add for me**.</span></span>

## <a name="7-test-your-messaging-extension"></a><span data-ttu-id="ac934-164">7. Teste sua extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="ac934-164">7. Test your messaging extension</span></span>

<span data-ttu-id="ac934-165">Saiba como as extensões de mensagens funcionam em um bate-papo Teams.</span><span class="sxs-lookup"><span data-stu-id="ac934-165">Learn how messaging extensions work in a Teams chat.</span></span>

1. <span data-ttu-id="ac934-166">Comece uma nova conversa.</span><span class="sxs-lookup"><span data-stu-id="ac934-166">Start a new chat.</span></span> Na caixa de composição, selecione **Mais** :::image type="icon" source="../assets/icons/teams-client-more.png"::: e selecione o aplicativo de extensão de mensagens que você acabou de carregar lateralmente.
1. <span data-ttu-id="ac934-168">Tente procurar algo (por exemplo, **Tickets**).</span><span class="sxs-lookup"><span data-stu-id="ac934-168">Try searching for something (for example, **Tickets**).</span></span> <span data-ttu-id="ac934-169">Se o seu aplicativo estiver funcionando, você verá os resultados de pesquisa de amostra (você pode adicionar o seu próprio mais tarde).</span><span class="sxs-lookup"><span data-stu-id="ac934-169">If your app is working, you'll see sample search results (you can add your own later).</span></span>

   :::image type="content" source="../assets/images/build-your-first-app/me-teams-test.png" alt-text="Uma captura de tela mostrando como uma extensão de mensagens baseada em pesquisa é usada na caixa de composição Teams.":::

## <a name="troubleshooting"></a><span data-ttu-id="ac934-171">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="ac934-171">Troubleshooting</span></span>

<span data-ttu-id="ac934-172">As informações a seguir podem ajudar se você tiver problemas para completar este tutorial.</span><span class="sxs-lookup"><span data-stu-id="ac934-172">The following information may help if you had issues completing this tutorial.</span></span>

<span data-ttu-id="ac934-173">**Bot não está conectado a Teams**</span><span class="sxs-lookup"><span data-stu-id="ac934-173">**Bot isn't connected to Teams**</span></span>

<span data-ttu-id="ac934-174">Se você instalou seu aplicativo, mas ele não está funcionando, certifique-se de que o bot da extensão de mensagens esteja [conectado ao *canal* Teams do Azure Bot Service](/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="ac934-174">If you installed your app but it isn't working, make sure the messaging extension's bot is [connected to the Azure Bot Service's Teams *channel*](/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true).</span></span>

<span data-ttu-id="ac934-175">É importante entender que isso não é o mesmo que um canal em Teams.</span><span class="sxs-lookup"><span data-stu-id="ac934-175">It's important to understand that this isn't the same as a channel in Teams.</span></span> <span data-ttu-id="ac934-176">Neste caso, um canal é como o Azure Bot Service conecta seu bot a Teams ou outro [aplicativo de comunicação suportado da Microsoft ou de terceiros.](/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="ac934-176">In this case, a channel is how the Azure Bot Service connects your bot to Teams or another [supported Microsoft or third-party communications app](/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true).</span></span>

## <a name="see-also"></a><span data-ttu-id="ac934-177">Confira também</span><span class="sxs-lookup"><span data-stu-id="ac934-177">See also</span></span>

* [<span data-ttu-id="ac934-178">Teams compor ou mandar caixa</span><span class="sxs-lookup"><span data-stu-id="ac934-178">Teams compose or command box</span></span>](../messaging-extensions/what-are-messaging-extensions.md) 
* [<span data-ttu-id="ac934-179">Inclua um recurso de desvendamento de link</span><span class="sxs-lookup"><span data-stu-id="ac934-179">Include a link unfurling feature</span></span>](../messaging-extensions/how-to/link-unfurling.md)
* [<span data-ttu-id="ac934-180">Diretrizes de design</span><span class="sxs-lookup"><span data-stu-id="ac934-180">Design guidelines</span></span>](../messaging-extensions/design/messaging-extension-design.md) 
* [<span data-ttu-id="ac934-181">Modelos de interface do usuário prontos para produção</span><span class="sxs-lookup"><span data-stu-id="ac934-181">Production-ready UI templates</span></span>](../concepts/design/design-teams-app-ui-templates.md) 
* [<span data-ttu-id="ac934-182">Adicionar autenticação</span><span class="sxs-lookup"><span data-stu-id="ac934-182">Add authentication</span></span>](../messaging-extensions/how-to/add-authentication.md)
* [<span data-ttu-id="ac934-183">Crie uma extensão de mensagens baseada em ação</span><span class="sxs-lookup"><span data-stu-id="ac934-183">Create an action-based messaging extension</span></span>](../messaging-extensions/how-to/action-commands/define-action-command.md)
* [<span data-ttu-id="ac934-184">Microsoft Bot Framework</span><span class="sxs-lookup"><span data-stu-id="ac934-184">Microsoft Bot Framework</span></span>](https://dev.botframework.com/)

## <a name="next-steps"></a><span data-ttu-id="ac934-185">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="ac934-185">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ac934-186">Definir comandos de pesquisa</span><span class="sxs-lookup"><span data-stu-id="ac934-186">Define search commands</span></span>](../messaging-extensions/how-to/search-commands/define-search-command.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="ac934-187">Responda às pesquisas dos usuários</span><span class="sxs-lookup"><span data-stu-id="ac934-187">Respond to users' searches</span></span>](../messaging-extensions/how-to/search-commands/respond-to-search.md)
