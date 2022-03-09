---
title: Teams Toolkit visão geral
author: zyxiaoyuer
description: Visão geral Teams Toolkit, Instalação de Teams Toolkit e Tour de Toolkit recursos
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: fd3a72d3738fb835a5ef1e8092d1e59c06dad454
ms.sourcegitcommit: 830fdc80556a5fde642850dd6b4d1b7efda3609d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2022
ms.locfileid: "63398817"
---
# <a name="teams-toolkit-overview"></a>Teams Toolkit visão geral

> [!NOTE]
> Atualmente, esse recurso está disponível apenas na **visualização de desenvolvedor** público.

Teams Toolkit for Microsoft Visual Studio Code ajuda você a criar e implantar aplicativos Teams com identidade integrada, acesso ao armazenamento em nuvem, dados do Microsoft Graph e outros serviços no Azure e Microsoft 365 com abordagem de configuração zero. Para Teams desenvolvimento de aplicativos, semelhante ao Teams Toolkit para Visual Studio, você pode usar a ferramenta [CLI](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md), que consiste em Toolkit `teamsfx`.
Teams Toolkit permite que você crie, depure e implante seu aplicativo Teams de Visual Studio Code. O desenvolvimento de aplicativos com o kit de ferramentas tem as vantagens de:

* Identidade integrada
* Acesso ao armazenamento em nuvem
* Dados do Microsoft Graph
* Serviços do Azure e Microsoft 365 com abordagem de configuração zero

Teams Toolkit todas as ferramentas necessárias para a criação de um aplicativo Teams em um só lugar.

Para Teams desenvolvimento de aplicativos, semelhante ao Teams Toolkit para Visual Studio Code, você pode usar a ferramenta [CLI](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md), que consiste em Toolkit `teamsfx`.

## <a name="user-journey-of-teams-toolkit"></a>Jornada do usuário Teams Toolkit

Teams Toolkit automatiza o trabalho manual e fornece uma ótima integração dos recursos Teams e do Azure. A imagem a seguir mostra Teams Toolkit de usuário:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/teams-toolkit-user-journey.png" alt-text="Teams Toolkit Jornada do Usuário" border="true":::

Os principais marcos dessa jornada são:

1. Comece criando um novo projeto ou tentando um aplicativo Teams exemplo.
1. Adicione recursos ou edite o arquivo de manifesto conforme necessário.
1. Use Microsoft 365 conta para criar e depurar seu Teams app.
1. Use a conta do Azure para provisionar e implantar seu aplicativo na nuvem.
1. Publique seu aplicativo no Teams.

## <a name="install-teams-toolkit-for-visual-studio-code"></a>Instalar Teams Toolkit para Visual Studio Code

1. Abra **Visual Studio Code.**
1. Selecione o exibição Extensões (**Ctrl+Shift+X** / **⌘⇧-X** ou **Exibir > Extensões**):

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/install toolkit-1.png" alt-text="install":::

1. Insira **Teams Toolkit** na caixa de pesquisa:

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/install toolkit-2.png" alt-text="Kit de ferramentas":::

1. Selecione **Instalar**:
  
   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/install.png" alt-text="install toolkit":::

> [!TIP]
> Você pode instalar Teams Toolkit do [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension).

## <a name="take-a-tour-of-teams-toolkit"></a>Fazer um tour por Teams Toolkit

Após Toolkit instalação, você verá a interface do usuário Teams Toolkit como mostrado na imagem a seguir:

:::image type="content" source="../assets/images/teams-toolkit-v2/manual/teams toolkit.png" alt-text="mini-funções":::

Você pode selecionar **Início** Rápido para explorar o Teams Toolkit ou selecionar **Criar** um novo aplicativo Teams para criar um Teams projeto. Se você tiver um projeto Teams criado pelo Teams Toolkit v2.+ aberto no Visual Studio Code Teams Toolkit, você verá uma interface do usuário com todas as funcionalidades, conforme mostrado na imagem a seguir: Você pode selecionar **Início** Rápido para explorar o Teams Toolkit , ou selecione **Criar um novo Teams App** para criar um Teams projeto. Você pode exibir uma lista de todos os Toolkit ao criar ou abrir um projeto existente na Visual Studio Code sidebar.

