---
title: Vários ambientes teamsFX em Teams Toolkit
author: MuyangAmigo
description: Sobre o ambiente multi TeamsFX
ms.author: nintan
ms.localizationpriority: medium
ms.topic: overview of multiple environment
ms.date: 11/29/2021
ms.openlocfilehash: 1c0bb7eb75ee982e7c08d3039e59f03fc7f18146
ms.sourcegitcommit: 2d5bdda6c52693ed682bbd543b0aa66e1feb3392
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/12/2022
ms.locfileid: "61768458"
---
# <a name="manage-multiple-environments-in-teams-toolkit"></a>Gerenciar vários ambientes em Teams Toolkit

 Teams Toolkit fornece uma maneira simples de criar e gerenciar vários ambientes, provisionar e implantar artefatos no ambiente de destino para Teams App.

 Com vários ambientes, você pode executar o seguinte:

1. **Teste antes** da produção : é uma prática comum configurar vários ambientes, como desenvolvimento, teste e preparação antes de publicar um aplicativo Teams para o ambiente de produção no ciclo de vida moderno do desenvolvimento de aplicativos.

2. **Gerenciar comportamentos de aplicativos** em ambientes diferentes: você pode definir comportamentos diferentes para vários ambientes, como habilitar a telemetria no ambiente de produção, mas desabilitá-la no ambiente de desenvolvimento.

## <a name="prerequisite"></a>Pré-requisito

* [Instale Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) versão v3.0.0+.

> [!TIP]
> Verifique se você Teams projeto de aplicativo aberto em código VS.

## <a name="create-a-new-environment"></a>Criar um novo ambiente

Depois de criar um novo projeto, Teams Toolkit por padrão cria:

- Um `local` ambiente para representar as configurações de ambiente de máquina local.
- Um `dev` ambiente para representar as configurações de ambiente remoto ou de nuvem.

> [!NOTE]
> Cada projeto pode ter apenas um `local` ambiente, mas vários ambientes remotos.

Para adicionar outro ambiente remoto, selecione o ícone Teams na barra lateral, selecione criar novo ambiente na seção Ambiente, conforme mostrado na imagem a seguir:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/create new env.png" alt-text="criar":::

> [!NOTE]
> Se você tiver mais de um ambiente existente, será necessário selecionar um ambiente existente para criar o mesmo. O comando copiará o conteúdo do arquivo do e do ambiente existente selecionado `config.<newEnv>.json` para o novo ambiente que está sendo `azure.parameters.<newEnv>.json` criado.

## <a name="select-target-environment"></a>Selecionar ambiente de destino 

Você pode selecionar o ambiente de destino para todas as operações relacionadas ao ambiente. O kit de ferramentas solicita e solicita um ambiente de destino quando você tem vários ambientes remotos, conforme mostrado na imagem a seguir:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview-1.png" alt-text="add env":::

## <a name="project-folder-structure"></a>Project de pastas 

Depois de criar o projeto, você pode exibir as pastas e arquivos do projeto na área de explorador de Visual Studio Code. Além dos códigos personalizados, alguns arquivos são usados por Teams Toolkit para manter a configuração, o estado e o modelo do aplicativo. A lista a seguir fornece arquivos e descreve sua relação com vários ambientes.

- `.fx/configs`: configure arquivos que o usuário pode personalizar para o Teams app.
  - `config.<envName>.json`: arquivo de configuração por ambiente.
  - `azure.parameters.<envName>.json`: arquivo de parâmetros por ambiente para provisionamento de bicep do Azure.
  - `projectSettings.json`: configurações globais do projeto , que se aplicam a todos os ambientes.
  - `localSettings.json`: arquivo de configuração de depuração local.
- `.fx/states`: resultado de provisionamento gerado pelo Toolkit.
  - `state.<envName>.json`: arquivo de saída de provisionamento por ambiente.
  - `<env>.userdata`: dados de usuário confidenciais por ambiente para a saída de provisionamento.
- `templates`
  - `appPackage`: arquivos de modelo de manifesto do aplicativo.
  - `azure`: Arquivos de modelo Bicep.

## <a name="customize-the-provision"></a>Personalizar a provisão 

Teams Toolkit permite alterar os arquivos de configuração e os arquivos de modelo para personalizar a provisão de recursos em cada ambiente.

A tabela a seguir lista os cenários comuns com suporte para provisionamento personalizado e onde personalizar:

| Cenários | Local| Descrição |
| --- | --- | --- |
| Personalizar o Recurso do Azure | <ul> <li>Arquivos Bicep em `templates/azure` .</li> <li>`.fx/azure.parameters.<envName>.json`.</li></ul> | [Personalizar ARM parâmetros e modelos.](provision.md#customize-arm-parameters-and-templates) |
| Reutilizar o aplicativo AAD existente para Teams app | <ul> <li>`auth` seção em `.fx/config.<envName>.json` .</li> </ul> |  [Use um aplicativo de AAD existente para seu Teams app](provision.md#use-an-existing-aad-app-for-your-teams-app). |
| Reutilizar o aplicativo AAD existente para bot | <ul> <li>`bot` seção em `.fx/config.<envName>.json` .</li> </ul> | [Use um aplicativo de AAD existente para seu bot](provision.md#use-an-existing-aad-app-for-your-bot). |
| Ignorar a adição de usuários durante o provisionamento SQL | <ul> <li>`skipAddingSqlUser` propriedade em `.fx/config.<envName>.json` .</li> </ul> | [Ignore a adição de usuário para SQL banco de dados](provision.md#skip-adding-user-for-sql-database). |
| Personalizar manifesto do aplicativo | <ul> <li>`templates/manifest.remote.template.json`.</li> <li>`manifest` seção em `.fx/config.<envName>.json` .</li>  </ul> | [Personalizar Teams Manifesto do Aplicativo no Teams Toolkit](TeamsFx-manifest-customization.md). |

## <a name="scenarios"></a>Cenários

### <a name="scenario-1-customize-teams-app-name-for-different-environment"></a>Cenário 1: personalizar Teams nome do aplicativo para ambientes diferentes

Você pode definir o nome Teams aplicativo para `myapp(dev)` o ambiente padrão e para o ambiente de `dev` `myapp(staging)` `staging` preparação.

Execute as etapas a seguir para personalização:

- 1. Abra o arquivo config `.fx/configs/config.dev.json` .
- 2. Atualizar a propriedade de *manifesto > appName > short* para `myapp(dev)`

  As atualizações a `.fx/configs/config.dev.json` seguir são as seguinte:

  ```json
  {
      "$schema": "https://aka.ms/teamsfx-env-config-schema",
      "description": "You can customize the TeamsFx config for different environments.   Visit https://aka.ms/teamsfx-env-config to learn more about this.",
      "manifest": {
          "appName": {
              "short": "myapp(dev)"
              ...
          }
      }
      ...
  }
  ```

- 3. Crie um novo ambiente e `staging` nomee-o se ele não existir.
- 4. Abra o arquivo config `.fx/configs/config.staging.json` .
- 5. Atualize a mesma propriedade `myapp(staging)` .
- 6. Execute o comando provisionamento `dev` em e ambiente para atualizar o nome do aplicativo em `staging` ambientes remotos. Para executar o comando provisionamento com Teams Toolkit, consulte [provision](provision.md#provision-using-teams-toolkit).

### <a name="scenario-2-customize-teams-app-description-for-different-environment"></a>Cenário 2: personalizar Teams Descrição do aplicativo para ambientes diferentes

Nesse cenário, você aprenderá a definir diferentes Teams de aplicativo para diferentes ambientes:

- Para o ambiente `dev` padrão, a descrição será `my app description for dev` ;
- Para o ambiente de `staging` preparação, a descrição será `my app description for staging` ;

Execute as etapas a seguir para personalização:

- 1. Abra o arquivo config `.fx/configs/config.dev.json` .
- 2. Adicione nova propriedade de *> descrição > short* com valor `my app description for dev` .

  As atualizações a `.fx/configs/config.dev.json` seguir são as seguinte:

  ```json
  {
      "$schema": "https://aka.ms/teamsfx-env-config-schema",
      "description": "You can customize the TeamsFx config for different environments.   Visit https://aka.ms/teamsfx-env-config to learn more about this.",
      "manifest": {
          ...
          "description": {
              "short": "`my app description for dev"
              ...
          }
      }
      ...
  }
  ```

- 3. Crie um novo ambiente e nomee-o `staging` se ele não existir.
- 4. Abra o arquivo config `.fx/configs/config.staging.json` .
- 5. Adicione a mesma propriedade a `my app description for staging` .
- 6. Abra Teams de manifesto do aplicativo para remoto `templates/appPackage/manifest.remote.template.json` .
- 7. Atualize a propriedade `description > short` para usar a **variável definida** em configurar arquivos com sintaxe de bigodão `{{config.manifest.description.short}}` .
  
  As atualizações a `manifest.remote.template.json` seguir são as seguinte:

  ```json
  {
    "$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.11/MicrosoftTeams.schema.json",
    "manifestVersion": "1.11",
    "version": "1.0.0",
    ...
    "description": {
      "short": "{{config.manifest.description.short}}", 
      ...
    },
    ...
  }
  ```
- 8. Execute o comando provisionamento `dev` em ambiente e para atualizar o nome do aplicativo em `staging` ambientes remotos. Para executar o comando provisionamento com Teams Toolkit, consulte [provision](provision.md#provision-using-teams-toolkit).

### <a name="scenario-3-customize-teams-app-description-for-all-environments"></a>Cenário 3: personalizar Teams Descrição do aplicativo para todos os ambientes

Nesse cenário, você aprenderá a definir a descrição do aplicativo Teams para `my app description` todos os ambientes.

Como o Teams de manifesto do aplicativo é compartilhado em todos os ambientes, podemos atualizar o valor de descrição nele para nosso destino:

- 1. Abra Teams de manifesto do aplicativo para remoto `templates/appPackage/manifest.remote.template.json` .
- 2. Atualize a propriedade `description > short` com **cadeia de caracteres codificada** em código `my app description` .
  
  As atualizações a `manifest.remote.template.json` seguir são as seguinte:

  ```json
  {
    "$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.11/MicrosoftTeams.schema.json",
    "manifestVersion": "1.11",
    "version": "1.0.0",
    ...
    "description": {
      "short": "my app description",
      ...
    },
    ...
  }

- 3. Run provision command against **all** environment to update the app name in remote environments. To run provision command with Teams Toolkit, see [provision](provision.md#provision-using-teams-toolkit).

### Scenario 4: customize Azure resources for different environment

You can customize Azure resources for each environment, for example specify Azure Function name, by editing the environment corresponding to `.fx/configs/azure.parameters.{env}.json` file.

For more information on Bicep template and parameter files, see [provision cloud resources](provision.md)

## See also

* [Provision cloud resources](provision.md)
* [Add more cloud resources](add-resource.md)
* [Collaborate with other developers on Teams project](TeamsFx-collaboration.md)
