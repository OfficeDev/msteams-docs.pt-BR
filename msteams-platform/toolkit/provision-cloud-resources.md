---
title: Usar o Kit de Ferramentas do Teams para provisionar recursos de nuvem usando o Kit de Ferramentas do Teams para Visual Studio
author: surbhigupta
description: Neste módulo, saiba como provisionar recursos de nuvem usando o Kit de Ferramentas do Teams. Também para criar recursos e personalizar o provisionamento de recursos no Visual Studio
ms.author: v-amprasad
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 00e021e3e42eed6eeb5881d258a9884a7e579377
ms.sourcegitcommit: 65ae3ccc2312ddc6cdaa05096e30bdf9dca10c3f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68027428"
---
# <a name="provision-cloud-resources-using-visual-studio"></a>Provisionar recursos de nuvem usando o Visual Studio

O TeamsFx integra-se ao Azure e à nuvem do Microsoft 365 que permite colocar seu aplicativo no Azure com um único comando. O TeamsFx integra-se ao Azure Resource Manager que permite provisionar recursos do Azure. Para a abordagem de código, seu aplicativo precisa dos recursos de nuvem.

## <a name="prerequisites"></a>Pré-requisitos

Aqui está uma lista de ferramentas necessárias para provisionar seus recursos de nuvem:

| &nbsp; | Instalar | Para usar... |
| --- | --- | --- |
| &nbsp; | **Required** | &nbsp; |
| &nbsp; | Visual Studio 2022 versão 17.3 | Você pode instalar a edição enterprise do Visual Studio e instalar a carga de trabalho "ASP.NET" e as Ferramentas de Desenvolvimento do Microsoft Teams. |
| &nbsp; | [Conta de desenvolvedor do Microsoft 365](https://developer.microsoft.com/en-us/microsoft-365/dev-program) | Acesso à conta do Teams com as permissões apropriadas para instalar um aplicativo. |
| &nbsp; | [Microsoft Teams](https://www.microsoft.com/microsoft-teams/download-app) | O Microsoft Teams para colaborar com todos com quem você trabalha por meio de aplicativos para chats, reuniões, chamadas - tudo em um só lugar. |
| &nbsp; | Kit de ferramentas do Teams | Uma extensão do Visual Studio que cria um scaffolding de projeto para seu aplicativo. Use a versão mais recente. |
| &nbsp; | [Conta do Azure](https://portal.azure.com/) | Conta do Azure com uma assinatura válida. |

## <a name="steps-to-provision-cloud-resources"></a>Etapas para provisionar recursos de nuvem

As etapas a seguir ajudam você a provisionar recursos de nuvem usando o Visual Studio:

### <a name="sign-in-to-your-microsoft-365-account"></a>Entre em sua conta do Microsoft 365

1. Visual Studio 2022.
2. Abra o projeto de aplicativo do Microsoft Teams.
3. Selecione **Projeto**.
4. Selecione **o Kit de Ferramentas do Teams**.
5. Selecione **Preparar Dependências de Aplicativos do Teams**.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Provision-cloud-resources-in-TTK-VS/teams-toolkit-vs-prepare-app-dependencies.png" alt-text="Preparar as dependências do aplicativo teams":::

7. Selecione **Entrar...** para entrar em sua conta do Azure.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Provision-cloud-resources-in-TTK-VS/teams-toolkit-vs-prepare1.png" alt-text="Entrar no Microsoft 365":::

    > [!NOTE]
    > Se você já estiver conectado, seu nome de usuário será exibido ou poderá selecionar o mesmo para alternar sua conta.

8. O navegador da Web padrão é aberto para permitir [que você entre](https://developer.microsoft.com/en-us/microsoft-365/dev-program) na conta.
9. Selecione **Continuar** depois de entrar em sua conta.

    :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Provision-cloud-resources-in-TTK-VS/teams-toolkit-vs-signin-M365.png" alt-text="Confirme selecionando continuar":::

### <a name="sign-in-to-your-azure-account"></a>Entrar em sua conta do Azure

1. Abra o Visual Studio 2022.
2. Abra o projeto de aplicativo do Teams.
3. Selecione **Projeto**.
4. Selecione **o Kit de Ferramentas do Teams**.
5. Selecione **Provisionar na nuvem**.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Provision-cloud-resources-in-TTK-VS/teams-toolkit-vs-provision-in-cloud.png" alt-text="Entrar na conta do Azure":::

6. Selecione **Entrar...** para entrar em sua conta do Azure.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Provision-cloud-resources-in-TTK-VS/teams-toolkit-vs-provision-start.png" alt-text="Entrar em sua conta do Azure":::

   > [!NOTE]
   > Se você já estiver conectado, seu nome de usuário será exibido ou você terá a opção de mudar de conta.

7. Entre na conta do Azure usando suas credenciais. O navegador é fechado automaticamente.

### <a name="to-provision-cloud-resources"></a>Para provisionar recursos de nuvem

1. Depois de abrir seu projeto no Visual Studio, selecione **Projeto**
2. Selecionar **o Kit de Ferramentas do Teams**
3. Selecione **Provisionar na nuvem**.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Provision-cloud-resources-in-TTK-VS/teams-toolkit-vs-provision-in-cloud1.png" alt-text="Provisionar na nuvem":::

4. Na caixa **de diálogo Provisionar** , você pode ver uma lista de todas as assinaturas em sua conta do Azure.
5. Você pode selecionar ou criar um novo **grupo de recursos**.
6. Selecione **Provisionar**.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Provision-cloud-resources-in-TTK-VS/teams-toolkit-vs-provision-select-subscription1.png" alt-text="Selecionar grupo de recursos":::

7. A caixa de diálogo avisa que os encargos podem ser adicionados de acordo com o uso do Azure. Selecione **Provisionar**.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Provision-cloud-resources-in-TTK-VS/teams-toolkit-vs-provision-warning.png" alt-text="Aviso de provisionamento":::

   O processo de provisionamento da criação dos recursos na nuvem do Azure pode levar algum tempo.

8. Verifique a janela de saída do Kit de Ferramentas do Teams para monitorar o progresso.
9. Você será solicitado após a conclusão do provisionamento. Selecione **Exibir Recursos Provisionados** para exibir todos os recursos que foram provisionados.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Provision-cloud-resources-in-TTK-VS/teams-toolkit-vs-provision-provision-success.png" alt-text="Exibir recursos provisionados":::

### <a name="create-resources"></a>Criar recursos

Ao disparar o comando provisionar no Teams Toolkit ou na CLI do TeamsFx, você pode criar os seguintes recursos:

* Microsoft Azure Active Directory (Azure AD) em seu locatário do Microsoft 365.
* Registro de aplicativo do Teams na plataforma do Teams do locatário do Microsoft 365.
* Recursos do Azure em sua assinatura do Azure selecionada.

Ao criar um novo projeto, você também precisa criar recursos do Azure. Os modelos do ARM (Azure Resource Manager) definem todos os recursos do Azure e ajudam você a criar os recursos necessários do Azure durante o provisionamento.

### <a name="create-resource-for-teams-tab-application"></a>Criar recurso para o aplicativo de guia do Teams

| Resource | Objetivo | Descrição |
| --- | --- | --- |
| Plano do serviço de aplicativo | Hospeda seu aplicativo Web da guia. | Não aplicável |
| Serviço de aplicativo | Hospeda o aplicativo da guia Blazor e o servidor de autenticação simples que ajuda a obter acesso a outros serviços. | Adiciona a identidade atribuída pelo usuário para acessar outros recursos do Azure. |
| Gerenciar identidade | Autenticar solicitações de serviço a serviço do Azure. | Compartilhamentos entre recursos e recursos diferentes. |

### <a name="create-resources-for-teams-message-extension-application"></a>Criar recursos para o aplicativo de extensão de mensagem do Teams

| Resource | Objetivo | Descrição |
| --- | --- | --- |
| Bot do Azure | Registra seu aplicativo como um bot com a estrutura do bot. | Conecta o bot ao Teams. |
| Serviço de Aplicativo plano | Hospeda seu aplicativo web bot. | Não aplicável |
| Serviço de Aplicativo | Hospeda seu aplicativo de bot. | Adiciona a identidade atribuída pelo usuário para acessar outros recursos do Azure. |
| Gerenciar identidade | Autenticar solicitações de serviço a serviço do Azure. | Compartilhamentos entre recursos e recursos diferentes. |

### <a name="create-resources-for-teams-command-bot-application"></a>Criar recursos para o aplicativo de bot de comando do Teams

| Resource | Objetivo | Descrição |
| --- | --- | --- |
| Bot do Azure | Registra seu aplicativo como um bot com a estrutura do bot. | Conecta o bot ao Teams. |
| Plano do serviço de aplicativo | Hospeda seu aplicativo web bot. | Não aplicável |
| Serviço de aplicativo | Hospeda seu aplicativo de bot. | Adiciona a identidade atribuída pelo usuário para acessar outros recursos do Azure. |
| Gerenciar identidade | Autenticar solicitações de serviço a serviço do Azure. | Compartilhamentos entre recursos e recursos diferentes. |

### <a name="create-resources-for-teams-notification-bot-with-http-trigger-web-api-server-application"></a>Criar recursos para o bot de notificação do Teams com o gatilho HTTP (servidor de API Web)

| Resource | Objetivo | Descrição |
| --- | --- | --- |
| Bot do Azure | Registra seu aplicativo como um bot com a estrutura do bot. | Conecta o bot ao Teams. |
| Plano do serviço de aplicativo | Hospeda seu aplicativo web bot. | Não aplicável |
| Serviço de aplicativo | Hospede seu aplicativo de bot. | Adiciona a identidade atribuída pelo usuário para acessar outros recursos do Azure. |
| Identidade Gerenciada | Autenticar solicitações de serviço a serviço do Azure. | Compartilhamentos entre recursos e recursos diferentes. |

### <a name="create-resource-for-teams-notification-bot-with-http-trigger-azure-function-application"></a>Criar recurso para o bot de notificação do Teams com o aplicativo gatilho HTTP (função do Azure)

| Resource | Objetivo | Descrição |
| --- | --- | --- |
| Bot do Azure | Registra seu aplicativo como um bot com a estrutura do bot. | Conecta o bot ao Teams. |
| Gerenciar identidade | Autentica solicitações de serviço a serviço do Azure. | Compartilhado entre recursos e recursos diferentes. |
| Conta de armazenamento | Ajuda a criar um aplicativo de funções. | Não aplicável |
| Plano do serviço de aplicativo | Hospeda o aplicativo de bot de função. | Não aplicável |
| Aplicativo de funções | Hospeda seu aplicativo de bot. | - Adiciona a identidade atribuída pelo usuário para acessar outros recursos do Azure.<br>-Adiciona a regra CORS (compartilhamento de recursos entre origens) para permitir solicitações de seu aplicativo guia.<br>- Adiciona a configuração de autenticação que só permite solicitações do aplicativo Teams.<br>- Adiciona as configurações de aplicativo exigidas pelo SDK do TeamsFx. |

### <a name="create-resource-for-teams-notification-bot-with-timer-trigger-azure-function-application"></a>Criar recurso para o bot de notificação do Teams com o aplicativo de gatilho de temporizador (função do Azure)

| Resource | Objetivo | Descrição |
| --- | --- | --- |
| Bot do Azure | Registra seu aplicativo como um bot com a estrutura do bot. | Conecta o bot ao Teams. |
| Gerenciar identidade | Autenticar solicitações de serviço a serviço do Azure. | Compartilhamentos entre recursos e recursos diferentes. |
| Conta de armazenamento | Ajuda a criar um aplicativo de funções. | Não aplicável. |
| Plano do serviço de aplicativo | Hospeda o aplicativo de bot de funções. | Não aplicável |
| Aplicativo de funções | Hospeda seu aplicativo de bot. | - Adiciona a identidade atribuída pelo usuário para acessar outros recursos do Azure.<br>-Adiciona a regra CORS (compartilhamento de recursos entre origens) para permitir solicitações de seu aplicativo guia.<br>- Adiciona a configuração de autenticação que só permite solicitações do aplicativo Teams.<br>- Adiciona as configurações de aplicativo exigidas pelo SDK do TeamsFx. |

### <a name="create-resources-for-teams-notification-bot-with-http-trigger--timer-trigger-azure-function-application"></a>Criar recursos para o bot de notificação do Teams com gatilho HTTP + gatilho de temporizador (função do Azure)

| Resource | Objetivo | Descrição |
| --- | --- | --- |
| Bot do Azure | Registra seu aplicativo como um bot com a estrutura do bot. | Conecta o bot ao Teams. |
| Gerenciar identidade | Autenticar solicitações de serviço a serviço do Azure. | Compartilhamentos entre recursos e recursos diferentes. |
| Conta de armazenamento | Ajuda a criar um aplicativo de funções. | Não aplicável |
| Plano do serviço de aplicativo | Hospeda o aplicativo de bot de funções. | Não aplicável |
| Aplicativo de funções | Hospeda seu aplicativo de bot. | - Adiciona a identidade atribuída pelo usuário para acessar outros recursos do Azure.<br>-Adiciona a regra CORS (compartilhamento de recursos entre origens) para permitir solicitações de seu aplicativo guia.<br>- Adiciona a configuração de autenticação que só permite solicitações do aplicativo Teams.<br>- Adiciona as configurações de aplicativo exigidas pelo SDK do TeamsFx. |

### <a name="manage-your-resources"></a>Gerenciar seus recursos

Você pode entrar [no portal do Azure e](https://portal.azure.com/) gerenciar todos os recursos criados pelo Kit de Ferramentas do Teams.

* Você pode selecionar o grupo de recursos na lista existente ou no novo grupo de recursos que você criou.
* Você pode ver os detalhes do grupo de recursos selecionado na seção de visão geral da tabela de conteúdo.

### <a name="customize-resource-provision"></a>Personalizar o provisionamento de recursos

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
| Microsoft 365 ClientId | {{state.fx-resource-aad-app-for-teams.clientId}} | A ID do cliente Azure AD aplicativo criada durante o provisionamento. | [Personalizar o valor](#use-an-existing-azure-ad-app-for-your-teams-app) |
| Microsoft 365 ClientSecret | {{state.fx-resource-aad-app-for-teams.clientSecret}} | O segredo do cliente Azure AD aplicativo criado durante o provisionamento. | [Personalizar o valor](#use-an-existing-azure-ad-app-for-your-teams-app)  |
| Microsoft 365 TenantId | {{state.fx-resource-aad-app-for-teams.tenantId}} | ID do locatário do aplicativo Azure AD aplicativo. | [Personalizar o valor](#use-an-existing-azure-ad-app-for-your-teams-app)  |
| Microsoft 365 OAuthAuthorityHost | {{state.fx-resource-aad-app-for-teams.oauthHost}} | Host de autoridade OAuth do aplicativo Azure AD aplicativo. | [Personalizar o valor](#use-an-existing-azure-ad-app-for-your-teams-app) |
| botAadAppClientId | {{state.fx-resource-bot.botId}} | A ID do Azure AD do bot criada durante o provisionamento. | [Personalizar o valor](#use-an-existing-azure-ad-app-for-your-bot) |
| botAadAppClientSecret | {{state.fx-resource-bot.botPassword}} | O segredo do cliente Azure AD aplicativo criado durante o provisionamento. | [Personalizar o valor](#use-an-existing-azure-ad-app-for-your-bot) |

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

## <a name="see-also"></a>Confira também

* [Implantar o aplicativo Teams na nuvem usando o Visual Studio](deploy-teams-app.md)
* [Editar manifesto do aplicativo Teams usando o Visual Studio](VS-TeamsFx-preview-and-customize-app-manifest.md)
* [Depurar o aplicativo Teams localmente para o Visual Studio](debug-teams-app-visual-studio.md)
