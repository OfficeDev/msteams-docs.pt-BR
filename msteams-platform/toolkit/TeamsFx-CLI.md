---
title: Interface da linha de comando do TeamsFx
author: MuyangAmigo
description: Descreve a interface de linha de comando do TeamsFx
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 6c8873bf952cd05e0315efb45403688f69471147
ms.sourcegitcommit: e16b51a49756e0fe4eaf239898e28d3021f552da
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2022
ms.locfileid: "65887643"
---
# <a name="teamsfx-library"></a>Biblioteca do TeamsFx

O Microsoft Teams Framework (TeamsFx) é uma biblioteca que encapsula padrões comuns de integração e funcionalidade, como acesso simplificado ao Microsoft Identity. Você pode criar aplicativos para o Microsoft Teams sem configuração.

Aqui está uma lista dos principais recursos do TeamsFx:

* **Colaboração do TeamsFx**: permite que os desenvolvedores e o proprietário do projeto convidem outros colaboradores para o projeto TeamsFx. Você pode colaborar para depurar e implantar um projeto do TeamsFx.

* **CLI do TeamsFx**: acelera o desenvolvimento de aplicativos do Teams. Ele também habilita o cenário de CI/CD em que você pode integrar a CLI em scripts para automação.

* **SDK do TeamsFx**: fornece acesso ao banco de dados, como a biblioteca de código principal do TeamsFx que contém autenticação simples para código do lado do cliente e do servidor personalizado para desenvolvedores do Teams.

## <a name="teamsfx-command-line-interface"></a>Interface da linha de comando do TeamsFx

O TeamsFx é uma interface de linha de comando baseada em texto que acelera o desenvolvimento de aplicativos do Teams. Ele tem como objetivo fornecer experiência centrada no teclado durante a criação de aplicativos do Teams. Ele também habilita o cenário de CI/CD em que você pode integrar a CLI em scripts para automação.

