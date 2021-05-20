## <a name="prerequisites"></a>Pré-requisitos

- Para completar este quickstart, você precisará de um inquilino Office 365 e uma equipe configurada com *Permitir o upload de aplicativos personalizados* ativados. Para saber mais, consulte [Prepare seu inquilino Office 365](~/concepts/build-and-test/prepare-your-o365-tenant.md).

  - Se você não tiver atualmente uma conta Office 365, você pode se inscrever para uma assinatura gratuita através do programa de desenvolvedor Office 365. A assinatura permanecerá ativa enquanto você estiver usando-a para o desenvolvimento contínuo. Veja [Bem-vindo ao Programa de Desenvolvedores Office 365](/office/developer-program/microsoft-365-developer-program).

Além disso, este projeto exige que você tenha o seguinte instalado em seu ambiente de desenvolvimento:

- Qualquer editor de texto ou IDE. Você pode instalar e usar [Visual Studio Code](https://code.visualstudio.com/download) gratuitamente.

- [Node.js/npm](https://nodejs.org/en/). Você deve usar a versão LTS mais recente. O Node Gerenciador de Pacotes (npm) será instalado em seu sistema com a instalação de Node.js.

- Depois de instalar com sucesso Node.js, instale os pacotes [Yeoman](https://yeoman.io/) e [gulp-cli](https://www.npmjs.com/package/gulp-cli) digitando o seguinte no seu prompt de comando:

    ```bash
    npm install yo gulp-cli --global
    ```

- Instale o gerador de aplicativos Microsoft Teams digitando o seguinte no prompt de comando:

    ```bash
    npm install generator-teams --global
    ```

## <a name="generate-your-project"></a>Gere seu projeto

- Abra um prompt de comando e crie um novo diretório para o seu projeto de guia.

- Para iniciar o gerador, navegue até o novo diretório e digite o seguinte comando:

    ```bash
    yo teams
    ```

- Em seguida, você fornecerá uma série de valores que serão usados nomanifest.jsdo seu aplicativo **no** arquivo:

    ![captura de tela de abertura do gerador](/microsoftteams/platform/assets/images/tab-images/teamsTabScreenshot.PNG)

    **Qual é o nome da sua solução?**

    Este é o nome do seu projeto. Você pode aceitar o nome sugerido pressionando enter.

    **Onde você deseja colocar os arquivos?**

    Você está no seu diretório de projetos. Pressione enter.

    **Título do seu projeto de aplicativo Microsoft Teams?**

    Este é o nome do seu pacote de aplicativo e será usado no manifesto e descrição do aplicativo.

    **Seu nome (empresa) ? (no máximo 32 caracteres)**

    O nome da sua empresa será usado no manifesto do aplicativo.

    **Qual versão manifesto você gostaria de usar?**

    Selecione o esquema padrão.

    **Andaimes rápidos? (Y/n)**

    O padrão é sim; enter **n** para inserir seu Microsoft Partner Id.

    **Digite seu Microsoft Partner Id, se você tiver um? (Deixe em branco para pular)**

    Este campo não é necessário e só deve ser usado se você já faz parte da [Microsoft Partner Network](https://partner.microsoft.com).

    **O que você quer adicionar ao seu projeto?**

    Selecione ( &ast; ) Uma guia.

    **A URL onde você vai hospedar esta solução?**

    Por padrão, o gerador sugere uma URL do Azure Web Sites. Você só estará testando seu aplicativo localmente, portanto, uma URL válida não é necessária para completar este quickstart.

    **Gostaria de incluir a estrutura de teste e os testes iniciais? (y/N)**

    Escolha **não** incluir uma estrutura de teste para este projeto. O padrão é sim; entrar **n**.

    **Deseja usar o Azure Applications Insights para telemetria? (y/N)**

    Escolha **não** incluir [insights de aplicativos do Azure](/azure-docs/articles/azure-monitor/app/app-insights-overview.md). O padrão é não; entrar **n**.

    **Nome da guia padrão (max 16 caracteres)?**

    Diga sua guia. Este nome da guia será usado em todo o seu projeto como um componente de caminho de arquivo/URL.
