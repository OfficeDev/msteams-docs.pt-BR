---
title: Implantar na nuvem
author: MuyangAmigo
description: Neste módulo, saiba como implantar o aplicativo na nuvem, no Azure ou no SharePoint e implantar aplicativos do Teams usando o Kit de Ferramentas do Teams
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
zone_pivot_groups: teams-app-platform
ms.openlocfilehash: 4f5afe23e9d8deefdf2b1b182fa51cfe034e5c4d
ms.sourcegitcommit: 40d4bde10b6820c62e49e2400b10ab3569c8c815
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68615139"
---
# <a name="deploy-teams-app-to-the-cloud"></a>Implantar o aplicativo Teams na nuvem

O Kit de Ferramentas do Teams ajuda você a implantar ou carregar o código de front-end e back-end em seu aplicativo para seus recursos de nuvem provisionados no Azure.

::: zone pivot="visual-studio-code"

## <a name="deploy-teams-app-to-the-cloud-using-visual-studio-code"></a>Implantar o aplicativo Teams na nuvem usando o Visual Studio Code

Você pode implantar o seguinte na nuvem:

* A guia, como aplicativos front-end, é implantada no Armazenamento do Azure e configurada para hospedagem na Web estática ou um site do SharePoint.
* As APIs de back-end são implantadas em Azure Functions.
* O bot ou a extensão de mensagem é implantado Serviço de Aplicativo do Azure.

  > [!NOTE]
  > Antes de implantar o código do aplicativo na nuvem do Azure, você precisa concluir com [êxito o provisionamento de recursos de nuvem](provision.md).

## <a name="deploy-teams-apps-using-teams-toolkit"></a>Implantar os aplicativos do Teams usando o Kit de Ferramentas do Teams

Os guias de introdução ajudam você a implantar usando o Kit de Ferramentas do Teams. Você pode usar o seguinte para implantar seu aplicativo do Teams:

* [Implantar seu aplicativo no Azure.](/microsoftteams/platform/sbs-gs-javascript?tabs=vscode%2Cvsc%2Cviscode%2Cvcode&tutorial-step=8&branch)
* [Implantar sua extensão no SharePoint](/microsoftteams/platform/sbs-gs-spfx?tabs=vscode%2Cviscode&tutorial-step=4&branch)

## <a name="details-on-teams-app-workload"></a>Detalhes sobre a carga de trabalho do aplicativo do Teams

| Carga de trabalho do aplicativo do Teams | Código-fonte | Artefato do Build| Recurso de destino |
|-------------|----------|---------------|---------------|
|Guias com Reagir </br> A carga de trabalho de front-end| `yourProjectFolder/tabs`| `tabs/build` |Armazenamento do Microsoft Azure |
|Guias com o SharePoint </br> A carga de trabalho de front-end | `yourProjectFolder/SPFx`| `SPFx/sharepoint/solution` |Catálogo de aplicativos do SharePoint |
|APIs em Azure Functions </br> A carga de trabalho de back-end | `yourProjectFolder/api`| Não aplicável |Azure Functions |
|Bots e extensões de mensagem </br> A carga de trabalho de back-end | `yourProjectFolder/bot` | Não aplicável | Serviço do Aplicativo do Azure |

> [!NOTE]
> Ao incluir o recurso de gerenciamento de API do Azure em seu projeto e disparar a implantação, você pode publicar suas APIs em Azure Functions serviço de gerenciamento de API do Azure.

::: zone-end

::: zone pivot="visual-studio"

## <a name="deploy-teams-app-to-the-cloud-using-visual-studio"></a>Implantar o aplicativo Teams na nuvem usando o Visual Studio

Os seguintes aplicativos podem ser implantados no Visual Studio:

* O aplicativo guia, como aplicativos de front-end, é implantado no Armazenamento do Azure, configurado para hospedagem na Web estática.
* O aplicativo de bot de notificação com Azure Functions gatilhos pode ser implantado em Azure Functions.
* O aplicativo de bot ou a extensão de mensagem pode ser implantado Azure App Serviços.

Após a implantação, você pode visualizar o aplicativo no cliente do Teams ou no navegador da Web antes de começar a usar.

