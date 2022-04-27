---
title: Visualizar Teams manifesto do aplicativo no Teams Toolkit
author: zyxiaoyuer
description: Visualizar Manifesto do Aplicativo Teams
ms.author: nliu
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 57dc719f872d502beded14c30a09d72c27ee74c3
ms.sourcegitcommit: 3bfd0d2c4d83f306023adb45c8a3f829f7150b1d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65073276"
---
# <a name="preview-app-manifest-in-toolkit"></a>Visualizar manifesto do aplicativo no Toolkit

O arquivo de modelo de `manifest.template.json` manifesto está disponível na pasta `templates/appPackage` após o scaffolding. O arquivo de modelo com espaços reservados e `.fx/configs` os valores reais são resolvidos Teams Toolkit arquivos em e `.fx/states` para ambientes diferentes.

## <a name="prerequisite"></a>Pré-requisito

* Instalar a [versão mais recente do Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension)

> [!TIP]
> Verifique se você Teams projeto de aplicativo aberto Visual Studio código.

## <a name="preview-manifest"></a>Manifesto de visualização

Para visualizar o manifesto com conteúdo real, Teams Toolkit arquivos de manifesto de visualização na `build/appPackage` pasta:

```text
└───build
    └───appPackage
        ├───appPackage.{env}.zip - Zipped app package of remote teams app
        ├───appPackage.local.zip - Zipped app package of local team app
        ├───manifest.{env}.json  - Previewed manifest of remote teams app
        └───manifest.local.json  - Previewed manifest of local teams app
```

### <a name="preview-local-manifest-file"></a>Visualizar arquivo de manifesto local

Para visualizar o arquivo de manifesto do aplicativo local do Teams, você pode pressionar **F5** para executar a depuração local. Ele gera configurações locais padrão para você e, em seguida, o pacote do aplicativo e o manifesto de visualização são compilados na `build/appPackage` pasta.

Você também pode visualizar o manifesto local seguindo as etapas:

1. Selecione **Visualizar** nos codelens do `manifest.template.json` arquivo e selecione **local**
2. Selecione **Visualizar arquivo de manifesto** na barra de menus do `manifest.template.json` arquivo
3. Selecione **Zip Teams de metadados** no Treeview e selecione **local**

A visualização local aparece conforme mostrado na imagem:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/preview-23.png" alt-text="Visualização":::

### <a name="preview-manifest-in-remote-environment"></a>Manifesto de visualização no ambiente remoto

Para visualizar o arquivo de manifesto do aplicativo de equipes remotas, selecione **Provisionar** na nuvem no painel **DESENVOLVIMENTO** do treeview da extensão Teams Toolkit ou dispare **Teams: Provisionar** na nuvem na paleta de comandos. Ele gera a configuração para o aplicativo de equipes remotas e compila o pacote e o manifesto de visualização na `build/appPackage` pasta.

Você também pode visualizar o manifesto no ambiente remoto seguindo as etapas:

1. Selecione **Visualizar** nos codelens do `manifest.template.json` arquivo
2. Selecione **Visualizar arquivo de manifesto** na barra de menus do `manifest.template.json` arquivo
3. Selecione **Zip Teams de metadados** no Treeview
4. Selecione seu ambiente

Se houver mais de um ambiente, você precisará selecionar o ambiente que deseja visualizar, conforme mostrado na imagem:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview-1.png" alt-text="Adicionar env":::

## <a name="sync-local-changes-to-developer-portal"></a>Sincronizar alterações locais no Portal do Desenvolvedor

Depois de visualizar o arquivo de manifesto, você pode sincronizar as alterações locais no Portal do Desenvolvedor seguindo as etapas:

1. Selecione **Atualizar para Teams plataforma** no canto superior esquerdo do`manifest.{env}.json`
2. Selecione **Teams: atualizar o manifesto para Teams plataforma** na barra de menus de`manifest.{env}.json`

 Você também pode disparar **Teams: atualizar o manifesto para Teams plataforma** na paleta de comandos:

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/pre.png" alt-text="modo de exibição em árvore":::

> [!NOTE]
> O gatilho de codelens do editor ou **do título** atualiza o arquivo de manifesto para Teams plataforma. O gatilho da paleta de comandos requer a seleção do ambiente de destino

  

Se o arquivo de manifesto estiver desatualizado devido à alteração do arquivo de configuração ou à alteração do modelo, selecione qualquer uma das seguintes ações:

* **Somente visualização**: o arquivo de manifesto local é substituído de acordo com a configuração atual
* **Versão prévia e atualização**: o arquivo de manifesto local é substituído de acordo com a configuração atual e também atualizado para Teams plataforma
* **Cancelar**: nenhuma ação é executada

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview -3.png" alt-text="pre":::



> [!NOTE]
> As alterações são atualizadas no Portal de Desenvolvimento. Todas as atualizações manuais no portal de desenvolvimento são substituídas.

## <a name="see-also"></a>Confira também

[Personalizar Teams manifesto do aplicativo no Teams Toolkit](TeamsFx-manifest-customization.md)
