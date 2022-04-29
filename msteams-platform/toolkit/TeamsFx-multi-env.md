---
title: Vários ambientes do TeamsFX no Kit de Ferramentas do Teams
author: MuyangAmigo
description: Sobre os vários-ambientes do TeamsFX
ms.author: nintan
ms.localizationpriority: high
ms.topic: overview of multiple environment
ms.date: 11/29/2021
ms.openlocfilehash: b9719add5036ae533ce6d7c395ab95a5905bcbb8
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111861"
---
# <a name="manage-multiple-environments"></a>Gerenciar vários ambientes

 O Teams Toolkit fornece uma maneira simples de criar e gerenciar vários ambientes, provisionar e implantar artefatos no ambiente de destino para o aplicativo Teams.

 Você pode executar o seguinte com os vários ambientes:

1. **Testar antes da produção**: você pode configurar vários ambientes, como desenvolvimento, teste e preparo antes de publicar um aplicativo Teams para o ambiente de produção no ciclo de vida de desenvolvimento de um aplicativo moderno

2. **Gerenciar comportamentos de aplicativo em ambientes diferentes**: você pode configurar comportamentos diferentes para vários ambientes, como habilitar a telemetria no ambiente de produção, mas desabilitá-la no ambiente de desenvolvimento

## <a name="prerequisite"></a>Pré-requisito

* Instalar a [versão mais recente do Kit de Ferramentas do Teams](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension).

> [!TIP]
> Verifique se você projeto de aplicativo Teams aberto no código do Microsoft Visual Studio.

## <a name="create-a-new-environment"></a>Criar um novo ambiente

Depois de criar um novo projeto, o Teams Toolkit por padrão cria:

* Um ambiente `local` para representar as configurações de ambiente do computador local
* Um ambiente `dev` para representar as configurações de ambiente remoto ou de nuvem

> [!NOTE]
> Cada projeto pode ter apenas um ambiente `local`, mas vários ambientes remotos.

**Para adicionar outro ambiente remoto**:

1. Selecione o ícone do **Teams** na barra lateral
2. Selecione **+Teams: criar novo ambiente** na seção Ambiente, conforme mostrado na imagem a seguir:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/create new env.png" alt-text="criar":::

Se você tiver mais de um ambiente, precisará selecionar um ambiente existente para criar o mesmo. O comando copia o conteúdo do arquivo de `config.<newEnv>.json` e `azure.parameters.<newEnv>.json` do ambiente existente que você selecionou para o novo ambiente criado.

## <a name="select-target-environment"></a>Selecionar ambiente de destino

Você pode selecionar o ambiente de destino para todas as operações relacionadas ao ambiente. O Toolkit solicita um ambiente de destino quando você tem vários ambientes remotos, conforme mostrado na imagem a seguir:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview-1.png" alt-text="add env":::

## <a name="project-folder-structure"></a>Estrutura da pasta do projeto

Depois de criar o projeto, você pode exibir as pastas e arquivos do projeto na área do Visual Studio Code. Além dos códigos personalizados, alguns arquivos são usados pelo Teams Toolkit para manter a configuração, o estado e o modelo do aplicativo. A lista a seguir fornece arquivos e descreve sua relação com vários ambientes.

* `.fx/configs`: configurar arquivos que o usuário pode personalizar para o aplicativo Teams
  * `config.<envName>.json`: arquivo de configuração por ambiente 
  * `azure.parameters.<envName>.json`: por arquivo de parâmetros de ambiente para provisionamento do Bicep do Azure
  * `projectSettings.json`: configurações globais do projeto, que se aplicam a todos os ambientes
* `.fx/states`: resultado de provisionamento gerado pelo Toolkit
  * `state.<envName>.json`: arquivo de saída de provisionamento por ambiente
  * `<env>.userdata`: dados de usuário confidenciais por ambiente para saída de provisionamento
* `templates`
  * `appPackage`: arquivos de modelo de manifesto do aplicativo
  * `azure`: arquivos de modelo Bicep

## <a name="customize-resource-provision"></a>Personalizar o provisionamento de recursos

O Teams Toolkit permite alterar os arquivos de configuração e os arquivos de modelo para personalizar o provisionamento de recursos em cada ambiente.

A tabela a seguir lista os cenários comuns para provisionamento de recursos personalizados:

| Cenários | Local| Descrição |
| --- | --- | --- |
| Personalizar o Recurso do Azure | <ul> <li>Arquivos Bicep em `templates/azure`</li> <li>`.fx/azure.parameters.<envName>.json`</li></ul> | [Personalizar parâmetros e modelos do ARM](provision.md#customize-arm-parameters-and-templates) |
| Reutilizar o aplicativo Azure AD existente para o aplicativo Teams | <ul> <li>Seção `auth` em `.fx/config.<envName>.json`</li> </ul> |  [Usar um aplicativo Azure AD existente para seu aplicativo Teams](provision.md#use-an-existing-azure-ad-app-for-your-teams-app) |
| Reutilizar o aplicativo Azure AD existente para bot | <ul> <li>Seção `bot` em `.fx/config.<envName>.json`</li> </ul> | [Usar um aplicativo Azure AD existente para seu bot](provision.md#use-an-existing-azure-ad-app-for-your-bot) |
| Ignorar a adição de usuário durante o provisionamento SQL | <ul> <li>Propriedade `skipAddingSqlUser` em `.fx/config.<envName>.json`</li> </ul> | [Ignorar a adição de usuário para o banco de dados SQL](provision.md#skip-adding-user-for-sql-database) |
| Personalizar manifesto do aplicativo | <ul> <li>`templates/manifest.template.json`</li> <li>Seção `manifest` em `.fx/config.<envName>.json`</li>  </ul> | [Personalizar Manifesto do Aplicativo Teams no Teams Toolkit](TeamsFx-manifest-customization.md) |

## <a name="scenarios"></a>Cenários

Há quatro cenários para personalizar o provisionamento de recursos em ambientes diferentes.
<br>

<br><details>
<summary><b>Cenário 1: personalizar o aplicativo Teams para um ambiente diferente</b></summary>

Você pode definir o nome do aplicativo Teams para `myapp(dev)` dos ambientes padrões `dev` e `myapp(staging)` para o ambiente de preparo `staging`.

Execute as seguintes etapas para personalização:

1. Abrir arquivo de configuração `.fx/configs/config.dev.json`
2. Atualizar a propriedade de *manifesto > appName > abreviação* para `myapp(dev)`

  As atualizações para `.fx/configs/config.dev.json` são as seguintes:

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

3. Criar um novo ambiente e nomeá-lo `staging` se ele não existir
4. Abrir arquivo de configuração `.fx/configs/config.staging.json`
5. Atualizar a mesma propriedade `myapp(staging)`
6. Execute o comando de provisão nos ambientes `dev` e `staging` para atualizar o nome do aplicativo em ambientes remotos. Para executar o comando provisionar com o Teams Toolkit, confira[provisionar](provision.md#provision-using-teams-toolkit)
</details>
<br>


<details>
<summary><b>Cenário 2: personalizar a descrição do aplicativo Teams para um ambiente diferente</b></summary>

Nesse cenário, você aprenderá a definir diferentes descrições do aplicativo Teams para os diferentes ambientes:

* Para o ambiente padrão `dev`, a descrição é `my app description for dev`
* Para o ambiente de preparo `staging`, a descrição é `my app description for staging`

Execute as seguintes etapas para personalização:

1. Abrir arquivo de configuração `.fx/configs/config.dev.json`
2. Adicionar nova propriedade de *manifesto > descrição > abreviação* com valor `my app description for dev`

  As atualizações para `.fx/configs/config.dev.json` são as seguintes:

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

3. Criar um novo ambiente e nomeá-lo `staging` se ele não existir
4. Abrir arquivo de configuração `.fx/configs/config.staging.json`
5. Adicionar a mesma propriedade para `my app description for staging`
6. Abrir o modelo de manifesto do aplicativo Teams`templates/appPackage/manifest.template.json`
7. Atualizar a propriedade `description > short` para usar a **variável** definida em configurar arquivos com sintaxe de mustache `{{config.manifest.description.short}}`
  
  As atualizações para `manifest.template.json` são as seguintes:

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

8. Execute o comando de provisão nos ambientes `dev` e `staging` para atualizar o nome do aplicativo em ambientes remotos. Para executar o comando de provisão com o Teams Toolkit, confira [provisionar](provision.md#provision-using-teams-toolkit)

</details>
<br>

<details>
<summary><b>Cenário 3: personalizar a descrição do aplicativo Teams para todos os ambientes</b></summary>

Nesse cenário, você aprenderá a definir a descrição do aplicativo Teams para `my app description` em todos os ambientes.

Como o modelo de manifesto do aplicativo Teams é compartilhado em todos os ambientes, podemos atualizar o valor de descrição nele para nosso destino:

1. Abrir o modelo de manifesto do aplicativo Teams`templates/appPackage/manifest.template.json`
2. Atualizar a propriedade `description > short` com **cadeia de caracteres codificada** `my app description`
  
  As atualizações para `manifest.template.json` são as seguintes:

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
 ```
3. Execute o comando de provisão em **todos** os ambientes para atualizar o nome do aplicativo em ambientes remotos. Para executar o comando de provisão com o Teams Toolkit, confira [provisionar](provision.md#provision-using-teams-toolkit)
<br></details>
<br>
<details>
<br><summary><b>Cenário 4: personalizar recursos do Azure para um ambiente diferente</b></summary>
Você pode personalizar os recursos do Azure para cada ambiente, por exemplo, especificar o nome da Função do Azure editando o ambiente correspondente para fx/configs/azure.parameters. {env}.json. arquivo.

Para obter mais informações sobre arquivos de parâmetro e modelo Bicep, confira [provisionar recursos de nuvem](provision.md)
</details> <br



## <a name="see-also"></a>Confira também

* [Provisionar recursos de nuvem](provision.md)
* [Adicionar mais recursos de nuvem](add-resource.md)
* [Colaborar com outros desenvolvedores no projeto do Teams](TeamsFx-collaboration.md)