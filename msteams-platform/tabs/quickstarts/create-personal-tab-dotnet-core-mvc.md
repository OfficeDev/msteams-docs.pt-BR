---
title: Crie uma guia pessoal com ASP. NET Core MVC
author: laujan
description: Um guia de início rápido para criar uma guia pessoal personalizada com ASP. NET Core MVC.
localization_priority: Normal
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: 3ec6b5c054384653e30e46cbffed4a2af6662c33
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019563"
---
# <a name="create-a-custom-personal-tab-with-asp-net-core-mvc"></a><span data-ttu-id="e4a7c-105">Crie uma guia pessoal personalizada com ASP.</span><span class="sxs-lookup"><span data-stu-id="e4a7c-105">Create a Custom Personal Tab with ASP.</span></span> <span data-ttu-id="e4a7c-106">NET Core MVC</span><span class="sxs-lookup"><span data-stu-id="e4a7c-106">NET Core MVC</span></span>

<span data-ttu-id="e4a7c-107">Neste início rápido, vamos passo a passo criando uma guia pessoal personalizada com C# e ASP.</span><span class="sxs-lookup"><span data-stu-id="e4a7c-107">In this quickstart we'll walk-through creating a custom personal tab with C# and ASP.</span></span> <span data-ttu-id="e4a7c-108">Net Core MVC.</span><span class="sxs-lookup"><span data-stu-id="e4a7c-108">Net Core MVC.</span></span> <span data-ttu-id="e4a7c-109">Também vamos usar o [App Studio para o Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) para finalizar o manifesto do aplicativo e implantar sua guia no Teams.</span><span class="sxs-lookup"><span data-stu-id="e4a7c-109">We'll also use [App Studio for Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) to finalize your app manifest and deploy your tab to Teams.</span></span>

[!INCLUDE [dotnet-core-prereq](~/includes/tabs/dotnet-core-prereq.md)]

## <a name="get-the-source-code"></a><span data-ttu-id="e4a7c-110">Obter o código-fonte</span><span class="sxs-lookup"><span data-stu-id="e4a7c-110">Get the source code</span></span>

<span data-ttu-id="e4a7c-111">Abra um prompt de comando e crie um novo diretório para seu projeto de guia.</span><span class="sxs-lookup"><span data-stu-id="e4a7c-111">Open a command prompt and create a new directory for your tab project.</span></span> <span data-ttu-id="e4a7c-112">Fornecemos um projeto simples para você começar.</span><span class="sxs-lookup"><span data-stu-id="e4a7c-112">We have provided a simple project to get you started.</span></span> <span data-ttu-id="e4a7c-113">Para recuperar o código-fonte, você pode baixar a pasta zip e extrair os arquivos ou clonar o repositório de exemplo em seu novo diretório:</span><span class="sxs-lookup"><span data-stu-id="e4a7c-113">To retrieve the source code you can download the zip folder and extract the files or clone the sample repository into your new directory:</span></span>

``` bash
git clone https://github.com/OfficeDev/microsoft-teams-sample-tabs.git
```

<span data-ttu-id="e4a7c-114">Depois de ter o código-fonte, abra Visual Studio e selecione **Abrir um projeto ou solução**.</span><span class="sxs-lookup"><span data-stu-id="e4a7c-114">Once you have the source code, open Visual Studio and select **Open a project or solution**.</span></span> <span data-ttu-id="e4a7c-115">Navegue até o diretório do aplicativo de tabulação e abra **PersonalTabMVC.sln**.</span><span class="sxs-lookup"><span data-stu-id="e4a7c-115">Navigate to the tab application directory and open **PersonalTabMVC.sln**.</span></span>

<span data-ttu-id="e4a7c-116">Para criar e executar seu aplicativo pressione **F5** ou escolha **Iniciar Depuração** no menu **Depurar.**</span><span class="sxs-lookup"><span data-stu-id="e4a7c-116">To build and run your application press **F5** or choose **Start Debugging** from the **Debug** menu.</span></span> <span data-ttu-id="e4a7c-117">Em um navegador, navegue até as URLs abaixo para verificar se o aplicativo foi carregado corretamente:</span><span class="sxs-lookup"><span data-stu-id="e4a7c-117">In a browser navigate to the URLs below to verify that the application loaded properly:</span></span>

