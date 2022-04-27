---
title: Vários ambientes do TeamsFX Teams Toolkit
author: MuyangAmigo
description: Sobre o multi-ambiente do TeamsFX
ms.author: nintan
ms.localizationpriority: medium
ms.topic: overview of multiple environment
ms.date: 11/29/2021
ms.openlocfilehash: 194c31d02424d08080dca981bb9fe6d963d0a416
ms.sourcegitcommit: 3bfd0d2c4d83f306023adb45c8a3f829f7150b1d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65073080"
---
# <a name="manage-multiple-environments"></a>Gerenciar vários ambientes

 Teams Toolkit fornece uma maneira simples de criar e gerenciar vários ambientes, provisionar e implantar artefatos no ambiente de destino para Teams App.

 Você pode executar o seguinte com os vários ambientes:

1. **Teste antes da produção**: você pode configurar vários ambientes, como desenvolvimento, teste e preparo antes de publicar um aplicativo Teams para o ambiente de produção no ciclo de vida de desenvolvimento de aplicativo moderno

2. **Gerenciar comportamentos de aplicativo em ambientes** diferentes: você pode configurar comportamentos diferentes para vários ambientes, como habilitar a telemetria no ambiente de produção, mas desabilitá-la no ambiente de desenvolvimento

## <a name="prerequisite"></a>Pré-requisito

* Instalar a [versão mais recente do Kit de Ferramentas do Teams](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension).

> [!TIP]
> Verifique se você Teams projeto de aplicativo aberto Microsoft Visual Studio código.

## <a name="create-a-new-environment"></a>Criar um novo ambiente

Depois de criar um novo projeto, Teams Toolkit por padrão cria:

* Um `local` ambiente para representar as configurações de ambiente do computador local
* Um ambiente `dev` para representar as configurações de ambiente remoto ou de nuvem

> [!NOTE]
> Cada projeto pode ter apenas um ambiente `local` , mas vários ambientes remotos.

**Para adicionar outro ambiente remoto**:

1. Selecione o **Teams** na barra lateral
2. Selecione **+Teams: crie um novo ambiente na** seção Ambiente, conforme mostrado na imagem a seguir:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/create new env.png" alt-text="criar":::

Se você tiver mais de um ambiente, precisará selecionar um ambiente existente para criar o mesmo. O comando copia o conteúdo do arquivo de `config.<newEnv>.json` e `azure.parameters.<newEnv>.json` do ambiente existente que você selecionou para o novo ambiente criado.

## <a name="select-target-environment"></a>Selecionar ambiente de destino

Você pode selecionar o ambiente de destino para todas as operações relacionadas ao ambiente. O Toolkit solicita e solicita um ambiente de destino quando você tem vários ambientes remotos, conforme mostrado na imagem a seguir:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview-1.png" alt-text="adicionar env":::

## <a name="project-folder-structure"></a>Project de pastas

Depois de criar o projeto, você pode exibir as pastas e arquivos do projeto na área de Visual Studio Code. Além dos códigos personalizados, alguns arquivos são usados pelo Teams Toolkit para manter a configuração, o estado e o modelo do aplicativo. A lista a seguir fornece arquivos e descreve sua relação com vários ambientes.

* `.fx/configs`: configurar arquivos que o usuário pode personalizar para o Teams aplicativo
  * `config.<envName>.json`: arquivo de configuração para por ambiente 
  * `azure.parameters.<envName>.json`: por arquivo de parâmetros de ambiente para provisionamento do bicep do Azure
  * `projectSettings.json`: configurações globais do projeto, que se aplicam a todos os ambientes
* `.fx/states`: resultado de provisionamento gerado pelo Toolkit
  * `state.<envName>.json`: arquivo de saída de provisionamento por ambiente
  * `<env>.userdata`: dados de usuário confidenciais por ambiente para a saída de provisionamento
* `templates`
  * `appPackage`: arquivos de modelo de manifesto do aplicativo
  * `azure`: arquivos de modelo Bicep

## <a name="customize-resource-provision"></a>Personalizar o provisionamento de recursos

Teams Toolkit permite alterar os arquivos de configuração e os arquivos de modelo para personalizar o provisionamento de recursos em cada ambiente.

A tabela a seguir lista os cenários comuns para provisionamento de recursos personalizados:

| Cenários | Local| Descrição |
| --- | --- | --- |
| Personalizar o Recurso do Azure | <ul> <li>Arquivos Bicep em `templates/azure`</li> <li>`.fx/azure.parameters.<envName>.json`</li></ul> | [Personalizar parâmetros e modelos do ARM](provision.md#customize-arm-parameters-and-templates) |
| Reutilizar o aplicativo existente do Azure AD para Teams aplicativo | <ul> <li>`auth` seção em`.fx/config.<envName>.json`</li> </ul> |  [Usar um aplicativo existente do Azure AD para seu Teams aplicativo](provision.md#use-an-existing-azure-ad-app-for-your-teams-app) |
| Reutilizar o aplicativo existente do Azure AD para bot | <ul> <li>`bot` seção em`.fx/config.<envName>.json`</li> </ul> | [Usar um aplicativo existente do Azure AD para seu bot](provision.md#use-an-existing-azure-ad-app-for-your-bot) |
| Ignorar a adição de usuário durante o provisionamento SQL | <ul> <li>`skipAddingSqlUser` propriedade in`.fx/config.<envName>.json`</li> </ul> | [Ignorar a adição de usuário para SQL banco de dados](provision.md#skip-adding-user-for-sql-database) |
| Personalizar manifesto do aplicativo | <ul> <li>`templates/manifest.template.json`</li> <li>`manifest` seção em `.fx/config.<envName>.json`</li>  </ul> | [Personalizar Teams manifesto do aplicativo no Teams Toolkit](TeamsFx-manifest-customization.md) |

## <a name="scenarios"></a>Cenários

Há quatro cenários para personalizar o provisionamento de recursos em ambientes diferentes.
<br>

<br><details>
<summary><b>Cenário 1: personalizar o Teams do aplicativo para um ambiente diferente</b></summary>

Você pode definir o nome Teams aplicativo para `myapp(dev)` o ambiente padrão e `dev` `myapp(staging)` para o ambiente de preparo`staging`.

Execute as seguintes etapas para personalização:

1. Abrir arquivo de configuração `.fx/configs/config.dev.json`
2. Atualizar a propriedade do *manifesto > appName > abreviação* de `myapp(dev)`

  As atualizações são `.fx/configs/config.dev.json` as seguintes:

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
6. Execute o comando provisionar e `dev` `staging` o ambiente para atualizar o nome do aplicativo em ambientes remotos. Para executar o comando provisionar com Teams Toolkit, consulte [provisionar](provision.md#provision-using-teams-toolkit)
</details>
<br>


<details>
<summary><b>Cenário 2: personalizar Teams descrição do aplicativo para um ambiente diferente</b></summary>

Nesse cenário, você aprenderá a definir diferentes Teams descrição do aplicativo para os diferentes ambientes:

* Para o ambiente padrão `dev`, a descrição é `my app description for dev`
* Para o ambiente de preparo `staging`, a descrição é `my app description for staging`

Execute as seguintes etapas para personalização:

1. Abrir arquivo de configuração `.fx/configs/config.dev.json`
2. Adicionar nova propriedade do *manifesto > descrição > curto* com valor `my app description for dev`

  As atualizações são `.fx/configs/config.dev.json` as seguintes:

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
5. Adicionar a mesma propriedade a `my app description for staging`
6. Abrir Teams manifesto do aplicativo`templates/appPackage/manifest.template.json`
7. Atualizar a propriedade para `description > short` usar a variável **definida em** configurar arquivos com sintaxe de bigode `{{config.manifest.description.short}}`
  
  As atualizações são `manifest.template.json` as seguintes:

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

8. Execute o comando provisionar em `dev` ambiente `staging` e ambiente para atualizar o nome do aplicativo em ambientes remotos. Para executar o comando provisionar com Teams Toolkit, consulte [provisionar](provision.md#provision-using-teams-toolkit)

</details>
<br>

<details>
<summary><b>Cenário 3: personalizar Teams descrição do aplicativo para todos os ambientes</b></summary>

Nesse cenário, você aprenderá a definir a descrição Teams aplicativo para `my app description` todos os ambientes.

Como o Teams de manifesto do aplicativo é compartilhado em todos os ambientes, podemos atualizar o valor de descrição nele para nosso destino:

1. Abrir Teams manifesto do aplicativo`templates/appPackage/manifest.template.json`
2. Atualizar a propriedade com `description > short` **cadeia de caracteres codificada** `my app description`
  
  As atualizações são `manifest.template.json` as seguintes:

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
3. Execute o comando provisionar em **todo o** ambiente para atualizar o nome do aplicativo em ambientes remotos. Para executar o comando provisionar com Teams Toolkit, consulte [provisionar](provision.md#provision-using-teams-toolkit)
<br></details>
<br>
<details>
<br><summary><b>Cenário 4: personalizar recursos do Azure para um ambiente diferente</b></summary>
Você pode personalizar os recursos do Azure para cada ambiente, por exemplo, especificar o nome da Função do Azure editando o ambiente correspondente a fx/configs/azure.parameters. {env}.json. Arquivo.

Para obter mais informações sobre arquivos de parâmetro e modelo Bicep, consulte [provisionar recursos de nuvem](provision.md)
</details> <br



## <a name="see-also"></a>Confira também

* [Provisionar recursos de nuvem](provision.md)
* [Adicionar mais recursos de nuvem](add-resource.md)
* [Colaborar com outros desenvolvedores no projeto do Teams](TeamsFx-collaboration.md)