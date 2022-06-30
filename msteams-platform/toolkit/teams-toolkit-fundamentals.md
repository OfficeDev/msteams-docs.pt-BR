---
title: Visão geral do Kit de ferramentas do Microsoft Teams
author: zyxiaoyuer
description: Neste módulo, aprenda o Kit de Ferramentas do Teams, a Instalação do Kit de Ferramentas do Teams e o percurso do usuário do Kit de Ferramentas do Teams
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 05/24/2022
ms.openlocfilehash: fe9bbbb7a6d3668f43c31322ad8099bf994051b1
ms.sourcegitcommit: c398dfdae9ed96f12e1401ac7c8d0228ff9c0a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/30/2022
ms.locfileid: "66558328"
---
# <a name="teams-toolkit-overview"></a>Visão geral do Kit de ferramentas do Microsoft Teams

O Kit de ferramentas do Teams para o Microsoft Visual Studio Code ajuda você a criar e implantar aplicativos do Teams com identidade integrada, acesso ao armazenamento em nuvem, dados do Microsoft Graph e outros serviços no Azure e Microsoft 365 com abordagem de configuração zero. Para o desenvolvimento de aplicativos do Teams, semelhante ao Kit de Ferramentas do Teams para o Visual Studio, você pode usar a [Ferramenta CLI](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md), que consiste no Kit de ferramentas `teamsfx`.
O Kit de Ferramentas do Teams permite que você crie, depure e implante seu aplicativo Teams diretamente do Visual Studio Code. O desenvolvimento de aplicativos com o kit de ferramentas tem as vantagens de:

* Identidade integrada
* Acesso ao armazenamento em nuvem
* Dados do Microsoft Graph
* Serviços do Azure e do Microsoft 365 com abordagem de configuração zero.

O Kit de ferramentas do Teams traz todas as ferramentas necessárias para criar um aplicativo do Teams em um só lugar.

## <a name="user-journey-of-teams-toolkit"></a>Percurso do usuário do Kit de ferramentas do Teams

O Kit de ferramentas do Teams automatiza o trabalho manual e fornece uma ótima integração do Teams com os recursos do Azure. A imagem a seguir mostra o percurso do usuário do Kit de ferramentas do Teams:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/teams-toolkit-user-journey1.png" alt-text="Percurso do usuário do Kit de Ferramentas do Teams" lightbox="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/teams-toolkit-user-journey2.png":::

Os principais marcos desta jornada são:

1. Comece criando um novo projeto ou experimentando um aplicativo Teams de exemplo.
1. Adicione recursos ou edite o arquivo de manifesto conforme necessário.
1. Use a Microsoft 365 para compilar e depurar seu aplicativo Teams.
1. Use a conta do Azure para provisionar e implantar seu aplicativo na nuvem.
1. Publique seu aplicativo no Teams.

## <a name="install-teams-toolkit-for-visual-studio-code"></a>Instale o Kit de ferramentas do Teams para o Visual Studio Code

1. Abra o **Visual Studio Code.**
1. Selecione o modo de exibição Extensões (**Ctrl+Shift+X** / **⌘⇧-X** ou **Exibir > Extensões**).

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/install toolkit-1.png" alt-text="Instalar":::

1. Insira **o Kit de Ferramentas do Teams** na caixa de pesquisa.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/install-toolkit2.png" alt-text="Kit de ferramentas":::

1. Selecione **Instalar**.
  
   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/install-toolkit.png" alt-text="instalar o kit de ferramentas 4.0.0":::

> [!TIP]
> Você pode instalar o Kit de ferramentas do Teams do [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension).

## <a name="take-a-tour-of-teams-toolkit"></a>Faça um tour pelo Kit de ferramentas do Teams

Após a instalação do Kit de ferramentas, você verá a interface do usuário (IU) do Kit de ferramentas do Teams, conforme mostrado na imagem a seguir:

