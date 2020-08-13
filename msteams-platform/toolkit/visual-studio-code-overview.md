---
title: Criar aplicativos com o Microsoft Teams Toolkit e o Visual Studio Code
description: Introdução ao desenvolvimento de aplicativos personalizados de grande parte diretamente no Visual Studio Code com o Microsoft Teams Toolkit
keywords: Kit de ferramentas de código do Visual Studio
ms.openlocfilehash: 7b8a32c099d85bec2584da2b42dcf5a524ecddbc
ms.sourcegitcommit: 9fbc701a9a039ecdc360aefbe86df52b9c3593f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/12/2020
ms.locfileid: "46651660"
---
# <a name="build-apps-with-the-microsoft-teams-toolkit-and-visual-studio-code"></a>Criar aplicativos com o Microsoft Teams Toolkit e o Visual Studio Code

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
- [Executar o aplicativo no Microsoft Teams](#run-your-app-in-teams)
- [Validar seu aplicativo](#validate-your-app)
- [Publicar seu aplicativo](#publish-your-app-to-teams)

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
1. A edição dos campos na página de detalhes do aplicativo atualiza o conteúdo do manifest.jsem um arquivo que será fornecido como parte do pacote de aplicativos. [Saiba Mais](https://aka.ms/teams-toolkit-manifest)

## <a name="package-your-app"></a>Empacotar seu aplicativo

Modificar você é a página de **detalhes do aplicativo** ou atualizar o **manifesto**, ou arquivos **. env** na pasta do seu aplicativo  **. publish** irá gerar automaticamente seu arquivo de **Development.zip** . Você precisará incluir [dois ícones](../concepts/build-and-test/apps-package.md#icons) na mesma pasta.

## <a name="install-and-run-your-app-locally"></a>Instalar e executar o aplicativo localmente

Confira o **Compilar e executar* conteúdo em sua página inicial do projeto para obter instruções detalhadas para empacotar e testar seu aplicativo. Em geral, você precisa instalar o servidor do aplicativo, fazê-lo em execução e, em seguida, configurar uma solução de encapsulamento para que o Microsoft Teams possa acessar o conteúdo em execução do localhost.

## <a name="add-a-trusted-certificate-for-localhost"></a>Adicionar um certificado confiável para localhost

Se você quiser depurar seu aplicativo baseado em guia no localhost usando HTTPS, será necessário adicionar um certificado para localhost ao `Trusted Root Certification Authorities` catálogo. Você só precisa concluir esta etapa uma vez por máquina.</br></br>

**Criar e instalar um certificado confiável:**
<details>
  <summary>Expanda aqui</summary>

* Criar e executar o aplicativo
  * Siga o instuctions na seção **criar e executar** do Leiame do projeto para que ele seja atendido https://localhost:3000/tab . Geralmente, isso envolverá a `npm install` execução `npm start`
  * Navegue até https://localhost:3000/tab no Google Chrome ou borda Chromium.

* Adquirir o certificado SSL:
  * Abra a janela do Chrome Developer Tools ( `ctrl + shift + i`  /  `cmd + option + i` ).
  * Clique na `Security` guia
  * Clique em `View certificate` e você terá a opção de baixar o certificado, arrastando-o para sua área de trabalho no os X, ou clicando na `Details` guia no Windows e clicando em `Copy to File…`
  * Nomeie o arquivo <*tudo*>. cer e salve-o em uma pasta que não exija consentimento do administrador para executar uma ação de gravação.
  
* Instalar o certificado no **Windows**
  * Escolha a `DER encoded binary X.509 (.CER)` opção (a primeira) e salve-a.
  * Clique duas vezes no certificado e instale-o.
  * Escolha `Local Machine`
  * Seleção `Place all certificates in the following store`
  * Escolha `Trusted Root Certification Authorities`
  * Confirmar sua instalação
  
* Instalar o certificado **Mac os X**
  * No OS X, abra o utilitário de acesso de chaves e selecione `System` no menu à esquerda. Clique no ícone de cadeado para habilitar as alterações.
  * Clique no botão de adição próximo à parte inferior para adicionar um novo certificado e selecione o `localhost.cer` arquivo que você arrastou para a área de trabalho. Clique `Always Trust` na caixa de diálogo exibida.
  * Após adicionar o certificado ao chaveiro do sistema, clique duas vezes no certificado e expanda a `Trust` seção dos detalhes do certificado. Selecione `Always Trust` para cada opção.

> [!IMPORTANT]
> Se você receber um aviso de certificado de segurança, navegue até https://localhost:3000/tab . Se o site ainda não for confiável, reinicie seu computador e localhost deverá ser aceito como confiável.
</details>

## <a name="run-your-app-in-teams"></a>Executar o aplicativo no Microsoft Teams
- Pré-requisitos:
  - [Habilitar o modo de visualização do desenvolvedor do teams](https://aka.ms/teams-toolkit-enable-devpreview)

1. Navegue até a barra de atividade no lado esquerdo da janela de código do Visual Studio.
1. Selecione o ícone **executar** para exibir o modo de exibição **executar e depurar** .
1. Você também pode usar o atalho de teclado `Ctrl+Shift+D` .

## <a name="validate-your-app"></a>Validar seu aplicativo

A página **validar** permite verificar o pacote do aplicativo antes de enviar o aplicativo para o AppSource. Basta carregar o pacote de manifesto e a ferramenta de validação verificará seu aplicativo em todos os casos de teste relacionados ao manifesto. Para cada teste com falha, a descrição fornece um link de documentação para ajudá-lo a corrigir o erro. Para os testes difíceis de automatizar, a lista de **verificação preliminar** detalha 7 dos casos de teste com falha mais comuns, bem como vincular a uma lista de verificação de envio completa.

## <a name="publish-your-app-to-teams"></a>Publicar seu aplicativo no Teams

Na home page do seu projeto, você pode carregar seu aplicativo para uma equipe, enviar seu aplicativo para o repositório de aplicativos personalizado da empresa para usuários em sua organização ou enviar seu aplicativo para a origem do aplicativo para todos os usuários do teams. Seu administrador de ti revisará esses envios. Você pode retornar à página *publicar* para verificar seu status de envio e saber se seu aplicativo foi aprovado ou rejeitado pelo seu administrador de ti. Este também é o local em que você vai enviar atualizações para seu aplicativo ou cancelar qualquer envio ativo no momento.

> [!div class="nextstepaction"]
> [Próxima etapa: manutenção e suporte do seu aplicativo publicado](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
