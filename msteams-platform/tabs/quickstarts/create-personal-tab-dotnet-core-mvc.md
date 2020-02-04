---
title: Criar uma guia pessoal com o ASP. NET Core MVC
author: laujan
description: Um guia de início rápido para criar uma guia pessoal personalizada com o ASP. NET Core MVC.
ms.topic: quickstart
ms.author: laujan
ms.openlocfilehash: 3bdd23692eca5ff3f6fc3f82cdaa233d34d4c69f
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672451"
---
# <a name="create-a-custom-personal-tab-with-asp-net-core-mvc"></a><span data-ttu-id="3b5a5-105">Criar uma guia pessoal personalizada com o ASP.</span><span class="sxs-lookup"><span data-stu-id="3b5a5-105">Create a Custom Personal Tab with ASP.</span></span> <span data-ttu-id="3b5a5-106">NET Core MVC</span><span class="sxs-lookup"><span data-stu-id="3b5a5-106">NET Core MVC</span></span>

<span data-ttu-id="3b5a5-107">Neste QuickStart, veremos como criar uma guia pessoal personalizada com C# e ASP.</span><span class="sxs-lookup"><span data-stu-id="3b5a5-107">In this quickstart we'll walk-through creating a custom personal tab with C# and ASP.</span></span> <span data-ttu-id="3b5a5-108">NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="3b5a5-108">Net Core MVC.</span></span> <span data-ttu-id="3b5a5-109">Também usaremos o [app Studio para o Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) para finalizar o manifesto do aplicativo e implantar sua guia no Teams.</span><span class="sxs-lookup"><span data-stu-id="3b5a5-109">We'll also use [App Studio for Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) to finalize your app manifest and deploy your tab to Teams.</span></span>

[!INCLUDE [dotnet-core-prereq](~/includes/tabs/dotnet-core-prereq.md)]

## <a name="get-the-source-code"></a><span data-ttu-id="3b5a5-110">Obter o código-fonte</span><span class="sxs-lookup"><span data-stu-id="3b5a5-110">Get the source code</span></span>

<span data-ttu-id="3b5a5-111">Abra um prompt de comando e crie um novo diretório para o projeto de tabulação.</span><span class="sxs-lookup"><span data-stu-id="3b5a5-111">Open a command prompt and create a new directory for your tab project.</span></span> <span data-ttu-id="3b5a5-112">Fornecemos um projeto simples para ajudá-lo a começar.</span><span class="sxs-lookup"><span data-stu-id="3b5a5-112">We have provided a simple project to get you started.</span></span> <span data-ttu-id="3b5a5-113">Para recuperar o código-fonte, você pode baixar a pasta zip e extrair os arquivos ou clonar o repositório de exemplo no novo diretório:</span><span class="sxs-lookup"><span data-stu-id="3b5a5-113">To retrieve the source code you can download the zip folder and extract the files or clone the sample repository into your new directory:</span></span>

``` bash
git clone https://github.com/OfficeDev/microsoft-teams-sample-tabs.git
```

<span data-ttu-id="3b5a5-114">Depois de ter o código-fonte, abra o Visual Studio e selecione **abrir um projeto ou solução**.</span><span class="sxs-lookup"><span data-stu-id="3b5a5-114">Once you have the source code, open Visual Studio and select **Open a project or solution**.</span></span> <span data-ttu-id="3b5a5-115">Navegue até o diretório do aplicativo guia e abra **PersonalTabMVC. sln**.</span><span class="sxs-lookup"><span data-stu-id="3b5a5-115">Navigate to the tab application directory and open **PersonalTabMVC.sln**.</span></span>

<span data-ttu-id="3b5a5-116">Para compilar e executar o aplicativo, pressione **F5** ou escolha **Iniciar Depuração** no menu **depurar** .</span><span class="sxs-lookup"><span data-stu-id="3b5a5-116">To build and run your application press **F5** or choose **Start Debugging** from the **Debug** menu.</span></span> <span data-ttu-id="3b5a5-117">Em um navegador, navegue até as URLs abaixo para verificar se o aplicativo foi carregado corretamente:</span><span class="sxs-lookup"><span data-stu-id="3b5a5-117">In a browser navigate to the URLs below to verify that the application loaded properly:</span></span>

