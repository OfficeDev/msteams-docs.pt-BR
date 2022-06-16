---
title: Criar aplicativos com o Kit de Ferramentas do Microsoft Teams e Visual Studio Code
description: Introdução criar ótimos aplicativos personalizados diretamente Visual Studio Code com o Microsoft Teams Toolkit.
keywords: Kit de ferramentas do Visual Studio Code do Teams
ms.localizationpriority: medium
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: 4672c6be9629d70c50885ecd0d9d034c943a337a
ms.sourcegitcommit: 5070746e736edb4ae77cd3efcb2ab8bb2e5819a0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/16/2022
ms.locfileid: "66123073"
---
# <a name="build-apps-with-the-teams-toolkit-and-visual-studio-code"></a>Criar aplicativos com Teams Toolkit e Visual Studio Code

O Teams Toolkit para Visual Studio Code ajuda os desenvolvedores a criar e implantar aplicativos do Teams com identidade integrada, acesso ao armazenamento em nuvem, dados do Microsoft Graph e outros serviços no Azure e no Microsoft 365 com uma abordagem de "configuração zero" para a experiência do desenvolvedor.

Você também pode usar o kit de ferramentas com Visual Studio ou como uma CLI (chamada`teamsfx`).

## <a name="install-the-teams-toolkit-for-visual-studio-code"></a>Instalar o Teams Toolkit para Visual Studio Code

1. Abra o Visual Studio Code.
1. Selecione o modo de exibição Extensões (**Ctrl+Shift+X** / **⌘⇧-X** ou **Exibir > Extensões**).
1. Na caixa de pesquisa, insira _Teams Toolkit_.
1. Selecione o botão de instalação verde ao lado do Teams Toolkit.

Você também pode encontrar o Teams Toolkit no [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension).

As ferramentas a seguir são instaladas pela Visual Studio Code quando são necessárias. Se já estiver instalado, a versão instalada será usada em vez disso. Se estiver usando o Linux (incluindo o WSL), você deverá instalar essas ferramentas antes de usar:

- [Ferramentas do Azure Functions Core versão 3.](/azure/azure-functions/functions-run-local)

    Azure Functions Core Tools é usado para executar qualquer componente de back-end localmente durante uma execução de depuração local, incluindo os auxiliares de autenticação necessários ao executar seus serviços no Azure. Ele é instalado no diretório do projeto usando o npm `devDependencies`.

- [SDK DO .NET](/dotnet/core/install/)

    O SDK do .NET é usado para instalar associações personalizadas para depuração local e implantações Azure Functions aplicativo. Se você ainda não instalou o SDK do .NET 3.1 ou posterior globalmente, a versão portátil será instalada.

