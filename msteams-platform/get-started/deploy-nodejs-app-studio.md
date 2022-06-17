---
title: Implantar seu primeiro aplicativo usando Node.js no App Studio
description: Saiba como implantar aplicativos Microsoft Teams com Node.js no App Studio
keywords: introdução ao node.js app studio
ms.custom: scenarios:getting-started; languages:ASP,Node.js
ms.localizationpriority: medium
ms.topic: tutorial
ms.date: 11/09/2018
ms.openlocfilehash: 15b5837fb8155d8b34b2c337a550ecbaaae9d86a
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66142518"
---
# <a name="update-nodejs-app-package-in-app-studio"></a>Atualizar Node.js pacote do aplicativo no App Studio

> [!TIP]
> **Experimente o Portal do Desenvolvedor**: o App Studio evoluiu. Configure, distribua e gerencie seus aplicativos do Teams com o novo [Portal do Desenvolvedor](https://dev.teams.microsoft.com/).

O App Studio é um Teams aplicativo que você pode instalar da Teams armazenamento. Ele simplifica a criação e o registro de um aplicativo.

Conclua as seguintes etapas para atualizar o pacote do aplicativo:

1. Para instalar o App Studio no Teams, selecione o ícone aplicativos na parte inferior da barra esquerda e pesquise o **App Studio**:

    <img  width="450px" alt="Finding App Studio in the Store View" src="~/assets/images/get-started/searchforAppStudio.png"/>

1. Selecione o **bloco do App Studio** e escolha **Instalar**. O App Studio está instalado:

    <img  width="450px" alt="Installing App Studio" src="~/assets/images/get-started/InstallingAppStudio.png"/>

1. Para criar o pacote de aplicativos para seu Teams, selecione a guia **Editor de manifesto** no **App Studio**:

    <img  width="450px" alt="App Studio" src="~/assets/images/get-started/AppStudio.png"/>

    O exemplo vem com seu próprio manifesto e foi projetado para criar um pacote de aplicativos quando o projeto é compilado. No Node.js, isso é feito digitando `gulp` na linha de comando no diretório raiz do projeto.

    Você pode criar o pacote do aplicativo Node.js digitando `gulp` na linha de comando no diretório raiz do projeto.

    ```bash
    $ gulp
    [13:39:27] Using gulpfile ~\documents\github\msteams-samples-hello-world-nodejs\gulpfile.js
    [13:39:27] Starting 'clean'...
    [13:39:27] Starting 'generate-manifest'...
    [13:39:27] Finished 'generate-manifest' after 11 ms
    [13:39:27] Finished 'clean' after 21 ms
    [13:39:27] Starting 'default'...
    Build completed. Output in manifest folder
    [13:39:27] Finished 'default' after 62 μs
    ```

    O nome do pacote do aplicativo gerado é `helloworldapp.zip`. Você poderá pesquisar esse arquivo se o local não estiver claro na ferramenta que você está usando.

1. Agora, para modificar esse pacote de aplicativos, selecione **Importar um aplicativo existente** no **editor de manifesto**:

    <img  width="450px" alt="Importing an existing app" src="~/assets/images/get-started/Importinganapp.png"/>

1. Selecione o **Olá, Mundo** para seu aplicativo recém-importado:

    <img  width="450px" alt="Newly imported app view" src="~/assets/images/get-started/HelloWorldappdetails.png"/>

    A imagem a seguir mostra o pacote do aplicativo importado no App Studio:

    <img  width="450px" alt="Importing the app package" src="~/assets/images/get-started/Importinganapp2.png"/>

    No lado esquerdo do editor de manifesto, há uma lista de etapas. No lado direito, há uma lista de propriedades que precisam ser preenchidas para cada etapa. Conforme você começou com um aplicativo de exemplo, grande parte das informações já está concluída. As próximas etapas permitem que você atualize as propriedades do Olá, Mundo aplicativo.

## <a name="app-details"></a>Detalhes do aplicativo

Selecione **Detalhes do aplicativo** em **Detalhes**. Selecione o **botão Gerar** para criar uma nova ID do aplicativo.

Sua nova ID do aplicativo é semelhante a `2322041b-72bf-459d-b107-f4f335bc35bd`.

Veja os detalhes do aplicativo no painel direito, incluindo informações **do desenvolvedor** e **detalhes de identidade visual** . Esses detalhes serão importantes se você estiver escrevendo um novo aplicativo para distribuição.

## <a name="tabs"></a>Guias

É simples adicionar guias a um Teams aplicativo. O aplicativo de exemplo já dá suporte a várias guias e você pode habilita-las.

### <a name="team-tab"></a>Guia Equipe

Seu aplicativo só pode ter uma guia Equipe:

<img  width="450px" alt="Adding a Teams tab" src="~/assets/images/get-started/TeamTab.png"/>

Neste exemplo, a guia Equipe é onde sua página de configuração é exibida. Selecione o **símbolo ...** da **URL de configuração da guia** e escolha **Editar** no menu suspenso. Altere a URL para `https://yourteamsapp.ngrok.io/configure` onde `yourteamsapp.ngrok.io` deve ser substituída pela URL que você usou ao hospedar seu aplicativo.

### <a name="personal-tabs"></a>Guias pessoais

Seu aplicativo pode ter até 16 guias, incluindo a guia Equipe.

As guias pessoais são diferentes da guia Equipe. **A guia Olá** já está listada na lista de guias pessoais com um valor de espaço reservado `com.contoso.helloworld.hellotab`. Selecione o **símbolo ...** da **URL de configuração da guia** e escolha **Editar** no menu suspenso. A caixa de diálogo a seguir é exibida:

<img  width="450px" alt="Adding a personal tab dialog" src="~/assets/images/get-started/PersonalTab.png"/>

Atualize as caixas a seguir com a URL do aplicativo:

* Alterar a **caixa URL de** Conteúdo para `https://yourteamsapp.ngrok.io/hello`
* Alterar a **caixa url do** site para `https://yourteamsapp.ngrok.io/hello`

Substitua `yourteamsapp.ngrok.io` pela URL que você usou ao hospedar seu aplicativo.

#### <a name="bots"></a>Bots

É fácil adicionar a funcionalidade de bots ao seu aplicativo. O **Olá, Mundo** de exemplo já tem um bot como parte do exemplo, mas você deve registrá-lo na Microsoft:

<img  width="450px" alt="Adding a bot" src="~/assets/images/get-started/Bots.png"/>

O bot que foi importado do exemplo não tem uma ID de aplicativo associada. Você deve criar um bot para que o App Studio possa criar uma nova ID do aplicativo e registrá-la na Microsoft.

> [!NOTE]
> A ID do Aplicativo criada pelo App Studio para o bot é diferente da ID do Aplicativo criada para o aplicativo. Cada bot em um aplicativo requer sua própria ID do aplicativo.

Conclua as seguintes etapas para configurar o bot:

1. Selecione **Excluir** ao lado do bot importado na lista de bots. Agora não há bots a serem mostrados.
1. Selecione **Configurar** para exibir **a caixa de diálogo Configurar um bot** .

    <img  width="450px" alt="Adding a bot dialog" src="~/assets/images/get-started/Setupbot.png"/>

1. Adicione um bot **contoso de nome de bot** e marque todas as três caixas de seleção em **Escopo**.
1. Escolha **Salvar** para sair da caixa de diálogo. O App Studio registra seu bot com a Microsoft e exibe seu novo bot na lista de bots.
1. Agora, abra um arquivo de texto no bloco de notas e copie e cole sua nova ID de bot nele.
1. Clique **em Gerar Nova Senha** e anote a senha no mesmo arquivo de texto que você anotou a ID do aplicativo do bot.
1. Atualize **o endereço do ponto de extremidade do** `https://yourteamsapp.ngrok.io/api/messages`Bot para e `yourteamsapp.ngrok.io` substitua pela URL que você usou ao hospedar seu aplicativo.
1. Agora, salve o arquivo de texto, pois você deve adicionar as informações do arquivo ao seu aplicativo hospedado para permitir a comunicação segura com o bot.

#### <a name="messaging-extensions"></a>Extensões de mensagens

As extensões de mensagens permitem que os usuários solicitem informações do seu serviço e postem essas informações. As informações são postadas na forma de cartões na conversa do canal. As extensões de mensagens aparecem na parte inferior da caixa de redação.

Conclua as seguintes etapas para configurar sua extensão de mensagens:

1. Selecione **extensões de Mensagens** em **Funcionalidades** no painel esquerdo do App Studio para configurar a extensão de mensagens:

    <img  width="450px" alt="Adding a messaging extension" src="~/assets/images/get-started/Messagingextensions.png"/>

    A extensão de mensagens de exemplo é listada no painel **Extensões de** Mensagens.

1. Selecione **Excluir** para remover a extensão de mensagens, selecione **Configurar** e siga as mesmas etapas [usadas para bots](#bots). A **caixa de diálogo Extensão** de Mensagens é exibida.
1. Selecione **a guia Usar bot existente** **e selecione em um dos meus bots existentes**.
1. Selecione o bot que você criou no menu suspenso. Adicione um **nome de Bot** e selecione **Salvar** para fechar a caixa de diálogo.
1. Na seção **Comando** , selecione **Adicionar**. Para adicionar um comando baseado em pesquisa, selecione Permitir que os usuários consultem seu serviço para obter informações e **insira-os em uma opção de** mensagem.
1. Na caixa **de diálogo Novo** comando, insira os seguintes valores:

    Em **Novo comando**:

    * **ID do comando**: inserir texto aleatório
    * **Título**: Inserir título aleatório
    * **Descrição**: insira a descrição aleatória

    Em **Parâmetro**:

    * **Nome**: insira o nome do parâmetro
    * **Título**: Insira o título do cartão
    * **Descrição**: insira a descrição do cartão

1. Depois de inserir as informações, selecione **Salvar** para fechar a caixa de diálogo.

#### <a name="register-your-app-in-teams"></a>Registre seu aplicativo no Teams

Depois de inserir os detalhes do aplicativo, conclua as seguintes etapas para registrar seu aplicativo Teams:

1. Use **Testar e distribuir** o App Studio para instalar seu aplicativo no Teams.
1. Atualize seu aplicativo hospedado com a ID do aplicativo e a senha do bot. Para o aplicativo de exemplo, use a mesma ID do aplicativo e a mesma senha para o bot e a extensão de mensagens.
1. Selecione **Testar e distribuir**  em **Concluir** no painel esquerdo do App Studio:

    <img  width="450px" alt="Testing your app" src="~/assets/images/get-started/Testanddistribute.png"/>

1. Para carregar seu aplicativo no Teams, selecione o **botão** Instalar em **Testar e Distribuir**:

    <img  width="450px" alt="Adding a messaging extension dialog" src="~/assets/images/get-started/InstallingHelloWorld.png"/>

    > [!NOTE]
    > Se não for possível realizar o sideload do aplicativo, verifique se você [habilitou o carregamento de aplicativo personalizado](../get-started/get-started-dotnet-app-studio.md#enable-sideloading-option).

1. Selecione a **caixa Pesquisar** na **seção Adicionar a uma equipe** e selecione uma equipe para adicionar o aplicativo de exemplo. Você pode configurar uma equipe especial para teste.
1. Selecione o **botão** Instalar na parte inferior da caixa de diálogo.

    Seu aplicativo agora está disponível no Teams. No entanto, o bot e a extensão de mensagens não funcionarão até que você atualize o ambiente de aplicativos hospedados com as IDs e senhas do aplicativo.

    <img  width="450px" alt="The finished app" src="~/assets/images/get-started/Finishedhelloworld.png"/>

## <a name="update-the-credentials-for-your-hosted-app"></a>Atualizar as credenciais do aplicativo hospedado

O aplicativo de exemplo requer que as seguintes variáveis de ambiente sejam definidas com os valores que você anotou anteriormente:

```
MICROSOFT_APP_ID=<YOUR BOT'S APP ID>
MICROSOFT_APP_PASSWORD=<YOUR BOT'S PASSWORD>
WEBSITE_NODE_DEFAULT_VERSION=8.9.4
```

As variáveis de ambiente fazem parte do seu ambiente. Somente o código do aplicativo pode accessá-los. Eles não são expostos a terceiros.

Se você estiver executando o aplicativo usando o ngrok, precisará configurar variáveis de ambiente locais. Você pode usar o Visual Studio Code para adicionar uma [configuração de inicialização](https://code.visualstudio.com/Docs/editor/debugging#_launch-configurations):

```json
{
    "type": "node",
    "request": "launch",
    "name": "Launch - Teams Debug",
    "program": "${workspaceRoot}/src/app.js",
    "cwd": "${workspaceFolder}/src",
    "env": {
        "BASE_URI": "https://yourNgrokURL.ngrok.io",
        "MICROSOFT_APP_ID": "00000000-0000-0000-0000-000000000000",
        "MICROSOFT_APP_PASSWORD": "yourBotAppPassword",
        "NODE_DEBUG": "botbuilder",
        "SUPPRESS_NO_CONFIG_WARNING": "y",
        "NODE_CONFIG_DIR": "../config"
    }
}
```

Onde:

* As credenciais de autorização para o bot são as seguintes:
  * MICROSOFT_APP_ID é a ID.
  * MICROSOFT_APP_PASSWORD é senha.
* NODE_DEBUG mostrar o que está acontecendo no bot no console Visual Studio Code depuração
* NODE_CONFIG_DIR aponta para o diretório na raiz do repositório (por padrão, quando o aplicativo é executado localmente, ele procura o diretório raiz na `src` pasta).

> [!Note]
> Se você não parou de npm anteriormente no tutorial, `npm stop` será necessário executar para que Visual Studio Code suas variáveis de configuração de inicialização corretamente.

<a name="ConfigureTheAppTab"></a>

## <a name="test-the-app-capabilities-in-teams"></a>Testar os recursos do aplicativo Teams

Depois de instalar o aplicativo no Teams, você precisará configurá-lo para mostrar o conteúdo.

### <a name="test-your-tab-in-teams"></a>Testar sua guia no Teams

1. Vá para um canal no Teams e selecione o botão **'+'** para adicionar uma nova guia.
1. Em seguida, você pode `Hello World` escolher na **lista Adicionar uma** guia.
1. Na caixa de diálogo de configuração, selecione a guia que você deseja exibir no canal. Em seguida, selecione **Salvar**.

Você pode ver a `Hello World` guia carregada com a guia escolhida:

<img width="430px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png"/>

### <a name="test-your-bot-in-teams"></a>Testar seu bot no Teams

Agora você pode interagir com o bot Teams. Escolha um canal na equipe em que você registrou seu aplicativo e digite `@your-bot-name`, seguido por sua mensagem. Esse tipo de mensagem é chamado de **menção\@**. Qualquer mensagem que você enviar para o bot será enviada de volta como uma resposta:

<img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png"/>

<a name="ComposeRichMessages"></a>

### <a name="test-your-messaging-extension"></a>Testar sua extensão de mensagens

Para testar sua extensão de mensagens:

1. Selecione os três pontos abaixo da caixa de entrada no modo de exibição de conversa. Um menu com o **aplicativo "Olá, Mundo"** é exibido.
1. Selecione o menu. Um conjunto de textos aleatórios é exibido. Você pode selecionar um dos textos aleatórios e que é inserido em sua conversa.

    <img width="430px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu1.png" />

    <img width="430px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result1.png" />

1. Selecione um dos textos aleatórios. O cartão formatado aparece pronto para ser enviado com sua própria mensagem incluída na parte inferior:

    <img width="430px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />

| &nbsp; | &nbsp; |
|:--- | ---:|
|[Back](get-started-overview.md) | &nbsp; |
|
