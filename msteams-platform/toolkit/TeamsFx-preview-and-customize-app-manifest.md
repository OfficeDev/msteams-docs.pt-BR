---
title: Personalizar o Manifesto do Aplicativo Teams no Kit de Ferramentas do Teams
author: zyxiaoyuer
description: Neste módulo, saiba como editar, visualizar e personalizar o Manifesto do Aplicativo do Teams no ambiente diferente.
ms.author: nliu
ms.localizationpriority: medium
ms.topic: overview
ms.date: 05/13/2022
zone_pivot_groups: teams-app-platform
ms.openlocfilehash: e92e30cf30dd06dbbe3c513a79fe4b7ed7c4bc1a
ms.sourcegitcommit: c3601696cced9aadc764f1e734646ee7711f154c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2022
ms.locfileid: "68833097"
---
# <a name="customize-teams-app-manifest"></a>Personalizar o manifesto do aplicativo Teams

O manifesto do aplicativo Teams descreve como seu aplicativo se integra ao produto do Microsoft Teams.

::: zone pivot="visual-studio-code"

## <a name="customize-teams-app-manifest-for-visual-studio-code"></a>Personalizar o manifesto do aplicativo teams para Visual Studio Code

O manifesto do aplicativo Teams descreve como seu aplicativo se integra ao produto do Microsoft Teams. Para obter mais informações sobre Manifesto, consulte [Esquema de manifesto do aplicativo para o Teams](../resources/schema/manifest-schema.md). Esta seção cobre:

