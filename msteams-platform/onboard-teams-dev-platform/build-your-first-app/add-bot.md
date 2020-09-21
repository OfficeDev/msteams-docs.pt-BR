---
title: Criar um bot para o Teams
author: heath-hamilton
description: Saiba como criar um bot no seu primeiro aplicativo do Microsoft Teams.
ms.author: lajanuar
ms.date: 08/31/2020
ms.topic: tutorial
ms.openlocfilehash: f1307bcc7bb864ddfa97b9297f34fa4f7d5fcb0d
ms.sourcegitcommit: d3bb4bbcdff9545c9869647dcdbe563a2db868be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2020
ms.locfileid: "47964640"
---
# <a name="create-a-bot-for-teams"></a><span data-ttu-id="50b06-103">Criar um bot para o Teams</span><span class="sxs-lookup"><span data-stu-id="50b06-103">Create a bot for Teams</span></span>

<span data-ttu-id="50b06-104">Você criará um aplicativo de *bot* básico neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="50b06-104">You'll build a basic *bot* app in this tutorial.</span></span> <span data-ttu-id="50b06-105">Um bot atua como intermediário entre os usuários do Teams e o serviço Web.</span><span class="sxs-lookup"><span data-stu-id="50b06-105">A bot acts as an intermediary between Teams users and your web service.</span></span> <span data-ttu-id="50b06-106">As pessoas podem bater papo com um bot para obter informações rapidamente ou iniciar fluxos de trabalho e tarefas realizadas pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="50b06-106">People can chat with a bot to quickly get information or initiate workflows and tasks performed by your service.</span></span>

## <a name="your-assignment"></a><span data-ttu-id="50b06-107">Sua atribuição</span><span class="sxs-lookup"><span data-stu-id="50b06-107">Your assignment</span></span>

<span data-ttu-id="50b06-108">Seu local de trabalho está usando [guias](../build-your-first-app/add-personal-tab.md) para trazer informações importantes de contato no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="50b06-108">Your workplace has been using [tabs](../build-your-first-app/add-personal-tab.md) to surface important contact information in Teams.</span></span> <span data-ttu-id="50b06-109">Por exemplo, os colegas têm acesso rápido ao número de telefone de suporte técnico.</span><span class="sxs-lookup"><span data-stu-id="50b06-109">For example, colleagues have quick access to the help desk phone number.</span></span> <span data-ttu-id="50b06-110">Mas em vez de chamar, e se as pessoas pudessem entrar em contato com o suporte técnico usando um chatbot?</span><span class="sxs-lookup"><span data-stu-id="50b06-110">But instead of calling, what if people could contact the help desk using a chatbot?</span></span> <span data-ttu-id="50b06-111">Seu chefe pede que você veja com rapidez como você pode obter um bot de conversação básico e em execução no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="50b06-111">Your boss asks you to look at how quickly you can get a basic conversational bot up and running in Teams.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="50b06-112">O que você aprenderá</span><span class="sxs-lookup"><span data-stu-id="50b06-112">What you'll learn</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="50b06-113">Criar um projeto de aplicativo e um bot usando o Microsoft Teams Toolkit para o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="50b06-113">Create an app project and bot using the Microsoft Teams Toolkit for Visual Studio Code</span></span>
> * <span data-ttu-id="50b06-114">Identificar as propriedades de manifesto do aplicativo e alguns dos scaffolding relevantes para bots</span><span class="sxs-lookup"><span data-stu-id="50b06-114">Identify the app manifest properties and some of the scaffolding relevant to bots</span></span>
> * <span data-ttu-id="50b06-115">Hospedar um bot localmente</span><span class="sxs-lookup"><span data-stu-id="50b06-115">Host a bot locally</span></span>
> * <span data-ttu-id="50b06-116">Configurar um bot para o Teams</span><span class="sxs-lookup"><span data-stu-id="50b06-116">Configure a bot for Teams</span></span>
> * <span data-ttu-id="50b06-117">Sideload e testar um bot no Teams</span><span class="sxs-lookup"><span data-stu-id="50b06-117">Sideload and test a bot in Teams</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="50b06-118">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="50b06-118">Before you begin</span></span>

