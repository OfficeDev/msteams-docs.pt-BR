---
title: Crie uma guia pessoal com ASP. NET Core MVC
author: laujan
description: Um guia de início rápido para criar uma guia pessoal personalizada com ASP. NET Core MVC.
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
# <a name="create-a-custom-personal-tab-with-aspnet-core-mvc"></a>Criar uma guia pessoal personalizada com ASP.NET Core MVC

Neste início rápido, vamos passo a passo criando uma guia pessoal personalizada com C# e ASP.Net Core MVC. Também vamos usar o [App Studio para Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) finalizar o manifesto do aplicativo e implantar sua guia Teams.

[!INCLUDE [dotnet-core-prereq](~/includes/tabs/dotnet-core-prereq.md)]

## <a name="get-the-source-code"></a>Obter o código-fonte

Abra um prompt de comando e crie um novo diretório para seu projeto de guia. Fornecemos um projeto simples para você começar. Para recuperar o código-fonte, você pode baixar a pasta zip e extrair os arquivos ou clonar o repositório de exemplo em seu novo diretório:

``` bash
git clone https://github.com/OfficeDev/microsoft-teams-sample-tabs.git
```

Depois de ter o código-fonte, abra Visual Studio e selecione **Abrir um projeto ou solução**. Navegue até o diretório do aplicativo de tabulação e abra **PersonalTabMVC.sln**.

Para criar e executar seu aplicativo pressione **F5** ou escolha **Iniciar Depuração** no menu **Depurar.** Em um navegador, navegue até as URLs abaixo para verificar se o aplicativo foi carregado corretamente:

* `http://localhost:44335`
* `http://localhost:44335/privacy`
* `http://localhost:44335/tou`

## <a name="review-the-source-code"></a>Revisar o código-fonte

### <a name="startupcs"></a>Startup.cs

Esse projeto foi criado a partir de um ASP. Modelo vazio do Aplicativo Web net Core 2.2 com a caixa de seleção *Avançado - Configurar para HTTPS* selecionada na instalação. Os serviços MVC são registrados pelo método da estrutura de injeção de `ConfigureServices()` dependência. Além disso, o modelo vazio não habilita o serviço de conteúdo estático por padrão, portanto, o middleware de arquivos estáticos é adicionado ao `Configure()` método:

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

### <a name="wwwroot-folder"></a>pasta wwwroot

Em ASP. NET Core, a pasta raiz da Web é onde o aplicativo procura arquivos estáticos.

### <a name="appmanifest-folder"></a>Pasta AppManifest

Esta pasta contém os seguintes arquivos de pacote de aplicativos necessários:

* Um **ícone de cor completo** medindo 192 x 192 pixels.
* Um **ícone de contorno transparente** medindo 32 x 32 pixels.
* Um **manifest.json** que especifica os atributos do seu aplicativo.

Esses arquivos precisam ser cortados em um pacote de aplicativos para uso ao carregar sua guia para Teams. Microsoft Teams carregará o especificado em seu manifesto, o inserirá em um IFrame e `contentUrl` o renderizará em sua guia.

### <a name="csproj"></a>.csproj

Na janela Visual Studio Do Explorador de Soluções clique com o botão direito do mouse no projeto e selecione **Editar Project Arquivo**. Na parte inferior do arquivo, você verá o código que cria e atualiza sua pasta zip quando o aplicativo é construído:

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

### <a name="models"></a>Modelos

**PersonalTab.cs** apresenta um objeto Message e métodos que serão chamados de *PersonalTabController* quando um usuário selecionar um botão no Modo de Exibição **PersonalTab.**

### <a name="views"></a>Exibições

#### <a name="home"></a>Página Inicial

ASP. O NET Core trata os arquivos chamados **Index** como o padrão ou home page do site. Quando a URL do navegador aponta para a raiz do site, **Index.cshtml** será exibida como a home page do aplicativo.

#### <a name="shared"></a>Compartilhados

A marcação de exibição *parcial _Layout.cshtml* contém a estrutura geral da página do aplicativo e elementos visuais compartilhados. Ele também fará referência à biblioteca Teams.

### <a name="controllers"></a>Controladores

Os controladores usam a propriedade ViewBag para transferir valores dinamicamente para o Views.

[!INCLUDE [dotnet-update-personal-app](~/includes/tabs/dotnet-update-personal-app.md)]

[!INCLUDE [dotnet-ngrok-intro](~/includes/tabs/dotnet-ngrok-intro.md)]

* Abra um prompt de comando na raiz do diretório do projeto e execute o seguinte comando:

    ``` bash
    ngrok http https://localhost:44345 -host-header="localhost:44345"
    ```

* O Ngrok ouvirá as solicitações da Internet e as encaminhará para seu aplicativo quando estiver sendo executado na porta 44325.  Deve parecer `https://y8rPrT2b.ngrok.io/` onde *y8rPrT2b* é substituído pela URL HTTPS alfanumérico ngrok.

* Certifique-se de manter o prompt de comando com o ngrok em execução e para anotar a URL , você precisará dele mais tarde.

* Verifique se **o ngrok** está sendo executado e funcionando corretamente abrindo seu navegador e indo para sua página de conteúdo por meio da URL HTTPS ngrok fornecida na janela do prompt de comando.

> [!TIP]
> Você precisa ter seu aplicativo em Visual Studio e ngrok em execução para concluir esse início rápido. Se você precisar parar de executar seu aplicativo Visual Studio para trabalhar nele, **mantenha o ngrok em execução**. Ele continuará escutando e retomará o roteamento da solicitação do aplicativo quando ele for reiniciado no Visual Studio. Se você precisar reiniciar o serviço ngrok, ele retornará uma nova URL e será preciso atualizar todos os lugares que usam essa URL.

### <a name="run-your-application"></a>Executar seu aplicativo

* Em Visual Studio pressione **F5** ou escolha **Iniciar Depuração** no menu **Depuração do** aplicativo.

[!INCLUDE [dotnet-personal-use-appstudio](~/includes/tabs/dotnet-personal-use-appstudio.md)]

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Crie um canal personalizado e uma guia de grupo usando Node.js e o Gerador Yeoman para Microsoft Teams](~/tabs/quickstarts/create-channel-group-tab-node-yeoman.md)
