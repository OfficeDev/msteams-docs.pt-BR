---
title: Suporte a CI ou CD para Teams desenvolvedores de aplicativos
author: MuyangAmigo
description: Modelos CICD
ms.author: ruhe
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: acd12a96365bf97bd419045c415e71efd3a118e2
ms.sourcegitcommit: aede47694894d281f6b725083bc0b46ab0e4846d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2021
ms.locfileid: "61591775"
---
# <a name="ci-or-cd-support-for-teams-application-developers"></a>Suporte a CI ou CD para Teams desenvolvedores de aplicativos

O TeamsFx ajuda a automatizar seu fluxo de trabalho de desenvolvimento durante a criação Teams aplicativo. O documento fornece ferramentas e modelos pré-preparados para você começar a configurar pipelines CI ou CD com as plataformas de desenvolvimento mais populares, incluindo GitHub, Azure Devops e Jenkins.

|Ferramentas e modelos|Descrição|
|---|---|
|[teamsfx-cli-action](https://github.com/OfficeDev/teamsfx-cli-action)|Uma ação de GitHub pronta para uso que se integra à CLI do TeamsFx.|
|[github-ci-template.yml](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/github-ci-template.yml) e [github-cd-template.yml](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/github-cd-template.yml)| GitHub modelos de CI ou CD para um Teams aplicativo. |
|[jenkins-ci-template. Modelo de jenkinsfile](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/jenkins-ci-template.Jenkinsfile) [e jenkins-cd. Jenkinsfile](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/jenkins-cd-template.Jenkinsfile)|Modelos de CI ou CD do Jenkins para um Teams aplicativo.|
|[script-ci-template.sh](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-ci-template.sh) e [script-cd-template.sh](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-cd-template.sh)| Modelos de script para automação em qualquer outro lugar fora do GitHub. |

## <a name="ci-or-cd-workflow-templates-in-github"></a>Modelos de fluxo de trabalho ci ou CD em GitHub

**Para incluir fluxos de trabalho ci** ou CD para automatizar Teams processo de desenvolvimento de aplicativos em GitHub :

1. Criar uma pasta em `.github/workflows`
1. Copie os arquivos de modelo (um ou ambos):
    * [github-ci-template.yml](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/github-ci-template.yml) para fluxo de trabalho ci.
    * [github-cd-template.yml](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/github-cd-template.yml) para fluxo de trabalho de CD.
1. Personalize esses fluxos de trabalho para ajustar seus cenários.

### <a name="customize-ci-workflow"></a>Personalizar fluxo de trabalho ci

Você pode fazer as seguintes alterações para adaptar o fluxo de trabalho do seu projeto:

1. Altere como o fluxo de CI é disparado. Padrão para quando uma solicitação pull é criada direcionando o `dev` branch.
1. Use um script de com build npm ou personalize a maneira como você cria o projeto no código de automação.
1. Use um script de teste npm que retorna zero para sucesso e/ou altere os comandos de teste.

### <a name="customize-cd-workflow"></a>Personalizar fluxo de trabalho de CD

As etapas a seguir para personalizar o fluxo de trabalho de CD:

1. Por padrão, o fluxo de trabalho de CD é acionado, quando novas confirmações são feitas no `main` branch.
1. Crie GitHub [de repositório por](https://docs.github.com/en/actions/reference/encrypted-secrets) ambiente para manter o Azure ou Microsoft 365 de logon. A tabela a seguir lista todos os segredos que você precisa criar no GitHub e, para uso detalhado, consulte o GitHub Ações [README.md](https://github.com/OfficeDev/teamsfx-cli-action/blob/main/README.md).
1. Altere os scripts de com build, se necessário.
1. Remova os scripts de teste se você não tiver testes.

> [!Note]
> A etapa de provisionamento não está incluída no modelo de CD, pois geralmente é executada apenas uma vez. Você pode executar o provisionamento em Teams Toolkit, no TeamsFx CLI ou usando um fluxo de trabalho separado. Lembre-se de se comprometer após o provisionamento (os resultados do provisionamento serão depositados dentro da pasta) e salve o conteúdo do arquivo em GitHub segredos do repositório com nome para uso `.fx` `.fx/states/{YOUR_ENV_NAME}.userdata` [](https://docs.github.com/en/actions/reference/encrypted-secrets) `USERDATA_CONTENT` futuro.

### <a name="environment-variables"></a>Variáveis de ambiente

Etapas para criar variáveis de ambiente em GitHub::

1. Na página **Configurações** projeto, navegue até **Ambientes e** selecione **Novo ambiente**.
1. Insira um nome para seu ambiente. O nome de ambiente padrão fornecido no modelo é `test_environment` . Selecione **Configurar ambiente** para continuar.
1. Na próxima página, Selecione **Adicionar Segredo** para adicionar segredos para cada um dos itens listados na tabela abaixo.

|Nome|Descrição|
|---|---|
|AZURE_ACCOUNT_NAME|O nome da conta do Azure que é usado para provisionar recursos.|
|AZURE_ACCOUNT_PASSWORD|A senha da conta do Azure.|
|AZURE_SUBSCRIPTION_ID|Para identificar a assinatura na qual os recursos serão provisionados.|
|AZURE_TENANT_ID|Para identificar o locatário no qual a assinatura reside.|
|Microsoft 365_ACCOUNT_NAME|A Microsoft 365 para criar e publicar o Teams App.|
|Microsoft 365_ACCOUNT_PASSWORD|A senha da conta Microsoft 365.|
|Microsoft 365_TENANT_ID|Para identificar o locatário no qual o Teams App será criado/publicado. Esse valor é opcional, a menos que você tenha uma conta com vários locatários e queira usar outro locatário. Leia mais sobre [como encontrar sua ID Microsoft 365 locatário.](/azure/active-directory/fundamentals/active-directory-how-to-find-tenant)|

> [!NOTE]
> Consulte a opção [Configurar Microsoft 365/Credenciais do Azure](https://github.com/OfficeDev/teamsfx-cli-action/blob/main/README.md#configure-m365azure-credentials-as-github-secret) para garantir que você desabilitou a Autenticação Multifaional e Os Padrões de Segurança para as credenciais usadas no fluxo de trabalho.

## <a name="set-up-ci-or-cd-pipelines-with-azure-devops"></a>Configurar ci ou cd Pipelines com Azure DevOps

Você pode configurar pipelines automatizados em Azure DevOps e fazer uma referência nos scripts. Siga as etapas abaixo para começar:

* [CI Scripts](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-ci-template.sh)
* [CD Scripts](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-cd-template.sh)

### <a name="set-up-ci-pipeline"></a>Configurar pipeline ci

1. Adicione [scripts ci ao](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-ci-template.sh) seu repositório Azure DevOps e faça as personalizações necessárias à medida que você pode inferir dos comentários no arquivo de script.
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

As possíveis alterações que você pode fazer para o script ou a definição de fluxo de trabalho:

1. Altere como o fluxo de CI é disparado. Padrão para quando uma nova confirmação é empurrada para o `dev` branch.
1. Altere a maneira de instalar o nó e o npm.
1. Use o script de com build npm ou personalize a maneira como você cria no código de automação.
1. Use o script de teste npm que retorna zero para sucesso e/ou altere os comandos de teste.

### <a name="set-up-cd-pipeline"></a>Configurar pipeline de CD

1. Adicione [scripts de CD](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-cd-template.sh) ao repositório Azure DevOps e faça as personalizações necessárias à medida que você pode inferir dos comentários no arquivo de script.
1. Crie seu Azure DevOps Pipeline para CD, como você pode se referir [a este link](/azure/devops/pipelines/create-first-pipeline). A definição do Pipeline pode ser referenciada para a definição de exemplo a seguir para o Pipeline CI.
1. Adicione variáveis necessárias [por Definir variáveis](/azure/devops/pipelines/process/variables)e torná-las como segredos, se necessário.

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

- task: DownloadSecureFile@1
  name: userdata
  inputs:
    secureFile: 'staging.userdata'
- task: Bash@3
  inputs:
    targetType: 'inline'
    script: |
      mkdir -p .fx/states/
      cp $(userdata.secureFilePath) .fx/states/staging.userdata
  
- task: Bash@3
  env:
    AZURE_ACCOUNT_NAME: $(AZURE_ACCOUNT_NAME)
    AZURE_ACCOUNT_PASSWORD: $(AZURE_ACCOUNT_PASSWORD)
    AZURE_TENANT_ID: $(AZURE_TENANT_ID)
    Microsoft 365_ACCOUNT_NAME: $(Microsoft 365_ACCOUNT_NAME)
    Microsoft 365_ACCOUNT_PASSWORD: $(Microsoft 365_ACCOUNT_PASSWORD)
  inputs:
    filePath: './others-script-cd-template.sh'
```

As possíveis alterações que você pode fazer para o script ou a definição de fluxo de trabalho:

1. Como o fluxo de CD é disparado. Por padrão, isso acontece quando novas confirmações são feitas no **branch** principal.
1. Altere a maneira de instalar o nó e o npm.
1. Altere o nome do ambiente, por padrão, **sua preparação**.
1. Verifique se você tem um script de com build npm ou personalize a maneira como você cria no código de automação.
1. Verifique se você tem um script de teste npm que retorna zero para sucesso e/ou altere os comandos de teste.

> [!Note]
> A etapa de provisionamento não está incluída no modelo de CD, pois geralmente é executada apenas uma vez. Você pode executar o provisionamento dentro Teams Toolkit, a CLI do TeamsFx ou usar um fluxo de trabalho seperado. Lembre-se de se comprometer após o provisionamento (os resultados do provisionamento serão depositados dentro da pasta) e carregar em Azure DevOps arquivos seguros `.fx` `.fx/states/{YOUR_ENV_NAME}.userdata` para uso futuro. [](/azure/devops/pipelines/library/secure-files)

### <a name="environment-variables-for-azure-devops"></a>Variáveis de ambiente para Azure DevOps

Etapas para criar variáveis pipeline em Azure DevOps:

1. Na página Edição do Pipeline, selecione **Variáveis** na parte superior direita e selecione **Nova variável**.
1. Insira o par Nome/Valor para sua variável.
1. Alterne a caixa de seleção de **Manter esse valor em segredo,** se necessário.
1. Selecione **OK** para criar a variável.

|Nome|Descrição|
|---|---|
|AZURE_ACCOUNT_NAME|O nome da conta do Azure que é usado para provisionar recursos.|
|AZURE_ACCOUNT_PASSWORD|A senha da conta do Azure.|
|AZURE_SUBSCRIPTION_ID|Para identificar a assinatura na qual os recursos serão provisionados.|
|AZURE_TENANT_ID|Para identificar o locatário no qual a assinatura reside.|
|Microsoft 365_ACCOUNT_NAME|A Microsoft 365 para criar e publicar o Teams App.|
|Microsoft 365_ACCOUNT_PASSWORD|A senha da conta Microsoft 365.|
|Microsoft 365_TENANT_ID|Para identificar o locatário no qual o Teams App será criado/publicado. Esse valor é opcional, a menos que você tenha uma conta com vários locatários e queira usar outro locatário. Leia mais sobre [como encontrar sua ID Microsoft 365 locatário.](/azure/active-directory/fundamentals/active-directory-how-to-find-tenant)|

> [!NOTE]
> A etapa de provisionamento não está incluída no modelo de CD, pois geralmente é executada apenas uma vez. Você pode executar o provisionamento dentro Teams Toolkit, a CLI do TeamsFx ou usar um fluxo de trabalho seperado. Lembre-se de se comprometer após o provisionamento (os resultados do provisionamento serão depositados dentro da pasta) e salve o conteúdo do arquivo de credenciais do Jenkins para uso `.fx` `.fx/states/{YOUR_ENV_NAME}.userdata` futuro.

## <a name="ci-or-cd-pipeline-templates-in-jenkins"></a>Modelos de pipeline de CI ou CD no Jenkins

Para adicionar esses modelos ao repositório, você precisará das versões do [modelo jenkins-ci. Modelo de jenkinsfile](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/jenkins-ci-template.Jenkinsfile)  [e jenkins-cd. Jenkinsfile](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/jenkins-cd-template.Jenkinsfile) a ser localizado em seu repositório por filial.

Além disso, você precisa criar pipelines CI ou CD no Jenkins que apontem para o **Jenkinsfile específico** correspondentemente.

Siga as etapas para verificar como conectar o Jenkins a diferentes plataformas SCM:

1. [Jenkins com GitHub](https://www.jenkins.io/solutions/github/)
2. [Jenkins com Azure DevOps](https://www.dragonspears.com/blog/ci-cd-with-jenkins-and-azure-devops-services)
3. [Jenkins com GitLab](https://docs.gitlab.com/ee/integration/jenkins.html)
4. [Jenkins com Bitbucket](https://medium.com/ampersand-academy/integrate-bitbucket-jenkins-c6e51103d0fe)

### <a name="customize-ci-pipeline"></a>Personalizar pipeline CI

Há algumas alterações possíveis que você pode fazer para adaptar seu projeto:

1. Renomeie o arquivo de modelo para **Jenkinsfile** já que é uma prática comum e coloque-o sob o branch de destino, por exemplo, o **branch de dev.**
1. Altere como o fluxo de CI é disparado. Padrão é usar os gatilhos do **pollSCM** quando uma nova alteração é empurrada para o **branch de dev.**
1. Verifique se você tem um script de com build npm ou personalize a maneira como você cria no código de automação.
1. Verifique se você tem um script de teste npm que retorna zero para sucesso e/ou altere os comandos de teste.

### <a name="customize-cd-pipeline"></a>Personalizar pipeline de CD

Altere as etapas a seguir para personalizar o pipeline de CD:

1. Renomeie o arquivo de modelo para **Jenkinsfile** já que é uma prática comum e coloque-o sob o branch de destino, por exemplo, o **branch** principal.
1. Como o fluxo de CD é disparado. Padrão é usar os gatilhos do **pollSCM** quando uma nova alteração é empurrada para o **branch** principal.
1. Crie credenciais [de pipeline do](https://www.jenkins.io/doc/book/using/using-credentials/) Jenkins para manter as credenciais de logon do Azure/Microsoft 365. A tabela abaixo lista todas as credenciais que você precisa criar em Jenkins.
1. Altere os scripts de com build, se necessário.
1. Remova os scripts de teste se você não tiver testes.

> [!Note]
 A etapa de provisionamento não está incluída no modelo de CD, pois geralmente é executada apenas uma vez. Você pode executar o provisionamento em Teams Toolkit, no TeamsFx CLI ou usando um fluxo de trabalho separado. Lembre-se de se comprometer após o provisionamento (os resultados do provisionamento serão depositados dentro da pasta) e salve o conteúdo do arquivo de credenciais do Jenkins para uso `.fx` `.fx/states/{YOUR_ENV_NAME}.userdata` futuro.

### <a name="environment-variables-for-jenkins"></a>Variáveis de ambiente para o Jenkins

Siga [as credenciais de uso](https://www.jenkins.io/doc/book/using/using-credentials/) para criar credenciais no Jenkins.

|Nome|Descrição|
|---|---|
|AZURE_ACCOUNT_NAME|O nome da conta do Azure usado para provisionar recursos.|
|AZURE_ACCOUNT_PASSWORD|A senha da conta do Azure.|
|AZURE_SUBSCRIPTION_ID|Para identificar a assinatura na qual os recursos serão provisionados.|
|AZURE_TENANT_ID|Para identificar o locatário no qual a assinatura reside.|
|Microsoft 365_ACCOUNT_NAME|A conta do M3icrosoft 365 para criar e publicar o Teams App.|
|Microsoft 365_ACCOUNT_PASSWORD|A senha da conta Microsoft 365.|
|Microsoft 365_TENANT_ID|Para identificar o locatário no qual o Teams App será criado/publicado. Esse valor é opcional, a menos que você tenha uma conta com vários locatários e queira usar outro locatário. Leia mais sobre [como encontrar sua ID Microsoft 365 locatário.](/azure/active-directory/fundamentals/active-directory-how-to-find-tenant)|
> Observação: consulte a opção Configurar credenciais [Microsoft 365/Azure](https://github.com/OfficeDev/teamsfx-cli-action/blob/main/README.md#configure-m365azure-credentials-as-github-secret) para certificar-se de ter desabilitado a Autenticação Multifatetiva e os Padrões de Segurança para as credenciais usadas no pipeline.

## <a name="get-started-guide-for-other-platforms"></a>Guia de início para outras plataformas

Você pode seguir os scripts de bash de exemplo pré-definidos listados para criar e personalizar pipelines de CI ou CD em outras plataformas:

* [CI Scripts](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-ci-template.sh)
* [Scripts de CD](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-cd-template.sh) Os scripts são bastante simples e a maioria delas é CLI entre plataformas, portanto, é fácil transformá-los em outros tipos de script, por exemplo, PowerShell.

Os scripts são baseados em uma ferramenta de linha de comando [TeamsFx-CLI](https://www.npmjs.com/package/@microsoft/teamsfx-cli)entre plataformas. Você pode instalá-lo com `npm install -g @microsoft/teamsfx-cli` e seguir a [documentação](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md) para personalizar os scripts.

> [!Note]
> Para `@microsoft/teamsfx-cli` habilitar a execução no modo CI, ative `CI_ENABLED` por `export CI_ENABLED=true` . No modo CI, `@microsoft/teamsfx-cli` é amigável para CI ou CD.

Certifique-se de definir credenciais do Azure e M365 em suas variáveis de ambiente com segurança. Por exemplo, se você estiver usando GitHub como repositório de código-fonte, poderá usar os [Segredos do Github](https://docs.github.com/en/actions/reference/encrypted-secrets) para armazenar com segurança as variáveis do seu ambiente.

## <a name="publish-teams-app-using-teams-developer-portal"></a>Publicar Teams aplicativo usando Teams Portal do Desenvolvedor

Se houver alterações relacionadas Teams arquivo de manifesto do aplicativo, talvez você queira publicar o Teams aplicativo novamente para atualizar o manifesto.

Para publicar Teams aplicativo manualmente, você pode aproveitar o Portal do [Desenvolvedor para Teams](https://dev.teams.microsoft.com/home).

**Para publicar seu aplicativo**

1. Entre no [Portal do Desenvolvedor para Teams](https://dev.teams.microsoft.com) usando a conta correspondente.
2. Importe seu pacote de aplicativo em zip selecionando `App -> Import app -> Replace` .
3. Selecione o aplicativo de destino na lista de aplicativos e você irá para a página visão geral.
4. Publicar seu aplicativo selecionando `Publish -> Publish to your org`

### <a name="see-also"></a>Confira também

* [Início rápido para GitHub ações](https://docs.github.com/en/actions/quickstart#creating-your-first-workflow)
* [Criar sua primeira Azure DevOps Pipeline](/azure/devops/pipelines/create-first-pipeline)
* [Criar seu primeiro Pipeline do Jenkins](https://www.jenkins.io/doc/pipeline/tour/hello-world/)
