---
title: Criar aplicativos com o Teams Toolkit e Visual Studio
description: Começar a criar grandes aplicativos personalizados diretamente Visual Studio com o Microsoft Teams Toolkit
keywords: kit de ferramentas do visual studio do teams
localization_priority: Normal
ms.topic: overview
ms.author: johmil
ms.openlocfilehash: 6a0f466ba0d95312695be8b5460fc949e3f70811
ms.sourcegitcommit: 4ac93d69927791a8ccf678ca5ee83e63b51566b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2021
ms.locfileid: "53095511"
---
# <a name="build-apps-with-the-teams-toolkit-and-visual-studio"></a><span data-ttu-id="82dcb-104">Criar aplicativos com o Teams Toolkit e Visual Studio</span><span class="sxs-lookup"><span data-stu-id="82dcb-104">Build apps with the Teams Toolkit and Visual Studio</span></span>

<span data-ttu-id="82dcb-105">O Kit de Ferramentas do Microsoft Teams permite criar aplicativos personalizados do Teams diretamente no ambiente de desenvolvimento integrado (IDE) do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="82dcb-105">The Microsoft Teams Toolkit enables you to create custom Teams apps directly within the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="82dcb-106">O kit de ferramentas do Microsoft Teams guia você através do processo e fornece o necessário para criar, depurar e iniciar seu aplicativo do Teams.</span><span class="sxs-lookup"><span data-stu-id="82dcb-106">The Microsoft Teams toolkit guides you through the process and provides everything you need to build, debug, and launch your Teams app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="82dcb-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="82dcb-107">Prerequisites</span></span>

