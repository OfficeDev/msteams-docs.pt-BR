---
title: Criar aplicativos com o Microsoft Teams Toolkit e o Visual Studio
description: Introdução ao desenvolvimento de aplicativos personalizados de grande parte diretamente no Visual Studio com o Microsoft Teams Toolkit
keywords: Kit de ferramentas do Visual Studio Teams
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: 5ba3cd8b5714876a96595aec295ff6d0066e115f
ms.sourcegitcommit: 7e47bf158249050c36d97509eea00e77089a54e6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "49476983"
---
# <a name="build-apps-with-the-teams-toolkit-and-visual-studio"></a><span data-ttu-id="9d25b-104">Criar aplicativos com o Teams Toolkit e o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9d25b-104">Build apps with the Teams Toolkit and Visual Studio</span></span>

<span data-ttu-id="9d25b-105">O Microsoft Teams Toolkit permite que você crie aplicativos personalizados do teams diretamente no IDE (ambiente de desenvolvimento integrado) do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9d25b-105">The Microsoft Teams Toolkit enables you to create custom Teams apps directly within the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="9d25b-106">O Microsoft Teams Toolkit orienta você durante o processo e oferece tudo o que você precisa para criar, depurar e iniciar o aplicativo Teams.</span><span class="sxs-lookup"><span data-stu-id="9d25b-106">The Microsoft Teams toolkit guides you through the process and provides everything you need to build, debug, and launch your Teams app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9d25b-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="9d25b-107">Prerequisites</span></span>

