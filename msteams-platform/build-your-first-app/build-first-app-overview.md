---
title: Começar - Criar sua primeira visão geral do aplicativo e pré-requisitos
author: heath-hamilton
description: Saiba como começar com o desenvolvimento de aplicativos do Microsoft Teams e configurar seu ambiente.
ms.author: lajanuar
ms.date: 11/03/2020
ms.topic: quickstart
ms.openlocfilehash: 11bc263fae28866338abf37456ccf483d9f0a9fd
ms.sourcegitcommit: e78c9f51c4538212c53bb6c6a45a09d994896f09
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/05/2021
ms.locfileid: "51585859"
---
# <a name="build-your-first-microsoft-teams-app-overview"></a><span data-ttu-id="ab7ea-103">Criar sua primeira visão geral do aplicativo do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="ab7ea-103">Build your first Microsoft Teams app overview</span></span>

<span data-ttu-id="ab7ea-104">Nas **lições de início,** você aprende a criar aplicativos básicos do Teams.</span><span class="sxs-lookup"><span data-stu-id="ab7ea-104">In the **get started** lessons, you learn how to create basic Teams apps.</span></span> <span data-ttu-id="ab7ea-105">Cada tutorial mostra como criar um aplicativo do Teams simples e real enquanto apresenta ferramentas comuns, conceitos fundamentais e recursos mais avançados.</span><span class="sxs-lookup"><span data-stu-id="ab7ea-105">Each tutorial walks through how to build a simple, real-world Teams app while introducing you to common tools, fundamental concepts, and more advanced features.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="ab7ea-106">O que você aprenderá</span><span class="sxs-lookup"><span data-stu-id="ab7ea-106">What you'll learn</span></span>

<span data-ttu-id="ab7ea-107">Aqui está uma ideia do que você vai saber depois de passar pelas lições.</span><span class="sxs-lookup"><span data-stu-id="ab7ea-107">Here's an idea of what you'll know after going through the lessons.</span></span>

> [!div class="checklist"]
  >
  > * <span data-ttu-id="ab7ea-108">**Obter e** executar rapidamente com o Teams Toolkit : o Microsoft Teams Toolkit para Visual Studio Code cuida da criação do seu projeto de aplicativo e do scaffolding para que você possa ter um aplicativo em execução em minutos.</span><span class="sxs-lookup"><span data-stu-id="ab7ea-108">**Get up and running quickly with the Teams Toolkit**: The Microsoft Teams Toolkit for Visual Studio Code takes care of creating your app project and scaffolding so you can have a running app in minutes.</span></span>
  > * <span data-ttu-id="ab7ea-109">**Configure seu aplicativo com o App Studio:** especifique os recursos e serviços que seu aplicativo do Teams usa.</span><span class="sxs-lookup"><span data-stu-id="ab7ea-109">**Configure your app with App Studio**: Specify the capabilities and services your Teams app uses.</span></span>
  > * <span data-ttu-id="ab7ea-110">**Escopo da audiência do seu aplicativo:** crie um aplicativo do Teams para uso pessoal, colaboração ou ambos.</span><span class="sxs-lookup"><span data-stu-id="ab7ea-110">**Scope your app's audience**: Build a Teams app for personal use, collaboration, or both.</span></span>
> * <span data-ttu-id="ab7ea-111">**Obter experiência com ferramentas e SDKs** do Teams : Personalizar seu aplicativo com a ajuda do SDK do cliente JavaScript do Teams.</span><span class="sxs-lookup"><span data-stu-id="ab7ea-111">**Get experience with Teams tools and SDKs**: Customize your app with help from the Teams JavaScript client SDK.</span></span> <span data-ttu-id="ab7ea-112">Por exemplo, altere o esquema de cores do aplicativo para corresponder ao tema do Teams.</span><span class="sxs-lookup"><span data-stu-id="ab7ea-112">For example, change your app's color scheme to match the Teams theme.</span></span> <span data-ttu-id="ab7ea-113">Além disso, saiba mais sobre ferramentas comuns para criar e gerenciar bots.</span><span class="sxs-lookup"><span data-stu-id="ab7ea-113">Also, learn about common tools for creating and managing bots.</span></span>
  > * <span data-ttu-id="ab7ea-114">**Expanda em seu aplicativo**: ao longo das lições, você encontrará tópicos relacionados em que provavelmente está interessado (como diretrizes de autenticação e design).</span><span class="sxs-lookup"><span data-stu-id="ab7ea-114">**Expand on your app**: Throughout the lessons, you'll find related topics you're probably interested in (such as authentication and design guidelines).</span></span>

## <a name="teams-app-fundamentals"></a><span data-ttu-id="ab7ea-115">Fundamentos do aplicativo teams</span><span class="sxs-lookup"><span data-stu-id="ab7ea-115">Teams app fundamentals</span></span>

