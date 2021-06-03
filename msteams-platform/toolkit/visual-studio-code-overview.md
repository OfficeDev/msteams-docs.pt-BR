---
title: Criar aplicativos com o Microsoft Teams Toolkit e Visual Studio Code
description: Começar a criar excelentes aplicativos personalizados diretamente Visual Studio Code com o Microsoft Teams Toolkit
keywords: kit de ferramentas de código do visual studio do teams
localization_priority: Normal
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: bc97a78df5618c87dfc66fae179145acd749ad1f
ms.sourcegitcommit: 33a43c61f27ae750776616b2cf90159455d8ba6c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2021
ms.locfileid: "52721819"
---
# <a name="build-apps-with-the-teams-toolkit-and-visual-studio-code"></a>Criar aplicativos com o Teams Toolkit e Visual Studio Code

O Teams Toolkit para Visual Studio Code ajuda os desenvolvedores a criar e implantar aplicativos Teams com identidade integrada, acesso ao armazenamento em nuvem, dados do Microsoft Graph e outros serviços no Azure e M365 com uma abordagem de "configuração zero" para a experiência do desenvolvedor.  

Você também pode usar o kit de ferramentas com Visual Studio ou como uma CLI (chamada `teamsfx` ).

## <a name="install-the-teams-toolkit-for-visual-studio-code"></a>Instale o Teams Toolkit para Visual Studio Code

1. Abra o Visual Studio Code.
1. Selecione o exibição Extensões (**Ctrl+Shift+X**  /  **⌘⇧-X** ou **Exibir > Extensões).**
1. Na caixa de pesquisa, digite _Teams Toolkit_.
1. Selecione no botão de instalação verde ao lado do Teams Toolkit.

Você também pode encontrar o Teams Toolkit no [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension).

As ferramentas a seguir serão instaladas pela extensão Visual Studio Code quando elas são necessárias.  Se já estiver instalada, a versão instalada será usada em vez disso.  Se estiver usando o Linux (incluindo o WSL), você deve instalar essas ferramentas antes de usar:

- [Ferramentas principais das funções do Azure](/azure/azure-functions/functions-run-local)

    As Ferramentas Principais de Funções do Azure são usadas para executar qualquer componente back-end localmente durante uma execução de depuração local, incluindo os auxiliares de autenticação necessários ao executar seus serviços no Azure.  Ele é instalado no diretório do projeto (usando o npm `devDependencies` ).

- [.NET SDK](/dotnet/core/install/)

    O .NET SDK é usado para instalar vinculações personalizadas para implantações de aplicativos de depuração local e funções do Azure.  Se você não tiver instalado o SDK .NET 3.1 (ou posterior) globalmente, a versão portátil será instalada.

