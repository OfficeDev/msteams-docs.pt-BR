---
title: Implantar na nuvem
author: MuyangAmigo
description: Implantar aplicativo na nuvem, no Azure ou SharePoint
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 1d0ade9abed4be212abfb96068626172c4f0f03e
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65104144"
---
# <a name="deploy-to-the-cloud"></a>Implantar na nuvem

Teams Toolkit ajuda você a implantar ou carregar o código de front-end e back-end em seu aplicativo para seus recursos de nuvem provisionados no Azure.

* A guia, como aplicativos de front-end, é implantada no armazenamento do Azure e configurada para hospedagem na Web estática ou um site do SharePoint.
* As APIs de back-end são implantadas nas funções do Azure.
* O bot ou a extensão de mensagem é implantado no serviço de aplicativo do Azure.

## <a name="prerequisite"></a>Pré-requisito

* [Instale Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) versão v3.0.0+.

> [!NOTE]
>
> * Verifique se você Teams projeto de aplicativo aberto no VS Code.
> * Antes de implantar o código do projeto na nuvem, [provisione os recursos de nuvem](provision.md).

## <a name="deploy-teams-apps-using-teams-toolkit"></a>Implantar Teams aplicativos usando Teams Toolkit

Os guias de introdução ajudam você a implantar usando Teams Toolkit. Você pode usar o seguinte para implantar seu Teams aplicativo:

* [Implantar seu aplicativo no Azure](/microsoftteams/platform/sbs-gs-javascript?tabs=vscode%2Cvsc%2Cviscode%2Cvcode&tutorial-step=8&branch)
* [Implantar seu aplicativo no SharePoint](/microsoftteams/platform/sbs-gs-spfx?tabs=vscode%2Cviscode&tutorial-step=4&branch)

## <a name="details-on-teams-app-workload"></a>Detalhes sobre a carga Teams do aplicativo

| Teams de trabalho do aplicativo | Código-fonte | Artefato de build| Recurso de destino |
|-------------|----------|---------------|---------------|
|Guias com React </br> A carga de trabalho de front-end| `yourProjectFolder/tabs`| `tabs/build` |Armazenamento do Azure |
|Guias com SharePoint </br> A carga de trabalho de front-end | `yourProjectFolder/SPFx`| `SPFx/sharepoint/solution` |SharePoint de aplicativos |
|APIs no Azure Functions </br> A carga de trabalho de back-end | `yourProjectFolder/api`| Não aplicável |Azure Functions |
|Bots e extensões de mensagem </br> A carga de trabalho de back-end | `yourProjectFolder/bot` | Não aplicável | Serviço de aplicativo do Azure |

> [!NOTE]
> Quando você inclui o recurso de gerenciamento de API do Azure em seu projeto e dispara a implantação. Você pode publicar suas APIs no Azure Functions no serviço de gerenciamento de API do Azure.

## <a name="see-also"></a>Confira também

* [Adicionar mais recursos de nuvem](add-resource.md)
* [Criar e implantar um serviço de nuvem do Azure](/azure/cloud-services/cloud-services-how-to-create-deploy-portal)
* [Adicionar mais recursos Teams aplicativo](add-capability.md)
* [Implantar o código do projeto com pipelines de CI/CD](use-CICD-template.md)
* [Gerenciar vários ambientes](TeamsFx-multi-env.md)
* [Colaborar com outros desenvolvedores no projeto do Teams](TeamsFx-collaboration.md)