* `http://localhost:44335`
* `http://localhost:44335/privacy`
* `http://localhost:44335/tou`

## <a name="review-the-source-code"></a><span data-ttu-id="e4a7c-118">Revisar o código-fonte</span><span class="sxs-lookup"><span data-stu-id="e4a7c-118">Review the source code</span></span>

### <a name="startupcs"></a><span data-ttu-id="e4a7c-119">Startup.cs</span><span class="sxs-lookup"><span data-stu-id="e4a7c-119">Startup.cs</span></span>

<span data-ttu-id="e4a7c-120">Esse projeto foi criado a partir de um ASP.</span><span class="sxs-lookup"><span data-stu-id="e4a7c-120">This project was created from an ASP.</span></span> <span data-ttu-id="e4a7c-121">Modelo vazio do Aplicativo Web net Core 2.2 com a caixa de seleção *Avançado - Configurar para HTTPS* selecionada na instalação.</span><span class="sxs-lookup"><span data-stu-id="e4a7c-121">NET Core 2.2 Web Application empty template with the *Advanced - Configure for HTTPS* check box selected at setup.</span></span> <span data-ttu-id="e4a7c-122">Os serviços MVC são registrados pelo método da estrutura de injeção de `ConfigureServices()` dependência.</span><span class="sxs-lookup"><span data-stu-id="e4a7c-122">The MVC services are registered by the dependency injection framework's `ConfigureServices()` method.</span></span> <span data-ttu-id="e4a7c-123">Além disso, o modelo vazio não habilita o serviço de conteúdo estático por padrão, portanto, o middleware de arquivos estáticos é adicionado ao `Configure()` método:</span><span class="sxs-lookup"><span data-stu-id="e4a7c-123">Additionally, the empty template doesn't enable serving static content by default, so the static files middleware is added to the `Configure()` method:</span></span>

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

### <a name="wwwroot-folder"></a><span data-ttu-id="e4a7c-124">pasta wwwroot</span><span class="sxs-lookup"><span data-stu-id="e4a7c-124">wwwroot folder</span></span>

<span data-ttu-id="e4a7c-125">Em ASP.</span><span class="sxs-lookup"><span data-stu-id="e4a7c-125">In ASP.</span></span> <span data-ttu-id="e4a7c-126">NET Core, a pasta raiz da Web é onde o aplicativo procura arquivos estáticos.</span><span class="sxs-lookup"><span data-stu-id="e4a7c-126">NET Core, the web root folder is where the application looks for static files.</span></span>

### <a name="appmanifest-folder"></a><span data-ttu-id="e4a7c-127">Pasta AppManifest</span><span class="sxs-lookup"><span data-stu-id="e4a7c-127">AppManifest folder</span></span>

<span data-ttu-id="e4a7c-128">Esta pasta contém os seguintes arquivos de pacote de aplicativos necessários:</span><span class="sxs-lookup"><span data-stu-id="e4a7c-128">This folder contains the following required app package files:</span></span>

* <span data-ttu-id="e4a7c-129">Um **ícone de cor completo** medindo 192 x 192 pixels.</span><span class="sxs-lookup"><span data-stu-id="e4a7c-129">A **full color icon** measuring 192 x 192 pixels.</span></span>
* <span data-ttu-id="e4a7c-130">Um **ícone de contorno transparente** medindo 32 x 32 pixels.</span><span class="sxs-lookup"><span data-stu-id="e4a7c-130">A **transparent outline icon** measuring 32 x 32 pixels.</span></span>
* <span data-ttu-id="e4a7c-131">Um **manifest.json** que especifica os atributos do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e4a7c-131">A **manifest.json** file that specifies the attributes of your app.</span></span>

