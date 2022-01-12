---
title: Usar Teams Toolkit para provisionar recursos de nuvem
author: MuyangAmigo
description: Provisione recursos de nuvem
ms.author: shenwe
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: e68596e9d109fcfa54708a76570874951fe326b2
ms.sourcegitcommit: 2d5bdda6c52693ed682bbd543b0aa66e1feb3392
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/12/2022
ms.locfileid: "61768612"
---
# <a name="use-teams-toolkit-to-provision-cloud-resources"></a>Usar Teams Toolkit para provisionar recursos de nuvem

O TeamsFx se integra ao Azure e Microsoft 365 nuvem, o que permite que você coloque seu aplicativo no Azure com um único comando. O TeamsFx se integra ao Gerenciador de Recursos do Azure que permite provisionar recursos do Azure, que seu aplicativo precisa para abordagem de código.  

## <a name="prerequisites"></a>Pré-requisitos

* Pré-requisitos da conta Para provisionar recursos de nuvem, você deve ter as seguintes contas:

    * Microsoft 365 conta com assinatura válida
    * Azure com assinatura válida Para obter mais informações, consulte como preparar contas para a [criação de Teams app](accounts.md).

* [Instale Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) versão v3.0.0+.

> [!TIP]
> Verifique se você Teams projeto de aplicativo aberto em código VS.

## <a name="provision-using-teams-toolkit"></a>Provisionamento usando Teams Toolkit

A provisionamento é executada com um único comando Teams Toolkit para Visual Studio Code ou CLI teamsFx da seguinte forma:

[Provisionar aplicativo baseado no Azure](/microsoftteams/platform/sbs-gs-javascript?tabs=vscode%2Cvsc%2Cviscode%2Cvcode&tutorial-step=8&branch)

## <a name="resource-creation"></a>Criação de recursos

Quando você aciona o comando provisionamento Teams Toolkit cli do TeamsFx ou do TeamsFx, você pode obter os seguintes recursos:

* AAD aplicativo em seu Microsoft 365 locatário
* Teams de aplicativos na plataforma Microsoft 365 do locatário Teams locatário
* Recursos do Azure em sua assinatura selecionada do Azure

Ao criar um novo projeto, você pode usar todos os recursos do Azure. O ARM define todos os recursos do Azure e ajuda a criar recursos necessários do Azure durante a provisionamento. Quando você [adiciona um novo recurso de recurso](./add-resource.md) a um projeto existente, o modelo ARM atualizado reflete a alteração mais recente.

