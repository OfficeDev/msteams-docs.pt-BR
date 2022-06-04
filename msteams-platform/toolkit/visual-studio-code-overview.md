---
title: Criar aplicativos com o Kit de Ferramentas do Microsoft Teams e Visual Studio Code
description: Introdução à criação de ótimos aplicativos personalizados diretamente no Visual Studio Code com o Kit de Ferramentas do Microsoft Teams
keywords: Kit de ferramentas do Visual Studio Code do Teams
ms.localizationpriority: medium
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: 841dddfd515fd202a36f4c8a6b490faccff7b537
ms.sourcegitcommit: e16b51a49756e0fe4eaf239898e28d3021f552da
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2022
ms.locfileid: "65887601"
---
# <a name="build-apps-with-the-teams-toolkit-and-visual-studio-code"></a>Criar aplicativos com o Kit de Ferramentas do Teams e o Visual Studio Code

O Kit de Ferramentas do Teams para Visual Studio Code ajuda os desenvolvedores a criar e implantar aplicativos do Teams com identidade integrada, acesso ao armazenamento em nuvem, dados do Microsoft Graph e outros serviços no Azure e no Microsoft 365 com uma abordagem de "configuração zero" para a experiência do desenvolvedor.  

Você também pode usar o kit de ferramentas com o Visual Studio ou como uma CLI (chamada `teamsfx`).

## <a name="install-the-teams-toolkit-for-visual-studio-code"></a>Instalar o Kit de Ferramentas do Teams para Visual Studio Code

1. Abra o Visual Studio Code.
1. Selecione o modo de exibição Extensões (**Ctrl+Shift+X** / **⌘⇧-X** ou **Exibir > Extensões**).
1. Na caixa de pesquisa, insira o _Kit de Ferramentas do Teams_.
1. Selecione o botão de instalação verde ao lado do Kit de Ferramentas do Teams.

Você também pode encontrar o Kit de Ferramentas do Teams no [Marketplace do Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension).

As ferramentas a seguir são instaladas pela extensão do Visual Studio Code quando são necessárias. Se já estiver instalado, a versão instalada será usada em vez disso. Se estiver usando o Linux (incluindo o WSL), você deverá instalar essas ferramentas antes de usar:

- [Ferramentas do Azure Functions Core versão 3.](/azure/azure-functions/functions-run-local)

    O Azure Functions Core Tools é usado para executar todos os componentes de back-end localmente durante uma execução de depuração local, incluindo os auxiliares de autenticação necessários ao executar seus serviços no Azure. Ele é instalado no diretório do projeto usando o npm `devDependencies`.

- [SDK DO .NET](/dotnet/core/install/)

    O SDK do .NET é usado para instalar associações personalizadas para depuração local e implantações de aplicativo do Azure Functions. Se você ainda não instalou o SDK do .NET 3.1 ou posterior globalmente, a versão portátil será instalada.

