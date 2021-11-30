---
title: Interface de linha de comando teamsFx
author: MuyangAmigo
description: Descreve a Interface de Linha de Comando teamsFx
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: b5ef65ec8d1377a99ddebe298e8f3ec4c4c8d3f0
ms.sourcegitcommit: f1e6f90fb6f7f5825e55a6d18ccf004d0091fb6d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2021
ms.locfileid: "61227687"
---
# <a name="teamsfx-command-line-interface"></a>Interface de linha de comando teamsFx

A CLI teamsFx é uma interface de linha de comando baseada em texto que acelera Teams desenvolvimento de aplicativos. Ele tem como objetivo fornecer uma experiência centrada no teclado ao criar Teams aplicativos. Ele também habilita cenário de CI/CD em que a CLI pode ser facilmente integrada em scripts para automação.

* [Código-fonte](https://github.com/OfficeDev/TeamsFx/tree/dev/packages/cli) 
* [Pacote (NPM)](https://www.npmjs.com/package/@microsoft/teamsfx-cli)

## <a name="get-started"></a>Introdução

Vamos começar instalando a `teamsfx-cli` partir de e executar para verificar todos os comandos `npm` `teamsfx -h` disponíveis:

```bash
  npm install -g @microsoft/teamsfx-cli
  teamsfx -h
```

## <a name="supported-commands"></a>Comandos com suporte

| `teamsfx` Comandos  | Descrições |
|:----------------  |:-------------|
| `teamsfx new`       | Crie um novo Teams aplicativo. |
| `teamsfx account`   | Gerenciar contas de serviço na nuvem. Os serviços de nuvem com suporte são 'Azure' e 'Microsoft 365'.          |
| `teamsfx env`       | Gerencie os ambientes. |
| `teamsfx capability`| Adicione novos recursos ao aplicativo atual.         |
| `teamsfx resource`  | Gerencie os recursos no aplicativo atual.         |
| `teamsfx provision` | Provisione os recursos de nuvem no aplicativo atual.             |
| `teamsfx deploy`    | Implantar o aplicativo atual.  |
| `teamsfx package`   | Crie seu Teams em um pacote para publicação.         |
| `teamsfx validate`  | Valide o aplicativo atual.             |
| `teamsfx publish`   | Publique o aplicativo no Teams.             |
| `teamsfx preview`   | Visualize o aplicativo atual. |
| `teamsfx config`    | Gerencie os dados de configuração. |
| `teamsfx permission`| Colabore com outros desenvolvedores no mesmo projeto.|

## `teamsfx new`

`teamsfx new`por padrão, entrar no modo interativo e orientá-lo pelo processo de criação de um novo Teams aplicativo fazendo algumas perguntas. Você também pode fazer isso no modo não interativo definindo `--interactive` o sinalizador como `false` .

| `teamsFx new` Comandos  | Descrições |
|:----------------  |:-------------|
| `teamsfx new template <template-name>`     | Criar um aplicativo a partir de um modelo existente |
| `teamsfx new template list`     | Listar todos os modelos disponíveis |

### <a name="parameters-for-teamsfx-new"></a>Parâmetros para `teamsfx new`

| Parâmetros  | Obrigatório | Descrições |
|:----------------  |:-------------|:-------------|
|`--app-name` | Sim| Nome do seu Teams aplicativo.|
|`--interactive`| Não | Selecione as opções interativamente. As opções `true` são e `false` . O valor padrão é `true`.|
|`--capabilities`| Não| Escolha Teams recursos do aplicativo, várias opções são: `tab` `bot` , e `messaging-extension` `tab-spfx` . O valor padrão é: `tab` .|
|`--programming-language`| Não| Linguagem de programação para o projeto. As opções `javascrip` são ou e o valor padrão `typescript` é: `javascript` .|
|`--folder`| Não | Project diretório. Uma sub pasta com o nome do aplicativo será criada neste diretório. O valor padrão é: `./` .|
|`--spfx-framework-type`| Não| Aplicável se `Tab(SPfx)` a funcionalidade estiver selecionada. Estrutura frontend. As opções `none` são e , o valor padrão `react` é: `none` .|
|`--spfx-web part-name`| Não | Aplicável se `Tab(SPfx)` a funcionalidade estiver selecionada. Nome da Web Part. O valor padrão é: "helloworld". |
|`--spfx-web part-desp`| Não | Aplicável se `Tab(SPfx)` a funcionalidade estiver selecionada. Descrição da Web Part. O valor padrão é: "helloworld description". |
|`--azure-resources`| Não| Aplicável se `tab` contiver funcionalidade. Adicione recursos do Azure ao seu projeto. Options(Multiple) are `sql` (Banco de Dados SQL do Azure) and `function` (Azure Functions). |

### <a name="scenarios-for-teamsfx-new"></a>Cenários para `teamsfx new`

Usando o modo interativo para criar um Teams app é super intuitivo, experimente começando com `teamsfx new` . Veja a seguir os poucos cenários para controlar todos os parâmetros:

#### <a name="a-tab-app-hosted-on-spfx-using-react"></a>Um aplicativo de guia hospedado no SPFx usando React

```bash
teamsfx new --interactive false --app-name newspfxapp --capabilities tab-spfx --spfx-framework-type react
```

#### <a name="a-teams-app-in-javascript-contains-tab-bot-capabilities-and-azure-functions"></a>Um Teams no JavaScript contém guias, recursos de bot e funções do Azure

```bash
teamsfx new --interactive false --app-name newtabbotapp --capabilities tab bot --programming-language javascript --azure-resources function
```

#### <a name="a-teams-tab-app-with-azure-functions-and-azure-sql"></a>Um Teams guia com funções do Azure e o Azure SQL

```bash
teamsfx new --interactive false app-name newapp --azure-resources sql function --programming-language typescript
```

## `teamsfx account`

Gerenciar contas de serviço na nuvem. Os serviços de nuvem com suporte `Azure` são e `Microsoft 365` .

| `teamsFx account` Comandos  | Descrições |
|:----------------  |:-------------|
| `teamsfx account login <service>`      | Faça logoff no serviço de nuvem selecionado. |
| `teamsfx account logout <service>`      | sair do serviço de nuvem selecionado. |
| `teamsfx account set --subscription`      | Atualize as configurações da conta para definir uma ID de assinatura. |

## `teamsfx env`

Gerencie os ambientes.

| `teamsfx env` Comandos  | Descrições |
|:----------------  |:-------------|
| `teamsfx env add <new_env_name> --env <existing_env_name>` | Adicione um novo ambiente copiando do ambiente especificado. |
| `teamsfx env list` | Listar todos os ambientes. |

### <a name="scenarios-for-teamsfx-env"></a>Cenários para `teamsfx env`

#### <a name="create-a-new-environment"></a>Criar um novo ambiente

Adicione um novo ambiente copiando do ambiente de dev existente:

```bash
teamsfx env add staging --env dev
```

## `teamsfx capability`

Adicione novos recursos ao aplicativo atual.

| `teamsFx capability` Comandos  | Descrições |
|:----------------  |:-------------|
| `teamsfx capability add tab`      | Adicione uma guia. |
| `teamsfx capability add bot`      | Adicione um bot. |
| `teamsfx capability add messaging-extension`      | Adicione uma Extensão de Mensagens. |

> [!NOTE]
> Depois que seu projeto incluir um bot, a extensão de mensagens não poderá ser adicionada mais e ela se aplicará vice-versa. Você pode incluir extensões de bot e mensagens em seu projeto ao criar um novo projeto Teams aplicativo.

## `teamsfx resource`

Gerencie os recursos no aplicativo atual. Os `<resource-type>` suportes são: `azure-sql` e `azure-function` `azure-apim` .

| `teamsFx resource` Comandos  | Descrições |
|:----------------  |:-------------|
| `teamsfx resource add <resource-type>`      | Adicione um recurso ao aplicativo atual.|
| `teamsfx resource show <resource-type>`      | Mostrar detalhes de configuração do recurso. |
| `teamsfx resource list`      | Listar todos os recursos no aplicativo atual. |

### <a name="parameters-for-teamsfx-resource-add-azure-function"></a>Parâmetros para `teamsfx resource add azure-function`

| Parâmetros  | Obrigatório | Descrições |
|:----------------  |:-------------|:-------------|
|`--function-name`| Sim | Forneça um nome de função. O valor padrão é: `getuserprofile` . |

### <a name="parameters-for-teamsfx-resource-add-azure-sql"></a>Parâmetros para `teamsfx resource add azure-sql`

#### `--function-name`

| Parâmetros  | Obrigatório | Descrições |
|:----------------  |:-------------|:-------------|
|`--function-name`| Sim | Forneça um nome de função. O valor padrão é: `getuserprofile` . |

> [!NOTE]
> O nome da função é verificado SQL precisa ser acessado a partir da carga de trabalho do servidor. Se seu projeto não contém `Azure Functions` , ele criará um para você.

### <a name="parameters-for-teamsfx-resource-add-azure-apim"></a>Parâmetros para `teamsfx resource add azure-apim`

> [!TIP]
> As opções abaixo terão efeito quando você tentar usar uma instância `APIM` existente. Por padrão, você não precisa especificar nenhuma opção e ela criará uma nova instância durante a `teamsfx provision` etapa.

| Parâmetros  | Obrigatório | Descrições |
|:----------------  |:-------------|:-------------|
|`--subscription`| Sim | Selecionar uma assinatura do Azure|
|`--apim-resource-group`| Sim| O nome do grupo de recursos. |
|`--apim-service-name`| Sim | O nome da instância do serviço de Gerenciamento de API. |
|`--function-name`| Sim | Forneça um nome de função. O valor padrão é: `getuserprofile` . |

> [!NOTE]
> Pedimos o nome da função porque `Azure API Management` precisa trabalhar com `Azure Functions` . Se seu projeto não `Azure Functions` conter, criaremos um para você.

## `teamsfx provision`

Provisione os recursos de nuvem no aplicativo atual.

### <a name="parameters-for-teamsfx-provision"></a>Parâmetros para `teamsfx provision`

| Parâmetros  | Obrigatório | Descrições |
|:----------------  |:-------------|:-------------|
|`--env`| Sim| Selecione um ambiente para o projeto. |
|`--subscription`| Não | Especifique uma ID de Assinatura do Azure. |
|`--resource-group`| Não | De definir o nome de um grupo de recursos existente. |
|`--sql-admin-name`| Não | Aplicável quando houver SQL recurso no projeto. Nome do administrador SQL.|
|`--sql-password`| Não| Aplicável quando houver SQL recurso no projeto. Senha de administrador SQL.|

## `teamsfx deploy`

Esse comando é usado para implantar o aplicativo atual. Por padrão, ele implantará todo o projeto, mas também é possível implantar parcialmente. As opções(Múltiplos) `frontend-hosting` são: `function` , , , `apim` , `teamsbot` `spfx` .

### <a name="parameters-for-teamsfx-deploy"></a>Parâmetros para `teamsfx deploy`

| Parâmetros  | Obrigatório | Descrições |
|:----------------  |:-------------|:-------------|
|`--env`| Sim| Selecione um ambiente existente para o projeto. |
|`--open-api-document`| Não | Aplicável quando há recurso APIM no projeto. O caminho do arquivo de documento abrir API. |
|`--api-prefix`| Não | Aplicável quando há recurso APIM no projeto. O prefixo de nome da API. O nome exclusivo padrão da API será `{api-prefix}-{resource-suffix}-{api-version}` . |
|`--api-version`| Não | Aplicável quando há recurso APIM no projeto. A versão da API. |

## `teamsfx validate`

Validar o aplicativo atual. Este comando validará o arquivo de manifesto do aplicativo.

### <a name="parameters-for-teamsfx-validate"></a>Parâmetros para `teamsfx validate`

`--env`: (Obrigatório) Selecione um ambiente existente para o projeto.

## `teamsfx publish`

Publique o aplicativo no Teams.

### <a name="parameters-for-teamsfx-publish"></a>Parâmetros para `teamsfx publish`

`--env`: (Obrigatório) Selecione um ambiente existente para o projeto.

## `teamsfx package`

Crie seu Teams em um pacote para publicação.

## `teamsfx preview`

Visualize o aplicativo atual de local ou remoto.

### <a name="parameters-for-teamsfx-preview"></a>Parâmetros para `teamsfx preview`

| Parâmetros  | Obrigatório | Descrições |
|:----------------  |:-------------|:-------------|
|`--local`| Não | Visualize o aplicativo de local. `--local` é exclusivo com `--remote` . |
|`--remote`| Não | Visualize o aplicativo do controle remoto. `--remote` é exclusivo com `--local` . |
|`--env`| Não | Selecione um ambiente existente para o projeto quando `--remote` o parâmetro for anexado. |
|`--folder`| Não | Project diretório raiz. O valor padrão é `./`. |
|`--browser`| Não | O navegador para abrir Teams cliente Web. As opções `chrome` são e `edge` `default` (navegador padrão do sistema). O valor padrão é `default`. |
|`--browser-arg`| Não | Argumento para passar para o navegador, requer --browser, pode ser usado várias vezes (por exemplo, --browser-args="--guest") |
|`--sharepoint-site`| Não | SharePoint URL do site, como (somente para SPFx `{your-tenant-name}.sharepoint.com` visualização remota do projeto). |

### <a name="scenarios-for-teamsfx-preview"></a>Cenários para `teamsfx preview`

#### <a name="local-preview"></a>Visualização Local

Dependências:

- Node.js
- .NET SDK
- Ferramentas principais das funções do Azure

```bash
teamsfx preview --local
teamsfx preview --local --browser chrome
```

#### <a name="remote-preview"></a>Visualização Remota

```bash
teamsfx preview --remote
teamsfx preview --remote --browser edge
```

> [!Note]
> Os logs dos serviços em segundo plano como React serão salvos em `~/.fx/cli-log/local-preview/` .

## `teamsfx config`

Gerencie os dados de configuração no escopo do usuário ou no escopo do projeto.

| `teamsfx config` Comandos  | Descrições |
|:----------------  |:-------------|
| `teamsfx config get [option]` | Exibir o valor de configuração da opção |
| `teamsfx config set <option> <value>` | Atualizar o valor de configuração da opção |

### <a name="parameters-for-teamsfx-config"></a>Parâmetros para `teamsfx config`

| Parâmetros  | Obrigatório | Descrições |
|:----------------  |:-------------|:-------------|
|`--env`| Sim | Selecione um ambiente existente para o projeto. |
|`--folder`| Não | Project diretório. Isso é usado quando a configuração do projeto é get/set. O valor padrão é: `./` . |
|`--global`| Não | Lidar com a configuração. Se isso for verdadeiro, o escopo será limitado ao escopo do usuário em vez do escopo do projeto. O valor padrão é: `false` . Atualmente, as configurações globais com suporte `telemetry` incluem: `validate-dotnet-sdk` , , , `validate-func-core-tools` `validate-node` . |

### <a name="scenerios-for-teamsfx-config"></a>Scenerios para `teamsfx config`

Os segredos `.userdata` no arquivo são criptografados, `teamsfx config` podem ajudá-lo a exibir/atualizar esses valores.

#### <a name="stop-sending-telemetry-data"></a>Parar de enviar dados de telemetria

```bash
teamsfx config set telemetry off
```

#### <a name="disable-environment-checker"></a>Desabilitar o checker de ambiente

Há três configs para ativar/desativar Node.js, validação do .NET SDK e ferramentas principais de funções do Azure, e todas elas estão habilitadas por padrão. Você pode definir a configuração como "off" se não precisar da validação de dependências e quiser instalar as dependências por conta própria. Verifique o [Node.js de](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/vscode-extension/envchecker-help.md#how-to-install-nodejs)instalação, o guia de instalação [do .NET SDK](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/vscode-extension/envchecker-help.md#how-to-install-net-sdk) e o guia de instalação ferramentas principais do [Azure Functions.](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/vscode-extension/envchecker-help.md#how-to-install-azure-functions-core-tools)

Por exemplo, para desabilitar a validação do .NET SDK, você pode usar o seguinte comando.

```bash
teamsfx config set validate-dotnet-sdk off
```

Para habilitar a validação do .NET SDK, você pode usar o seguinte comando.

```bash
teamsfx config set validate-dotnet-sdk on
```

#### <a name="view-all-the-user-scope-configuration"></a>Exibir toda a configuração do escopo do usuário

```bash
teamsfx config get -g
```

#### <a name="view-all-the-configuration-in-project"></a>Exibir toda a configuração no projeto

O segredo será descriptografado automaticamente:

```bash
teamsfx config get --env dev
```

#### <a name="update-the-secret-configuration-in-project"></a>Atualizar a configuração secreta no projeto

```bash
teamsfx config set fx-resource-aad-app-for-teams.clientSecret xxx --env dev
```

## `teamsfx permission`

A CLI teamsFx fornece `teamsFx permission` Comandos para cenário de colaboração.

| `teamsFx permission` Comandos | Descrições |
|:------------------------------|-------------|
| `teamsfx permission grant --env --email` | Conceda permissão para a conta Microsoft 365 do colaborador para o projeto de um ambiente especificado. |
| `teamsfx permission status` | Mostrar status de permissão para o projeto |

### <a name="parameters-for-teamsfx-permission-grant"></a>Parâmetros para `teamsfx permission grant`

| Parâmetros  | Obrigatório | Descrições |
|:----------------  |:-------------|:-------------|
|`--env`| Sim | Forneça o nome do env. |
|`--email`| Sim | Forneça o endereço de email Microsoft 365 do colaborador. Observe que a conta do colaborador deve estar no mesmo locatário com o criador. |

### <a name="parameters-for-teamsfx-permission-status"></a>Parâmetros para `teamsfx permission status`

| Parâmetros  | Obrigatório | Descrições |
|:----------------  |:-------------|:-------------|
|`--env`| Sim | Forneça o nome do env. |
|`--list-all-collaborators` | Não | Com esse sinalizador, Teams Toolkit CLI imprimirá todos os colaboradores deste projeto. |

### <a name="scenarios-for-teamsfx-permission"></a>Cenários para `teamsfx permission`

Aqui estão alguns exemplos, para melhor manipulação de permissões para `TeamsFx` projetos.

#### <a name="grant-permission"></a>Conceder Permissão

Project criadores e colaboradores podem usar `teamsfx permission grant` o comando para adicionar um novo colaborador ao projeto:

```bash
teamsfx permission grant --env dev --email user-email@user-tenant.com
```

Após a permissão concedida com êxito, o criador do projeto e os colaboradores podem compartilhar o projeto com o novo colaborador pelo Github, e o novo colaborador terá toda a permissão para Microsoft 365 conta.

#### <a name="show-permission-status"></a>Mostrar Status da Permissão

Project criadores e colaboradores podem usar o comando para exibir sua Microsoft 365 de conta `teamsfx permission status` para env específico:

```bash
teamsfx permission status --env dev
```

#### <a name="list-all-collaborators"></a>Listar Todos os Colaboradores

Project criadores e colaboradores podem usar `teamsfx permission status` o comando para exibir todos os colaboradores para env específico:

```bash
teamsfx permission status --env dev --list-all-collaborators
```

#### <a name="e2e-collaboration-work-flow-in-cli"></a>Fluxo de trabalho de colaboração do E2E na CLI

Como criador do projeto:

- Crie um novo projeto de Guia teamsFx (Você também pode selecionar bot) e o tipo de hospedagem selecione Azure.

  ```bash
  teamsfx new --interactive false --app-name newapp --host-type azure
  ```

- Faça logon Microsoft 365 conta e conta do Azure.

  ```bash
  teamsfx account login azure
  teamsfx account login Microsoft 365
  ```

- Provisione seu projeto.

  ```bash
  teamsfx provision
  ```

- Exibir colaboradores. Você deve se ver aqui.

  ```bash
  teamsfx permission status --env dev --list-all-collaborators
  ```

  ![list-all-collaborators](./images/permission-status-all.png)
- Adicione outra conta como colaborador. Observe que a conta adicionada deve estar no mesmo locatário:

  ```bash
  teamsfx permission grant --env dev --email user-email@user-tenant.com
  ```

  ![add-new-collaborator](./images/permission-grant.png)
- Pressione seu projeto para GitHub

Como colaborador Project:

- Clone o projeto de GitHub.
- Faça logon Microsoft 365 conta. Observe que a Microsoft 365 deve ser a mesma que foi adicionada acima:

  ```bash
  teamsfx account login Microsoft 365
  ```

- Logon Conta do Azure que tem permissão de colaborador para todos os recursos do Azure.

  ```bash
  teamsfx account login azure
  ```

- Verifique o status da permissão. Você deve encontrar a permissão do proprietário do projeto:

  ```bash
  teamsfx permission status --env dev
  ```

  ![status da permissão](./images/permission-status.png)
- Atualize o código da guia e implante o projeto no controle remoto.
- Iniciar remoto e o projeto deve funcionar bem.
