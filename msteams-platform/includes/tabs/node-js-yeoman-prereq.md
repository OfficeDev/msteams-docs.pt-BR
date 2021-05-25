## <a name="prerequisites"></a>Pré-requisitos

- Para concluir esse início rápido, você precisará de um locatário Office 365 e uma equipe configurada com Permitir o carregamento de *aplicativos personalizados* habilitados. Para saber mais, consulte [Prepare your Office 365 tenant](~/concepts/build-and-test/prepare-your-o365-tenant.md).

  - Se você não tiver uma conta Office 365, poderá inscrever-se para uma assinatura gratuita por meio do programa Office 365 Desenvolvedor. A assinatura permanecerá ativa enquanto você a estiver usando para desenvolvimento contínuo. Consulte [Welcome to the Office 365 Developer Program](/office/developer-program/microsoft-365-developer-program).

Além disso, este projeto exige que você tenha o seguinte instalado em seu ambiente de desenvolvimento:

- Qualquer editor de texto ou IDE. Você pode instalar e usar [Visual Studio Code](https://code.visualstudio.com/download) gratuitamente.

- [Node.js/npm](https://nodejs.org/en/). Você deve usar a versão LTS mais recente. O nó Gerenciador de Pacotes (npm) será instalado em seu sistema com a instalação de Node.js.

- Depois de instalar o Node.js, instale os pacotes [Yeoman](https://yeoman.io/) e [gulp-cli](https://www.npmjs.com/package/gulp-cli) digitando o seguinte no prompt de comando:

    ```bash
    npm install yo gulp-cli --global
    ```

- Instale o Microsoft Teams aplicativos digitando o seguinte no prompt de comando:

    ```bash
    npm install generator-teams --global
    ```

## <a name="generate-your-project"></a>Gerar seu projeto

- Abra um prompt de comando e crie um novo diretório para seu projeto de guia.

- Para iniciar o gerador, navegue até o novo diretório e digite o seguinte comando:

    ```bash
    yo teams
    ```

- Em seguida, você fornecerá uma série de valores que serão usados no arquivomanifest.js **no** aplicativo:

    ![captura de tela de abertura do gerador](/microsoftteams/platform/assets/images/tab-images/teamsTabScreenshot.PNG)

    **Qual é o nome da solução?**

    Esse é o nome do seu projeto. Você pode aceitar o nome sugerido pressionando enter.

    **Onde você deseja colocar os arquivos?**

    No momento, você está no diretório do projeto. Pressione Enter.

    **Título do seu projeto Microsoft Teams aplicativo?**

    Esse é o nome do pacote do aplicativo e será usado no manifesto e na descrição do aplicativo.

    **Seu nome (empresa) ? (máx. 32 caracteres)**

    O nome da empresa será usado no manifesto do aplicativo.

    **Qual versão de manifesto você gostaria de usar?**

    Selecione o esquema padrão.

    **Scaffolding rápido? (Y/n)**

    O padrão é sim; insira **n** para inserir sua ID do Microsoft Partner.

    **Insira sua ID do Microsoft Partner, se você tiver uma? (Deixe em branco para ignorar)**

    Esse campo não é obrigatório e só deve ser usado se você já faz parte da [Rede de Parceiros da Microsoft.](https://partner.microsoft.com)

    **O que você deseja adicionar ao seu projeto?**

    Selecione ( &ast; ) Uma guia.

    **A URL onde você hospedará essa solução?**

    Por padrão, o gerador sugere uma URL de Sites do Azure. Você só estará testando seu aplicativo localmente, portanto, uma URL válida não é necessária para concluir esse início rápido.

    **Você gostaria de incluir a estrutura de teste e testes iniciais? (y/N)**

    Escolha **não** incluir uma estrutura de teste para este projeto. O padrão é sim; enter **n**.

    **Você gostaria de usar o Azure Applications Insights para telemetria? (y/N)**

    Escolha **não incluir** o [Azure Application Insights.](/azure/azure-monitor/app/app-insights-overview) O padrão é não; enter **n**.

    **Nome da guia padrão (máx. 16 caracteres)?**

    Nomeia sua guia. Esse nome de guia será usado em todo o seu projeto como um componente de caminho de arquivo/URL.
