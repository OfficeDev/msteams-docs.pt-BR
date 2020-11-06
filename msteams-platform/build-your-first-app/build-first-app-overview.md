---
title: Introdução-Crie sua primeira visão geral e pré-requisitos do aplicativo
author: heath-hamilton
description: Saiba como começar a usar o desenvolvimento de aplicativos do Microsoft Teams e configurar seu ambiente.
ms.author: lajanuar
ms.date: 11/03/2020
ms.topic: quickstart
ms.openlocfilehash: 7fc3f7e9fd9d3c2a028999be53ba6bdcd5b3ba72
ms.sourcegitcommit: 99c35de7e2c604bd8bce392242c2c2fa709cd50b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/06/2020
ms.locfileid: "48931789"
---
# <a name="build-your-first-microsoft-teams-app-overview"></a><span data-ttu-id="7588b-103">Criar sua primeira visão geral do aplicativo Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="7588b-103">Build your first Microsoft Teams app overview</span></span>

<span data-ttu-id="7588b-104">Nas aulas **Compilar suas primeiras aplicativos** , você cria aplicativos básicos do teams.</span><span class="sxs-lookup"><span data-stu-id="7588b-104">In the **build your first app** lessons, you create basic Teams apps.</span></span> <span data-ttu-id="7588b-105">Cada tutorial percorre como criar um aplicativo simples e de equipe real ao apresentar as ferramentas comuns, conceitos fundamentais e recursos mais avançados.</span><span class="sxs-lookup"><span data-stu-id="7588b-105">Each tutorial walks through how to build a simple, real-world Teams app while introducing you to common tools, fundamental concepts, and more advanced features.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="7588b-106">O que você aprenderá</span><span class="sxs-lookup"><span data-stu-id="7588b-106">What you'll learn</span></span>

<span data-ttu-id="7588b-107">Aqui está uma ideia do que você saberá depois de percorrer as lições.</span><span class="sxs-lookup"><span data-stu-id="7588b-107">Here's an idea of what you'll know after going through the lessons.</span></span>

> [!div class="checklist"]
  >
  > * <span data-ttu-id="7588b-108">**Comece a trabalhar rapidamente com o Teams Toolkit** : o Microsoft Teams Toolkit para Visual Studio Code cuida da criação do seu projeto de aplicativo e do scaffolding, para que você possa ter um aplicativo em execução em minutos.</span><span class="sxs-lookup"><span data-stu-id="7588b-108">**Get up and running quickly with the Teams Toolkit** : The Microsoft Teams Toolkit for Visual Studio Code takes care of creating your app project and scaffolding so you can have a running app in minutes.</span></span>
  > * <span data-ttu-id="7588b-109">**Configurar seu aplicativo com o app Studio** : Especifique os recursos e serviços que seu aplicativo de equipe usa.</span><span class="sxs-lookup"><span data-stu-id="7588b-109">**Configure your app with App Studio** : Specify the capabilities and services your Teams app uses.</span></span>
  > * <span data-ttu-id="7588b-110">**Escopo do seu aplicativo público** : Crie um aplicativo do teams para uso pessoal, colaboração ou ambos.</span><span class="sxs-lookup"><span data-stu-id="7588b-110">**Scope your app's audience** : Build a Teams app for personal use, collaboration, or both.</span></span>
  > * <span data-ttu-id="7588b-111">**Obtenha experiência com ferramentas e SDKs do Microsoft Teams** : Personalize seu aplicativo (por exemplo, altere seu esquema de cores para corresponder ao tema do Teams) com a ajuda do SDK do Microsoft Teams JavaScript.</span><span class="sxs-lookup"><span data-stu-id="7588b-111">**Get experience with Teams tools and SDKs** : Customize your app (for example, change its color scheme to match the Teams theme) with help from the Teams JavaScript SDK.</span></span> <span data-ttu-id="7588b-112">Além disso, saiba mais sobre as ferramentas comuns para criar e gerenciar bots.</span><span class="sxs-lookup"><span data-stu-id="7588b-112">Also, learn about common tools for creating and managing bots.</span></span>
  > * <span data-ttu-id="7588b-113">**Expanda em seu aplicativo** : em todas as lições, você encontrará tópicos relacionados que provavelmente você está interessado (como diretrizes de autenticação e Design).</span><span class="sxs-lookup"><span data-stu-id="7588b-113">**Expand on your app** : Throughout the lessons, you'll find related topics you're probably interested in (such as authentication and design guidelines).</span></span>

