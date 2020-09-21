---
title: Introdução à criação do seu primeiro aplicativo do teams
author: heath-hamilton
ms.author: lajanuar
description: Visão geral e pré-requisitos para criar seu primeiro aplicativo do Microsoft Teams
ms.openlocfilehash: 9392096a285a43d3a1f8bed5020e3464da0f7f18
ms.sourcegitcommit: d3bb4bbcdff9545c9869647dcdbe563a2db868be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2020
ms.locfileid: "47964628"
---
# <a name="get-started-building-your-first-teams-app"></a><span data-ttu-id="1b406-103">Introdução à criação do seu primeiro aplicativo do teams</span><span class="sxs-lookup"><span data-stu-id="1b406-103">Get started building your first Teams app</span></span>

<span data-ttu-id="1b406-104">Nas aulas **Compilar suas primeiras aplicativos** , você cria aplicativos básicos do teams.</span><span class="sxs-lookup"><span data-stu-id="1b406-104">In the **build your first app** lessons, you create basic Teams apps.</span></span> <span data-ttu-id="1b406-105">Cada tutorial percorre como criar um aplicativo simples e de equipe real ao apresentar as ferramentas comuns, conceitos fundamentais e alguns recursos mais avançados.</span><span class="sxs-lookup"><span data-stu-id="1b406-105">Each tutorial walks through how to build a simple, real-world Teams app while introducing you to common tools, fundamental concepts, and some more advanced features.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="1b406-106">O que você aprenderá</span><span class="sxs-lookup"><span data-stu-id="1b406-106">What you'll learn</span></span>

<span data-ttu-id="1b406-107">Aqui está uma ideia do que você saberá depois de percorrer as lições.</span><span class="sxs-lookup"><span data-stu-id="1b406-107">Here's an idea of what you'll know after going through the lessons.</span></span>

> [!div class="checklist"]
  >
  > * <span data-ttu-id="1b406-108">**Comece a trabalhar rapidamente com o Teams Toolkit**: o Microsoft Teams Toolkit para Visual Studio Code cuida da criação do seu projeto de aplicativo e do scaffolding, para que você possa ter um aplicativo em execução em minutos.</span><span class="sxs-lookup"><span data-stu-id="1b406-108">**Get up and running quickly with the Teams Toolkit**: The Microsoft Teams Toolkit for Visual Studio Code takes care of creating your app project and scaffolding so you can have a running app in minutes.</span></span>
  > * <span data-ttu-id="1b406-109">**Defina seu aplicativo com o manifesto**: o manifesto do aplicativo é onde você especifica os recursos e serviços que seu aplicativo da equipe usa.</span><span class="sxs-lookup"><span data-stu-id="1b406-109">**Define your app with the manifest**: The app manifest is where you specify the capabilities and services your Teams app uses.</span></span>
  > * <span data-ttu-id="1b406-110">**Escopo do seu aplicativo público**: Crie um aplicativo do teams para uso pessoal, colaboração ou ambos.</span><span class="sxs-lookup"><span data-stu-id="1b406-110">**Scope your app's audience**: Build a Teams app for personal use, collaboration, or both.</span></span>
  > * <span data-ttu-id="1b406-111">**Obtenha experiência com estruturas**: Personalize seu aplicativo (por exemplo, altere seu esquema de cores para corresponder ao tema do Teams) com a ajuda do SDK do JavaScript do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="1b406-111">**Get experience with frameworks**: Customize your app (for example, change its color scheme to match the Teams theme) with help from the Teams JavaScript SDK.</span></span> <span data-ttu-id="1b406-112">Além disso, saiba mais sobre as ferramentas comuns para criar e gerenciar bots.</span><span class="sxs-lookup"><span data-stu-id="1b406-112">Also, learn about common tools for creating and managing bots.</span></span>
  > * <span data-ttu-id="1b406-113">**Expanda em seu aplicativo**: em todas as lições, você encontrará tópicos relacionados que provavelmente você está interessado (como diretrizes de autenticação e Design).</span><span class="sxs-lookup"><span data-stu-id="1b406-113">**Expand on your app**: Throughout the lessons, you'll find related topics you're probably interested in (such as authentication and design guidelines).</span></span>

## <a name="teams-app-fundamentals"></a><span data-ttu-id="1b406-114">Conceitos básicos do aplicativo Teams</span><span class="sxs-lookup"><span data-stu-id="1b406-114">Teams app fundamentals</span></span>

<span data-ttu-id="1b406-115">Antes de começar os tutoriais, você deve saber o seguinte sobre a criação de aplicativos para o Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="1b406-115">Before you begin the tutorials, you should know the following about building apps for Teams.</span></span>

### <a name="apps-can-have-multiple-capabilities"></a><span data-ttu-id="1b406-116">Os aplicativos podem ter vários recursos</span><span class="sxs-lookup"><span data-stu-id="1b406-116">Apps can have multiple capabilities</span></span>

