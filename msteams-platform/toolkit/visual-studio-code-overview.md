---
title: Criar aplicativos com o Microsoft Teams Toolkit e o Visual Studio Code
description: Introdução ao desenvolvimento de aplicativos personalizados de grande parte diretamente no Visual Studio Code com o Microsoft Teams Toolkit
keywords: Kit de ferramentas de código do Visual Studio
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: 41b0eeaeef1c7094fc9c8cbdc05c2db899245fc6
ms.sourcegitcommit: 7e47bf158249050c36d97509eea00e77089a54e6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "49476927"
---
# <a name="build-apps-with-the-teams-toolkit-and-visual-studio-code"></a>Criar aplicativos com o Teams Toolkit e o Visual Studio Code

O Microsoft Teams Toolkit permite que você crie aplicativos personalizados do teams diretamente no ambiente de código do Visual Studio. O kit de ferramentas orienta você durante o processo e oferece tudo o que você precisa para criar, depurar e iniciar o aplicativo Teams.

## <a name="installing-the-teams-toolkit"></a>Instalando o Teams Toolkit

O Microsoft Teams Toolkit para Visual Studio Code está disponível para download no [Visual Studio Marketplace](https://aka.ms/teams-toolkit) ou diretamente como uma extensão dentro do Visual Studio Code.

> [!TIP]
> Após a instalação, você deve ver o Teams Toolkit na barra de atividade de código do Visual Studio. Caso contrário, clique com o botão direito do mouse na barra de atividades e selecione **Microsoft Teams** para fixar o kit de ferramentas para facilitar o acesso.

## <a name="using-the-toolkit"></a>Usando o kit de ferramentas

- [Configurar um novo projeto](#set-up-a-new-teams-project)
- [Importar um projeto existente](#import-an-existing-teams-app-project)
- [Configurar seu aplicativo](#configure-your-app)
- [Empacotar seu aplicativo](#package-your-app)
- [Executar o aplicativo localmente ou no Teams](#run-your-app)

## <a name="set-up-a-new-teams-project"></a>Configurar um novo projeto do teams

1. Crie um espaço de trabalho/pasta para o seu projeto no seu ambiente local.
1. No Visual Studio Code, selecione o ícone Teams ![Ícone do Teams](../assets/icons/favicon-16x16.png) na barra de atividades no lado esquerdo da janela.
1. Selecione **abrir o Microsoft Teams Toolkit** no menu de comando.
1. Selecione **criar um novo aplicativo do teams** no menu de comando.
1. Quando solicitado, insira o nome do espaço de trabalho. Ele será usado como o nome da pasta onde o seu projeto residirá e o nome padrão do seu aplicativo.
1. Pressione **Enter** e você chegará à tela **Adicionar recursos** para configurar as propriedades do novo aplicativo.
1. Selecione o botão **concluir** para concluir o processo de configuração.

## <a name="import-an-existing-teams-app-project"></a>Importar um projeto de aplicativo do teams existente

1. No Visual Studio Code, selecione o ícone Teams ![Ícone do Teams](../assets/icons/favicon-16x16.png) na barra de atividades no lado esquerdo da janela.
1. Selecione **Importar pacote de aplicativos** no menu de comandos.
1. Escolha seu arquivo zip do [pacote de aplicativos do teams](../concepts/build-and-test/apps-package.md) existente.
1. Escolha o botão **selecionar pacote de publicação** . A guia de configuração do kit de ferramentas deve agora ser preenchida com os detalhes do seu aplicativo.
1. No Visual Studio Code, selecione **arquivo**  ->  **Adicionar pasta ao espaço de trabalho** para adicionar seu diretório de código-fonte ao espaço de trabalho do código do Visual Studio.

## <a name="configure-your-app"></a>Configurar seu aplicativo

Em seu núcleo, o aplicativo Teams engloba três componentes:

  1. O cliente Microsoft Teams (Web, desktop ou celular) onde os usuários interagem com seu aplicativo.
  1. Um servidor que responde às solicitações de conteúdo que será exibido no Microsoft Teams, por exemplo, o conteúdo da guia HTML ou um cartão adaptável de bot.
  1. Um [pacote de aplicativos](/concepts/build-and-test/apps-package.md) do teams que consiste em três arquivos:

  > [!div class="checklist"]
  >
  > - O manifest.jsem 
  > - Um [ícone de cor](../resources/schema/manifest-schema.md#icons) para seu aplicativo exibir no catálogo de aplicativos públicos ou de organização
 > - Um [ícone de estrutura de tópicos](../resources/schema/manifest-schema.md#icons) para exibição na barra de atividades do Microsoft Teams.

Quando um aplicativo é instalado, o cliente do teams analisa o arquivo de manifesto para determinar as informações necessárias, como o nome do seu aplicativo e a URL onde os serviços estão localizados.

1. Para configurar seu aplicativo, navegue até a guia **Microsoft Teams Toolkit** no Visual Studio Code.
1. Selecione **Editar pacote de aplicativos** para exibir a página de **detalhes do aplicativo** .
1. A edição dos campos na página de detalhes do aplicativo atualiza o conteúdo do manifest.jsem um arquivo que será fornecido como parte do pacote de aplicativos. *Consulte* [Editor de manifesto do App Studio](https://aka.ms/teams-toolkit-manifest)

## <a name="package-your-app"></a>Empacotar seu aplicativo

A modificação da página de **detalhes do aplicativo** ou a atualização do **manifesto** ou arquivos **. env** na pasta do seu aplicativo  **. publish** gerará automaticamente seu arquivo de **Development.zip** . Você precisará incluir [dois ícones](../concepts/build-and-test/apps-package.md#icons) na mesma pasta.

## <a name="run-your-app"></a>Executar o aplicativo

### <a name="install-and-run-your-app-locally"></a>Instalar e executar o aplicativo localmente

Confira o **Compilar e executar* o conteúdo na página inicial do seu projeto para obter instruções detalhadas sobre como empacotar e testar seu aplicativo. Em geral, você precisa instalar o servidor do aplicativo, fazê-lo em execução e, em seguida, configurar uma solução de encapsulamento para que o Microsoft Teams possa acessar o conteúdo em execução do localhost.

### <a name="enable-development-from-localhost"></a>Habilitar o desenvolvimento do localhost

Se quiser depurar seu aplicativo baseado em guia no localhost usando HTTPS, você precisará informar ao seu navegador para confiar no aplicativo que está sendo servido <https://localhost> . Navegue até <https://localhost:3000/tab>. Se você vir um aviso indicando que o site não é confiável, escolha a opção para continuar mesmo assim. Agora, seu aplicativo deve estar acessível no cliente do teams.

### <a name="run-your-app-in-teams"></a>Executar o aplicativo no Microsoft Teams

Pré-requisitos: [habilitar o modo de visualização do desenvolvedor do teams](https://aka.ms/teams-toolkit-enable-devpreview)

1. Navegue até a barra de atividade no lado esquerdo da janela de código do Visual Studio.
1. Selecione o ícone **executar** para exibir o modo de exibição **executar e depurar** .
1. Você também pode usar o atalho de teclado `Ctrl+Shift+D` .

> [!div class="nextstepaction"]
> [Próxima etapa: manutenção e suporte do seu aplicativo publicado](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
