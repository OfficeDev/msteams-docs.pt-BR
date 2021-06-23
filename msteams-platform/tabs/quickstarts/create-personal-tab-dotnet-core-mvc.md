---
title: Crie uma guia pessoal com ASP. NET Core MVC
author: surbhigupta
description: Um guia de início rápido para criar uma guia pessoal personalizada com ASP. NET Core MVC.
localization_priority: Normal
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: ac01ae64f44ccf3e06476d4412b16ac9a4730f6c
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069154"
---
# <a name="create-a-custom-personal-tab-with-aspnet-core-mvc"></a><span data-ttu-id="494a0-105">Criar uma guia pessoal personalizada com ASP.NET Core MVC</span><span class="sxs-lookup"><span data-stu-id="494a0-105">Create a Custom Personal Tab with ASP.NET Core MVC</span></span>

<span data-ttu-id="494a0-106">Neste início rápido, vamos passo a passo criando uma guia pessoal personalizada com C# e ASP.Net Core MVC.</span><span class="sxs-lookup"><span data-stu-id="494a0-106">In this quickstart we'll walk-through creating a custom personal tab with C# and ASP.Net Core MVC.</span></span> <span data-ttu-id="494a0-107">Também vamos usar o [App Studio para Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) finalizar o manifesto do aplicativo e implantar sua guia Teams.</span><span class="sxs-lookup"><span data-stu-id="494a0-107">We'll also use [App Studio for Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) to finalize your app manifest and deploy your tab to Teams.</span></span>

[!INCLUDE [dotnet-core-prereq](~/includes/tabs/dotnet-core-prereq.md)]

## <a name="get-the-source-code"></a><span data-ttu-id="494a0-108">Obter o código-fonte</span><span class="sxs-lookup"><span data-stu-id="494a0-108">Get the source code</span></span>

<span data-ttu-id="494a0-109">Abra um prompt de comando e crie um novo diretório para seu projeto de guia.</span><span class="sxs-lookup"><span data-stu-id="494a0-109">Open a command prompt and create a new directory for your tab project.</span></span> <span data-ttu-id="494a0-110">Fornecemos um projeto simples para você começar.</span><span class="sxs-lookup"><span data-stu-id="494a0-110">We have provided a simple project to get you started.</span></span> <span data-ttu-id="494a0-111">Para recuperar o código-fonte, você pode baixar a pasta zip e extrair os arquivos ou clonar o repositório de exemplo em seu novo diretório:</span><span class="sxs-lookup"><span data-stu-id="494a0-111">To retrieve the source code you can download the zip folder and extract the files or clone the sample repository into your new directory:</span></span>

``` bash
git clone https://github.com/OfficeDev/microsoft-teams-sample-tabs.git
```

<span data-ttu-id="494a0-112">Depois de ter o código-fonte, abra Visual Studio e selecione **Abrir um projeto ou solução**.</span><span class="sxs-lookup"><span data-stu-id="494a0-112">Once you have the source code, open Visual Studio and select **Open a project or solution**.</span></span> <span data-ttu-id="494a0-113">Navegue até o diretório do aplicativo de tabulação e abra **PersonalTabMVC.sln**.</span><span class="sxs-lookup"><span data-stu-id="494a0-113">Navigate to the tab application directory and open **PersonalTabMVC.sln**.</span></span>

<span data-ttu-id="494a0-114">Para criar e executar seu aplicativo pressione **F5** ou escolha **Iniciar Depuração** no menu **Depurar.**</span><span class="sxs-lookup"><span data-stu-id="494a0-114">To build and run your application press **F5** or choose **Start Debugging** from the **Debug** menu.</span></span> <span data-ttu-id="494a0-115">Em um navegador, navegue até as URLs abaixo para verificar se o aplicativo foi carregado corretamente:</span><span class="sxs-lookup"><span data-stu-id="494a0-115">In a browser navigate to the URLs below to verify that the application loaded properly:</span></span>

* `http://localhost:44335`
* `http://localhost:44335/privacy`
* `http://localhost:44335/tou`

