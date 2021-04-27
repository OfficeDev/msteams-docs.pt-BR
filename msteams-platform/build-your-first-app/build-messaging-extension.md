---
title: Começar - Criar uma extensão de mensagens
author: heath-hamilton
description: Crie rapidamente uma extensão de mensagens do Microsoft Teams usando o microsoft Teams Toolkit.
ms.author: lajanuar
localization_priority: Normal
ms.date: 11/04/2020
ms.topic: tutorial
ms.openlocfilehash: f3b5bc9c749d5e5276c0c7af7ff92f4ff5a00d0b
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020867"
---
# <a name="build-a-messaging-extension-for-microsoft-teams"></a><span data-ttu-id="f40ad-103">Criar uma extensão de mensagens para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="f40ad-103">Build a messaging extension for Microsoft Teams</span></span>

<span data-ttu-id="f40ad-104">Há dois tipos de extensões de mensagens *do* Teams: comandos [de pesquisa](../messaging-extensions/how-to/search-commands/define-search-command.md) e comandos de [ação.](../messaging-extensions/how-to/action-commands/define-action-command.md)</span><span class="sxs-lookup"><span data-stu-id="f40ad-104">There are two types of Teams *messaging extensions*: [Search commands](../messaging-extensions/how-to/search-commands/define-search-command.md) and [action commands](../messaging-extensions/how-to/action-commands/define-action-command.md).</span></span>

<span data-ttu-id="f40ad-105">Nesta lição, você criará um comando de pesquisa *(também* conhecido como extensão de mensagens baseada em pesquisa *),* que é um atalho para localizar conteúdo externo e compartilhamento no Teams.</span><span class="sxs-lookup"><span data-stu-id="f40ad-105">In this lesson, you'll create a *search command* (also known as a *search-based messaging extension*), which is a shortcut for finding external content and sharing it in Teams.</span></span> <span data-ttu-id="f40ad-106">Os usuários podem acessar comandos de pesquisa na [caixa de comando ou composição do Teams.](../messaging-extensions/what-are-messaging-extensions.md)</span><span class="sxs-lookup"><span data-stu-id="f40ad-106">Users can access search commands from the [Teams compose or command box](../messaging-extensions/what-are-messaging-extensions.md).</span></span>

## <a name="your-assignment"></a><span data-ttu-id="f40ad-107">Sua atribuição</span><span class="sxs-lookup"><span data-stu-id="f40ad-107">Your assignment</span></span>

<span data-ttu-id="f40ad-108">O help desk da sua organização se comunica com os usuários por meio do Teams, mas os tíquetes residem em um sistema separado.</span><span class="sxs-lookup"><span data-stu-id="f40ad-108">Your organization's help desk communicates with users through Teams, but the tickets reside in a separate system.</span></span> <span data-ttu-id="f40ad-109">Isso significa que a equipe de suporte deve ir e voltar constantemente entre aplicativos.</span><span class="sxs-lookup"><span data-stu-id="f40ad-109">This means support staff must constantly go back and forth between apps.</span></span> <span data-ttu-id="f40ad-110">Você investigará como reduzir essa alternação de contexto criando uma extensão de mensagens simples baseada em pesquisa para o Teams.</span><span class="sxs-lookup"><span data-stu-id="f40ad-110">You'll investigate how you might reduce this much context switching by creating a simple search-based messaging extension for Teams.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="f40ad-111">O que você aprenderá</span><span class="sxs-lookup"><span data-stu-id="f40ad-111">What you'll learn</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="f40ad-112">Criar um projeto de aplicativo e um bot de extensão de mensagens usando o microsoft Teams Toolkit para Visual Studio Código</span><span class="sxs-lookup"><span data-stu-id="f40ad-112">Create an app project and messaging extension bot using the Microsoft Teams Toolkit for Visual Studio Code</span></span>
> * <span data-ttu-id="f40ad-113">Identificar as configurações do aplicativo e alguns dos scaffolding relevantes para extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="f40ad-113">Identify the app configurations and some of the scaffolding relevant to messaging extensions</span></span>
> * <span data-ttu-id="f40ad-114">Hospedar um aplicativo localmente</span><span class="sxs-lookup"><span data-stu-id="f40ad-114">Host an app locally</span></span>
> * <span data-ttu-id="f40ad-115">Configurar o bot para sua extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="f40ad-115">Configure the bot for your messaging extension</span></span>
> * <span data-ttu-id="f40ad-116">Fazer sideload e testar uma extensão de mensagens no Teams</span><span class="sxs-lookup"><span data-stu-id="f40ad-116">Sideload and test a messaging extension in Teams</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="f40ad-117">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="f40ad-117">Before you begin</span></span>

