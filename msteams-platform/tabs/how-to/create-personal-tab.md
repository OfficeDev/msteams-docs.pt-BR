---
title: Criar uma guia pessoal
author: laujan
description: Neste módulo, saiba como criar uma guia pessoal com o Gerador Yeoman, ASP.NET Core ou ASP.NET Core MVC para o Microsoft Teams usando Node.js e atualizando o manifesto do aplicativo.
ms.localizationpriority: high
ms.topic: quickstart
ms.author: lajanuar
zone_pivot_groups: teams-app-environment
ms.openlocfilehash: dcc000c64068cbcbd24a03da365e799e9dd1c155
ms.sourcegitcommit: 79d525c0be309200e930cdd942bc2c753d0b718c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/19/2022
ms.locfileid: "66841691"
---
# <a name="create-a-personal-tab"></a>Criar uma guia pessoal

Guias pessoais, junto com bots de conversação direta, fazem parte de aplicativos pessoais e têm como escopo um único usuário. Eles podem ser fixados no painel esquerdo para facilitar o acesso. Você também pode [reordenar](#reorder-static-personal-tabs) suas guias pessoais.

Certifique-se de ter todos os [pré-requisitos](~/tabs/how-to/tab-requirements.md) para criar sua guia pessoal.

[!INCLUDE [sdk-include](~/includes/sdk-include.md)]

::: zone pivot="node-java-script"

## <a name="create-a-personal-tab-with-nodejs"></a>Criar uma guia pessoal com Node.js

1. No prompt de comando, instale os pacotes [Yeoman](https://yeoman.io/) e [gulp-cli](https://www.npmjs.com/package/gulp-cli) inserindo o seguinte comando após a instalação do Node.js:

    ```cmd
    npm install yo gulp-cli --global
    ```

1. No prompt de comando, instale o gerador de aplicativos do Microsoft Teams inserindo o seguinte comando:

    ```cmd
    npm install generator-teams --global
    ```

A seguir estão as etapas para criar uma guia pessoal:

1. [Gerar seu aplicativo com uma guia pessoal](#generate-your-application-with-a-personal-tab)
1. [Adicionar uma página de conteúdo à guia pessoal](#add-a-content-page-to-the-personal-tab)
1. [Criar um pacote do aplicativo](#create-your-app-package)
1. [Criar e executar o aplicativo](#build-and-run-your-application)
1. [Estabelecer um túnel seguro para sua guia pessoal](#establish-a-secure-tunnel-to-your-tab)
1. [Carregar seu aplicativo para o Teams](#upload-your-application-to-teams)

### <a name="generate-your-application-with-a-personal-tab"></a>Gerar seu aplicativo com uma guia pessoal

1. No prompt de comando, crie um novo diretório para sua guia pessoal.

1. Insira o seguinte comando em seu novo diretório para iniciar o gerador de aplicativos do Microsoft Teams:

    ```cmd
    yo teams
    ```

1. Forneça seus valores para uma série de perguntas solicitadas pelo gerador de aplicativos do Microsoft Teams para atualizar o arquivo `manifest.json`.

    :::image type="content" source="~/assets/images/tab-images/teamsTabScreenshot.PNG" alt-text="Gerador do Teams":::

    <details>
    <summary><b>Série de perguntas para atualizar seu arquivo manifest.json</b></summary>

    * **Qual é o nome da solução?**

      O nome da solução é o nome do projeto. Você pode aceitar o nome sugerido selecionando **Enter**.

    * **Onde você deseja colocar os arquivos?**

      No momento, você está no diretório do projeto. Selecione **Enter**.

    * **Título do seu projeto de aplicativo Microsoft Teams?**

      O título é o nome do pacote do aplicativo e é usado no manifesto e na descrição do aplicativo. Insira um título ou selecione **Enter** para aceitar o nome padrão.

    * **O nome da sua (empresa)? (máximo de 32 caracteres)**

      O nome da empresa será usado no manifesto do aplicativo. Insira um nome para a empresa ou selecione **Enter** para aceitar o nome padrão.

    * **Qual versão do manifesto você gostaria de usar?**

      Selecione o esquema padrão.

    * **Scaffolding rápido? (S/N)**

      O padrão é sim; insira **n** para inserir sua ID de Parceiro da Microsoft.

    * **Inserir sua ID de Parceiro da Microsoft, se tiver uma?: (Deixe em branco para ignorar)**

      Este campo não é obrigatório e deve ser usado somente se você já faz parte do [Microsoft Partner Network](https://partner.microsoft.com).

    * **Quais recursos você deseja adicionar ao seu projeto?**

      Selecione **( &ast; ) uma guia**.

    * **Em qual URL você hospedará essa solução?**

      Por padrão, o gerador sugere uma URL de Sites do Azure. Você só está testando seu aplicativo localmente, portanto, uma URL válida não é necessária.

    * **Você gostaria de mostrar um indicador de carregamento quando seu aplicativo/guia carregar?**

      Escolha **não** para incluir um indicador de carregamento quando seu aplicativo ou guia for carregado. O padrão é não, insira **n**.

    * **Você gostaria que aplicativos pessoais fossem renderizados sem uma barra de texto de tabulação?**

      Escolha **não** para incluir aplicativos pessoais a serem renderizados sem uma barra de cabeçalho de tabulação. O padrão é não, insira **n**.

    * **Você gostaria de incluir a estrutura de teste e os testes iniciais? (S/N)**

      Escolha **não** para incluir uma estrutura de teste para este projeto. O padrão é não, insira **n**.

    * **Deseja incluir o suporte ao ESLint? (S/N)**

      Opte por não incluir o suporte ao ESLint. O padrão é não, insira **n**.

    * **Você gostaria de usar o Azure Application Insights para telemetria? (S/N)**

      Escolha **não** para incluir o [Azure Application Insights](/azure/azure-monitor/app/app-insights-overview). O padrão é não, insira **n**.

    * **Nome da guia padrão (máximo de 16 caracteres)**:Guia SSO

      Nomeie sua guia. Esse nome de guia é usado em todo o projeto como um arquivo ou componente de caminho de URL.

    * **Que tipo de Guia você gostaria de criar?**

      Use as teclas de direção para selecionar **Pessoal (estático)**.

    * **Deseja exigir o suporte ao logon único do Microsoft Azure Active Directory (Azure AD) para a guia?**

      Escolha **não** para incluir o suporte de logon único do Azure AD para a guia. O padrão é sim, insira **n**.

    </details>

### <a name="add-a-content-page-to-the-personal-tab"></a>Adicionar uma página de conteúdo à guia pessoal

Crie uma página de conteúdo e atualize os arquivos existentes do aplicativo de guia pessoal:

1. Crie um novo arquivo **personal.html** no Visual Studio Code com a seguinte marcação:

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

1. Salve **personal.html** na pasta **pública** do aplicativo no seguinte local:

    ```
    ./src/public/<yourDefaultTabNameTab>/personal.html
    ```

1. Abra `manifest.json` no seguinte local no Visual Studio Code:

    ```
     ./src/manifest/manifest.json
    ```

1. Adicione o seguinte à matriz `staticTabs` (`staticTabs":[]`) e adicione o seguinte objeto JSON:

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
    > O componente de caminho **DefaultTabNameTab** é o valor que você inseriu no gerador para **Nome da guia padrão** mais a palavra **Guia**.
    >
    > Por exemplo: o DefaultTabName é **MyTab** depois **/MyTabTab/**

1. Atualize Componente de caminho **contentURL** **seu DefaultTabNameTab** com o nome verdadeiro da guia.

1. Salve o arquivo `manifest.json` atualizado.

1. Abra **Tab.ts** no Visual Studio Code no seguinte caminho para fornecer sua página de conteúdo em um IFrame:

    ```bash
    ./src/server/<yourDefaultTabNameTab>/<yourDefaultTabNameTab>.ts
    ```

1. Adicione o seguinte à lista de decoradores IFrame:

    ```typescript
     @PreventIframe("/<yourDefaultTabName Tab>/personal.html")
    ```

1. Salve o arquivo atualizado. O código da guia está concluído.

### <a name="create-your-app-package"></a>Criar um pacote do aplicativo

Você deve ter um pacote de aplicativos para compilar e executar seu aplicativo no Teams. O pacote do aplicativo é criado por meio de uma tarefa gulp que valida o arquivo `manifest.json` e gera a pasta zip no diretório `./package`. No prompt de comando, use o comando `gulp manifest`:

### <a name="build-and-run-your-application"></a>Compilar e executar seu aplicativo

#### <a name="build-your-application"></a>Compilar seu aplicativo

Insira o seguinte comando no prompt de comando para transcompilar sua solução para a pasta **./dist** :

```cmd
gulp build
```

#### <a name="run-your-application"></a>Executar seu aplicativo

1. No prompt de comando, digite o seguinte comando para iniciar um servidor Web local:

    ```cmd
    gulp serve
    ```

1. Insira `http://localhost:3007/<yourDefaultAppNameTab>/` em seu navegador para exibir a página inicila do seu aplicativo.

    :::image type="content" source="~/assets/images/tab-images/homePage.png" alt-text="Guia padrão":::

1. Navegue por `http://localhost:3007/<yourDefaultAppNameTab>/personal.html` para exibir sua guia pessoal.

    :::image type="content" source="~/assets/images/tab-images/personalTab.PNG" alt-text="Guia html padrão":::

### <a name="establish-a-secure-tunnel-to-your-tab"></a>Estabelecer um túnel seguro para sua guia

No prompt de comando, saia do localhost e insira o seguinte comando para estabelecer um túnel seguro para sua guia:

```cmd
gulp ngrok-serve
```

> [!IMPORTANT]
> Depois que sua guia for carregada para o Microsoft Teams por meio do **ngrok** e salva com êxito, você poderá exibi-la no Teams até que a sessão de túnel termine.

### <a name="upload-your-application-to-teams"></a>Carregar seu aplicativo no Teams

1. Vá para o Teams e selecione **Aplicativos**&nbsp;:::image type="content" source="~/assets/images/tab-images/store.png" alt-text="Loja do Teams":::.
1. Selecione **Gerenciar seus aplicativos** e **Fazer upload de um aplicativo personalizado**.
1. Vá para o diretório do projeto, navegue até a pasta **./package** , selecione a pasta zip e escolha **Abrir**.

    :::image type="content" source="~/assets/images/tab-images/addingpersonaltab.png" alt-text="Adicionar sua guia pessoal":::

1. Selecione **Adicionar** na caixa de diálogo. Sua guia é carregada no Teams.

    :::image type="content" source="~/assets/images/tab-images/personaltabuploaded.png" alt-text="Guia pessoal carregada":::

1. No painel esquerdo do Teams, selecione reticências &#x25CF;&#x25CF;&#x25CF; e escolha seu aplicativo carregado para exibir sua guia pessoal.

   Agora você criou e adicionou com êxito sua guia pessoal no Teams.
  
   Como você tem sua guia pessoal no Teams, você também pode [reordenar](#reorder-static-personal-tabs) sua guia pessoal.

::: zone-end

::: zone pivot="razor-csharp"

## <a name="create-a-personal-tab-with-aspnet-core"></a>Criar uma guia pessoal com o ASP.NET Core

1. No prompt de comando, crie um novo diretório para o projeto de guia.

1. Clone o repositório de exemplo em seu novo diretório usando o comando a seguir ou você pode baixar o [código-fonte](https://github.com/OfficeDev/Microsoft-Teams-Samples) e extrair os arquivos:

    ```cmd
    git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
    ```

A seguir estão as etapas para criar uma guia pessoal:

1. [Gerar seu aplicativo com uma guia pessoal](#generate-your-application-with-a-personal-tab-1)
1. [Atualizar e execute seu aplicativo](#update-and-run-your-application)
1. [Estabelecer um túnel seguro para sua guia](#establish-a-secure-tunnel-to-your-tab-1)
1. [Atualizar o pacote do aplicativo com Portal do Desenvolvedor](#update-your-app-package-with-developer-portal)
1. [Pré-visualizar seu aplicativo no Teams](#preview-your-app-in-teams)

### <a name="generate-your-application-with-a-personal-tab"></a>Gerar seu aplicativo com uma guia pessoal

1. Abra o Visual Studio e selecione **Abrir um projeto ou solução**.

1. Acesse a pasta de **exemplos** > **microsoft-teams** > **tab-personal** > **razor-csharp** e abra **personalTab.sln**.

1. No Visual Studio, selecione **F5** ou escolha **Iniciar Depuração** no menu de **Depuração** do aplicativo para verificar se o aplicativo foi carregado corretamente. Em um navegador, vá para as seguintes URLs:

    * `<http://localhost:3978/>`
    * `<http://localhost:3978/personalTab>`
    * `<http://localhost:3978/privacy>`
    * `<http://localhost:3978/tou>`

<details>
<summary><b>Exibir o código-fonte</b></summary>

#### <a name="startupcs"></a>Startup.cs

Este projeto foi criado com base em um modelo vazio de aplicativo Web do ASP.NET Core 3.1 com a caixa de seleção **Avançado: configurar para HTTPS** marcada na instalação. Os serviços MVC são registrados pelo método `ConfigureServices()` da estrutura de injeção de dependência. Além disso, o modelo vazio não habilita o fornecimento de conteúdo estático por padrão, portanto, o middleware de arquivos estáticos é adicionado ao método `Configure()` usando o seguinte código:

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

ASP.NET Core trata arquivos chamados **Índice** como o padrão ou página inicial para o site. Quando a URL do navegador aponta para a raiz do site,**index.cshtml** é exibido como o página inicial para seu aplicativo.

#### <a name="appmanifest-folder"></a>Pasta AppManifest

Esta pasta contém os seguintes arquivos de pacote de aplicativos necessários:

* Um ícone de cor completo medindo 192 x 192 pixels.
* Um ícone de contorno transparente medindo 32 x 32 pixels.
* Um arquivo `manifest.json` que especifica os atributos do seu aplicativo.

Esses arquivos devem ser compactados em um pacote de aplicativos para uso no carregamento de sua guia para o Teams. O Teams carrega o `contentUrl` especificado no manifesto, insere-o em um <iframe\> e renderiza-o em sua guia.

#### <a name="csproj"></a>.csproj

No Gerenciador de Soluções do Visual Studio, clique com o botão direito do mouse no projeto e selecione **Editar arquivo de projeto**. No final do arquivo, você pode ver o seguinte código que cria e atualiza sua pasta zip quando o aplicativo é compilado:

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

1. Abra Gerenciador de Soluções do Visual Studio, vá para a pasta **Páginas** > **Compartilhada**, abra **_Layout.cshtml** e adicione o seguinte à seção `<head>` marcas:

    ```HTML
    <script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
    <script src="https://res.cdn.office.net/teams-js/2.0.0/js/MicrosoftTeams.min.js" integrity="sha384-QtTBFeFlfRDZBfwHJHYQp7MdLJ2C3sfAEB1Qpy+YblvjavBye+q87TELpTnvlXw4" crossorigin="anonymous"></script>
    ```

1. No Gerenciador de Soluções do Visual Studio, abra **PersonalTab.cshtml** da pasta **Páginas** e adicione `app.initialize()` nas marcas `<script>` e salve.

1. No Visual Studio, selecione **F5** ou escolha **Iniciar Depuração** no menu **Depuração** do aplicativo para verificar se o aplicativo foi carregado corretamente.

### <a name="establish-a-secure-tunnel-to-your-tab"></a>Estabelecer um túnel seguro para sua guia

No prompt de comando na raiz do diretório do projeto, execute o seguinte comando para estabelecer um túnel seguro para sua guia:

```cmd
ngrok http 3978 --host-header=localhost
```

### <a name="update-your-app-package-with-developer-portal"></a>Atualize seu pacote de aplicativos com o Portal do Desenvolvedor

1. Vá para [**Portal do Desenvolvimento**](https://dev.teams.microsoft.com/home).

1. Abra **Aplicativos** e selecione **Importar aplicativo**.

1. O nome do arquivo do pacote do aplicativo é `tab.zip` e está disponível no caminho `/bin/Debug/netcoreapp3.1/tab.zip`.

1. Selecione `tab.zip` e abra-o no Portal do Desenvolvedor.

1. Uma **ID de aplicativo padrão** é criada e preenchida na seção **Informações básicas**.

1. Adicione a descrição Curta e Longa para seu aplicativo em **Descrições**.

1. Em **Informações do desenvolvedor**, adicione os detalhes necessários e, no site do **(deve ser uma URL HTTPS válida),** forneça sua URL HTTPS ngrok.

1. Em **urls de aplicativo**, atualize a política de privacidade para `https://<yourngrokurl>/privacy` e Termos de uso para `https://<yourngrokurl>/tou` e salvar.

1. Em **Recursos do aplicativo**, selecione **Aplicativo pessoal** > **Criar sua primeira guia de aplicativo pessoal** e insira o Nome e atualize a **URL de Conteúdo** com `https://<yourngrokurl>/personalTab`. Deixe o campo URL do Site em branco e selecione **Contexto** como personalTab na lista suspensa e **Adicionar**.

1. Selecione **Salvar**.

1. Na seção Domínios, os domínios de suas guias devem conter sua URL ngrok sem o prefixo HTTPS `<yourngrokurl>.ngrok.io`.

### <a name="preview-your-app-in-teams"></a>Visualizar seu aplicativo no Teams

1. Selecione **Visualização no Teams** na barra de ferramentas Portal do Desenvolvedor, Portal do Desenvolvedor informa que seu aplicativo foi carregado com êxito. A página **Adicionar** é exibida para seu aplicativo no Teams.

1. Selecione **Adicionar** para carregar a guia no Teams. Sua guia agora está disponível no Teams.

    :::image type="content" source="~/assets/images/tab-images/personaltabaspnetuploaded.png" alt-text="Guia padrão":::

   Agora você criou e adicionou com êxito sua guia pessoal no Teams.
  
   Como você tem sua guia pessoal no Teams, você também pode [reordenar](#reorder-static-personal-tabs) sua guia pessoal.

::: zone-end

::: zone pivot="mvc-csharp"

## <a name="create-a-personal-tab-with-aspnet-core-mvc"></a>Criar uma guia pessoal com o ASP.NET Core MVC

1. No prompt de comando, crie um novo diretório para o projeto de guia.

1. Clone o repositório de exemplo em seu novo diretório usando o comando a seguir ou você pode baixar o [código-fonte](https://github.com/OfficeDev/Microsoft-Teams-Samples) e extrair os arquivos:

    ```cmd
    git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
    ```

A seguir estão as etapas para criar uma guia pessoal:

1. [Gerar seu aplicativo com uma guia pessoal](#generate-your-application-with-a-personal-tab-2)
1. [Criar e executar o aplicativo](#update-and-run-your-application-1).
1. [Estabelecer um túnel seguro para sua guia](#establish-a-secure-tunnel-to-your-tab-2)
1. [Atualizar o pacote do aplicativo com Portal do Desenvolvedor](#update-your-app-package-with-developer-portal-1)
1. [Pré-visualizar seu aplicativo no Teams](#preview-your-app-in-teams-1)

### <a name="generate-your-application-with-a-personal-tab"></a>Gerar seu aplicativo com uma guia pessoal

1. Abra o Visual Studio e selecione **Abrir um projeto ou solução**.

1. Acesse a pasta de **exemplos** > **microsoft-teams** > **tab-personal** > **razor-csharp** e abra **PersonalTabMVC.sln** no Visual Studio.

1. No Visual Studio, selecione **F5** ou escolha **Iniciar Depuração** no menu de **Depuração** do aplicativo para verificar se o aplicativo foi carregado corretamente. Em um navegador, vá para as seguintes URLs:

    * `<http://localhost:3978>`
    * `<http://localhost:3978/personalTab>`
    * `<http://localhost:3978/privacy>`
    * `<http://localhost:3978/tou>`

<details>
<summary><b>Exibir o código-fonte</b></summary>

#### <a name="startupcs"></a>Startup.cs

Este projeto foi criado com base em um modelo vazio de aplicativo Web do ASP.NET Core 3.1 com a caixa de seleção **Avançado: configurar para HTTPS** marcada na instalação. Os serviços MVC são registrados pelo método `ConfigureServices()` da estrutura de injeção de dependência. Além disso, o modelo vazio não habilita o fornecimento de conteúdo estático por padrão, portanto, o middleware de arquivos estáticos é adicionado ao método `Configure()` usando o seguinte código:

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

Esta pasta contém os seguintes arquivos de pacote de aplicativos necessários:

* Um **ícone de cor completo** medindo 192 x 192 pixels.
* Um **ícone transparente de contorno** medindo 32 x 32 pixels.
* Um arquivo `manifest.json` que especifica os atributos do seu aplicativo.

Esses arquivos devem ser compactados em um pacote de aplicativos para uso no carregamento de sua guia para o Teams. O Teams carrega o `contentUrl` especificado no manifesto, insere-o em um IFrame e renderiza-o em sua guia.

#### <a name="csproj"></a>.csproj

No Gerenciador de Soluções do Visual Studio, clique com o botão direito do mouse no projeto e selecione **Editar arquivo de projeto**. No final do arquivo, você verá o seguinte código que cria e atualiza sua pasta zip quando o aplicativo é compilado:

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

**PersonalTab.cs** apresenta um objeto de mensagem e métodos que são chamados do **PersonalTabController** quando um usuário seleciona um botão no modo de exibição **PersonalTab**.

#### <a name="views"></a>Visualizações

Essas exibições são as diferentes exibições ASP.NET Core MVC:

* ASP.NET Core trata arquivos chamados **Índice** como o padrão ou página inicial para o site. Quando a URL do navegador aponta para a raiz do site,**index.cshtml** é exibido como o página inicial para seu aplicativo.

* Compartilhado: a marcação de exibição parcial **_Layout.cshtml** contém a estrutura de página geral do aplicativo e os elementos visuais compartilhados. Ele também faz referência à Biblioteca do Teams.

#### <a name="controllers"></a>Controladores

Os controladores usam a propriedade `ViewBag` para transferir valores dinamicamente para as Exibições.

</details>

### <a name="update-and-run-your-application"></a>Atualizar e executar seu aplicativo

1. Abra Gerenciador de Soluções do Visual Studio, vá para a pasta **Páginas** > **Compartilhada**, abra **_Layout.cshtml** e adicione o seguinte à seção `<head>` marcas:

    ```HTML
    <script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
    <script src="https://res.cdn.office.net/teams-js/2.0.0/js/MicrosoftTeams.min.js" integrity="sha384-QtTBFeFlfRDZBfwHJHYQp7MdLJ2C3sfAEB1Qpy+YblvjavBye+q87TELpTnvlXw4" crossorigin="anonymous"></script>
    ```

1. No Gerenciador de Soluções do Visual Studio, abra **PersonalTab.cshtml** da pasta **Visualizações** > **PersonalTab** e adicione `app.initialize()` nas marcas `<script>` e salve.

1. No Visual Studio, selecione **F5** ou escolha **Iniciar Depuração** no menu **Depuração** do aplicativo para verificar se o aplicativo foi carregado corretamente.

### <a name="establish-a-secure-tunnel-to-your-tab"></a>Estabelecer um túnel seguro para sua guia

No prompt de comando na raiz do diretório do projeto, execute o seguinte comando para estabelecer um túnel seguro para sua guia:

```cmd
ngrok http 3978 --host-header=localhost
```

### <a name="update-your-app-package-with-developer-portal"></a>Atualize seu pacote de aplicativos com o Portal do Desenvolvedor

1. Vá para [**Portal do Desenvolvimento**](https://dev.teams.microsoft.com/home).

1. Abra **Aplicativos** e selecione **Importar aplicativo**.

1. O nome do pacote do aplicativo é **tab.zip**. Ele está disponível no seguinte caminho:

    ```
    /bin/Debug/netcoreapp3.1/tab.zip
    ```

1. Selecione **tab.zip** e abra-o no Portal do Desenvolvedor.

1. Uma **ID de aplicativo padrão** é criada e preenchida na seção **Informações básicas**.

1. Adicione a descrição Curta e Longa para seu aplicativo em **Descrições**.

1. Em **Informações do desenvolvedor**, adicione os detalhes necessários e, no site do **(deve ser uma URL HTTPS válida),** forneça sua URL HTTPS ngrok.

1. Em **urls de aplicativo**, atualize a política de privacidade para `https://<yourngrokurl>/privacy` e Termos de uso para `https://<yourngrokurl>/tou` e salvar.

1. Em **Recursos do aplicativo**, selecione **Aplicativo pessoal** > **Criar sua primeira guia de aplicativo pessoal** e insira o Nome e atualize a **URL de Conteúdo** com `https://<yourngrokurl>/personalTab`. Deixe o campo URL do Site em branco e selecione **Contexto** como personalTab na lista suspensa e **Adicionar**.

1. Selecione **Salvar**.

1. Na seção Domínios, os domínios de suas guias devem conter sua URL ngrok sem o prefixo HTTPS `<yourngrokurl>.ngrok.io`.

### <a name="preview-your-app-in-teams"></a>Visualizar seu aplicativo no Teams

1. Selecione **Visualização no Teams** na barra de ferramentas Portal do Desenvolvedor, Portal do Desenvolvedor informa que seu aplicativo foi carregado com êxito. A página **Adicionar** é exibida para seu aplicativo no Teams.

1. Selecione **Adicionar** para carregar a guia no Teams. Sua guia agora está disponível no Teams.

    :::image type="content" source="~/assets/images/tab-images/personaltabaspnetmvccoreuploaded.png" alt-text="Guia pessoal":::
  
   Agora você criou e adicionou com êxito sua guia pessoal no Teams.

   Como você tem sua guia pessoal no Teams, você também pode [reordenar](#reorder-static-personal-tabs) sua guia pessoal.

::: zone-end

## <a name="reorder-static-personal-tabs"></a>Reordenar guias pessoais estáticas

A partir da versão 1.7 do manifesto, os desenvolvedores podem reorganizar todas as guias em seu aplicativo pessoal. Em particular, um desenvolvedor pode mover a guia **chat do bot**, que sempre usa como padrão a primeira posição, em qualquer lugar no cabeçalho da guia do aplicativo pessoal. Duas palavras-chave da guia reservada `entityId` são reservadas, **conversas** e **sobre**.

Se você criar um bot com um escopo **pessoal**, ele aparecerá na primeira posição da guia em um aplicativo pessoal por padrão. Se você quiser movê-lo para outra posição, deverá adicionar um objeto de guia estático ao manifesto com a palavra-chave reservada, **conversas**. A guia **conversa** aparece na Web ou na área de trabalho, dependendo de onde você adiciona a guia **conversa** na matriz `staticTabs`.

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

* [Guias do Teams](~/tabs/what-are-tabs.md)
* [Guias em dispositivos móveis](~/tabs/design/tabs-mobile.md)
* [Criar guias com Cartões Adaptáveis](~/tabs/how-to/build-adaptive-card-tabs.md)
* [Criar abas para conversação](~/tabs/how-to/conversational-tabs.md)
* [Compartilhar com o Teams a partir do aplicativo ou guia pessoal](~/concepts/build-and-test/share-to-teams-from-personal-app-or-tab.md)