## <a name="review-the-source-code"></a><span data-ttu-id="494a0-116">Revisar o código-fonte</span><span class="sxs-lookup"><span data-stu-id="494a0-116">Review the source code</span></span>

### <a name="startupcs"></a><span data-ttu-id="494a0-117">Startup.cs</span><span class="sxs-lookup"><span data-stu-id="494a0-117">Startup.cs</span></span>

<span data-ttu-id="494a0-118">Esse projeto foi criado a partir de um ASP.</span><span class="sxs-lookup"><span data-stu-id="494a0-118">This project was created from an ASP.</span></span> <span data-ttu-id="494a0-119">Modelo vazio do Aplicativo Web net Core 2.2 com a caixa de seleção *Avançado - Configurar para HTTPS* selecionada na instalação.</span><span class="sxs-lookup"><span data-stu-id="494a0-119">NET Core 2.2 Web Application empty template with the *Advanced - Configure for HTTPS* check box selected at setup.</span></span> <span data-ttu-id="494a0-120">Os serviços MVC são registrados pelo método da estrutura de injeção de `ConfigureServices()` dependência.</span><span class="sxs-lookup"><span data-stu-id="494a0-120">The MVC services are registered by the dependency injection framework's `ConfigureServices()` method.</span></span> <span data-ttu-id="494a0-121">Além disso, o modelo vazio não habilita o serviço de conteúdo estático por padrão, portanto, o middleware de arquivos estáticos é adicionado ao `Configure()` método:</span><span class="sxs-lookup"><span data-stu-id="494a0-121">Additionally, the empty template doesn't enable serving static content by default, so the static files middleware is added to the `Configure()` method:</span></span>

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

### <a name="wwwroot-folder"></a><span data-ttu-id="494a0-122">pasta wwwroot</span><span class="sxs-lookup"><span data-stu-id="494a0-122">wwwroot folder</span></span>

<span data-ttu-id="494a0-123">Em ASP.</span><span class="sxs-lookup"><span data-stu-id="494a0-123">In ASP.</span></span> <span data-ttu-id="494a0-124">NET Core, a pasta raiz da Web é onde o aplicativo procura arquivos estáticos.</span><span class="sxs-lookup"><span data-stu-id="494a0-124">NET Core, the web root folder is where the application looks for static files.</span></span>

### <a name="appmanifest-folder"></a><span data-ttu-id="494a0-125">Pasta AppManifest</span><span class="sxs-lookup"><span data-stu-id="494a0-125">AppManifest folder</span></span>

<span data-ttu-id="494a0-126">Esta pasta contém os seguintes arquivos de pacote de aplicativos necessários:</span><span class="sxs-lookup"><span data-stu-id="494a0-126">This folder contains the following required app package files:</span></span>

* <span data-ttu-id="494a0-127">Um **ícone de cor completo** medindo 192 x 192 pixels.</span><span class="sxs-lookup"><span data-stu-id="494a0-127">A **full color icon** measuring 192 x 192 pixels.</span></span>
* <span data-ttu-id="494a0-128">Um **ícone de contorno transparente** medindo 32 x 32 pixels.</span><span class="sxs-lookup"><span data-stu-id="494a0-128">A **transparent outline icon** measuring 32 x 32 pixels.</span></span>
* <span data-ttu-id="494a0-129">Um **manifest.json** que especifica os atributos do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="494a0-129">A **manifest.json** file that specifies the attributes of your app.</span></span>

<span data-ttu-id="494a0-130">Esses arquivos precisam ser cortados em um pacote de aplicativos para uso ao carregar sua guia para Teams.</span><span class="sxs-lookup"><span data-stu-id="494a0-130">These files need to be zipped in an app package for use in uploading your tab to Teams.</span></span> <span data-ttu-id="494a0-131">Microsoft Teams carregará o especificado em seu manifesto, o inserirá em um IFrame e `contentUrl` o renderizará em sua guia.</span><span class="sxs-lookup"><span data-stu-id="494a0-131">Microsoft Teams will load the `contentUrl` specified in your manifest, embed it in an IFrame, and render it in your tab.</span></span>