<span data-ttu-id="1b406-117">Os aplicativos do teams são compostos por um ou mais [recursos de plataforma](../capabilities-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1b406-117">Teams apps are made up of one or more [platform capabilities](../capabilities-overview.md).</span></span> <span data-ttu-id="1b406-118">Você pode exibir esses recursos usando uma série de [componentes e convenções de interface do usuário específicos da](../doc-links/teams-ui-conventions.md)equipe, como módulos de cartões e tarefas.</span><span class="sxs-lookup"><span data-stu-id="1b406-118">You can display these capabilities using a number of Teams-specific [UI components and conventions](../doc-links/teams-ui-conventions.md), such as cards and task modules.</span></span>

### <a name="teams-doesnt-host-your-app"></a><span data-ttu-id="1b406-119">O Microsoft Teams não hospeda seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="1b406-119">Teams doesn't host your app</span></span>

<span data-ttu-id="1b406-120">Um aplicativo do teams inclui três partes importantes:</span><span class="sxs-lookup"><span data-stu-id="1b406-120">A Teams app includes three important pieces:</span></span>

* <span data-ttu-id="1b406-121">A lógica, o armazenamento de dados e as chamadas de API que alimentam o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1b406-121">The logic, data storage, and API calls that power your app.</span></span> <span data-ttu-id="1b406-122">Esses serviços não são hospedados pelo Microsoft Teams e devem ser acessíveis via HTTPS.</span><span class="sxs-lookup"><span data-stu-id="1b406-122">These services are not hosted by Teams and must be accessible via HTTPS.</span></span>
* <span data-ttu-id="1b406-123">O cliente do Microsoft Teams (Web, desktop ou celular) onde as pessoas usam o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1b406-123">The Teams client (web, desktop, or mobile) where people use your app.</span></span>
* <span data-ttu-id="1b406-124">Seu pacote de aplicativos, que você usa para instalar o aplicativo no Teams.</span><span class="sxs-lookup"><span data-stu-id="1b406-124">Your app package, which you use to install the app in Teams.</span></span> <span data-ttu-id="1b406-125">Ele contém metadados do aplicativo e ponteiros para seus serviços hospedados.</span><span class="sxs-lookup"><span data-stu-id="1b406-125">It contains app metadata and pointers to your hosted services.</span></span>

## <a name="get-prerequisites"></a><span data-ttu-id="1b406-126">Obter pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="1b406-126">Get prerequisites</span></span>

<span data-ttu-id="1b406-127">Verifique se você tem a conta certa para criar aplicativos do Teams e instalar algumas ferramentas de desenvolvimento recomendadas.</span><span class="sxs-lookup"><span data-stu-id="1b406-127">Verify you have the right account for building Teams apps and install some recommended development tools.</span></span>

### <a name="set-up-your-development-account"></a><span data-ttu-id="1b406-128">Configurar sua conta de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="1b406-128">Set up your development account</span></span>

<span data-ttu-id="1b406-129">Você precisa de uma conta do Microsoft Teams que permite o Sideload de aplicativos personalizado.</span><span class="sxs-lookup"><span data-stu-id="1b406-129">You need a Teams account that allows custom app sideloading.</span></span> <span data-ttu-id="1b406-130">(Sua conta já pode fornecer isso).</span><span class="sxs-lookup"><span data-stu-id="1b406-130">(Your account may already provide this.)</span></span>

1. <span data-ttu-id="1b406-131">Se você tiver uma conta do Microsoft Teams, verifique se você pode Sideload aplicativos no Microsoft Teams:</span><span class="sxs-lookup"><span data-stu-id="1b406-131">If you have a Teams account, verify if you can sideload apps in Teams:</span></span>
    1. <span data-ttu-id="1b406-132">No cliente do Microsoft Teams, selecione **aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="1b406-132">In the Teams client, select **Apps**.</span></span>
    1. <span data-ttu-id="1b406-133">Procure uma opção para **carregar um aplicativo personalizado**.</span><span class="sxs-lookup"><span data-stu-id="1b406-133">Look for an option to **Upload a custom app**.</span></span>

    :::image type="content" source="../doc-links/images/upload-custom-app-closeup.png" alt-text="exibição de opção Sideload":::

<!-- markdownlint-disable MD033 -->
<details>

<summary><span data-ttu-id="1b406-135"><b>Selecione aqui</b> se você não conseguir ver a opção Sideload ou se não tiver uma conta do teams.</span><span class="sxs-lookup"><span data-stu-id="1b406-135"><b>Select here</b> if you can't see the sideload option or don't have a Teams account.</span></span></summary>

<span data-ttu-id="1b406-136">Você pode obter uma conta de teste gratuita do teams que permite que o aplicativo Sideload ingresse no programa de desenvolvedor do 365 da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1b406-136">You can get a free Teams test account that allows app sideloading by joining the Microsoft 365 developer program.</span></span> <span data-ttu-id="1b406-137">(O processo de registro leva aproximadamente dois minutos.)</span><span class="sxs-lookup"><span data-stu-id="1b406-137">(The registration process takes approximately two minutes.)</span></span>

1. <span data-ttu-id="1b406-138">Vá para o [programa Microsoft 365 Developer](https://developer.microsoft.com/microsoft-365/dev-program).</span><span class="sxs-lookup"><span data-stu-id="1b406-138">Go to the [Microsoft 365 developer program](https://developer.microsoft.com/microsoft-365/dev-program).</span></span>
1. <span data-ttu-id="1b406-139">Selecione **ingressar agora** e siga as instruções na tela.</span><span class="sxs-lookup"><span data-stu-id="1b406-139">Select **Join Now** and follow the onscreen instructions.</span></span>
1. <span data-ttu-id="1b406-140">Quando você chegar à tela de boas-vindas, selecione **Configurar a assinatura E5**.</span><span class="sxs-lookup"><span data-stu-id="1b406-140">When you get to the welcome screen, select **Set up E5 subscription**.</span></span>
1. <span data-ttu-id="1b406-141">Configurar sua conta de administrador.</span><span class="sxs-lookup"><span data-stu-id="1b406-141">Set up your administrator account.</span></span> <span data-ttu-id="1b406-142">Após concluir, você verá uma tela como esta.</span><span class="sxs-lookup"><span data-stu-id="1b406-142">Once you finish, you should see a screen like this.</span></span>
:::image type="content" source="../doc-links/images/dev-program-subscription.png" alt-text="exibição de assinatura do programa dev":::
1. <span data-ttu-id="1b406-144">Faça logon no Microsoft Teams usando a conta de administrador que você acabou de configurar.</span><span class="sxs-lookup"><span data-stu-id="1b406-144">Log in to Teams using the administrator account you just set up.</span></span>
1. <span data-ttu-id="1b406-145">Verifique se agora você tem a opção **carregar um aplicativo personalizado** .</span><span class="sxs-lookup"><span data-stu-id="1b406-145">Verify if you now have the **Upload a custom app** option.</span></span>

</details>

### <a name="install-your-development-tools"></a><span data-ttu-id="1b406-146">Instalar suas ferramentas de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="1b406-146">Install your development tools</span></span>

<span data-ttu-id="1b406-147">Você pode criar aplicativos do teams com suas ferramentas preferenciais, mas essas lições mostram como você pode começar rapidamente com o Microsoft Teams Toolkit para o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="1b406-147">You can build Teams apps with your preferred tools, but these lessons show how you can get started quickly with the Microsoft Teams Toolkit for Visual Studio Code.</span></span>

<span data-ttu-id="1b406-148">O Microsoft Teams exibe o conteúdo do aplicativo apenas por meio de conexões HTTPS.</span><span class="sxs-lookup"><span data-stu-id="1b406-148">Teams displays app content only through HTTPS connections.</span></span> <span data-ttu-id="1b406-149">Desde que você hospedará seu primeiro aplicativo localmente, você aprenderá a usar o [ngrok para configurar um túnel seguro](../doc-links/debug.md#locally-hosted) entre o Teams e seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1b406-149">Since you'll host your first app locally, you'll learn how to use [ngrok to set up a secure tunnel](../doc-links/debug.md#locally-hosted) between Teams and your app.</span></span>

1. <span data-ttu-id="1b406-150">Instale o [Node.js](https://nodejs.org/en/).</span><span class="sxs-lookup"><span data-stu-id="1b406-150">Install [Node.js](https://nodejs.org/en/).</span></span>
1. <span data-ttu-id="1b406-151">Instale a versão mais recente do [Visual Studio Code](https://code.visualstudio.com/download).</span><span class="sxs-lookup"><span data-stu-id="1b406-151">Install the latest version of [Visual Studio Code](https://code.visualstudio.com/download).</span></span> <span data-ttu-id="1b406-152">(As versões anteriores podem não funcionar com o kit de ferramentas.)</span><span class="sxs-lookup"><span data-stu-id="1b406-152">(Earlier versions might not work with the toolkit.)</span></span>
1. No Visual Studio Code, selecione **extensões** :::image type="icon" source="../doc-links/images/vs-code-extensions.png"::: na barra de atividades à esquerda e instale o **Microsoft Teams Toolkit**.
    :::image type="content" source="../doc-links/images/vsc-install-toolkit.png" alt-text="instalar modo de edição do kit de ferramentas":::
1. <span data-ttu-id="1b406-155">Instale o [ngrok](https://ngrok.com/download).</span><span class="sxs-lookup"><span data-stu-id="1b406-155">Install [ngrok](https://ngrok.com/download).</span></span>

## <a name="next-step"></a><span data-ttu-id="1b406-156">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="1b406-156">Next step</span></span>

<span data-ttu-id="1b406-157">Depois de configurar sua conta e ambiente, você pode começar a criar.</span><span class="sxs-lookup"><span data-stu-id="1b406-157">Once you set up your account and environment, you can start building.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1b406-158">Criar e executar seu primeiro aplicativo</span><span class="sxs-lookup"><span data-stu-id="1b406-158">Build and run your first app</span></span>](../build-your-first-app/build-and-run.md)
