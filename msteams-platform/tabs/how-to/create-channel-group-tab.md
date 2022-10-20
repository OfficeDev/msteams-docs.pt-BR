---
title: Criar uma guia de canal ou guia de grupo
author: laujan
description: Criar canal personalizado, guia agrupar com Node.js, ASP.NET Core, ASP.NET Core MVC. Gerar aplicativo, criar pacote, compilar e executar aplicativo, túnel secreto, carregar no Teams
ms.localizationpriority: high
ms.topic: quickstart
ms.author: lajanuar
zone_pivot_groups: teams-app-environment
ms.openlocfilehash: c21be77b03bf99224467213a4c257635388c57eb
ms.sourcegitcommit: 40d4bde10b6820c62e49e2400b10ab3569c8c815
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68615237"
---
# <a name="create-a-channel-tab-or-group-tab"></a>Criar uma guia de canal ou guia de grupo

As guias de canal ou grupo fornecem conteúdo para canais e chats em grupo, o que ajuda a criar espaços colaborativos em torno de conteúdo dedicado baseado na Web.

Verifique se você tem todos os [pré-requisitos para](~/tabs/how-to/tab-requirements.md) criar a guia canal ou grupo.

[!INCLUDE [sdk-include](~/includes/sdk-include.md)]

::: zone pivot="node-java-script"

## <a name="create-a-custom-channel-or-group-tab-with-nodejs"></a>Criar um canal personalizado ou guia de grupo com Node.js

