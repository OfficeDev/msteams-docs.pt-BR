---
title: Personalizar Teams manifesto do aplicativo no Teams Toolkit
author: zyxiaoyuer
description: Personalizar Manifesto do Aplicativo Teams
ms.author: nliu
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 047cd9bcd86c103c3c9cab22793fb7d187f7493d
ms.sourcegitcommit: 8a0ffd21c800eecfcd6d1b5c4abd8c107fcf3d33
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2022
ms.locfileid: "63453597"
---
# <a name="customize-app-manifest-in-teams-toolkit"></a>Personalizar o manifesto do aplicativo Teams Toolkit

Teams Toolkit consiste nos seguintes arquivos de modelo de manifesto na `templates/appPackage` pasta:

* `manifest.local.template.json` - aplicativo de equipes de depuração local
* `manifest.remote.template.json` - compartilhado em todos os ambientes

## <a name="prerequisite"></a>Pré-requisito

* [Instale Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) versão v3.0.0+.

> [!TIP]
> Verifique se você Teams projeto de aplicativo aberto Visual Studio Code.

Durante o provisionamento, Teams Toolkit carrega manifesto `manifest.remote.template.json`de , combinado com `state.{env}.json` configurações de e `config.{env}.json`, e cria o aplicativo teams no [Portal deV](https://dev.teams.microsoft.com/apps).

Durante a depuração local, Teams Toolkit carrega manifesto `manifest.local.template.json`de , combinado com `localSettings.json`configurações de , e cria o aplicativo teams no [Portal de Desenvolvimento](https://dev.teams.microsoft.com/apps).

## <a name="supported-placeholder-in-manifestremotetemplatejson"></a>Espaço reservado suportado em manifest.remote.template.json

* `{{state.xx}}`é um espaço reservado pré-definido cujo valor é resolvido por Teams Toolkit, definido em `state.{env}.json`. Certifique-se de não modificar os valores em estado. {env}.json.
* `{{config.manifest.xx}}` é um espaço reservado personalizado cujo valor é resolvido de `config.{env}.json`.
  * Você pode adicionar um parâmetro personalizado da seguinte forma:
    * Adicione um espaço reservado em manifest.remote.template.json com padrão: `{{config.manifest.xx}}`
    * Adicione um valor config em config. {env}.json

        ```json
        {
            "manifest": {
                "KEY": "VALUE"
            }
        }
        ```

    Além de cada espaço reservado de configuração em `manifest.remote.template.json`, há um `Go to config file`. Você pode navegar até o arquivo de configuração selecionando-o.

## <a name="supported-placeholder-in-manifestlocaltemplatejson"></a>Espaço reservado suportado em manifest.local.template.json

`{{localSettings.xx}}`é um espaço reservado pré-definido cujo valor é resolvido por Teams Toolkit, definido em `localSettings.json`. Certifique-se de não modificar os valores em localSettings.json.

 > [!NOTE]
 > Certifique-se de não personalizar o manifesto local.

## <a name="see-also"></a>Confira também

[Visualizar Teams Manifesto do Aplicativo no Teams Toolkit](TeamsFx-manifest-preview.md)