### <a name="csproj"></a><span data-ttu-id="494a0-132">.csproj</span><span class="sxs-lookup"><span data-stu-id="494a0-132">.csproj</span></span>

<span data-ttu-id="494a0-133">Na janela Visual Studio Do Explorador de Soluções clique com o botão direito do mouse no projeto e selecione **Editar Project Arquivo**.</span><span class="sxs-lookup"><span data-stu-id="494a0-133">In the Visual Studio Solution Explorer window right-click on the project and select **Edit Project File**.</span></span> <span data-ttu-id="494a0-134">Na parte inferior do arquivo, você verá o código que cria e atualiza sua pasta zip quando o aplicativo é construído:</span><span class="sxs-lookup"><span data-stu-id="494a0-134">At the bottom of the file you'll see the code that creates and updates your zip folder when the application builds:</span></span>

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

### <a name="models"></a><span data-ttu-id="494a0-135">Modelos</span><span class="sxs-lookup"><span data-stu-id="494a0-135">Models</span></span>

<span data-ttu-id="494a0-136">**PersonalTab.cs** apresenta um objeto Message e métodos que serão chamados de *PersonalTabController* quando um usuário selecionar um botão no Modo de Exibição **PersonalTab.**</span><span class="sxs-lookup"><span data-stu-id="494a0-136">**PersonalTab.cs** presents a Message object and methods that will be called from *PersonalTabController* when a user selects a button in the **PersonalTab** View.</span></span>

### <a name="views"></a><span data-ttu-id="494a0-137">Exibições</span><span class="sxs-lookup"><span data-stu-id="494a0-137">Views</span></span>

#### <a name="home"></a><span data-ttu-id="494a0-138">Página Inicial</span><span class="sxs-lookup"><span data-stu-id="494a0-138">Home</span></span>

<span data-ttu-id="494a0-139">ASP.</span><span class="sxs-lookup"><span data-stu-id="494a0-139">ASP.</span></span> <span data-ttu-id="494a0-140">O NET Core trata os arquivos chamados **Index** como o padrão ou home page do site.</span><span class="sxs-lookup"><span data-stu-id="494a0-140">NET Core treats files called **Index** as the default or home page for the site.</span></span> <span data-ttu-id="494a0-141">Quando a URL do navegador aponta para a raiz do site, **Index.cshtml** será exibida como a home page do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="494a0-141">When your browser URL points to the root of the site, **Index.cshtml** will be displayed as the home page for your application.</span></span>

#### <a name="shared"></a><span data-ttu-id="494a0-142">Compartilhados</span><span class="sxs-lookup"><span data-stu-id="494a0-142">Shared</span></span>

<span data-ttu-id="494a0-143">A marcação de exibição *parcial _Layout.cshtml* contém a estrutura geral da página do aplicativo e elementos visuais compartilhados.</span><span class="sxs-lookup"><span data-stu-id="494a0-143">The partial view markup *_Layout.cshtml* contains the application's overall page structure and shared visual elements.</span></span> <span data-ttu-id="494a0-144">Ele também fará referência à biblioteca Teams.</span><span class="sxs-lookup"><span data-stu-id="494a0-144">It will also reference the Teams Library.</span></span>

### <a name="controllers"></a><span data-ttu-id="494a0-145">Controladores</span><span class="sxs-lookup"><span data-stu-id="494a0-145">Controllers</span></span>

<span data-ttu-id="494a0-146">Os controladores usam a propriedade ViewBag para transferir valores dinamicamente para o Views.</span><span class="sxs-lookup"><span data-stu-id="494a0-146">The controllers use the ViewBag property to transfer values dynamically to the Views.</span></span>

[!INCLUDE [dotnet-update-personal-app](~/includes/tabs/dotnet-update-personal-app.md)]

[!INCLUDE [dotnet-ngrok-intro](~/includes/tabs/dotnet-ngrok-intro.md)]

