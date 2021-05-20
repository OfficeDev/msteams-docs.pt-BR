---
title: Crie uma guia pessoal com ASP. NÚCLEO NET MVC
author: laujan
description: Um guia de início rápido para criar uma guia pessoal personalizada com ASP. NÚCLEO NET MVC.
localization_priority: Normal
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: 01418adb32335660bb20f74ecfaa0e7e27230c93
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566619"
---
# <a name="create-a-custom-personal-tab-with-aspnet-core-mvc"></a><span data-ttu-id="a6710-105">Crie uma guia pessoal personalizada com ASP.NET Core MVC</span><span class="sxs-lookup"><span data-stu-id="a6710-105">Create a Custom Personal Tab with ASP.NET Core MVC</span></span>

<span data-ttu-id="a6710-106">Nesta partida rápida, vamos caminhar criando uma guia pessoal personalizada com C# e ASP.Net Core MVC.</span><span class="sxs-lookup"><span data-stu-id="a6710-106">In this quickstart we'll walk-through creating a custom personal tab with C# and ASP.Net Core MVC.</span></span> <span data-ttu-id="a6710-107">Também usaremos [o App Studio para Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) para finalizar seu manifesto de aplicativo e implantar sua guia para Teams.</span><span class="sxs-lookup"><span data-stu-id="a6710-107">We'll also use [App Studio for Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) to finalize your app manifest and deploy your tab to Teams.</span></span>

[!INCLUDE [dotnet-core-prereq](~/includes/tabs/dotnet-core-prereq.md)]

## <a name="get-the-source-code"></a><span data-ttu-id="a6710-108">Obtenha o código fonte</span><span class="sxs-lookup"><span data-stu-id="a6710-108">Get the source code</span></span>

<span data-ttu-id="a6710-109">Abra um prompt de comando e crie um novo diretório para o seu projeto de guia.</span><span class="sxs-lookup"><span data-stu-id="a6710-109">Open a command prompt and create a new directory for your tab project.</span></span> <span data-ttu-id="a6710-110">Nós fornecemos um projeto simples para começar você.</span><span class="sxs-lookup"><span data-stu-id="a6710-110">We have provided a simple project to get you started.</span></span> <span data-ttu-id="a6710-111">Para recuperar o código-fonte, você pode baixar a pasta zip e extrair os arquivos ou clonar o repositório de amostras em seu novo diretório:</span><span class="sxs-lookup"><span data-stu-id="a6710-111">To retrieve the source code you can download the zip folder and extract the files or clone the sample repository into your new directory:</span></span>

``` bash
git clone https://github.com/OfficeDev/microsoft-teams-sample-tabs.git
```

<span data-ttu-id="a6710-112">Depois de ter o código-fonte, abra Visual Studio e selecione **Abrir um projeto ou solução**.</span><span class="sxs-lookup"><span data-stu-id="a6710-112">Once you have the source code, open Visual Studio and select **Open a project or solution**.</span></span> <span data-ttu-id="a6710-113">Navegue até o diretório de aplicativos da guia e abra **PersonalTabMVC.sln**.</span><span class="sxs-lookup"><span data-stu-id="a6710-113">Navigate to the tab application directory and open **PersonalTabMVC.sln**.</span></span>

<span data-ttu-id="a6710-114">Para construir e executar seu aplicativo pressione **F5** ou escolha Iniciar a **depuração** no menu **Debug.**</span><span class="sxs-lookup"><span data-stu-id="a6710-114">To build and run your application press **F5** or choose **Start Debugging** from the **Debug** menu.</span></span> <span data-ttu-id="a6710-115">Em um navegador navegue até os URLs abaixo para verificar se o aplicativo foi carregado corretamente:</span><span class="sxs-lookup"><span data-stu-id="a6710-115">In a browser navigate to the URLs below to verify that the application loaded properly:</span></span>

* `http://localhost:44335`
* `http://localhost:44335/privacy`
* `http://localhost:44335/tou`

