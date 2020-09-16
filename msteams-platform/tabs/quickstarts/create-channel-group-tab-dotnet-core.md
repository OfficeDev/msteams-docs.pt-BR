---
title: Criar uma guia de canal e grupo com o ASP.NET Core
author: laujan
description: Um guia de início rápido para criar uma guia de canal e grupo personalizado com o ASP.NET Core.
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: 6a21d40d4d474fd587b43760d818082b4ab2502d
ms.sourcegitcommit: e8dfcb167274e996395b77d65999991a18f2051a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "47818917"
---
# <a name="create-a-custom-channel-and-group-tab-with-aspnet-core"></a><span data-ttu-id="0eb27-103">Criar uma guia de canal e grupo personalizado com o ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0eb27-103">Create a Custom Channel and Group Tab with ASP.NET Core</span></span>

<span data-ttu-id="0eb27-104">Neste QuickStart, abordaremos a criação de uma guia de canal/grupo personalizado com a página principal do Razor em C# e ASP.Net.</span><span class="sxs-lookup"><span data-stu-id="0eb27-104">In this quickstart we'll walk-through creating a custom channel/group tab with C# and ASP.Net Core Razor page.</span></span> <span data-ttu-id="0eb27-105">Também usaremos o [app Studio para o Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) para finalizar o manifesto do aplicativo e implantar sua guia no Teams.</span><span class="sxs-lookup"><span data-stu-id="0eb27-105">We'll also use [App Studio for Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) to finalize your app manifest and deploy your tab to Teams.</span></span>

[!INCLUDE [dotnet-core-prereq](~/includes/tabs/dotnet-core-prereq.md)]

## <a name="get-the-source-code"></a><span data-ttu-id="0eb27-106">Obter o código-fonte</span><span class="sxs-lookup"><span data-stu-id="0eb27-106">Get the source code</span></span>

<span data-ttu-id="0eb27-107">Abra um prompt de comando e crie um novo diretório para o projeto de tabulação.</span><span class="sxs-lookup"><span data-stu-id="0eb27-107">Open a command prompt and create a new directory for your tab project.</span></span> <span data-ttu-id="0eb27-108">Fornecemos um projeto simples para ajudá-lo a começar.</span><span class="sxs-lookup"><span data-stu-id="0eb27-108">We have provided a simple project to get you started.</span></span> <span data-ttu-id="0eb27-109">Para recuperar o código-fonte, você pode baixar a pasta zip e extrair os arquivos ou clonar o repositório de exemplo no novo diretório:</span><span class="sxs-lookup"><span data-stu-id="0eb27-109">To retrieve the source code you can download the zip folder and extract the files or clone the sample repository into your new directory:</span></span>

```bash
git clone https://github.com/OfficeDev/microsoft-teams-sample-tabs.git
```

<span data-ttu-id="0eb27-110">Depois de ter o código-fonte, abra o Visual Studio e selecione **abrir um projeto ou solução**.</span><span class="sxs-lookup"><span data-stu-id="0eb27-110">Once you have the source code, open Visual Studio and select **Open a project or solution**.</span></span> <span data-ttu-id="0eb27-111">Navegue até o diretório do aplicativo guia e abra **ChannelGroupTab. sln**.</span><span class="sxs-lookup"><span data-stu-id="0eb27-111">Navigate to the tab application directory and open **ChannelGroupTab.sln**.</span></span>

<span data-ttu-id="0eb27-112">Para compilar e executar o aplicativo, pressione **F5** ou escolha **Iniciar Depuração** no menu **depurar** .</span><span class="sxs-lookup"><span data-stu-id="0eb27-112">To build and run your application press **F5** or choose **Start Debugging** from the **Debug** menu.</span></span> <span data-ttu-id="0eb27-113">Em um navegador, navegue até as URLs abaixo e verifique se o aplicativo foi carregado corretamente:</span><span class="sxs-lookup"><span data-stu-id="0eb27-113">In a browser navigate to the URLs below and verify the application loaded properly:</span></span>

- `http://localhost:44355`
- `http://localhost:44355/privacy`
- `http://localhost:44355/tou`

## <a name="review-the-source-code"></a><span data-ttu-id="0eb27-114">Examinar o código-fonte</span><span class="sxs-lookup"><span data-stu-id="0eb27-114">Review the source code</span></span>

### <a name="startupcs"></a><span data-ttu-id="0eb27-115">Startup.cs</span><span class="sxs-lookup"><span data-stu-id="0eb27-115">Startup.cs</span></span>