## <a name="deploy-teams-app-using-teams-toolkit"></a>Implantar o aplicativo Teams usando o Kit de Ferramentas do Teams

1. Abra o Visual Studio.
1. Selecione **Criar um novo projeto** ou abra um projeto existente na lista.
1. Clique com o botão direito do mouse no **projeto MyTeamsApp1** > **Teams Toolkit** > **Deploy na nuvem**.

   :::image type="content" source="../assets/images/deploy-teams-app-cloud-vs/vs-deploy-cloud.png" alt-text="implantar na nuvem":::

   > [!NOTE]
   > Nesse cenário, o nome do projeto é MyTeamsApp1.

1. Selecione **Implantar** na caixa de diálogo de confirmação.

   :::image type="content" source="../assets/images/deploy-teams-app-cloud-vs/vs-deploy-confirmation.png" alt-text="Caixa de diálogo Implantar na nuvem de confirmação":::

   Depois que o processo de implantação for concluído, você poderá ver um pop-up com a confirmação de que ele foi implantado com êxito. Você também pode verificar o status na janela de saída.

   :::image type="content" source="../assets/images/deploy-teams-app-cloud-vs/VS-deploy-popup.png" alt-text="implantar no pop-up de nuvem":::

### <a name="preview-your-app"></a>Visualizar seu aplicativo

Para visualizar seu aplicativo, primeiro você precisa criar um pacote do aplicativo Zip e fazer sideload no cliente do Teams.

1. Selecione **Pacote do Aplicativo****Zip do Kit de** >  Ferramentas **do** Project  >  Teams.
1. Selecione a **opção Local** ou **Para o Azure para** gerar o pacote de aplicativos do Teams.

   :::image type="content" source="../assets/images/deploy-teams-app-cloud-vs/vs-deploy-ZipApp-package1.png" alt-text="Gerar pacote de aplicativos do Teams":::

**Para visualizar seu aplicativo no cliente do Teams**

1. Selecione **o Project** > **Teams Toolkit** > **Preview no Teams**.

   :::image type="content" source="../assets/images/deploy-teams-app-cloud-vs/vs-deploy-preview-teams2.png" alt-text="Visualizar o aplicativo Teams no cliente do Teams":::

   Agora seu aplicativo é sideload no Teams.

   :::image type="content" source="../assets/images/deploy-teams-app-cloud-vs/sideload-teams.png" alt-text="Realizar sideload do aplicativo Teams no cliente do Teams":::

A outra maneira de visualizar seu aplicativo:

1. Clique com o botão direito do mouse **no projeto MyTeamsApp1** **em Gerenciador de Soluções**.
1. Selecione **o Teams Toolkit** > **Preview no Teams** para iniciar o aplicativo Teams no navegador da Web.

   :::image type="content" source="../assets/images/deploy-teams-app-cloud-vs/vs-deploy-preview-teams.png" alt-text="Visualizar o aplicativo teams no navegador da Web":::

   > [!NOTE]
   > As mesmas opções de menu estão disponíveis no menu Projeto.

   Agora seu aplicativo é sideload no Teams.

   :::image type="content" source="../assets/images/deploy-teams-app-cloud-vs/sideload-teams.png" alt-text="Realizar sideload do aplicativo Teams no cliente do Teams":::

::: zone-end

## <a name="see-also"></a>Confira também

* [Criar e implantar um serviço na nuvem do Azure](/azure/cloud-services/cloud-services-how-to-create-deploy-portal)
* [Criar aplicativos do Teams de vários recursos](add-capability.md)
* [Adicionar recursos de nuvem ao aplicativo Microsoft Teams](add-resource.md)
* [Criar um novo aplicativo teams no Visual Studio](create-new-teams-app-for-Visual-Studio.md)
* [Provisionar recursos de nuvem usando o Visual Studio](provision-cloud-resources.md)
* [Editar manifesto do aplicativo Teams usando o Visual Studio](VS-TeamsFx-preview-and-customize-app-manifest.md)
* [Depurar seu aplicativo teams localmente usando o Visual Studio](debug-teams-app-visual-studio.md)