> [!NOTE]
> Os serviços do Azure incorrem em custos em sua assinatura, para obter mais informações sobre estimativa de custo, consulte [a calculadora de preços](https://azure.microsoft.com/pricing/calculator/).

### <a name="resource-creation-for-teams-tab-application"></a>Criação de recursos para Teams aplicativo Tab

|Recurso|Objetivo|Descrição |
|----------|--------------------------------|-----|
| Armazenamento do Azure | Hospedar seu aplicativo de tabulação | Habilita o recurso de aplicativo Web estático para hospedar seu aplicativo de guia |
| Plano de serviço de aplicativo para auth simples | Hospedar o aplicativo Web do Simple Auth |Não aplicável |
| Aplicativo Web para auth simples | Hospedar servidor de auth simples para obter acesso a outros serviços em seu aplicativo de página única | Adiciona identidade atribuída ao usuário para acessar outros recursos do Azure |
| Identidade atribuída pelo usuário | Autenticar solicitações de serviço para serviço do Azure | Compartilhado entre recursos e recursos diferentes |

### <a name="resource-creation-for-teams-bot-or-messaging-extension-application"></a>Criação de recursos para Teams bot ou aplicativo de extensão de mensagens

|Recurso|Objetivo| Descrição |
|----------|--------------------------------|-----|
| Serviço de bot do Azure | Registra seu aplicativo como um bot com a estrutura de bot | Conecta o bot ao Teams |
| Plano de serviço de aplicativo para bot | Hospedar o aplicativo Web do bot |Não aplicável |
| Aplicativo Web para bot | Hospedar seu aplicativo bot | Adiciona identidade atribuída ao usuário para acessar outros recursos do Azure. <br /> Adiciona configurações de aplicativo exigidas pelo [SDK teamsFx](https://www.npmjs.com/package/@microsoft/teamsfx) |
| Identidade atribuída pelo usuário | Autenticar solicitações de serviço para serviço do Azure | Compartilhado entre recursos e recursos diferentes |

### <a name="resource-creation-for-azure-functions-in-the-project"></a>Criação de recursos para funções do Azure no projeto

|Recurso|Objetivo| Descrição|
|----------|--------------------------------|-----|
| Plano de serviço de aplicativo para aplicativo de função | Hospedar o aplicativo de função |Não aplicável |
| Aplicativo function | Hospedar suas APIs de funções do Azure | Adiciona identidade atribuída ao usuário para acessar outros recursos do Azure. <br /> Adiciona a regra de compartilhamento de recursos de origem cruzada (CORS) para permitir solicitações do aplicativo de tabulação <br /> Adiciona a configuração de autenticação que permite apenas solicitações de seu Teams app. <br /> Adiciona configurações de aplicativo exigidas pelo [SDK teamsFx](https://www.npmjs.com/package/@microsoft/teamsfx) |
| Armazenamento do Azure para aplicativo de função | Obrigatório para criar aplicativo de função |Não aplicável|
| Identidade atribuída pelo usuário | Autenticar solicitações de serviço para serviço do Azure | Compartilhado entre recursos e recursos diferentes |

### <a name="resource-creation-for-azure-sql-in-the-project"></a>Criação de recursos para o Azure SQL no projeto

|Recurso|Objetivo | Descrição |
|----------|--------------------------------|-----|
| Servidor SQL Azure | Hospedar a instância de banco de dados SQL do Azure | Permite que todos os serviços do Azure acessem o servidor |
| Banco de dados SQL Azure | Armazenar dados para seu aplicativo | Concede ao usuário a identidade atribuída, a permissão de leitura ou gravação para o banco de dados |
| Identidade atribuída pelo usuário | Autenticar solicitações de serviço para serviço do Azure | Compartilhado entre recursos e recursos diferentes |

### <a name="resource-creation-for-azure-api-management-in-the-project"></a>Criação de recursos para o Gerenciamento de API do Azure no projeto

|Recurso|Objetivo|
|----------|--------------------------------|
| Aplicativo do Active Directory do Azure para serviço de gerenciamento de API | Permite que as APIs de acesso da Plataforma do Microsoft Power gerenciadas pelo serviço de gerenciamento de API |
| Serviço de gerenciamento de API | Gerenciar suas APIs hospedadas no aplicativo de função |
| Produto de gerenciamento de API | Agrupar suas APIs, definir termos de uso e políticas de tempo de execução |
| Servidor OAuth de gerenciamento de API | Permite que o Microsoft Power Platform acesse suas APIs hospedadas no aplicativo de função |
| Identidade atribuída pelo usuário | Autenticar solicitações de serviço para serviço do Azure |

### <a name="resources-created-when-including-azure-key-vault-in-the-project"></a>Recursos criados ao incluir o Azure Key Vault no projeto

|Recursos|Finalidade desse recurso|
|----------|--------------------------------|
| Serviço de Cofre de Chaves do Azure | Gerenciar segredos (por exemplo, AAD do cliente de aplicativo) usados por outros Serviços do Azure |
| Identidade atribuída pelo usuário | Autenticar solicitações de serviço para serviço do Azure |

## <a name="customize-resource-provision"></a>Personalizar o provisionamento de recursos

Teams Toolkit permite que você use uma infraestrutura como abordagem de código para definir quais recursos do Azure você deseja provisionar e como deseja configurar. A ferramenta usa ARM para definir recursos do Azure. O ARM é um conjunto de arquivos bicep que define a infraestrutura e a configuração do seu projeto. Você pode personalizar os recursos do Azure modificando o ARM modelo. Para obter mais informações, consulte [bicep document](/azure/azure-resource-manager/bicep.md). 

A provisão ARM envolve a alteração dos seguintes conjuntos de arquivos, parâmetros e modelos:

* ARM de parâmetros ( `azure.parameters.{your_env_name}.json` ) localizados na `.fx/configs` pasta, para passar parâmetros para modelos.
* ARM de modelo localizados em `templates/azure` , esta pasta contém os seguintes arquivos:

| Arquivo | Função | Permitir personalização |
| --- | --- | --- |
| main.bicep | Fornecer ponto de entrada para provisionamento de recursos do Azure | Sim |
| provision.bicep | Criar e configurar recursos do Azure | Sim |
| config.bicep | Adicionar configurações necessárias do TeamsFx aos recursos do Azure | Sim |
| provision/xxx.bicep | Criar e configurar cada recurso do Azure consumido por `provision.bicep` | Sim |
| teamsfx/xxx.bicep | Adicionar configurações necessárias do TeamsFx a cada recurso do Azure consumido por `config.bicep`| Não |

> [!NOTE]
> Quando você adiciona recursos ou recursos ao seu projeto, `teamsfx/xxx.bicep` será regenerado, não é possível personalizar o mesmo. Para modificar os arquivos do bicep, você pode usar o Git para controlar suas alterações nos arquivos, o que ajuda você a não perder alterações ao adicionar `teamsfx/xxx.bicep` recursos ou recursos.

### <a name="customize-arm-parameters-and-templates"></a>Personalizar ARM parâmetros e modelos

Você pode personalizar os recursos do Azure personalizando os arquivos de parâmetros e personalização dos arquivos de bíceps.

#### <a name="customize-arm-template-parameter-files"></a>Personalizar ARM de parâmetro de modelo

O kit de ferramentas fornece um conjunto de parâmetros predefinidos para você personalizar os recursos do Azure. Os arquivos de parâmetro estão `.fx/configs/azure.parameters.{env}.json` localizados em e todos os parâmetros disponíveis são definidos na `provisionParameters` propriedade. É recomendável personalizar os arquivos de parâmetros se os parâmetros predefinidos satisfazem seu requisito.

A tabela a seguir fornece uma lista de parâmetros predefinidos disponíveis:

| Nome do parâmetro | Valor padrão | O que pode ser personalizado pelo parâmetro | Restrições de valor |
| --- | --- | --- | --- |
| resourceBaseName | Gerado automaticamente para cada ambiente | Nome padrão para todos os recursos | 2 a 20 letras minúsculas e números |
| simpleAuthServerFarmsName | ${resourceBaseName}simpleAuth | Nome do plano de serviço de aplicativo de auth simples | 1-40 alfanuméricos e hífens |
| simpleAuthWebAppName | ${resourceBaseName}simpleAuth | Nome do aplicativo Web de auth simples | 2 a 60 alfanuméricos e hífens <br /> Não é possível iniciar ou terminar com hífen |
| simpleAuthSku | F1 | SKU do plano de serviço de aplicativo de auth simples | Não aplicável |
| frontendHostingStorageName | Guia ${resourceBaseName} | Nome da conta de armazenamento de hospedagem de frontend | 3 a 24 letras minúsculas e números |
| frontendHostingStorageSku | Standard_LRS | SKU da conta de armazenamento de hospedagem front-end |[SKUs disponíveis](/azure/templates/microsoft.storage/storageaccounts?tabs=bicep&branch)|
| functionServerfarmsName | ${resourceBaseName}api | Nome do plano de serviço de aplicativos de função | 1-40 alfanuméricos e hífens |
| functionServerfarmsSku | Y1 | SKU do plano de serviço de aplicativos de função | Não aplicável|
| functionAppName | ${resourceBaseName}api | Nome do aplicativo de função | 2 a 60 alfanuméricos e hífens <br /> Não é possível iniciar ou terminar com hífen |
| functionStorageName | ${resourceBaseName}api | Nome da conta de armazenamento do aplicativo de função | 3 a 24 letras minúsculas e números |
| functionStorageSku | Standard_LRS | SKU da conta de armazenamento do aplicativo de função | [SKUs disponíveis](/azure/templates/microsoft.storage/storageaccounts?tabs=bicep&branch=pr-en-us-4713) |
| botServiceName | ${resourceBaseName} | Nome do serviço de bot do Azure | 2 a 64 alfanuméricos, sublinhados, pontos e hífens <br /> Iniciar com alfanumérico |
| botServiceSku | F0 | SKU do serviço de bot do Azure | [SKUs disponíveis](/azure/templates/microsoft.botservice/2021-05-01-preview/botservices?tabs=bicep&branch) |
| botDisplayName | ${resourceBaseName} | Nome de exibição do bot | 1 a 42 caracteres |
| botServerfarmsName | ${resourceBaseName}bot | Nome do plano de serviço de aplicativo do bot | 1-40 alfanuméricos e hífens |
| botWebAppName | ${resourceBaseName}bot | Nome do aplicativo Web do bot | 2 a 60 alfanuméricos e hífens <br /> Não é possível iniciar ou terminar com hífen |
| botWebAppSKU | F1 | SKU do Plano de Serviço de Aplicativo bot | Não aplicável |
| userAssignedIdentityName | ${resourceBaseName} | Nome da identidade atribuída pelo usuário | 3-128 alfanuméricos, hífens e sublinhados <br /> Iniciar com letra ou número |
| sqlServerName | ${resourceBaseName} | Nome do servidor SQL Azure | 1 a 63 letras minúsculas, números e hífens <br /> Não é possível iniciar ou terminar com hífen |
| sqlDatabaseName | ${resourceBaseName} | Nome do banco de dados SQL Azure | De 1 a 128 caracteres, não é possível usar <>*%&: \/ ? ou caracteres de controle <br /> Não é possível terminar com ponto ou espaço |
| sqlDatabaseSku | Básico | SKU do banco de dados SQL Azure | Não aplicável  |
| apimServiceName | ${resourceBaseName} | Nome do serviço APIM | 1 a 50 alfanuméricos e hífens <br /> Comece com letra e termine com alfanumérico |
| apimServiceSku | Consumo | SKU do serviço APIM | [SKUs disponíveis](/azure/templates/microsoft.apimanagement/service?tabs=bicep&branch) |
| apimProductName | ${resourceBaseName} | Nome do produto APIM | 1-80 alfanuméricos e hífens <br /> Comece com letra e termine com alfanumérico |
| apimOauthServerName | ${resourceBaseName} | Nome do servidor OAuth do APIM | 1-80 alfanuméricos e hífens <br /> Comece com letra e termine com alfanumérico |
| keyVaultSkuName | standard | Nome SKU do Serviço de Cofre de Chaves do Azure| |

Entretanto, os parâmetros a seguir estão disponíveis com valores preenchidos durante a provisionamento. O objetivo desses espaço reservados é garantir que possamos criar novos recursos para você em um novo ambiente. Os valores reais são resolvidos de `.fx/states/state.{env}.json` .

##### <a name="aad-application-related-parameters"></a>AAD parâmetros relacionados a aplicativos

| Nome do parâmetro | Porta-valores padrão | Significado do titular do local | Como personalizar |
| --- | --- | --- | --- |
| Microsoft 365 ClientId | {{state.fx-resource-aad-app-for-teams.clientId}} | A ID do cliente AAD aplicativo do seu aplicativo criada durante a provisão | [Personalizar o valor](#use-an-existing-aad-app-for-your-teams-app) |
| Microsoft 365 ClientSecret | {{state.fx-resource-aad-app-for-teams.clientSecret}} | O segredo do cliente AAD aplicativo criado durante a provisionamento | [Personalizar o valor](#use-an-existing-aad-app-for-your-teams-app)  |
| Microsoft 365 TenantId | {{state.fx-resource-aad-app-for-teams.tenantId}} | ID do locatário do aplicativo AAD aplicativo | [Personalizar o valor](#use-an-existing-aad-app-for-your-teams-app)  |
| Microsoft 365 OAuthAuthorityHost | {{state.fx-resource-aad-app-for-teams.oauthHost}} | Host de autoridade OAuth do aplicativo AAD aplicativo | [Personalizar o valor](#use-an-existing-aad-app-for-your-teams-app) |
| botAadAppClientId | {{state.fx-resource-bot.botId}} | ID do cliente de aplicativo AAD bot criada durante a provisionamento | [Personalizar o valor](#use-an-existing-aad-app-for-your-bot) |
| botAadAppClientSecret | {{state.fx-resource-bot.botPassword}} | O segredo do AAD de aplicativo criado durante a provisionamento | [Personalizar o valor](#use-an-existing-aad-app-for-your-bot) |
| apimClientId | {{state.fx-resource-apim.apimClientAADClientId}} | ID do cliente de aplicativo AAD APIM criada durante a provisionamento | Excluir o espaço reservado e preencher o valor real |
| apimClientSecret | {{state.fx-resource-apim.apimClientAADClientSecret}} | O segredo do cliente de aplicativo AAD APIM criado durante a provisionamento | Excluir o espaço reservado e preencher o valor real |

##### <a name="azure-resource-related-parameters"></a>Parâmetros relacionados a recursos do Azure

| Nome do parâmetro | Porta-valores padrão | Significado do titular do local | Como personalizar |
| --- | --- | --- | --- |
| azureSqlAdmin | {{state.fx-resource-azure-sql.admin}} | Azure SQL Server conta de administrador que você forneceu durante o provisionamento | Excluir o espaço reservado e preencher o valor real |
| azureSqlAdminPassword | {{state.fx-resource-azure-sql.adminPassword}} | Azure SQL Server senha de administrador que você forneceu durante o provisionamento | Excluir o espaço reservado e preencher o valor real |
| apimPublisherEmail | {{state.fx-resource-apim.publisherEmail}} | Email do editor da APIM, valor padrão é sua conta do Azure | Excluir o espaço reservado e preencher o valor real |
| apimPublisherName | {{state.fx-resource-apim.publisherName}} | Nome do editor da APIM, valor padrão é sua conta do Azure | Excluir o espaço reservado e preencher o valor real |

#### <a name="referencing-environment-variables-in-parameter-files"></a>Fazendo referência a variáveis de ambiente em arquivos de parâmetros

Se você não quiser codificar os valores em arquivos de parâmetro, por exemplo, quando o valor for um segredo. Os arquivos de parâmetros suportam fazer referência aos valores de variáveis de ambiente. Você pode usar sintaxe `{{$env.YOUR_ENV_VARIABLE_NAME}}` em valores de parâmetros para a ferramenta resolver a partir da variável de ambiente atual.

O exemplo a seguir lê o valor do `mySelfHostedDbConnectionString` parâmetro da variável de ambiente `DB_CONNECTION_STRING` :

```json
...
    "mySelfHostedDbConnectionString": "{{$env.DB_CONNECTION_STRING}}"
...
```

#### <a name="customize-arm-template-files"></a>Personalizar ARM de modelo

Se os modelos predefinidos não atenderem ao requisito do aplicativo, você poderá personalizar os modelos ARM em `templates/azure` pasta. Por exemplo, você pode personalizar o modelo ARM para criar alguns recursos adicionais do Azure para seu aplicativo. Você precisa ter conhecimento básico do idioma bicep, que é usado para ARM modelo. Você pode começar a usar o bicep na [documentação do bicep.](/azure/azure-resource-manager/bicep/?branch)

> [!NOTE]
> O ARM é compartilhado por todos os ambientes. Você pode usar [a implantação condicional](/azure/azure-resource-manager/bicep/conditional-resource-deployment?branch) se o comportamento de provisionamento varia entre ambientes.

Para garantir que a ferramenta TeamsFx funcione corretamente, certifique-se de personalizar ARM modelo, que atende ao seguinte requisito. Se você usar outra ferramenta para desenvolvimento posterior, poderá ignorar esses requisitos.

* Mantenha a estrutura da pasta e o nome do arquivo inalterado. A ferramenta pode acrescentar novo conteúdo a arquivos existentes quando você adiciona mais recursos ou recursos ao seu projeto.
* Mantenha o nome dos parâmetros gerados automaticamente, bem como seus nomes de propriedade inalterados. Os parâmetros gerados automaticamente podem ser usados quando você adiciona mais recursos ou recursos ao seu projeto.
* Mantenha a saída do modelo de ARM gerado automaticamente inalterada. Você pode adicionar saídas adicionais ao ARM modelo. A saída é e pode ser usada em outros recursos, como `.fx/states/state.{env}.json` implantar, validar arquivo de manifesto.

### <a name="customization-scenarios"></a>Cenários de personalização

Você pode personalizar os seguintes cenários:

#### <a name="use-an-existing-aad-app-for-your-teams-app"></a>Usar um aplicativo de AAD existente para seu Teams app

Você pode adicionar o seguinte trecho de configuração ao arquivo para usar um aplicativo AAD criado por você mesmo para `.fx/configs/config.{env}.json` seu Teams app. Para criar um AAD, consulte <https://aka.ms/teamsfx-existing-aad-doc> .

```json
"auth": {
    "clientId": "<your AAD app client id>",
    "clientSecret": "{{$env.ENV_NAME_THAT_STORES_YOUR_SECRET}}",
    "objectId": "<your AAD app object id>",
    "accessAsUserScopeId": "<id of the access_as_user scope>"
}
```

Depois de adicionar o trecho, adicione seu segredo à variável de ambiente relacionada para que a ferramenta possa resolver o segredo real durante a provisionamento.

> [!NOTE]
> Certifique-se de não compartilhar o mesmo AAD aplicativo em vários ambientes. Se você não tiver permissão para atualizar o aplicativo AAD, você poderá receber um aviso com instruções sobre como atualizar manualmente o aplicativo AAD. Siga as instruções para atualizar seu aplicativo AAD após a provisão.

#### <a name="use-an-existing-aad-app-for-your-bot"></a>Usar um aplicativo de AAD existente para seu bot

Você pode adicionar o seguinte trecho de configuração ao arquivo para usar um aplicativo `.fx/configs/config.{env}.json` AAD criado por você mesmo para seu bot:

```json
"bot": {
    "appId": "<your AAD app client id>",
    "appPassword": "{{$env.ENV_NAME_THAT_STORES_YOUR_SECRET}}"
}
```

Depois de adicionar o trecho anterior, adicione seu segredo à variável de ambiente relacionada para a ferramenta resolver o segredo real durante a provisão.

#### <a name="skip-adding-user-for-sql-database"></a>Ignorar a adição de usuário para SQL banco de dados

Se você tiver erro de permissão insuficiente quando a ferramenta tentar adicionar o usuário ao banco de dados SQL, você poderá adicionar o seguinte trecho de configuração ao arquivo para ignorar a adição SQL usuário de banco de `.fx/configs/config.{env}.json` dados:

```json
"skipAddingSqlUser": true
```

### <a name="specifying-the-name-of-function-app-instance"></a>Especificando o nome da instância do Aplicativo de Função

Você pode usar `contosoteamsappapi` para a instância do aplicativo de função em vez de usar o nome padrão.

> [!NOTE]
> Se você já tiver provisionado o ambiente, especificar o nome pode criar uma nova instância de aplicativo de função para você, em vez de renomear a instância criada anteriormente.

As etapas a seguir são:

1. Abra `.fx/configs/azure.parameters.{env}.json` para seu ambiente atual.
2. Adicione uma nova propriedade `functionAppName` ao valor do parâmetro `provisionParameters` .
3. Insira `contosoteamsappapi` como valor de `functionAppName`
4. O arquivo de parâmetro final é mostrado no trecho a seguir:

    ```json
    {
        "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentParameters.json#",
        "contentVersion": "1.0.0.0",
        "parameters": {
            "provisionParameters": {
            "value": {
                "functionAppName": "contosoteamsappapi"
                ...
                }
            }
        }
    }
    ```

### <a name="scenerio"></a>Scenerio 

**Para adicionar outro recurso ou armazenamento do Azure ao aplicativo**

Considere o cenário, você deseja adicionar o armazenamento do Azure ao back-end da função do Azure para armazenar dados blob. Não há fluxo automático para atualizar o modelo de bicep com suporte a armazenamento do Azure. No entanto, você pode editar o arquivo bicep e adicionar o recurso. As etapas são as seguintes:

1. Criar um projeto de guia.
2. Adicionar função ao projeto. Para obter mais informações, consulte [add resources](./add-resource.md).
3. Declare a nova conta de armazenamento no ARM modelo. Você pode declarar o recurso `templates/azure/provision/function.bicep` diretamente. Você pode declarar os recursos em outros lugares.

    `````````bicep
    var applicationStorageAccountName = 'myapp${uniqueString(resourceGroup().id)}'
    resource applicationStorageAccount 'Microsoft.Storage/storageAccounts@2021-06-01' = {
        name: applicationStorageAccountName
        location: resourceGroup().location
        kind: 'Storage'
        sku: {
            name: 'Standard_LRS'
        }
    }
    `````````

4. Atualizar as configurações do aplicativo de função do Azure com a cadeia de conexão de armazenamento do Azure em `templates/azure/provision/function.bicep` . Adicione o seguinte trecho à `functionApp` matriz do `appSettings` recurso:

    ``````````````````bicep
    {
        name: 'MyAppStorageAccountConnectionString'
        value: 'DefaultEndpointsProtocol=https;AccountName=${applicationStorageAccount.name};AccountKey=${listKeys(applicationStorageAccount.id, '2021-06-01').keys[0].value}'
    }
    ```````````````````

5. Você pode atualizar sua função com as vinculações de saída de armazenamento do Azure.

## <a name="faq"></a>Perguntas frequentes

<br>

<details>

<summary><b>Como solucionar problemas?</b></summary>

Se você receber erros com Teams Toolkit no Visual Studio Code, você  poderá selecionar Obter Ajuda na notificação de erro para navegar até o documento relacionado. Se você estiver usando a CLI do TeamsFx, haverá um hiperlink no final da mensagem de erro que aponta para o doc de ajuda. Você também pode exibir o [documento de ajuda de provisionamento](https://aka.ms/teamsfx-arm-help) diretamente.

<br>

</details>

<details>

<summary><b>Como posso alternar para outra assinatura do Azure durante o provisionamento?</b></summary>

1. Alternar assinatura na conta atual ou fazer logon e selecionar uma nova assinatura.
2. Se você já tiver provisionado o ambiente atual, precisará criar um novo ambiente e executar o provisionamento porque ARM não dá suporte à movimentação de recursos.
3. Se você não provisionou o ambiente atual, pode disparar a provisão diretamente.

<br>

</details>

<details>

<summary><b>Como posso alterar o grupo de recursos durante o provisionamento?</b></summary>

Antes do provisionamento, a ferramenta perguntará se você deseja criar um novo grupo de recursos ou usar um existente. Você pode fornecer um novo nome de grupo de recursos ou escolher um existente nesta etapa.

<br>

</details>

<details>

<summary><b>Como posso provisionar um aplicativo baseado no SharePoint?</b></summary>

Você pode seguir [o provisionamento SharePoint aplicativo baseado em .](/microsoftteams/platform/sbs-gs-spfx?tabs=vscode%2Cviscode&tutorial-step=4&branch)

> [!NOTE]
> Atualmente, a criação de um aplicativo Teams com a estrutura do sharepoint com Teams Toolkit não tem integração direta com o Azure, o conteúdo no documento não se aplica SPFx aplicativos baseados em SPFx.


<br>

</details>

## <a name="see-also"></a>Confira também

* [Implantar Teams aplicativo na nuvem](deploy.md)
* [Gerenciar vários ambientes](TeamsFx-multi-env.md)
* [Colaborar com outros desenvolvedores no Teams projeto](TeamsFx-collaboration.md)
