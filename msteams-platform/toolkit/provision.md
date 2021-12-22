---
title: Usar Teams Toolkit para provisionar recursos de nuvem
author: MuyangAmigo
description: Provisione recursos de nuvem
ms.author: shenwe
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: c8899131876533fdd64913fb6790cff9f258e8f5
ms.sourcegitcommit: aede47694894d281f6b725083bc0b46ab0e4846d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2021
ms.locfileid: "61591782"
---
# <a name="use-teams-toolkit-to-provision-cloud-resources"></a>Usar Teams Toolkit para provisionar recursos de nuvem

O TeamsFx fornece integração perfeita com o Azure e Microsoft 365 nuvem que permite que você coloque seu aplicativo no Azure com um único comando. O TeamsFx se integra ao Gerenciador de Recursos do Azure que permite provisionar declarativamente os recursos do Azure que seu aplicativo precisa usando a infraestrutura como abordagem de código.  

## <a name="prerequisites"></a>Pré-requisitos

* Pré-requisitos da conta

    Para provisionar recursos de nuvem, você deve ter as seguintes contas com permissões adequadas. Para obter mais informações, [consulte prepare accounts to build Teams app](accounts.md).
    * Microsoft 365
    * Azure com assinatura válida

* [Instale Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) versão v3.0.0+.

> [!TIP]
> Você já deve ter um projeto Teams aplicativo aberto em código VS.

## <a name="provision-using-teams-toolkit"></a>Provisionamento usando Teams Toolkit

A provisionamento é executada com um único comando Teams Toolkit para Visual Studio Code ou CLI teamsFx da seguinte forma:

[Provisionar aplicativo baseado no Azure](/microsoftteams/platform/sbs-gs-javascript?tabs=vscode%2Cvsc%2Cviscode%2Cvcode&tutorial-step=8&branch)

## <a name="resource-creation"></a>Criação de recursos

Quando você aciona o comando provisionamento Teams Toolkit cli do TeamsFx ou do TeamsFx, você pode obter os seguintes recursos:

* AAD aplicativo em seu Microsoft 365 locatário
* Teams de aplicativos na plataforma Microsoft 365 do locatário Teams locatário
* Recursos do Azure em sua assinatura selecionada do Azure

Ao criar um novo projeto, você obterá todos os recursos do Azure a serem criados. O modelo ARM gerado define todos os recursos do Azure e ajuda a criar recursos necessários do Azure durante a provisionamento. Quando você [adiciona novo recurso/recurso](./add-resource.md) a um projeto existente, o modelo de ARM atualizado reflete a alteração mais recente.

