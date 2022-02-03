---
title: Teams Toolkit visão geral
author: zyxiaoyuer
description: Visão geral Teams Toolkit, instalação de Teams Toolkit e tour de Toolkit recursos
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 0a048e12167847c1cc34560531cba13da9d74f8f
ms.sourcegitcommit: 58a24422bb04a529b6629a56803ed2efabc17cb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/02/2022
ms.locfileid: "62323159"
---
# <a name="teams-toolkit-overview"></a>Teams Toolkit visão geral

> [!NOTE]
> Atualmente, esse recurso está disponível apenas na **visualização de desenvolvedor** público.

Teams Toolkit permite que você crie, depure e implante seu aplicativo Teams de Visual Studio Code. O desenvolvimento de aplicativos com o kit de ferramentas tem as vantagens de:

- Identidade integrada
- Acesso ao armazenamento em nuvem
- Dados do Microsoft Graph
- Serviços do Azure e Microsoft 365 com abordagem de configuração zero

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

Você pode selecionar **Início** Rápido para explorar o Teams Toolkit ou selecionar **Criar** um novo aplicativo Teams para criar um Teams projeto. Você pode exibir uma lista de todos os Toolkit ao criar ou abrir um projeto existente na Visual Studio Code sidebar.

:::image type="content" source="../assets/images/teams-toolkit-v2/manual/toolkit functions.png" alt-text="funções":::

Vamos explorar Teams Toolkit recursos.

| Teams Toolkit recursos | Inclui... | O que você pode fazer |
| --- | --- | --- |
| **Accounts** | &nbsp; | &nbsp; |
| &nbsp; | Microsoft 365 conta | Use sua Microsoft 365 com uma assinatura E5 válida para criar seu aplicativo. |
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
| &nbsp; | Pacote Teams de metadados zip | Crie o pacote de aplicativos que pode ser carregado para Teams ou Portal do Desenvolvedor. Ele contém o manifesto do aplicativo e os ícones do aplicativo.  |
| &nbsp; | Implantar na nuvem | Implante o código-fonte no Azure. |
| &nbsp; | Publicar no Teams | Publique seu aplicativo desenvolvido e distribua-o em escopos, como pessoal, equipe, canal ou organização. |
| &nbsp; | Portal do Desenvolvedor do Teams | Use o Portal do Desenvolvedor para configurar e gerenciar seu Teams app. |
| &nbsp; | Guia de CI/CD | Automatize seu fluxo de trabalho de desenvolvimento durante a criação Teams aplicativo. |
| **Ajuda e comentários** | &nbsp; | &nbsp; |
| &nbsp; | Início Rápido | Exibir a Teams Toolkit de Início Rápido dentro Visual Studio Code.  |
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
