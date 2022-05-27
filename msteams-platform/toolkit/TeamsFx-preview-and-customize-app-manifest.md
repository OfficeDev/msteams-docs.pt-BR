---
title: Teams manifesto do aplicativo no Teams Toolkit
author: zyxiaoyuer
description: Teams manifesto do aplicativo
ms.author: nliu
ms.localizationpriority: medium
ms.topic: overview
ms.date: 05/13/2022
ms.openlocfilehash: 94f02ce31a9af3acb78fc6fef6f071df02bfd565
ms.sourcegitcommit: d9025e959dcdd011ed4feca820dae7c5d1251b27
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2022
ms.locfileid: "65755857"
---
# <a name="edit-teams-app-manifest"></a>Editar Teams manifesto do aplicativo

O arquivo de modelo do manifesto `manifest.template.json` está disponível na pasta `templates/appPackage` após o scaffolding. O arquivo de modelo com espaços reservados e `.fx/configs` os valores reais são resolvidos Teams Toolkit arquivos em e `.fx/states` para ambientes diferentes.

**Para visualizar o manifesto com conteúdo real, o Teams Toolkit gera arquivos de manifesto de visualização na `build/appPackage` pasta**:

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
 
### <a name="preview-manifest-file-in-local-environment"></a>Visualizar arquivo de manifesto no ambiente local

Para visualizar o arquivo de manifesto no ambiente local, você pode pressionar **F5** para executar a depuração local. Ele gera configurações locais padrão para você e o pacote do aplicativo e o manifesto de visualização são compilados na `build/appPackage` pasta.

Você também pode visualizar o arquivo de manifesto local seguindo as etapas:

1. Selecione **Visualizar** nos codelens do `manifest.template.json` arquivo e selecione **local**.
2. Selecione **Visualizar arquivo de manifesto** na barra de menus do `manifest.template.json` arquivo.
3. Selecione **Zip Teams de metadados** no Treeview e selecione **local**.

A visualização local é exibida conforme mostrado na imagem:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/preview-23.png" alt-text="Visualização":::

### <a name="preview-manifest-file-in-remote-environment"></a>Visualizar arquivo de manifesto no ambiente remoto

**Para visualizar o arquivo de manifesto no ambiente remoto**

* Selecione **Provisionar na nuvem em** **DESENVOLVIMENTO** Teams Toolkit extensão ou
* Gatilho **Teams: provisionar na nuvem da** paleta de comandos.
 
Ele gera a configuração para o aplicativo Teams remoto e compila o pacote e o manifesto de visualização na `build/appPackage` pasta.

Você também pode visualizar o arquivo de manifesto no ambiente remoto seguindo estas etapas:

1. Selecione **Visualizar** nos codelens do `manifest.template.json` arquivo.
2. Selecione **Visualizar arquivo de manifesto** na barra de menus do `manifest.template.json` arquivo.
3. Selecione **Zip Teams de metadados** no Treeview.
4. Selecione seu ambiente.

> [!NOTE]
> Se houver mais de um ambiente, você precisará selecionar o ambiente que você quer visualizar, conforme mostrado na imagem:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview-1.png" alt-text="Adicionar env":::

## <a name="sync-local-changes-to-dev-portal"></a>Sincronizar alterações locais no Portal de Desenvolvimento

Depois de visualizar o arquivo de manifesto, você pode sincronizar as alterações locais no Portal de Desenvolvimento das seguintes maneiras:

1. Implantar Teams manifesto do aplicativo.

   Você pode implantar Teams manifesto do aplicativo de qualquer uma das seguintes maneiras:

   * Vá para `manifest.template.json` o arquivo e clique com o botão direito do mouse para selecionar no `Deploy Teams app manifest` menu de contexto.

      :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/deploy-manifest.png" alt-text="Implantar manifesto":::

   * Disparar da `Teams: Deploy Teams app manifest` paleta de comandos.

      :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/deploy-command.png" alt-text="Implantar da paleta de comandos":::