* <span data-ttu-id="494a0-147">Abra um prompt de comando na raiz do diretório do projeto e execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="494a0-147">Open a command prompt in the root of your project directory and run the following command:</span></span>

    ``` bash
    ngrok http https://localhost:44345 -host-header="localhost:44345"
    ```

* <span data-ttu-id="494a0-148">O Ngrok ouvirá as solicitações da Internet e as encaminhará para seu aplicativo quando estiver sendo executado na porta 44325.</span><span class="sxs-lookup"><span data-stu-id="494a0-148">Ngrok will listen to requests from the internet and will route them to your application when it is running on port 44325.</span></span>  <span data-ttu-id="494a0-149">Deve parecer `https://y8rPrT2b.ngrok.io/` onde *y8rPrT2b* é substituído pela URL HTTPS alfanumérico ngrok.</span><span class="sxs-lookup"><span data-stu-id="494a0-149">It should resemble `https://y8rPrT2b.ngrok.io/` where *y8rPrT2b* is replaced by your ngrok alpha-numeric HTTPS URL.</span></span>

* <span data-ttu-id="494a0-150">Certifique-se de manter o prompt de comando com o ngrok em execução e para anotar a URL , você precisará dele mais tarde.</span><span class="sxs-lookup"><span data-stu-id="494a0-150">Be sure to keep the command prompt with ngrok running, and to make a note of the URL — you'll need it later.</span></span>

* <span data-ttu-id="494a0-151">Verifique se **o ngrok** está sendo executado e funcionando corretamente abrindo seu navegador e indo para sua página de conteúdo por meio da URL HTTPS ngrok fornecida na janela do prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="494a0-151">Verify that **ngrok** is running and working properly by opening your browser and going to your content page via the ngrok HTTPS URL that was provided in your command prompt window.</span></span>

> [!TIP]
> <span data-ttu-id="494a0-152">Você precisa ter seu aplicativo em Visual Studio e ngrok em execução para concluir esse início rápido.</span><span class="sxs-lookup"><span data-stu-id="494a0-152">You need to have both your application in Visual Studio and ngrok running to complete this quickstart.</span></span> <span data-ttu-id="494a0-153">Se você precisar parar de executar seu aplicativo Visual Studio para trabalhar nele, **mantenha o ngrok em execução**.</span><span class="sxs-lookup"><span data-stu-id="494a0-153">If you need to stop running your application in Visual Studio to work on it, **keep ngrok running**.</span></span> <span data-ttu-id="494a0-154">Ele continuará escutando e retomará o roteamento da solicitação do aplicativo quando ele for reiniciado no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="494a0-154">It will continue to listen and will resume routing your application's request when it restarts in Visual Studio.</span></span> <span data-ttu-id="494a0-155">Se você precisar reiniciar o serviço ngrok, ele retornará uma nova URL e será preciso atualizar todos os lugares que usam essa URL.</span><span class="sxs-lookup"><span data-stu-id="494a0-155">If you have to restart the ngrok service it will return a new URL and you'll have to update every place that uses that URL.</span></span>

### <a name="run-your-application"></a><span data-ttu-id="494a0-156">Executar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="494a0-156">Run your application</span></span>

* <span data-ttu-id="494a0-157">Em Visual Studio pressione **F5** ou escolha **Iniciar Depuração** no menu **Depuração do** aplicativo.</span><span class="sxs-lookup"><span data-stu-id="494a0-157">In Visual Studio press **F5** or choose **Start Debugging** from your application's **Debug** menu.</span></span>

[!INCLUDE [dotnet-personal-use-appstudio](~/includes/tabs/dotnet-personal-use-appstudio.md)]

## <a name="next-step"></a><span data-ttu-id="494a0-158">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="494a0-158">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="494a0-159">Crie um canal personalizado e uma guia de grupo usando Node.js e o Gerador Yeoman para Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="494a0-159">Create a custom channel and group tab using Node.js and the Yeoman Generator for Microsoft Teams</span></span>](~/tabs/quickstarts/create-channel-group-tab-node-yeoman.md)
