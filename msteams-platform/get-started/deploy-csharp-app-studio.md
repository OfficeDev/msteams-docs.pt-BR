---
title: Implantar seu primeiro aplicativo usando C# no App Studio
description: Saiba como implantar aplicativos do Microsoft Teams com C# ou .NET. no App Studio
keywords: getting started .net c# csharp app studio
ms.custom: scenarios:getting-started; languages:ASP.NET,C#
ms.localizationpriority: medium
ms.topic: tutorial
ms.date: 11/09/2018
ms.openlocfilehash: 6fa0b290b0d0918c02427959b96eb897931aa4de
ms.sourcegitcommit: c398dfdae9ed96f12e1401ac7c8d0228ff9c0a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/30/2022
ms.locfileid: "66558454"
---
# <a name="update-c-app-package-in-app-studio"></a>Atualizar o pacote do aplicativo C# no App Studio

> [!TIP]
> **Experimente o Portal do Desenvolvedor**: o App Studio evoluiu. Configure, distribua e gerencie seus aplicativos do Teams com o novo [Portal do Desenvolvedor](https://dev.teams.microsoft.com/).

O App Studio é um aplicativo do Teams que você pode instalar na loja do Teams. Ele simplifica a criação e o registro de um aplicativo.

Conclua as seguintes etapas para atualizar o pacote do aplicativo:

1. Para instalar o App Studio no Teams, selecione  o ícone Aplicativos na parte inferior da barra à esquerda e pesquise **o App Studio**:

    <img  width="450px" alt="Finding App Studio in the Store View" src="~/assets/images/get-started/searchforAppStudio.png"/>

1. Selecione o **bloco do App Studio** e escolha **Instalar**. O App Studio está instalado:

    <img  width="450px" alt="Installing App Studio" src="~/assets/images/get-started/InstallingAppStudio.png"/>

1. Para criar o pacote de aplicativos para seu aplicativo do Teams, selecione a **guia Editor de** manifesto no **App Studio**:

    <img  width="450px" alt="App Studio" src="~/assets/images/get-started/AppStudio.png"/>

    O exemplo vem com seu próprio manifesto e foi projetado para criar um pacote de aplicativos quando o projeto é compilado. O arquivo manifest.json pode estar localizado no Visual Studio no Manifesto em ```Microsoft.Teams.Samples.HelloWorld.Web```.

     No Visual Studio, o arquivo manifest.json está localizado em **Manifesto** em `Microsoft.Teams.Samples.HelloWorld.Web`. Esta etapa é descrita pela seguinte imagem:  

    <img  width="450px" alt="Build the app package on .NET with Visual Studio" src="~/assets/images/get-started/app-package-on-.NET-with-Visual-Studio.png"/>

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

É simples adicionar guias a um aplicativo do Teams. O aplicativo de exemplo já dá suporte a várias guias e você pode habilita-las.

### <a name="team-tab"></a>Guia Equipe

Seu aplicativo só pode ter uma guia Equipe:

<img  width="450px" alt="Adding a Teams tab" src="~/assets/images/get-started/TeamTab.png"/>

Neste exemplo, a guia Equipe é onde sua página de configuração é exibida. Selecione o **símbolo ...** da **URL de configuração da guia** e escolha **Editar** no menu suspenso. Altere a URL para `https://yourteamsapp.ngrok.io/configure` onde `yourteamsapp.ngrok.io` deve ser substituída pela URL que você usou ao hospedar seu aplicativo.

### <a name="personal-tabs"></a>Guias pessoais

Seu aplicativo pode ter até 16 guias, incluindo a guia Equipe.

As guias pessoais são diferentes da guia Equipe. **A guia Olá** já está listada na lista de guias pessoais com um valor de espaço reservado `com.contoso.helloworld.hellotab`. Selecione o **símbolo ...** da **URL de configuração da guia** e escolha **Editar** no menu suspenso. A caixa de diálogo a seguir é exibida:

<img  width="450px" alt="Adding a personal tab dialog" src="~/assets/images/get-started/PersonalTab.png"/>

Atualize as caixas a seguir com a URL do aplicativo:

- Alterar a **caixa URL de** Conteúdo para `https://yourteamsapp.ngrok.io/hello`
- Alterar a **caixa url do** site para `https://yourteamsapp.ngrok.io/hello`

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

    - **ID do comando**: inserir texto aleatório
    - **Título**: Inserir título aleatório
    - **Descrição**: insira a descrição aleatória

    Em **Parâmetro**:

    - **Nome**: insira o nome do parâmetro
    - **Título**: Insira o título do cartão
    - **Descrição**: insira a descrição do cartão

1. Depois de inserir as informações, selecione **Salvar** para fechar a caixa de diálogo.

#### <a name="register-your-app-in-teams"></a>Registrar seu aplicativo no Teams

Depois de inserir os detalhes do aplicativo, conclua as seguintes etapas para registrar seu aplicativo no Teams:

1. Use **Testar e distribuir o** App Studio para instalar seu aplicativo no Teams.
1. Atualize seu aplicativo hospedado com a ID do aplicativo e a senha do bot. Para o aplicativo de exemplo, use a mesma ID do aplicativo e a mesma senha para o bot e a extensão de mensagens.
1. Selecione **Testar e distribuir**  em **Concluir** no painel esquerdo do App Studio:

    <img  width="450px" alt="Testing your app" src="~/assets/images/get-started/Testanddistribute.png"/>

1. Para carregar seu aplicativo no Teams, selecione o **botão Instalar** em **Testar e Distribuir**:

    <img  width="450px" alt="Adding a messaging extension dialog" src="~/assets/images/get-started/InstallingHelloWorld.png"/>

    > [!NOTE]
    > Se não for possível realizar o sideload do aplicativo, verifique se você [habilitou o carregamento de aplicativo personalizado](../get-started/get-started-dotnet-app-studio.md#enable-sideloading-option).

1. Selecione a **caixa Pesquisar** na **seção Adicionar a uma equipe** e selecione uma equipe para adicionar o aplicativo de exemplo. Você pode configurar uma equipe especial para teste.
1. Selecione o **botão** Instalar na parte inferior da caixa de diálogo.

    Seu aplicativo agora está disponível no Teams. No entanto, o bot e a extensão de mensagens não funcionarão até que você atualize o ambiente de aplicativos hospedados com as IDs e senhas do aplicativo.

    <img  width="450px" alt="The finished app" src="~/assets/images/get-started/Finishedhelloworld.png"/>

## <a name="register-your-app-in-teams"></a>Registrar seu aplicativo no Teams

Depois de inserir os detalhes do aplicativo, conclua as seguintes etapas para registrar seu aplicativo no Teams:

1. Use **a Visualização** do Portal do Desenvolvedor para instalar seu aplicativo no Teams.

    :::image type="content" source="../assets/images/teams-toolkit-v2/preview-in-teams.png" alt-text="Imagem mostrando o botão Visualizar":::

1. Atualize seu aplicativo hospedado com a ID do aplicativo e a senha do bot. Para o aplicativo de exemplo, use a mesma ID do aplicativo e a mesma senha para o bot e a extensão de mensagens.

1. Selecione **Publicar para armazenar**  em **Publicar** no painel esquerdo do Portal do Desenvolvedor:

    :::image type="content" source="../assets/images/teams-toolkit-v2/devp-publish-left-pane.png" alt-text="Imagem mostrando a opção Publicar no painel esquerdo":::

    > [!NOTE]
    > Se não for possível realizar o sideload do aplicativo, verifique se você [habilitou o carregamento de aplicativo personalizado](../get-started/get-started-dotnet-app-studio.md#enable-sideloading-option).

1. Selecione **Adicionar** para instalar o aplicativo no Teams.

    Seu aplicativo agora está disponível no Teams. No entanto, o bot e a extensão de mensagens não funcionarão até que você atualize o ambiente de aplicativos hospedados com as IDs e senhas do aplicativo.

## <a name="update-the-credentials-for-your-hosted-app"></a>Atualizar as credenciais do aplicativo hospedado

O aplicativo de exemplo exige que as variáveis de ambiente sejam definidas com os valores salvos no arquivo de texto.

1. Abra o Gerenciador de Soluções.

    :::image type="content" source="../assets/images/get-started/csharp-repo-cloned.png" alt-text="Repositório de exemplo para o aplicativo Teams em c#":::

1. Abra o arquivo `appsettings.json`.

    :::image type="content" source="../assets/images/teams-toolkit-v2/csharp-appsetting-json.png" alt-text="Imagem mostrando o arquivo appsettings.json":::

1. Atualize **o valor de MicrosoftAppId** com a ID do bot que você salvou no arquivo de texto.
1. Atualize **o MicrosoftAppPassword** com a senha do bot que você salvou.

    :::image type="content" source="../assets/images/get-started/get-started-net-azure-add-keys.png" alt-text="Imagem mostrando a adição de chaves do Azure":::

    Depois de fazer essas alterações, recompile o aplicativo. Se você estiver usando o ngrok, poderá executar o aplicativo localmente e, se o tiver hospedado no Azure, reimplante o aplicativo.

## <a name="test-the-app-capabilities-in-teams"></a>Testar os recursos do aplicativo no Teams

### <a name="test-your-tab"></a>Testar sua guia

Depois de instalar o aplicativo no Teams, configure-o para exibir a guia que você deseja que o aplicativo carregue.

Para configurar a guia do aplicativo:

1. Vá para um canal na equipe em que você instalou o aplicativo de exemplo e selecione o botão **'+'** para adicionar uma nova guia.
1. Selecione **Olá, Mundo** na lista **Adicionar uma** guia. É exibida uma caixa de diálogo de configuração que permite selecionar a guia a ser exibida neste canal.
1. Selecione **Salvar**. A `Hello World` guia é carregada com a guia.

    <img width="530px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png" />

### <a name="test-your-bot-in-teams"></a>Testar seu bot no Teams

Agora você pode testar o bot no Teams.

Para testar seu bot:

- Selecione um canal na equipe em que você registrou seu aplicativo e digite `@your-bot-name`. Esse tipo de mensagem é chamado de **menção\@**. O bot responde a qualquer mensagem que você enviar.

    <img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png" />

### <a name="test-your-messaging-extension"></a>Testar sua extensão de mensagens

Para testar sua extensão de mensagens:

1. Selecione **...** abaixo da caixa de entrada no modo de exibição de conversa. Um menu com o **aplicativo "Olá, Mundo"** é exibido.
1. Selecione o menu, um conjunto de textos aleatórios é exibido. Você pode selecionar um dos textos aleatórios e que é inserido em sua conversa.

    <img width="530px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu1.png" />

    <img width="530px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result1.png" />

1. Selecione um dos textos aleatórios. Um cartão formatado e pronto para enviar com sua própria mensagem é mostrado.

    <img width="530px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />

| &nbsp; | &nbsp; |
|:--- | ---:|
|[Back](get-started-overview.md) | &nbsp; |
|
