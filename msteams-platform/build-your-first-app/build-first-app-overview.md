---
title: Começar - Criar sua primeira visão geral do aplicativo e pré-requisitos
author: heath-hamilton
description: Saiba como começar a usar o desenvolvimento de aplicativos do Microsoft Teams e configurar seu ambiente.
ms.author: lajanuar
ms.date: 11/03/2020
ms.topic: quickstart
ms.openlocfilehash: 4288efdbfada5f1a51fa1d4aeccdd6cdf9c64382
ms.sourcegitcommit: 4539479289b43812eaae07a1c0f878bed815d2d2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/12/2021
ms.locfileid: "49797894"
---
# <a name="build-your-first-microsoft-teams-app-overview"></a><span data-ttu-id="bec21-103">Crie sua primeira visão geral do aplicativo Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="bec21-103">Build your first Microsoft Teams app overview</span></span>

<span data-ttu-id="bec21-104">Nas **lições de começar,** você aprende a criar aplicativos básicos do Teams.</span><span class="sxs-lookup"><span data-stu-id="bec21-104">In the **get started** lessons, you learn how to create basic Teams apps.</span></span> <span data-ttu-id="bec21-105">Cada tutorial explica como criar um aplicativo teams simples e real ao mesmo tempo em que apresenta ferramentas comuns, conceitos fundamentais e recursos mais avançados.</span><span class="sxs-lookup"><span data-stu-id="bec21-105">Each tutorial walks through how to build a simple, real-world Teams app while introducing you to common tools, fundamental concepts, and more advanced features.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="bec21-106">O que você aprenderá</span><span class="sxs-lookup"><span data-stu-id="bec21-106">What you'll learn</span></span>

<span data-ttu-id="bec21-107">Aqui está uma ideia do que você vai saber depois de passar pelas lições.</span><span class="sxs-lookup"><span data-stu-id="bec21-107">Here's an idea of what you'll know after going through the lessons.</span></span>

> [!div class="checklist"]
  >
  > * <span data-ttu-id="bec21-108">**Começar a usar** rapidamente o Kit de Ferramentas do Teams: o Microsoft Teams Toolkit para Visual Studio Code cuida da criação do projeto do aplicativo e do scaffolding para que você possa ter um aplicativo em execução em minutos.</span><span class="sxs-lookup"><span data-stu-id="bec21-108">**Get up and running quickly with the Teams Toolkit**: The Microsoft Teams Toolkit for Visual Studio Code takes care of creating your app project and scaffolding so you can have a running app in minutes.</span></span>
  > * <span data-ttu-id="bec21-109">**Configure seu aplicativo com o App Studio:** especifique os recursos e serviços que seu aplicativo do Teams usa.</span><span class="sxs-lookup"><span data-stu-id="bec21-109">**Configure your app with App Studio**: Specify the capabilities and services your Teams app uses.</span></span>
  > * <span data-ttu-id="bec21-110">**Escopo do público do seu aplicativo:** crie um aplicativo do Teams para uso pessoal, colaboração ou ambos.</span><span class="sxs-lookup"><span data-stu-id="bec21-110">**Scope your app's audience**: Build a Teams app for personal use, collaboration, or both.</span></span>
> * <span data-ttu-id="bec21-111">**Obter experiência com ferramentas e SDKs do Teams:** personalize seu aplicativo com a ajuda do SDK do cliente JavaScript do Teams.</span><span class="sxs-lookup"><span data-stu-id="bec21-111">**Get experience with Teams tools and SDKs**: Customize your app with help from the Teams JavaScript client SDK.</span></span> <span data-ttu-id="bec21-112">Por exemplo, altere o esquema de cores do seu aplicativo para corresponder ao tema do Teams.</span><span class="sxs-lookup"><span data-stu-id="bec21-112">For example, change your app's color scheme to match the Teams theme.</span></span> <span data-ttu-id="bec21-113">Além disso, saiba mais sobre as ferramentas comuns para criar e gerenciar bots.</span><span class="sxs-lookup"><span data-stu-id="bec21-113">Also, learn about common tools for creating and managing bots.</span></span>
  > * <span data-ttu-id="bec21-114">**Expanda seu aplicativo:** ao longo das lições, você encontrará tópicos relacionados em que provavelmente está interessado (como diretrizes de autenticação e design).</span><span class="sxs-lookup"><span data-stu-id="bec21-114">**Expand on your app**: Throughout the lessons, you'll find related topics you're probably interested in (such as authentication and design guidelines).</span></span>

