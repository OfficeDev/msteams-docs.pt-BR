---
title: Implantar na nuvem
author: MuyangAmigo
description: Implantar na nuvem
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 0eeda4842ad3f0443d46b5075b1520b0042130ec
ms.sourcegitcommit: 2d5bdda6c52693ed682bbd543b0aa66e1feb3392
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/12/2022
ms.locfileid: "61768375"
---
# <a name="deploy-to-the-cloud"></a>Implantar na nuvem

Teams Toolkit ajuda você a implantar ou carregar o código front-end e back-end em seu aplicativo para seus recursos de nuvem provisionados no Azure.

* A guia, como aplicativos front-end, é implantada no armazenamento do Azure e configurada para hospedagem estática da Web ou um site do sharepoint.
* As APIs de back-end são implantadas nas funções do Azure.
* O bot ou extensão de mensagens é implantado no serviço de aplicativo do Azure.

## <a name="prerequisite"></a>Pré-requisito

* [Instale Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) versão v3.0.0+.

> [!NOTE]
> * Verifique se você Teams projeto de aplicativo aberto em código VS.
> * Antes de implantar o código do projeto na nuvem, [provisione os recursos de nuvem.](provision.md)

## <a name="deploy-teams-apps-using-teams-toolkit"></a>Implantar Teams aplicativos usando Teams Toolkit

Os guias de início ajudam você a implantar usando Teams Toolkit. Você pode usar o seguinte para implantar seu Teams aplicativo:
* [Implantar seu aplicativo no Azure](/microsoftteams/platform/sbs-gs-javascript?tabs=vscode%2Cvsc%2Cviscode%2Cvcode&tutorial-step=8&branch)
* [Implantar seu aplicativo para SharePoint](/microsoftteams/platform/sbs-gs-spfx?tabs=vscode%2Cviscode&tutorial-step=4&branch)

## <a name="details-on-teams-app-workload"></a>Detalhes sobre a Teams de aplicativo

| Teams carga de trabalho do aplicativo | Código-fonte | Artefato de com build| Recurso Target |
|-------------|----------|---------------|---------------|
|Guias com React </br> A carga de trabalho front-end| `yourProjectFolder/tabs`| `tabs/build` |Armazenamento do Azure |
|Guias com SharePoint </br> A carga de trabalho front-end | `yourProjectFolder/SPFx`| `SPFx/sharepoint/solution` |SharePoint catálogo de aplicativos |
|APIs em funções do Azure </br> A carga de trabalho de back-end | `yourProjectFolder/api`| Não aplicável |Funções do Azure |
|Bots e extensões de mensagens </br> A carga de trabalho de back-end | `yourProjectFolder/bot` | Não aplicável | Serviço de aplicativo do Azure |

> [!NOTE]
> Quando você inclui o recurso de gerenciamento da API do Azure em seu projeto e dispara a implantação. Você pode publicar suas APIs nas funções do Azure no serviço de gerenciamento de API do Azure.

## <a name="see-also"></a>Confira também

* [Adicionar mais recursos de nuvem](add-resource.md)
* [Adicionar mais recursos Teams aplicativos](add-capability.md)
* [Implantar código de projeto com pipelines CI/CD](use-CICD-template.md)
* [Gerenciar vários ambientes](TeamsFx-multi-env.md)
* [Colaborar com outros desenvolvedores no Teams projeto](TeamsFx-collaboration.md)