<span data-ttu-id="ab7ea-116">Antes de começar os tutoriais, você deve saber o seguinte sobre como criar aplicativos para o Teams.</span><span class="sxs-lookup"><span data-stu-id="ab7ea-116">Before you begin the tutorials, you should know the following about building apps for Teams.</span></span>

### <a name="apps-can-have-multiple-capabilities-and-entry-points"></a><span data-ttu-id="ab7ea-117">Os aplicativos podem ter vários recursos e pontos de entrada</span><span class="sxs-lookup"><span data-stu-id="ab7ea-117">Apps can have multiple capabilities and entry points</span></span>

<span data-ttu-id="ab7ea-118">Um aplicativo do Teams é feito de um ou mais recursos de plataforma [(como](../concepts/capabilities-overview.md) as pessoas usam o aplicativo) e pontos de entrada [(onde](../concepts/extensibility-points.md) as pessoas usam o aplicativo).</span><span class="sxs-lookup"><span data-stu-id="ab7ea-118">A Teams app is made up of one or more [platform capabilities](../concepts/capabilities-overview.md) (how people use the app) and [entry points](../concepts/extensibility-points.md) (where people use the app).</span></span>

### <a name="teams-doesnt-host-your-app"></a><span data-ttu-id="ab7ea-119">O Teams não hospeda seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="ab7ea-119">Teams doesn't host your app</span></span>

<span data-ttu-id="ab7ea-120">Um aplicativo do Teams inclui as seguintes partes importantes:</span><span class="sxs-lookup"><span data-stu-id="ab7ea-120">A Teams app includes the following important pieces:</span></span>

* <span data-ttu-id="ab7ea-121">A lógica, o armazenamento de dados e as chamadas de API que a energia do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ab7ea-121">The logic, data storage, and API calls that power your app.</span></span> <span data-ttu-id="ab7ea-122">Esses serviços não são hospedados pelo Teams e devem estar acessíveis por meio de HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ab7ea-122">These services are not hosted by Teams and must be accessible via HTTPS.</span></span>
* <span data-ttu-id="ab7ea-123">O cliente do Teams (web, área de trabalho ou celular) onde as pessoas usam seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ab7ea-123">The Teams client (web, desktop, or mobile) where people use your app.</span></span>
* <span data-ttu-id="ab7ea-124">Sua ID do aplicativo, que permite configurar seu aplicativo com o App Studio.</span><span class="sxs-lookup"><span data-stu-id="ab7ea-124">Your app ID, which lets you configure your app with App Studio.</span></span>

## <a name="get-prerequisites"></a><span data-ttu-id="ab7ea-125">Obter pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="ab7ea-125">Get prerequisites</span></span>

<span data-ttu-id="ab7ea-126">Verifique se você tem a conta certa para criar aplicativos do Teams e instalar algumas ferramentas de desenvolvimento recomendadas.</span><span class="sxs-lookup"><span data-stu-id="ab7ea-126">Verify you have the right account for building Teams apps and install some recommended development tools.</span></span>

### <a name="set-up-your-development-account"></a><span data-ttu-id="ab7ea-127">Configurar sua conta de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="ab7ea-127">Set up your development account</span></span>

<span data-ttu-id="ab7ea-128">Você precisa de uma conta do Teams que permita o sideload de aplicativo personalizado.</span><span class="sxs-lookup"><span data-stu-id="ab7ea-128">You need a Teams account that allows custom app sideloading.</span></span> <span data-ttu-id="ab7ea-129">(Sua conta pode já fornecer isso.)</span><span class="sxs-lookup"><span data-stu-id="ab7ea-129">(Your account may already provide this.)</span></span>

1. <span data-ttu-id="ab7ea-130">Se você tiver uma conta do Teams, verifique se pode fazer sideload de aplicativos no Teams:</span><span class="sxs-lookup"><span data-stu-id="ab7ea-130">If you have a Teams account, verify if you can sideload apps in Teams:</span></span>
    1. <span data-ttu-id="ab7ea-131">No cliente do Teams, selecione **Aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="ab7ea-131">In the Teams client, select **Apps**.</span></span>
    1. <span data-ttu-id="ab7ea-132">Procure uma opção para **Carregar um aplicativo personalizado.**</span><span class="sxs-lookup"><span data-stu-id="ab7ea-132">Look for an option to **Upload a custom app**.</span></span>

    :::image type="content" source="../assets/images/build-your-first-app/upload-custom-app-closeup.png" alt-text="Ilustração mostrando onde no Teams você pode carregar um aplicativo personalizado.":::
    
    <span data-ttu-id="ab7ea-134">Se você não vir o botão, não terá permissão para carregar aplicativos personalizados em sua organização. Você pode obter esse recurso se inscrever para uma assinatura gratuita do desenvolvedor do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="ab7ea-134">If you don't see the button, you don't have permission to upload custom apps in your org. You can get this feature by signing up for a free Microsoft 365 developer subscription.</span></span>