## <a name="teams-app-fundamentals"></a><span data-ttu-id="bec21-115">Conceitos básicos do aplicativo Teams</span><span class="sxs-lookup"><span data-stu-id="bec21-115">Teams app fundamentals</span></span>

<span data-ttu-id="bec21-116">Antes de começar os tutoriais, você deve saber o seguinte sobre como criar aplicativos para o Teams.</span><span class="sxs-lookup"><span data-stu-id="bec21-116">Before you begin the tutorials, you should know the following about building apps for Teams.</span></span>

### <a name="apps-can-have-multiple-capabilities-and-entry-points"></a><span data-ttu-id="bec21-117">Os aplicativos podem ter vários recursos e pontos de entrada</span><span class="sxs-lookup"><span data-stu-id="bec21-117">Apps can have multiple capabilities and entry points</span></span>

<span data-ttu-id="bec21-118">Um aplicativo teams é feito de um ou mais recursos de plataforma [(como](../concepts/capabilities-overview.md) as pessoas usam o aplicativo) e pontos de entrada [(onde](../concepts/extensibility-points.md) as pessoas usam o aplicativo).</span><span class="sxs-lookup"><span data-stu-id="bec21-118">A Teams app is made up of one or more [platform capabilities](../concepts/capabilities-overview.md) (how people use the app) and [entry points](../concepts/extensibility-points.md) (where people use the app).</span></span>

### <a name="teams-doesnt-host-your-app"></a><span data-ttu-id="bec21-119">O Teams não hospeda seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="bec21-119">Teams doesn't host your app</span></span>

<span data-ttu-id="bec21-120">Um aplicativo do Teams inclui as seguintes partes importantes:</span><span class="sxs-lookup"><span data-stu-id="bec21-120">A Teams app includes the following important pieces:</span></span>

* <span data-ttu-id="bec21-121">A lógica, o armazenamento de dados e as chamadas à API que ligarão seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bec21-121">The logic, data storage, and API calls that power your app.</span></span> <span data-ttu-id="bec21-122">Esses serviços não são hospedados pelo Teams e devem estar acessíveis via HTTPS.</span><span class="sxs-lookup"><span data-stu-id="bec21-122">These services are not hosted by Teams and must be accessible via HTTPS.</span></span>
* <span data-ttu-id="bec21-123">O cliente do Teams (web, desktop ou dispositivos móveis) onde as pessoas usam seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bec21-123">The Teams client (web, desktop, or mobile) where people use your app.</span></span>
* <span data-ttu-id="bec21-124">Sua ID de aplicativo, que permite configurar seu aplicativo com o App Studio.</span><span class="sxs-lookup"><span data-stu-id="bec21-124">Your app ID, which lets you configure your app with App Studio.</span></span>

## <a name="get-prerequisites"></a><span data-ttu-id="bec21-125">Obter pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="bec21-125">Get prerequisites</span></span>

<span data-ttu-id="bec21-126">Verifique se você tem a conta certa para criar aplicativos do Teams e instalar algumas ferramentas de desenvolvimento recomendadas.</span><span class="sxs-lookup"><span data-stu-id="bec21-126">Verify you have the right account for building Teams apps and install some recommended development tools.</span></span>

### <a name="set-up-your-development-account"></a><span data-ttu-id="bec21-127">Configurar sua conta de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="bec21-127">Set up your development account</span></span>

<span data-ttu-id="bec21-128">Você precisa de uma conta do Teams que permita o sideload de aplicativo personalizado.</span><span class="sxs-lookup"><span data-stu-id="bec21-128">You need a Teams account that allows custom app sideloading.</span></span> <span data-ttu-id="bec21-129">(Sua conta pode já fornecer isso.)</span><span class="sxs-lookup"><span data-stu-id="bec21-129">(Your account may already provide this.)</span></span>

1. <span data-ttu-id="bec21-130">Se você tiver uma conta do Teams, verifique se é possível fazer o sideload de aplicativos no Teams:</span><span class="sxs-lookup"><span data-stu-id="bec21-130">If you have a Teams account, verify if you can sideload apps in Teams:</span></span>
    1. <span data-ttu-id="bec21-131">No cliente do Teams, selecione **Aplicativos.**</span><span class="sxs-lookup"><span data-stu-id="bec21-131">In the Teams client, select **Apps**.</span></span>
    1. <span data-ttu-id="bec21-132">Procure uma opção para **carregar um aplicativo personalizado.**</span><span class="sxs-lookup"><span data-stu-id="bec21-132">Look for an option to **Upload a custom app**.</span></span>

    :::image type="content" source="../assets/images/build-your-first-app/upload-custom-app-closeup.png" alt-text="Imagem mostrando onde no Teams você pode carregar um aplicativo personalizado.":::

