---
title: Criar uma guia Canal e Grupo com ASP.NET Core MVC
author: laujan
description: Um guia de início rápido para criar um canal personalizado e uma guia de grupo com ASP.NET Core MVC
localization_priority: Normal
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: 9d89fd98bae9732a8f9e2d34b82d7fc0e6985e01
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020307"
---
# <a name="create-a-custom-channel-and-group-tab-with-aspnet-core-mvc"></a><span data-ttu-id="ae042-103">Criar um Canal Personalizado e Uma Guia de Grupo com ASP.NET Core MVC</span><span class="sxs-lookup"><span data-stu-id="ae042-103">Create a Custom Channel and Group Tab with ASP.NET Core MVC</span></span>

<span data-ttu-id="ae042-104">Neste início rápido, vamos passo a passo criando uma guia de canal/grupo personalizada com C# e ASP.Net Core MVC.</span><span class="sxs-lookup"><span data-stu-id="ae042-104">In this quickstart we'll walk-through creating a custom channel/group tab with C# and ASP.Net Core MVC.</span></span> <span data-ttu-id="ae042-105">Também vamos usar o [App Studio para o Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) para finalizar o manifesto do aplicativo e implantar sua guia no Teams.</span><span class="sxs-lookup"><span data-stu-id="ae042-105">We'll also use [App Studio for Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) to finalize your app manifest and deploy your tab to Teams.</span></span>

[!INCLUDE [dotnet-core-prereq](~/includes/tabs/dotnet-core-prereq.md)]

## <a name="get-the-source-code"></a><span data-ttu-id="ae042-106">Obter o código-fonte</span><span class="sxs-lookup"><span data-stu-id="ae042-106">Get the source code</span></span>

