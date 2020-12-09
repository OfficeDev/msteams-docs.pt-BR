---
title: Criar aplicativos com o Microsoft Teams Toolkit e o Visual Studio
description: Introdução ao desenvolvimento de aplicativos personalizados de grande parte diretamente no Visual Studio com o Microsoft Teams Toolkit
keywords: Kit de ferramentas do Visual Studio Teams
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: a1221945659b2dd0f45bdd3a966d9b029ddcde09
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2020
ms.locfileid: "49604484"
---
# <a name="build-apps-with-the-teams-toolkit-and-visual-studio"></a>Criar aplicativos com o Teams Toolkit e o Visual Studio

O Microsoft Teams Toolkit permite que você crie aplicativos personalizados do teams diretamente no IDE (ambiente de desenvolvimento integrado) do Visual Studio. O Microsoft Teams Toolkit orienta você durante o processo e oferece tudo o que você precisa para criar, depurar e iniciar o aplicativo Teams.

## <a name="prerequisites"></a>Pré-requisitos

1. [Habilitar visualização do desenvolvedor](../resources/dev-preview/developer-preview-intro.md#enable-developer-preview)

1. Certifique-se de que o **<span>ASP.ne</span>T e o módulo de desenvolvimento da Web** foram adicionados à sua instância do Visual Studio. Você pode verificar seguindo as etapas descritas em [Modificar o Visual Studio adicionando ou removendo cargas de trabalho e](/visualstudio/install/modify-visual-studio?view=vs-2019&preserve-view=true) documentação de componente.

![módulo asp.net do Visual Studio](../assets/images/visual-studio-web-dev-module.png)

3. Se quiser testar seu aplicativo implantando-o a partir do Visual Studio, você precisará ter o IIS (serviços de informações da Internet) instalado em seu ambiente de desenvolvimento. O Visual Studio não inclui o IIS e ele não está incluído na configuração padrão do Windows 10, Windows 8 ou Windows 7; no entanto, você pode baixar a versão mais recente no [centro de download da Microsoft](https://www.microsoft.com/download/details.aspx?id=48264).

![Exibição da página de download do IIS](../assets/images/iis.png)

## <a name="install-the-teams-toolkit"></a>Instalar o kit de ferramentas do teams

O Microsoft Teams Toolkit para Visual Studio está disponível para download no [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.vsteamstemplate) ou diretamente a partir do menu **Extensions** no Visual Studio.

## <a name="using-the-toolkit"></a>Usando o kit de ferramentas

- [Configurar um novo projeto](#set-up-a-new-teams-project)
- [Configurar seu aplicativo](#configure-your-app)
- [Empacotar seu aplicativo](#package-your-app)
- [Executar o aplicativo no Microsoft Teams](#install-and-run-your-app-locally)
- [Validar seu aplicativo](#validate-your-app)
- [Publicar seu aplicativo](#publish-your-app-to-teams)

## <a name="set-up-a-new-teams-project"></a>Configurar um novo projeto do teams

1. Selecione **criar um novo projeto**.
1. Escolha **aplicativo Microsoft Teams** e selecione **Avançar**.
1. Você chegará à tela **configurar seu novo projeto** , onde você pode escolher o **nome do projeto**, o **local** e o **nome da solução**.
1. Marque a caixa rotulada **Colocar solução e projeto no mesmo diretório**.
1. Uma janela pop-up com o rótulo **Adicionar recursos** permitirá que você escolha um ou mais recursos para a configuração do projeto.
1. Selecione o botão **Avançar** para concluir o processo de configuração.
1. Uma janela pop-up com o rótulo **Adicionar recursos** permitirá que você escolha as propriedades para cada recurso selecionado.
1. Selecione **concluir** e você irá parar na página inicial do **Microsoft Teams Toolkit** .

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

> [!NOTE]
>Caso ainda não tenha feito isso, você precisará entrar no seu Microsoft 365 ou conta para continuar com o processo de desenvolvimento.
>
> Se você não tem uma conta da Microsoft 365, você pode se inscrever para uma assinatura do [microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program) . É *grátis* por 90 dias e será renovado continuamente, desde que você o esteja usando para a atividade de desenvolvimento. Se você tiver uma assinatura do Visual Studio *Enterprise* ou *Professional* , ambos os programas incluirão uma [assinatura](https://aka.ms/MyVisualStudioBenefits)gratuita de desenvolvedor do Microsoft 365, ativa pela vida da sua assinatura do Visual Studio. *Confira* [Configurar uma assinatura de desenvolvedor do Microsoft 365](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started).
>

### <a name="configuration-steps"></a>Etapas de configuração

1. Para configurar seu aplicativo, na página inicial do **Microsoft Teams Toolkit** , selecione **Editar pacote de aplicativos** .
1. No menu suspenso **meus ambientes** , selecione **desenvolvimento**.
1. Você vai parar na página de **detalhes do aplicativo** , onde você pode editar os campos de Propriedade do seu aplicativo.
1. A edição dos campos na página de detalhes do aplicativo atualiza o conteúdo do manifest.jsem um arquivo que será fornecido como parte do pacote de aplicativos. [Saiba mais](https://aka.ms/teams-toolkit-manifest)

## <a name="package-your-app"></a>Empacotar seu aplicativo

A modificação da página de **detalhes do aplicativo** ou a atualização do **manifesto** ou arquivos **. env** na pasta do seu aplicativo  **. publish** gerará automaticamente seu arquivo de **Development.zip** . O arquivo Development.zip inclui três arquivos necessários: o **manifest.jsem** e [dois ícones](../concepts/build-and-test/apps-package.md#app-icons).

## <a name="install-and-run-your-app-locally"></a>Instalar e executar o aplicativo localmente

1. No menu suspenso **configurações de solução** , selecione **implantar**.

![Menu configurações de solução](../assets/images/solution-configurations.png)

2. Selecione o botão **ISS Express + Teams** .

1. O Microsoft Teams será iniciado e a caixa de diálogo de instalação do aplicativo deverá aparecer no cliente do teams.

## <a name="validate-your-app"></a>Validar seu aplicativo

A página **validar** permite verificar o pacote do aplicativo antes de enviar o aplicativo para o AppSource. Basta carregar o pacote de manifesto e a ferramenta de validação verificará seu aplicativo em todos os casos de teste relacionados ao manifesto. Para cada teste com falha, a descrição fornece um link de documentação para ajudá-lo a corrigir o erro. Para os testes difíceis de automatizar, a lista de **verificação preliminar** detalha 7 dos casos de teste com falha mais comuns, bem como vincular a uma lista de verificação de envio completa.

## <a name="publish-your-app-to-teams"></a>Publicar seu aplicativo no Teams

✔ Na home page do seu projeto, você pode carregar seu aplicativo para uma equipe, enviar seu aplicativo para o repositório de aplicativos personalizado da empresa para usuários em sua organização ou enviar seu aplicativo para a origem do aplicativo para todos os usuários do teams.

✔ Seu administrador de ti revisará esses envios.

✔ Você pode retornar à página **publicar** para verificar seu status de envio e saber se seu aplicativo foi aprovado ou rejeitado pelo seu administrador de ti. Este também é o local em que você vai enviar atualizações para seu aplicativo ou cancelar qualquer envio ativo no momento.

> [!div class="nextstepaction"]
> [Próxima etapa: manutenção e suporte do seu aplicativo publicado](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
>
