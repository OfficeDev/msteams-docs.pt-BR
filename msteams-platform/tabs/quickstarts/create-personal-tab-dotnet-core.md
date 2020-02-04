---
title: Criar uma guia pessoal com o ASP.NET Core
author: laujan
description: Um guia de início rápido para criar uma guia pessoal personalizada com o ASP.NET Core.
ms.topic: quickstart
ms.author: laujan
ms.openlocfilehash: b279c96f47265fe1928ae90d661e7dc042085b39
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672916"
---
# <a name="create-a-custom-personal-tab-with-aspnet-core"></a>Criar uma guia pessoal personalizada com o ASP.NET Core

Neste QuickStart, veremos como criar uma guia pessoal personalizada com as páginas principais do Razor do ASP.Net C# e do. Também usaremos o [app Studio para o Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) para finalizar o manifesto do aplicativo e implantar sua guia no Teams.

[!INCLUDE [dotnet-core-prereq](~/includes/tabs/dotnet-core-prereq.md)]

## <a name="get-the-source-code"></a>Obter o código-fonte

Abra um prompt de comando e crie um novo diretório para o projeto de tabulação. Fornecemos um projeto simples para ajudá-lo a começar. Para recuperar o código-fonte, você pode baixar a pasta zip e extrair os arquivos ou clonar o repositório de exemplo no novo diretório:

```bash
git clone https://github.com/OfficeDev/microsoft-teams-sample-tabs.git
```

Depois de ter o código-fonte, abra o Visual Studio e selecione **abrir um projeto ou solução**. Navegue até o diretório do aplicativo guia e abra **PersonalTab. sln**.

Para compilar e executar o aplicativo, pressione **F5** ou escolha **Iniciar Depuração** no menu **depurar** . Em um navegador, navegue até as URLs abaixo para verificar se o aplicativo foi carregado corretamente:

- `http://localhost:44325/`
- `http://localhost:44325/personal`
- `http://localhost:44325/privacy`
- `http://localhost:44325/tou`

## <a name="review-the-source-code"></a>Examinar o código-fonte

### <a name="startupcs"></a>Startup.cs

Este projeto foi criado a partir de um modelo vazio do aplicativo Web do ASP.NET Core 2,2 com a caixa de seleção *avançado-configurar para https* selecionada na instalação. Os serviços do MVC são registrados pelo método da `ConfigureServices()` estrutura de injeção de dependência. Além disso, o modelo vazio não habilita o fornecimento de conteúdo estático por padrão, portanto, o middleware de arquivos estáticos é adicionado ao `Configure()` método:

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

### <a name="indexcshtml"></a>Index. cshtml

ASP.NET Core trata os arquivos denominados *index* como o padrão/home page do site. Quando a URL do navegador apontar para a raiz do site, **index. cshtml** será exibido como a home page do seu aplicativo.

### <a name="appmanifest-folder"></a>Pasta arquivo AppManifest

Esta pasta contém os seguintes arquivos de pacote de aplicativos necessários:

- Um **ícone de cor completa** medindo 192 x 192 pixels.
- Um **ícone de contorno transparente** medindo 32 x 32 pixels.
- Um arquivo **manifest. JSON** que especifica os atributos do seu aplicativo.

Esses arquivos precisam ser zipados em um pacote de aplicativos para uso no carregamento de sua guia para o Microsoft Teams. O Microsoft Teams carregará o `contentUrl` especificado no manifesto, o incorporará em um iframe e o renderizará na sua guia.

### <a name="csproj"></a>. csproj

Na janela do Visual Studio Solution Explorer, clique com o botão direito do mouse no projeto e selecione **Editar arquivo de projeto**. Na parte inferior do arquivo, você verá o código que cria e atualiza sua pasta zip quando o aplicativo é criado:

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

- Abra um prompt de comando na raiz do diretório do projeto e execute o seguinte comando:

```bash
ngrok http https://localhost:44325 -host-header="localhost:44325"
```

- O Ngrok ouvirá as solicitações da Internet e as roteará para seu aplicativo quando estiver em execução na porta 44325.  Deve ser parecido com `https://y8rPrT2b.ngrok.io/` o local em que o *y8rPrT2b* é substituído pela URL https do ngrok alfanumérico.

- Certifique-se de manter o prompt de comando com o ngrok em execução e tome nota da URL — você precisará dela mais tarde.

- Verifique se o *ngrok* está em execução e funcionando corretamente abrindo o navegador e acessando a página de conteúdo por meio da URL https do ngrok que foi fornecida na janela de prompt de comando.

>[!TIP]
>Você precisa ter o aplicativo no Visual Studio e o ngrok em execução para concluir este QuickStart. Se você precisar parar a execução do aplicativo no Visual Studio para trabalhar nele, **Mantenha o ngrok em execução**. Ele continuará a escutar e retomará o roteamento da solicitação do aplicativo quando ele for reiniciado no Visual Studio. Se for necessário reiniciar o serviço do ngrok, ele retornará uma nova URL e você terá que atualizar todos os locais que usam essa URL.

### <a name="run-your-application"></a>Executar o aplicativo

- No Visual Studio, pressione **F5** ou escolha **Iniciar Depuração** no menu **depurar** do aplicativo.

[!INCLUDE [dotnet-personal-use-appstudio](~/includes/tabs/dotnet-personal-use-appstudio.md)]