<span data-ttu-id="ae042-107">Abra um prompt de comando e crie um novo diretório para seu projeto de guia.</span><span class="sxs-lookup"><span data-stu-id="ae042-107">Open a command prompt and create a new directory for your tab project.</span></span> <span data-ttu-id="ae042-108">Fornecemos um projeto simples [de Guia de Grupo](https://github.com/OfficeDev/microsoft-teams-sample-tabs/ChannelGroupTabMVC) de Canal para você começar.</span><span class="sxs-lookup"><span data-stu-id="ae042-108">We have provided a simple [Channel Group Tab](https://github.com/OfficeDev/microsoft-teams-sample-tabs/ChannelGroupTabMVC) project to get you started.</span></span> <span data-ttu-id="ae042-109">Para recuperar o código-fonte, você pode baixar a pasta zip e extrair os arquivos ou clonar o repositório de exemplo em seu novo diretório:</span><span class="sxs-lookup"><span data-stu-id="ae042-109">To retrieve the source code you can download the zip folder and extract the files or clone the sample repository into your new directory:</span></span>

```bash
git clone https://github.com/OfficeDev/microsoft-teams-sample-tabs.git
```

<span data-ttu-id="ae042-110">Depois de ter o código-fonte, abra Visual Studio e selecione **Abrir um projeto ou solução**.</span><span class="sxs-lookup"><span data-stu-id="ae042-110">Once you have the source code, open Visual Studio and select **Open a project or solution**.</span></span> <span data-ttu-id="ae042-111">Navegue até o diretório de aplicativos de tabulação e abra **ChannelGroupTabMVC.sln**.</span><span class="sxs-lookup"><span data-stu-id="ae042-111">Navigate to the tab application directory and open **ChannelGroupTabMVC.sln**.</span></span>

<span data-ttu-id="ae042-112">Para criar e executar seu aplicativo pressione **F5** ou escolha **Iniciar Depuração** no menu **Depurar.**</span><span class="sxs-lookup"><span data-stu-id="ae042-112">To build and run your application press **F5** or choose **Start Debugging** from the **Debug** menu.</span></span> <span data-ttu-id="ae042-113">Em um navegador, navegue até as URLs abaixo e verifique se o aplicativo foi carregado corretamente:</span><span class="sxs-lookup"><span data-stu-id="ae042-113">In a browser, navigate to the URLs below and verify that the application loaded properly:</span></span>

- `http://localhost:44360`
- `http://localhost:44360/privacy`
- `http://localhost:44360/tou`

## <a name="review-the-source-code"></a><span data-ttu-id="ae042-114">Revisar o código-fonte</span><span class="sxs-lookup"><span data-stu-id="ae042-114">Review the source code</span></span>

### <a name="startupcs"></a><span data-ttu-id="ae042-115">Startup.cs</span><span class="sxs-lookup"><span data-stu-id="ae042-115">Startup.cs</span></span>

<span data-ttu-id="ae042-116">Este projeto foi criado ASP.NET modelo vazio do Aplicativo Web do Núcleo 2.2 com a caixa de seleção Avançado - Configurar para *HTTPS* selecionada na instalação.</span><span class="sxs-lookup"><span data-stu-id="ae042-116">This project was created from an ASP.NET Core 2.2 Web Application empty template with the *Advanced - Configure for HTTPS* check box selected at setup.</span></span> <span data-ttu-id="ae042-117">Os serviços MVC são registrados pelo método da estrutura de injeção de `ConfigureServices()` dependência.</span><span class="sxs-lookup"><span data-stu-id="ae042-117">The MVC services are registered by the dependency injection framework's `ConfigureServices()` method.</span></span> <span data-ttu-id="ae042-118">Além disso, o modelo vazio não habilita o serviço de conteúdo estático por padrão, portanto, o middleware de arquivos estáticos é adicionado ao `Configure()` método:</span><span class="sxs-lookup"><span data-stu-id="ae042-118">Additionally, the empty template doesn't enable serving static content by default, so the static files middleware is added to the `Configure()` method:</span></span>

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

### <a name="wwwroot-folder"></a><span data-ttu-id="ae042-119">pasta wwwroot</span><span class="sxs-lookup"><span data-stu-id="ae042-119">wwwroot folder</span></span>

<span data-ttu-id="ae042-120">No ASP.NET Core, a pasta raiz da Web é onde o aplicativo procura arquivos estáticos.</span><span class="sxs-lookup"><span data-stu-id="ae042-120">In ASP.NET Core, the web root folder is where the application looks for static files.</span></span>

### <a name="appmanifest-folder"></a><span data-ttu-id="ae042-121">Pasta AppManifest</span><span class="sxs-lookup"><span data-stu-id="ae042-121">AppManifest folder</span></span>

<span data-ttu-id="ae042-122">Esta pasta contém os seguintes arquivos de pacote de aplicativos necessários:</span><span class="sxs-lookup"><span data-stu-id="ae042-122">This folder contains the following required app package files:</span></span>

- <span data-ttu-id="ae042-123">Um **ícone de cor completo** medindo 192 x 192 pixels.</span><span class="sxs-lookup"><span data-stu-id="ae042-123">A **full color icon** measuring 192 x 192 pixels.</span></span>
- <span data-ttu-id="ae042-124">Um **ícone de contorno transparente** medindo 32 x 32 pixels.</span><span class="sxs-lookup"><span data-stu-id="ae042-124">A **transparent outline icon** measuring 32 x 32 pixels.</span></span>
- <span data-ttu-id="ae042-125">Um **manifest.json** que especifica os atributos do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ae042-125">A **manifest.json** file that specifies the attributes of your app.</span></span>

<span data-ttu-id="ae042-126">Esses arquivos precisam ser cortados em um pacote de aplicativos para uso no carregamento da guia para o Teams.</span><span class="sxs-lookup"><span data-stu-id="ae042-126">These files need to be zipped in an app package for use in uploading your tab to Teams.</span></span>

### <a name="csproj"></a><span data-ttu-id="ae042-127">.csproj</span><span class="sxs-lookup"><span data-stu-id="ae042-127">.csproj</span></span>

<span data-ttu-id="ae042-128">Na janela Visual Studio Do Explorador de Soluções clique com o botão direito do mouse no projeto e selecione **Editar Arquivo do Projeto**.</span><span class="sxs-lookup"><span data-stu-id="ae042-128">In the Visual Studio Solution Explorer window right-click on the project and select **Edit Project File**.</span></span> <span data-ttu-id="ae042-129">Na parte inferior do arquivo, você verá o código que cria e atualiza sua pasta zip quando o aplicativo é construído:</span><span class="sxs-lookup"><span data-stu-id="ae042-129">At the bottom of the file you'll see the code that creates and updates your zip folder when the application builds:</span></span>

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

### <a name="models"></a><span data-ttu-id="ae042-130">Modelos</span><span class="sxs-lookup"><span data-stu-id="ae042-130">Models</span></span>

<span data-ttu-id="ae042-131">*ChannelGroup.cs* apresenta um objeto Message e métodos que serão chamados dos Controladores durante a configuração.</span><span class="sxs-lookup"><span data-stu-id="ae042-131">*ChannelGroup.cs* presents a Message object and methods that will be called from the Controllers during configuration.</span></span>

### <a name="views"></a><span data-ttu-id="ae042-132">Modos de exibição</span><span class="sxs-lookup"><span data-stu-id="ae042-132">Views</span></span>

#### <a name="home"></a><span data-ttu-id="ae042-133">Página Inicial</span><span class="sxs-lookup"><span data-stu-id="ae042-133">Home</span></span>

<span data-ttu-id="ae042-134">ASP.NET Core trata arquivos chamados *Index* como a home page padrão do site.</span><span class="sxs-lookup"><span data-stu-id="ae042-134">ASP.NET Core treats files called *Index* as the default/home page for the site.</span></span> <span data-ttu-id="ae042-135">Quando a URL do navegador aponta para a raiz do site, **Index.cshtml** será exibida como a home page do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ae042-135">When your browser URL points to the root of the site, **Index.cshtml** will be displayed as the home page for your application.</span></span>

#### <a name="shared"></a><span data-ttu-id="ae042-136">Compartilhados</span><span class="sxs-lookup"><span data-stu-id="ae042-136">Shared</span></span>

<span data-ttu-id="ae042-137">A marcação de exibição *parcial _Layout.cshtml* contém a estrutura geral da página do aplicativo e elementos visuais compartilhados.</span><span class="sxs-lookup"><span data-stu-id="ae042-137">The partial view markup *_Layout.cshtml* contains the application's overall page structure and shared visual elements.</span></span> <span data-ttu-id="ae042-138">Ele também fará referência à Biblioteca do Teams.</span><span class="sxs-lookup"><span data-stu-id="ae042-138">It will also reference the Teams Library.</span></span>

### <a name="controllers"></a><span data-ttu-id="ae042-139">Controladores</span><span class="sxs-lookup"><span data-stu-id="ae042-139">Controllers</span></span>

<span data-ttu-id="ae042-140">Os controladores usam a propriedade ViewBag para transferir valores dinamicamente para o Views.</span><span class="sxs-lookup"><span data-stu-id="ae042-140">The controllers use the ViewBag property to transfer values dynamically to the Views.</span></span>

[!INCLUDE [dotnet-ngrok-intro](~/includes/tabs/dotnet-ngrok-intro.md)]

- <span data-ttu-id="ae042-141">Abra um prompt de comando na raiz do diretório do projeto e execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="ae042-141">Open a command prompt in the root of your project directory and run the following command:</span></span>

```bash
ngrok http https://localhost:443560 -host-header="localhost:44360"
```

- <span data-ttu-id="ae042-142">O Ngrok ouvirá as solicitações da Internet e as encaminhará para seu aplicativo quando estiver sendo executado na porta 44355.</span><span class="sxs-lookup"><span data-stu-id="ae042-142">Ngrok will listen to requests from the internet and will route them to your application when it is running on port 44355.</span></span>  <span data-ttu-id="ae042-143">Deve parecer `https://y8rCgT2b.ngrok.io/` onde *y8rCgT2b* é substituído pela URL HTTPS alfanumérico ngrok.</span><span class="sxs-lookup"><span data-stu-id="ae042-143">It should resemble `https://y8rCgT2b.ngrok.io/` where *y8rCgT2b* is replaced by your ngrok alpha-numeric HTTPS URL.</span></span>

- <span data-ttu-id="ae042-144">Certifique-se de manter o prompt de comando com o ngrok em execução e tomar nota da URL — você precisará dele mais tarde.</span><span class="sxs-lookup"><span data-stu-id="ae042-144">Be sure to keep the command prompt with ngrok running and to make note of the URL — you'll need it later.</span></span>

## <a name="update-your-application"></a><span data-ttu-id="ae042-145">Atualizar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="ae042-145">Update your application</span></span>

<span data-ttu-id="ae042-146">Em **Tab.cshtml,** o aplicativo apresenta ao usuário dois botões de opção para exibir a guia com um ícone vermelho ou cinza.</span><span class="sxs-lookup"><span data-stu-id="ae042-146">Within **Tab.cshtml** the application presents the user with two option buttons for displaying the tab with either a red or gray icon.</span></span> <span data-ttu-id="ae042-147">Escolher o **botão Selecionar Cinza** ou Selecionar **Vermelho** é acionado ou , respectivamente, define e habilita o botão Salvar `saveGray()` `saveRed()` na página de `settings.setValidityState(true)` configuração. </span><span class="sxs-lookup"><span data-stu-id="ae042-147">Choosing the **Select Gray** or **Select Red** button fires `saveGray()` or `saveRed()`, respectively, sets `settings.setValidityState(true)`, and enables the **Save** button on the configuration page.</span></span> <span data-ttu-id="ae042-148">Esse código permite que o Teams saiba que você atendia aos requisitos de configuração e que a instalação pode continuar.</span><span class="sxs-lookup"><span data-stu-id="ae042-148">This code lets Teams know that you have satisfied the configuration requirements and the installation can proceed.</span></span> <span data-ttu-id="ae042-149">Ao salvar, os parâmetros de `settings.setSettings` são definidos.</span><span class="sxs-lookup"><span data-stu-id="ae042-149">On save, the parameters of `settings.setSettings` are set.</span></span> <span data-ttu-id="ae042-150">Por fim, `saveEvent.notifySuccess()` é chamado para indicar que a URL de conteúdo foi resolvida com êxito.</span><span class="sxs-lookup"><span data-stu-id="ae042-150">Finally, `saveEvent.notifySuccess()` is called to indicate that the content URL has successfully resolved.</span></span>

[!INCLUDE [dotnet-update-app](~/includes/tabs/dotnet-update-chan-grp-app.md)]

[!INCLUDE [dotnet-upload-to-teams](~/includes/tabs/dotnet-upload-to-teams.md)]
