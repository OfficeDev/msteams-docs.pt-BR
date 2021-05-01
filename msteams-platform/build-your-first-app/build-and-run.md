---
title: Começar - Criar e executar seu primeiro aplicativo
author: girliemac
description: Crie rapidamente um Microsoft Teams que exibe um "Hello, World!" usando o Microsoft Teams Toolkit.
ms.author: timura
ms.date: 03/22/2021
ms.topic: quickstart
ms.openlocfilehash: 6c3d215a3f2c1aa89a9a2bf28aad081d98c6dc33
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101720"
---
# <a name="create-your-first-microsoft-teams-app"></a><span data-ttu-id="4e47c-104">Criar seu primeiro Microsoft Teams app</span><span class="sxs-lookup"><span data-stu-id="4e47c-104">Create your first Microsoft Teams app</span></span>

<span data-ttu-id="4e47c-105">Esse início rápido ensina você a criar e executar um Microsoft Teams que exibe "Hello, World!"</span><span class="sxs-lookup"><span data-stu-id="4e47c-105">This quickstart teaches you to build and run Microsoft Teams app that displays "Hello, World!"</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4e47c-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="4e47c-106">Prerequisites</span></span>

<span data-ttu-id="4e47c-107">Antes de começar, você precisa configurar seu locatário de desenvolvimento [Teams](#set-up-your-teams-development-tenant) e instalar suas [ferramentas Teams de desenvolvimento.](#install-your-development-tools)</span><span class="sxs-lookup"><span data-stu-id="4e47c-107">Before you begin, you need to [set up your Teams development tenant](#set-up-your-teams-development-tenant) and [install your Teams development tools](#install-your-development-tools).</span></span>

### <a name="set-up-your-teams-development-tenant"></a><span data-ttu-id="4e47c-108">Configurar seu locatário Teams desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="4e47c-108">Set up your Teams development tenant</span></span>

<span data-ttu-id="4e47c-109">Um **locatário** é como um contêiner para uma organização.</span><span class="sxs-lookup"><span data-stu-id="4e47c-109">A **tenant** is like a container for an organization.</span></span> <span data-ttu-id="4e47c-110">Em Teams, um locatário é onde as pessoas dessa organização conversam, compartilham arquivos e executem reuniões.</span><span class="sxs-lookup"><span data-stu-id="4e47c-110">In Teams terms, a tenant is where people from that org chat, share files, and run meetings.</span></span> <span data-ttu-id="4e47c-111">Como desenvolvedor, você precisa de um locatário para fazer sideload e testar o Teams aplicativos que você está criando.</span><span class="sxs-lookup"><span data-stu-id="4e47c-111">As a developer, you need a tenant to sideload and test the Teams apps that you are building.</span></span>  

# <a name="do-not-have-a-tenant"></a>[<span data-ttu-id="4e47c-112">Não tem um locatário</span><span class="sxs-lookup"><span data-stu-id="4e47c-112">Do not have a tenant</span></span>](#tab/do-not-have-a-tenant)

<span data-ttu-id="4e47c-113">Você pode obter uma conta Teams de teste gratuita, que inclui um locatário que permite o sideload de aplicativos, juntando-se ao programa Microsoft 365 desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="4e47c-113">You can get a free Teams test account, which includes a tenant that allows app sideloading, by joining the Microsoft 365 developer program.</span></span> <span data-ttu-id="4e47c-114">O processo de registro leva aproximadamente dois minutos.</span><span class="sxs-lookup"><span data-stu-id="4e47c-114">The registration process takes approximately two minutes.</span></span>

<span data-ttu-id="4e47c-115">**Para obter um locatário**</span><span class="sxs-lookup"><span data-stu-id="4e47c-115">**To get a tenant**</span></span>

1. <span data-ttu-id="4e47c-116">Vá para o programa [Microsoft 365 desenvolvedor.](https://developer.microsoft.com/microsoft-365/dev-program)</span><span class="sxs-lookup"><span data-stu-id="4e47c-116">Go to the [Microsoft 365 developer program](https://developer.microsoft.com/microsoft-365/dev-program).</span></span>
1. <span data-ttu-id="4e47c-117">Selecione **Ingressar agora** e siga as instruções na tela.</span><span class="sxs-lookup"><span data-stu-id="4e47c-117">Select **Join Now** and follow the onscreen instructions.</span></span>
1. <span data-ttu-id="4e47c-118">Na tela De boas-vindas, selecione **Configurar assinatura do E5**.</span><span class="sxs-lookup"><span data-stu-id="4e47c-118">In the Welcome screen, select **Set up E5 subscription**.</span></span>
1. <span data-ttu-id="4e47c-119">Configurar sua conta Microsoft 365 desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="4e47c-119">Set up your Microsoft 365 developer account.</span></span> 
   <span data-ttu-id="4e47c-120">Depois de concluir, a tela a seguir será exibida:</span><span class="sxs-lookup"><span data-stu-id="4e47c-120">After you finish, the following screen appears:</span></span>

   :::image type="content" source="../assets/images/build-your-first-app/dev-program-subscription.png" alt-text="Exemplo do que você vê depois de se inscrever no programa Microsoft 365 desenvolvedor.":::

1. <span data-ttu-id="4e47c-122">Entre no Teams com sua nova conta.</span><span class="sxs-lookup"><span data-stu-id="4e47c-122">Sign in to Teams with your new account.</span></span>
1. <span data-ttu-id="4e47c-123">No cliente Teams, selecione **Aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="4e47c-123">In the Teams client, select **Apps**.</span></span>
1. <span data-ttu-id="4e47c-124">Verifique se você pode ver o Upload **uma opção de aplicativo** personalizada.</span><span class="sxs-lookup"><span data-stu-id="4e47c-124">Verify that you can see the **Upload a custom app** option.</span></span> <span data-ttu-id="4e47c-125">Se fizer isso, isso significa que você pode fazer sideload de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="4e47c-125">If you do, this means you can sideload apps.</span></span>

   :::image type="content" source="../assets/images/build-your-first-app/upload-custom-app-closeup.png" alt-text="Ilustração mostrando onde Teams você pode carregar um aplicativo personalizado.":::

# <a name="have-a-tenant"></a>[<span data-ttu-id="4e47c-127">Ter um locatário</span><span class="sxs-lookup"><span data-stu-id="4e47c-127">Have a tenant</span></span>](#tab/have-a-tenant)

<span data-ttu-id="4e47c-128">Se você já tiver um locatário, verifique se pode fazer sideload de aplicativos Teams.</span><span class="sxs-lookup"><span data-stu-id="4e47c-128">If you already have a tenant, verify if you can sideload apps in Teams.</span></span>

<span data-ttu-id="4e47c-129">**Verifique se você pode fazer sideload de seus aplicativos**</span><span class="sxs-lookup"><span data-stu-id="4e47c-129">**Verify that you can sideload your apps**</span></span> 

1. <span data-ttu-id="4e47c-130">No cliente Teams, selecione **Aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="4e47c-130">In the Teams Client, select **Apps**.</span></span> 
1.  <span data-ttu-id="4e47c-131">Verifique se você pode ver o Upload **uma opção de aplicativo** personalizada.</span><span class="sxs-lookup"><span data-stu-id="4e47c-131">Verify that you can see the **Upload a custom app** option.</span></span> <span data-ttu-id="4e47c-132">Se fizer isso, isso significa que você pode fazer sideload de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="4e47c-132">If you do, this means you can sideload apps.</span></span> 

   :::image type="content" source="../assets/images/build-your-first-app/upload-custom-app-closeup.png" alt-text="Ilustração mostrando onde Teams você pode carregar um aplicativo personalizado.":::

---

### <a name="install-your-development-tools"></a><span data-ttu-id="4e47c-134">Instalar suas ferramentas de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="4e47c-134">Install your development tools</span></span>

<span data-ttu-id="4e47c-135">Para criar esse aplicativo, você usará o Teams Toolkit para Visual Studio Code começar rapidamente.</span><span class="sxs-lookup"><span data-stu-id="4e47c-135">To build this app, you'll use the Teams Toolkit for Visual Studio Code to quickly get started.</span></span> <span data-ttu-id="4e47c-136">Você também pode criar Teams aplicativos com qualquer uma de suas ferramentas prefered.</span><span class="sxs-lookup"><span data-stu-id="4e47c-136">You can also build Teams apps with any of your preffered tools.</span></span> 

> [!NOTE]
> <span data-ttu-id="4e47c-137">Teams exibe o conteúdo do aplicativo somente por meio de conexões HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4e47c-137">Teams displays app content only through HTTPS connections.</span></span> <span data-ttu-id="4e47c-138">Para depurar determinados tipos de aplicativos localmente, como um bot, você aprenderá a usar o ngrok para configurar um túnel seguro entre o Teams e seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4e47c-138">To debug certain types of apps locally, such as a bot, you'll learn how to use ngrok to set up a secure tunnel between Teams and your app.</span></span>
> 
> <span data-ttu-id="4e47c-139">Os Teams de produção são hospedados na nuvem.</span><span class="sxs-lookup"><span data-stu-id="4e47c-139">Production Teams apps are hosted in the cloud.</span></span>

<span data-ttu-id="4e47c-140">**Para instalar Microsoft Teams ferramentas**</span><span class="sxs-lookup"><span data-stu-id="4e47c-140">**To install Microsoft Teams tools**</span></span>

1. <span data-ttu-id="4e47c-141">Instale o [Node.js](https://nodejs.org/en/).</span><span class="sxs-lookup"><span data-stu-id="4e47c-141">Install [Node.js](https://nodejs.org/en/).</span></span>
1. <span data-ttu-id="4e47c-142">Se você planeja criar um bot ou extensão de mensagens, instale [o ngrok](https://ngrok.com/download) e exponha seu localhost à [Internet usando ngrok](../tutorials/get-started-dotnet-app-studio.md#tunnel-using-ngrok).</span><span class="sxs-lookup"><span data-stu-id="4e47c-142">If you plan to build a bot or messaging extension, install [ngrok](https://ngrok.com/download) and [expose your localhost to the Internet using ngrok](../tutorials/get-started-dotnet-app-studio.md#tunnel-using-ngrok).</span></span>
1. <span data-ttu-id="4e47c-143">Instale a versão mais recente [do Visual Studio Code](https://code.visualstudio.com/download).</span><span class="sxs-lookup"><span data-stu-id="4e47c-143">Install the latest version of [Visual Studio Code](https://code.visualstudio.com/download).</span></span> 
   
   > [!NOTE]
   > <span data-ttu-id="4e47c-144">O kit de ferramentas não dá suporte a versões anteriores Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="4e47c-144">The toolkit does not support earlier versions of Visual Studio Code.</span></span>

1. Na barra de atividades esquerda, selecione **Extensões** :::image type="icon" source="../assets/icons/vs-code-extensions.png"::: .
1. <span data-ttu-id="4e47c-146">Em **Microsoft Teams Toolkit,** selecione **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="4e47c-146">In **Microsoft Teams Toolkit**, select **Install**.</span></span>

   :::image type="content" source="../assets/images/build-your-first-app/vsc-install-toolkit.png" alt-text="Ilustração mostrando onde Visual Studio Code você pode instalar a extensão Microsoft Teams Toolkit.":::

## <a name="1-create-your-app-project"></a><span data-ttu-id="4e47c-148">1. Crie seu projeto de aplicativo</span><span class="sxs-lookup"><span data-stu-id="4e47c-148">1. Create your app project</span></span>

1. <span data-ttu-id="4e47c-149">Abra Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="4e47c-149">Open Visual Studio Code.</span></span>
1. Selecione **Microsoft Teams Toolkit** :::image type="icon" source="../assets/icons/vsc-toolkit.png":::  >  **Criar um novo Teams app**.

   :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-02.png" alt-text="Captura de tela mostrando como criar seu projeto de aplicativo com o Visual Studio Code Teams Toolkit.":::
   
1. <span data-ttu-id="4e47c-152">Entre com sua conta Microsoft 365 de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="4e47c-152">Sign in with your Microsoft 365 development account.</span></span> <span data-ttu-id="4e47c-153">A que você acabou de criar ou a conta que você já tinha que permite o sideload do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4e47c-153">Either the one you just created or the account you already had that allows app sideloading.</span></span>
1. <span data-ttu-id="4e47c-154">Na tela **Selecionar projeto,** vá para **Aplicativo Pessoal** e selecione **JS** (JavaScript) > **Próximo.**</span><span class="sxs-lookup"><span data-stu-id="4e47c-154">On the **Select project** screen, go to **Personal app** and select **JS** (JavaScript) > **Next**.</span></span>

   :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-03.png" alt-text="Captura de tela mostrando como configurar seu projeto de aplicativo com o Visual Studio Code Teams Toolkit.":::

1. <span data-ttu-id="4e47c-156">Insira um nome para seu Teams app.</span><span class="sxs-lookup"><span data-stu-id="4e47c-156">Enter a name for your Teams app.</span></span>

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-04.png" alt-text="Captura de tela mostrando como adicionar um nome ao seu projeto de aplicativo com o Visual Studio Code Teams Toolkit.":::

1. <span data-ttu-id="4e47c-158">Selecione **Concluir**.</span><span class="sxs-lookup"><span data-stu-id="4e47c-158">Select **Finish**.</span></span> 
   <span data-ttu-id="4e47c-159">Seu projeto agora está configurado.</span><span class="sxs-lookup"><span data-stu-id="4e47c-159">Your project is now configured.</span></span> 

## <a name="2-understand-your-app-project-components"></a><span data-ttu-id="4e47c-160">2. Entenda os componentes do projeto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="4e47c-160">2. Understand your app project components</span></span>

<span data-ttu-id="4e47c-161">Depois que o kit de ferramentas configurar seu projeto de aplicativo, você terá os componentes para criar seu "Hello, World!"</span><span class="sxs-lookup"><span data-stu-id="4e47c-161">After the toolkit configures your app project, you have the components to build your "Hello, World!"</span></span> <span data-ttu-id="4e47c-162">Teams aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4e47c-162">Teams app.</span></span> <span data-ttu-id="4e47c-163">Os diretórios e arquivos do projeto estão localizados no Visual Studio Code Explorer.</span><span class="sxs-lookup"><span data-stu-id="4e47c-163">The project's directories and files are located in the Visual Studio Code Explorer.</span></span> 

   :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-05.png" alt-text="Captura de tela mostrando o scaffolding em seu projeto de aplicativo com o Visual Studio Code Teams Toolkit.":::

<span data-ttu-id="4e47c-165">O kit de ferramentas cria automaticamente o scaffolding de aplicativos no `src` diretório com base nos recursos adicionados durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="4e47c-165">The toolkit automatically creates app scaffolding in the `src` directory based on the capabilities you added during setup.</span></span> <span data-ttu-id="4e47c-166">Desde que você criou uma guia durante a instalação, o arquivo no diretório lida com a inicialização e o `App.js` `src/components` roteamento do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4e47c-166">Since you created a tab during setup, the `App.js` file in the `src/components` directory handles the initialization and routing of your app.</span></span> <span data-ttu-id="4e47c-167">O arquivo também chama o Microsoft Teams SDK do cliente JavaScript para estabelecer a comunicação entre seu aplicativo e Teams.</span><span class="sxs-lookup"><span data-stu-id="4e47c-167">The file also calls the Microsoft Teams JavaScript client SDK to establish communication between your app and Teams.</span></span> 

## <a name="3-build-and-run-your-app"></a><span data-ttu-id="4e47c-168">3. Crie e execute seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="4e47c-168">3. Build and run your app</span></span>

<span data-ttu-id="4e47c-169">Crie e execute seu aplicativo localmente para economizar tempo.</span><span class="sxs-lookup"><span data-stu-id="4e47c-169">Build and run your app locally to save time.</span></span> 

<span data-ttu-id="4e47c-170">**Para criar e executar seu aplicativo**</span><span class="sxs-lookup"><span data-stu-id="4e47c-170">**To build and run your app**</span></span>

1. <span data-ttu-id="4e47c-171">Em Visual Studio Code, selecione **Exibir**  >  **Terminal**.</span><span class="sxs-lookup"><span data-stu-id="4e47c-171">In Visual Studio Code, select **View** > **Terminal**.</span></span>
1. <span data-ttu-id="4e47c-172">Executar `npm install` .</span><span class="sxs-lookup"><span data-stu-id="4e47c-172">Run `npm install`.</span></span>
1. <span data-ttu-id="4e47c-173">Executar `npm start` .</span><span class="sxs-lookup"><span data-stu-id="4e47c-173">Run `npm start`.</span></span>
  
  <span data-ttu-id="4e47c-174">Compilado **com êxito!**</span><span class="sxs-lookup"><span data-stu-id="4e47c-174">A **Compiled successfully!**</span></span> <span data-ttu-id="4e47c-175">aparece no terminal.</span><span class="sxs-lookup"><span data-stu-id="4e47c-175">message appears in the terminal.</span></span> <span data-ttu-id="4e47c-176">Seu aplicativo agora está sendo executado em seu localhost em `https://localhost:3000` .</span><span class="sxs-lookup"><span data-stu-id="4e47c-176">Your app is now running on your localhost at `https://localhost:3000`.</span></span> 

## <a name="4-sideload-your-app-in-teams"></a><span data-ttu-id="4e47c-177">4. Fazer sideload do aplicativo no Teams</span><span class="sxs-lookup"><span data-stu-id="4e47c-177">4. Sideload your app in Teams</span></span>

<span data-ttu-id="4e47c-178">Sideload é o processo de instalação de um aplicativo no Teams que não foi aprovado pelo administrador ou pela Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4e47c-178">Sideloading is the process of installing an app in Teams that hasn't been approved by your admin or Microsoft.</span></span> <span data-ttu-id="4e47c-179">O sideload é comum ao testar e depurar Teams aplicativos.</span><span class="sxs-lookup"><span data-stu-id="4e47c-179">Sideloading is common when testing and debugging Teams apps.</span></span>

<span data-ttu-id="4e47c-180">Por padrão, Teams não permite o sideload do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4e47c-180">By default, Teams doesn't allow app sideloading.</span></span> <span data-ttu-id="4e47c-181">Você pode alterar essa configuração no Teams de administração.</span><span class="sxs-lookup"><span data-stu-id="4e47c-181">You can change this setting in the Teams admin center.</span></span>

<span data-ttu-id="4e47c-182">**Para habilitar o sideload de aplicativos Teams**</span><span class="sxs-lookup"><span data-stu-id="4e47c-182">**To enable app sideloading in Teams**</span></span>

1. <span data-ttu-id="4e47c-183">Entre no centro de administração [Microsoft 365 com](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) suas credenciais de administrador.</span><span class="sxs-lookup"><span data-stu-id="4e47c-183">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) with your admin credentials.</span></span>  
1. <span data-ttu-id="4e47c-184">Selecione **Mostrar todos os**  >  **Teams**.</span><span class="sxs-lookup"><span data-stu-id="4e47c-184">Select **Show All** > **Teams**.</span></span> 

   ![imagem do menu do centro de administração](~/assets/images/prepare-test-tenant/admin-center.png)

   > [!Note] 
   > <span data-ttu-id="4e47c-186">Pode levar até 24 horas para que a opção **Teams** apareça.</span><span class="sxs-lookup"><span data-stu-id="4e47c-186">It can take up to 24 hours for the **Teams** option to appear.</span></span> 

1. <span data-ttu-id="4e47c-187">Vá para **Teams políticas de instalação**  >  **de**  >  **aplicativos Global** (padrão em toda a organização).</span><span class="sxs-lookup"><span data-stu-id="4e47c-187">Go to **Teams apps** > **Setup policies** > **Global** (Org-wide default).</span></span>

   ![ativar o sideload view](~/assets/images/prepare-test-tenant/turn-on-sideload.png)

1. <span data-ttu-id="4e47c-189">Ativar a **alternância carregar aplicativos personalizados.**</span><span class="sxs-lookup"><span data-stu-id="4e47c-189">Turn on the **upload custom apps** toggle.</span></span>

1. <span data-ttu-id="4e47c-190">Selecione **Salvar** para salvar as alterações.</span><span class="sxs-lookup"><span data-stu-id="4e47c-190">Select **Save** to save the changes.</span></span>

   <span data-ttu-id="4e47c-191">Seu locatário de teste agora permite o sideload de aplicativo personalizado.</span><span class="sxs-lookup"><span data-stu-id="4e47c-191">Your test tenant now allows custom app sideloading.</span></span>

   > [!Note]
   > <span data-ttu-id="4e47c-192">Verifique se há problemas antes de fazer sideload do aplicativo usando o recurso de validação no App Studio, que está incluído no kit de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="4e47c-192">Check for issues before sideloading your app using the validation feature in App Studio, which is included in the toolkit.</span></span> <span data-ttu-id="4e47c-193">Correção dos erros para fazer sideload com êxito do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4e47c-193">Fix the errors to successfully sideload the app.</span></span>


### <a name="sideload-your-app"></a><span data-ttu-id="4e47c-194">Fazer sideload do aplicativo</span><span class="sxs-lookup"><span data-stu-id="4e47c-194">Sideload your app</span></span>

1. <span data-ttu-id="4e47c-195">Em Visual Studio Code, abra o Teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="4e47c-195">In Visual Studio Code, open the Teams Toolkit.</span></span>
1. <span data-ttu-id="4e47c-196">Vá para **App Studio**.</span><span class="sxs-lookup"><span data-stu-id="4e47c-196">Go to **App Studio**.</span></span>  
1. <span data-ttu-id="4e47c-197">Selecione **Testar e Distribuir**  >  **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="4e47c-197">Select **Test and Distribute** > **Install**.</span></span>

   :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-appstudio.png" alt-text="Captura de tela mostrando como fazer sideload do aplicativo para Teams cliente com o Visual Studio Code Teams Toolkit.":::

<span data-ttu-id="4e47c-199">**Como alternativa**</span><span class="sxs-lookup"><span data-stu-id="4e47c-199">**Alternatively**</span></span>

1. <span data-ttu-id="4e47c-200">Selecione a **chave F5** para abrir a janela do navegador para instalar.</span><span class="sxs-lookup"><span data-stu-id="4e47c-200">Select the **F5** key to open browser window to install.</span></span> <span data-ttu-id="4e47c-201">Isso ignorará o processo de instalação no **App Studio** e Teams no navegador.</span><span class="sxs-lookup"><span data-stu-id="4e47c-201">This will skip the installation process in the **App Studio** and lauch Teams in your browser.</span></span>
1. <span data-ttu-id="4e47c-202">Na caixa de diálogo instalação, selecione **Adicionar** para instalar seu aplicativo Teams.</span><span class="sxs-lookup"><span data-stu-id="4e47c-202">In the installation dialog, select **Add** to install your app to Teams.</span></span>

   :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-install.png" alt-text="Captura de tela mostrando como fazer sideload do aplicativo para Teams cliente.":::

   > [!Note]
   > <span data-ttu-id="4e47c-204">O App Studio também está disponível como um aplicativo autônomo para Teams cliente.</span><span class="sxs-lookup"><span data-stu-id="4e47c-204">App Studio is also available as a stand-alone app for Teams client.</span></span>

### <a name="troubleshoot-sideloading-issues"></a><span data-ttu-id="4e47c-205">Solucionar problemas de sideload</span><span class="sxs-lookup"><span data-stu-id="4e47c-205">Troubleshoot sideloading issues</span></span>

<span data-ttu-id="4e47c-206">**Falha na instalação**</span><span class="sxs-lookup"><span data-stu-id="4e47c-206">**Installation failed**</span></span>

<span data-ttu-id="4e47c-207">Se a `Manifest parsing has failed` mensagem de erro for exibida durante a instalação do aplicativo, verifique se as informações do aplicativo foram inseridas corretamente.</span><span class="sxs-lookup"><span data-stu-id="4e47c-207">If the `Manifest parsing has failed` error message appears while installing your app, verify that the app information is correctly entered.</span></span>

<span data-ttu-id="4e47c-208">**Para verificar as informações do aplicativo**</span><span class="sxs-lookup"><span data-stu-id="4e47c-208">**To verify the app information**</span></span>

* <span data-ttu-id="4e47c-209">Na Teams Toolkit, vá para **Detalhes** do App Studio App e verifique se todas as informações necessárias  >   foram inseridas corretamente.</span><span class="sxs-lookup"><span data-stu-id="4e47c-209">In the Teams Toolkit, go to **App Studio** > **App details** and verify that all the required information is correctly entered.</span></span>
*  <span data-ttu-id="4e47c-210">Se você editou manualmente o arquivo, verifique se o JSON está bem definido na ferramenta Manifesto do Aplicativo `manifest.json` no App Studio. </span><span class="sxs-lookup"><span data-stu-id="4e47c-210">If you manually edited the `manifest.json` file, verify that the JSON is well-defined in the **App Manifest** tool in App Studio.</span></span>

<span data-ttu-id="4e47c-211">**Conteúdo de tabulação não exibido**</span><span class="sxs-lookup"><span data-stu-id="4e47c-211">**Tab content not displayed**</span></span>

<span data-ttu-id="4e47c-212">Verifique se seu aplicativo está em execução.</span><span class="sxs-lookup"><span data-stu-id="4e47c-212">Verify that your app is running.</span></span> <span data-ttu-id="4e47c-213">Se não estiver, vá para o terminal e execute `npm start` .</span><span class="sxs-lookup"><span data-stu-id="4e47c-213">If it isn't, go to the terminal and run `npm start`.</span></span>

## <a name="see-also"></a><span data-ttu-id="4e47c-214">Confira também</span><span class="sxs-lookup"><span data-stu-id="4e47c-214">See also</span></span>

* [<span data-ttu-id="4e47c-215">Preparar o locatário do Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="4e47c-215">Prepare your Microsoft 365 tenant</span></span>](https://docs.microsoft.com/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant)
* [<span data-ttu-id="4e47c-216">Escolher uma instalação para testar e depurar seu Microsoft Teams app</span><span class="sxs-lookup"><span data-stu-id="4e47c-216">Choosing a setup to test and debug your Microsoft Teams app</span></span>](../concepts/build-and-test/debug.md)
* [<span data-ttu-id="4e47c-217">Criando guias e outras experiências hospedadas com o SDK do cliente JavaScript Microsoft Teams JavaScript</span><span class="sxs-lookup"><span data-stu-id="4e47c-217">Building tabs and other hosted experiences with the Microsoft Teams JavaScript client SDK</span></span>](../tabs/how-to/using-teams-client-sdk.md)
* [<span data-ttu-id="4e47c-218">Preparar para envio do AppSource</span><span class="sxs-lookup"><span data-stu-id="4e47c-218">Prepare for AppSource submission</span></span>](../concepts/deploy-and-publish/appsource/prepare/submission-checklist.md)
* [<span data-ttu-id="4e47c-219">Desenvolva aplicativos rapidamente com o App Studio para Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="4e47c-219">Quickly develop apps with App Studio for Microsoft Teams</span></span>](../concepts/build-and-test/app-studio-overview.md)
* [<span data-ttu-id="4e47c-220">Construir uma guia de canal</span><span class="sxs-lookup"><span data-stu-id="4e47c-220">Build a channel tab</span></span>](../build-your-first-app/build-channel-tab.md)

## <a name="next-step"></a><span data-ttu-id="4e47c-221">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="4e47c-221">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4e47c-222">Crie uma guia pessoal para Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="4e47c-222">Build a personal tab for Microsoft Teams</span></span>](../build-your-first-app/build-personal-tab.md)
