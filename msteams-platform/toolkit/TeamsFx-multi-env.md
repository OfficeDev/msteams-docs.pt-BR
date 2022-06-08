---
title: Vários ambientes do TeamsFX no Kit de Ferramentas do Teams
author: MuyangAmigo
description: Sobre os vários-ambientes do TeamsFX
ms.author: nintan
ms.localizationpriority: medium
ms.topic: overview of multiple environment
ms.date: 11/29/2021
ms.openlocfilehash: 284cc455cdbb7a0c5b859fd4909f0c3a1a99b037
ms.sourcegitcommit: ff31cbe4840191f004d8fc61dd4fd93d35fcaecb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/07/2022
ms.locfileid: "65938944"
---
# <a name="manage-multiple-environments"></a>Gerenciar vários ambientes

 O Teams Toolkit fornece uma maneira simples de criar e gerenciar vários ambientes, provisionar e implantar artefatos no ambiente de destino para o aplicativo Teams.

 Você pode executar o seguinte com os vários ambientes:

1. **Teste antes da produção**: você pode configurar vários ambientes, como desenvolvimento, teste e preparo antes de publicar um Aplicativo do Teams no ambiente de produção no ciclo de vida de desenvolvimento de aplicativos modernos.

2. **Gerenciar comportamentos de aplicativo em ambientes** diferentes: você pode configurar comportamentos diferentes para vários ambientes, como habilitar a telemetria no ambiente de produção, mas desabilitá-la no ambiente de desenvolvimento.

## <a name="prerequisite"></a>Pré-requisito

* Instalar a [versão mais recente do Kit de Ferramentas do Teams](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension).

> [!TIP]
> Verifique se você tem um projeto de aplicativo do Teams aberto no código do Visual Studio.

## <a name="create-a-new-environment"></a>Criar um novo ambiente

Depois de criar um novo projeto, o Teams Toolkit por padrão cria:

* Um ambiente `local` para representar as configurações de ambiente do computador local
* Um ambiente `dev` para representar as configurações de ambiente remoto ou de nuvem

> [!NOTE]
> Cada projeto pode ter apenas um ambiente `local`, mas vários ambientes remotos.

**Para adicionar outro ambiente remoto**:

1. Selecione a barra **lateral de** :::image type="content" source="../assets/images/teams-toolkit-v2/add-sso/teams-toolkit-sidebar-icon.png" alt-text="adição do SSO do Teams na"::: barra de navegação esquerda.
2. Selecione **+Teams: crie um novo ambiente** na **seção** Ambiente, conforme mostrado na imagem a seguir:

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/create new env.png" alt-text="criar":::

   Se você tiver mais de um ambiente, precisará selecionar um ambiente existente para criar o mesmo. O comando copia o conteúdo do arquivo de `config.<newEnv>.json` e `azure.parameters.<newEnv>.json` do ambiente existente que você selecionou para o novo ambiente criado.

## <a name="select-target-environment"></a>Selecionar ambiente de destino

Você pode selecionar o ambiente de destino para todas as operações relacionadas ao ambiente. O Toolkit solicita um ambiente de destino quando você tem vários ambientes remotos, conforme mostrado na imagem a seguir:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview-1.png" alt-text="add env":::

## <a name="project-folder-structure"></a>Estrutura da pasta do projeto

Depois de criar o projeto, você pode exibir as pastas e os arquivos do projeto no **Explorer** no VS Code. Além dos códigos personalizados, o Kit de Ferramentas do Teams usa alguns arquivos para manter a configuração, o estado e o modelo do aplicativo. A lista a seguir fornece arquivos e descreve sua relação com vários ambientes.

* `.fx/configs`: configurar arquivos que o usuário pode personalizar para o aplicativo Teams
  * `config.<envName>.json`: arquivo de configuração por ambiente
  * `azure.parameters.<envName>.json`: arquivo de parâmetros para provisionamento do bicep do Azure por ambiente
  * `projectSettings.json`: configurações globais de projeto que se aplicam a todos os ambientes