<span data-ttu-id="e4a7c-132">Esses arquivos precisam ser cortados em um pacote de aplicativos para uso no carregamento da guia para o Teams.</span><span class="sxs-lookup"><span data-stu-id="e4a7c-132">These files need to be zipped in an app package for use in uploading your tab to Teams.</span></span> <span data-ttu-id="e4a7c-133">O Microsoft Teams carregará o especificado em seu manifesto, o inserirá em um IFrame e `contentUrl` o renderizará em sua guia.</span><span class="sxs-lookup"><span data-stu-id="e4a7c-133">Microsoft Teams will load the `contentUrl` specified in your manifest, embed it in an IFrame, and render it in your tab.</span></span>

### <a name="csproj"></a><span data-ttu-id="e4a7c-134">.csproj</span><span class="sxs-lookup"><span data-stu-id="e4a7c-134">.csproj</span></span>

<span data-ttu-id="e4a7c-135">Na janela Visual Studio Do Explorador de Soluções clique com o botão direito do mouse no projeto e selecione **Editar Arquivo do Projeto**.</span><span class="sxs-lookup"><span data-stu-id="e4a7c-135">In the Visual Studio Solution Explorer window right-click on the project and select **Edit Project File**.</span></span> <span data-ttu-id="e4a7c-136">Na parte inferior do arquivo, você verá o código que cria e atualiza sua pasta zip quando o aplicativo é construído:</span><span class="sxs-lookup"><span data-stu-id="e4a7c-136">At the bottom of the file you'll see the code that creates and updates your zip folder when the application builds:</span></span>

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

### <a name="models"></a><span data-ttu-id="e4a7c-137">Modelos</span><span class="sxs-lookup"><span data-stu-id="e4a7c-137">Models</span></span>

<span data-ttu-id="e4a7c-138">*PersonalTab.cs* apresenta um objeto Message e métodos que serão chamados de *PersonalTabController* quando um usuário selecionar um botão no Modo de Exibição *PersonalTab.*</span><span class="sxs-lookup"><span data-stu-id="e4a7c-138">*PersonalTab.cs* presents a Message object and methods that will be called from *PersonalTabController* when a user selects a button in the *PersonalTab* View.</span></span>

### <a name="views"></a><span data-ttu-id="e4a7c-139">Modos de exibição</span><span class="sxs-lookup"><span data-stu-id="e4a7c-139">Views</span></span>

#### <a name="home"></a><span data-ttu-id="e4a7c-140">Página Inicial</span><span class="sxs-lookup"><span data-stu-id="e4a7c-140">Home</span></span>

<span data-ttu-id="e4a7c-141">ASP.</span><span class="sxs-lookup"><span data-stu-id="e4a7c-141">ASP.</span></span> <span data-ttu-id="e4a7c-142">NET Core trata arquivos chamados *Index* como a home page padrão do site.</span><span class="sxs-lookup"><span data-stu-id="e4a7c-142">NET Core treats files called *Index* as the default/home page for the site.</span></span> <span data-ttu-id="e4a7c-143">Quando a URL do navegador aponta para a raiz do site, *Index.cshtml* será exibida como a home page do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e4a7c-143">When your browser URL points to the root of the site, *Index.cshtml* will be displayed as the home page for your application.</span></span>

#### <a name="shared"></a><span data-ttu-id="e4a7c-144">Compartilhados</span><span class="sxs-lookup"><span data-stu-id="e4a7c-144">Shared</span></span>

<span data-ttu-id="e4a7c-145">A marcação de exibição *parcial _Layout.cshtml* contém a estrutura geral da página do aplicativo e elementos visuais compartilhados.</span><span class="sxs-lookup"><span data-stu-id="e4a7c-145">The partial view markup *_Layout.cshtml* contains the application's overall page structure and shared visual elements.</span></span> <span data-ttu-id="e4a7c-146">Ele também fará referência à Biblioteca do Teams.</span><span class="sxs-lookup"><span data-stu-id="e4a7c-146">It will also reference the Teams Library.</span></span>

### <a name="controllers"></a><span data-ttu-id="e4a7c-147">Controladores</span><span class="sxs-lookup"><span data-stu-id="e4a7c-147">Controllers</span></span>

<span data-ttu-id="e4a7c-148">Os controladores usam a propriedade ViewBag para transferir valores dinamicamente para o Views.</span><span class="sxs-lookup"><span data-stu-id="e4a7c-148">The controllers use the ViewBag property to transfer values dynamically to the Views.</span></span>

