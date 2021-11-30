---
title: Implantar na nuvem
author: MuyangAmigo
description: Implantar na nuvem
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 3f7dc4b320bccfa8a6017f87045b27a37d8199f7
ms.sourcegitcommit: f1e6f90fb6f7f5825e55a6d18ccf004d0091fb6d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2021
ms.locfileid: "61227667"
---
# <a name="deploy-to-the-cloud"></a>Implantar na nuvem

Teams Toolkit ajuda você a implantar ou carregar o código front-end e back-end em seu aplicativo para seus recursos de nuvem provisionados no Azure.

* A Guia, como aplicativos front-end, é implantada no armazenamento do Azure e configurada para hospedagem estática da Web ou um site SharePoint site.
* As APIs de back-end são implantadas nas Funções do Azure.
* O Bot ou a Extensão de Mensagens é implantado no Serviço de Aplicativo do Azure.

## <a name="prerequisite"></a>Pré-requisito

* [Instale Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) versão v3.0.0+.

> [!TIP]
> Você já deve ter um projeto Teams aplicativo aberto em código VS.

> [!NOTE]
> Antes de implantar o código do projeto na nuvem, execute as etapas de [provisionamento de recursos de nuvem](provision.md) primeiro.


## <a name="deploy-teams-apps-using-teams-toolkit"></a>Implantar Teams aplicativos usando Teams Toolkit

Em Tutoriais introdução, há guias passo a passo de como implantar usando Teams Toolkit. Você pode usar o seguinte para implantar seu Teams aplicativo:

* [Implantar seu aplicativo no Azure](/microsoftteams/platform/sbs-gs-javascript?tabs=vscode%2Cvsc%2Cviscode%2Cvcode&tutorial-step=8&branch)
* [Implantar seu aplicativo para SharePoint](/microsoftteams/platform/sbs-gs-spfx?tabs=vscode%2Cviscode&tutorial-step=4&branch)

## <a name="details-on-teams-app-workloads"></a>Detalhes sobre Teams cargas de trabalho do aplicativo

| Teams cargas de trabalho do aplicativo| Código-fonte | Criar Artifacts| Recursos de destino |
|-------------|----------|---------------|---------------|
|Guias com React </br> A carga de trabalho front-end| `yourProjectFolder/tabs`| `tabs/build` |Armazenamento do Microsoft Azure |
|Guias com SharePoint </br> A carga de trabalho front-end | `yourProjectFolder/SPFx`| `SPFx/sharepoint/solution` |SharePoint catálogo de aplicativos |
|APIs em Funções do Azure </br> A carga de trabalho de back-end | `yourProjectFolder/api`| N/D |Azure Functions |
|Bots e extensões de mensagens </br> A carga de trabalho de back-end | `yourProjectFolder/bot` | N/D | Serviço de Aplicativo do Azure |

> [!NOTE]
> Quando você inclui o recurso de gerenciamento da API do Azure em seu projeto e dispara a implantação. Você pode publicar suas APIs em Funções do Azure no Serviço de Gerenciamento de API do Azure.

## <a name="see-also"></a>Confira também

> [!div class="nextstepaction"]
> [Adicionar mais recursos de nuvem](add-resource.md)

> [!div class="nextstepaction"]
> [Adicionar mais recursos Teams aplicativos](add-capability.md)

> [!div class="nextstepaction"]
> [Implantar código de projeto com pipelines CI/CD](use-CICD-template.md)

> [!div class="nextstepaction"]
> [Gerenciar vários ambientes](TeamsFx-multi-env.md)

> [!div class="nextstepaction"]
> [Colaborar com outros desenvolvedores no Teams projeto](TeamsFx-collaboration.md)
