---
title: Implantar na nuvem
author: MuyangAmigo
description: Implantar aplicativo na nuvem, no Azure ou no SharePoint
ms.author: zhany
ms.localizationpriority: high
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 3e9368dcaa87003da2872a500ffaa281092774df
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111567"
---
# <a name="deploy-to-the-cloud"></a>Implantar na nuvem

O Kit de Ferramentas do Teams o ajuda a implantar ou carregar o código de front-end e back-end no seu aplicativo para seus recursos na nuvem provisionados no Azure.

* A guia, como os aplicativos de front-end, é implantada no armazenamento do Azure e configurada para hospedagem na Web estática ou um site do SharePoint.
* As APIs de back-end são implantadas nas funções do Azure.
* O bot ou a extensão de mensagem são implantados no serviço de aplicativo do Azure.

## <a name="prerequisite"></a>Pré-requisito

* [Instalar o Kit de Ferramentas do Teams](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) versão v3.0.0+.

> [!NOTE]
>
> * Certifique-se de ter o projeto do aplicativo Teams aberto no VS code.
> * Antes de implantar o código do projeto na nuvem, [provisione os recursos na nuvem](provision.md).

## <a name="deploy-teams-apps-using-teams-toolkit"></a>Implantar os aplicativos do Teams usando o Kit de Ferramentas do Teams

Os guias de introdução o ajudam a implantar usando o Kit de Ferramentas do Teams. Você pode usar o seguinte para implantar seu aplicativo do Teams:

* [Implantar seu aplicativo no Azure.](/microsoftteams/platform/sbs-gs-javascript?tabs=vscode%2Cvsc%2Cviscode%2Cvcode&tutorial-step=8&branch)
* [Implantar sua extensão no SharePoint](/microsoftteams/platform/sbs-gs-spfx?tabs=vscode%2Cviscode&tutorial-step=4&branch)

## <a name="details-on-teams-app-workload"></a>Detalhes sobre a carga de trabalho do aplicativo do Teams

| Carga de trabalho do aplicativo do Teams | Código-fonte | Artefato do Build| Recurso de destino |
|-------------|----------|---------------|---------------|
|Guias com Reagir </br> A carga de trabalho de front-end| `yourProjectFolder/tabs`| `tabs/build` |Armazenamento do Azure |
|Guias com o SharePoint </br> A carga de trabalho de front-end | `yourProjectFolder/SPFx`| `SPFx/sharepoint/solution` |Catálogo de aplicativos do SharePoint |
|APIs nas funções do Azure </br> A carga de trabalho de back-end | `yourProjectFolder/api`| Não aplicável |Funções do Azure |
|Bots e extensões de mensagem </br> A carga de trabalho de back-end | `yourProjectFolder/bot` | Não aplicável | Serviço do Aplicativo do Azure |

> [!NOTE]
> Quando você inclui o recurso de gerenciamento da API do Azure no seu projeto e dispara a implantação. Você pode publicar suas APIs nas Fnções do Azure no serviço de gerenciamento da API do Azure.

## <a name="see-also"></a>Confira também

* [Adicionar mais recursos na nuvem](add-resource.md)
* [Criar e implantar um serviço na nuvem do Azure](/azure/cloud-services/cloud-services-how-to-create-deploy-portal)
* [Adicionar mais recursos do aplicativo do Teams](add-capability.md)
* [Implantar o código do projeto com pipelines de CI/CD](use-CICD-template.md)
* [Gerenciar vários ambientes](TeamsFx-multi-env.md)
* [Colaborar com outros desenvolvedores no projeto do Teams](TeamsFx-collaboration.md)
