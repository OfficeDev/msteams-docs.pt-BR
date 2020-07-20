---
title: Criar aplicativos com o Microsoft Teams Toolkit e o Visual Studio
description: Introdução ao desenvolvimento de aplicativos personalizados de grande parte diretamente no Visual Studio com o Microsoft Teams Toolkit
keywords: Kit de ferramentas do Visual Studio Teams
ms.date: 06/30/2020
ms.openlocfilehash: e5715cf23cfd221b65afe0e6258ce06ff98770aa
ms.sourcegitcommit: 694babb79d379360a20cf928a9d2b88dd6d3bdd0
ms.translationtype: Auto
ms.contentlocale: pt-BR
ms.lasthandoff: 07/07/2020
ms.locfileid: "45051704"
---
# <a name="build-apps-with-the-microsoft-teams-toolkit-and-visual-studio"></a><span data-ttu-id="45ecd-104">Criar aplicativos com o Microsoft Teams Toolkit e o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="45ecd-104">Build apps with the Microsoft Teams Toolkit and Visual Studio</span></span>

<span data-ttu-id="45ecd-105">O Microsoft Teams Toolkit permite que você crie aplicativos personalizados do teams diretamente no ambiente do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="45ecd-105">The Microsoft Teams Toolkit enables you to create custom Teams apps directly within the Visual Studio environment.</span></span> <span data-ttu-id="45ecd-106">O kit de ferramentas orienta você durante o processo e oferece tudo o que você precisa para criar, depurar e iniciar o aplicativo Teams.</span><span class="sxs-lookup"><span data-stu-id="45ecd-106">The toolkit guides you through the process and provides everything you need to build, debug, and launch your Teams app.</span></span>

## <a name="installing-the-teams-toolkit"></a><span data-ttu-id="45ecd-107">Instalando o Teams Toolkit</span><span class="sxs-lookup"><span data-stu-id="45ecd-107">Installing the Teams Toolkit</span></span>

