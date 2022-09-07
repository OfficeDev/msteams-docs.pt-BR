---
title: Implantar na nuvem
author: MuyangAmigo
description: Neste módulo, saiba como implantar o aplicativo na nuvem, no Azure ou no SharePoint e implantar aplicativos do Teams usando o Kit de Ferramentas do Teams
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 9ad2c9d16901990344ca521599b94b84b0e76217
ms.sourcegitcommit: ed7488415f814d0f60faa15ee8ec3d64ee336380
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2022
ms.locfileid: "67616923"
---
# <a name="deploy-teams-app-to-the-cloud"></a>Implantar o aplicativo Teams na nuvem

O Kit de Ferramentas do Teams o ajuda a implantar ou carregar o código de front-end e back-end no seu aplicativo para seus recursos na nuvem provisionados no Azure. Você pode implantar o seguinte na nuvem:

* A guia, como os aplicativos de front-end, é implantada no armazenamento do Azure e configurada para hospedagem na Web estática ou um site do SharePoint.
* As APIs de back-end são implantadas nas funções do Azure.
* O bot ou a extensão de mensagem são implantados no serviço de aplicativo do Azure.

  > [!NOTE]
  > Antes de implantar o código do aplicativo na nuvem do Azure, você precisa concluir com [êxito o provisionamento de recursos de nuvem](provision.md).

## <a name="deploy-teams-apps-using-teams-toolkit"></a>Implantar os aplicativos do Teams usando o Kit de Ferramentas do Teams

Os guias de introdução ajudam você a implantar usando o Kit de Ferramentas do Teams. Você pode usar o seguinte para implantar seu aplicativo do Teams:

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
> Ao incluir o recurso de gerenciamento de API do Azure em seu projeto e disparar a implantação, você pode publicar suas APIs nas funções do Azure no serviço de gerenciamento de API do Azure.

## <a name="see-also"></a>Confira também

* [Criar e implantar um serviço na nuvem do Azure](/azure/cloud-services/cloud-services-how-to-create-deploy-portal)
* [Criar aplicativos do Teams de vários recursos](add-capability.md)
* [Adicionar recursos de nuvem ao aplicativo Microsoft Teams](add-resource.md)