> [!NOTE]
> Os serviços do Azure incorrem em custos em sua assinatura, você pode consultar a calculadora [de preços](https://azure.microsoft.com/pricing/calculator/) para entender uma estimativa.

### <a name="resource-creation-for-teams-tab-application"></a>Criação de recursos para Teams aplicativo Tab

|Recursos|Finalidade desse recurso| Notas |
|----------|--------------------------------|-----|
| Armazenamento do Microsoft Azure | Hospedar seu aplicativo de tabulação | Habilita o recurso de aplicativo Web estático para hospedar seu aplicativo de guia |
| Plano de Serviço de Aplicativo para Auth Simples | Hospedar o aplicativo Web do Simple Auth | |
| Web App para Auth Simples | Host simple auth server that helps you gain access to other services in your single page application | Adiciona identidade atribuída ao usuário para facilitar o acesso a outros recursos do Azure |
| Identidade atribuída pelo usuário | Autenticar solicitações de serviço para serviço do Azure | Compartilhado entre recursos e recursos diferentes |

### <a name="resources-created-for-teams-bot-or-messaging-extension-application"></a>Recursos criados para Teams bot ou aplicativo de extensão de mensagens

|Recursos|Finalidade desse recurso| Notas |
|----------|--------------------------------|-----|
| Serviço bot do Azure | Registra seu aplicativo como um bot com a Estrutura de Bots | Conecta o bot ao Teams |
| Plano de Serviço de Aplicativo para Bot | Hospedar o aplicativo Web do Bot | |
| Web App para Bot | Hospedar seu aplicativo bot | Adiciona identidade atribuída ao usuário para facilitar o acesso a outros recursos do Azure. <br /> Adiciona configurações de aplicativo exigidas pelo [SDK teamsFx](https://www.npmjs.com/package/@microsoft/teamsfx) |
| Identidade atribuída pelo usuário | Autenticar solicitações de serviço para serviço do Azure | Compartilhado entre recursos e recursos diferentes |

### <a name="resources-created-when-including-azure-functions-in-the-project"></a>Recursos criados ao incluir funções do Azure no projeto

|Recursos|Finalidade desse recurso| Notas |
|----------|--------------------------------|-----|
| Plano de Serviço de Aplicativo para Aplicativo de Função | Hospedar o Aplicativo de Função | |
| Aplicativo function | Hospedar suas APIs de Funções do Azure | Adiciona identidade atribuída ao usuário para facilitar o acesso a outros recursos do Azure. <br /> Adiciona a regra CORS para permitir solicitações do seu aplicativo de guia <br /> Adiciona a configuração de autenticação que permite apenas solicitações de seu Teams app. <br /> Adiciona configurações de aplicativo exigidas pelo [SDK teamsFx](https://www.npmjs.com/package/@microsoft/teamsfx) |
| Azure Armazenamento aplicativo de função | Obrigatório ao criar o Aplicativo de Função | |
| Identidade atribuída pelo usuário | Autenticar solicitações de serviço para serviço do Azure | Compartilhado entre recursos e recursos diferentes |

### <a name="resources-created-when-including-azure-sql-in-the-project"></a>Recursos criados ao incluir o Azure SQL no projeto

|Recursos|Finalidade desse recurso| Notas |
|----------|--------------------------------|-----|
| Azure SQL Server | Hospedar a Banco de Dados SQL do Azure de usuário | Permite que todos os serviços do Azure acessem o servidor |
| Banco de Dados SQL Azure | Armazenar dados para seu aplicativo | Concede ao usuário permissão de leitura/gravação atribuída ao banco de dados |
| Identidade atribuída pelo usuário | Autenticar solicitações de serviço para serviço do Azure | Compartilhado entre recursos e recursos diferentes |

### <a name="resources-created-when-including-azure-api-management-in-the-project"></a>Recursos criados ao incluir o Gerenciamento de API do Azure no projeto

|Recursos|Finalidade desse recurso|
|----------|--------------------------------|
| Azure Active Directory aplicativo para serviço de Gerenciamento de API | Permite que as APIs de acesso da Plataforma do Microsoft Power gerenciadas pelo serviço de Gerenciamento de API |
| Serviço de Gerenciamento de API | Gerenciar suas APIs hospedadas no Aplicativo de Função |
| Produto de Gerenciamento de API | Agrupar suas APIs, definir termos de uso e políticas de tempo de execução |
| Servidor OAuth de Gerenciamento de API | Permite que o Microsoft Power Platform acesse suas APIs hospedadas no Aplicativo de Função |
| Identidade atribuída pelo usuário | Autenticar solicitações de serviço para serviço do Azure |

## <a name="customize-resource-provision"></a>Personalizar o provisionamento de recursos

Teams Toolkit permite que você use uma infraestrutura como abordagem de código para definir quais recursos do Azure você deseja provisionar e como deseja configurá-los. A ferramenta usa um ARM para definir recursos do Azure. O ARM é um conjunto de arquivos bicep que define a infraestrutura e a configuração do seu projeto. Você pode personalizar os recursos do Azure criados modificando o ARM modelo. Para obter mais informações, consulte [bicep document](/azure/azure-resource-manager/bicep.md). O provisionamento com ARM envolve a alteração de dois conjuntos de arquivos, parâmetros e modelos:

* ARM arquivos de parâmetros ( `azure.parameters.{your_env_name}.json` ) estão localizados na `.fx/configs` pasta, para passar parâmetros para modelos.
* ARM de modelo localizados em `templates/azure` , esta pasta contém os seguintes arquivos:

| File | O que ele faz | Permitir personalização |
| --- | --- | --- |
| main.bicep | Fornecer ponto de entrada para provisionamento de recursos do Azure | Sim |
| provision.bicep | Criar e config recursos do Azure | Sim |
| config.bicep | Adicionar configurações necessárias do TeamsFx aos recursos do Azure | Sim |
| provision/xxx.bicep | criar e config cada recurso do Azure consumido por `provision.bicep` | Sim |
| teamsfx/xxx.bicep | Adicionar configurações necessárias do TeamsFx a cada recurso do Azure consumido por `config.bicep`| Não |

> [!NOTE]
> quando você adicionar recursos ou recursos ao seu projeto, `teamsfx/xxx.bicep` será regenerado. É por isso que ele é marcado como não personalizável. Se você realmente tiver requisitos para modificar esses arquivos do bicep, recomendamos usar o Git para controlar suas alterações nos arquivos para que você não perca suas alterações ao adicionar recursos `teamsfx/xxx.bicep` ou recursos.

### <a name="customize-arm-parameters-and-templates"></a>Personalizar ARM parâmetros e modelos

Você pode personalizar os recursos do Azure personalizando os arquivos de parâmetros e personalização dos arquivos de bíceps.

#### <a name="customize-arm-template-parameter-files"></a>Personalizar ARM de parâmetro de modelo

O kit de ferramentas fornece um conjunto de parâmetros predefinidos para você personalizar os recursos do Azure. Os arquivos de parâmetro estão `.fx/configs/azure.parameters.{env}.json` localizados em e todos os parâmetros disponíveis são definidos na `provisionParameters` propriedade. É preferível personalizar os arquivos de parâmetros se os parâmetros predefinidos satisfazem seu requisito.

Aqui está uma lista de parâmetros predefinidos disponíveis:

| Nome do parâmetro | Valor padrão | O que pode ser personalizado pelo parâmetro | Restrições de valor |
| --- | --- | --- | --- |
| resourceBaseName | Gerado automaticamente para cada ambiente | Nome padrão para todos os recursos | 2 a 20 letras minúsculas e números |
| simpleAuthServerFarmsName | ${resourceBaseName}simpleAuth | Nome do Plano de Serviço de Aplicativo Simples de Auth | 1-40 alfanuméricos e hífens |
| simpleAuthWebAppName | ${resourceBaseName}simpleAuth | Nome do Aplicativo Web de Auth Simples | 2 a 60 alfanuméricos e hífens <br /> Não é possível iniciar ou terminar com hífen |
| simpleAuthSku | F1 | SKU do Plano de Serviço de Aplicativo Simples de Auth |  |
| frontendHostingStorageName | Guia ${resourceBaseName} | Nome do Frontend Hosting Armazenamento Account | 3 a 24 letras minúsculas e números |
| frontendHostingStorageSku | Standard_LRS | SKU do Frontend Hosting Armazenamento Account | Consulte esta [página para](/azure/templates/microsoft.storage/storageaccounts?tabs=bicep&branch) SKUs disponíveis |
| functionServerfarmsName | ${resourceBaseName}api | Nome do Plano de Serviço de Aplicativo do Aplicativo de Função | 1-40 alfanuméricos e hífens |
| functionServerfarmsSku | Y1 | SKU do Plano de Serviço de Aplicativo do FUnction App |
| functionAppName | ${resourceBaseName}api | Nome do Aplicativo de Função | 2 a 60 alfanuméricos e hífens <br /> Não é possível iniciar ou terminar com hífen |
| functionStorageName | ${resourceBaseName}api | Nome da conta de Armazenamento do Aplicativo de Função | 3 a 24 letras minúsculas e números |
| functionStorageSku | Standard_LRS | SKU da conta de Armazenamento do Aplicativo de Função | Consulte esta [página para](/azure/templates/microsoft.storage/storageaccounts?tabs=bicep&branch=pr-en-us-4713)SKUs disponíveis |
| botServiceName | ${resourceBaseName} | Nome do serviço bot do Azure | 2 a 64 alfanuméricos, sublinhados, pontos e hífens <br /> Iniciar com alfanumérico |
| botServiceSku | F0 | SKU do serviço Azure Bot | Consulte esta [página para](/azure/templates/microsoft.botservice/2021-05-01-preview/botservices?tabs=bicep&branch) SKUs disponíveis |
| botDisplayName | ${resourceBaseName} | Nome de exibição do bot | 1 a 42 caracteres |
| botServerfarmsName | ${resourceBaseName}bot | Nome do Plano de Serviço de Aplicativo do Bot | 1-40 alfanuméricos e hífens |
| botWebAppName | ${resourceBaseName}bot | Nome do Aplicativo Web do Bot | 2 a 60 alfanuméricos e hífens <br /> Não é possível iniciar ou terminar com hífen |
| botWebAppSKU | F1 | SKU do Plano de Serviço de Aplicativo bot |  |
| userAssignedIdentityName | ${resourceBaseName} | Nome da identidade atribuída pelo usuário | 3-128 alfanuméricos, hífens e sublinhados <br /> Iniciar com letra ou número |
| sqlServerName | ${resourceBaseName} | Nome do Azure SQL Server | 1 a 63 letras minúsculas, números e hífens <br /> Não é possível iniciar ou terminar com hífen |
| sqlDatabaseName | ${resourceBaseName} | Nome da Banco de Dados SQL do Azure | De 1 a 128 caracteres, não é possível usar <>*%&: \/ ? ou caracteres de controle <br /> Não é possível terminar com ponto ou espaço |
| sqlDatabaseSku | Básico | SKU de Banco de Dados SQL do Azure |  |
| apimServiceName | ${resourceBaseName} | Nome do Serviço APIM | 1 a 50 alfanuméricos e hífens <br /> Comece com letra e termine com alfanumérico |
| apimServiceSku | Consumo | SKU do Serviço APIM | Consulte esta [página para](/azure/templates/microsoft.apimanagement/service?tabs=bicep&branch)SKUs disponíveis |
| apimProductName | ${resourceBaseName} | Nome do produto APIM | 1-80 alfanuméricos e hífens <br /> Comece com letra e termine com alfanumérico |
| apimOauthServerName | ${resourceBaseName} | Nome do APIM OAuth Server | 1-80 alfanuméricos e hífens <br /> Comece com letra e termine com alfanumérico |

Entretanto, os parâmetros a seguir estão disponíveis com valores preenchidos durante a provisionamento. O objetivo desses espaço reservados é garantir que possamos criar novos recursos para você quando você criou um novo ambiente. Os valores reais são resolvidos de `.fx/states/state.{env}.json` .

##### <a name="aad-application-related-parameters"></a>AAD parâmetros relacionados a aplicativos

| Nome do parâmetro | Porta-valores padrão | Significado do titular do local | Como personalizar |
| --- | --- | --- | --- |
| Microsoft 365 ClientId | {{state.fx-resource-aad-app-for-teams.clientId}} | A ID do cliente AAD aplicativo do seu aplicativo criada durante a provisão | Consulte [esta seção](#use-an-existing-aad-app-for-your-teams-app) para personalizar o valor |
| Microsoft 365 ClientSecret | {{state.fx-resource-aad-app-for-teams.clientSecret}} | O segredo do cliente AAD aplicativo criado durante a provisionamento | Consulte [esta seção](#use-an-existing-aad-app-for-your-teams-app) para personalizar o valor |
| Microsoft 365TenantId | {{state.fx-resource-aad-app-for-teams.tenantId}} | ID do locatário do aplicativo AAD aplicativo | Consulte [esta seção](#use-an-existing-aad-app-for-your-teams-app) para personalizar o valor |
| Microsoft 365 OauthAuthorityHost | {{state.fx-resource-aad-app-for-teams.oauthHost}} | Host de autoridade OAuth do aplicativo AAD aplicativo | Consulte [esta seção](#use-an-existing-aad-app-for-your-teams-app) para personalizar o valor |
| botAadAppClientId | {{state.fx-resource-bot.botId}} | ID do cliente de aplicativo AAD bot criada durante a provisionamento | Consulte [esta seção](#use-an-existing-aad-app-for-your-bot) para personalizar o valor |
| botAadAppClientSecret | {{state.fx-resource-bot.botPassword}} | O segredo do AAD de aplicativo criado durante a provisionamento | Consulte [esta seção](#use-an-existing-aad-app-for-your-bot) para personalizar o valor |
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

Algumas vezes, talvez você não queira codificar os valores nos arquivos de parâmetros. Por exemplo, quando o valor é um segredo. Os arquivos de parâmetros suportam fazer referência aos valores de variáveis de ambiente. Você pode usar sintaxe em valores de parâmetro para dizer à ferramenta `{{$env.YOUR_ENV_VARIABLE_NAME}}` que o valor precisa ser resolvido a partir da variável de ambiente atual.

O exemplo a seguir lerá o valor do `mySelfHostedDbConnectionString` parâmetro da variável de ambiente `DB_CONNECTION_STRING` :

```json
...
    "mySelfHostedDbConnectionString": "{{$env.DB_CONNECTION_STRING}}"
...
```

#### <a name="customize-arm-template-files"></a>Personalizar ARM de modelo

Se os modelos predefinidos não atenderem ao seu requisito de aplicativo, você poderá personalizar os modelos ARM em `templates/azure` pasta. Por exemplo, você pode personalizar o modelo ARM para criar alguns recursos adicionais do Azure para seu aplicativo. Este é um cenário avançado e exige que você tenha conhecimento básico do idioma do bicep que é usado para ARM modelo. Você pode começar a usar o bicep na [documentação do bicep.](/azure/azure-resource-manager/bicep/?branch)
> [!NOTE]
> O ARM é compartilhado por todos os ambientes. Você pode usar [a implantação condicional](/azure/azure-resource-manager/bicep/conditional-resource-deployment?branch) se o comportamento de provisionamento for vários entre ambientes.

Para garantir que as funções de ferramenta teamsFx funcionem corretamente, verifique se o modelo de ARM personalizado atende ao requisito a seguir. Se você usar outras ferramentas para desenvolvimento posterior, poderá ignorar esses requisitos.

* Mantenha a estrutura da pasta e o nome do arquivo inalterado. A ferramenta pode acrescentar novo conteúdo a arquivos existentes quando você adiciona mais recursos/recursos ao seu projeto.
* Mantenha o nome dos parâmetros gerados automaticamente, bem como seus nomes de propriedade inalterados. Os parâmetros gerados automaticamente podem ser usados quando você adiciona mais recursos/recursos ao seu projeto.
* Mantenha a saída do modelo de ARM gerado automaticamente inalterada. Você pode adicionar saídas adicionais ao ARM modelo. A saída será persistente e usada em outros recursos, como `.fx/states/state.{env}.json` implantar, validar arquivo de manifesto, etc.

### <a name="customization-scenarios"></a>Cenários de personalização

Esses são alguns cenários comuns que você pode personalizar o comportamento de provisionamento.

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

Depois de adicionado trecho acima, adicione seu segredo à variável de ambiente relacionada para que a ferramenta possa resolver o segredo real durante a provisionação.

> [!NOTE]
> Você não deve compartilhar um aplicativo AAD em vários ambientes. Se você não tiver permissão para atualizar o aplicativo AAD, receberá um aviso com instruções sobre como atualizar manualmente o AAD app. Siga as instruções para atualizar seu aplicativo AAD após o provisionamento.

#### <a name="use-an-existing-aad-app-for-your-bot"></a>Usar um aplicativo de AAD existente para seu bot

Você pode adicionar o seguinte trecho de configuração ao arquivo para usar um aplicativo `.fx/configs/config.{env}.json` AAD criado por você mesmo para seu bot.

```json
"bot": {
    "appId": "<your AAD app client id>",
    "appPassword": "{{$env.ENV_NAME_THAT_STORES_YOUR_SECRET}}"
}
```

Depois de adicionado trecho acima, adicione seu segredo à variável de ambiente relacionada para que a ferramenta possa resolver o segredo real durante a provisionação.

> [!NOTE]
> Você não deve compartilhar um aplicativo AAD em vários ambientes.

#### <a name="skip-adding-user-for-sql-database"></a>Ignorar a adição de usuário para SQL banco de dados

Às vezes, você pode obter erro de permissão insuficiente quando a ferramenta tenta adicionar o usuário SQL banco de dados. Você pode adicionar o seguinte trecho de configuração ao `.fx/configs/config.{env}.json` arquivo para ignorar a adição SQL usuário do banco de dados.

```json
"skipAddingSqlUser": true
```

### <a name="specifying-the-name-of-function-app-instance"></a>Especificando o nome da instância do Aplicativo de Função

Este exemplo, especificarei outro nome para a instância do Aplicativo de Função `contosoteamsappapi` em vez de usar o nome padrão.

> [!NOTE]
> Se você já provisionou o ambiente, especificar o nome criará uma nova instância do Aplicativo de Função para você, em vez de renomear a instância criada anteriormente.

As etapas a seguir são:

1. Abra `.fx/configs/azure.parameters.{env}.json` para seu ambiente atual.
2. Adicione uma nova propriedade `functionAppName` ao valor do parâmetro `provisionParameters` .
3. Preencha "contosoteamsappapi" como valor de `functionAppName`
4. O arquivo de parâmetro final é mostrado da seguinte forma:

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

**Para adicionar outro recurso do Azure (armazenamento do Azure) ao aplicativo**

Considere o cenário, você deseja adicionar o Azure Armazenamento seu back-end da Função do Azure para armazenar alguns dados blob. Não há fluxo automático para atualizar o modelo de bicep com o suporte Armazenamento Azure. No entanto, você pode editar o arquivo bicep e adicionar o recurso. As etapas são as seguintes:

1. Criar um projeto de guia
2. Adicione uma função ao projeto. Você pode visitar [Adicionar Recursos](./add-resource.md) para saber mais sobre como adicionar recursos.
3. Declare o novo Armazenamento Conta no ARM modelo. Para simplificar, declararemos o recurso `templates/azure/provision/function.bicep` diretamente. Você pode declarar os recursos em outros lugares.

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

4. Atualize o aplicativo de função do Azure Configurações com a cadeia de Armazenamento de conexão do Azure em , que é o `templates/azure/provision/function.bicep` mesmo arquivo na etapa 3. Adicione o trecho a seguir `functionApp` à matriz do `appSettings` recurso.

    ``````````````````bicep
    {
        name: 'MyAppStorageAccountConnectionString'
        value: 'DefaultEndpointsProtocol=https;AccountName=${applicationStorageAccount.name};AccountKey=${listKeys(applicationStorageAccount.id, '2021-06-01').keys[0].value}'
    }
    ```````````````````

5. Agora, você pode atualizar sua função com as Armazenamento de saída do Azure.

## <a name="faq"></a>Perguntas frequentes

<br>

<details>

<summary><b>Como solucionar problemas?</b></summary>

Se você encontrou erros com Teams Toolkit no Visual Studio Code, clique no botão na notificação de erro para navegar até o doc `Get Help` de ajuda relacionado. Se você estiver usando a CLI do TeamsFx, haverá um hiper link no final da mensagem de erro que aponta para o doc de ajuda. Você também pode exibir o [documento de ajuda de provisionamento](https://aka.ms/teamsfx-arm-help) diretamente.

<br>

</details>

<details>

<summary><b>Como posso alternar para outra assinatura do Azure durante o provisionamento?</b></summary>

1. Alternar assinatura na conta atual ou fazer logon e selecionar uma nova assinatura.
2. Se você já provisionou o ambiente atual, precisará criar um novo ambiente e executar o provisionamento porque ARM não dá suporte à movimentação de recursos.
3. Se você não provisionou o ambiente atual, poderá acionar o provisionamento diretamente.

<br>

</details>

<details>

<summary><b>Como posso alterar o grupo de recursos durante o provisionamento?</b></summary>

Antes do provisionamento, a ferramenta perguntará se você deseja criar um novo grupo de recursos ou usar um existente. Você pode fornecer um novo nome de grupo de recursos ou escolher um existente nesta etapa.

<br>

</details>

<details>

<summary><b>Como posso provisionar SharePoint aplicativo baseado em SharePoint?</b></summary>

Você pode seguir [Provisionar SharePoint aplicativo baseado em SharePoint](/microsoftteams/platform/sbs-gs-spfx?tabs=vscode%2Cviscode&tutorial-step=4&branch) aplicativo baseado em provisionamento.

> [!NOTE]
> Atualmente, a criação do Teams App com Estrutura do SharePoint usando Teams Toolkit não tem integração direta com o Azure, o conteúdo deste documento não se aplica a aplicativos baseados SPFx.


<br>

</details>

## <a name="see-also"></a>Confira também

> [!div class="nextstepaction"]
> [Implantar Teams aplicativo na nuvem](deploy.md)

> [!div class="nextstepaction"]
> [Gerenciar vários ambientes](TeamsFx-multi-env.md)

> [!div class="nextstepaction"]
> [Colaborar com outros desenvolvedores no Teams projeto](TeamsFx-collaboration.md)