## <a name="teams-app-fundamentals"></a><span data-ttu-id="7588b-114">Conceitos básicos do aplicativo Teams</span><span class="sxs-lookup"><span data-stu-id="7588b-114">Teams app fundamentals</span></span>

<span data-ttu-id="7588b-115">Antes de começar os tutoriais, você deve saber o seguinte sobre a criação de aplicativos para o Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="7588b-115">Before you begin the tutorials, you should know the following about building apps for Teams.</span></span>

### <a name="apps-can-have-multiple-capabilities-and-entry-points"></a><span data-ttu-id="7588b-116">Os aplicativos podem ter vários recursos e pontos de entrada</span><span class="sxs-lookup"><span data-stu-id="7588b-116">Apps can have multiple capabilities and entry points</span></span>

<span data-ttu-id="7588b-117">Um aplicativo do teams é composto por um ou mais [recursos de plataforma](../concepts/capabilities-overview.md) (como as pessoas usam o aplicativo) e pontos de [entrada](../concepts/extensibility-points.md) (onde as pessoas detectam o aplicativo).</span><span class="sxs-lookup"><span data-stu-id="7588b-117">A Teams app is made up of one or more [platform capabilities](../concepts/capabilities-overview.md) (how people use the app) and [entry points](../concepts/extensibility-points.md) (where people discover the app).</span></span>

### <a name="teams-doesnt-host-your-app"></a><span data-ttu-id="7588b-118">O Microsoft Teams não hospeda seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="7588b-118">Teams doesn't host your app</span></span>

<span data-ttu-id="7588b-119">Um aplicativo do teams inclui as seguintes partes importantes:</span><span class="sxs-lookup"><span data-stu-id="7588b-119">A Teams app includes the following important pieces:</span></span>

* <span data-ttu-id="7588b-120">A lógica, o armazenamento de dados e as chamadas de API que alimentam o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7588b-120">The logic, data storage, and API calls that power your app.</span></span> <span data-ttu-id="7588b-121">Esses serviços não são hospedados pelo Microsoft Teams e devem ser acessíveis via HTTPS.</span><span class="sxs-lookup"><span data-stu-id="7588b-121">These services are not hosted by Teams and must be accessible via HTTPS.</span></span>
* <span data-ttu-id="7588b-122">O cliente do Microsoft Teams (Web, desktop ou celular) onde as pessoas usam o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7588b-122">The Teams client (web, desktop, or mobile) where people use your app.</span></span>
* <span data-ttu-id="7588b-123">Sua ID de aplicativo, que permite que você configure seu aplicativo com o app Studio.</span><span class="sxs-lookup"><span data-stu-id="7588b-123">Your app ID, which lets you configure your app with App Studio.</span></span>

## <a name="get-prerequisites"></a><span data-ttu-id="7588b-124">Obter pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="7588b-124">Get prerequisites</span></span>

<span data-ttu-id="7588b-125">Verifique se você tem a conta certa para criar aplicativos do Teams e instalar algumas ferramentas de desenvolvimento recomendadas.</span><span class="sxs-lookup"><span data-stu-id="7588b-125">Verify you have the right account for building Teams apps and install some recommended development tools.</span></span>

### <a name="set-up-your-development-account"></a><span data-ttu-id="7588b-126">Configurar sua conta de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="7588b-126">Set up your development account</span></span>

<span data-ttu-id="7588b-127">Você precisa de uma conta do Microsoft Teams que permite o Sideload de aplicativos personalizado.</span><span class="sxs-lookup"><span data-stu-id="7588b-127">You need a Teams account that allows custom app sideloading.</span></span> <span data-ttu-id="7588b-128">(Sua conta já pode fornecer isso).</span><span class="sxs-lookup"><span data-stu-id="7588b-128">(Your account may already provide this.)</span></span>

1. <span data-ttu-id="7588b-129">Se você tiver uma conta do Microsoft Teams, verifique se você pode Sideload aplicativos no Microsoft Teams:</span><span class="sxs-lookup"><span data-stu-id="7588b-129">If you have a Teams account, verify if you can sideload apps in Teams:</span></span>
    1. <span data-ttu-id="7588b-130">No cliente do Microsoft Teams, selecione **aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="7588b-130">In the Teams client, select **Apps**.</span></span>
    1. <span data-ttu-id="7588b-131">Procure uma opção para **carregar um aplicativo personalizado**.</span><span class="sxs-lookup"><span data-stu-id="7588b-131">Look for an option to **Upload a custom app**.</span></span>

    :::image type="content" source="../assets/images/build-your-first-app/upload-custom-app-closeup.png" alt-text="Ilustração mostrando onde você pode carregar um aplicativo personalizado no Microsoft Teams.":::