- [ngrok](https://ngrok.com/download)

    Alguns recursos do aplicativo Teams (bots de conversa, extensões de mensagens e webhooks de entrada) exigem conexões de entrada.  Você precisa expor seu sistema de desenvolvimento ao Teams por meio de um túnel. Um túnel não é necessário para aplicativos que incluem apenas guias.  Esse pacote é instalado no diretório do projeto (usando npm `devDependencies`).

## <a name="use-the-teams-toolkit-for-visual-studio-code"></a>Usar o Kit de Ferramentas do Teams para Visual Studio Code

- [Configurar um novo projeto](#set-up-a-new-teams-project)
- [Configurar seu aplicativo](#configure-your-app)
- [Executar seu aplicativo localmente](#install-and-run-your-app-locally)
- [Publicar seu aplicativo](#publish-your-app-to-teams)

## <a name="set-up-a-new-teams-project"></a>Configurar um novo projeto do Teams

O Kit de Ferramentas do Teams pode criar aplicativos React hospedados em Web Parts do Azure ou SPFx hospedadas em seu ambiente do Microsoft 365 SharePoint. Para criar um novo aplicativo React a ser hospedado no Azure:

1. Abra o Visual Studio Code.
1. Abra o Kit de ferramentas do Teams selecionando o ícone do Teams na barra lateral:

    :::image type="content" source="../assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="O ícone do Teams na barra lateral do Visual Studio Code":::

1. Selecione **Criar Novo Projeto**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project.png" alt-text="Localização do link de Criação de Novo Projeto na barra lateral do Kit de ferramentas do Teams.":::

1. Selecione **Criar um novo aplicativo do Teams**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-new-project-intro.png" alt-text="Início do assistente para Criar Novo Projeto":::

1. Na etapa **Selecionar recursos** , a funcionalidade **Tab** já está selecionada. Opcionalmente, você também pode selecionar **Bot** e **Extensão de Mensagens**.  Pressione **OK**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-capabilities.png" alt-text="Captura de tela mostrando como adicionar capacidades ao seu novo aplicativo.":::

1. Na etapa **Tipo de hospedagem front-end**, selecione **Azure**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-hosting.png" alt-text="Captura de tela mostrando como selecionar a hospedagem para seu novo aplicativo.":::

1. Opcionalmente, na etapa recursos **de nuvem** , selecione os recursos de nuvem que seu aplicativo usa. Você pode selecionar o acesso CRUD (criar, ler, atualizar e excluir) a uma tabela SQL ou a uma API:

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-cloud-resources.png" alt-text="Captura de tela mostrando como adicionar recursos em nuvem ao seu novo aplicativo.":::

1. Na etapa **de Linguagem de** Programação, você pode escolher **JavaScript** ou **TypeScript**:

    :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-programming-languages.png" alt-text="Captura de tela mostrando como selecionar a linguagem de programação.":::

1. Selecione uma pasta do espaço de trabalho. Uma pasta é criada na pasta do workspace para o projeto que você está criando.

1. Insira um nome adequado para seu aplicativo, como `helloworld`. O nome do aplicativo deve consistir apenas de caracteres alfanuméricos.  Pressione **Inserir** para continuar.

Seu aplicativo teams é criado em alguns segundos. O aplicativo com scaffolding contém código para lidar com o logon único com o Azure Active Directory e o acesso ao Microsoft Graph.  Se você selecionou recursos do Azure, o código para esses recursos também estará disponível.

Para obter um passo a passo do processo de criação e publicação do SPFx, consulte o [tutorial do SPFx](../get-started/first-app-spfx.md).

## <a name="configure-your-app"></a>Configurar seu aplicativo

Em seu núcleo, o aplicativo Teams adota três componentes:

  1. O cliente do Microsoft Teams (Web, desktop ou móvel) em que os usuários interagem com seu aplicativo.
  1. Um servidor que responde a solicitações de conteúdo que é exibido no Teams. Por exemplo, conteúdo da guia HTML ou um Cartão Adaptável do bot.
  1. Um pacote de aplicativos do Teams consiste em três arquivos:

      > [!div class="checklist"]
      >
      > - O manifest.json.
      > - Um [ícone de cor](../resources/schema/manifest-schema.md#icons) para seu aplicativo ser exibido no catálogo de aplicativos públicos ou da organização.
      > - Um [ícone de estrutura de](../resources/schema/manifest-schema.md#icons) tópicos para exibição na barra de atividades do Teams.

O manifesto e os ícones são armazenados na `.fx` pasta do seu projeto antes de serem carregados no Teams. Quando um aplicativo é instalado, o cliente do Teams analisa o arquivo de manifesto para determinar as informações necessárias, como o nome do aplicativo e a URL em que os serviços estão localizados.

1. Para configurar seu aplicativo, navegue até a guia **Kit de Ferramentas do Teams** no Visual Studio Code.
1. Selecione **Editor de Manifesto** na **seção** Projeto.

Editar os campos na página de detalhes do aplicativo atualiza o conteúdo do arquivo manifest.json que, por fim, é enviado como parte do pacote do aplicativo.

## <a name="install-and-run-your-app-locally"></a>Instalar e executar seu aplicativo localmente

Para compilar e executar seu aplicativo localmente:

1. No Visual Studio Code, pressione **F5** para executar seu aplicativo no modo de depuração.

   > Quando você executa o aplicativo pela primeira vez, todas as dependências são baixadas e o aplicativo é compilado.  Uma janela do navegador é aberta automaticamente quando a compilação é concluída.  Isto pode levar de 3 a 5 minutos para ser concluído.

   O kit de ferramentas solicita que você instale um certificado local, se necessário. Esse certificado permite que o Teams carregue seu aplicativo a partir de `https://localhost`. Selecione Sim quando aparecer a seguinte caixa de diálogo:

   :::image type="content" source="../assets/images/teams-toolkit-v2/ssl-prompt.png" alt-text="Captura de tela mostrando como a solicitação de instalação de um certificado SSL para permitir que o Teams carregue seu aplicativo a partir do localhost.":::

1. O seu navegador da web é iniciado para executar o aplicativo. Se for solicitado a abrir o Microsoft Teams, selecione Cancelar para permanecer no navegador. Você também pode ser solicitado a alternar para o aplicativo Teams em outros momentos. Selecione o aplicativo Web quando isso acontecer.

   :::image type="content" source="../assets/images/teams-toolkit-v2/launch-web-browser-and-pick-webapp.png" alt-text="Captura de tela mostrando como escolher a versão da web das equipes quando lançadas":::

1. Você pode ser solicitado a entrar. Nesse caso, entre com sua conta do Microsoft 365.
1. Quando solicitado a instalar o aplicativo no Teams, pressione **Adicionar**.

O back-end e o front-end são conectados ao depurador do Visual Studio Code.  Isso permite que você defina pontos de interrupção em qualquer lugar em seu código e inspecione o estado.  Você também pode usar qualquer ferramenta de depuração de front-end (como as Ferramentas para Desenvolvedores do React) no navegador.  Para obter mais informações sobre depuração no Visual Studio Code, examine [a documentação](https://code.visualstudio.com/Docs/editor/debugging).

## <a name="publish-your-app-to-teams"></a>Publicar seu aplicativo no Teams

Antes que ele possa ser usado por outras pessoas, você deve publicar seu aplicativo no Portal do Desenvolvedor para Teams.

1. Para publicar seu aplicativo, navegue até a guia **Kit de Ferramentas do Teams** no Visual Studio Code.
1. Selecione **Publicar no Teams** na **seção** Projeto.

Se estiver usando a hospedagem do Azure, você deverá ter provisionado e implantado na nuvem. Para obter um passo a passo do processo de publicação SPFx, consulte o [tutorial spFx](../get-started/first-app-spfx.md).

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Mantendo e dando suporte ao aplicativo publicado](../concepts/deploy-and-publish/appsource/post-publish/overview.md)

## <a name="see-also"></a>Confira também

* [Criar aplicativos com o Kit de ferramentas do Teams para o Visual Studio](~/toolkit/visual-studio-overview.md)
* [Criar guias e outras experiências hospedadas com o SDK do cliente JavaScript do Microsoft Teams](~/tabs/how-to/using-teams-client-sdk.md)