<!-- markdownlint-disable MD033 -->
<details>

<summary><span data-ttu-id="bec21-134"><b>Selecione aqui</b> se não conseguir ver a opção de sideload ou se não tiver uma conta do Teams.</span><span class="sxs-lookup"><span data-stu-id="bec21-134"><b>Select here</b> if you can't see the sideload option or don't have a Teams account.</span></span></summary>

<span data-ttu-id="bec21-135">Você pode obter uma conta de teste gratuita do Teams que permite o sideload do aplicativo in joining the Microsoft 365 developer program.</span><span class="sxs-lookup"><span data-stu-id="bec21-135">You can get a free Teams test account that allows app sideloading by joining the Microsoft 365 developer program.</span></span> <span data-ttu-id="bec21-136">(O processo de registro leva aproximadamente dois minutos.)</span><span class="sxs-lookup"><span data-stu-id="bec21-136">(The registration process takes approximately two minutes.)</span></span>

1. <span data-ttu-id="bec21-137">Vá para o [programa de desenvolvedor do Microsoft 365.](https://developer.microsoft.com/microsoft-365/dev-program)</span><span class="sxs-lookup"><span data-stu-id="bec21-137">Go to the [Microsoft 365 developer program](https://developer.microsoft.com/microsoft-365/dev-program).</span></span>
1. <span data-ttu-id="bec21-138">Selecione **Ingressar Agora** e siga as instruções na tela.</span><span class="sxs-lookup"><span data-stu-id="bec21-138">Select **Join Now** and follow the onscreen instructions.</span></span>
1. <span data-ttu-id="bec21-139">Quando você chegar à tela de boas-vindas, selecione **Configurar assinatura do E5.**</span><span class="sxs-lookup"><span data-stu-id="bec21-139">When you get to the welcome screen, select **Set up E5 subscription**.</span></span>
1. <span data-ttu-id="bec21-140">Configurar sua conta de administrador.</span><span class="sxs-lookup"><span data-stu-id="bec21-140">Set up your administrator account.</span></span> <span data-ttu-id="bec21-141">Depois de concluir, você deverá ver uma tela como esta.</span><span class="sxs-lookup"><span data-stu-id="bec21-141">Once you finish, you should see a screen like this.</span></span>
:::image type="content" source="../assets/images/build-your-first-app/dev-program-subscription.png" alt-text="Exemplo do que você vê depois de se inscrever no programa para desenvolvedores do Microsoft 365.":::
1. <span data-ttu-id="bec21-143">Entre no Teams usando a conta de administrador que você acabou de configurar.</span><span class="sxs-lookup"><span data-stu-id="bec21-143">Log in to Teams using the administrator account you just set up.</span></span>
1. <span data-ttu-id="bec21-144">Verifique se agora você tem **a opção Carregar um aplicativo** personalizado.</span><span class="sxs-lookup"><span data-stu-id="bec21-144">Verify if you now have the **Upload a custom app** option.</span></span>

</details>

> [!Note]
> <span data-ttu-id="bec21-145">Se você ainda não conseguir fazer o sideload de aplicativos, confira habilitar aplicativos personalizados do Teams e [ativar o carregamento de aplicativos personalizados.](https://docs.microsoft.com/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant#enable-custom-teams-apps-and-turn-on-custom-app-uploading)</span><span class="sxs-lookup"><span data-stu-id="bec21-145">If you still can't sideload apps, see [enable custom Teams apps and turn on custom app uploading](https://docs.microsoft.com/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant#enable-custom-teams-apps-and-turn-on-custom-app-uploading).</span></span>

### <a name="install-your-development-tools"></a><span data-ttu-id="bec21-146">Instalar suas ferramentas de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="bec21-146">Install your development tools</span></span>

<span data-ttu-id="bec21-147">Você pode criar aplicativos do Teams com suas ferramentas preferidas, mas essas lições mostram como você pode começar rapidamente com o Microsoft Teams Toolkit para Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="bec21-147">You can build Teams apps with your preferred tools, but these lessons show how you can get started quickly with the Microsoft Teams Toolkit for Visual Studio Code.</span></span>

<span data-ttu-id="bec21-148">O Teams exibe o conteúdo do aplicativo somente por meio de conexões HTTPS.</span><span class="sxs-lookup"><span data-stu-id="bec21-148">Teams displays app content only through HTTPS connections.</span></span> <span data-ttu-id="bec21-149">Para depurar certos tipos de aplicativos localmente, como um bot, você aprenderá a usar [o ngrok](../concepts/build-and-test/debug.md#locally-hosted) para configurar um túnel seguro entre o Teams e seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bec21-149">To debug certain types of apps locally, such as a bot, you'll learn how to use [ngrok to set up a secure tunnel](../concepts/build-and-test/debug.md#locally-hosted) between Teams and your app.</span></span> <span data-ttu-id="bec21-150">(Os aplicativos do Teams de produção são hospedados na nuvem.)</span><span class="sxs-lookup"><span data-stu-id="bec21-150">(Production Teams apps are hosted in the cloud.)</span></span>

1. <span data-ttu-id="bec21-151">Instale o [Node.js](https://nodejs.org/en/).</span><span class="sxs-lookup"><span data-stu-id="bec21-151">Install [Node.js](https://nodejs.org/en/).</span></span>
1. <span data-ttu-id="bec21-152">Instale [o ngrok](https://ngrok.com/download) se você planeja criar um bot ou extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="bec21-152">Install [ngrok](https://ngrok.com/download) if you plan to build a bot or messaging extension.</span></span>
1. <span data-ttu-id="bec21-153">Instale a versão mais recente do [Visual Studio Code.](https://code.visualstudio.com/download)</span><span class="sxs-lookup"><span data-stu-id="bec21-153">Install the latest version of [Visual Studio Code](https://code.visualstudio.com/download).</span></span> <span data-ttu-id="bec21-154">(As versões anteriores podem não funcionar com o kit de ferramentas.)</span><span class="sxs-lookup"><span data-stu-id="bec21-154">(Earlier versions might not work with the toolkit.)</span></span>
1. No Visual Studio Code, selecione **Extensões na** :::image type="icon" source="../assets/icons/vs-code-extensions.png"::: Barra de Atividades à esquerda e instale o Kit de Ferramentas do Microsoft **Teams.**

    :::image type="content" source="../assets/images/build-your-first-app/vsc-install-toolkit.png" alt-text="Imagem mostrando onde no Visual Studio Code você pode instalar a extensão do Kit de Ferramentas do Microsoft Teams.":::

## <a name="about-the-tutorials"></a><span data-ttu-id="bec21-157">Sobre os tutoriais</span><span class="sxs-lookup"><span data-stu-id="bec21-157">About the tutorials</span></span>

<span data-ttu-id="bec21-158">Você pode começar com qualquer uma das lições de **iniciação do** Teams.</span><span class="sxs-lookup"><span data-stu-id="bec21-158">You can start with any of the Teams **get started** lessons.</span></span> <span data-ttu-id="bec21-159">Se você não tiver certeza de onde ir primeiro, siga nosso caminho amigável para iniciantes e crie um "Hello, World!"</span><span class="sxs-lookup"><span data-stu-id="bec21-159">If you're not sure where to go first, follow our beginner friendly path and build a "Hello, World!"</span></span> <span data-ttu-id="bec21-160">app.</span><span class="sxs-lookup"><span data-stu-id="bec21-160">app.</span></span>

:::image type="content" source="../assets/images/build-your-first-app/skill-tree-overview.png" alt-text="Árvore de habilidades mostrando caminhos de aprendizagem para as lições de &quot;começar&quot; do Teams." border="false":::

## <a name="next-step"></a><span data-ttu-id="bec21-162">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="bec21-162">Next step</span></span>

<span data-ttu-id="bec21-163">Depois de configurar sua conta e seu ambiente, você pode começar a criar.</span><span class="sxs-lookup"><span data-stu-id="bec21-163">Once you set up your account and environment, you can start building.</span></span>

### <a name="beginner-friendly-tutorial"></a><span data-ttu-id="bec21-164">Tutorial amigável para iniciantes</span><span class="sxs-lookup"><span data-stu-id="bec21-164">Beginner friendly tutorial</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bec21-165">Criar um aplicativo "Hello, World!"</span><span class="sxs-lookup"><span data-stu-id="bec21-165">Build a "Hello, World!" app</span></span>](../build-your-first-app/build-and-run.md)

### <a name="other-tutorials"></a><span data-ttu-id="bec21-166">Outros tutoriais</span><span class="sxs-lookup"><span data-stu-id="bec21-166">Other tutorials</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bec21-167">Construir um bot</span><span class="sxs-lookup"><span data-stu-id="bec21-167">Build a bot</span></span>](../build-your-first-app/build-bot.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="bec21-168">Construir uma extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="bec21-168">Build a messaging extension</span></span>](../build-your-first-app/build-messaging-extension.md)