- [ngrok](https://ngrok.com/download)

    Alguns Teams de aplicativo (bots de conversação, extensões de mensagens e webhooks de entrada) exigem conexões de entrada.  Você precisa expor seu sistema de desenvolvimento para Teams através de um túnel.  Um túnel não é necessário para aplicativos que incluem apenas guias.  Este pacote é instalado no diretório do projeto (usando npm `devDependencies` ).

## <a name="use-the-teams-toolkit-for-visual-studio-code"></a>Use o Teams Toolkit para Visual Studio Code

- [Configurar um novo projeto](#set-up-a-new-teams-project)
- [Configurar seu aplicativo](#configure-your-app)
- [Executar seu aplicativo localmente](#install-and-run-your-app-locally)
- [Publicar seu aplicativo](#publish-your-app-to-teams)

## <a name="set-up-a-new-teams-project"></a>Configurar um novo Teams projeto

O Teams Toolkit pode criar React aplicativos que serão hospedados no Azure ou SPFx Web Parts que serão hospedados em seu ambiente de SharePoint M365.  Para criar um novo React para ser hospedado no Azure:

1. Abra o Visual Studio Code.
1. Abra o Kit de ferramentas do Teams selecionando o ícone do Teams na barra lateral:

    :::image type="content" source="../assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="O ícone do Teams na barra lateral do Visual Studio Code":::

1. Selecione **Criar Novo Projeto**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project.png" alt-text="Localização do link de Criação de Novo Projeto na barra lateral do Kit de ferramentas do Teams.":::

1. Selecione **Criar um novo aplicativo do Teams**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-new-project-intro.png" alt-text="Início do assistente para Criar Novo Projeto":::

1. Na etapa **Selecionar capacidades**, a capacidade da **Guia** já será selecionada.  Você também pode, opcionalmente, selecionar **Bot** e **Extensão de Mensagens.**  Pressione **OK**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-capabilities.png" alt-text="Captura de tela mostrando como adicionar capacidades ao seu novo aplicativo.":::

1. Na etapa **Tipo de hospedagem front-end**, selecione **Azure**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-hosting.png" alt-text="Captura de tela mostrando como selecionar a hospedagem para seu novo aplicativo.":::

1. (Opcional) Na etapa **Recursos de nuvem,** selecione recursos de nuvem que seu aplicativo usará.  Você pode selecionar CRUD (criar, ler, atualizar, excluir) acesso a uma SQL ou uma API:

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-cloud-resources.png" alt-text="Captura de tela mostrando como adicionar recursos em nuvem ao seu novo aplicativo.":::

1. Na etapa **Linguagem de Programação,** você pode escolher **JavaScript** ou **TypeScript**:

    :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-programming-languages.png" alt-text="Captura de tela mostrando como selecionar a linguagem de programação.":::

1. Selecione uma pasta do espaço de trabalho.  Uma pasta será criada dentro de sua pasta do espaço de trabalho para o projeto que você está criando.

1. Insira um nome adequado para seu aplicativo, como `helloworld`.  O nome do aplicativo deve consistir apenas de caracteres alfanuméricos.  Pressione **Inserir** para continuar.

O seu aplicativo do Teams será criado em alguns segundos.  O aplicativo scaffolded contém código para manipular o login único com Azure Active Directory acesso ao microsoft Graph.  Se você selecionou os recursos do Azure, o código para esses recursos também estará disponível.

Para ver um passo a passo do processo SPFx criação e publicação, consulte o [tutorial SPFx .](../get-started/first-app-spfx.md)

## <a name="configure-your-app"></a>Configurar seu aplicativo

No seu núcleo, o Teams aplicativo abrange três componentes:

  1. O Microsoft Teams cliente (Web, desktop ou móvel) onde os usuários interagem com seu aplicativo.
  1. Um servidor que responde a solicitações de conteúdo que serão exibidas em Teams. Por exemplo, conteúdo de guia HTML ou um cartão adaptável de bot.
  1. Um Teams de aplicativo consiste em três arquivos:

      > [!div class="checklist"]
      >
      > - A manifest.jsestá.
      > - Um [ícone de cor](../resources/schema/manifest-schema.md#icons) para seu aplicativo ser exibido no catálogo de aplicativos público ou da organização.
      > - Um [ícone de contorno](../resources/schema/manifest-schema.md#icons) para exibição na barra de Teams de atividades.

O manifesto e os ícones são armazenados na pasta do seu projeto antes `.fx` de serem carregados para Teams. Quando um aplicativo é instalado, o cliente Teams analisado o arquivo de manifesto para determinar as informações necessárias, como o nome do seu aplicativo e a URL onde os serviços estão localizados.

1. Para configurar seu aplicativo, navegue até a guia **Teams Toolkit** no Visual Studio Code.
1. Selecione **Editor de Manifesto** na seção **Project.**

A edição dos campos na página detalhes do aplicativo atualiza o conteúdo do arquivo manifest.jsno arquivo que, em última análise, será shipado como parte do pacote de aplicativos.

## <a name="install-and-run-your-app-locally"></a>Instalar e executar seu aplicativo localmente

Para compilar e executar seu aplicativo localmente:

1. No Visual Studio Code, pressione **F5** para executar seu aplicativo no modo de depuração.

   > Quando você executa o aplicativo pela primeira vez, todas as dependências são baixadas e o aplicativo é compilado.  Uma janela do navegador é aberta automaticamente quando a compilação é concluída.  Isto pode levar de 3 a 5 minutos para ser concluído.

   O kit de ferramentas solicitará que você instale um certificado local, se necessário. Esse certificado permite que o Teams carregue seu aplicativo a partir de `https://localhost`. Selecione Sim quando aparecer a seguinte caixa de diálogo:

   :::image type="content" source="../assets/images/teams-toolkit-v2/ssl-prompt.png" alt-text="Captura de tela mostrando como a solicitação de instalação de um certificado SSL para permitir que o Teams carregue seu aplicativo a partir do localhost.":::

1. O seu navegador da web é iniciado para executar o aplicativo. Se for solicitado a abrir o Microsoft Teams, selecione Cancelar para permanecer no navegador. Você também pode ser solicitado a alternar para o aplicativo Teams outras vezes. Selecione o aplicativo Web quando isso acontecer.

   :::image type="content" source="../assets/images/teams-toolkit-v2/launch-web-browser-and-pick-webapp.png" alt-text="Captura de tela mostrando como escolher a versão da web das equipes quando lançadas":::

1. Você pode ser solicitado a entrar.  Em caso afirmativo, entre com sua conta M365.
1. Quando solicitado a instalar o aplicativo no Teams, pressione **Adicionar**.

Tanto o back-end quanto o front-end são conectados ao Visual Studio Code depurador.  Isso permite definir pontos de interrupção em qualquer lugar em seu código e inspecionar o estado.  Você também pode usar qualquer ferramenta de depuração de front-end (como o React Ferramentas de Desenvolvedor) no navegador.  Para obter mais informações sobre a depuração Visual Studio Code, revise [a documentação](https://code.visualstudio.com/Docs/editor/debugging).

## <a name="publish-your-app-to-teams"></a>Publicar seu aplicativo no Teams

Antes que ele possa ser usado por outras pessoas, você deve publicar seu aplicativo no Portal do Desenvolvedor para Teams.

1. Para publicar seu aplicativo, navegue até a **guia Teams Toolkit** no Visual Studio Code.
1. Selecione **Publicar no Teams** na seção **Project.**

Se estiver usando a hospedagem do Azure, você deverá ter provisionado e implantado na nuvem. Para ver um passo a passo do processo SPFx publicação, consulte o [tutorial SPFx .](../get-started/first-app-spfx.md)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Mantendo e dando suporte ao aplicativo publicado](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
