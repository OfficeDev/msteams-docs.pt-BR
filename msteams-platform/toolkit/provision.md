---
title: Usar o Kit de Ferramentas do Teams para provisionar recursos de nuvem
author: MuyangAmigo
description: Neste módulo, saiba como provisionar recursos de nuvem usando o Kit de Ferramentas do Teams, criar recursos e personalizar o provisionamento de recursos
ms.author: shenwe
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
zone_pivot_groups: teams-app-platform
ms.openlocfilehash: 175854db36b85a1fc68cc299bd733b7abd539ac9
ms.sourcegitcommit: de7496f9586316bed12d115cd3e4c18ba0854d4f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2022
ms.locfileid: "67780943"
---
# <a name="provision-cloud-resources"></a>Provisionar recursos de nuvem

O TeamsFx integra-se ao Azure e à nuvem do Microsoft 365, o que permite que você coloque seu aplicativo no Azure com um único comando. O TeamsFx integra-se ao Azure Resource Manager que permite provisionar recursos do Azure dos quais seu aplicativo precisa para a abordagem de código.

::: zone pivot="visual-studio-code"

## <a name="provision-using-teams-toolkit-in-visual-studio-code"></a>Provisionar usando o Kit de Ferramentas do Teams Visual Studio Code

O provisionamento é executado com um único comando no Kit de Ferramentas do Teams Visual Studio Code ou na CLI do TeamsFx. Para obter mais informações, consulte [Provisionar aplicativo baseado no Azure](/microsoftteams/platform/sbs-gs-javascript?tabs=vscode%2Cvsc%2Cviscode%2Cvcode&tutorial-step=8)

## <a name="create-resources"></a>Criar recursos

Ao disparar o comando provisionar no Kit de Ferramentas do Teams ou na CLI do TeamsFx, é possível obter os seguintes recursos:

* Microsoft Azure Active Directory (Azure AD) em seu locatário do Microsoft 365.
* Registro de aplicativo do Teams na plataforma do Teams do locatário do Microsoft 365.
* Recursos do Azure em sua assinatura do Azure selecionada.

Ao criar um novo projeto, é possível usar todos os recursos do Azure. O modelo do ARM define todos os recursos do Azure e ajuda a criar recursos necessários do Azure durante o provisionamento. Quando você [adiciona um novo recurso de funcionalidade](./add-resource.md) a um projeto existente, o modelo do ARM atualizado reflete a alteração mais recente.