:::image type="content" source="../assets/images/teams-toolkit-v2/manual/toolkit functions.png" alt-text="funções":::

Vamos fazer um tour dos tópicos abordados neste documento:

## <a name="accounts"></a>Contas

Para desenvolver um Teams, você precisa de pelo menos uma Microsoft 365 com uma assinatura válida. Se você quiser hospedar seus recursos de back-end no Azure, uma conta do Azure também será necessária. Teams Toolkit oferece suporte à experiência integrada para entrar, provisionar e implantação para recursos do Azure. Você pode [criar uma conta gratuita do Azure](https://azure.microsoft.com/free/) antes de começar.

## <a name="environment"></a>Ambiente

Teams Toolkit ajuda você a criar e gerenciar vários ambientes, provisionar e implantar artefatos no ambiente de destino para Teams App.

### <a name="teamsfx-collaboration"></a>Colaboração teamsFx

Ele permite que os desenvolvedores e o proprietário do projeto convidem outros colaboradores para o projeto TeamsFx para depurar, provisionar e implantar o mesmo projeto teamsFx.

## <a name="development"></a>Desenvolvimento

Teams Toolkit ajuda você a criar e personalizar seu projeto de aplicativo Teams que torna o Teams de aplicativos mais simples.

### <a name="create-a-new-teams-app"></a>Criar um novo Teams app

Ele ajuda você a começar com Teams desenvolvimento de aplicativos criando um novo projeto Teams usando Teams Toolkit usando Criar novo projeto ou Criar a partir **de exemplos**.

### <a name="add-capabilities"></a>Adicionar recursos

Ele ajuda a adicionar outros recursos de Teams necessários Teams aplicativo durante o processo de desenvolvimento.

### <a name="add-cloud-resources"></a>Adicionar recursos de nuvem

Ele ajuda você a adicionar, opcionalmente, recursos de nuvem que se ajustam às suas necessidades de desenvolvimento.

### <a name="edit-manifest-file"></a>Editar arquivo de manifesto

Ele ajuda você a editar a integração Teams aplicativo com Teams cliente.

## <a name="deployment"></a>Implantação

Durante ou após o desenvolvimento, certifique-se de provisionar, implantar e publicar Teams aplicativo antes de ser acessível aos usuários.

### <a name="provision-in-the-cloud"></a>Provisionamento na nuvem

Ele se integra ao gerenciador de recursos do Azure que permite provisionar recursos do Azure, que seu aplicativo precisa para abordagem de código.

### <a name="deploy-to-the-cloud"></a>Implantar na nuvem

 Ele ajuda você a implantar o código-fonte no Azure.

### <a name="publish-to-teams"></a>Publicar no Teams

Depois de criar o aplicativo, você pode distribuir seu aplicativo para escopos diferentes, como individual, equipe, organização ou qualquer pessoa. Publicar no Teams ajuda você a publicar seu aplicativo desenvolvido.

### <a name="cicd-guide"></a>Guia de CI/CD

Ele ajuda a automatizar seu fluxo de trabalho de desenvolvimento ao criar Teams aplicativo. O guia CI/CD fornece ferramentas e modelos para você começar a configurar pipelines ci ou CD.

#### <a name="teamsfx-cli"></a>TeamsFx CLI

É uma interface de linha de comando baseada em texto que acelera Teams desenvolvimento de aplicativos e também habilita cenário de CI/CD em que você pode integrar a CLI em scripts para automação.

#### <a name="teamsfx-sdk"></a>TeamsFx SDK

Ele ajuda você a reduzir tarefas de implementação de identidade e acesso a recursos de nuvem para instruções de linha única com configuração zero.

## <a name="help-and-feedback"></a>Ajuda e comentários

Nesta seção, você pode encontrar a documentação e os recursos necessários. Você pode selecionar **Relatar problemas GitHub** no Teams Toolkit para obter **suporte rápido do especialista** em produtos. Navegue pelo problema antes de criar um novo ou visite a marca [StackOverflow `teams-toolkit`](https://stackoverflow.com/questions/tagged/teams-toolkit) para enviar comentários.

Vamos explorar Teams Toolkit recursos.

| Teams Toolkit recursos | Inclui... | O que você pode fazer |
| --- | --- | --- |
| **Accounts** | &nbsp; | &nbsp; |
| &nbsp; | Conta do Microsoft 365 | Use sua Microsoft 365 com uma assinatura E5 válida para criar seu aplicativo. |
| &nbsp; | Conta do Azure | Use sua conta do Azure para implantar o aplicativo no Azure. |
| **Ambiente** | &nbsp; | &nbsp; |
| &nbsp; | local | Implante seu aplicativo no ambiente local padrão com configurações de ambiente de máquina local. |
| &nbsp; | dev | Implante seu aplicativo no ambiente de dev padrão com configurações de ambiente remoto ou de nuvem. Você pode criar mais ambientes, conforme necessário. |
| **Desenvolvimento** | &nbsp; | &nbsp; |
| &nbsp; | Criar um novo Teams app | Use o assistente de kit de ferramentas para preparar o scaffolding do projeto para desenvolvimento de aplicativos. |
| &nbsp; | Exibir amostras | Selecione qualquer um dos Teams Toolkit 12 aplicativos de exemplo do Teams Toolkit. O kit de ferramentas baixa o código do aplicativo GitHub e você pode criar o aplicativo de exemplo. |
| &nbsp; | Adicionar recursos | Adicione outros recursos de Teams necessários ao aplicativo Teams durante o processo de desenvolvimento. |
| &nbsp; | Adicionar recursos de nuvem | Adicione recursos opcionais de nuvem adequados para seu aplicativo. |
| &nbsp; | Editar arquivo de manifesto | Edite a Teams de aplicativos com Teams cliente. |
| **Implantação** | &nbsp; | &nbsp; |
| &nbsp; | Provisionamento na nuvem | Alocar recursos do Azure para seu aplicativo. Teams Toolkit é integrado ao Gerenciador de Recursos do Azure. |
| &nbsp; | Pacote Teams de metadados zip | Crie o pacote de aplicativos que pode ser carregado no Teams ou no Portal do Desenvolvedor. Ele contém o manifesto do aplicativo e os ícones do aplicativo.  |
| &nbsp; | Implantar na nuvem | Implante o código-fonte no Azure. |
| &nbsp; | Publicar no Teams | Publique seu aplicativo desenvolvido e distribua-o em escopos, como pessoal, equipe, canal ou organização. |
| &nbsp; | Portal do Desenvolvedor do Teams | Use o Portal do Desenvolvedor para configurar e gerenciar seu Teams app. |
| &nbsp; | Guia de CI/CD | Automatize seu fluxo de trabalho de desenvolvimento durante a criação Teams aplicativo. |
| **Ajuda e comentários** | &nbsp; | &nbsp; |
| &nbsp; | Início Rápido | Exibir a ajuda Teams Toolkit início rápido no Visual Studio Code.  |
| &nbsp; | Documentação | Selecione para acessar a documentação Microsoft Teams desenvolvedor. |
| &nbsp; | Relatar problemas no GitHub | Selecione para acessar GitHub página e levantar quaisquer problemas. |
|

> [!TIP]
> Navegue por problemas existentes antes de criar um novo ou visite a marca [StackOverflow `teams-toolkit`](https://stackoverflow.com/questions/tagged/teams-toolkit) para enviar comentários.

## <a name="see-also"></a>Confira também

* [Criar novo projeto usando Teams Toolkit](create-new-project.md)
* [Preparar contas para criar Teams aplicativos](accounts.md)
* [Publicar aplicativos do Teams usando o Kit de Ferramentas do Teams](publish.md)
* [Usar Teams Toolkit para provisionar recursos de nuvem](provision.md)
* [Implantar na nuvem](deploy.md)
