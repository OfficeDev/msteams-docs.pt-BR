---
title: Saiba como usar modelos de pipeline de CI/CD no GitHub, no Azure DevOps e no Jenkins para desenvolvedores de aplicativos do Teams
author: MuyangAmigo
description: Modelos de CI/CD
ms.author: ruhe
ms.localizationpriority: medium
ms.topic: overview
ms.date: 04/20/2022
ms.openlocfilehash: c39ad23fe42fd9cfd97ae2fcf49390cf19fac4a2
ms.sourcegitcommit: ff31cbe4840191f004d8fc61dd4fd93d35fcaecb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/07/2022
ms.locfileid: "65938930"
---
# <a name="set-up-cicd-pipelines"></a>Configurar pipelines de CI/CD

O TeamsFx ajuda a automatizar seu fluxo de trabalho de desenvolvimento durante a criação de aplicativos do Teams. A seguir estão as ferramentas e modelos que você pode usar para configurar pipelines de CI/CD, criar modelos de fluxo de trabalho e personalizar o fluxo de trabalho de CI/CD com GitHub, Azure DevOps, Jenkins e outras plataformas. Para provisionar e implantar recursos, você pode criar entidades de serviço do Azure e publicar o aplicativo Teams usando o Teams Portal do Desenvolvedor. Para publicar o aplicativo Teams manualmente, você pode aproveitar [Portal do Desenvolvedor para o Teams](https://dev.teams.microsoft.com/home).

|Ferramentas e Modelos | Descrição |
|---|---|
|[TeamsFx-CLI-Action](https://github.com/OfficeDev/teamsfx-cli-action)|Ação do GitHub que se integra à CLI do TeamsFx.|
|[Kit de ferramentas do Teams para Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension)| Visual Studio Code extensão que ajuda você a desenvolver fluxos de trabalho de automação e aplicativos do Teams para GitHub, Azure DevOps e Jenkins. |
|[TeamsFx CLI](https://www.npmjs.com/package/@microsoft/teamsfx-cli) | Ferramenta de linha de comando que ajuda você a desenvolver fluxos de trabalho de automação e aplicativos do Teams para GitHub, Azure DevOps e Jenkins.|
|[script-ci-template.sh](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-ci-template.sh) e [script-cd-template.sh](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-cd-template.sh)| Modelos de script para automação fora do GitHub, Azure DevOps ou Jenkins. |

## <a name="set-up-pipelines"></a>Configurar pipelines

Você pode configurar pipelines com as seguintes plataformas:

1. [Configurar pipelines com o GitHub](#set-up-pipelines-with-github)
1. [Configurar pipelines com o Azure DevOps](#set-up-pipelines-with-azure-devops)
1. [Configurar pipelines com o GitHub](#set-up-pipelines-with-jenkins)
1. [Configurar pipelines para outras plataformas](#set-up-pipelines-for-other-platforms)

## <a name="set-up-pipelines-with-github"></a>Configurar pipelines com o GitHub

Para configurar pipelines com o GitHub para CI/CD:

* Crie modelos de fluxo de trabalho.

  * Visual Studio Code
  * TeamsFx CLI

* Personalize o fluxo de trabalho de CI/CD.

### <a name="create-workflow-templates"></a>Criar modelos de fluxo de trabalho

Você pode criar os seguintes modelos de fluxo de trabalho com o GitHub:

**Kit de ferramentas do Teams para Visual Studio Code**

1. Criar um novo aplicativo de Equipes usando o Kit de Ferramentas do Teams.
1. Selecione o **ícone da API de** :::image type="icon" source="../assets/images/teams-toolkit-v2/add-API/api-add-icon.png" alt-text="ícone do Kit de Ferramentas do"::: Teams na barra de navegação à esquerda.
1. Selecione **Adicionar fluxos de trabalho de CI/CD**.
1. Selecione um ambiente no prompt de comando.
1. Selecione **GitHub** como o provedor de CI/CD.
1. Selecione pelo menos um modelo destas opções: CI, CD, Provisionar ou Publicar no Teams.
1. Abra o modelo e personalize os fluxos de trabalho que se encaixam em seus cenários.
1. Siga os arquivos LEIAME em `.github/workflows` para configurar o fluxo de trabalho no GitHub.

**TeamsFx CLI**

1. Insira `cd` no diretório do projeto de aplicativo do Teams.
2. Insira `teamsfx add cicd` para iniciar o processo de comando interativo.
3. Selecione um ambiente no prompt de comando.
4. Selecione **GitHub** como o provedor de CI/CD.
5. Selecione pelo menos um modelo destas opções: CI, CD, Provisionar ou Publicar no Teams.
7. Abra o modelo e personalize os fluxos de trabalho que se encaixam em seus cenários.
8. Siga os arquivos LEIAME em `.github/workflows` para configurar o fluxo de trabalho no GitHub.

> [!NOTE]
> Se você precisar adicionar modelos de fluxo de trabalho adicionais, poderá seguir o mesmo procedimento para criar um modelo de fluxo de trabalho no Visual Studio Code ou na CLI do TeamsFx.

### <a name="customize-cicd-workflow"></a>Personalizar fluxo de trabalho de CI/CD

Você pode alterar ou remover os scripts de teste para personalizar o fluxo de trabalho de CI/CD:

1. Por padrão, o fluxo de trabalho de CD é disparado, quando novas confirmações são feitas na ramificação`main`.
1. Altere os scripts de build, se necessário.
1. Remova os scripts de teste conforme necessário.

## <a name="set-up-pipelines-with-azure-devops"></a>Configurar pipelines com Azure DevOps

Para configurar pipelines com Azure DevOps para CI/CD:

* Crie modelos de fluxo de trabalho.

  * Visual Studio Code
  * TeamsFx CLI

* Personalize o fluxo de trabalho de CI/CD.

### <a name="create-workflow-templates"></a>Criar modelos de fluxo de trabalho

Você pode criar os seguintes modelos de fluxo de trabalho com o Azure DevOps:

**Kit de ferramentas do Teams para Visual Studio Code**

1. Criar um novo aplicativo de Equipes usando o Kit de Ferramentas do Teams.
2. Selecione o **ícone da API de** :::image type="icon" source="../assets/images/teams-toolkit-v2/add-API/api-add-icon.png" alt-text="ícone do Kit de Ferramentas do"::: Teams na barra de navegação à esquerda.
3. Selecione **Adicionar fluxos de trabalho de CI/CD**.
4. Selecione um ambiente no prompt de comando.
5. Selecione **Azure DevOps** como provedor de CI/CD.
6. Selecione pelo menos um modelo destas opções: CI, CD, Provisionar e Publicar no Teams.
7. Abra o modelo e personalize os fluxos de trabalho que se encaixam em seus cenários.
8. Siga os arquivos LEIAME em `.azure/pipelines` para configurar o fluxo de trabalho no Azure DevOps.

**TeamsFx CLI**

1. Insira `cd` no diretório do projeto de aplicativo do Teams.
2. Insira `teamsfx add cicd` para iniciar o processo de comando interativo.
3. Selecione um ambiente no prompt de comando.
4. Selecione **Azure DevOps** como provedor de CI/CD.
5. Selecione pelo menos um modelo destas opções: CI, CD, Provisionar ou Publicar no Teams.
7. Abra o modelo e personalize os fluxos de trabalho que se encaixam em seus cenários.
8. Siga os arquivos LEIAME em `.azure/pipelines` para configurar o fluxo de trabalho no Azure DevOps.

> [!NOTE]
> Se você precisar adicionar modelos de fluxo de trabalho adicionais, poderá seguir o mesmo procedimento para criar um modelo de fluxo de trabalho no Visual Studio Code ou na CLI do TeamsFx.

### <a name="customize-ci-workflow"></a>Personalizar fluxo de trabalho de CI

Você pode fazer as seguintes alterações para o script ou a definição de fluxo de trabalho:

1. Usar o script de build npm ou personalize a maneira como você cria no código de automação.
1. Use o script de teste npm, que retorna zero para êxito, e altere os comandos de teste.

### <a name="customize-cd-workflow"></a>Personalizar fluxo de trabalho de CD

Você pode fazer as seguintes alterações para o script ou a definição de fluxo de trabalho:

1. Certifique-se de ter um script de compilação npm ou personalize a maneira como você compila o código de automação.
1. Certifique-se de ter um script de teste npm, que retorne zero para sucesso ou altere os comandos de teste.

## <a name="set-up-pipelines-with-jenkins"></a>Configurar pipelines com Jenkins

Para configurar pipelines com Jenkins para CI/CD:

* Crie modelos de fluxo de trabalho.

  * Visual Studio Code
  * TeamsFx CLI

* Personalize o fluxo de trabalho de CI/CD.

### <a name="create-workflow-templates"></a>Criar modelos de fluxo de trabalho

Você pode criar os seguintes modelos de fluxo de trabalho com Jenkins:

**Kit de ferramentas do Teams para Visual Studio Code**

1. Criar um novo aplicativo de Equipes usando o Kit de Ferramentas do Teams.
2. Selecione o **ícone da API de** :::image type="icon" source="../assets/images/teams-toolkit-v2/add-API/api-add-icon.png" alt-text="ícone do Kit de Ferramentas do"::: Teams na barra de navegação à esquerda.
3. Selecione **Adicionar fluxos de trabalho de CI/CD**.
4. Selecione um ambiente no prompt de comando.
5. Selecione **Jenkins** como provedor de CI/CD.
6. Selecione pelo menos um modelo destas opções: CI, CD, Provisionar ou Publicar no Teams.
7. Abra o modelo e personalize os fluxos de trabalho que se encaixam em seus cenários.
8. Siga os arquivos LEIAME em `.jenkins/pipelines` para configurar o fluxo de trabalho com o Jenkins.

**TeamsFx CLI**

1. Insira `cd` no diretório do projeto de aplicativo do Teams.
2. Insira `teamsfx add cicd` para iniciar o processo de comando interativo.
3. Selecione um ambiente no prompt de comando.
4. Selecione **Jenkins** como provedor de CI/CD.
5. Selecione pelo menos um modelo destas opções: CI, CD, Provisionar ou Publicar no Teams.
7. Abra o modelo e personalize os fluxos de trabalho que se encaixam em seus cenários.
8. Siga os arquivos LEIAME em `.jenkins/pipelines` para configurar o fluxo de trabalho com o Jenkins.

> [!NOTE]
> Se você precisar adicionar modelos de fluxo de trabalho adicionais, poderá seguir o mesmo procedimento para criar um modelo de fluxo de trabalho no Visual Studio Code ou na CLI do TeamsFx.

### <a name="customize-ci-workflow"></a>Personalizar fluxo de trabalho de CI

Você pode fazer as seguintes alterações em seu projeto:

1. Altere como o fluxo de CI é acionado. O padrão é usar os gatilhos do **pollSCM** quando uma nova alteração é enviada para o branch **dev**.
1. Certifique-se de ter um script de compilação npm ou personalize a maneira como você compila o código de automação.
1. Certifique-se de ter um script de teste npm, que retorne zero para sucesso ou altere os comandos de teste.

### <a name="customize-cd-workflow"></a>Personalizar fluxo de trabalho de CD

Execute as seguintes etapas para personalizar o pipeline de CD:

1. Altere o fluxo de CD. O padrão é usar os gatilhos de `pollSCM` quando uma nova alteração é enviada por push para o branch `main`.
1. Altere os scripts de build, se necessário.
1. Remova os scripts de teste se você não tiver testes.

## <a name="set-up-pipelines-for-other-platforms"></a>Configurar pipelines para outras plataformas

Você pode seguir os scripts bash de exemplo listados predefinidos para criar e personalizar pipelines de CI/CD em outras plataformas:

* [Scripts CI](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-ci-template.sh)
* [Scripts CI](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-cd-template.sh)

Os scripts são baseados em uma ferramenta de linha de comando do TeamsFx multiplataforma [TeamsFx-CLI](https://www.npmjs.com/package/@microsoft/teamsfx-cli). Você pode instalá-lo com `npm install -g @microsoft/teamsfx-cli` e seguir a [documentação](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md) para personalizar os scripts.

> [!NOTE]
>
> * Para habilitar `@microsoft/teamsfx-cli` em execução no modo CI, ative `CI_ENABLED` por `export CI_ENABLED=true`. No modo CI, `@microsoft/teamsfx-cli` é amigável para CI/CD.
> * Para habilitar `@microsoft/teamsfx-cli` em execução no modo não interativo, defina uma configuração global com o comando: `teamsfx config set -g interactive false`. No modo não interativo, `@microsoft/teamsfx-cli` não solicita entradas.

Certifique-se de configurar as credenciais do Azure e do Microsoft 365 em suas variáveis de ambiente com segurança. Por exemplo, se você estiver usando o GitHub como repositório de código-fonte, consulte [GitHub Secrets](https://docs.github.com/en/actions/reference/encrypted-secrets).

## <a name="provision-and-deploy-resources"></a>Provisionar e implantar recursos

Para provisionar e implantar recursos direcionados ao Azure dentro de CI/CD, você deve criar uma entidade de serviço do Azure para uso.

Execute as seguintes etapas para criar entidades de serviço do Azure:

1. Registre um aplicativo do Microsoft Azure Active Directory (Azure AD) em um único locatário.
2. Atribua uma função ao seu aplicativo do Azure AD para acessar sua assinatura do Azure. A `Contributor` função é recomendada.
3. Crie um novo segredo do aplicativo do Azure AD.

> [!TIP]
> Salve sua ID de locatário, ID do aplicativo (AZURE_SERVICE_PRINCIPAL_NAME) e o segredo (AZURE_SERVICE_PRINCIPAL_PASSWORD) para uso futuro.

Para obter mais informações, consulte[Diretrizes de entidades de serviço do Azure](/azure/active-directory/develop/howto-create-service-principal-portal). A seguir estão as três maneiras de criar entidades de serviço:

* [Portal do Microsoft Azure](/azure/active-directory/develop/howto-create-service-principal-portal)
* [Windows PowerShell](/azure/active-directory/develop/howto-authenticate-service-principal-powershell)
* [CLI do Microsoft Azure](/cli/azure/create-an-azure-service-principal-azure-cli)

## <a name="publish-teams-app-using-teams-developer-portal"></a>Publicar o aplicativo do Teams usando o Portal do Desenvolvedor do Teams

Se houver alterações relacionadas ao arquivo de manifesto do aplicativo Teams, você poderá atualizar o manifesto e publicar o aplicativo do Teams novamente. Para publicar o aplicativo do Teams manualmente, você pode aproveitar o [Portal do Desenvolvedor para o Teams](https://dev.teams.microsoft.com/home).

Execute as seguintes etapas para publicar o aplicativo :

1. Entre no portal do [desenvolvedor do Teams](https://dev.teams.microsoft.com) usando a conta correspondente.
2. Importe o pacote do aplicativo em zip, selecione `App -> Import app -> Replace`.
3. Selecione o aplicativo de destino na lista de aplicativos.
4. Publique seu aplicativo, selecione `Publish -> Publish to your org`.

### <a name="see-also"></a>Confira também

* [Início Rápido para Ações do GitHub](https://docs.github.com/en/actions/quickstart#creating-your-first-workflow)
* [Criar seu primeiro pipeline do Azure DevOps](/azure/devops/pipelines/create-first-pipeline)
* [Criar seu primeiro pipeline do Jenkins](https://www.jenkins.io/doc/pipeline/tour/hello-world/)
* [Gerencie seus aplicativos com o Portal do Desenvolvedor do Microsoft Teams](../concepts/build-and-test/teams-developer-portal.md)
