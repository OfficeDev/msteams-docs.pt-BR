---
title: Criar uma guia pessoal com o ASP.NET Core
author: laujan
description: Um guia de início rápido para criar uma guia pessoal personalizada com o ASP.NET Core.
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: c6b58ffd09f952a6237b765e5457fe7a8e943390
ms.sourcegitcommit: aabfd65a67e1889ec16f09476bc757dd4a46ec5b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2020
ms.locfileid: "48097876"
---
# <a name="create-a-custom-personal-tab-with-aspnet-core"></a><span data-ttu-id="a1392-103">Criar uma guia pessoal personalizada com o ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a1392-103">Create a Custom Personal Tab with ASP.NET Core</span></span>

<span data-ttu-id="a1392-104">Neste QuickStart, veremos como criar uma guia pessoal personalizada com as páginas principais do Razor do ASP.Net C# e do.</span><span class="sxs-lookup"><span data-stu-id="a1392-104">In this quickstart we'll walk-through creating a custom personal tab with C# and ASP.Net Core Razor pages.</span></span> <span data-ttu-id="a1392-105">Também usaremos o [app Studio para o Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) para finalizar o manifesto do aplicativo e implantar sua guia no Teams.</span><span class="sxs-lookup"><span data-stu-id="a1392-105">We'll also use [App Studio for Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) to finalize your app manifest and deploy your tab to Teams.</span></span>

[!INCLUDE [dotnet-core-prereq](~/includes/tabs/dotnet-core-prereq.md)]

## <a name="get-the-source-code"></a><span data-ttu-id="a1392-106">Obter o código-fonte</span><span class="sxs-lookup"><span data-stu-id="a1392-106">Get the source code</span></span>

<span data-ttu-id="a1392-107">Abra um prompt de comando e crie um novo diretório para o projeto de tabulação.</span><span class="sxs-lookup"><span data-stu-id="a1392-107">Open a command prompt and create a new directory for your tab project.</span></span> <span data-ttu-id="a1392-108">Fornecemos um projeto simples para ajudá-lo a começar.</span><span class="sxs-lookup"><span data-stu-id="a1392-108">We have provided a simple project to get you started.</span></span> <span data-ttu-id="a1392-109">Para recuperar o código-fonte, você pode baixar a pasta zip e extrair os arquivos ou clonar o repositório de exemplo no novo diretório:</span><span class="sxs-lookup"><span data-stu-id="a1392-109">To retrieve the source code you can download the zip folder and extract the files or clone the sample repository into your new directory:</span></span>

```bash
git clone https://github.com/OfficeDev/microsoft-teams-sample-tabs.git
```

<span data-ttu-id="a1392-110">Depois de ter o código-fonte, abra o Visual Studio e selecione **abrir um projeto ou solução**.</span><span class="sxs-lookup"><span data-stu-id="a1392-110">Once you have the source code, open Visual Studio and select **Open a project or solution**.</span></span> <span data-ttu-id="a1392-111">Navegue até o diretório do aplicativo guia e abra **PersonalTab. sln**.</span><span class="sxs-lookup"><span data-stu-id="a1392-111">Navigate to the tab application directory and open **PersonalTab.sln**.</span></span>

<span data-ttu-id="a1392-112">Para compilar e executar o aplicativo, pressione **F5** ou escolha **Iniciar Depuração** no menu **depurar** .</span><span class="sxs-lookup"><span data-stu-id="a1392-112">To build and run your application press **F5** or choose **Start Debugging** from the **Debug** menu.</span></span> <span data-ttu-id="a1392-113">Em um navegador, navegue até as URLs abaixo para verificar se o aplicativo foi carregado corretamente:</span><span class="sxs-lookup"><span data-stu-id="a1392-113">In a browser navigate to the URLs below to verify the application loaded properly:</span></span>

- `http://localhost:44325/`
- `http://localhost:44325/personal`
- `http://localhost:44325/privacy`
- `http://localhost:44325/tou`

## <a name="review-the-source-code"></a><span data-ttu-id="a1392-114">Examinar o código-fonte</span><span class="sxs-lookup"><span data-stu-id="a1392-114">Review the source code</span></span>

### <a name="startupcs"></a><span data-ttu-id="a1392-115">Startup.cs</span><span class="sxs-lookup"><span data-stu-id="a1392-115">Startup.cs</span></span>

