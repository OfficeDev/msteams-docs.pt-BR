---
title: Criar uma guia pessoal
author: laujan
description: Um guia de início rápido para criar uma guia pessoal com o Gerador Yeoman para Microsoft Teams.
localization_priority: Normal
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: 47ed3027f936366964871733e78c7a43851ffb99
ms.sourcegitcommit: 85a52119df6c4cb4536572e6d2e7407f0e5e8a23
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2021
ms.locfileid: "53179821"
---
# <a name="create-a-personal-tab"></a><span data-ttu-id="0f23f-103">Criar uma guia pessoal</span><span class="sxs-lookup"><span data-stu-id="0f23f-103">Create a personal tab</span></span>

## <a name="create-a-custom-personal-tab"></a><span data-ttu-id="0f23f-104">Criar uma guia pessoal personalizada</span><span class="sxs-lookup"><span data-stu-id="0f23f-104">Create a custom personal tab</span></span>

<span data-ttu-id="0f23f-105">Você pode criar uma guia pessoal usando Node.js e o Gerador Yeoman, ASP.NET Core ou ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="0f23f-105">You can create a personal tab using Node.js and the Yeoman Generator, ASP.NET Core, or ASP.NET Core MVC.</span></span>

# <a name="nodejs"></a>[<span data-ttu-id="0f23f-106">Node.js</span><span class="sxs-lookup"><span data-stu-id="0f23f-106">Node.js</span></span>](#tab/nodejs)

### <a name="create-a-custom-personal-tab-using-nodejs-and-the-yeoman-generator"></a><span data-ttu-id="0f23f-107">Criar uma guia pessoal personalizada usando Node.js e o Gerador Yeoman</span><span class="sxs-lookup"><span data-stu-id="0f23f-107">Create a custom personal tab using Node.js and the Yeoman Generator</span></span>

> [!NOTE]
> <span data-ttu-id="0f23f-108">Este artigo segue as etapas descritas na [com](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) build do seu primeiro wiki de aplicativo Microsoft Teams encontrado no repositório do Microsoft OfficeDev GitHub.</span><span class="sxs-lookup"><span data-stu-id="0f23f-108">This article follows the steps outlined in the [build your first Microsoft Teams app](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) Wiki found in the Microsoft OfficeDev GitHub repository.</span></span>

<span data-ttu-id="0f23f-109">Você pode criar uma guia pessoal personalizada usando o [Teams do Yeoman](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App).</span><span class="sxs-lookup"><span data-stu-id="0f23f-109">You can create a custom personal tab using the [Teams Yeoman generator](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App).</span></span> <span data-ttu-id="0f23f-110">O aplicativo também é carregado para Teams.</span><span class="sxs-lookup"><span data-stu-id="0f23f-110">The application is also uploaded to Teams.</span></span>

### <a name="prerequisites-for-teams-apps"></a><span data-ttu-id="0f23f-111">Pré-requisitos para Teams aplicativos</span><span class="sxs-lookup"><span data-stu-id="0f23f-111">Prerequisites for Teams apps</span></span>

<span data-ttu-id="0f23f-112">Você deve ter uma compreensão dos seguintes pré-requisitos:</span><span class="sxs-lookup"><span data-stu-id="0f23f-112">You must have an understanding of the following prerequisites:</span></span>

