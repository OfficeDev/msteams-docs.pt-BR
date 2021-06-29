---
title: Criar um canal ou uma guia de grupo
author: laujan
description: Um guia de início rápido para criar um canal e uma guia de grupo com o Gerador Yeoman para Microsoft Teams.
localization_priority: Normal
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: fedaf3ec639917110e16c666734fa3eedbcda18e
ms.sourcegitcommit: 85a52119df6c4cb4536572e6d2e7407f0e5e8a23
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2021
ms.locfileid: "53179963"
---
# <a name="create-a-channel-or-group-tab"></a><span data-ttu-id="53546-103">Criar um canal ou uma guia de grupo</span><span class="sxs-lookup"><span data-stu-id="53546-103">Create a channel or group tab</span></span>

## <a name="create-a-custom-channel-or-group-tab"></a><span data-ttu-id="53546-104">Criar um canal personalizado ou uma guia de grupo</span><span class="sxs-lookup"><span data-stu-id="53546-104">Create a custom channel or group tab</span></span>

<span data-ttu-id="53546-105">Você pode criar uma guia de canal ou grupo usando Node.js e o Gerador Yeoman, ASP.NETCore ou MVC ASP.NETCore.</span><span class="sxs-lookup"><span data-stu-id="53546-105">You can create a channel or group tab using Node.js and the Yeoman Generator, ASP.NETCore, or ASP.NETCore MVC.</span></span>

# <a name="nodejs"></a>[<span data-ttu-id="53546-106">Node.js</span><span class="sxs-lookup"><span data-stu-id="53546-106">Node.js</span></span>](#tab/nodejs)

### <a name="create-a-custom-channel-and-group-tab-using-nodejs-and-the-yeoman-generator"></a><span data-ttu-id="53546-107">Criar um canal personalizado e uma guia de grupo usando Node.js e o Gerador Yeoman</span><span class="sxs-lookup"><span data-stu-id="53546-107">Create a custom channel and group tab using Node.js and the Yeoman Generator</span></span>

> [!NOTE]
> <span data-ttu-id="53546-108">Este artigo segue as etapas descritas na com build [Seu](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) primeiro wiki do aplicativo Microsoft Teams encontrado no repositório de GitHub do Microsoft OfficeDev.</span><span class="sxs-lookup"><span data-stu-id="53546-108">This article follows the steps outlined in the [build Your first Microsoft Teams app](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) Wiki found in the Microsoft OfficeDev GitHub repository.</span></span>