1. <span data-ttu-id="82dcb-108">[Habilitar a visualização do desenvolvedor](../resources/dev-preview/developer-preview-intro.md#enable-developer-preview).</span><span class="sxs-lookup"><span data-stu-id="82dcb-108">[Enable developer preview](../resources/dev-preview/developer-preview-intro.md#enable-developer-preview).</span></span>

2. <span data-ttu-id="82dcb-109">Certifique-se de que o **<span>ASP.NET</span> e** o módulo de desenvolvimento da Web foram adicionados à sua Visual Studio instância.</span><span class="sxs-lookup"><span data-stu-id="82dcb-109">Make sure that the **<span>ASP.NET</span> and web development module** has been added to your Visual Studio instance.</span></span> <span data-ttu-id="82dcb-110">Para obter mais informações, consulte [Modify Visual Studio by adding or remove workloads and components](/visualstudio/install/modify-visual-studio?view=vs-2019&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="82dcb-110">For more information, see [Modify Visual Studio by adding or removing workloads and components](/visualstudio/install/modify-visual-studio?view=vs-2019&preserve-view=true).</span></span>

![Módulo de asp.net visual studio](../assets/images/visual-studio-web-dev-module.png)

## <a name="install-the-teams-toolkit"></a><span data-ttu-id="82dcb-112">Instalar o Teams Toolkit</span><span class="sxs-lookup"><span data-stu-id="82dcb-112">Install the Teams Toolkit</span></span>

<span data-ttu-id="82dcb-113">O Microsoft Teams Toolkit para Visual Studio está disponível para download no [marketplace do Visual Studio ou](https://marketplace.visualstudio.com/items?itemName=msft-vsteamstoolkit.vsteamstoolkit) diretamente no menu **Extensões** no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="82dcb-113">The Microsoft Teams Toolkit for Visual Studio is available for download from the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=msft-vsteamstoolkit.vsteamstoolkit) or directly from the **Extensions** menu within Visual Studio.</span></span>

## <a name="use-the-toolkit"></a><span data-ttu-id="82dcb-114">Usar o kit de ferramentas</span><span class="sxs-lookup"><span data-stu-id="82dcb-114">Use the toolkit</span></span>

- [<span data-ttu-id="82dcb-115">Configurar um novo projeto</span><span class="sxs-lookup"><span data-stu-id="82dcb-115">Set up a new project</span></span>](#set-up-a-new-teams-project)
- [<span data-ttu-id="82dcb-116">Configurar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="82dcb-116">Configure your app</span></span>](#configure-your-app)
- [<span data-ttu-id="82dcb-117">Execute seu aplicativo em Teams</span><span class="sxs-lookup"><span data-stu-id="82dcb-117">Run your app in Teams</span></span>](#install-and-run-your-app-locally)
- [<span data-ttu-id="82dcb-118">Valide o seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="82dcb-118">Validate your app</span></span>](#validate-your-app)
- [<span data-ttu-id="82dcb-119">Publicar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="82dcb-119">Publish your app</span></span>](#publish-your-app-to-teams)

## <a name="set-up-a-new-teams-project"></a><span data-ttu-id="82dcb-120">Configurar um novo Teams projeto</span><span class="sxs-lookup"><span data-stu-id="82dcb-120">Set up a new Teams project</span></span>

1. <span data-ttu-id="82dcb-121">Iniciar Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="82dcb-121">Launch Visual Studio 2019.</span></span>
2. <span data-ttu-id="82dcb-122">Selecione **Criar um novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="82dcb-122">Select **Create a new project**.</span></span>
3. <span data-ttu-id="82dcb-123">Pesquise **Microsoft Teams App e** selecione **Próximo**.</span><span class="sxs-lookup"><span data-stu-id="82dcb-123">Search for **Microsoft Teams App** and select **Next**.</span></span>
4. <span data-ttu-id="82dcb-124">Na **configuração do novo projeto,** insira **o** nome Project, **Local** e Nome **da solução.**</span><span class="sxs-lookup"><span data-stu-id="82dcb-124">In the **Configure your new project**, enter the **Project name**, **Location**, and **Solution name**.</span></span>
5. <span data-ttu-id="82dcb-125">Selecione **Próximo** para inserir um nome para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="82dcb-125">Select **Next** to enter a name for the app.</span></span>
6. <span data-ttu-id="82dcb-126">Na tela Informações Adicionais, insira um **Nome do Aplicativo** e Nome do Desenvolvedor **ou** Empresa para seu Teams app.</span><span class="sxs-lookup"><span data-stu-id="82dcb-126">In the Additional Information screen, enter an **Application Name** and **Developer or Company name** for your Teams app.</span></span>

## <a name="configure-your-app"></a><span data-ttu-id="82dcb-127">Configurar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="82dcb-127">Configure your app</span></span>

<span data-ttu-id="82dcb-128">No seu núcleo, o Teams aplicativo abrange três componentes:</span><span class="sxs-lookup"><span data-stu-id="82dcb-128">At its core, the Teams app embraces three components:</span></span>

- <span data-ttu-id="82dcb-129">O Microsoft Teams cliente (Web, desktop ou móvel) onde os usuários interagem com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="82dcb-129">The Microsoft Teams client (web, desktop or mobile) where users interact with your app.</span></span>
- <span data-ttu-id="82dcb-130">Um servidor que responde a solicitações de conteúdo exibido em Teams.</span><span class="sxs-lookup"><span data-stu-id="82dcb-130">A server that responds to requests for content displayed in Teams.</span></span> <span data-ttu-id="82dcb-131">Por exemplo, conteúdo de guia HTML ou um cartão adaptável de bot.</span><span class="sxs-lookup"><span data-stu-id="82dcb-131">For example, HTML tab content or a bot adaptive card.</span></span>
- <span data-ttu-id="82dcb-132">Um Teams de aplicativo consiste em três arquivos:</span><span class="sxs-lookup"><span data-stu-id="82dcb-132">A Teams app package consists of three files:</span></span>

    > [!div class="checklist"]
    >
    > - <span data-ttu-id="82dcb-133">O manifest.json</span><span class="sxs-lookup"><span data-stu-id="82dcb-133">The manifest.json</span></span>
    > - <span data-ttu-id="82dcb-134">Um [ícone de cor](../resources/schema/manifest-schema.md#icons) para seu aplicativo ser exibido no catálogo de aplicativos público ou da organização.</span><span class="sxs-lookup"><span data-stu-id="82dcb-134">A [color icon](../resources/schema/manifest-schema.md#icons) for your app to display in the public or organization app catalog.</span></span>
    > - <span data-ttu-id="82dcb-135">Um [ícone de contorno](../resources/schema/manifest-schema.md#icons) para exibição na barra de Teams de atividades.</span><span class="sxs-lookup"><span data-stu-id="82dcb-135">An [outline icon](../resources/schema/manifest-schema.md#icons) for display on the Teams activity bar.</span></span>

<span data-ttu-id="82dcb-136">Quando um aplicativo é instalado, o cliente Teams analisado o arquivo de manifesto para determinar as informações necessárias, como o nome do seu aplicativo e a URL onde os serviços estão localizados.</span><span class="sxs-lookup"><span data-stu-id="82dcb-136">When an app is installed, the Teams client parses the manifest file to determine needed information like the name of your app and the URL where the services are located.</span></span>

> [!NOTE]
><span data-ttu-id="82dcb-137">Se você ainda não fez isso, você deve entrar na sua conta Microsoft 365 para continuar com o processo de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="82dcb-137">If you have not done so already, you must sign in to your Microsoft 365 account to continue with the development process.</span></span>
>
> <span data-ttu-id="82dcb-138">Se você não tiver uma conta Microsoft 365, poderá inscrever-se para uma assinatura Microsoft 365 programa de [desenvolvedor.](https://developer.microsoft.com/microsoft-365/dev-program)</span><span class="sxs-lookup"><span data-stu-id="82dcb-138">If you do not have a Microsoft 365 account, you can sign up for a [Microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program) subscription.</span></span> <span data-ttu-id="82dcb-139">Ele é gratuito por 90 dias e é renovado desde que você o use para atividades de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="82dcb-139">It's free for 90 days and renews as long as you are using it for development activity.</span></span> <span data-ttu-id="82dcb-140">Se você tiver uma assinatura Visual Studio Enterprise ou Professional, ambos os programas incluem uma assinatura de desenvolvedor Microsoft 365 gratuita [,](https://aka.ms/MyVisualStudioBenefits)ativa para o tempo de vida da sua assinatura Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="82dcb-140">If you have a Visual Studio Enterprise or Professional subscription, both programs include a free Microsoft 365 [developer subscription](https://aka.ms/MyVisualStudioBenefits), active for the life of your Visual Studio subscription.</span></span> <span data-ttu-id="82dcb-141">Para obter mais informações, [consulte configurar uma assinatura Microsoft 365 desenvolvedor.](/office/developer-program/office-365-developer-program-get-started)</span><span class="sxs-lookup"><span data-stu-id="82dcb-141">For more information, see [set up a Microsoft 365 developer subscription](/office/developer-program/office-365-developer-program-get-started).</span></span>

### <a name="configuration-steps"></a><span data-ttu-id="82dcb-142">Etapas de configuração</span><span class="sxs-lookup"><span data-stu-id="82dcb-142">Configuration steps</span></span>

1. <span data-ttu-id="82dcb-143">Para configurar seu aplicativo, selecione o menu **Project > TeamsFx > Configurar para SSO...**</span><span class="sxs-lookup"><span data-stu-id="82dcb-143">To configure your app, select the **Project > TeamsFx > Configure for SSO...** menu.</span></span>

<span data-ttu-id="82dcb-144">Quando solicitado, entre em sua conta da Microsoft que tenha um locatário do M365.</span><span class="sxs-lookup"><span data-stu-id="82dcb-144">When prompted, sign in to your Microsoft account that has an M365 tenant.</span></span>

## <a name="install-and-run-your-app-locally"></a><span data-ttu-id="82dcb-145">Instalar e executar seu aplicativo localmente</span><span class="sxs-lookup"><span data-stu-id="82dcb-145">Install and run your app locally</span></span>

<span data-ttu-id="82dcb-146">Pressione F5 para iniciar a depuração.</span><span class="sxs-lookup"><span data-stu-id="82dcb-146">Press F5 to start debugging.</span></span> <span data-ttu-id="82dcb-147">A caixa de diálogo de instalação do aplicativo é exibida no Teams cliente.</span><span class="sxs-lookup"><span data-stu-id="82dcb-147">The app installation dialog box appears in the Teams client.</span></span>

## <a name="validate-your-app"></a><span data-ttu-id="82dcb-148">Valide o seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="82dcb-148">Validate your app</span></span>

<span data-ttu-id="82dcb-149">O **Project > do TeamsFx Validar** > Teams manifesto permite verificar se o pacote do aplicativo é válido.</span><span class="sxs-lookup"><span data-stu-id="82dcb-149">The **Project > TeamsFx Validate > Teams Manifest** menu allows you to check that your app package is valid.</span></span>

## <a name="publish-your-app-to-teams"></a><span data-ttu-id="82dcb-150">Publicar seu aplicativo no Teams</span><span class="sxs-lookup"><span data-stu-id="82dcb-150">Publish your app to Teams</span></span>

<span data-ttu-id="82dcb-151">No [portal](https://dev.teams.microsoft.com/home)do desenvolvedor do Teams , você pode carregar seu aplicativo em uma equipe, enviar seu aplicativo para a loja de aplicativos personalizada da sua empresa para usuários em sua organização ou enviar seu aplicativo para a Fonte do Aplicativo para todos os Teams usuários.</span><span class="sxs-lookup"><span data-stu-id="82dcb-151">In the [Teams Developer Portal](https://dev.teams.microsoft.com/home), you can upload your app to a team, submit your app to your company custom app store for users in your organization, or submit your app to App Source for all Teams users.</span></span>

- <span data-ttu-id="82dcb-152">Seu administrador de TI revisará esses envios.</span><span class="sxs-lookup"><span data-stu-id="82dcb-152">Your IT admin will review these submissions.</span></span>
- <span data-ttu-id="82dcb-153">Você pode retornar à página **Publicar** para verificar o status do envio e saber se seu aplicativo foi aprovado ou rejeitado pelo administrador de TI. Isso também é onde você pode enviar atualizações para seu aplicativo ou cancelar quaisquer envios ativos no momento.</span><span class="sxs-lookup"><span data-stu-id="82dcb-153">You can return to the **Publish** page to check on your submission status and learn if your app was approved or rejected by your IT admin. This is also where you can submit updates to your app or cancel any currently active submissions.</span></span>

## <a name="next-step"></a><span data-ttu-id="82dcb-154">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="82dcb-154">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="82dcb-155">Criar e executar seu primeiro aplicativo Microsoft Teams com o Blazor</span><span class="sxs-lookup"><span data-stu-id="82dcb-155">Build and run your first Microsoft Teams app with Blazor</span></span>](../get-started/first-app-blazor.md)
