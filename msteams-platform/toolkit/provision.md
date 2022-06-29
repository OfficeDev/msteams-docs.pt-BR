---
title: Usar o Kit de Ferramentas do Teams para provisionar recursos de nuvem
author: MuyangAmigo
description: Neste módulo, saiba como provisionar recursos de nuvem usando o Kit de Ferramentas do Teams, criar recursos e personalizar o provisionamento de recursos
ms.author: shenwe
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 7d95c5310147f9f974802d007a951d80a12acbe0
ms.sourcegitcommit: ffc57e128f0ae21ad2144ced93db7c78a5ae25c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66503365"
---
# <a name="provision-cloud-resources-using-teams-toolkit"></a>Provisionar recursos de nuvem usando o Kit de Ferramentas do Teams

O TeamsFx integra-se ao Azure e à nuvem do Microsoft 365, o que permite que você coloque seu aplicativo no Azure com um único comando. O TeamsFx integra-se ao Azure Resource Manager que permite provisionar recursos do Azure dos quais seu aplicativo precisa para a abordagem de código.

## <a name="prerequisites"></a>Pré-requisitos

* Pré-requisitos da conta Para provisionar recursos de nuvem, você deve ter as seguintes contas:

  * Conta do Microsoft 365 com assinatura válida.
  * Azure com assinatura válida.
  Para obter mais informações, [confira como preparar contas para a criação de aplicativos do Teams](accounts.md).

* [Instalar o Kit de Ferramentas do Teams](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) versão v3.0.0+.

> [!TIP]
> Certifique-se de ter o projeto do aplicativo Teams aberto no VS code.

## <a name="provision-using-teams-toolkit"></a>Provisionar usando o Kit de Ferramentas do Teams

O provisionamento é executado com um único comando no Kit de Ferramentas do Teams para Visual Studio Code ou a CLI do TeamsFx da seguinte maneira:

[Provisionar aplicativo baseado no Azure](/microsoftteams/platform/sbs-gs-javascript?tabs=vscode%2Cvsc%2Cviscode%2Cvcode&tutorial-step=8)

## <a name="resource-creation"></a>Criação de recursos

Ao disparar o comando provisionar no Kit de Ferramentas do Teams ou na CLI do TeamsFx, é possível obter os seguintes recursos:

* Microsoft Azure Active Directory (Azure AD) em seu locatário do Microsoft 365.
* Registro de aplicativo do Teams na plataforma do Teams do locatário do Microsoft 365.
* Recursos do Azure em sua assinatura do Azure selecionada.

Ao criar um novo projeto, é possível usar todos os recursos do Azure. O modelo do ARM define todos os recursos do Azure e ajuda a criar recursos necessários do Azure durante o provisionamento. Quando você [adiciona um novo recurso de funcionalidade](./add-resource.md) a um projeto existente, o modelo do ARM atualizado reflete a alteração mais recente.

