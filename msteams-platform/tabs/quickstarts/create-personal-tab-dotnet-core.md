---
title: Crie uma guia pessoal com ASP.NET Core
author: laujan
description: Um guia de início rápido para criar uma guia pessoal personalizada com ASP.NET Core.
ms.topic: quickstart
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: 41aa916f4c69d50e48254d0f4934109429dab83c
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566891"
---
# <a name="create-a-personal-tab-using-aspnetcore"></a><span data-ttu-id="ffee2-103">Crie uma guia pessoal usando o ASP.NETCore</span><span class="sxs-lookup"><span data-stu-id="ffee2-103">Create a personal tab using ASP.NETCore</span></span>

<span data-ttu-id="ffee2-104">Nesta partida rápida, vamos caminhar criando uma guia pessoal personalizada com páginas C# e ASP.Net Core Razor.</span><span class="sxs-lookup"><span data-stu-id="ffee2-104">In this quickstart, we'll walk-through creating a custom personal tab with C# and ASP.Net Core Razor pages.</span></span> <span data-ttu-id="ffee2-105">Também usaremos [o App Studio para Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) para finalizar seu manifesto de aplicativo e implantar sua guia para Teams.</span><span class="sxs-lookup"><span data-stu-id="ffee2-105">We'll also use [App Studio for Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) to finalize your app manifest and deploy your tab to Teams.</span></span>

[!INCLUDE [dotnet-core-prereq](~/includes/tabs/dotnet-core-prereq.md)]

## <a name="get-the-source-code"></a><span data-ttu-id="ffee2-106">Obtenha o código fonte</span><span class="sxs-lookup"><span data-stu-id="ffee2-106">Get the source code</span></span>

<span data-ttu-id="ffee2-107">Abra um prompt de comando e crie um novo diretório para o seu projeto de guia.</span><span class="sxs-lookup"><span data-stu-id="ffee2-107">Open a command prompt and create a new directory for your tab project.</span></span> <span data-ttu-id="ffee2-108">Nós fornecemos um projeto simples para começar você.</span><span class="sxs-lookup"><span data-stu-id="ffee2-108">We have provided a simple project to get you started.</span></span> <span data-ttu-id="ffee2-109">Para recuperar o código-fonte, você pode baixar a pasta zip e extrair os arquivos ou clonar o repositório de amostras em seu novo diretório:</span><span class="sxs-lookup"><span data-stu-id="ffee2-109">To retrieve the source code you can download the zip folder and extract the files or clone the sample repository into your new directory:</span></span>

```bash
git clone https://github.com/OfficeDev/microsoft-teams-sample-tabs.git
```

<span data-ttu-id="ffee2-110">Depois de ter o código-fonte, abra Visual Studio e selecione **Abrir um projeto ou solução**.</span><span class="sxs-lookup"><span data-stu-id="ffee2-110">Once you have the source code, open Visual Studio and select **Open a project or solution**.</span></span> <span data-ttu-id="ffee2-111">Navegue até o diretório de aplicativos da guia e abra **o PersonalTab.sln**.</span><span class="sxs-lookup"><span data-stu-id="ffee2-111">Navigate to the tab application directory and open **PersonalTab.sln**.</span></span>

<span data-ttu-id="ffee2-112">Para construir e executar seu aplicativo pressione **F5** ou escolha Iniciar a **depuração** no menu **Debug.**</span><span class="sxs-lookup"><span data-stu-id="ffee2-112">To build and run your application press **F5** or choose **Start Debugging** from the **Debug** menu.</span></span> <span data-ttu-id="ffee2-113">Em um navegador navegue até os URLs abaixo para verificar o aplicativo carregado corretamente:</span><span class="sxs-lookup"><span data-stu-id="ffee2-113">In a browser navigate to the URLs below to verify the application loaded properly:</span></span>

- `http://localhost:44325/`
- `http://localhost:44325/personal`
- `http://localhost:44325/privacy`
- `http://localhost:44325/tou`

## <a name="review-the-source-code"></a><span data-ttu-id="ffee2-114">Revise o código-fonte</span><span class="sxs-lookup"><span data-stu-id="ffee2-114">Review the source code</span></span>

### <a name="startupcs"></a><span data-ttu-id="ffee2-115">Startup.cs</span><span class="sxs-lookup"><span data-stu-id="ffee2-115">Startup.cs</span></span>

