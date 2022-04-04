---
title: Criar um canal ou uma guia de grupo
author: laujan
description: Um guia de início rápido para criar uma guia de canal e grupo com o Gerador Yeoman para Microsoft Teams, incluindo a revisão do código-fonte com exemplos de código.
ms.localizationpriority: medium
ms.topic: quickstart
ms.author: lajanuar
zone_pivot_groups: teams-app-environment
ms.openlocfilehash: 31da2a8ee267ef42e6c0abd4e3bd695cf69d2f01
ms.sourcegitcommit: 3d6aa10d2f58a63c6a4281a30e8771469dba0d0b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64636135"
---
# <a name="channel-or-group-tab"></a>Guia Canal ou grupo

Canal ou guias de grupo forneça conteúdo para canais e chats em grupo e é uma ótima maneira de criar espaços colaborativos em torno de conteúdo dedicado baseado na web.

::: zone pivot="node-java-script"

## <a name="create-a-custom-channel-or-group-tab-with-nodejs"></a>Criar um canal personalizado ou uma guia de grupo com Node.js

1. No prompt de comando, instale os pacotes [Yeoman](https://yeoman.io/) e [gulp-cli](https://www.npmjs.com/package/gulp-cli) inserindo o seguinte comando após a instalação do **Node.js**:

    ```cmd
    npm install yo gulp-cli --global
    ```

2. No prompt de comando, instale o Microsoft Teams App inserindo o seguinte comando:

    ```cmd
    npm install generator-teams --global
    ```

A seguir estão as etapas para criar um canal ou uma guia de grupo:

* [Gerar seu aplicativo com uma guia canal ou grupo](#generate-your-application-with-a-channel-or-group-tab)
* [Criar um pacote do aplicativo](#create-your-app-package)
* [Criar e executar seu aplicativo](#build-and-run-your-application)
* [Estabelecer um túnel seguro para sua guia](#establish-a-secure-tunnel-to-your-tab)
* [Upload seu aplicativo para Teams](#upload-your-application-to-teams)

### <a name="generate-your-application-with-a-channel-or-group-tab"></a>Gerar seu aplicativo com uma guia canal ou grupo

1. No prompt de comando, crie um novo diretório para seu canal ou guia de grupo.

1. Insira o seguinte comando em seu novo diretório para iniciar o gerador Microsoft Teams App:

    ```cmd
    yo teams
    ```

1. Forneça seus valores a uma série de perguntas Microsoft Teams gerador de aplicativos para atualizar seu **arquivo manifest.json**:

    ![captura de tela de abertura do gerador](/microsoftteams/platform/assets/images/tab-images/teamsTabScreenshot.PNG)

    <details>
    <summary><b>Série de perguntas para atualizar seu arquivo manifest.json</b></summary>

    * **Qual é o nome da solução?**

        O nome da solução é o nome do projeto. Você pode aceitar o nome sugerido selecionando **Enter**.

    * **Onde você deseja colocar os arquivos?**

        No momento, você está no diretório do projeto. Selecione **Enter**.

    * **Título do seu projeto Microsoft Teams aplicativo?**

        O título é o nome do pacote do aplicativo e é usado no manifesto e na descrição do aplicativo. Insira um título ou selecione **Enter** para aceitar o nome padrão.

    * **Seu nome (empresa) ? (máx. 32 caracteres)**

        O nome da empresa será usado no manifesto do aplicativo. Insira um nome da empresa ou selecione **Enter** para aceitar o nome padrão.

    * **Qual versão de manifesto você gostaria de usar?**

        Selecione o esquema padrão.

    * **Scaffolding rápido? (Y/n)**

        O padrão é sim; insira **n** para inserir sua ID do Microsoft Partner.

    * **Insira sua ID do Microsoft Partner, se você tiver uma? (Deixe em branco para ignorar)**

        Esse campo não é obrigatório e deve ser usado somente se você já faz parte da [Rede do Microsoft Partner](https://partner.microsoft.com).

    * **O que você deseja adicionar ao seu projeto?**

        Selecione **( &ast; ) Uma guia**.

    * **A URL onde você hospedará essa solução?**

        Por padrão, o gerador sugere uma URL de Sites do Azure. Você só está testando seu aplicativo localmente, portanto, uma URL válida não é necessária.

    * **Você gostaria de mostrar um indicador de carregamento quando seu aplicativo/guia é carregado?**

        Escolha **não incluir** um indicador de carregamento quando seu aplicativo ou guia for carregado. O padrão é não, digite **n**.

    * **Você gostaria que aplicativos pessoais fossem renderizados sem uma barra de texto de tabulação?**

        Escolha **não** incluir aplicativos pessoais a serem renderizados sem uma barra de header-bar de tabulação. O padrão é não, digite **n**.

    * **Você gostaria de incluir a estrutura de teste e testes iniciais? (y/N)**

        Escolha **não** incluir uma estrutura de teste para este projeto. O padrão é não, digite **n**.

    * **Você gostaria de incluir suporte ao ESLint? (y/N)**

        Escolha não incluir suporte ao ESLint. O padrão é não, digite **n**.

    * **Você gostaria de usar aplicativos do Azure Insights para telemetria? (y/N)**

        Escolha **não** incluir [Aplicativo Azure Insights](/azure/azure-monitor/app/app-insights-overview). O padrão é não; enter **n**.

    * **Nome da guia padrão (máx. 16 caracteres)?**

        Nomeia sua guia. Esse nome de guia é usado em todo o seu projeto como um componente de caminho de arquivo ou URL.

    * **Que tipo de Guia você gostaria de criar?**

        Use as teclas de seta para selecionar **a guia Configurável** .

    * **Quais escopos você pretende usar para sua Guia?**

        Você pode selecionar uma equipe ou um chat em grupo.

    * **Você precisa de Microsoft Azure Active Directory (Azure AD) suporte a um único sign-on para a guia?**

        Escolha **não** incluir o Microsoft Azure Active Directory (Azure AD) suporte a Single-On para a guia. O padrão é sim, digite **n**.

    * **Deseja que essa guia seja disponibilizada no SharePoint Online? (Y/n)**

        Insira **n**.

    </details>

> [!IMPORTANT]
> O componente de **caminho yourDefaultTabNameTab** é o valor que você inscrevia no gerador para Nome da Guia **Padrão** mais a **palavra Tab**.
>
> Por exemplo: DefaultTabName é **MyTab** e **/MyTabTab/**

### <a name="create-your-app-package"></a>Criar um pacote do aplicativo

Você deve ter um pacote de aplicativos para criar e executar seu aplicativo Teams. O pacote do aplicativo é criado por meio de uma tarefa gulp que valida o **arquivo manifest.json** e gera a pasta zip no **diretório ./package** . No prompt de comando, insira o seguinte comando:

```cmd
gulp manifest
```

### <a name="build-and-run-your-application"></a>Criar e executar seu aplicativo

#### <a name="build-your-application"></a>Criar seu aplicativo

Insira o seguinte comando no prompt de comando para transpile sua solução na **pasta ./dist** :

```cmd
gulp build
```

#### <a name="run-your-application"></a>Executar seu aplicativo

1. No prompt de comando, insira o seguinte comando para iniciar um servidor Web local:

    ```bash
    gulp serve
    ```

1. Insira `http://localhost:3007/<yourDefaultAppNameTab>/` no navegador para exibir a home page do aplicativo.

    :::image type="content" source="~/assets/images/tab-images/homePage.png" alt-text="Guia Padrão" border="true":::

1. Para exibir sua página de configuração de tabulação, vá para `http://localhost:3007/<yourDefaultAppNameTab>/config.html`. O seguinte é mostrado:

    :::image type="content" source="~/assets/images/tab-images/configurationPage.png" alt-text="Página de configuração de tabulação" border="true":::

### <a name="establish-a-secure-tunnel-to-your-tab"></a>Estabelecer um túnel seguro para sua guia

Para estabelecer um túnel seguro em sua guia, saia do localhost e insira o seguinte comando:

```cmd
gulp ngrok-serve
```

> [!IMPORTANT]
> Depois que sua guia é carregada para Microsoft Teams por **meio do ngrok** e salva com êxito, você pode exibi-la no Teams até que sua sessão de túnel termine. Se você reiniciar sua sessão de ngrok, deverá atualizar seu aplicativo com a nova URL.

### <a name="upload-your-application-to-teams"></a>Upload seu aplicativo para Teams

1. Vá para Microsoft Teams e selecione **Store**&nbsp; :::image type="content" source="~/assets/images/tab-images/store.png" alt-text="Teams Store":::.
1. Selecione **Gerenciar seus aplicativos**.
1. Selecione **Publicar um aplicativo** e **Upload um aplicativo personalizado**.

    :::image type="content" source="~/assets/images/tab-images/publish-app.png" alt-text="Upload aplicativo personalizado" border="true":::

1. Vá para o diretório do projeto, navegue até a pasta **./package** , selecione a pasta zip do pacote do aplicativo e escolha **Abrir**.
    
    :::image type="content" source="~/assets/images/tab-images/channeltabadded.png" alt-text="Guia Canal Carregado" border="true":::

1. Selecione **Adicionar** na caixa de diálogo. Sua guia é carregada para Teams.
    
    > [!NOTE]
    > Se  **Add** não for exibido na caixa de diálogo, remova o código a seguir do manifesto da pasta zip do pacote do aplicativo carregado. Feche novamente a pasta e carregue-a Teams.
    >
    >```Json
    >"staticTabs": [],
    >"bots": [],
    >"connectors": [],
    >"composeExtensions": [],
    >```

1. Siga as instruções para adicionar uma guia. Há uma caixa de diálogo de configuração personalizada para seu canal ou guia de grupo.
1. Selecione **Salvar** e sua guia é adicionada à barra de guias do canal.

    :::image type="content" source="~/assets/images/tab-images/channeltabuploaded.png" alt-text="Guia canal carregado" border="true":::
    
    Agora você criou e adicionou seu canal ou guia de grupo com sucesso Teams.

::: zone-end

::: zone pivot="razor-csharp"

## <a name="create-a-custom-channel-or-group-tab-with-aspnet-core"></a>Criar um canal personalizado ou uma guia de grupo com ASP.NET Core

1. No prompt de comando, crie um novo diretório para seu projeto de guia.

1. Clone o repositório de exemplo em seu novo diretório usando o seguinte comando ou você pode [baixar o](https://github.com/OfficeDev/Microsoft-Teams-Samples) código-fonte e extrair os arquivos:

    ```cmd
    git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
    ```

A seguir estão as etapas para criar um canal ou uma guia de grupo:

* [Gerar seu aplicativo com uma guia canal ou grupo](#generate-your-application-with-a-channel-or-group-tab-1)
* [Estabelecer um túnel seguro para sua guia](#establish-a-secure-tunnel-to-your-tab-1)
* [Atualizar seu aplicativo](#update-your-application)
* [Criar e executar seu aplicativo](#build-and-run-your-application-1)
* [Atualizar seu pacote de aplicativos com o Portal do Desenvolvedor](#update-your-app-package-with-developer-portal)
* [Visualizar seu aplicativo em Teams](#preview-your-app-in-teams)

### <a name="generate-your-application-with-a-channel-or-group-tab"></a>Gerar seu aplicativo com uma guia canal ou grupo

1. Abra Visual Studio e selecione **Abrir um projeto ou solução**.

1. Vá para **a pasta Microsoft-Teams-Samplessamplestab-channel-grouprazor-csharp** >  >  >  e abra **channelGroupTab.sln**.

1. Em Visual Studio, selecione **F5** ou escolha **Iniciar Depuração** no menu **Depuração** do aplicativo para verificar se o aplicativo foi carregado corretamente. Em um navegador, vá para as seguintes URLs:

    * https://localhost:3978/
    * https://localhost:3978/privacy
    * https://localhost:3978/tou

<details>
<summary><b>Revisar o código-fonte</b></summary>

#### <a name="startupcs"></a>Startup.cs

Esse projeto foi criado a partir de um modelo vazio do aplicativo Web 3.1 ASP.NET Core 3.1 com a caixa de seleção **Avançado * Configurar para HTTPS** selecionado na instalação. Os serviços MVC são registrados pelo método da estrutura de injeção de `ConfigureServices()` dependência. Além disso, o modelo vazio não habilita o serviço de conteúdo estático por padrão, portanto, o middleware `Configure()` de arquivos estáticos é adicionado ao método usando o seguinte código:

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

#### <a name="wwwroot-folder"></a>pasta wwwroot

Em ASP.NET Core, a pasta raiz da Web é onde o aplicativo procura arquivos estáticos.

#### <a name="indexcshtml"></a>Index.cshtml

ASP.NET Core trata arquivos chamados **Index** como o padrão ou home page do site. Quando a URL do navegador aponta para a raiz do site, **Index.cshtml** é exibida como a home page do aplicativo.

#### <a name="tabcs"></a>Tab.cs

Esse C# contém um método chamado de **Tab.cshtml** durante a configuração.

#### <a name="appmanifest-folder"></a>Pasta AppManifest

Esta pasta contém os seguintes arquivos de pacote de aplicativos necessários:

* Um **ícone de cor completo** medindo 192 x 192 pixels.
* Um **ícone de contorno transparente** medindo 32 x 32 pixels.
* Um **arquivo manifest.json** que especifica os atributos do seu aplicativo.

Esses arquivos precisam ser cortados em um pacote de aplicativos para uso ao carregar sua guia para Teams. Quando um usuário opta por adicionar ou atualizar sua guia, `configurationUrl` Microsoft Teams carrega o especificado em seu manifesto, incorpora-o em um IFrame e o renderiza em sua guia.

#### <a name="csproj"></a>.csproj

Na janela Visual Studio Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione **Editar Project Arquivo**. No final do arquivo, você vê o seguinte código que cria e atualiza sua pasta zip quando o aplicativo é construído:

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

</details>

### <a name="establish-a-secure-tunnel-to-your-tab"></a>Estabelecer um túnel seguro para sua guia

No prompt de comando na raiz do diretório do projeto, execute o seguinte comando para estabelecer um túnel seguro para sua guia:

```cmd
ngrok http 3978 --host-header=localhost
```

Certifique-se de manter o prompt de comando com o ngrok em execução e anote a URL.

### <a name="update-your-application"></a>Atualizar seu aplicativo

1. Abra Visual Studio Gerenciador de Soluções e vá para a pasta **PagesShared**  >  e abra **_Layout.cshtml** e adicione o seguinte ao <head> seção tags:

    ```html
    <script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
    <script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>
    ```
    
    > [!IMPORTANT]
    > Não copie e colará as `<script src="...">` URLs desta página, pois elas não representam a versão mais recente. Para obter a versão mais recente do SDK, sempre vá [para Microsoft Teams API JavaScript](https://www.npmjs.com/package/@microsoft/teams-js).
    
1. Insira uma chamada na `microsoftTeams.initialize();` `script` marca.

1. Em Visual Studio Gerenciador de Soluções vá para a pasta **Páginas** e abra **Tab.cshtml**

    Em **Tab.cshtml** , o aplicativo apresenta ao usuário dois botões de opção para exibir a guia com um ícone vermelho ou cinza. Escolher os **gatilhos**  `saveGray()` `saveRed()`do botão Selecionar Cinza ou Selecionar Vermelho ou , respectivamente, define `settings.setValidityState(true)`e habilita o botão **Salvar** na página de configuração. Esse código permite Teams que você concluiu os requisitos de configuração e que a instalação pode continuar. Os parâmetros de são `settings.setSettings` definidos. Por fim, `saveEvent.notifySuccess()` é chamado para indicar que a URL de conteúdo foi resolvida com êxito.

1. Atualize os `websiteUrl` valores `contentUrl` e em cada função com a URL de ngrok HTTPS para sua guia.

    Seu código agora deve incluir o seguinte **com y8rCgT2b** substituído pela URL do ngrok:

    ```javascript
        
        let saveGray = () => {
            microsoftTeams.settings.registerOnSaveHandler(function (saveEvent) {
                microsoftTeams.settings.setSettings({
                    websiteUrl: `https://y8rCgT2b.ngrok.io`,
                    contentUrl: `https://y8rCgT2b.ngrok.io/gray/`,
                    entityId: "grayIconTab",
                    suggestedDisplayName: "MyNewTab"
                });
                saveEvent.notifySuccess();
            });
        }

        let saveRed = () => {
            microsoftTeams.settings.registerOnSaveHandler(function (saveEvent) {
                microsoftTeams.settings.setSettings({
                    websiteUrl: `https://y8rCgT2b.ngrok.io`,
                    contentUrl: `https://y8rCgT2b.ngrok.io/red/`,
                    entityId: "redIconTab",
                    suggestedDisplayName: "MyNewTab"
                });
                saveEvent.notifySuccess();
        });
        }
    ```

1. Salve o **Tab.cshtml atualizado**.

### <a name="build-and-run-your-application"></a>Criar e executar seu aplicativo

1. Em Visual Studio, selecione **F5** ou escolha **Iniciar Depuração** no menu **Depurar**.

1. Verifique se **o ngrok** está sendo executado e funcionando corretamente abrindo seu navegador e indo para sua página de conteúdo por meio da URL HTTPS ngrok fornecida na janela do prompt de comando.

    > [!TIP]
    > Você precisa ter seu aplicativo em Visual Studio e ngrok em execução para concluir as etapas fornecidas neste artigo. Se você precisar parar de executar seu aplicativo Visual Studio para trabalhar nele, **mantenha o ngrok em execução**. Ele escuta e retoma o roteamento da solicitação do aplicativo quando ele é reiniciado no Visual Studio. Se você tiver que reiniciar o serviço ngrok, ele retornará uma nova URL e será preciso atualizar seu aplicativo com a nova URL.

### <a name="update-your-app-package-with-developer-portal"></a>Atualizar seu pacote de aplicativos com o Portal do Desenvolvedor

1. Vá para Microsoft Teams. Se você usar a [versão baseada na Web](https://teams.microsoft.com), poderá inspecionar seu código front-end usando as ferramentas de desenvolvedor [do navegador](~/tabs/how-to/developer-tools.md).

1. Vá para [**Portal do Desenvolvedor**](https://dev.teams.microsoft.com/home).

1. Abra **Aplicativos** e selecione **Importar aplicativo**.

1. O nome do pacote do aplicativo é **tab.zip**. Ele está disponível no seguinte caminho:

    ```bash
    /bin/Debug/netcoreapp3.1/tab.zip
    ```

1. Selecione **tab.zip** e abra-o no Portal do Desenvolvedor.

1. Uma **ID de aplicativo padrão** é criada e preenchida na **seção Informações básicas** .

1. Adicione a descrição Short e Long para seu aplicativo em **Descrições**.

1. Em **Informações do Desenvolvedor**, adicione os detalhes necessários e, no Site (deve ser uma **URL HTTPS válida),** dê sua URL HTTPS ngrok.

1. Em **URLs de aplicativos**, atualize a política de Privacidade para `https://<yourngrokurl>/privacy` e Os Termos de uso para `https://<yourngrokurl>/tou` e salvar.

1. Em **Recursos do aplicativo**, selecione Grupo e aplicativo de canal. Atualize a **URL de Configuração** com `https://<yourngrokurl>/tab` e selecione a guia **Escopo**.

1. Selecione **Salvar**.

1. Na seção Domínios, domínios de suas guias devem conter sua URL ngrok sem o prefixo `<yourngrokurl>.ngrok.io`HTTPS .

### <a name="preview-your-app-in-teams"></a>Visualizar seu aplicativo em Teams

1. Selecione **Visualizar no Teams** na barra de ferramentas portal do desenvolvedor, o Portal do Desenvolvedor informa que seu aplicativo é sideloaded com êxito. A **página Adicionar** é exibida para seu aplicativo Teams.

1. Selecione **Adicionar à equipe** para Configurar a guia em uma equipe. Configure sua guia e selecione **Salvar**. Sua guia agora está disponível no Teams.

    :::image type="content" source="~/assets/images/tab-images/channeltabaspnetuploaded.png" alt-text="Guia canal CARREGADO ASPNET" border="true":::
    
    Agora você criou e adicionou seu canal ou guia de grupo com sucesso Teams.

::: zone-end

::: zone pivot="mvc-csharp"

## <a name="create-a-custom-channel-or-group-tab-with-aspnet-core-mvc"></a>Criar um canal personalizado ou uma guia de grupo com ASP.NET Core MVC

1. No prompt de comando, crie um novo diretório para seu projeto de guia.

1. Clone o repositório de exemplo em seu novo diretório usando o seguinte comando ou você pode [baixar o](https://github.com/OfficeDev/Microsoft-Teams-Samples) código-fonte e extrair os arquivos:

    ```cmd
    git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
    ```

A seguir estão as etapas para criar um canal ou uma guia de grupo:

* [Gerar seu aplicativo com uma guia canal ou grupo](#generate-your-application-with-a-channel-or-group-tab-2)
* [Estabelecer um túnel seguro para sua guia](#establish-a-secure-tunnel-to-your-tab-2)
* [Atualizar seu aplicativo](#update-your-application-1)
* [Criar e executar seu aplicativo](#build-and-run-your-application-2)
* [Atualizar seu pacote de aplicativos com o Portal do Desenvolvedor](#update-your-app-package-with-developer-portal-1)
* [Visualizar seu aplicativo em Teams](#preview-your-app-in-teams-1)

### <a name="generate-your-application-with-a-channel-or-group-tab"></a>Gerar seu aplicativo com uma guia canal ou grupo

1. Abra Visual Studio e selecione **Abrir um projeto ou solução**.

1. Vá para **a pasta Microsoft-Teams-Samplessamplestab-channel-groupmvc-csharp** >  >  >  e abra **ChannelGroupTabMVC.sln**.

1. Em Visual Studio, selecione **F5** ou escolha **Iniciar Depuração** no menu **Depuração** do aplicativo para verificar se o aplicativo foi carregado corretamente. Em um navegador, vá para as seguintes URLs:

    * https://localhost:3978/
    * https://localhost:3978/privacy
    * https://localhost:3978/tou

<details>
<summary><b>Revisar o código-fonte</b></summary>

#### <a name="startupcs"></a>Startup.cs

Esse projeto foi criado a partir de um modelo vazio do aplicativo Web 3.1 do ASP.NET Core 3.1 com a caixa de seleção **Avançado - Configurar para HTTPS** selecionada na instalação. Os serviços MVC são registrados pelo método da estrutura de injeção de `ConfigureServices()` dependência. Além disso, o modelo vazio não habilita o serviço de conteúdo estático por padrão, portanto, o middleware `Configure()` de arquivos estáticos é adicionado ao método usando o seguinte código:

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

#### <a name="wwwroot-folder"></a>pasta wwwroot

Em ASP.NET Core, a pasta raiz da Web é onde o aplicativo procura arquivos estáticos.

#### <a name="appmanifest-folder"></a>Pasta AppManifest

Esta pasta contém os seguintes arquivos de pacote de aplicativos necessários:

* Um **ícone de cor completo** medindo 192 x 192 pixels.
* Um **ícone de contorno transparente** medindo 32 x 32 pixels.
* Um **arquivo manifest.json** que especifica os atributos do seu aplicativo.

Esses arquivos precisam ser cortados em um pacote de aplicativos para uso ao carregar sua guia para Teams.

#### <a name="csproj"></a>.csproj

Na janela Visual Studio Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione **Editar Project Arquivo**. No final do arquivo, você vê o seguinte código que cria e atualiza sua pasta zip quando o aplicativo é construído:

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

#### <a name="models"></a>Modelos

**ChannelGroup.cs** apresenta um objeto Message e métodos que serão chamados dos controladores durante a configuração.

#### <a name="views"></a>Visualizações

Estas são as diferentes exibições em ASP.NET Core MVC:

* Home: ASP.NET Core trata arquivos chamados **Index** como o padrão ou home page do site. Quando a URL do navegador aponta para a raiz do site, **Index.cshtml** será exibida como a home page do aplicativo.

* Compartilhado: a marcação de exibição **parcial _Layout.cshtml** contém a estrutura geral da página do aplicativo e elementos visuais compartilhados. Ele também fará referência à biblioteca Teams.

#### <a name="controllers"></a>Controladores

Os controladores usam a propriedade `ViewBag` para transferir valores dinamicamente para os exibições.

</details>

### <a name="establish-a-secure-tunnel-to-your-tab"></a>Estabelecer um túnel seguro para sua guia

No prompt de comando na raiz do diretório do projeto, execute o seguinte comando para estabelecer um túnel seguro para sua guia:

```cmd
ngrok http 3978 --host-header=localhost
```

Certifique-se de manter o prompt de comando com o ngrok em execução e anote a URL.

### <a name="update-your-application"></a>Atualizar seu aplicativo

1. Abra Visual Studio Gerenciador de Soluções e vá para a pasta **ViewsShared**  >  e abra **_Layout.cshtml** e adicione o seguinte ao <head> seção tags:

    ```html
    <script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
    <script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>
    ```
    
    > [!IMPORTANT]
    > Não copie e colará as `<script src="...">` URLs desta página, pois elas não representam a versão mais recente. Para obter a versão mais recente do SDK, sempre vá [para Microsoft Teams API JavaScript](https://www.npmjs.com/package/@microsoft/teams-js).
    
1. Insira uma chamada na `microsoftTeams.initialize();` `script` marca.

1. Em Visual Studio Gerenciador de Soluções vá para a pasta **Tab** e abra **Tab.cshtml**

    Em **Tab.cshtml** , o aplicativo apresenta ao usuário dois botões de opção para exibir a guia com um ícone vermelho ou cinza. Escolher os **gatilhos**  `saveGray()` `saveRed()`do botão Selecionar Cinza ou Selecionar Vermelho ou , respectivamente, define `settings.setValidityState(true)`e habilita o botão **Salvar** na página de configuração. Esse código permite Teams que você concluiu os requisitos de configuração e que a instalação pode continuar. Os parâmetros de são `settings.setSettings` definidos. Por fim, `saveEvent.notifySuccess()` é chamado para indicar que a URL de conteúdo foi resolvida com êxito. 

1. Atualize os `websiteUrl` valores `contentUrl` e em cada função com a URL de ngrok HTTPS para sua guia.

    Seu código agora deve incluir o seguinte **com y8rCgT2b** substituído pela URL do ngrok:

    ```javascript

        let saveGray = () => {
            microsoftTeams.settings.registerOnSaveHandler(function (saveEvent) {
                microsoftTeams.settings.setSettings({
                    websiteUrl: `https://y8rCgT2b.ngrok.io`,
                    contentUrl: `https://y8rCgT2b.ngrok.io/gray/`,
                    entityId: "grayIconTab",
                    suggestedDisplayName: "MyNewTab"
                });
                saveEvent.notifySuccess();
            });
        }
    
        let saveRed = () => {
            microsoftTeams.settings.registerOnSaveHandler(function (saveEvent) {
                microsoftTeams.settings.setSettings({
                    websiteUrl: `https://y8rCgT2b.ngrok.io`,
                    contentUrl: `https://y8rCgT2b.ngrok.io/red/`,
                    entityId: "redIconTab",
                    suggestedDisplayName: "MyNewTab"
                });
                saveEvent.notifySuccess();
            });
        }
    ```

1. Certifique-se de salvar **o Tab.cshtml atualizado**.

### <a name="build-and-run-your-application"></a>Criar e executar seu aplicativo

1. Em Visual Studio, selecione **F5** ou escolha **Iniciar Depuração** no menu **Depurar**.

1. Verifique se **o ngrok** está sendo executado e funcionando corretamente abrindo seu navegador e indo para sua página de conteúdo por meio da URL HTTPS ngrok fornecida na janela do prompt de comando.

    > [!TIP]
    > Você precisa ter seu aplicativo em Visual Studio e ngrok em execução para concluir as etapas fornecidas neste artigo. Se você precisar parar de executar seu aplicativo Visual Studio para trabalhar nele, **mantenha o ngrok em execução**. Ele escuta e retoma o roteamento da solicitação do aplicativo quando ele é reiniciado no Visual Studio. Se você tiver que reiniciar o serviço ngrok, ele retornará uma nova URL e será preciso atualizar seu aplicativo com a nova URL.

### <a name="update-your-app-package-with-developer-portal"></a>Atualizar seu pacote de aplicativos com o Portal do Desenvolvedor

1. Vá para Microsoft Teams. Se você usar a [versão baseada na Web](https://teams.microsoft.com), poderá inspecionar seu código front-end usando as ferramentas de desenvolvedor [do navegador](~/tabs/how-to/developer-tools.md).

1. Vá para [**Portal do Desenvolvedor**](https://dev.teams.microsoft.com/home).

1. Abra **Aplicativos** e selecione **Importar aplicativo**.

1. O nome do pacote do aplicativo é **tab.zip**. Ele está disponível no seguinte caminho:

    ```bash
    /bin/Debug/netcoreapp3.1/tab.zip
    ```

1. Selecione **tab.zip** e abra-o no Portal do Desenvolvedor.

1. Uma **ID de aplicativo padrão** é criada e preenchida na **seção Informações básicas** .

1. Adicione a descrição Short e Long para seu aplicativo em **Descrições**.

1. Em **Informações do Desenvolvedor**, adicione os detalhes necessários e, no Site (deve ser uma **URL HTTPS válida),** dê sua URL HTTPS ngrok.

1. Em **URLs de aplicativos**, atualize a política de Privacidade para `https://<yourngrokurl>/privacy` e Os Termos de uso para `https://<yourngrokurl>/tou` e salvar.

1. Em **Recursos do aplicativo**, selecione Grupo e aplicativo de canal. Atualize a **URL de Configuração** com `https://<yourngrokurl>/tab` e selecione a guia **Escopo**.

1. Selecione **Salvar**.

1. Na seção Domínios, domínios de suas guias devem conter sua URL ngrok sem o prefixo `<yourngrokurl>.ngrok.io`HTTPS .

### <a name="preview-your-app-in-teams"></a>Visualizar seu aplicativo em Teams

1. Selecione **Visualizar no Teams** na barra de ferramentas portal do desenvolvedor, o Portal do Desenvolvedor informa que seu aplicativo é sideloaded com êxito. A **página Adicionar** é exibida para seu aplicativo Teams.

1. Selecione **Adicionar à equipe** para Configurar a guia em uma equipe. Configure sua guia e selecione **Salvar**. Sua guia agora está disponível no Teams.

    :::image type="content" source="~/assets/images/tab-images/channeltabaspnetuploaded.png" alt-text="Guia canal ASPNET MVC carregado" border="true":::
    
    Agora você criou e adicionou seu canal ou guia de grupo com sucesso Teams.

::: zone-end

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Criar uma página de conteúdo](~/tabs/how-to/create-tab-pages/content-page.md)

## <a name="see-also"></a>Confira também

* [Teams guias](~/tabs/what-are-tabs.md)
* [Criar uma guia pessoal](~/tabs/how-to/create-personal-tab.md)
* [Guias em dispositivos móveis](~/tabs/design/tabs-mobile.md)
* [Criar guias com Cartões Adaptáveis](~/tabs/how-to/build-adaptive-card-tabs.md)
* [Criar uma página de remoção](~/tabs/how-to/create-tab-pages/removal-page.md)
