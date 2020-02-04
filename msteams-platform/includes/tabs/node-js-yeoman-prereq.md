## <a name="prerequisites"></a>Pré-requisitos

- Para concluir este QuickStart, você precisará de um locatário do Office 365 e de uma equipe configurada para *permitir o carregamento de aplicativos personalizados* habilitados. Para saber mais, confira [preparar seu locatário do Office 365](~/concepts/build-and-test/prepare-your-o365-tenant.md).

  - Se você não tiver uma conta do Office 365, você poderá inscrever-se em uma assinatura gratuita por meio do programa de desenvolvedor do Office 365. A assinatura permanecerá ativa, contanto que você esteja usando-a para desenvolvimento contínuo. Confira [Bem-vindo ao programa para desenvolvedores do Office 365](/OfficeDev/office-dev-program-docs/docs/office-365-developer-program.md).

Além disso, este projeto requer que você tenha o seguinte instalado em seu ambiente de desenvolvimento:

- Qualquer editor de texto ou IDE. Você pode instalar e usar o [Visual Studio Code](https://code.visualstudio.com/download) gratuitamente.

- [Node. js/NPM](https://nodejs.org/en/). Você deve usar a versão mais recente do LTS. O Gerenciador de pacotes de nó (NPM) será instalado no seu sistema com a instalação do node. js.

- Depois de instalar o Node. js com êxito, instale os pacotes do [Yeoman](https://yeoman.io/) e do [Gulp-CLI](https://www.npmjs.com/package/gulp-cli) digitando o seguinte no prompt de comando:

```bash
npm install yo gulp-cli --global
```

- Instale o gerador de aplicativos do Microsoft Teams digitando o seguinte no prompt de comando:

```bash
npm install generator-teams --global
```

## <a name="generate-your-project"></a>Gerar seu projeto

- Abra um prompt de comando e crie um novo diretório para o projeto de tabulação.

- Para iniciar o gerador, navegue até o novo diretório e digite o seguinte comando:

```bash
yo teams
```

- Em seguida, você fornecerá uma série de valores que serão usados no arquivo **manifest. JSON** do aplicativo:

![captura de tela de abertura do gerador](/microsoftteams/platform/assets/images/tab-images/teamsTabScreenshot.PNG)

**Qual é o nome da sua solução?**

Este é o nome do projeto. Você pode aceitar o nome sugerido pressionando ENTER.

**Onde você deseja colocar os arquivos?**

No momento, você está no diretório do projeto. Pressione Enter.

**Título do seu projeto de aplicativo do Microsoft Teams?**

Este é o nome do pacote de aplicativos e será usado no manifesto do aplicativo e na descrição.

**Seu nome (empresa)? (máximo de 32 caracteres)**

O nome da sua empresa será usado no manifesto do aplicativo.

<br>**Qual versão do manifesto você gostaria de usar?**

Selecione o esquema padrão.

**Insira sua ID de parceiro da Microsoft, se você tiver uma? (Deixe em branco para ignorar)**

Este campo não é obrigatório e só deve ser usado se você já faz parte da [rede de parceiros da Microsoft](https://partner.microsoft.com).

**O que você deseja adicionar ao seu projeto?**

Selecione ( &ast; ) uma tabulação.

**A URL na qual você hospedará esta solução?**

Por padrão, o gerador sugere uma URL de sites do Azure. Você só testará seu aplicativo localmente, portanto, uma URL válida não é necessária para concluir este QuickStart.

**Deseja incluir a estrutura de teste e os testes iniciais? (s/N)**

Escolha **não** incluir uma estrutura de teste para este projeto. O padrão é sim; Digite **n**.

**Gostaria de usar o Azure Application insights para telemetria? (s/N)**

Escolha **não** incluir o [Azure Application insights](/azure-docs/articles/azure-monitor/app/app-insights-overview.md). O padrão é não; Digite **n**.

**Nome da guia padrão (máximo de 16 caracteres)?**

Nomeie sua guia. Este nome de guia será usado em todo o projeto como um componente de caminho de arquivo/URL.
