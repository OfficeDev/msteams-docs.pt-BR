---
title: Introdução-criar uma extensão de mensagens
author: heath-hamilton
description: Crie rapidamente uma extensão de mensagens do Microsoft Teams usando o Microsoft Teams Toolkit.
ms.author: lajanuar
ms.date: 09/22/2020
ms.topic: tutorial
ms.openlocfilehash: b19856eacee866ebbc89f21ac12575f1392918b3
ms.sourcegitcommit: d61f14053fc695bc1956bf50e83956613c19ccca
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/13/2020
ms.locfileid: "48452831"
---
# <a name="build-a-messaging-extension-for-microsoft-teams"></a><span data-ttu-id="edef5-103">Criar uma extensão de mensagens para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="edef5-103">Build a messaging extension for Microsoft Teams</span></span>

<span data-ttu-id="edef5-104">Há dois tipos de extensões de *mensagens*do Microsoft Teams: [comandos de pesquisa](../messaging-extensions/how-to/search-commands/define-search-command.md) e [comandos de ação](../messaging-extensions/how-to/action-commands/define-action-command.md).</span><span class="sxs-lookup"><span data-stu-id="edef5-104">There are two types of Teams *messaging extensions*: [Search commands](../messaging-extensions/how-to/search-commands/define-search-command.md) and [action commands](../messaging-extensions/how-to/action-commands/define-action-command.md).</span></span>

<span data-ttu-id="edef5-105">Nesta lição, você criará um *comando de pesquisa* (também conhecido como uma *extensão de mensagens baseada em pesquisa*), que é um atalho para localizar conteúdo externo e compartilhá-lo no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="edef5-105">In this lesson, you'll create a *search command* (also known as a *search-based messaging extension*), which is a shortcut for finding external content and sharing it in Teams.</span></span> <span data-ttu-id="edef5-106">Os usuários podem acessar os comandos de pesquisa a partir da [caixa de comando ou de composição do teams](../messaging-extensions/what-are-messaging-extensions.md).</span><span class="sxs-lookup"><span data-stu-id="edef5-106">Users can access search commands from the [Teams compose or command box](../messaging-extensions/what-are-messaging-extensions.md).</span></span>

## <a name="your-assignment"></a><span data-ttu-id="edef5-107">Sua atribuição</span><span class="sxs-lookup"><span data-stu-id="edef5-107">Your assignment</span></span>

<span data-ttu-id="edef5-108">O suporte técnico da sua organização comunica-se com os usuários por meio do Teams, mas os tíquetes residem em um sistema separado.</span><span class="sxs-lookup"><span data-stu-id="edef5-108">Your organization's help desk communicates with users through Teams, but the tickets reside in a separate system.</span></span> <span data-ttu-id="edef5-109">Isso significa que a equipe de suporte deve continuamente voltar e avançar entre os aplicativos.</span><span class="sxs-lookup"><span data-stu-id="edef5-109">This means support staff must constantly go back and forth between apps.</span></span> <span data-ttu-id="edef5-110">Você investigará como você pode reduzir essa alteração de contexto por meio da criação de uma extensão de mensagens simples baseada em pesquisa para o Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="edef5-110">You'll investigate how you might reduce this much context switching by creating a simple search-based messaging extension for Teams.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="edef5-111">O que você aprenderá</span><span class="sxs-lookup"><span data-stu-id="edef5-111">What you'll learn</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="edef5-112">Criar um projeto de aplicativo e um bot de extensão de mensagens usando o Microsoft Teams Toolkit para o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="edef5-112">Create an app project and messaging extension bot using the Microsoft Teams Toolkit for Visual Studio Code</span></span>
> * <span data-ttu-id="edef5-113">Identificar as propriedades de manifesto do aplicativo e alguns dos scaffolding relevantes para as extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="edef5-113">Identify the app manifest properties and some of the scaffolding relevant to messaging extensions</span></span>
> * <span data-ttu-id="edef5-114">Hospedar um aplicativo localmente</span><span class="sxs-lookup"><span data-stu-id="edef5-114">Host an app locally</span></span>
> * <span data-ttu-id="edef5-115">Configurar o bot para sua extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="edef5-115">Configure the bot for your messaging extension</span></span>
> * <span data-ttu-id="edef5-116">Sideload e testar uma extensão de mensagens no Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="edef5-116">Sideload and test a messaging extension in Teams</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="edef5-117">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="edef5-117">Before you begin</span></span>

