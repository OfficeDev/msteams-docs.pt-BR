---
title: Crie aplicativos com o Microsoft Teams Toolkit e Visual Studio
description: Comece a construir ótimos aplicativos personalizados diretamente dentro de Visual Studio com o Microsoft Teams Toolkit
keywords: equipes estúdio de ferramentas kit de ferramentas
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
# <a name="build-apps-with-the-teams-toolkit-and-visual-studio"></a>Crie aplicativos com os Teams Toolkit e Visual Studio

O Kit de Ferramentas do Microsoft Teams permite criar aplicativos personalizados do Teams diretamente no ambiente de desenvolvimento integrado (IDE) do Visual Studio. O kit de ferramentas do Microsoft Teams guia você através do processo e fornece o necessário para criar, depurar e iniciar seu aplicativo do Teams.

## <a name="prerequisites"></a>Pré-requisitos

1. [Habilitar a visualização do desenvolvedor](../resources/dev-preview/developer-preview-intro.md#enable-developer-preview).

1. Certifique-se de que o **<span></span>ASP.NE T e o módulo de desenvolvimento web** foram adicionados à sua Visual Studio instância. Você pode verificar seguindo as etapas do [Visual Studio modificação adicionando ou removendo cargas de trabalho e](/visualstudio/install/modify-visual-studio?view=vs-2019&preserve-view=true) documentação de componentes.

![módulo de asp.net de estúdio visual](../assets/images/visual-studio-web-dev-module.png)

3. Se você quiser testar seu aplicativo implantando-o a partir de Visual Studio, você precisará ter iIS (Serviços de Informações da Internet) instalado em seu ambiente de desenvolvimento. Visual Studio não inclui iIS e não está incluído na configuração padrão Windows 10, Windows 8 ou Windows 7; no entanto, você pode baixar a versão mais recente do centro de [downloads](https://www.microsoft.com/download/details.aspx?id=48264)da Microsoft .

![Visualização de página de download do IIS](../assets/images/iis.png)

## <a name="install-the-teams-toolkit"></a>Instale o Teams Toolkit

O Microsoft Teams Toolkit para Visual Studio está disponível para download no [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.vsteamstemplate) ou diretamente no menu **Extensões** dentro de Visual Studio.

## <a name="using-the-toolkit"></a>Usando o kit de ferramentas

- [Criar um novo projeto](#set-up-a-new-teams-project)
- [Configure seu aplicativo](#configure-your-app)
- [Empacote seu aplicativo](#package-your-app)
- [Execute seu aplicativo em Teams](#install-and-run-your-app-locally)
- [Valide o seu aplicativo](#validate-your-app)
- [Publicar seu aplicativo](#publish-your-app-to-teams)

## <a name="set-up-a-new-teams-project"></a>Criar um novo projeto de Teams

1. Selecione **Criar um novo projeto**.
1. Escolha **Microsoft Teams App** e selecione **Next**.
1. Você chegará à **tela configurar seu novo projeto** onde você pode escolher o nome **Project,** **Localização** e Nome **da Solução**.
1. Verifique a **solução e o projeto place rotulados na** caixa no mesmo diretório .
1. Uma janela pop-up rotulada **Adicionar recursos** permitirá que você escolha um ou mais recursos para a configuração do seu projeto.
1. Selecione o botão **Seguir** para concluir o processo de configuração.
1. Uma janela pop-up rotulada **Adicionar recursos** permitirá que você escolha as propriedades para cada recurso selecionado.
1. Selecione **Concluir** e você pousará na **Microsoft Teams Toolkit** página de aterrissagem.

## <a name="configure-your-app"></a>Configure seu aplicativo

Em sua essência, o aplicativo Teams abraça três componentes:

  1. O Microsoft Teams cliente (web, desktop ou celular) onde os usuários interagem com seu aplicativo.
  1. Um servidor que responde a solicitações de conteúdo que será exibido em Teams, por exemplo, conteúdo de guia HTML ou um cartão adaptativo de bot .
  1. Um pacote de aplicativos Teams consiste em três arquivos:

      > [!div class="checklist"]
      >
      > - O manifest.js
      > - Um [ícone de cores](../resources/schema/manifest-schema.md#icons) para seu aplicativo ser exibido no catálogo de aplicativos públicos ou de organização
      > - Um [ícone de contorno](../resources/schema/manifest-schema.md#icons) para exibição na barra de atividades Teams.

Quando um aplicativo é instalado, o cliente Teams analisa o arquivo manifesto para determinar informações necessárias, como o nome do seu aplicativo e a URL onde os serviços estão localizados.

> [!NOTE]
>Se você ainda não fez isso, você precisará fazer login em sua Microsoft 365 ou conta para continuar com o processo de desenvolvimento.
>
> Se você não tiver uma conta Microsoft 365, você pode se inscrever para uma assinatura [do Programa de Desenvolvedores Microsoft 365.](https://developer.microsoft.com/microsoft-365/dev-program) É *gratuito* por 90 dias e se renovará continuamente enquanto estiver usando-o para atividades de desenvolvimento. Se você tem uma assinatura *Visual Studio Enterprise* ou *Professional,* ambos os programas incluem uma assinatura gratuita Microsoft 365 [desenvolvedor,](https://aka.ms/MyVisualStudioBenefits)ativa para a vida útil de sua assinatura Visual Studio. Para obter mais informações, consulte [Configurar uma assinatura de desenvolvedor Microsoft 365](/office/developer-program/office-365-developer-program-get-started).
>

### <a name="configuration-steps"></a>Etapas de configuração

1. Para configurar seu aplicativo, na **Microsoft Teams Toolkit** página de destino, selecione **Editar pacote de aplicativo**.
1. No menu suspenso **Do My Environments,** selecione **o desenvolvimento**.
1. Você vai pousar na página **de detalhes** do Aplicativo onde você pode editar os campos de propriedade do seu aplicativo.
1. A edição dos campos na página de detalhes do App atualiza o conteúdo do manifest.jsno arquivo que, em última análise, será enviado como parte do pacote do aplicativo. [Saiba mais](https://aka.ms/teams-toolkit-manifest)

## <a name="package-your-app"></a>Empacote seu aplicativo

Modificar a página de **detalhes** do aplicativo ou atualizar os arquivos **manifesto** ou **.env** na pasta **.publish** do seu aplicativo gerará automaticamente o **seu arquivoDevelopment.zip.** O arquivo Development.zip inclui três arquivos necessários — o **manifest.jse** [dois ícones](../concepts/build-and-test/apps-package.md#app-icons).

## <a name="install-and-run-your-app-locally"></a>Instale e execute seu aplicativo localmente

1. No menu suspenso configurações de configurações de **solução,** selecione **Implantar** como mostrado na imagem a seguir:

    ![Menu de configurações de soluções](../assets/images/solution-configurations.png)

2. Selecione o botão **IIS Express + Teams.**

1. Teams será lançado e o diálogo de instalação do aplicativo deve aparecer no Teams cliente.

## <a name="validate-your-app"></a>Valide o seu aplicativo

A página **Validar** permite que você verifique seu pacote de aplicativos antes de enviar seu aplicativo para o AppSource. Basta carregar o pacote manifesto e a ferramenta de validação verificará seu aplicativo em todos os casos de teste relacionados ao manifesto. Para cada teste com falha, a descrição fornece um link de documentação para ajudá-lo a corrigir o erro. Para os testes difíceis de automatizar, a **lista preliminar** detalha 7 dos casos de teste com falha mais comuns, bem como vincula a uma lista completa de verificação de submissão.

## <a name="publish-your-app-to-teams"></a>Publicar seu aplicativo no Teams

✔ Na página inicial do seu projeto, você pode carregar seu aplicativo para uma equipe, enviar seu aplicativo para a loja de aplicativos personalizada da sua empresa para usuários em sua organização ou enviar seu aplicativo para a App Source para todos os usuários Teams.

✔ Seu administrador de TI revisará essas submissões.

✔ Você pode retornar à página **Publicar** para verificar seu status de envio e saber se seu aplicativo foi aprovado ou rejeitado pelo administrador de TI. É também aqui que você virá enviar atualizações para o seu aplicativo ou cancelar quaisquer submissões atualmente ativas.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Mantendo e apoiando seu aplicativo publicado](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
>
