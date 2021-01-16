---
title: Criar aplicativos com o Kit de Ferramentas do Microsoft Teams e o Visual Studio
description: Começar a criar ótimos aplicativos personalizados diretamente no Visual Studio com o Kit de Ferramentas do Microsoft Teams
keywords: kit de ferramentas do visual studio do teams
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: 08df1d3907a1a3683eb42222e247cd7fd6c0177b
ms.sourcegitcommit: 5e1300d6f4f2ea23beb3cdbbf4bd46999eef4e87
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/15/2021
ms.locfileid: "49875004"
---
# <a name="build-apps-with-the-teams-toolkit-and-visual-studio"></a><span data-ttu-id="f977b-104">Criar aplicativos com o Kit de Ferramentas do Teams e o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f977b-104">Build apps with the Teams Toolkit and Visual Studio</span></span>

<span data-ttu-id="f977b-105">O Kit de Ferramentas do Microsoft Teams permite que você crie aplicativos personalizados do Teams diretamente no IDE (ambiente de desenvolvimento integrado) do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f977b-105">The Microsoft Teams Toolkit enables you to create custom Teams apps directly within the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="f977b-106">O kit de ferramentas do Microsoft Teams orienta você durante o processo e fornece tudo o que você precisa para criar, depurar e iniciar seu aplicativo do Teams.</span><span class="sxs-lookup"><span data-stu-id="f977b-106">The Microsoft Teams toolkit guides you through the process and provides everything you need to build, debug, and launch your Teams app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f977b-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="f977b-107">Prerequisites</span></span>

