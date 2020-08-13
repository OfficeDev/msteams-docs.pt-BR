---
title: Criar e executar seu primeiro aplicativo do Microsoft Teams
author: heath-hamilton
description: Execute seu primeiro aplicativo do Microsoft Teams.
ms.openlocfilehash: 98af8d8d6d89007e36c24bd34661ec21b33cbdf1
ms.sourcegitcommit: 9fbc701a9a039ecdc360aefbe86df52b9c3593f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/12/2020
ms.locfileid: "46651862"
---
# <a name="build-and-run-your-first-microsoft-teams-app"></a><span data-ttu-id="51b33-103">Criar e executar seu primeiro aplicativo do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="51b33-103">Build and run your first Microsoft Teams app</span></span>

<span data-ttu-id="51b33-104">Você pode ir diretamente para o desenvolvimento na plataforma do Microsoft Teams, criando e executando rapidamente um aplicativo básico.</span><span class="sxs-lookup"><span data-stu-id="51b33-104">You can jump right into developing on the Microsoft Teams platform by quickly building and running a basic app.</span></span>

> [!NOTE]
> <span data-ttu-id="51b33-105">É útil ter conhecimento de trabalho do JavaScript (reagir especificamente) ao seguir estes tutoriais.</span><span class="sxs-lookup"><span data-stu-id="51b33-105">It's helpful to have working knowledge of JavaScript (specifically React) when following these tutorials.</span></span>

## <a name="set-up-your-development-account"></a><span data-ttu-id="51b33-106">Configurar sua conta de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="51b33-106">Set up your development account</span></span>

<span data-ttu-id="51b33-107">Para criar aplicativos para o Microsoft Teams, você precisa de uma conta do Microsoft Teams que permite o Sideload (sua conta já pode fornecer isso).</span><span class="sxs-lookup"><span data-stu-id="51b33-107">To build apps for Teams, you need a Teams account that allows sideloading (your account may already provide this).</span></span> <span data-ttu-id="51b33-108">Caso contrário, registre-se para uma assinatura de desenvolvedor do Microsoft 365 para que você possa obter um locatário de teste.</span><span class="sxs-lookup"><span data-stu-id="51b33-108">If it doesn't, register for a Microsoft 365 developer subscription so you can get a test tenant.</span></span>

1. <span data-ttu-id="51b33-109">Verifique se você pode Sideload aplicativos no Microsoft Teams:</span><span class="sxs-lookup"><span data-stu-id="51b33-109">Verify if you can sideload apps in Teams:</span></span>
    1. <span data-ttu-id="51b33-110">No cliente do Microsoft Teams, selecione **aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="51b33-110">In the Teams client, select **Apps**.</span></span>
    1. <span data-ttu-id="51b33-111">Procure uma opção para **carregar um aplicativo personalizado**.</span><span class="sxs-lookup"><span data-stu-id="51b33-111">Look for an option to **Upload a custom app**.</span></span>
1. <span data-ttu-id="51b33-112">Se você tiver essa opção, pode começar a criar.</span><span class="sxs-lookup"><span data-stu-id="51b33-112">If you have this option, you can start building.</span></span> <span data-ttu-id="51b33-113">Caso contrário, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="51b33-113">If not, do the following:</span></span>
    1. <span data-ttu-id="51b33-114">Registre-se para uma [assinatura de desenvolvedor do Microsoft 365](../doc-links/prepare-your-o365-tenant.md).</span><span class="sxs-lookup"><span data-stu-id="51b33-114">Register for a [Microsoft 365 developer subscription](../doc-links/prepare-your-o365-tenant.md).</span></span>
    1. <span data-ttu-id="51b33-115">[Habilitar o Sideload de aplicativos personalizado](../doc-links/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading) para sua conta de teste.</span><span class="sxs-lookup"><span data-stu-id="51b33-115">[Enable custom app sideloading](../doc-links/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading) for your test account.</span></span>

## <a name="get-your-development-tools"></a><span data-ttu-id="51b33-116">Obtenha suas ferramentas de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="51b33-116">Get your development tools</span></span>

<span data-ttu-id="51b33-117">Você pode criar aplicativos do teams com suas ferramentas preferidas, mas aqui está o que você precisa para começar rapidamente com o Visual Studio Code e o Microsoft Teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="51b33-117">You can build Teams apps with your preferred tools, but here's what you need to get started quickly with Visual Studio Code and the Microsoft Teams Toolkit.</span></span>

