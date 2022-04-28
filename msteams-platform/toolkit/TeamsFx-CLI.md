---
title: Interface de linha de comando do TeamsFx
author: MuyangAmigo
description: Descreve a interface de linha de comando do TeamsFx
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 5fde7e94c198bfe76810a52ede78d0be7270ba0c
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65104515"
---
# <a name="teamsfx-library"></a>Biblioteca TeamsFx

Microsoft Teams Framework (TeamsFx) é uma biblioteca que encapsula padrões comuns de integração e funcionalidade (como acesso simplificado ao Microsoft Identity). Você pode criar aplicativos para Microsoft Teams sem configuração.

Aqui está uma lista dos principais recursos do TeamsFx:

* **Colaboração do TeamsFx**: permitir que os desenvolvedores e o proprietário do projeto convidem outros colaboradores para o projeto TeamsFx. Você pode colaborar para depurar e implantar um projeto do TeamsFx.

* **CLI do TeamsFx**: acelera o Teams de aplicativos. Ele também habilita o cenário de CI/CD em que você pode integrar a CLI em scripts para automação.

* **SDK do TeamsFx: O SDK** (Kit de Desenvolvimento de Software) do TeamsFx é a principal biblioteca de códigos do TeamsFx encapsulando a autenticação simples para o cliente e o código do lado do servidor personalizado para Teams desenvolvedores.

## <a name="teamsfx-command-line-interface"></a>Interface de linha de comando do TeamsFx

A CLI do TeamsFx é uma interface de linha de comando baseada em texto que acelera Teams desenvolvimento de aplicativos. Ele tem como objetivo fornecer experiência centrada no teclado durante a criação de Teams aplicativos. Ele também habilita o cenário de CI/CD em que você pode integrar a CLI em scripts para automação.

Para saber mais, confira:

* [Código-fonte](https://github.com/OfficeDev/TeamsFx/tree/dev/packages/cli)
* [Pacote (NPM)](https://www.npmjs.com/package/@microsoft/teamsfx-cli)

## <a name="get-started"></a>Introdução

Instale `teamsfx-cli` e `npm` execute para `teamsfx -h` verificar todos os comandos disponíveis:

```bash
  npm install -g @microsoft/teamsfx-cli
  teamsfx -h
```

## <a name="supported-commands"></a>Comandos com suporte

| Comando | Descrição |
|----------------|-------------|
| `teamsfx new`| Crie um novo Teams aplicativo.|
| `teamsfx account`| Gerenciar contas de serviço de nuvem. Os serviços de nuvem com suporte são "Azure" e "Microsoft 365". |
| `teamsfx env` | Gerenciar ambientes. |
| `teamsfx capability`| Adicione novos recursos ao aplicativo atual.|
| `teamsfx resource`  | Gerencie os recursos no aplicativo atual.|
| `teamsfx provision` | Provisione recursos de nuvem no aplicativo atual.|
| `teamsfx deploy` | Implante o aplicativo atual.  |
| `teamsfx package` | Crie seu Teams aplicativo em pacote para publicação.|
| `teamsfx validate` | Valide o aplicativo atual.|
| `teamsfx publish` | Publique o aplicativo no Teams.|
| `teamsfx preview` | Visualize o aplicativo atual. |
| `teamsfx config`  | Gerencie os dados de configuração. |
| `teamsfx permission`| Colabore com outros desenvolvedores no mesmo projeto.|

## `teamsfx new`

Por padrão, `teamsfx new` entra no modo interativo e orienta você pelo processo de criação de um novo Teams aplicativo. Você também pode trabalhar com o modo não interativo definindo o `--interactive` sinalizador como `false`.

| `teamsFx new` Comando | Descrição |
|:----------------  |:-------------|
| `teamsfx new template <template-name>`     | Criar um aplicativo com base em um modelo existente |
| `teamsfx new template list`     | Listar todos os modelos disponíveis |

### <a name="parameters-for-teamsfx-new"></a>Parâmetros para `teamsfx new`

| Parâmetro | Requisito | Descrição |
|:---------------- |:-------------|:-------------|
|`--app-name` | Sim| Nome do seu Teams aplicativo.|
|`--interactive`| Não | Selecione as opções interativamente. As opções são `true` e o `false` valor padrão é `true`.|
|`--capabilities`| Não| Escolha Teams recursos do aplicativo, as várias opções `tab`são , `bot`e `messaging-extension` `tab-spfx`. O valor padrão é `tab`.|
|`--programming-language`| Não| Linguagem de programação para o projeto. As opções são ou `javascript` e `typescript` o valor padrão é `javascript`.|
|`--folder`| Não | Project diretório. Uma subpasta com o nome do aplicativo é criada nesse diretório. O valor padrão é `./`.|
|`--spfx-framework-type`| Não| Aplicável se `Tab(SPfx)` a funcionalidade estiver selecionada. Estrutura de front-end. As opções são `none` e `react`, e o valor padrão é `none`.|
|`--spfx-web part-name`| Não | Aplicável se `Tab(SPfx)` a funcionalidade estiver selecionada. O valor padrão é "helloworld".|
|`--spfx-web part-desp`| Não | Aplicável se `Tab(SPfx)` a funcionalidade estiver selecionada. O valor padrão é "helloworld description". |
|`--azure-resources`| Não| Aplicável se contiver `tab` funcionalidade. Adicione recursos do Azure ao seu projeto. As várias opções são `sql` (Banco de Dados SQL do Azure) e `function` (Azure Functions). |

### <a name="scenarios-for-teamsfx-new"></a>Cenários para `teamsfx new`

Você pode usar o modo interativo para criar um Teams aplicativo. Os cenários para controlar todos os parâmetros são `teamsfx new` os seguintes:

#### <a name="tab-app-hosted-on-spfx-using-react"></a>Aplicativo tab hospedado no SPFx usando React

```bash
teamsfx new --interactive false --app-name newspfxapp --capabilities tab-spfx --spfx-framework-type react
```

#### <a name="teams-app-in-javascript-with-tab-bot-capabilities-and-azure-functions"></a>Teams aplicativo em JavaScript com guias, recursos de bot e Azure Functions

```bash
teamsfx new --interactive false --app-name newtabbotapp --capabilities tab bot --programming-language javascript --azure-resources function
```

#### <a name="teams-tab-app-with-azure-functions-and-azure-sql"></a>Teams aplicativo guia com Azure Functions e SQL do Azure

```bash
teamsfx new --interactive false app-name newapp --azure-resources sql function --programming-language typescript
```

## `teamsfx account`

Gerenciar contas de serviço de nuvem. Os serviços de nuvem com suporte são `Azure` e `Microsoft 365`.

| `teamsFx account` Comando | Descrição |
|:----------------  |:-------------|
| `teamsfx account login <service>`  | Faça logon no serviço de nuvem selecionado. |
| `teamsfx account logout <service>`  | fazer logo out do serviço de nuvem selecionado. |
| `teamsfx account set --subscription` | Atualize as configurações da conta para definir uma ID de assinatura. |

## `teamsfx env`

Gerencie os ambientes.

| `teamsfx env` Comando  | Descrição |
|:----------------  |:-------------|
| `teamsfx env add <new_env_name> --env <existing_env_name>` | Adicione um novo ambiente copiando do ambiente especificado. |
| `teamsfx env list` | Listar todos os ambientes. |

### <a name="scenarios-for-teamsfx-env"></a>Cenários para `teamsfx env`

Os cenários são `teamsfx env` os seguintes:

#### <a name="create-a-new-environment"></a>Criar um novo ambiente

Adicione um novo ambiente copiando do ambiente de desenvolvimento existente:

```bash
teamsfx env add staging --env dev
```

## `teamsfx capability`

Adicione novos recursos ao aplicativo atual.

| `teamsFx capability` Comando  | Descrição |
|:----------------  |:-------------|
| `teamsfx capability add tab` | Adicionar guia |
| `teamsfx capability add bot` | Adicionar bot |
| `teamsfx capability add messaging-extension`| Adicionar extensão de mensagens |

> [!NOTE]
> Se o projeto incluir um bot, a extensão de mensagem não poderá ser adicionada e ela será aplicada vice-versa. Você pode incluir extensões de bot e de mensagem em seu projeto ao criar um novo projeto Teams aplicativo.

## `teamsfx resource`

Gerencie os recursos no aplicativo atual. Os suportes `<resource-type>` são: `azure-sql`e `azure-apim` `azure-function` .

| `teamsFx resource` Comando  | Descrição |
|:----------------  |:-------------|
| `teamsfx resource add <resource-type>`      | Adicionar recurso ao aplicativo atual.|
| `teamsfx resource show <resource-type>`      | Mostrar detalhes de configuração do recurso. |
| `teamsfx resource list`      | Liste todos os recursos no aplicativo atual. |

### <a name="parameters-for-teamsfx-resource-add-azure-function"></a>Parâmetros para `teamsfx resource add azure-function`

| Parâmetro  | Requisito | Descrição |
|----------------  |-------------|-------------|
|`--function-name`| Sim | Forneça um nome de função. O valor padrão é `getuserprofile`. |

### <a name="parameters-for-teamsfx-resource-add-azure-sql"></a>Parâmetros para `teamsfx resource add azure-sql`

#### `--function-name`

| Parâmetro  | Requisito | Descrição |
|:----------------  |:-------------|:-------------|
|`--function-name`| Sim | Forneça um nome de função. O valor padrão é `getuserprofile`. |

> [!NOTE]
> O nome da função é verificado como SQL e precisa ser acessado da carga de trabalho do servidor. Se o projeto não contiver `Azure Functions`, crie um para você.

### <a name="parameters-for-teamsfx-resource-add-azure-apim"></a>Parâmetros para `teamsfx resource add azure-apim`

> [!TIP]
> As opções entram em vigor quando você tenta usar uma instância `APIM` existente. Por padrão, você não precisa especificar nenhuma opção e ela cria uma nova instância durante a `teamsfx provision` etapa.

| Parâmetro  | Requisito | Descrição |
|:----------------  |:-------------|:-------------|
|`--subscription`| Sim | Selecionar uma assinatura do Azure|
|`--apim-resource-group`| Sim| O nome do grupo de recursos. |
|`--apim-service-name`| Sim | O nome da instância do serviço de gerenciamento de API. |
|`--function-name`| Sim | Forneça um nome de função. O valor padrão é `getuserprofile`. |

> [!NOTE]
> `Azure API Management` precisa trabalhar com `Azure Functions`. Se o projeto não contiver `Azure Functions`, você poderá criar um.

## `teamsfx provision`

Provisione os recursos de nuvem no aplicativo atual.

### <a name="parameters-for-teamsfx-provision"></a>Parâmetros para `teamsfx provision`

| Parâmetro  | Requisito | Descrição |
|:----------------  |:-------------|:-------------|
|`--env`| Sim| Selecione um ambiente para o projeto. |
|`--subscription`| Não | Especifique uma ID de Assinatura do Azure. |
|`--resource-group`| Não | Defina o nome de um grupo de recursos existente. |
|`--sql-admin-name`| Não | Aplicável quando há SQL recurso no projeto. Nome do administrador SQL.|
|`--sql-password`| Não| Aplicável quando há SQL recurso no projeto. Senha de administrador do SQL.|

## `teamsfx deploy`

Esse comando é usado para implantar o aplicativo atual. Por padrão, ele implanta todo o projeto, mas também é possível implantar parcialmente. As várias opções são `frontend-hosting`, `function``apim`, `teamsbot`e `spfx`.

### <a name="parameters-for-teamsfx-deploy"></a>Parâmetros para `teamsfx deploy`

| Parâmetro  | Requisito | Descrição |
|:----------------  |:-------------|:-------------|
|`--env`| Sim| Selecione um ambiente existente para o projeto. |
|`--open-api-document`| Não | Aplicável quando há recurso de APIM no projeto. O caminho do arquivo de documento de API aberto. |
|`--api-prefix`| Não | Aplicável quando há recurso de APIM no projeto. O prefixo do nome da API. O nome exclusivo padrão da API é `{api-prefix}-{resource-suffix}-{api-version}`. |
|`--api-version`| Não | Aplicável quando há recurso de APIM no projeto. A versão da API. |

## `teamsfx validate`

Valide o aplicativo atual. Esse comando valida o arquivo de manifesto do aplicativo.

### <a name="parameters-for-teamsfx-validate"></a>Parâmetros para `teamsfx validate`

`--env`: selecione um ambiente existente para o projeto.

## `teamsfx publish`

Publique o aplicativo no Teams.

### <a name="parameters-for-teamsfx-publish"></a>Parâmetros para `teamsfx publish`

`--env`: selecione um ambiente existente para o projeto.

## `teamsfx package`

Crie seu Teams aplicativo em um pacote para publicação.

## `teamsfx preview`

Visualize o aplicativo atual do local ou remoto.

### <a name="parameters-for-teamsfx-preview"></a>Parâmetros para `teamsfx preview`

| Parâmetro  | Requisito | Descrição |
|:----------------  |:-------------|:-------------|
|`--local`| Não | Visualize o aplicativo do local. `--local` é exclusivo com `--remote`. |
|`--remote`| Não | Visualize o aplicativo do modo remoto. `--remote` é exclusivo com `--local`. |
|`--env`| Não | Selecione um ambiente existente para o projeto quando o `--remote` parâmetro for acrescentado. |
|`--folder`| Não | Project diretório raiz. O valor padrão é `./`. |
|`--browser`| Não | O navegador a ser aberto Teams cliente Web. As opções são `chrome`, e `edge` como `default` o navegador padrão do sistema e o valor é `default`. |
|`--browser-arg`| Não | O argumento a ser passado para o navegador, requer --browser, pode ser usado várias vezes, por exemplo, --browser-args="--guest" |
|`--sharepoint-site`| Não | SharePoint URL do site, como para `{your-tenant-name}.sharepoint.com` uma SPFx remota do projeto. |

### <a name="scenarios-for-teamsfx-preview"></a>Cenários para `teamsfx preview`

#### <a name="local-preview"></a>Visualização Local

Dependências:

* Node.js
* SDK do .NET
* Azure Functions Core Tools

```bash
teamsfx preview --local
teamsfx preview --local --browser chrome
```

#### <a name="remote-preview"></a>Visualização Remota

```bash
teamsfx preview --remote
teamsfx preview --remote --browser edge
```

> [!NOTE]
> Os logs dos serviços em segundo plano, como React são salvos em `~/.fx/cli-log/local-preview/`.

## `teamsfx config`

Gerencie os dados de configuração no escopo do usuário ou no escopo do projeto.

| `teamsfx config` Comando  | Descrição |
|:----------------  |:-------------|
| `teamsfx config get [option]` | Exibir o valor de configuração da opção |
| `teamsfx config set <option> <value>` | Atualizar o valor de configuração da opção |

### <a name="parameters-for-teamsfx-config"></a>Parâmetros para `teamsfx config`

| Parâmetro  | Requisito | Descrição |
|:----------------  |:-------------|:-------------|
|`--env`| Sim | Selecione um ambiente existente para o projeto. |
|`--folder`| Não | Project diretório. Isso é usado para obter ou definir a configuração do projeto. O valor padrão é `./`. |
|`--global`| Não | Lidar com a configuração. Se isso for verdadeiro, o escopo será limitado ao escopo do usuário em vez do escopo do projeto. O valor padrão é `false`. No momento, as configurações globais com suporte incluem `telemetry`, `validate-dotnet-sdk`, `validate-func-core-tools`, `validate-node`. |

### <a name="scenerios-for-teamsfx-config"></a>Scenerios para `teamsfx config`

Os segredos `.userdata` no arquivo são criptografados e `teamsfx config` podem ajudá-lo a exibir ou atualizar os valores.

#### <a name="stop-sending-telemetry-data"></a>Parar de enviar dados de telemetria

```bash
teamsfx config set telemetry off
```

#### <a name="disable-environment-checker"></a>Desabilitar o verificador de ambiente

Há três configurações para ativar ou desativar Node.js, o SDK do .NET e a validação do Azure Functions Core Tools, e todas elas são habilitadas por padrão. Você pode definir a configuração como "desativada" se não precisar da validação de dependências e quiser instalar as dependências por conta própria. Verifique os seguintes guias:

* [Node.js de instalação](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/vscode-extension/envchecker-help.md#how-to-install-nodejs)
* [Guia de instalação do SDK do .NET](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/vscode-extension/envchecker-help.md#how-to-install-net-sdk)
* [Azure Functions de instalação do Core Tools](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/vscode-extension/envchecker-help.md#how-to-install-azure-functions-core-tools).

Para desabilitar a validação do SDK do .NET, você pode usar o seguinte comando:

```bash
teamsfx config set validate-dotnet-sdk off
```

Para habilitar a validação do SDK do .NET, você pode usar o seguinte comando:

```bash
teamsfx config set validate-dotnet-sdk on
```

#### <a name="view-all-the-user-scope-configuration"></a>Exibir toda a configuração de escopo do usuário

```bash
teamsfx config get -g
```

#### <a name="view-all-the-configuration-in-project"></a>Exibir toda a configuração no projeto

O segredo é descriptografado automaticamente:

```bash
teamsfx config get --env dev
```

#### <a name="update-the-secret-configuration-in-project"></a>Atualizar a configuração secreta no projeto

```bash
teamsfx config set fx-resource-aad-app-for-teams.clientSecret xxx --env dev
```

## `teamsfx permission`

A CLI do TeamsFx fornece comandos `teamsFx permission` para o cenário de colaboração.

| `teamsFx permission` Comando | Descrição |
|:------------------------------|-------------|
| `teamsfx permission grant --env --email` | Conceda permissão para a conta Microsoft 365 colaborador para o projeto de um ambiente especificado. |
| `teamsfx permission status` | Mostrar status de permissão para o projeto |

### <a name="parameters-for-teamsfx-permission-grant"></a>Parâmetros para `teamsfx permission grant`

| Parâmetro  | Requisito | Descrição |
|:----------------  |:-------------|:-------------|
|`--env`| Sim | Forneça o nome do env. |
|`--email`| Sim | Forneça o endereço de email Microsoft 365 colaborador. Verifique se a conta do colaborador está no mesmo locatário com o criador. |

### <a name="parameters-for-teamsfx-permission-status"></a>Parâmetros para `teamsfx permission status`

| Parâmetro | Requisito | Descrição |
|:----------------  |:-------------|:-------------|
|`--env`| Sim | Forneça o nome do env. |
|`--list-all-collaborators` | Não | Com esse sinalizador, Teams Toolkit CLI imprime todos os colaboradores para este projeto. |

### <a name="scenarios-for-teamsfx-permission"></a>Cenários para `teamsfx permission`

As permissões para projetos `TeamsFx` são as seguintes:

#### <a name="grant-permission"></a>Conceder Permissão

Project criador e colaboradores podem usar o `teamsfx permission grant` comando para adicionar um novo colaborador ao projeto:

```bash
teamsfx permission grant --env dev --email user-email@user-tenant.com
```

Depois de receber a permissão necessária, o criador e os colaboradores do projeto podem compartilhar o projeto com o novo colaborador pelo GitHub, e o novo colaborador pode ter toda a permissão para Microsoft 365 conta.

#### <a name="show-permission-status"></a>Mostrar Status da Permissão

Project criador e colaboradores podem usar `teamsfx permission status` o comando para exibir sua Microsoft 365 de conta para env específico:

```bash
teamsfx permission status --env dev
```

#### <a name="list-all-collaborators"></a>Listar Todos os Colaboradores

Project criadores e colaboradores podem usar o `teamsfx permission status` comando para exibir todos os colaboradores para env específico:

```bash
teamsfx permission status --env dev --list-all-collaborators
```

#### <a name="e2e-collaboration-work-flow-in-cli"></a>Fluxo de trabalho de Colaboração E2E na CLI

Como um criador de projeto:

* Para criar uma nova guia ou projeto de bot do TeamsFx e selecionar o Azure como o tipo de host:

  ```bash
  teamsfx new --interactive false --app-name newapp --host-type azure
  ```

* Para fazer logon Microsoft 365 conta e conta do Azure:

  ```bash
  teamsfx account login azure
  teamsfx account login Microsoft 365
  ```

* Para provisionar seu projeto:

  ```bash
  teamsfx provision
  ```

* Para exibir colaboradores:

  ```bash
  teamsfx permission status --env dev --list-all-collaborators
  ```

  :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/permission-status-all-1.png" alt-text="permission-1":::

* Para adicionar outra conta como colaborador. Verifique se a conta adicionada está no mesmo locatário:

  ```bash
  teamsfx permission grant --env dev --email user-email@user-tenant.com
  ```

  :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/permission-grant-1.png" alt-text="permissão":::

* Para enviar por push seu projeto para GitHub

Como um Project colaborador:

* Clone o projeto de GitHub.
* Faça logon Microsoft 365 conta. Verifique se a mesma Microsoft 365 conta foi adicionada:

  ```bash
  teamsfx account login Microsoft 365
  ```

* Faça logon na conta do Azure com permissão de colaborador para todos os recursos do Azure.

  ```bash
  teamsfx account login azure
  ```

* Verifique o status da permissão. Você deve ter a permissão de proprietário do projeto:

  ```bash
  teamsfx permission status --env dev
  ```

  ![status da permissão](./images/permission-status.png)

* Atualize o código da guia e implante o projeto no remoto.
* Inicie remotamente e o projeto deve funcionar bem.

## <a name="see-also"></a>Confira também

* [SDK do TeamsFx para TypeScript ou JavaScript](TeamsFx-SDK.md)
* [Gerenciar vários ambientes no Kit de Ferramentas do Teams](TeamsFx-multi-env.md)
* [Colaborar no Teams usando o Teams Toolkit](TeamsFx-collaboration.md)
* [Visão geral do Kit de ferramentas do Microsoft Teams](teams-toolkit-fundamentals.md)
