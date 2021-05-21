---
title: Criar aplicativos com o Microsoft Teams Toolkit e Visual Studio Code
description: Começar a criar excelentes aplicativos personalizados diretamente Visual Studio Code com o Microsoft Teams Toolkit
keywords: kit de ferramentas de código do visual studio do teams
localization_priority: Normal
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: efd0962e9c4c0d64dbac47caf29b2e56907937b3
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566555"
---
# <a name="build-apps-with-the-teams-toolkit-and-visual-studio-code"></a>Criar aplicativos com o Teams Toolkit e Visual Studio Code

O Kit de Ferramentas do Microsoft Teams permite criar aplicativos personalizados do Teams diretamente no ambiente do Visual Studio Code. O kit de ferramentas guia você através do processo e fornece o necessário para criar, depurar e iniciar seu aplicativo do Teams.

## <a name="installing-the-teams-toolkit"></a>Instalando o Teams Toolkit

O Microsoft Teams Toolkit para Visual Studio Code está disponível para download do [Visual Studio Marketplace](https://aka.ms/teams-toolkit) ou diretamente como uma extensão dentro Visual Studio Code.

> [!TIP]
> Após a instalação, você deve ver o Teams Toolkit na barra de Visual Studio Code de atividade. Se não, clique com o botão direito do mouse na barra de atividades e selecione **Microsoft Teams** fixar o kit de ferramentas para facilitar o acesso.

## <a name="using-the-toolkit"></a>Usando o kit de ferramentas

- [Configurar um novo projeto](#set-up-a-new-teams-project)
- [Importar um projeto existente](#import-an-existing-teams-app-project)
- [Configurar seu aplicativo](#configure-your-app)
- [Empacote seu aplicativo](#package-your-app)
- [Execute seu aplicativo localmente ou em Teams](#run-your-app)

## <a name="set-up-a-new-teams-project"></a>Configurar um novo Teams projeto

1. Crie um espaço de trabalho ou pasta para seu projeto em seu ambiente local.
1. Em Visual Studio Code, selecione o Teams ícone ![Ícone do Teams](../assets/icons/favicon-16x16.png) da barra de atividades no lado esquerdo da janela.
1. Selecione **Abrir o Microsoft Teams Toolkit** no menu de comando.
1. Selecione **Criar um novo aplicativo Teams no** menu de comando.
1. Quando solicitado, digite o nome do espaço de trabalho . Isso será usado como o nome da pasta onde seu projeto irá residir e o nome padrão do seu aplicativo.
1. Pressione **Enter** e você chegará à tela **Adicionar recursos** configurar as propriedades do seu novo aplicativo.
1. Selecione o **botão Concluir** para concluir o processo de configuração.

## <a name="import-an-existing-teams-app-project"></a>Importar um projeto de aplicativo Teams existente

1. Em Visual Studio Code, selecione o Teams ícone ![Ícone do Teams](../assets/icons/favicon-16x16.png) da barra de atividades no lado esquerdo da janela.
1. Selecione **Importar pacote de aplicativos** no menu de comando.
1. Escolha o arquivo zip do [pacote Teams aplicativo](../concepts/build-and-test/apps-package.md) existente.
1. Escolha o **botão Selecionar pacote de publicação.** A guia de configuração do kit de ferramentas agora deve ser preenchida com os detalhes do aplicativo.
1. Em Visual Studio Code, selecione **Adicionar** Pasta de Arquivo ao Espaço de Trabalho para adicionar seu diretório de código-fonte  ->   ao Visual Studio Code de trabalho.

## <a name="configure-your-app"></a>Configurar seu aplicativo

No seu núcleo, o Teams aplicativo abrange três componentes:

  1. O Microsoft Teams cliente (Web, desktop ou móvel) onde os usuários interagem com seu aplicativo.
  1. Um servidor que responde a solicitações de conteúdo que serão exibidas em Teams. Por exemplo, conteúdo de guia HTML ou um cartão adaptável de bot.
  1. Um Teams [de aplicativos](/concepts/build-and-test/apps-package.md) que consiste em três arquivos:

      > [!div class="checklist"]
      >
      > - A manifest.jsestá. 
      > - Um [ícone de cor](../resources/schema/manifest-schema.md#icons) para seu aplicativo ser exibido no catálogo de aplicativos público ou da organização.
      > - Um [ícone de contorno](../resources/schema/manifest-schema.md#icons) para exibição na barra de Teams de atividades.

Quando um aplicativo é instalado, o cliente Teams analisado o arquivo de manifesto para determinar as informações necessárias, como o nome do seu aplicativo e a URL onde os serviços estão localizados.

1. Para configurar seu aplicativo, navegue até a **guia Microsoft Teams Toolkit** no Visual Studio Code.
1. Selecione **Editar pacote de aplicativos** para exibir a página Detalhes **do** aplicativo.
1. A edição dos campos na página detalhes do aplicativo atualiza o conteúdo do arquivo manifest.jsno arquivo que, em última análise, será shipado como parte do pacote de aplicativos. Para obter mais informações, consulte [Editor de manifesto do App Studio](https://aka.ms/teams-toolkit-manifest)

## <a name="package-your-app"></a>Empacote seu aplicativo

Modificar a **página de** detalhes do aplicativo, os arquivos de manifesto ou **.env** na pasta **.publish** do aplicativo gerará automaticamente seu **arquivoDevelopment.zip.**  Você precisará incluir dois [ícones](../concepts/build-and-test/apps-package.md#app-icons) na mesma pasta.

## <a name="install-and-run-your-app-locally"></a>Instalar e executar seu aplicativo localmente

## <a name="run-your-app"></a>Executar seu aplicativo

### <a name="install-and-run-your-app-locally"></a>Instalar e executar seu aplicativo localmente

Consulte a **página inicial criar e** executar conteúdo em seu projeto para obter instruções detalhadas sobre como empacotar e testar seu aplicativo. Em geral, você precisa instalar o servidor do aplicativo, fazer com que ele seja executado e, em seguida, configurar uma solução de tunelamento para que Teams possa acessar o conteúdo executado do localhost.

### <a name="enable-development-from-localhost"></a>Habilitar o desenvolvimento do localhost

Se você deseja depurar seu aplicativo baseado em guia em localhost usando HTTPS, você precisará dizer ao navegador para confiar no aplicativo que está sendo servido de <https://localhost> . Navegue até <https://localhost:3000/tab>. Se você vir um aviso indicando que o site não é confiável, escolha a opção para prosseguir de qualquer maneira. Seu aplicativo agora deve estar acessível a partir do Teams cliente.

### <a name="run-your-app-in-teams"></a>Execute seu aplicativo em Teams

Pré-requisitos: [Habilitar Teams modo de visualização do desenvolvedor](https://aka.ms/teams-toolkit-enable-devpreview)

1. Navegue até a barra de atividades no lado esquerdo da janela Visual Studio Code.
1. Selecione o **ícone Executar** para exibir o **exibição Executar e Depurar.**
1. Você também pode usar o atalho do teclado `Ctrl+Shift+D` .

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Mantendo e dando suporte ao aplicativo publicado](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
