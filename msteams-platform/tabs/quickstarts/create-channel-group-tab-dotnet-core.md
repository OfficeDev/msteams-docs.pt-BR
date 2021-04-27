---
title: Criar uma guia Canal e Grupo com ASP.NET Core
author: laujan
description: Um guia de início rápido para criar um canal personalizado e uma guia de grupo com ASP.NET Core.
localization_priority: Normal
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: 8271e2d225d5ae3f6458b17b9595c4d23c3ca6c9
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019570"
---
# <a name="create-a-custom-channel-and-group-tab-with-aspnet-core"></a>Criar um Canal Personalizado e Uma Guia de Grupo com ASP.NET Core

Neste início rápido, vamos passo a passo criando uma guia de canal/grupo personalizada com a página C# e ASP.Net Core Razor. Também vamos usar o [App Studio para o Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) para finalizar o manifesto do aplicativo e implantar sua guia no Teams.

[!INCLUDE [dotnet-core-prereq](~/includes/tabs/dotnet-core-prereq.md)]

## <a name="get-the-source-code"></a>Obter o código-fonte

Abra um prompt de comando e crie um novo diretório para seu projeto de guia. Fornecemos um projeto simples para você começar. Para recuperar o código-fonte, você pode baixar a pasta zip e extrair os arquivos ou clonar o repositório de exemplo em seu novo diretório:

```bash
git clone https://github.com/OfficeDev/microsoft-teams-sample-tabs.git
```

Depois de ter o código-fonte, abra Visual Studio e selecione **Abrir um projeto ou solução**. Navegue até o diretório de aplicativos de tabulação e abra **ChannelGroupTab.sln**.

Para criar e executar seu aplicativo pressione **F5** ou escolha **Iniciar Depuração** no menu **Depurar.** Em um navegador, navegue até as URLs abaixo e verifique se o aplicativo foi carregado corretamente:

- `http://localhost:44355`
- `http://localhost:44355/privacy`
- `http://localhost:44355/tou`

## <a name="review-the-source-code"></a>Revisar o código-fonte

### <a name="startupcs"></a>Startup.cs

Este projeto foi criado ASP.NET modelo vazio do Aplicativo Web do Núcleo 2.2 com a caixa de seleção Avançado - Configurar para *HTTPS* selecionada na instalação. Os serviços MVC são registrados pelo método da estrutura de injeção de `ConfigureServices()` dependência. Além disso, o modelo vazio não habilita o serviço de conteúdo estático por padrão, portanto, o middleware de arquivos estáticos é adicionado ao `Configure()` método:

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

### <a name="wwwroot-folder"></a>pasta wwwroot

No ASP.NET Core, a pasta raiz da Web é onde o aplicativo procura arquivos estáticos.

### <a name="indexcshtml"></a>Index.cshtml

ASP.NET Core trata arquivos chamados *Index* como a home page padrão do site. Quando a URL do navegador aponta para a raiz do site, **Index.cshtml** será exibida como a home page do aplicativo.

### <a name="tabcs"></a>Tab.cs

Esse C# contém um método que será chamado de **Tab.cshtml** durante a configuração.

### <a name="appmanifest-folder"></a>Pasta AppManifest

Esta pasta contém os seguintes arquivos de pacote de aplicativos necessários:

- Um **ícone de cor completo** medindo 192 x 192 pixels.
- Um **ícone de contorno transparente** medindo 32 x 32 pixels.
- Um **manifest.json** que especifica os atributos do seu aplicativo.

Esses arquivos precisam ser cortados em um pacote de aplicativos para uso no carregamento da guia para o Teams. Quando um usuário optar por adicionar ou atualizar sua guia, o Microsoft Teams carregará o especificado em seu manifesto, o inserirá em um IFrame e o renderizará `configurationUrl` em sua guia.

### <a name="csproj"></a>.csproj

Na janela Visual Studio Do Explorador de Soluções clique com o botão direito do mouse no projeto e selecione **Editar Arquivo do Projeto**. Na parte inferior do arquivo, você verá o código que cria e atualiza sua pasta zip quando o aplicativo é construído:

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

- Abra um prompt de comando na raiz do diretório do projeto e execute o seguinte comando:

```bash
ngrok http https://localhost:44355 -host-header="localhost:44355"
```

- O Ngrok ouvirá as solicitações da Internet e as encaminhará para seu aplicativo quando estiver sendo executado na porta 44355. Deve parecer `https://y8rCgT2b.ngrok.io/` onde *y8rCgT2b* é substituído pela URL HTTPS alfanumérico ngrok.

- Certifique-se de manter o prompt de comando com o ngrok em execução e tomar nota da URL — você precisará dele mais tarde.

## <a name="update-your-application"></a>Atualizar seu aplicativo

Em *Tab.cshtml,* o aplicativo apresenta ao usuário dois botões de opção para exibir a guia com um ícone vermelho ou cinza. Escolher o **botão Selecionar Cinza** ou Selecionar **Vermelho** é acionado ou , respectivamente, define e habilita o botão Salvar `saveGray()` `saveRed()` na página de `settings.setValidityState(true)` configuração.  Esse código permite que o Teams saiba que você atendia aos requisitos de configuração e que a instalação pode continuar. Ao salvar, os parâmetros de `settings.setSettings` são definidos. Por fim, `saveEvent.notifySuccess()` é chamado para indicar que a URL de conteúdo foi resolvida com êxito.

[!INCLUDE [dotnet-update-app](~/includes/tabs/dotnet-update-chan-grp-app.md)]