Para saber mais, confira:
* [Código-fonte](https://github.com/OfficeDev/TeamsFx/tree/dev/packages/cli)
* [Pacote (NPM)](https://www.npmjs.com/package/@microsoft/teamsfx-cli)

## <a name="get-started"></a>Introdução

Instale `teamsfx-cli` de `npm` e execute `teamsfx -h` para verificar todos os comandos disponíveis:

```bash
  npm install -g @microsoft/teamsfx-cli
  teamsfx -h
```

## <a name="supported-commands"></a>Comandos com suporte

| Comando | Descrição |
|----------------|-------------|
| `teamsfx new`| Crie um novo aplicativo do Teams.|
| `teamsfx add`| Adiciona recursos ao aplicativo Teams.|
| `teamsfx account`| Gerencie contas de serviço de nuvem. Os serviços de nuvem com suporte são o “Azure” e o “Microsoft 365”. |
| `teamsfx env` | Gerencie ambientes. |
| `teamsfx provision` | Provisione recursos de nuvem no aplicativo atual.|
| `teamsfx deploy` | Implante o aplicativo atual.  |
| `teamsfx package` | Crie seu aplicativo do Teams em um pacote para publicação.|
| `teamsfx validate` | Valide o aplicativo atual|
| `teamsfx publish` | Publique o aplicativo no Teams.|
| `teamsfx preview` | Pré-visualize o aplicativo atual. |
| `teamsfx config`  | Gerencie os dados de configuração. |
| `teamsfx permission`| Colabore com outros desenvolvedores no mesmo projeto.|

## `teamsfx new`

Por padrão, está `teamsfx new` no modo interativo e guias para criar um novo aplicativo do Teams. Você pode trabalhar no modo não interativo definindo o sinalizador `--interactive` como `false`.

| Comando | Descrição |
|:----------------  |:-------------|
| `teamsfx new template <template-name>`     | Crie um aplicativo com base em um modelo existente |
| `teamsfx new template list`     | Liste todos os modelos disponíveis |

### <a name="parameters-for-teamsfx-new"></a>Parâmetros para `teamsfx new`

| Parâmetro | Requisito | Descrição |
|:---------------- |:-------------|:-------------|
|`--app-name` | Sim| Nome do aplicativo do Teams.|
|`--interactive`| Não | Selecione as opções interativamente. As opções são `true` e `false` e o valor padrão é `true`.|
|`--capabilities`| Não| Escolha os recursos de aplicativo do Teams, as opções `tab`são , `tab-non-sso`, `tab-spfx`, `bot`, `message-extension`, `notification`, `command-bot`, , `sso-launch-page`. `search-app` O valor padrão é `tab`.|
|`--programming-language`| Não| Linguagem de programação para o projeto. As opções são `javascript` ou `typescript` e o valor padrão é `javascript`.|
|`--folder`| Não | Diretório do projeto. Uma subpasta com o nome do aplicativo é criada neste diretório. O valor padrão é `./`.|
|`--spfx-framework-type`| Não| Aplicável se o recurso `SPFx tab` estiver selecionado. Estrutura de front-end. As opções são `none`, e `minimal``react` , e o valor padrão é `none`.|
|`--spfx-web part-name`| Não | Aplicável se o recurso `SPFx tab` estiver selecionado. O valor padrão é "helloworld".|
|`--bot-host-type-trigger`| Não | Aplicável se o recurso `Notification bot` estiver selecionado. As opções são `http-restify`, `http-functions`e `timer-functions`. O valor padrão é `http-restify`.|

### <a name="scenarios-for-teamsfx-new"></a>Cenários para `teamsfx new`

Você pode usar o modo interativo para criar um aplicativo do Teams. A lista a seguir fornece cenários sobre como controlar todos os parâmetros com `teamsfx new`:

* Bot de notificação disparada por HTTP com servidor restify

  ```bash
  teamsfx new --interactive false --capabilities "notification" --bot-host-type-trigger "http-restify" --programming-language "typescript" --folder "./" --app-name       MyAppName
  ```

* Bot de comando e resposta do Teams

  ```bash
  teamsfx new --interactive false --capabilities "command-bot" --programming-language "typescript" --folder "./" --app-name myAppName
  ```

* Aplicativo de guia hospedado no SPFx usando React

  ```bash
  teamsfx new --interactive false --app-name newspfxapp --capabilities tab-spfx --spfx-framework-type react
  ```

## `teamsfx add`

A tabela a seguir lista os diferentes recursos para o aplicativo Teams, juntamente com a descrição.

| Comando | Descrição |
|:----------------  |:-------------|
| `teamsfx add notification` | Envie uma notificação para o Microsoft Teams por meio de vários gatilhos. |
| `teamsfx add command-and-response` | Responder a comandos simples no chat do Microsoft Teams.|
| `teamsfx add sso-tab` | Páginas da Web com reconhecimento de identidade do Teams inseridas no Microsoft Teams.|
| `teamsfx add tab` | Páginas da Web Hello World inseridas no Microsoft Teams.|
| `teamsfx add bot` | Olá, mundo chatbot para executar tarefas simples e repetitivas por usuário. |
| `teamsfx add message-extension` | Extensão de mensagem Olá, Mundo, permitindo interações por meio de botões e formulários. |
| `teamsfx add azure-function`| Uma solução de computação controlada por eventos sem servidor que permite que você escreva menos código. |
| `teamsfx add azure-apim` | Uma plataforma de gerenciamento híbrida e multinuvem para APIs em todos os ambientes.|
| `teamsfx add azure-sql` | Um serviço de banco de dados relacional sempre atualizado criado para a nuvem. |
| `teamsfx add azure-keyvault` | Um serviço de nuvem para armazenar e acessar segredos com segurança. |
| `teamsfx add sso` | Desenvolva um recurso de Sign-On para as páginas de Inicialização do Teams e a funcionalidade de Bot. |
| `teamsfx add api-connection [auth-type]` | Conecte-se a uma API com suporte de autenticação usando o SDK do TeamsFx. |
| `teamsfx add cicd` | Adicione fluxos de trabalho de CI/CD para GitHub, Azure DevOps ou Jenkins.|

## `teamsfx account`

A tabela a seguir lista as contas de serviço de nuvem, como o Azure e o Microsoft 365.

| Comando | Descrição |
|:----------------  |:-------------|
| `teamsfx account login <service>`  | Faça logon no serviço de nuvem selecionado. As opções de serviço são M365 ou Azure. |
| `teamsfx account logout <service>`  | Faça logoff do serviço de nuvem selecionado. As opções de serviço são M365 ou Azure. |
| `teamsfx account set --subscription` | Atualize as configurações da conta para definir uma ID de assinatura. |

## `teamsfx env`

A tabela a seguir lista os diferentes ambientes.

|  Comando  | Descrição |
|:----------------  |:-------------|
| `teamsfx env add <new_env_name> --env <existing_env_name>` | Adicione um novo ambiente copiando do ambiente especificado. |
| `teamsfx env list` | Liste todos os ambientes. |

### <a name="scenarios-for-teamsfx-env"></a>Cenários para `teamsfx env`

Crie um novo ambiente copiando do ambiente de desenvolvimento existente:

```bash
teamsfx env add staging --env dev
```

## `teamsfx provision`

Provisione os recursos de nuvem no aplicativo atual.

| Comando `teamsFx provision` | Descrição |
|:----------------  |:-------------|
| `teamsfx provision manifest` | Provisione um aplicativo do Teams no portal do Desenvolvedor do Teams com as informações correspondentes especificadas no arquivo de manifesto fornecido. |

### <a name="parameters-for-teamsfx-provision"></a>Parâmetros para `teamsfx provision`

| Parâmetro  | Requisito | Descrição |
|:----------------  |:-------------|:-------------|
|`--env`| Sim| Selecionar um ambiente para o projeto. |
|`--subscription`| Não | Especificar uma ID de Assinatura do Azure. |
|`--resource-group`| Não | Definir o nome de um grupo de recursos existente. |
|`--sql-admin-name`| Não | Aplicável quando há um recurso SQL no projeto. Nome do administrador do SQL.|
|`--sql-password`| Não| Aplicável quando há um recurso SQL no projeto. Senha de administrador do SQL.|

## `teamsfx deploy`

Esse comando é usado para implantar o aplicativo atual. Por padrão, ele implanta todo o projeto, mas também é possível implantar parcialmente. As opções são `frontend-hosting`, `function`, `apim`, `bot`, `spfx`e `aad-manifest` `manifest`.

### <a name="parameters-for-teamsfx-deploy"></a>Parâmetros para `teamsfx deploy`

| Parâmetro  | Requisito | Descrição |
|:----------------  |:-------------|:-------------|
|`--env`| Sim| Selecionar um ambiente existente para o projeto. |
|`--open-api-document`| Não | Aplicável quando há recurso de APIM no projeto. O caminho do arquivo de documento de API aberto. |
|`--api-prefix`| Não | Aplicável quando há recurso de APIM no projeto. O prefixo do nome da API. O nome exclusivo padrão da API é `{api-prefix}-{resource-suffix}-{api-version}`. |
|`--api-version`| Não | Aplicável quando há recurso de APIM no projeto. A versão da API. |
|`--include-app-manifest`| Não | Se deseja implantar o manifesto do aplicativo na plataforma Teams. As opções são `yes` e `not`. O valor padrão é `no`. |
|`--include-aad-manifest`| Não | Se deseja implantar o manifesto do aad. As opções são `yes` e `not`. O valor padrão é `no`. |


## `teamsfx validate`

Validar o aplicativo atual. Esse comando valida o arquivo de manifesto do aplicativo.

### <a name="parameters-for-teamsfx-validate"></a>Parâmetros para `teamsfx validate`

`--env`: selecionar um ambiente existente para o projeto.

## `teamsfx publish`

Publicar o aplicativo no Teams.

### <a name="parameters-for-teamsfx-publish"></a>Parâmetros para `teamsfx publish`

`--env`: selecionar um ambiente existente para o projeto.

## `teamsfx package`

Crie seu aplicativo do Teams em um pacote para publicação.

## `teamsfx preview`

Visualizar o aplicativo atual do local ou remoto.

### <a name="parameters-for-teamsfx-preview"></a>Parâmetros para `teamsfx preview`

| Parâmetro  | Requisito | Descrição |
|:----------------  |:-------------|:-------------|
|`--local`| Não | Visualizar o aplicativo do local. `--local` é exclusivo com `--remote`. |
|`--remote`| Não | Visualizar o aplicativo do remoto. `--remote` é exclusivo com `--local`. |
|`--env`| Não | Selecionar um ambiente existente para o projeto quando o parâmetro `--remote` for acrescentado. |
|`--folder`| Não | Diretório raiz do projeto. O valor padrão é `./`. |
|`--browser`| Não | O navegador para abrir o cliente Web do Teams. As opções são `chrome`, `edge` e `default` como o navegador padrão do sistema e o valor é `default`. |
|`--browser-arg`| Não | O argumento a ser passado para o navegador, requer --browser, pode ser usado várias vezes, por exemplo, --browser-args="--guest" |
|`--sharepoint-site`| Não | URL do site do SharePoint, como `{your-tenant-name}.sharepoint.com` para visualização remota do projeto SPFx. |
|`--m365-host`| Visualize o aplicativo no Teams, no Outlook ou no Office. As opções são `teams`e `office``outlook` . O valor padrão é `teams`. |

### <a name="scenarios-for-teamsfx-preview"></a>Cenários para `teamsfx preview`

A lista a seguir fornece os cenários comuns para a versão prévia do teamsfx:

* Visualização local

  Dependências:

  * Node.js
  * SDK DO .NET
  * Ferramentas do Azure Functions Core versão 3.

  ```bash
  teamsfx preview --local
  teamsfx preview --local --browser chrome
  ```

* Visualização Remota

  ```bash
  teamsfx preview --remote
  teamsfx preview --remote --browser edge
  ```

  > [!NOTE]
  > Os logs dos serviços em segundo plano, como React, são salvos em `~/.fx/cli-log/local-preview/`.

## `teamsfx config`

Os dados de configuração estão no escopo do usuário ou no escopo do projeto.

|  Comando  | Descrição |
|:----------------  |:-------------|
| `teamsfx config get [option]` | Exibir o valor de configuração da opção |
| `teamsfx config set <option> <value>` | Atualizar o valor de configuração da opção |

### <a name="parameters-for-teamsfx-config"></a>Parâmetros para `teamsfx config`

| Parâmetro  | Requisito | Descrição |
|:----------------  |:-------------|:-------------|
|`--env`| Sim | Selecionar um ambiente existente para o projeto. |
|`--folder`| Não | Diretório do projeto usado para obter ou definir a configuração do projeto. O valor padrão é `./`. |
|`--global`| Não | Escopo da configuração. Se for true, o escopo será limitado ao escopo do usuário em vez do escopo do projeto. O valor padrão é `false`. Agora, as configurações globais com suporte incluem `telemetry`, `validate-dotnet-sdk`, `validate-func-core-tools`, `validate-node`. |

### <a name="scenarios-for-teamsfx-config"></a>Cenários para `teamsfx config`

Os segredos no arquivo `.userdata` são criptografados e `teamsfx config` podem ajudá-lo a exibir ou atualizar os valores necessários.

* Parar de enviar dados de telemetria

  ```bash
  teamsfx config set telemetry off
  ```

* Desabilitar verificador de ambiente

  Há três configurações para ativar ou desativar o Node.js, o SDK do .NET e a validação do Azure Functions Core Tools e todas elas estão habilitadas por padrão. Você pode definir a configuração como "desativada" se não precisar da validação de dependências e quiser instalar as dependências por conta própria. Verifique os seguintes guias:

  * [Guia de instalação do Node.js](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/vscode-extension/envchecker-help.md#how-to-install-nodejs)
  * [Guia de instalação do SDK do .NET](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/vscode-extension/envchecker-help.md#how-to-install-net-sdk)
  * [Guia de instalação das Ferramentas do Azure Functions Core](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/vscode-extension/envchecker-help.md#how-to-install-azure-   functions-core-tools).

  Para desabilitar a validação do SDK do .NET, você pode usar o seguinte comando:

  ```bash
  teamsfx config set validate-dotnet-sdk off
  ```

  Para habilitar a validação do SDK do .NET, você pode usar o seguinte comando:

  ```bash
  teamsfx config set validate-dotnet-sdk on
  ```

* Exibir toda a configuração de escopo do usuário

  ```bash
  teamsfx config get -g
  ```

* Exibir toda a configuração no projeto

  O segredo é descriptografado automaticamente:

    ```bash
    teamsfx config get --env dev
    ```

* Atualizar a configuração secreta no projeto

  ```bash
  teamsfx config set fx-resource-aad-app-for-teams.clientSecret xxx --env dev
  ```

## `teamsfx permission`

A CLI do TeamsFx fornece `teamsFx permission` comandos para cenários de colaboração.

|  Comando | Descrição |
|:------------------------------|-------------|
| `teamsfx permission grant --env --email` | Conceder permissão para a conta do colaborador do Microsoft 365 para o projeto de um ambiente especificado. |
| `teamsfx permission status` | Mostrar status de permissão para o projeto |

### <a name="parameters-for-teamsfx-permission-grant"></a>Parâmetros para `teamsfx permission grant`

| Parâmetro  | Requisito | Descrição |
|:----------------  |:-------------|:-------------|
|`--env`| Sim | Fornecer o nome do env. |
|`--email`| Sim | Fornecer o endereço de email do colaborador do Microsoft 365. Verifique se a conta do colaborador está no mesmo locatário com o criador. |

### <a name="parameters-for-teamsfx-permission-status"></a>Parâmetros para `teamsfx permission status`

| Parâmetro | Requisito | Descrição |
|:----------------  |:-------------|:-------------|
|`--env`| Sim | Fornecer o nome do env. |
|`--list-all-collaborators` | Não | Com esse sinalizador, a CLI do Kit de Ferramentas do Teams imprime todos os colaboradores para este projeto. |

### <a name="scenarios-for-teamsfx-permission"></a>Cenários para `teamsfx permission`

A lista a seguir fornece as permissões necessárias para projetos `TeamsFx` :

* Conceder Permissões

  O criador e os colaboradores do projeto podem usar o comando `teamsfx permission grant` para adicionar um novo colaborador ao projeto:

  ```bash
  teamsfx permission grant --env dev --email user-email@user-tenant.com
  ```

  Depois de receber a permissão necessária, o criador do projeto e os colaboradores podem compartilhar o projeto com o novo colaborador pelo GitHub, e o novo colaborador pode ter toda a permissão para a conta do Microsoft 365.

* Mostrar Status da Permissão

  O criador do projeto e os colaboradores podem usar o `teamsfx permission status` comando para exibir a permissão de conta do Microsoft 365 para env específico:

  ```bash
  teamsfx permission status --env dev
  ```

* Listar todos os colaboradores

  O criador e os colaboradores do projeto podem usar o comando `teamsfx permission status` para exibir todos os colaboradores para env específico:

  ```bash
  teamsfx permission status --env dev --list-all-collaborators
  ```

* Fluxo de trabalho de Colaboração E2E na CLI

  * Como criador de projeto:

    * Para criar uma nova guia do TeamsFx ou um projeto de bot e selecionar o Azure como o tipo de host:

      ```bash
      teamsfx new --interactive false --app-name newapp --host-type azure
      ```

    * Para fazer logon nas contas do Microsoft 365 e do Azure:

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

      :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/permission-status-all-1.png" alt-text="permissão-1":::

    * Para adicionar outra conta como colaborador. Verifique se a conta adicionada está no mesmo locatário:

      ```bash
      teamsfx permission grant --env dev --email user-email@user-tenant.com
      ```

      :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/permission-grant-1.png" alt-text="permissão":::

    * Para enviar seu projeto por push para o GitHub

  * Como colaborador de projeto:

    * Clone o projeto do GitHub.
    * Faça logon na conta do Microsoft 365. Verifique se a mesma conta do Microsoft 365 foi adicionada:

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
* [Colaborar no projeto do Teams usando o Kit de Ferramentas do Teams](TeamsFx-collaboration.md)
* [Visão geral do Kit de ferramentas do Microsoft Teams](teams-toolkit-fundamentals.md)
