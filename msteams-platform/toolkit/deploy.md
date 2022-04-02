---
title: Implantar na nuvem
author: MuyangAmigo
description: Implantar aplicativo na nuvem, no Azure ou SharePoint
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 35a60e718bb97cdcc24de66729e3929b2d21a59f
ms.sourcegitcommit: 2236204ff710f4eca606ceffb233572981f6edbe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/01/2022
ms.locfileid: "64614527"
---
# <a name="deploy-to-the-cloud"></a>Implantar na nuvem

Teams Toolkit ajuda você a implantar ou carregar o código front-end e back-end em seu aplicativo para seus recursos de nuvem provisionados no Azure.

* A guia, como aplicativos front-end, é implantada no armazenamento do Azure e configurada para hospedagem estática da Web ou um site do sharepoint.
* As APIs de back-end são implantadas nas funções do Azure.
* O bot ou extensão de mensagens é implantado no serviço de aplicativo do Azure.

## <a name="prerequisite"></a>Pré-requisito

* [Instale Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) versão v3.0.0+.

> [!NOTE]
>
> * Verifique se você Teams projeto de aplicativo aberto em código VS.
> * Antes de implantar o código do projeto na nuvem, [provisione os recursos de nuvem](provision.md).

## <a name="deploy-teams-apps-using-teams-toolkit"></a>Implantar Teams aplicativos usando Teams Toolkit

As guias de início ajudam você a implantar usando Teams Toolkit. Você pode usar o seguinte para implantar seu Teams aplicativo:

* [Implantar seu aplicativo no Azure](/microsoftteams/platform/sbs-gs-javascript?tabs=vscode%2Cvsc%2Cviscode%2Cvcode&tutorial-step=8&branch)
* [Implantar seu aplicativo para SharePoint](/microsoftteams/platform/sbs-gs-spfx?tabs=vscode%2Cviscode&tutorial-step=4&branch)

## <a name="details-on-teams-app-workload"></a>Detalhes sobre a carga de trabalho Teams aplicativo

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
* [Criar e implantar um serviço de nuvem do Azure](/azure/cloud-services/cloud-services-how-to-create-deploy-portal)
* [Adicionar mais recursos Teams aplicativos](add-capability.md)
* [Implantar código de projeto com pipelines CI/CD](use-CICD-template.md)
* [Gerenciar vários ambientes](TeamsFx-multi-env.md)
* [Colaborar com outros desenvolvedores no projeto do Teams](TeamsFx-collaboration.md)