<span data-ttu-id="0eb27-116">Este projeto foi criado a partir de um modelo vazio do aplicativo Web do ASP.NET Core 2,2 com a caixa de seleção *avançado-configurar para https* selecionada na instalação.</span><span class="sxs-lookup"><span data-stu-id="0eb27-116">This project was created from an ASP.NET Core 2.2 Web Application empty template with the *Advanced - Configure for HTTPS* check box selected at setup.</span></span> <span data-ttu-id="0eb27-117">Os serviços do MVC são registrados pelo método da estrutura de injeção de dependência `ConfigureServices()` .</span><span class="sxs-lookup"><span data-stu-id="0eb27-117">The MVC services are registered by the dependency injection framework's `ConfigureServices()` method.</span></span> <span data-ttu-id="0eb27-118">Além disso, o modelo vazio não habilita o fornecimento de conteúdo estático por padrão, portanto, o middleware de arquivos estáticos é adicionado ao `Configure()` método:</span><span class="sxs-lookup"><span data-stu-id="0eb27-118">Additionally, the empty template doesn't enable serving static content by default, so the static files middleware is added to the `Configure()` method:</span></span>

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

### <a name="wwwroot-folder"></a><span data-ttu-id="0eb27-119">pasta wwwroot</span><span class="sxs-lookup"><span data-stu-id="0eb27-119">wwwroot folder</span></span>

<span data-ttu-id="0eb27-120">No ASP.NET Core, a pasta raiz da Web é onde o aplicativo procura arquivos estáticos.</span><span class="sxs-lookup"><span data-stu-id="0eb27-120">In ASP.NET Core, the web root folder is where the application looks for static files.</span></span>

### <a name="indexcshtml"></a><span data-ttu-id="0eb27-121">Index. cshtml</span><span class="sxs-lookup"><span data-stu-id="0eb27-121">Index.cshtml</span></span>

<span data-ttu-id="0eb27-122">ASP.NET Core trata os arquivos denominados *index* como o padrão/home page do site.</span><span class="sxs-lookup"><span data-stu-id="0eb27-122">ASP.NET Core treats files called *Index* as the default/home page for the site.</span></span> <span data-ttu-id="0eb27-123">Quando a URL do navegador apontar para a raiz do site, **index. cshtml** será exibido como a home page do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0eb27-123">When your browser URL points to the root of the site, **Index.cshtml** will be displayed as the home page for your application.</span></span>

### <a name="tabcs"></a><span data-ttu-id="0eb27-124">Tab.cs</span><span class="sxs-lookup"><span data-stu-id="0eb27-124">Tab.cs</span></span>

<span data-ttu-id="0eb27-125">Este arquivo C# contém um método que será chamado a partir de **Tab. cshtml** durante a configuração.</span><span class="sxs-lookup"><span data-stu-id="0eb27-125">This C# file contains a method that will be called from **Tab.cshtml** during configuration.</span></span>

### <a name="appmanifest-folder"></a><span data-ttu-id="0eb27-126">Pasta arquivo AppManifest</span><span class="sxs-lookup"><span data-stu-id="0eb27-126">AppManifest folder</span></span>

<span data-ttu-id="0eb27-127">Esta pasta contém os seguintes arquivos de pacote de aplicativos necessários:</span><span class="sxs-lookup"><span data-stu-id="0eb27-127">This folder contains the following required app package files:</span></span>

- <span data-ttu-id="0eb27-128">Um **ícone de cor completa** medindo 192 x 192 pixels.</span><span class="sxs-lookup"><span data-stu-id="0eb27-128">A **full color icon** measuring 192 x 192 pixels.</span></span>
- <span data-ttu-id="0eb27-129">Um **ícone de contorno transparente** medindo 32 x 32 pixels.</span><span class="sxs-lookup"><span data-stu-id="0eb27-129">A **transparent outline icon** measuring 32 x 32 pixels.</span></span>
- <span data-ttu-id="0eb27-130">Um **manifest.jsno** arquivo que especifica os atributos do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0eb27-130">A **manifest.json** file that specifies the attributes of your app.</span></span>

<span data-ttu-id="0eb27-131">Esses arquivos precisam ser zipados em um pacote de aplicativos para uso no carregamento de sua guia para o Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="0eb27-131">These files need to be zipped in an app package for use in uploading your tab to Teams.</span></span> <span data-ttu-id="0eb27-132">Quando um usuário optar por adicionar ou atualizar sua guia, o Microsoft Teams carregará o `configurationUrl` especificado no manifesto, o incorporará em um iframe e o renderizará na sua guia.</span><span class="sxs-lookup"><span data-stu-id="0eb27-132">When a user chooses to add or update your tab, Microsoft Teams will load the `configurationUrl` specified in your manifest, embed it in an IFrame, and render it in your tab.</span></span>

