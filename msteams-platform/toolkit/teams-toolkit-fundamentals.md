---
title: Visão geral do Kit de ferramentas do Microsoft Teams
author: zyxiaoyuer
description: Visão geral do Kit de ferramentas do Teams, Instalação do Kit de ferramentas do Teams e Tour dos recursos do Kit de ferramentas
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 05/17/2022
ms.openlocfilehash: 36436b5cc2cf7edec784ab653b12d8cf44172b8b
ms.sourcegitcommit: 80edf3c964bb47a2ee13f9eda4334ad19e21f331
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65654605"
---
# <a name="teams-toolkit-overview"></a>Visão geral do Kit de ferramentas do Microsoft Teams


O Kit de ferramentas do Teams para o Microsoft Visual Studio Code ajuda você a criar e implantar aplicativos do Teams com identidade integrada, acesso ao armazenamento em nuvem, dados do Microsoft Graph e outros serviços no Azure e Microsoft 365 com abordagem de configuração zero. Para o desenvolvimento de aplicativos do Teams, semelhante ao Kit de Ferramentas do Teams para o Visual Studio, você pode usar a [Ferramenta CLI](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md), que consiste no Kit de ferramentas `teamsfx`.
O Kit de Ferramentas do Teams permite que você crie, depure e implante seu aplicativo Teams diretamente do Visual Studio Code. O desenvolvimento de aplicativos com o kit de ferramentas tem as vantagens de:

* Identidade integrada
* Acesso ao armazenamento em nuvem
* Dados do Microsoft Graph
* Azure e serviços Microsoft 365 com abordagem de configuração zero

O Kit de ferramentas do Teams traz todas as ferramentas necessárias para criar um aplicativo do Teams em um só lugar.

## <a name="user-journey-of-teams-toolkit"></a>Percurso do usuário do Kit de ferramentas do Teams

O Kit de ferramentas do Teams automatiza o trabalho manual e fornece uma ótima integração do Teams com os recursos do Azure. A imagem a seguir mostra o percurso do usuário do Kit de ferramentas do Teams:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/teams-toolkit-user-journey.png" alt-text="Jornada do Usuário do Kit de ferramentas do Teams" border="true":::

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

1. Insira **Teams Toolkit** na caixa de pesquisa.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/install-toolkit2.png" alt-text="Kit de ferramentas":::

1. Selecionar **Instalar**.
  
   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/install-toolkit.png" alt-text="instalar o kit de ferramentas 4.0.0":::

> [!TIP]
> Você pode instalar o Kit de ferramentas do Teams do [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension).

## <a name="take-a-tour-of-teams-toolkit"></a>Faça um tour pelo Kit de ferramentas do Teams

Após a instalação do Kit de ferramentas, você verá a interface do usuário (IU) do Kit de ferramentas do Teams, conforme mostrado na imagem a seguir:

:::image type="content" source="../assets/images/teams-toolkit-v2/manual/Teams-toolkit.png" alt-text="mini funções":::

Você pode selecionar **Introdução** para explorar o Teams Toolkit ou selecionar Criar um novo aplicativo **Teams para criar** um Teams projeto. Se você tiver um projeto Teams criado pelo Teams Toolkit aberto no Visual Studio Code, verá uma interface do usuário Teams Toolkit com todas as funcionalidades, conforme mostrado na imagem a seguir:

:::image type="content" source="../assets/images/teams-toolkit-v2/manual/teamstookit1.png" alt-text="Captura de tela do kit de ferramentas de equipes":::

Vamos fazer um tour pelos tópicos abordados neste documento.

## <a name="accounts"></a>Contas

