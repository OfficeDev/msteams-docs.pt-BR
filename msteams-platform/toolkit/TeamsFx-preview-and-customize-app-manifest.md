---
title: Personalizar o Manifesto do Aplicativo Teams no Kit de Ferramentas do Teams
author: zyxiaoyuer
description: Neste módulo, saiba como editar, visualizar e personalizar o Manifesto do Aplicativo teams em um ambiente diferente.
ms.author: nliu
ms.localizationpriority: medium
ms.topic: overview
ms.date: 05/13/2022
zone_pivot_groups: teams-app-platform
ms.openlocfilehash: 02bbcc86c769f8ebff87803b6a12bf882e214bf6
ms.sourcegitcommit: de7496f9586316bed12d115cd3e4c18ba0854d4f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2022
ms.locfileid: "67780698"
---
# <a name="customize-teams-app-manifest"></a>Personalizar o manifesto do aplicativo Teams

O manifesto do aplicativo Teams descreve como seu aplicativo se integra ao produto Microsoft Teams.

::: zone pivot="visual-studio-code"

## <a name="customize-teams-app-manifest-for-visual-studio-code"></a>Personalizar o manifesto do aplicativo Teams para Visual Studio Code

O manifesto do aplicativo Teams descreve como seu aplicativo se integra ao produto Microsoft Teams. Para obter mais informações sobre Manifesto, consulte [o esquema de manifesto do aplicativo para o Teams](../resources/schema/manifest-schema.md). Esta seção cobre:

* [Visualizar arquivo de manifesto no ambiente local](#preview-manifest-file-in-local-environment)
* [Visualizar arquivo de manifesto no ambiente remoto](#preview-manifest-file-in-remote-environment)
* [Sincronizar alterações locais no Portal do Desenvolvedor](#sync-local-changes-to-developer-portal)
* [Personalizar o manifesto do aplicativo Teams](#customize-your-teams-app-manifest)
* [Validar manifesto](#validate-manifest)

O arquivo de modelo do manifesto `manifest.template.json` está disponível na pasta `templates/appPackage` após o scaffolding. O arquivo de modelo com espaços reservados e os valores reais são resolvidos pelo Kit de Ferramentas do Teams usando arquivos em `.fx/configs` e `.fx/states` para ambientes diferentes.

Para visualizar o manifesto com conteúdo real, o Kit de Ferramentas do Teams gera arquivos de manifesto de visualização na `build/appPackage` pasta:

```text
└───build
    └───appPackage
        ├───appPackage.{env}.zip - Zipped app package of remote Teams app
        ├───appPackage.local.zip - Zipped app package of local Teams app
        ├───manifest.{env}.json  - Previewed manifest of remote Teams app
        └───manifest.local.json  - Previewed manifest of local Teams app
```

Você pode visualizar o arquivo de manifesto em ambientes locais e remotos.

* [Visualizar arquivo de manifesto no ambiente local](#preview-manifest-file-in-local-environment)
* [Visualizar arquivo de manifesto no ambiente remoto](#preview-manifest-file-in-remote-environment)

## <a name="preview-manifest-file-in-local-environment"></a>Visualizar arquivo de manifesto no ambiente local

Para visualizar o arquivo de manifesto no ambiente local, você pode pressionar **F5** para executar a depuração local. Ele gera configurações locais padrão para você e o pacote do aplicativo e o manifesto de visualização são compilados na `build/appPackage` pasta.

Você também pode visualizar o arquivo de manifesto local por dois métodos

* Usando a opção de visualização no codelens
* Usando a opção **de pacote de metadados do Zip Teams**

As etapas a seguir ajudam a visualizar o arquivo de manifesto local usando a opção de visualização no codelens:

1. Selecione **Visualizar** nos codelens do `manifest.template.json` arquivo.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/preview-23.png" alt-text="Visualização":::

1. Selecione **local**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-env1.png" alt-text="Selecionar environment1":::

As etapas a seguir ajudam a visualizar o arquivo de manifesto local usando a opção de pacote de **metadados do Zip Teams** :

1. Selecione `manifest.template.json` o arquivo.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-manifest-json.png" alt-text="Selecione Manifesto":::

1. Selecione o ícone do Kit de Ferramentas do :::image type="icon" source="../assets/images/teams-toolkit-v2/teams-toolkit-sidebar-icon.PNG"::: Teams na Visual Studio Code de ferramentas.

1. Selecione o **pacote de metadados do Zip Teams** em **DEPLOYMENT**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/teams-metadata-package.png" alt-text="Selecionar pacote de metadados do Teams":::

1. Selecione **local**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-env1.png" alt-text="Selecionar ambiente":::

A visualização local é exibida conforme mostrado na imagem:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/preview-23.png" alt-text="Visualização":::

## <a name="preview-manifest-file-in-remote-environment"></a>Visualizar arquivo de manifesto no ambiente remoto

Para visualizar o arquivo de manifesto usando Visual Studio Code:

* Selecione **Provisionar na nuvem em** **DESENVOLVIMENTO na** extensão kit de ferramentas do Teams
  
  :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/provision.png" alt-text="Provisionar recurso de nuvem":::

Para visualizar o arquivo de manifesto usando o comando palatte:

* Disparar **o Teams: provisionar na nuvem da** paleta de comandos.

  :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/command palatte.png" alt-text="Provisionar recurso de nuvem usando o paladar de comando":::

Ele gera a configuração para o aplicativo Remoto do Teams e compila o pacote e o manifesto de visualização na `build/appPackage` pasta.

Você também pode visualizar o arquivo de manifesto por dois métodos no ambiente remoto

* Usando a opção de visualização no codelens
* Usando a opção **de pacote de metadados do Zip Teams**

As etapas a seguir ajudam a visualizar o arquivo de manifesto usando a opção de visualização no codelens:

1. Selecione **Visualizar** nos codelens do `manifest.template.json` arquivo.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/preview-23.png" alt-text="Visualização":::

1. Selecione seu ambiente.

   > [!NOTE]
   > Se houver mais de um ambiente, você precisará selecionar o ambiente que você quer visualizar, conforme mostrado na imagem:

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview-1.png" alt-text="Adicionar env":::

As etapas a seguir ajudam a visualizar o arquivo de manifesto usando a opção de pacote de **metadados do Zip Teams** no ambiente remoto:

1. Selecione `manifest.template.json` o arquivo.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-manifest-json.png" alt-text="Selecione Manifesto":::

1. Selecione o ícone do Kit de Ferramentas do :::image type="icon" source="../assets/images/teams-toolkit-v2/teams-toolkit-sidebar-icon.PNG"::: Teams na Visual Studio Code de ferramentas.

1. Selecione o **pacote de metadados do Zip Teams** em **DEPLOYMENT**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/teams-metadata-package.png" alt-text="Selecionar pacote de metadados do Teams":::

1. Selecione seu ambiente.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview-1.png" alt-text="Adicionar env":::

   > [!NOTE]
   > Se houver mais de um ambiente, você precisará selecionar o ambiente que você quer visualizar, conforme mostrado na imagem:

## <a name="sync-local-changes-to-developer-portal"></a>Sincronizar alterações locais no Portal do Desenvolvedor

Depois de visualizar o arquivo de manifesto, você pode sincronizar as alterações locais no Portal do Desenvolvedor das seguintes maneiras:

> [!NOTE]
> Para obter mais informações sobre o Portal do Desenvolvedor, consulte [o Portal do Desenvolvedor para Teams](../concepts/build-and-test/teams-developer-portal.md).

1. Implantar o manifesto do aplicativo Teams.

   Você pode implantar o manifesto do aplicativo Teams de qualquer uma das seguintes maneiras:

   * Vá para `manifest.template.json` o arquivo e clique com o botão direito do mouse para selecionar no `Deploy Teams app manifest` menu de contexto.

      :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/deploy-manifest.png" alt-text="Implantar manifesto":::

   * Disparar da `Teams: Deploy Teams app manifest` paleta de comandos.

      :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/deploy-command.png" alt-text="Implantar da paleta de comandos":::

2. Atualizar para a plataforma teams.

   Você pode atualizar para a plataforma Teams de qualquer uma das seguintes maneiras:

   * Selecione **Atualizar para a plataforma Teams** no canto superior esquerdo de `manifest.{env}.json`.

   * Disparar **o Teams: atualizar o manifesto para a plataforma Teams** na barra de menus de `manifest.{env}.json`.

      :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/update-to-teams.png" alt-text="Atualizar para equipes":::

Você também pode disparar **o Teams: atualizar o manifesto para a plataforma Teams** na paleta de comandos:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/pre.png" alt-text="modo de exibição em árvore":::

> [!NOTE]
> O gatilho do codelens do editor ou da barra de menus atualiza o arquivo de manifesto atual para a plataforma teams. O gatilho da paleta de comandos requer a seleção do ambiente de destino.

 Comando da CLI:

``` bash
        teamsfx deploy manifest --include-app-manifest yes
```

---

> [!NOTE]
> As atualizações de alteração no Portal de Desenvolvimento. Todas as atualizações manuais no Portal de Desenvolvimento são substituídas.

Se o arquivo de manifesto estiver desatualizado devido à alteração do arquivo de configuração ou à alteração do modelo, selecione qualquer uma das seguintes ações:

* **Somente visualização**: o arquivo de manifesto local é substituído de acordo com a configuração atual.
* **Versão prévia e atualização**: o arquivo de manifesto local é substituído de acordo com a configuração atual e também atualizado para a plataforma Teams.
* **Cancelar**: nenhuma ação é executada.

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview -3.png" alt-text="pre":::

## <a name="customize-your-teams-app-manifest"></a>Personalizar o manifesto do aplicativo Teams

O Kit de Ferramentas do Teams consiste nos seguintes arquivos de modelo de manifesto na pasta `manifest.template.json` em ambientes locais e remotos:

* `manifest.template.json`
* `templates/appPackage`

Durante a depuração ou provisionamento local, o Kit de Ferramentas do Teams `manifest.template.json`carrega o manifesto de , `state.{env}.json`com as configurações de , `config.{env}.json`e cria o aplicativo Teams no [Portal de Desenvolvimento](https://dev.teams.microsoft.com/apps).

### <a name="supported-placeholders-in-manifesttemplatejson"></a>Espaços reservados com suporte em manifest.template.json

A lista a seguir fornece espaços reservados com suporte em `manifest.template.json`:

* `{{state.xx}}` é um espaço reservado predefinido e seu valor é resolvido pelo Kit de Ferramentas do Teams, definido em `state.{env}.json`. Certifique-se de não modificar os valores em `state.{env}.json`
* `{{config.manifest.xx}}` é um espaço reservado personalizado e seu valor é resolvido de `config.{env}.json`

**Para adicionar um parâmetro personalizado**

1. Adicione o parâmetro personalizado da seguinte maneira:</br>
   a. Adicione um espaço reservado com `manifest.template.json` padrão `{{config.manifest.xx}}`.</br>
   b. Adicione um valor de configuração em `config.{env}.json`.

     ```json
     {
         "manifest": {
          "KEY": "VALUE"
          }
     }
     ```

2. Você pode navegar até o arquivo de configuração selecionando qualquer um dos espaços **reservados de** configuração Ir para o arquivo de configuração ou **exibir o arquivo de estado** em `manifest.template.json`.

### <a name="validate-manifest"></a>Validar manifesto

Durante operações como o pacote de **metadados do Zip Teams**, o Kit de Ferramentas do Teams valida o manifesto em relação ao esquema. A lista a seguir fornece diferentes maneiras de validar o manifesto:

* Na VSC, dispare da `Teams: Validate manifest file` paleta de comandos:

  :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/validate.png" alt-text="Validar arquivo":::

* Na CLI, use o comando:

     ``` bash
        teamsfx validate --env local
        teamsfx validate --env dev
        ```

---

## To preview values for local and dev environment

In `manifest.template.json`, you can navigate to codelens to preview the values for `local` and `dev` environment.

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/codelens.png" alt-text="Preview values":::

> [!NOTE]
> Provision the environment or execute local debug to generate values for placeholders.

You can navigate to state file or configuration file by selecting the codelens, which provides a drop-down list with all the environment names. After selecting one environment, the corresponding state file or configuration file opens.

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-environment.png" alt-text="Select your environment":::

To preview values for all the environments, you can hover over the placeholder. It shows a list with environment names and corresponding values. If you haven't provisioned the environment or executed the local debug, select `Trigger Teams: Provision in the cloud command to see placeholder value` or `Trigger local debug to see placeholder value`.

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/hover.png" alt-text="Preview all values":::

::: zone-end

::: zone pivot="visual-studio"

## Edit Teams app manifest using Visual Studio

Teams Toolkit in Visual Studio loads manifest from `manifest.template.json` with configurations from `state.{env}.json` and `config.{env}.json` while provisioning and preparing app dependencies. You can also create Microsoft Teams app in [Developer Portal](https://dev.teams.microsoft.com/apps) with the manifest.

After scaffolding, in the manifest template file under `templates/appPackage` folder,
`manifest.template.json` is shared between local and remote environment.

In the manifest template, select **Project** > **Teams Toolkit** > **Open Manifest File**.

:::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-open-manifest.png" alt-text="Open manifest file" lightbox="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-open-manifest.png":::

### Customize app manifest in Teams Toolkit

There are two types of placeholders in `manifest.template.json`:

* `{{state.xx}}` is pre-defined placeholder, whose value is resolved by Teams Toolkit, defined in `state.{env}.json`. It's recommended to not modify the values in `state.{env}.json`.
* `{{config.manifest.xx}}` is customized placeholder, whose value is resolved from `config.{env}.json`.

You can add a customized parameter by:

* Adding a placeholder in `manifest.template.json` with pattern: `{{config.manifest.xx}}`.
* Adding a config value in `config.{env}.json`.

    ```
        {
            "manifest": {
            "KEY": "VALUE"
            }
    }
    ```

### Preview app manifest in Teams Toolkit

You can preview values in app manifest in two ways:

* When you hover over the placeholder in `manifest.template.json`, then you can see the values for **dev** and **local** environment.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-hover-placeholder1.png" alt-text="Hover over placeholder" lightbox="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-hover-placeholder1.png":::

* You can also hover over the key besides each placeholder in `manifest.template.json`, and you can see the same values for **dev** and **local** environment.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-hover-key-placeholder.png" alt-text="Hover over key beside placeholder" lightbox="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-hover-key-placeholder.png":::

   > [!NOTE]
   > If the environment has not been provisioned, or the Teams app dependencies have not been prepared, it indicates that the values for placeholder have not been generated. Please follow the guidance inside hover to generate corresponding values.

### Preview manifest file

To preview the manifest file, you can sideload for local or deploy for Azure. You can preview the manifest file by performing the following step:

* Select **Project** > **Teams Toolkit** and trigger **Prepare Teams App Dependencies** or **Provision in the Cloud** that generates configuration for local or remote Teams app.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-preview-manifest1.png" alt-text="Preview manifest file" lightbox="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-preview-manifest1.png":::

There are two other ways to upload zip app package before you can preview manifest file:

1. From the list of menu select **Project** > **Teams Toolkit** > **Zip App Package**, and select **For Local** or **For Azure**.

    :::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-zip1.png" alt-text="Zip app package" lightbox="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-zip1.png":::

1. You can also upload zip app package from Solution Explorer, if you right-click on **MyTeamsApp1** and then select **Teams Toolkit** > **Zip App Package** > **For Local** or **For Azure**.

  > [!NOTE]
  > In this scenario the project name is **MyTeamsApp1**.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-solution-explorer1.png" alt-text="List of Teams Toolkit menus from solution explorer" lightbox="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-solution-explorer1.png":::

Teams Toolkit generates the zip app package, and to preview manifest file content you can follow the step below:

* Right-click on **manifest.template.json** under **appPackage** folder, select **Preview Manifest File** > **For Local** or **For Azure**.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-preview1.png" alt-text="Preview context menu" lightbox="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-preview1.png":::

This displays the preview of the manifest file in Visual Studio.

### Sync local changes to Developer Portal

After you've previewed the manifest file in Visual Studio, you can now sync the local changes to the Developer Portal. Select **Project** > **Teams Toolkit** > **Update Manifest in Teams Developer Portal**, or context menu from Solution Explorer. You can now preview the manifest file in Developer Portal as a result of syncing the local changes.

:::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-update-manifest1.png" alt-text="Update manifest in teams developer portal" lightbox="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-update-manifest1.png":::

> [!NOTE]
> The changes are updated to Teams Developer Portal. If you have some manual updates in Developer Portal, that can be overwritten. In the **Warning** dialog box you can select **Overwrite and update** or **Cancel**.

:::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-overwrite.png" alt-text="Update warning" lightbox="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-overwrite.png":::

::: zone-end

## See also

* [Manage multiple environments](TeamsFx-multi-env.md)
* [Reference: Manifest schema for Microsoft Teams](../resources/schema/manifest-schema.md)
* [Public developer preview for Microsoft Teams](../resources/dev-preview/developer-preview-intro.md)

* [Provision cloud resources using Visual Studio](provision-cloud-resources.md)

* [Deploy Teams app to the cloud using Visual Studio](deploy-teams-app.md)