<!-- markdownlint-disable MD033 -->
<details>

<summary><span data-ttu-id="7588b-133"><b>Selecione aqui</b> se você não conseguir ver a opção Sideload ou se não tiver uma conta do teams.</span><span class="sxs-lookup"><span data-stu-id="7588b-133"><b>Select here</b> if you can't see the sideload option or don't have a Teams account.</span></span></summary>

<span data-ttu-id="7588b-134">Você pode obter uma conta de teste gratuita do teams que permite que o aplicativo Sideload ingresse no programa de desenvolvedor do 365 da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7588b-134">You can get a free Teams test account that allows app sideloading by joining the Microsoft 365 developer program.</span></span> <span data-ttu-id="7588b-135">(O processo de registro leva aproximadamente dois minutos.)</span><span class="sxs-lookup"><span data-stu-id="7588b-135">(The registration process takes approximately two minutes.)</span></span>

1. <span data-ttu-id="7588b-136">Vá para o [programa Microsoft 365 Developer](https://developer.microsoft.com/microsoft-365/dev-program).</span><span class="sxs-lookup"><span data-stu-id="7588b-136">Go to the [Microsoft 365 developer program](https://developer.microsoft.com/microsoft-365/dev-program).</span></span>
1. <span data-ttu-id="7588b-137">Selecione **ingressar agora** e siga as instruções na tela.</span><span class="sxs-lookup"><span data-stu-id="7588b-137">Select **Join Now** and follow the onscreen instructions.</span></span>
1. <span data-ttu-id="7588b-138">Quando você chegar à tela de boas-vindas, selecione **Configurar a assinatura E5**.</span><span class="sxs-lookup"><span data-stu-id="7588b-138">When you get to the welcome screen, select **Set up E5 subscription**.</span></span>
1. <span data-ttu-id="7588b-139">Configurar sua conta de administrador.</span><span class="sxs-lookup"><span data-stu-id="7588b-139">Set up your administrator account.</span></span> <span data-ttu-id="7588b-140">Após concluir, você verá uma tela como esta.</span><span class="sxs-lookup"><span data-stu-id="7588b-140">Once you finish, you should see a screen like this.</span></span>
:::image type="content" source="../assets/images/build-your-first-app/dev-program-subscription.png" alt-text="Exemplo do que você vê após se inscrever no programa de desenvolvedor do Microsoft 365.":::
1. <span data-ttu-id="7588b-142">Faça logon no Microsoft Teams usando a conta de administrador que você acabou de configurar.</span><span class="sxs-lookup"><span data-stu-id="7588b-142">Log in to Teams using the administrator account you just set up.</span></span>
1. <span data-ttu-id="7588b-143">Verifique se agora você tem a opção **carregar um aplicativo personalizado** .</span><span class="sxs-lookup"><span data-stu-id="7588b-143">Verify if you now have the **Upload a custom app** option.</span></span>

</details>

### <a name="install-your-development-tools"></a><span data-ttu-id="7588b-144">Instalar suas ferramentas de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="7588b-144">Install your development tools</span></span>

<span data-ttu-id="7588b-145">Você pode criar aplicativos do teams com suas ferramentas preferenciais, mas essas lições mostram como você pode começar rapidamente com o Microsoft Teams Toolkit para o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="7588b-145">You can build Teams apps with your preferred tools, but these lessons show how you can get started quickly with the Microsoft Teams Toolkit for Visual Studio Code.</span></span>

<span data-ttu-id="7588b-146">O Microsoft Teams exibe o conteúdo do aplicativo apenas por meio de conexões HTTPS.</span><span class="sxs-lookup"><span data-stu-id="7588b-146">Teams displays app content only through HTTPS connections.</span></span> <span data-ttu-id="7588b-147">Para depurar determinados tipos de aplicativos localmente, como um bot, você aprenderá a usar o [ngrok para configurar um túnel seguro](../concepts/build-and-test/debug.md#locally-hosted) entre o Teams e seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7588b-147">To debug certain types of apps locally, such as a bot, you'll learn how to use [ngrok to set up a secure tunnel](../concepts/build-and-test/debug.md#locally-hosted) between Teams and your app.</span></span> <span data-ttu-id="7588b-148">(Os aplicativos do teams de produção são hospedados na nuvem.)</span><span class="sxs-lookup"><span data-stu-id="7588b-148">(Production Teams apps are hosted in the cloud.)</span></span>

1. <span data-ttu-id="7588b-149">Instale o [Node.js](https://nodejs.org/en/).</span><span class="sxs-lookup"><span data-stu-id="7588b-149">Install [Node.js](https://nodejs.org/en/).</span></span>
1. <span data-ttu-id="7588b-150">Instale o [ngrok](https://ngrok.com/download) se você planeja criar um bot ou uma extensão de mensagem.</span><span class="sxs-lookup"><span data-stu-id="7588b-150">Install [ngrok](https://ngrok.com/download) if you plan to build a bot or messaging extension.</span></span>
1. <span data-ttu-id="7588b-151">Instale a versão mais recente do [Visual Studio Code](https://code.visualstudio.com/download).</span><span class="sxs-lookup"><span data-stu-id="7588b-151">Install the latest version of [Visual Studio Code](https://code.visualstudio.com/download).</span></span> <span data-ttu-id="7588b-152">(As versões anteriores podem não funcionar com o kit de ferramentas.)</span><span class="sxs-lookup"><span data-stu-id="7588b-152">(Earlier versions might not work with the toolkit.)</span></span>
1. No Visual Studio Code, selecione **extensões** :::image type="icon" source="../assets/icons/vs-code-extensions.png"::: na barra de atividades à esquerda e instale o **Microsoft Teams Toolkit**.

    :::image type="content" source="../assets/images/build-your-first-app/vsc-install-toolkit.png" alt-text="Ilustração que mostra onde no Visual Studio Code você pode instalar a extensão do kit de ferramentas do Microsoft Teams.":::

## <a name="about-the-tutorials"></a><span data-ttu-id="7588b-155">Sobre os tutoriais</span><span class="sxs-lookup"><span data-stu-id="7588b-155">About the tutorials</span></span>

<span data-ttu-id="7588b-156">Você pode começar com qualquer um dos Teams **Construa suas primeiras lições de aplicativos** .</span><span class="sxs-lookup"><span data-stu-id="7588b-156">You can start with any of the Teams **build your first app** lessons.</span></span> <span data-ttu-id="7588b-157">Se você não tem certeza de onde começar, siga nosso caminho amigável de iniciantes e crie um "Olá, mundo!"</span><span class="sxs-lookup"><span data-stu-id="7588b-157">If you're not sure where to go first, follow our beginner friendly path and build a "Hello, World!"</span></span> <span data-ttu-id="7588b-158">aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7588b-158">app.</span></span>

:::image type="content" source="../assets/images/build-your-first-app/skill-tree-overview.png" alt-text="Árvore de qualificações que mostra os planos de aprendizado dos tutoriais de criação dos seus primeiros aplicativos do teams." border="false":::

## <a name="next-step"></a><span data-ttu-id="7588b-160">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="7588b-160">Next step</span></span>

<span data-ttu-id="7588b-161">Depois de configurar sua conta e ambiente, você pode começar a criar.</span><span class="sxs-lookup"><span data-stu-id="7588b-161">Once you set up your account and environment, you can start building.</span></span>

### <a name="beginner-friendly-tutorial"></a><span data-ttu-id="7588b-162">Tutorial amigável de iniciantes</span><span class="sxs-lookup"><span data-stu-id="7588b-162">Beginner friendly tutorial</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7588b-163">Criar um aplicativo "Olá, mundo!"</span><span class="sxs-lookup"><span data-stu-id="7588b-163">Build a "Hello, World!" app</span></span>](../build-your-first-app/build-and-run.md)

### <a name="other-tutorials"></a><span data-ttu-id="7588b-164">Outros tutoriais</span><span class="sxs-lookup"><span data-stu-id="7588b-164">Other tutorials</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7588b-165">Construir um bot</span><span class="sxs-lookup"><span data-stu-id="7588b-165">Build a bot</span></span>](../build-your-first-app/build-bot.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="7588b-166">Construir uma extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="7588b-166">Build a messaging extension</span></span>](../build-your-first-app/build-messaging-extension.md)
