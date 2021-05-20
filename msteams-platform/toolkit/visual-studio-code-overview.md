---
title: Crie aplicativos com o Microsoft Teams Toolkit e Visual Studio Code
description: Comece a construir ótimos aplicativos personalizados diretamente dentro de Visual Studio Code com o Microsoft Teams Toolkit
keywords: equipes estúdio visual código kit ferramentas
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
# <a name="build-apps-with-the-teams-toolkit-and-visual-studio-code"></a>Crie aplicativos com os Teams Toolkit e Visual Studio Code

O Kit de Ferramentas do Microsoft Teams permite criar aplicativos personalizados do Teams diretamente no ambiente do Visual Studio Code. O kit de ferramentas guia você através do processo e fornece o necessário para criar, depurar e iniciar seu aplicativo do Teams.

## <a name="installing-the-teams-toolkit"></a>Instalando o Teams Toolkit

O Microsoft Teams Toolkit para Visual Studio Code está disponível para download no [Visual Studio Marketplace](https://aka.ms/teams-toolkit) ou diretamente como uma extensão dentro de Visual Studio Code.

> [!TIP]
> Após a instalação, você deve ver o Teams Toolkit na barra de atividades Visual Studio Code. Caso não, clique com o botão direito do mouse na barra de atividades e selecione **Microsoft Teams** para fixar o kit de ferramentas para fácil acesso.

## <a name="using-the-toolkit"></a>Usando o kit de ferramentas

- [Criar um novo projeto](#set-up-a-new-teams-project)
- [Importar um projeto existente](#import-an-existing-teams-app-project)
- [Configure seu aplicativo](#configure-your-app)
- [Empacote seu aplicativo](#package-your-app)
- [Execute seu aplicativo localmente ou em Teams](#run-your-app)

## <a name="set-up-a-new-teams-project"></a>Criar um novo projeto de Teams

1. Crie um espaço de trabalho ou pasta para o seu projeto em seu ambiente local.
1. Em Visual Studio Code, selecione o ícone Teams ![Ícone do Teams](../assets/icons/favicon-16x16.png) da barra de atividade no lado esquerdo da janela.
1. Selecione **Abrir o Microsoft Teams Toolkit** no menu de comando.
1. Selecione **Criar um novo aplicativo de Teams** no menu de comando.
1. Quando solicitado, digite o nome do espaço de trabalho . Isso será usado tanto como o nome da pasta onde seu projeto irá residir, quanto o nome padrão do seu aplicativo.
1. Pressione **Enter** e você chegará à tela **Adicionar recursos** configurar as propriedades para o seu novo aplicativo.
1. Selecione o botão **Terminar** para concluir o processo de configuração.

## <a name="import-an-existing-teams-app-project"></a>Importar um projeto de aplicativo de Teams existente

1. Em Visual Studio Code, selecione o ícone Teams ![Ícone do Teams](../assets/icons/favicon-16x16.png) da barra de atividade no lado esquerdo da janela.
1. Selecione **o pacote de aplicativos de importação** no menu de comando.
1. Escolha o arquivo zip do [pacote de Teams](../concepts/build-and-test/apps-package.md) existente.
1. Escolha o botão **Selecionar pacote de publicação.** A guia de configuração do kit de ferramentas deve agora ser preenchida com os detalhes do seu aplicativo.
1. Em Visual Studio Code, selecione **Arquivo**  ->  **Adicionar pasta ao espaço de trabalho** para adicionar seu diretório de código-fonte ao espaço de trabalho Visual Studio Code.

## <a name="configure-your-app"></a>Configure seu aplicativo

Em sua essência, o aplicativo Teams abraça três componentes:

  1. O Microsoft Teams cliente (web, desktop ou celular) onde os usuários interagem com seu aplicativo.
  1. Um servidor que responde a solicitações de conteúdo que será exibido em Teams. Por exemplo, conteúdo de guia HTML ou um cartão adaptativo de bot.
  1. Um [pacote de aplicativo](/concepts/build-and-test/apps-package.md) Teams composto por três arquivos:

      > [!div class="checklist"]
      >
      > - O manifest.js. 
      > - Um [ícone de cores](../resources/schema/manifest-schema.md#icons) para seu aplicativo ser exibido no catálogo do aplicativo público ou de organização.
      > - Um [ícone de contorno](../resources/schema/manifest-schema.md#icons) para exibição na barra de atividades Teams.

Quando um aplicativo é instalado, o cliente Teams analisa o arquivo manifesto para determinar informações necessárias, como o nome do seu aplicativo e a URL onde os serviços estão localizados.

1. Para configurar seu aplicativo, navegue até a guia **Microsoft Teams Toolkit** em Visual Studio Code.
1. Selecione **Editar pacote de aplicativo** para exibir a página de detalhes do **Aplicativo.**
1. A edição dos campos na página de detalhes do App atualiza o conteúdo do manifest.jsno arquivo que, em última análise, será enviado como parte do pacote do aplicativo. Para obter mais informações, consulte [o editor manifesto do App Studio](https://aka.ms/teams-toolkit-manifest)

## <a name="package-your-app"></a>Empacote seu aplicativo

Modificar os **detalhes** do aplicativo página, **manifesto** ou **arquivos .env** na pasta **.publish** do seu aplicativo gerará automaticamente o **seu arquivoDevelopment.zip.** Você precisará incluir [dois ícones](../concepts/build-and-test/apps-package.md#app-icons) na mesma pasta.

## <a name="install-and-run-your-app-locally"></a>Instale e execute seu aplicativo localmente

## <a name="run-your-app"></a>Execute seu aplicativo

### <a name="install-and-run-your-app-locally"></a>Instale e execute seu aplicativo localmente

Consulte o conteúdo **Build and Run** na página inicial do projeto para obter instruções detalhadas sobre como empacotar e testar seu aplicativo. Em geral, você precisa instalar o servidor do seu aplicativo, fazê-lo funcionar e, em seguida, configurar uma solução de tunelamento para que Teams possa acessar o conteúdo executado a partir do local.

### <a name="enable-development-from-localhost"></a>Permitir o desenvolvimento a partir do localhost

Se você deseja depurar seu aplicativo baseado em guia no localhost usando HTTPS, você precisará dizer ao seu navegador para confiar no aplicativo que está sendo servido <https://localhost> . Navegue até <https://localhost:3000/tab>. Se você vir um aviso indicando que o site não é confiável, escolha a opção de prosseguir de qualquer maneira. Seu aplicativo agora deve ser acessível a partir do cliente Teams.

### <a name="run-your-app-in-teams"></a>Execute seu aplicativo em Teams

Pré-requisitos: [Habilitar Teams modo de visualização do desenvolvedor](https://aka.ms/teams-toolkit-enable-devpreview)

1. Navegue até a barra de atividade no lado esquerdo da janela Visual Studio Code.
1. Selecione o ícone **Executar** para exibir a **exibição de Executar e Depurar.**
1. Você também pode usar o atalho do teclado `Ctrl+Shift+D` .

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Mantendo e apoiando seu aplicativo publicado](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
