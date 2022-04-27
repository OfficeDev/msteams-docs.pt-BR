---
title: Saiba como usar modelos de pipeline de CI/CD em GitHub, Azure DevOps e Jenkins para desenvolvedores Teams aplicativos
author: MuyangAmigo
description: Modelos de CI/CD
ms.author: ruhe
ms.localizationpriority: medium
ms.topic: overview
ms.date: 04/20/2022
ms.openlocfilehash: 66560b1f228c32b0faf6569ff0ae536a81dc33c0
ms.sourcegitcommit: 3bfd0d2c4d83f306023adb45c8a3f829f7150b1d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65073290"
---
# <a name="set-up-cicd-pipelines"></a>Configurar pipelines de CI/CD

O TeamsFx ajuda a automatizar seu fluxo de trabalho de desenvolvimento ao criar Teams aplicativo. A seguir estão as ferramentas e modelos que você pode usar para configurar pipelines de CI/CD, criar modelos de fluxo de trabalho e personalizar o fluxo de trabalho de CI/CD com GitHub, Azure DevOps, Jenkins e outras plataformas. Para provisionar e implantar recursos, você pode criar entidades de serviço do Azure e publicar o aplicativo Teams usando Teams Portal do Desenvolvedor. Para publicar Teams aplicativo manualmente, você pode aproveitar o [Portal do Desenvolvedor para Teams](https://dev.teams.microsoft.com/home).


|Ferramentas e modelos | Descrição |
|---|---|
|[TeamsFx-CLI-Action](https://github.com/OfficeDev/teamsfx-cli-action)|GitHub ação que se integra à CLI do TeamsFx.|
|[Teams Toolkit em Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension)| Visual Studio Code extensão que ajuda você a desenvolver um aplicativo Teams, bem como fluxos de trabalho de automação para GitHub, Azure DevOps e Jenkins. |
|[TeamsFx CLI](https://www.npmjs.com/package/@microsoft/teamsfx-cli) | Ferramenta de Linha de Comando que ajuda você a desenvolver um aplicativo Teams, bem como fluxos de trabalho de automação para GitHub, Azure DevOps e Jenkins.|
|[script-ci-template.sh](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-ci-template.sh) e [script-cd-template.sh](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-cd-template.sh)| Modelos de script para automação fora GitHub, Azure DevOps ou Jenkins. |


## <a name="set-up-pipelines"></a>Configurar pipelines

Você pode configurar pipelines com as seguintes plataformas:

1. [Configurar pipelines com GitHub](#set-up-pipelines-with-github)
1. [Configurar pipelines com Azure DevOps](#set-up-pipelines-with-azure-devops)
1. [Configurar pipelines com Jenkins](#set-up-pipelines-with-jenkins)
1. [Configurar pipelines para outras plataformas](#set-up-pipelines-for-other-platforms)


### <a name="set-up-pipelines-with-github"></a>Configurar pipelines com GitHub

Para configurar pipelines com GitHub para CI/CD:

1. Criar modelos de fluxo de trabalho.

   * Visual Studio Code
   * TeamsFx CLI

1. Personalize o fluxo de trabalho de CI/CD.


## <a name="create-workflow-templates-with-github"></a>Criar modelos de fluxo de trabalho com GitHub

**Criar modelos de fluxo de trabalho usando o Teams Toolkit no Visual Studio Code**

1. Crie um novo projeto Teams aplicativo usando Teams Toolkit.
1. Selecione **Teams Toolkit** ícone na barra Visual Studio Code atividade.
1. Selecione **Adicionar Fluxos de Trabalho de CI/CD**.
1. Selecione um ambiente no prompt de comando.
1. Selecione **GitHub** como o provedor de CI/CD.
1. Selecione pelo menos um modelo destas opções: CI, CD, Provisionar ou Publicar no Teams.
1. Abra o modelo e personalize os fluxos de trabalho que se ajustam aos seus cenários.
1. Siga os arquivos LEIAME abaixo `.github/workflows` para configurar o fluxo de trabalho no GitHub.

**Criar modelos de fluxo de trabalho usando a CLI do TeamsFx**

1. Insira `cd` o diretório do projeto Teams aplicativo.
2. Insira `teamsfx add cicd` o comando para iniciar o processo de comando interativo.
3. Selecione um ambiente no prompt de comando.
4. Selecione **GitHub** como o provedor de CI/CD.
5. Selecione pelo menos um modelo destas opções: CI, CD, Provisionar ou Publicar no Teams.
7. Abra o modelo e personalize os fluxos de trabalho que se ajustam aos seus cenários.
8. Siga os arquivos LEIAME abaixo `.github/workflows` para configurar o fluxo de trabalho no GitHub.

> [!NOTE]
> Se você precisar adicionar modelos de fluxo de trabalho adicionais, poderá seguir o mesmo procedimento para criar um modelo de fluxo de trabalho no Visual Studio Code ou na CLI do TeamsFx.

### <a name="customize-cicd-workflow"></a>Personalizar fluxo de trabalho de CI/CD

Você pode alterar ou remover os scripts de teste para personalizar o fluxo de trabalho de CI/CD:

1. Por padrão, o fluxo de trabalho de CD é disparado, quando novas confirmações são feitas no `main` branch.
1. Altere os scripts de build, se necessário.
1. Remova os scripts de teste conforme necessário.

### <a name="set-up-pipelines-with-azure-devops"></a>Configurar pipelines com Azure DevOps

Para configurar pipelines com Azure DevOps para CI/CD:

1. Criar modelos de fluxo de trabalho.

   * Visual Studio Code
   * TeamsFx CLI

1. Personalize o fluxo de trabalho de CI/CD.


## <a name="create-workflow-templates-with-azure-devops"></a>Criar modelos de fluxo de trabalho com Azure DevOps

**Criar modelos de fluxo de trabalho usando o Teams Toolkit no Visual Studio Code**

1. Crie um novo projeto Teams aplicativo usando Teams Toolkit.
2. Selecione **Teams Toolkit** ícone na barra Visual Studio Code atividade.
3. Selecione **Adicionar Fluxos de Trabalho de CI/CD**.
4. Selecione um ambiente no prompt de comando.
5. Selecione **Azure DevOps** como provedor de CI/CD.
6. Selecione pelo menos um modelo destas opções: CI, CD, Provisionar e Publicar no Teams.
7. Abra o modelo e personalize os fluxos de trabalho que se ajustam aos seus cenários.
8. Siga os arquivos LEIAME abaixo para `.azure/pipelines` configurar o fluxo de trabalho no Azure DevOps.

**Criar modelos de fluxo de trabalho usando a CLI do TeamsFx**

1. Insira `cd` o diretório do projeto Teams aplicativo.
2. Insira `teamsfx add cicd` o comando para iniciar o processo de comando interativo.
3. Selecione um ambiente no prompt de comando.
4. Selecione **Azure DevOps** como provedor de CI/CD.
5. Selecione pelo menos um modelo destas opções: CI, CD, Provisionar ou Publicar no Teams.
7. Abra o modelo e personalize os fluxos de trabalho que se ajustam aos seus cenários.
8. Siga os arquivos LEIAME abaixo para `.azure/pipelines` configurar o fluxo de trabalho no Azure DevOps.

> [!NOTE]
> Se você precisar adicionar modelos de fluxo de trabalho adicionais, poderá seguir o mesmo procedimento para criar um modelo de fluxo de trabalho no Visual Studio Code ou na CLI do TeamsFx.

### <a name="customize-ci-workflow"></a>Personalizar fluxo de trabalho de CI

A seguir estão as alterações que você pode fazer para o script ou definição de fluxo de trabalho:

1. Use o script de build npm ou personalize a maneira como você cria no código de automação.
1. Use o script de teste npm que retorna zero para êxito e altere os comandos de teste.

### <a name="customize-cd-workflow"></a>Personalizar fluxo de trabalho de CD

A seguir estão as alterações que você pode fazer para o script ou definição de fluxo de trabalho:

1. Verifique se você tem um script de build npm ou personalize a maneira como você cria no código de automação.
1. Verifique se você tem um script de teste npm que retorna zero para êxito ou altere os comandos de teste.

### <a name="set-up-pipelines-with-jenkins"></a>Configurar pipelines com Jenkins

Para configurar pipelines com o Jenkins para CI/CD:

1. Criar modelos de fluxo de trabalho.

   * Visual Studio Code
   * TeamsFx CLI

1. Personalize o fluxo de trabalho de CI/CD.

## <a name="create-workflow-templates-with-jenkins"></a>Criar modelos de fluxo de trabalho com Jenkins

**Criar modelos de fluxo de trabalho usando o Teams Toolkit no Visual Studio Code**

1. Crie um novo projeto Teams aplicativo usando Teams Toolkit.
2. Selecione **Teams Toolkit** ícone na barra Visual Studio Code lateral.
3. Selecione **Adicionar Fluxos de Trabalho de CI/CD**.
4. Selecione um ambiente no prompt de comando.
5. Selecione **Jenkins como** provedor de CI/CD.
6. Selecione pelo menos um modelo destas opções: CI, CD, Provisionar ou Publicar no Teams.
7. Abra o modelo e personalize os fluxos de trabalho que se ajustam aos seus cenários.
8. Siga os arquivos LEIAME abaixo para `.jenkins/pipelines` configurar o fluxo de trabalho com o Jenkins.

**Criar modelos de fluxo de trabalho usando a CLI do TeamsFx**

1. Insira `cd` o diretório do projeto Teams aplicativo.
2. Insira `teamsfx add cicd` o comando para iniciar o processo de comando interativo.
3. Selecione um ambiente no prompt de comando.
4. Selecione **Jenkins como** provedor de CI/CD.
5. Selecione pelo menos um modelo destas opções: CI, CD, Provisionar ou Publicar no Teams.
7. Abra o modelo e personalize os fluxos de trabalho que se ajustam aos seus cenários.
8. Siga os arquivos LEIAME abaixo para `.jenkins/pipelines` configurar o fluxo de trabalho com o Jenkins.

> [!NOTE]
> Se você precisar adicionar modelos de fluxo de trabalho adicionais, poderá seguir o mesmo procedimento para criar um modelo de fluxo de trabalho no Visual Studio Code ou na CLI do TeamsFx.

### <a name="customize-ci-workflow"></a>Personalizar fluxo de trabalho de CI

A seguir estão algumas das alterações que você pode fazer em seu projeto:

1. Altere como o fluxo de CI é disparado. O padrão é usar os gatilhos do **pollSCM** quando uma nova alteração é enviada por push para o **branch de** desenvolvimento.
1. Verifique se você tem um script de build npm ou personalize a maneira como você cria no código de automação.
1. Verifique se você tem um script de teste npm que retorna zero para êxito ou altere os comandos de teste.


### <a name="customize-cd-workflow"></a>Personalizar fluxo de trabalho de CD

Execute as seguintes etapas para personalizar o pipeline de CD:

1. Altere o fluxo de CD. O padrão é usar os gatilhos de `pollSCM` quando uma nova alteração é enviada por push para o `main` branch.
1. Altere os scripts de build, se necessário.
1. Remova os scripts de teste se você não tiver testes.


### <a name="set-up-pipelines-for-other-platforms"></a>Configurar pipelines para outras plataformas

Você pode seguir os scripts bash de exemplo listados predefinidos para criar e personalizar pipelines de CI/CD em outras plataformas:

* [CI Scripts](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-ci-template.sh)
* [CD Scripts](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-cd-template.sh)

Os scripts são baseados em uma ferramenta de linha de comando teamsFx multiplataforma [TeamsFx-CLI](https://www.npmjs.com/package/@microsoft/teamsfx-cli). Você pode instalá-lo com `npm install -g @microsoft/teamsfx-cli` e seguir a [documentação](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md) para personalizar os scripts.

> [!NOTE]
>
> * Para habilitar `@microsoft/teamsfx-cli` a execução no modo CI, ative `CI_ENABLED` por `export CI_ENABLED=true`. No modo CI, é `@microsoft/teamsfx-cli` amigável para CI/CD.
> * Para habilitar `@microsoft/teamsfx-cli` a execução no modo não interativo, defina uma configuração global com o comando: `teamsfx config set -g interactive false`. No modo não interativo, `@microsoft/teamsfx-cli` não solicita entradas.

Certifique-se de configurar o Azure e Microsoft 365 credenciais em suas variáveis de ambiente com segurança. Por exemplo, se você estiver usando GitHub seu repositório de código-fonte, consulte [Segredos do Github](https://docs.github.com/en/actions/reference/encrypted-secrets).


## <a name="provision-and-deploy-resources"></a>Provisionar e implantar recursos

Para provisionar e implantar recursos direcionados ao Azure dentro de CI/CD, você deve criar uma entidade de serviço do Azure para uso.

Execute as seguintes etapas para criar entidades de serviço do Azure:

1. Registre um Microsoft Azure Active Directory (Azure AD) em um único locatário.
2. Atribua uma função ao seu aplicativo do Azure AD para acessar sua assinatura do Azure. A `Contributor` função é recomendada.
3. Crie um novo segredo do aplicativo do Azure AD.

> [!TIP]
> Salve sua ID de locatário, id do aplicativo (AZURE_SERVICE_PRINCIPAL_NAME) e o segredo (AZURE_SERVICE_PRINCIPAL_PASSWORD) para uso futuro.

Para obter mais informações, consulte [as diretrizes de entidades de serviço do Azure](/azure/active-directory/develop/howto-create-service-principal-portal). Estas são as três maneiras de criar entidades de serviço:

* [Microsoft Azure portal](/azure/active-directory/develop/howto-create-service-principal-portal)
* [Windows PowerShell](/azure/active-directory/develop/howto-authenticate-service-principal-powershell)
* [Microsoft Azure CLI](/cli/azure/create-an-azure-service-principal-azure-cli)

## <a name="publish-teams-app-using-teams-developer-portal"></a>Publicar Teams aplicativo usando Teams Portal do Desenvolvedor

Se houver alterações relacionadas Teams arquivo de manifesto do aplicativo, você poderá atualizar o manifesto e publicar o Teams aplicativo novamente.

Para publicar Teams aplicativo manualmente, você pode aproveitar o [Portal do Desenvolvedor para Teams](https://dev.teams.microsoft.com/home).

Execute as seguintes etapas para publicar seu aplicativo:

1. Entre no [portal do desenvolvedor para Teams](https://dev.teams.microsoft.com) usando a conta correspondente.
2. Importe o pacote do aplicativo em zip selecionando `App -> Import app -> Replace`.
3. Selecione o aplicativo de destino na lista de aplicativos.
4. Publique seu aplicativo selecionando `Publish -> Publish to your org`.

### <a name="see-also"></a>Confira também

* [Início Rápido para GitHub Actions](https://docs.github.com/en/actions/quickstart#creating-your-first-workflow)
* [Criar seu primeiro pipeline de Azure DevOps](/azure/devops/pipelines/create-first-pipeline)
* [Criar seu primeiro pipeline do Jenkins](https://www.jenkins.io/doc/pipeline/tour/hello-world/)
* [Gerencie seus aplicativos com o Portal do Desenvolvedor do Microsoft Teams](/concepts/build-and-test/teams-developer-portal)