> [!NOTE]
> Os serviços do Azure resultam em custos em sua assinatura. Para obter mais informações sobre estimativa de custo, consulte [a calculadora de preços](https://azure.microsoft.com/pricing/calculator/).

A lista a seguir mostra a criação de recursos para diferentes tipos de aplicativos e recursos do Azure:
<br>

<details>
<summary><b>Criação de recursos para o aplicativo Guia do Teams</b></summary>

|Resource|Objetivo|Descrição |
|----------|--------------------------------|-----|
| Armazenamento do Microsoft Azure | Hospedar seu aplicativo de guia | Habilita o recurso de aplicativo Web estático para hospedar seu aplicativo de guia |
| Plano do serviço de aplicativo para autenticação simples | Hospedar o aplicativo Web para Autenticação Simples |Não aplicável |
| Aplicativo Web para autenticação simples | Hospedar servidor de autenticação simples para obter acesso a outros serviços em seu aplicativo de página única | Adiciona a identidade atribuída pelo usuário para acessar outros recursos do Azure |
| Identidade atribuída pelo usuário | Autenticar solicitações de serviço a serviço do Azure | Compartilhado entre funcionalidades e recursos diferentes |

</details>
<br>

<details>
<summary><b>Criação de recursos para bot do Teams ou aplicativo de extensão de mensagem</b></summary>

|Resource|Objetivo| Descrição |
|----------|--------------------------------|-----|
| Serviço de bot do Azure | Registra seu aplicativo como um bot com a estrutura de bot | Conecta o bot ao Teams |
| Plano do serviço de aplicativo para bot | Hospedar o aplicativo Web do bot |Não aplicável |
| Aplicativo Web para bot | Hospedar seu aplicativo de bot | Adiciona a identidade atribuída pelo usuário para acessar outros recursos do Azure. <br /> Adiciona as configurações de aplicativo exigidas pelo [SDK do TeamsFx](https://www.npmjs.com/package/@microsoft/teamsfx) |
| Identidade atribuída pelo usuário | Autenticar solicitações de serviço a serviço do Azure | Compartilhado entre funcionalidades e recursos diferentes |

</details>
<br>

<details>
<summary><b>Criação de recursos para Azure Functions no projeto</b></summary>

|Resource|Objetivo| Descrição|
|----------|--------------------------------|-----|
| Plano do serviço de aplicativo para o aplicativo de funções | Hospedar o aplicativo de funções |Não aplicável |
| Aplicativo de funções | Hospedar suas APIs do Azure Functions | Adiciona a identidade atribuída pelo usuário para acessar outros recursos do Azure. <br /> Adiciona a regra CORS (compartilhamento de recursos entre origens) para permitir solicitações de seu aplicativo de guia <br /> Adiciona a configuração de autenticação que permite apenas solicitações do aplicativo Teams. <br /> Adiciona as configurações de aplicativo exigidas pelo [SDK do TeamsFx](https://www.npmjs.com/package/@microsoft/teamsfx) |
| Armazenamento do Azure para aplicativo de funções | Necessário para criar um aplicativo de funções |Não aplicável|
| Identidade atribuída pelo usuário | Autenticar solicitações de serviço a serviço do Azure | Compartilhado entre funcionalidades e recursos diferentes |

</details>
<br>

<details>
<summary><b>Criação de recursos para SQL do Azure no projeto</b></summary>

|Resource|Objetivo | Descrição |
|----------|--------------------------------|-----|
| SQL Server do Azure | Hospedar a instância do banco de dados SQL do Azure | Permite que todos os serviços do Azure acessem o servidor |
| Banco de Dados SQL do Azure | Armazenar dados para seu aplicativo | Concede a permissão de identidade atribuída pelo usuário, leitura ou gravação no banco de dados |
| Identidade atribuída pelo usuário | Autenticar solicitações de serviço a serviço do Azure | Compartilhado entre funcionalidades e recursos diferentes |

</details>
<br>

<details>
<summary><b>Criação de recursos para o Gerenciamento de API do Azure no projeto</b></summary>

|Resource|Objetivo|
|----------|--------------------------------|
| Aplicativo Azure AD para o serviço de gerenciamento de API | Permite que o Microsoft Power Platform acesse às API gerenciadas pelo serviço de gerenciamento de API |
| Serviço de gerenciamento de API | Gerenciar suas APIs hospedadas no aplicativo de funções |
| Produto de gerenciamento de API | Agrupar suas APIs, definir termos de uso e políticas de runtime |
| Servidor OAuth de gerenciamento de API | Permite que o Microsoft Power Platform acesse suas APIs hospedadas no aplicativo de funções |
| Identidade atribuída pelo usuário | Autenticar solicitações de serviço a serviço do Azure |

</details>
<br>

<details>
<summary><b>Recursos criados ao incluir o Azure Key Vault no projeto</b></summary>

|Recursos|Finalidade deste recurso|
|----------|--------------------------------|
| Serviço do Azure Key Vault | Gerenciar segredos (por exemplo, segredo do cliente do aplicativo Azure AD) usados por outros Serviços do Azure |
| Identidade Atribuída pelo Usuário | Autenticar solicitações de serviço a serviço do Azure |

</details>
<br>

## <a name="customize-resource-provision"></a>Personalizar o provisionamento de recursos

O Kit de Ferramentas do Teams permite que você use uma abordagem de infraestrutura como código para definir os recursos do Azure que você deseja provisionar e como deseja configurar. A ferramenta usa o modelo do ARM para definir recursos do Azure. O modelo do ARM é um conjunto de arquivos bicep que define a infraestrutura e a configuração do seu projeto. É possível personalizar os recursos do Azure modificando o modelo do ARM. Para obter mais informações, confira este [documento bicep](/azure/azure-resource-manager/bicep).

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

### <a name="azure-ad-parameters"></a>Azure AD parâmetros

Os arquivos de modelo do ARM usam espaços reservados para parâmetros. A finalidade desses espaços reservados é garantir a criação de novos recursos para você em um novo ambiente. Os valores reais são resolvidos de `.fx/states/state.{env}.json`.

Há dois tipos de parâmetros, como parâmetros relacionados Azure AD aplicativo e parâmetros relacionados a recursos do Azure.

##### <a name="azure-ad-application-related-parameters"></a>Parâmetros relacionados ao aplicativo Azure AD

| Nome do parâmetro | Espaço reservado para valor padrão | Significado do espaço reservado | Como personalizar |
| --- | --- | --- | --- |
| Microsoft 365 ClientId | {{state.fx-resource-aad-app-for-teams.clientId}} | A ID do cliente do aplicativo Azure AD criada durante o provisionamento | [Usar um aplicativo Azure AD existente para seu bot](#use-an-existing-azure-ad-app-for-your-bot) |
| Microsoft 365 ClientSecret | {{state.fx-resource-aad-app-for-teams.clientSecret}} | O segredo do cliente do aplicativo Azure AD criado durante o provisionamento | [Usar um aplicativo Azure AD existente para seu aplicativo Teams](#use-an-existing-azure-ad-app-for-your-teams-app) |
| Microsoft 365 TenantId | {{state.fx-resource-aad-app-for-teams.tenantId}} | ID do locatário do aplicativo Azure AD | [Usar um aplicativo Azure AD existente para seu aplicativo Teams](#use-an-existing-azure-ad-app-for-your-teams-app)  |
| Microsoft 365 OAuthAuthorityHost | {{state.fx-resource-aad-app-for-teams.oauthHost}} | Host de autoridade OAuth do aplicativo Azure AD | [Usar um aplicativo Azure AD existente para seu aplicativo Teams](#use-an-existing-azure-ad-app-for-your-teams-app) |
| botAadAppClientId | {{state.fx-resource-bot.botId}} | ID do cliente do aplicativo Azure AD do bot criada durante o provisionamento | [Usar um aplicativo Azure AD existente para seu bot](#use-an-existing-azure-ad-app-for-your-bot) |
| botAadAppClientSecret | {{state.fx-resource-bot.botPassword}} | O segredo do cliente do aplicativo Azure AD do bot criado durante o provisionamento | [Usar um aplicativo Azure AD existente para seu bot](#use-an-existing-azure-ad-app-for-your-bot) |

##### <a name="azure-resource-related-parameters"></a>Parâmetros relacionados a recursos do Azure

| Nome do parâmetro | Espaço reservado para valor padrão | Significado do espaço reservado | Como personalizar |
| --- | --- | --- | --- |
| azureSqlAdmin | {{state.fx-resource-azure-sql.admin}} | Conta de administrador do SQL Server do Azure que você forneceu durante o provisionamento | Excluir o espaço reservado e preencher o valor real |
| azureSqlAdminPassword | {{state.fx-resource-azure-sql.adminPassword}} | Senha do administrador do SQL Server do Azure que você forneceu durante o provisionamento | Excluir o espaço reservado e preencher o valor real |

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
2. Adicione uma nova propriedade, por exemplo, `functionAppName` na `provisionParameters` seção.
3. Insira um valor de `functionAppName`, por exemplo `contosoteamsappapi`.
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

Para adicionar outro recurso ou armazenamento do Azure ao aplicativo:

Considere o seguinte cenário:

Você deseja adicionar o armazenamento do Azure ao back-end da função do Azure para armazenar dados de blob. Não há nenhum fluxo automático para atualizar o modelo bicep com suporte de armazenamento do Azure. No entanto, é possível editar o arquivo bicep e adicionar o recurso. As etapas são as seguintes:

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

::: zone-end

::: zone pivot="visual-studio"

## <a name="provision-using-teams-toolkit-in-visual-studio"></a>Provisionar usando o Kit de Ferramentas do Teams no Visual Studio

As etapas a seguir ajudam você a provisionar recursos de nuvem usando o Visual Studio:

### <a name="sign-in-to-your-microsoft-365-account"></a>Entre em sua conta do Microsoft 365

1. Abra o Visual Studio 2022.
1. Abra o projeto de aplicativo do Microsoft Teams.
1. Selecione **Kit de****Ferramentas do Project** >  Teams **–** >  Preparar dependências de aplicativo do Teams.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Provision-cloud-resources-in-TTK-VS/teams-toolkit-vs-prepare-app-dependencies1.png" alt-text="Preparar as dependências do aplicativo teams":::

1. Selecione **Entrar para** entrar em sua conta do Azure.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Provision-cloud-resources-in-TTK-VS/teams-toolkit-vs-prepare1.png" alt-text="Entrar no Microsoft 365":::

    > [!NOTE]
    > Se você já estiver conectado, seu nome de usuário será exibido ou poderá selecionar o mesmo para alternar sua conta.

1. O navegador da Web padrão é aberto para permitir [que você entre](https://developer.microsoft.com/en-us/microsoft-365/dev-program) na conta.

1. Selecione **Continuar** depois de entrar em sua conta.

    :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Provision-cloud-resources-in-TTK-VS/teams-toolkit-vs-signin-M365.png" alt-text="Confirme selecionando continuar":::

### <a name="sign-in-to-your-azure-account"></a>Entrar em sua conta do Azure

1. Abra o Visual Studio 2022.
1. Abra o projeto de aplicativo do Teams.
1. Selecione **Provisionar o Kit de Ferramentas do** >  **Project** >  Teams **na nuvem**.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Provision-cloud-resources-in-TTK-VS/teams-toolkit-vs-provision-in-cloud2.png" alt-text="Entrar na conta do Azure":::

1. Selecione **Entrar...** para entrar em sua conta do Azure.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Provision-cloud-resources-in-TTK-VS/teams-toolkit-vs-provision-start.png" alt-text="Entrar em sua conta do Azure":::

   > [!NOTE]
   > Se você já estiver conectado, seu nome de usuário será exibido ou você terá a opção de mudar de conta.

   Depois de entrar em sua conta do Azure usando suas credenciais, o navegador é fechado automaticamente.

### <a name="to-provision-cloud-resources"></a>Para provisionar recursos de nuvem

Depois de abrir o projeto no Visual Studio:

1. Selecione **Provisionar o Kit de Ferramentas do** >  **Project** >  Teams **na nuvem**.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Provision-cloud-resources-in-TTK-VS/teams-toolkit-vs-provision-in-cloud2.png" alt-text="Provisionar na nuvem":::

   A **janela Provisionar** é exibida.

1. Insira os detalhes a seguir para provisionar seus recursos.

    :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Provision-cloud-resources-in-TTK-VS/teams-toolkit-vs-provision-select-subscription1.png" alt-text="Selecionar grupo de recursos":::

   1. Selecione o **nome da assinatura** na lista suspensa.
   1. Selecione seu **Grupo de recursos** na lista suspensa.
   1. Selecione sua **região** na lista suspensa.

      > [!NOTE]
      > Você pode criar um novo grupo de recursos selecionando **Novo**.

   1. Selecione **Provisionar**.

1. A caixa de diálogo é exibida mencionando que os encargos podem ser adicionados de acordo com o uso do Azure. Selecione **Provisionar**.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Provision-cloud-resources-in-TTK-VS/teams-toolkit-vs-provision-warning.png" alt-text="Aviso de provisionamento":::

   O processo de provisionamento cria recursos na nuvem do Azure. Você pode monitorar o progresso observando a janela de saída do Kit de Ferramentas do Teams.

1. Você será solicitado após a conclusão do provisionamento. Selecione **Exibir Recursos Provisionados** para exibir todos os recursos que foram provisionados.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Provision-cloud-resources-in-TTK-VS/teams-toolkit-vs-provision-provision-success.png" alt-text="Exibir recursos provisionados":::

## <a name="create-resources"></a>Criar recursos

Ao disparar o comando provisionar no Teams Toolkit ou na CLI do TeamsFx, você pode criar os seguintes recursos:

* Microsoft Azure Active Directory (Azure AD) em seu locatário do Microsoft 365.
* Registro de aplicativo do Teams na plataforma do Teams do locatário do Microsoft 365.
* Recursos do Azure em sua assinatura do Azure selecionada.

Ao criar um novo projeto, você também precisa criar recursos do Azure. Os modelos do ARM (Azure Resource Manager) definem todos os recursos do Azure e ajudam você a criar os recursos necessários do Azure durante o provisionamento.

A lista a seguir mostra a criação de recursos para diferentes tipos de aplicativos e recursos do Azure:
<br>

<details>
<summary><b>Criação de recursos para o aplicativo Guia do Teams</b></summary>

| Resource | Objetivo | Descrição |
| --- | --- | --- |
| Plano do serviço de aplicativo | Hospeda seu aplicativo Web da guia. | Não aplicável |
| Serviço de aplicativo | Hospeda o aplicativo da guia Blazor e o servidor de autenticação simples que ajuda a obter acesso a outros serviços. | Adiciona a identidade atribuída pelo usuário para acessar outros recursos do Azure. |
| Gerenciar identidade | Autenticar solicitações de serviço a serviço do Azure. | Compartilhamentos entre recursos e recursos diferentes. |

</details>
<br>

<details>
<summary><b>Criação de recursos para o aplicativo de extensão de mensagem do Teams</b></summary>

| Resource | Objetivo | Descrição |
| --- | --- | --- |
| Bot do Azure | Registra seu aplicativo como um bot com a estrutura do bot. | Conecta o bot ao Teams. |
| Serviço de Aplicativo plano | Hospeda seu aplicativo web bot. | Não aplicável |
| Serviço de Aplicativo | Hospeda seu aplicativo de bot. | Adiciona a identidade atribuída pelo usuário para acessar outros recursos do Azure. |
| Gerenciar identidade | Autenticar solicitações de serviço a serviço do Azure. | Compartilhamentos entre recursos e recursos diferentes. |

</details>
<br>

<details>
<summary><b>Criação de recursos para o aplicativo de bot de comando do Teams</b></summary>

| Resource | Objetivo | Descrição |
| --- | --- | --- |
| Bot do Azure | Registra seu aplicativo como um bot com a estrutura do bot. | Conecta o bot ao Teams. |
| Plano do serviço de aplicativo | Hospeda seu aplicativo web bot. | Não aplicável |
| Serviço de aplicativo | Hospeda seu aplicativo de bot. | Adiciona a identidade atribuída pelo usuário para acessar outros recursos do Azure. |
| Gerenciar identidade | Autenticar solicitações de serviço a serviço do Azure. | Compartilhamentos entre recursos e recursos diferentes. |

</details>
<br>

<details>
<summary><b>Criação de recursos para o bot de notificação do Teams com o gatilho HTTP (servidor de API Web)</b></summary>

| Resource | Objetivo | Descrição |
| --- | --- | --- |
| Bot do Azure | Registra seu aplicativo como um bot com a estrutura do bot. | Conecta o bot ao Teams. |
| Plano do serviço de aplicativo | Hospeda seu aplicativo web bot. | Não aplicável |
| Serviço de aplicativo | Hospede seu aplicativo de bot. | Adiciona a identidade atribuída pelo usuário para acessar outros recursos do Azure. |
| Identidade Gerenciada | Autenticar solicitações de serviço a serviço do Azure. | Compartilhamentos entre recursos e recursos diferentes. |

</details>
<br>

<details>
<summary><b>Criação de recursos para o bot de notificação do Teams com o aplicativo gatilho HTTP (função do Azure)</b></summary>

| Resource | Objetivo | Descrição |
| --- | --- | --- |
| Bot do Azure | Registra seu aplicativo como um bot com a estrutura do bot. | Conecta o bot ao Teams. |
| Gerenciar identidade | Autentica solicitações de serviço a serviço do Azure. | Compartilhado entre recursos e recursos diferentes. |
| Conta de armazenamento | Ajuda a criar um aplicativo de funções. | Não aplicável |
| Plano do serviço de aplicativo | Hospeda o aplicativo de bot de função. | Não aplicável |
| Aplicativo de funções | Hospeda seu aplicativo de bot. | - Adiciona a identidade atribuída pelo usuário para acessar outros recursos do Azure.<br>-Adiciona a regra CORS (compartilhamento de recursos entre origens) para permitir solicitações de seu aplicativo guia.<br>- Adiciona a configuração de autenticação que só permite solicitações do aplicativo Teams.<br>- Adiciona as configurações de aplicativo exigidas pelo SDK do TeamsFx. |

</details>
<br>

<details>
<summary><b>Criação de recursos para o bot de notificação do Teams com o aplicativo de gatilho de temporizador (função do Azure)</b></summary>

| Resource | Objetivo | Descrição |
| --- | --- | --- |
| Bot do Azure | Registra seu aplicativo como um bot com a estrutura do bot. | Conecta o bot ao Teams. |
| Gerenciar identidade | Autenticar solicitações de serviço a serviço do Azure. | Compartilhamentos entre recursos e recursos diferentes. |
| Conta de armazenamento | Ajuda a criar um aplicativo de funções. | Não aplicável. |
| Plano do serviço de aplicativo | Hospeda o aplicativo de bot de funções. | Não aplicável |
| Aplicativo de funções | Hospeda seu aplicativo de bot. | - Adiciona a identidade atribuída pelo usuário para acessar outros recursos do Azure.<br>-Adiciona a regra CORS (compartilhamento de recursos entre origens) para permitir solicitações de seu aplicativo guia.<br>- Adiciona a configuração de autenticação que só permite solicitações do aplicativo Teams.<br>- Adiciona as configurações de aplicativo exigidas pelo SDK do TeamsFx. |

</details>
<br>

<details>
<summary><b>Criação de recursos para o bot de notificação do Teams com gatilho HTTP + gatilho de temporizador (função do Azure)</b></summary>

| Resource | Objetivo | Descrição |
| --- | --- | --- |
| Bot do Azure | Registra seu aplicativo como um bot com a estrutura do bot. | Conecta o bot ao Teams. |
| Gerenciar identidade | Autenticar solicitações de serviço a serviço do Azure. | Compartilhamentos entre recursos e recursos diferentes. |
| Conta de armazenamento | Ajuda a criar um aplicativo de funções. | Não aplicável |
| Plano do serviço de aplicativo | Hospeda o aplicativo de bot de funções. | Não aplicável |
| Aplicativo de funções | Hospeda seu aplicativo de bot. | - Adiciona a identidade atribuída pelo usuário para acessar outros recursos do Azure.<br>-Adiciona a regra CORS (compartilhamento de recursos entre origens) para permitir solicitações de seu aplicativo guia.<br>- Adiciona a configuração de autenticação que só permite solicitações do aplicativo Teams.<br>- Adiciona as configurações de aplicativo exigidas pelo SDK do TeamsFx. |

</details>
<br>

### <a name="manage-your-resources"></a>Gerenciar seus recursos

Você pode entrar [no portal do Azure e](https://portal.azure.com/) gerenciar todos os recursos criados pelo Kit de Ferramentas do Teams.

* Você pode selecionar o grupo de recursos na lista existente ou no novo grupo de recursos que você criou.
* Você pode ver os detalhes do grupo de recursos selecionado na seção de visão geral da tabela de conteúdo.

## <a name="customize-resource-provision"></a>Personalizar o provisionamento de recursos

O Kit de Ferramentas do Teams permite que você use uma infraestrutura para a abordagem de código para definir os recursos do Azure que você deseja provisionar. Você pode alterar a configuração no Kit de Ferramentas do Teams de acordo com suas necessidades.

O Kit de Ferramentas do Teams usa o modelo arm para definir recursos do Azure. O modelo do ARM é um conjunto de arquivos bicep que define a infraestrutura e a configuração do seu projeto. É possível personalizar os recursos do Azure modificando o modelo do ARM. Para obter mais informações, confira este [documento bicep](/azure/azure-resource-manager/bicep).

O provisionamento com o ARM envolve a alteração dos seguintes conjuntos de arquivos, parâmetros e modelos:

* Arquivos de parâmetro ARM (`azure.parameters.{your_env_name}.json`) localizados na `.fx/configs` pasta, para passar parâmetros para modelos.
* Os arquivos de modelo do ARM localizados `templates/azure` na pasta contêm os seguintes arquivos:

| Arquivo | Função | Permitir personalização |
| --- | --- | --- |
| main.bicep | Forneça um ponto de entrada para o recurso do Azure. Disposição | Sim |
| provision.bicep | Criar e configurar recursos do Azure. | Sim |
| config.bicep | Adicione as configurações necessárias do TeamsFx aos recursos do Azure. | Sim |
| provision/xxx.bicep | Criar e configurar cada recurso do Azure consumido por `provision.bicep`. | Sim |
| teamsfx/xxx.bicep | Adicione as configurações necessárias do TeamsFx a cada recurso do Azure consumido por `config.bicep`.| Não |

> [!NOTE]
> Depois de adicionar recursos ou recursos ao seu projeto, ele `teamsfx/xxx.bicep` será regenerado. Para modificar os arquivos bicep, você pode usar o Git para controlar suas alterações nos `teamsfx/xxx.bicep` arquivos. Isso não faz você perder nenhuma alteração ao adicionar recursos ou recursos ao seu projeto.

Os arquivos de modelo do ARM usam espaços reservados para parâmetros. A finalidade dos espaços reservados é garantir que novos recursos possam ser criados no novo ambiente. Os valores reais são resolvidos do `.fx/states/state.{env}.json` arquivo.

### <a name="azure-ad-application-related-parameters"></a>Azure AD parâmetros relacionados ao aplicativo

| Nome do parâmetro | Espaço reservado para valor padrão | Significado do espaço reservado | Como personalizar |
| --- | --- | --- | --- |
| Microsoft 365 ClientId | {{state.fx-resource-aad-app-for-teams.clientId}} | A ID do cliente Azure AD aplicativo criada durante o provisionamento. | [Usar um aplicativo Azure AD existente para seu aplicativo Teams](#use-an-existing-azure-ad-app-for-your-teams-app) |
| Microsoft 365 ClientSecret | {{state.fx-resource-aad-app-for-teams.clientSecret}} | O segredo do cliente Azure AD aplicativo criado durante o provisionamento. | [Usar um aplicativo Azure AD existente para seu aplicativo Teams](#use-an-existing-azure-ad-app-for-your-teams-app)  |
| Microsoft 365 TenantId | {{state.fx-resource-aad-app-for-teams.tenantId}} | ID do locatário do aplicativo Azure AD aplicativo. | [Usar um aplicativo Azure AD existente para seu aplicativo Teams](#use-an-existing-azure-ad-app-for-your-teams-app)  |
| Microsoft 365 OAuthAuthorityHost | {{state.fx-resource-aad-app-for-teams.oauthHost}} | Host de autoridade OAuth do aplicativo Azure AD aplicativo. | [Usar um aplicativo Azure AD existente para seu aplicativo Teams](#use-an-existing-azure-ad-app-for-your-teams-app) |
| botAadAppClientId | {{state.fx-resource-bot.botId}} | A ID do Azure AD do bot criada durante o provisionamento. | [Usar um aplicativo Azure AD existente para seu bot](#use-an-existing-azure-ad-app-for-your-bot) |
| botAadAppClientSecret | {{state.fx-resource-bot.botPassword}} | O segredo do cliente Azure AD aplicativo criado durante o provisionamento. | [Usar um aplicativo Azure AD existente para seu bot](#use-an-existing-azure-ad-app-for-your-bot) |

### <a name="reference-environment-variables-in-parameter-files"></a>Referenciar variáveis de ambiente em arquivos de parâmetro

Quando o valor é secreto, você não precisa embuti-los em código no arquivo de parâmetro. Os arquivos de parâmetro dão suporte à referência aos valores de variáveis de ambiente. Você pode usar essa sintaxe nos valores `{{$env.YOUR_ENV_VARIABLE_NAME}}` de parâmetro do Kit de Ferramentas do Teams para resolver da variável de ambiente atual.

O exemplo a seguir lê o valor do `mySelfHostedDbConnectionString` parâmetro da variável de ambiente `DB_CONNECTION_STRING`:

```json
...
    "mySelfHostedDbConnectionString": "{{$env.DB_CONNECTION_STRING}}"
...
```

### <a name="customize-arm-template-files"></a>Personalizar arquivos de modelo do ARM

Se os modelos predefinidos não atenderem às suas necessidades de aplicativo, você poderá personalizar os modelos do ARM na `templates/azure` pasta. Por exemplo, você pode personalizar o modelo do ARM para criar alguns recursos extras do Azure para seu aplicativo. É necessário ter conhecimento básico da linguagem bicep, que é usada para criar um modelo do ARM.

Para garantir que a ferramenta TeamsFx funcione corretamente, personalize o modelo do ARM, que atenda ao seguinte requisito:

* Verifique se a estrutura da pasta e o nome do arquivo permanecem inalterados. A ferramenta pode acrescentar novo conteúdo aos arquivos existentes quando você adiciona mais recursos ou funcionalidades ao seu projeto.
* Verifique se o nome dos parâmetros gerados automaticamente e seus nomes de propriedade permanecem invariáveis. Os parâmetros gerados automaticamente podem ser usados quando você adiciona mais recursos ou funcionalidades ao seu projeto.
* Verifique se a saída do modelo do ARM gerado automaticamente também não foi alterada. Você pode adicionar mais saídas ao modelo do ARM. A saída é `.fx/states/state.{env}.json` e pode ser usada em outros recursos, como implantar e validar o arquivo de manifesto.

### <a name="customize-teams-app"></a>Personalizar o aplicativo Teams

Você pode personalizar seu bot ou o aplicativo Teams adicionando snippets de configuração para usar um Azure AD aplicativo criado por você. Você pode executar das seguintes maneiras:

#### <a name="use-an-existing-azure-ad-app-for-your-bot"></a>Usar um aplicativo Azure AD existente para seu bot

Você pode adicionar o snippet `.fx/configs/config.{env}.json` de configuração a seguir para usar Azure AD aplicativo criado por você para seu aplicativo teams. Para criar um Azure AD, siga o link<https://aka.ms/teamsfx-existing-aad-doc>.

```json
"auth": {
    "clientId": "<your Azure AD app client id>",
    "clientSecret": "{{$env.ENV_NAME_THAT_STORES_YOUR_SECRET}}",
    "objectId": "<your Azure AD app object id>",
    "accessAsUserScopeId": "<id of the access_as_user scope>"
}
```

Depois de adicionar o snippet, adicione o segredo do cliente à variável de ambiente relacionada para que o Kit de Ferramentas do Teams possa resolver o segredo real do cliente durante o provisionamento.

> [!NOTE]
> Certifique-se de não compartilhar o mesmo aplicativo Azure AD em vários ambientes. Se você não tiver permissão para atualizar o aplicativo Azure AD, receberá um aviso com instruções para atualizar manualmente o Azure AD aplicativo. Siga estas instruções para atualizar seu aplicativo Azure AD após o provisionamento.

#### <a name="use-an-existing-azure-ad-app-for-your-teams-app"></a>Usar um aplicativo Azure AD existente para seu aplicativo Teams

Você pode adicionar o seguinte snippet de configuração `.fx/configs/config.{env}.json` para usar o Azure AD aplicativo criado para o bot:

```json
"bot": {
    "appId": "<your Azure AD app client id>",
    "appPassword": "{{$env.ENV_NAME_THAT_STORES_YOUR_SECRET}}"
}
```

Depois de adicionar o snippet, adicione o segredo do cliente à variável de ambiente relacionada para o Kit de Ferramentas do Teams para resolver o segredo real do cliente durante o provisionamento.

#### <a name="skip-adding-user-for-sql-database"></a>Ignorar a adição de usuário para o banco de dados SQL

Se você receber um erro de permissão insuficiente quando o Kit de Ferramentas do Teams tentar adicionar o usuário ao banco de dados SQL, poderá adicionar o seguinte snippet `.fx/configs/config.{env}.json` de configuração para ignorar a adição do usuário do banco de dados SQL:

```json
"skipAddingSqlUser": true
```

::: zone-end

## <a name="see-also"></a>Confira também

* [Implantar o aplicativo Teams na nuvem](deploy.md)
* [Gerenciar vários ambientes](TeamsFx-multi-env.md)
* [Colaborar com outros desenvolvedores no projeto do Teams](TeamsFx-collaboration.md)
* [Implantar o aplicativo Teams na nuvem usando o Visual Studio](deploy-teams-app.md)
* [Editar manifesto do aplicativo Teams usando o Visual Studio](VS-TeamsFx-preview-and-customize-app-manifest.md)
* [Depurar o aplicativo Teams localmente para o Visual Studio](debug-teams-app-visual-studio.md)