1. [<span data-ttu-id="9d25b-108">Habilitar visualização do desenvolvedor</span><span class="sxs-lookup"><span data-stu-id="9d25b-108">Enable developer preview</span></span>](../resources/dev-preview/developer-preview-intro.md#enable-developer-preview)

1. <span data-ttu-id="9d25b-109">Certifique-se de que o **<span>ASP.ne</span>T e o módulo de desenvolvimento da Web** foram adicionados à sua instância do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9d25b-109">Make sure that the **<span>ASP.NE</span>T and web development module** has been added to your Visual Studio instance.</span></span> <span data-ttu-id="9d25b-110">Você pode verificar seguindo as etapas descritas em [Modificar o Visual Studio adicionando ou removendo cargas de trabalho e](/visualstudio/install/modify-visual-studio?view=vs-2019&preserve-view=true) documentação de componente.</span><span class="sxs-lookup"><span data-stu-id="9d25b-110">You can check by following the steps in the [Modify Visual Studio by adding or removing workloads and component](/visualstudio/install/modify-visual-studio?view=vs-2019&preserve-view=true) documentation.</span></span>

![módulo asp.net do Visual Studio](../assets/images/visual-studio-web-dev-module.png)

3. <span data-ttu-id="9d25b-112">Se quiser testar seu aplicativo implantando-o a partir do Visual Studio, você precisará ter o IIS (serviços de informações da Internet) instalado em seu ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="9d25b-112">If you would like test your app by deploy it from Visual Studio, you'll need to have IIS (Internet Information Services) installed in your development environment.</span></span> <span data-ttu-id="9d25b-113">O Visual Studio não inclui o IIS e ele não está incluído na configuração padrão do Windows 10, Windows 8 ou Windows 7; no entanto, você pode baixar a versão mais recente no [centro de download da Microsoft](https://www.microsoft.com/download/details.aspx?id=48264).</span><span class="sxs-lookup"><span data-stu-id="9d25b-113">Visual Studio does not include IIS and it isn't included in the default Windows 10, Windows 8, or Windows 7 configuration; however, you can download the latest version from the [Microsoft download center](https://www.microsoft.com/download/details.aspx?id=48264).</span></span>

![Exibição da página de download do IIS](../assets/images/iis.png)

## <a name="install-the-teams-toolkit"></a><span data-ttu-id="9d25b-115">Instalar o kit de ferramentas do teams</span><span class="sxs-lookup"><span data-stu-id="9d25b-115">Install the Teams Toolkit</span></span>

<span data-ttu-id="9d25b-116">O Microsoft Teams Toolkit para Visual Studio está disponível para download no [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.vsteamstemplate) ou diretamente a partir do menu **Extensions** no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9d25b-116">The Microsoft Teams Toolkit for Visual Studio is available for download from the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.vsteamstemplate) or directly from the **Extensions** menu within Visual Studio.</span></span>

## <a name="using-the-toolkit"></a><span data-ttu-id="9d25b-117">Usando o kit de ferramentas</span><span class="sxs-lookup"><span data-stu-id="9d25b-117">Using the toolkit</span></span>

- [<span data-ttu-id="9d25b-118">Configurar um novo projeto</span><span class="sxs-lookup"><span data-stu-id="9d25b-118">Set up a new project</span></span>](#set-up-a-new-teams-project)
- [<span data-ttu-id="9d25b-119">Configurar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="9d25b-119">Configure your app</span></span>](#configure-your-app)
- [<span data-ttu-id="9d25b-120">Empacotar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="9d25b-120">Package your app</span></span>](#package-your-app)
- [<span data-ttu-id="9d25b-121">Executar o aplicativo no Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="9d25b-121">Run your app in Teams</span></span>](#install-and-run-your-app-locally)
- [<span data-ttu-id="9d25b-122">Validar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="9d25b-122">Validate your app</span></span>](#validate-your-app)
- [<span data-ttu-id="9d25b-123">Publicar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="9d25b-123">Publish your app</span></span>](#publish-your-app-to-teams)

## <a name="set-up-a-new-teams-project"></a><span data-ttu-id="9d25b-124">Configurar um novo projeto do teams</span><span class="sxs-lookup"><span data-stu-id="9d25b-124">Set up a new Teams project</span></span>

1. <span data-ttu-id="9d25b-125">Selecione **criar um novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="9d25b-125">Select **Create a new project**.</span></span>
1. <span data-ttu-id="9d25b-126">Escolha **aplicativo Microsoft Teams** e selecione **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="9d25b-126">Choose **Microsoft Teams App** and select **Next**.</span></span>
1. <span data-ttu-id="9d25b-127">Você chegará à tela **configurar seu novo projeto** , onde você pode escolher o **nome do projeto**, o **local** e o **nome da solução**.</span><span class="sxs-lookup"><span data-stu-id="9d25b-127">You will arrive at the **Configure your new project** screen where you can choose the **Project name**, **Location**, and **Solution name**.</span></span>
1. <span data-ttu-id="9d25b-128">Marque a caixa rotulada **Colocar solução e projeto no mesmo diretório**.</span><span class="sxs-lookup"><span data-stu-id="9d25b-128">Check the box labeled **Place solution and project in the same directory**.</span></span>
1. <span data-ttu-id="9d25b-129">Uma janela pop-up com o rótulo **Adicionar recursos** permitirá que você escolha um ou mais recursos para a configuração do projeto.</span><span class="sxs-lookup"><span data-stu-id="9d25b-129">A pop-up window labeled **Add Capabilities** will allow you to choose one or more capabilities for your project setup.</span></span>
1. <span data-ttu-id="9d25b-130">Selecione o botão **Avançar** para concluir o processo de configuração.</span><span class="sxs-lookup"><span data-stu-id="9d25b-130">Select the **Next** button to complete the configuration process.</span></span>
1. <span data-ttu-id="9d25b-131">Uma janela pop-up com o rótulo **Adicionar recursos** permitirá que você escolha as propriedades para cada recurso selecionado.</span><span class="sxs-lookup"><span data-stu-id="9d25b-131">A pop-up window labeled **Add Capabilities** will allow you to choose the properties for each selected capability.</span></span>
1. <span data-ttu-id="9d25b-132">Selecione **concluir** e você irá parar na página inicial do **Microsoft Teams Toolkit** .</span><span class="sxs-lookup"><span data-stu-id="9d25b-132">Select **Finish** and you will  land on the **Microsoft Teams Toolkit** landing page.</span></span>

## <a name="configure-your-app"></a><span data-ttu-id="9d25b-133">Configurar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="9d25b-133">Configure your app</span></span>

<span data-ttu-id="9d25b-134">Em seu núcleo, o aplicativo Teams engloba três componentes:</span><span class="sxs-lookup"><span data-stu-id="9d25b-134">At its core, the Teams app embraces three components:</span></span>

  1. <span data-ttu-id="9d25b-135">O cliente Microsoft Teams (Web, desktop ou celular) onde os usuários interagem com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9d25b-135">The Microsoft Teams client (web, desktop or mobile) where users interact with your app.</span></span>
  1. <span data-ttu-id="9d25b-136">Um servidor que responde às solicitações de conteúdo que será exibido no Microsoft Teams, por exemplo, o conteúdo da guia HTML ou um cartão adaptável de bot.</span><span class="sxs-lookup"><span data-stu-id="9d25b-136">A server that responds to requests for content that will be displayed in Teams, e.g., HTML tab content or a bot adaptive card .</span></span>
  1. <span data-ttu-id="9d25b-137">Um [pacote de aplicativos](/concepts/build-and-test/apps-package.md) do teams que consiste em três arquivos:</span><span class="sxs-lookup"><span data-stu-id="9d25b-137">A Teams [app package](/concepts/build-and-test/apps-package.md) consisting of three files:</span></span>

  > [!div class="checklist"]
  >
  > - <span data-ttu-id="9d25b-138">O manifest.jsem</span><span class="sxs-lookup"><span data-stu-id="9d25b-138">The manifest.json</span></span>
  > - <span data-ttu-id="9d25b-139">Um [ícone de cor](../resources/schema/manifest-schema.md#icons) para seu aplicativo exibir no catálogo de aplicativos públicos ou de organização</span><span class="sxs-lookup"><span data-stu-id="9d25b-139">A [color icon](../resources/schema/manifest-schema.md#icons) for your app to display in the public or organization app catalog</span></span>
 > - <span data-ttu-id="9d25b-140">Um [ícone de estrutura de tópicos](../resources/schema/manifest-schema.md#icons) para exibição na barra de atividades do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="9d25b-140">An [outline icon](../resources/schema/manifest-schema.md#icons) for display on the Teams activity bar.</span></span>

<span data-ttu-id="9d25b-141">Quando um aplicativo é instalado, o cliente do teams analisa o arquivo de manifesto para determinar as informações necessárias, como o nome do seu aplicativo e a URL onde os serviços estão localizados.</span><span class="sxs-lookup"><span data-stu-id="9d25b-141">When an app is installed, the Teams client parses the manifest file to determine needed information like the name of your app and the URL where the services are located.</span></span>

> [!NOTE]
><span data-ttu-id="9d25b-142">Caso ainda não tenha feito isso, você precisará entrar no seu Microsoft 365 ou conta para continuar com o processo de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="9d25b-142">If you haven't done so already, you will need to sign in to your Microsoft 365  or account to continue with the development process.</span></span>
>
> <span data-ttu-id="9d25b-143">Se você não tem uma conta da Microsoft 365, você pode se inscrever para uma assinatura do [microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program) .</span><span class="sxs-lookup"><span data-stu-id="9d25b-143">If you don't have a Microsoft 365 account, you can sign up for a [Microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program) subscription.</span></span> <span data-ttu-id="9d25b-144">É *grátis* por 90 dias e será renovado continuamente, desde que você o esteja usando para a atividade de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="9d25b-144">It's *free* for 90 days and will continually renew as long as you're using it for development activity.</span></span> <span data-ttu-id="9d25b-145">Se você tiver uma assinatura do Visual Studio *Enterprise* ou *Professional* , ambos os programas incluirão uma [assinatura](https://aka.ms/MyVisualStudioBenefits)gratuita de desenvolvedor do Microsoft 365, ativa pela vida da sua assinatura do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9d25b-145">If you have a Visual Studio *Enterprise* or *Professional* subscription, both programs include a free Microsoft 365 [developer subscription](https://aka.ms/MyVisualStudioBenefits), active for the life of your Visual Studio subscription.</span></span> <span data-ttu-id="9d25b-146">*Confira* [Configurar uma assinatura de desenvolvedor do Microsoft 365](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started).</span><span class="sxs-lookup"><span data-stu-id="9d25b-146">*See* [Set up a Microsoft 365 developer subscription](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started).</span></span>
>

### <a name="configuration-steps"></a><span data-ttu-id="9d25b-147">Etapas de configuração</span><span class="sxs-lookup"><span data-stu-id="9d25b-147">Configuration steps</span></span>

1. <span data-ttu-id="9d25b-148">Para configurar seu aplicativo, na página inicial do **Microsoft Teams Toolkit** , selecione **Editar pacote de aplicativos** .</span><span class="sxs-lookup"><span data-stu-id="9d25b-148">To configure your app, on the **Microsoft Teams Toolkit** landing page, select **Edit app package** .</span></span>
1. <span data-ttu-id="9d25b-149">No menu suspenso **meus ambientes** , selecione **desenvolvimento**.</span><span class="sxs-lookup"><span data-stu-id="9d25b-149">From the **My Environments** drop-down menu, select **development**.</span></span>
1. <span data-ttu-id="9d25b-150">Você vai parar na página de **detalhes do aplicativo** , onde você pode editar os campos de Propriedade do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9d25b-150">You will land on the **App details** page where you can edit your app's property fields.</span></span>
1. <span data-ttu-id="9d25b-151">A edição dos campos na página de detalhes do aplicativo atualiza o conteúdo do manifest.jsem um arquivo que será fornecido como parte do pacote de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="9d25b-151">Editing the fields in the App details page updates the contents of the manifest.json file that will ultimately ship as part of the app package.</span></span> [<span data-ttu-id="9d25b-152">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="9d25b-152">Learn more</span></span>](https://aka.ms/teams-toolkit-manifest)

## <a name="package-your-app"></a><span data-ttu-id="9d25b-153">Empacotar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="9d25b-153">Package your app</span></span>

<span data-ttu-id="9d25b-154">A modificação da página de **detalhes do aplicativo** ou a atualização do **manifesto** ou arquivos **. env** na pasta do seu aplicativo  **. publish** gerará automaticamente seu arquivo de **Development.zip** .</span><span class="sxs-lookup"><span data-stu-id="9d25b-154">Modifying the **app details** page or updating the **manifest**, or **.env** files in your app's  **.publish** folder will automatically generate your **Development.zip** file.</span></span> <span data-ttu-id="9d25b-155">O arquivo Development.zip inclui três arquivos necessários: o **manifest.js** e os [dois arquivos de ícone](../concepts/build-and-test/apps-package.md#icons).</span><span class="sxs-lookup"><span data-stu-id="9d25b-155">The Development.zip file includes three required files — the **manifest.json** and [two icon files](../concepts/build-and-test/apps-package.md#icons).</span></span>

## <a name="install-and-run-your-app-locally"></a><span data-ttu-id="9d25b-156">Instalar e executar o aplicativo localmente</span><span class="sxs-lookup"><span data-stu-id="9d25b-156">Install and run your app locally</span></span>

1. <span data-ttu-id="9d25b-157">No menu suspenso **configurações de solução** , selecione **implantar**.</span><span class="sxs-lookup"><span data-stu-id="9d25b-157">From the **Solution Configurations** dropdown menu, select **Deploy**.</span></span>

![Menu configurações de solução](../assets/images/solution-configurations.png)

2. <span data-ttu-id="9d25b-159">Selecione o botão **ISS Express + Teams** .</span><span class="sxs-lookup"><span data-stu-id="9d25b-159">Select the **ISS Express + Teams** button.</span></span>

1. <span data-ttu-id="9d25b-160">O Microsoft Teams será iniciado e a caixa de diálogo de instalação do aplicativo deverá aparecer no cliente do teams.</span><span class="sxs-lookup"><span data-stu-id="9d25b-160">Teams will launch and the app installation dialogue should appear in the Teams client.</span></span>

## <a name="validate-your-app"></a><span data-ttu-id="9d25b-161">Validar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="9d25b-161">Validate your app</span></span>

<span data-ttu-id="9d25b-162">A página **validar** permite verificar o pacote do aplicativo antes de enviar o aplicativo para o AppSource.</span><span class="sxs-lookup"><span data-stu-id="9d25b-162">The **Validate** page allows you to check your app package before submitting your app to AppSource.</span></span> <span data-ttu-id="9d25b-163">Basta carregar o pacote de manifesto e a ferramenta de validação verificará seu aplicativo em todos os casos de teste relacionados ao manifesto.</span><span class="sxs-lookup"><span data-stu-id="9d25b-163">Simply upload the manifest package and the validation tool will check your app against all manifest related test cases.</span></span> <span data-ttu-id="9d25b-164">Para cada teste com falha, a descrição fornece um link de documentação para ajudá-lo a corrigir o erro.</span><span class="sxs-lookup"><span data-stu-id="9d25b-164">For each failed tests, the description provides a documentation link to help you fix the error.</span></span> <span data-ttu-id="9d25b-165">Para os testes difíceis de automatizar, a lista de **verificação preliminar** detalha 7 dos casos de teste com falha mais comuns, bem como vincular a uma lista de verificação de envio completa.</span><span class="sxs-lookup"><span data-stu-id="9d25b-165">For the tests that are hard to automate, the **Preliminary checklist** details 7 of the most common failed test cases as well as link to a complete submission checklist.</span></span>

## <a name="publish-your-app-to-teams"></a><span data-ttu-id="9d25b-166">Publicar seu aplicativo no Teams</span><span class="sxs-lookup"><span data-stu-id="9d25b-166">Publish your app to Teams</span></span>

<span data-ttu-id="9d25b-167">✔ Na home page do seu projeto, você pode carregar seu aplicativo para uma equipe, enviar seu aplicativo para o repositório de aplicativos personalizado da empresa para usuários em sua organização ou enviar seu aplicativo para a origem do aplicativo para todos os usuários do teams.</span><span class="sxs-lookup"><span data-stu-id="9d25b-167">✔ On your project home page, you can upload your app to a team, submit your app to your company custom app store for users in your organization, or submit your app to App Source for all Teams users.</span></span>

<span data-ttu-id="9d25b-168">✔ Seu administrador de ti revisará esses envios.</span><span class="sxs-lookup"><span data-stu-id="9d25b-168">✔ Your IT admin will review these submissions.</span></span>

<span data-ttu-id="9d25b-169">✔ Você pode retornar à página **publicar** para verificar seu status de envio e saber se seu aplicativo foi aprovado ou rejeitado pelo seu administrador de ti. Este também é o local em que você vai enviar atualizações para seu aplicativo ou cancelar qualquer envio ativo no momento.</span><span class="sxs-lookup"><span data-stu-id="9d25b-169">✔  You can return to the **Publish** page to check on your submission status and learn if your app was approved or rejected by your IT admin. This is also where you'll come to submit updates to your app or cancel any currently active submissions.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9d25b-170">Próxima etapa: manutenção e suporte do seu aplicativo publicado</span><span class="sxs-lookup"><span data-stu-id="9d25b-170">Next step: Maintaining and supporting your published app</span></span>](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
>