<span data-ttu-id="53546-109">Você pode criar um canal personalizado ou uma guia de grupo usando o [gerador Teams Yeoman](https://github.com/OfficeDev/generator-teams/).</span><span class="sxs-lookup"><span data-stu-id="53546-109">You can create a custom channel or group tab using the [Teams Yeoman generator](https://github.com/OfficeDev/generator-teams/).</span></span>

### <a name="prerequisites-for-apps"></a><span data-ttu-id="53546-110">Pré-requisitos para aplicativos</span><span class="sxs-lookup"><span data-stu-id="53546-110">Prerequisites for apps</span></span>

<span data-ttu-id="53546-111">Você deve ter uma compreensão dos seguintes pré-requisitos:</span><span class="sxs-lookup"><span data-stu-id="53546-111">You must have an understanding of the following prerequisites:</span></span>

- <span data-ttu-id="53546-112">Você deve ter um locatário Office 365 e uma equipe configurada com **Permitir o carregamento de aplicativos personalizados** habilitados.</span><span class="sxs-lookup"><span data-stu-id="53546-112">You must have an Office 365 tenant and a team configured with **Allow uploading custom apps** enabled.</span></span> <span data-ttu-id="53546-113">Para obter mais informações, [consulte prepare your Office 365 tenant](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span><span class="sxs-lookup"><span data-stu-id="53546-113">For more information, see [prepare your Office 365 tenant](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="53546-114">Se você não tiver uma conta Office 365, poderá inscrever-se para uma assinatura gratuita por meio do programa Office 365 Desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="53546-114">If you do not currently have an Office 365 account, you can sign up for a free subscription through the Office 365 Developer Program.</span></span> <span data-ttu-id="53546-115">A assinatura permanece ativa desde que você a use para desenvolvimento contínuo.</span><span class="sxs-lookup"><span data-stu-id="53546-115">The subscription remains active as long as you are using it for ongoing development.</span></span> <span data-ttu-id="53546-116">Consulte [welcome to the Office 365 Developer Program](/office/developer-program/microsoft-365-developer-program).</span><span class="sxs-lookup"><span data-stu-id="53546-116">See [welcome to the Office 365 Developer Program](/office/developer-program/microsoft-365-developer-program).</span></span>

<span data-ttu-id="53546-117">Além disso, este projeto exige que você tenha o seguinte instalado em seu ambiente de desenvolvimento:</span><span class="sxs-lookup"><span data-stu-id="53546-117">In addition, this project requires that you have the following installed in your development environment:</span></span>

- <span data-ttu-id="53546-118">Qualquer editor de texto ou IDE.</span><span class="sxs-lookup"><span data-stu-id="53546-118">Any text editor or IDE.</span></span> <span data-ttu-id="53546-119">Você pode instalar e usar [Visual Studio Code](https://code.visualstudio.com/download) gratuitamente.</span><span class="sxs-lookup"><span data-stu-id="53546-119">You can install and use [Visual Studio Code](https://code.visualstudio.com/download) for free.</span></span>

- <span data-ttu-id="53546-120">[Node.js/npm](https://nodejs.org/en/).</span><span class="sxs-lookup"><span data-stu-id="53546-120">[Node.js/npm](https://nodejs.org/en/).</span></span> <span data-ttu-id="53546-121">Use a versão LTS mais recente.</span><span class="sxs-lookup"><span data-stu-id="53546-121">Use the latest LTS version.</span></span> <span data-ttu-id="53546-122">O nó Gerenciador de Pacotes (npm) instala em seu sistema com a instalação de Node.js.</span><span class="sxs-lookup"><span data-stu-id="53546-122">The Node Package Manager (npm) installs in your system with the installation of Node.js.</span></span>

- <span data-ttu-id="53546-123">Depois de instalar o Node.js, instale os pacotes [Yeoman](https://yeoman.io/) e [gulp-cli](https://www.npmjs.com/package/gulp-cli) inserindo o seguinte no prompt de comando:</span><span class="sxs-lookup"><span data-stu-id="53546-123">After you have successfully installed Node.js, install the [Yeoman](https://yeoman.io/) and [gulp-cli](https://www.npmjs.com/package/gulp-cli) packages by entering the following in your command prompt:</span></span>

    ```bash
    npm install yo gulp-cli --global
    ```

- <span data-ttu-id="53546-124">Instale o Microsoft Teams aplicativos inserindo o seguinte no prompt de comando:</span><span class="sxs-lookup"><span data-stu-id="53546-124">Install the Microsoft Teams Apps generator by entering the following in your command prompt:</span></span>

    ```bash
    npm install generator-teams --global
    ```

### <a name="generate-your-project"></a><span data-ttu-id="53546-125">Gerar seu projeto</span><span class="sxs-lookup"><span data-stu-id="53546-125">Generate your project</span></span>

<span data-ttu-id="53546-126">**Para gerar seu projeto**</span><span class="sxs-lookup"><span data-stu-id="53546-126">**To generate your project**</span></span>

1. <span data-ttu-id="53546-127">Em um prompt de comando, crie um novo diretório para seu projeto de guia.</span><span class="sxs-lookup"><span data-stu-id="53546-127">At a command prompt, create a new directory for your tab project.</span></span>

1. <span data-ttu-id="53546-128">Para iniciar o gerador, vá para o novo diretório e digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="53546-128">To start the generator, go to your new directory and type the following command:</span></span>

    ```bash
    yo teams
    ```

1. <span data-ttu-id="53546-129">Em seguida, forneça uma série de valores usados no arquivomanifest.js **no** aplicativo:</span><span class="sxs-lookup"><span data-stu-id="53546-129">Next, provide a series of values that are used in your application's **manifest.json** file:</span></span>

    ![captura de tela de abertura do gerador](/microsoftteams/platform/assets/images/tab-images/teamsTabScreenshot.PNG)

    <span data-ttu-id="53546-131">**Qual é o nome da solução?**</span><span class="sxs-lookup"><span data-stu-id="53546-131">**What is your solution name?**</span></span>

    <span data-ttu-id="53546-132">Esse é o nome do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="53546-132">This is your project name.</span></span> <span data-ttu-id="53546-133">Você pode aceitar o nome sugerido selecionando a **tecla Enter.**</span><span class="sxs-lookup"><span data-stu-id="53546-133">You can accept the suggested name by selecting the **Enter** key.</span></span>

    <span data-ttu-id="53546-134">**Onde você deseja colocar os arquivos?**</span><span class="sxs-lookup"><span data-stu-id="53546-134">**Where do you want to place the files?**</span></span>

    <span data-ttu-id="53546-135">No momento, você está no diretório do projeto.</span><span class="sxs-lookup"><span data-stu-id="53546-135">You are currently in your project directory.</span></span> <span data-ttu-id="53546-136">Selecione **Inserir**.</span><span class="sxs-lookup"><span data-stu-id="53546-136">Select **Enter**.</span></span>

    <span data-ttu-id="53546-137">**Título do seu projeto Microsoft Teams aplicativo?**</span><span class="sxs-lookup"><span data-stu-id="53546-137">**Title of your Microsoft Teams app project?**</span></span>

    <span data-ttu-id="53546-138">Esse é o nome do pacote do aplicativo e será usado no manifesto e na descrição do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="53546-138">This is your app package name and will be used in the app manifest and description.</span></span> <span data-ttu-id="53546-139">Insira um título ou selecione **Enter** para aceitar o nome padrão.</span><span class="sxs-lookup"><span data-stu-id="53546-139">Enter a title or select **Enter** to accept the default name.</span></span>

    <span data-ttu-id="53546-140">**Seu nome (empresa) ? (máx. 32 caracteres)**</span><span class="sxs-lookup"><span data-stu-id="53546-140">**Your (company) name? (max 32 characters)**</span></span>

    <span data-ttu-id="53546-141">O nome da empresa será usado no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="53546-141">Your company name will be used in the app manifest.</span></span> <span data-ttu-id="53546-142">Insira um nome da empresa ou selecione **Enter** para aceitar o nome padrão.</span><span class="sxs-lookup"><span data-stu-id="53546-142">Enter a company name or select **Enter** to accept the default name.</span></span>

    <span data-ttu-id="53546-143">**Qual versão de manifesto você gostaria de usar?**</span><span class="sxs-lookup"><span data-stu-id="53546-143">**Which manifest version would you like to use?**</span></span>

    <span data-ttu-id="53546-144">Selecione o esquema padrão.</span><span class="sxs-lookup"><span data-stu-id="53546-144">Select the default schema.</span></span>

    <span data-ttu-id="53546-145">**Scaffolding rápido? (Y/n)**</span><span class="sxs-lookup"><span data-stu-id="53546-145">**Quick scaffolding? (Y/n)**</span></span>

    <span data-ttu-id="53546-146">O padrão é sim; insira **n** para inserir sua ID do Microsoft Partner.</span><span class="sxs-lookup"><span data-stu-id="53546-146">The default is yes; enter **n** to enter your Microsoft Partner Id.</span></span>

    <span data-ttu-id="53546-147">**Insira sua ID do Microsoft Partner, se você tiver uma? (Deixe em branco para ignorar)**</span><span class="sxs-lookup"><span data-stu-id="53546-147">**Enter your Microsoft Partner Id, if you have one? (Leave blank to skip)**</span></span>

    <span data-ttu-id="53546-148">Esse campo não é obrigatório e só deve ser usado se você já faz parte da [Rede de Parceiros da Microsoft.](https://partner.microsoft.com)</span><span class="sxs-lookup"><span data-stu-id="53546-148">This field is not required and should only be used if you are already part of the [Microsoft Partner Network](https://partner.microsoft.com).</span></span>

    <span data-ttu-id="53546-149">**O que você deseja adicionar ao seu projeto?**</span><span class="sxs-lookup"><span data-stu-id="53546-149">**What do you want to add to your project?**</span></span>

    <span data-ttu-id="53546-150">Selecione **( ) Uma &ast; guia**.</span><span class="sxs-lookup"><span data-stu-id="53546-150">Select **( &ast; ) A Tab**.</span></span>

    <span data-ttu-id="53546-151">**A URL onde você hospedará essa solução?**</span><span class="sxs-lookup"><span data-stu-id="53546-151">**The URL where you will host this solution?**</span></span>

    <span data-ttu-id="53546-152">Por padrão, o gerador sugere uma URL de Sites do Azure.</span><span class="sxs-lookup"><span data-stu-id="53546-152">By default the generator suggests an Azure Web Sites URL.</span></span> <span data-ttu-id="53546-153">Você só está testando seu aplicativo localmente, portanto, uma URL válida não é necessária.</span><span class="sxs-lookup"><span data-stu-id="53546-153">You are only testing your app locally, therefore, a valid URL is not necessary.</span></span>

    <span data-ttu-id="53546-154">**Você gostaria de mostrar um indicador de carregamento quando seu aplicativo/guia é carregado?**</span><span class="sxs-lookup"><span data-stu-id="53546-154">**Would you like show a loading indicator when your app/tab loads?**</span></span>

    <span data-ttu-id="53546-155">Escolha **não incluir** um indicador de carregamento quando seu aplicativo ou guia for carregado.</span><span class="sxs-lookup"><span data-stu-id="53546-155">Choose **not** to include a loading indicator when your app or tab loads.</span></span> <span data-ttu-id="53546-156">O padrão é não, digite **n**.</span><span class="sxs-lookup"><span data-stu-id="53546-156">The default is no, enter **n**.</span></span>

   <span data-ttu-id="53546-157">**Você gostaria que aplicativos pessoais fossem renderizados sem uma barra de texto de tabulação?**</span><span class="sxs-lookup"><span data-stu-id="53546-157">**Would you like personal apps to be rendered without a tab header-bar?**</span></span>

    <span data-ttu-id="53546-158">Escolha **não** incluir aplicativos pessoais a serem renderizados sem uma barra de header-bar de tabulação.</span><span class="sxs-lookup"><span data-stu-id="53546-158">Choose **not** to include personal apps to be rendered without a tab header-bar.</span></span> <span data-ttu-id="53546-159">O padrão é não, digite **n**.</span><span class="sxs-lookup"><span data-stu-id="53546-159">Default is no, enter **n**.</span></span>

    <span data-ttu-id="53546-160">**Você gostaria de incluir a estrutura de teste e testes iniciais? (y/N)**</span><span class="sxs-lookup"><span data-stu-id="53546-160">**Would you like to include Test framework and initial tests? (y/N)**</span></span>

    <span data-ttu-id="53546-161">Escolha **não** incluir uma estrutura de teste para este projeto.</span><span class="sxs-lookup"><span data-stu-id="53546-161">Choose **not** to include a test framework for this project.</span></span> <span data-ttu-id="53546-162">O padrão é sim; enter **n**.</span><span class="sxs-lookup"><span data-stu-id="53546-162">The default is yes; enter **n**.</span></span>

    <span data-ttu-id="53546-163">**Você gostaria de usar aplicativos do Azure Insights para telemetria? (y/N)**</span><span class="sxs-lookup"><span data-stu-id="53546-163">**Would you like to use Azure Applications Insights for telemetry? (y/N)**</span></span>

    <span data-ttu-id="53546-164">Escolha **não** incluir o [aplicativo Azure Insights](/azure/azure-monitor/app/app-insights-overview).</span><span class="sxs-lookup"><span data-stu-id="53546-164">Choose **not** to include [Azure Application Insights](/azure/azure-monitor/app/app-insights-overview).</span></span> <span data-ttu-id="53546-165">O padrão é não; enter **n**.</span><span class="sxs-lookup"><span data-stu-id="53546-165">The default is no; enter **n**.</span></span>

    <span data-ttu-id="53546-166">**Nome da guia padrão (máx. 16 caracteres)?**</span><span class="sxs-lookup"><span data-stu-id="53546-166">**Default Tab Name (max 16 characters)?**</span></span>

    <span data-ttu-id="53546-167">Nomeia sua guia. Esse nome de guia será usado em todo o seu projeto como um componente de caminho de arquivo ou URL.</span><span class="sxs-lookup"><span data-stu-id="53546-167">Name your tab. This tab name will be used throughout your project as a file or URL path component.</span></span>

    <span data-ttu-id="53546-168">**Que tipo de Guia você gostaria de criar?**</span><span class="sxs-lookup"><span data-stu-id="53546-168">**What kind of Tab would you like to create?**</span></span>

    <span data-ttu-id="53546-169">Use as teclas de seta para selecionar **a guia Configurável.**</span><span class="sxs-lookup"><span data-stu-id="53546-169">Use the arrow keys to select **Configurable** tab.</span></span>

    <span data-ttu-id="53546-170">**Quais escopos você pretende usar para sua Guia?**</span><span class="sxs-lookup"><span data-stu-id="53546-170">**What scopes do you intend to use for your Tab?**</span></span>

    <span data-ttu-id="53546-171">Você pode selecionar uma equipe ou um chat em grupo.</span><span class="sxs-lookup"><span data-stu-id="53546-171">You can select a team or a group chat.</span></span>

    <span data-ttu-id="53546-172">**Você precisa do suporte para o Microsoft Azure Active Directory com Login Único para a guia?**</span><span class="sxs-lookup"><span data-stu-id="53546-172">**Do you require Azure AD Single-Sign-On support for the tab?**</span></span>

    <span data-ttu-id="53546-173">Escolha **não** incluir o suporte ao Azure AD Single-Sign-On para a guia. O padrão é sim, digite **n**.</span><span class="sxs-lookup"><span data-stu-id="53546-173">Choose **not** to include Azure AD Single-Sign-On support for the tab. The default is yes, enter **n**.</span></span>

    <span data-ttu-id="53546-174">**Deseja que essa guia seja disponibilizada no SharePoint Online? (Y/n)**</span><span class="sxs-lookup"><span data-stu-id="53546-174">**Do you want this tab to be available in SharePoint Online? (Y/n)**</span></span>

    <span data-ttu-id="53546-175">Insira **n**.</span><span class="sxs-lookup"><span data-stu-id="53546-175">Enter **n**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="53546-176">O componente de **caminho yourDefaultTabNameTab**, é o valor que você inscrevia no gerador para **Nome** da Guia Padrão mais a **palavra Tab**.</span><span class="sxs-lookup"><span data-stu-id="53546-176">The path component **yourDefaultTabNameTab**, is the value that you entered in the generator for **Default Tab Name** plus the word **Tab**.</span></span>
    >
    > <span data-ttu-id="53546-177">Por exemplo: DefaultTabName: **MyTab**  >  **/MyTabTab/**</span><span class="sxs-lookup"><span data-stu-id="53546-177">For example: DefaultTabName: **MyTab** > **/MyTabTab/**</span></span>

1. <span data-ttu-id="53546-178">Em Visual Studio Code ou em qualquer editor de código, vá para o diretório do projeto e abra o seguinte arquivo:</span><span class="sxs-lookup"><span data-stu-id="53546-178">In Visual Studio Code or any code editor, go to your project directory and open the following file:</span></span>

    ```bash
    ./src/app/scripts/<yourDefaultTabNameTab>/<yourDefaultTabNameTab>.tsx
    ```

1. <span data-ttu-id="53546-179">Localize `render()` o método e adicione a seguinte marca e conteúdo à parte superior do código do `<div>` `<PanelBody>` contêiner:</span><span class="sxs-lookup"><span data-stu-id="53546-179">Locate the `render()` method and add the following `<div>` tag and content to the top of the `<PanelBody>` container code:</span></span>

    ```html
        <PanelBody>
            <div style={styles.section}>
                Hello World! Yo Teams rocks!
            </div>
        </PanelBody>
    ```

1. <span data-ttu-id="53546-180">Certifique-se de salvar o arquivo atualizado.</span><span class="sxs-lookup"><span data-stu-id="53546-180">Make sure to save the updated file.</span></span>

### <a name="build-and-run-your-application"></a><span data-ttu-id="53546-181">Criar e executar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="53546-181">Build and run your application</span></span>

<span data-ttu-id="53546-182">Em um prompt de comando, abra o diretório do projeto para concluir as próximas tarefas.</span><span class="sxs-lookup"><span data-stu-id="53546-182">At a command prompt, open your project directory to complete the next tasks.</span></span>

#### <a name="create-the-app-package"></a><span data-ttu-id="53546-183">Criar o pacote do aplicativo</span><span class="sxs-lookup"><span data-stu-id="53546-183">Create the app package</span></span>

<span data-ttu-id="53546-184">Você deve ter um pacote de aplicativos para testar sua guia Teams.</span><span class="sxs-lookup"><span data-stu-id="53546-184">You must have an app package to test your tab in Teams.</span></span> <span data-ttu-id="53546-185">É uma pasta zip que contém os seguintes arquivos necessários:</span><span class="sxs-lookup"><span data-stu-id="53546-185">It is a zip folder that contains the following required files:</span></span>

- <span data-ttu-id="53546-186">Um **ícone de cor completo** medindo 192 x 192 pixels.</span><span class="sxs-lookup"><span data-stu-id="53546-186">A **full color icon** measuring 192 x 192 pixels.</span></span>
- <span data-ttu-id="53546-187">Um **ícone de contorno transparente** medindo 32 x 32 pixels.</span><span class="sxs-lookup"><span data-stu-id="53546-187">A **transparent outline icon** measuring 32 x 32 pixels.</span></span>
- <span data-ttu-id="53546-188">Um **manifest.json** que especifica os atributos do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="53546-188">A **manifest.json** file that specifies the attributes of your app.</span></span>

<span data-ttu-id="53546-189">O pacote é criado por meio de uma tarefa gulp que valida o manifest.jsno arquivo on e gera a pasta zip no **diretório ./package.**</span><span class="sxs-lookup"><span data-stu-id="53546-189">The package is created through a gulp task that validates the manifest.json file and generates the zip folder in the **./package directory**.</span></span> <span data-ttu-id="53546-190">No prompt de comando, insira o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="53546-190">In the command prompt, enter the following command:</span></span>

```bash
gulp manifest
```

#### <a name="build-your-application"></a><span data-ttu-id="53546-191">Criar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="53546-191">Build your application</span></span>

<span data-ttu-id="53546-192">O comando build transpila sua solução para a **pasta ./dist.**</span><span class="sxs-lookup"><span data-stu-id="53546-192">The build command transpiles your solution into the **./dist** folder.</span></span> <span data-ttu-id="53546-193">Insira o seguinte comando no prompt de comando:</span><span class="sxs-lookup"><span data-stu-id="53546-193">Enter the following command in the command prompt:</span></span>

```bash
gulp build
```

#### <a name="run-your-application-in-localhost"></a><span data-ttu-id="53546-194">Executar seu aplicativo no localhost</span><span class="sxs-lookup"><span data-stu-id="53546-194">Run your application in localhost</span></span>

1. <span data-ttu-id="53546-195">Inicie um servidor Web local inserindo o seguinte no prompt de comando:</span><span class="sxs-lookup"><span data-stu-id="53546-195">Start a local web server by entering the following in the command prompt:</span></span>

    ```bash
    gulp serve
    ```

1. <span data-ttu-id="53546-196">Insira no navegador, substitua pelo nome da guia e veja a home page do aplicativo, conforme `http://localhost:3007/<yourDefaultAppNameTab>/` mostrado na imagem a **<yourDefaultAppNameTab>** seguir:</span><span class="sxs-lookup"><span data-stu-id="53546-196">Enter `http://localhost:3007/<yourDefaultAppNameTab>/` in your browser, replace **<yourDefaultAppNameTab>** with your tab name, and view your application's home page as shown in the following image:</span></span>

    ![captura de tela da home page](~/assets/images/tab-images/homePage.png)

1. <span data-ttu-id="53546-198">Para exibir sua página de configuração de tabulação, vá para `https://localhost:3007/<yourDefaultAppNameTab>/config.html` .</span><span class="sxs-lookup"><span data-stu-id="53546-198">To view your tab configuration page, go to `https://localhost:3007/<yourDefaultAppNameTab>/config.html`.</span></span> <span data-ttu-id="53546-199">O seguinte é mostrado:</span><span class="sxs-lookup"><span data-stu-id="53546-199">The following is shown:</span></span>

    ![Captura de tela da página de configuração](~/assets/images/tab-images/configurationPage.png)

### <a name="establish-a-secure-tunnel-to-your-tab"></a><span data-ttu-id="53546-201">Estabelecer um túnel seguro para sua guia</span><span class="sxs-lookup"><span data-stu-id="53546-201">Establish a secure tunnel to your tab</span></span>

<span data-ttu-id="53546-202">Microsoft Teams é um produto baseado em nuvem e exige que o conteúdo da guia seja disponibilizado na nuvem usando pontos de extremidade HTTPS.</span><span class="sxs-lookup"><span data-stu-id="53546-202">Microsoft Teams is a cloud-based product and requires that your tab content be available from the cloud using HTTPS endpoints.</span></span> <span data-ttu-id="53546-203">Teams não permite hospedagem local.</span><span class="sxs-lookup"><span data-stu-id="53546-203">Teams does not allow local hosting.</span></span> <span data-ttu-id="53546-204">Você deve publicar sua guia em uma URL pública ou usar um proxy que exponha sua porta local a uma URL voltada para a Internet.</span><span class="sxs-lookup"><span data-stu-id="53546-204">You must either publish your tab to a public URL or use a proxy that exposes your local port to an internet-facing URL.</span></span>

<span data-ttu-id="53546-205">Para testar sua extensão de tabulação, use [ngrok](https://ngrok.com/docs), que é integrado a esse aplicativo.</span><span class="sxs-lookup"><span data-stu-id="53546-205">To test your tab extension, use [ngrok](https://ngrok.com/docs), which is built into this application.</span></span> <span data-ttu-id="53546-206">O Ngrok é uma ferramenta de software de proxy reverso que cria um túnel para os pontos de extremidade HTTPS do servidor Web em execução localmente.</span><span class="sxs-lookup"><span data-stu-id="53546-206">Ngrok is a reverse proxy software tool that creates a tunnel to your locally running web server's publicly-available HTTPS endpoints.</span></span> <span data-ttu-id="53546-207">Os pontos de extremidade da Web do seu servidor estão disponíveis durante a sessão atual em seu computador.</span><span class="sxs-lookup"><span data-stu-id="53546-207">Your server's web endpoints are available during the current session on your computer.</span></span> <span data-ttu-id="53546-208">Quando o computador é desligado ou vai para o sono, o serviço não está mais disponível.</span><span class="sxs-lookup"><span data-stu-id="53546-208">When the computer is shut down or goes to sleep the service is no longer available.</span></span>

<span data-ttu-id="53546-209">No prompt de comando, saia do localhost e insira o seguinte:</span><span class="sxs-lookup"><span data-stu-id="53546-209">In your command prompt, exit localhost and enter the following:</span></span>

```bash
gulp ngrok-serve
```

> [!IMPORTANT]
> <span data-ttu-id="53546-210">Depois que sua guia for carregada no Microsoft Teams e salva com êxito, você poderá exibi-la na galeria de guias, adicioná-la à barra de guias e interagir com ela até que sua sessão de túnel de ngrok termine.</span><span class="sxs-lookup"><span data-stu-id="53546-210">After your tab has been uploaded to Microsoft Teams and successfully saved, you can view it in the tabs gallery, add it to the tabs bar, and interact with it until your ngrok tunnel session ends.</span></span> <span data-ttu-id="53546-211">Se você reiniciar sua sessão de ngrok, deverá atualizar seu aplicativo com a nova URL.</span><span class="sxs-lookup"><span data-stu-id="53546-211">If you restart your ngrok session, you must update your app with the new URL.</span></span>

### <a name="upload-your-application-to-teams"></a><span data-ttu-id="53546-212">Upload seu aplicativo para Teams</span><span class="sxs-lookup"><span data-stu-id="53546-212">Upload your application to Teams</span></span>

<span data-ttu-id="53546-213">**Para carregar seu aplicativo para Teams**</span><span class="sxs-lookup"><span data-stu-id="53546-213">**To upload your application to Teams**</span></span>

1. <span data-ttu-id="53546-214">Vá para Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="53546-214">Go to Microsoft Teams.</span></span> <span data-ttu-id="53546-215">Se você usar a [versão baseada na Web,](https://teams.microsoft.com) poderá inspecionar seu código front-end usando as ferramentas de desenvolvedor [do navegador.](~/tabs/how-to/developer-tools.md)</span><span class="sxs-lookup"><span data-stu-id="53546-215">If you use the [web-based version](https://teams.microsoft.com) you can inspect your front-end code using your browser's [developer tools](~/tabs/how-to/developer-tools.md).</span></span>
1. <span data-ttu-id="53546-216">Em suas equipes no painel esquerdo, selecione as releições &#x25CF;&#x25CF;&#x25CF; ao lado da equipe que você está usando para testar sua guia e escolha **Gerenciar equipe**.</span><span class="sxs-lookup"><span data-stu-id="53546-216">From your teams on the left pane, select the ellipses &#x25CF;&#x25CF;&#x25CF; next to the team that you are using to test your tab and choose **Manage team**.</span></span>
1. <span data-ttu-id="53546-217">No painel principal, selecione **Aplicativos** na barra de guias e escolha Upload um **aplicativo** personalizado localizado no canto inferior direito da página.</span><span class="sxs-lookup"><span data-stu-id="53546-217">In the main pane, select **Apps** from the tab bar and choose **Upload a custom app** located in the lower right corner of the page.</span></span>
1. <span data-ttu-id="53546-218">Vá para o diretório do projeto, navegue até a pasta **./package,** selecione a pasta zip do pacote do aplicativo e escolha **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="53546-218">Go your project directory, browse to the **./package** folder, select the app package zip folder, and choose **Open**.</span></span>

    ![Guia Canal adicionado](../../assets/images/tab-images/channeltabadded.png)

1. <span data-ttu-id="53546-220">Selecione **Adicionar** na caixa de diálogo pop-up.</span><span class="sxs-lookup"><span data-stu-id="53546-220">Select **Add** in the pop-up dialog box.</span></span> <span data-ttu-id="53546-221">Sua guia é carregada em Teams.</span><span class="sxs-lookup"><span data-stu-id="53546-221">Your tab uploads into Teams.</span></span>
1. <span data-ttu-id="53546-222">Retorne à sua equipe, escolha o canal onde você deseja exibir a guia, selecione ➕ na barra de guias e escolha sua guia na galeria.</span><span class="sxs-lookup"><span data-stu-id="53546-222">Return to your team, choose the channel where you want to display the tab, select ➕ from the tab bar, and choose your tab from the gallery.</span></span>
1. <span data-ttu-id="53546-223">Siga as instruções para adicionar uma guia. Há uma caixa de diálogo de configuração personalizada para seu canal ou guia de grupo.</span><span class="sxs-lookup"><span data-stu-id="53546-223">Follow the directions for adding a tab. There is a custom configuration dialog box for your channel or group tab.</span></span>
1. <span data-ttu-id="53546-224">Selecione **Salvar** e sua guia é adicionada à barra de guias do canal.</span><span class="sxs-lookup"><span data-stu-id="53546-224">Select **Save** and your tab is added to the channel's tab bar.</span></span>

    ![Guia canal carregado](../../assets/images/tab-images/channeltabuploaded.png)

# <a name="aspnet-core"></a>[<span data-ttu-id="53546-226">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="53546-226">ASP.NET Core</span></span>](#tab/aspnetcore)

### <a name="create-a-custom-channel-or-group-tab-with-aspnet-core"></a><span data-ttu-id="53546-227">Criar um canal personalizado ou uma guia de grupo com ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="53546-227">Create a custom channel or group tab with ASP.NET Core</span></span>

<span data-ttu-id="53546-228">Você pode criar um canal personalizado ou uma guia de grupo usando a C# e ASP.Net core de lâmina.</span><span class="sxs-lookup"><span data-stu-id="53546-228">You can create a custom channel or group tab using C# and ASP.Net Core Razor page.</span></span> <span data-ttu-id="53546-229">[O App Studio para Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) também é usado para finalizar o manifesto do aplicativo e implantar sua guia para Teams.</span><span class="sxs-lookup"><span data-stu-id="53546-229">[App Studio for Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) is also used to finalize your app manifest and deploy your tab to Teams.</span></span>

### <a name="prerequisites-for-teams-apps"></a><span data-ttu-id="53546-230">Pré-requisitos para Teams aplicativos</span><span class="sxs-lookup"><span data-stu-id="53546-230">Prerequisites for Teams apps</span></span>

<span data-ttu-id="53546-231">Você deve ter uma compreensão dos seguintes pré-requisitos:</span><span class="sxs-lookup"><span data-stu-id="53546-231">You must have an understanding of the following prerequisites:</span></span>

- <span data-ttu-id="53546-232">Você deve ter um locatário Office 365 e uma equipe configurada com **Permitir o carregamento de aplicativos personalizados** habilitados.</span><span class="sxs-lookup"><span data-stu-id="53546-232">You must have an Office 365 tenant and a team configured with **Allow uploading custom apps** enabled.</span></span> <span data-ttu-id="53546-233">Para obter mais informações, [consulte prepare your Office 365 tenant](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span><span class="sxs-lookup"><span data-stu-id="53546-233">For more information, see [prepare your Office 365 tenant](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="53546-234">Se você não tiver uma conta Microsoft 365, poderá inscrever-se para uma assinatura gratuita por meio do [Programa de Desenvolvedores da Microsoft.](https://developer.microsoft.com/en-us/microsoft-365/dev-program)</span><span class="sxs-lookup"><span data-stu-id="53546-234">If you do not currently have a Microsoft 365 account, you can sign up for a free subscription through the [Microsoft Developer Program](https://developer.microsoft.com/en-us/microsoft-365/dev-program).</span></span> <span data-ttu-id="53546-235">A assinatura permanece ativa desde que você a use para desenvolvimento contínuo.</span><span class="sxs-lookup"><span data-stu-id="53546-235">The subscription remains active as long as you are using it for ongoing development.</span></span>

- <span data-ttu-id="53546-236">Use o App Studio para importar seu aplicativo para Teams.</span><span class="sxs-lookup"><span data-stu-id="53546-236">Use App Studio to import your application to Teams.</span></span> <span data-ttu-id="53546-237">Para instalar o App Studio, selecione **Aplicativo** da Loja de Aplicativos no canto inferior esquerdo do aplicativo Teams ![ e ](~/assets/images/tab-images/storeApp.png) pesquise **por App Studio**.</span><span class="sxs-lookup"><span data-stu-id="53546-237">To install App Studio, select **Apps** ![Store App](~/assets/images/tab-images/storeApp.png) at the lower left corner of the Teams app, and search for **App Studio**.</span></span> <span data-ttu-id="53546-238">Depois de encontrar o azulejo, selecione-o e escolha **Adicionar** na caixa de diálogo pop-up para instalá-lo.</span><span class="sxs-lookup"><span data-stu-id="53546-238">After you find the tile, select it and choose **Add** in the pop-up dialog box to install it.</span></span>

<span data-ttu-id="53546-239">Além disso, este projeto exige que você tenha o seguinte instalado em seu ambiente de desenvolvimento:</span><span class="sxs-lookup"><span data-stu-id="53546-239">In addition, this project requires that you have the following installed in your development environment:</span></span>

- <span data-ttu-id="53546-240">A versão atual do Visual Studio IDE com a carga de trabalho de desenvolvimento entre **plataformas .NET CORE** instalada.</span><span class="sxs-lookup"><span data-stu-id="53546-240">The current version of the Visual Studio IDE with the **.NET CORE cross-platform development** workload installed.</span></span> <span data-ttu-id="53546-241">Se você ainda não tiver Visual Studio, poderá baixar e instalar a versão Microsoft Visual Studio Community [versão](https://visualstudio.microsoft.com/downloads) mais recente gratuitamente.</span><span class="sxs-lookup"><span data-stu-id="53546-241">If you do not already have Visual Studio, you can download and install the latest [Microsoft Visual Studio Community](https://visualstudio.microsoft.com/downloads) version for free.</span></span>

- <span data-ttu-id="53546-242">A [ferramenta proxy reverso ngrok.](https://ngrok.com)</span><span class="sxs-lookup"><span data-stu-id="53546-242">The [ngrok](https://ngrok.com) reverse proxy tool.</span></span> <span data-ttu-id="53546-243">Use ngrok para criar um túnel para os pontos de extremidade HTTPS do servidor Web em execução localmente.</span><span class="sxs-lookup"><span data-stu-id="53546-243">Use ngrok to create a tunnel to your locally running web server's publicly-available HTTPS endpoints.</span></span> <span data-ttu-id="53546-244">Você pode [baixar ngrok](https://ngrok.com/download).</span><span class="sxs-lookup"><span data-stu-id="53546-244">You can [download ngrok](https://ngrok.com/download).</span></span>

### <a name="get-the-source-code"></a><span data-ttu-id="53546-245">Obter o código-fonte</span><span class="sxs-lookup"><span data-stu-id="53546-245">Get the source code</span></span>

<span data-ttu-id="53546-246">Em um prompt de comando, crie um novo diretório para seu projeto de guia.</span><span class="sxs-lookup"><span data-stu-id="53546-246">At a command prompt, create a new directory for your tab project.</span></span> <span data-ttu-id="53546-247">Um projeto simples é fornecido para você começar.</span><span class="sxs-lookup"><span data-stu-id="53546-247">A simple project is provided to get you started.</span></span> <span data-ttu-id="53546-248">Clone o repositório de exemplo em seu novo diretório usando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="53546-248">Clone the sample repository into your new directory using the following command:</span></span>

```bash
git clone https://github.com/OfficeDev/microsoft-teams-sample-tabs.git
```

<span data-ttu-id="53546-249">Como alternativa, você pode recuperar o código-fonte baixando a pasta zip e extraindo os arquivos.</span><span class="sxs-lookup"><span data-stu-id="53546-249">Alternately, you can retrieve the source code by downloading the zip folder and extracting the files.</span></span>

<span data-ttu-id="53546-250">**Para criar e executar o projeto de guia**</span><span class="sxs-lookup"><span data-stu-id="53546-250">**To build and run the tab project**</span></span>

1. <span data-ttu-id="53546-251">Depois de ter o código-fonte, vá para Visual Studio e selecione **Abrir um projeto ou solução**.</span><span class="sxs-lookup"><span data-stu-id="53546-251">After you have the source code, go to Visual Studio and select **Open a project or solution**.</span></span>
1. <span data-ttu-id="53546-252">Vá para o diretório de aplicativos de tabulação e abra **ChannelGroupTab.sln**.</span><span class="sxs-lookup"><span data-stu-id="53546-252">Go to the tab application directory and open **ChannelGroupTab.sln**.</span></span>
1. <span data-ttu-id="53546-253">Para criar e executar seu aplicativo, pressione **F5** ou escolha **Iniciar Depuração** no menu **Depurar.**</span><span class="sxs-lookup"><span data-stu-id="53546-253">To build and run your application, press **F5** or choose **Start Debugging** from the **Debug** menu.</span></span>
1. <span data-ttu-id="53546-254">Em um navegador, vá para as SEGUINTES URLs e verifique se o aplicativo foi carregado corretamente:</span><span class="sxs-lookup"><span data-stu-id="53546-254">In a browser, go to the following URLs and verify the application loaded properly:</span></span>

    - `http://localhost:44355`
    - `http://localhost:44355/privacy`
    - `http://localhost:44355/tou`

### <a name="review-the-source-code"></a><span data-ttu-id="53546-255">Revisar o código-fonte</span><span class="sxs-lookup"><span data-stu-id="53546-255">Review the source code</span></span>

#### <a name="startupcs"></a><span data-ttu-id="53546-256">Startup.cs</span><span class="sxs-lookup"><span data-stu-id="53546-256">Startup.cs</span></span>

<span data-ttu-id="53546-257">Esse projeto foi criado a partir de um modelo vazio do Aplicativo Web 2.2 do ASP.NET Core 2.2 com a caixa de seleção Avançado - Configurar para **HTTPS** selecionada na instalação.</span><span class="sxs-lookup"><span data-stu-id="53546-257">This project was created from an ASP.NET Core 2.2 Web Application empty template with the **Advanced - Configure for HTTPS** check box selected at setup.</span></span> <span data-ttu-id="53546-258">Os serviços MVC são registrados pelo método da estrutura de injeção de `ConfigureServices()` dependência.</span><span class="sxs-lookup"><span data-stu-id="53546-258">The MVC services are registered by the dependency injection framework's `ConfigureServices()` method.</span></span> <span data-ttu-id="53546-259">Além disso, o modelo vazio não habilita o serviço de conteúdo estático por padrão, portanto, o middleware de arquivos estáticos é adicionado ao método usando `Configure()` o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="53546-259">Additionally, the empty template does not enable serving static content by default, so the static files middleware is added to the `Configure()` method using the following code:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
  {
    services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_2);
  }
public void Configure(IApplicationBuilder app)
  {
    app.UseStaticFiles();
    app.UseMvc();
  }
```

#### <a name="wwwroot-folder"></a><span data-ttu-id="53546-260">pasta wwwroot</span><span class="sxs-lookup"><span data-stu-id="53546-260">wwwroot folder</span></span>

<span data-ttu-id="53546-261">Em ASP.NET Core, a pasta raiz da Web é onde o aplicativo procura arquivos estáticos.</span><span class="sxs-lookup"><span data-stu-id="53546-261">In ASP.NET Core, the web root folder is where the application looks for static files.</span></span>

#### <a name="indexcshtml"></a><span data-ttu-id="53546-262">Index.cshtml</span><span class="sxs-lookup"><span data-stu-id="53546-262">Index.cshtml</span></span>

<span data-ttu-id="53546-263">ASP.NET Core trata arquivos chamados **Index** como o padrão ou home page do site.</span><span class="sxs-lookup"><span data-stu-id="53546-263">ASP.NET Core treats files called **Index** as the default or home page for the site.</span></span> <span data-ttu-id="53546-264">Quando a URL do navegador aponta para a raiz do site, **Index.cshtml** é exibida como a home page do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="53546-264">When your browser URL points to the root of the site, **Index.cshtml** is displayed as the home page for your application.</span></span>

#### <a name="tabcs"></a><span data-ttu-id="53546-265">Tab.cs</span><span class="sxs-lookup"><span data-stu-id="53546-265">Tab.cs</span></span>

<span data-ttu-id="53546-266">Esse C# contém um método chamado de **Tab.cshtml** durante a configuração.</span><span class="sxs-lookup"><span data-stu-id="53546-266">This C# file contains a method that is called from **Tab.cshtml** during configuration.</span></span>

#### <a name="appmanifest-folder"></a><span data-ttu-id="53546-267">Pasta AppManifest</span><span class="sxs-lookup"><span data-stu-id="53546-267">AppManifest folder</span></span>

<span data-ttu-id="53546-268">Esta pasta contém os seguintes arquivos de pacote de aplicativos necessários:</span><span class="sxs-lookup"><span data-stu-id="53546-268">This folder contains the following required app package files:</span></span>

- <span data-ttu-id="53546-269">Um **ícone de cor completo** medindo 192 x 192 pixels.</span><span class="sxs-lookup"><span data-stu-id="53546-269">A **full color icon** measuring 192 x 192 pixels.</span></span>
- <span data-ttu-id="53546-270">Um **ícone de contorno transparente** medindo 32 x 32 pixels.</span><span class="sxs-lookup"><span data-stu-id="53546-270">A **transparent outline icon** measuring 32 x 32 pixels.</span></span>
- <span data-ttu-id="53546-271">Um **manifest.json** que especifica os atributos do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="53546-271">A **manifest.json** file that specifies the attributes of your app.</span></span>

<span data-ttu-id="53546-272">Esses arquivos precisam ser cortados em um pacote de aplicativos para uso ao carregar sua guia para Teams.</span><span class="sxs-lookup"><span data-stu-id="53546-272">These files need to be zipped in an app package for use in uploading your tab to Teams.</span></span> <span data-ttu-id="53546-273">Quando um usuário opta por adicionar ou atualizar sua guia, Microsoft Teams carrega o especificado em seu manifesto, incorpora-o em um IFrame e a renderiza em `configurationUrl` sua guia.</span><span class="sxs-lookup"><span data-stu-id="53546-273">When a user chooses to add or update your tab, Microsoft Teams loads the `configurationUrl` specified in your manifest, embeds it in an IFrame, and renders it in your tab.</span></span>

#### <a name="csproj"></a><span data-ttu-id="53546-274">.csproj</span><span class="sxs-lookup"><span data-stu-id="53546-274">.csproj</span></span>

<span data-ttu-id="53546-275">Na janela Visual Studio Do Explorador de Soluções, clique com o botão direito do mouse no projeto e selecione **Editar Project Arquivo**.</span><span class="sxs-lookup"><span data-stu-id="53546-275">In the Visual Studio Solution Explorer window, right-click on the project and select **Edit Project File**.</span></span> <span data-ttu-id="53546-276">No final do arquivo, você vê o seguinte código que cria e atualiza sua pasta zip quando o aplicativo é construído:</span><span class="sxs-lookup"><span data-stu-id="53546-276">At the end of the file, you see the following code that creates and updates your zip folder when the application builds:</span></span>

```xml
<PropertyGroup>
    <PostBuildEvent>powershell.exe Compress-Archive -Path \"$(ProjectDir)AppManifest\*\" -DestinationPath \"$(TargetDir)tab.zip\" -Force</PostBuildEvent>
  </PropertyGroup>

  <ItemGroup>
    <EmbeddedResource Include="AppManifest\icon-outline.png">
      <CopyToOutputDirectory>Always</CopyToOutputDirectory>
    </EmbeddedResource>
    <EmbeddedResource Include="AppManifest\icon-color.png">
      <CopyToOutputDirectory>Always</CopyToOutputDirectory>
    </EmbeddedResource>
    <EmbeddedResource Include="AppManifest\manifest.json">
      <CopyToOutputDirectory>Always</CopyToOutputDirectory>
    </EmbeddedResource>
  </ItemGroup>
```

### <a name="establish-a-secure-tunnel-to-your-tab-for-teams"></a><span data-ttu-id="53546-277">Estabeleça um túnel seguro para sua guia para Teams</span><span class="sxs-lookup"><span data-stu-id="53546-277">Establish a secure tunnel to your tab for Teams</span></span>

<span data-ttu-id="53546-278">Microsoft Teams é um produto baseado em nuvem e exige que o conteúdo da guia seja disponibilizado na nuvem usando pontos de extremidade HTTPS.</span><span class="sxs-lookup"><span data-stu-id="53546-278">Microsoft Teams is a cloud-based product and requires that your tab content be available from the cloud using HTTPS endpoints.</span></span> <span data-ttu-id="53546-279">Teams não permite hospedagem local.</span><span class="sxs-lookup"><span data-stu-id="53546-279">Teams does not allow local hosting.</span></span> <span data-ttu-id="53546-280">Você deve publicar sua guia em uma URL pública ou usar um proxy que exponha sua porta local a uma URL voltada para a Internet.</span><span class="sxs-lookup"><span data-stu-id="53546-280">You must either publish your tab to a public URL, or use a proxy that exposes your local port to an internet-facing URL.</span></span>

<span data-ttu-id="53546-281">Para testar sua guia, use [ngrok](https://ngrok.com/docs).</span><span class="sxs-lookup"><span data-stu-id="53546-281">To test your tab, use [ngrok](https://ngrok.com/docs).</span></span> <span data-ttu-id="53546-282">Os pontos de extremidade da Web do seu servidor estão disponíveis enquanto o ngrok está em execução no computador.</span><span class="sxs-lookup"><span data-stu-id="53546-282">Your server's web endpoints are available while ngrok is running on your computer.</span></span> <span data-ttu-id="53546-283">Na versão gratuita do ngrok, se você fechar o ngrok, as URLs serão diferentes na próxima vez em que você a iniciar.</span><span class="sxs-lookup"><span data-stu-id="53546-283">In the free version of ngrok, if you close ngrok, the URLs are different the next time you start it.</span></span>

- <span data-ttu-id="53546-284">Em um prompt de comando na raiz do diretório do projeto, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="53546-284">At a command prompt in the root of your project directory, run the following command:</span></span>

    ```bash
    ngrok http https://localhost:44355 -host-header="localhost:44355"
    ```

- <span data-ttu-id="53546-285">O Ngrok escuta as solicitações da Internet e as encaminha para seu aplicativo quando está sendo executado na porta 44355.</span><span class="sxs-lookup"><span data-stu-id="53546-285">Ngrok listens to requests from the internet and routes them to your application when it is running on port 44355.</span></span> <span data-ttu-id="53546-286">Deve parecer `https://y8rCgT2b.ngrok.io/` onde **y8rCgT2b** é substituído pela URL HTTPS alfanumérico ngrok.</span><span class="sxs-lookup"><span data-stu-id="53546-286">It should resemble `https://y8rCgT2b.ngrok.io/` where **y8rCgT2b** is replaced by your ngrok alpha-numeric HTTPS URL.</span></span>

- <span data-ttu-id="53546-287">Certifique-se de manter o prompt de comando com o ngrok em execução e anote a URL.</span><span class="sxs-lookup"><span data-stu-id="53546-287">Ensure that you keep the command prompt with ngrok running and make a note of the URL.</span></span>

### <a name="update-your-application"></a><span data-ttu-id="53546-288">Atualizar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="53546-288">Update your application</span></span>

<span data-ttu-id="53546-289">Em **Tab.cshtml,** o aplicativo apresenta ao usuário dois botões de opção para exibir a guia com um ícone vermelho ou cinza.</span><span class="sxs-lookup"><span data-stu-id="53546-289">Within **Tab.cshtml** the application presents the user with two option buttons for displaying the tab with either a red or gray icon.</span></span> <span data-ttu-id="53546-290">Escolher os **gatilhos do** botão Selecionar Cinza ou Selecionar Vermelho ou , respectivamente, define e habilita o botão  `saveGray()` `saveRed()` `settings.setValidityState(true)` **Salvar** na página de configuração.</span><span class="sxs-lookup"><span data-stu-id="53546-290">Choosing the **Select Gray** or **Select Red** button triggers `saveGray()` or `saveRed()`, respectively, sets `settings.setValidityState(true)`, and enables the **Save** button on the configuration page.</span></span> <span data-ttu-id="53546-291">Esse código permite Teams que você concluiu os requisitos de configuração e que a instalação pode continuar.</span><span class="sxs-lookup"><span data-stu-id="53546-291">This code lets Teams know that you have completed the configuration requirements and the installation can proceed.</span></span> <span data-ttu-id="53546-292">Os parâmetros de `settings.setSettings` são definidos.</span><span class="sxs-lookup"><span data-stu-id="53546-292">The parameters of `settings.setSettings` are set.</span></span> <span data-ttu-id="53546-293">Por fim, `saveEvent.notifySuccess()` é chamado para indicar que a URL de conteúdo foi resolvida com êxito.</span><span class="sxs-lookup"><span data-stu-id="53546-293">Finally, `saveEvent.notifySuccess()` is called to indicate that the content URL has been successfully resolved.</span></span>

#### <a name="_layoutcshtml"></a><span data-ttu-id="53546-294">_Layout.cshtml</span><span class="sxs-lookup"><span data-stu-id="53546-294">_Layout.cshtml</span></span>

<span data-ttu-id="53546-295">Para que sua guia seja exibida Teams, você deve incluir o **SDK** do cliente JavaScript Microsoft Teams e incluir uma chamada depois que a página `microsoftTeams.initialize()` for carregada.</span><span class="sxs-lookup"><span data-stu-id="53546-295">For your tab to display in Teams, you must include the **Microsoft Teams JavaScript client SDK** and include a call to `microsoftTeams.initialize()` after your page loads.</span></span> <span data-ttu-id="53546-296">É assim que sua guia e o cliente Teams se comunicam:</span><span class="sxs-lookup"><span data-stu-id="53546-296">This is how your tab and the Teams client communicate:</span></span>

<span data-ttu-id="53546-297">Vá para **a pasta Shared,** abra **_Layout.cshtml** e adicione o seguinte à `<head>` marca:</span><span class="sxs-lookup"><span data-stu-id="53546-297">Go to the **Shared** folder, open **_Layout.cshtml**, and add the following to the `<head>` tag:</span></span>

```html
<script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
<script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>
```

> [!IMPORTANT]
> <span data-ttu-id="53546-298">Não copie e colará `<script src="...">` as URLs desta página, pois elas não representam a versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="53546-298">Do not copy and paste the `<script src="...">` URLs from this page, as they do not represent the latest version.</span></span> <span data-ttu-id="53546-299">Para obter a versão mais recente do SDK, sempre vá [para Microsoft Teams API JavaScript](https://www.npmjs.com/package/@microsoft/teams-js).</span><span class="sxs-lookup"><span data-stu-id="53546-299">To get the latest version of the SDK, always go to [Microsoft Teams JavaScript API](https://www.npmjs.com/package/@microsoft/teams-js).</span></span>

#### <a name="tabcshtml"></a><span data-ttu-id="53546-300">Tab.cshtml</span><span class="sxs-lookup"><span data-stu-id="53546-300">Tab.cshtml</span></span>

<span data-ttu-id="53546-301">**Para atualizar Tab.cshtml**</span><span class="sxs-lookup"><span data-stu-id="53546-301">**To update Tab.cshtml**</span></span>

1. <span data-ttu-id="53546-302">Abra **Tab.cshtml** no Visual Studio e atualize o `<script>` .</span><span class="sxs-lookup"><span data-stu-id="53546-302">Open **Tab.cshtml** in Visual Studio and update the embedded `<script>`.</span></span>

1. <span data-ttu-id="53546-303">Na parte superior do script, chame `microsoftTeams.initialize()` .</span><span class="sxs-lookup"><span data-stu-id="53546-303">At the top of the script, call `microsoftTeams.initialize()`.</span></span>

1. <span data-ttu-id="53546-304">Atualize `websiteUrl` os valores e em cada função com a URL de `contentUrl` ngrok HTTPS para sua guia.</span><span class="sxs-lookup"><span data-stu-id="53546-304">Update the `websiteUrl` and `contentUrl` values in each function with the HTTPS ngrok URL to your tab.</span></span>

    <span data-ttu-id="53546-305">Seu código agora deve incluir o seguinte **com y8rCgT2b** substituído pela URL do ngrok:</span><span class="sxs-lookup"><span data-stu-id="53546-305">Your code should now include the following with **y8rCgT2b** replaced with your ngrok URL:</span></span>

    ```javascript
        microsoftTeams.initialize();

        let saveGray = () => {
            microsoftTeams.settings.registerOnSaveHandler(function (saveEvent) {
                microsoftTeams.settings.setSettings({
                    websiteUrl: `https://y8rCgT2b.ngrok.io`,
                    contentUrl: `https://y8rCgT2b.ngrok.io/gray/`,
                    entityId: "grayIconTab",
                    suggestedDisplayName: "MyNewTab"
                });
                saveEvent.notifySuccess();
            });
        }

        let saveRed = () => {
            microsoftTeams.settings.registerOnSaveHandler(function (saveEvent) {
                microsoftTeams.settings.setSettings({
                    websiteUrl: `https://y8rCgT2b.ngrok.io`,
                    contentUrl: `https://y8rCgT2b.ngrok.io/red/`,
                    entityId: "redIconTab",
                    suggestedDisplayName: "MyNewTab"
                });
                saveEvent.notifySuccess();
        });
        }
    ```

1. <span data-ttu-id="53546-306">Salve o **Tab.cshtml atualizado**.</span><span class="sxs-lookup"><span data-stu-id="53546-306">Save the updated **Tab.cshtml**.</span></span>

### <a name="build-and-run-your-application-for-teams"></a><span data-ttu-id="53546-307">Criar e executar seu aplicativo para Teams</span><span class="sxs-lookup"><span data-stu-id="53546-307">Build and run your application for Teams</span></span>

<span data-ttu-id="53546-308">**Para criar e executar seu aplicativo**</span><span class="sxs-lookup"><span data-stu-id="53546-308">**To build and run your application**</span></span>

1. <span data-ttu-id="53546-309">Em Visual Studio, pressione **F5** ou escolha **Iniciar Depuração** no menu **Depurar.**</span><span class="sxs-lookup"><span data-stu-id="53546-309">In Visual Studio, press **F5** or choose **Start Debugging** from the **Debug** menu.</span></span>
1. <span data-ttu-id="53546-310">Verifique se **o ngrok** está sendo executado e funcionando corretamente abrindo seu navegador e indo para sua página de conteúdo por meio da URL HTTPS ngrok fornecida na janela do prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="53546-310">Verify that **ngrok** is running and working properly by opening your browser and going to your content page via the ngrok HTTPS URL that was provided in your command prompt window.</span></span>

> [!TIP]
> <span data-ttu-id="53546-311">Você precisa ter seu aplicativo no Visual Studio e ngrok em execução para concluir as etapas fornecidas neste artigo.</span><span class="sxs-lookup"><span data-stu-id="53546-311">You need to have both your application in Visual Studio and ngrok running to complete the steps provided in this article.</span></span> <span data-ttu-id="53546-312">Se você precisar parar de executar seu aplicativo Visual Studio para trabalhar nele, **mantenha o ngrok em execução**.</span><span class="sxs-lookup"><span data-stu-id="53546-312">If you need to stop running your application in Visual Studio to work on it, **keep ngrok running**.</span></span> <span data-ttu-id="53546-313">Ele escuta e retoma o roteamento da solicitação do aplicativo quando ele é reiniciado no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="53546-313">It listens and resumes routing your application's request when it restarts in Visual Studio.</span></span> <span data-ttu-id="53546-314">Se você tiver que reiniciar o serviço ngrok, ele retornará uma nova URL e será preciso atualizar seu aplicativo com a nova URL.</span><span class="sxs-lookup"><span data-stu-id="53546-314">If you have to restart the ngrok service it returns a new URL and you have to update your application with the new URL.</span></span>

### <a name="upload-your-tab-for-teams"></a><span data-ttu-id="53546-315">Upload sua guia para Teams</span><span class="sxs-lookup"><span data-stu-id="53546-315">Upload your tab for Teams</span></span>

> [!NOTE]
> <span data-ttu-id="53546-316">O App Studio pode ser usado para editar seu **manifest.jsno** arquivo e carregar o pacote concluído para Teams.</span><span class="sxs-lookup"><span data-stu-id="53546-316">App Studio can be used to edit your **manifest.json** file and upload the completed package to Teams.</span></span> <span data-ttu-id="53546-317">Você também pode editar manualmente o **manifest.jsno** arquivo.</span><span class="sxs-lookup"><span data-stu-id="53546-317">You can also manually edit the **manifest.json** file.</span></span> <span data-ttu-id="53546-318">Se fizer isso, certifique-se de criar a solução novamente para criar o arquivo **tab.zip** para carregar.</span><span class="sxs-lookup"><span data-stu-id="53546-318">If you do, ensure that you build the solution again to create the **tab.zip** file to upload.</span></span>

<span data-ttu-id="53546-319">**Para carregar sua guia com o App Studio**</span><span class="sxs-lookup"><span data-stu-id="53546-319">**To upload your tab with App Studio**</span></span>

1. <span data-ttu-id="53546-320">Vá para Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="53546-320">Go to Microsoft Teams.</span></span> <span data-ttu-id="53546-321">Se você usar a [versão baseada na Web,](https://teams.microsoft.com)poderá inspecionar seu código front-end usando as ferramentas de desenvolvedor [do navegador.](~/tabs/how-to/developer-tools.md)</span><span class="sxs-lookup"><span data-stu-id="53546-321">If you use the [web-based version](https://teams.microsoft.com), you can inspect your front-end code using your browser's [developer tools](~/tabs/how-to/developer-tools.md).</span></span>

1. <span data-ttu-id="53546-322">Vá para **o App Studio** e selecione a guia Editor **de** manifesto.</span><span class="sxs-lookup"><span data-stu-id="53546-322">Go to **App Studio** and select the **Manifest editor** tab.</span></span>

1. <span data-ttu-id="53546-323">Selecione **Importar um aplicativo existente** no editor de **Manifesto** para começar a atualizar o pacote de aplicativos para sua guia. O código-fonte vem com seu próprio manifesto parcialmente completo.</span><span class="sxs-lookup"><span data-stu-id="53546-323">Select **Import an existing app** in the **Manifest editor** to begin updating the app package for your tab. The source code comes with its own partially complete manifest.</span></span> <span data-ttu-id="53546-324">O nome do pacote do aplicativo é **tab.zip**.</span><span class="sxs-lookup"><span data-stu-id="53546-324">The name of your app package is **tab.zip**.</span></span> <span data-ttu-id="53546-325">Ele está disponível no seguinte caminho:</span><span class="sxs-lookup"><span data-stu-id="53546-325">It is available from the following path:</span></span>

    ```bash
    /bin/Debug/netcoreapp2.2/tab.zip
    ```

1. <span data-ttu-id="53546-326">Upload **tab.zip** App Studio.</span><span class="sxs-lookup"><span data-stu-id="53546-326">Upload **tab.zip** to App Studio.</span></span>

#### <a name="update-your-app-package-with-manifest-editor"></a><span data-ttu-id="53546-327">Atualizar seu pacote de aplicativos com o editor de manifesto</span><span class="sxs-lookup"><span data-stu-id="53546-327">Update your app package with Manifest editor</span></span>

<span data-ttu-id="53546-328">Depois de carregar seu pacote de aplicativos no App Studio, você deve configurá-lo.</span><span class="sxs-lookup"><span data-stu-id="53546-328">After you have uploaded your app package into App Studio, you must configure it.</span></span>

<span data-ttu-id="53546-329">Selecione o azulejo para sua guia recém-importada no painel direito da página de boas-vindas do editor de manifesto.</span><span class="sxs-lookup"><span data-stu-id="53546-329">Select the tile for your newly imported tab in the right panel of the Manifest editor welcome page.</span></span>

<span data-ttu-id="53546-330">Há uma lista de etapas no lado esquerdo do editor de Manifesto e, à direita, uma lista de propriedades que devem ter valores para cada uma dessas etapas.</span><span class="sxs-lookup"><span data-stu-id="53546-330">There is a list of steps on the left side of the Manifest editor, and on the right, a list of properties that must have values for each of those steps.</span></span> <span data-ttu-id="53546-331">Grande parte das informações foi fornecida pelo seumanifest.js **em,** mas há campos que você deve atualizar.</span><span class="sxs-lookup"><span data-stu-id="53546-331">Much of the information has been provided by your **manifest.json** but there are fields that you must update.</span></span>

##### <a name="details-app-details"></a><span data-ttu-id="53546-332">Detalhes: Detalhes do aplicativo</span><span class="sxs-lookup"><span data-stu-id="53546-332">Details: App details</span></span>

<span data-ttu-id="53546-333">Na seção **Detalhes do** aplicativo:</span><span class="sxs-lookup"><span data-stu-id="53546-333">In the **App details** section:</span></span>

1. <span data-ttu-id="53546-334">Em **Identificação**, selecione **Gerar** para substituir a ID do espaço reservado pelo GUID necessário para sua guia.</span><span class="sxs-lookup"><span data-stu-id="53546-334">Under **Identification**, select **Generate** to replace the placeholder ID with the required GUID for your tab.</span></span>

1. <span data-ttu-id="53546-335">Em **Informações do desenvolvedor**, **atualize Site** com sua URL HTTPS **ngrok.**</span><span class="sxs-lookup"><span data-stu-id="53546-335">Under **Developer information**, update **Website** with your **ngrok** HTTPS URL.</span></span>

1. <span data-ttu-id="53546-336">Em **URLs do aplicativo,** atualize a **instrução Privacy** para `https://<yourngrokurl>/privacy` e Termos de **uso** para `https://<yourngrokurl>/tou`>.</span><span class="sxs-lookup"><span data-stu-id="53546-336">Under **App URLs**, update the **Privacy statement** to `https://<yourngrokurl>/privacy` and **Terms of use** to `https://<yourngrokurl>/tou`>.</span></span>

##### <a name="capabilities-tabs"></a><span data-ttu-id="53546-337">Recursos: guias</span><span class="sxs-lookup"><span data-stu-id="53546-337">Capabilities: Tabs</span></span>

<span data-ttu-id="53546-338">Na seção **Guias:**</span><span class="sxs-lookup"><span data-stu-id="53546-338">In the **Tabs** section:</span></span>

1. <span data-ttu-id="53546-339">Na **guia Equipe,** selecione **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="53546-339">Under **Team tab**, select **Add**.</span></span>

1. <span data-ttu-id="53546-340">Na janela **pop-up da guia** Equipe, atualize a URL de **configuração** para `https://<yourngrokurl>/tab` .</span><span class="sxs-lookup"><span data-stu-id="53546-340">In the **Team tab** pop-up window, update the **Configuration URL** to `https://<yourngrokurl>/tab`.</span></span>

1. <span data-ttu-id="53546-341">Verifique se as caixas de seleção Pode **atualizar configuração?**, **Equipe** e **Chat** de Grupo estão selecionadas e selecione **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="53546-341">Ensure the **Can update configuration?**, **Team**, and **Group chat** checkboxes are selected and select **Save**.</span></span>

##### <a name="finish-domains-and-permissions"></a><span data-ttu-id="53546-342">Concluir: domínios e permissões</span><span class="sxs-lookup"><span data-stu-id="53546-342">Finish: Domains and permissions</span></span>

<span data-ttu-id="53546-343">Na seção **Domínios e** permissões, **domínios** de suas guias devem conter sua URL ngrok sem o prefixo HTTPS `<yourngrokurl>.ngrok.io/` .</span><span class="sxs-lookup"><span data-stu-id="53546-343">In the **Domains and permissions** section, **Domains from your tabs** must contain your ngrok URL without the HTTPS prefix `<yourngrokurl>.ngrok.io/`.</span></span>

##### <a name="finish-test-and-distribute"></a><span data-ttu-id="53546-344">Concluir: Testar e distribuir</span><span class="sxs-lookup"><span data-stu-id="53546-344">Finish: Test and distribute</span></span>

> [!IMPORTANT]
> <span data-ttu-id="53546-345">À direita, em **Descrição,** você verá o seguinte aviso:</span><span class="sxs-lookup"><span data-stu-id="53546-345">On the right, in **Description**, you see the following warning:</span></span>
>
> <span data-ttu-id="53546-346">&#9888; "**A matriz 'validDomains' não pode conter um site de tunelamento...**"</span><span class="sxs-lookup"><span data-stu-id="53546-346">&#9888; "**The 'validDomains' array cannot contain a tunneling site...**"</span></span>
>
> <span data-ttu-id="53546-347">Esse aviso pode ser ignorado durante o teste da guia.</span><span class="sxs-lookup"><span data-stu-id="53546-347">This warning can be ignored while testing your tab.</span></span>

1. <span data-ttu-id="53546-348">Na seção **Testar e Distribuir,** selecione **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="53546-348">In the **Test and Distribute** section, select **Install**.</span></span>

1. <span data-ttu-id="53546-349">Na caixa de diálogo pop-up, selecione **Adicionar a** uma equipe ou no drop-down, selecione Adicionar a **um chat**.</span><span class="sxs-lookup"><span data-stu-id="53546-349">In the pop-up dialog box, select **Add to a team** or from the drop-down, select **Add to a chat**.</span></span>

1. <span data-ttu-id="53546-350">Escolha a equipe ou o chat onde você deseja que a guia seja exibida e selecione **Configurar uma guia**.</span><span class="sxs-lookup"><span data-stu-id="53546-350">Choose the team or chat where you want the tab to be displayed and select **Set up a tab**.</span></span>

1. <span data-ttu-id="53546-351">Na próxima caixa de diálogo pop-up, escolha **Selecionar** Cinza ou **Selecionar Vermelho** e **selecione Salvar**.</span><span class="sxs-lookup"><span data-stu-id="53546-351">In the next pop-up dialog box, choose either **Select Gray** or **Select Red**, and select **Save**.</span></span>

1. <span data-ttu-id="53546-352">Para exibir sua guia, vá para a equipe ou chat onde você instalou a guia e selecione-a na barra de guias.</span><span class="sxs-lookup"><span data-stu-id="53546-352">To view your tab, go to the team or chat where you installed the tab, and select it from the tab bar.</span></span> <span data-ttu-id="53546-353">A página escolhida durante a configuração é exibida.</span><span class="sxs-lookup"><span data-stu-id="53546-353">The page that you chose during configuration is displayed.</span></span>

    ![Guia canal CARREGADO ASPNET](../../assets/images/tab-images/channeltabaspnetuploaded.png)

# <a name="aspnet-core-mvc"></a>[<span data-ttu-id="53546-355">ASP.NET Core MVC</span><span class="sxs-lookup"><span data-stu-id="53546-355">ASP.NET Core MVC</span></span>](#tab/aspnetcoremvc)

### <a name="create-a-custom-channel-or-group-tab-with-aspnet-core-mvc"></a><span data-ttu-id="53546-356">Criar um canal personalizado ou uma guia de grupo com ASP.NET Core MVC</span><span class="sxs-lookup"><span data-stu-id="53546-356">Create a custom channel or group tab with ASP.NET Core MVC</span></span>

<span data-ttu-id="53546-357">Você pode criar um canal personalizado ou uma guia de grupo usando C# e ASP.Net Core MVC.</span><span class="sxs-lookup"><span data-stu-id="53546-357">You can create a custom channel or group tab using C# and ASP.Net Core MVC.</span></span> <span data-ttu-id="53546-358">[O App Studio para Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) também é usado para finalizar o manifesto do aplicativo e implantar sua guia para Teams.</span><span class="sxs-lookup"><span data-stu-id="53546-358">[App Studio for Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) is also used to finalize your app manifest and deploy your tab to Teams.</span></span>

### <a name="prerequisites-for-custom-channel-or-group-tab"></a><span data-ttu-id="53546-359">Pré-requisitos para canal personalizado ou guia grupo</span><span class="sxs-lookup"><span data-stu-id="53546-359">Prerequisites for custom channel or group tab</span></span>

- <span data-ttu-id="53546-360">Você deve ter um locatário Microsoft 365 e uma equipe configurada com **Permitir o carregamento de aplicativos personalizados** habilitados.</span><span class="sxs-lookup"><span data-stu-id="53546-360">You must have a Microsoft 365 tenant and a team configured with **Allow uploading custom apps** enabled.</span></span> <span data-ttu-id="53546-361">Para obter mais informações, [consulte prepare your Office 365 tenant](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span><span class="sxs-lookup"><span data-stu-id="53546-361">For more information, see [prepare your Office 365 tenant](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="53546-362">Se você não tiver uma conta Microsoft 365, poderá inscrever-se para uma assinatura gratuita por meio do [Programa de Desenvolvedores da Microsoft.](https://developer.microsoft.com/en-us/microsoft-365/dev-program)</span><span class="sxs-lookup"><span data-stu-id="53546-362">If you do not currently have a Microsoft 365 account, you can sign up for a free subscription through the [Microsoft Developer Program](https://developer.microsoft.com/en-us/microsoft-365/dev-program).</span></span> <span data-ttu-id="53546-363">A assinatura permanece ativa desde que você a use para desenvolvimento contínuo.</span><span class="sxs-lookup"><span data-stu-id="53546-363">The subscription remains active as long as you are using it for ongoing development.</span></span>

- <span data-ttu-id="53546-364">Use o App Studio para importar seu aplicativo para Teams.</span><span class="sxs-lookup"><span data-stu-id="53546-364">Use App Studio to import your application to Teams.</span></span> <span data-ttu-id="53546-365">Para instalar o App Studio, selecione **Aplicativo** da Loja de Aplicativos no canto inferior esquerdo do aplicativo Teams ![ e ](~/assets/images/tab-images/storeApp.png) pesquise **por App Studio**.</span><span class="sxs-lookup"><span data-stu-id="53546-365">To install App Studio, select **Apps** ![Store App](~/assets/images/tab-images/storeApp.png) at the lower left corner of the Teams app, and search for **App Studio**.</span></span> <span data-ttu-id="53546-366">Depois de encontrar o azulejo, selecione-o e escolha **Adicionar** na caixa de diálogo pop-up para instalá-lo.</span><span class="sxs-lookup"><span data-stu-id="53546-366">After you find the tile, select it and choose **Add** in the pop-up dialog box to install it.</span></span>

<span data-ttu-id="53546-367">Além disso, este projeto exige que você tenha o seguinte instalado em seu ambiente de desenvolvimento:</span><span class="sxs-lookup"><span data-stu-id="53546-367">In addition, this project requires that you have the following installed in your development environment:</span></span>

- <span data-ttu-id="53546-368">A versão atual do Visual Studio IDE com a carga de trabalho de desenvolvimento entre **plataformas .NET CORE** instalada.</span><span class="sxs-lookup"><span data-stu-id="53546-368">The current version of the Visual Studio IDE with the **.NET CORE cross-platform development** workload installed.</span></span> <span data-ttu-id="53546-369">Se você ainda não tiver Visual Studio, poderá baixar e instalar a versão Microsoft Visual Studio Community [versão](https://visualstudio.microsoft.com/downloads) mais recente gratuitamente.</span><span class="sxs-lookup"><span data-stu-id="53546-369">If you do not already have Visual Studio, you can download and install the latest [Microsoft Visual Studio Community](https://visualstudio.microsoft.com/downloads) version for free.</span></span>

- <span data-ttu-id="53546-370">A [ferramenta proxy reverso ngrok.](https://ngrok.com)</span><span class="sxs-lookup"><span data-stu-id="53546-370">The [ngrok](https://ngrok.com) reverse proxy tool.</span></span> <span data-ttu-id="53546-371">Use ngrok para criar um túnel para os pontos de extremidade HTTPS do servidor Web em execução localmente.</span><span class="sxs-lookup"><span data-stu-id="53546-371">Use ngrok to create a tunnel to your locally running web server's publicly-available HTTPS endpoints.</span></span> <span data-ttu-id="53546-372">Você pode [baixar ngrok](https://ngrok.com/download).</span><span class="sxs-lookup"><span data-stu-id="53546-372">You can [download ngrok](https://ngrok.com/download).</span></span>

### <a name="get-the-source-code"></a><span data-ttu-id="53546-373">Obter o código-fonte</span><span class="sxs-lookup"><span data-stu-id="53546-373">Get the source code</span></span>

<span data-ttu-id="53546-374">Em um prompt de comando, crie um novo diretório para seu projeto de guia.</span><span class="sxs-lookup"><span data-stu-id="53546-374">At a command prompt, create a new directory for your tab project.</span></span> <span data-ttu-id="53546-375">Um projeto [simples de Guia de Grupo](https://github.com/OfficeDev/microsoft-teams-sample-tabs/tree/master/ChannelGroupTabMVC) de Canal é fornecido para você começar.</span><span class="sxs-lookup"><span data-stu-id="53546-375">A simple [Channel Group Tab](https://github.com/OfficeDev/microsoft-teams-sample-tabs/tree/master/ChannelGroupTabMVC) project is provided to get you started.</span></span> <span data-ttu-id="53546-376">Clone o repositório de exemplo em seu novo diretório usando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="53546-376">Clone the sample repository into your new directory using the following command:</span></span>

```bash
git clone https://github.com/OfficeDev/microsoft-teams-sample-tabs.git
```

<span data-ttu-id="53546-377">Como alternativa, você pode recuperar o código-fonte baixando a pasta zip e extraindo os arquivos.</span><span class="sxs-lookup"><span data-stu-id="53546-377">Alternately, you can retrieve the source code by downloading the zip folder and extracting the files.</span></span>

<span data-ttu-id="53546-378">**Para criar e executar o projeto de guia**</span><span class="sxs-lookup"><span data-stu-id="53546-378">**To build and run the tab project**</span></span>

1. <span data-ttu-id="53546-379">Depois de ter o código-fonte, vá para Visual Studio e selecione **Abrir um projeto ou solução**.</span><span class="sxs-lookup"><span data-stu-id="53546-379">After you have the source code, go to Visual Studio and select **Open a project or solution**.</span></span>
1. <span data-ttu-id="53546-380">Vá para o diretório de aplicativos de tabulação e abra **ChannelGroupTabMVC.sln**.</span><span class="sxs-lookup"><span data-stu-id="53546-380">Go to the tab application directory and open **ChannelGroupTabMVC.sln**.</span></span>
1. <span data-ttu-id="53546-381">Para criar e executar seu aplicativo, pressione **F5** ou escolha **Iniciar Depuração** no menu **Depurar.**</span><span class="sxs-lookup"><span data-stu-id="53546-381">To build and run your application, press **F5** or choose **Start Debugging** from the **Debug** menu.</span></span>
1. <span data-ttu-id="53546-382">Em um navegador, navegue até as SEGUINTES URLs e verifique se o aplicativo foi carregado corretamente:</span><span class="sxs-lookup"><span data-stu-id="53546-382">In a browser, navigate to the following URLs and verify that the application loaded properly:</span></span>

    - `http://localhost:44360`
    - `http://localhost:44360/privacy`
    - `http://localhost:44360/tou`

### <a name="review-the-source-code"></a><span data-ttu-id="53546-383">Revisar o código-fonte</span><span class="sxs-lookup"><span data-stu-id="53546-383">Review the source code</span></span>

#### <a name="startupcs"></a><span data-ttu-id="53546-384">Startup.cs</span><span class="sxs-lookup"><span data-stu-id="53546-384">Startup.cs</span></span>

<span data-ttu-id="53546-385">Esse projeto foi criado a partir de um modelo vazio do Aplicativo Web 2.2 do ASP.NET Core 2.2 com a caixa de seleção Avançado - Configurar para **HTTPS** selecionada na instalação.</span><span class="sxs-lookup"><span data-stu-id="53546-385">This project was created from an ASP.NET Core 2.2 Web Application empty template with the **Advanced - Configure for HTTPS** check box selected at setup.</span></span> <span data-ttu-id="53546-386">Os serviços MVC são registrados pelo método da estrutura de injeção de `ConfigureServices()` dependência.</span><span class="sxs-lookup"><span data-stu-id="53546-386">The MVC services are registered by the dependency injection framework's `ConfigureServices()` method.</span></span> <span data-ttu-id="53546-387">Além disso, o modelo vazio não habilita o serviço de conteúdo estático por padrão, portanto, o middleware de arquivos estáticos é adicionado ao método usando `Configure()` o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="53546-387">Additionally, the empty template does not enable serving static content by default, so the static files middleware is added to the `Configure()` method using the following code:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
  {
    services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_2);
  }
public void Configure(IApplicationBuilder app)
  {
    app.UseStaticFiles();
    app.UseMvc();
  }
```

#### <a name="wwwroot-folder"></a><span data-ttu-id="53546-388">pasta wwwroot</span><span class="sxs-lookup"><span data-stu-id="53546-388">wwwroot folder</span></span>

<span data-ttu-id="53546-389">Em ASP.NET Core, a pasta raiz da Web é onde o aplicativo procura arquivos estáticos.</span><span class="sxs-lookup"><span data-stu-id="53546-389">In ASP.NET Core, the web root folder is where the application looks for static files.</span></span>

#### <a name="appmanifest-folder"></a><span data-ttu-id="53546-390">Pasta AppManifest</span><span class="sxs-lookup"><span data-stu-id="53546-390">AppManifest folder</span></span>

<span data-ttu-id="53546-391">Esta pasta contém os seguintes arquivos de pacote de aplicativos necessários:</span><span class="sxs-lookup"><span data-stu-id="53546-391">This folder contains the following required app package files:</span></span>

- <span data-ttu-id="53546-392">Um **ícone de cor completo** medindo 192 x 192 pixels.</span><span class="sxs-lookup"><span data-stu-id="53546-392">A **full color icon** measuring 192 x 192 pixels.</span></span>
- <span data-ttu-id="53546-393">Um **ícone de contorno transparente** medindo 32 x 32 pixels.</span><span class="sxs-lookup"><span data-stu-id="53546-393">A **transparent outline icon** measuring 32 x 32 pixels.</span></span>
- <span data-ttu-id="53546-394">Um **manifest.json** que especifica os atributos do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="53546-394">A **manifest.json** file that specifies the attributes of your app.</span></span>

<span data-ttu-id="53546-395">Esses arquivos precisam ser cortados em um pacote de aplicativos para uso ao carregar sua guia para Teams.</span><span class="sxs-lookup"><span data-stu-id="53546-395">These files need to be zipped in an app package for use in uploading your tab to Teams.</span></span>

#### <a name="csproj"></a><span data-ttu-id="53546-396">.csproj</span><span class="sxs-lookup"><span data-stu-id="53546-396">.csproj</span></span>

<span data-ttu-id="53546-397">Na janela Visual Studio Do Explorador de Soluções, clique com o botão direito do mouse no projeto e selecione **Editar Project Arquivo**.</span><span class="sxs-lookup"><span data-stu-id="53546-397">In the Visual Studio Solution Explorer window, right-click on the project and select **Edit Project File**.</span></span> <span data-ttu-id="53546-398">No final do arquivo, você vê o seguinte código que cria e atualiza sua pasta zip quando o aplicativo é construído:</span><span class="sxs-lookup"><span data-stu-id="53546-398">At the end of the file you see the following code that creates and updates your zip folder when the application builds:</span></span>

```xml
<PropertyGroup>
    <PostBuildEvent>powershell.exe Compress-Archive -Path \"$(ProjectDir)AppManifest\*\" -DestinationPath \"$(TargetDir)tab.zip\" -Force</PostBuildEvent>
  </PropertyGroup>

  <ItemGroup>
    <EmbeddedResource Include="AppManifest\icon-outline.png">
      <CopyToOutputDirectory>Always</CopyToOutputDirectory>
    </EmbeddedResource>
    <EmbeddedResource Include="AppManifest\icon-color.png">
      <CopyToOutputDirectory>Always</CopyToOutputDirectory>
    </EmbeddedResource>
    <EmbeddedResource Include="AppManifest\manifest.json">
      <CopyToOutputDirectory>Always</CopyToOutputDirectory>
    </EmbeddedResource>
  </ItemGroup>
```

#### <a name="models"></a><span data-ttu-id="53546-399">Modelos</span><span class="sxs-lookup"><span data-stu-id="53546-399">Models</span></span>

<span data-ttu-id="53546-400">**ChannelGroup.cs** apresenta um objeto Message e métodos que serão chamados dos controladores durante a configuração.</span><span class="sxs-lookup"><span data-stu-id="53546-400">**ChannelGroup.cs** presents a Message object and methods that will be called from the controllers during configuration.</span></span>

#### <a name="views"></a><span data-ttu-id="53546-401">Modos de exibição</span><span class="sxs-lookup"><span data-stu-id="53546-401">Views</span></span>

<span data-ttu-id="53546-402">Estas são as diferentes exibições em ASP.NET Core MVC:</span><span class="sxs-lookup"><span data-stu-id="53546-402">These are the different views in ASP.NET Core MVC:</span></span>

* <span data-ttu-id="53546-403">Home: ASP.NET Core trata arquivos chamados **Index** como o padrão ou home page do site.</span><span class="sxs-lookup"><span data-stu-id="53546-403">Home: ASP.NET Core treats files called **Index** as the default or home page for the site.</span></span> <span data-ttu-id="53546-404">Quando a URL do navegador aponta para a raiz do site, **Index.cshtml** será exibida como a home page do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="53546-404">When your browser URL points to the root of the site, **Index.cshtml** will be displayed as the home page for your application.</span></span>

* <span data-ttu-id="53546-405">Compartilhado: a marcação de exibição **parcial _Layout.cshtml** contém a estrutura geral da página do aplicativo e elementos visuais compartilhados.</span><span class="sxs-lookup"><span data-stu-id="53546-405">Shared: The partial view markup **_Layout.cshtml** contains the application's overall page structure and shared visual elements.</span></span> <span data-ttu-id="53546-406">Ele também fará referência à biblioteca Teams.</span><span class="sxs-lookup"><span data-stu-id="53546-406">It will also reference the Teams Library.</span></span>

#### <a name="controllers"></a><span data-ttu-id="53546-407">Controladores</span><span class="sxs-lookup"><span data-stu-id="53546-407">Controllers</span></span>

<span data-ttu-id="53546-408">Os controladores usam a `ViewBag` propriedade para transferir valores dinamicamente para os exibições.</span><span class="sxs-lookup"><span data-stu-id="53546-408">The controllers use the `ViewBag` property to transfer values dynamically to the views.</span></span>

[!INCLUDE [dotnet-ngrok-intro](~/includes/tabs/dotnet-ngrok-intro.md)]

* <span data-ttu-id="53546-409">Abra um prompt de comando na raiz do diretório do projeto e execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="53546-409">Open a command prompt in the root of your project directory and run the following command:</span></span>

    ```bash
    ngrok http https://localhost:443560 -host-header="localhost:44360"
    ```

* <span data-ttu-id="53546-410">O Ngrok ouvirá as solicitações da Internet e as encaminhará para seu aplicativo quando estiver sendo executado na porta 44355.</span><span class="sxs-lookup"><span data-stu-id="53546-410">Ngrok will listen to requests from the internet and will route them to your application when it is running on port 44355.</span></span> <span data-ttu-id="53546-411">Deve parecer `https://y8rCgT2b.ngrok.io/` onde **y8rCgT2b** é substituído pela URL HTTPS alfanumérico ngrok.</span><span class="sxs-lookup"><span data-stu-id="53546-411">It should resemble `https://y8rCgT2b.ngrok.io/` where **y8rCgT2b** is replaced by your ngrok alpha-numeric HTTPS URL.</span></span>

* <span data-ttu-id="53546-412">Certifique-se de manter o prompt de comando com o ngrok em execução e anote a URL.</span><span class="sxs-lookup"><span data-stu-id="53546-412">Ensure that you keep the command prompt with ngrok running and make a note of the URL.</span></span>

### <a name="update-your-application"></a><span data-ttu-id="53546-413">Atualizar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="53546-413">Update your application</span></span>

<span data-ttu-id="53546-414">Em **Tab.cshtml,** o aplicativo apresenta ao usuário dois botões de opção para exibir a guia com um ícone vermelho ou cinza.</span><span class="sxs-lookup"><span data-stu-id="53546-414">Within **Tab.cshtml** the application presents the user with two option buttons for displaying the tab with either a red or gray icon.</span></span> <span data-ttu-id="53546-415">Escolher o **botão Selecionar Cinza** ou Selecionar **Vermelho,** dispara ou , respectivamente, define e habilita o botão Salvar `saveGray()` `saveRed()` na página de `settings.setValidityState(true)` configuração. </span><span class="sxs-lookup"><span data-stu-id="53546-415">Choosing the **Select Gray** or **Select Red** button, triggers `saveGray()` or `saveRed()`, respectively, sets `settings.setValidityState(true)`, and enables the **Save** button on the configuration page.</span></span> <span data-ttu-id="53546-416">Esse código permite Teams que você concluiu os requisitos de configuração e que a instalação pode continuar.</span><span class="sxs-lookup"><span data-stu-id="53546-416">This code lets Teams know that you have completed the configuration requirements and the installation can proceed.</span></span> <span data-ttu-id="53546-417">Ao salvar, os parâmetros de `settings.setSettings` são definidos.</span><span class="sxs-lookup"><span data-stu-id="53546-417">On save, the parameters of `settings.setSettings` are set.</span></span> <span data-ttu-id="53546-418">Por fim, `saveEvent.notifySuccess()` é chamado para indicar que a URL de conteúdo foi resolvida com êxito.</span><span class="sxs-lookup"><span data-stu-id="53546-418">Finally, `saveEvent.notifySuccess()` is called to indicate that the content URL has been successfully resolved.</span></span>

[!INCLUDE [dotnet-update-app](~/includes/tabs/dotnet-update-chan-grp-app.md)]

---

## <a name="see-also"></a><span data-ttu-id="53546-419">Confira também</span><span class="sxs-lookup"><span data-stu-id="53546-419">See also</span></span>

* [<span data-ttu-id="53546-420">Teams guias</span><span class="sxs-lookup"><span data-stu-id="53546-420">Teams tabs</span></span>](~/tabs/what-are-tabs.md)
* [<span data-ttu-id="53546-421">Criar uma guia pessoal</span><span class="sxs-lookup"><span data-stu-id="53546-421">Create a personal tab</span></span>](~/tabs/how-to/create-personal-tab.md)
* [<span data-ttu-id="53546-422">Guias em dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="53546-422">Tabs on mobile</span></span>](~/tabs/design/tabs-mobile.md)
* [<span data-ttu-id="53546-423">Criar guias com Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="53546-423">Build tabs with Adaptive Cards</span></span>](~/tabs/how-to/build-adaptive-card-tabs.md)

## <a name="next-step"></a><span data-ttu-id="53546-424">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="53546-424">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="53546-425">Criar uma página de conteúdo</span><span class="sxs-lookup"><span data-stu-id="53546-425">Create a content page</span></span>](~/tabs/how-to/create-tab-pages/content-page.md)