* `http://localhost:44335`
* `http://localhost:44335/privacy`
* `http://localhost:44335/tou`

## <a name="review-the-source-code"></a><span data-ttu-id="3b5a5-118">Examinar o código-fonte</span><span class="sxs-lookup"><span data-stu-id="3b5a5-118">Review the source code</span></span>

### <a name="startupcs"></a><span data-ttu-id="3b5a5-119">Startup.cs</span><span class="sxs-lookup"><span data-stu-id="3b5a5-119">Startup.cs</span></span>

<span data-ttu-id="3b5a5-120">Este projeto foi criado a partir de um ASP.</span><span class="sxs-lookup"><span data-stu-id="3b5a5-120">This project was created from an ASP.</span></span> <span data-ttu-id="3b5a5-121">Modelo vazio do aplicativo Web do NET Core 2,2 com a caixa de seleção *avançado-configurar para https* selecionada na instalação.</span><span class="sxs-lookup"><span data-stu-id="3b5a5-121">NET Core 2.2 Web Application empty template with the *Advanced - Configure for HTTPS* check box selected at setup.</span></span> <span data-ttu-id="3b5a5-122">Os serviços do MVC são registrados pelo método da `ConfigureServices()` estrutura de injeção de dependência.</span><span class="sxs-lookup"><span data-stu-id="3b5a5-122">The MVC services are registered by the dependency injection framework's `ConfigureServices()` method.</span></span> <span data-ttu-id="3b5a5-123">Além disso, o modelo vazio não habilita o fornecimento de conteúdo estático por padrão, portanto, o middleware de arquivos estáticos é adicionado ao `Configure()` método:</span><span class="sxs-lookup"><span data-stu-id="3b5a5-123">Additionally, the empty template doesn't enable serving static content by default, so the static files middleware is added to the `Configure()` method:</span></span>

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

### <a name="wwwroot-folder"></a><span data-ttu-id="3b5a5-124">pasta wwwroot</span><span class="sxs-lookup"><span data-stu-id="3b5a5-124">wwwroot folder</span></span>

<span data-ttu-id="3b5a5-125">No ASP.</span><span class="sxs-lookup"><span data-stu-id="3b5a5-125">In ASP.</span></span> <span data-ttu-id="3b5a5-126">NET Core, a pasta raiz da Web é onde o aplicativo procura arquivos estáticos.</span><span class="sxs-lookup"><span data-stu-id="3b5a5-126">NET Core, the web root folder is where the application looks for static files.</span></span>

### <a name="appmanifest-folder"></a><span data-ttu-id="3b5a5-127">Pasta arquivo AppManifest</span><span class="sxs-lookup"><span data-stu-id="3b5a5-127">AppManifest folder</span></span>

<span data-ttu-id="3b5a5-128">Esta pasta contém os seguintes arquivos de pacote de aplicativos necessários:</span><span class="sxs-lookup"><span data-stu-id="3b5a5-128">This folder contains the following required app package files:</span></span>

* <span data-ttu-id="3b5a5-129">Um **ícone de cor completa** medindo 192 x 192 pixels.</span><span class="sxs-lookup"><span data-stu-id="3b5a5-129">A **full color icon** measuring 192 x 192 pixels.</span></span>
* <span data-ttu-id="3b5a5-130">Um **ícone de contorno transparente** medindo 32 x 32 pixels.</span><span class="sxs-lookup"><span data-stu-id="3b5a5-130">A **transparent outline icon** measuring 32 x 32 pixels.</span></span>
* <span data-ttu-id="3b5a5-131">Um arquivo **manifest. JSON** que especifica os atributos do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3b5a5-131">A **manifest.json** file that specifies the attributes of your app.</span></span>