<span data-ttu-id="f40ad-118">Se você ainda não entendeu e instalou os [pré-requisitos de](build-first-app-overview.md#get-prerequisites)desenvolvimento do Teams.</span><span class="sxs-lookup"><span data-stu-id="f40ad-118">If you haven't yet, make sure you [understand and install the Teams development prerequisites](build-first-app-overview.md#get-prerequisites).</span></span>

## <a name="1-create-your-app-project"></a><span data-ttu-id="f40ad-119">1. Crie seu projeto de aplicativo</span><span class="sxs-lookup"><span data-stu-id="f40ad-119">1. Create your app project</span></span>

<span data-ttu-id="f40ad-120">A Toolkit do Microsoft Teams ajuda você a configurar os seguintes componentes para a extensão de mensagens:</span><span class="sxs-lookup"><span data-stu-id="f40ad-120">The Microsoft Teams Toolkit helps you set up the following components for your messaging extension:</span></span>

* <span data-ttu-id="f40ad-121">**Configurações de aplicativo e scaffolding relevantes** para extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="f40ad-121">**App configurations and scaffolding** relevant to messaging extensions</span></span>
* <span data-ttu-id="f40ad-122">**Bot** para a extensão de mensagens que é registrada automaticamente com o Serviço de Bot do Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="f40ad-122">**Bot** for your messaging extension that's automatically registered with the Microsoft Azure Bot Service</span></span>

> [!TIP]
> <span data-ttu-id="f40ad-123">Se você não tiver criado um projeto de aplicativo do [](../build-your-first-app/build-and-run.md) Teams antes, talvez seja útil seguir estas instruções que explicam os projetos com mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="f40ad-123">If you haven't created a Teams app project before, you might find it helpful to follow [these instructions](../build-your-first-app/build-and-run.md) that explain projects in more detail.</span></span>

1. Em Visual Studio Código, selecione **Microsoft Teams** na Barra de Atividades à esquerda e escolha Criar um novo aplicativo do :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: **Teams.**
1. <span data-ttu-id="f40ad-125">Quando solicitado, entre com sua conta de desenvolvimento do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="f40ad-125">When prompted, sign in with your Microsoft 365 development account.</span></span>
1. <span data-ttu-id="f40ad-126">Na tela **Adicionar recursos,** selecione **Extensão de Mensagens,** em **seguida, Próximo**.</span><span class="sxs-lookup"><span data-stu-id="f40ad-126">On the **Add capabilities** screen, select **Messaging Extension** then **Next**.</span></span>
1. <span data-ttu-id="f40ad-127">Insira um nome para seu aplicativo do Teams.</span><span class="sxs-lookup"><span data-stu-id="f40ad-127">Enter a name for your Teams app.</span></span> <span data-ttu-id="f40ad-128">(Esse é o nome padrão para seu aplicativo e também o nome do diretório do projeto do aplicativo em sua máquina local.)</span><span class="sxs-lookup"><span data-stu-id="f40ad-128">(This is the default name for your app and also the name of the app project directory on your local machine.)</span></span>
1. <span data-ttu-id="f40ad-129">Na tela **Configurar extensão de mensagens,** faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f40ad-129">On the **Configure messaging extension** screen, do the following:</span></span>
    1. <span data-ttu-id="f40ad-130">Escolha apenas a **opção baseada em** Pesquisa para o tipo de extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="f40ad-130">Choose only the **Search-based** option for the type of messaging extension.</span></span>
    1. <span data-ttu-id="f40ad-131">Selecione **Criar um novo Bot** e Crie Registro de **Bot.**</span><span class="sxs-lookup"><span data-stu-id="f40ad-131">Select **Create a new Bot** then **Create Bot Registration**.</span></span> <span data-ttu-id="f40ad-132">Se tiver êxito, seu novo bot terá um status **Registrado.**</span><span class="sxs-lookup"><span data-stu-id="f40ad-132">If successful, your new bot will have a **Registered** status.</span></span>
    1. <span data-ttu-id="f40ad-133">Por enquanto, selecione **Não** para a opção de desalinização do link.</span><span class="sxs-lookup"><span data-stu-id="f40ad-133">For now, select **No** for the link unfurling option.</span></span>
1. <span data-ttu-id="f40ad-134">Selecione **Concluir** na parte inferior da tela para configurar seu projeto.</span><span class="sxs-lookup"><span data-stu-id="f40ad-134">Select **Finish** at the bottom of the screen to configure your project.</span></span>

## <a name="2-identify-relevant-app-project-components"></a><span data-ttu-id="f40ad-135">2. Identificar componentes relevantes do projeto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="f40ad-135">2. Identify relevant app project components</span></span>

<span data-ttu-id="f40ad-136">Grande parte das configurações e scaffolding do aplicativo são configuradas automaticamente quando você cria seu projeto com o teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="f40ad-136">Much of the app configurations and scaffolding are set up automatically when you create your project with the Teams Toolkit.</span></span>

### <a name="app-configurations"></a><span data-ttu-id="f40ad-137">Configurações de aplicativo</span><span class="sxs-lookup"><span data-stu-id="f40ad-137">App configurations</span></span>

<span data-ttu-id="f40ad-138">Para exibir ou atualizar as configurações da extensão de mensagens, selecione **App Studio** no kit de ferramentas e acesse **Extensões de mensagens.**</span><span class="sxs-lookup"><span data-stu-id="f40ad-138">To view or update your messaging extension's configurations, select **App Studio** in the toolkit and go to **Messaging extensions**.</span></span>

### <a name="app-scaffolding"></a><span data-ttu-id="f40ad-139">Scaffolding de aplicativos</span><span class="sxs-lookup"><span data-stu-id="f40ad-139">App scaffolding</span></span>

<span data-ttu-id="f40ad-140">O scaffolding de aplicativo fornece um arquivo, localizado no diretório raiz do seu projeto, para manipular como sua extensão de mensagens (ou tecnicamente, o bot da extensão de mensagens ) responde às consultas de pesquisa no `botActivityHandler.js` Teams. [](#4-configure-the-bot-for-your-messaging-extension)</span><span class="sxs-lookup"><span data-stu-id="f40ad-140">The app scaffolding provides a `botActivityHandler.js` file, located in the root directory of your project, for handling how your messaging extension (or technically, the [messaging extension's bot](#4-configure-the-bot-for-your-messaging-extension)) responds to search queries in Teams.</span></span>

## <a name="3-set-up-a-secure-tunnel-to-your-app"></a><span data-ttu-id="f40ad-141">3. Configurar um túnel seguro para seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="f40ad-141">3. Set up a secure tunnel to your app</span></span>

<span data-ttu-id="f40ad-142">Para fins de teste, vamos hospedar sua extensão de mensagens em um servidor Web local (porta 3978).</span><span class="sxs-lookup"><span data-stu-id="f40ad-142">For testing purposes, let's host your messaging extension on a local web server (port 3978).</span></span>

1. <span data-ttu-id="f40ad-143">Caso ainda não tenha feito isso, instale [ngrok](https://ngrok.com/download).</span><span class="sxs-lookup"><span data-stu-id="f40ad-143">If you haven't already, install [ngrok](https://ngrok.com/download).</span></span>
1. <span data-ttu-id="f40ad-144">Em um terminal, execute `ngrok http -host-header=rewrite 3978` .</span><span class="sxs-lookup"><span data-stu-id="f40ad-144">In a terminal, run `ngrok http -host-header=rewrite 3978`.</span></span>
1. <span data-ttu-id="f40ad-145">Copie a URL HTTPS na saída (por exemplo, ) já que o `https://468b9ab725e9.ngrok.io` Teams requer conexões HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f40ad-145">Copy the HTTPS URL in the output (for example, `https://468b9ab725e9.ngrok.io`) since Teams requires HTTPS connections.</span></span>

<span data-ttu-id="f40ad-146">Com essa URL, o Teams (que requer conexões HTTPS) poderá túnel para onde você está hospedando seu aplicativo ( `localhost` na porta 3978).</span><span class="sxs-lookup"><span data-stu-id="f40ad-146">With this URL, Teams (which requires HTTPS connections) will be able tunnel to where you're hosting your app (`localhost` on port 3978).</span></span>

## <a name="4-configure-the-bot-for-your-messaging-extension"></a><span data-ttu-id="f40ad-147">4. Configure o bot para sua extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="f40ad-147">4. Configure the bot for your messaging extension</span></span>

<span data-ttu-id="f40ad-148">As extensões de mensagens dependem de bots para enviar e processar solicitações de usuário do Teams para seu serviço hospedado.</span><span class="sxs-lookup"><span data-stu-id="f40ad-148">Messaging extensions rely on bots to send and process user requests from Teams to your hosted service.</span></span> <span data-ttu-id="f40ad-149">O bot deve ser registrado com o Serviço bot do Azure, que foi feito quando você configura seu aplicativo usando o teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="f40ad-149">The bot must be registered with the Azure Bot Service, which was done when you set up your app using the Teams Toolkit.</span></span>

<span data-ttu-id="f40ad-150">Você ainda deve especificar uma URL de ponto de extremidade de bot para receber e processar consultas de pesquisa em sua extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="f40ad-150">You still must specify a bot endpoint URL to receive and process search queries in your messaging extension.</span></span> <span data-ttu-id="f40ad-151">Normalmente, a URL se parece com `https://HOST_URL/api/messages` .</span><span class="sxs-lookup"><span data-stu-id="f40ad-151">Typically, the URL looks like `https://HOST_URL/api/messages`.</span></span> <span data-ttu-id="f40ad-152">Você pode configurar isso rapidamente no kit de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="f40ad-152">You can configure this quickly in the toolkit.</span></span>

1. Em Visual Studio Código, selecione **Microsoft Teams** na Barra de Atividades à esquerda e escolha Abrir o Microsoft Teams :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: **Toolkit**.
1. <span data-ttu-id="f40ad-154">Vá para **Bots > registros de bot existentes** e selecione o bot que você criou durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="f40ad-154">Go to **Bots > Existing bot registrations** and select the bot you created during setup.</span></span>
1. <span data-ttu-id="f40ad-155">No campo **Endereço do ponto** de extremidade bot, insira a URL do ngrok (por exemplo, ) onde você está hospedando o bot e `https://468b9ab725e9.ngrok.io` adeque `/api/messages` a ele.</span><span class="sxs-lookup"><span data-stu-id="f40ad-155">In the **Bot endpoint address** field, enter the ngrok URL (for example, `https://468b9ab725e9.ngrok.io`) where you're hosting the bot and append `/api/messages` to it.</span></span>

<span data-ttu-id="f40ad-156">Seu bot poderá lidar com consultas em sua extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="f40ad-156">Your bot will be able to handle queries in your messaging extension.</span></span>

## <a name="5-build-and-run-your-app"></a><span data-ttu-id="f40ad-157">5. Crie e execute seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="f40ad-157">5. Build and run your app</span></span>

<span data-ttu-id="f40ad-158">Você configurou uma URL para hospedar sua extensão de mensagens e configurá-la para lidar com pesquisas.</span><span class="sxs-lookup"><span data-stu-id="f40ad-158">You've set up a URL to host your messaging extension and configured it to handle searches.</span></span> <span data-ttu-id="f40ad-159">É hora de fazer o aplicativo funcionar.</span><span class="sxs-lookup"><span data-stu-id="f40ad-159">It's time to get your app up and running.</span></span>

1. <span data-ttu-id="f40ad-160">Em um terminal, vá para o diretório raiz do seu projeto de aplicativo e execute `npm install` .</span><span class="sxs-lookup"><span data-stu-id="f40ad-160">In a terminal, go to the root directory of your app project and run `npm install`.</span></span>
1. <span data-ttu-id="f40ad-161">Executar `npm start` .</span><span class="sxs-lookup"><span data-stu-id="f40ad-161">Run `npm start`.</span></span>

<span data-ttu-id="f40ad-162">Se tiver êxito, você verá a seguinte mensagem indicando que seu serviço de extensão de mensagens está escutando atividades em seu `localhost` :</span><span class="sxs-lookup"><span data-stu-id="f40ad-162">If successful, you see the following message indicating your messaging extension service is listening for activity at your `localhost`:</span></span>

`Bot/ME service listening at http://localhost:3978`

## <a name="6-sideload-your-messaging-extension-in-teams"></a><span data-ttu-id="f40ad-163">6. Fazer sideload da extensão de mensagens no Teams</span><span class="sxs-lookup"><span data-stu-id="f40ad-163">6. Sideload your messaging extension in Teams</span></span>

<span data-ttu-id="f40ad-164">Com a extensão de mensagens em execução, você pode instalá-la no Teams.</span><span class="sxs-lookup"><span data-stu-id="f40ad-164">With your messaging extension running, you can install it in Teams.</span></span>

> [!TIP]
> <span data-ttu-id="f40ad-165">Se você ainda não fez sideload de um aplicativo do Teams antes e correu para problemas, siga estas [instruções](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams).</span><span class="sxs-lookup"><span data-stu-id="f40ad-165">If you haven't sideloaded a Teams app before and run into issues, follow these [instructions](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams).</span></span>

1. <span data-ttu-id="f40ad-166">Em Visual Studio Código, pressione a **tecla F5** para iniciar um cliente Web do Teams.</span><span class="sxs-lookup"><span data-stu-id="f40ad-166">In Visual Studio Code, press the **F5** key to launch a Teams web client.</span></span>
1. <span data-ttu-id="f40ad-167">Na caixa de diálogo de instalação do aplicativo, selecione **Adicionar para mim**.</span><span class="sxs-lookup"><span data-stu-id="f40ad-167">In the app install dialog, select **Add for me**.</span></span>

## <a name="7-test-your-messaging-extension"></a><span data-ttu-id="f40ad-168">7. Teste sua extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="f40ad-168">7. Test your messaging extension</span></span>

<span data-ttu-id="f40ad-169">Saiba como as extensões de mensagens funcionam em um chat do Teams.</span><span class="sxs-lookup"><span data-stu-id="f40ad-169">Learn how messaging extensions work in a Teams chat.</span></span>

1. <span data-ttu-id="f40ad-170">Inicie um novo chat.</span><span class="sxs-lookup"><span data-stu-id="f40ad-170">Start a new chat.</span></span> Na caixa de redação, selecione **Mais** e escolha o aplicativo de extensão de mensagens :::image type="icon" source="../assets/icons/teams-client-more.png"::: que você acabou de fazer sideload.
1. <span data-ttu-id="f40ad-172">Tente pesquisar algo (por exemplo, **Tíquetes).**</span><span class="sxs-lookup"><span data-stu-id="f40ad-172">Try searching for something (for example, **Tickets**).</span></span> <span data-ttu-id="f40ad-173">Se seu aplicativo estiver funcionando, você verá resultados de pesquisa de exemplo (você pode adicionar seus próprios posteriormente).</span><span class="sxs-lookup"><span data-stu-id="f40ad-173">If your app is working, you'll see sample search results (you can add your own later).</span></span><br/>
   :::image type="content" source="../assets/images/build-your-first-app/me-teams-test.png" alt-text="Uma captura de tela mostrando como uma extensão de mensagens baseada em pesquisa é usada na caixa de redação do Teams.":::

## <a name="well-done"></a><span data-ttu-id="f40ad-175">Muito bem</span><span class="sxs-lookup"><span data-stu-id="f40ad-175">Well done</span></span>

<span data-ttu-id="f40ad-176">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="f40ad-176">Congratulations!</span></span> <span data-ttu-id="f40ad-177">Você tem uma extensão básica de mensagens do Teams configurada para pesquisar conteúdo externo na caixa de composição ou comando.</span><span class="sxs-lookup"><span data-stu-id="f40ad-177">You have a basic Teams messaging extension that's set up to search for external content in the compose or command box.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f40ad-178">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="f40ad-178">Next steps</span></span>

<span data-ttu-id="f40ad-179">Consulte as páginas a seguir para continuar e criar uma extensão de mensagens totalmente em destaque:</span><span class="sxs-lookup"><span data-stu-id="f40ad-179">See the following pages to continue and build a fully featured messaging extension:</span></span>

1. <span data-ttu-id="f40ad-180">[Defina comandos de](../messaging-extensions/how-to/search-commands/define-search-command.md) pesquisa relevantes ao seu serviço.</span><span class="sxs-lookup"><span data-stu-id="f40ad-180">[Define search commands](../messaging-extensions/how-to/search-commands/define-search-command.md) that are relevant to your service.</span></span>
1. <span data-ttu-id="f40ad-181">Configure seu serviço [para responder às pesquisas dos usuários.](../messaging-extensions/how-to/search-commands/respond-to-search.md)</span><span class="sxs-lookup"><span data-stu-id="f40ad-181">Configure your service to [respond to users' searches](../messaging-extensions/how-to/search-commands/respond-to-search.md).</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="f40ad-182">Solução de Problemas</span><span class="sxs-lookup"><span data-stu-id="f40ad-182">Troubleshooting</span></span>

<span data-ttu-id="f40ad-183">As informações a seguir podem ajudar se você tiver problemas ao concluir este tutorial.</span><span class="sxs-lookup"><span data-stu-id="f40ad-183">The following information may help if you had issues completing this tutorial.</span></span>

### <a name="bot-isnt-connected-to-teams"></a><span data-ttu-id="f40ad-184">Bot não está conectado ao Teams</span><span class="sxs-lookup"><span data-stu-id="f40ad-184">Bot isn't connected to Teams</span></span>

<span data-ttu-id="f40ad-185">Se você instalou seu aplicativo, mas ele não está funcionando, certifique-se de que o bot da extensão de mensagens esteja conectado ao canal do Teams do Serviço de Bot do [Azure. ](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="f40ad-185">If you installed your app but it isn't working, make sure the messaging extension's bot is [connected to the Azure Bot Service's Teams *channel*](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true).</span></span>

<span data-ttu-id="f40ad-186">É importante entender que isso não é o mesmo que um canal no Teams.</span><span class="sxs-lookup"><span data-stu-id="f40ad-186">It's important to understand that this isn't the same as a channel in Teams.</span></span> <span data-ttu-id="f40ad-187">Nesse caso, um canal é como o Serviço bot do Azure conecta seu bot ao Teams ou a outro aplicativo de comunicações da Microsoft ou de terceiros com [suporte.](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="f40ad-187">In this case, a channel is how the Azure Bot Service connects your bot to Teams or another [supported Microsoft or third-party communications app](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true).</span></span>

## <a name="learn-more"></a><span data-ttu-id="f40ad-188">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="f40ad-188">Learn more</span></span>

* [<span data-ttu-id="f40ad-189">Incluir um recurso de desfralização de link</span><span class="sxs-lookup"><span data-stu-id="f40ad-189">Include a link unfurling feature</span></span>](../messaging-extensions/how-to/link-unfurling.md)
* <span data-ttu-id="f40ad-190">Siga nossas [diretrizes de design](../messaging-extensions/design/messaging-extension-design.md) e crie com modelos [de interface](../concepts/design/design-teams-app-ui-templates.md) do usuário prontos para produção para criar uma experiência perfeita.</span><span class="sxs-lookup"><span data-stu-id="f40ad-190">Follow our [design guidelines](../messaging-extensions/design/messaging-extension-design.md) and build with [production-ready UI templates](../concepts/design/design-teams-app-ui-templates.md) to create a seamless experience.</span></span>
* [<span data-ttu-id="f40ad-191">Adicionar autenticação</span><span class="sxs-lookup"><span data-stu-id="f40ad-191">Add authentication</span></span>](../messaging-extensions/how-to/add-authentication.md)
* [<span data-ttu-id="f40ad-192">Criar uma extensão de mensagens baseada em ação</span><span class="sxs-lookup"><span data-stu-id="f40ad-192">Create an action-based messaging extension</span></span>](../messaging-extensions/how-to/action-commands/define-action-command.md)
* [<span data-ttu-id="f40ad-193">Microsoft Bot Framework</span><span class="sxs-lookup"><span data-stu-id="f40ad-193">Microsoft Bot Framework</span></span>](https://dev.botframework.com/)