1. <span data-ttu-id="51b33-118">Instale a versão mais recente do [Visual Studio Code](https://code.visualstudio.com/download).</span><span class="sxs-lookup"><span data-stu-id="51b33-118">Install the latest version of [Visual Studio Code](https://code.visualstudio.com/download).</span></span>
1. <span data-ttu-id="51b33-119">No Visual Studio Code, selecione **Extensions** ![ Visual Studio Toolkit View ](../doc-links/images/vs-code-extensions.png) na barra de atividades à esquerda e instale o **Microsoft Teams Toolkit**.</span><span class="sxs-lookup"><span data-stu-id="51b33-119">In Visual Studio Code, select **Extensions** ![visual studio toolkit view](../doc-links/images/vs-code-extensions.png) on the left Activity Bar and install the **Microsoft Teams Toolkit**.</span></span>
1. <span data-ttu-id="51b33-120">Instale o [Node.js](https://nodejs.org/en/).</span><span class="sxs-lookup"><span data-stu-id="51b33-120">Install [Node.js](https://nodejs.org/en/).</span></span>

## <a name="create-an-app-project"></a><span data-ttu-id="51b33-121">Criar um projeto de aplicativo</span><span class="sxs-lookup"><span data-stu-id="51b33-121">Create an app project</span></span>

<span data-ttu-id="51b33-122">O Microsoft Teams Toolkit pode ajudar você a configurar seu primeiro projeto de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="51b33-122">The Microsoft Teams Toolkit can help you set up your first app project.</span></span>

1. <span data-ttu-id="51b33-123">No Visual Studio Code, abra o kit de ferramentas selecionando o ícone do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="51b33-123">In Visual Studio Code, open the toolkit by selecting the Teams icon</span></span> ![ícone do teams](../doc-links/images/favicon-16x16.png) <span data-ttu-id="51b33-125">na barra de atividades à esquerda.</span><span class="sxs-lookup"><span data-stu-id="51b33-125">on the left Activity Bar.</span></span>
1. <span data-ttu-id="51b33-126">Selecione **criar um novo aplicativo do teams**.</span><span class="sxs-lookup"><span data-stu-id="51b33-126">Select **Create a new Teams app**.</span></span>
1. <span data-ttu-id="51b33-127">Quando solicitado, insira um nome para o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="51b33-127">When prompted, enter a name for your app.</span></span> <span data-ttu-id="51b33-128">Este é o nome padrão para seu aplicativo e também o nome do diretório do projeto em sua máquina local.</span><span class="sxs-lookup"><span data-stu-id="51b33-128">This is the default name for your app and also the name of the project directory on your local machine.</span></span>
1. <span data-ttu-id="51b33-129">Na tela **Adicionar recursos** , selecione **Tab** e **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="51b33-129">On the **Add capabilities** screen, select **Tab** then **Next**.</span></span>
1. <span data-ttu-id="51b33-130">Marque a opção **guia pessoal** e selecione **concluir** para configurar seu projeto.</span><span class="sxs-lookup"><span data-stu-id="51b33-130">Check the **Personal tab** option and select **Finish** to configure your project.</span></span>

![Kit de ferramentas Adicionar exibição de guias](../doc-links/images/toolkit-add-tabs.PNG)

<span data-ttu-id="51b33-132">Após a conclusão, você tem os componentes de scaffolding de aplicativo para criar uma guia pessoal.</span><span class="sxs-lookup"><span data-stu-id="51b33-132">Once complete, you have the app scaffolding components for building a personal tab.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="51b33-133">Executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="51b33-133">Run your app</span></span>

<span data-ttu-id="51b33-134">Siga o `README.md` em seu projeto para compilar, executar e implantar seu aplicativo no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="51b33-134">Follow the `README.md` in your project to build, run, and deploy your app to Teams.</span></span> <span data-ttu-id="51b33-135">Em geral, essas instruções ajudam você a fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="51b33-135">In general, these instructions help you do the following:</span></span>

* <span data-ttu-id="51b33-136">Hospedar o aplicativo `localhost` .</span><span class="sxs-lookup"><span data-stu-id="51b33-136">Host your app on `localhost`.</span></span>
* <span data-ttu-id="51b33-137">[Configure um túnel seguro com o ngrok](../doc-links/debug.md#locally-hosted) para que o Microsoft Teams possa acessar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="51b33-137">[Set up a secure tunnel with ngrok](../doc-links/debug.md#locally-hosted) so that Teams can access your app.</span></span> <span data-ttu-id="51b33-138">(Instale o [ngrok](https://ngrok.com/download).)</span><span class="sxs-lookup"><span data-stu-id="51b33-138">(Install [ngrok](https://ngrok.com/download).)</span></span>
* <span data-ttu-id="51b33-139">[Sideload seu aplicativo](../doc-links/apps-upload.md) no cliente do teams usando o `Development.zip` na `.publish` pasta.</span><span class="sxs-lookup"><span data-stu-id="51b33-139">[Sideload your app](../doc-links/apps-upload.md) in the Teams client using the `Development.zip` in the `.publish` folder.</span></span>

<span data-ttu-id="51b33-140">Depois que você Sideload seu aplicativo, ele deve ter a seguinte aparência no cliente Teams.</span><span class="sxs-lookup"><span data-stu-id="51b33-140">Once you sideload your app, it should look like this in the Teams client.</span></span>

![Guia de exemplo Hello World](../doc-links/images/tab-running.png)

## <a name="important-app-project-files"></a><span data-ttu-id="51b33-142">Arquivos de projeto de aplicativo importantes</span><span class="sxs-lookup"><span data-stu-id="51b33-142">Important app project files</span></span>

<span data-ttu-id="51b33-143">Com seu projeto de aplicativo e o scaffolding configurados, Reserve algum tempo para entender alguns dos principais arquivos da equipe de aplicativos do teams que trabalham com o.</span><span class="sxs-lookup"><span data-stu-id="51b33-143">With your app project and scaffolding set up, take some time to understand some of the key files Teams app developers work with.</span></span>

### <a name="app-manifest-manifestjson"></a><span data-ttu-id="51b33-144">Manifesto do aplicativo ( `manifest.json` )</span><span class="sxs-lookup"><span data-stu-id="51b33-144">App manifest (`manifest.json`)</span></span>

<span data-ttu-id="51b33-145">Localizado no `.publish` diretório, o manifesto do aplicativo é o ponto de partida para qualquer projeto de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="51b33-145">Located in the `.publish` directory, the app manifest is the starting point for any app project.</span></span> <span data-ttu-id="51b33-146">O manifesto define os atributos fundamentais do aplicativo e aponta para os recursos necessários.</span><span class="sxs-lookup"><span data-stu-id="51b33-146">The manifest defines your app's fundamental attributes and points to required resources.</span></span> <span data-ttu-id="51b33-147">Quando você instala um aplicativo, o Teams analisa o manifesto para entender como renderizar seu aplicativo no cliente.</span><span class="sxs-lookup"><span data-stu-id="51b33-147">When you install an app, Teams parses the manifest to understand how to render your app in the client.</span></span>

<span data-ttu-id="51b33-148">Nos tutoriais a seguir, você se concentrará nas seções do manifesto de aplicativo para criar as guias pessoal e canal.</span><span class="sxs-lookup"><span data-stu-id="51b33-148">In the following tutorials, you'll focus on the sections of the app manifest for building personal and channel tabs.</span></span>

### <a name="package-developmentzip"></a><span data-ttu-id="51b33-149">Package ( `Development.zip` )</span><span class="sxs-lookup"><span data-stu-id="51b33-149">Package (`Development.zip`)</span></span>

<span data-ttu-id="51b33-150">Também localizado no `.publish` diretório, você precisará do pacote de aplicativos para [Sideload seu aplicativo](../../overview.md#how-can-you-share-your-teams-app) no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="51b33-150">Also located in the `.publish` directory, you need the app package to [sideload your app](../../overview.md#how-can-you-share-your-teams-app) in Teams.</span></span> <span data-ttu-id="51b33-151">Também é usada ao [publicar no catálogo de aplicativos da sua organização](../../overview.md#how-can-you-share-your-teams-app) ou no [AppSource](../../concepts/deploy-and-publish/appsource/publish.md).</span><span class="sxs-lookup"><span data-stu-id="51b33-151">It's also used when [publishing to your organization's app catalog](../../overview.md#how-can-you-share-your-teams-app) or [AppSource](../../concepts/deploy-and-publish/appsource/publish.md).</span></span>

<span data-ttu-id="51b33-152">Veja alguns detalhes sobre os arquivos de pacote de aplicativos:</span><span class="sxs-lookup"><span data-stu-id="51b33-152">Here are some details about the app package files:</span></span>

|<span data-ttu-id="51b33-153">Nome</span><span class="sxs-lookup"><span data-stu-id="51b33-153">Name</span></span>|<span data-ttu-id="51b33-154">Tipo</span><span class="sxs-lookup"><span data-stu-id="51b33-154">Type</span></span>|<span data-ttu-id="51b33-155">Size</span><span class="sxs-lookup"><span data-stu-id="51b33-155">Size</span></span>|<span data-ttu-id="51b33-156">Local do manifesto</span><span class="sxs-lookup"><span data-stu-id="51b33-156">Manifest location</span></span>|<span data-ttu-id="51b33-157">Nome do arquivo de kit</span><span class="sxs-lookup"><span data-stu-id="51b33-157">Toolkit filename</span></span>|
|---|---|:---:|:---:|-----|
|<span data-ttu-id="51b33-158">**Manifesto do aplicativo**</span><span class="sxs-lookup"><span data-stu-id="51b33-158">**App manifest**</span></span>|`.json`| <span data-ttu-id="51b33-159">—</span><span class="sxs-lookup"><span data-stu-id="51b33-159">—</span></span> | <span data-ttu-id="51b33-160">—</span><span class="sxs-lookup"><span data-stu-id="51b33-160">—</span></span> |`.publish/manifest.json`|
|<span data-ttu-id="51b33-161">**Logotipo colorido**</span><span class="sxs-lookup"><span data-stu-id="51b33-161">**Color logo**</span></span>|`.png`|<span data-ttu-id="51b33-162">192 &times; 192 pixels</span><span class="sxs-lookup"><span data-stu-id="51b33-162">192&times;192 pixels</span></span>|`icon.color`|`.publish/color.png`|
|<span data-ttu-id="51b33-163">**Logotipo da estrutura de tópicos**</span><span class="sxs-lookup"><span data-stu-id="51b33-163">**Outline logo**</span></span>|`.png`|<span data-ttu-id="51b33-164">32 &times; 32 pixels</span><span class="sxs-lookup"><span data-stu-id="51b33-164">32&times;32 pixels</span></span>|`icon.outline`|`.publish/outline.png`|

### <a name="scaffolding-src"></a><span data-ttu-id="51b33-165">Scaffolding ( `src` )</span><span class="sxs-lookup"><span data-stu-id="51b33-165">Scaffolding (`src`)</span></span>

<span data-ttu-id="51b33-166">O kit de ferramentas cria automaticamente o scaffolding para você no `src` diretório com base nos recursos adicionados durante a configuração.</span><span class="sxs-lookup"><span data-stu-id="51b33-166">The toolkit automatically creates scaffolding for you in the `src` directory based on the capabilities you added during setup.</span></span>

<span data-ttu-id="51b33-167">No entanto, alguns arquivos são criados independentemente do tipo de aplicativo que você tem.</span><span class="sxs-lookup"><span data-stu-id="51b33-167">Some files are created no matter what kind of app you have, though.</span></span> <span data-ttu-id="51b33-168">Por exemplo, o `App.js` arquivo no `src/components` diretório é importante porque trata a inicialização e o roteamento do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="51b33-168">For example, the `App.js` file in the `src/components` directory is important because it handles the initialization and routing of your app.</span></span> <span data-ttu-id="51b33-169">O mais importante é que ele chama o [SDK do Microsoft Teams](../doc-links/using-teams-client-sdk.md) para estabelecer a comunicação entre o seu aplicativo e o Teams.</span><span class="sxs-lookup"><span data-stu-id="51b33-169">Most importantly, it calls the [Microsoft Teams SDK](../doc-links/using-teams-client-sdk.md) to establish communication between your app and Teams.</span></span>

<span data-ttu-id="51b33-170">Você pode saber mais sobre o scaffolding nos tutoriais para criar guias pessoais e de canal.</span><span class="sxs-lookup"><span data-stu-id="51b33-170">You can learn more about scaffolding in the tutorials for creating personal and channel tabs.</span></span>

## <a name="next-step"></a><span data-ttu-id="51b33-171">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="51b33-171">Next step</span></span>

<span data-ttu-id="51b33-172">🎉 Parabéns!</span><span class="sxs-lookup"><span data-stu-id="51b33-172">🎉 Congratulations!</span></span> <span data-ttu-id="51b33-173">Você tem um aplicativo do teams em execução.</span><span class="sxs-lookup"><span data-stu-id="51b33-173">You have a running Teams app.</span></span> <span data-ttu-id="51b33-174">Selecione o botão a seguir para saber como adicionar um recurso do mundo real a ele.</span><span class="sxs-lookup"><span data-stu-id="51b33-174">Select the following button to learn how to add a real-world feature to it.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="51b33-175">Criar uma guia pessoal</span><span class="sxs-lookup"><span data-stu-id="51b33-175">Build a personal tab</span></span>](add-personal-tab.md)
