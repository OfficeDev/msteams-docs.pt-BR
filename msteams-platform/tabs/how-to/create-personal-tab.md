---
title: Criar uma guia pessoal
author: laujan
description: Um guia de início rápido para criar uma guia pessoal com o Gerador Yeoman, ASP.NET Core ou ASP.NET Core MVC para Microsoft Teams usando Node.js e atualizando o manifesto do aplicativo.
ms.localizationpriority: medium
ms.topic: quickstart
ms.author: lajanuar
keywords: yeoman ASP.NET pacote MVC appmanifest conversation domain permission store
zone_pivot_groups: teams-app-environment
ms.openlocfilehash: d19ecc04aa14561d443a65d4ea896c210fdf4d94
ms.sourcegitcommit: 3d6aa10d2f58a63c6a4281a30e8771469dba0d0b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64636161"
---
# <a name="create-a-personal-tab"></a>Criar uma guia pessoal

Guias pessoais, junto com bots de conversação direta, fazem parte de aplicativos pessoais e têm como escopo um único usuário. Eles podem ser fixados no painel esquerdo para facilitar o acesso. Você também pode [reordenar e](#reorder-static-personal-tabs) adicionar [`registerOnFocused` API](#add-registeronfocused-api-for-tabs-or-personal-apps) para guias pessoais.

Verifique se você tem todos [os pré-requisitos para](~/tabs/how-to/tab-requirements.md) criar sua guia pessoal.

::: zone pivot="node-java-script"

## <a name="create-a-personal-tab-with-nodejs"></a>Criar uma guia pessoal com Node.js

1. No prompt de comando, instale os pacotes [Yeoman](https://yeoman.io/) e [gulp-cli](https://www.npmjs.com/package/gulp-cli) inserindo o seguinte comando após a instalação do Node.js:

    ```cmd
    npm install yo gulp-cli --global
    ```

1. No prompt de comando, instale o Microsoft Teams App inserindo o seguinte comando:

    ```cmd
    npm install generator-teams --global
    ```

A seguir estão as etapas para criar uma guia pessoal:

1. [Gerar seu aplicativo com uma guia pessoal](#generate-your-application-with-a-personal-tab)
1. [Adicionar uma página de conteúdo à guia pessoal](#add-a-content-page-to-the-personal-tab)
1. [Criar um pacote do aplicativo](#create-your-app-package)
1. [Criar e executar seu aplicativo](#build-and-run-your-application)
1. [Estabelecer um túnel seguro para sua guia pessoal](#establish-a-secure-tunnel-to-your-tab)
1. [Upload seu aplicativo para Teams](#upload-your-application-to-teams)

### <a name="generate-your-application-with-a-personal-tab"></a>Gerar seu aplicativo com uma guia pessoal

1. No prompt de comando, crie um novo diretório para sua guia pessoal.

1. Insira o seguinte comando em seu novo diretório para iniciar o gerador Microsoft Teams App:

    ```cmd
    yo teams
    ```

1. Forneça seus valores a uma série de perguntas solicitadas pelo Microsoft Teams App para atualizar seu **arquivo manifest.json**.

    :::image type="content" source="~/assets/images/tab-images/teamsTabScreenshot.PNG" alt-text="Teams gerador" border="true":::

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

      Use as teclas de seta para selecionar **Pessoal (estático)**.

    * **Você precisa de Microsoft Azure Active Directory (Azure AD) suporte a um único sign-on para a guia?**

      Escolha **não** incluir o suporte ao Azure AD Single-Sign-On para a guia. O padrão é sim, digite **n**.

    </details>

### <a name="add-a-content-page-to-the-personal-tab"></a>Adicionar uma página de conteúdo à guia pessoal

Crie uma página de conteúdo e atualize os arquivos existentes do aplicativo de guia pessoal:

1. Crie um novo **personal.html** em seu Visual Studio Code com a seguinte marcação:

    ```html
    <!DOCTYPE html>
    <html>
        <head>
            <meta charset="UTF-8">
            <title>
                <!-- Todo: add your a title here -->
            </title>
            <meta name="viewport" content="width=device-width, initial-scale=1.0">
            <!-- inject:css -->
            <!-- endinject -->
        </head>
            <body>
                <h1>Personal Tab</h1>
                <p><img src="/assets/icon.png"></p>
                <p>This is your personal tab!</p>
            </body>
    </html>
    ```

1. Salve **personal.html** na pasta **pública do aplicativo** no seguinte local:

    ```
    ./src/public/<yourDefaultTabNameTab>/personal.html
    ```

1. Abra **manifest.json** a partir do seguinte local em sua Visual Studio Code:

    ```
     ./src/manifest/manifest.json
    ```

1. Adicione o seguinte à matriz `staticTabs` vazia (`staticTabs":[]`) e adicione o seguinte objeto JSON:

    ```json
    {
        "entityId": "personalTab",
        "name": "Personal Tab ",
        "contentUrl": "https://{{PUBLIC_HOSTNAME}}/<yourDefaultTabNameTab>/personal.html",
        "websiteUrl": "https://{{PUBLIC_HOSTNAME}}",
        "scopes": ["personal"]
    }
    ```

    > [!IMPORTANT]
    > O componente de **caminho yourDefaultTabNameTab** é o valor que você inscrevia no gerador para Nome da Guia **Padrão** mais a **palavra Tab**.
    >
    > Por exemplo: DefaultTabName é **MyTab** e **/MyTabTab/**

1. Atualize **o componente de caminho contentURL** **yourDefaultTabNameTab** com o nome da guia real.

1. Salve o arquivo **manifest.json** atualizado.

1. Abra **Tab.ts** em seu Visual Studio Code do seguinte caminho para fornecer sua página de conteúdo em um IFrame:

    ```bash
    ./src/server/<yourDefaultTabNameTab>/<yourDefaultTabNameTab>.ts
    ```

1. Adicione o seguinte à lista de decoradores IFrame:

    ```typescript
     @PreventIframe("/<yourDefaultTabName Tab>/personal.html")
    ```

1. Salve o arquivo atualizado. Seu código de tabulação está completo.

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

    ```cmd
    gulp serve
    ```

1. Insira `http://localhost:3007/<yourDefaultAppNameTab>/` no navegador para exibir a home page do aplicativo.

    :::image type="content" source="~/assets/images/tab-images/homePage.png" alt-text="Guia Padrão" border="true":::

1. Navegue `http://localhost:3007/<yourDefaultAppNameTab>/personal.html`, para exibir sua guia pessoal.

    :::image type="content" source="~/assets/images/tab-images/personalTab.PNG" alt-text="Guia html padrão" border="true":::

### <a name="establish-a-secure-tunnel-to-your-tab"></a>Estabelecer um túnel seguro para sua guia

No prompt de comando, saia do localhost e insira o seguinte comando para estabelecer um túnel seguro em sua guia:

```cmd
gulp ngrok-serve
```

> [!IMPORTANT]
> Depois que sua guia é carregada para Microsoft Teams por **meio do ngrok** e salva com êxito, você pode exibi-la no Teams até que sua sessão de túnel termine.

### <a name="upload-your-application-to-teams"></a>Upload seu aplicativo para Teams

1. Vá para Microsoft Teams e selecione **Store**&nbsp; :::image type="content" source="~/assets/images/tab-images/store.png" alt-text="Teams Store":::.
1. Selecione **Gerenciar seus aplicativos**
1. Selecione **Publicar um aplicativo** e **Upload um aplicativo personalizado**.

    :::image type="content" source="~/assets/images/tab-images/publish-app.png" alt-text="Upload aplicativo personalizado" border="true":::

1. Vá para o diretório do projeto, navegue até a **pasta ./package** , selecione a pasta zip e escolha **Abrir**.

    :::image type="content" source="~/assets/images/tab-images/addingpersonaltab.png" alt-text="Adicionar sua guia pessoal" border="true":::

1. Selecione **Adicionar** na caixa de diálogo. Sua guia é carregada para Teams.

    :::image type="content" source="~/assets/images/tab-images/personaltabuploaded.png" alt-text="Guia pessoal carregado" border="true":::

1. No painel esquerdo do Teams, selecione &#x25CF;&#x25CF;&#x25CF; e escolha seu aplicativo carregado para exibir sua guia pessoal.

   Agora você criou e adicionou sua guia pessoal com sucesso Teams.
  
   Como você tem sua guia pessoal Teams, você também pode [reordenar](#reorder-static-personal-tabs) e adicionar [`registerOnFocused` API](#add-registeronfocused-api-for-tabs-or-personal-apps) para sua guia pessoal.

::: zone-end

::: zone pivot="razor-csharp"

## <a name="create-a-personal-tab-with-aspnet-core"></a>Criar uma guia pessoal com ASP.NET Core

1. No prompt de comando, crie um novo diretório para seu projeto de guia.

1. Clone o repositório de exemplo em seu novo diretório usando o seguinte comando ou você pode [baixar o](https://github.com/OfficeDev/Microsoft-Teams-Samples) código-fonte e extrair os arquivos:

    ```cmd
    git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
    ```

A seguir estão as etapas para criar uma guia pessoal:

1. [Gerar seu aplicativo com uma guia pessoal](#generate-your-application-with-a-personal-tab-1)
1. [Atualizar e executar seu aplicativo](#update-and-run-your-application)
1. [Estabelecer um túnel seguro para sua guia](#establish-a-secure-tunnel-to-your-tab-1)
1. [Atualizar seu pacote de aplicativos com o Portal do Desenvolvedor](#update-your-app-package-with-developer-portal)
1. [Visualizar seu aplicativo em Teams](#preview-your-app-in-teams)

### <a name="generate-your-application-with-a-personal-tab"></a>Gerar seu aplicativo com uma guia pessoal

1. Abra Visual Studio e selecione **Abrir um projeto ou solução**.

1. Vá para **a pasta Microsoft-Teams-Samplessamplestab-personalrazor-csharp** >  >  >  e abra **PersonalTab.sln**.

1. Em Visual Studio, selecione **F5** ou escolha **Iniciar Depuração** no menu **Depuração** do aplicativo para verificar se o aplicativo foi carregado corretamente. Em um navegador, vá para as seguintes URLs:

    * <http://localhost:3978/>
    * <http://localhost:3978/personalTab>
    * <http://localhost:3978/privacy>
    * <http://localhost:3978/tou>

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

#### <a name="indexcshtml"></a>Index.cshtml

ASP.NET Core trata arquivos chamados **Index** como o padrão ou home page do site. Quando a URL do navegador aponta para a raiz do site, **Index.cshtml** é exibida como a home page do aplicativo.

#### <a name="appmanifest-folder"></a>Pasta AppManifest

Esta pasta contém os seguintes arquivos de pacote de aplicativos necessários:

* Um **ícone de cor completo** medindo 192 x 192 pixels.
* Um **ícone de contorno transparente** medindo 32 x 32 pixels.
* Um **arquivo manifest.json** que especifica os atributos do seu aplicativo.

Esses arquivos devem ser zipped em um pacote de aplicativos para uso ao carregar sua guia para Teams. Microsoft Teams carrega `contentUrl` o especificado em seu manifesto, o incorpora em um <iframe\> e o renderiza em sua guia.

#### <a name="csproj"></a>.csproj

Em Visual Studio Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione **Editar Project Arquivo**. No final do arquivo, você pode ver o seguinte código que cria e atualiza sua pasta zip quando o aplicativo é construído:

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

### <a name="update-and-run-your-application"></a>Atualizar e executar seu aplicativo

1. Abra Visual Studio Gerenciador de Soluções e vá para a pasta **PagesShared**  >  e abra **_Layout.cshtml** e adicione o seguinte à seção `<head>` tags:

    ```HTML
    <script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
    <script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>
    ```

1. Em Visual Studio Gerenciador de Soluções **abra PersonalTab.cshtml** da pasta **Páginas** e adicione `microsoftTeams.initialize()` as `<script>` marcas e salve.

1. Em Visual Studio, selecione **F5** ou **escolha Iniciar Depuração** no menu **Depuração do** aplicativo.

### <a name="establish-a-secure-tunnel-to-your-tab"></a>Estabelecer um túnel seguro para sua guia

No prompt de comando na raiz do diretório do projeto, execute o seguinte comando para estabelecer um túnel seguro para sua guia:

```cmd
ngrok http 3978 --host-header=localhost
```

### <a name="update-your-app-package-with-developer-portal"></a>Atualizar seu pacote de aplicativos com o Portal do Desenvolvedor

1. Vá para [**Portal do Desenvolvedor**](https://dev.teams.microsoft.com/home).

1. Abra **Aplicativos** e selecione **Importar aplicativo**.

1. O nome do pacote do aplicativo é **tab.zip**. Ele está disponível no seguinte caminho:

    ```
    /bin/Debug/netcoreapp3.1/tab.zip
    ```

1. Selecione **tab.zip** e abra-o no Portal do Desenvolvedor.

1. Uma **ID de aplicativo padrão** é criada e preenchida na **seção Informações básicas** .

1. Adicione a descrição Short e Long para seu aplicativo em **Descrições**.

1. Em **Informações do Desenvolvedor**, adicione os detalhes necessários e, no Site (deve ser uma **URL HTTPS válida),** dê sua URL HTTPS ngrok.

1. Em **URLs de aplicativos**, atualize a política de Privacidade para `https://<yourngrokurl>/privacy` e Os Termos de uso para `https://<yourngrokurl>/tou` e salvar.

1. Em **Recursos do aplicativo**, selecione **Aplicativo** >  **PessoalCrie sua primeira guia de aplicativo pessoal** e insira o Nome e atualize a **URL de Conteúdo** com `https://<yourngrokurl>/personalTab`. Deixe o campo URL do site em branco e selecione **Contexto** como personalTab na lista lista suspenso e **Adicionar**.

1. Selecione **Salvar**.

1. Na seção Domínios, domínios de suas guias devem conter sua URL ngrok sem o prefixo `<yourngrokurl>.ngrok.io`HTTPS .

### <a name="preview-your-app-in-teams"></a>Visualizar seu aplicativo em Teams

1. Selecione **Visualizar no Teams** na barra de ferramentas portal do desenvolvedor, o Portal do Desenvolvedor informa que seu aplicativo é sideloaded com êxito. A **página Adicionar** é exibida para seu aplicativo Teams.

1. Selecione **Adicionar** para carregar a guia Teams. Sua guia agora está disponível no Teams.

    :::image type="content" source="~/assets/images/tab-images/personaltabaspnetuploaded.png" alt-text="Guia Padrão" border="true":::

   Agora você criou e adicionou sua guia pessoal com sucesso Teams.
  
   Como você tem sua guia pessoal Teams, você também pode [reordenar](#reorder-static-personal-tabs) e adicionar [`registerOnFocused` API](#add-registeronfocused-api-for-tabs-or-personal-apps) para sua guia pessoal.

::: zone-end

::: zone pivot="mvc-csharp"

## <a name="create-a-personal-tab-with-aspnet-core-mvc"></a>Criar uma guia pessoal com ASP.NET Core MVC

1. No prompt de comando, crie um novo diretório para seu projeto de guia.

1. Clone o repositório de exemplo em seu novo diretório usando o seguinte comando ou você pode [baixar o](https://github.com/OfficeDev/Microsoft-Teams-Samples) código-fonte e extrair os arquivos:

    ```cmd
    git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
    ```

A seguir estão as etapas para criar uma guia pessoal:

1. [Gerar seu aplicativo com uma guia pessoal](#generate-your-application-with-a-personal-tab-2)
1. [Atualizar e executar aplicativo](#update-and-run-your-application-1)
1. [Estabelecer um túnel seguro para sua guia](#establish-a-secure-tunnel-to-your-tab-2)
1. [Atualizar seu pacote de aplicativos com o Portal do Desenvolvedor](#update-your-app-package-with-developer-portal-1)
1. [Visualizar seu aplicativo em Teams](#preview-your-app-in-teams-1)

### <a name="generate-your-application-with-a-personal-tab"></a>Gerar seu aplicativo com uma guia pessoal

1. Abra Visual Studio e selecione **Abrir um projeto ou solução**.

1. Vá para **a pasta Microsoft-Teams-Samplessamplestab-personalmvc-csharp** >  >  >  e abra **PersonalTabMVC.sln** no Visual Studio.

1. Em Visual Studio, selecione **F5** ou escolha **Iniciar Depuração** no menu **Depuração** do aplicativo para verificar se o aplicativo foi carregado corretamente. Em um navegador, vá para as seguintes URLs:

    * <http://localhost:3978>
    * <http://localhost:3978/personalTab>
    * <http://localhost:3978/privacy>
    * <http://localhost:3978/tou>

<details>
<summary><b>Revisar o código-fonte</b></summary>

#### <a name="startupcs"></a>Startup.cs

Esse projeto foi criado a partir de um modelo vazio do aplicativo Web 3.1 do ASP.NET Core 3.1 com a caixa de seleção **Avançado - Configurar para HTTPS** selecionada na instalação. Os serviços MVC são registrados pelo método da estrutura de injeção de `ConfigureServices()` dependência. Além disso, o modelo vazio não habilita o serviço de conteúdo estático por padrão, portanto, o middleware `Configure()` de arquivos estáticos é adicionado ao método usando o seguinte código:

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

#### <a name="wwwroot-folder"></a>pasta wwwroot

Em ASP.NET Core, a pasta raiz da Web é onde o aplicativo procura arquivos estáticos.

#### <a name="appmanifest-folder"></a>Pasta AppManifest

Esta pasta contém os seguintes arquivos de pacote de aplicativos necessários:

* Um **ícone de cor completo** medindo 192 x 192 pixels.
* Um **ícone de contorno transparente** medindo 32 x 32 pixels.
* Um **arquivo manifest.json** que especifica os atributos do seu aplicativo.

Esses arquivos devem ser zipped em um pacote de aplicativos para uso ao carregar sua guia para Teams. Microsoft Teams carrega `contentUrl` o especificado em seu manifesto, o incorpora em um IFrame e o renderiza em sua guia.

#### <a name="csproj"></a>.csproj

Na Visual Studio Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione **Editar Project Arquivo**. No final do arquivo, você vê o seguinte código que cria e atualiza sua pasta zip quando o aplicativo é construído:

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

#### <a name="models"></a>Modelos

**PersonalTab.cs** apresenta um objeto de mensagem e métodos que são chamados de **PersonalTabController** quando um usuário seleciona um botão no Modo de Exibição **PersonalTab** .

#### <a name="views"></a>Visualizações

Essas exibições são as diferentes exibições ASP.NET Core MVC:

* Home: ASP.NET Core trata arquivos chamados **Index** como o padrão ou home page do site. Quando a URL do navegador aponta para a raiz do site, **Index.cshtml** é exibida como a home page do aplicativo.

* Compartilhado: a marcação de exibição **parcial _Layout.cshtml** contém a estrutura geral da página do aplicativo e elementos visuais compartilhados. Ele também faz referência à biblioteca Teams.

#### <a name="controllers"></a>Controladores

Os controladores usam a propriedade `ViewBag` para transferir valores dinamicamente para o Views.

</details>

### <a name="update-and-run-your-application"></a>Atualizar e executar seu aplicativo

1. Abra Visual Studio Gerenciador de Soluções e vá para a pasta **ViewsShared**  >  e abra **_Layout.cshtml** e adicione o seguinte à seção `<head>` tags:

    ```HTML
    <script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
    <script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>
    ```

1. Em Visual Studio Gerenciador de Soluções **abrir PersonalTab.cshtml** da pasta **ViewsPersonalTab**  >  e adicionar `microsoftTeams.initialize()` dentro das `<script>` marcas e salvar.

1. Em Visual Studio, selecione **F5** ou **escolha Iniciar Depuração** no menu **Depuração do** aplicativo.

### <a name="establish-a-secure-tunnel-to-your-tab"></a>Estabelecer um túnel seguro para sua guia

No prompt de comando na raiz do diretório do projeto, execute o seguinte comando para estabelecer um túnel seguro para sua guia:

```cmd
ngrok http 3978 --host-header=localhost
```

### <a name="update-your-app-package-with-developer-portal"></a>Atualizar seu pacote de aplicativos com o Portal do Desenvolvedor

1. Vá para [**Portal do Desenvolvedor**](https://dev.teams.microsoft.com/home).

1. Abra **Aplicativos** e selecione **Importar aplicativo**.

1. O nome do pacote do aplicativo é **tab.zip**. Ele está disponível no seguinte caminho:

    ```
    /bin/Debug/netcoreapp3.1/tab.zip
    ```

1. Selecione **tab.zip** e abra-o no Portal do Desenvolvedor.

1. Uma **ID de aplicativo padrão** é criada e preenchida na **seção Informações básicas** .

1. Adicione a descrição Short e Long para seu aplicativo em **Descrições**.

1. Em **Informações do Desenvolvedor**, adicione os detalhes necessários e, no Site (deve ser uma **URL HTTPS válida),** dê sua URL HTTPS ngrok.

1. Em **URLs de aplicativos**, atualize a política de Privacidade para `https://<yourngrokurl>/privacy` e Os Termos de uso para `https://<yourngrokurl>/tou` e salvar.

1. Em **Recursos do aplicativo**, selecione **Aplicativo** >  **PessoalCrie sua primeira guia de aplicativo pessoal** e insira o Nome e atualize a **URL de Conteúdo** com `https://<yourngrokurl>/personalTab`. Deixe o campo URL do site em branco e selecione **Contexto** como personalTab na lista lista suspenso e **Adicionar**.

1. Selecione **Salvar**.

1. Na seção Domínios, domínios de suas guias devem conter sua URL ngrok sem o prefixo `<yourngrokurl>.ngrok.io`HTTPS .

### <a name="preview-your-app-in-teams"></a>Visualizar seu aplicativo em Teams

1. Selecione **Visualizar no Teams** na barra de ferramentas portal do desenvolvedor, o Portal do Desenvolvedor informa que seu aplicativo é sideloaded com êxito. A **página Adicionar** é exibida para seu aplicativo Teams.

1. Selecione **Adicionar** para carregar a guia Teams. Sua guia agora está disponível no Teams.

    :::image type="content" source="~/assets/images/tab-images/personaltabaspnetmvccoreuploaded.png" alt-text="Guia pessoal" border="true":::
  
   Agora você criou e adicionou sua guia pessoal com sucesso Teams.

   Como você tem sua guia pessoal Teams, você também pode [reordenar](#reorder-static-personal-tabs) e adicionar [`registerOnFocused` API](#add-registeronfocused-api-for-tabs-or-personal-apps) para sua guia pessoal.

::: zone-end

## <a name="reorder-static-personal-tabs"></a>Reordenar guias pessoais estáticas

A partir da versão 1.7 do manifesto, os desenvolvedores podem reorganizar todas as guias em seu aplicativo pessoal. Em particular, um desenvolvedor pode mover a guia de **chat** bot, que sempre é padrão para a primeira posição, em qualquer lugar no header da guia do aplicativo pessoal. Duas palavras-chave de guia reservadas `entityId` são declaradas, **conversas** e **sobre**.

Se você criar um bot com **um escopo pessoal** , ele aparecerá na primeira posição da guia em um aplicativo pessoal por padrão. Se você quiser movê-lo para outra posição, adicione um objeto de guia estático ao manifesto com a palavra-chave reservada, **conversas**. A **guia** conversa é exibida na Web ou na área de trabalho, dependendo de onde você adicionar a guia **de** conversa na `staticTabs` matriz.

``` JSON

{
   "staticTabs":[
      {
         
      },
      {
         "entityId":"conversations",
         "scopes":[
            "personal"
         ]
      }
   ]
}

```

## <a name="add-registeronfocused-api-for-tabs-or-personal-apps"></a>Adicionar `registerOnFocused` API para guias ou aplicativos pessoais

A `registerOnFocused` API SDK permite que você use um teclado em Teams. Você pode retornar a um aplicativo pessoal e manter o foco em uma guia ou aplicativo pessoal com a ajuda das teclas Ctrl, Shift e F6. Por exemplo, você pode se afastar do aplicativo pessoal para pesquisar algo e, em seguida, retornar ao aplicativo pessoal ou usar Ctrl+F6 para dar a volta nos locais necessários.

O código a seguir fornece um exemplo de definição de manipulador no `registerFocusEnterHandler` SDK quando o foco deve ser retornado para a guia ou aplicativo pessoal:

``` C#

export function registerFocusEnterHandler(handler: (navigateForward: boolean) => void): 
void {
  HandlersPrivate.focusEnterHandler = handler;
  handler && sendMessageToParent('registerHandler', ['focusEnter']);
}
function handleFocusEnter(navigateForward: boolean): void
 {
  if (HandlersPrivate.focusEnterHandler)
   {
    HandlersPrivate.focusEnterHandler(navigateForward);
  }
}

```

Depois que o manipulador é acionado com a palavra-chave `focusEnter`, `registerFocusEnterHandler` o manipulador é invocado com uma função de retorno de chamada `focusEnterHandler` que recebe um parâmetro chamado `navigateForward`. O valor de `navigateForward` determina o tipo de eventos. O `focusEnterHandler` é invocado apenas por Ctrl+F6 e não pela tecla de tabulação.
As chaves úteis para mover eventos dentro Teams são as seguinte:

* Evento Forward: teclas Ctrl+F6
* Evento backward: teclas Ctrl+Shift+F6

``` C#

case 'focusEnter':     
this.registerFocusEnterHandler((navigateForward: boolean = true) => {
this.sdkWindowMessageHandler.sendRequestMessage(this.frame, this.constants.SdkMessageTypes.focusEnter, [navigateForward]);
// Set focus on iframe or webview
if (this.frame && this.frame.sourceElem) {
  this.frame.sourceElem.focus();
}
return true;
});
}

// callback function to be passed to the handler
private focusEnterHandler: (navigateForward: boolean) => boolean;

// function that gets invoked after handler is registered.
private registerFocusEnterHandler(focusEnterHandler: (navigateForward: boolean) => boolean): void {
this.focusEnterHandler = focusEnterHandler;
this.layoutService.registerAppFocusEnterCallback(this.focusEnterHandler);
}

```

### <a name="personal-app"></a>Aplicativo pessoal

:::image type="content" source="../../assets/images/personal-apps/registerfocus.png" alt-text="Exemplo mostra opções para adicionar a API registerOnFocussed" border="true":::

#### <a name="personal-app-forward-event"></a>Aplicativo pessoal: evento Forward

:::image type="content" source="../../assets/images/personal-apps/registerfocus-forward-event.png" alt-text="Exemplo mostra opções para adicionar a movimentação de encaminhamento da API registerOnFocussed" border="true":::

#### <a name="personal-app-backward-event"></a>Aplicativo pessoal: evento Backward

:::image type="content" source="../../assets/images/personal-apps/registerfocus-backward-event.png" alt-text="Exemplo mostra opções para adicionar a movimentação para trás registerOnFocussed API" border="true":::

### <a name="tab"></a>Tab

:::image type="content" source="../../assets/images/personal-apps/registerfocus-tab.png" alt-text="Exemplo mostra opções para adicionar a guia registerOnFocussed API para" border="true":::

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Criar um canal ou uma guia de grupo](~/tabs/how-to/create-channel-group-tab.md)

## <a name="see-also"></a>Confira também

* [Teams guias](~/tabs/what-are-tabs.md)
* [Guias em dispositivos móveis](~/tabs/design/tabs-mobile.md)
* [Criar guias com Cartões Adaptáveis](~/tabs/how-to/build-adaptive-card-tabs.md)
* [Criar abas para conversação](~/tabs/how-to/conversational-tabs.md)
