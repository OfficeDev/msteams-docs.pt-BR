---
title: Personalizar Teams manifesto do aplicativo no Teams Toolkit
author: zyxiaoyuer
description: Personalizar Manifesto do Aplicativo Teams
ms.author: nliu
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: de85674891a53c1e87b43ae1d472daf35716c348
ms.sourcegitcommit: 3bfd0d2c4d83f306023adb45c8a3f829f7150b1d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65073537"
---
# <a name="customize-app-manifest-in-toolkit"></a>Personalizar o manifesto do aplicativo Toolkit

Teams Toolkit consiste nos seguintes arquivos de modelo de manifesto em `manifest.template.json` pasta em ambientes locais e remotos:

* `manifest.template.json`
* `templates/appPackage`


## <a name="prerequisite"></a>Pré-requisito

* Instalar a [versão mais recente do Kit de Ferramentas do Teams](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension).

> [!TIP]
> Verifique se você Teams projeto de aplicativo aberto Visual Studio Code.

Durante a depuração ou provisionamento `manifest.template.json`local, Teams Toolkit carrega o manifesto de , `state.{env}.json`com configurações de , `config.{env}.json`e cria o aplicativo teams no [Portal de Desenvolvimento](https://dev.teams.microsoft.com/apps).


## <a name="placeholders-supported-in-manifesttemplatejson"></a>Espaços reservados com suporte em manifest.template.json

* `{{state.xx}}`é um espaço reservado predefinido e seu valor é resolvido por Teams Toolkit, definido em `state.{env}.json`. Certifique-se de não modificar os valores no estado. {env}.json
* `{{config.manifest.xx}}` é um espaço reservado personalizado e seu valor é resolvido de `config.{env}.json`

  1. Você pode adicionar um parâmetro personalizado da seguinte maneira:
      1. Adicione um espaço reservado em manifest.template.json com padrão: `{{config.manifest.xx}}`
      2. Adicione um valor de configuração na configuração. {env}.json

        ```json
        {
            "manifest": {
                "KEY": "VALUE"
            }
        }
        ```

   2. Você pode navegar até o arquivo de configuração selecionando qualquer um dos espaços reservados de configuração **Ir** para o arquivo de configuração ou **Exibir o arquivo de estado** em `manifest.template.json`

## <a name="see-also"></a>Confira também

[Visualizar Teams manifesto do aplicativo no Teams Toolkit](TeamsFx-manifest-preview.md)