* [Visualizar arquivo de manifesto no ambiente local](#preview-manifest-file-in-local-environment)
* [Visualizar arquivo de manifesto em ambiente remoto](#preview-manifest-file-in-remote-environment)
* [Sincronizar alterações locais no Portal do Desenvolvedor](#sync-local-changes-to-developer-portal)
* [Personalizar o manifesto do aplicativo teams](#customize-your-teams-app-manifest)
* [Validar manifesto](#validate-manifest)

O arquivo de modelo do manifesto `manifest.template.json` está disponível na pasta `templates/appPackage` após o scaffolding. O arquivo de modelo com espaços reservados e os valores reais são resolvidos pelo Teams Toolkit usando arquivos em `.fx/configs` e `.fx/states` para diferentes ambientes.

Para visualizar o manifesto com o conteúdo real, o Teams Toolkit gera arquivos de manifesto de visualização em `build/appPackage` pasta:

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
* [Visualizar arquivo de manifesto em ambiente remoto](#preview-manifest-file-in-remote-environment)

## <a name="preview-manifest-file-in-local-environment"></a>Visualizar arquivo de manifesto no ambiente local

Para visualizar o arquivo de manifesto no ambiente local, pressione **F5** para executar a depuração local. Ele gera configurações locais padrão para você e o pacote do aplicativo e o manifesto de visualização são compilados na `build/appPackage` pasta.

Você também pode visualizar o arquivo de manifesto local por dois métodos

* Usando a opção de visualização em codelens
* Usando a opção **pacote de metadados do Zip Teams**

As etapas a seguir ajudam a visualizar o arquivo de manifesto local usando a opção de visualização em codelens:

1. Selecione **Visualizar** nos codelens do `manifest.template.json` arquivo.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/preview-23.png" alt-text="Captura de tela é um exemplo que mostra a visualização nos codelens do arquivo de manifesto.":::

1. Selecione **local**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-env1.png" alt-text="Captura de tela é um exemplo de mostrar a seleção de local no ambiente.":::

As etapas a seguir ajudam a visualizar o arquivo de manifesto local usando a opção **pacote de metadados do Zip Teams** :

1. Selecione `manifest.template.json` arquivo.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-manifest-json.png" alt-text="Captura de tela é um exemplo de mostrar a seleção de manifest.template.json.":::

1. Selecione o ícone kit de :::image type="icon" source="../assets/images/teams-toolkit-v2/teams-toolkit-sidebar-icon.PNG"::: ferramentas do Teams na barra de ferramentas Visual Studio Code.

1. Selecione **Pacote de metadados do Zip Teams** em **DEPLOYMENT**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/teams-metadata-package.png" alt-text="Captura de tela é um exemplo de mostrar a seleção do pacote de metadados zip teams.":::

1. Selecione **local**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-env1.png" alt-text="Captura de tela é um exemplo de mostrar a seleção de local no ambiente.":::

A visualização local é exibida conforme mostrado na imagem:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/preview-23.png" alt-text="Captura de tela é um exemplo de mostrar a visualização do local.":::

## <a name="preview-manifest-file-in-remote-environment"></a>Visualizar arquivo de manifesto em ambiente remoto

Para visualizar o arquivo de manifesto usando Visual Studio Code:

* Selecione **Provisionar na nuvem em** **DESENVOLVIMENTO** na extensão kit de ferramentas do Teams
  
  :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/provision.png" alt-text="Captura de tela é um exemplo de mostrar a seleção de provisionamento no recurso de nuvem.":::

Para visualizar o arquivo de manifesto usando a paleta de comandos:

* Equipes de Gatilho **: Provisionar na nuvem a** partir da paleta de comandos.

  :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/command palatte.png" alt-text="Captura de tela é um exemplo de mostrar o recurso de nuvem de provisionamento usando a paleta de comandos.":::

Ele gera configuração para o aplicativo remoto do Teams e cria o pacote e o manifesto de visualização em `build/appPackage` pasta.

Você também pode visualizar o arquivo de manifesto por dois métodos em ambiente remoto

* Usando a opção de visualização em codelens
* Usando a opção **pacote de metadados do Zip Teams**

As etapas a seguir ajudam a visualizar o arquivo de manifesto usando a opção de visualização em codelens:

1. Selecione **Visualizar** nos codelens do `manifest.template.json` arquivo.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/preview-23.png" alt-text="Captura de tela é um exemplo de exibição de visualização nos codelens do arquivo de manifesto.":::

1. Selecione seu ambiente.

   > [!NOTE]
   > Se houver mais de um ambiente, você precisará selecionar o ambiente que você quer visualizar, conforme mostrado na imagem:

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview-1.png" alt-text="Captura de tela é um exemplo de mostrando a adição de ambiente.":::

As etapas a seguir ajudam a visualizar o arquivo de manifesto usando a opção **pacote de metadados do Zip Teams** em ambiente remoto:

1. Selecione `manifest.template.json` arquivo.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-manifest-json.png" alt-text="Captura de tela é um exemplo de mostrar a seleção de manifest.template.json.":::

1. Selecione o ícone kit de :::image type="icon" source="../assets/images/teams-toolkit-v2/teams-toolkit-sidebar-icon.PNG"::: ferramentas do Teams na barra de ferramentas Visual Studio Code.

1. Selecione **Pacote de metadados do Zip Teams** em **DEPLOYMENT**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/teams-metadata-package.png" alt-text="Captura de tela é um exemplo de mostrar a seleção do pacote de metadados zip teams.":::

1. Selecione seu ambiente.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview-1.png" alt-text="Captura de tela é um exemplo de mostrando a adição de ambiente.":::

   > [!NOTE]
   > Se houver mais de um ambiente, você precisará selecionar o ambiente que você quer visualizar, conforme mostrado na imagem:

## <a name="sync-local-changes-to-developer-portal"></a>Sincronizar alterações locais no Portal do Desenvolvedor

Depois de visualizar o arquivo de manifesto, você pode sincronizar suas alterações locais com o Portal do Desenvolvedor pelas seguintes maneiras:

> [!NOTE]
> Para obter mais informações sobre o Portal do Desenvolvedor, consulte [Portal do Desenvolvedor para Teams](../concepts/build-and-test/teams-developer-portal.md).

1. Implantar manifesto do aplicativo Teams.

   Você pode implantar o manifesto do aplicativo teams de qualquer uma das seguintes maneiras:

   * Vá para o `manifest.template.json` arquivo e clique com o botão direito do mouse para selecionar `Deploy Teams app manifest` no menu de contexto.

      :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/deploy-manifest.png" alt-text="Captura de tela é um exemplo de mostrar a seleção de implantar o manifesto do aplicativo Teams.":::

   * Disparar `Teams: Deploy Teams app manifest` da paleta de comandos.

      :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/deploy-command.png" alt-text="Captura de tela é um exemplo de mostrar a implantação da paleta de comandos.":::

2. Atualizar para a plataforma do Teams.

   Você pode atualizar para a plataforma do Teams de qualquer uma das seguintes maneiras:

   * Selecione **Atualizar para a plataforma do Teams** no canto superior esquerdo do `manifest.{env}.json`.

   * Trigger **Teams: atualizar manifesto para a plataforma do Teams** na barra de menus de `manifest.{env}.json`.

      :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/update-to-teams.png" alt-text="Captura de tela é um exemplo de mostrar a atualização para a plataforma do Teams na barra de menus do manifesto.":::

Você também pode disparar **o Teams: atualizar o manifesto para a plataforma do Teams** na paleta de comandos:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/pre.png" alt-text="Captura de tela é um exemplo de mostrar a seleção do Teams: atualizar o manifesto para a plataforma do Teams da paleta de comandos.":::

> [!NOTE]
> O gatilho de codelens do editor ou da barra de menus atualiza o arquivo de manifesto atual para a plataforma do Teams. O gatilho da paleta de comandos requer a seleção do ambiente de destino.

 Comando CLI:

``` bash
        teamsfx deploy manifest --include-app-manifest yes
```

---

> [!NOTE]
> A alteração é atualizada para o Portal de Desenvolvimento. Todas as atualizações manuais no Portal de Desenvolvimento são substituídas.

Se o arquivo de manifesto estiver desatualizado devido à alteração do arquivo de configuração ou à alteração do modelo, selecione qualquer uma das seguintes ações:

* **Somente visualização**: o arquivo de manifesto local é substituído de acordo com a configuração atual.
* **Visualização e atualização**: o arquivo de manifesto local é substituído de acordo com a configuração atual e também atualizado para a plataforma do Teams.
* **Cancelar**: nenhuma ação é tomada.

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview -3.png" alt-text="Captura de tela é um exemplo de exibição, a navegação para selecionar somente visualização, visualizar e atualizar e cancelar opções quando o arquivo de manifesto estiver desatualizado devido à configuração ou alteração de modelo.":::

## <a name="customize-your-teams-app-manifest"></a>Personalizar o manifesto do aplicativo teams

O Kit de Ferramentas do Teams consiste nos seguintes arquivos de modelo de manifesto na pasta `manifest.template.json` em ambientes locais e remotos:

* `manifest.template.json`
* `templates/appPackage`

Durante a depuração ou provisionamento local, o Teams Toolkit carrega o manifesto de `manifest.template.json`, com as configurações de `state.{env}.json`, `config.{env}.json`e cria o aplicativo Teams no [Portal de Desenvolvimento](https://dev.teams.microsoft.com/apps).

### <a name="supported-placeholders-in-manifesttemplatejson"></a>Espaços reservados com suporte em manifest.template.json

A lista a seguir fornece espaços reservados com suporte em `manifest.template.json`:

* `{{state.xx}}` é um espaço reservado predefinido e seu valor é resolvido pelo Kit de Ferramentas do Teams, definido em `state.{env}.json`. Certifique-se de não modificar os valores em `state.{env}.json`
* `{{config.manifest.xx}}` é um espaço reservado personalizado e seu valor é resolvido de `config.{env}.json`

**Para adicionar parâmetro personalizado**

1. Adicione o parâmetro personalizado da seguinte maneira:</br>
   a. Adicione um espaço reservado `manifest.template.json` com o padrão `{{config.manifest.xx}}`.</br>
   b. Adicione um valor de configuração em `config.{env}.json`.

     ```json
     {
         "manifest": {
          "KEY": "VALUE"
          }
     }
     ```

2. Você pode ir para o arquivo de configuração selecionando qualquer um dos espaços reservados de configuração **Ir para o arquivo de configuração** ou **Exibir o arquivo de estado** em `manifest.template.json`.

### <a name="validate-manifest"></a>Validar manifesto

Durante operações como o pacote de **metadados do Zip Teams**, o Teams Toolkit valida o manifesto em relação ao esquema. A lista a seguir fornece diferentes maneiras de validar o manifesto:

* No VSC, dispara `Teams: Validate manifest file` da paleta de comandos:

  :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/validate.png" alt-text="Captura de tela é um exemplo de mostrando o Teams validar o arquivo de manifesto da paleta de comandos.":::

* Na CLI, use o comando:

     ``` bash
        teamsfx validate --env local
        teamsfx validate --env dev
        ```

---

## To preview values for local and dev environment

In `manifest.template.json`, you can go to codelens to preview the values for `local` and `dev` environment.

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/codelens.png" alt-text="Screenshot is an example of showing preview values for local and dev environment.":::

> [!NOTE]
> Provision the environment or execute local debug to generate values for placeholders.

You can go to state file or configuration file by selecting the codelens, which provides a drop-down list with all the environment names. After selecting one environment, the corresponding state file or configuration file opens.

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-environment.png" alt-text="Screenshot is an example of showing the selection of an environment.":::

To preview values for all the environments, you can hover over the placeholder. It shows a list with environment names and corresponding values. If you haven't provisioned the environment or executed the local debug, select `Trigger Teams: Provision in the cloud command to see placeholder value` or `Trigger local debug to see placeholder value`.

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/hover.png" alt-text="Screenshot is an example of showing the preview values for all environments.":::

::: zone-end

::: zone pivot="visual-studio"

## Edit Teams app manifest using Visual Studio

Teams Toolkit in Visual Studio loads manifest from `manifest.template.json` with configurations from `state.{env}.json` and `config.{env}.json` while provisioning and preparing app dependencies. You can also create Microsoft Teams app in [Developer Portal](https://dev.teams.microsoft.com/apps) with the manifest.

After scaffolding, in the manifest template file under `templates/appPackage` folder,
`manifest.template.json` is shared between local and remote environment.

In the manifest template, select **Project** > **Teams Toolkit** > **Open Manifest File**.

:::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-open-manifest.png" alt-text="Screenshot is an example of showing the navigation to open manifest file." lightbox="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-open-manifest.png":::

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

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-hover-placeholder1.png" alt-text="Screenshot is an example showing when you hover over placeholder, can view the values for dev and local environment." lightbox="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-hover-placeholder1.png":::

* You can also hover over the key besides each placeholder in `manifest.template.json`, and you can see the same values for **dev** and **local** environment.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-hover-key-placeholder.png" alt-text="Screenshot is an example showing when you hover over key beside placeholder can view the same values for dev and local environment." lightbox="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-hover-key-placeholder.png":::

   > [!NOTE]
   > If the environment has not been provisioned, or the Teams app dependencies have not been prepared, it indicates that the values for placeholder have not been generated. Please follow the guidance inside hover to generate corresponding values.

### Preview manifest file

To preview the manifest file, you can sideload for local or deploy for Azure. You can preview the manifest file by performing the following step:

* Select **Project** > **Teams Toolkit** and trigger **Prepare Teams App Dependencies** or **Provision in the Cloud** that generates configuration for local or remote Teams app.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-preview-manifest1.png" alt-text="Screenshot is an example of showing preview manifest file." lightbox="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-preview-manifest1.png":::

There are two other ways to upload zip app package before you can preview manifest file:

1. From the list of menu select **Project** > **Teams Toolkit** > **Zip App Package**, and select **For Local** or **For Azure**.

    :::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-zip1.png" alt-text="Screenshot is an example of showing the navigation to zip app package for local and azure." lightbox="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-zip1.png":::

1. You can also upload zip app package from Solution Explorer, if you right-click on **MyTeamsApp1** and then select **Teams Toolkit** > **Zip App Package** > **For Local** or **For Azure**.

  > [!NOTE]
  > In this scenario the project name is **MyTeamsApp1**.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-solution-explorer1.png" alt-text="Screenshot is an example of showing the list of Teams toolkit menus from solution explorer." lightbox="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-solution-explorer1.png":::

Teams Toolkit generates the zip app package, and to preview manifest file content you can follow the step below:

* Right-click on **manifest.template.json** under **appPackage** folder, select **Preview Manifest File** > **For Local** or **For Azure**.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-preview1.png" alt-text="Screenshot is an example of showing the preview manifest menu for local and azure." lightbox="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-preview1.png":::

This displays the preview of the manifest file in Visual Studio.

### Sync local changes to Developer Portal

After you've previewed the manifest file in Visual Studio, you can now sync the local changes to the Developer Portal. Select **Project** > **Teams Toolkit** > **Update Manifest in Teams Developer Portal**, or context menu from Solution Explorer. You can now preview the manifest file in Developer Portal as a result of syncing the local changes.

:::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-update-manifest1.png" alt-text="Screenshot is an example of showing the navigation to update manifest in Teams developer portal." lightbox="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-update-manifest1.png":::

The changes are updated to Teams Developer Portal.

> [!NOTE]
>
> * Select **Overwrite and update** or **Cancel** from the **Warning** dialog box to make any manual updates that can be overwritten in the Developer Portal.
> * When you create a Teams command bot using Visual Studio, two app IDs are registered in Azure Active Directory. You can identify the app IDs in the Developer Portal as **Application client ID** under Basic information and existing **Bot ID** under **App features**.

:::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-overwrite.png" alt-text="Screenshot is an example of showing the update warning." lightbox="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-overwrite.png":::

::: zone-end

## See also

* [Manage multiple environments](TeamsFx-multi-env.md)
* [Reference: Manifest schema for Microsoft Teams](../resources/schema/manifest-schema.md)
* [Public developer preview for Microsoft Teams](../resources/dev-preview/developer-preview-intro.md)
* [Provision cloud resources using Visual Studio](provision-cloud-resources.md)
* [Deploy Teams app to the cloud using Visual Studio](deploy.md#deploy-teams-app-to-the-cloud-using-visual-studio)