<span data-ttu-id="ffee2-116">Este projeto foi criado a partir de um modelo vazio de ASP.NET Core 2.2 Web Application com a caixa de seleção **Advanced - Configure for HTTPS** selecionada na configuração.</span><span class="sxs-lookup"><span data-stu-id="ffee2-116">This project was created from an ASP.NET Core 2.2 Web Application empty template with the **Advanced - Configure for HTTPS** check box selected at setup.</span></span> <span data-ttu-id="ffee2-117">Os serviços de MVC são registrados pelo método da estrutura de injeção de `ConfigureServices()` dependência.</span><span class="sxs-lookup"><span data-stu-id="ffee2-117">The MVC services are registered by the dependency injection framework's `ConfigureServices()` method.</span></span> <span data-ttu-id="ffee2-118">Além disso, o modelo vazio não permite servir conteúdo estático por padrão, de modo que o middleware de arquivos estáticos é adicionado ao `Configure()` método:</span><span class="sxs-lookup"><span data-stu-id="ffee2-118">Additionally, the empty template doesn't enable serving static content by default, so the static files middleware is added to the `Configure()` method:</span></span>

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

### <a name="wwwroot-folder"></a><span data-ttu-id="ffee2-119">wwwroot pasta</span><span class="sxs-lookup"><span data-stu-id="ffee2-119">wwwroot folder</span></span>

<span data-ttu-id="ffee2-120">Em ASP.NET Core, a pasta raiz da Web é onde o aplicativo procura arquivos estáticos.</span><span class="sxs-lookup"><span data-stu-id="ffee2-120">In ASP.NET Core, the web root folder is where the application looks for static files.</span></span>

### <a name="indexcshtml"></a><span data-ttu-id="ffee2-121">Index.cshtml</span><span class="sxs-lookup"><span data-stu-id="ffee2-121">Index.cshtml</span></span>

<span data-ttu-id="ffee2-122">ASP.NET Core trata arquivos chamados *Índice* como a página padrão/inicial para o site.</span><span class="sxs-lookup"><span data-stu-id="ffee2-122">ASP.NET Core treats files called *Index* as the default/home page for the site.</span></span> <span data-ttu-id="ffee2-123">Quando a URL do seu navegador aponta para a raiz do site, **o Index.cshtml** será exibido como a página inicial do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ffee2-123">When your browser URL points to the root of the site, **Index.cshtml** will be displayed as the home page for your application.</span></span>

### <a name="appmanifest-folder"></a><span data-ttu-id="ffee2-124">Pasta AppManifest</span><span class="sxs-lookup"><span data-stu-id="ffee2-124">AppManifest folder</span></span>

<span data-ttu-id="ffee2-125">Esta pasta contém os seguintes arquivos de pacote de aplicativos necessários:</span><span class="sxs-lookup"><span data-stu-id="ffee2-125">This folder contains the following required app package files:</span></span>

- <span data-ttu-id="ffee2-126">Um **ícone de cores completo** medindo 192 x 192 pixels.</span><span class="sxs-lookup"><span data-stu-id="ffee2-126">A **full color icon** measuring 192 x 192 pixels.</span></span>
- <span data-ttu-id="ffee2-127">Um **ícone de contorno transparente** medindo 32 x 32 pixels.</span><span class="sxs-lookup"><span data-stu-id="ffee2-127">A **transparent outline icon** measuring 32 x 32 pixels.</span></span>
- <span data-ttu-id="ffee2-128">Um **manifest.jsno** arquivo que especifica os atributos do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ffee2-128">A **manifest.json** file that specifies the attributes of your app.</span></span>

<span data-ttu-id="ffee2-129">Esses arquivos precisam ser fechados em um pacote de aplicativo para uso no upload de sua guia para Teams.</span><span class="sxs-lookup"><span data-stu-id="ffee2-129">These files need to be zipped in an app package for use in uploading your tab to Teams.</span></span> <span data-ttu-id="ffee2-130">Microsoft Teams carregará o `contentUrl` especificado em seu manifesto, incorporará-no em um <iframe \> e renderizará-no em sua guia.</span><span class="sxs-lookup"><span data-stu-id="ffee2-130">Microsoft Teams will load the `contentUrl` specified in your manifest, embed it in an <iframe\>, and render it in your tab.</span></span>

### <a name="csproj"></a><span data-ttu-id="ffee2-131">.csproj</span><span class="sxs-lookup"><span data-stu-id="ffee2-131">.csproj</span></span>

