### <a name="use-app-studio-to-update-the-app-package"></a>Use o App Studio para atualizar o pacote de aplicativos

App Studio é um aplicativo Teams que você pode instalar na loja Teams. Simplifica a criação e o registro de um aplicativo.

Complete as seguintes etapas para atualizar o pacote do aplicativo:

1. Para instalar o App Studio em Teams, selecione o ícone **Apps** na parte inferior da barra esquerda e procure por **App Studio**:

    <img  width="450px" alt="Finding App Studio in the Store View" src="~/assets/images/get-started/searchforAppStudio.png"/>

1. Selecione o **azulejo App Studio** e escolha **Instalar**. O App Studio está instalado:

    <img  width="450px" alt="Installing App Studio" src="~/assets/images/get-started/InstallingAppStudio.png"/>

1. Para criar o pacote de aplicativos para o aplicativo Teams, selecione a guia **do editor Manifest** no App **Studio**:

    <img  width="450px" alt="App Studio" src="~/assets/images/get-started/AppStudio.png"/>

    A amostra vem com seu próprio manifesto e foi projetada para construir um pacote de aplicativos quando o projeto é construído. No .NET isso é feito em Visual Studio e em Node.js isso é feito digitando `gulp` na linha de comando no diretório raiz do projeto.

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

    O nome do pacote de aplicativos gerados é **helloworldapp.zip**. Você pode procurar por este arquivo se o local não estiver claro na ferramenta que você está usando.

1. Agora, para modificar este pacote de aplicativos, selecione **Importar um aplicativo existente** no editor **Manifest**:

    <img  width="450px" alt="Importing an existing app" src="~/assets/images/get-started/Importinganapp.png"/>

1. Selecione a telha **Hello World** para o seu aplicativo recém-importado:

    <img  width="450px" alt="Newly imported app view" src="~/assets/images/get-started/HelloWorldappdetails.png"/>

A imagem a seguir mostra o pacote de aplicativo importado no App Studio:

<img  width="450px" alt="Importing the app package" src="~/assets/images/get-started/Importinganapp2.png"/>

No lado esquerdo do editor do Manifest há uma lista de passos. No lado direito há uma lista de propriedades que precisam ser preenchidas para cada etapa. Como você começou com um aplicativo de exemplo, grande parte das informações já estão concluídas. Os próximos passos permitem que você atualize as propriedades do aplicativo Hello World.

#### <a name="app-details"></a>Detalhes do aplicativo

Selecione **os detalhes do aplicativo** em **detalhes**. Selecione o botão **Gerar** para criar um novo ID do aplicativo.

Seu novo App ID é semelhante a `2322041b-72bf-459d-b107-f4f335bc35bd` .

Passe pelos detalhes do aplicativo no painel direito, incluindo **informações do Desenvolvedor** e detalhes de **Branding.** Esses detalhes são importantes se você estiver escrevendo um novo aplicativo para distribuição.

#### <a name="tabs"></a>Guias

É simples adicionar guias a um aplicativo Teams. O aplicativo de amostra já suporta várias guias, e você pode habilitá-las.

##### <a name="team-tab"></a>Guia da equipe

Seu aplicativo só pode ter uma guia Team:

<img  width="450px" alt="Adding a Teams tab" src="~/assets/images/get-started/TeamTab.png"/>