<span data-ttu-id="a1392-116">Este projeto foi criado a partir de um modelo vazio do aplicativo Web do ASP.NET Core 2,2 com a caixa de seleção *avançado-configurar para https* selecionada na instalação.</span><span class="sxs-lookup"><span data-stu-id="a1392-116">This project was created from an ASP.NET Core 2.2 Web Application empty template with the *Advanced - Configure for HTTPS* check box selected at setup.</span></span> <span data-ttu-id="a1392-117">Os serviços do MVC são registrados pelo método da estrutura de injeção de dependência `ConfigureServices()` .</span><span class="sxs-lookup"><span data-stu-id="a1392-117">The MVC services are registered by the dependency injection framework's `ConfigureServices()` method.</span></span> <span data-ttu-id="a1392-118">Além disso, o modelo vazio não habilita o fornecimento de conteúdo estático por padrão, portanto, o middleware de arquivos estáticos é adicionado ao `Configure()` método:</span><span class="sxs-lookup"><span data-stu-id="a1392-118">Additionally, the empty template doesn't enable serving static content by default, so the static files middleware is added to the `Configure()` method:</span></span>

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

### <a name="wwwroot-folder"></a><span data-ttu-id="a1392-119">pasta wwwroot</span><span class="sxs-lookup"><span data-stu-id="a1392-119">wwwroot folder</span></span>

<span data-ttu-id="a1392-120">No ASP.NET Core, a pasta raiz da Web é onde o aplicativo procura arquivos estáticos.</span><span class="sxs-lookup"><span data-stu-id="a1392-120">In ASP.NET Core, the web root folder is where the application looks for static files.</span></span>

### <a name="indexcshtml"></a><span data-ttu-id="a1392-121">Index. cshtml</span><span class="sxs-lookup"><span data-stu-id="a1392-121">Index.cshtml</span></span>

<span data-ttu-id="a1392-122">ASP.NET Core trata os arquivos denominados *index* como o padrão/home page do site.</span><span class="sxs-lookup"><span data-stu-id="a1392-122">ASP.NET Core treats files called *Index* as the default/home page for the site.</span></span> <span data-ttu-id="a1392-123">Quando a URL do navegador apontar para a raiz do site, **index. cshtml** será exibido como a home page do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a1392-123">When your browser URL points to the root of the site, **Index.cshtml** will be displayed as the home page for your application.</span></span>

### <a name="appmanifest-folder"></a><span data-ttu-id="a1392-124">Pasta arquivo AppManifest</span><span class="sxs-lookup"><span data-stu-id="a1392-124">AppManifest folder</span></span>

<span data-ttu-id="a1392-125">Esta pasta contém os seguintes arquivos de pacote de aplicativos necessários:</span><span class="sxs-lookup"><span data-stu-id="a1392-125">This folder contains the following required app package files:</span></span>

- <span data-ttu-id="a1392-126">Um **ícone de cor completa** medindo 192 x 192 pixels.</span><span class="sxs-lookup"><span data-stu-id="a1392-126">A **full color icon** measuring 192 x 192 pixels.</span></span>
- <span data-ttu-id="a1392-127">Um **ícone de contorno transparente** medindo 32 x 32 pixels.</span><span class="sxs-lookup"><span data-stu-id="a1392-127">A **transparent outline icon** measuring 32 x 32 pixels.</span></span>
- <span data-ttu-id="a1392-128">Um **manifest.jsno** arquivo que especifica os atributos do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a1392-128">A **manifest.json** file that specifies the attributes of your app.</span></span>

<span data-ttu-id="a1392-129">Esses arquivos precisam ser zipados em um pacote de aplicativos para uso no carregamento de sua guia para o Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="a1392-129">These files need to be zipped in an app package for use in uploading your tab to Teams.</span></span> <span data-ttu-id="a1392-130">O Microsoft Teams carregará o `contentUrl` especificado no manifesto, o incorporará em um iframe e o renderizará na sua guia.</span><span class="sxs-lookup"><span data-stu-id="a1392-130">Microsoft Teams will load the `contentUrl` specified in your manifest, embed it in an IFrame, and render it in your tab.</span></span>

### <a name="csproj"></a><span data-ttu-id="a1392-131">. csproj</span><span class="sxs-lookup"><span data-stu-id="a1392-131">.csproj</span></span>