* `.fx/states`: resultado de provisionamento gerado pelo Kit de Ferramentas
  * `state.<envName>.json`: provisionar o arquivo de saída por ambiente
  * `<env>.userdata`: dados do usuário para a saída de provisionamento por ambiente
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
| Personalizar manifesto do aplicativo | <ul> <li>`templates/manifest.template.json`</li> <li>Seção `manifest` em `.fx/config.<envName>.json`</li>  </ul> | [Visualizar manifesto do aplicativo no Kit de Ferramentas](TeamsFx-preview-and-customize-app-manifest.md)|

## <a name="scenarios"></a>Cenários

Você pode ver os cenários a seguir para personalizar o provisionamento de recursos em ambientes diferentes.
<br>

<br><details>
<summary><b>Cenário 1: Personalizar o nome do aplicativo Teams para um ambiente diferente </b></summary>

Você pode definir o nome do aplicativo Teams para `myapp(dev)` o ambiente padrão `dev` e para `myapp(staging)` o ambiente de preparo `staging`.

Siga as etapas para personalização:

1. Abra o arquivo de configuração `.fx/configs/config.dev.json`.
2. Atualize a propriedade do *> appName > abreviada* como `myapp(dev)`.

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

3. Crie um novo ambiente e nomeie-o `staging` se ele não existir.
4. Abra o arquivo de configuração `.fx/configs/config.staging.json`.
5. Atualize a mesma propriedade `myapp(staging)`.
6. Execute o comando de provisão nos ambientes `dev` e `staging` para atualizar o nome do aplicativo em ambientes remotos. Para executar o comando provisionar com o Kit de Ferramentas do Teams, consulte [provisionar](provision.md#provision-using-teams-toolkit).

</details>

<details>
<summary><b>Cenário 2: personalizar a descrição do aplicativo Teams para um ambiente diferente</b></summary>

Você pode definir uma descrição diferente do aplicativo Teams para os diferentes ambientes:

* Para o ambiente padrão `dev`, a descrição é `my app description for dev`
* Para o ambiente de preparo `staging`, a descrição é `my app description for staging`

Siga as etapas para personalização:

1. Abra o arquivo de configuração `.fx/configs/config.dev.json`.
2. Adicione uma nova propriedade do *manifesto > descrição > abreviada* com valor `my app description for dev`.

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

3. Crie um novo ambiente e nomeie-o `staging` se ele não existir.
4. Abra o arquivo de configuração `.fx/configs/config.staging.json`.
5. Adicione a mesma propriedade a `my app description for staging`.
6. Abra o modelo de manifesto do aplicativo Teams `templates/appPackage/manifest.template.json`.
7. Atualize a propriedade para `description > short` usar a **variável definida** em arquivos de configuração com sintaxe de bigode `{{config.manifest.description.short}}`.
  
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

8. Execute o comando de provisão nos ambientes `dev` e `staging` para atualizar o nome do aplicativo em ambientes remotos.

</details>

<details>
<summary><b>Cenário 3: personalizar a descrição do aplicativo Teams para todos os ambientes</b></summary>

Você pode definir a descrição do aplicativo Teams para `my app description` todos os ambientes.

Como o modelo de manifesto do aplicativo Teams é compartilhado em todos os ambientes, podemos atualizar o valor de descrição nele para nosso destino:

1. Abra o modelo de manifesto do aplicativo Teams `templates/appPackage/manifest.template.json`.
2. Atualize a propriedade `description > short` com **cadeia de caracteres embutida em código**`my app description`.
  
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

3. Execute o comando de provisão em **todos** os ambientes para atualizar o nome do aplicativo em ambientes remotos.

</details>

<details>
<br><summary><b>Cenário 4: personalizar recursos do Azure para um ambiente diferente</b></summary>
Você pode personalizar os recursos do Azure para cada ambiente, por exemplo, editar o ambiente correspondente a fx/configs/azure.parameters. Arquivo {env}.json para especificar o nome da Função do Azure.

Para obter mais informações sobre arquivos de parâmetro e modelo Bicep, consulte [provisionar recursos de nuvem](provision.md)
</details>
</br>

## <a name="see-also"></a>Confira também

* [Provisionar recursos de nuvem](provision.md)
* [Adicionar mais recursos de nuvem](add-resource.md)
* [Colaborar com outros desenvolvedores no projeto do Teams](TeamsFx-collaboration.md)
