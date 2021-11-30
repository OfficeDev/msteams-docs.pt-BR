---
title: Vários ambientes teamsFX em Teams Toolkit
author: MuyangAmigo
description: Sobre o ambiente multi TeamsFX
ms.author: nintan
ms.localizationpriority: medium
ms.topic: overview of multiple environment
ms.date: 11/29/2021
ms.openlocfilehash: 0e53d90dd6ead30200dd1f07ba9a100a3d1f4ca1
ms.sourcegitcommit: f1e6f90fb6f7f5825e55a6d18ccf004d0091fb6d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2021
ms.locfileid: "61227913"
---
# <a name="manage-multiple-environments-in-teams-toolkit"></a>Gerenciar vários ambientes em Teams Toolkit

 Teams Toolkit fornece uma maneira simples para os desenvolvedores criarem e gerenciarem vários ambientes, provisionar e implantar artefatos no ambiente de destino para Teams App.

 Com vários ambientes, os desenvolvedores podem:

1. **Teste antes** da produção : é uma prática comum configurar vários ambientes (desenvolvimento, teste, preparação) antes de publicar um aplicativo Teams para o ambiente de produção no ciclo de vida moderno do desenvolvimento de aplicativos.

2. **Gerenciar comportamentos de aplicativos** em ambientes diferentes: os desenvolvedores podem definir comportamentos diferentes para ambientes diferentes, como desenvolvedores, talvez queira habilitar a telemetria no ambiente de produção, mas desabilitá-la no ambiente de desenvolvimento.

## <a name="prerequisite"></a>Pré-requisito

* [Instale Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) versão v3.0.0+.

>[!TIP]
> Você já deve ter um projeto Teams aplicativo aberto em código VS.

## <a name="create-a-new-environment"></a>Criar um novo ambiente

Depois de criar um novo projeto, Teams Toolkit por padrão cria:

- Um `local` ambiente para representar as configurações de ambiente de máquina local.
- Um `dev` ambiente para representar as configurações de ambiente remoto/de nuvem.

> [!NOTE]
> Cada projeto pode ter apenas um `local` ambiente, mas vários ambientes remotos.

Para adicionar outro ambiente remoto, selecione o ícone Teams na barra lateral, clique no botão Mais em Ambiente e siga as perguntas a ser publicadas conforme mostrado na imagem a seguir:

![add-env](./images/create-env.png)

> [!NOTE]
> Se você tiver mais de um ambiente existente, será necessário selecionar um ambiente existente para criar o ambiente. O comando copiará o conteúdo do arquivo do e do ambiente existente selecionado `config.<newEnv>.json` para o novo ambiente que está sendo `azure.parameters.<newEnv>.json` criado.

## <a name="select-target-environment"></a>Selecionar ambiente de destino 

Com o conceito de ambiente introduzido Teams Toolkit, para todas as operações relacionadas ao ambiente, você pode selecionar o ambiente de destino para executar as operações. O kit de ferramentas solicitará e solicitará um ambiente de destino quando você tiver vários ambientes remotos, conforme mostrado na imagem a seguir:

![selecionar env](./images/select-env.png)

## <a name="project-folder-structure"></a>Project de pastas 

Depois de criar o projeto, você pode exibir as pastas e arquivos do projeto na área Explorer de Visual Studio Code. Além dos códigos personalizados, alguns arquivos são usados por Teams Toolkit para manter a configuração, o estado e o modelo do aplicativo. Lista a seguir esses arquivos e descreve sua relação com vários ambientes.

- `.fx/configs`: config arquivos que o usuário pode personalizar para o Teams app.
  - `config.<envName>.json`: arquivo de configuração por ambiente.
  - `azure.parameters.<envName>.json`: arquivo de parâmetros por ambiente para provisionamento do Azure BICEP.
  - `projectSettings.json`: configurações globais do projeto , que se aplicam a todos os ambientes.
  - `localSettings.json`: arquivo de configuração de depuração local.
- `.fx/states`: resultado de provisionamento gerado pelo Toolkit.
  - `state.<envName>.json`: arquivo de saída de provisionamento por ambiente.
  - `<env>.userdata`: dados de usuário confidenciais por ambiente para a saída de provisionamento.
- `templates`
  - `appPackage`: arquivos de modelo de manifesto do aplicativo.
  - `azure`: Arquivos de modelo BICEP.

## <a name="customize-the-provision"></a>Personalizar a provisão 

Teams Toolkit permite alterar os arquivos de configuração e os arquivos de modelo para personalizar a provisão de recursos em cada ambiente.

A tabela a seguir lista os cenários comuns com suporte para provisionamento personalizado e onde personalizar:

| Cenários | Onde personalizar | Como personalizar |
| --- | --- | --- |
| Personalizar o Recurso do Azure | <ul> <li>Arquivos BICEP em `templates/azure` .</li> <li>`.fx/azure.parameters.<envName>.json`.</li></ul> | Consulte personalizar [ARM parâmetros e modelos para](provision.md#customize-arm-parameters-and-templates) obter mais detalhes. |
| Reutilando o aplicativo AAD existente para Teams app | <ul> <li>`auth` seção em `.fx/config.<envName>.json` .</li> </ul> | Consulte usar [um aplicativo de AAD existente para seu aplicativo Teams para](provision.md#use-an-existing-aad-app-for-your-teams-app) obter mais detalhes. |
| Reutilando o aplicativo AAD existente para bot | <ul> <li>`bot` seção em `.fx/config.<envName>.json` .</li> </ul> | Consulte usar [um aplicativo de AAD existente para seu bot](provision.md#use-an-existing-aad-app-for-your-bot) para obter mais detalhes. |
| Ignorar a adição de usuário ao provisionar SQL | <ul> <li>`skipAddingSqlUser` propriedade em `.fx/config.<envName>.json` .</li> </ul> | Consulte skip [adding user for SQL database para](provision.md#skip-adding-user-for-sql-database) obter mais detalhes. |
| Personalizar Manifesto do Aplicativo | <ul> <li>`templates/manifest.remote.template.json`.</li> <li>`manifest` seção em `.fx/config.<envName>.json` .</li>  </ul> | Consulte customize [Teams App Manifest in Teams Toolkit](TeamsFx-manifest-customization.md) para obter mais detalhes. |

## <a name="scenarios"></a>Cenários

### <a name="scenario-1-customize-teams-app-name-for-different-environment"></a>Cenário 1: personalizar Teams nome do aplicativo para ambientes diferentes

Neste exemplo, você aprenderá como definir o nome do aplicativo Teams para o ambiente padrão e para o ambiente `myapp(dev)` `dev` de `myapp(staging)` `staging` preparação.

Siga as etapas para personalização:

- Etapa 1: abrir arquivo de configuração `.fx/configs/config.dev.json` .
- Etapa 2: atualizar a propriedade *de manifesto > appName > short* para `myapp(dev)`

  Atualizações para `.fx/configs/config.dev.json` :

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

- Etapa 3: criar um novo ambiente `staging` nomeado se ele não existir.
- Etapa 4: abrir arquivo de configuração `.fx/configs/config.staging.json` .
- Etapa 5: atualizar a mesma propriedade da etapa 2 para `myapp(staging)` .
- Etapa 6: executar o comando provisionamento e `dev` o ambiente para atualizar o nome do aplicativo em `staging` ambientes remotos. Para executar o comando provisionamento com Teams Toolkit. Para obter mais informações, consulte [este documento](provision.md#provision-using-teams-toolkit).

### <a name="scenario-2-customize-teams-app-description-for-different-environment"></a>Cenário 2: personalizar Teams Descrição do aplicativo para ambientes diferentes

Nesse cenário, você aprenderá a definir diferentes Teams Descrição do aplicativo para ambientes diferentes:

- Para o ambiente `dev` padrão, a descrição será `my app description for dev` ;
- Para o ambiente de `staging` preparação, a descrição será `my app description for staging` ;

Etapas para fazer a personalização:

- Etapa 1: abrir arquivo de configuração `.fx/configs/config.dev.json` .
- Etapa 2: Adicionar nova propriedade de *> descrição > short* com valor `my app description for dev` .

  Atualizações para `.fx/configs/config.dev.json`

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

- Etapa 3: criar um novo ambiente chamado `staging` se ele não existir.
- Etapa 4: abrir arquivo de configuração `.fx/configs/config.staging.json` .
- Etapa 5: adicionar a mesma propriedade da etapa 2 a `my app description for staging` .
- Etapa 6: abra Teams de manifesto do aplicativo para remoto `templates/appPackage/manifest.remote.template.json` .
- Etapa 7: atualizar a propriedade `description > short` para usar a **variável** definida em arquivos de configuração com sintaxe de sintaxe de bigome `{{config.manifest.description.short}}` .
  
  Atualizações para `manifest.remote.template.json` :

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
- Etapa 8: executar o comando provisionamento em ambiente e para atualizar o nome `dev` `staging` do aplicativo em ambientes remotos. Para saber como executar o comando provisionamento com Teams Toolkit, consulte [este documento para](provision.md#provision-using-teams-toolkit) obter mais detalhes.

### <a name="scenario-3-customize-teams-app-description-for-all-environments"></a>Cenário 3: personalizar Teams Descrição do aplicativo para todos os ambientes

Nesse cenário, você aprenderá a definir a descrição do aplicativo Teams para `my app description` todos os ambientes.

Como o Teams de manifesto do aplicativo é compartilhado em todos os ambientes, podemos atualizar o valor de descrição nele para nosso destino:

- Etapa 1: abra Teams de manifesto do aplicativo para remoto `templates/appPackage/manifest.remote.template.json` .
- Etapa 2: atualizar a propriedade `description > short` com **cadeia de caracteres codificada.** `my app description`
  
  Atualizações para `manifest.remote.template.json` :

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

- Step 3: run provision command against **all** environment to update the app name in remote environments. For how to run provision command with Teams Toolkit, you can refer to [this document](provision.md#provision-using-teams-toolkit) for more details.

### Scenario 4: customize Azure resources for different environment

You can customize Azure resources for each environment, for example specifying Azure Function name, by editing the environment corresponding `.fx/configs/azure.parameters.{env}.json` file.

For more information on BICEP template and parameter files, see [provision cloud resources](provision.md)

## See also

> [!div class="nextstepaction"]
> [Provision cloud resources](provision.md)

> [!div class="nextstepaction"]
> [Add more cloud resources](add-resource.md)

> [!div class="nextstepaction"]
> [Collaborate with other developers on Teams project](TeamsFx-collaboration.md)