2. Atualize para Teams plataforma.

   Você pode atualizar para Teams plataforma de qualquer uma das seguintes maneiras:

   * Selecione **Atualizar para Teams plataforma** no canto superior esquerdo de `manifest.{env}.json`.

   * Gatilho **Teams: atualize o manifesto Teams plataforma** na barra de menus de `manifest.{env}.json`.

      :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/update-to-teams.png" alt-text="Atualizar para equipes":::

Você também pode disparar **Teams: atualizar o manifesto para Teams plataforma** na paleta de comandos:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/pre.png" alt-text="modo de exibição em árvore":::

> [!NOTE]
> O gatilho de codelens do editor ou da barra de menus atualiza o arquivo de manifesto atual para Teams plataforma. O gatilho da paleta de comandos requer a seleção do ambiente de destino.

 Comando da CLI:

``` bash
        teamsfx deploy manifest --include-app-manifest yes
```

---

> [!NOTE]
> As atualizações de alteração no Portal de Desenvolvimento. Todas as atualizações manuais no Portal de Desenvolvimento são substituídas.

Se o arquivo de manifesto estiver desatualizado por causa da alteração do arquivo de configuração ou da alteração do modelo, selecione uma das seguintes ações:

* **Somente visualização**: o arquivo de manifesto local é substituído de acordo com a configuração atual.
* **Versão prévia e atualização**: o arquivo de manifesto local é substituído de acordo com a configuração atual e também atualizado para Teams plataforma.
* **Cancelar**: nenhuma ação é executada.

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview -3.png" alt-text="pre" border="true":::

## <a name="customize-teams-app-manifest"></a>Personalizar o manifesto do aplicativo Teams

O Kit de Ferramentas do Teams consiste nos seguintes arquivos de modelo de manifesto na pasta `manifest.template.json` em ambientes locais e remotos:

* `manifest.template.json`
* `templates/appPackage`


Durante a depuração ou provisionamento local, `manifest.template.json`Teams Toolkit carrega o manifesto de , `state.{env}.json`com as configurações de , `config.{env}.json`e cria Teams aplicativo no [Portal de Desenvolvimento](https://dev.teams.microsoft.com/apps).

## <a name="supported-placeholders-in-manifesttemplatejson"></a>Espaços reservados com suporte em manifest.template.json

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

2. Você pode navegar até o arquivo de configuração selecionando qualquer um dos espaços reservados de configuração **Ir** para o arquivo de configuração ou **Exibir o arquivo de estado** em `manifest.template.json`.

### <a name="validate-manifest"></a>Validar manifesto

Durante operações como o **pacote Teams** zip, Teams Toolkit valida o manifesto em relação ao esquema. A lista a seguir fornece diferentes maneiras de validar o manifesto:

* Na VSC, dispare da `Teams: Validate manifest file` paleta de comandos:

  :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/validate.png" alt-text="Validar arquivo":::

* Na CLI, use o comando:

     ``` bash
        teamsfx validate --env local
        teamsfx validate --env dev
        ```

---

## Codelenses and hovers

In `manifest.template.json`, you can navigate to codelens to preview the values for `local` and `dev` environment.

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/codelens.png" alt-text="Preview values":::

> [!NOTE]
> Provision the environment or execute local debug to generate values for placeholders.

You can navigate to state file or configuration file by selecting the codelens, which provides a drop-down list with all the environment names. After selecting one environment, the corresponding state file or configuration file opens.

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-environment.png" alt-text="Select your environment":::

To preview values for all the environments, you can hover over the placeholder. It shows a list with environment names and corresponding values. If you haven't provisioned the environment or executed the local debug, select `Trigger Teams: Provision in the cloud command to see placeholder value` or `Trigger local debug to see placeholder value`.

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/hover.png" alt-text="Preview all values":::

## See also

* [Manage multiple environments](TeamsFx-multi-env.md)
* [Reference: Manifest schema for Microsoft Teams](../resources/schema/manifest-schema.md)
* [Public developer preview for Microsoft Teams](../resources/dev-preview/developer-preview-intro.md) 
