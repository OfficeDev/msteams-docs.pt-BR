---
title: Vários ambientes do TeamsFX no Kit de Ferramentas do Teams
author: surbhigupta
description: Neste módulo, saiba mais sobre o multi-ambiente do TeamsFX, como criar um novo ambiente, selecionar o ambiente de destino e muito mais
ms.author: v-amprasad
ms.localizationpriority: medium
ms.topic: conceptual
ms.date: 11/29/2021
ms.openlocfilehash: 4a4b67399b2ec7c78fa536b06ee7faa9bb352468
ms.sourcegitcommit: ed7488415f814d0f60faa15ee8ec3d64ee336380
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2022
ms.locfileid: "67616938"
---
# <a name="manage-multiple-environments"></a>Gerenciar vários ambientes

 O Kit de Ferramentas do Microsoft Teams fornece uma maneira simples de criar e gerenciar vários ambientes, provisionar e implantar artefatos no ambiente de destino para seu Aplicativo do Microsoft Teams.

 Você pode executar o seguinte com vários ambientes:

1. **Teste antes da produção**: você pode configurar vários ambientes, como desenvolvimento, teste e preparo antes de publicar um Aplicativo do Teams no ambiente de produção no ciclo de vida de desenvolvimento de aplicativos modernos.

2. **Gerenciar comportamentos de aplicativo em ambientes** diferentes: você pode configurar comportamentos de aplicativo diferentes para vários ambientes, como habilitar a telemetria no ambiente de produção.

   > [!NOTE]
   > Verifique se a telemetria está desabilitada no ambiente de desenvolvimento.

   > [!TIP]
   > Verifique se você tem um projeto de aplicativo do Teams aberto no código do Visual Studio.

## <a name="create-new-environment"></a>Criar novo ambiente

Depois de criar um projeto, o Kit de Ferramentas do Teams configura, por padrão:

* Um ambiente `local` para representar a configuração do ambiente do computador local.
* Um ambiente `dev` para representar a configuração de ambiente remoto ou de nuvem.

> [!NOTE]
> Cada projeto pode ter apenas um ambiente `local`, mas vários ambientes remotos.

**Adicionar ambiente remoto**:

1. Selecione o **Kit de Ferramentas do Teams** :::image type="content" source="~/assets/images/teams-toolkit-v2/teams-toolkit-sidebar-icon.png" alt-text="na barra de atividades"::: na barra de atividades.
2. Selecione **+Teams: crie um novo ambiente** na **seção AMBIENTE** , conforme mostrado na imagem a seguir:

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/create new env.png" alt-text="criar novo ambiente":::

> [!Note]
> Se você tiver mais de um ambiente, precisará selecionar um ambiente existente para criar o mesmo. O comando copia o conteúdo do arquivo de `config.<newEnv>.json` e `azure.parameters.<newEnv>.json` do ambiente existente que você selecionou para o novo ambiente criado.

## <a name="target-environment"></a>Ambiente de destino

Você pode selecionar o ambiente de destino, o Kit de Ferramentas do Teams solicita que você selecione um ambiente de destino quando tiver vários ambientes remotos:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview-1.png" alt-text="add env":::

## <a name="project-folder-structure"></a>Estrutura da pasta do projeto

Depois de criar o projeto, você pode exibir as pastas e os arquivos do projeto no **Explorer** Visual Studio Code. Além dos códigos personalizados, o Kit de Ferramentas do Teams `configs`usa alguns arquivos para manter o , `states`e `templates` do aplicativo. A lista a seguir fornece arquivos e descreve sua relação com vários ambientes.

* `.fx/configs`: configura os arquivos que o usuário pode personalizar para o aplicativo Teams.
  * `config.<envName>.json`: arquivo de configuração por ambiente.
  * `azure.parameters.<envName>.json`: arquivo de parâmetros para provisionamento do bicep do Azure por ambiente.
  * `projectSettings.json`: configurações globais do projeto que se aplicam a todos os ambientes.
* `.fx/states`: provisione o resultado gerado pelo Kit de Ferramentas do Teams.
  * `state.<envName>.json`: provisionar o arquivo de saída por ambiente.
  * `<env>.userdata`: dados do usuário para a saída de provisionamento por ambiente.
* `templates`
  * `appPackage`: arquivos de modelo de manifesto do aplicativo.
  * `azure`: arquivos de modelo Bicep.

## <a name="customize-resource-provision"></a>Personalizar o provisionamento de recursos

O Teams Toolkit permite alterar os arquivos de configuração e os arquivos de modelo para personalizar o provisionamento de recursos em cada ambiente.

A tabela a seguir lista os cenários comuns para provisionamento de recursos personalizados:

| Cenários | Local| Descrição |
| --- | --- | --- |
| Personalizar o Recurso do Azure |Arquivos Bicep em `templates/azure` `.fx/azure.parameters.<envName>.json` | [Personalizar parâmetros e modelos do ARM](provision.md#customize-arm-template-files) |
| Reutilizar o aplicativo Azure AD existente para o aplicativo Teams | Seção `auth` em `.fx/config.<envName>.json`|  [Usar um aplicativo Azure AD existente para seu aplicativo Teams](provision.md#use-an-existing-azure-ad-app-for-your-teams-app) |
| Reutilizar o aplicativo Azure AD existente para bot |Seção `bot` em `.fx/config.<envName>.json`| [Usar um aplicativo Azure AD existente para seu bot](provision.md#use-an-existing-azure-ad-app-for-your-bot) |
| Ignorar a adição de usuário durante o provisionamento SQL |Propriedade `skipAddingSqlUser` em `.fx/config.<envName>.json`| [Ignorar a adição de usuário para o banco de dados SQL](provision.md#skip-adding-user-for-sql-database) |
| Personalizar manifesto do aplicativo |`templates/manifest.template.json` arquivo na `manifest` seção em `.fx/config.<envName>.json`| [Visualizar manifesto do aplicativo no Kit de Ferramentas](TeamsFx-preview-and-customize-app-manifest.md)|

## <a name="scenarios"></a>Cenários

Você pode ver os cenários a seguir para personalizar o provisionamento de recursos em ambientes diferentes.
<br>

<br><details>
<summary><b>Cenário 1: Personalizar o nome do aplicativo Teams para um ambiente diferente </b></summary>

Você pode definir o nome do aplicativo Teams para `myapp(dev)` o ambiente padrão `dev` e para `myapp(staging)` o ambiente de preparo `staging`.

Etapas para personalização:

1. Abra o arquivo de configuração `.fx/configs/config.dev.json`.
2. Atualize a propriedade de **`manifest`** > **`appName`** > **abreviação** de **`myapp(dev)`**.

  As atualizações a serem `.fx/configs/config.dev.json` :

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

3. Você pode criar um novo ambiente e nomeá-lo `staging` se ele não existir.
4. Abra o arquivo de configuração `.fx/configs/config.staging.json`.
5. Atualize a mesma propriedade `myapp(staging)`.
6. Agora você pode executar o comando provisionar e `dev` o `staging` ambiente para atualizar o nome do aplicativo em ambientes remotos. Para executar o comando provisionar com o Kit de Ferramentas do Teams, consulte [provisionar](provision.md#provision-using-teams-toolkit).

</details>

<details>
<summary><b>Cenário 2: personalizar a descrição do aplicativo Teams para um ambiente diferente</b></summary>

Você pode definir uma descrição diferente do aplicativo Teams para os diferentes ambientes:

* Para o ambiente padrão `dev`, a descrição é `my app description for dev`.
* Para o ambiente de preparo `staging`, a descrição é `my app description for staging`.

Etapas para personalização:

1. Abra o arquivo de configuração `.fx/configs/config.dev.json`.
2. Adicionar nova propriedade de **`manifest`** > **`short`** > **`description`** com valor .**`my app description for dev`**

  As atualizações a serem `.fx/configs/config.dev.json` :

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
7. Atualize a propriedade para **`description`** > **`short`** usar a **variável definida** em arquivos de configuração com sintaxe de bigode **`{{config.manifest.description.short}}`**.
  
  As atualizações a serem `manifest.template.json` :

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

8. Agora você pode executar o comando provisionar e `dev` o `staging` ambiente para atualizar o nome do aplicativo em ambientes remotos.

</details>

<details>
<summary><b>Cenário 3: personalizar a descrição do aplicativo Teams para todos os ambientes</b></summary>

Você pode definir a descrição do aplicativo Teams para `my app description` todos os ambientes.

Como o modelo de manifesto do aplicativo Teams é compartilhado em todos os ambientes, podemos atualizar o valor de descrição nele para nosso destino:

1. Abra o modelo de manifesto do aplicativo Teams `templates/appPackage/manifest.template.json`.
2. Atualize a propriedade **`description`** > **`short`** com cadeia de caracteres embutida em código.**`my app description`**
  
  As atualizações a serem `manifest.template.json` :

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

3. Agora você pode executar o comando provisionar em **todo o** ambiente para atualizar o nome do aplicativo em ambientes remotos.

</details>

<details>
<br><summary><b>Cenário 4: Personalizar recursos do Azure para um ambiente diferente</b></summary>

Você pode personalizar os recursos do Azure para cada ambiente, por exemplo, editar o ambiente correspondente a fx/configs/azure.parameters. Arquivo {env}.json para especificar o nome da Função do Azure.

Para obter mais informações sobre arquivos de parâmetro e modelo Bicep, consulte [provisionar recursos de nuvem](provision.md).
</details>
</br>

## <a name="see-also"></a>Confira também

* [Provisionar recursos de nuvem](provision.md)
* [Adicionar mais recursos de nuvem](add-resource.md)
* [Colaborar com outros desenvolvedores no projeto do Teams](TeamsFx-collaboration.md)
* [Testar o comportamento do aplicativo em um ambiente diferente](test-app-behavior.md)