## <a name="review-the-source-code"></a><span data-ttu-id="a6710-116">Revise o código-fonte</span><span class="sxs-lookup"><span data-stu-id="a6710-116">Review the source code</span></span>

### <a name="startupcs"></a><span data-ttu-id="a6710-117">Startup.cs</span><span class="sxs-lookup"><span data-stu-id="a6710-117">Startup.cs</span></span>

<span data-ttu-id="a6710-118">Este projeto foi criado a partir de um ASP.</span><span class="sxs-lookup"><span data-stu-id="a6710-118">This project was created from an ASP.</span></span> <span data-ttu-id="a6710-119">NET Core 2.2 Web Application modelo vazio com o *Advanced - Configure para caixa de* seleção HTTPS selecionada na configuração.</span><span class="sxs-lookup"><span data-stu-id="a6710-119">NET Core 2.2 Web Application empty template with the *Advanced - Configure for HTTPS* check box selected at setup.</span></span> <span data-ttu-id="a6710-120">Os serviços de MVC são registrados pelo método da estrutura de injeção de `ConfigureServices()` dependência.</span><span class="sxs-lookup"><span data-stu-id="a6710-120">The MVC services are registered by the dependency injection framework's `ConfigureServices()` method.</span></span> <span data-ttu-id="a6710-121">Além disso, o modelo vazio não permite servir conteúdo estático por padrão, de modo que o middleware de arquivos estáticos é adicionado ao `Configure()` método:</span><span class="sxs-lookup"><span data-stu-id="a6710-121">Additionally, the empty template doesn't enable serving static content by default, so the static files middleware is added to the `Configure()` method:</span></span>

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

### <a name="wwwroot-folder"></a><span data-ttu-id="a6710-122">wwwroot pasta</span><span class="sxs-lookup"><span data-stu-id="a6710-122">wwwroot folder</span></span>

<span data-ttu-id="a6710-123">Em ASP.</span><span class="sxs-lookup"><span data-stu-id="a6710-123">In ASP.</span></span> <span data-ttu-id="a6710-124">NET Core, a pasta raiz da Web é onde o aplicativo procura arquivos estáticos.</span><span class="sxs-lookup"><span data-stu-id="a6710-124">NET Core, the web root folder is where the application looks for static files.</span></span>

### <a name="appmanifest-folder"></a><span data-ttu-id="a6710-125">Pasta AppManifest</span><span class="sxs-lookup"><span data-stu-id="a6710-125">AppManifest folder</span></span>

<span data-ttu-id="a6710-126">Esta pasta contém os seguintes arquivos de pacote de aplicativos necessários:</span><span class="sxs-lookup"><span data-stu-id="a6710-126">This folder contains the following required app package files:</span></span>

* <span data-ttu-id="a6710-127">Um **ícone de cores completo** medindo 192 x 192 pixels.</span><span class="sxs-lookup"><span data-stu-id="a6710-127">A **full color icon** measuring 192 x 192 pixels.</span></span>
* <span data-ttu-id="a6710-128">Um **ícone de contorno transparente** medindo 32 x 32 pixels.</span><span class="sxs-lookup"><span data-stu-id="a6710-128">A **transparent outline icon** measuring 32 x 32 pixels.</span></span>
* <span data-ttu-id="a6710-129">Um **manifest.jsno** arquivo que especifica os atributos do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a6710-129">A **manifest.json** file that specifies the attributes of your app.</span></span>

<span data-ttu-id="a6710-130">Esses arquivos precisam ser fechados em um pacote de aplicativo para uso no upload de sua guia para Teams.</span><span class="sxs-lookup"><span data-stu-id="a6710-130">These files need to be zipped in an app package for use in uploading your tab to Teams.</span></span> <span data-ttu-id="a6710-131">Microsoft Teams carregará o `contentUrl` especificado em seu manifesto, incorporará-no em um IFrame e o renderizará em sua guia.</span><span class="sxs-lookup"><span data-stu-id="a6710-131">Microsoft Teams will load the `contentUrl` specified in your manifest, embed it in an IFrame, and render it in your tab.</span></span>

