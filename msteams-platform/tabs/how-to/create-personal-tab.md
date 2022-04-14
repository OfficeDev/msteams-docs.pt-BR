---
title: Criar uma guia pessoal
author: laujan
description: Um guia de início rápido para criar uma guia pessoal com o Gerador Yeoman, o ASP.NET Core ou o ASP.NET Core MVC para Microsoft Teams usando Node.js e atualizar o manifesto do aplicativo.
ms.localizationpriority: medium
ms.topic: quickstart
ms.author: lajanuar
keywords: yeoman ASP.NET de permissão de domínio de conversa appmanifest do pacote MVC
zone_pivot_groups: teams-app-environment
ms.openlocfilehash: fda21b5bf9908529a9a20820867551202b761362
ms.sourcegitcommit: 77e92360bd8fb5afcda76195d90122ce8ef0389e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64838479"
---
# <a name="create-a-personal-tab"></a>Criar uma guia pessoal

Guias pessoais, junto com bots de conversação direta, fazem parte de aplicativos pessoais e têm como escopo um único usuário. Eles podem ser fixados no painel esquerdo para facilitar o acesso. Você também pode [reordenar](#reorder-static-personal-tabs) suas guias pessoais.

Verifique se você tem todos os [pré-requisitos para](~/tabs/how-to/tab-requirements.md) criar sua guia pessoal.

::: zone pivot="node-java-script"

## <a name="create-a-personal-tab-with-nodejs"></a>Criar uma guia pessoal com Node.js

1. No prompt de comando, instale os [pacotes Yeoman](https://yeoman.io/) e [gulp-cli](https://www.npmjs.com/package/gulp-cli) inserindo o seguinte comando depois de instalar o Node.js:

    ```cmd
    npm install yo gulp-cli --global
    ```

1. No prompt de comando, instale o Microsoft Teams app inserindo o seguinte comando:

    ```cmd
    npm install generator-teams --global
    ```

A seguir estão as etapas para criar uma guia pessoal:

1. [Gerar seu aplicativo com uma guia pessoal](#generate-your-application-with-a-personal-tab)
1. [Adicionar uma página de conteúdo à guia pessoal](#add-a-content-page-to-the-personal-tab)
1. [Criar um pacote do aplicativo](#create-your-app-package)
1. [Compilar e executar seu aplicativo](#build-and-run-your-application)
1. [Estabelecer um túnel seguro para sua guia pessoal](#establish-a-secure-tunnel-to-your-tab)
1. [Upload seu aplicativo para Teams](#upload-your-application-to-teams)

### <a name="generate-your-application-with-a-personal-tab"></a>Gerar seu aplicativo com uma guia pessoal

1. No prompt de comando, crie um novo diretório para sua guia pessoal.

1. Insira o seguinte comando em seu novo diretório para iniciar o gerador Microsoft Teams Aplicativo:

    ```cmd
    yo teams
    ```

1. Forneça seus valores para uma série de perguntas solicitadas pelo Microsoft Teams App para atualizar o `manifest.json` arquivo.

    :::image type="content" source="~/assets/images/tab-images/teamsTabScreenshot.PNG" alt-text="Teams gerador" border="true":::

    <details>
    <summary><b>Série de perguntas para atualizar o arquivo manifest.json</b></summary>

    * **Qual é o nome da solução?**

      O nome da solução é o nome do projeto. Você pode aceitar o nome sugerido selecionando **Enter**.

    * **Onde você deseja colocar os arquivos?**

      No momento, você está no diretório do projeto. Selecione **Enter**.

    * **Título do seu projeto Microsoft Teams aplicativo?**

      O título é o nome do pacote do aplicativo e é usado no manifesto e na descrição do aplicativo. Insira um título ou selecione **Enter** para aceitar o nome padrão.

    * **O nome da sua (empresa)? (máximo de 32 caracteres)**

      O nome da empresa será usado no manifesto do aplicativo. Insira um nome de empresa ou selecione **Enter** para aceitar o nome padrão.

    * **Qual versão de manifesto você deseja usar?**

      Selecione o esquema padrão.

    * **Scaffolding rápido? (Y/n)**

      O padrão é sim; insira **n** para inserir sua ID de Parceiro da Microsoft.

    * **Insira sua ID de Parceiro da Microsoft, se você tiver uma? (Deixe em branco para ignorar)**

      Esse campo não é obrigatório e deve ser usado somente se você já fizer parte do [Microsoft Partner Network](https://partner.microsoft.com).

    * **O que você deseja adicionar ao seu projeto?**

      Selecione **( &ast; ) uma guia**.

    * **A URL em que você hospedará essa solução?**

      Por padrão, o gerador sugere uma URL de Sites do Azure. Você só está testando seu aplicativo localmente, portanto, uma URL válida não é necessária.

    * **Deseja mostrar um indicador de carregamento quando seu aplicativo/guia for carregado?**

      Escolha **não** incluir um indicador de carregamento quando seu aplicativo ou guia for carregado. O padrão é não, insira **n**.

    * **Você gostaria que aplicativos pessoais fossem renderizados sem uma barra de texto de tabulação?**

      Escolha **não** incluir aplicativos pessoais a serem renderizados sem uma barra de cabeçalho de tabulação. O padrão é não, insira **n**.

    * **Deseja incluir a estrutura de teste e os testes iniciais? (y/N)**

      Escolha **não** incluir uma estrutura de teste para este projeto. O padrão é não, insira **n**.

    * **Deseja incluir o suporte ao ESLint? (y/N)**

      Opte por não incluir o suporte ao ESLint. O padrão é não, insira **n**.

    * **Deseja usar aplicativos do Azure Insights telemetria? (y/N)**

      Escolha **não** [incluir Aplicativo Azure Insights.](/azure/azure-monitor/app/app-insights-overview) O padrão é não; enter **n**.

    * **Nome da guia padrão (máximo de 16 caracteres)?**

      Nomeie sua guia. Esse nome de guia é usado em todo o projeto como um componente de caminho de arquivo ou URL.

    * **Que tipo de Guia você gostaria de criar?**

      Use as teclas de direção para selecionar **Pessoal (estático)**.

    * **Você precisa do Microsoft Azure Active Directory (Azure AD) de logon único para a guia?**

      Escolha **não** incluir o suporte de Logon Único do Azure AD para a guia. O padrão é sim, insira **n**.

    </details>

### <a name="add-a-content-page-to-the-personal-tab"></a>Adicionar uma página de conteúdo à guia pessoal

Crie uma página de conteúdo e atualize os arquivos existentes do aplicativo de guia pessoal:

1. Crie um novo **personal.html** arquivo no Visual Studio Code com a seguinte marcação:

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

1. Abra `manifest.json` a partir do seguinte local em seu Visual Studio Code:

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
    > O componente de **caminho yourDefaultTabNameTab é** o valor que você inseriu no gerador para o Nome da Guia **Padrão mais a** palavra **Tab**.
    >
    > Por exemplo: DefaultTabName é **MyTab** e **/MyTabTab/**

1. Atualize **o componente de caminho contentURL** **yourDefaultTabNameTab** com o nome real da guia.

1. Salve o arquivo `manifest.json` atualizado.

1. Abra **Tab.ts** em seu Visual Studio Code do seguinte caminho para fornecer sua página de conteúdo em um IFrame:

    ```bash
    ./src/server/<yourDefaultTabNameTab>/<yourDefaultTabNameTab>.ts
    ```

1. Adicione o seguinte à lista de decoradores IFrame:

    ```typescript
     @PreventIframe("/<yourDefaultTabName Tab>/personal.html")
    ```

1. Salve o arquivo atualizado. O código da guia foi concluído.

### <a name="create-your-app-package"></a>Criar um pacote do aplicativo

Você deve ter um pacote de aplicativos para compilar e executar seu aplicativo Teams. O pacote do aplicativo é criado por meio de uma tarefa gulp que valida `manifest.json` o arquivo e gera a pasta zip no `./package` diretório. No prompt de comando, use o comando `gulp manifest`.

### <a name="build-and-run-your-application"></a>Compilar e executar seu aplicativo

#### <a name="build-your-application"></a>Criar seu aplicativo

Insira o seguinte comando no prompt de comando para transpile sua solução para a **pasta ./dist** :

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

1. Procure `http://localhost:3007/<yourDefaultAppNameTab>/personal.html`, para exibir sua guia pessoal.

    :::image type="content" source="~/assets/images/tab-images/personalTab.PNG" alt-text="Guia html padrão" border="true":::

### <a name="establish-a-secure-tunnel-to-your-tab"></a>Estabelecer um túnel seguro para sua guia

No prompt de comando, saia do localhost e insira o seguinte comando para estabelecer um túnel seguro para sua guia:

```cmd
gulp ngrok-serve
```

> [!IMPORTANT]
> Depois que a guia for carregada para Microsoft Teams por meio do **ngrok** e for salva com êxito, você poderá exibi-la no Teams até que a sessão de túnel seja encerrada.

### <a name="upload-your-application-to-teams"></a>Upload seu aplicativo para Teams

1. Vá para Microsoft Teams e selecione **Aplicativos**&nbsp; :::image type="content" source="~/assets/images/tab-images/store.png" alt-text="Teams Store":::.
1. Selecione **Gerenciar seus aplicativos** **e Upload um aplicativo personalizado**.
1. Vá para o diretório do projeto, navegue até **a pasta ./package** , selecione a pasta zip e escolha **Abrir**.

    :::image type="content" source="~/assets/images/tab-images/addingpersonaltab.png" alt-text="Adicionando sua guia pessoal" border="true":::

1. Selecione **Adicionar** na caixa de diálogo. Sua guia é carregada para Teams.

    :::image type="content" source="~/assets/images/tab-images/personaltabuploaded.png" alt-text="Guia Pessoal carregada" border="true":::

1. No painel esquerdo do Teams, selecione as reticências &#x25CF;&#x25CF;&#x25CF; e escolha seu aplicativo carregado para exibir sua guia pessoal.

   Agora você criou e adicionou sua guia pessoal com êxito Teams.
  
   Como você tem sua guia pessoal Teams, você também pode [reordenar](#reorder-static-personal-tabs) sua guia pessoal.

::: zone-end

::: zone pivot="razor-csharp"

## <a name="create-a-personal-tab-with-aspnet-core"></a>Criar uma guia pessoal com ASP.NET Core

1. No prompt de comando, crie um novo diretório para o projeto de guia.

1. Clone o repositório de exemplo em seu novo diretório usando o seguinte comando ou você pode baixar o [código-fonte](https://github.com/OfficeDev/Microsoft-Teams-Samples) e extrair os arquivos:

    ```cmd
    git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
    ```

A seguir estão as etapas para criar uma guia pessoal:

1. [Gerar seu aplicativo com uma guia pessoal](#generate-your-application-with-a-personal-tab-1)
1. [Atualizar e executar seu aplicativo](#update-and-run-your-application)
1. [Estabelecer um túnel seguro para sua guia](#establish-a-secure-tunnel-to-your-tab-1)
1. [Atualizar o pacote do aplicativo com o Portal do Desenvolvedor](#update-your-app-package-with-developer-portal)
1. [Visualizar seu aplicativo no Teams](#preview-your-app-in-teams)

### <a name="generate-your-application-with-a-personal-tab"></a>Gerar seu aplicativo com uma guia pessoal

1. Abra Visual Studio e selecione **Abrir um projeto ou solução**.

1. Vá para **a pasta Microsoft-Teams-Samplessamplestab-personalrazor-csharp** >  >  >  e abra **PersonalTab.sln**.

1. No Visual Studio, selecione **F5** ou inicie **a depuração no menu de depuração** do aplicativo  para verificar se o aplicativo foi carregado corretamente. Em um navegador, vá para as seguintes URLs:

    * <http://localhost:3978/>
    * <http://localhost:3978/personalTab>
    * <http://localhost:3978/privacy>
    * <http://localhost:3978/tou>

<details>
<summary><b>Examinar o código-fonte</b></summary>

#### <a name="startupcs"></a>Startup.cs

Este projeto foi criado com base em um modelo vazio do aplicativo Web ASP.NET Core 3.1 com a caixa de seleção Avançado – Configurar para **HTTPS** selecionada na instalação. Os serviços MVC são registrados pelo método da estrutura de injeção de `ConfigureServices()` dependência. Além disso, o modelo vazio não habilita o fornecimento de conteúdo estático por padrão, portanto, o middleware `Configure()` de arquivos estáticos é adicionado ao método usando o seguinte código:

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

No ASP.NET Core, a pasta raiz da Web é onde o aplicativo procura arquivos estáticos.

#### <a name="indexcshtml"></a>Index.cshtml

ASP.NET Core trata arquivos chamados **Index** como o padrão ou home page do site. Quando a URL do navegador aponta para a raiz do site, **Index.cshtml** é exibida como a home page do aplicativo.

#### <a name="appmanifest-folder"></a>Pasta AppManifest

Essa pasta contém os seguintes arquivos de pacote de aplicativos necessários:

* Um ícone de cor completo medindo 192 x 192 pixels.
* Um ícone de estrutura de tópicos transparente medindo 32 x 32 pixels.
* Um `manifest.json` arquivo que especifica os atributos do seu aplicativo.

Esses arquivos devem ser compactados em um pacote do aplicativo para uso no carregamento da guia para Teams. Microsoft Teams carrega o `contentUrl` especificado em seu manifesto, insere-o em um <iframe\> e o renderiza em sua guia.

#### <a name="csproj"></a>.csproj

No Visual Studio Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione **Editar Project Arquivo**. No final do arquivo, você pode ver o seguinte código que cria e atualiza sua pasta zip quando o aplicativo é compilado:

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

1. Abra Visual Studio Gerenciador de Soluções e vá para a pasta **PagesShared** > , abra **_Layout.cshtml** e adicione o seguinte à seção `<head>` de marcas:

    ```HTML
    <script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
    <script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>
    ```

1. Em Visual Studio Gerenciador de Soluções **personalTab.cshtml** na pasta **Páginas**, `microsoftTeams.initialize()` adicione as `<script>` marcas e salve.

1. No Visual Studio, selecione **F5** ou **inicie a depuração** no menu **Depuração do** aplicativo.

### <a name="establish-a-secure-tunnel-to-your-tab"></a>Estabelecer um túnel seguro para sua guia

No prompt de comando na raiz do diretório do projeto, execute o seguinte comando para estabelecer um túnel seguro para sua guia:

```cmd
ngrok http 3978 --host-header=localhost
```

### <a name="update-your-app-package-with-developer-portal"></a>Atualizar o pacote do aplicativo com o Portal do Desenvolvedor

1. Acesse o [**portal do desenvolvedor**](https://dev.teams.microsoft.com/home).

1. Abra **aplicativos** e selecione **Importar aplicativo**.

1. O nome do arquivo do pacote do aplicativo `tab.zip` é e está disponível no `/bin/Debug/netcoreapp3.1/tab.zip` caminho.

1. Selecione `tab.zip` e abra-o no Portal do Desenvolvedor.

1. Uma **ID de aplicativo padrão** é criada e preenchida na **seção Informações** básicas.

1. Adicione a descrição Curta e Longa para seu aplicativo em **Descrições**.

1. Em **Informações do Desenvolvedor**, adicione os detalhes necessários e, no site (deve ser uma **URL HTTPS válida), forneça a** URL HTTPS do ngrok.

1. Em **URLs de aplicativo**, atualize a política de privacidade e `https://<yourngrokurl>/privacy` os Termos de uso para `https://<yourngrokurl>/tou` salvar e salvar.

1. Nos **recursos do aplicativo**, **selecione Personal appCreate** >  **sua primeira guia de** aplicativo pessoal, insira o Nome e atualize a **URL de Conteúdo** com `https://<yourngrokurl>/personalTab`. Deixe o campo URL do Site em branco e selecione **Contexto** como personalTab na lista suspensa e **Adicionar**.

1. Selecione **Salvar**.

1. Na seção Domínios, os domínios de suas guias devem conter a URL do ngrok sem o prefixo `<yourngrokurl>.ngrok.io`HTTPS.

### <a name="preview-your-app-in-teams"></a>Visualizar seu aplicativo no Teams

1. Selecione **Visualizar no Teams** na barra de ferramentas do Portal do Desenvolvedor, o Portal do Desenvolvedor informa que seu aplicativo foi carregado com êxito. A **página** Adicionar é exibida para seu aplicativo Teams.

1. Selecione **Adicionar** para carregar a guia Teams. Sua guia agora está disponível no Teams.

    :::image type="content" source="~/assets/images/tab-images/personaltabaspnetuploaded.png" alt-text="Guia Padrão" border="true":::

   Agora você criou e adicionou sua guia pessoal com êxito Teams.
  
   Como você tem sua guia pessoal Teams, você também pode [reordenar](#reorder-static-personal-tabs) sua guia pessoal.

::: zone-end

::: zone pivot="mvc-csharp"

## <a name="create-a-personal-tab-with-aspnet-core-mvc"></a>Criar uma guia pessoal com ASP.NET Core MVC

1. No prompt de comando, crie um novo diretório para o projeto de guia.

1. Clone o repositório de exemplo em seu novo diretório usando o seguinte comando ou você pode baixar o [código-fonte](https://github.com/OfficeDev/Microsoft-Teams-Samples) e extrair os arquivos:

    ```cmd
    git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
    ```

A seguir estão as etapas para criar uma guia pessoal:

1. [Gerar seu aplicativo com uma guia pessoal](#generate-your-application-with-a-personal-tab-2)
1. [Atualizar e executar o aplicativo](#update-and-run-your-application-1)
1. [Estabelecer um túnel seguro para sua guia](#establish-a-secure-tunnel-to-your-tab-2)
1. [Atualizar o pacote do aplicativo com o Portal do Desenvolvedor](#update-your-app-package-with-developer-portal-1)
1. [Visualizar seu aplicativo no Teams](#preview-your-app-in-teams-1)

### <a name="generate-your-application-with-a-personal-tab"></a>Gerar seu aplicativo com uma guia pessoal

1. Abra Visual Studio e selecione **Abrir um projeto ou solução**.

1. Acesse **a pasta Microsoft-Teams-Samplessamplestab-personalmvc-csharp** >  >  >  e abra **PersonalTabMVC.sln** Visual Studio.

1. No Visual Studio, selecione **F5** ou inicie **a depuração no menu de depuração** do aplicativo  para verificar se o aplicativo foi carregado corretamente. Em um navegador, vá para as seguintes URLs:

    * <http://localhost:3978>
    * <http://localhost:3978/personalTab>
    * <http://localhost:3978/privacy>
    * <http://localhost:3978/tou>

<details>
<summary><b>Examinar o código-fonte</b></summary>

#### <a name="startupcs"></a>Startup.cs

Este projeto foi criado com base em um modelo vazio do aplicativo Web ASP.NET Core 3.1 com a caixa de seleção Avançado – Configurar para **HTTPS** selecionada na instalação. Os serviços MVC são registrados pelo método da estrutura de injeção de `ConfigureServices()` dependência. Além disso, o modelo vazio não habilita o fornecimento de conteúdo estático por padrão, portanto, o middleware `Configure()` de arquivos estáticos é adicionado ao método usando o seguinte código:

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

No ASP.NET Core, a pasta raiz da Web é onde o aplicativo procura arquivos estáticos.

#### <a name="appmanifest-folder"></a>Pasta AppManifest

Essa pasta contém os seguintes arquivos de pacote de aplicativos necessários:

* Um **ícone de cor completo** medindo 192 x 192 pixels.
* Um **ícone de estrutura de tópicos transparente** medindo 32 x 32 pixels.
* Um `manifest.json` arquivo que especifica os atributos do seu aplicativo.

Esses arquivos devem ser compactados em um pacote do aplicativo para uso no carregamento da guia para Teams. Microsoft Teams carrega o `contentUrl` especificado em seu manifesto, insere-o em um IFrame e o renderiza em sua guia.

#### <a name="csproj"></a>.csproj

No Visual Studio Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione **Editar Project Arquivo**. No final do arquivo, você verá o seguinte código que cria e atualiza sua pasta zip quando o aplicativo é compilado:

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

* Compartilhado: a marcação de exibição **parcial _Layout.cshtml** contém a estrutura geral da página do aplicativo e os elementos visuais compartilhados. Ele também faz referência à biblioteca Teams dados.

#### <a name="controllers"></a>Controladores

Os controladores usam a propriedade `ViewBag` para transferir valores dinamicamente para as exibições.

</details>

### <a name="update-and-run-your-application"></a>Atualizar e executar seu aplicativo

1. Abra Visual Studio Gerenciador de Soluções e vá para a pasta **ViewsShared** > , abra **_Layout.cshtml** e adicione o seguinte à seção `<head>` de marcas:

    ```HTML
    <script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
    <script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>
    ```

1. Em Visual Studio Gerenciador de Soluções **personalTab.cshtml** da pasta **ViewsPersonalTab**  >  e adicione `microsoftTeams.initialize()` dentro das `<script>` marcas e salve.

1. No Visual Studio, selecione **F5** ou **inicie a depuração** no menu **Depuração do** aplicativo.

### <a name="establish-a-secure-tunnel-to-your-tab"></a>Estabelecer um túnel seguro para sua guia

No prompt de comando na raiz do diretório do projeto, execute o seguinte comando para estabelecer um túnel seguro para sua guia:

```cmd
ngrok http 3978 --host-header=localhost
```

### <a name="update-your-app-package-with-developer-portal"></a>Atualizar o pacote do aplicativo com o Portal do Desenvolvedor

1. Acesse o [**portal do desenvolvedor**](https://dev.teams.microsoft.com/home).

1. Abra **aplicativos** e selecione **Importar aplicativo**.

1. O nome do pacote do aplicativo é **tab.zip**. Ele está disponível no seguinte caminho:

    ```
    /bin/Debug/netcoreapp3.1/tab.zip
    ```

1. Selecione **tab.zip** e abra-o no Portal do Desenvolvedor.

1. Uma **ID de aplicativo padrão** é criada e preenchida na **seção Informações** básicas.

1. Adicione a descrição Curta e Longa para seu aplicativo em **Descrições**.

1. Em **Informações do Desenvolvedor**, adicione os detalhes necessários e, no site (deve ser uma **URL HTTPS válida), forneça a** URL HTTPS do ngrok.

1. Em **URLs de aplicativo**, atualize a política de privacidade e `https://<yourngrokurl>/privacy` os Termos de uso para `https://<yourngrokurl>/tou` salvar e salvar.

1. Nos **recursos do aplicativo**, **selecione Personal appCreate** >  **sua primeira guia de** aplicativo pessoal, insira o Nome e atualize a **URL de Conteúdo** com `https://<yourngrokurl>/personalTab`. Deixe o campo URL do Site em branco e selecione **Contexto** como personalTab na lista suspensa e **Adicionar**.

1. Selecione **Salvar**.

1. Na seção Domínios, domínios de suas guias devem conter a URL do ngrok sem o prefixo `<yourngrokurl>.ngrok.io`HTTPS.

### <a name="preview-your-app-in-teams"></a>Visualizar seu aplicativo no Teams

1. Selecione **Visualizar no Teams** na barra de ferramentas do Portal do Desenvolvedor, o Portal do Desenvolvedor informa que seu aplicativo foi carregado com êxito. A **página** Adicionar é exibida para seu aplicativo Teams.

1. Selecione **Adicionar** para carregar a guia Teams. Sua guia agora está disponível no Teams.

    :::image type="content" source="~/assets/images/tab-images/personaltabaspnetmvccoreuploaded.png" alt-text="Guia pessoal" border="true":::
  
   Agora você criou e adicionou sua guia pessoal com êxito Teams.

   Como você tem sua guia pessoal Teams, você também pode [reordenar](#reorder-static-personal-tabs) sua guia pessoal.

::: zone-end

## <a name="reorder-static-personal-tabs"></a>Reordenar guias pessoais estáticas

A partir da versão 1.7 do manifesto, os desenvolvedores podem reorganizar todas as guias em seu aplicativo pessoal. Em particular, um desenvolvedor pode mover a guia **de chat do bot** , que sempre assume como padrão a primeira posição, em qualquer lugar no cabeçalho da guia do aplicativo pessoal. Duas palavras-chave de guia `entityId` reservadas são declaradas, **conversas** e **sobre**.

Se você criar um bot com um **escopo pessoal** , ele aparecerá na primeira posição da guia em um aplicativo pessoal por padrão. Se você quiser movê-lo para outra posição, deverá adicionar um objeto de guia estático ao manifesto com a palavra-chave reservada, **conversas**. A **guia** conversa é exibida na Web ou na área de trabalho, dependendo de onde você adiciona a **guia de** conversa na `staticTabs` matriz.

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

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Criar uma guia de canal ou grupo](~/tabs/how-to/create-channel-group-tab.md)

## <a name="see-also"></a>Confira também

* [Teams guias](~/tabs/what-are-tabs.md)
* [Guias em dispositivos móveis](~/tabs/design/tabs-mobile.md)
* [Criar guias com Cartões Adaptáveis](~/tabs/how-to/build-adaptive-card-tabs.md)
* [Criar abas para conversação](~/tabs/how-to/conversational-tabs.md)
* [Compartilhar com o Teams a partir do aplicativo ou guia pessoal](~/concepts/build-and-test/share-to-teams-from-personal-app-or-tab.md)