Para desenvolver um aplicativo Teams, você precisa de pelo menos uma Microsoft 365 com uma assinatura válida. Se você quiser hospedar seus recursos de back-end no Azure, uma conta do Azure também será necessária. Teams Toolkit dá suporte à experiência integrada para entrar, provisionar e implantar recursos do Azure. Você pode [criar uma conta gratuita do Azure](https://azure.microsoft.com/free/) antes de começar.

## <a name="environment"></a>Ambiente

O Kit de ferramentas do Teams te ajuda a criar e gerenciar vários ambientes, provisionar e implantar artefatos no ambiente de destino para o aplicativo Teams.

### <a name="teamsfx-collaboration"></a>Colaboração do TeamsFx

Ele permite que os desenvolvedores e o proprietário do projeto convidem outros colaboradores para o projeto TeamsFx para depurar, provisionar e implantar o mesmo projeto TeamsFx.

:::image type="content" source="../assets/images/teams-toolkit-v2/manual/teamsfx.png" alt-text="Projeto teamsfx":::

## <a name="development"></a>Desenvolvimento

O Kit de Ferramentas do Teams ajuda você a criar e personalizar seu projeto de aplicativo do Teams que simplifica o trabalho de desenvolvimento de aplicativos do Teams.

### <a name="create-a-new-teams-app"></a>Criar um novo aplicativo do Teams

Ele ajuda você a começar Teams desenvolvimento de aplicativos criando um novo projeto Teams usando Teams Toolkit usando Criar novo projeto ou **Iniciar de um exemplo**.

### <a name="add-features"></a>Adicionar recursos

Ele ajuda você a adicionar incrementalmente recursos adicionais do Teams, como **Tab** ou **Bot**, ou, opcionalmente, adicionar recursos do Azure, como **o Banco de Dados SQL do Azure** ou o **Azure Key Vault**, que atendem às suas necessidades de desenvolvimento ao seu aplicativo Teams atual. Você também pode adicionar **fluxos de trabalho de Logon** Único ou **CI/CD** para seu Teams aplicativo. 

### <a name="edit-manifest-file"></a>Editar arquivo de manifesto

Ele ajuda você a editar a integração de aplicativos do Teams com o cliente do Teams.

## <a name="deployment"></a>Implantação

Durante ou após o desenvolvimento, certifique-se de provisionar, implantar e publicar o aplicativo Teams antes que ele seja acessível aos usuários.

### <a name="provision-in-the-cloud"></a>Provisionar na nuvem

Ele se integra aos recursos do gerenciador do Azure que permite provisionar recursos do Azure, que seu aplicativo precisa para a abordagem de código.

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

Vamos explorar os recursos do Kit de Ferramentas do Teams.

| Recursos do Kit de ferramentas do Teams | Contém... | O que você pode fazer |
| --- | --- | --- |
| **Accounts** | &nbsp; | &nbsp; |
| &nbsp; | Conta do Microsoft 365 | Use sua conta Microsoft 365 com uma assinatura válida do E5 para criar seu aplicativo. |
| &nbsp; | Conta do Azure | Use sua conta do Azure para implantar o aplicativo no Azure. |
| **Ambiente** | &nbsp; | &nbsp; |
| &nbsp; | local | Implante seu aplicativo no ambiente local padrão com configurações de ambiente de computador local. |
| &nbsp; | dev | Implante seu aplicativo no ambiente de desenvolvimento padrão com configurações de ambiente remoto ou de nuvem. Você pode criar mais ambientes, conforme necessário. |
| **Desenvolvimento** | &nbsp; | &nbsp; |
| &nbsp; | Criar um novo aplicativo do Teams | Use o assistente do kit de ferramentas para preparar a estrutura do projeto para o desenvolvimento de aplicativos. |
| &nbsp; | Exibir amostras | Selecione qualquer um dos 12 aplicativos de exemplo do Kit de ferramentas do Teams. O kit de ferramentas baixa o código do aplicativo do GitHub e você pode criar o aplicativo de exemplo. |
| &nbsp; | Adicionar recursos | – Adicione outros recursos Teams necessários ao aplicativo Teams durante o processo de desenvolvimento. </br> – Adicione recursos de nuvem opcionais adequados para seu aplicativo. |
| &nbsp; | Editar arquivo de manifesto | Edite a integração do aplicativo Teams ao cliente do Teams. |
| **Implantação** | &nbsp; | &nbsp; |
| &nbsp; | Provisionar na nuvem | Atribua recursos do Azure para seu aplicativo. O Kit de ferramentas do Teams está integrado ao Gerenciador de Recursos do Teams. |
| &nbsp; | Pacote de metadados do Zip Teams | Crie o pacote do aplicativo que pode ser carregado no Teams ou Portal do Desenvolvedor. Ele contém o manifesto do aplicativo e os ícones do aplicativo.  |
| &nbsp; | Implantar na nuvem | Implante o código-fonte no Azure. |
| &nbsp; | Publicar no Teams | Publique seu aplicativo desenvolvido e distribua-o para escopos, como pessoal, equipe, canal ou organização. |
| &nbsp; | Portal do Desenvolvedor do Teams | Use o Portal do Desenvolvedor para configurar e gerenciar seu aplicativo do Teams. |
| **Ajuda e Comentários** | &nbsp; | &nbsp; |
| &nbsp; | Início rápido | Exiba a Teams Toolkit de início rápido no Visual Studio Code.  |
| &nbsp; | Tutorial | Selecione para acessar tutoriais diferentes. |
| &nbsp; | Documentação | Selecione para acessar a Documentação do Desenvolvedor do Microsoft Teams. |
| &nbsp; | Relatar problemas no GitHub | Selecione para acessar a página do GitHub e gere problemas. |


> [!TIP]
> Navegue pelos problemas existentes antes de criar um novo ou visite [o rótulo StackOverflow `teams-toolkit`](https://stackoverflow.com/questions/tagged/teams-toolkit) para enviar comentários.

## <a name="see-also"></a>Confira também

* [Criar novo projeto usando o Kit de Ferramentas do Teams](create-new-project.md)
* [Preparar contas para criar o aplicativo Teams](accounts.md)
* [Publicar aplicativos do Teams usando o Kit de Ferramentas do Teams](publish.md)
* [Usar o Kit de Ferramentas do Teams para provisionar recursos de nuvem](provision.md)
* [Implantar na nuvem](deploy.md)