<span data-ttu-id="45ecd-108">O Microsoft Teams Toolkit para Visual Studio está disponível para download no [Visual Studio Marketplace](https://aka.ms/teams-toolkit) ou diretamente como uma extensão no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="45ecd-108">The Microsoft Teams Toolkit for Visual Studio is available for download from the [Visual Studio Marketplace](https://aka.ms/teams-toolkit) or directly as an extension within Visual Studio.</span></span>

## <a name="using-the-toolkit"></a><span data-ttu-id="45ecd-109">Usando o kit de ferramentas</span><span class="sxs-lookup"><span data-stu-id="45ecd-109">Using the toolkit</span></span>

- [<span data-ttu-id="45ecd-110">Configurar um novo projeto</span><span class="sxs-lookup"><span data-stu-id="45ecd-110">Set up a new project</span></span>](#set-up-a-new-teams-project)
- [<span data-ttu-id="45ecd-111">Configurar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="45ecd-111">Configure your app</span></span>](#configure-your-app)
- [<span data-ttu-id="45ecd-112">Empacotar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="45ecd-112">Package your app</span></span>](#package-your-app)
- [<span data-ttu-id="45ecd-113">Executar o aplicativo no Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="45ecd-113">Run your app in Teams</span></span>](#install-and-run-your-app-locally)
- [<span data-ttu-id="45ecd-114">Validar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="45ecd-114">Validate your app</span></span>](#validate-your-app)
- [<span data-ttu-id="45ecd-115">Publicar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="45ecd-115">Publish your app</span></span>](#publish-your-app-to-teams)

## <a name="set-up-a-new-teams-project"></a><span data-ttu-id="45ecd-116">Configurar um novo projeto do teams</span><span class="sxs-lookup"><span data-stu-id="45ecd-116">Set up a new Teams project</span></span>

1. <span data-ttu-id="45ecd-117">Crie um novo projeto e selecione o modelo Microsoft Terams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="45ecd-117">Create a new project and select the Microsoft Terams Toolkit template.</span></span>
1. <span data-ttu-id="45ecd-118">Você chegará à tela **Adicionar recursos** para configurar as propriedades do novo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="45ecd-118">You will arrive at the **Add capabilities** screen configure the properties for your new app.</span></span>
1. <span data-ttu-id="45ecd-119">Selecione o botão **concluir** para concluir o processo de configuração.</span><span class="sxs-lookup"><span data-stu-id="45ecd-119">Select the **Finish** button to complete the configuration process.</span></span>

## <a name="configure-your-app"></a><span data-ttu-id="45ecd-120">Configurar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="45ecd-120">Configure your app</span></span>

<span data-ttu-id="45ecd-121">Em seu núcleo, o aplicativo Teams engloba três componentes:</span><span class="sxs-lookup"><span data-stu-id="45ecd-121">At its core, the Teams app embraces three components:</span></span>

  1. <span data-ttu-id="45ecd-122">O cliente Microsoft Teams (Web, desktop ou celular) onde os usuários interagem com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="45ecd-122">The Microsoft Teams client (web, desktop or mobile) where users interact with your app.</span></span>
  1. <span data-ttu-id="45ecd-123">Um servidor que responde às solicitações de conteúdo que será exibido no Microsoft Teams, por exemplo, o conteúdo da guia HTML ou um cartão adaptável de bot.</span><span class="sxs-lookup"><span data-stu-id="45ecd-123">A server that responds to requests for content that will be displayed in Teams, e.g., HTML tab content or a bot adaptive card .</span></span>
  1. <span data-ttu-id="45ecd-124">Um [pacote de aplicativos](/concepts/build-and-test/apps-package.md) do teams que consiste em três arquivos:</span><span class="sxs-lookup"><span data-stu-id="45ecd-124">A Teams [app package](/concepts/build-and-test/apps-package.md) consisting of three files:</span></span>

  > [!div class="checklist"]
  >
  > - <span data-ttu-id="45ecd-125">O manifest.jsem</span><span class="sxs-lookup"><span data-stu-id="45ecd-125">The manifest.json</span></span> 
  > - <span data-ttu-id="45ecd-126">Um [ícone de cor](../resources/schema/manifest-schema.md#icons) para seu aplicativo exibir no catálogo de aplicativos públicos ou de organização</span><span class="sxs-lookup"><span data-stu-id="45ecd-126">A [color icon](../resources/schema/manifest-schema.md#icons) for your app to display in the public or organization app catalog</span></span>
 > - <span data-ttu-id="45ecd-127">Um [ícone de estrutura de tópicos](../resources/schema/manifest-schema.md#icons) para exibição na barra de atividades do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="45ecd-127">An [outline icon](../resources/schema/manifest-schema.md#icons) for display on the Teams activity bar.</span></span>

<span data-ttu-id="45ecd-128">Quando um aplicativo é instalado, o cliente do teams analisa o arquivo de manifesto para determinar as informações necessárias, como o nome do seu aplicativo e a URL onde os serviços estão localizados.</span><span class="sxs-lookup"><span data-stu-id="45ecd-128">When an app is installed, the Teams client parses the manifest file to determine needed information like the name of your app and the URL where the services are located.</span></span>

1. <span data-ttu-id="45ecd-129">Para configurar seu aplicativo, navegue até a janela extensão do **Kit de ferramentas do Microsoft Teams** .</span><span class="sxs-lookup"><span data-stu-id="45ecd-129">To configure your app, navigate to the **Microsoft Teams Toolkit** extension window.</span></span>
1. <span data-ttu-id="45ecd-130">Selecione **Editar pacote de aplicativos** para exibir a página de **detalhes do aplicativo** .</span><span class="sxs-lookup"><span data-stu-id="45ecd-130">Select **Edit app package** to view the **App details** page.</span></span>
1. <span data-ttu-id="45ecd-131">A edição dos campos na página de detalhes do aplicativo atualiza o conteúdo do manifest.jsem um arquivo que será fornecido como parte do pacote de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="45ecd-131">Editing the fields in the App details page updates the contents of the manifest.json file that will ultimately ship as part of the app package.</span></span> [<span data-ttu-id="45ecd-132">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="45ecd-132">Learn more</span></span>](https://aka.ms/teams-toolkit-manifest)

## <a name="package-your-app"></a><span data-ttu-id="45ecd-133">Empacotar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="45ecd-133">Package your app</span></span>

<span data-ttu-id="45ecd-134">Modificar você é a página de **detalhes do aplicativo** ou atualizar o **manifesto**, ou arquivos **. env** na pasta do seu aplicativo **. publish** irá gerar automaticamente seu arquivo de **Development.zip** .</span><span class="sxs-lookup"><span data-stu-id="45ecd-134">Modifying your the **app details** page or updating the **manifest**, or **.env** files in your app's  **.publish** folder will automatically generate your **Development.zip** file.</span></span> <span data-ttu-id="45ecd-135">Você precisará incluir [dois ícones](../concepts/build-and-test/apps-package.md#icons) na mesma pasta.</span><span class="sxs-lookup"><span data-stu-id="45ecd-135">You'll need to include [two icons](../concepts/build-and-test/apps-package.md#icons) in that same folder.</span></span>

## <a name="install-and-run-your-app-locally"></a><span data-ttu-id="45ecd-136">Instalar e executar o aplicativo localmente</span><span class="sxs-lookup"><span data-stu-id="45ecd-136">Install and run your app locally</span></span>

<span data-ttu-id="45ecd-137">No menu suspenso de *configurações de soluções* , selecione *implantar*.</span><span class="sxs-lookup"><span data-stu-id="45ecd-137">From the *Solutions Configurations* dropdown menu, select *Deploy*.</span></span> <span data-ttu-id="45ecd-138">Pressione o botão *ISS Express + Teams* .</span><span class="sxs-lookup"><span data-stu-id="45ecd-138">Press the *ISS Express + Teams* button.</span></span> <span data-ttu-id="45ecd-139">O Microsoft Teams será iniciado e a caixa de diálogo de instalação do aplicativo deverá aparecer no cliente do teams.</span><span class="sxs-lookup"><span data-stu-id="45ecd-139">Teams will launch and the app installation dialogue should appear in the Teams client.</span></span>

## <a name="validate-your-app"></a><span data-ttu-id="45ecd-140">Validar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="45ecd-140">Validate your app</span></span>

<span data-ttu-id="45ecd-141">A página **validar** permite verificar o pacote do aplicativo antes de enviar o aplicativo para o AppSource.</span><span class="sxs-lookup"><span data-stu-id="45ecd-141">The **Validate** page allows you to check your app package before submitting your app to AppSource.</span></span> <span data-ttu-id="45ecd-142">Basta carregar o pacote de manifesto e a ferramenta de validação verificará seu aplicativo em todos os casos de teste relacionados ao manifesto.</span><span class="sxs-lookup"><span data-stu-id="45ecd-142">Simply upload the manifest package and the validation tool will check your app against all manifest related test cases.</span></span> <span data-ttu-id="45ecd-143">Para cada teste com falha, a descrição fornece um link de documentação para ajudá-lo a corrigir o erro.</span><span class="sxs-lookup"><span data-stu-id="45ecd-143">For each failed tests, the description provides a documentation link to help you fix the error.</span></span> <span data-ttu-id="45ecd-144">Para os testes difíceis de automatizar, a lista de **verificação preliminar** detalha 7 dos casos de teste com falha mais comuns, bem como vincular a uma lista de verificação de envio completa.</span><span class="sxs-lookup"><span data-stu-id="45ecd-144">For the tests that are hard to automate, the **Preliminary checklist** details 7 of the most common failed test cases as well as link to a complete submission checklist.</span></span>

## <a name="publish-your-app-to-teams"></a><span data-ttu-id="45ecd-145">Publicar seu aplicativo no Teams</span><span class="sxs-lookup"><span data-stu-id="45ecd-145">Publish your app to Teams</span></span>

<span data-ttu-id="45ecd-146">Na home page do seu projeto, você pode carregar seu aplicativo para uma equipe, enviar seu aplicativo para o repositório de aplicativos personalizado da empresa para usuários em sua organização ou enviar seu aplicativo para a origem do aplicativo para todos os usuários do teams.</span><span class="sxs-lookup"><span data-stu-id="45ecd-146">On your project home page, you can upload your app to a team, submit your app to your company custom app store for users in your organization, or submit your app to App Source for all Teams users.</span></span> <span data-ttu-id="45ecd-147">Seu administrador de ti revisará esses envios.</span><span class="sxs-lookup"><span data-stu-id="45ecd-147">Your IT admin will review these submissions.</span></span> <span data-ttu-id="45ecd-148">Você pode retornar à página *publicar* para verificar seu status de envio e saber se seu aplicativo foi aprovado ou rejeitado pelo seu administrador de ti. Este também é o local em que você vai enviar atualizações para seu aplicativo ou cancelar qualquer envio ativo no momento.</span><span class="sxs-lookup"><span data-stu-id="45ecd-148">You can return to the *Publish* page to check on your submission status and learn if your app was approved or rejected by your IT admin. This is also where you'll come to submit updates to your app or cancel any currently active submissions.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="45ecd-149">Próxima etapa: manutenção e suporte do seu aplicativo publicado</span><span class="sxs-lookup"><span data-stu-id="45ecd-149">Next step: Maintaining and supporting your published app</span></span>](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
