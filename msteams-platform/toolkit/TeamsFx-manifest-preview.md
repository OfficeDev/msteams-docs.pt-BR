---
title: Visualizar o manifesto do aplicativo Teams no Kit de Ferramentas do Teams
author: zyxiaoyuer
description: Visualizar Manifesto do Aplicativo Teams
ms.author: nliu
ms.localizationpriority: high
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 91bc070d30136ce1f004676172594f26ca37dea5
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111868"
---
# <a name="preview-app-manifest-in-toolkit"></a>Visualizar manifesto do aplicativo no Kit de Ferramentas

O arquivo de modelo do manifesto `manifest.template.json` está disponível na pasta `templates/appPackage` após o scaffolding. O arquivo de modelo com espaços reservados e os valores reais são resolvidos pelo Kit de Ferramentas do Teams a partir de arquivos em `.fx/configs` e `.fx/states` para ambientes diferentes.

## <a name="prerequisite"></a>Pré-requisito

* Instalar a [versão mais recente do Kit de Ferramentas do Teams](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension).

> [!TIP]
> Verifique se você tem um projeto de aplicativo do Teams aberto no código do Visual Studio.

## <a name="preview-manifest"></a>Visualizar manifesto

Para visualizar o manifesto com o conteúdo real, o Kit de Ferramentas do Teams gera arquivos de manifesto de visualização na `build/appPackage` pasta:

```text
└───build
    └───appPackage
        ├───appPackage.{env}.zip - Zipped app package of remote teams app
        ├───appPackage.local.zip - Zipped app package of local team app
        ├───manifest.{env}.json  - Previewed manifest of remote teams app
        └───manifest.local.json  - Previewed manifest of local teams app
```

### <a name="preview-local-manifest-file"></a>Visualizar o arquivo de manifesto local

Para visualizar o arquivo de manifesto do aplicativo local do Teams, você pode clicar em **F5** para executar a depuração local. Ele gera configurações locais padrão para você e o pacote do aplicativo e o manifesto de visualização são compilados na `build/appPackage` pasta.

Você também pode visualizar o manifesto local seguindo as etapas:

1. Selecione **Visualizar** nos codelens do `manifest.template.json` arquivo e selecione **local**
2. Selecione **Visualizar arquivo de manifesto** na barra de menu do `manifest.template.json` arquivo
3. Selecione **Pacote de metadados do Zip Teams** em Treeview e selecione **local**

A visualização local é exibida conforme mostrado na imagem:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/preview-23.png" alt-text="Visualização":::

### <a name="preview-manifest-in-remote-environment"></a>Visualizar manifesto no ambiente remoto

Para visualizar o arquivo de manifesto do aplicativo de equipes remotas, selecione **Provisionar na nuvem** no painel **DESENVOLVIMENTO** da extensão Treeview do Kit de Ferramentas do Teams ou dispare o **Teams: provisionar na nuvem** na paleta de comandos. Ele gera a configuração do aplicativo de equipes remotas e compila o pacote e o manifesto de visualização na `build/appPackage` pasta.

Você também pode visualizar o manifesto no ambiente remoto seguindo as etapas:

1. Selecione **Visualizar** nos codelens do `manifest.template.json` arquivo
2. Selecione **Visualizar arquivo de manifesto** na barra de menu do `manifest.template.json` arquivo
3. Selecione **Pacote de metadados do Zip Teams** em Treeview
4. Selecione seu ambiente

Se houver mais de um ambiente, você precisará selecionar o ambiente que você quer visualizar, conforme mostrado na imagem:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview-1.png" alt-text="Adicionar env":::

## <a name="sync-local-changes-to-developer-portal"></a>Sincronizar alterações locais no Portal do Desenvolvedor

Depois de visualizar o arquivo de manifesto, você pode sincronizar suas alterações locais no Portal do Desenvolvedor seguindo as etapas:

1. Selecione **Atualizar para a plataforma do Teams** no canto superior esquerdo da `manifest.{env}.json`
2. Selecione **Teams: atualize o manifesto para a plataforma do Teams** na barra de menu da `manifest.{env}.json`

 Você também pode disparar o **Teams: atualizar o manifesto para a plataforma do Teams** da paleta de comandos:

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/pre.png" alt-text="modo de exibição em árvore":::

> [!NOTE]
> O gatilho de codelens do editor ou do **título** atualiza o arquivo de manifesto para a plataforma do Teams. O gatilho da paleta de comandos requer a seleção do ambiente de destino

  

Se o arquivo de manifesto estiver desatualizado por causa da alteração do arquivo de configuração ou da alteração do modelo, selecione uma das seguintes ações:

* **Somente visualização**: o arquivo de manifesto local é substituído de acordo com a configuração atual
* **Visualização e atualização**: o arquivo de manifesto local é substituído de acordo com a configuração atual e também atualizado para a plataforma do Teams
* **Cancelar**: nenhuma ação foi tomada

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview -3.png" alt-text="pre":::



> [!NOTE]
> As alterações são atualizadas no Portal de Desenvolvimento. Todas as atualizações manuais no Portal de Desenvolvimento são substituídas.

## <a name="see-also"></a>Confira também

[Personalizar o manifesto do aplicativo Teams no Kit de Ferramentas do Teams](TeamsFx-manifest-customization.md)
