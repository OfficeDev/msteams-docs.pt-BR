---
title: Criar aplicativos com o Kit de Ferramentas do Microsoft Teams e o Visual Studio
description: Começar a criar ótimos aplicativos personalizados diretamente no Visual Studio com o Kit de Ferramentas do Microsoft Teams
keywords: kit de ferramentas do visual studio do teams
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: 08df1d3907a1a3683eb42222e247cd7fd6c0177b
ms.sourcegitcommit: 5e1300d6f4f2ea23beb3cdbbf4bd46999eef4e87
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/15/2021
ms.locfileid: "49875004"
---
# <a name="build-apps-with-the-teams-toolkit-and-visual-studio"></a>Criar aplicativos com o Kit de Ferramentas do Teams e o Visual Studio

O Kit de Ferramentas do Microsoft Teams permite que você crie aplicativos personalizados do Teams diretamente no IDE (ambiente de desenvolvimento integrado) do Visual Studio. O kit de ferramentas do Microsoft Teams orienta você durante o processo e fornece tudo o que você precisa para criar, depurar e iniciar seu aplicativo do Teams.

## <a name="prerequisites"></a>Pré-requisitos

1. [Habilitar a visualização do desenvolvedor](../resources/dev-preview/developer-preview-intro.md#enable-developer-preview)

1. Certifique-se de que **<span>o ASP.NE</span>T e o** módulo de desenvolvimento da Web foram adicionados à sua instância do Visual Studio. Você pode verificar seguindo as etapas no Modify Visual Studio adicionando [ou removendo cargas de](/visualstudio/install/modify-visual-studio?view=vs-2019&preserve-view=true) trabalho e documentação de componentes.

![módulo de asp.net visual studio](../assets/images/visual-studio-web-dev-module.png)

3. Se você quiser testar seu aplicativo implantando-o no Visual Studio, precisará ter o IIS (Serviços de Informações da Internet) instalado em seu ambiente de desenvolvimento. O Visual Studio não inclui o IIS e não está incluído na configuração padrão do Windows 10, do Windows 8 ou do Windows 7; No entanto, você pode baixar a versão mais recente do centro [de download da Microsoft.](https://www.microsoft.com/download/details.aspx?id=48264)

![Exibição da página de download do IIS](../assets/images/iis.png)

## <a name="install-the-teams-toolkit"></a>Instalar o Kit de Ferramentas do Teams

O Microsoft Teams Toolkit para Visual Studio está disponível para download no [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.vsteamstemplate) ou diretamente no menu Extensões no Visual Studio. 

## <a name="using-the-toolkit"></a>Usando o kit de ferramentas

- [Configurar um novo projeto](#set-up-a-new-teams-project)
- [Configurar seu aplicativo](#configure-your-app)
- [Empacote seu aplicativo](#package-your-app)
- [Executar seu aplicativo no Teams](#install-and-run-your-app-locally)
- [Valide o seu aplicativo](#validate-your-app)
- [Publicar seu aplicativo](#publish-your-app-to-teams)

## <a name="set-up-a-new-teams-project"></a>Configurar um novo projeto do Teams

1. Selecione **Criar um novo projeto.**
1. Escolha **o aplicativo Microsoft Teams e** selecione **Próximo.**
1. Você chegará na tela **Configurar seu novo projeto,** onde poderá escolher o **nome** do **projeto,** o local e o nome **da solução.**
1. Marque a caixa rotulada **Colocar solução e projeto no mesmo diretório.**
1. Uma janela pop-up rotulada adicionar **recursos** permitirá que você escolha um ou mais recursos para a configuração do seu projeto.
1. Selecione o **botão Próximo** para concluir o processo de configuração.
1. Uma janela pop-up rotulada adicionar **recursos** permitirá que você escolha as propriedades para cada recurso selecionado.
1. Selecione **Concluir** e você chegará à página inicial do **Microsoft Teams Toolkit.**

## <a name="configure-your-app"></a>Configurar seu aplicativo

Em seu núcleo, o aplicativo Teams adota três componentes:

  1. O cliente do Microsoft Teams (web, desktop ou dispositivos móveis) em que os usuários interagem com seu aplicativo.
  1. Um servidor que responde a solicitações de conteúdo que será exibido no Teams, por exemplo, conteúdo de guia HTML ou um cartão adaptável de bot.
  1. Um pacote [de aplicativos do](/concepts/build-and-test/apps-package.md) Teams que consiste em três arquivos:

  > [!div class="checklist"]
  >
  > - O manifest.jsem
  > - Um [ícone de cor](../resources/schema/manifest-schema.md#icons) para seu aplicativo ser exibido no catálogo de aplicativos público ou da organização
 > - Um [ícone de contorno](../resources/schema/manifest-schema.md#icons) para exibição na barra de atividades do Teams.

Quando um aplicativo é instalado, o cliente do Teams analisará o arquivo de manifesto para determinar as informações necessárias, como o nome do seu aplicativo e a URL onde os serviços estão localizados.

> [!NOTE]
>Se ainda não tiver feito isso, você precisará entrar no Microsoft 365 ou conta para continuar com o processo de desenvolvimento.
>
> Se você não tiver uma conta do Microsoft 365, inscreva-se para uma assinatura do Programa para Desenvolvedores do [Microsoft 365.](https://developer.microsoft.com/microsoft-365/dev-program) Ele é *gratuito por* 90 dias e será renovado continuamente, desde que você o esteja usando para atividades de desenvolvimento. Se você tiver uma assinatura do Visual Studio *Enterprise* ou *Professional,* ambos os programas incluirão uma assinatura gratuita de desenvolvedor do Microsoft 365, ativa durante a vida de sua assinatura do Visual Studio. [](https://aka.ms/MyVisualStudioBenefits) *Confira* [Configurar uma assinatura de desenvolvedor do Microsoft 365.](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started)
>

### <a name="configuration-steps"></a>Etapas de configuração

1. Para configurar seu aplicativo, na página inicial do Kit de Ferramentas do **Microsoft Teams,** selecione **Editar pacote do aplicativo.**
1. No menu **suspenso Meus Ambientes,** selecione **desenvolvimento.**
1. Você chegará à página **de detalhes do** aplicativo onde poderá editar os campos de propriedades do seu aplicativo.
1. A edição dos campos na página de detalhes do aplicativo atualiza o conteúdo do arquivo manifest.jsno arquivo que, por fim, será oferecido como parte do pacote do aplicativo. [Saiba mais](https://aka.ms/teams-toolkit-manifest)

## <a name="package-your-app"></a>Empacote seu aplicativo

Modificar a página **de detalhes** do aplicativo ou atualizar o manifesto ou **arquivos .env** na pasta **.publish** do aplicativo gerará automaticamente o arquivo **Development.zip** arquivo. O Development.zip arquivo inclui três arquivos obrigatórios — a **manifest.jse** [dois ícones](../concepts/build-and-test/apps-package.md#app-icons).

## <a name="install-and-run-your-app-locally"></a>Instalar e executar seu aplicativo localmente

1. No menu **suspenso Configurações** da Solução, selecione **Implantar.**

![Menu Configurações da solução](../assets/images/solution-configurations.png)

2. Selecione o **botão IIS Express + Teams.**

1. O Teams será lançado e a caixa de diálogo de instalação do aplicativo deverá aparecer no cliente do Teams.

## <a name="validate-your-app"></a>Valide o seu aplicativo

A **página Validar** permite que você verifique o pacote do aplicativo antes de enviar seu aplicativo ao AppSource. Basta carregar o pacote de manifesto e a ferramenta de validação verificará seu aplicativo em relação a todos os casos de teste relacionados ao manifesto. Para cada teste com falha, a descrição fornece um link de documentação para ajudá-lo a corrigir o erro. Para os testes difíceis de  automatizar, a lista de verificação preliminar detalha 7 dos casos de teste com falha mais comuns, bem como o link para uma lista de verificação de envio completa.

## <a name="publish-your-app-to-teams"></a>Publicar seu aplicativo no Teams

✔ Na home page do seu projeto, você pode carregar seu aplicativo para uma equipe, enviar seu aplicativo para a loja de aplicativos personalizada da empresa para usuários em sua organização ou enviar seu aplicativo para a Fonte de Aplicativos para todos os usuários do Teams.

✔ seu administrador de IT revisará esses envios.

✔ Você pode retornar à  página Publicar para verificar o status do envio e saber se o aplicativo foi aprovado ou rejeitado pelo administrador de TI. Também é aqui que você enviará atualizações para seu aplicativo ou cancelará quaisquer envios ativos no momento.

> [!div class="nextstepaction"]
> [Próxima etapa: manter e dar suporte ao seu aplicativo publicado](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
>
