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
# <a name="create-a-personal-tab-using-aspnetcore"></a>Crie uma guia pessoal usando o ASP.NETCore

Nesta partida rápida, vamos caminhar criando uma guia pessoal personalizada com páginas C# e ASP.Net Core Razor. Também usaremos [o App Studio para Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) para finalizar seu manifesto de aplicativo e implantar sua guia para Teams.

[!INCLUDE [dotnet-core-prereq](~/includes/tabs/dotnet-core-prereq.md)]

## <a name="get-the-source-code"></a>Obtenha o código fonte

Abra um prompt de comando e crie um novo diretório para o seu projeto de guia. Nós fornecemos um projeto simples para começar você. Para recuperar o código-fonte, você pode baixar a pasta zip e extrair os arquivos ou clonar o repositório de amostras em seu novo diretório:

```bash
git clone https://github.com/OfficeDev/microsoft-teams-sample-tabs.git
```

Depois de ter o código-fonte, abra Visual Studio e selecione **Abrir um projeto ou solução**. Navegue até o diretório de aplicativos da guia e abra **o PersonalTab.sln**.

Para construir e executar seu aplicativo pressione **F5** ou escolha Iniciar a **depuração** no menu **Debug.** Em um navegador navegue até os URLs abaixo para verificar o aplicativo carregado corretamente:

- `http://localhost:44325/`
- `http://localhost:44325/personal`
- `http://localhost:44325/privacy`
- `http://localhost:44325/tou`

## <a name="review-the-source-code"></a>Revise o código-fonte

### <a name="startupcs"></a>Startup.cs

Este projeto foi criado a partir de um modelo vazio de ASP.NET Core 2.2 Web Application com a caixa de seleção **Advanced - Configure for HTTPS** selecionada na configuração. Os serviços de MVC são registrados pelo método da estrutura de injeção de `ConfigureServices()` dependência. Além disso, o modelo vazio não permite servir conteúdo estático por padrão, de modo que o middleware de arquivos estáticos é adicionado ao `Configure()` método:

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

### <a name="wwwroot-folder"></a>wwwroot pasta

Em ASP.NET Core, a pasta raiz da Web é onde o aplicativo procura arquivos estáticos.

### <a name="indexcshtml"></a>Index.cshtml

ASP.NET Core trata arquivos chamados *Índice* como a página padrão/inicial para o site. Quando a URL do seu navegador aponta para a raiz do site, **o Index.cshtml** será exibido como a página inicial do seu aplicativo.

### <a name="appmanifest-folder"></a>Pasta AppManifest

Esta pasta contém os seguintes arquivos de pacote de aplicativos necessários:

- Um **ícone de cores completo** medindo 192 x 192 pixels.
- Um **ícone de contorno transparente** medindo 32 x 32 pixels.
- Um **manifest.jsno** arquivo que especifica os atributos do seu aplicativo.

Esses arquivos precisam ser fechados em um pacote de aplicativo para uso no upload de sua guia para Teams. Microsoft Teams carregará o `contentUrl` especificado em seu manifesto, incorporará-no em um <iframe \> e renderizará-no em sua guia.

### <a name="csproj"></a>.csproj

Na janela Visual Studio Solution Explorer, clique com o botão direito do mouse no projeto e selecione **Editar arquivo Project**. Na parte inferior do arquivo você verá o código que cria e atualiza sua pasta zip quando o aplicativo é construído:

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

- A Ngrok ouvirá os pedidos da internet e os encaminhará para o seu aplicativo quando estiver sendo executado na porta 44325.  Ele deve se assemelhar `https://y8rPrT2b.ngrok.io/` onde *y8rPrT2b* é substituído por sua URL HTTPS alfa-numérica ngrok.

- Certifique-se de manter o prompt de comando com ngrok em execução e para anotar a URL — você precisará dele mais tarde.

- Verifique se **o ngrok** está executando e funcionando corretamente abrindo seu navegador e indo para sua página de conteúdo através da URL ngrok HTTPS que foi fornecida na janela do prompt de comando.

>[!TIP]
>Você precisa ter sua aplicação em Visual Studio e ngrok correndo para completar este quickstart. Se você precisar parar de executar seu aplicativo em Visual Studio para trabalhar nele, **mantenha ngrok funcionando**. Ele continuará ouvindo e retomará o encaminhamento da solicitação do seu aplicativo quando ele for reiniciado em Visual Studio. Se você tiver que reiniciar o serviço ngrok, ele retornará uma nova URL e você terá que atualizar todos os lugares que usarem essa URL.

### <a name="run-your-application"></a>Execute sua aplicação

- Em Visual Studio **pressione F5** ou escolha Iniciar a **depuração** no menu **Depuração** do seu aplicativo.

[!INCLUDE [dotnet-personal-use-appstudio](~/includes/tabs/dotnet-personal-use-appstudio.md)]

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Crie uma guia pessoal personalizada com o ASP.NETCore MVC](~/tabs/quickstarts/create-personal-tab-dotnet-core-mvc.md)