<span data-ttu-id="a1392-132">Na janela do Visual Studio Solution Explorer, clique com o botão direito do mouse no projeto e selecione **Editar arquivo de projeto**.</span><span class="sxs-lookup"><span data-stu-id="a1392-132">In the Visual Studio Solution Explorer window right-click on the project and select **Edit Project File**.</span></span> <span data-ttu-id="a1392-133">Na parte inferior do arquivo, você verá o código que cria e atualiza sua pasta zip quando o aplicativo é criado:</span><span class="sxs-lookup"><span data-stu-id="a1392-133">At the bottom of the file you'll see the code that creates and updates your zip folder when the application builds:</span></span>

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

[!INCLUDE  [dotnet-update-personal-app](~/includes/tabs/dotnet-update-personal-app.md)]

[!INCLUDE [dotnet-ngrok-intro](~/includes/tabs/dotnet-ngrok-intro.md)]

- <span data-ttu-id="a1392-134">Abra um prompt de comando na raiz do diretório do projeto e execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="a1392-134">Open a command prompt in the root of your project directory and run the following command:</span></span>

```bash
ngrok http https://localhost:44325 -host-header="localhost:44325"
```

- <span data-ttu-id="a1392-135">O Ngrok ouvirá as solicitações da Internet e as roteará para seu aplicativo quando estiver em execução na porta 44325.</span><span class="sxs-lookup"><span data-stu-id="a1392-135">Ngrok will listen to requests from the internet and will route them to your application when it is running on port 44325.</span></span>  <span data-ttu-id="a1392-136">Deve ser parecido `https://y8rPrT2b.ngrok.io/` com o local em que o *y8rPrT2b* é substituído pela URL https do ngrok alfanumérico.</span><span class="sxs-lookup"><span data-stu-id="a1392-136">It should resemble `https://y8rPrT2b.ngrok.io/` where *y8rPrT2b* is replaced by your ngrok alpha-numeric HTTPS URL.</span></span>

- <span data-ttu-id="a1392-137">Certifique-se de manter o prompt de comando com o ngrok em execução e tome nota da URL — você precisará dela mais tarde.</span><span class="sxs-lookup"><span data-stu-id="a1392-137">Be sure to keep the command prompt with ngrok running, and to make a note of the URL—you'll need it later.</span></span>

- <span data-ttu-id="a1392-138">Verifique se o *ngrok* está em execução e funcionando corretamente abrindo o navegador e acessando a página de conteúdo por meio da URL https do ngrok que foi fornecida na janela de prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="a1392-138">Verify that *ngrok* is running and working properly by opening your browser and going to your content page via the ngrok HTTPS URL that was provided in your command prompt window.</span></span>

>[!TIP]
><span data-ttu-id="a1392-139">Você precisa ter o aplicativo no Visual Studio e o ngrok em execução para concluir este QuickStart.</span><span class="sxs-lookup"><span data-stu-id="a1392-139">You need to have both your application in Visual Studio and ngrok running to complete this quickstart.</span></span> <span data-ttu-id="a1392-140">Se você precisar parar a execução do aplicativo no Visual Studio para trabalhar nele, **Mantenha o ngrok em execução**.</span><span class="sxs-lookup"><span data-stu-id="a1392-140">If you need to stop running your application in Visual Studio to work on it, **keep ngrok running**.</span></span> <span data-ttu-id="a1392-141">Ele continuará a escutar e retomará o roteamento da solicitação do aplicativo quando ele for reiniciado no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a1392-141">It will continue to listen and will resume routing your application's request when it restarts in Visual Studio.</span></span> <span data-ttu-id="a1392-142">Se for necessário reiniciar o serviço do ngrok, ele retornará uma nova URL e você terá que atualizar todos os locais que usam essa URL.</span><span class="sxs-lookup"><span data-stu-id="a1392-142">If you have to restart the ngrok service it will return a new URL and you'll have to update every place that uses that URL.</span></span>

### <a name="run-your-application"></a><span data-ttu-id="a1392-143">Executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="a1392-143">Run your application</span></span>

- <span data-ttu-id="a1392-144">No Visual Studio, pressione **F5** ou escolha **Iniciar Depuração** no menu **depurar** do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a1392-144">In Visual Studio press **F5** or choose **Start Debugging** from your application's **Debug** menu.</span></span>

[!INCLUDE [dotnet-personal-use-appstudio](~/includes/tabs/dotnet-personal-use-appstudio.md)]
