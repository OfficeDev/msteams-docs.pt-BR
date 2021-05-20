---
title: Crie aplicativos com o Microsoft Teams Toolkit e Visual Studio
description: Comece a construir ótimos aplicativos personalizados diretamente dentro de Visual Studio com o Microsoft Teams Toolkit
keywords: equipes estúdio de ferramentas kit de ferramentas
localization_priority: Normal
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: eb94a8de0355283344ebe890a6fa3a3050e243ea
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566548"
---
# <a name="build-apps-with-the-teams-toolkit-and-visual-studio"></a><span data-ttu-id="d7228-104">Crie aplicativos com os Teams Toolkit e Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d7228-104">Build apps with the Teams Toolkit and Visual Studio</span></span>

<span data-ttu-id="d7228-105">O Kit de Ferramentas do Microsoft Teams permite criar aplicativos personalizados do Teams diretamente no ambiente de desenvolvimento integrado (IDE) do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d7228-105">The Microsoft Teams Toolkit enables you to create custom Teams apps directly within the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="d7228-106">O kit de ferramentas do Microsoft Teams guia você através do processo e fornece o necessário para criar, depurar e iniciar seu aplicativo do Teams.</span><span class="sxs-lookup"><span data-stu-id="d7228-106">The Microsoft Teams toolkit guides you through the process and provides everything you need to build, debug, and launch your Teams app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d7228-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="d7228-107">Prerequisites</span></span>