### <a name="csproj"></a><span data-ttu-id="a6710-132">.csproj</span><span class="sxs-lookup"><span data-stu-id="a6710-132">.csproj</span></span>

<span data-ttu-id="a6710-133">Na janela Visual Studio Solution Explorer clique com o botão direito do mouse no projeto e selecione **Editar arquivo Project**.</span><span class="sxs-lookup"><span data-stu-id="a6710-133">In the Visual Studio Solution Explorer window right-click on the project and select **Edit Project File**.</span></span> <span data-ttu-id="a6710-134">Na parte inferior do arquivo você verá o código que cria e atualiza sua pasta zip quando o aplicativo é construído:</span><span class="sxs-lookup"><span data-stu-id="a6710-134">At the bottom of the file you'll see the code that creates and updates your zip folder when the application builds:</span></span>

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

### <a name="models"></a><span data-ttu-id="a6710-135">Modelos</span><span class="sxs-lookup"><span data-stu-id="a6710-135">Models</span></span>

<span data-ttu-id="a6710-136">**O PersonalTab.cs** apresenta um objeto de mensagem e métodos que serão chamados do *PersonalTabController* quando um usuário selecionar um botão na **Exibição do PersonalTab.**</span><span class="sxs-lookup"><span data-stu-id="a6710-136">**PersonalTab.cs** presents a Message object and methods that will be called from *PersonalTabController* when a user selects a button in the **PersonalTab** View.</span></span>

### <a name="views"></a><span data-ttu-id="a6710-137">Exibições</span><span class="sxs-lookup"><span data-stu-id="a6710-137">Views</span></span>

#### <a name="home"></a><span data-ttu-id="a6710-138">Página Inicial</span><span class="sxs-lookup"><span data-stu-id="a6710-138">Home</span></span>

<span data-ttu-id="a6710-139">áspide.</span><span class="sxs-lookup"><span data-stu-id="a6710-139">ASP.</span></span> <span data-ttu-id="a6710-140">O NET Core trata arquivos chamados **Index** como a página padrão ou inicial para o site.</span><span class="sxs-lookup"><span data-stu-id="a6710-140">NET Core treats files called **Index** as the default or home page for the site.</span></span> <span data-ttu-id="a6710-141">Quando a URL do seu navegador aponta para a raiz do site, **o Index.cshtml** será exibido como a página inicial do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a6710-141">When your browser URL points to the root of the site, **Index.cshtml** will be displayed as the home page for your application.</span></span>

#### <a name="shared"></a><span data-ttu-id="a6710-142">Compartilhados</span><span class="sxs-lookup"><span data-stu-id="a6710-142">Shared</span></span>

<span data-ttu-id="a6710-143">A marcação de visualização parcial *_Layout.cshtml* contém a estrutura geral da página do aplicativo e elementos visuais compartilhados.</span><span class="sxs-lookup"><span data-stu-id="a6710-143">The partial view markup *_Layout.cshtml* contains the application's overall page structure and shared visual elements.</span></span> <span data-ttu-id="a6710-144">Também fará referência à Biblioteca Teams.</span><span class="sxs-lookup"><span data-stu-id="a6710-144">It will also reference the Teams Library.</span></span>

### <a name="controllers"></a><span data-ttu-id="a6710-145">Controladores</span><span class="sxs-lookup"><span data-stu-id="a6710-145">Controllers</span></span>

<span data-ttu-id="a6710-146">Os controladores usam a propriedade ViewBag para transferir valores dinamicamente para as Visualizações.</span><span class="sxs-lookup"><span data-stu-id="a6710-146">The controllers use the ViewBag property to transfer values dynamically to the Views.</span></span>

[!INCLUDE [dotnet-update-personal-app](~/includes/tabs/dotnet-update-personal-app.md)]

[!INCLUDE [dotnet-ngrok-intro](~/includes/tabs/dotnet-ngrok-intro.md)]

