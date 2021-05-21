---
title: Criar aplicativos com o Microsoft Teams Toolkit e Visual Studio
description: Começar a criar grandes aplicativos personalizados diretamente Visual Studio com o Microsoft Teams Toolkit
keywords: kit de ferramentas do visual studio do teams
localization_priority: Normal
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: eb94a8de0355283344ebe890a6fa3a3050e243ea
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566548"
---
# <a name="build-apps-with-the-teams-toolkit-and-visual-studio"></a>Criar aplicativos com o Teams Toolkit e Visual Studio

O Kit de Ferramentas do Microsoft Teams permite criar aplicativos personalizados do Teams diretamente no ambiente de desenvolvimento integrado (IDE) do Visual Studio. O kit de ferramentas do Microsoft Teams guia você através do processo e fornece o necessário para criar, depurar e iniciar seu aplicativo do Teams.

## <a name="prerequisites"></a>Pré-requisitos

1. [Habilitar a visualização do desenvolvedor](../resources/dev-preview/developer-preview-intro.md#enable-developer-preview).

1. Certifique-se de que **<span>o ASP.NE</span>T e** o módulo de desenvolvimento da Web foram adicionados à sua Visual Studio instância. Você pode verificar seguindo as etapas na documentação Modificar Visual Studio adicionando ou [removendo cargas](/visualstudio/install/modify-visual-studio?view=vs-2019&preserve-view=true) de trabalho e componentes.

![módulo de asp.net visual studio](../assets/images/visual-studio-web-dev-module.png)

3. Se você quiser testar seu aplicativo implantando-o Visual Studio, você precisará ter o IIS (Serviços de Informações da Internet) instalado em seu ambiente de desenvolvimento. Visual Studio não inclui o IIS e ele não está incluído na configuração padrão Windows 10, Windows 8 ou Windows 7; no entanto, você pode baixar a versão mais recente do centro [de download da Microsoft.](https://www.microsoft.com/download/details.aspx?id=48264)

![Exibição de página de download do IIS](../assets/images/iis.png)

## <a name="install-the-teams-toolkit"></a>Instalar o Teams Toolkit

O Microsoft Teams Toolkit para Visual Studio está disponível para download no [marketplace do Visual Studio ou](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.vsteamstemplate) diretamente no menu **Extensões** no Visual Studio.

## <a name="using-the-toolkit"></a>Usando o kit de ferramentas

- [Configurar um novo projeto](#set-up-a-new-teams-project)
- [Configurar seu aplicativo](#configure-your-app)
- [Empacote seu aplicativo](#package-your-app)
- [Execute seu aplicativo em Teams](#install-and-run-your-app-locally)
- [Valide o seu aplicativo](#validate-your-app)
- [Publicar seu aplicativo](#publish-your-app-to-teams)

## <a name="set-up-a-new-teams-project"></a>Configurar um novo Teams projeto

1. Selecione **Criar um novo projeto**.
1. Escolha **Microsoft Teams App e** selecione **Próximo**.
1. Você chegará na tela Configurar seu novo **projeto,** onde poderá escolher o nome do **Project,** **Local** e Nome **da solução.**
1. Marque a caixa rotulada **Place solution and project no mesmo diretório**.
1. Uma janela pop-up rotulada de **Adicionar Recursos** permitirá que você escolha um ou mais recursos para a configuração do projeto.
1. Selecione o **botão Próximo** para concluir o processo de configuração.
1. Uma janela pop-up rotulada **Adicionar Recursos** permitirá que você escolha as propriedades para cada recurso selecionado.
1. Selecione **Concluir** e você pousará na **página** Microsoft Teams Toolkit inicial.

## <a name="configure-your-app"></a>Configurar seu aplicativo

No seu núcleo, o Teams aplicativo abrange três componentes:

  1. O Microsoft Teams cliente (Web, desktop ou móvel) onde os usuários interagem com seu aplicativo.
  1. Um servidor que responde a solicitações de conteúdo que serão exibidas em Teams, por exemplo, conteúdo de guia HTML ou um cartão adaptável de bot.
  1. Um Teams de aplicativo consiste em três arquivos:

      > [!div class="checklist"]
      >
      > - O manifest.json
      > - Um [ícone de cor](../resources/schema/manifest-schema.md#icons) para seu aplicativo ser exibido no catálogo de aplicativos público ou da organização
      > - Um [ícone de contorno](../resources/schema/manifest-schema.md#icons) para exibição na barra de Teams de atividades.

Quando um aplicativo é instalado, o cliente Teams analisado o arquivo de manifesto para determinar as informações necessárias, como o nome do seu aplicativo e a URL onde os serviços estão localizados.

> [!NOTE]
>Se você ainda não fez isso, você precisará entrar no seu Microsoft 365 ou conta para continuar com o processo de desenvolvimento.
>
> Se você não tiver uma conta Microsoft 365, poderá inscrever-se para uma assinatura do [Programa Microsoft 365 Desenvolvedor.](https://developer.microsoft.com/microsoft-365/dev-program) Ele é gratuito *por* 90 dias e será continuamente renovado, desde que você esteja usando-o para atividades de desenvolvimento. Se você tiver uma assinatura de Visual Studio *Enterprise* ou *Professional,* ambos os programas incluem uma assinatura de desenvolvedor gratuita Microsoft 365 [,](https://aka.ms/MyVisualStudioBenefits)ativa para a vida útil de sua assinatura Visual Studio. Para obter mais informações, consulte [Set up a Microsoft 365 developer subscription](/office/developer-program/office-365-developer-program-get-started).
>

### <a name="configuration-steps"></a>Etapas de configuração

1. Para configurar seu aplicativo, na **página** inicial Microsoft Teams Toolkit, selecione **Editar pacote de aplicativos**.
1. No menu **suspenso Meus Ambientes,** selecione **desenvolvimento**.
1. Você pousará na página Detalhes **do aplicativo** onde poderá editar os campos de propriedades do seu aplicativo.
1. A edição dos campos na página detalhes do aplicativo atualiza o conteúdo do arquivo manifest.jsno arquivo que, em última análise, será shipado como parte do pacote de aplicativos. [Saiba Mais](https://aka.ms/teams-toolkit-manifest)

## <a name="package-your-app"></a>Empacote seu aplicativo

Modificar a página de detalhes **do** aplicativo ou atualizar o **manifesto** ou **arquivos .env** na pasta **.publish** do aplicativo gerará automaticamente seu **arquivoDevelopment.zip.** O Development.zip inclui três arquivos necessários — omanifest.js **e** [dois ícones](../concepts/build-and-test/apps-package.md#app-icons).

## <a name="install-and-run-your-app-locally"></a>Instalar e executar seu aplicativo localmente

1. No menu **suspenso Configurações** da Solução, selecione **Implantar** conforme mostrado na imagem a seguir:

    ![Menu Configurações da solução](../assets/images/solution-configurations.png)

2. Selecione o **IIS Express + Teams** botão.

1. Teams iniciará e o diálogo de instalação do aplicativo deverá aparecer no cliente Teams aplicativo.

## <a name="validate-your-app"></a>Valide o seu aplicativo

A **página Validar** permite que você verifique seu pacote de aplicativos antes de enviar seu aplicativo ao AppSource. Basta carregar o pacote de manifesto e a ferramenta de validação verificará seu aplicativo em relação a todos os casos de teste relacionados ao manifesto. Para cada teste com falha, a descrição fornece um link de documentação para ajudá-lo a corrigir o erro. Para os testes difíceis de  automatizar, a lista de verificação preliminar detalha 7 dos casos de teste com falha mais comuns, bem como o link para uma lista de verificação de envio completa.

## <a name="publish-your-app-to-teams"></a>Publicar seu aplicativo no Teams

✔ Na home page do projeto, você pode carregar seu aplicativo em uma equipe, enviar seu aplicativo para a loja de aplicativos personalizada da sua empresa para usuários em sua organização ou enviar seu aplicativo para a Fonte do Aplicativo para todos os Teams usuários.

✔ seu administrador de IT revisará esses envios.

✔ Você pode retornar à  página Publicar para verificar o status do envio e saber se seu aplicativo foi aprovado ou rejeitado pelo administrador de TI. Também é aqui que você enviará atualizações para seu aplicativo ou cancelará quaisquer envios ativos no momento.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Mantendo e dando suporte ao aplicativo publicado](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
>
