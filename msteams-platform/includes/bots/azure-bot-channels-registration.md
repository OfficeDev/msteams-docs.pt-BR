1. No [portal do Azure] [Azure-portal], no painel de navegação à esquerda, selecione **criar um recurso**.
1. Na caixa de seleção do painel direito, digite "bot". E, na lista suspensa, selecione o **registro de canais de bot**.
1. Clique no botão **criar** .
1. Na lâmina de **registro do canal do bot** , forneça as informações solicitadas sobre o bot.
1. Deixe a caixa de **ponto de extremidade de mensagens** vazia por enquanto, você inserirá a URL necessária após a implantação do bot. A imagem a seguir mostra um exemplo das configurações de registro:

    ![registro de canais de aplicativos bot](../../assets/images/authentication/auth-bot-channels-registration.png)

1. Clique em **ID e senha do aplicativo Microsoft** e **crie novo**.
1. Clique em **criar ID do aplicativo no link do portal de registro do aplicativo** .
1. Na janela de **registro de aplicativo** exibido, clique na guia **novo registro** no canto superior esquerdo.
1. Insira o nome do aplicativo bot que você está registrando, usamos *BotTeamsAuth* (você precisa selecionar seu próprio nome exclusivo).
1. Para os **tipos de conta com suporte** *, selecione contas em qualquer diretório organizacional (qualquer diretório do Azure ad-multilocatário) e contas pessoais da Microsoft (por exemplo, Skype, Xbox)*.
1. Clique no botão **registrar** . Depois de concluído, o Azure exibe a página *visão geral* do aplicativo.
1. Copie e salve em um arquivo o valor de **ID do aplicativo (cliente)** .
1. No painel esquerdo, clique em **certificado e segredos**.
    1. Em *segredos do cliente*, clique em **novo segredo do cliente**.
    1. Adicione uma descrição para identificar esse segredo de outras pessoas que você talvez precise criar para este aplicativo.
    1. Definir *expira* para sua seleção.
    1. Clique em **Adicionar**.
    1. Copie o segredo do cliente e salve-o em um arquivo.
1. Volte para a janela de **registro do canal do bot** e copie a ID do *aplicativo* e o segredo do *cliente* nas caixas ID do **aplicativo da Microsoft** e **senha** , respectivamente.
1. Clique em **OK**.
1. Por fim, clique em **criar**.