<span data-ttu-id="3b5a5-132">Esses arquivos precisam ser zipados em um pacote de aplicativos para uso no carregamento de sua guia para o Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="3b5a5-132">These files need to be zipped in an app package for use in uploading your tab to Teams.</span></span> <span data-ttu-id="3b5a5-133">O Microsoft Teams carregará o `contentUrl` especificado no manifesto, o incorporará em um iframe e o renderizará na sua guia.</span><span class="sxs-lookup"><span data-stu-id="3b5a5-133">Microsoft Teams will load the `contentUrl` specified in your manifest, embed it in an IFrame, and render it in your tab.</span></span>

### <a name="csproj"></a><span data-ttu-id="3b5a5-134">. csproj</span><span class="sxs-lookup"><span data-stu-id="3b5a5-134">.csproj</span></span>

<span data-ttu-id="3b5a5-135">Na janela do Visual Studio Solution Explorer, clique com o botão direito do mouse no projeto e selecione **Editar arquivo de projeto**.</span><span class="sxs-lookup"><span data-stu-id="3b5a5-135">In the Visual Studio Solution Explorer window right-click on the project and select **Edit Project File**.</span></span> <span data-ttu-id="3b5a5-136">Na parte inferior do arquivo, você verá o código que cria e atualiza sua pasta zip quando o aplicativo é criado:</span><span class="sxs-lookup"><span data-stu-id="3b5a5-136">At the bottom of the file you'll see the code that creates and updates your zip folder when the application builds:</span></span>

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

### <a name="models"></a><span data-ttu-id="3b5a5-137">Modelo</span><span class="sxs-lookup"><span data-stu-id="3b5a5-137">Models</span></span>

<span data-ttu-id="3b5a5-138">*PersonalTab.cs* apresenta um objeto Message e métodos que serão chamados de *PersonalTabController* quando um usuário seleciona um botão no modo de exibição do *PersonalTab* .</span><span class="sxs-lookup"><span data-stu-id="3b5a5-138">*PersonalTab.cs* presents a Message object and methods that will be called from *PersonalTabController* when a user selects a button in the *PersonalTab* View.</span></span>

### <a name="views"></a><span data-ttu-id="3b5a5-139">Modos de exibição</span><span class="sxs-lookup"><span data-stu-id="3b5a5-139">Views</span></span>

#### <a name="home"></a><span data-ttu-id="3b5a5-140">Página Inicial</span><span class="sxs-lookup"><span data-stu-id="3b5a5-140">Home</span></span>

<span data-ttu-id="3b5a5-141">Pelas.</span><span class="sxs-lookup"><span data-stu-id="3b5a5-141">ASP.</span></span> <span data-ttu-id="3b5a5-142">NET Core trata os arquivos denominados *index* como o padrão/home page do site.</span><span class="sxs-lookup"><span data-stu-id="3b5a5-142">NET Core treats files called *Index* as the default/home page for the site.</span></span> <span data-ttu-id="3b5a5-143">Quando a URL do navegador apontar para a raiz do site, *index. cshtml* será exibido como a home page do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3b5a5-143">When your browser URL points to the root of the site, *Index.cshtml* will be displayed as the home page for your application.</span></span>

#### <a name="shared"></a><span data-ttu-id="3b5a5-144">Compartilhados</span><span class="sxs-lookup"><span data-stu-id="3b5a5-144">Shared</span></span>

<span data-ttu-id="3b5a5-145">A marcação de exibição parcial *_Layout. cshtml* contém a estrutura de página Geral do aplicativo e elementos visuais compartilhados.</span><span class="sxs-lookup"><span data-stu-id="3b5a5-145">The partial view markup *_Layout.cshtml* contains the application's overall page structure and shared visual elements.</span></span> <span data-ttu-id="3b5a5-146">Ele também fará referência à biblioteca do teams.</span><span class="sxs-lookup"><span data-stu-id="3b5a5-146">It will also reference the Teams Library.</span></span>

### <a name="controllers"></a><span data-ttu-id="3b5a5-147">Controladores</span><span class="sxs-lookup"><span data-stu-id="3b5a5-147">Controllers</span></span>

<span data-ttu-id="3b5a5-148">Os controladores usam a propriedade ViewBag para transferir valores dinamicamente para os modos de exibição.</span><span class="sxs-lookup"><span data-stu-id="3b5a5-148">The controllers use the ViewBag property to transfer values dynamically to the Views.</span></span>