### <a name="csproj"></a><span data-ttu-id="0eb27-133">. csproj</span><span class="sxs-lookup"><span data-stu-id="0eb27-133">.csproj</span></span>

<span data-ttu-id="0eb27-134">Na janela do Visual Studio Solution Explorer, clique com o botão direito do mouse no projeto e selecione **Editar arquivo de projeto**.</span><span class="sxs-lookup"><span data-stu-id="0eb27-134">In the Visual Studio Solution Explorer window right-click on the project and select **Edit Project File**.</span></span> <span data-ttu-id="0eb27-135">Na parte inferior do arquivo, você verá o código que cria e atualiza sua pasta zip quando o aplicativo é criado:</span><span class="sxs-lookup"><span data-stu-id="0eb27-135">At the bottom of the file you'll see the code that creates and updates your zip folder when the application builds:</span></span>

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

[!INCLUDE [dotnet-ngrok-intro](~/includes/tabs/dotnet-ngrok-intro.md)]

- <span data-ttu-id="0eb27-136">Abra um prompt de comando na raiz do diretório do projeto e execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="0eb27-136">Open a command prompt in the root of your project directory and run the following command:</span></span>

```bash
ngrok http https://localhost:44355 -host-header="localhost:44355"
```

- <span data-ttu-id="0eb27-137">O Ngrok ouvirá as solicitações da Internet e as roteará para seu aplicativo quando estiver em execução na porta 44355.</span><span class="sxs-lookup"><span data-stu-id="0eb27-137">Ngrok will listen to requests from the internet and will route them to your application when it is running on port 44355.</span></span> <span data-ttu-id="0eb27-138">Deve ser parecido `https://y8rCgT2b.ngrok.io/` com o local em que o *y8rCgT2b* é substituído pela URL https do ngrok alfanumérico.</span><span class="sxs-lookup"><span data-stu-id="0eb27-138">It should resemble `https://y8rCgT2b.ngrok.io/` where *y8rCgT2b* is replaced by your ngrok alpha-numeric HTTPS URL.</span></span>

- <span data-ttu-id="0eb27-139">Certifique-se de manter o prompt de comando com o ngrok em execução e tome nota da URL — você precisará dela mais tarde.</span><span class="sxs-lookup"><span data-stu-id="0eb27-139">Be sure to keep the command prompt with ngrok running and to make note of the URL — you'll need it later.</span></span>

## <a name="update-your-application"></a><span data-ttu-id="0eb27-140">Atualizar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="0eb27-140">Update your application</span></span>

<span data-ttu-id="0eb27-141">Na *guia. cshtml* o aplicativo apresenta ao usuário dois botões de opção para exibir a guia com um ícone vermelho ou cinza.</span><span class="sxs-lookup"><span data-stu-id="0eb27-141">Within *Tab.cshtml* the application presents the user with two option buttons for displaying the tab with either a red or gray icon.</span></span> <span data-ttu-id="0eb27-142">A seleção do botão **selecionar cinza** ou **selecionar vermelho** dispara `saveGray()` ou `saveRed()` , respectivamente, define `settings.setValidityState(true)` e habilita o botão **salvar** na página de configuração.</span><span class="sxs-lookup"><span data-stu-id="0eb27-142">Choosing the **Select Gray** or **Select Red** button fires `saveGray()` or `saveRed()`, respectively, sets `settings.setValidityState(true)`, and enables the **Save** button on the configuration page.</span></span> <span data-ttu-id="0eb27-143">Esse código permite que as equipes saibam que você atende aos requisitos de configuração e a instalação pode continuar.</span><span class="sxs-lookup"><span data-stu-id="0eb27-143">This code lets Teams know that you have satisfied the configuration requirements and the installation can proceed.</span></span> <span data-ttu-id="0eb27-144">Ao salvar, os parâmetros de `settings.setSettings` são definidos.</span><span class="sxs-lookup"><span data-stu-id="0eb27-144">On save, the parameters of `settings.setSettings` are set.</span></span> <span data-ttu-id="0eb27-145">Por fim, `saveEvent.notifySuccess()` é chamado para indicar que a URL de conteúdo foi resolvida com êxito.</span><span class="sxs-lookup"><span data-stu-id="0eb27-145">Finally, `saveEvent.notifySuccess()` is called to indicate that the content URL has successfully resolved.</span></span>

[!INCLUDE [dotnet-update-app](~/includes/tabs/dotnet-update-chan-grp-app.md)]

