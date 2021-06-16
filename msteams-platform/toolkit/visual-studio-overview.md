---
title: Criar aplicativos com o Teams Toolkit e Visual Studio
description: Começar a criar grandes aplicativos personalizados diretamente Visual Studio com o Microsoft Teams Toolkit
keywords: kit de ferramentas do visual studio do teams
localization_priority: Normal
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: 996037f5bb1caaa2493e1eebe51039724822fef9
ms.sourcegitcommit: 9f499908437655d6ebdc6c4b3c3603ee220315b7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/15/2021
ms.locfileid: "52949690"
---
# <a name="build-apps-with-the-teams-toolkit-and-visual-studio"></a><span data-ttu-id="3a7c6-104">Criar aplicativos com o Teams Toolkit e Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3a7c6-104">Build apps with the Teams Toolkit and Visual Studio</span></span>

<span data-ttu-id="3a7c6-105">O Kit de Ferramentas do Microsoft Teams permite criar aplicativos personalizados do Teams diretamente no ambiente de desenvolvimento integrado (IDE) do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3a7c6-105">The Microsoft Teams Toolkit enables you to create custom Teams apps directly within the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="3a7c6-106">O kit de ferramentas do Microsoft Teams guia você através do processo e fornece o necessário para criar, depurar e iniciar seu aplicativo do Teams.</span><span class="sxs-lookup"><span data-stu-id="3a7c6-106">The Microsoft Teams toolkit guides you through the process and provides everything you need to build, debug, and launch your Teams app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3a7c6-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="3a7c6-107">Prerequisites</span></span>

