---
title: Personalizar o Manifesto do Aplicativo Teams no Kit de Ferramentas do Teams
author: zyxiaoyuer
description: Personalizar Manifesto do Aplicativo Teams
ms.author: nliu
ms.localizationpriority: high
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 28a06da170ee52e4340aa3d401d39ad08f58e2ba
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2022
ms.locfileid: "65110257"
---
# <a name="customize-app-manifest-in-toolkit"></a>Personalizar o manifesto do aplicativo no Kit de Ferramentas

O Kit de Ferramentas do Teams consiste nos seguintes arquivos de modelo de manifesto na pasta `manifest.template.json` em ambientes locais e remotos:

* `manifest.template.json`
* `templates/appPackage`


## <a name="prerequisite"></a>Pré-requisito

* Instalar a [versão mais recente do Kit de Ferramentas do Teams](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension).

> [!TIP]
> Certifique-se de que você tem um projeto de aplicativo Teams aberto no código do Visual Studio.

Durante a depuração ou provisionamento local, o Kit de Ferramentas do Teams carrega o manifesto do `manifest.template.json`, com configurações do `state.{env}.json`, `config.{env}.json`e cria o aplicativo teams no [Portal de Desenvolvimento](https://dev.teams.microsoft.com/apps).


## <a name="placeholders-supported-in-manifesttemplatejson"></a>Espaços reservados com suporte em manifest.template.json

* `{{state.xx}}` é um espaço reservado predefinido e seu valor é resolvido pelo Kit de Ferramentas do Teams, definido em `state.{env}.json`. Certifique-se de não modificar os valores no estado.{env}.json
* `{{config.manifest.xx}}` é um espaço reservado personalizado e seu valor é resolvido de `config.{env}.json`

  1. Você pode adicionar um parâmetro personalizado como se segue:
      1. Adicione um espaço reservado no manifest.template.json com o padrão: `{{config.manifest.xx}}`
      2. Adicione um valor de configuração em config.{env}.json

        ```json
        {
            "manifest": {
                "KEY": "VALUE"
            }
        }
        ```

   2. Você pode navegar até o arquivo de configuração selecionando qualquer um dos espaços reservados de configuração **Ir para o arquivo de configuração** ou **Exibir o arquivo de estado** no `manifest.template.json`

## <a name="see-also"></a>Confira também

[Visualizar Manifesto do Aplicativo Teams no Kit de Ferramentas do Teams](TeamsFx-manifest-preview.md)
