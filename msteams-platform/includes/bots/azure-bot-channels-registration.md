1. No [portal do Microsoft Azure](https://ms.portal.azure.com/#home), em serviços do Azure, selecione **Criar um recurso**.
1. Na caixa de pesquisa insira "bot". E na lista suspensa, selecione **Registro de Canais de Bot**.
1. Selecione o botão **Criar**.
1. Na folha de **Registro de Canal de Bot**, forneça as informações solicitadas sobre o bot.
1. Deixe a caixa do **Ponto de extremidade do Messaging** vazia por enquanto, você inserirá a URL necessária após implantar o bot. A imagem a seguir mostra um exemplo das configurações de registro:

    ![Registro de canais de aplicativos do bot](../../assets/images/authentication/auth-bot-channels-registration.png)

1. Clique **ID do Aplicativo da Microsoft** e **Criar Novo**.

    ![Criar uma ID do Aplicativo da Microsoft](../../assets/images/authentication/CreateMicrosoftAppID.png) ![Criar uma nova ID do Aplicativo da Microsoft](../../assets/images/authentication/CreateNewMicrosoftAppID.png)    

1. Clique no link **Criar ID de aplicativo no Portal de Registro**.

   ![Registros de Aplicativos](../../assets/images/authentication/AppRegistration.png)
   
1. Na janela de **Registro do aplicativo** exibida, clique na guia **Novo registro** no canto superior esquerdo.
1. Insira o nome do aplicativo bot que você está registrando, costumamos usar *BotTeamsAuth* (você precisa selecionar seu próprio nome exclusivo).
1. Para os **Tipos de conta com suporte**, selecione *Contas em qualquer diretório organizacional (Qualquer diretório do Azure Active Directory - Multitenant) e contas pessoais da Microsoft (por exemplo, Skype e Xbox)*.
1. Clique no botão **Registrar**. Quando concluir, o Azure exibirá a página *visão geral* para o aplicativo.
1. Copie e salve em um arquivo o valor do **ID do aplicativo (cliente)**.
1. No painel esquerdo, clique em **Certificado e segredos**.
    1. Em *Segredos do cliente*, clique em **Novo segredo do cliente**.
    1. Adicione uma descrição para identificar este segredo de outros que você possa precisar criar para este aplicativo.
    1. Defina *Expirar* à sua seleção.
    1. Clique em **Adicionar**.
    1. Copiar o segredo do cliente e salvá-lo em um arquivo.
1. Volte para a janela de **Registro do Canal de Bot** e copie o *ID do aplicativo* e o *Segredo do cliente* nas caixas **ID do aplicativo Microsoft** e **Senha**, respectivamente.
1. Clique em **OK**.
1. Por fim, clique em **Criar**.

Depois que o Azure criar o recurso de registro, ele será incluído na lista de grupos de recursos.  

![grupo de registro de canais de aplicativos bot](~/assets/images/authentication/auth-bot-channels-registration-group.PNG)

Depois de criar o registro de canais de bot, você precisará habilitar o canal do Teams.

1. No [portal do Microsoft Azure](https://ms.portal.azure.com/#home), em serviços do Azure, selecione o **Registro do Canal Bot** que você acabou de criar.
1. No painel esquerdo, clique em **Canais**.
1. Clique no ícone do Microsoft Teams e escolha **Salvar**.