1. <span data-ttu-id="d7228-108">[Habilitar a visualização do desenvolvedor](../resources/dev-preview/developer-preview-intro.md#enable-developer-preview).</span><span class="sxs-lookup"><span data-stu-id="d7228-108">[Enable developer preview](../resources/dev-preview/developer-preview-intro.md#enable-developer-preview).</span></span>

1. <span data-ttu-id="d7228-109">Certifique-se de que o **<span></span>ASP.NE T e o módulo de desenvolvimento web** foram adicionados à sua Visual Studio instância.</span><span class="sxs-lookup"><span data-stu-id="d7228-109">Make sure that the **<span>ASP.NE</span>T and web development module** has been added to your Visual Studio instance.</span></span> <span data-ttu-id="d7228-110">Você pode verificar seguindo as etapas do [Visual Studio modificação adicionando ou removendo cargas de trabalho e](/visualstudio/install/modify-visual-studio?view=vs-2019&preserve-view=true) documentação de componentes.</span><span class="sxs-lookup"><span data-stu-id="d7228-110">You can check by following the steps in the [Modify Visual Studio by adding or removing workloads and component](/visualstudio/install/modify-visual-studio?view=vs-2019&preserve-view=true) documentation.</span></span>

![módulo de asp.net de estúdio visual](../assets/images/visual-studio-web-dev-module.png)

3. <span data-ttu-id="d7228-112">Se você quiser testar seu aplicativo implantando-o a partir de Visual Studio, você precisará ter iIS (Serviços de Informações da Internet) instalado em seu ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="d7228-112">If you would like test your app by deploying it from Visual Studio, you'll need to have IIS (Internet Information Services) installed in your development environment.</span></span> <span data-ttu-id="d7228-113">Visual Studio não inclui iIS e não está incluído na configuração padrão Windows 10, Windows 8 ou Windows 7; no entanto, você pode baixar a versão mais recente do centro de [downloads](https://www.microsoft.com/download/details.aspx?id=48264)da Microsoft .</span><span class="sxs-lookup"><span data-stu-id="d7228-113">Visual Studio does not include IIS and it isn't included in the default Windows 10, Windows 8, or Windows 7 configuration; however, you can download the latest version from the [Microsoft download center](https://www.microsoft.com/download/details.aspx?id=48264).</span></span>

![Visualização de página de download do IIS](../assets/images/iis.png)

## <a name="install-the-teams-toolkit"></a><span data-ttu-id="d7228-115">Instale o Teams Toolkit</span><span class="sxs-lookup"><span data-stu-id="d7228-115">Install the Teams Toolkit</span></span>

<span data-ttu-id="d7228-116">O Microsoft Teams Toolkit para Visual Studio está disponível para download no [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.vsteamstemplate) ou diretamente no menu **Extensões** dentro de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d7228-116">The Microsoft Teams Toolkit for Visual Studio is available for download from the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.vsteamstemplate) or directly from the **Extensions** menu within Visual Studio.</span></span>

## <a name="using-the-toolkit"></a><span data-ttu-id="d7228-117">Usando o kit de ferramentas</span><span class="sxs-lookup"><span data-stu-id="d7228-117">Using the toolkit</span></span>

- [<span data-ttu-id="d7228-118">Criar um novo projeto</span><span class="sxs-lookup"><span data-stu-id="d7228-118">Set up a new project</span></span>](#set-up-a-new-teams-project)
- [<span data-ttu-id="d7228-119">Configure seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="d7228-119">Configure your app</span></span>](#configure-your-app)
- [<span data-ttu-id="d7228-120">Empacote seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="d7228-120">Package your app</span></span>](#package-your-app)
- [<span data-ttu-id="d7228-121">Execute seu aplicativo em Teams</span><span class="sxs-lookup"><span data-stu-id="d7228-121">Run your app in Teams</span></span>](#install-and-run-your-app-locally)
- [<span data-ttu-id="d7228-122">Valide o seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="d7228-122">Validate your app</span></span>](#validate-your-app)
- [<span data-ttu-id="d7228-123">Publicar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="d7228-123">Publish your app</span></span>](#publish-your-app-to-teams)

## <a name="set-up-a-new-teams-project"></a><span data-ttu-id="d7228-124">Criar um novo projeto de Teams</span><span class="sxs-lookup"><span data-stu-id="d7228-124">Set up a new Teams project</span></span>

1. <span data-ttu-id="d7228-125">Selecione **Criar um novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="d7228-125">Select **Create a new project**.</span></span>
1. <span data-ttu-id="d7228-126">Escolha **Microsoft Teams App** e selecione **Next**.</span><span class="sxs-lookup"><span data-stu-id="d7228-126">Choose **Microsoft Teams App** and select **Next**.</span></span>
1. <span data-ttu-id="d7228-127">Você chegará à **tela configurar seu novo projeto** onde você pode escolher o nome **Project,** **Localização** e Nome **da Solução**.</span><span class="sxs-lookup"><span data-stu-id="d7228-127">You will arrive at the **Configure your new project** screen where you can choose the **Project name**, **Location**, and **Solution name**.</span></span>
1. <span data-ttu-id="d7228-128">Verifique a **solução e o projeto place rotulados na** caixa no mesmo diretório .</span><span class="sxs-lookup"><span data-stu-id="d7228-128">Check the box labeled **Place solution and project in the same directory**.</span></span>
1. <span data-ttu-id="d7228-129">Uma janela pop-up rotulada **Adicionar recursos** permitirá que você escolha um ou mais recursos para a configuração do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="d7228-129">A pop-up window labeled **Add Capabilities** will allow you to choose one or more capabilities for your project setup.</span></span>
1. <span data-ttu-id="d7228-130">Selecione o botão **Seguir** para concluir o processo de configuração.</span><span class="sxs-lookup"><span data-stu-id="d7228-130">Select the **Next** button to complete the configuration process.</span></span>
1. <span data-ttu-id="d7228-131">Uma janela pop-up rotulada **Adicionar recursos** permitirá que você escolha as propriedades para cada recurso selecionado.</span><span class="sxs-lookup"><span data-stu-id="d7228-131">A pop-up window labeled **Add Capabilities** will allow you to choose the properties for each selected capability.</span></span>
1. <span data-ttu-id="d7228-132">Selecione **Concluir** e você pousará na **Microsoft Teams Toolkit** página de aterrissagem.</span><span class="sxs-lookup"><span data-stu-id="d7228-132">Select **Finish** and you will  land on the **Microsoft Teams Toolkit** landing page.</span></span>

## <a name="configure-your-app"></a><span data-ttu-id="d7228-133">Configure seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="d7228-133">Configure your app</span></span>

<span data-ttu-id="d7228-134">Em sua essência, o aplicativo Teams abraça três componentes:</span><span class="sxs-lookup"><span data-stu-id="d7228-134">At its core, the Teams app embraces three components:</span></span>

  1. <span data-ttu-id="d7228-135">O Microsoft Teams cliente (web, desktop ou celular) onde os usuários interagem com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d7228-135">The Microsoft Teams client (web, desktop or mobile) where users interact with your app.</span></span>
  1. <span data-ttu-id="d7228-136">Um servidor que responde a solicitações de conteúdo que será exibido em Teams, por exemplo, conteúdo de guia HTML ou um cartão adaptativo de bot .</span><span class="sxs-lookup"><span data-stu-id="d7228-136">A server that responds to requests for content that will be displayed in Teams, e.g., HTML tab content or a bot adaptive card .</span></span>
  1. <span data-ttu-id="d7228-137">Um pacote de aplicativos Teams consiste em três arquivos:</span><span class="sxs-lookup"><span data-stu-id="d7228-137">A Teams app package consists of three files:</span></span>

      > [!div class="checklist"]
      >
      > - <span data-ttu-id="d7228-138">O manifest.js</span><span class="sxs-lookup"><span data-stu-id="d7228-138">The manifest.json</span></span>
      > - <span data-ttu-id="d7228-139">Um [ícone de cores](../resources/schema/manifest-schema.md#icons) para seu aplicativo ser exibido no catálogo de aplicativos públicos ou de organização</span><span class="sxs-lookup"><span data-stu-id="d7228-139">A [color icon](../resources/schema/manifest-schema.md#icons) for your app to display in the public or organization app catalog</span></span>
      > - <span data-ttu-id="d7228-140">Um [ícone de contorno](../resources/schema/manifest-schema.md#icons) para exibição na barra de atividades Teams.</span><span class="sxs-lookup"><span data-stu-id="d7228-140">An [outline icon](../resources/schema/manifest-schema.md#icons) for display on the Teams activity bar.</span></span>

<span data-ttu-id="d7228-141">Quando um aplicativo é instalado, o cliente Teams analisa o arquivo manifesto para determinar informações necessárias, como o nome do seu aplicativo e a URL onde os serviços estão localizados.</span><span class="sxs-lookup"><span data-stu-id="d7228-141">When an app is installed, the Teams client parses the manifest file to determine needed information like the name of your app and the URL where the services are located.</span></span>

> [!NOTE]
><span data-ttu-id="d7228-142">Se você ainda não fez isso, você precisará fazer login em sua Microsoft 365 ou conta para continuar com o processo de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="d7228-142">If you haven't done so already, you will need to sign in to your Microsoft 365  or account to continue with the development process.</span></span>
>
> <span data-ttu-id="d7228-143">Se você não tiver uma conta Microsoft 365, você pode se inscrever para uma assinatura [do Programa de Desenvolvedores Microsoft 365.](https://developer.microsoft.com/microsoft-365/dev-program)</span><span class="sxs-lookup"><span data-stu-id="d7228-143">If you don't have a Microsoft 365 account, you can sign up for a [Microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program) subscription.</span></span> <span data-ttu-id="d7228-144">É *gratuito* por 90 dias e se renovará continuamente enquanto estiver usando-o para atividades de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="d7228-144">It's *free* for 90 days and will continually renew as long as you're using it for development activity.</span></span> <span data-ttu-id="d7228-145">Se você tem uma assinatura *Visual Studio Enterprise* ou *Professional,* ambos os programas incluem uma assinatura gratuita Microsoft 365 [desenvolvedor,](https://aka.ms/MyVisualStudioBenefits)ativa para a vida útil de sua assinatura Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d7228-145">If you have a Visual Studio *Enterprise* or *Professional* subscription, both programs include a free Microsoft 365 [developer subscription](https://aka.ms/MyVisualStudioBenefits), active for the life of your Visual Studio subscription.</span></span> <span data-ttu-id="d7228-146">Para obter mais informações, consulte [Configurar uma assinatura de desenvolvedor Microsoft 365](/office/developer-program/office-365-developer-program-get-started).</span><span class="sxs-lookup"><span data-stu-id="d7228-146">For more information, See [Set up a Microsoft 365 developer subscription](/office/developer-program/office-365-developer-program-get-started).</span></span>
>

### <a name="configuration-steps"></a><span data-ttu-id="d7228-147">Etapas de configuração</span><span class="sxs-lookup"><span data-stu-id="d7228-147">Configuration steps</span></span>

1. <span data-ttu-id="d7228-148">Para configurar seu aplicativo, na **Microsoft Teams Toolkit** página de destino, selecione **Editar pacote de aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="d7228-148">To configure your app, on the **Microsoft Teams Toolkit** landing page, select **Edit app package**.</span></span>
1. <span data-ttu-id="d7228-149">No menu suspenso **Do My Environments,** selecione **o desenvolvimento**.</span><span class="sxs-lookup"><span data-stu-id="d7228-149">From the **My Environments** drop-down menu, select **development**.</span></span>
1. <span data-ttu-id="d7228-150">Você vai pousar na página **de detalhes** do Aplicativo onde você pode editar os campos de propriedade do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d7228-150">You will land on the **App details** page where you can edit your app's property fields.</span></span>
1. <span data-ttu-id="d7228-151">A edição dos campos na página de detalhes do App atualiza o conteúdo do manifest.jsno arquivo que, em última análise, será enviado como parte do pacote do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d7228-151">Editing the fields in the App details page updates the contents of the manifest.json file that will ultimately ship as part of the app package.</span></span> [<span data-ttu-id="d7228-152">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="d7228-152">Learn more</span></span>](https://aka.ms/teams-toolkit-manifest)

## <a name="package-your-app"></a><span data-ttu-id="d7228-153">Empacote seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="d7228-153">Package your app</span></span>

<span data-ttu-id="d7228-154">Modificar a página de **detalhes** do aplicativo ou atualizar os arquivos **manifesto** ou **.env** na pasta **.publish** do seu aplicativo gerará automaticamente o **seu arquivoDevelopment.zip.**</span><span class="sxs-lookup"><span data-stu-id="d7228-154">Modifying the **app details** page or updating the **manifest**, or **.env** files in your app's  **.publish** folder will automatically generate your **Development.zip** file.</span></span> <span data-ttu-id="d7228-155">O arquivo Development.zip inclui três arquivos necessários — o **manifest.jse** [dois ícones](../concepts/build-and-test/apps-package.md#app-icons).</span><span class="sxs-lookup"><span data-stu-id="d7228-155">The Development.zip file includes three required files — the **manifest.json** and [two icons](../concepts/build-and-test/apps-package.md#app-icons).</span></span>

## <a name="install-and-run-your-app-locally"></a><span data-ttu-id="d7228-156">Instale e execute seu aplicativo localmente</span><span class="sxs-lookup"><span data-stu-id="d7228-156">Install and run your app locally</span></span>

1. <span data-ttu-id="d7228-157">No menu suspenso configurações de configurações de **solução,** selecione **Implantar** como mostrado na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="d7228-157">From the **Solution Configurations** dropdown menu, select **Deploy** as shown in the following image:</span></span>

    ![Menu de configurações de soluções](../assets/images/solution-configurations.png)

2. <span data-ttu-id="d7228-159">Selecione o botão **IIS Express + Teams.**</span><span class="sxs-lookup"><span data-stu-id="d7228-159">Select the **IIS Express + Teams** button.</span></span>

1. <span data-ttu-id="d7228-160">Teams será lançado e o diálogo de instalação do aplicativo deve aparecer no Teams cliente.</span><span class="sxs-lookup"><span data-stu-id="d7228-160">Teams will launch and the app installation dialogue should appear in the Teams client.</span></span>

## <a name="validate-your-app"></a><span data-ttu-id="d7228-161">Valide o seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="d7228-161">Validate your app</span></span>

<span data-ttu-id="d7228-162">A página **Validar** permite que você verifique seu pacote de aplicativos antes de enviar seu aplicativo para o AppSource.</span><span class="sxs-lookup"><span data-stu-id="d7228-162">The **Validate** page allows you to check your app package before submitting your app to AppSource.</span></span> <span data-ttu-id="d7228-163">Basta carregar o pacote manifesto e a ferramenta de validação verificará seu aplicativo em todos os casos de teste relacionados ao manifesto.</span><span class="sxs-lookup"><span data-stu-id="d7228-163">Simply upload the manifest package and the validation tool will check your app against all manifest related test cases.</span></span> <span data-ttu-id="d7228-164">Para cada teste com falha, a descrição fornece um link de documentação para ajudá-lo a corrigir o erro.</span><span class="sxs-lookup"><span data-stu-id="d7228-164">For each failed tests, the description provides a documentation link to help you fix the error.</span></span> <span data-ttu-id="d7228-165">Para os testes difíceis de automatizar, a **lista preliminar** detalha 7 dos casos de teste com falha mais comuns, bem como vincula a uma lista completa de verificação de submissão.</span><span class="sxs-lookup"><span data-stu-id="d7228-165">For the tests that are hard to automate, the **Preliminary checklist** details 7 of the most common failed test cases as well as link to a complete submission checklist.</span></span>

## <a name="publish-your-app-to-teams"></a><span data-ttu-id="d7228-166">Publicar seu aplicativo no Teams</span><span class="sxs-lookup"><span data-stu-id="d7228-166">Publish your app to Teams</span></span>

<span data-ttu-id="d7228-167">✔ Na página inicial do seu projeto, você pode carregar seu aplicativo para uma equipe, enviar seu aplicativo para a loja de aplicativos personalizada da sua empresa para usuários em sua organização ou enviar seu aplicativo para a App Source para todos os usuários Teams.</span><span class="sxs-lookup"><span data-stu-id="d7228-167">✔ On your project home page, you can upload your app to a team, submit your app to your company custom app store for users in your organization, or submit your app to App Source for all Teams users.</span></span>

<span data-ttu-id="d7228-168">✔ Seu administrador de TI revisará essas submissões.</span><span class="sxs-lookup"><span data-stu-id="d7228-168">✔ Your IT admin will review these submissions.</span></span>

<span data-ttu-id="d7228-169">✔ Você pode retornar à página **Publicar** para verificar seu status de envio e saber se seu aplicativo foi aprovado ou rejeitado pelo administrador de TI. É também aqui que você virá enviar atualizações para o seu aplicativo ou cancelar quaisquer submissões atualmente ativas.</span><span class="sxs-lookup"><span data-stu-id="d7228-169">✔  You can return to the **Publish** page to check on your submission status and learn if your app was approved or rejected by your IT admin. This is also where you'll come to submit updates to your app or cancel any currently active submissions.</span></span>

## <a name="next-step"></a><span data-ttu-id="d7228-170">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="d7228-170">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d7228-171">Mantendo e apoiando seu aplicativo publicado</span><span class="sxs-lookup"><span data-stu-id="d7228-171">Maintaining and supporting your published app</span></span>](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
>