<span data-ttu-id="50b06-119">Se você ainda não tiver feito isso, configure sua [conta](building-real-world-app.md#set-up-your-development-account) de desenvolvimento do Microsoft 365 e [ferramentas de aplicativos do teams](building-real-world-app.md#install-your-development-tools).</span><span class="sxs-lookup"><span data-stu-id="50b06-119">If you haven't yet, set up your Microsoft 365 development [account](building-real-world-app.md#set-up-your-development-account) and [Teams app tools](building-real-world-app.md#install-your-development-tools).</span></span>

## <a name="create-your-app-project-and-bot"></a><span data-ttu-id="50b06-120">Criar seu projeto de aplicativo e bot</span><span class="sxs-lookup"><span data-stu-id="50b06-120">Create your app project and bot</span></span>

<span data-ttu-id="50b06-121">O Microsoft Teams Toolkit ajuda você a configurar os seguintes componentes para seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="50b06-121">The Microsoft Teams Toolkit helps you set up the following components for your app:</span></span>

* <span data-ttu-id="50b06-122">**Projeto do aplicativo**: inclui o manifesto do aplicativo e o scaffolding relevantes para bots</span><span class="sxs-lookup"><span data-stu-id="50b06-122">**App project**: Includes the app manifest and scaffolding relevant to bots</span></span>
* <span data-ttu-id="50b06-123">**Bot**: configura um novo bot e o registra com o serviço de bot do Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="50b06-123">**Bot**: Configures a new bot and registers it with the Microsoft Azure Bot Service</span></span>

> [!TIP]
> <span data-ttu-id="50b06-124">Se você ainda não criou um projeto de aplicativos do Microsoft Teams, talvez ache útil seguir [estas instruções](../build-your-first-app/build-and-run.md) para explicar os projetos com mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="50b06-124">If you haven't created a Teams app project before, you might find it helpful to follow [these instructions](../build-your-first-app/build-and-run.md) that explain projects in more detail.</span></span>

1. No Visual Studio Code, selecione **Microsoft Teams** :::image type="icon" source="../doc-links/images/vsc-toolkit.png"::: na barra de atividades à esquerda e escolha **criar um novo aplicativo Teams**.
1. <span data-ttu-id="50b06-126">Insira um nome para seu aplicativo do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="50b06-126">Enter a name for your Teams app.</span></span> <span data-ttu-id="50b06-127">(Esse é o nome padrão para seu aplicativo e também o nome do diretório do projeto de aplicativo em sua máquina local.)</span><span class="sxs-lookup"><span data-stu-id="50b06-127">(This is the default name for your app and also the name of the app project directory on your local machine.)</span></span>
1. <span data-ttu-id="50b06-128">Na tela **Adicionar recursos** , selecione **bot** e, em seguida, **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="50b06-128">On the **Add capabilities** screen, select **Bot** then **Next**.</span></span>
1. <span data-ttu-id="50b06-129">Selecione **criar um novo bot** e **login** para entrar com sua conta de desenvolvimento do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="50b06-129">Select **Create a new Bot** and **Login** to sign in with your Microsoft 365 development account.</span></span><br/>
:::image type="content" source="../doc-links/images/vsc-create-bot.png" alt-text="Ilustração mostrando como, no Teams Toolkit, para fazer logon na sua conta do Microsoft 365 para criar um novo bot.":::
1. <span data-ttu-id="50b06-131">Opcion Insira um nome personalizado para o bot e selecione **criar**.</span><span class="sxs-lookup"><span data-stu-id="50b06-131">(Optional) Enter a custom name for your bot and select **Create**.</span></span> <span data-ttu-id="50b06-132">(Lembre-se de que esse é o nome do seu bot e não o nome do aplicativo Teams que você já especificou.)</span><span class="sxs-lookup"><span data-stu-id="50b06-132">(Remember, this is the name for your bot and not the name of the Teams app you already specified.)</span></span>
1. <span data-ttu-id="50b06-133">Selecione **concluir** na parte inferior da tela para configurar seu projeto.</span><span class="sxs-lookup"><span data-stu-id="50b06-133">Select **Finish** at the bottom of the screen to configure your project.</span></span>

## <a name="identify-relevant-app-project-components"></a><span data-ttu-id="50b06-134">Identificar componentes de projeto de aplicativo relevantes</span><span class="sxs-lookup"><span data-stu-id="50b06-134">Identify relevant app project components</span></span>

<span data-ttu-id="50b06-135">Grande parte do manifesto do aplicativo e do scaffolding são configuradas automaticamente quando você cria seu projeto com o Teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="50b06-135">Much of the app manifest and scaffolding are set up automatically when you create your project with the Teams Toolkit.</span></span> <span data-ttu-id="50b06-136">Vamos examinar os principais componentes para a criação de um bot.</span><span class="sxs-lookup"><span data-stu-id="50b06-136">Let's look at the main components for building a bot.</span></span>

### <a name="app-manifest"></a><span data-ttu-id="50b06-137">Manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="50b06-137">App manifest</span></span>

<span data-ttu-id="50b06-138">O trecho de código a seguir do manifesto do aplicativo (o `manifest.json` arquivo no diretório do seu projeto `.publish` ) mostra as propriedades e os valores padrão relevantes para bots.</span><span class="sxs-lookup"><span data-stu-id="50b06-138">The following snippet from the app manifest (the `manifest.json` file in your project's `.publish` directory) shows the properties and default values relevant to bots.</span></span>

```JSON
    "bots": [
        {
            "botId": "{botId0}",
            "scopes": [
                "personal",
                "groupchat",
                "team"
            ],
            "supportsFiles": false,
            "isNotificationOnly": false,
            "commandLists": [
                {
                    "scopes": [
                        "personal",
                        "groupchat",
                        "team"
                    ],
                    "commands": [
                        {
                            "title": "Hello",
                            "description": "Sends a hello message and @mention the sender"
                        }
                    ]
                }
            ]
        }
    ],
```

<span data-ttu-id="50b06-139">Por enquanto, vamos apenas nos concentrar nas seguintes propriedades obrigatórias.</span><span class="sxs-lookup"><span data-stu-id="50b06-139">For now, let's just focus on the following required properties.</span></span> <span data-ttu-id="50b06-140">(Veja a lista completa de propriedades com suporte [`bots`](../../resources/schema/manifest-schema.md#bots) .)</span><span class="sxs-lookup"><span data-stu-id="50b06-140">(See the full list of supported [`bots`](../../resources/schema/manifest-schema.md#bots) properties.)</span></span>

* <span data-ttu-id="50b06-141">`botId`: A ID do bot que você criou configurando seu projeto.</span><span class="sxs-lookup"><span data-stu-id="50b06-141">`botId`: The ID of the bot you created setting up your project.</span></span> <span data-ttu-id="50b06-142">(Armazenado no `{botId0}` , você pode encontrar a ID real no `Development.env` .)</span><span class="sxs-lookup"><span data-stu-id="50b06-142">(Stored in `{botId0}`, you can find the actual ID in `Development.env`.)</span></span>
* <span data-ttu-id="50b06-143">`scopes`: Especifica se o bot está disponível nos `personal` `groupchat` `team` contextos, ou (por exemplo, canal).</span><span class="sxs-lookup"><span data-stu-id="50b06-143">`scopes`: Specifies if your bot is available in `personal`, `groupchat`, or `team` (i.e., channel) contexts.</span></span>
* <span data-ttu-id="50b06-144">`commands`: Comandos disponíveis os usuários podem enviar para o bot.</span><span class="sxs-lookup"><span data-stu-id="50b06-144">`commands`: Available commands users can send to your bot.</span></span>
* <span data-ttu-id="50b06-145">`title`: Um nome de comando de bot que os usuários vêem no cliente do teams.</span><span class="sxs-lookup"><span data-stu-id="50b06-145">`title`: A bot command name users see in the Teams client.</span></span>
* <span data-ttu-id="50b06-146">`description`: Uma breve descrição ou exemplo da sintaxe e dos argumentos para ajudar os usuários a entender o que é um comando bot.</span><span class="sxs-lookup"><span data-stu-id="50b06-146">`description`: A short description or example of the syntax and arguments to help users understand what a bot command does.</span></span>

### <a name="app-scaffolding"></a><span data-ttu-id="50b06-147">Aplicativo scaffolding</span><span class="sxs-lookup"><span data-stu-id="50b06-147">App scaffolding</span></span>

<span data-ttu-id="50b06-148">O aplicativo scaffolding fornece um `botActivityHandler.js` arquivo, localizado no diretório raiz do seu projeto, para lidar com o modo como seu bot processa as atividades no Teams (por exemplo, como o bot responde a mensagens específicas como "Hello").</span><span class="sxs-lookup"><span data-stu-id="50b06-148">The app scaffolding provides a `botActivityHandler.js` file, located in the root directory of your project, for handling how your bot processes activities in Teams (for example, how the bot responds to specific messages such as "Hello").</span></span>

## <a name="set-up-a-secure-tunnel-to-your-app"></a><span data-ttu-id="50b06-149">Configurar um túnel seguro para seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="50b06-149">Set up a secure tunnel to your app</span></span>

<span data-ttu-id="50b06-150">Para fins de teste, vamos hospedar seu bot em um servidor Web local (porta 3978).</span><span class="sxs-lookup"><span data-stu-id="50b06-150">For testing purposes, let's host your bot on a local web server (port 3978).</span></span>

1. <span data-ttu-id="50b06-151">Em um terminal, execute `ngrok http -host-header=rewrite 3978` .</span><span class="sxs-lookup"><span data-stu-id="50b06-151">In a terminal, run `ngrok http -host-header=rewrite 3978`.</span></span>
1. <span data-ttu-id="50b06-152">Copie a URL HTTPS na saída, pois o Microsoft Teams requer conexões HTTPS.</span><span class="sxs-lookup"><span data-stu-id="50b06-152">Copy the HTTPS URL in the output since Teams requires HTTPS connections.</span></span>
1. <span data-ttu-id="50b06-153">Em seu `.publish` diretório, abra `Development.env` .</span><span class="sxs-lookup"><span data-stu-id="50b06-153">In your `.publish` directory, open `Development.env`.</span></span>
1. <span data-ttu-id="50b06-154">Substitua o `baseUrl0` valor pela URL copiada.</span><span class="sxs-lookup"><span data-stu-id="50b06-154">Replace the `baseUrl0` value with the copied URL.</span></span> <span data-ttu-id="50b06-155">(Por exemplo, alterar `baseUrl0=http://localhost:3000` para `baseUrl0=https://85528b2b3ca5.ngrok.io` .)</span><span class="sxs-lookup"><span data-stu-id="50b06-155">(For example, change `baseUrl0=http://localhost:3000` to `baseUrl0=https://85528b2b3ca5.ngrok.io`.)</span></span>

<span data-ttu-id="50b06-156">O manifesto do aplicativo está apontando para o local em que você está hospedando o bot.</span><span class="sxs-lookup"><span data-stu-id="50b06-156">Your app manifest is pointing to where you're hosting the bot.</span></span>

## <a name="configuring-your-bot"></a><span data-ttu-id="50b06-157">Configurando o bot</span><span class="sxs-lookup"><span data-stu-id="50b06-157">Configuring your bot</span></span>

<span data-ttu-id="50b06-158">Para usar um bot no Teams, você deve registrá-lo com o serviço de bot do Azure.</span><span class="sxs-lookup"><span data-stu-id="50b06-158">To use a bot in Teams, you must register it with the Azure Bot Service.</span></span> <span data-ttu-id="50b06-159">Sorte para você, isso é feito automaticamente quando você configura seu aplicativo usando o Teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="50b06-159">Lucky for you, this is done automatically when you set up your app using the Teams Toolkit.</span></span>

### <a name="add-the-bot-endpoint-address"></a><span data-ttu-id="50b06-160">Adicionar o endereço do ponto de extremidade do bot</span><span class="sxs-lookup"><span data-stu-id="50b06-160">Add the bot endpoint address</span></span>

<span data-ttu-id="50b06-161">Você deve especificar uma URL de ponto de extremidade para receber e processar mensagens de usuário (ou seja, solicitações) enviadas ao bot.</span><span class="sxs-lookup"><span data-stu-id="50b06-161">You must specify an endpoint URL to receive and process user messages (i.e., requests) sent to the bot.</span></span> <span data-ttu-id="50b06-162">Normalmente, a URL é semelhante `https://HOST_URL/api/messages` .</span><span class="sxs-lookup"><span data-stu-id="50b06-162">Typically, the URL looks like `https://HOST_URL/api/messages`.</span></span> <span data-ttu-id="50b06-163">Você pode configurar isso rapidamente no kit de ferramentas do teams.</span><span class="sxs-lookup"><span data-stu-id="50b06-163">You can configure this quickly in the Teams Toolkit.</span></span>

1. No Visual Studio Code, selecione **Microsoft Teams** :::image type="icon" source="../doc-links/images/vsc-toolkit.png"::: na barra de atividades à esquerda e escolha **abrir o Microsoft Teams Toolkit**.
1. <span data-ttu-id="50b06-165">Vá para **Gerenciamento de bot > registros de bot existentes** e selecione o bot que você criou durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="50b06-165">Go to **Bot management > Existing bot registrations** and select the bot you created during setup.</span></span>
1. <span data-ttu-id="50b06-166">No campo **endereço do ponto de extremidade do bot** , insira o servidor Web local onde você está hospedando o bot e anexe `/api/messages` a ele.</span><span class="sxs-lookup"><span data-stu-id="50b06-166">In the **Bot endpoint address** field, enter the local web server where you're hosting the bot and append `/api/messages` to it.</span></span>

    :::image type="content" source="../doc-links/images/bot-config-endpoint-url.png" alt-text="Ilustração mostrando onde você pode configurar a URL do ponto de extremidade do bot no kit de ferramentas do teams.":::

<span data-ttu-id="50b06-168">Seu bot poderá responder às mensagens no Teams.</span><span class="sxs-lookup"><span data-stu-id="50b06-168">Your bot will be able to respond to messages in Teams.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="50b06-169">Executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="50b06-169">Run your app</span></span>

<span data-ttu-id="50b06-170">Você configurou uma URL para hospedar seu bot e configurá-la para lidar com as mensagens.</span><span class="sxs-lookup"><span data-stu-id="50b06-170">You've set up a URL to host your bot and configured it to handle messages.</span></span> <span data-ttu-id="50b06-171">É hora de colocar o bot em funcionamento.</span><span class="sxs-lookup"><span data-stu-id="50b06-171">It's time to get your bot up and running.</span></span>

1. <span data-ttu-id="50b06-172">Em um terminal, vá para o diretório raiz do seu projeto de aplicativo e execute `npm install` .</span><span class="sxs-lookup"><span data-stu-id="50b06-172">In a terminal, go to the root directory of your app project and run `npm install`.</span></span>
1. <span data-ttu-id="50b06-173">Executar `npm start` .</span><span class="sxs-lookup"><span data-stu-id="50b06-173">Run `npm start`.</span></span>

<span data-ttu-id="50b06-174">Se tiver êxito, você verá algo parecido com a seguinte mensagem, indicando que o seu bot está ouvindo a atividade no seu `localhost` :</span><span class="sxs-lookup"><span data-stu-id="50b06-174">If successful, you see something like the following message indicating your bot is listening for activity at your `localhost`:</span></span>

`Bot/ME service listening at http://localhost:3978`

## <a name="sideload-your-bot-in-teams"></a><span data-ttu-id="50b06-175">Sideload seu bot no Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="50b06-175">Sideload your bot in Teams</span></span>

<span data-ttu-id="50b06-176">Com o bot em execução, você pode instalá-lo no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="50b06-176">With your bot running, you can install it in Teams.</span></span>

> [!TIP]
> <span data-ttu-id="50b06-177">Se você ainda não suplementos foi feito um aplicativo do Microsoft Teams e tiver problemas, siga estas [instruções](../build-your-first-app/build-and-run.md#sideload-your-app-in-teams).</span><span class="sxs-lookup"><span data-stu-id="50b06-177">If you haven't sideloaded a Teams app before and run into issues, follow these [instructions](../build-your-first-app/build-and-run.md#sideload-your-app-in-teams).</span></span>

1. <span data-ttu-id="50b06-178">Faça logon no cliente do teams com sua conta que permita o aplicativo Sideload.</span><span class="sxs-lookup"><span data-stu-id="50b06-178">Log in to the Teams client with your account that allows app sideloading.</span></span>
1. <span data-ttu-id="50b06-179">Selecione **aplicativos**e, em seguida, escolha **carregar um aplicativo personalizado**.</span><span class="sxs-lookup"><span data-stu-id="50b06-179">Select **Apps**, then choose **Upload a custom app**.</span></span>
1. <span data-ttu-id="50b06-180">Vá para a pasta do projeto de aplicativo `.publish` e selecione `Development.zip` .</span><span class="sxs-lookup"><span data-stu-id="50b06-180">Go to your app project `.publish` folder and select `Development.zip`.</span></span>
1. <span data-ttu-id="50b06-181">Na janela instalar, selecione **Adicionar** para instalar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="50b06-181">In the install modal, select **Add** to install your app.</span></span>

## <a name="test-your-bot"></a><span data-ttu-id="50b06-182">Testar o bot</span><span class="sxs-lookup"><span data-stu-id="50b06-182">Test your bot</span></span>

<span data-ttu-id="50b06-183">Agora, para a parte divertida: Vamos dizer "Olá" ao seu bot em um chat de um a um.</span><span class="sxs-lookup"><span data-stu-id="50b06-183">Now for the fun part: Let's say "Hello" to your bot in a one-on-one chat.</span></span>

1. No Teams, selecione **mais** :::image type="icon" source="../doc-links/images/teams-client-more.png"::: no lado esquerdo.
1. <span data-ttu-id="50b06-185">Localize e selecione o bot que você acabou de suplementos foi feito.</span><span class="sxs-lookup"><span data-stu-id="50b06-185">Locate and select the bot you just sideloaded.</span></span><br/>
   :::image type="content" source="../doc-links/images/bot-teams-access.png" alt-text="Ilustração mostrando onde você acessa o bot no Microsoft Teams.":::
1. <span data-ttu-id="50b06-187">Na caixa redigir, envie uma `Hello` mensagem.</span><span class="sxs-lookup"><span data-stu-id="50b06-187">In the compose box, send a `Hello` message.</span></span>

<span data-ttu-id="50b06-188">Seu bot responde com algo como a mensagem a seguir.</span><span class="sxs-lookup"><span data-stu-id="50b06-188">Your bot replies with something like the following message.</span></span>

:::image type="content" source="../doc-links/images/contoso-chatbot.png" alt-text="Uma captura de tela mostrando um usuário diga "Olá" para um bot do Microsoft Teams e obtendo uma resposta de retorno.":::

> [!NOTE]
> <span data-ttu-id="50b06-190">Se você fizer alterações de código após testar o bot — por exemplo, você `botActivityHandler.js` deve executar o aplicativo novamente para ver essas alterações refletidas no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="50b06-190">If you make code changes after testing your bot—for example, you update `botActivityHandler.js`—you must run your app again to see those changes reflected in Teams.</span></span>

## <a name="well-done"></a><span data-ttu-id="50b06-191">Muito bem</span><span class="sxs-lookup"><span data-stu-id="50b06-191">Well done</span></span>

<span data-ttu-id="50b06-192">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="50b06-192">Congratulations!</span></span> <span data-ttu-id="50b06-193">Você tem um bot de equipe básico que pode se comunicar com os usuários, um ou em configurações de grupo (canais e chats).</span><span class="sxs-lookup"><span data-stu-id="50b06-193">You have a basic Teams bot that can communicate with users one-on-one or in group settings (channels and chats).</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="50b06-194">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="50b06-194">Troubleshooting</span></span>

<span data-ttu-id="50b06-195">As informações a seguir podem ajudar se você tiver problemas para concluir este tutorial.</span><span class="sxs-lookup"><span data-stu-id="50b06-195">The following information may help if you had issues completing this tutorial.</span></span>

### <a name="toolkit-setup-fails"></a><span data-ttu-id="50b06-196">Falha na instalação do kit de ferramentas</span><span class="sxs-lookup"><span data-stu-id="50b06-196">Toolkit setup fails</span></span>

<span data-ttu-id="50b06-197">Ao configurar seu projeto de aplicativo com o Teams Toolkit, você recebe um erro depois de selecionar a opção **criar um novo bot** e fazer logon com sua conta de desenvolvimento do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="50b06-197">While setting up your app project with the Teams Toolkit, you get an error after selecting the **Create a new Bot** option and logging in with your Microsoft 365 development account.</span></span>

<span data-ttu-id="50b06-198">Isso pode ser um problema de autenticação.</span><span class="sxs-lookup"><span data-stu-id="50b06-198">This could be an authentication issue.</span></span> <span data-ttu-id="50b06-199">Siga estas etapas para concluir a configuração do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="50b06-199">Follow these steps to finish setting up your project.</span></span>

1. No Visual Studio Code, selecione **Microsoft Teams** :::image type="icon" source="../doc-links/images/vsc-toolkit.png"::: na barra de atividades à esquerda e escolha **sair**.
1. <span data-ttu-id="50b06-201">Execute o processo de instalação novamente, conectando-se com a mesma conta e criando um novo bot.</span><span class="sxs-lookup"><span data-stu-id="50b06-201">Go through the setup process again by logging in with the same account and creating a new bot.</span></span>

### <a name="bot-isnt-connected-to-teams"></a><span data-ttu-id="50b06-202">O bot não está conectado ao Teams</span><span class="sxs-lookup"><span data-stu-id="50b06-202">Bot isn't connected to Teams</span></span>

<span data-ttu-id="50b06-203">Se você instalou seu aplicativo, mas o bot não está funcionando, certifique-se de que o bot está [conectado ao *canal*Teams do serviço de bot do Azure](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="50b06-203">If you installed your app but the bot isn't working, make sure the bot is [connected to the Azure Bot Service's Teams *channel*](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true).</span></span>

<span data-ttu-id="50b06-204">É importante entender que isso não é o mesmo que um canal no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="50b06-204">It's important to understand that this isn't the same as a channel in Teams.</span></span> <span data-ttu-id="50b06-205">Nesse caso, um canal é como o serviço de bot do Azure conecta seu bot ao Teams ou a um [aplicativo de comunicação da Microsoft ou de terceiros com suporte](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="50b06-205">In this case, a channel is how the Azure Bot Service connects your bot to Teams or another [supported Microsoft or third-party communications app](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true).</span></span>

## <a name="learn-more"></a><span data-ttu-id="50b06-206">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="50b06-206">Learn more</span></span>

* [<span data-ttu-id="50b06-207">Veja o que mais os bots de equipe podem fazer com um de nossos exemplos (GitHub)</span><span class="sxs-lookup"><span data-stu-id="50b06-207">See what else Teams bots can do with one of our samples (GitHub)</span></span>](https://github.com/microsoft/BotBuilder-Samples#teams-samples)
* [<span data-ttu-id="50b06-208">Princípios básicos de conversas</span><span class="sxs-lookup"><span data-stu-id="50b06-208">Bot conversation basics</span></span>](../../bots/how-to/conversations/conversation-basics.md)
* [<span data-ttu-id="50b06-209">Autenticação de bot no Teams</span><span class="sxs-lookup"><span data-stu-id="50b06-209">Bot authentication in Teams</span></span>](../../bots/how-to/authentication/auth-flow-bot.md)
* [<span data-ttu-id="50b06-210">Microsoft bot Framework</span><span class="sxs-lookup"><span data-stu-id="50b06-210">Microsoft Bot Framework</span></span>](https://dev.botframework.com/)