<span data-ttu-id="edef5-118">Se você ainda não tiver feito isso, não se esqueça de [entender e instalar os pré-requisitos de desenvolvimento do teams](build-first-app-overview.md#get-prerequisites).</span><span class="sxs-lookup"><span data-stu-id="edef5-118">If you haven't yet, make sure you [understand and install the Teams development prerequisites](build-first-app-overview.md#get-prerequisites).</span></span>

## <a name="1-create-your-app-project"></a><span data-ttu-id="edef5-119">1. criar seu projeto de aplicativo</span><span class="sxs-lookup"><span data-stu-id="edef5-119">1. Create your app project</span></span>

<span data-ttu-id="edef5-120">O Microsoft Teams Toolkit ajuda você a configurar os seguintes componentes para sua extensão de mensagens:</span><span class="sxs-lookup"><span data-stu-id="edef5-120">The Microsoft Teams Toolkit helps you set up the following components for your messaging extension:</span></span>

* <span data-ttu-id="edef5-121">**Manifesto de aplicativo e scaffolding** relevantes para extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="edef5-121">**App manifest and scaffolding** relevant to messaging extensions</span></span>
* <span data-ttu-id="edef5-122">**Bot** para sua extensão de mensagens que é automaticamente registrado com o serviço de bot do Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="edef5-122">**Bot** for your messaging extension that's automatically registered with the Microsoft Azure Bot Service</span></span>

> [!TIP]
> <span data-ttu-id="edef5-123">Se você ainda não criou um projeto de aplicativos do Microsoft Teams, talvez ache útil seguir [estas instruções](../build-your-first-app/build-and-run.md) para explicar os projetos com mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="edef5-123">If you haven't created a Teams app project before, you might find it helpful to follow [these instructions](../build-your-first-app/build-and-run.md) that explain projects in more detail.</span></span>

1. No Visual Studio Code, selecione **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: na barra de atividades à esquerda e escolha **criar um novo aplicativo Teams**.
1. <span data-ttu-id="edef5-125">Insira um nome para seu aplicativo do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="edef5-125">Enter a name for your Teams app.</span></span> <span data-ttu-id="edef5-126">(Esse é o nome padrão para seu aplicativo e também o nome do diretório do projeto de aplicativo em sua máquina local.)</span><span class="sxs-lookup"><span data-stu-id="edef5-126">(This is the default name for your app and also the name of the app project directory on your local machine.)</span></span>
1. <span data-ttu-id="edef5-127">Na tela **Adicionar recursos** , selecione **extensão de mensagens** e **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="edef5-127">On the **Add capabilities** screen, select **Messaging Extension** then **Next**.</span></span>
1. <span data-ttu-id="edef5-128">Na tela **Configurar extensão de mensagens** , faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="edef5-128">On the **Configure messaging extension** screen, do the following:</span></span>
    1. <span data-ttu-id="edef5-129">Escolha somente a opção **baseado em pesquisa** para o tipo de extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="edef5-129">Choose only the **Search-based** option for the type of messaging extension.</span></span>
    1. <span data-ttu-id="edef5-130">Selecione **criar um novo bot** e **login** para entrar com sua conta de desenvolvimento do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="edef5-130">Select **Create a new Bot** and **Login** to sign in with your Microsoft 365 development account.</span></span>
    1. <span data-ttu-id="edef5-131">Armazene sua ID de bot e senha (você precisará de um pouco mais tarde).</span><span class="sxs-lookup"><span data-stu-id="edef5-131">Store your bot ID and password (you need this a little later).</span></span>
    1. <span data-ttu-id="edef5-132">Opcion Insira um nome personalizado para o bot e selecione **criar**.</span><span class="sxs-lookup"><span data-stu-id="edef5-132">(Optional) Enter a custom name for your bot and select **Create**.</span></span> <span data-ttu-id="edef5-133">(Este não é o nome do aplicativo Teams que você já especificou.)</span><span class="sxs-lookup"><span data-stu-id="edef5-133">(This is not the name of the Teams app you already specified.)</span></span>
    1. <span data-ttu-id="edef5-134">Selecione **não** para a opção vincular Unfurling.</span><span class="sxs-lookup"><span data-stu-id="edef5-134">For now, select **No** for the link unfurling option.</span></span></br>
:::image type="content" source="../assets/images/build-your-first-app/choose-me-search.png" alt-text="Ilustração mostrando como, no Teams Toolkit, para fazer logon na sua conta do Microsoft 365 para criar um novo bot para sua extensão de mensagens.":::
1. <span data-ttu-id="edef5-136">Selecione **concluir** na parte inferior da tela para configurar seu projeto.</span><span class="sxs-lookup"><span data-stu-id="edef5-136">Select **Finish** at the bottom of the screen to configure your project.</span></span>

## <a name="2-identify-relevant-app-project-components"></a><span data-ttu-id="edef5-137">2. identificar componentes de projeto de aplicativo relevantes</span><span class="sxs-lookup"><span data-stu-id="edef5-137">2. Identify relevant app project components</span></span>

<span data-ttu-id="edef5-138">Grande parte do manifesto do aplicativo e do scaffolding são configuradas automaticamente quando você cria seu projeto com o Teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="edef5-138">Much of the app manifest and scaffolding are set up automatically when you create your project with the Teams Toolkit.</span></span>

### <a name="app-manifest"></a><span data-ttu-id="edef5-139">Manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="edef5-139">App manifest</span></span>

<span data-ttu-id="edef5-140">O trecho de código a seguir do manifesto do aplicativo (o `manifest.json` arquivo no diretório do seu projeto `.publish` ) mostra as propriedades e os valores padrão relevantes para as extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="edef5-140">The following snippet from the app manifest (the `manifest.json` file in your project's `.publish` directory) shows the properties and default values relevant to messaging extensions.</span></span>

```JSON
"composeExtensions": [
    {
        "botId": "{botId0}",
        "canUpdateConfiguration": true,
        "commands": [
            {
                "id": "searchQuery",
                "context": [
                    "compose",
                    "commandBox"
                ],
                "description": "Test command to run query",
                "title": "Search",
                "type": "query",
                "parameters": [
                    {
                        "name": "searchQuery",
                        "title": "Search Query",
                        "description": "Your search query",
                        "inputType": "text"
                    }
                ]
            }
        ]
    }
],
```

<span data-ttu-id="edef5-141">Vamos entender algumas das propriedades que o kit de ferramentas criou para você.</span><span class="sxs-lookup"><span data-stu-id="edef5-141">Let's understand some of the properties the toolkit created for you.</span></span> <span data-ttu-id="edef5-142">(Veja a lista completa de propriedades com suporte [`composeExtensions`](../resources/schema/manifest-schema.md#composeextensions) .)</span><span class="sxs-lookup"><span data-stu-id="edef5-142">(See the full list of supported [`composeExtensions`](../resources/schema/manifest-schema.md#composeextensions) properties.)</span></span>

* <span data-ttu-id="edef5-143">`botId`: A ID do bot que você criou configurando seu projeto.</span><span class="sxs-lookup"><span data-stu-id="edef5-143">`botId`: The ID of the bot you created setting up your project.</span></span> <span data-ttu-id="edef5-144">(Armazenado no `{botId0}` , você pode encontrar a ID real no `Development.env` .)</span><span class="sxs-lookup"><span data-stu-id="edef5-144">(Stored in `{botId0}`, you can find the actual ID in `Development.env`.)</span></span>
* <span data-ttu-id="edef5-145">`commands`: Comandos disponíveis para a extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="edef5-145">`commands`: Available commands for the messaging extension.</span></span> <span data-ttu-id="edef5-146">O kit de ferramentas ofereceu a você scaffolding um comando de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="edef5-146">The toolkit provided you scaffolding for a search command.</span></span>
* <span data-ttu-id="edef5-147">`context`: Onde os usuários podem invocar a extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="edef5-147">`context`: Where users can invoke the messaging extension.</span></span> <span data-ttu-id="edef5-148">Nesse caso, você pode iniciar a extensão de mensagens da caixa de comando ou de composição do teams.</span><span class="sxs-lookup"><span data-stu-id="edef5-148">In this case, you can launch the messaging extension from the Teams compose or command box.</span></span>
* <span data-ttu-id="edef5-149">`description`: Texto de ajuda da interface do usuário que indica o que o comando faz ou como usá-lo.</span><span class="sxs-lookup"><span data-stu-id="edef5-149">`description`: UI help text indicating what the command does or how to use it.</span></span>
* <span data-ttu-id="edef5-150">`parameters`: Inclui todos os parâmetros aceitos por um comando (você deve ter pelo menos um e até cinco).</span><span class="sxs-lookup"><span data-stu-id="edef5-150">`parameters`: Includes all parameters a command accepts (you must have at least one and can have up to five).</span></span>
* <span data-ttu-id="edef5-151">`parameters.description`: O texto da ajuda da interface do usuário que descreve a finalidade do parâmetro ou a entrada de exemplo.</span><span class="sxs-lookup"><span data-stu-id="edef5-151">`parameters.description`: UI help text describing the parameter's purpose or example input.</span></span>

### <a name="app-scaffolding"></a><span data-ttu-id="edef5-152">Aplicativo scaffolding</span><span class="sxs-lookup"><span data-stu-id="edef5-152">App scaffolding</span></span>

<span data-ttu-id="edef5-153">O aplicativo scaffolding inclui um `.env` arquivo, localizado no diretório raiz do seu projeto, que armazena a ID e a senha do bot da extensão do sistema de mensagens.</span><span class="sxs-lookup"><span data-stu-id="edef5-153">The app scaffolding includes a `.env` file, located in the root directory of your project, which stores the ID and password of your messaging extension's bot.</span></span>

<span data-ttu-id="edef5-154">Além disso, no diretório raiz, há um `botActivityHandler.js` arquivo para lidar com a sua extensão de mensagens (ou tecnicamente, o [bot da extensão de mensagens](#4-configure-the-bot-for-your-messaging-extension)) responde a consultas de pesquisa no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="edef5-154">Also in the root directory, there's a `botActivityHandler.js` file for handling how your messaging extension (or technically, the [messaging extension's bot](#4-configure-the-bot-for-your-messaging-extension)) responds to search queries in Teams.</span></span>

## <a name="3-set-up-a-secure-tunnel-to-your-app"></a><span data-ttu-id="edef5-155">3. configurar um túnel seguro para seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="edef5-155">3. Set up a secure tunnel to your app</span></span>

<span data-ttu-id="edef5-156">Para fins de teste, vamos hospedar sua extensão de mensagens em um servidor Web local (porta 3978).</span><span class="sxs-lookup"><span data-stu-id="edef5-156">For testing purposes, let's host your messaging extension on a local web server (port 3978).</span></span>

1. <span data-ttu-id="edef5-157">Em um terminal, execute `ngrok http -host-header=rewrite 3978` .</span><span class="sxs-lookup"><span data-stu-id="edef5-157">In a terminal, run `ngrok http -host-header=rewrite 3978`.</span></span>
1. <span data-ttu-id="edef5-158">Copie a URL HTTPS na saída, pois o Microsoft Teams requer conexões HTTPS.</span><span class="sxs-lookup"><span data-stu-id="edef5-158">Copy the HTTPS URL in the output since Teams requires HTTPS connections.</span></span>
1. <span data-ttu-id="edef5-159">Em seu `.publish` diretório, abra `Development.env` .</span><span class="sxs-lookup"><span data-stu-id="edef5-159">In your `.publish` directory, open `Development.env`.</span></span>
1. <span data-ttu-id="edef5-160">Substitua o `baseUrl0` valor pela URL copiada.</span><span class="sxs-lookup"><span data-stu-id="edef5-160">Replace the `baseUrl0` value with the copied URL.</span></span> <span data-ttu-id="edef5-161">(Por exemplo, alterar `baseUrl0=http://localhost:3000` para `baseUrl0=https://85528b2b3ca5.ngrok.io` .)</span><span class="sxs-lookup"><span data-stu-id="edef5-161">(For example, change `baseUrl0=http://localhost:3000` to `baseUrl0=https://85528b2b3ca5.ngrok.io`.)</span></span>

<span data-ttu-id="edef5-162">O manifesto do aplicativo está apontando para o local em que você está hospedando o bot usado pela extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="edef5-162">Your app manifest is pointing to where you're hosting the bot used by the messaging extension.</span></span>

## <a name="4-configure-the-bot-for-your-messaging-extension"></a><span data-ttu-id="edef5-163">4. Configure o bot para sua extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="edef5-163">4. Configure the bot for your messaging extension</span></span>

<span data-ttu-id="edef5-164">As extensões de mensagens dependem de bots para enviar e processar solicitações de usuário do teams para seu serviço hospedado.</span><span class="sxs-lookup"><span data-stu-id="edef5-164">Messaging extensions rely on bots to send and process user requests from Teams to your hosted service.</span></span>

<span data-ttu-id="edef5-165">O bot deve ser registrado no serviço do Azure bot, que foi feito quando você configurou seu aplicativo usando o Teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="edef5-165">The bot must be registered with the Azure Bot Service, which was done when you set up your app using the Teams Toolkit.</span></span>

### <a name="specify-your-bot-id-and-password"></a><span data-ttu-id="edef5-166">Especificar a ID e a senha do bot</span><span class="sxs-lookup"><span data-stu-id="edef5-166">Specify your bot ID and password</span></span>

<span data-ttu-id="edef5-167">Quando o bot é registrado com o serviço de bot do Azure, é atribuída uma ID e uma senha que o aplicativo de equipes deve conhecer.</span><span class="sxs-lookup"><span data-stu-id="edef5-167">When your bot is registered with the Azure Bot Service, it's assigned an ID and password that your Teams app must know about.</span></span>

1. <span data-ttu-id="edef5-168">Localize a ID e a senha do bot que você armazenou durante a instalação do kit de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="edef5-168">Locate the bot ID and password you stored during toolkit setup.</span></span>
1. <span data-ttu-id="edef5-169">No diretório raiz, abra o `.env` arquivo.</span><span class="sxs-lookup"><span data-stu-id="edef5-169">In your root directory, open the `.env` file.</span></span>
1. <span data-ttu-id="edef5-170">Defina sua ID de bot e senha para `BotId` as `BotPassword` Propriedades e, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="edef5-170">Set your bot ID and password to the `BotId` and `BotPassword` properties, respectively.</span></span>

### <a name="add-the-bot-endpoint-address"></a><span data-ttu-id="edef5-171">Adicionar o endereço do ponto de extremidade do bot</span><span class="sxs-lookup"><span data-stu-id="edef5-171">Add the bot endpoint address</span></span>

<span data-ttu-id="edef5-172">Você deve especificar uma URL de ponto de extremidade de bot para receber e processar consultas de pesquisa em sua extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="edef5-172">You must specify a bot endpoint URL to receive and process search queries in your messaging extension.</span></span> <span data-ttu-id="edef5-173">Normalmente, a URL é semelhante `https://HOST_URL/api/messages` .</span><span class="sxs-lookup"><span data-stu-id="edef5-173">Typically, the URL looks like `https://HOST_URL/api/messages`.</span></span> <span data-ttu-id="edef5-174">Você pode configurar isso rapidamente no kit de ferramentas do teams.</span><span class="sxs-lookup"><span data-stu-id="edef5-174">You can configure this quickly in the Teams Toolkit.</span></span>

1. No Visual Studio Code, selecione **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: na barra de atividades à esquerda e escolha **abrir o Microsoft Teams Toolkit**.
1. <span data-ttu-id="edef5-176">Vá para **Gerenciamento de bot > registros de bot existentes** e selecione o bot que você criou durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="edef5-176">Go to **Bot management > Existing bot registrations** and select the bot you created during setup.</span></span>
1. <span data-ttu-id="edef5-177">No campo **endereço do ponto de extremidade do bot** , insira o servidor Web local onde você está hospedando o bot ( `baseUrl10` valor) e anexe `/api/messages` a ele.</span><span class="sxs-lookup"><span data-stu-id="edef5-177">In the **Bot endpoint address** field, enter the local web server where you're hosting the bot (`baseUrl10` value) and append `/api/messages` to it.</span></span>

<span data-ttu-id="edef5-178">O bot será capaz de lidar com consultas em sua extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="edef5-178">Your bot will be able to handle queries in your messaging extension.</span></span>

## <a name="5-run-your-app"></a><span data-ttu-id="edef5-179">5. Execute o aplicativo</span><span class="sxs-lookup"><span data-stu-id="edef5-179">5. Run your app</span></span>

<span data-ttu-id="edef5-180">Você configurou uma URL para hospedar sua extensão de mensagens e configurá-la para lidar com pesquisas.</span><span class="sxs-lookup"><span data-stu-id="edef5-180">You've set up a URL to host your messaging extension and configured it to handle searches.</span></span> <span data-ttu-id="edef5-181">É hora de colocar seu aplicativo em funcionamento.</span><span class="sxs-lookup"><span data-stu-id="edef5-181">It's time to get your app up and running.</span></span>

1. <span data-ttu-id="edef5-182">Em um terminal, vá para o diretório raiz do seu projeto de aplicativo e execute `npm install` .</span><span class="sxs-lookup"><span data-stu-id="edef5-182">In a terminal, go to the root directory of your app project and run `npm install`.</span></span>
1. <span data-ttu-id="edef5-183">Executar `npm start` .</span><span class="sxs-lookup"><span data-stu-id="edef5-183">Run `npm start`.</span></span>

<span data-ttu-id="edef5-184">Se tiver êxito, você verá algo parecido com a seguinte mensagem, indicando que o serviço de extensão de mensagens está ouvindo a atividade no seu `localhost` :</span><span class="sxs-lookup"><span data-stu-id="edef5-184">If successful, you see something like the following message indicating your messaging extension service is listening for activity at your `localhost`:</span></span>

`Bot/ME service listening at http://localhost:3978`

## <a name="6-sideload-your-messaging-extension-in-teams"></a><span data-ttu-id="edef5-185">6. Sideload sua extensão de mensagens no Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="edef5-185">6. Sideload your messaging extension in Teams</span></span>

<span data-ttu-id="edef5-186">Com sua extensão de mensagens em execução, você pode instalá-lo no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="edef5-186">With your messaging extension running, you can install it in Teams.</span></span>

> [!TIP]
> <span data-ttu-id="edef5-187">Se você ainda não suplementos foi feito um aplicativo do Microsoft Teams e tiver problemas, siga estas [instruções](../build-your-first-app/build-and-run.md#5-sideload-your-app-in-teams).</span><span class="sxs-lookup"><span data-stu-id="edef5-187">If you haven't sideloaded a Teams app before and run into issues, follow these [instructions](../build-your-first-app/build-and-run.md#5-sideload-your-app-in-teams).</span></span>

1. <span data-ttu-id="edef5-188">Faça logon no cliente do teams com sua conta que permita o aplicativo Sideload.</span><span class="sxs-lookup"><span data-stu-id="edef5-188">Log in to the Teams client with your account that allows app sideloading.</span></span>
1. <span data-ttu-id="edef5-189">Selecione **aplicativos**e, em seguida, escolha **carregar um aplicativo personalizado**.</span><span class="sxs-lookup"><span data-stu-id="edef5-189">Select **Apps**, then choose **Upload a custom app**.</span></span>
1. <span data-ttu-id="edef5-190">Vá para a pasta do projeto de aplicativo `.publish` e selecione `Development.zip` .</span><span class="sxs-lookup"><span data-stu-id="edef5-190">Go to your app project `.publish` folder and select `Development.zip`.</span></span>
1. <span data-ttu-id="edef5-191">Na janela instalar, selecione **Adicionar** para instalar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="edef5-191">In the install modal, select **Add** to install your app.</span></span>

## <a name="7-test-your-messaging-extension"></a><span data-ttu-id="edef5-192">7. testar sua extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="edef5-192">7. Test your messaging extension</span></span>

<span data-ttu-id="edef5-193">Saiba como as extensões de mensagens funcionam em um chat do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="edef5-193">Learn how messaging extensions work in a Teams chat.</span></span>

1. <span data-ttu-id="edef5-194">Inicie um novo chat.</span><span class="sxs-lookup"><span data-stu-id="edef5-194">Start a new chat.</span></span> Na caixa redigir e selecione **mais** :::image type="icon" source="../assets/icons/teams-client-more.png"::: e escolha o aplicativo de extensão de mensagens que você acabou de suplementos foi feito.<br/>
   :::image type="content" source="../assets/images/build-your-first-app/me-teams-access.png" alt-text="Ilustração mostrando como, no Teams Toolkit, para fazer logon na sua conta do Microsoft 365 para criar um novo bot para sua extensão de mensagens.":::
1. <span data-ttu-id="edef5-197">Tente pesquisar algo (por exemplo, "bilhetes").</span><span class="sxs-lookup"><span data-stu-id="edef5-197">Try searching for something (for example, "Tickets").</span></span> <span data-ttu-id="edef5-198">Se seu aplicativo estiver funcionando, você verá resultados de pesquisa de exemplo (você pode adicionar o seu próprio mais tarde).</span><span class="sxs-lookup"><span data-stu-id="edef5-198">If your app is working, you'll see sample search results (you can add your own later).</span></span><br/>
   :::image type="content" source="../assets/images/build-your-first-app/me-teams-test.png" alt-text="Ilustração mostrando como, no Teams Toolkit, para fazer logon na sua conta do Microsoft 365 para criar um novo bot para sua extensão de mensagens.":::

## <a name="well-done"></a><span data-ttu-id="edef5-200">Muito bem</span><span class="sxs-lookup"><span data-stu-id="edef5-200">Well done</span></span>

<span data-ttu-id="edef5-201">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="edef5-201">Congratulations!</span></span> <span data-ttu-id="edef5-202">Você tem uma extensão de mensagens básica do teams que está configurada para pesquisar conteúdo externo na caixa redigir ou comando.</span><span class="sxs-lookup"><span data-stu-id="edef5-202">You have a basic Teams messaging extension that's set up to search for external content in the compose or command box.</span></span>

## <a name="next-steps"></a><span data-ttu-id="edef5-203">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="edef5-203">Next steps</span></span>

<span data-ttu-id="edef5-204">Confira as seguintes páginas para continuar e criar uma extensão de mensagens totalmente em destaque:</span><span class="sxs-lookup"><span data-stu-id="edef5-204">See the following pages to continue and build a fully featured messaging extension:</span></span>

1. <span data-ttu-id="edef5-205">[Definir comandos de pesquisa](../messaging-extensions/how-to/search-commands/define-search-command.md) que são relevantes para o serviço.</span><span class="sxs-lookup"><span data-stu-id="edef5-205">[Define search commands](../messaging-extensions/how-to/search-commands/define-search-command.md) that are relevant to your service.</span></span>
1. <span data-ttu-id="edef5-206">Configure seu serviço para [responder às pesquisas dos usuários](../messaging-extensions/how-to/search-commands/respond-to-search.md).</span><span class="sxs-lookup"><span data-stu-id="edef5-206">Configure your service to [respond to users' searches](../messaging-extensions/how-to/search-commands/respond-to-search.md).</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="edef5-207">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="edef5-207">Troubleshooting</span></span>

<span data-ttu-id="edef5-208">As informações a seguir podem ajudar se você tiver problemas para concluir este tutorial.</span><span class="sxs-lookup"><span data-stu-id="edef5-208">The following information may help if you had issues completing this tutorial.</span></span>

### <a name="toolkit-setup-fails"></a><span data-ttu-id="edef5-209">Falha na instalação do kit de ferramentas</span><span class="sxs-lookup"><span data-stu-id="edef5-209">Toolkit setup fails</span></span>

<span data-ttu-id="edef5-210">Ao configurar seu projeto de aplicativo com o Teams Toolkit, você recebe um erro depois de selecionar a opção **criar um novo bot** e fazer logon com sua conta de desenvolvimento do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="edef5-210">While setting up your app project with the Teams Toolkit, you get an error after selecting the **Create a new Bot** option and logging in with your Microsoft 365 development account.</span></span>

<span data-ttu-id="edef5-211">Isso pode ser um problema de autenticação.</span><span class="sxs-lookup"><span data-stu-id="edef5-211">This could be an authentication issue.</span></span> <span data-ttu-id="edef5-212">Siga estas etapas para concluir a configuração do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="edef5-212">Follow these steps to finish setting up your project.</span></span>

1. No Visual Studio Code, selecione **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: na barra de atividades à esquerda e escolha **sair**.
1. <span data-ttu-id="edef5-214">Execute o processo de instalação novamente, conectando-se com a mesma conta e criando um novo bot.</span><span class="sxs-lookup"><span data-stu-id="edef5-214">Go through the setup process again by logging in with the same account and creating a new bot.</span></span>

### <a name="bot-isnt-connected-to-teams"></a><span data-ttu-id="edef5-215">O bot não está conectado ao Teams</span><span class="sxs-lookup"><span data-stu-id="edef5-215">Bot isn't connected to Teams</span></span>

<span data-ttu-id="edef5-216">Se você instalou o aplicativo, mas não está funcionando, certifique-se de que o bot da extensão de mensagens está [conectado ao *canal*da equipe do serviço de bot do Azure](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="edef5-216">If you installed your app but it isn't working, make sure the messaging extension's bot is [connected to the Azure Bot Service's Teams *channel*](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true).</span></span>

<span data-ttu-id="edef5-217">É importante entender que isso não é o mesmo que um canal no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="edef5-217">It's important to understand that this isn't the same as a channel in Teams.</span></span> <span data-ttu-id="edef5-218">Nesse caso, um canal é como o serviço de bot do Azure conecta seu bot ao Teams ou a um [aplicativo de comunicação da Microsoft ou de terceiros com suporte](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="edef5-218">In this case, a channel is how the Azure Bot Service connects your bot to Teams or another [supported Microsoft or third-party communications app](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true).</span></span>

## <a name="learn-more"></a><span data-ttu-id="edef5-219">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="edef5-219">Learn more</span></span>

* [<span data-ttu-id="edef5-220">Incluir um recurso de Unfurling de link</span><span class="sxs-lookup"><span data-stu-id="edef5-220">Include a link unfurling feature</span></span>](../messaging-extensions/how-to/link-unfurling.md)
* [<span data-ttu-id="edef5-221">Adicionar autenticação</span><span class="sxs-lookup"><span data-stu-id="edef5-221">Add authentication</span></span>](../messaging-extensions/how-to/add-authentication.md)
* [<span data-ttu-id="edef5-222">Criar uma extensão de mensagens baseada na ação</span><span class="sxs-lookup"><span data-stu-id="edef5-222">Create an action-based messaging extension</span></span>](../messaging-extensions/how-to/action-commands/define-action-command.md)
* [<span data-ttu-id="edef5-223">Microsoft bot Framework</span><span class="sxs-lookup"><span data-stu-id="edef5-223">Microsoft Bot Framework</span></span>](https://dev.botframework.com/)
