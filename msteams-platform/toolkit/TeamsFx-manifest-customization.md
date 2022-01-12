---
title: Personalizar Teams Manifesto do Aplicativo no Teams Toolkit
author: zyxiaoyuer
description: Personalizar Manifesto do Aplicativo Teams
ms.author: nliu
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: d9f2ea49ece8728101a738129e45dd8155887ebc
ms.sourcegitcommit: 2d5bdda6c52693ed682bbd543b0aa66e1feb3392
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/12/2022
ms.locfileid: "61768074"
---
# <a name="customize-app-manifest-in-teams-toolkit"></a>Personalizar o manifesto do aplicativo Teams Toolkit

Teams Toolkit consiste nos seguintes arquivos de modelo de manifesto na `templates/appPackage` pasta:

- `manifest.local.template.json` - aplicativo de equipes de depuração local
- `manifest.remote.template.json` - compartilhado em todos os ambientes

## <a name="prerequisite"></a>Pré-requisito

* [Instale Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) versão v3.0.0+.

> [!TIP]
> Verifique se você Teams projeto de aplicativo aberto VS Code.

Durante a provisionamento, Teams Toolkit carrega manifesto de , combinado com configurações de e , e cria o `manifest.remote.template.json` aplicativo teams no Portal de `state.{env}.json` `config.{env}.json` [Dev](https://dev.teams.microsoft.com/apps).

Durante a depuração local, Teams Toolkit carrega manifesto de , combinado com configurações de , e cria o `manifest.local.template.json` aplicativo teams no Portal de `localSettings.json` [Desenvolvimento](https://dev.teams.microsoft.com/apps).

## <a name="supported-placeholder-in-manifestremotetemplatejson"></a>Espaço reservado suportado em manifest.remote.template.json

- `{{state.xx}}`é um espaço reservado pré-definido cujo valor é resolvido por Teams Toolkit, definido em `state.{env}.json` . Certifique-se de não modificar os valores em estado. {env}.json.
- `{{config.manifest.xx}}` é um espaço reservado personalizado cujo valor é resolvido de `config.{env}.json` .
  - Você pode adicionar um parâmetro personalizado da seguinte forma:
    - Adicione um espaço reservado em manifest.remote.template.json com padrão: `{{config.manifest.xx}}`
    - Adicione um valor config em config. {env}.json

        ```json
        {
            "manifest": {
                "KEY": "VALUE"
            }
        }
        ```

    Além de cada espaço reservado de configuração `manifest.remote.template.json` em , há um `Go to config file` . Você pode navegar até o arquivo de configuração selecionando-o.

## <a name="supported-placeholder-in-manifestlocaltemplatejson"></a>Espaço reservado suportado em manifest.local.template.json

`{{localSettings.xx}}`é um espaço reservado pré-definido cujo valor é resolvido por Teams Toolkit, definido em `localSettings.json` . Certifique-se de não modificar os valores em localSettings.json.

 > [!NOTE]
 > Certifique-se de não personalizar o manifesto local.

## <a name="see-also"></a>Confira também

[Visualizar Teams Manifesto do Aplicativo no Teams Toolkit](TeamsFx-manifest-preview.md)