* <span data-ttu-id="a6710-147">Abra um prompt de comando na raiz do diretório do projeto e execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="a6710-147">Open a command prompt in the root of your project directory and run the following command:</span></span>

    ``` bash
    ngrok http https://localhost:44345 -host-header="localhost:44345"
    ```

* <span data-ttu-id="a6710-148">A Ngrok ouvirá os pedidos da internet e os encaminhará para o seu aplicativo quando estiver sendo executado na porta 44325.</span><span class="sxs-lookup"><span data-stu-id="a6710-148">Ngrok will listen to requests from the internet and will route them to your application when it is running on port 44325.</span></span>  <span data-ttu-id="a6710-149">Ele deve se assemelhar `https://y8rPrT2b.ngrok.io/` onde *y8rPrT2b* é substituído por sua URL HTTPS alfa-numérica ngrok.</span><span class="sxs-lookup"><span data-stu-id="a6710-149">It should resemble `https://y8rPrT2b.ngrok.io/` where *y8rPrT2b* is replaced by your ngrok alpha-numeric HTTPS URL.</span></span>

* <span data-ttu-id="a6710-150">Certifique-se de manter o prompt de comando com ngrok em execução e para anotar a URL — você precisará dele mais tarde.</span><span class="sxs-lookup"><span data-stu-id="a6710-150">Be sure to keep the command prompt with ngrok running, and to make a note of the URL — you'll need it later.</span></span>

* <span data-ttu-id="a6710-151">Verifique se **o ngrok** está executando e funcionando corretamente abrindo seu navegador e indo para sua página de conteúdo através da URL ngrok HTTPS que foi fornecida na janela do prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="a6710-151">Verify that **ngrok** is running and working properly by opening your browser and going to your content page via the ngrok HTTPS URL that was provided in your command prompt window.</span></span>

> [!TIP]
> <span data-ttu-id="a6710-152">Você precisa ter sua aplicação em Visual Studio e ngrok correndo para completar este quickstart.</span><span class="sxs-lookup"><span data-stu-id="a6710-152">You need to have both your application in Visual Studio and ngrok running to complete this quickstart.</span></span> <span data-ttu-id="a6710-153">Se você precisar parar de executar seu aplicativo em Visual Studio para trabalhar nele, **mantenha ngrok funcionando**.</span><span class="sxs-lookup"><span data-stu-id="a6710-153">If you need to stop running your application in Visual Studio to work on it, **keep ngrok running**.</span></span> <span data-ttu-id="a6710-154">Ele continuará ouvindo e retomará o encaminhamento da solicitação do seu aplicativo quando ele for reiniciado em Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a6710-154">It will continue to listen and will resume routing your application's request when it restarts in Visual Studio.</span></span> <span data-ttu-id="a6710-155">Se você tiver que reiniciar o serviço ngrok, ele retornará uma nova URL e você terá que atualizar todos os lugares que usarem essa URL.</span><span class="sxs-lookup"><span data-stu-id="a6710-155">If you have to restart the ngrok service it will return a new URL and you'll have to update every place that uses that URL.</span></span>

### <a name="run-your-application"></a><span data-ttu-id="a6710-156">Execute sua aplicação</span><span class="sxs-lookup"><span data-stu-id="a6710-156">Run your application</span></span>

* <span data-ttu-id="a6710-157">Em Visual Studio **pressione F5** ou escolha Iniciar a **depuração** no menu **Depuração** do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a6710-157">In Visual Studio press **F5** or choose **Start Debugging** from your application's **Debug** menu.</span></span>

[!INCLUDE [dotnet-personal-use-appstudio](~/includes/tabs/dotnet-personal-use-appstudio.md)]

## <a name="next-step"></a><span data-ttu-id="a6710-158">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="a6710-158">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a6710-159">Crie uma guia personalizada de canal e grupo usando Node.js e o Gerador Yeoman para Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="a6710-159">Create a custom channel and group tab using Node.js and the Yeoman Generator for Microsoft Teams</span></span>](~/tabs/quickstarts/create-channel-group-tab-node-yeoman.md)