> [!NOTE]
> Os serviços do Azure resultam em custos em sua assinatura. Para obter mais informações sobre estimativa de custo, consulte [a calculadora de preços](https://azure.microsoft.com/pricing/calculator/).

### <a name="resource-creation-for-teams-tab-application"></a>Criação de recursos para o aplicativo Guia do Teams

|Resource|Objetivo|Descrição |
|----------|--------------------------------|-----|
| Armazenamento do Microsoft Azure | Hospedar seu aplicativo de guia | Habilita o recurso de aplicativo Web estático para hospedar seu aplicativo de guia |
| Plano do serviço de aplicativo para autenticação simples | Hospedar o aplicativo Web para Autenticação Simples |Não aplicável |
| Aplicativo Web para autenticação simples | Hospedar servidor de autenticação simples para obter acesso a outros serviços em seu aplicativo de página única | Adiciona a identidade atribuída pelo usuário para acessar outros recursos do Azure |
| Identidade atribuída pelo usuário | Autenticar solicitações de serviço a serviço do Azure | Compartilhado entre funcionalidades e recursos diferentes |

### <a name="resource-creation-for-teams-bot-or-message-extension-application"></a>Criação de recursos para bot do Teams ou aplicativo de extensão de mensagem

|Resource|Objetivo| Descrição |
|----------|--------------------------------|-----|
| Serviço de bot do Azure | Registra seu aplicativo como um bot com a estrutura de bot | Conecta o bot ao Teams |
| Plano do serviço de aplicativo para bot | Hospedar o aplicativo Web do bot |Não aplicável |
| Aplicativo Web para bot | Hospedar seu aplicativo de bot | Adiciona a identidade atribuída pelo usuário para acessar outros recursos do Azure. <br /> Adiciona as configurações de aplicativo exigidas pelo [SDK do TeamsFx](https://www.npmjs.com/package/@microsoft/teamsfx) |
| Identidade atribuída pelo usuário | Autenticar solicitações de serviço a serviço do Azure | Compartilhado entre funcionalidades e recursos diferentes |

### <a name="resource-creation-for-azure-functions-in-the-project"></a>Criação de recursos para Azure Functions no projeto

|Resource|Objetivo| Descrição|
|----------|--------------------------------|-----|
| Plano do serviço de aplicativo para o aplicativo de funções | Hospedar o aplicativo de funções |Não aplicável |
| Aplicativo de funções | Hospedar suas APIs do Azure Functions | Adiciona a identidade atribuída pelo usuário para acessar outros recursos do Azure. <br /> Adiciona a regra CORS (compartilhamento de recursos entre origens) para permitir solicitações de seu aplicativo de guia <br /> Adiciona a configuração de autenticação que permite apenas solicitações do aplicativo Teams. <br /> Adiciona as configurações de aplicativo exigidas pelo [SDK do TeamsFx](https://www.npmjs.com/package/@microsoft/teamsfx) |
| Armazenamento do Azure para aplicativo de funções | Necessário para criar um aplicativo de funções |Não aplicável|
| Identidade atribuída pelo usuário | Autenticar solicitações de serviço a serviço do Azure | Compartilhado entre funcionalidades e recursos diferentes |

### <a name="resource-creation-for-azure-sql-in-the-project"></a>Criação de recursos para SQL do Azure no projeto

|Resource|Objetivo | Descrição |
|----------|--------------------------------|-----|
| SQL Server do Azure | Hospedar a instância do banco de dados SQL do Azure | Permite que todos os serviços do Azure acessem o servidor |
| Banco de Dados SQL do Azure | Armazenar dados para seu aplicativo | Concede a permissão de identidade atribuída pelo usuário, leitura ou gravação no banco de dados |
| Identidade atribuída pelo usuário | Autenticar solicitações de serviço a serviço do Azure | Compartilhado entre funcionalidades e recursos diferentes |

### <a name="resource-creation-for-azure-api-management-in-the-project"></a>Criação de recursos para o Gerenciamento de API do Azure no projeto

|Resource|Objetivo|
|----------|--------------------------------|
| Aplicativo Azure AD para o serviço de gerenciamento de API | Permite que o Microsoft Power Platform acesse às API gerenciadas pelo serviço de gerenciamento de API |
| Serviço de gerenciamento de API | Gerenciar suas APIs hospedadas no aplicativo de funções |
| Produto de gerenciamento de API | Agrupar suas APIs, definir termos de uso e políticas de runtime |
| Servidor OAuth de gerenciamento de API | Permite que o Microsoft Power Platform acesse suas APIs hospedadas no aplicativo de funções |
| Identidade atribuída pelo usuário | Autenticar solicitações de serviço a serviço do Azure |

### <a name="resources-created-when-including-azure-key-vault-in-the-project"></a>Recursos criados ao incluir o Azure Key Vault no projeto

|Recursos|Finalidade deste recurso|
|----------|--------------------------------|
| Serviço do Azure Key Vault | Gerenciar segredos (por exemplo, segredo do cliente do aplicativo Azure AD) usados por outros Serviços do Azure |
| Identidade Atribuída pelo Usuário | Autenticar solicitações de serviço a serviço do Azure |

## <a name="customize-resource-provision"></a>Personalizar o provisionamento de recursos

O Kit de Ferramentas do Teams permite que você use uma infraestrutura como abordagem de código para definir quais recursos do Azure deseja provisionar e como deseja configurar. A ferramenta usa o modelo do ARM para definir recursos do Azure. O modelo do ARM é um conjunto de arquivos bicep que define a infraestrutura e a configuração do seu projeto. É possível personalizar os recursos do Azure modificando o modelo do ARM. Para obter mais informações, confira este [documento bicep](/azure/azure-resource-manager/bicep).

O provisionamento com o ARM envolve a alteração dos seguintes conjuntos de arquivos, parâmetros e modelos:

* Arquivos de parâmetro do ARM (`azure.parameters.{your_env_name}.json`) localizados na pasta `.fx/configs`, para passar parâmetros para modelos.
* Arquivos de modelo do ARM localizados em `templates/azure`, esta pasta contém os seguintes arquivos:

| Arquivo | Função | Permitir personalização |
| --- | --- | --- |
| main.bicep | Fornecer ponto de entrada para provisionamento de recursos do Azure | Sim |
| provision.bicep | Criar e configurar recursos do Azure | Sim |
| config.bicep | Adicionar as configurações necessárias do TeamsFx aos recursos do Azure | Sim |
| provision/xxx.bicep | Criar e configurar cada recurso do Azure consumido por `provision.bicep` | Sim |
| teamsfx/xxx.bicep | Adicionar as configurações necessárias do TeamsFx a cada recurso do Azure consumido por `config.bicep`| Não |

> [!NOTE]
> Ao adicionar recursos ou funcionalidades ao seu projeto, `teamsfx/xxx.bicep` será regenerado, não será possível personalizar o mesmo. Para modificar os arquivos bicep, é possível usar o Git para controlar suas alterações em arquivos `teamsfx/xxx.bicep`, o que ajuda você a não perder alterações ao adicionar recursos ou funcionalidades.

### <a name="customize-arm-parameters-and-templates"></a>Personalizar parâmetros e modelos do ARM

É possível personalizar os recursos do Azure personalizando os arquivos de parâmetro e personalizando os arquivos bicep.

#### <a name="customize-arm-template-parameter-files"></a>Personalizar arquivos de parâmetro de modelo do ARM

O kit de ferramentas fornece um conjunto de parâmetros predefinidos para personalizar os recursos do Azure. Os arquivos de parâmetro estão localizados em `.fx/configs/azure.parameters.{env}.json` e todos os parâmetros disponíveis são definidos na propriedade `provisionParameters`. É recomendável personalizar os arquivos de parâmetro se os parâmetros predefinidos atenderem às suas necessidades.

A tabela a seguir fornece uma lista de parâmetros predefinidos disponíveis:

| Nome do parâmetro | Valor padrão | O que pode ser personalizado pelo parâmetro | Restrições de valor |
| --- | --- | --- | --- |
| resourceBaseName | Gerado automaticamente para cada ambiente | Nome padrão para todos os recursos | 2 a 20 letras minúsculas e números |
| simpleAuthServerFarmsName | ${resourceBaseName}simpleAuth | Nome do plano de serviço de aplicativo de autenticação simples | 1 a 40 alfanuméricos e hifens |
| simpleAuthWebAppName | ${resourceBaseName}simpleAuth | Nome do aplicativo Web de autenticação simples | 2 a 60 alfanuméricos e hifens <br /> Não é possível iniciar ou terminar com hífen |
| simpleAuthSku | F1 | SKU do plano de serviço de aplicativo de autenticação simples | Não aplicável |
| frontendHostingStorageName | ${resourceBaseName}tab | Nome da conta de armazenamento de hospedagem de front-end | 3 a 24 letras minúsculas e números |
| frontendHostingStorageSku | Standard_LRS | SKU da conta de armazenamento de hospedagem de front-end |[SKUs disponíveis](/azure/templates/microsoft.storage/storageaccounts?tabs=bicep)|
| functionServerfarmsName | ${resourceBaseName}api | Nome do plano de serviço de aplicativos de funções | 1 a 40 alfanuméricos e hifens |
| functionServerfarmsSku | Y1 | SKU do plano de serviço de aplicativos de funções | Não aplicável|
| functionAppName | ${resourceBaseName}api | Nome do aplicativo de funções | 2 a 60 alfanuméricos e hifens <br /> Não é possível iniciar ou terminar com hífen |
| functionStorageName | ${resourceBaseName}api | Nome da conta de armazenamento do aplicativo de funções | 3 a 24 letras minúsculas e números |
| functionStorageSku | Standard_LRS | SKU da conta de armazenamento do aplicativo de funções | [SKUs disponíveis](/azure/templates/microsoft.storage/storageaccounts?tabs=bicep) |
| botServiceName | ${resourceBaseName} | Nome do serviço de bot do Azure | 2 a64 alfanuméricos, sublinhados, pontos e hifens <br /> Começar com alfanumérico |
| botServiceSku | F0 | SKU do serviço de bot do Azure | [SKUs disponíveis](/azure/templates/microsoft.botservice/2021-05-01-preview/botservices?tabs=bicep) |
| botDisplayName | ${resourceBaseName} | Nome de exibição do bot | 1 a 42 caracteres |
| botServerfarmsName | ${resourceBaseName}bot | Nome do plano do serviço de aplicativo do bot | 1 a 40 alfanuméricos e hifens |
| botWebAppName | ${resourceBaseName}bot | Nome do aplicativo Web do bot | 2 a 60 alfanuméricos e hifens <br /> Não é possível iniciar ou terminar com hífen |
| botWebAppSKU | F1 | SKU do Plano do Serviço de Aplicativo de Bot | Não aplicável |
| userAssignedIdentityName | ${resourceBaseName} | Nome da identidade atribuída pelo usuário | 3 a 128 alfanuméricos, hifens e sublinhados <br /> Começar com letra ou número |
| sqlServerName | ${resourceBaseName} | Nome do SQL server do Azure | 1 a 63 letras minúsculas, números e hifens <br /> Não é possível iniciar ou terminar com hífen |
| sqlDatabaseName | ${resourceBaseName} | Nome do banco de dados SQL do Azure | 1 a 128 caracteres, não é possível usar <>*%&:\/? ou caracteres de controle <br /> Não é possível terminar com ponto ou espaço |
| sqlDatabaseSku | Básico | SKU do banco de dados SQL do Azure | Não aplicável  |
| apimServiceName | ${resourceBaseName} | Nome do serviço APIM | 1 a 50 alfanuméricos e hifens <br /> Começar com letra e terminar com alfanumérico |
| apimServiceSku | Consumo | SKU do serviço APIM | [SKUs disponíveis](/azure/templates/microsoft.apimanagement/service?tabs=bicep) |
| apimProductName | ${resourceBaseName} | Nome do produto APIM | 1 a 80 alfanuméricos e hifens <br /> Começar com letra e terminar com alfanumérico |
| apimOauthServerName | ${resourceBaseName} | Nome do servidor OAuth do APIM | 1 a 80 alfanuméricos e hifens <br /> Começar com letra e terminar com alfanumérico |
| keyVaultSkuName | padrão | Nome da SKU do Serviço de Key Vault Azure| |

Enquanto isso, os parâmetros a seguir estão disponíveis com valores preenchidos durante o provisionamento. A finalidade desses espaços reservados é garantir que possamos criar novos recursos para você em um novo ambiente. Os valores reais são resolvidos de `.fx/states/state.{env}.json`.

##### <a name="azure-ad-application-related-parameters"></a>Parâmetros relacionados ao aplicativo Azure AD

| Nome do parâmetro | Espaço reservado para valor padrão | Significado do espaço reservado | Como personalizar |
| --- | --- | --- | --- |
| Microsoft 365 ClientId | {{state.fx-resource-aad-app-for-teams.clientId}} | A ID do cliente do aplicativo Azure AD criada durante o provisionamento | [Personalizar o valor](#use-an-existing-azure-ad-app-for-your-teams-app) |
| Microsoft 365 ClientSecret | {{state.fx-resource-aad-app-for-teams.clientSecret}} | O segredo do cliente do aplicativo Azure AD criado durante o provisionamento | [Personalizar o valor](#use-an-existing-azure-ad-app-for-your-teams-app)  |
| Microsoft 365 TenantId | {{state.fx-resource-aad-app-for-teams.tenantId}} | ID do locatário do aplicativo Azure AD | [Personalizar o valor](#use-an-existing-azure-ad-app-for-your-teams-app)  |
| Microsoft 365 OAuthAuthorityHost | {{state.fx-resource-aad-app-for-teams.oauthHost}} | Host de autoridade OAuth do aplicativo Azure AD | [Personalizar o valor](#use-an-existing-azure-ad-app-for-your-teams-app) |
| botAadAppClientId | {{state.fx-resource-bot.botId}} | ID do cliente do aplicativo Azure AD do bot criada durante o provisionamento | [Personalizar o valor](#use-an-existing-azure-ad-app-for-your-bot) |
| botAadAppClientSecret | {{state.fx-resource-bot.botPassword}} | O segredo do cliente do aplicativo Azure AD do bot criado durante o provisionamento | [Personalizar o valor](#use-an-existing-azure-ad-app-for-your-bot) |
| apimClientId | {{state.fx-resource-apim.apimClientAADClientId}} | ID do cliente do aplicativo Azure AD do APIM criada durante o provisionamento | Excluir o espaço reservado e preencher o valor real |
| apimClientSecret | {{state.fx-resource-apim.apimClientAADClientSecret}} | O segredo do cliente do aplicativo Azure AD do APIM criado durante o provisionamento | Excluir o espaço reservado e preencher o valor real |

##### <a name="azure-resource-related-parameters"></a>Parâmetros relacionados a recursos do Azure

| Nome do parâmetro | Espaço reservado para valor padrão | Significado do espaço reservado | Como personalizar |
| --- | --- | --- | --- |
| azureSqlAdmin | {{state.fx-resource-azure-sql.admin}} | Conta de administrador do SQL Server do Azure que você forneceu durante o provisionamento | Excluir o espaço reservado e preencher o valor real |
| azureSqlAdminPassword | {{state.fx-resource-azure-sql.adminPassword}} | Senha do administrador do SQL Server do Azure que você forneceu durante o provisionamento | Excluir o espaço reservado e preencher o valor real |
| apimPublisherEmail | {{state.fx-resource-apim.publisherEmail}} | Email do editor do APIM, o valor padrão é sua conta do Azure | Excluir o espaço reservado e preencher o valor real |
| apimPublisherName | {{state.fx-resource-apim.publisherName}} | Nome do editor do APIM, o valor padrão é sua conta do Azure | Excluir o espaço reservado e preencher o valor real |

#### <a name="referencing-environment-variables-in-parameter-files"></a>Referenciando variáveis de ambiente em arquivos de parâmetro

Se você não quiser codificar os valores em arquivos de parâmetro, por exemplo, quando o valor for um segredo. Os arquivos de parâmetro dão suporte à referência aos valores de variáveis de ambiente. É possível usar a sintaxe `{{$env.YOUR_ENV_VARIABLE_NAME}}` em valores de parâmetro para a ferramenta resolver da variável de ambiente atual.

O exemplo a seguir lê o valor do `mySelfHostedDbConnectionString` parâmetro da variável de ambiente `DB_CONNECTION_STRING`:

```json
...
    "mySelfHostedDbConnectionString": "{{$env.DB_CONNECTION_STRING}}"
...
```

#### <a name="customize-arm-template-files"></a>Personalizar arquivos de modelo do ARM

Se os modelos predefinidos não atenderem às suas necessidades de aplicativo, será possível personalizar os modelos do ARM na pasta `templates/azure`. Por exemplo, é possível personalizar o modelo do ARM para criar alguns recursos adicionais do Azure para seu aplicativo. É necessário ter conhecimento básico da linguagem bicep, que é usada para criar um modelo do ARM. É possível começar a usar o bicep na [documentação do bicep](/azure/azure-resource-manager/bicep/).

> [!NOTE]
> O modelo do ARM é compartilhado por todos os ambientes. Será possível usar a [implantação condicional](/azure/azure-resource-manager/bicep/conditional-resource-deployment) se o comportamento de provisionamento variar entre ambientes.

Para garantir que a ferramenta do TeamsFx funcione corretamente, personalize o modelo do ARM, que atende ao requisito a seguir. Se você usar outra ferramenta para desenvolvimento adicional, poderá ignorar esses requisitos.

* Mantenha a estrutura da pasta e o nome do arquivo inalterados. A ferramenta pode acrescentar novo conteúdo a arquivos existentes quando você adiciona mais recursos ou funcionalidades ao seu projeto.
* Mantenha o nome dos parâmetros gerados automaticamente, bem como seus nomes de propriedade inalterados. Os parâmetros gerados automaticamente podem ser usados quando você adiciona mais recursos ou funcionalidades ao seu projeto.
* Mantenha a saída do modelo do ARM gerado automaticamente inalterada. É possível adicionar saídas adicionais ao modelo do ARM. A saída é `.fx/states/state.{env}.json` e pode ser usada em outros recursos, como implantar, validar arquivo de manifesto.

### <a name="customization-scenarios"></a>Cenários de personalização

É possível personalizar os seguintes cenários:

#### <a name="use-an-existing-azure-ad-app-for-your-bot"></a>Usar um aplicativo Azure AD existente para seu bot

É possível adicionar o seguinte trecho de código de configuração ao arquivo `.fx/configs/config.{env}.json` para usar um aplicativo Azure AD criado por você mesmo para seu aplicativo Teams. Para criar um aplicativo Azure AD, consulte <https://aka.ms/teamsfx-existing-aad-doc>.

```json
"auth": {
    "clientId": "<your Azure AD app client id>",
    "clientSecret": "{{$env.ENV_NAME_THAT_STORES_YOUR_SECRET}}",
    "objectId": "<your Azure AD app object id>",
    "accessAsUserScopeId": "<id of the access_as_user scope>"
}
```

Depois de adicionar o trecho de código, adicione seu segredo à variável de ambiente relacionada para que a ferramenta possa resolver o segredo real durante o provisionamento.

> [!NOTE]
> Certifique-se de não compartilhar o mesmo aplicativo Azure AD em vários ambientes. Se você não tiver permissão para atualizar o aplicativo Azure AD, poderá receber um aviso com instruções sobre como atualizar manualmente o aplicativo Azure AD. Siga as instruções para atualizar seu aplicativo Azure AD após o provisionamento.

#### <a name="use-an-existing-azure-ad-app-for-your-teams-app"></a>Usar um aplicativo Azure AD existente para seu aplicativo Teams

É possível adicionar o seguinte trecho de código de configuração ao arquivo `.fx/configs/config.{env}.json` para usar um aplicativo Azure AD criado por conta própria para o bot:

```json
"bot": {
    "appId": "<your Azure AD app client id>",
    "appPassword": "{{$env.ENV_NAME_THAT_STORES_YOUR_SECRET}}"
}
```

Depois de adicionar o trecho de código anterior, adicione seu segredo à variável de ambiente relacionada para que a ferramenta resolva o segredo real durante o provisionamento.

#### <a name="skip-adding-user-for-sql-database"></a>Ignorar a adição de usuário para o banco de dados SQL

Se você tiver um erro de permissão insuficiente quando a ferramenta tentar adicionar o usuário ao banco de dados SQL, poderá adicionar o seguinte trecho de código de configuração ao arquivo `.fx/configs/config.{env}.json` para ignorar a adição de usuário do banco de dados SQL:

```json
"skipAddingSqlUser": true
```

### <a name="specifying-the-name-of-function-app-instance"></a>Especificando o nome da instância do Aplicativo de Funções

É possível usar `contosoteamsappapi` para a instância do aplicativo de funções em vez de usar o nome padrão.

> [!NOTE]
> Se você já tiver provisionado o ambiente, especificar o nome poderá criar uma nova instância de aplicativo de funções para você, em vez de renomear a instância criada anteriormente.

As etapas a seguir são:

1. Abra `.fx/configs/azure.parameters.{env}.json` para seu ambiente atual.
2. Adicione uma nova propriedade `functionAppName` ao valor do parâmetro `provisionParameters`.
3. Insira `contosoteamsappapi` como valor de `functionAppName`.
4. O arquivo de parâmetro final é mostrado no trecho de código a seguir:

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

### <a name="scenerio"></a>Cenário

Para adicionar outro recurso ou armazenamento do Azure ao aplicativo:

Considere o cenário, você deseja adicionar o armazenamento do Azure ao back-end do Azure Functions para armazenar dados de blob. Não há nenhum fluxo automático para atualizar o modelo bicep com suporte de armazenamento do Azure. No entanto, é possível editar o arquivo bicep e adicionar o recurso. As etapas são as seguintes:

1. Crie um projeto de guia.
2. Adicione a função ao projeto. Para saber mais, consulte [adicionar recursos](./add-resource.md).
3. Declare a nova conta de armazenamento no modelo do ARM. É possível declarar o recurso em `templates/azure/provision/function.bicep` diretamente. É possível declarar os recursos em outros locais.

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

4. Atualize as configurações de aplicativo do Azure Functions com a cadeia de conexão de armazenamento do Azure em `templates/azure/provision/function.bicep`. Adicione o seguinte trecho de código à matriz `appSettings` do recurso `functionApp`:

    ``````````````````bicep
    {
        name: 'MyAppStorageAccountConnectionString'
        value: 'DefaultEndpointsProtocol=https;AccountName=${applicationStorageAccount.name};AccountKey=${listKeys(applicationStorageAccount.id, '2021-06-01').keys[0].value}'
    }
    ```````````````````

5. É possível atualizar sua função com associações de saída de armazenamento do Azure.

## <a name="faq"></a>Perguntas frequentes

<br>

<details>

<summary><b>Como solucionar problemas?</b></summary>

Se você receber mensagens de erro com o Kit de Ferramentas do Teams no Visual Studio Code, poderá selecionar **Obter Ajuda** na notificação de erro para navegar até o documento relacionado. Se você estiver usando a CLI do TeamsFx, haverá um hiperlink no final da mensagem de erro que aponta para o documento de ajuda. Também é possível visualizar o [documento de ajuda de provisionamento](https://aka.ms/teamsfx-arm-help) diretamente.

<br>

</details>

<details>

<summary><b>Como posso alternar para outra assinatura do Azure durante o provisionamento?</b></summary>

1. Alterne a assinatura na conta atual ou faça logoff e selecione uma nova assinatura.
2. Se você já tiver provisionado o ambiente atual, precisará criar um novo ambiente e executar o provisionamento porque o ARM não dá suporte à movimentação de recursos.
3. Se você não provisionou o ambiente atual, poderá disparar o provisionamento diretamente.

<br>

</details>

<details>

<summary><b>Como posso alterar o grupo de recursos durante o provisionamento?</b></summary>

Antes de provisionar, a ferramenta pergunta se você deseja criar um novo grupo de recursos ou usar um existente. É possível fornecer um novo nome de grupo de recursos ou escolher um existente nesta etapa.

<br>

</details>

<details>

<summary><b>Como posso provisionar um aplicativo baseado no SharePoint?</b></summary>

É possível seguir [provisionar aplicativos baseados no SharePoint](/microsoftteams/platform/sbs-gs-spfx?tabs=vscode%2Cviscode&tutorial-step=4).

> [!NOTE]
> Atualmente, a criação de aplicativos do Teams com a estrutura do SharePoint com o Kit de Ferramentas do Teams não tem integração direta com o Azure, o conteúdo no documento não se aplica a aplicativos baseados em SPFx.

<br>

</details>

## <a name="see-also"></a>Confira também

* [Implantar o aplicativo Teams na nuvem](deploy.md)
* [Gerenciar vários ambientes](TeamsFx-multi-env.md)
* [Colaborar com outros desenvolvedores no projeto do Teams](TeamsFx-collaboration.md)