1. No prompt de comando, instale os pacotes [Yeoman](https://yeoman.io/) e [gulp-cli](https://www.npmjs.com/package/gulp-cli) inserindo o seguinte comando após a instalação do **Node.js**:

    ```cmd
    npm install yo gulp-cli --global
    ```

2. No prompt de comando, instale o gerador de aplicativos do Microsoft Teams inserindo o seguinte comando:

    ```cmd
    npm install generator-teams --global
    ```

A seguir estão as etapas para criar uma guia de canal ou grupo:

* [Gerar seu aplicativo com uma guia de canal ou grupo](#generate-your-application-with-a-channel-or-group-tab)
* [Criar um pacote do aplicativo](#create-your-app-package)
* [Criar e executar o aplicativo](#build-and-run-your-application)
* [Estabelecer um túnel seguro para sua guia](#establish-a-secure-tunnel-to-your-tab)
* [Carregar seu aplicativo para o Teams](#upload-your-application-to-teams)

### <a name="generate-your-application-with-a-channel-or-group-tab"></a>Gerar seu aplicativo com uma guia de canal ou grupo

1. No prompt de comando, crie um novo diretório para seu canal ou guia de grupo.

1. Insira o seguinte comando em seu novo diretório para iniciar o gerador de aplicativos do Microsoft Teams:

    ```cmd
    yo teams
    ```

1. Forneça seus valores para uma série de perguntas solicitadas pelo gerador de aplicativos do Microsoft Teams para atualizar o `manifest.json` arquivo:

    ![captura de tela de abertura do gerador](/microsoftteams/platform/assets/images/tab-images/teamsTabScreenshot.PNG)

    <details>
    <summary><b>Série de perguntas para atualizar seu arquivo manifest.json</b></summary>

    * **Qual é o nome da solução?**

        O nome da solução é o nome do projeto. Você pode aceitar o nome sugerido selecionando **Enter**.

    * **Onde você deseja colocar os arquivos?**

        No momento, você está no diretório do projeto. Selecione **Enter**.

    * **Título do seu projeto de aplicativo Microsoft Teams?**

        O título é o nome do pacote do aplicativo e é usado no manifesto e na descrição do aplicativo. Insira um título ou selecione **Enter** para aceitar o nome padrão.

    * **O nome da sua (empresa)? (máximo de 32 caracteres)**

        O nome da empresa pode ser usado no manifesto do aplicativo. Insira um nome para a empresa ou selecione **Enter** para aceitar o nome padrão.

    * **Qual versão do manifesto você gostaria de usar?**

        Selecione o esquema padrão.

    * **Scaffolding rápido? (S/N)**

        O padrão é sim; insira **n** para inserir sua ID de Parceiro da Microsoft.

    * **Inserir sua ID de Parceiro da Microsoft, se tiver uma?: (Deixe em branco para ignorar)**

        Este campo não é obrigatório e deve ser usado somente se você já faz parte do [Microsoft Partner Network](https://partner.microsoft.com).

    * **Quais recursos você deseja adicionar ao seu projeto?**

        Selecione **( &ast; ) uma guia**.

    * **A URL para hospedar essa solução?**

        Por padrão, o gerador sugere uma URL do site do Azure. Você só está testando seu aplicativo localmente, portanto, uma URL válida não é necessária.

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

        Use as teclas de direção para selecionar a guia **Configurável**.

    * **Quais escopos você pretende usar na sua guia?**

        Você pode selecionar uma equipe ou um chat em grupo.

    * **Deseja exigir o suporte ao logon único do Microsoft Azure Active Directory (Azure AD) para a guia?**

        Escolha **não** para incluir o suporte de logon único do Microsoft Azure Active Directory (Azure AD) à guia. O padrão é sim, insira **n**.

    * **Deseja que esta guia seja disponibilizada no SharePoint Online? (s/n)** 

        Insira **n**.

    </details>

> [!IMPORTANT]
> O componente de caminho **DefaultTabNameTab** é o valor que você inseriu no gerador para **Nome da guia padrão** mais a palavra **Guia**. Por exemplo, `DefaultTabName` é **myTab** depois **/MyTabTab/**

<!--- TBD: this info seems removed from the main branch.
* A **full color icon** measuring 192 x 192 pixels.
* A **transparent outline icon** measuring 32 x 32 pixels.
* A `manifest.json` file that specifies the attributes of your app.
--->

### <a name="create-your-app-package"></a>Criar um pacote do aplicativo

Você deve ter um pacote de aplicativos para compilar e executar seu aplicativo no Teams. O pacote do aplicativo é criado por meio de uma tarefa gulp que valida o arquivo `manifest.json` e gera a pasta zip no diretório `./package`. No prompt de comando, digite o seguinte comando:

```cmd
gulp manifest
```

### <a name="build-and-run-your-application"></a>Compilar e executar seu aplicativo

#### <a name="build-your-application"></a>Compilar seu aplicativo

Insira o seguinte comando no prompt de comando para transcompilar sua solução para a pasta `./dist`:

```cmd
gulp build
```

#### <a name="run-your-application"></a>Executar seu aplicativo

1. No prompt de comando, insira o seguinte comando para iniciar um servidor Web local:

    ```bash
    gulp serve
    ```

1. Insira `http://localhost:3007/<yourDefaultAppNameTab>/` em seu navegador para exibir a página inicila do seu aplicativo.

    :::image type="content" source="~/assets/images/tab-images/homePage.png" alt-text="Guia padrão":::

1. Para exibir a página de configuração da guia, vá para `http://localhost:3007/<yourDefaultAppNameTab>/config.html`.

    :::image type="content" source="~/assets/images/tab-images/configurationPage.png" alt-text="Página de configuração da guia":::

### <a name="establish-a-secure-tunnel-to-your-tab"></a>Estabelecer um túnel seguro para sua guia

Para estabelecer um túnel seguro para sua guia, saia do localhost e insira o seguinte comando:

```cmd
gulp ngrok-serve
```

> [!IMPORTANT]
> Depois que sua guia for carregada para o Microsoft Teams por meio do **ngrok** e salva com êxito, você poderá exibi-la no Teams até que a sessão de túnel termine. Se você reiniciar sua sessão ngrok, deverá atualizar seu aplicativo com a nova URL.

### <a name="upload-your-application-to-teams"></a>Carregar seu aplicativo no Teams

1. Vá para o Teams e selecione **Aplicativos**&nbsp;:::image type="content" source="~/assets/images/tab-images/store.png" alt-text="Loja do Teams":::.
1. Selecione **Gerenciar seus aplicativos** > **Carregar um aplicativo** > **Carregar um aplicativo personalizado**.
1. Vá para o diretório do projeto, navegue até a pasta **./package**, selecione a pasta zip do pacote de aplicativo e escolha **Abrir**.

    :::image type="content" source="~/assets/images/tab-images/channeltabadded.png" alt-text="Guia de canal carregada":::

1. Selecione **Adicionar** na caixa de diálogo. Sua guia é carregada no Teams.

    > [!NOTE]
    > Se  **Adicionar** não for exibido na caixa de diálogo, remova o código a seguir do manifesto da pasta zip do pacote do aplicativo carregado. Compacte novamente a pasta e carregue-a no Teams.
    >
    >```Json
    >"staticTabs": [],
    >"bots": [],
    >"connectors": [],
    >"composeExtensions": [],
    >```

1. Siga as instruções para adicionar uma guia. Há uma caixa de diálogo de configuração personalizada para seu canal ou guia de grupo.
1. Selecione **Salvar** e sua guia será adicionada à barra de guias do canal.

    :::image type="content" source="~/assets/images/tab-images/channeltabuploaded.png" alt-text="Guia de canal carregada":::

    Agora você criou e adicionou com êxito seu canal ou guia de grupo no Teams.

::: zone-end

::: zone pivot="razor-csharp"

## <a name="create-a-custom-channel-or-group-tab-with-aspnet-core"></a>Criar um canal personalizado ou uma guia de grupo com ASP.NET Core

1. No prompt de comando, crie um novo diretório para o projeto de guia.

1. Clone o repositório de exemplo em seu novo diretório usando o comando a seguir ou você pode baixar o [código-fonte](https://github.com/OfficeDev/Microsoft-Teams-Samples) e extrair os arquivos:

    ```cmd
    git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
    ```

A seguir estão as etapas para criar uma guia de canal ou grupo:

* [Gerar seu aplicativo com uma guia de canal ou grupo](#generate-your-application-with-a-channel-or-group-tab-1)
* [Estabelecer um túnel seguro para sua guia](#establish-a-secure-tunnel-to-your-tab-1)
* [Atualizar seu aplicativo](#update-your-application)
* [Criar e executar o aplicativo](#build-and-run-your-application-1)
* [Atualizar o pacote do aplicativo com Portal do Desenvolvedor](#update-your-app-package-with-developer-portal)
* [Pré-visualizar seu aplicativo no Teams](#preview-your-app-in-teams)

### <a name="generate-your-application-with-a-channel-or-group-tab"></a>Gerar seu aplicativo com uma guia de canal ou grupo

1. Abra o Visual Studio e selecione **Abrir um projeto ou solução**.

1. Vá para a pasta **Microsoft-Teams-Samples** > **samples** > **tab-channel-group** > **razor-csharp** e abra **channelGroupTab.sln**.

1. No Visual Studio, selecione **F5** ou escolha **Iniciar Depuração** no menu de **Depuração** do aplicativo para verificar se o aplicativo foi carregado corretamente. Em um navegador, vá para as seguintes URLs:

    * `https://localhost:3978/`
    * `https://localhost:3978/privacy`
    * `https://localhost:3978/tou`

<details>
<summary><b>Exibir o código-fonte</b></summary>

#### <a name="startupcs"></a>Startup.cs

Este projeto foi criado com base em um modelo vazio de aplicativo Web do ASP.NET Core 3.1 com a caixa de seleção **Avançado: configurar para HTTPS** marcada na instalação. Os serviços MVC são registrados pelo método `ConfigureServices()` da estrutura de injeção de dependência. Além disso, o modelo vazio não habilita o fornecimento de conteúdo estático por padrão, portanto, o middleware de arquivos estáticos é adicionado ao método `Configure()` usando o seguinte código:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc(options => options.EnableEndpointRouting = false);
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

#### <a name="tabcs"></a>Tab.cs

Esse arquivo C# contém um método que é chamado de **Tab.cshtml** durante a configuração.

#### <a name="appmanifest-folder"></a>Pasta AppManifest

Esta pasta contém os seguintes arquivos de pacote de aplicativos necessários:

* Um **ícone de cor completo** medindo 192 x 192 pixels.
* Um **ícone transparente de contorno** medindo 32 x 32 pixels.
* Um arquivo `manifest.json` que especifica os atributos do seu aplicativo.

Esses arquivos precisam ser compactados em um pacote de aplicativos para uso no carregamento de sua guia para o Teams. Quando um usuário opta por adicionar ou atualizar sua guia, o Teams `configurationUrl` carrega o especificado em seu manifesto, insere-o em um IFrame e o renderiza em sua guia.

#### <a name="csproj"></a>.csproj

Na janela do Gerenciador de Soluções do Visual Studio, clique com o botão direito do mouse no projeto e selecione **Editar arquivo de projeto**. No final do arquivo, você verá o seguinte código que cria e atualiza sua pasta zip quando o aplicativo é compilado:

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

Certifique-se de manter o prompt de comando com ngrok em execução e anote a URL.

### <a name="update-your-application"></a>Atualizar seu aplicativo

1. Abra Gerenciador de Soluções do Visual Studio, vá para a pasta **Páginas** > **Compartilhadas**, abra **_Layout.cshtml** e adicione o seguinte à <head> seção de marcas:

    ```html
    <script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
    <script src="https://res.cdn.office.net/teams-js/2.2.0/js/MicrosoftTeams.min.js" 
      integrity="sha384yBjE++eHeBPzIg+IKl9OHFqMbSdrzY2S/LW3qeitc5vqXewEYRWegByWzBN/chRh" 
      crossorigin="anonymous" >
    </script>
    ```

    > [!IMPORTANT]
    > Não copie e cole as URLs `<script src="...">` desta página, pois elas não representam a versão mais recente. Para obter a versão mais recente do SDK, acesse sempre a[API JavaScript do Microsoft Teams](https://www.npmjs.com/package/@microsoft/teams-js).

1. Insira uma chamada para `microsoftTeams.app.initialize();` na marca `script`.

1. No Visual Studio Gerenciador de Soluções, vá para a pasta **Páginas** e abra **Tab.cshtml**

    Em **Tab.cshtml**, o aplicativo apresenta ao usuário duas opções para exibir a guia com um ícone vermelho ou cinza. O **botão Selecionar Cinza** **ou Selecionar Vermelho** `saveGray()` `saveRed()` dispara ou, respectivamente, define `pages.config.setValidityState(true)`e habilita **Salvar** na página de configuração. Esse código permite que o Teams saiba que você concluiu a configuração de requisitos e pode continuar com a instalação. Os parâmetros de `pages.config.setConfig` são definidos. Por fim, `saveEvent.notifySuccess()` é chamado para indicar que a URL de conteúdo foi resolvida com êxito.

1. Atualize os valores `websiteUrl` e `contentUrl` em cada função com a URL HTTPS do ngrok para sua guia.

    Seu código agora deve incluir o seguinte com **y8rCgT2b** substituído pela URL do ngrok:

    ```javascript
        
        let saveGray = () => {
            microsoftTeams.pages.config.registerOnSaveHandler((saveEvent) => {
                microsoftTeams.pages.config.setConfig({
                    websiteUrl: `https://y8rCgT2b.ngrok.io`,
                    contentUrl: `https://y8rCgT2b.ngrok.io/gray/`,
                    entityId: "grayIconTab",
                    suggestedDisplayName: "MyNewTab",
                    removeUrl: ""
                });
                saveEvent.notifySuccess();
            });
        }

        let saveRed = () => {
            microsoftTeams.pages.config.registerOnSaveHandler((saveEvent) => {
                microsoftTeams.pages.config.setConfig({
                    websiteUrl: `https://y8rCgT2b.ngrok.io`,
                    contentUrl: `https://y8rCgT2b.ngrok.io/red/`,
                    entityId: "redIconTab",
                    suggestedDisplayName: "MyNewTab",
                    removeUrl: ""
                });
                saveEvent.notifySuccess();
            });
        }
    ```

1. Salve o arquivo **Tab.cshtml**.

### <a name="build-and-run-your-application"></a>Compilar e executar seu aplicativo

1. No Visual Studio, selecione **F5** ou escolha **Iniciar Depuração** no menu **Depuração**.

1. Verifique se **ngrok** está em execução e funcionando corretamente abrindo o navegador e acessando sua página de conteúdo por meio da URL HTTPS do ngrok que foi fornecida na janela do prompt de comando.

    > [!TIP]
    > Você precisa ter seu aplicativo no Visual Studio e ngrok em execução para concluir as etapas fornecidas neste artigo. Se você precisar parar de executar seu aplicativo no Visual Studio para trabalhar nele, **mantenha o ngrok em execução**. Ele escuta e retoma o roteamento da solicitação do aplicativo quando ele é reiniciado no Visual Studio. Se você precisar reiniciar o serviço ngrok, ele retornará uma nova URL e você precisará atualizar seu aplicativo com a nova URL.

<!--- TBD: This note seems to be removed from main. Commenting it for now.
> [!NOTE]
> App Studio can be used to edit your `manifest.json` file and upload the completed package to Teams. You can also manually edit the `manifest.json` file. If you do, ensure that you build the solution again to create the `tab.zip` file to upload.
--->

### <a name="update-your-app-package-with-developer-portal"></a>Atualize seu pacote de aplicativos com o Portal do Desenvolvedor

1. Vá para o Teams. Se você usar [versão baseada na Web](https://teams.microsoft.com), poderá inspecionar seu código front-end usando as [ferramentas de desenvolvedor](~/tabs/how-to/developer-tools.md) do navegador.

1. Vá para [**Portal do Desenvolvimento**](https://dev.teams.microsoft.com/home).

1. Abra **Aplicativos** e selecione **Importar aplicativo**.

<!--- TBD: This steps seems to be removed from main now so commenting it for now.

1. Select **Import an existing app** in the **Manifest editor** to begin updating the app package for your tab. The source code comes with its own partially complete manifest. The name of your app package is `tab.zip`. It is available from the following path:
--->

1. O nome do pacote do aplicativo é `tab.zip`. Ele está disponível no seguinte caminho:

    ```bash
    /bin/Debug/netcoreapp3.1/tab.zip
    ```

1. Selecione `tab.zip` e abra-o no Portal do Desenvolvedor.

1. Uma **ID de aplicativo padrão** é criada e preenchida na seção **Informações básicas**.

1. Adicione a descrição Curta e Longa para seu aplicativo em **Descrições**.

1. Em **Informações do desenvolvedor**, adicione os detalhes necessários e, no site do **(deve ser uma URL HTTPS válida),** forneça sua URL HTTPS ngrok.

1. Em **urls de aplicativo**, atualize a política de privacidade para `https://<yourngrokurl>/privacy` e Termos de uso para `https://<yourngrokurl>/tou` e salvar.

1. Em **Recursos do aplicativo**, selecione **Grupo e aplicativo de canal**. Atualize a **URL de configuração** com `https://<yourngrokurl>/tab` e selecione sua guia **Escopo**.

1. Selecione **Salvar**.

1. Na seção Domínios, os domínios de suas guias devem conter sua URL ngrok sem o prefixo HTTPS `<yourngrokurl>.ngrok.io`.

### <a name="preview-your-app-in-teams"></a>Visualizar seu aplicativo no Teams

1. Selecione **Visualização no Teams** na barra de ferramentas Portal do Desenvolvedor, Portal do Desenvolvedor informa que seu aplicativo foi carregado com êxito. A página **Adicionar** é exibida para seu aplicativo no Teams.

1. Selecione **Adicionar à equipe** para configurar a guia em uma equipe. Configure sua guia e selecione **Salvar**. Sua guia agora está disponível no Teams.

    :::image type="content" source="~/assets/images/tab-images/channeltabaspnetuploaded.png" alt-text="guia Cana dal ASPNET carregada":::

    Agora você criou e adicionou com êxito seu canal ou guia de grupo no Teams.

::: zone-end

::: zone pivot="mvc-csharp"

## <a name="create-a-custom-channel-or-group-tab-with-aspnet-core-mvc"></a>Criar um canal personalizado ou guia de grupo com ASP.NET Core MVC

1. No prompt de comando, crie um novo diretório para o projeto de guia.

1. Clone o repositório de exemplo em seu novo diretório usando o comando a seguir ou você pode baixar o [código-fonte](https://github.com/OfficeDev/Microsoft-Teams-Samples) e extrair os arquivos:

    ```cmd
    git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
    ```

A seguir estão as etapas para criar uma guia de canal ou grupo:

* [Gerar seu aplicativo com uma guia de canal ou grupo](#generate-your-application-with-a-channel-or-group-tab-2)
* [Estabelecer um túnel seguro para sua guia](#establish-a-secure-tunnel-to-your-tab-2)
* [Atualizar seu aplicativo](#update-your-application-1)
* [Criar e executar o aplicativo](#build-and-run-your-application-2)
* [Atualizar o pacote do aplicativo com Portal do Desenvolvedor](#update-your-app-package-with-developer-portal-1)
* [Pré-visualizar seu aplicativo no Teams](#preview-your-app-in-teams-1)

### <a name="generate-your-application-with-a-channel-or-group-tab"></a>Gerar seu aplicativo com uma guia de canal ou grupo

1. Abra o Visual Studio e selecione **Abrir um projeto ou solução**.

1. Vá para a pasta **Microsoft-Teams-Samples** > **samples** > **tab-channel-group** > **mvc-csharp** e abra **ChannelGroupTabMVC.sln**.

1. No Visual Studio, selecione **F5** ou escolha **Iniciar Depuração** no menu de **Depuração** do aplicativo para verificar se o aplicativo foi carregado corretamente. Em um navegador, vá para as seguintes URLs:

    * `https://localhost:3978/`
    * `https://localhost:3978/privacy`
    * `https://localhost:3978/tou`

<details>
<summary><b>Exibir o código-fonte</b></summary>

#### <a name="startupcs"></a>Startup.cs

Este projeto foi criado com base em um modelo vazio de aplicativo Web do ASP.NET Core 3.1 com a caixa de seleção **Avançado: configurar para HTTPS** marcada na instalação. Os serviços MVC são registrados pelo método `ConfigureServices()` da estrutura de injeção de dependência. Além disso, o modelo vazio não habilita o fornecimento de conteúdo estático por padrão, portanto, o middleware de arquivos estáticos é adicionado ao método `Configure()` usando o seguinte código:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc(options => options.EnableEndpointRouting = false);
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

Esses arquivos precisam ser compactados em um pacote de aplicativos para uso no carregamento de sua guia para o Teams.

#### <a name="csproj"></a>.csproj

Na janela do Gerenciador de Soluções do Visual Studio, clique com o botão direito do mouse no projeto e selecione **Editar arquivo de projeto**. No final do arquivo, você verá o seguinte código que cria e atualiza sua pasta zip quando o aplicativo é compilado:

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

**ChannelGroup.cs** apresenta um objeto de mensagem e métodos que podem ser chamados dos controladores durante a configuração.

#### <a name="views"></a>Visualizações

Estas são as diferentes exibições no ASP.NET Core MVC:

* ASP.NET Core trata arquivos chamados **Índice** como o padrão ou página inicial para o site. Quando a URL do navegador aponta para a raiz do site, **Index.cshtml** pode ser exibida como a home page do aplicativo.

* Compartilhado: a marcação de exibição parcial **_Layout.cshtml** contém a estrutura geral da página do aplicativo e os elementos visuais compartilhados que também fazem referência à Biblioteca do Teams.

#### <a name="controllers"></a>Controladores

Os controladores usam a propriedade `ViewBag` para transferir valores dinamicamente para as Exibições.

</details>

### <a name="establish-a-secure-tunnel-to-your-tab"></a>Estabelecer um túnel seguro para sua guia

No prompt de comando na raiz do diretório do projeto, execute o seguinte comando para estabelecer um túnel seguro para sua guia:

```cmd
ngrok http 3978 --host-header=localhost
```

Certifique-se de manter o prompt de comando com ngrok em execução e anote a URL.

### <a name="update-your-application"></a>Atualizar seu aplicativo

1. Abra Gerenciador de Soluções do Visual Studio, vá para a pasta **Visualizações** > **Compartilhadas**, abra **_Layout.cshtml** e adicione o seguinte à <head> seção de marcas:

    ```html
    <script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
    <script src="https://res.cdn.office.net/teams-js/2.2.0/js/MicrosoftTeams.min.js" 
      integrity="sha384yBjE++eHeBPzIg+IKl9OHFqMbSdrzY2S/LW3qeitc5vqXewEYRWegByWzBN/chRh" 
      crossorigin="anonymous" >
    </script>
    ```

    > [!IMPORTANT]
    > Não copie e cole as URLs `<script src="...">` desta página, pois elas não representam a versão mais recente. Para obter a versão mais recente do SDK, acesse sempre a[API JavaScript do Microsoft Teams](https://www.npmjs.com/package/@microsoft/teams-js).

1. Insira uma chamada para `microsoftTeams.app.initialize();` na marca `script`.

1. No Visual Studio Gerenciador de Soluções, vá para a pasta **Tab** e abra **Tab.cshtml**

    Em **Tab.cshtml**, o aplicativo apresenta ao usuário duas opções para exibir a guia com um ícone vermelho ou cinza. O **botão Selecionar Cinza** **ou Selecionar Vermelho** `saveGray()` `saveRed()` dispara ou, respectivamente, define `pages.config.setValidityState(true)`e habilita **Salvar** na página de configuração. Esse código permite que o Teams saiba que você concluiu a configuração de requisitos e pode continuar com a instalação. Os parâmetros de `pages.config.setConfig` são definidos. Por fim, `saveEvent.notifySuccess()` é chamado para indicar que a URL de conteúdo foi resolvida com êxito.

1. Atualize os valores `websiteUrl` e `contentUrl` em cada função com a URL HTTPS do ngrok para sua guia.

    Seu código agora deve incluir o seguinte com **y8rCgT2b** substituído pela URL do ngrok:

    ```javascript

        let saveGray = () => {
            microsoftTeams.pages.config.registerOnSaveHandler((saveEvent) => {
                microsoftTeams.pages.config.setConfig({
                    websiteUrl: `https://y8rCgT2b.ngrok.io`,
                    contentUrl: `https://y8rCgT2b.ngrok.io/gray/`,
                    entityId: "grayIconTab",
                    suggestedDisplayName: "MyNewTab",
                    removeUrl:""
                });
                saveEvent.notifySuccess();
            });
        }
    
        let saveRed = () => {
            microsoftTeams.pages.config.registerOnSaveHandler((saveEvent) => {
                microsoftTeams.pages.config.setConfig({
                    websiteUrl: `https://y8rCgT2b.ngrok.io`,
                    contentUrl: `https://y8rCgT2b.ngrok.io/red/`,
                    entityId: "redIconTab",
                    suggestedDisplayName: "MyNewTab",
                    removeUrl:""
                });
                saveEvent.notifySuccess();
            });
        }
    ```

1. Certifique-se de salvar o **Tab.cshtml** atualizado.

### <a name="build-and-run-your-application"></a>Compilar e executar seu aplicativo

1. No Visual Studio, selecione **F5** ou escolha **Iniciar Depuração** no menu **Depuração**.

1. Verifique se **ngrok** está em execução e funcionando corretamente abrindo o navegador e acessando sua página de conteúdo por meio da URL HTTPS do ngrok que foi fornecida na janela do prompt de comando.

    > [!TIP]
    > Você precisa ter seu aplicativo no Visual Studio e ngrok em execução para concluir as etapas fornecidas neste artigo. Se você precisar parar de executar seu aplicativo no Visual Studio para trabalhar nele, **mantenha o ngrok em execução**. Ele escuta e retoma o roteamento da solicitação do aplicativo quando ele é reiniciado no Visual Studio. Se você precisar reiniciar o serviço ngrok, ele retornará uma nova URL e você precisará atualizar seu aplicativo com a nova URL.

### <a name="update-your-app-package-with-developer-portal"></a>Atualize seu pacote de aplicativos com o Portal do Desenvolvedor

1. Vá para o Teams. Se você usar [versão baseada na Web](https://teams.microsoft.com), poderá inspecionar seu código front-end usando as [ferramentas de desenvolvedor](~/tabs/how-to/developer-tools.md) do navegador.

1. Vá para [**Portal do Desenvolvimento**](https://dev.teams.microsoft.com/home).

1. Abra **Aplicativos** e selecione **Importar aplicativo**.

1. O nome do pacote do aplicativo é **tab.zip**. Ele está disponível no seguinte caminho:

    ```bash
    /bin/Debug/netcoreapp3.1/tab.zip
    ```

1. Selecione **tab.zip** e abra-o no Portal do Desenvolvedor.

1. Uma **ID de aplicativo padrão** é criada e preenchida na seção **Informações básicas**.

1. Adicione a descrição Curta e Longa para seu aplicativo em **Descrições**.

1. Em **Informações do desenvolvedor**, adicione os detalhes necessários e, no site do **(deve ser uma URL HTTPS válida),** forneça sua URL HTTPS ngrok.

1. Em **urls de aplicativo**, atualize a política de privacidade para `https://<yourngrokurl>/privacy` e Termos de uso para `https://<yourngrokurl>/tou` e salvar.

1. Em **Recursos do aplicativo**, selecione **Grupo e aplicativo de canal**. Atualize a **URL de configuração** com `https://<yourngrokurl>/tab` e selecione sua guia **Escopo**.

1. Selecione **Salvar**.

1. Na seção Domínios, os domínios de suas guias devem conter sua URL ngrok sem o prefixo HTTPS `<yourngrokurl>.ngrok.io`.

### <a name="preview-your-app-in-teams"></a>Visualizar seu aplicativo no Teams

1. Selecione **Visualização no Teams** na barra de ferramentas Portal do Desenvolvedor, Portal do Desenvolvedor informa que seu aplicativo foi carregado com êxito. A página **Adicionar** é exibida para seu aplicativo no Teams.

1. Selecione **Adicionar à equipe** para configurar a guia em uma equipe. Configure sua guia e selecione **Salvar**. Sua guia agora está disponível no Teams.

    :::image type="content" source="~/assets/images/tab-images/channeltabaspnetuploaded.png" alt-text="Guia de canal do ASPNET MVC carregado":::

    Agora você criou e adicionou com êxito seu canal ou guia de grupo no Teams.

::: zone-end

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Criar uma página de conteúdo](~/tabs/how-to/create-tab-pages/content-page.md)

## <a name="see-also"></a>Confira também

* [Guias do Teams](~/tabs/what-are-tabs.md)
* [Criar uma guia pessoal](~/tabs/how-to/create-personal-tab.md)
* [Guias em dispositivos móveis](~/tabs/design/tabs-mobile.md)
* [Criar guias com Cartões Adaptáveis](~/tabs/how-to/build-adaptive-card-tabs.md)
* [Criar uma página de remoção](~/tabs/how-to/create-tab-pages/removal-page.md)
* [Adicionar uma página do SharePoint como uma guia no Teams](https://support.microsoft.com/en-us/office/add-a-sharepoint-page-list-or-document-library-as-a-tab-in-teams-131edef1-455f-4c67-a8ce-efa2ebf25f0b)