1. [<span data-ttu-id="f977b-108">Habilitar a visualização do desenvolvedor</span><span class="sxs-lookup"><span data-stu-id="f977b-108">Enable developer preview</span></span>](../resources/dev-preview/developer-preview-intro.md#enable-developer-preview)

1. <span data-ttu-id="f977b-109">Certifique-se de que **<span>o ASP.NE</span>T e o** módulo de desenvolvimento da Web foram adicionados à sua instância do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f977b-109">Make sure that the **<span>ASP.NE</span>T and web development module** has been added to your Visual Studio instance.</span></span> <span data-ttu-id="f977b-110">Você pode verificar seguindo as etapas no Modify Visual Studio adicionando [ou removendo cargas de](/visualstudio/install/modify-visual-studio?view=vs-2019&preserve-view=true) trabalho e documentação de componentes.</span><span class="sxs-lookup"><span data-stu-id="f977b-110">You can check by following the steps in the [Modify Visual Studio by adding or removing workloads and component](/visualstudio/install/modify-visual-studio?view=vs-2019&preserve-view=true) documentation.</span></span>

![módulo de asp.net visual studio](../assets/images/visual-studio-web-dev-module.png)

3. <span data-ttu-id="f977b-112">Se você quiser testar seu aplicativo implantando-o no Visual Studio, precisará ter o IIS (Serviços de Informações da Internet) instalado em seu ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="f977b-112">If you would like test your app by deploying it from Visual Studio, you'll need to have IIS (Internet Information Services) installed in your development environment.</span></span> <span data-ttu-id="f977b-113">O Visual Studio não inclui o IIS e não está incluído na configuração padrão do Windows 10, do Windows 8 ou do Windows 7; No entanto, você pode baixar a versão mais recente do centro [de download da Microsoft.](https://www.microsoft.com/download/details.aspx?id=48264)</span><span class="sxs-lookup"><span data-stu-id="f977b-113">Visual Studio does not include IIS and it isn't included in the default Windows 10, Windows 8, or Windows 7 configuration; however, you can download the latest version from the [Microsoft download center](https://www.microsoft.com/download/details.aspx?id=48264).</span></span>

![Exibição da página de download do IIS](../assets/images/iis.png)

## <a name="install-the-teams-toolkit"></a><span data-ttu-id="f977b-115">Instalar o Kit de Ferramentas do Teams</span><span class="sxs-lookup"><span data-stu-id="f977b-115">Install the Teams Toolkit</span></span>

<span data-ttu-id="f977b-116">O Microsoft Teams Toolkit para Visual Studio está disponível para download no [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.vsteamstemplate) ou diretamente no menu Extensões no Visual Studio. </span><span class="sxs-lookup"><span data-stu-id="f977b-116">The Microsoft Teams Toolkit for Visual Studio is available for download from the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.vsteamstemplate) or directly from the **Extensions** menu within Visual Studio.</span></span>

## <a name="using-the-toolkit"></a><span data-ttu-id="f977b-117">Usando o kit de ferramentas</span><span class="sxs-lookup"><span data-stu-id="f977b-117">Using the toolkit</span></span>

- [<span data-ttu-id="f977b-118">Configurar um novo projeto</span><span class="sxs-lookup"><span data-stu-id="f977b-118">Set up a new project</span></span>](#set-up-a-new-teams-project)
- [<span data-ttu-id="f977b-119">Configurar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="f977b-119">Configure your app</span></span>](#configure-your-app)
- [<span data-ttu-id="f977b-120">Empacote seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="f977b-120">Package your app</span></span>](#package-your-app)
- [<span data-ttu-id="f977b-121">Executar seu aplicativo no Teams</span><span class="sxs-lookup"><span data-stu-id="f977b-121">Run your app in Teams</span></span>](#install-and-run-your-app-locally)
- [<span data-ttu-id="f977b-122">Valide o seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="f977b-122">Validate your app</span></span>](#validate-your-app)
- [<span data-ttu-id="f977b-123">Publicar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="f977b-123">Publish your app</span></span>](#publish-your-app-to-teams)

## <a name="set-up-a-new-teams-project"></a><span data-ttu-id="f977b-124">Configurar um novo projeto do Teams</span><span class="sxs-lookup"><span data-stu-id="f977b-124">Set up a new Teams project</span></span>

1. <span data-ttu-id="f977b-125">Selecione **Criar um novo projeto.**</span><span class="sxs-lookup"><span data-stu-id="f977b-125">Select **Create a new project**.</span></span>
1. <span data-ttu-id="f977b-126">Escolha **o aplicativo Microsoft Teams e** selecione **Próximo.**</span><span class="sxs-lookup"><span data-stu-id="f977b-126">Choose **Microsoft Teams App** and select **Next**.</span></span>
1. <span data-ttu-id="f977b-127">Você chegará na tela **Configurar seu novo projeto,** onde poderá escolher o **nome** do **projeto,** o local e o nome **da solução.**</span><span class="sxs-lookup"><span data-stu-id="f977b-127">You will arrive at the **Configure your new project** screen where you can choose the **Project name**, **Location**, and **Solution name**.</span></span>
1. <span data-ttu-id="f977b-128">Marque a caixa rotulada **Colocar solução e projeto no mesmo diretório.**</span><span class="sxs-lookup"><span data-stu-id="f977b-128">Check the box labeled **Place solution and project in the same directory**.</span></span>
1. <span data-ttu-id="f977b-129">Uma janela pop-up rotulada adicionar **recursos** permitirá que você escolha um ou mais recursos para a configuração do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="f977b-129">A pop-up window labeled **Add Capabilities** will allow you to choose one or more capabilities for your project setup.</span></span>
1. <span data-ttu-id="f977b-130">Selecione o **botão Próximo** para concluir o processo de configuração.</span><span class="sxs-lookup"><span data-stu-id="f977b-130">Select the **Next** button to complete the configuration process.</span></span>
1. <span data-ttu-id="f977b-131">Uma janela pop-up rotulada adicionar **recursos** permitirá que você escolha as propriedades para cada recurso selecionado.</span><span class="sxs-lookup"><span data-stu-id="f977b-131">A pop-up window labeled **Add Capabilities** will allow you to choose the properties for each selected capability.</span></span>
1. <span data-ttu-id="f977b-132">Selecione **Concluir** e você chegará à página inicial do **Microsoft Teams Toolkit.**</span><span class="sxs-lookup"><span data-stu-id="f977b-132">Select **Finish** and you will  land on the **Microsoft Teams Toolkit** landing page.</span></span>

## <a name="configure-your-app"></a><span data-ttu-id="f977b-133">Configurar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="f977b-133">Configure your app</span></span>

<span data-ttu-id="f977b-134">Em seu núcleo, o aplicativo Teams adota três componentes:</span><span class="sxs-lookup"><span data-stu-id="f977b-134">At its core, the Teams app embraces three components:</span></span>

  1. <span data-ttu-id="f977b-135">O cliente do Microsoft Teams (web, desktop ou dispositivos móveis) em que os usuários interagem com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f977b-135">The Microsoft Teams client (web, desktop or mobile) where users interact with your app.</span></span>
  1. <span data-ttu-id="f977b-136">Um servidor que responde a solicitações de conteúdo que será exibido no Teams, por exemplo, conteúdo de guia HTML ou um cartão adaptável de bot.</span><span class="sxs-lookup"><span data-stu-id="f977b-136">A server that responds to requests for content that will be displayed in Teams, e.g., HTML tab content or a bot adaptive card .</span></span>
  1. <span data-ttu-id="f977b-137">Um pacote [de aplicativos do](/concepts/build-and-test/apps-package.md) Teams que consiste em três arquivos:</span><span class="sxs-lookup"><span data-stu-id="f977b-137">A Teams [app package](/concepts/build-and-test/apps-package.md) consisting of three files:</span></span>

  > [!div class="checklist"]
  >
  > - <span data-ttu-id="f977b-138">O manifest.jsem</span><span class="sxs-lookup"><span data-stu-id="f977b-138">The manifest.json</span></span>
  > - <span data-ttu-id="f977b-139">Um [ícone de cor](../resources/schema/manifest-schema.md#icons) para seu aplicativo ser exibido no catálogo de aplicativos público ou da organização</span><span class="sxs-lookup"><span data-stu-id="f977b-139">A [color icon](../resources/schema/manifest-schema.md#icons) for your app to display in the public or organization app catalog</span></span>
 > - <span data-ttu-id="f977b-140">Um [ícone de contorno](../resources/schema/manifest-schema.md#icons) para exibição na barra de atividades do Teams.</span><span class="sxs-lookup"><span data-stu-id="f977b-140">An [outline icon](../resources/schema/manifest-schema.md#icons) for display on the Teams activity bar.</span></span>

<span data-ttu-id="f977b-141">Quando um aplicativo é instalado, o cliente do Teams analisará o arquivo de manifesto para determinar as informações necessárias, como o nome do seu aplicativo e a URL onde os serviços estão localizados.</span><span class="sxs-lookup"><span data-stu-id="f977b-141">When an app is installed, the Teams client parses the manifest file to determine needed information like the name of your app and the URL where the services are located.</span></span>

> [!NOTE]
><span data-ttu-id="f977b-142">Se ainda não tiver feito isso, você precisará entrar no Microsoft 365 ou conta para continuar com o processo de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="f977b-142">If you haven't done so already, you will need to sign in to your Microsoft 365  or account to continue with the development process.</span></span>
>
> <span data-ttu-id="f977b-143">Se você não tiver uma conta do Microsoft 365, inscreva-se para uma assinatura do Programa para Desenvolvedores do [Microsoft 365.](https://developer.microsoft.com/microsoft-365/dev-program)</span><span class="sxs-lookup"><span data-stu-id="f977b-143">If you don't have a Microsoft 365 account, you can sign up for a [Microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program) subscription.</span></span> <span data-ttu-id="f977b-144">Ele é *gratuito por* 90 dias e será renovado continuamente, desde que você o esteja usando para atividades de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="f977b-144">It's *free* for 90 days and will continually renew as long as you're using it for development activity.</span></span> <span data-ttu-id="f977b-145">Se você tiver uma assinatura do Visual Studio *Enterprise* ou *Professional,* ambos os programas incluirão uma assinatura gratuita de desenvolvedor do Microsoft 365, ativa durante a vida de sua assinatura do Visual Studio. [](https://aka.ms/MyVisualStudioBenefits)</span><span class="sxs-lookup"><span data-stu-id="f977b-145">If you have a Visual Studio *Enterprise* or *Professional* subscription, both programs include a free Microsoft 365 [developer subscription](https://aka.ms/MyVisualStudioBenefits), active for the life of your Visual Studio subscription.</span></span> <span data-ttu-id="f977b-146">*Confira* [Configurar uma assinatura de desenvolvedor do Microsoft 365.](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started)</span><span class="sxs-lookup"><span data-stu-id="f977b-146">*See* [Set up a Microsoft 365 developer subscription](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started).</span></span>
>

### <a name="configuration-steps"></a><span data-ttu-id="f977b-147">Etapas de configuração</span><span class="sxs-lookup"><span data-stu-id="f977b-147">Configuration steps</span></span>

1. <span data-ttu-id="f977b-148">Para configurar seu aplicativo, na página inicial do Kit de Ferramentas do **Microsoft Teams,** selecione **Editar pacote do aplicativo.**</span><span class="sxs-lookup"><span data-stu-id="f977b-148">To configure your app, on the **Microsoft Teams Toolkit** landing page, select **Edit app package** .</span></span>
1. <span data-ttu-id="f977b-149">No menu **suspenso Meus Ambientes,** selecione **desenvolvimento.**</span><span class="sxs-lookup"><span data-stu-id="f977b-149">From the **My Environments** drop-down menu, select **development**.</span></span>
1. <span data-ttu-id="f977b-150">Você chegará à página **de detalhes do** aplicativo onde poderá editar os campos de propriedades do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f977b-150">You will land on the **App details** page where you can edit your app's property fields.</span></span>
1. <span data-ttu-id="f977b-151">A edição dos campos na página de detalhes do aplicativo atualiza o conteúdo do arquivo manifest.jsno arquivo que, por fim, será oferecido como parte do pacote do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f977b-151">Editing the fields in the App details page updates the contents of the manifest.json file that will ultimately ship as part of the app package.</span></span> [<span data-ttu-id="f977b-152">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="f977b-152">Learn more</span></span>](https://aka.ms/teams-toolkit-manifest)

## <a name="package-your-app"></a><span data-ttu-id="f977b-153">Empacote seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="f977b-153">Package your app</span></span>

<span data-ttu-id="f977b-154">Modificar a página **de detalhes** do aplicativo ou atualizar o manifesto ou **arquivos .env** na pasta **.publish** do aplicativo gerará automaticamente o arquivo **Development.zip** arquivo.</span><span class="sxs-lookup"><span data-stu-id="f977b-154">Modifying the **app details** page or updating the **manifest**, or **.env** files in your app's  **.publish** folder will automatically generate your **Development.zip** file.</span></span> <span data-ttu-id="f977b-155">O Development.zip arquivo inclui três arquivos obrigatórios — a **manifest.jse** [dois ícones](../concepts/build-and-test/apps-package.md#app-icons).</span><span class="sxs-lookup"><span data-stu-id="f977b-155">The Development.zip file includes three required files — the **manifest.json** and [two icons](../concepts/build-and-test/apps-package.md#app-icons).</span></span>

## <a name="install-and-run-your-app-locally"></a><span data-ttu-id="f977b-156">Instalar e executar seu aplicativo localmente</span><span class="sxs-lookup"><span data-stu-id="f977b-156">Install and run your app locally</span></span>

1. <span data-ttu-id="f977b-157">No menu **suspenso Configurações** da Solução, selecione **Implantar.**</span><span class="sxs-lookup"><span data-stu-id="f977b-157">From the **Solution Configurations** dropdown menu, select **Deploy**.</span></span>

![Menu Configurações da solução](../assets/images/solution-configurations.png)

2. <span data-ttu-id="f977b-159">Selecione o **botão IIS Express + Teams.**</span><span class="sxs-lookup"><span data-stu-id="f977b-159">Select the **IIS Express + Teams** button.</span></span>

1. <span data-ttu-id="f977b-160">O Teams será lançado e a caixa de diálogo de instalação do aplicativo deverá aparecer no cliente do Teams.</span><span class="sxs-lookup"><span data-stu-id="f977b-160">Teams will launch and the app installation dialogue should appear in the Teams client.</span></span>

## <a name="validate-your-app"></a><span data-ttu-id="f977b-161">Valide o seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="f977b-161">Validate your app</span></span>

<span data-ttu-id="f977b-162">A **página Validar** permite que você verifique o pacote do aplicativo antes de enviar seu aplicativo ao AppSource.</span><span class="sxs-lookup"><span data-stu-id="f977b-162">The **Validate** page allows you to check your app package before submitting your app to AppSource.</span></span> <span data-ttu-id="f977b-163">Basta carregar o pacote de manifesto e a ferramenta de validação verificará seu aplicativo em relação a todos os casos de teste relacionados ao manifesto.</span><span class="sxs-lookup"><span data-stu-id="f977b-163">Simply upload the manifest package and the validation tool will check your app against all manifest related test cases.</span></span> <span data-ttu-id="f977b-164">Para cada teste com falha, a descrição fornece um link de documentação para ajudá-lo a corrigir o erro.</span><span class="sxs-lookup"><span data-stu-id="f977b-164">For each failed tests, the description provides a documentation link to help you fix the error.</span></span> <span data-ttu-id="f977b-165">Para os testes difíceis de  automatizar, a lista de verificação preliminar detalha 7 dos casos de teste com falha mais comuns, bem como o link para uma lista de verificação de envio completa.</span><span class="sxs-lookup"><span data-stu-id="f977b-165">For the tests that are hard to automate, the **Preliminary checklist** details 7 of the most common failed test cases as well as link to a complete submission checklist.</span></span>

## <a name="publish-your-app-to-teams"></a><span data-ttu-id="f977b-166">Publicar seu aplicativo no Teams</span><span class="sxs-lookup"><span data-stu-id="f977b-166">Publish your app to Teams</span></span>

<span data-ttu-id="f977b-167">✔ Na home page do seu projeto, você pode carregar seu aplicativo para uma equipe, enviar seu aplicativo para a loja de aplicativos personalizada da empresa para usuários em sua organização ou enviar seu aplicativo para a Fonte de Aplicativos para todos os usuários do Teams.</span><span class="sxs-lookup"><span data-stu-id="f977b-167">✔ On your project home page, you can upload your app to a team, submit your app to your company custom app store for users in your organization, or submit your app to App Source for all Teams users.</span></span>

<span data-ttu-id="f977b-168">✔ seu administrador de IT revisará esses envios.</span><span class="sxs-lookup"><span data-stu-id="f977b-168">✔ Your IT admin will review these submissions.</span></span>

<span data-ttu-id="f977b-169">✔ Você pode retornar à  página Publicar para verificar o status do envio e saber se o aplicativo foi aprovado ou rejeitado pelo administrador de TI. Também é aqui que você enviará atualizações para seu aplicativo ou cancelará quaisquer envios ativos no momento.</span><span class="sxs-lookup"><span data-stu-id="f977b-169">✔  You can return to the **Publish** page to check on your submission status and learn if your app was approved or rejected by your IT admin. This is also where you'll come to submit updates to your app or cancel any currently active submissions.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f977b-170">Próxima etapa: manter e dar suporte ao seu aplicativo publicado</span><span class="sxs-lookup"><span data-stu-id="f977b-170">Next step: Maintaining and supporting your published app</span></span>](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
>