<!-- markdownlint-disable MD033 -->
<details>

<summary><span data-ttu-id="ab7ea-135"><b>Obter sua assinatura gratuita de desenvolvedor do Microsoft 365</b></span><span class="sxs-lookup"><span data-stu-id="ab7ea-135"><b>Get your free Microsoft 365 developer subscription</b></span></span></summary>

<span data-ttu-id="ab7ea-136">Você pode obter uma conta de teste gratuita do Teams que permite o sideload de aplicativos ao ingressar no programa de desenvolvedor do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="ab7ea-136">You can get a free Teams test account that allows app sideloading by joining the Microsoft 365 developer program.</span></span> <span data-ttu-id="ab7ea-137">(O processo de registro leva aproximadamente dois minutos.)</span><span class="sxs-lookup"><span data-stu-id="ab7ea-137">(The registration process takes approximately two minutes.)</span></span>

1. <span data-ttu-id="ab7ea-138">Vá para o programa de desenvolvedor do [Microsoft 365](https://developer.microsoft.com/microsoft-365/dev-program).</span><span class="sxs-lookup"><span data-stu-id="ab7ea-138">Go to the [Microsoft 365 developer program](https://developer.microsoft.com/microsoft-365/dev-program).</span></span>
1. <span data-ttu-id="ab7ea-139">Selecione **Ingressar agora** e siga as instruções na tela.</span><span class="sxs-lookup"><span data-stu-id="ab7ea-139">Select **Join Now** and follow the onscreen instructions.</span></span>
1. <span data-ttu-id="ab7ea-140">Quando você chegar à tela de boas-vindas, selecione **Configurar assinatura do E5**.</span><span class="sxs-lookup"><span data-stu-id="ab7ea-140">When you get to the welcome screen, select **Set up E5 subscription**.</span></span>
1. <span data-ttu-id="ab7ea-141">Configurar sua conta de administrador.</span><span class="sxs-lookup"><span data-stu-id="ab7ea-141">Set up your administrator account.</span></span> <span data-ttu-id="ab7ea-142">Depois de concluir, você deverá ver uma tela como esta.</span><span class="sxs-lookup"><span data-stu-id="ab7ea-142">Once you finish, you should see a screen like this.</span></span>
:::image type="content" source="../assets/images/build-your-first-app/dev-program-subscription.png" alt-text="Exemplo do que você vê depois de se inscrever no programa de desenvolvedor do Microsoft 365.":::
1. <span data-ttu-id="ab7ea-144">Faça logoff no Teams usando a conta de administrador que você acabou de configurar.</span><span class="sxs-lookup"><span data-stu-id="ab7ea-144">Log in to Teams using the administrator account you just set up.</span></span>
1. <span data-ttu-id="ab7ea-145">Verifique se agora você tem **a opção Carregar um aplicativo** personalizado.</span><span class="sxs-lookup"><span data-stu-id="ab7ea-145">Verify if you now have the **Upload a custom app** option.</span></span>

</details>

> [!Note]
> <span data-ttu-id="ab7ea-146">Se você ainda não puder fazer sideload de aplicativos, consulte [enable custom Teams apps and turn on custom app uploading](https://docs.microsoft.com/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant#enable-custom-teams-apps-and-turn-on-custom-app-uploading).</span><span class="sxs-lookup"><span data-stu-id="ab7ea-146">If you still can't sideload apps, see [enable custom Teams apps and turn on custom app uploading](https://docs.microsoft.com/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant#enable-custom-teams-apps-and-turn-on-custom-app-uploading).</span></span>

### <a name="install-your-development-tools"></a><span data-ttu-id="ab7ea-147">Instalar suas ferramentas de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="ab7ea-147">Install your development tools</span></span>

<span data-ttu-id="ab7ea-148">Você pode criar aplicativos do Teams com suas ferramentas preferenciais, mas essas lições mostram como você pode começar rapidamente com o Microsoft Teams Toolkit para Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="ab7ea-148">You can build Teams apps with your preferred tools, but these lessons show how you can get started quickly with the Microsoft Teams Toolkit for Visual Studio Code.</span></span>

<span data-ttu-id="ab7ea-149">O Teams exibe o conteúdo do aplicativo somente por meio de conexões HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ab7ea-149">Teams displays app content only through HTTPS connections.</span></span> <span data-ttu-id="ab7ea-150">Para depurar determinados tipos de aplicativos localmente, como um bot, você aprenderá a usar [o ngrok](../concepts/build-and-test/debug.md#locally-hosted) para configurar um túnel seguro entre o Teams e seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ab7ea-150">To debug certain types of apps locally, such as a bot, you'll learn how to use [ngrok to set up a secure tunnel](../concepts/build-and-test/debug.md#locally-hosted) between Teams and your app.</span></span> <span data-ttu-id="ab7ea-151">(Os aplicativos do Production Teams são hospedados na nuvem.)</span><span class="sxs-lookup"><span data-stu-id="ab7ea-151">(Production Teams apps are hosted in the cloud.)</span></span>

1. <span data-ttu-id="ab7ea-152">Instale o [Node.js](https://nodejs.org/en/).</span><span class="sxs-lookup"><span data-stu-id="ab7ea-152">Install [Node.js](https://nodejs.org/en/).</span></span>
1. <span data-ttu-id="ab7ea-153">Instale [o ngrok](https://ngrok.com/download) se você planeja criar um bot ou extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="ab7ea-153">Install [ngrok](https://ngrok.com/download) if you plan to build a bot or messaging extension.</span></span>
1. <span data-ttu-id="ab7ea-154">Instale a versão mais recente do [Visual Studio Code](https://code.visualstudio.com/download).</span><span class="sxs-lookup"><span data-stu-id="ab7ea-154">Install the latest version of [Visual Studio Code](https://code.visualstudio.com/download).</span></span> <span data-ttu-id="ab7ea-155">(As versões anteriores podem não funcionar com o kit de ferramentas.)</span><span class="sxs-lookup"><span data-stu-id="ab7ea-155">(Earlier versions might not work with the toolkit.)</span></span>
1. Em Visual Studio Código, selecione **Extensões** na Barra de Atividades à esquerda e instale o :::image type="icon" source="../assets/icons/vs-code-extensions.png"::: Microsoft Teams **Toolkit**.

    :::image type="content" source="../assets/images/build-your-first-app/vsc-install-toolkit.png" alt-text="Ilustração mostrando onde, Visual Studio Código, você pode instalar a extensão Toolkit Microsoft Teams.":::

## <a name="about-the-tutorials"></a><span data-ttu-id="ab7ea-158">Sobre os tutoriais</span><span class="sxs-lookup"><span data-stu-id="ab7ea-158">About the tutorials</span></span>

<span data-ttu-id="ab7ea-159">Você pode começar com qualquer uma das lições de início **do** Teams.</span><span class="sxs-lookup"><span data-stu-id="ab7ea-159">You can start with any of the Teams **get started** lessons.</span></span> <span data-ttu-id="ab7ea-160">Se você não tiver certeza de onde ir primeiro, siga nosso caminho amigável iniciante e crie um "Hello, World!"</span><span class="sxs-lookup"><span data-stu-id="ab7ea-160">If you're not sure where to go first, follow our beginner friendly path and build a "Hello, World!"</span></span> <span data-ttu-id="ab7ea-161">app.</span><span class="sxs-lookup"><span data-stu-id="ab7ea-161">app.</span></span>

:::image type="content" source="../assets/images/build-your-first-app/skill-tree-overview.png" alt-text="Árvore de habilidades mostrando caminhos de aprendizado para as lições de &quot;começar&quot; do Teams." border="false":::

## <a name="next-step"></a><span data-ttu-id="ab7ea-163">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="ab7ea-163">Next step</span></span>

<span data-ttu-id="ab7ea-164">Depois de configurar sua conta e seu ambiente, você pode começar a criar.</span><span class="sxs-lookup"><span data-stu-id="ab7ea-164">Once you set up your account and environment, you can start building.</span></span>

### <a name="beginner-friendly-tutorial"></a><span data-ttu-id="ab7ea-165">Tutorial amigável para iniciantes</span><span class="sxs-lookup"><span data-stu-id="ab7ea-165">Beginner friendly tutorial</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ab7ea-166">Criar um aplicativo "Hello, World!"</span><span class="sxs-lookup"><span data-stu-id="ab7ea-166">Build a "Hello, World!" app</span></span>](../build-your-first-app/build-and-run.md)

### <a name="other-tutorials"></a><span data-ttu-id="ab7ea-167">Outros tutoriais</span><span class="sxs-lookup"><span data-stu-id="ab7ea-167">Other tutorials</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ab7ea-168">Construir um bot</span><span class="sxs-lookup"><span data-stu-id="ab7ea-168">Build a bot</span></span>](../build-your-first-app/build-bot.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="ab7ea-169">Construir uma extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="ab7ea-169">Build a messaging extension</span></span>](../build-your-first-app/build-messaging-extension.md)