1. <span data-ttu-id="3a7c6-108">[Habilitar a visualização do desenvolvedor](../resources/dev-preview/developer-preview-intro.md#enable-developer-preview).</span><span class="sxs-lookup"><span data-stu-id="3a7c6-108">[Enable developer preview](../resources/dev-preview/developer-preview-intro.md#enable-developer-preview).</span></span>

1. <span data-ttu-id="3a7c6-109">Certifique-se de que **<span>o ASP.NE</span>T e** o módulo de desenvolvimento da Web foram adicionados à sua Visual Studio instância.</span><span class="sxs-lookup"><span data-stu-id="3a7c6-109">Make sure that the **<span>ASP.NE</span>T and web development module** has been added to your Visual Studio instance.</span></span> <span data-ttu-id="3a7c6-110">Você pode verificar seguindo as etapas na Visual Studio [adicionando ou removendo cargas](/visualstudio/install/modify-visual-studio?view=vs-2019&preserve-view=true) de trabalho e documentação de componentes.</span><span class="sxs-lookup"><span data-stu-id="3a7c6-110">You can check by following the steps in the [modify Visual Studio by adding or removing workloads and component](/visualstudio/install/modify-visual-studio?view=vs-2019&preserve-view=true) documentation.</span></span>

![Módulo de asp.net visual studio](../assets/images/visual-studio-web-dev-module.png)

3. <span data-ttu-id="3a7c6-112">Se você deseja testar seu aplicativo implantando-o Visual Studio, você deve ter Serviços de Informações da Internet (IIS)) instalado em seu ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="3a7c6-112">If you want to test your app by deploying it from Visual Studio, you must have Internet Information Services (IIS)) installed in your development environment.</span></span> <span data-ttu-id="3a7c6-113">Visual Studio não inclui o IIS e ele não está incluído na configuração padrão Windows 10, Windows 8 ou Windows 7; no entanto, você pode baixar a versão mais recente do centro [de download da Microsoft.](https://www.microsoft.com/download/details.aspx?id=48264)</span><span class="sxs-lookup"><span data-stu-id="3a7c6-113">Visual Studio does not include IIS and it is not included in the default Windows 10, Windows 8, or Windows 7 configuration; however, you can download the latest version from the [Microsoft download center](https://www.microsoft.com/download/details.aspx?id=48264).</span></span>

![Exibição de página de download do IIS](../assets/images/iis.png)

## <a name="install-the-teams-toolkit"></a><span data-ttu-id="3a7c6-115">Instalar o Teams Toolkit</span><span class="sxs-lookup"><span data-stu-id="3a7c6-115">Install the Teams Toolkit</span></span>

<span data-ttu-id="3a7c6-116">O Microsoft Teams Toolkit para Visual Studio está disponível para download no [marketplace do Visual Studio ou](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.vsteamstemplate) diretamente no menu **Extensões** no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3a7c6-116">The Microsoft Teams Toolkit for Visual Studio is available for download from the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.vsteamstemplate) or directly from the **Extensions** menu within Visual Studio.</span></span> <span data-ttu-id="3a7c6-117">A partir do Visual Studio Marketplace também baixar [Teams Toolkit para Visual Studio 2019](https://marketplace.visualstudio.com/items?itemName=msft-vsteamstoolkit.vsteamstoolkit).</span><span class="sxs-lookup"><span data-stu-id="3a7c6-117">From the Visual Studio Marketplace also download [Teams Toolkit for Visual Studio 2019](https://marketplace.visualstudio.com/items?itemName=msft-vsteamstoolkit.vsteamstoolkit).</span></span>

## <a name="using-the-toolkit"></a><span data-ttu-id="3a7c6-118">Usando o kit de ferramentas</span><span class="sxs-lookup"><span data-stu-id="3a7c6-118">Using the toolkit</span></span>

- [<span data-ttu-id="3a7c6-119">Configurar um novo projeto</span><span class="sxs-lookup"><span data-stu-id="3a7c6-119">Set up a new project</span></span>](#set-up-a-new-teams-project)
- [<span data-ttu-id="3a7c6-120">Configurar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="3a7c6-120">Configure your app</span></span>](#configure-your-app)
- [<span data-ttu-id="3a7c6-121">Empacote seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="3a7c6-121">Package your app</span></span>](#package-your-app)
- [<span data-ttu-id="3a7c6-122">Instalar e executar seu aplicativo em Teams</span><span class="sxs-lookup"><span data-stu-id="3a7c6-122">Install and run your app in Teams</span></span>](#install-and-run-your-app-locally)
- [<span data-ttu-id="3a7c6-123">Valide o seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="3a7c6-123">Validate your app</span></span>](#validate-your-app)
- [<span data-ttu-id="3a7c6-124">Publicar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="3a7c6-124">Publish your app</span></span>](#publish-your-app-to-teams)

## <a name="set-up-a-new-teams-project"></a><span data-ttu-id="3a7c6-125">Configurar um novo Teams projeto</span><span class="sxs-lookup"><span data-stu-id="3a7c6-125">Set up a new Teams project</span></span>

![Teams kit de ferramentas instalado](../assets/images/teamstoolkiticon.png)

1. <span data-ttu-id="3a7c6-127">Selecione **Criar Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="3a7c6-127">Select **Create New Project**.</span></span>

    ![Criar novo projeto](../assets/images/createnewproject.png)

1. <span data-ttu-id="3a7c6-129">Escolha a ferramenta de início rápido para **Microsoft Teams App** e selecione **Próximo**.</span><span class="sxs-lookup"><span data-stu-id="3a7c6-129">Choose the quickstart tool for **Microsoft Teams App** and select **Next**.</span></span>
1. <span data-ttu-id="3a7c6-130">Na página **Configurar seu novo projeto,** insira **o** nome do Project, **Local** e Nome **da solução.**</span><span class="sxs-lookup"><span data-stu-id="3a7c6-130">In the **Configure your new project** page, enter the **Project name**, **Location**, and **Solution name**.</span></span>
1. <span data-ttu-id="3a7c6-131">Selecione a **solução Place e o projeto na mesma caixa de** seleção de diretório.</span><span class="sxs-lookup"><span data-stu-id="3a7c6-131">Select the **Place solution and project in the same directory** checkbox.</span></span>
1. <span data-ttu-id="3a7c6-132">Na janela **pop-up Adicionar Recursos,** escolha um ou mais recursos para a configuração do projeto.</span><span class="sxs-lookup"><span data-stu-id="3a7c6-132">In the **Add Capabilities** pop-up window, choose one or more capabilities for your project setup.</span></span>
1. <span data-ttu-id="3a7c6-133">Selecione o **botão Próximo** para concluir o processo de configuração.</span><span class="sxs-lookup"><span data-stu-id="3a7c6-133">Select the **Next** button to complete the configuration process.</span></span>
1. <span data-ttu-id="3a7c6-134">Na janela **pop-up Adicionar Recursos,** escolha as propriedades para cada recurso selecionado.</span><span class="sxs-lookup"><span data-stu-id="3a7c6-134">In the **Add Capabilities** pop-up window, choose the properties for each selected capability.</span></span>
1. <span data-ttu-id="3a7c6-135">Selecione **Concluir**.</span><span class="sxs-lookup"><span data-stu-id="3a7c6-135">Select **Finish**.</span></span> <span data-ttu-id="3a7c6-136">A **Microsoft Teams Toolkit** de aterrissagem é mostrada.</span><span class="sxs-lookup"><span data-stu-id="3a7c6-136">The **Microsoft Teams Toolkit** landing page is shown.</span></span>

    ![Teams de aterrissagem do kit de ferramentas](../assets/images/Teamstoolkitpage.png)

## <a name="configure-your-app"></a><span data-ttu-id="3a7c6-138">Configurar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="3a7c6-138">Configure your app</span></span>

<span data-ttu-id="3a7c6-139">No seu núcleo, o Teams aplicativo abrange três componentes:</span><span class="sxs-lookup"><span data-stu-id="3a7c6-139">At its core, the Teams app embraces three components:</span></span>

  1. <span data-ttu-id="3a7c6-140">O Microsoft Teams cliente, incluindo web, área de trabalho ou celular, onde os usuários interagem com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3a7c6-140">The Microsoft Teams client including web, desktop, or mobile, where users interact with your app.</span></span>
  1. <span data-ttu-id="3a7c6-141">Um servidor que responde a solicitações de conteúdo que é exibido em Teams, por exemplo, conteúdo de guia HTML ou um cartão adaptável de bot.</span><span class="sxs-lookup"><span data-stu-id="3a7c6-141">A server that responds to requests for content that is displayed in Teams, for example, HTML tab content or a bot adaptive card.</span></span>
  1. <span data-ttu-id="3a7c6-142">Um Teams de aplicativo consiste em três arquivos:</span><span class="sxs-lookup"><span data-stu-id="3a7c6-142">A Teams app package consists of three files:</span></span>

      - <span data-ttu-id="3a7c6-143">O manifest.json</span><span class="sxs-lookup"><span data-stu-id="3a7c6-143">The manifest.json</span></span>
      - <span data-ttu-id="3a7c6-144">Um [ícone de cor](../resources/schema/manifest-schema.md#icons) para seu aplicativo ser exibido no catálogo de aplicativos público ou da organização.</span><span class="sxs-lookup"><span data-stu-id="3a7c6-144">A [color icon](../resources/schema/manifest-schema.md#icons) for your app to display in the public or organization app catalog.</span></span>
      - <span data-ttu-id="3a7c6-145">Um [ícone de contorno](../resources/schema/manifest-schema.md#icons) para exibição na barra de Teams de atividades.</span><span class="sxs-lookup"><span data-stu-id="3a7c6-145">An [outline icon](../resources/schema/manifest-schema.md#icons) for display on the Teams activity bar.</span></span>

<span data-ttu-id="3a7c6-146">Quando um aplicativo é instalado, o cliente Teams analisado o arquivo de manifesto para determinar as informações necessárias, como o nome do seu aplicativo e a URL onde os serviços estão localizados.</span><span class="sxs-lookup"><span data-stu-id="3a7c6-146">When an app is installed, the Teams client parses the manifest file to determine needed information like the name of your app and the URL where the services are located.</span></span>

> [!NOTE]
><span data-ttu-id="3a7c6-147">Se você ainda não fez isso, você deve entrar na sua conta Microsoft 365 para continuar com o processo de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="3a7c6-147">If you have not done so already, you must sign in to your Microsoft 365 account to continue with the development process.</span></span>
>
> <span data-ttu-id="3a7c6-148">Se você não tiver uma conta Microsoft 365, poderá inscrever-se para uma assinatura Microsoft 365 programa de [desenvolvedor.](https://developer.microsoft.com/microsoft-365/dev-program)</span><span class="sxs-lookup"><span data-stu-id="3a7c6-148">If you do not have a Microsoft 365 account, you can sign up for a [Microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program) subscription.</span></span> <span data-ttu-id="3a7c6-149">Ele é gratuito por 90 dias e é renovado desde que você o use para atividades de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="3a7c6-149">It's free for 90 days and renews as long as you are using it for development activity.</span></span> <span data-ttu-id="3a7c6-150">Se você tiver uma assinatura Visual Studio Enterprise ou Professional, ambos os programas incluem uma assinatura de desenvolvedor Microsoft 365 gratuita [,](https://aka.ms/MyVisualStudioBenefits)ativa para o tempo de vida da sua assinatura Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3a7c6-150">If you have a Visual Studio Enterprise or Professional subscription, both programs include a free Microsoft 365 [developer subscription](https://aka.ms/MyVisualStudioBenefits), active for the life of your Visual Studio subscription.</span></span> <span data-ttu-id="3a7c6-151">Para obter mais informações, [consulte configurar uma assinatura Microsoft 365 desenvolvedor.](/office/developer-program/office-365-developer-program-get-started)</span><span class="sxs-lookup"><span data-stu-id="3a7c6-151">For more information, see [set up a Microsoft 365 developer subscription](/office/developer-program/office-365-developer-program-get-started).</span></span>

### <a name="configuration-steps"></a><span data-ttu-id="3a7c6-152">Etapas de configuração</span><span class="sxs-lookup"><span data-stu-id="3a7c6-152">Configuration steps</span></span>

1. <span data-ttu-id="3a7c6-153">Para configurar seu aplicativo, na **página** inicial Microsoft Teams Toolkit, selecione **Editar pacote de aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="3a7c6-153">To configure your app, on the **Microsoft Teams Toolkit** landing page, select **Edit app package**.</span></span>
1. <span data-ttu-id="3a7c6-154">No menu **suspenso Meus Ambientes,** selecione **desenvolvimento**.</span><span class="sxs-lookup"><span data-stu-id="3a7c6-154">From the **My Environments** drop-down menu, select **development**.</span></span>
1. <span data-ttu-id="3a7c6-155">Na página **Detalhes do** aplicativo, edite os campos de propriedade do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3a7c6-155">In the **App details** page, edit your app's property fields.</span></span>
    
    <span data-ttu-id="3a7c6-156">A edição dos campos na página detalhes do aplicativo atualiza o conteúdo do manifest.jsno arquivo que será shipado como parte do pacote do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3a7c6-156">Editing the fields in the App details page updates the contents of the manifest.json file that will ship as part of the app package.</span></span> <span data-ttu-id="3a7c6-157">Para obter mais informações, [consulte Teams Toolkit manifesto](https://aka.ms/teams-toolkit-manifest).</span><span class="sxs-lookup"><span data-stu-id="3a7c6-157">For more information, see [Teams Toolkit manifest](https://aka.ms/teams-toolkit-manifest).</span></span>

## <a name="package-your-app"></a><span data-ttu-id="3a7c6-158">Empacote seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="3a7c6-158">Package your app</span></span>

<span data-ttu-id="3a7c6-159">Modificar a página de detalhes **do** aplicativo ou atualizar o **manifesto** ou **arquivos .env** na pasta **.publish** do aplicativo gerará automaticamente seu **arquivoDevelopment.zip.**</span><span class="sxs-lookup"><span data-stu-id="3a7c6-159">Modifying the **app details** page or updating the **manifest**, or **.env** files in your app's  **.publish** folder will automatically generate your **Development.zip** file.</span></span> <span data-ttu-id="3a7c6-160">O Development.zip inclui três arquivos necessários, omanifest.js **e** [dois ícones](../concepts/build-and-test/apps-package.md#app-icons).</span><span class="sxs-lookup"><span data-stu-id="3a7c6-160">The Development.zip file includes three required files, the **manifest.json** and [two icons](../concepts/build-and-test/apps-package.md#app-icons).</span></span>

## <a name="install-and-run-your-app-locally"></a><span data-ttu-id="3a7c6-161">Instalar e executar seu aplicativo localmente</span><span class="sxs-lookup"><span data-stu-id="3a7c6-161">Install and run your app locally</span></span>

1. <span data-ttu-id="3a7c6-162">No menu **suspenso Configurações** da Solução, selecione **Implantar** conforme mostrado na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="3a7c6-162">From the **Solution Configurations** dropdown menu, select **Deploy** as shown in the following image:</span></span>

    ![Menu Configurações da solução](../assets/images/solution-configurations.png)

1. <span data-ttu-id="3a7c6-164">Selecione o **IIS Express + Teams** botão.</span><span class="sxs-lookup"><span data-stu-id="3a7c6-164">Select the **IIS Express + Teams** button.</span></span>

    <span data-ttu-id="3a7c6-165">A caixa de diálogo de instalação do aplicativo é exibida no Teams cliente.</span><span class="sxs-lookup"><span data-stu-id="3a7c6-165">The app installation dialog box appears in the Teams client.</span></span>

## <a name="validate-your-app"></a><span data-ttu-id="3a7c6-166">Valide o seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="3a7c6-166">Validate your app</span></span>

<span data-ttu-id="3a7c6-167">A **página Validar** permite que você verifique seu pacote de aplicativos antes de enviar seu aplicativo ao AppSource.</span><span class="sxs-lookup"><span data-stu-id="3a7c6-167">The **Validate** page allows you to check your app package before submitting your app to AppSource.</span></span> <span data-ttu-id="3a7c6-168">Basta carregar o pacote de manifesto e a ferramenta de validação verificará seu aplicativo em relação a todos os casos de teste relacionados ao manifesto.</span><span class="sxs-lookup"><span data-stu-id="3a7c6-168">Simply upload the manifest package and the validation tool will check your app against all manifest related test cases.</span></span> <span data-ttu-id="3a7c6-169">Para cada teste com falha, a descrição fornece um link de documentação para ajudá-lo a corrigir o erro.</span><span class="sxs-lookup"><span data-stu-id="3a7c6-169">For each failed tests, the description provides a documentation link to help you fix the error.</span></span> <span data-ttu-id="3a7c6-170">Para os testes difíceis de  automatizar, a lista de verificação preliminar detalha 7 dos casos de teste com falha mais comuns, bem como o link para uma lista de verificação de envio completa.</span><span class="sxs-lookup"><span data-stu-id="3a7c6-170">For the tests that are hard to automate, the **Preliminary checklist** details 7 of the most common failed test cases as well as link to a complete submission checklist.</span></span>

## <a name="publish-your-app-to-teams"></a><span data-ttu-id="3a7c6-171">Publicar seu aplicativo no Teams</span><span class="sxs-lookup"><span data-stu-id="3a7c6-171">Publish your app to Teams</span></span>

* <span data-ttu-id="3a7c6-172">Na página inicial do seu projeto, você pode carregar seu aplicativo em uma equipe, enviar seu aplicativo para a loja de aplicativos personalizada da empresa para os usuários em sua organização ou enviar seu aplicativo para a Fonte de Aplicativos para todos os usuários do Teams.</span><span class="sxs-lookup"><span data-stu-id="3a7c6-172">On your project home page, you can upload your app to a team, submit your app to your company custom app store for users in your organization, or submit your app to App Source for all Teams users.</span></span>

* <span data-ttu-id="3a7c6-173">Seu administrador de TI revisará esses envios.</span><span class="sxs-lookup"><span data-stu-id="3a7c6-173">Your IT admin will review these submissions.</span></span>

* <span data-ttu-id="3a7c6-174">Você pode retornar à página **Publicar** para verificar o status do envio e saber se seu aplicativo foi aprovado ou rejeitado pelo administrador de TI. Isso também é onde você pode enviar atualizações para seu aplicativo ou cancelar quaisquer envios ativos no momento.</span><span class="sxs-lookup"><span data-stu-id="3a7c6-174">You can return to the **Publish** page to check on your submission status and learn if your app was approved or rejected by your IT admin. This is also where you can submit updates to your app or cancel any currently active submissions.</span></span>

## <a name="next-step"></a><span data-ttu-id="3a7c6-175">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="3a7c6-175">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3a7c6-176">Mantendo e dando suporte ao aplicativo publicado</span><span class="sxs-lookup"><span data-stu-id="3a7c6-176">Maintaining and supporting your published app</span></span>](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
>