- [ngrok](https://ngrok.com/download)

    Alguns Teams de aplicativo (bots de conversa, extensões de mensagens e webhooks de entrada) exigem conexões de entrada.  Você precisa expor seu sistema de desenvolvimento para Teams por um túnel. Um túnel não é necessário para aplicativos que incluem apenas guias.  Esse pacote é instalado no diretório do projeto (usando npm`devDependencies`).

## <a name="use-the-teams-toolkit-for-visual-studio-code"></a>Use o Teams Toolkit para Visual Studio Code

- [Configurar um novo projeto](#set-up-a-new-teams-project)
- [Configurar seu aplicativo](#configure-your-app)
- [Executar seu aplicativo localmente](#install-and-run-your-app-locally)
- [Publicar seu aplicativo](#publish-your-app-to-teams)

## <a name="set-up-a-new-teams-project"></a>Configurar um novo Teams projeto

O Teams Toolkit pode criar React aplicativos hospedados no Azure ou SPFx Web Parts hospedadas em seu Microsoft 365 SharePoint ambiente. Para criar um novo React aplicativo a ser hospedado no Azure:

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

1. Opcionalmente, na etapa recursos **de nuvem** , selecione os recursos de nuvem que seu aplicativo usa. Você pode selecionar o acesso CRUD (criar, ler, atualizar e excluir) a uma tabela SQL ou uma API:

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-cloud-resources.png" alt-text="Captura de tela mostrando como adicionar recursos em nuvem ao seu novo aplicativo.":::

1. Na etapa **de Linguagem de** Programação, você pode escolher **JavaScript** ou **TypeScript**:

    :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-programming-languages.png" alt-text="Captura de tela mostrando como selecionar a linguagem de programação.":::

1. Selecione uma pasta do espaço de trabalho. Uma pasta é criada na pasta do workspace para o projeto que você está criando.

1. Insira um nome adequado para seu aplicativo, como `helloworld`. O nome do aplicativo deve consistir apenas de caracteres alfanuméricos. Pressione **Inserir** para continuar.

Seu Teams aplicativo é criado em alguns segundos. O aplicativo com scaffolding contém código para lidar com o logon único com Azure Active Directory acesso ao Microsoft Graph. Se você selecionou recursos do Azure, o código para esses recursos também estará disponível.

Para obter um passo a passo do processo SPFx criação e publicação, consulte [o tutorial SPFx.](../get-started/first-app-spfx.md)

## <a name="configure-your-app"></a>Configurar seu aplicativo

Em seu núcleo, o Teams aplicativo adota três componentes:

  1. O Microsoft Teams cliente (Web, desktop ou móvel) em que os usuários interagem com seu aplicativo.
  1. Um servidor que responde a solicitações de conteúdo que é exibido no Teams. Por exemplo, conteúdo da guia HTML ou um Cartão Adaptável do bot.
  1. Um Teams de aplicativos consiste em três arquivos:

      > [!div class="checklist"]
      >
      > - O manifest.json.
      > - Um [ícone de cor](../resources/schema/manifest-schema.md#icons) para seu aplicativo ser exibido no catálogo de aplicativos públicos ou da organização.
      > - Um [ícone de estrutura](../resources/schema/manifest-schema.md#icons) de tópicos para exibição na Teams de atividades.

O manifesto e os ícones são armazenados na `.fx` pasta do seu projeto antes de serem carregados para Teams. Quando um aplicativo é instalado, o Teams analisa o arquivo de manifesto para determinar as informações necessárias, como o nome do aplicativo e a URL em que os serviços estão localizados.

1. Para configurar seu aplicativo, navegue até a **guia Teams Toolkit** no Visual Studio Code.
1. Selecione **o Editor de** Manifesto **na Project** seção.

Editar os campos na página de detalhes do aplicativo atualiza o conteúdo do arquivo manifest.json que, por fim, é enviado como parte do pacote do aplicativo.

## <a name="install-and-run-your-app-locally"></a>Instalar e executar seu aplicativo localmente

Para compilar e executar seu aplicativo localmente:

1. No Visual Studio Code, pressione **F5** para executar seu aplicativo no modo de depuração.

   > Quando você executa o aplicativo pela primeira vez, todas as dependências são baixadas e o aplicativo é compilado.  Uma janela do navegador é aberta automaticamente quando a compilação é concluída. Isto pode levar de 3 a 5 minutos para ser concluído.

   O kit de ferramentas solicita que você instale um certificado local, se necessário. Esse certificado permite que o Teams carregue seu aplicativo a partir de `https://localhost`. Selecione Sim quando aparecer a seguinte caixa de diálogo:

   :::image type="content" source="../assets/images/teams-toolkit-v2/ssl-prompt.png" alt-text="Captura de tela mostrando como a solicitação de instalação de um certificado SSL para permitir que o Teams carregue seu aplicativo a partir do localhost.":::

1. O seu navegador da web é iniciado para executar o aplicativo. Se for solicitado a abrir o Microsoft Teams, selecione Cancelar para permanecer no navegador. Você também pode ser solicitado a alternar para o aplicativo Teams outras vezes. Selecione o aplicativo Web quando isso acontecer.

   :::image type="content" source="../assets/images/teams-toolkit-v2/launch-web-browser-and-pick-webapp.png" alt-text="Captura de tela mostrando como escolher a versão da web das equipes quando lançadas":::

1. Você pode ser solicitado a entrar. Nesse caso, entre com sua conta Microsoft 365 usuário.
1. Quando solicitado a instalar o aplicativo no Teams, pressione **Adicionar**.

Tanto o back-end quanto o front-end são conectados ao Visual Studio Code depurador. Isso permite que você defina pontos de interrupção em qualquer lugar em seu código e inspecione o estado.  Você também pode usar qualquer ferramenta de depuração de front-end (como o React Developer Tools) no navegador.  Para obter mais informações sobre a depuração no Visual Studio Code, examine [a documentação](https://code.visualstudio.com/Docs/editor/debugging).

## <a name="publish-your-app-to-teams"></a>Publicar seu aplicativo no Teams

Antes que ele possa ser usado por outras pessoas, você deve publicar seu aplicativo no Portal do Desenvolvedor para Teams.

1. Para publicar seu aplicativo, navegue até a **guia Teams Toolkit** no Visual Studio Code.
1. Selecione **Publicar em Teams** na **seção Project**.

Se estiver usando a hospedagem do Azure, você deverá ter provisionado e implantado na nuvem. Para obter um passo a passo do processo de SPFx publicação, consulte o [tutorial SPFx exemplo](../get-started/first-app-spfx.md).

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Mantendo e dando suporte ao aplicativo publicado](../concepts/deploy-and-publish/appsource/post-publish/overview.md)

## <a name="see-also"></a>Confira também

- [Criar aplicativos com o Kit de ferramentas do Teams para o Visual Studio](~/toolkit/visual-studio-overview.md)
- [Criar guias e outras experiências hospedadas com o SDK Microsoft Teams cliente JavaScript](~/tabs/how-to/using-teams-client-sdk.md)
