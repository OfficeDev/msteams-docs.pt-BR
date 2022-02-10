---
title: Suporte a CI ou CD para Teams desenvolvedores de aplicativos
author: MuyangAmigo
description: Modelos CICD
ms.author: ruhe
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: f8de6dd66b281f8cf842e5439d3a217598f46047
ms.sourcegitcommit: 90587b1ec04bf20d716ed6feb8ccca4313e87f8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/10/2022
ms.locfileid: "62518111"
---
# <a name="cicd-guide"></a>Guia de CI/CD

O TeamsFx ajuda a automatizar seu fluxo de trabalho de desenvolvimento durante a criação Teams aplicativo. O documento fornece ferramentas e modelos para você começar a configurar pipelines CI ou CD com GitHub, Azure Devops e Jenkins.

|Ferramentas e modelos|Descrição| 
|---|---|
|[teamsfx-cli-action](https://github.com/OfficeDev/teamsfx-cli-action)|GitHub Ação que se integra ao TeamsFx CLI.|
|[github-ci-template.yml](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/github-ci-template.yml) e [github-cd-template.yml](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/github-cd-template.yml)| GitHub modelos CI ou CD para Teams aplicativo. |
|[jenkins-ci-template. Modelo de jenkinsfile](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/jenkins-ci-template.Jenkinsfile) [e jenkins-cd. Jenkinsfile](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/jenkins-cd-template.Jenkinsfile)|Modelos de CI ou CD do Jenkins para um Teams aplicativo.|
|[script-ci-template.sh](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-ci-template.sh) e [script-cd-template.sh](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-cd-template.sh)| Modelos de script para automação fora do GitHub. |

## <a name="ci-or-cd-workflow-templates-in-github"></a>Modelos de fluxo de trabalho ci ou CD em GitHub

**Para incluir fluxos de trabalho de CI ou CD para automatizar Teams processo de desenvolvimento de aplicativos GitHub**:

1. Criar pasta em `.github/workflows`
1. Copie um dos seguintes arquivos de modelo:
    * [github-ci-template.yml](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/github-ci-template.yml) para fluxo de trabalho ci.
    * [github-cd-template.yml](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/github-cd-template.yml) para fluxo de trabalho de CD.
1. Personalize os fluxos de trabalho que se ajustam aos seus cenários.

### <a name="customize-ci-workflow"></a>Personalizar fluxo de trabalho ci

Execute as etapas a seguir para adaptar o fluxo de trabalho do seu projeto:

1. Altere o fluxo de CI. 
1. Use o script de com build npm ou personalize a maneira como você cria o projeto no código de automação.
1. Use o script de teste npm que retorna zero para sucesso e altere os comandos de teste.

### <a name="customize-cd-workflow"></a>Personalizar fluxo de trabalho de CD

Execute as etapas a seguir para personalizar o fluxo de trabalho de CD:

1. Por padrão, o fluxo de trabalho de CD é acionado, quando novas confirmações são feitas no `main` branch.
1. Crie GitHub [de repositório por](https://docs.github.com/en/actions/reference/encrypted-secrets) ambiente para manter a entidade de serviço do Azure e Microsoft 365 de logon da conta. Para obter mais informações, [consulte GitHub Actions](https://github.com/OfficeDev/teamsfx-cli-action/blob/main/README.md).
1. Altere os scripts de com build, se necessário.
1. Remova os scripts de teste conforme necessário.

> [!NOTE]
> A etapa de provisionamento não está incluída no modelo de CD, pois geralmente é executada apenas uma vez. Você pode executar o provisionamento Teams Toolkit, a CLI do TeamsFx ou usar um fluxo de trabalho separado. Certifique-se de se comprometer após o provisionamento. Os resultados do provisionamento são depositados na `.fx` pasta.

### <a name="github-secrets"></a>Segredos github

A tabela a seguir lista todos os segredos necessários para criar ambiente em GitHub:

1. Selecione **Configurações**.
1. Vá para **a seção Ambientes** .
1. Selecione **Novo ambiente**.
1. Insira um nome para seu ambiente. O nome de ambiente padrão fornecido no modelo é `test_environment`. 
1. Selecione **Configurar ambiente**.
1. Selecione **Adicionar Segredo**.

A tabela a seguir lista todos os segredos necessários para criar o ambiente:

|Nome|Descrição|
|---|---|
|`AZURE_SERVICE_PRINCIPAL_NAME`|O nome principal do serviço do Azure usado para provisionar recursos.|
|`AZURE_SERVICE_PRINCIPAL_PASSWORD`|A senha da entidade de serviço do Azure.|
|`AZURE_SUBSCRIPTION_ID`|Para identificar a assinatura na qual os recursos serão provisionados.|
|`AZURE_TENANT_ID`|Para identificar o locatário no qual a assinatura reside.|
|`M365_ACCOUNT_NAME`|A Microsoft 365 para criar e publicar Teams app.|
|`M365_ACCOUNT_PASSWORD`|A senha da conta Microsoft 365.|
|`M365_TENANT_ID`|Para identificar o locatário no qual o Teams App será criado/publicado. Esse valor é opcional, a menos que você tenha uma conta com vários locatários e queira usar outro locatário. Para obter mais informações, [consulte como encontrar sua Microsoft 365 ID de locatário](/azure/active-directory/fundamentals/active-directory-how-to-find-tenant).|

> [!NOTE]
> Atualmente, a entidade de serviço do Azure é usada em fluxos de trabalho ci/CD. Para obter mais informações, consulte [create Azure service principles](#create-azure-service-principals).

## <a name="set-up-ci-or-cd-pipelines-with-azure-devops"></a>Configurar pipelines CI ou CD com Azure DevOps

Você pode configurar pipelines automatizados em Azure DevOps e fazer uma referência nos scripts.

Execute as seguintes etapas para começar:

* [CI Scripts](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-ci-template.sh)
* [CD Scripts](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-cd-template.sh)

### <a name="set-up-ci-pipeline"></a>Configurar pipeline CI

1. Adicione [scripts ci](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-ci-template.sh) ao seu repositório Azure DevOps e faça as personalizações necessárias à medida que você pode inferir dos comentários no arquivo de script.
1. Siga as [etapas para criar seu Azure DevOps Pipeline para CI](/azure/devops/pipelines/create-first-pipeline).
Aqui está um cenário de scripts de pipeline CI comuns:

```yml
trigger:
- dev 

pool:
  vmImage: ubuntu-latest

steps:
- task: NodeTool@0
  inputs:
    versionSpec: '14.17.0'
    checkLatest: true
  
- task: Bash@3
  inputs:
    filePath: './others-script-ci-template.sh'
```

Veja a seguir as alterações que você pode fazer para o script ou a definição de fluxo de trabalho:

1. Altere o fluxo de CI. Padrão para quando uma nova confirmação é empurrada para o `dev` branch.
1. Altere a maneira de instalar o nó e o npm.
1. Use o script de com build npm ou personalize a maneira como você cria no código de automação.
1. Use o script de teste npm que retorna zero para sucesso e altere os comandos de teste.

### <a name="set-up-cd-pipeline"></a>Configurar pipeline de CD

1. Adicione [scripts de CD](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-cd-template.sh) ao repositório Azure DevOps e faça as personalizações necessárias à medida que você pode inferir dos comentários no arquivo de script.
1. Crie seu Azure DevOps para CD. Para obter mais informações, consulte [create first pipeline](/azure/devops/pipelines/create-first-pipeline). A definição do Pipeline pode ser referenciada para a definição de exemplo a seguir para o Pipeline CI.
1. Adicione as variáveis necessárias [por Definir](/azure/devops/pipelines/process/variables) variáveis e as faça como segredos, se necessário.

```yml
trigger:
- main 

pool:
  vmImage: ubuntu-latest

steps:
- task: NodeTool@0
  inputs:
    versionSpec: '14.17.0'
    checkLatest: true
  
- task: Bash@3
  env:
    SP_NAME: $(AZURE_SERVICE_PRINCIPAL_NAME)
    SP_PASSWORD: $(AZURE_SERVICE_PRINCIPAL_PASSWORD)
    TENANT_ID: $(AZURE_TENANT_ID)
    AZURE_SUBSCRIPTION_ID: $(AZURE_SUBSCRIPTION_ID)
    M365_ACCOUNT_NAME: $(M365_ACCOUNT_NAME)
    M365_ACCOUNT_PASSWORD: $(M365_ACCOUNT_PASSWORD)
  inputs:
    filePath: './others-script-cd-template.sh'
```

Veja a seguir as alterações que você pode fazer para o script ou a definição de fluxo de trabalho:

1. Como o fluxo de CD é disparado. Por padrão, isso acontece quando novas confirmações são feitas no **branch** principal.
1. Altere a maneira de instalar o nó e o npm.
1. Altere o nome do ambiente, por padrão, **sua preparação**.
1. Verifique se você tem um script de com build npm ou personalize a maneira como você cria no código de automação.
1. Verifique se você tem um script de teste npm que retorna zero para sucesso e/ou altere os comandos de teste.

### <a name="pipeline-variables-for-azure-devops"></a>Variáveis de pipeline para Azure DevOps

Execute as etapas a seguir para criar variáveis pipeline em Azure DevOps:

1. Na página Edição do Pipeline, selecione **Variáveis** e selecione **Nova variável**.
1. Insira o par Nome ou Valor para sua variável.
1. Alterne a caixa de seleção de **Manter esse valor em segredo** , se necessário.
1. Selecione **OK** para criar a variável.

|Nome|Descrição|
|---|---|
|`AZURE_SERVICE_PRINCIPAL_NAME`|O nome principal do serviço do Azure usado para provisionar recursos.|
|`AZURE_SERVICE_PRINCIPAL_PASSWORD`|A senha da entidade de serviço do Azure.|
|`AZURE_SUBSCRIPTION_ID`|Para identificar a assinatura na qual os recursos serão provisionados.|
|`AZURE_TENANT_ID`|Para identificar o locatário no qual a assinatura reside.|
|`M365_ACCOUNT_NAME`|A Microsoft 365 para criar e publicar o Teams App.|
|`M365_ACCOUNT_PASSWORD`|A senha da conta Microsoft 365.|
|`M365_TENANT_ID`|Para identificar o locatário no qual o Teams App será criado/publicado. Esse valor é opcional, a menos que você tenha uma conta com vários locatários e queira usar outro locatário. Leia mais sobre [como encontrar sua ID Microsoft 365 locatário.](/azure/active-directory/fundamentals/active-directory-how-to-find-tenant)|

## <a name="ci-or-cd-pipeline-templates-in-jenkins"></a>Modelos de pipeline ci ou CD no Jenkins

Para adicionar esses modelos ao repositório, você exige as versões do [modelo jenkins-ci. Modelo de jenkinsfile](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/jenkins-ci-template.Jenkinsfile)  [e jenkins-cd. Jenkinsfile](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/jenkins-cd-template.Jenkinsfile) a ser localizado em seu repositório por filial.

Além disso, você precisa criar pipelines CI ou CD no Jenkins que apontem para o **Jenkinsfile específico** correspondentemente.

Siga as etapas para verificar como conectar o Jenkins a diferentes plataformas SCM:

1. [Jenkins com GitHub](https://www.jenkins.io/solutions/github/)
2. [Jenkins com Azure DevOps](https://www.dragonspears.com/blog/ci-cd-with-jenkins-and-azure-devops-services)
3. [Jenkins com GitLab](https://docs.gitlab.com/ee/integration/jenkins.html)
4. [Jenkins com Bitbucket](https://medium.com/ampersand-academy/integrate-bitbucket-jenkins-c6e51103d0fe)

### <a name="customize-ci-pipeline"></a>Personalizar pipeline CI

Veja a seguir algumas das alterações que você pode fazer para adaptar seu projeto:

1. Renomeie o arquivo de modelo para **Jenkinsfile** e coloque-o sob o branch de destino, por exemplo, o **branch de dev** .
1. Altere como o fluxo de CI é disparado. Padrão é usar os gatilhos do **pollSCM** quando uma nova alteração é empurrada para o **branch de dev** .
1. Verifique se você tem um script de com build npm ou personalize a maneira como você cria no código de automação.
1. Verifique se você tem um script de teste npm que retorna zero para sucesso e/ou altere os comandos de teste.

### <a name="customize-cd-pipeline"></a>Personalizar pipeline de CD

Execute as seguintes etapas para personalizar o pipeline de CD:

1. Renomeie o arquivo de modelo para **Jenkinsfile** e coloque-o sob o branch de destino, por exemplo, o **branch** principal.
1. Altere o fluxo de CD. Padrão é usar os gatilhos do **pollSCM** quando uma nova alteração é empurrada para o **branch** principal.
1. Crie credenciais [de pipeline do](https://www.jenkins.io/doc/book/using/using-credentials/) Jenkins para manter a entidade de serviço do Azure e Microsoft 365 de logon da conta.
1. Altere os scripts de com build, se necessário.
1. Remova os scripts de teste se você não tiver testes.

### <a name="credentials-for-jenkins"></a>Credenciais para o Jenkins

Siga [as credenciais de uso](https://www.jenkins.io/doc/book/using/using-credentials/) para criar credenciais no Jenkins.

|Nome|Descrição|
|---|---|
|`AZURE_SERVICE_PRINCIPAL_NAME`|O nome principal do serviço do Azure usado para provisionar recursos.|
|`AZURE_SERVICE_PRINCIPAL_PASSWORD`|A senha da entidade de serviço do Azure.|
|`AZURE_SUBSCRIPTION_ID`|Para identificar a assinatura na qual os recursos serão provisionados.|
|`AZURE_TENANT_ID`|Para identificar o locatário no qual a assinatura reside.|
|`M365_ACCOUNT_NAME`|A Microsoft 365 para criar e publicar o Teams App.|
|`M365_ACCOUNT_PASSWORD`|A senha da conta Microsoft 365.|
|`M365_TENANT_ID`|Para identificar o locatário no qual o aplicativo Teams é criado ou publicado. O valor é opcional, a menos que você tenha uma conta com vários locatários e queira usar outro locatário. Leia mais sobre [como encontrar sua ID Microsoft 365 locatário.](/azure/active-directory/fundamentals/active-directory-how-to-find-tenant)|

## <a name="get-started-guide-for-other-platforms"></a>Guia de início para outras plataformas

Você pode seguir os scripts de bash de exemplo pré-definidos listados para criar e personalizar pipelines de CI ou CD em outras plataformas:

* [CI Scripts](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-ci-template.sh)
* [CD Scripts](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-cd-template.sh)

Os scripts são baseados em uma ferramenta de linha de comando [TeamsFx-CLI](https://www.npmjs.com/package/@microsoft/teamsfx-cli) entre plataformas. Você pode instalá-lo com `npm install -g @microsoft/teamsfx-cli` e seguir a [documentação](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md) para personalizar os scripts.

> [!NOTE]
> * Para habilitar `@microsoft/teamsfx-cli` a execução no modo CI, ative `CI_ENABLED` por `export CI_ENABLED=true`. No modo CI, `@microsoft/teamsfx-cli` é amigável para CI ou CD.
> * Para habilitar `@microsoft/teamsfx-cli` a execução no modo não interativo, de definir uma configuração global com o comando: `teamsfx config set -g interactive false`. No modo não interativo, `@microsoft/teamsfx-cli` não fará perguntas sobre entradas interativamente.

Certifique-se de definir credenciais do Azure e do Microsoft365 em suas variáveis de ambiente com segurança. Por exemplo, se você estiver usando GitHub como repositório de código-fonte. Para obter mais informações, consulte [Github Secrets](https://docs.github.com/en/actions/reference/encrypted-secrets).

## <a name="create-azure-service-principals"></a>Criar entidades de serviço do Azure

Para provisionar e implantar recursos destinados ao Azure dentro de CI/CD, você deve criar uma entidade de serviço do Azure para uso.

Execute as seguintes etapas para criar entidades de serviço do Azure:
1. Registre um Microsoft Azure Active Directory (Azure AD) em locatário único.
2. Atribua uma função ao seu aplicativo Microsoft Azure Active Directory (Azure AD) para acessar sua assinatura do Azure e `Contributor` a função é recomendada. 
3. Crie um novo Microsoft Azure Active Directory de aplicativo (Azure AD).

> [!TIP]
> Salve sua id de locatário, id do aplicativo(AZURE_SERVICE_PRINCIPAL_NAME) e o segredo(AZURE_SERVICE_PRINCIPAL_PASSWORD) para uso futuro.

Para obter mais informações, consulte [Diretrizes de entidades de serviço do Azure](/azure/active-directory/develop/howto-create-service-principal-portal). Veja a seguir as três maneiras de criar a entidade de serviço: 
* [Microsoft Azure portal](/azure/active-directory/develop/howto-create-service-principal-portal)
* [Windows PowerShell](/azure/active-directory/develop/howto-authenticate-service-principal-powershell)
* [Microsoft Azure CLI](/cli/azure/create-an-azure-service-principal-azure-cli)

## <a name="publish-teams-app-using-teams-developer-portal"></a>Publicar Teams aplicativo usando Teams Portal do Desenvolvedor
Se houver alterações relacionadas Teams arquivo de manifesto do aplicativo, talvez você queira publicar o Teams aplicativo novamente para atualizar o manifesto.

Para publicar Teams aplicativo manualmente, você pode aproveitar o Portal do [Desenvolvedor para Teams](https://dev.teams.microsoft.com/home).

Execute as seguintes etapas para publicar seu aplicativo:
1. Entre no [portal do desenvolvedor para Teams](https://dev.teams.microsoft.com) usando a conta correspondente.
2. Importe seu pacote de aplicativo em zip selecionando `App -> Import app -> Replace`.
3. Selecione o aplicativo de destino na lista de aplicativos.
4. Publicar seu aplicativo selecionando `Publish -> Publish to your org`

### <a name="see-also"></a>Confira também

* [Início rápido para GitHub ações](https://docs.github.com/en/actions/quickstart#creating-your-first-workflow)
* [Criar sua primeira Azure DevOps Pipeline](/azure/devops/pipelines/create-first-pipeline)
* [Criar seu primeiro Pipeline do Jenkins](https://www.jenkins.io/doc/pipeline/tour/hello-world/)
* [Gerencie seus aplicativos com o Portal do Desenvolvedor do Microsoft Teams](/concepts/build-and-test/teams-developer-portal)