Nesta amostra, a guia Equipe é onde sua página de configuração é exibida. Selecione o **...** símbolo da url de **configuração da guia** e escolha **Editar** no menu suspenso. Altere a URL para `https://yourteamsapp.ngrok.io/configure` onde deve ser substituída pela URL que você usou ao `yourteamsapp.ngrok.io` [hospedar seu aplicativo](#host-the-sample-app).

##### <a name="personal-tabs"></a>Guias pessoais

Seu aplicativo pode ter até 16 guias, incluindo a guia Equipe.

As guias pessoais são diferentes da guia Equipe. **Hello Tab** já está listada na lista de guias pessoais com um valor de espaço reservado `com.contoso.helloworld.hellotab` . Selecione o **...** símbolo da url de **configuração da guia** e escolha **Editar** no menu suspenso. A seguinte caixa de diálogo é exibida:

<img  width="450px" alt="Adding a personal tab dialog" src="~/assets/images/get-started/PersonalTab.png"/>

Atualize as seguintes caixas com a URL do seu aplicativo:

- Alterar a caixa **de URL de conteúdo** para `https://yourteamsapp.ngrok.io/hello`
- Alterar a caixa **de URL do site** para `https://yourteamsapp.ngrok.io/hello`

Substitua `yourteamsapp.ngrok.io` pela URL usada ao hospedar seu aplicativo.

#### <a name="bots"></a>Bots

É fácil adicionar a funcionalidade bots ao seu aplicativo. O aplicativo de amostra **Hello World** já tem um bot como parte da amostra, mas você deve registrá-lo na Microsoft:

<img  width="450px" alt="Adding a bot" src="~/assets/images/get-started/Bots.png"/>

O bot importado da amostra não possui um ID de aplicativo associado. Você deve criar um novo bot para que o App Studio possa criar um novo App ID e registrá-lo na Microsoft.

> [!NOTE]
> O App ID criado pelo App Studio para o bot é diferente do App ID criado para o aplicativo. Cada bot em um aplicativo requer seu próprio App ID.

Complete as seguintes etapas para configurar seu bot:

1. Selecione **Excluir** ao lado do bot importado na lista de bots. Agora não há mais robôs para mostrar. 
1. Selecione **Configuração** para exibir a caixa de diálogo **Configurar um bot.**

    <img  width="450px" alt="Adding a bot dialog" src="~/assets/images/get-started/Setupbot.png"/>

1. Adicione um bot **contoso bot** e selecione todas as três caixas de seleção em **Escopo**.
1. Escolha **Salvar** para sair da caixa de diálogo. App Studio registra seu bot com a Microsoft e exibe seu novo bot na lista de bots. 
1. Agora abra um arquivo de texto no bloco de notas e copie e cole seu novo ID de bot nele.
1. Clique **em Gerar nova senha** e observe a senha no mesmo arquivo de texto que você anotou o ID do aplicativo do bot.
1. Atualize o **endereço de ponto final** do Bot e `https://yourteamsapp.ngrok.io/api/messages` substitua com a URL usada ao `yourteamsapp.ngrok.io` hospedar seu aplicativo.
1. Agora salve seu arquivo de texto, pois você deve adicionar as informações do arquivo ao seu aplicativo hospedado para permitir uma comunicação segura com o seu bot.

#### <a name="messaging-extensions"></a>Extensões de mensagens

As extensões de mensagens permitem que os usuários peçam informações do seu serviço e publiquem essas informações. As informações são postadas na forma de cartões na conversa do canal. As extensões de mensagens aparecem na parte inferior da caixa de composição.

Complete as seguintes etapas para configurar sua extensão de mensagens:

1. Selecione **as extensões de mensagens** em **recursos** no painel esquerdo do App Studio para configurar a extensão de mensagens:

    <img  width="450px" alt="Adding a messaging extension" src="~/assets/images/get-started/Messagingextensions.png"/>

    A extensão de mensagens de amostra está listada no painel **de extensões de mensagens.**

1. Selecione **Excluir** para remover a extensão de mensagens, selecione **Configurar** e siga os mesmos passos usados para [bots](#bots). A caixa de diálogo **De extensão de mensagens** é exibida.
1. Selecione a guia **Use bot existente** e selecione em um dos meus **bots existentes**.
1. Selecione o bot que você criou no menu suspenso. Adicione um **nome Bot** e selecione **Salvar** para fechar a caixa de diálogo.
1. Na seção **Comando,** selecione **Adicionar**. Para adicionar um comando baseado em pesquisa, selecione **Permitir que os usuários consultem seu serviço para obter informações e insira isso em uma opção de mensagem.**
1. Na caixa de diálogo **do novo comando,** digite os seguintes valores:

    Sob **novo comando:**

    - **ID de comando**: Digite texto aleatório
    - **Título**: Digite título aleatório
    - **Descrição**: Digite a descrição aleatória

    Sob **parâmetro:**

    - **Nome**: Digite o nome do parâmetro
    - **Título**: Digite o título do cartão
    - **Descrição**: Digite a descrição do cartão

1. Depois de inserir as informações, selecione **Salvar** para fechar a caixa de diálogo.

#### <a name="register-your-app-in-teams"></a>Registre seu aplicativo em Teams

Depois de inserir os detalhes do seu aplicativo, complete as seguintes etapas para registrar seu aplicativo em Teams:

1. Use **Teste e distribua** do App Studio para instalar seu aplicativo em Teams. 
1. Atualize seu aplicativo hospedado com o ID do aplicativo e senha para o seu bot. Para o aplicativo de exemplo, use o mesmo ID do aplicativo e senha para a extensão de bot e mensagens. 
1. Selecione **Teste e distribua**  em **Acabamento** no painel esquerdo do App Studio:

    <img  width="450px" alt="Testing your app" src="~/assets/images/get-started/Testanddistribute.png"/>

1. Para carregar seu aplicativo para Teams, selecione o botão **Instalar** em **Teste e Distribuir**:

    <img  width="450px" alt="Adding a messaging extension dialog" src="~/assets/images/get-started/InstallingHelloWorld.png"/>

1. Selecione a caixa **'Pesquisar** na seção **Adicionar a uma equipe'** e selecione uma equipe para adicionar o aplicativo de amostra. Você pode montar uma equipe especial para testes.
1. Selecione o botão **Instalar** na parte inferior da caixa de diálogo.

Seu aplicativo já está disponível em Teams. No entanto, o bot e a extensão de mensagens não funcionarão até que você atualize o ambiente de aplicativos hospedados com os IDs e senhas do aplicativo.

<img  width="450px" alt="The finished app" src="~/assets/images/get-started/Finishedhelloworld.png"/>