[!INCLUDE [dotnet-update-personal-app](~/includes/tabs/dotnet-update-personal-app.md)]

[!INCLUDE [dotnet-ngrok-intro](~/includes/tabs/dotnet-ngrok-intro.md)]

* <span data-ttu-id="3b5a5-149">Abra um prompt de comando na raiz do diretório do projeto e execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="3b5a5-149">Open a command prompt in the root of your project directory and run the following command:</span></span>

``` bash
ngrok http https://localhost:44345 -host-header="localhost:44345"
```

* <span data-ttu-id="3b5a5-150">O Ngrok ouvirá as solicitações da Internet e as roteará para seu aplicativo quando estiver em execução na porta 44325.</span><span class="sxs-lookup"><span data-stu-id="3b5a5-150">Ngrok will listen to requests from the internet and will route them to your application when it is running on port 44325.</span></span>  <span data-ttu-id="3b5a5-151">Deve ser parecido com `https://y8rPrT2b.ngrok.io/` o local em que o *y8rPrT2b* é substituído pela URL https do ngrok alfanumérico.</span><span class="sxs-lookup"><span data-stu-id="3b5a5-151">It should resemble `https://y8rPrT2b.ngrok.io/` where *y8rPrT2b* is replaced by your ngrok alpha-numeric HTTPS URL.</span></span>

* <span data-ttu-id="3b5a5-152">Certifique-se de manter o prompt de comando com o ngrok em execução e tome nota da URL — você precisará dela mais tarde.</span><span class="sxs-lookup"><span data-stu-id="3b5a5-152">Be sure to keep the command prompt with ngrok running, and to make a note of the URL — you'll need it later.</span></span>

* <span data-ttu-id="3b5a5-153">Verifique se o *ngrok* está em execução e funcionando corretamente abrindo o navegador e acessando a página de conteúdo por meio da URL https do ngrok que foi fornecida na janela de prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="3b5a5-153">Verify that *ngrok* is running and working properly by opening your browser and going to your content page via the ngrok HTTPS URL that was provided in your command prompt window.</span></span>

> <span data-ttu-id="3b5a5-154">[!</span><span class="sxs-lookup"><span data-stu-id="3b5a5-154">[!</span></span> <span data-ttu-id="3b5a5-155">Dica] você precisa ter o aplicativo no Visual Studio e o ngrok em execução para concluir este QuickStart.</span><span class="sxs-lookup"><span data-stu-id="3b5a5-155">TIP] You need to have both your application in Visual Studio and ngrok running to complete this quickstart.</span></span> <span data-ttu-id="3b5a5-156">Se você precisar parar a execução do aplicativo no Visual Studio para trabalhar nele, **Mantenha o ngrok em execução**.</span><span class="sxs-lookup"><span data-stu-id="3b5a5-156">If you need to stop running your application in Visual Studio to work on it, **keep ngrok running**.</span></span> <span data-ttu-id="3b5a5-157">Ele continuará a escutar e retomará o roteamento da solicitação do aplicativo quando ele for reiniciado no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3b5a5-157">It will continue to listen and will resume routing your application's request when it restarts in Visual Studio.</span></span> <span data-ttu-id="3b5a5-158">Se for necessário reiniciar o serviço do ngrok, ele retornará uma nova URL e você terá que atualizar todos os locais que usam essa URL.</span><span class="sxs-lookup"><span data-stu-id="3b5a5-158">If you have to restart the ngrok service it will return a new URL and you'll have to update every place that uses that URL.</span></span>

### <a name="run-your-application"></a><span data-ttu-id="3b5a5-159">Executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="3b5a5-159">Run your application</span></span>

* <span data-ttu-id="3b5a5-160">No Visual Studio, pressione **F5** ou escolha **Iniciar Depuração** no menu **depurar** do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3b5a5-160">In Visual Studio press **F5** or choose **Start Debugging** from your application's **Debug** menu.</span></span>

[!INCLUDE [dotnet-personal-use-appstudio](~/includes/tabs/dotnet-personal-use-appstudio.md)]