[!INCLUDE [dotnet-update-personal-app](~/includes/tabs/dotnet-update-personal-app.md)]

[!INCLUDE [dotnet-ngrok-intro](~/includes/tabs/dotnet-ngrok-intro.md)]

* <span data-ttu-id="e4a7c-149">Abra um prompt de comando na raiz do diretório do projeto e execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="e4a7c-149">Open a command prompt in the root of your project directory and run the following command:</span></span>

``` bash
ngrok http https://localhost:44345 -host-header="localhost:44345"
```

* <span data-ttu-id="e4a7c-150">O Ngrok ouvirá as solicitações da Internet e as encaminhará para seu aplicativo quando estiver sendo executado na porta 44325.</span><span class="sxs-lookup"><span data-stu-id="e4a7c-150">Ngrok will listen to requests from the internet and will route them to your application when it is running on port 44325.</span></span>  <span data-ttu-id="e4a7c-151">Deve parecer `https://y8rPrT2b.ngrok.io/` onde *y8rPrT2b* é substituído pela URL HTTPS alfanumérico ngrok.</span><span class="sxs-lookup"><span data-stu-id="e4a7c-151">It should resemble `https://y8rPrT2b.ngrok.io/` where *y8rPrT2b* is replaced by your ngrok alpha-numeric HTTPS URL.</span></span>

* <span data-ttu-id="e4a7c-152">Certifique-se de manter o prompt de comando com o ngrok em execução e para anotar a URL , você precisará dele mais tarde.</span><span class="sxs-lookup"><span data-stu-id="e4a7c-152">Be sure to keep the command prompt with ngrok running, and to make a note of the URL — you'll need it later.</span></span>

* <span data-ttu-id="e4a7c-153">Verifique se *o ngrok* está sendo executado e funcionando corretamente abrindo seu navegador e indo para sua página de conteúdo por meio da URL HTTPS ngrok fornecida na janela do prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="e4a7c-153">Verify that *ngrok* is running and working properly by opening your browser and going to your content page via the ngrok HTTPS URL that was provided in your command prompt window.</span></span>

> <span data-ttu-id="e4a7c-154">[!</span><span class="sxs-lookup"><span data-stu-id="e4a7c-154">[!</span></span> <span data-ttu-id="e4a7c-155">DICA] Você precisa ter seu aplicativo em Visual Studio e ngrok em execução para concluir esse início rápido.</span><span class="sxs-lookup"><span data-stu-id="e4a7c-155">TIP] You need to have both your application in Visual Studio and ngrok running to complete this quickstart.</span></span> <span data-ttu-id="e4a7c-156">Se você precisar parar de executar seu aplicativo Visual Studio para trabalhar nele, **mantenha o ngrok em execução**.</span><span class="sxs-lookup"><span data-stu-id="e4a7c-156">If you need to stop running your application in Visual Studio to work on it, **keep ngrok running**.</span></span> <span data-ttu-id="e4a7c-157">Ele continuará a ouvir e retomará o roteamento da solicitação do aplicativo quando ele for reiniciado no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e4a7c-157">It will continue to listen and will resume routing your application's request when it restarts in Visual Studio.</span></span> <span data-ttu-id="e4a7c-158">Se você precisar reiniciar o serviço ngrok, ele retornará uma nova URL e será preciso atualizar todos os lugares que usam essa URL.</span><span class="sxs-lookup"><span data-stu-id="e4a7c-158">If you have to restart the ngrok service it will return a new URL and you'll have to update every place that uses that URL.</span></span>

### <a name="run-your-application"></a><span data-ttu-id="e4a7c-159">Executar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="e4a7c-159">Run your application</span></span>

* <span data-ttu-id="e4a7c-160">Em Visual Studio pressione **F5** ou escolha **Iniciar Depuração** no menu **Depuração do** aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e4a7c-160">In Visual Studio press **F5** or choose **Start Debugging** from your application's **Debug** menu.</span></span>

[!INCLUDE [dotnet-personal-use-appstudio](~/includes/tabs/dotnet-personal-use-appstudio.md)]
