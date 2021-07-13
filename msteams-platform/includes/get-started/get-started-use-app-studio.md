### <a name="use-app-studio-to-update-the-app-package"></a>Usar o App Studio para atualizar o pacote de aplicativos

> [!TIP]
> **Experimente o Portal do Desenvolvedor**: o App Studio em breve será preterido. Configure, distribua e gerencie seus aplicativos Teams com o novo [Portal do Desenvolvedor.](https://dev.teams.microsoft.com/)

O App Studio é um Teams que você pode instalar na Teams store. Simplifica a criação e o registro de um aplicativo.

Conclua as etapas a seguir para atualizar o pacote do aplicativo:

1. Para instalar o App Studio Teams, selecione o ícone **Aplicativos** na parte inferior da barra à esquerda e procure **o App Studio**:

    <img  width="450px" alt="Finding App Studio in the Store View" src="~/assets/images/get-started/searchforAppStudio.png"/>

1. Selecione o **telha do App Studio** e escolha **Instalar**. O App Studio está instalado:

    <img  width="450px" alt="Installing App Studio" src="~/assets/images/get-started/InstallingAppStudio.png"/>

1. Para criar o pacote de aplicativos para seu Teams aplicativo, selecione a guia **Editor de manifesto** no App **Studio**:

    <img  width="450px" alt="App Studio" src="~/assets/images/get-started/AppStudio.png"/>


    O exemplo vem com seu próprio manifesto e foi projetado para criar um pacote de aplicativos quando o projeto é criado. No .NET, o arquivo manifest.json pode estar localizado Visual Studio em Manifesto em ```Microsoft.Teams.Samples.HelloWorld.Web``` . No Node.js, isso é feito digitando na linha de comando no `gulp` diretório raiz do projeto.

     Em Visual Studio, o arquivo manifest.json está localizado em **em Manifesto** em `Microsoft.Teams.Samples.HelloWorld.Web` . Esta etapa é descrita pela imagem a seguir:  
    
    <img  width="450px" alt="Build the app package on .NET with Visual Studio" src="~/assets/images/get-started/app-package-on-.NET-with-Visual-Studio.png"/>
    
    Você pode criar o pacote do aplicativo Node.js digitando na linha de comando no `gulp` diretório raiz do projeto.


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

    O nome do pacote de aplicativos gerado é **helloworldapp.zip**. Você pode pesquisar esse arquivo se o local não estiver claro na ferramenta que você está usando.

1. Agora, para modificar este pacote de aplicativos, selecione **Importar um aplicativo existente** no editor de **Manifesto:**

    <img  width="450px" alt="Importing an existing app" src="~/assets/images/get-started/Importinganapp.png"/>

1. Selecione o **azulejo Hello World** para seu aplicativo recém-importado:

    <img  width="450px" alt="Newly imported app view" src="~/assets/images/get-started/HelloWorldappdetails.png"/>

    A imagem a seguir mostra o pacote de aplicativos importado no App Studio:

    <img  width="450px" alt="Importing the app package" src="~/assets/images/get-started/Importinganapp2.png"/>

    No lado esquerdo do editor de Manifesto há uma lista de etapas. No lado direito, há uma lista de propriedades que precisam ser preenchidas para cada etapa. Conforme você começou com um aplicativo de exemplo, grande parte das informações já foi concluída. As próximas etapas permitem que você atualize as propriedades do aplicativo Hello World.

#### <a name="app-details"></a>Detalhes do aplicativo

Selecione **Detalhes do aplicativo** em **Detalhes**. Selecione o **botão Gerar** para criar uma nova ID do aplicativo.

Sua nova ID do aplicativo é semelhante a `2322041b-72bf-459d-b107-f4f335bc35bd` .

Veja os detalhes do aplicativo no painel à direita, incluindo informações **do desenvolvedor** e detalhes **de identidade** visual. Esses detalhes são importantes se você estiver escrevendo um novo aplicativo para distribuição.

#### <a name="tabs"></a>Guias

É simples adicionar guias a um Teams aplicativo. O aplicativo de exemplo já dá suporte a várias guias e você pode habilita-las.

##### <a name="team-tab"></a>Guia Equipe

Seu aplicativo só pode ter uma guia Equipe:

<img  width="450px" alt="Adding a Teams tab" src="~/assets/images/get-started/TeamTab.png"/>

Neste exemplo, a guia Equipe é onde sua página de configuração é exibida. Selecione o **símbolo ...** da url de configuração **de tabulação** e escolha **Editar** no menu suspenso. Altere a URL `https://yourteamsapp.ngrok.io/configure` para onde deve ser substituída pela URL que você usou ao hospedar seu `yourteamsapp.ngrok.io` aplicativo.

##### <a name="personal-tabs"></a>Guias pessoais

Seu aplicativo pode ter até 16 guias, incluindo a guia Equipe.

As guias pessoais são diferentes da guia Equipe. A Guia **Hello** já está listada na lista de guias pessoais com um valor de espaço reservado `com.contoso.helloworld.hellotab` . Selecione o **símbolo ...** da url de configuração **de tabulação** e escolha **Editar** no menu suspenso. A caixa de diálogo a seguir é exibida:

<img  width="450px" alt="Adding a personal tab dialog" src="~/assets/images/get-started/PersonalTab.png"/>

Atualize as caixas a seguir com a URL do aplicativo:

- Alterar a **caixa URL** de conteúdo para `https://yourteamsapp.ngrok.io/hello`
- Alterar a **caixa URL do** site para `https://yourteamsapp.ngrok.io/hello`

Substitua `yourteamsapp.ngrok.io` pela URL que você usou ao hospedar seu aplicativo.

#### <a name="bots"></a>Bots

É fácil adicionar a funcionalidade de bots ao seu aplicativo. O aplicativo de exemplo **Hello World** já tem um bot como parte do exemplo, mas você deve registrá-lo com a Microsoft:

<img  width="450px" alt="Adding a bot" src="~/assets/images/get-started/Bots.png"/>

O bot importado do exemplo não tem uma ID de aplicativo associada. Você deve criar um novo bot para que o App Studio possa criar uma nova ID de aplicativo e registrá-la na Microsoft.

> [!NOTE]
> A ID do aplicativo criada pelo App Studio para o bot é diferente da ID do aplicativo criada para o aplicativo. Cada bot em um aplicativo requer sua própria ID de aplicativo.

Conclua as etapas a seguir para configurar seu bot:

1. Selecione **Excluir** ao lado do bot importado na lista de bots. Agora não há mais bots para mostrar. 
1. Selecione **Configurar para** exibir a caixa de diálogo Configurar um **bot.**

    <img  width="450px" alt="Adding a bot dialog" src="~/assets/images/get-started/Setupbot.png"/>

1. Adicione um bot nome **contoso bot** e selecione todas as três caixas de seleção em **Escopo**.
1. Escolha **Salvar** para sair da caixa de diálogo. O App Studio registra seu bot com a Microsoft e exibe seu novo bot na lista de bots. 
1. Agora abra um arquivo de texto no bloco de notas e copie e colar sua nova ID de bot nele.
1. Clique **em Gerar Nova Senha** e anote a senha no mesmo arquivo de texto que você anotou a ID do aplicativo bot.
1. Atualize **o endereço de ponto de** extremidade bot para e substitua pela URL que você usou ao hospedar seu `https://yourteamsapp.ngrok.io/api/messages` `yourteamsapp.ngrok.io` aplicativo.
1. Agora salve seu arquivo de texto, pois você deve adicionar as informações do arquivo ao seu aplicativo hospedado para permitir a comunicação segura com seu bot.

#### <a name="messaging-extensions"></a>Extensões de mensagens

As extensões de mensagens permitem que os usuários peçam informações do seu serviço e postem essas informações. As informações são postadas na forma de cartões na conversa do canal. As extensões de mensagens aparecem na parte inferior da caixa de redação.

Conclua as etapas a seguir para configurar sua extensão de mensagens:

1. Selecione **Extensões de mensagens** em **Recursos** no painel esquerdo do App Studio para configurar a extensão de mensagens:

    <img  width="450px" alt="Adding a messaging extension" src="~/assets/images/get-started/Messagingextensions.png"/>

    A extensão de mensagens de exemplo está listada no painel **Extensões de** Mensagens.

1. Selecione **Excluir** para remover a extensão de mensagens, selecione **Configurar** e siga as mesmas etapas usadas para [bots](#bots). A **caixa de diálogo Extensão** de Mensagens é exibida.
1. Selecione a **guia Usar bot existente** e Selecione de um dos meus **bots existentes.**
1. Selecione o bot criado no menu suspenso. Adicione um **nome de Bot** e selecione **Salvar** para fechar a caixa de diálogo.
1. Na seção **Comando,** selecione **Adicionar**. Para adicionar um comando baseado em pesquisa, selecione a opção Permitir que os usuários consultem seu serviço para obter informações e **insira-o em uma opção de** mensagem.
1. Na caixa **de diálogo** Novo comando, insira os seguintes valores:

    Em **Novo comando**:

    - **ID do comando**: Insira texto aleatório
    - **Título**: Insira título aleatório
    - **Descrição**: Insira a descrição aleatória

    Em **Parâmetro**:

    - **Nome**: Insira o nome do parâmetro
    - **Título**: Insira o título do cartão
    - **Descrição**: Insira a descrição do cartão

1. Depois de inserir as informações, selecione **Salvar** para fechar a caixa de diálogo.

#### <a name="register-your-app-in-teams"></a>Registre seu aplicativo no Teams

Depois de inserir os detalhes do seu aplicativo, conclua as seguintes etapas para registrar seu aplicativo Teams:

1. Use **Test and distribute** of App Studio to install your app in Teams. 
1. Atualize seu aplicativo hospedado com a ID do aplicativo e a senha do bot. Para o aplicativo de exemplo, use a mesma ID de aplicativo e senha para bot e extensão de mensagens. 
1. Selecione **Testar e distribuir**  em **Concluir** no painel esquerdo do App Studio:

    <img  width="450px" alt="Testing your app" src="~/assets/images/get-started/Testanddistribute.png"/>

1. Para carregar seu aplicativo no Teams, selecione o botão **Instalar** em **Testar e Distribuir:**

    <img  width="450px" alt="Adding a messaging extension dialog" src="~/assets/images/get-started/InstallingHelloWorld.png"/>
    
    > [!NOTE]
    > Se você não conseguir fazer sideload do aplicativo, verifique se você [habilitar o carregamento personalizado de aplicativos](#prepare-your-development-environment).

1. Selecione a **caixa Pesquisar** na seção Adicionar a **uma equipe** e selecione uma equipe para adicionar o aplicativo de exemplo. Você pode configurar uma equipe especial para teste.
1. Selecione o **botão Instalar** na parte inferior da caixa de diálogo.

    Seu aplicativo agora está disponível no Teams. No entanto, o bot e a extensão de mensagens não funcionarão até que você atualize o ambiente de aplicativos hospedados com as IDs de aplicativo e senhas.

    <img  width="450px" alt="The finished app" src="~/assets/images/get-started/Finishedhelloworld.png"/>