<span data-ttu-id="ffee2-132">Na janela Visual Studio Solution Explorer, clique com o botão direito do mouse no projeto e selecione **Editar arquivo Project**.</span><span class="sxs-lookup"><span data-stu-id="ffee2-132">In the Visual Studio Solution Explorer window, right-click on the project and select **Edit Project File**.</span></span> <span data-ttu-id="ffee2-133">Na parte inferior do arquivo você verá o código que cria e atualiza sua pasta zip quando o aplicativo é construído:</span><span class="sxs-lookup"><span data-stu-id="ffee2-133">At the bottom of the file you'll see the code that creates and updates your zip folder when the application builds:</span></span>

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

- <span data-ttu-id="ffee2-134">Abra um prompt de comando na raiz do diretório do projeto e execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="ffee2-134">Open a command prompt in the root of your project directory and run the following command:</span></span>

    ```bash
    ngrok http https://localhost:44325 -host-header="localhost:44325"
    ```

- <span data-ttu-id="ffee2-135">A Ngrok ouvirá os pedidos da internet e os encaminhará para o seu aplicativo quando estiver sendo executado na porta 44325.</span><span class="sxs-lookup"><span data-stu-id="ffee2-135">Ngrok will listen to requests from the internet and will route them to your application when it is running on port 44325.</span></span>  <span data-ttu-id="ffee2-136">Ele deve se assemelhar `https://y8rPrT2b.ngrok.io/` onde *y8rPrT2b* é substituído por sua URL HTTPS alfa-numérica ngrok.</span><span class="sxs-lookup"><span data-stu-id="ffee2-136">It should resemble `https://y8rPrT2b.ngrok.io/` where *y8rPrT2b* is replaced by your ngrok alpha-numeric HTTPS URL.</span></span>

- <span data-ttu-id="ffee2-137">Certifique-se de manter o prompt de comando com ngrok em execução e para anotar a URL — você precisará dele mais tarde.</span><span class="sxs-lookup"><span data-stu-id="ffee2-137">Be sure to keep the command prompt with ngrok running, and to make a note of the URL — you'll need it later.</span></span>

- <span data-ttu-id="ffee2-138">Verifique se **o ngrok** está executando e funcionando corretamente abrindo seu navegador e indo para sua página de conteúdo através da URL ngrok HTTPS que foi fornecida na janela do prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="ffee2-138">Verify that **ngrok** is running and working properly by opening your browser and going to your content page via the ngrok HTTPS URL that was provided in your command prompt window.</span></span>

>[!TIP]
><span data-ttu-id="ffee2-139">Você precisa ter sua aplicação em Visual Studio e ngrok correndo para completar este quickstart.</span><span class="sxs-lookup"><span data-stu-id="ffee2-139">You need to have both your application in Visual Studio and ngrok running to complete this quickstart.</span></span> <span data-ttu-id="ffee2-140">Se você precisar parar de executar seu aplicativo em Visual Studio para trabalhar nele, **mantenha ngrok funcionando**.</span><span class="sxs-lookup"><span data-stu-id="ffee2-140">If you need to stop running your application in Visual Studio to work on it, **keep ngrok running**.</span></span> <span data-ttu-id="ffee2-141">Ele continuará ouvindo e retomará o encaminhamento da solicitação do seu aplicativo quando ele for reiniciado em Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ffee2-141">It will continue to listen and will resume routing your application's request when it restarts in Visual Studio.</span></span> <span data-ttu-id="ffee2-142">Se você tiver que reiniciar o serviço ngrok, ele retornará uma nova URL e você terá que atualizar todos os lugares que usarem essa URL.</span><span class="sxs-lookup"><span data-stu-id="ffee2-142">If you have to restart the ngrok service it will return a new URL and you'll have to update every place that uses that URL.</span></span>

### <a name="run-your-application"></a><span data-ttu-id="ffee2-143">Execute sua aplicação</span><span class="sxs-lookup"><span data-stu-id="ffee2-143">Run your application</span></span>

- <span data-ttu-id="ffee2-144">Em Visual Studio **pressione F5** ou escolha Iniciar a **depuração** no menu **Depuração** do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ffee2-144">In Visual Studio press **F5** or choose **Start Debugging** from your application's **Debug** menu.</span></span>

[!INCLUDE [dotnet-personal-use-appstudio](~/includes/tabs/dotnet-personal-use-appstudio.md)]

## <a name="next-step"></a><span data-ttu-id="ffee2-145">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="ffee2-145">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ffee2-146">Crie uma guia pessoal personalizada com o ASP.NETCore MVC</span><span class="sxs-lookup"><span data-stu-id="ffee2-146">Create a Custom Personal Tab with ASP.NETCore MVC</span></span>](~/tabs/quickstarts/create-personal-tab-dotnet-core-mvc.md)