:::image type="content" source="../assets/images/teams-toolkit-v2/manual/Teams-toolkit.png" alt-text="mini funções":::

Você pode selecionar **Introdução para** explorar o Kit de Ferramentas do Teams ou criar um **novo aplicativo do Teams** para criar um projeto do Teams. Se você tiver um projeto do Teams criado pelo Kit de Ferramentas do Teams aberto no Visual Studio Code, verá a interface do usuário do Kit de Ferramentas do Teams com todas as funcionalidades, conforme mostrado na imagem a seguir:

:::image type="content" source="../assets/images/teams-toolkit-v2/manual/teamstookit1.png" alt-text="Captura de tela do kit de ferramentas de equipes":::

Vamos fazer um tour pelos tópicos abordados neste documento.

## <a name="accounts"></a>Contas

Para desenvolver um aplicativo Teams, você precisa de pelo menos uma Microsoft 365 com uma assinatura válida. Se você quiser hospedar seus recursos de back-end no Azure, uma conta do Azure também será necessária. O Kit de Ferramentas do Teams dá suporte à experiência integrada para entrar, provisionar e implantar recursos do Azure. Você pode [criar uma conta gratuita do Azure](https://azure.microsoft.com/free/) antes de começar.

## <a name="environment"></a>Ambiente

O Kit de ferramentas do Teams te ajuda a criar e gerenciar vários ambientes, provisionar e implantar artefatos no ambiente de destino para o aplicativo Teams.

### <a name="teamsfx-collaboration"></a>Colaboração do TeamsFx

Ele permite que os desenvolvedores e o proprietário do projeto convidem outros colaboradores para o projeto TeamsFx para depurar, provisionar e implantar o mesmo projeto TeamsFx.

:::image type="content" source="../assets/images/teams-toolkit-v2/manual/teamsfx.png" alt-text="Projeto teamsfx":::

## <a name="development"></a>Desenvolvimento

O Kit de Ferramentas do Teams ajuda você a criar e personalizar seu projeto de aplicativo do Teams que simplifica o trabalho de desenvolvimento de aplicativos do Teams.

### <a name="create-a-new-teams-app"></a>Criar um novo aplicativo do Teams

Ele ajuda você a começar com o desenvolvimento de aplicativos do Teams criando um novo projeto do Teams usando o  Kit de Ferramentas do Teams usando Criar novo projeto ou **Iniciar de um exemplo**.

### <a name="add-features"></a>Adicionar recursos

Ele ajuda **você a** adicionar incrementalmente recursos adicionais do Teams, como **Tab** ou **Bot**, ou, opcionalmente, adicionar recursos do Azure, como o Banco de Dados do SQL do Azure ou o **Azure Key Vault**, que atende às suas necessidades de desenvolvimento ao seu aplicativo atual do Teams. Você também pode adicionar **fluxos de trabalho de Logon Único** ou **CI/CD** para seu aplicativo do Teams.

### <a name="edit-manifest-file"></a>Editar arquivo de manifesto

Ele ajuda você a editar a integração de aplicativos do Teams com o cliente do Teams.

## <a name="deployment"></a>Implantação

Durante ou após o desenvolvimento, certifique-se de provisionar, implantar e publicar o aplicativo Teams antes que ele seja acessível aos usuários.

### <a name="provision-in-the-cloud"></a>Provisionar na nuvem

Ele se integra ao Azure Resource Manager que permite provisionar recursos do Azure, que seu aplicativo precisa para a abordagem de código.

### <a name="deploy-to-the-cloud"></a>Implantar na nuvem

 Ele ajuda você a implantar o código-fonte no Azure.

### <a name="publish-to-teams"></a>Publicar no Teams

Após criar o aplicativo, você poderá distribuí-lo para diferentes escopos, tais como individual, equipe, organização ou qualquer pessoa. Publicar no Teams ajuda você a publicar seu aplicativo desenvolvido.

#### <a name="teamsfx-cli"></a>TeamsFx CLI

É uma interface de linha de comando baseada em texto que acelera o desenvolvimento de aplicativos do Teams e também permite um cenário de CI/CD em que você pode integrar a CLI em scripts para automação.

#### <a name="teamsfx-sdk"></a>TeamsFx SDK

Ele ajuda você a reduzir tarefas de implementação de identidade e acesso a recursos de nuvem para instruções de linha única sem configuração.

## <a name="help-and-feedback"></a>Ajuda e Comentários

Nesta seção, você pode encontrar a documentação e os recursos necessários. Você pode selecionar **Relatar problemas sobre o GitHub** no Kit de ferramentas do Teams para obter **Suporte rápido** do especialista em produtos. Procure o problema antes de criar um novo ou visite o [rótulo StackOverflow `teams-toolkit`](https://stackoverflow.com/questions/tagged/teams-toolkit) para enviar comentários.
<!--  
Let's explore Teams Toolkit features.

| Teams Toolkit Features | Includes | What you can do |
| --- | --- | --- |
| **Accounts** | &nbsp; | &nbsp; |
| &nbsp; | Microsoft 365 account | Use your Microsoft 365 account with a valid E5 subscription for building your app. |
| &nbsp; | Azure account | Use your Azure account for deploying app on Azure. |
| **Environment** | &nbsp; | &nbsp; |
| &nbsp; | local | Deploy your app in the default local environment with local machine environment configurations. |
| &nbsp; | dev | Deploy your app in the default dev environment with remote or cloud environment configurations. You can create more environments, as you need. |
| **Development** | &nbsp; | &nbsp; |
| &nbsp; | Create a new Teams app | Use the toolkit wizard to prepare project scaffolding for app development. |
| &nbsp; | View samples | Select any of Teams Toolkit's 12 sample apps. The toolkit downloads the app code from GitHub, and you can build the sample app. |
| &nbsp; | Add Features | - Add other required Teams capabilities to Teams app during development process. </br> - Add optional cloud resources suitable for your app. |
| &nbsp; | Edit manifest file | Edit the Teams app integration with Teams client. |
| **Deployment** | &nbsp; | &nbsp; |
| &nbsp; | Provision in the cloud | Allocate Azure resources for your application. Teams Toolkit is integrated with Azure Resource Manager. |
| &nbsp; | Zip Teams metadata package | Create the app package that can be uploaded to Teams or Developer Portal. It contains the app manifest and app icons.  |
| &nbsp; | Deploy to the cloud | Deploy the source code to Azure. |
| &nbsp; | Publish to Teams | Publish your developed app and distribute it to scopes, such as personal, team, channel, or organization. |
| &nbsp; | Developer Portal for Teams | Use Developer Portal to configure and manage your Teams app. |
| **Help and Feedback** | &nbsp; | &nbsp; |
| &nbsp; | Quick start | View the Teams Toolkit Quick start help within Visual Studio Code.  |
| &nbsp; | Tutorial | Select to access different tutorials. |
| &nbsp; | Documentation | Select to access the Microsoft Teams Developer Documentation. |
| &nbsp; | Report issues on GitHub | Select to access GitHub page and raise any issues. |

-->
> [!TIP]
> Navegue pelos problemas existentes antes de criar um novo ou visite [o rótulo StackOverflow `teams-toolkit`](https://stackoverflow.com/questions/tagged/teams-toolkit) para enviar comentários.

## <a name="see-also"></a>Confira também

* [Criar novo projeto usando o Kit de Ferramentas do Teams](create-new-project.md)
* [Preparar contas para criar o aplicativo Teams](accounts.md)
* [Publicar aplicativos do Teams usando o Kit de Ferramentas do Teams](publish.md)
* [Usar o Kit de Ferramentas do Teams para provisionar recursos de nuvem](provision.md)
* [Implantar na nuvem](deploy.md)