- <span data-ttu-id="0f23f-113">Você deve ter um locatário Office 365 e uma equipe configurada com **Permitir o carregamento de aplicativos personalizados** habilitados.</span><span class="sxs-lookup"><span data-stu-id="0f23f-113">You must have an Office 365 tenant and a team configured with **Allow uploading custom apps** enabled.</span></span> <span data-ttu-id="0f23f-114">Para obter mais informações, [consulte prepare your Office 365 tenant](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span><span class="sxs-lookup"><span data-stu-id="0f23f-114">For more information, see [prepare your Office 365 tenant](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="0f23f-115">Se você não tiver uma conta Office 365, poderá inscrever-se para uma assinatura gratuita por meio do programa Office 365 Desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="0f23f-115">If you do not have an Office 365 account, you can sign up for a free subscription through the Office 365 Developer Program.</span></span> <span data-ttu-id="0f23f-116">A assinatura permanece ativa desde que você a use para desenvolvimento contínuo.</span><span class="sxs-lookup"><span data-stu-id="0f23f-116">The subscription remains active as long as you are using it for ongoing development.</span></span> <span data-ttu-id="0f23f-117">Consulte [welcome to the Office 365 Developer Program](/office/developer-program/microsoft-365-developer-program).</span><span class="sxs-lookup"><span data-stu-id="0f23f-117">See [welcome to the Office 365 Developer Program](/office/developer-program/microsoft-365-developer-program).</span></span>

<span data-ttu-id="0f23f-118">Além disso, este projeto exige que você tenha o seguinte instalado em seu ambiente de desenvolvimento:</span><span class="sxs-lookup"><span data-stu-id="0f23f-118">In addition, this project requires that you have the following installed in your development environment:</span></span>

- <span data-ttu-id="0f23f-119">Qualquer editor de texto ou IDE.</span><span class="sxs-lookup"><span data-stu-id="0f23f-119">Any text editor or IDE.</span></span> <span data-ttu-id="0f23f-120">Você pode instalar e usar [Visual Studio Code](https://code.visualstudio.com/download) gratuitamente.</span><span class="sxs-lookup"><span data-stu-id="0f23f-120">You can install and use [Visual Studio Code](https://code.visualstudio.com/download) for free.</span></span>

- <span data-ttu-id="0f23f-121">[Node.js/npm](https://nodejs.org/en/).</span><span class="sxs-lookup"><span data-stu-id="0f23f-121">[Node.js/npm](https://nodejs.org/en/).</span></span> <span data-ttu-id="0f23f-122">Use a versão LTS mais recente.</span><span class="sxs-lookup"><span data-stu-id="0f23f-122">Use the latest LTS version.</span></span> <span data-ttu-id="0f23f-123">O nó Gerenciador de Pacotes (npm) é instalado em seu sistema com a instalação de Node.js.</span><span class="sxs-lookup"><span data-stu-id="0f23f-123">The Node Package Manager (npm) is installed in your system with the installation of Node.js.</span></span>

- <span data-ttu-id="0f23f-124">Depois de instalar o Node.js, instale os pacotes [Yeoman](https://yeoman.io/) e [gulp-cli](https://www.npmjs.com/package/gulp-cli) inserindo o seguinte no prompt de comando:</span><span class="sxs-lookup"><span data-stu-id="0f23f-124">After you have successfully installed Node.js, install the [Yeoman](https://yeoman.io/) and [gulp-cli](https://www.npmjs.com/package/gulp-cli) packages by entering the following in your command prompt:</span></span>

    ```bash
    npm install yo gulp-cli --global
    ```

- <span data-ttu-id="0f23f-125">Instale o Microsoft Teams aplicativos inserindo o seguinte no prompt de comando:</span><span class="sxs-lookup"><span data-stu-id="0f23f-125">Install the Microsoft Teams Apps generator by entering the following in your command prompt:</span></span>

    ```bash
    npm install generator-teams --global
    ```

### <a name="generate-your-project"></a><span data-ttu-id="0f23f-126">Gerar seu projeto</span><span class="sxs-lookup"><span data-stu-id="0f23f-126">Generate your project</span></span>

<span data-ttu-id="0f23f-127">**Para gerar seu projeto**</span><span class="sxs-lookup"><span data-stu-id="0f23f-127">**To generate your project**</span></span>

1. <span data-ttu-id="0f23f-128">Em um prompt de comando, crie um novo diretório para seu projeto de guia.</span><span class="sxs-lookup"><span data-stu-id="0f23f-128">At a command prompt, create a new directory for your tab project.</span></span>

1. <span data-ttu-id="0f23f-129">Para iniciar o gerador, vá para o novo diretório e insira o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="0f23f-129">To start the generator, go to your new directory and enter the following command:</span></span>

    ```bash
    yo teams
    ```

1. <span data-ttu-id="0f23f-130">Em seguida, forneça uma série de valores usados no arquivomanifest.js **no** aplicativo:</span><span class="sxs-lookup"><span data-stu-id="0f23f-130">Next, provide a series of values that are used in your application's **manifest.json** file:</span></span>

    ![captura de tela de abertura do gerador](/microsoftteams/platform/assets/images/tab-images/teamsTabScreenshot.PNG)

    <span data-ttu-id="0f23f-132">**Qual é o nome da solução?**</span><span class="sxs-lookup"><span data-stu-id="0f23f-132">**What is your solution name?**</span></span>

    <span data-ttu-id="0f23f-133">Esse é o nome do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="0f23f-133">This is your project name.</span></span> <span data-ttu-id="0f23f-134">Você pode aceitar o nome sugerido selecionando a **tecla Enter.**</span><span class="sxs-lookup"><span data-stu-id="0f23f-134">You can accept the suggested name by selecting the **Enter** key.</span></span>

    <span data-ttu-id="0f23f-135">**Onde você deseja colocar os arquivos?**</span><span class="sxs-lookup"><span data-stu-id="0f23f-135">**Where do you want to place the files?**</span></span>

    <span data-ttu-id="0f23f-136">No momento, você está no diretório do projeto.</span><span class="sxs-lookup"><span data-stu-id="0f23f-136">You are currently in your project directory.</span></span> <span data-ttu-id="0f23f-137">Selecione **Inserir**.</span><span class="sxs-lookup"><span data-stu-id="0f23f-137">Select **Enter**.</span></span>

    <span data-ttu-id="0f23f-138">**Título do seu projeto Microsoft Teams aplicativo?**</span><span class="sxs-lookup"><span data-stu-id="0f23f-138">**Title of your Microsoft Teams app project?**</span></span>

    <span data-ttu-id="0f23f-139">Esse é o nome do pacote do aplicativo e será usado no manifesto e na descrição do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0f23f-139">This is your app package name and will be used in the app manifest and description.</span></span> <span data-ttu-id="0f23f-140">Insira um título ou selecione **Enter** para aceitar o nome padrão.</span><span class="sxs-lookup"><span data-stu-id="0f23f-140">Enter a title or select **Enter** to accept the default name.</span></span>

    <span data-ttu-id="0f23f-141">**Seu nome (empresa) ? (máx. 32 caracteres)**</span><span class="sxs-lookup"><span data-stu-id="0f23f-141">**Your (company) name? (max 32 characters)**</span></span>

    <span data-ttu-id="0f23f-142">O nome da empresa será usado no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0f23f-142">Your company name will be used in the app manifest.</span></span> <span data-ttu-id="0f23f-143">Insira um nome da empresa ou selecione **Enter** para aceitar o nome padrão.</span><span class="sxs-lookup"><span data-stu-id="0f23f-143">Enter a company name or select **Enter** to accept the default name.</span></span>

    <span data-ttu-id="0f23f-144">**Qual versão de manifesto você gostaria de usar?**</span><span class="sxs-lookup"><span data-stu-id="0f23f-144">**Which manifest version would you like to use?**</span></span>

    <span data-ttu-id="0f23f-145">Selecione o esquema padrão.</span><span class="sxs-lookup"><span data-stu-id="0f23f-145">Select the default schema.</span></span>

    <span data-ttu-id="0f23f-146">**Scaffolding rápido? (Y/n)**</span><span class="sxs-lookup"><span data-stu-id="0f23f-146">**Quick scaffolding? (Y/n)**</span></span>

    <span data-ttu-id="0f23f-147">O padrão é sim; insira **n** para inserir sua ID do Microsoft Partner.</span><span class="sxs-lookup"><span data-stu-id="0f23f-147">The default is yes; enter **n** to enter your Microsoft Partner Id.</span></span>

    <span data-ttu-id="0f23f-148">**Insira sua ID do Microsoft Partner, se você tiver uma? (Deixe em branco para ignorar)**</span><span class="sxs-lookup"><span data-stu-id="0f23f-148">**Enter your Microsoft Partner Id, if you have one? (Leave blank to skip)**</span></span>

    <span data-ttu-id="0f23f-149">Esse campo não é obrigatório e só deve ser usado se você já faz parte da [Rede de Parceiros da Microsoft.](https://partner.microsoft.com)</span><span class="sxs-lookup"><span data-stu-id="0f23f-149">This field is not required and should only be used if you are already part of the [Microsoft Partner Network](https://partner.microsoft.com).</span></span>

    <span data-ttu-id="0f23f-150">**O que você deseja adicionar ao seu projeto?**</span><span class="sxs-lookup"><span data-stu-id="0f23f-150">**What do you want to add to your project?**</span></span>

    <span data-ttu-id="0f23f-151">Selecione **( ) Uma &ast; guia**.</span><span class="sxs-lookup"><span data-stu-id="0f23f-151">Select **( &ast; ) A Tab**.</span></span>

    <span data-ttu-id="0f23f-152">**A URL onde você hospedará essa solução?**</span><span class="sxs-lookup"><span data-stu-id="0f23f-152">**The URL where you will host this solution?**</span></span>

    <span data-ttu-id="0f23f-153">Por padrão, o gerador sugere uma URL de Sites do Azure.</span><span class="sxs-lookup"><span data-stu-id="0f23f-153">By default the generator suggests an Azure Web Sites URL.</span></span> <span data-ttu-id="0f23f-154">Você só está testando seu aplicativo localmente, portanto, uma URL válida não é necessária.</span><span class="sxs-lookup"><span data-stu-id="0f23f-154">You are only testing your app locally, therefore, a valid URL is not necessary.</span></span>

    <span data-ttu-id="0f23f-155">**Você gostaria de mostrar um indicador de carregamento quando seu aplicativo/guia é carregado?**</span><span class="sxs-lookup"><span data-stu-id="0f23f-155">**Would you like show a loading indicator when your app/tab loads?**</span></span>

    <span data-ttu-id="0f23f-156">Escolha **não incluir** um indicador de carregamento quando seu aplicativo ou guia for carregado.</span><span class="sxs-lookup"><span data-stu-id="0f23f-156">Choose **not** to include a loading indicator when your app or tab loads.</span></span> <span data-ttu-id="0f23f-157">O padrão é não, digite **n**.</span><span class="sxs-lookup"><span data-stu-id="0f23f-157">The default is no, enter **n**.</span></span>

    <span data-ttu-id="0f23f-158">**Você gostaria que aplicativos pessoais fossem renderizados sem uma barra de texto de tabulação?**</span><span class="sxs-lookup"><span data-stu-id="0f23f-158">**Would you like personal apps to be rendered without a tab header-bar?**</span></span>

    <span data-ttu-id="0f23f-159">Escolha **não** incluir aplicativos pessoais a serem renderizados sem uma barra de header-bar de tabulação.</span><span class="sxs-lookup"><span data-stu-id="0f23f-159">Choose **not** to include personal apps to be rendered without a tab header-bar.</span></span> <span data-ttu-id="0f23f-160">O padrão é não, digite **n**.</span><span class="sxs-lookup"><span data-stu-id="0f23f-160">Default is no, enter **n**.</span></span>

    <span data-ttu-id="0f23f-161">**Você gostaria de incluir a estrutura de teste e testes iniciais? (y/N)**</span><span class="sxs-lookup"><span data-stu-id="0f23f-161">**Would you like to include Test framework and initial tests? (y/N)**</span></span>

    <span data-ttu-id="0f23f-162">Escolha **não** incluir uma estrutura de teste para este projeto.</span><span class="sxs-lookup"><span data-stu-id="0f23f-162">Choose **not** to include a test framework for this project.</span></span> <span data-ttu-id="0f23f-163">O padrão é sim, digite **n**.</span><span class="sxs-lookup"><span data-stu-id="0f23f-163">The default is yes, enter **n**.</span></span>

    <span data-ttu-id="0f23f-164">**Você gostaria de usar aplicativos do Azure Insights para telemetria? (y/N)**</span><span class="sxs-lookup"><span data-stu-id="0f23f-164">**Would you like to use Azure Applications Insights for telemetry? (y/N)**</span></span>

    <span data-ttu-id="0f23f-165">Escolha **não** incluir o [aplicativo Azure Insights](/azure/azure-monitor/app/app-insights-overview).</span><span class="sxs-lookup"><span data-stu-id="0f23f-165">Choose **not** to include [Azure Application Insights](/azure/azure-monitor/app/app-insights-overview).</span></span> <span data-ttu-id="0f23f-166">O padrão é não; enter **n**.</span><span class="sxs-lookup"><span data-stu-id="0f23f-166">The default is no; enter **n**.</span></span>

    <span data-ttu-id="0f23f-167">**Nome da guia padrão (máx. 16 caracteres)?**</span><span class="sxs-lookup"><span data-stu-id="0f23f-167">**Default Tab Name (max 16 characters)?**</span></span>

    <span data-ttu-id="0f23f-168">Nomeia sua guia. Esse nome de guia é usado em todo o seu projeto como um componente de caminho de arquivo ou URL.</span><span class="sxs-lookup"><span data-stu-id="0f23f-168">Name your tab. This tab name is used throughout your project as a file or URL path component.</span></span>

    <span data-ttu-id="0f23f-169">**Que tipo de Guia você gostaria de criar?**</span><span class="sxs-lookup"><span data-stu-id="0f23f-169">**What kind of Tab would you like to create?**</span></span>

    <span data-ttu-id="0f23f-170">Use as teclas de seta para selecionar **Pessoal (estático)**.</span><span class="sxs-lookup"><span data-stu-id="0f23f-170">Use the arrow keys to select **Personal (static)**.</span></span>

    <span data-ttu-id="0f23f-171">**Você precisa do suporte para o Microsoft Azure Active Directory com Login Único para a guia?**</span><span class="sxs-lookup"><span data-stu-id="0f23f-171">**Do you require Azure AD Single-Sign-On support for the tab?**</span></span>

    <span data-ttu-id="0f23f-172">Escolha **não** incluir o suporte ao Azure AD Single-Sign-On para a guia. O padrão é sim, digite **n**.</span><span class="sxs-lookup"><span data-stu-id="0f23f-172">Choose **not** to include Azure AD Single-Sign-On support for the tab. The default is yes, enter **n**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="0f23f-173">O componente de **caminho yourDefaultTabNameTab** é o valor que você inscrevia no gerador para Nome da Guia **Padrão** mais a **palavra Tab**.</span><span class="sxs-lookup"><span data-stu-id="0f23f-173">The path component **yourDefaultTabNameTab** is the value that you entered in the generator for **Default Tab Name** plus the word **Tab**.</span></span>
    >
    > <span data-ttu-id="0f23f-174">Por exemplo: DefaultTabName: **MyTab**  >  **/MyTabTab/**</span><span class="sxs-lookup"><span data-stu-id="0f23f-174">For example: DefaultTabName: **MyTab** > **/MyTabTab/**</span></span>

### <a name="add-a-personal-tab"></a><span data-ttu-id="0f23f-175">Adicionar uma guia pessoal</span><span class="sxs-lookup"><span data-stu-id="0f23f-175">Add a personal tab</span></span>

<span data-ttu-id="0f23f-176">**Para adicionar uma guia pessoal a esse aplicativo, crie uma página de conteúdo e atualize arquivos existentes**</span><span class="sxs-lookup"><span data-stu-id="0f23f-176">**To add a personal tab to this application, create a content page, and update existing files**</span></span>

1. <span data-ttu-id="0f23f-177">No editor de código, crie um novo arquivo HTML, **personal.html** e adicione a seguinte marcação:</span><span class="sxs-lookup"><span data-stu-id="0f23f-177">In your code editor, create a new HTML file, **personal.html** and add the following markup:</span></span>

    ```html
    <!DOCTYPE html>
    <html>
        <head>
            <meta charset="UTF-8">
            <title>
                <!-- Todo: add your a title here -->
            </title>
            <meta name="viewport" content="width=device-width, initial-scale=1.0">
            <!-- inject:css -->
            <!-- endinject -->
        </head>
            <body>
                <h1>Personal Tab</h1>
                <p><img src="/assets/icon.png"></p>
                <p>This is your personal tab!</p>
            </body>
    </html>
    ```

1. <span data-ttu-id="0f23f-178">Salve **personal.html** na pasta **web** do aplicativo no seguinte local:</span><span class="sxs-lookup"><span data-stu-id="0f23f-178">Save **personal.html** in your application's **web** folder in the following location:</span></span>

    ```bash
    ./src/app/web/<yourDefaultTabNameTab>/personal.html
    ```

1. <span data-ttu-id="0f23f-179">Abra **manifest.jsa partir** do seguinte local no editor de código:</span><span class="sxs-lookup"><span data-stu-id="0f23f-179">Open **manifest.json** from the following location in your code editor:</span></span>

    ```bash
    ./src/manifest/manifest.json/
    ```

1. <span data-ttu-id="0f23f-180">Adicione o seguinte à matriz `staticTabs` vazia ( ) e adicione o seguinte objeto `staticTabs":[]` JSON:</span><span class="sxs-lookup"><span data-stu-id="0f23f-180">Add the following to the empty `staticTabs` array (`staticTabs":[]`) and add the following JSON object:</span></span>

    ```json
    {
        "entityId": "personalTab",
        "name": "Personal Tab ",
        "contentUrl": "https://{{HOSTNAME}}/<yourDefaultTabNameTab>/personal.html",
        "websiteUrl": "https://{{HOSTNAME}}",
        "scopes": ["personal"]
    }
    ```

1. <span data-ttu-id="0f23f-181">Atualize **o componente de caminho contentURL** **yourDefaultTabNameTab** com o nome da guia real.</span><span class="sxs-lookup"><span data-stu-id="0f23f-181">Update the **contentURL** path component **yourDefaultTabNameTab** with your actual tab name.</span></span>

1. <span data-ttu-id="0f23f-182">Salve o arquivo **manifest.jsno** arquivo.</span><span class="sxs-lookup"><span data-stu-id="0f23f-182">Save the updated **manifest.json** file.</span></span>

1. <span data-ttu-id="0f23f-183">Para fornecer sua página de conteúdo em um IFrame, abra **Tab.ts** no editor de código do seguinte caminho:</span><span class="sxs-lookup"><span data-stu-id="0f23f-183">To provide your content page in an IFrame, open **Tab.ts** in your code editor from the following path:</span></span>

    ```bash
    ./src/app/<yourDefaultTabNameTab>/<yourDefaultTabNameTab>.ts
    ```

1. <span data-ttu-id="0f23f-184">Adicione o seguinte à lista de decoradores IFrame:</span><span class="sxs-lookup"><span data-stu-id="0f23f-184">Add the following to the list of IFrame decorators:</span></span>

    ```typescript
     @PreventIframe("/<yourDefaultAppName>TabNameTab>/personal.html")
    ```

1. <span data-ttu-id="0f23f-185">Salve o arquivo **Tab.ts** atualizado.</span><span class="sxs-lookup"><span data-stu-id="0f23f-185">Save the updated **Tab.ts** file.</span></span> <span data-ttu-id="0f23f-186">Seu código de tabulação está completo.</span><span class="sxs-lookup"><span data-stu-id="0f23f-186">Your tab code is complete.</span></span>

### <a name="build-and-run-your-application"></a><span data-ttu-id="0f23f-187">Criar e executar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="0f23f-187">Build and run your application</span></span>

<span data-ttu-id="0f23f-188">Em um prompt de comando, abra o diretório do projeto para concluir as próximas tarefas.</span><span class="sxs-lookup"><span data-stu-id="0f23f-188">At a command prompt, open your project directory to complete the next tasks.</span></span>

#### <a name="create-the-app-package"></a><span data-ttu-id="0f23f-189">Criar o pacote do aplicativo</span><span class="sxs-lookup"><span data-stu-id="0f23f-189">Create the app package</span></span>

<span data-ttu-id="0f23f-190">Você deve ter um pacote de aplicativos para testar sua guia Teams.</span><span class="sxs-lookup"><span data-stu-id="0f23f-190">You must have an app package to test your tab in Teams.</span></span> <span data-ttu-id="0f23f-191">É uma pasta zip que contém os seguintes arquivos necessários:</span><span class="sxs-lookup"><span data-stu-id="0f23f-191">It is a zip folder that contains the following required files:</span></span>

- <span data-ttu-id="0f23f-192">Um **ícone de cor completo** medindo 192 x 192 pixels.</span><span class="sxs-lookup"><span data-stu-id="0f23f-192">A **full color icon** measuring 192 x 192 pixels.</span></span>
- <span data-ttu-id="0f23f-193">Um **ícone de contorno transparente** medindo 32 x 32 pixels.</span><span class="sxs-lookup"><span data-stu-id="0f23f-193">A **transparent outline icon** measuring 32 x 32 pixels.</span></span>
- <span data-ttu-id="0f23f-194">Um **manifest.json** que especifica os atributos do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0f23f-194">A **manifest.json** file that specifies the attributes of your app.</span></span>

<span data-ttu-id="0f23f-195">O pacote é criado por meio de uma tarefa gulp que valida o manifest.jsno arquivo on e gera a pasta zip no **diretório ./package.**</span><span class="sxs-lookup"><span data-stu-id="0f23f-195">The package is created through a gulp task that validates the manifest.json file and generates the zip folder in the **./package directory**.</span></span> <span data-ttu-id="0f23f-196">No prompt de comando, insira o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="0f23f-196">In the command prompt, enter the following command:</span></span>

```bash
gulp manifest
```

#### <a name="build-your-application"></a><span data-ttu-id="0f23f-197">Criar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="0f23f-197">Build your application</span></span>

<span data-ttu-id="0f23f-198">O comando build transpila sua solução para a **pasta ./dist.**</span><span class="sxs-lookup"><span data-stu-id="0f23f-198">The build command transpiles your solution into the **./dist** folder.</span></span> <span data-ttu-id="0f23f-199">Insira o seguinte comando no prompt de comando:</span><span class="sxs-lookup"><span data-stu-id="0f23f-199">Enter the following command in the command prompt:</span></span>

```bash
gulp build
```

#### <a name="run-your-application-in-localhost"></a><span data-ttu-id="0f23f-200">Executar seu aplicativo no localhost</span><span class="sxs-lookup"><span data-stu-id="0f23f-200">Run your application in localhost</span></span>

1. <span data-ttu-id="0f23f-201">Inicie um servidor Web local inserindo o seguinte no prompt de comando:</span><span class="sxs-lookup"><span data-stu-id="0f23f-201">Start a local web server by entering the following in the command prompt:</span></span>

    ```bash
    gulp serve
    ```

1. <span data-ttu-id="0f23f-202">Insira no navegador, substitua pelo nome da guia e veja a home page do aplicativo, conforme `http://localhost:3007/<yourDefaultAppNameTab>/` mostrado na imagem a **<yourDefaultAppNameTab>** seguir:</span><span class="sxs-lookup"><span data-stu-id="0f23f-202">Enter `http://localhost:3007/<yourDefaultAppNameTab>/` in your browser, replace **<yourDefaultAppNameTab>** with your tab name, and view your application's home page as shown in the following image:</span></span>

    ![captura de tela da home page](~/assets/images/tab-images/homePage.png)

1. <span data-ttu-id="0f23f-204">Para exibir sua guia pessoal, vá para `http://localhost:3007/<yourDefaultAppNameTab>/personal.html` .</span><span class="sxs-lookup"><span data-stu-id="0f23f-204">To view your personal tab, go to `http://localhost:3007/<yourDefaultAppNameTab>/personal.html`.</span></span>

    >![Captura de tela de guia pessoal](/microsoftteams/platform/assets/images/tab-images/personalTab.PNG)

### <a name="establish-a-secure-tunnel-to-your-tab"></a><span data-ttu-id="0f23f-206">Estabelecer um túnel seguro para sua guia</span><span class="sxs-lookup"><span data-stu-id="0f23f-206">Establish a secure tunnel to your tab</span></span>

<span data-ttu-id="0f23f-207">Microsoft Teams é um produto baseado em nuvem e exige que o conteúdo da guia seja disponibilizado na nuvem usando pontos de extremidade HTTPS.</span><span class="sxs-lookup"><span data-stu-id="0f23f-207">Microsoft Teams is a cloud-based product and requires that your tab content be available from the cloud using HTTPS endpoints.</span></span> <span data-ttu-id="0f23f-208">Teams não permite hospedagem local.</span><span class="sxs-lookup"><span data-stu-id="0f23f-208">Teams does not allow local hosting.</span></span> <span data-ttu-id="0f23f-209">Você deve publicar sua guia em uma URL pública ou usar um proxy que exponha sua porta local a uma URL voltada para a Internet.</span><span class="sxs-lookup"><span data-stu-id="0f23f-209">You must either publish your tab to a public URL or use a proxy that exposes your local port to an internet-facing URL.</span></span>

<span data-ttu-id="0f23f-210">Para testar sua extensão de tabulação, você pode usar [ngrok](https://ngrok.com/docs), que é integrado a esse aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0f23f-210">To test your tab extension, you can use [ngrok](https://ngrok.com/docs), which is built into this application.</span></span> <span data-ttu-id="0f23f-211">O Ngrok é uma ferramenta de software de proxy reverso que cria um túnel para os pontos de extremidade HTTPS do servidor Web em execução localmente.</span><span class="sxs-lookup"><span data-stu-id="0f23f-211">Ngrok is a reverse proxy software tool that creates a tunnel to your locally running web server's publicly-available HTTPS endpoints.</span></span> <span data-ttu-id="0f23f-212">Os pontos de extremidade da Web do seu servidor estão disponíveis durante a sessão atual em seu computador.</span><span class="sxs-lookup"><span data-stu-id="0f23f-212">Your server's web endpoints are available during the current session on your computer.</span></span> <span data-ttu-id="0f23f-213">Quando o computador é desligado ou vai para o sono, o serviço não está mais disponível.</span><span class="sxs-lookup"><span data-stu-id="0f23f-213">When the computer is shut down or goes to sleep, the service is no longer available.</span></span>

<span data-ttu-id="0f23f-214">No prompt de comando, saia do localhost e insira o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0f23f-214">In your command prompt, exit localhost and enter the following:</span></span>

```bash
gulp ngrok-serve
```

> [!IMPORTANT]
> <span data-ttu-id="0f23f-215">Depois que sua guia for carregada para Microsoft Teams por meio do **ngrok** e salva com êxito, você poderá exibi-la em Teams até que sua sessão de túnel termine.</span><span class="sxs-lookup"><span data-stu-id="0f23f-215">After your tab has been uploaded to Microsoft Teams through **ngrok**, and successfully saved, you can view it in Teams until your tunnel session ends.</span></span>

### <a name="upload-your-application-to-teams"></a><span data-ttu-id="0f23f-216">Upload seu aplicativo para Teams</span><span class="sxs-lookup"><span data-stu-id="0f23f-216">Upload your application to Teams</span></span>

<span data-ttu-id="0f23f-217">**Para carregar seu aplicativo para Teams**</span><span class="sxs-lookup"><span data-stu-id="0f23f-217">**To upload your application to Teams**</span></span>

1. <span data-ttu-id="0f23f-218">Vá para Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="0f23f-218">Go to Microsoft Teams.</span></span> <span data-ttu-id="0f23f-219">Se você usar a [versão baseada na Web,](https://teams.microsoft.com) poderá inspecionar seu código front-end usando as ferramentas de desenvolvedor [do navegador.](~/tabs/how-to/developer-tools.md)</span><span class="sxs-lookup"><span data-stu-id="0f23f-219">If you use the [web-based version](https://teams.microsoft.com) you can inspect your front-end code using your browser's [developer tools](~/tabs/how-to/developer-tools.md).</span></span>
1. <span data-ttu-id="0f23f-220">No canto inferior esquerdo, selecione **Aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="0f23f-220">From the lower left corner, select **Apps**.</span></span>
1. <span data-ttu-id="0f23f-221">No canto inferior esquerdo, escolha **Upload um aplicativo personalizado.**</span><span class="sxs-lookup"><span data-stu-id="0f23f-221">From the lower left corner, choose **Upload a custom app**.</span></span>
1. <span data-ttu-id="0f23f-222">Vá para o diretório do projeto, navegue até a pasta **./package,** selecione a pasta zip e escolha **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="0f23f-222">Go to your project directory, browse to the **./package** folder, select the zip folder, and choose **Open**.</span></span>

    ![Adicionar sua guia pessoal](../../assets/images/tab-images/addingpersonaltab.png)

1. <span data-ttu-id="0f23f-224">Selecione **Adicionar** na caixa de diálogo pop-up.</span><span class="sxs-lookup"><span data-stu-id="0f23f-224">Select **Add** in the pop-up dialog box.</span></span> <span data-ttu-id="0f23f-225">Sua guia é carregada para Teams.</span><span class="sxs-lookup"><span data-stu-id="0f23f-225">Your tab is uploaded to Teams.</span></span>

    ![Guia pessoal carregado](../../assets/images/tab-images/personaltabuploaded.png)

### <a name="view-your-personal-tab"></a><span data-ttu-id="0f23f-227">Exibir sua guia pessoal</span><span class="sxs-lookup"><span data-stu-id="0f23f-227">View your personal tab</span></span>

<span data-ttu-id="0f23f-228">Na barra de navegação localizada à esquerda no Teams, selecione as releições &#x25CF;&#x25CF;&#x25CF; e escolha seu aplicativo na lista.</span><span class="sxs-lookup"><span data-stu-id="0f23f-228">In the navigation bar located at the far left in Teams, select the ellipses &#x25CF;&#x25CF;&#x25CF; and choose your app from the list.</span></span>

# <a name="aspnet-core"></a>[<span data-ttu-id="0f23f-229">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0f23f-229">ASP.NET Core</span></span>](#tab/aspnetcore)

### <a name="create-a-custom-personal-tab-using-aspnet-core"></a><span data-ttu-id="0f23f-230">Criar uma guia pessoal personalizada usando ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0f23f-230">Create a custom personal tab using ASP.NET Core</span></span>

<span data-ttu-id="0f23f-231">Você pode criar uma guia pessoal personalizada usando C# e ASP.NET Core Páginas de lâmina de corte.</span><span class="sxs-lookup"><span data-stu-id="0f23f-231">You can create a custom personal tab using C# and ASP.NET Core Razor pages.</span></span> <span data-ttu-id="0f23f-232">[O App Studio para Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) também é usado para finalizar o manifesto do aplicativo e implantar sua guia para Teams.</span><span class="sxs-lookup"><span data-stu-id="0f23f-232">[App Studio for Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) is also used to finalize your app manifest and deploy your tab to Teams.</span></span>

### <a name="prerequisites-for-personal-tab"></a><span data-ttu-id="0f23f-233">Pré-requisitos para guia pessoal</span><span class="sxs-lookup"><span data-stu-id="0f23f-233">Prerequisites for personal tab</span></span>

<span data-ttu-id="0f23f-234">Você deve ter uma compreensão dos seguintes pré-requisitos:</span><span class="sxs-lookup"><span data-stu-id="0f23f-234">You must have an understanding of the following prerequisites:</span></span>

- <span data-ttu-id="0f23f-235">Você deve ter um locatário Office 365 e uma equipe configurada com **Permitir o carregamento de aplicativos personalizados** habilitados.</span><span class="sxs-lookup"><span data-stu-id="0f23f-235">You must have an Office 365 tenant and a team configured with **Allow uploading custom apps** enabled.</span></span> <span data-ttu-id="0f23f-236">Para obter mais informações, [consulte prepare your Office 365 tenant](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span><span class="sxs-lookup"><span data-stu-id="0f23f-236">For more information, see [prepare your Office 365 tenant](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="0f23f-237">Se você não tiver uma conta Microsoft 365, poderá se inscrever para uma assinatura gratuita por meio do [Programa de Desenvolvedores da Microsoft.](https://developer.microsoft.com/en-us/microsoft-365/dev-program)</span><span class="sxs-lookup"><span data-stu-id="0f23f-237">If you do not have a Microsoft 365 account, you can sign up for a free subscription through the [Microsoft Developer Program](https://developer.microsoft.com/en-us/microsoft-365/dev-program).</span></span> <span data-ttu-id="0f23f-238">A assinatura permanece ativa desde que você a use para desenvolvimento contínuo.</span><span class="sxs-lookup"><span data-stu-id="0f23f-238">The subscription remains active as long as you are using it for ongoing development.</span></span>

- <span data-ttu-id="0f23f-239">Use o App Studio para importar seu aplicativo para Teams.</span><span class="sxs-lookup"><span data-stu-id="0f23f-239">Use App Studio to import your application to Teams.</span></span> <span data-ttu-id="0f23f-240">Para instalar o App Studio, selecione **Aplicativo** da Loja de Aplicativos no canto inferior esquerdo do aplicativo Teams ![ e ](~/assets/images/tab-images/storeApp.png) pesquise **por App Studio**.</span><span class="sxs-lookup"><span data-stu-id="0f23f-240">To install App Studio, select **Apps** ![Store App](~/assets/images/tab-images/storeApp.png) at the lower left corner of the Teams app, and search for **App Studio**.</span></span> <span data-ttu-id="0f23f-241">Depois de encontrar o azulejo, selecione-o e escolha **Adicionar** na caixa de diálogo pop-up para instalá-lo.</span><span class="sxs-lookup"><span data-stu-id="0f23f-241">After you find the tile, select it and choose **Add** in the pop-up dialog box to install it.</span></span>

<span data-ttu-id="0f23f-242">Além disso, este projeto exige que você tenha o seguinte instalado em seu ambiente de desenvolvimento:</span><span class="sxs-lookup"><span data-stu-id="0f23f-242">In addition, this project requires that you have the following installed in your development environment:</span></span>

- <span data-ttu-id="0f23f-243">A versão atual do Visual Studio IDE com a carga de trabalho de desenvolvimento entre **plataformas .NET CORE** instalada.</span><span class="sxs-lookup"><span data-stu-id="0f23f-243">The current version of the Visual Studio IDE with the **.NET CORE cross-platform development** workload installed.</span></span> <span data-ttu-id="0f23f-244">Se você ainda não tiver Visual Studio, poderá baixar e instalar a versão Microsoft Visual Studio Community [versão](https://visualstudio.microsoft.com/downloads) mais recente gratuitamente.</span><span class="sxs-lookup"><span data-stu-id="0f23f-244">If you do not already have Visual Studio, you can download and install the latest [Microsoft Visual Studio Community](https://visualstudio.microsoft.com/downloads) version for free.</span></span>

- <span data-ttu-id="0f23f-245">A [ferramenta proxy reverso ngrok.](https://ngrok.com)</span><span class="sxs-lookup"><span data-stu-id="0f23f-245">The [ngrok](https://ngrok.com) reverse proxy tool.</span></span> <span data-ttu-id="0f23f-246">Use ngrok para criar um túnel para os pontos de extremidade HTTPS do servidor Web em execução localmente.</span><span class="sxs-lookup"><span data-stu-id="0f23f-246">Use ngrok to create a tunnel to your locally running web server's publicly-available HTTPS endpoints.</span></span> <span data-ttu-id="0f23f-247">Você pode [baixar ngrok](https://ngrok.com/download).</span><span class="sxs-lookup"><span data-stu-id="0f23f-247">You can [download ngrok](https://ngrok.com/download).</span></span>

### <a name="get-the-source-code"></a><span data-ttu-id="0f23f-248">Obter o código-fonte</span><span class="sxs-lookup"><span data-stu-id="0f23f-248">Get the source code</span></span>

<span data-ttu-id="0f23f-249">Em um prompt de comando, crie um novo diretório para seu projeto de guia.</span><span class="sxs-lookup"><span data-stu-id="0f23f-249">At a command prompt, create a new directory for your tab project.</span></span> <span data-ttu-id="0f23f-250">Um projeto simples é fornecido para você começar.</span><span class="sxs-lookup"><span data-stu-id="0f23f-250">A simple project is provided to get you started.</span></span> <span data-ttu-id="0f23f-251">Clone o repositório de exemplo em seu novo diretório usando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="0f23f-251">Clone the sample repository into your new directory using the following command:</span></span>

```bash
git clone https://github.com/OfficeDev/microsoft-teams-sample-tabs.git
```

<span data-ttu-id="0f23f-252">Como alternativa, você pode recuperar o código-fonte baixando a pasta zip e extraindo os arquivos.</span><span class="sxs-lookup"><span data-stu-id="0f23f-252">Alternately, you can retrieve the source code by downloading the zip folder and extracting the files.</span></span>

<span data-ttu-id="0f23f-253">**Para criar e executar o projeto de guia**</span><span class="sxs-lookup"><span data-stu-id="0f23f-253">**To build and run the tab project**</span></span>

1. <span data-ttu-id="0f23f-254">Depois de obter o código-fonte, vá para Visual Studio e selecione **Abrir um projeto ou solução**.</span><span class="sxs-lookup"><span data-stu-id="0f23f-254">After you get the source code, go to Visual Studio and select **Open a project or solution**.</span></span>
1. <span data-ttu-id="0f23f-255">Vá para o diretório de aplicativos de tabulação e abra **PersonalTab.sln**.</span><span class="sxs-lookup"><span data-stu-id="0f23f-255">Go to the tab application directory and open **PersonalTab.sln**.</span></span>
1. <span data-ttu-id="0f23f-256">Para criar e executar seu aplicativo, pressione **F5** ou escolha **Iniciar Depuração** no menu **Depurar.**</span><span class="sxs-lookup"><span data-stu-id="0f23f-256">To build and run your application, press **F5** or choose **Start Debugging** from the **Debug** menu.</span></span>
1. <span data-ttu-id="0f23f-257">Em um navegador, vá para as SEGUINTES URLs para verificar se o aplicativo foi carregado corretamente:</span><span class="sxs-lookup"><span data-stu-id="0f23f-257">In a browser, go to the following URLs to verify the application loaded properly:</span></span>

    - `http://localhost:44325/`
    - `http://localhost:44325/personal`
    - `http://localhost:44325/privacy`
    - `http://localhost:44325/tou`

### <a name="review-the-source-code"></a><span data-ttu-id="0f23f-258">Revisar o código-fonte</span><span class="sxs-lookup"><span data-stu-id="0f23f-258">Review the source code</span></span>

#### <a name="startupcs"></a><span data-ttu-id="0f23f-259">Startup.cs</span><span class="sxs-lookup"><span data-stu-id="0f23f-259">Startup.cs</span></span>

<span data-ttu-id="0f23f-260">Esse projeto foi criado a partir de um modelo vazio do Aplicativo Web 2.2 do ASP.NET Core 2.2 com a caixa de seleção Avançado - Configurar para **HTTPS** selecionada na instalação.</span><span class="sxs-lookup"><span data-stu-id="0f23f-260">This project was created from an ASP.NET Core 2.2 Web Application empty template with the **Advanced - Configure for HTTPS** check box selected at setup.</span></span> <span data-ttu-id="0f23f-261">Os serviços MVC são registrados pelo método da estrutura de injeção de `ConfigureServices()` dependência.</span><span class="sxs-lookup"><span data-stu-id="0f23f-261">The MVC services are registered by the dependency injection framework's `ConfigureServices()` method.</span></span> <span data-ttu-id="0f23f-262">Além disso, o modelo vazio não habilita o serviço de conteúdo estático por padrão, portanto, o middleware de arquivos estáticos é adicionado ao método usando `Configure()` o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="0f23f-262">Additionally, the empty template does not enable serving static content by default, so the static files middleware is added to the `Configure()` method using the following code:</span></span>

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

#### <a name="wwwroot-folder"></a><span data-ttu-id="0f23f-263">pasta wwwroot</span><span class="sxs-lookup"><span data-stu-id="0f23f-263">wwwroot folder</span></span>

<span data-ttu-id="0f23f-264">Em ASP.NET Core, a pasta raiz da Web é onde o aplicativo procura arquivos estáticos.</span><span class="sxs-lookup"><span data-stu-id="0f23f-264">In ASP.NET Core, the web root folder is where the application looks for static files.</span></span>

#### <a name="indexcshtml"></a><span data-ttu-id="0f23f-265">Index.cshtml</span><span class="sxs-lookup"><span data-stu-id="0f23f-265">Index.cshtml</span></span>

<span data-ttu-id="0f23f-266">ASP.NET Core trata arquivos chamados **Index** como o padrão ou home page do site.</span><span class="sxs-lookup"><span data-stu-id="0f23f-266">ASP.NET Core treats files called **Index** as the default or home page for the site.</span></span> <span data-ttu-id="0f23f-267">Quando a URL do navegador aponta para a raiz do site, **Index.cshtml** é exibida como a home page do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0f23f-267">When your browser URL points to the root of the site, **Index.cshtml** is displayed as the home page for your application.</span></span>

#### <a name="appmanifest-folder"></a><span data-ttu-id="0f23f-268">Pasta AppManifest</span><span class="sxs-lookup"><span data-stu-id="0f23f-268">AppManifest folder</span></span>

<span data-ttu-id="0f23f-269">Esta pasta contém os seguintes arquivos de pacote de aplicativos necessários:</span><span class="sxs-lookup"><span data-stu-id="0f23f-269">This folder contains the following required app package files:</span></span>

- <span data-ttu-id="0f23f-270">Um **ícone de cor completo** medindo 192 x 192 pixels.</span><span class="sxs-lookup"><span data-stu-id="0f23f-270">A **full color icon** measuring 192 x 192 pixels.</span></span>
- <span data-ttu-id="0f23f-271">Um **ícone de contorno transparente** medindo 32 x 32 pixels.</span><span class="sxs-lookup"><span data-stu-id="0f23f-271">A **transparent outline icon** measuring 32 x 32 pixels.</span></span>
- <span data-ttu-id="0f23f-272">Um **manifest.json** que especifica os atributos do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0f23f-272">A **manifest.json** file that specifies the attributes of your app.</span></span>

<span data-ttu-id="0f23f-273">Esses arquivos precisam ser cortados em um pacote de aplicativos para uso ao carregar sua guia para Teams.</span><span class="sxs-lookup"><span data-stu-id="0f23f-273">These files need to be zipped in an app package for use in uploading your tab to Teams.</span></span> <span data-ttu-id="0f23f-274">Microsoft Teams carrega o especificado em seu manifesto, incorpora-o em um `contentUrl` <iframe \> e o renderiza em sua guia.</span><span class="sxs-lookup"><span data-stu-id="0f23f-274">Microsoft Teams loads the `contentUrl` specified in your manifest, embeds it in an <iframe\>, and renders it in your tab.</span></span>

#### <a name="csproj"></a><span data-ttu-id="0f23f-275">.csproj</span><span class="sxs-lookup"><span data-stu-id="0f23f-275">.csproj</span></span>

<span data-ttu-id="0f23f-276">Na janela Visual Studio Do Explorador de Soluções, clique com o botão direito do mouse no projeto e selecione **Editar Project Arquivo**.</span><span class="sxs-lookup"><span data-stu-id="0f23f-276">In the Visual Studio Solution Explorer window, right-click on the project and select **Edit Project File**.</span></span> <span data-ttu-id="0f23f-277">No final do arquivo, você vê o seguinte código que cria e atualiza sua pasta zip quando o aplicativo é construído:</span><span class="sxs-lookup"><span data-stu-id="0f23f-277">At the end of the file, you see the following code that creates and updates your zip folder when the application builds:</span></span>

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

### <a name="update-your-application-for-teams"></a><span data-ttu-id="0f23f-278">Atualize seu aplicativo para Teams</span><span class="sxs-lookup"><span data-stu-id="0f23f-278">Update your application for Teams</span></span>

#### <a name="_layoutcshtml"></a><span data-ttu-id="0f23f-279">_Layout.cshtml</span><span class="sxs-lookup"><span data-stu-id="0f23f-279">_Layout.cshtml</span></span>

<span data-ttu-id="0f23f-280">Para que sua guia seja exibida Teams, você deve incluir o **SDK** do cliente JavaScript Microsoft Teams e incluir uma chamada depois que a página `microsoftTeams.initialize()` for carregada.</span><span class="sxs-lookup"><span data-stu-id="0f23f-280">For your tab to display in Teams, you must include the **Microsoft Teams JavaScript client SDK** and include a call to `microsoftTeams.initialize()` after your page loads.</span></span> <span data-ttu-id="0f23f-281">É assim que sua guia e o aplicativo Teams se comunicam:</span><span class="sxs-lookup"><span data-stu-id="0f23f-281">This is how your tab and the Teams app communicate:</span></span>

<span data-ttu-id="0f23f-282">Vá para **a pasta Shared,** **abra _Layout.cshtml** e adicione o seguinte à seção `<head>` tags:</span><span class="sxs-lookup"><span data-stu-id="0f23f-282">Go to the **Shared** folder, open **_Layout.cshtml**, and add the following to the `<head>` tags section:</span></span>

```html
<script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
<script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>
```

#### <a name="personaltabcshtml"></a><span data-ttu-id="0f23f-283">PersonalTab.cshtml</span><span class="sxs-lookup"><span data-stu-id="0f23f-283">PersonalTab.cshtml</span></span>

<span data-ttu-id="0f23f-284">Abra **PersonalTab.cshtml** e atualize as `<script>` marcas incorporadas chamando `microsoftTeams.initialize()` .</span><span class="sxs-lookup"><span data-stu-id="0f23f-284">Open **PersonalTab.cshtml** and update the embedded `<script>` tags by calling `microsoftTeams.initialize()`.</span></span>

<span data-ttu-id="0f23f-285">Certifique-se de salvar **seu PersonalTab.cshtml atualizado.**</span><span class="sxs-lookup"><span data-stu-id="0f23f-285">Ensure you save your updated **PersonalTab.cshtml**.</span></span>

### <a name="establish-a-secure-tunnel-to-your-tab-for-teams"></a><span data-ttu-id="0f23f-286">Estabeleça um túnel seguro para sua guia para Teams</span><span class="sxs-lookup"><span data-stu-id="0f23f-286">Establish a secure tunnel to your tab for Teams</span></span>

<span data-ttu-id="0f23f-287">Microsoft Teams é um produto baseado em nuvem e exige que o conteúdo da guia seja disponibilizado na nuvem usando pontos de extremidade HTTPS.</span><span class="sxs-lookup"><span data-stu-id="0f23f-287">Microsoft Teams is a cloud-based product and requires that your tab content be available from the cloud using HTTPS endpoints.</span></span> <span data-ttu-id="0f23f-288">Teams não permite hospedagem local.</span><span class="sxs-lookup"><span data-stu-id="0f23f-288">Teams does not allow local hosting.</span></span> <span data-ttu-id="0f23f-289">Você deve publicar sua guia em uma URL pública ou usar um proxy que exponha sua porta local a uma URL voltada para a Internet.</span><span class="sxs-lookup"><span data-stu-id="0f23f-289">You must either publish your tab to a public URL, or use a proxy that exposes your local port to an internet-facing URL.</span></span>

<span data-ttu-id="0f23f-290">Para testar sua guia, use [ngrok](https://ngrok.com/docs).</span><span class="sxs-lookup"><span data-stu-id="0f23f-290">To test your tab, use [ngrok](https://ngrok.com/docs).</span></span> <span data-ttu-id="0f23f-291">Os pontos de extremidade da Web do seu servidor estão disponíveis enquanto o ngrok está em execução no computador.</span><span class="sxs-lookup"><span data-stu-id="0f23f-291">Your server's web endpoints are available while ngrok is running on your computer.</span></span> <span data-ttu-id="0f23f-292">Na versão gratuita do ngrok, se você fechar o ngrok, as URLs serão diferentes na próxima vez em que você a iniciar.</span><span class="sxs-lookup"><span data-stu-id="0f23f-292">In the free version of ngrok, if you close ngrok, the URLs are different the next time you start it.</span></span>

<span data-ttu-id="0f23f-293">**Para estabelecer um túnel seguro para sua guia**</span><span class="sxs-lookup"><span data-stu-id="0f23f-293">**To establish a secure tunnel to your tab**</span></span>

1. <span data-ttu-id="0f23f-294">Em um prompt de comando na raiz do diretório do projeto, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="0f23f-294">At a command prompt in the root of your project directory, run the following command:</span></span>

    ```bash
    ngrok http https://localhost:44325 -host-header="localhost:44325"
    ```

    <span data-ttu-id="0f23f-295">O Ngrok escuta as solicitações da Internet e as encaminha para seu aplicativo quando está sendo executado na porta 44325.</span><span class="sxs-lookup"><span data-stu-id="0f23f-295">Ngrok listens to requests from the internet and routes them to your application when it is running on port 44325.</span></span> <span data-ttu-id="0f23f-296">Ela se parece `https://y8rPrT2b.ngrok.io/` com onde **y8rPrT2b** é substituído pela URL HTTPS alfanumérico ngrok.</span><span class="sxs-lookup"><span data-stu-id="0f23f-296">It resembles `https://y8rPrT2b.ngrok.io/` where **y8rPrT2b** is replaced by your ngrok alpha-numeric HTTPS URL.</span></span>

    <span data-ttu-id="0f23f-297">Certifique-se de manter o prompt de comando com o ngrok em execução e anote a URL.</span><span class="sxs-lookup"><span data-stu-id="0f23f-297">Ensure that you keep the command prompt with ngrok running, and make a note of the URL.</span></span>

2. <span data-ttu-id="0f23f-298">Verifique se **o ngrok** está sendo executado e funcionando corretamente abrindo seu navegador e indo para sua página de conteúdo por meio da URL HTTPS ngrok fornecida na janela do prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="0f23f-298">Verify that **ngrok** is running and working properly by opening your browser and going to your content page through the ngrok HTTPS URL that was provided in your command prompt window.</span></span>

> [!TIP]
> <span data-ttu-id="0f23f-299">Você precisa ter seu aplicativo no Visual Studio e ngrok em execução para concluir as etapas fornecidas neste artigo.</span><span class="sxs-lookup"><span data-stu-id="0f23f-299">You need to have both your application in Visual Studio and ngrok running to complete the steps provided in this article.</span></span> <span data-ttu-id="0f23f-300">Se você precisar parar de executar seu aplicativo Visual Studio para trabalhar nele, **mantenha o ngrok em execução**.</span><span class="sxs-lookup"><span data-stu-id="0f23f-300">If you need to stop running your application in Visual Studio to work on it, **keep ngrok running**.</span></span> <span data-ttu-id="0f23f-301">Ele escuta e retoma o roteamento da solicitação do aplicativo quando ele é reiniciado no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0f23f-301">It listens and resumes routing your application's request when it restarts in Visual Studio.</span></span> <span data-ttu-id="0f23f-302">Se você tiver que reiniciar o serviço ngrok, ele retornará uma nova URL e será preciso atualizar todos os lugares que usam essa URL.</span><span class="sxs-lookup"><span data-stu-id="0f23f-302">If you have to restart the ngrok service, it returns a new URL and you have to update every place that uses that URL.</span></span>

#### <a name="run-your-application"></a><span data-ttu-id="0f23f-303">Executar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="0f23f-303">Run your application</span></span>

<span data-ttu-id="0f23f-304">Em Visual Studio, pressione **F5** ou escolha **Iniciar Depuração** no menu **Depuração do** aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0f23f-304">In Visual Studio, press **F5** or choose **Start Debugging** from your application's **Debug** menu.</span></span>

### <a name="upload-your-tab-with-app-studio-for-teams"></a><span data-ttu-id="0f23f-305">Upload sua guia com o App Studio para Teams</span><span class="sxs-lookup"><span data-stu-id="0f23f-305">Upload your tab with App Studio for Teams</span></span>

> [!NOTE]
> <span data-ttu-id="0f23f-306">**O App Studio** pode ser usado para editar seu **manifest.jsno** arquivo e carregar o pacote concluído para Teams.</span><span class="sxs-lookup"><span data-stu-id="0f23f-306">**App Studio** can be used to edit your **manifest.json** file and upload the completed package to Teams.</span></span> <span data-ttu-id="0f23f-307">Você também pode editar manualmente **manifest.jsem**.</span><span class="sxs-lookup"><span data-stu-id="0f23f-307">You can also manually edit **manifest.json**.</span></span> <span data-ttu-id="0f23f-308">Se fizer isso, certifique-se de criar a solução novamente para criar o arquivo **Tab.zip** para carregar.</span><span class="sxs-lookup"><span data-stu-id="0f23f-308">If you do, ensure that you build the solution again to create the **Tab.zip** file to upload.</span></span>

<span data-ttu-id="0f23f-309">**Para carregar sua guia com o App Studio**</span><span class="sxs-lookup"><span data-stu-id="0f23f-309">**To upload your tab with App Studio**</span></span>

1. <span data-ttu-id="0f23f-310">Vá para Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="0f23f-310">Go to Microsoft Teams.</span></span> <span data-ttu-id="0f23f-311">Se você usar a [versão baseada na Web,](https://teams.microsoft.com)poderá inspecionar seu código front-end usando as ferramentas de desenvolvedor [do navegador.](~/tabs/how-to/developer-tools.md)</span><span class="sxs-lookup"><span data-stu-id="0f23f-311">If you use the [web-based version](https://teams.microsoft.com), you can inspect your front-end code using your browser's [developer tools](~/tabs/how-to/developer-tools.md).</span></span>

1. <span data-ttu-id="0f23f-312">Vá para **o App Studio** e selecione a guia Editor **de** manifesto.</span><span class="sxs-lookup"><span data-stu-id="0f23f-312">Go to **App Studio** and select the **Manifest editor** tab.</span></span>

1. <span data-ttu-id="0f23f-313">Selecione **Importar um aplicativo existente** no editor de **Manifesto** para começar a atualizar o pacote de aplicativos para sua guia. O código-fonte vem com seu próprio manifesto parcialmente completo.</span><span class="sxs-lookup"><span data-stu-id="0f23f-313">Select **Import an existing app** in the **Manifest editor** to begin updating the app package for your tab. The source code comes with its own partially complete manifest.</span></span> <span data-ttu-id="0f23f-314">O nome do pacote do aplicativo é **tab.zip**.</span><span class="sxs-lookup"><span data-stu-id="0f23f-314">The name of your app package is **tab.zip**.</span></span> <span data-ttu-id="0f23f-315">Ele está disponível no seguinte caminho:</span><span class="sxs-lookup"><span data-stu-id="0f23f-315">It is available from the following path:</span></span>

    ```bash
    /bin/Debug/netcoreapp2.2/tab.zip
    ```

1. <span data-ttu-id="0f23f-316">Upload **tab.zip** App **Studio.**</span><span class="sxs-lookup"><span data-stu-id="0f23f-316">Upload **tab.zip** to **App Studio**.</span></span>

#### <a name="update-your-app-package-with-manifest-editor"></a><span data-ttu-id="0f23f-317">Atualizar seu pacote de aplicativos com o editor de manifesto</span><span class="sxs-lookup"><span data-stu-id="0f23f-317">Update your app package with Manifest editor</span></span>

<span data-ttu-id="0f23f-318">Depois de carregar seu pacote de aplicativos no App Studio, você deve configurá-lo.</span><span class="sxs-lookup"><span data-stu-id="0f23f-318">After you have uploaded your app package into App Studio, you must configure it.</span></span>

<span data-ttu-id="0f23f-319">Selecione o azulejo para sua guia recém-importada no painel direito da página de boas-vindas do editor de manifesto.</span><span class="sxs-lookup"><span data-stu-id="0f23f-319">Select the tile for your newly imported tab in the right pane of the Manifest editor welcome page.</span></span>

<span data-ttu-id="0f23f-320">Há uma lista de etapas no lado esquerdo do editor de Manifesto e, à direita, uma lista de propriedades que devem ter valores para cada uma dessas etapas.</span><span class="sxs-lookup"><span data-stu-id="0f23f-320">There is a list of steps on the left side of the Manifest editor, and on the right, a list of properties that must have values for each of those steps.</span></span> <span data-ttu-id="0f23f-321">Grande parte das informações foi fornecida pelo seumanifest.js **em,** mas há campos que você deve atualizar.</span><span class="sxs-lookup"><span data-stu-id="0f23f-321">Much of the information has been provided by your **manifest.json** but there are fields that you must update.</span></span>

##### <a name="details-app-details"></a><span data-ttu-id="0f23f-322">Detalhes: Detalhes do aplicativo</span><span class="sxs-lookup"><span data-stu-id="0f23f-322">Details: App details</span></span>

<span data-ttu-id="0f23f-323">Na seção **Detalhes do** aplicativo:</span><span class="sxs-lookup"><span data-stu-id="0f23f-323">In the **App details** section:</span></span>

1. <span data-ttu-id="0f23f-324">Em **Identificação**, selecione **Gerar** para gerar uma nova ID de aplicativo para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0f23f-324">Under **Identification**, select **Generate** to generate a new App ID for your app.</span></span>

1. <span data-ttu-id="0f23f-325">Em **Informações do desenvolvedor**, **atualize Site** com sua URL HTTPS **ngrok.**</span><span class="sxs-lookup"><span data-stu-id="0f23f-325">Under **Developer information**, update **Website** with your **ngrok** HTTPS URL.</span></span>

    ![URLs do aplicativo atualizadas](../../assets/images/tab-images/appurls.png)

1. <span data-ttu-id="0f23f-327">Em **URLs do aplicativo,** atualize a **instrução Privacy** para `https://<yourngrokurl>/privacy` e Termos de **uso** para `https://<yourngrokurl>/tou`>.</span><span class="sxs-lookup"><span data-stu-id="0f23f-327">Under **App URLs**, update the **Privacy statement** to `https://<yourngrokurl>/privacy` and **Terms of use** to `https://<yourngrokurl>/tou`>.</span></span>

##### <a name="capabilities-tabs"></a><span data-ttu-id="0f23f-328">Recursos: guias</span><span class="sxs-lookup"><span data-stu-id="0f23f-328">Capabilities: Tabs</span></span>

<span data-ttu-id="0f23f-329">Na seção **Guias:**</span><span class="sxs-lookup"><span data-stu-id="0f23f-329">In the **Tabs** section:</span></span>

1. <span data-ttu-id="0f23f-330">Em **Adicionar uma guia pessoal,** selecione **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="0f23f-330">Under **Add a personal tab**, select **Add**.</span></span> <span data-ttu-id="0f23f-331">Uma caixa de diálogo pop-up é exibida.</span><span class="sxs-lookup"><span data-stu-id="0f23f-331">A pop-up dialog box appears.</span></span>

1. <span data-ttu-id="0f23f-332">Insira um nome para a guia pessoal em **Nome**.</span><span class="sxs-lookup"><span data-stu-id="0f23f-332">Enter a name for the personal tab in **Name**.</span></span>

1. <span data-ttu-id="0f23f-333">Insira a **ID da entidade**.</span><span class="sxs-lookup"><span data-stu-id="0f23f-333">Enter the **Entity ID**.</span></span>

1. <span data-ttu-id="0f23f-334">Atualizar **a URL de conteúdo** com `https://<yourngrokurl>/personalTab` .</span><span class="sxs-lookup"><span data-stu-id="0f23f-334">Update **Content URL** with `https://<yourngrokurl>/personalTab`.</span></span>

    <span data-ttu-id="0f23f-335">Deixe o **campo URL do site** em branco.</span><span class="sxs-lookup"><span data-stu-id="0f23f-335">Leave the **Website URL** field blank.</span></span>

    ![Detalhes da guia pessoal](../../assets/images/tab-images/personaltabdetails.png)

1. <span data-ttu-id="0f23f-337">Selecione **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="0f23f-337">Select **Save**.</span></span>

##### <a name="finish-domains-and-permissions"></a><span data-ttu-id="0f23f-338">Concluir: domínios e permissões</span><span class="sxs-lookup"><span data-stu-id="0f23f-338">Finish: Domains and permissions</span></span>

<span data-ttu-id="0f23f-339">Na seção **Domínios e** permissões, **domínios** de suas guias devem conter sua URL ngrok sem o prefixo HTTPS `<yourngrokurl>.ngrok.io/` .</span><span class="sxs-lookup"><span data-stu-id="0f23f-339">In the **Domains and permissions** section, **Domains from your tabs** must contain your ngrok URL without the HTTPS prefix `<yourngrokurl>.ngrok.io/`.</span></span>

###### <a name="finish-test-and-distribute"></a><span data-ttu-id="0f23f-340">Concluir: Testar e distribuir</span><span class="sxs-lookup"><span data-stu-id="0f23f-340">Finish: Test and distribute</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0f23f-341">À direita, em **Descrição,** você verá o seguinte aviso:</span><span class="sxs-lookup"><span data-stu-id="0f23f-341">On the right, in **Description**, you see the following warning:</span></span>
>
> <span data-ttu-id="0f23f-342">&#9888; A **matriz 'validDomains' não pode conter um site de tunelamento...**</span><span class="sxs-lookup"><span data-stu-id="0f23f-342">&#9888; **The 'validDomains' array cannot contain a tunneling site...**</span></span>
>
> <span data-ttu-id="0f23f-343">Esse aviso pode ser ignorado durante o teste da guia.</span><span class="sxs-lookup"><span data-stu-id="0f23f-343">This warning can be ignored while testing your tab.</span></span>

1. <span data-ttu-id="0f23f-344">Na seção **Testar e Distribuir,** selecione **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="0f23f-344">In the **Test and Distribute** section, select **Install**.</span></span>

1. <span data-ttu-id="0f23f-345">Na caixa de diálogo pop-up, selecione **Adicionar** e sua guia será exibida.</span><span class="sxs-lookup"><span data-stu-id="0f23f-345">In the pop-up dialog box, select **Add** and your tab is displayed.</span></span>

    ![Guia pessoal ASPNET carregada](../../assets/images/tab-images/personaltabaspnetuploaded.png)

### <a name="view-your-personal-tab-in-teams"></a><span data-ttu-id="0f23f-347">Exibir sua guia pessoal no Teams</span><span class="sxs-lookup"><span data-stu-id="0f23f-347">View your personal tab in Teams</span></span>

1. <span data-ttu-id="0f23f-348">Na barra de navegação localizada à extrema esquerda do aplicativo Teams, selecione as releições &#x25CF;&#x25CF;&#x25CF;.</span><span class="sxs-lookup"><span data-stu-id="0f23f-348">In the navigation bar located at the far left of the Teams app, select the ellipses &#x25CF;&#x25CF;&#x25CF;.</span></span> <span data-ttu-id="0f23f-349">Uma lista de aplicativos pessoais é mostrada.</span><span class="sxs-lookup"><span data-stu-id="0f23f-349">A list of personal apps is shown.</span></span>

1. <span data-ttu-id="0f23f-350">Selecione sua guia na lista para exibi-la.</span><span class="sxs-lookup"><span data-stu-id="0f23f-350">Select your tab from the list to view it.</span></span>

# <a name="aspnet-core-mvc"></a>[<span data-ttu-id="0f23f-351">ASP.NET Core MVC</span><span class="sxs-lookup"><span data-stu-id="0f23f-351">ASP.NET Core MVC</span></span>](#tab/aspnetcoremvc)

### <a name="create-a-custom-personal-tab-with-aspnet-core-mvc"></a><span data-ttu-id="0f23f-352">Criar uma guia pessoal personalizada com ASP.NET Core MVC</span><span class="sxs-lookup"><span data-stu-id="0f23f-352">Create a custom personal tab with ASP.NET Core MVC</span></span>

<span data-ttu-id="0f23f-353">Você pode criar uma guia pessoal personalizada usando C# e ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="0f23f-353">You can create a custom personal tab using C# and ASP.NET Core MVC.</span></span> <span data-ttu-id="0f23f-354">[O App Studio para Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) também é usado para finalizar o manifesto do aplicativo e implantar sua guia para Teams.</span><span class="sxs-lookup"><span data-stu-id="0f23f-354">[App Studio for Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) is also used to finalize your app manifest and deploy your tab to Teams.</span></span>

### <a name="prerequisites-for-personal-tab-with-aspnet-core-mvc"></a><span data-ttu-id="0f23f-355">Pré-requisitos para guia pessoal com ASP.NET Core MVC</span><span class="sxs-lookup"><span data-stu-id="0f23f-355">Prerequisites for personal tab with ASP.NET Core MVC</span></span>

- <span data-ttu-id="0f23f-356">Você deve ter um locatário Microsoft 365 e uma equipe configurada com **Permitir o carregamento de aplicativos personalizados** habilitados.</span><span class="sxs-lookup"><span data-stu-id="0f23f-356">You must have a Microsoft 365 tenant and a team configured with **Allow uploading custom apps** enabled.</span></span> <span data-ttu-id="0f23f-357">Para obter mais informações, [consulte prepare your Office 365 tenant](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span><span class="sxs-lookup"><span data-stu-id="0f23f-357">For more information, see [prepare your Office 365 tenant](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="0f23f-358">Se você não tiver uma conta Microsoft 365, poderá se inscrever para uma assinatura gratuita por meio do [Programa de Desenvolvedores da Microsoft.](https://developer.microsoft.com/en-us/microsoft-365/dev-program)</span><span class="sxs-lookup"><span data-stu-id="0f23f-358">If you do not have a Microsoft 365 account, you can sign up for a free subscription through the [Microsoft Developer Program](https://developer.microsoft.com/en-us/microsoft-365/dev-program).</span></span> <span data-ttu-id="0f23f-359">A assinatura permanece ativa desde que você a use para desenvolvimento contínuo.</span><span class="sxs-lookup"><span data-stu-id="0f23f-359">The subscription remains active as long as you are using it for ongoing development.</span></span>

- <span data-ttu-id="0f23f-360">Use o App Studio para importar seu aplicativo para Teams.</span><span class="sxs-lookup"><span data-stu-id="0f23f-360">Use App Studio to import your application to Teams.</span></span> <span data-ttu-id="0f23f-361">Para instalar o App Studio, selecione **Aplicativo** da Loja de Aplicativos no canto inferior esquerdo do aplicativo Teams ![ e ](~/assets/images/tab-images/storeApp.png) pesquise **por App Studio**.</span><span class="sxs-lookup"><span data-stu-id="0f23f-361">To install App Studio, select **Apps** ![Store App](~/assets/images/tab-images/storeApp.png) at the lower left corner of the Teams app, and search for **App Studio**.</span></span> <span data-ttu-id="0f23f-362">Depois de encontrar o azulejo, selecione-o e escolha **Adicionar** na caixa de diálogo pop-up para instalá-lo.</span><span class="sxs-lookup"><span data-stu-id="0f23f-362">After you find the tile, select it and choose **Add** in the pop-up dialog box to install it.</span></span>

<span data-ttu-id="0f23f-363">Além disso, este projeto exige que você tenha o seguinte instalado em seu ambiente de desenvolvimento:</span><span class="sxs-lookup"><span data-stu-id="0f23f-363">In addition, this project requires that you have the following installed in your development environment:</span></span>

- <span data-ttu-id="0f23f-364">A versão atual do Visual Studio IDE com a carga de trabalho de desenvolvimento entre **plataformas .NET CORE** instalada.</span><span class="sxs-lookup"><span data-stu-id="0f23f-364">The current version of the Visual Studio IDE with the **.NET CORE cross-platform development** workload installed.</span></span> <span data-ttu-id="0f23f-365">Se você ainda não tiver Visual Studio, poderá baixar e instalar a versão Microsoft Visual Studio Community [versão](https://visualstudio.microsoft.com/downloads) mais recente gratuitamente.</span><span class="sxs-lookup"><span data-stu-id="0f23f-365">If you do not already have Visual Studio, you can download and install the latest [Microsoft Visual Studio Community](https://visualstudio.microsoft.com/downloads) version for free.</span></span>

- <span data-ttu-id="0f23f-366">A [ferramenta proxy reverso ngrok.](https://ngrok.com)</span><span class="sxs-lookup"><span data-stu-id="0f23f-366">The [ngrok](https://ngrok.com) reverse proxy tool.</span></span> <span data-ttu-id="0f23f-367">Use ngrok para criar um túnel para os pontos de extremidade HTTPS do servidor Web em execução localmente.</span><span class="sxs-lookup"><span data-stu-id="0f23f-367">Use ngrok to create a tunnel to your locally running web server's publicly-available HTTPS endpoints.</span></span> <span data-ttu-id="0f23f-368">Você pode [baixar ngrok](https://ngrok.com/download).</span><span class="sxs-lookup"><span data-stu-id="0f23f-368">You can [download ngrok](https://ngrok.com/download).</span></span>

### <a name="get-the-source-code"></a><span data-ttu-id="0f23f-369">Obter o código-fonte</span><span class="sxs-lookup"><span data-stu-id="0f23f-369">Get the source code</span></span>

<span data-ttu-id="0f23f-370">Em um prompt de comando, crie um novo diretório para seu projeto de guia.</span><span class="sxs-lookup"><span data-stu-id="0f23f-370">At a command prompt, create a new directory for your tab project.</span></span> <span data-ttu-id="0f23f-371">Um projeto simples é fornecido para você começar.</span><span class="sxs-lookup"><span data-stu-id="0f23f-371">A simple project is provided to get you started.</span></span> <span data-ttu-id="0f23f-372">Clone o repositório de exemplo em seu novo diretório usando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="0f23f-372">Clone the sample repository into your new directory using the following command:</span></span>

``` bash
git clone https://github.com/OfficeDev/microsoft-teams-sample-tabs.git
```

<span data-ttu-id="0f23f-373">Como alternativa, você pode recuperar o código-fonte baixando a pasta zip e extraindo os arquivos.</span><span class="sxs-lookup"><span data-stu-id="0f23f-373">Alternately, you can retrieve the source code by downloading the zip folder and extracting the files.</span></span>

<span data-ttu-id="0f23f-374">**Para criar e executar o projeto de guia**</span><span class="sxs-lookup"><span data-stu-id="0f23f-374">**To build and run the tab project**</span></span>

1. <span data-ttu-id="0f23f-375">Depois de ter o código-fonte, vá para Visual Studio e selecione **Abrir um projeto ou solução**.</span><span class="sxs-lookup"><span data-stu-id="0f23f-375">After you have the source code, go to Visual Studio and select **Open a project or solution**.</span></span>
1. <span data-ttu-id="0f23f-376">Vá para o diretório de aplicativos de tabulação e abra **PersonalTabMVC.sln**.</span><span class="sxs-lookup"><span data-stu-id="0f23f-376">Go to the tab application directory and open **PersonalTabMVC.sln**.</span></span>
1. <span data-ttu-id="0f23f-377">Para criar e executar seu aplicativo, pressione **F5** ou escolha **Iniciar Depuração** no menu **Depurar.**</span><span class="sxs-lookup"><span data-stu-id="0f23f-377">To build and run your application, press **F5** or choose **Start Debugging** from the **Debug** menu.</span></span>
1. <span data-ttu-id="0f23f-378">Em um navegador, vá para as SEGUINTES URLs para verificar se o aplicativo foi carregado corretamente:</span><span class="sxs-lookup"><span data-stu-id="0f23f-378">In a browser, go to the following URLs to verify that the application loaded properly:</span></span>

    * `http://localhost:44335`
    * `http://localhost:44335/privacy`
    * `http://localhost:44335/tou`

### <a name="review-the-source-code"></a><span data-ttu-id="0f23f-379">Revisar o código-fonte</span><span class="sxs-lookup"><span data-stu-id="0f23f-379">Review the source code</span></span>

#### <a name="startupcs"></a><span data-ttu-id="0f23f-380">Startup.cs</span><span class="sxs-lookup"><span data-stu-id="0f23f-380">Startup.cs</span></span>

<span data-ttu-id="0f23f-381">Esse projeto foi criado a partir de um modelo vazio do Aplicativo Web 2.2 do ASP.NET Core 2.2 com a caixa de seleção Avançado - Configurar para **HTTPS** selecionada na instalação.</span><span class="sxs-lookup"><span data-stu-id="0f23f-381">This project was created from an ASP.NET Core 2.2 Web Application empty template with the **Advanced - Configure for HTTPS** check box selected at setup.</span></span> <span data-ttu-id="0f23f-382">Os serviços MVC são registrados pelo método da estrutura de injeção de `ConfigureServices()` dependência.</span><span class="sxs-lookup"><span data-stu-id="0f23f-382">The MVC services are registered by the dependency injection framework's `ConfigureServices()` method.</span></span> <span data-ttu-id="0f23f-383">Além disso, o modelo vazio não habilita o serviço de conteúdo estático por padrão, portanto, o middleware de arquivos estáticos é adicionado ao método usando `Configure()` o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="0f23f-383">Additionally, the empty template does not enable serving static content by default, so the static files middleware is added to the `Configure()` method using the following code:</span></span>

``` csharp
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

#### <a name="wwwroot-folder"></a><span data-ttu-id="0f23f-384">pasta wwwroot</span><span class="sxs-lookup"><span data-stu-id="0f23f-384">wwwroot folder</span></span>

<span data-ttu-id="0f23f-385">Em ASP.NET Core, a pasta raiz da Web é onde o aplicativo procura arquivos estáticos.</span><span class="sxs-lookup"><span data-stu-id="0f23f-385">In ASP.NET Core, the web root folder is where the application looks for static files.</span></span>

#### <a name="appmanifest-folder"></a><span data-ttu-id="0f23f-386">Pasta AppManifest</span><span class="sxs-lookup"><span data-stu-id="0f23f-386">AppManifest folder</span></span>

<span data-ttu-id="0f23f-387">Esta pasta contém os seguintes arquivos de pacote de aplicativos necessários:</span><span class="sxs-lookup"><span data-stu-id="0f23f-387">This folder contains the following required app package files:</span></span>

* <span data-ttu-id="0f23f-388">Um **ícone de cor completo** medindo 192 x 192 pixels.</span><span class="sxs-lookup"><span data-stu-id="0f23f-388">A **full color icon** measuring 192 x 192 pixels.</span></span>
* <span data-ttu-id="0f23f-389">Um **ícone de contorno transparente** medindo 32 x 32 pixels.</span><span class="sxs-lookup"><span data-stu-id="0f23f-389">A **transparent outline icon** measuring 32 x 32 pixels.</span></span>
* <span data-ttu-id="0f23f-390">Um **manifest.json** que especifica os atributos do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0f23f-390">A **manifest.json** file that specifies the attributes of your app.</span></span>

<span data-ttu-id="0f23f-391">Esses arquivos precisam ser cortados em um pacote de aplicativos para uso ao carregar sua guia para Teams.</span><span class="sxs-lookup"><span data-stu-id="0f23f-391">These files need to be zipped in an app package for use in uploading your tab to Teams.</span></span> <span data-ttu-id="0f23f-392">Microsoft Teams carrega o especificado em seu manifesto, incorpora-o em um IFrame e `contentUrl` o renderiza em sua guia.</span><span class="sxs-lookup"><span data-stu-id="0f23f-392">Microsoft Teams loads the `contentUrl` specified in your manifest, embeds it in an IFrame, and renders it in your tab.</span></span>

#### <a name="csproj"></a><span data-ttu-id="0f23f-393">.csproj</span><span class="sxs-lookup"><span data-stu-id="0f23f-393">.csproj</span></span>

<span data-ttu-id="0f23f-394">Na janela Visual Studio Do Explorador de Soluções, clique com o botão direito do mouse no projeto e selecione **Editar Project Arquivo**.</span><span class="sxs-lookup"><span data-stu-id="0f23f-394">In the Visual Studio Solution Explorer window, right-click on the project and select **Edit Project File**.</span></span> <span data-ttu-id="0f23f-395">No final do arquivo, você vê o seguinte código que cria e atualiza sua pasta zip quando o aplicativo é construído:</span><span class="sxs-lookup"><span data-stu-id="0f23f-395">At the end of the file, you see the following code that creates and updates your zip folder when the application builds:</span></span>

``` xml
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

#### <a name="models"></a><span data-ttu-id="0f23f-396">Modelos</span><span class="sxs-lookup"><span data-stu-id="0f23f-396">Models</span></span>

<span data-ttu-id="0f23f-397">**PersonalTab.cs** apresenta um objeto Message e métodos que são chamados de **PersonalTabController** quando um usuário seleciona um botão no Modo de Exibição **PersonalTab.**</span><span class="sxs-lookup"><span data-stu-id="0f23f-397">**PersonalTab.cs** presents a Message object and methods that are called from **PersonalTabController** when a user selects a button in the **PersonalTab** View.</span></span>

#### <a name="views"></a><span data-ttu-id="0f23f-398">Modos de exibição</span><span class="sxs-lookup"><span data-stu-id="0f23f-398">Views</span></span>

<span data-ttu-id="0f23f-399">Estas são as diferentes exibições em ASP.NET Core MVC:</span><span class="sxs-lookup"><span data-stu-id="0f23f-399">These are the different views in ASP.NET Core MVC:</span></span>

* <span data-ttu-id="0f23f-400">Home: ASP.NET Core trata arquivos chamados **Index** como o padrão ou home page do site.</span><span class="sxs-lookup"><span data-stu-id="0f23f-400">Home: ASP.NET Core treats files called **Index** as the default or home page for the site.</span></span> <span data-ttu-id="0f23f-401">Quando a URL do navegador aponta para a raiz do site, **Index.cshtml** é exibida como a home page do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0f23f-401">When your browser URL points to the root of the site, **Index.cshtml** is displayed as the home page for your application.</span></span>

* <span data-ttu-id="0f23f-402">Compartilhado: a marcação de exibição **parcial _Layout.cshtml** contém a estrutura geral da página do aplicativo e elementos visuais compartilhados.</span><span class="sxs-lookup"><span data-stu-id="0f23f-402">Shared: The partial view markup **_Layout.cshtml** contains the application's overall page structure and shared visual elements.</span></span> <span data-ttu-id="0f23f-403">Ele também faz referência à biblioteca Teams.</span><span class="sxs-lookup"><span data-stu-id="0f23f-403">It also references the Teams Library.</span></span>

#### <a name="controllers"></a><span data-ttu-id="0f23f-404">Controladores</span><span class="sxs-lookup"><span data-stu-id="0f23f-404">Controllers</span></span>

<span data-ttu-id="0f23f-405">Os controladores usam a `ViewBag` propriedade para transferir valores dinamicamente para o Views.</span><span class="sxs-lookup"><span data-stu-id="0f23f-405">The controllers use the `ViewBag` property to transfer values dynamically to the Views.</span></span>

[!INCLUDE [dotnet-update-personal-app](~/includes/tabs/dotnet-update-personal-app.md)]

[!INCLUDE [dotnet-ngrok-intro](~/includes/tabs/dotnet-ngrok-intro.md)]

<span data-ttu-id="0f23f-406">**Para executar o ngrok e verificar a página de conteúdo**</span><span class="sxs-lookup"><span data-stu-id="0f23f-406">**To run ngrok and verify the content page**</span></span>

1. <span data-ttu-id="0f23f-407">Em um prompt de comando na raiz do diretório do projeto, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="0f23f-407">At a command prompt in the root of your project directory, run the following command:</span></span>

    ``` bash
    ngrok http https://localhost:44345 -host-header="localhost:44345"
    ```

    <span data-ttu-id="0f23f-408">O Ngrok escuta as solicitações da Internet e as encaminha para seu aplicativo quando está sendo executado na porta 44325.</span><span class="sxs-lookup"><span data-stu-id="0f23f-408">Ngrok listens to requests from the internet and routes them to your application when it is running on port 44325.</span></span> <span data-ttu-id="0f23f-409">Ela se parece `https://y8rPrT2b.ngrok.io/` com onde **y8rPrT2b** é substituído pela URL HTTPS alfanumérico ngrok.</span><span class="sxs-lookup"><span data-stu-id="0f23f-409">It resembles `https://y8rPrT2b.ngrok.io/` where **y8rPrT2b** is replaced by your ngrok alpha-numeric HTTPS URL.</span></span>

    <span data-ttu-id="0f23f-410">Certifique-se de manter o prompt de comando com o ngrok em execução e anote a URL.</span><span class="sxs-lookup"><span data-stu-id="0f23f-410">Ensure you keep the command prompt with ngrok running, and make a note of the URL.</span></span>

1. <span data-ttu-id="0f23f-411">Verifique se **o ngrok** está sendo executado e funcionando corretamente abrindo seu navegador e indo para sua página de conteúdo por meio da URL HTTPS ngrok fornecida na janela do prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="0f23f-411">Verify that **ngrok** is running and working properly by opening your browser and going to your content page through the ngrok HTTPS URL that was provided in your command prompt window.</span></span>

> [!TIP]
> <span data-ttu-id="0f23f-412">Você precisa ter seu aplicativo no Visual Studio e ngrok em execução para concluir as etapas fornecidas neste artigo.</span><span class="sxs-lookup"><span data-stu-id="0f23f-412">You need to have both your application in Visual Studio and ngrok running to complete the steps provided in this article.</span></span> <span data-ttu-id="0f23f-413">Se você precisar parar de executar seu aplicativo Visual Studio para trabalhar nele, **mantenha o ngrok em execução**.</span><span class="sxs-lookup"><span data-stu-id="0f23f-413">If you need to stop running your application in Visual Studio to work on it, **keep ngrok running**.</span></span> <span data-ttu-id="0f23f-414">Ele escuta e retoma o roteamento da solicitação do aplicativo quando ele é reiniciado no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0f23f-414">It listens and resumes routing your application's request when it restarts in Visual Studio.</span></span> <span data-ttu-id="0f23f-415">Se você tiver que reiniciar o serviço ngrok, ele retornará uma nova URL e será preciso atualizar todos os lugares que usam essa URL.</span><span class="sxs-lookup"><span data-stu-id="0f23f-415">If you have to restart the ngrok service it returns a new URL and you have to update every place that uses that URL.</span></span>

#### <a name="run-your-application"></a><span data-ttu-id="0f23f-416">Executar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="0f23f-416">Run your application</span></span>

<span data-ttu-id="0f23f-417">Em Visual Studio, pressione **F5** ou escolha **Iniciar Depuração** no menu **Depuração do** aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0f23f-417">In Visual Studio, press **F5** or choose **Start Debugging** from your application's **Debug** menu.</span></span>

[!INCLUDE [dotnet-personal-use-appstudio](~/includes/tabs/dotnet-personal-use-appstudio.md)]

---

## <a name="reorder-static-personal-tabs"></a><span data-ttu-id="0f23f-418">Reordenar guias pessoais estáticas</span><span class="sxs-lookup"><span data-stu-id="0f23f-418">Reorder static personal tabs</span></span>

<span data-ttu-id="0f23f-419">A partir da versão 1.7 do manifesto, os desenvolvedores podem reorganizar todas as guias em seu aplicativo pessoal.</span><span class="sxs-lookup"><span data-stu-id="0f23f-419">Starting with manifest version 1.7, developers can rearrange all tabs in their personal app.</span></span> <span data-ttu-id="0f23f-420">Em particular, um desenvolvedor pode mover a guia de **chat** bot, que sempre é padrão para a primeira posição, em qualquer lugar no header da guia do aplicativo pessoal.</span><span class="sxs-lookup"><span data-stu-id="0f23f-420">In particular, a developer can move the **bot chat** tab, which always defaults to the first position, anywhere in the personal app tab header.</span></span> <span data-ttu-id="0f23f-421">Duas palavras-chave de guia `entityId` reservadas são declaradas, **conversas** e **sobre**.</span><span class="sxs-lookup"><span data-stu-id="0f23f-421">Two reserved tab `entityId` keywords are declared, **conversations** and **about**.</span></span>

<span data-ttu-id="0f23f-422">Se você criar um bot com **um escopo pessoal,** ele aparecerá na primeira posição da guia em um aplicativo pessoal por padrão.</span><span class="sxs-lookup"><span data-stu-id="0f23f-422">If you create a bot with a **personal** scope, it appears in the first tab position in a personal app by default.</span></span> <span data-ttu-id="0f23f-423">Se você quiser movê-lo para outra posição, adicione um objeto de guia estático ao manifesto com a palavra-chave reservada, **conversas**.</span><span class="sxs-lookup"><span data-stu-id="0f23f-423">If you want to move it to another position, you must add a static tab object to your manifest with the reserved keyword, **conversations**.</span></span> <span data-ttu-id="0f23f-424">A **guia** conversa é exibida na Web ou na área de trabalho, dependendo de onde você adicionar a guia **de** conversa na `staticTabs` matriz.</span><span class="sxs-lookup"><span data-stu-id="0f23f-424">The **conversation** tab appears on web or desktop depending on where you add the **conversation** tab in the `staticTabs` array.</span></span>

```json
{
   "staticTabs":[
      {
         
      },
      {
         "entityId":"conversations",
         "scopes":[
            "personal"
         ]
      }
   ]
}
```

## <a name="see-also"></a><span data-ttu-id="0f23f-425">Confira também</span><span class="sxs-lookup"><span data-stu-id="0f23f-425">See also</span></span>

* [<span data-ttu-id="0f23f-426">Teams guias</span><span class="sxs-lookup"><span data-stu-id="0f23f-426">Teams tabs</span></span>](~/tabs/what-are-tabs.md)
* [<span data-ttu-id="0f23f-427">Guias em dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="0f23f-427">Tabs on mobile</span></span>](~/tabs/design/tabs-mobile.md)
* [<span data-ttu-id="0f23f-428">Criar guias com Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="0f23f-428">Build tabs with Adaptive Cards</span></span>](~/tabs/how-to/build-adaptive-card-tabs.md)
* [<span data-ttu-id="0f23f-429">Criar abas para conversação</span><span class="sxs-lookup"><span data-stu-id="0f23f-429">Create conversational tabs</span></span>](~/tabs/how-to/conversational-tabs.md)

## <a name="next-step"></a><span data-ttu-id="0f23f-430">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="0f23f-430">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0f23f-431">Criar um canal ou uma guia de grupo</span><span class="sxs-lookup"><span data-stu-id="0f23f-431">Create a channel or group tab</span></span>](~/tabs/how-to/create-channel-group-tab.md)
