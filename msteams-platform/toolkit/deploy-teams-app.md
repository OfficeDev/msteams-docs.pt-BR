---
title: Implantar o aplicativo Teams na nuvem usando o Visual Studio
author: surbhigupta
description: Neste módulo, saiba como implantar o aplicativo na nuvem, no Azure ou no SharePoint e implantar aplicativos do Teams usando o Kit de Ferramentas do Teams no Visual Studio
ms.author: v-amprasad
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: be4eeb10e16b0dda4d789e4607ac8ffbc302b0e1
ms.sourcegitcommit: 65ae3ccc2312ddc6cdaa05096e30bdf9dca10c3f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68027418"
---
# <a name="deploy-teams-app-to-the-cloud-using-visual-studio"></a>Implantar o aplicativo Teams na nuvem usando o Visual Studio

O Kit de Ferramentas do Teams ajuda você a implantar ou carregar o código de front-end e back-end do aplicativo para os recursos de nuvem provisionados em sua assinatura do Azure. Após a implantação, você pode visualizar o aplicativo no cliente do Teams ou no navegador da Web antes de começar a usar. Os seguintes aplicativos podem ser implantados no Visual Studio:

* O aplicativo guia, como aplicativos de front-end, é implantado no armazenamento do Azure, configurado para hospedagem na Web estática.
* O aplicativo de bot de notificação com gatilhos de função do Azure pode ser implantado no Azure Functions.
* O aplicativo de bot ou a extensão de mensagem pode ser implantado nos serviços de aplicativo do Azure.

## <a name="prerequisite"></a>Pré-requisito

Aqui está uma lista de ferramentas necessárias para criar e implantar seus aplicativos.

| &nbsp; | Instalar | Para usar... |
| --- | --- | --- |
| &nbsp; | **Required** | &nbsp; |
| &nbsp; | Visual Studio 2022 versão 17.3 | Você pode instalar a edição enterprise do Visual Studio e instalar a carga de trabalho "ASP.NET" e as Ferramentas de Desenvolvimento do Microsoft Teams. |
| &nbsp; | Kit de ferramentas do Teams | Uma extensão do Visual Studio que cria um scaffolding de projeto para seu aplicativo. Use a versão mais recente. |
| &nbsp; | [Microsoft Teams](https://www.microsoft.com/microsoft-teams/download-app) | O Microsoft Teams para colaborar com todos com quem você trabalha por meio de aplicativos para chats, reuniões, chamadas - tudo em um só lugar. |
| &nbsp; | Ferramentas do Azure e [CLI do Microsoft Azure](/cli/azure/install-azure-cli) | Ferramentas do Azure para acessar dados armazenados ou implantar um back-end baseado em nuvem para seu aplicativo Teams no Azure. |

  > [!NOTE]
  > Antes de implantar o código do projeto na nuvem, [provisione recursos de nuvem para o Visual Studio do TTK](provision VS.md).

## <a name="deploy-teams-app-using-teams-toolkit"></a>Implantar o aplicativo Teams usando o Kit de Ferramentas do Teams

1. Inicie o Visual Studio.
1. Selecione **Criar um novo projeto** ou abra um projeto existente na lista.
1. Clique com o botão direito do mouse **no projeto MyTeamsApp1**.
1. Selecione **o Kit de Ferramentas do Teams**.
1. Selecione **Implantar na nuvem...**

   :::image type="content" source="../assets/images/deploy-teams-app-cloud-vs/vs-deploy-cloud.png" alt-text="implantar na nuvem":::

   > [!NOTE]
   > Nesse cenário, o nome do projeto é MyTeamsApp1.

1. Selecione **Implantar** na caixa de diálogo de confirmação.

   :::image type="content" source="../assets/images/deploy-teams-app-cloud-vs/vs-deploy-confirmation.png" alt-text="Caixa de diálogo Implantar na nuvem de confirmação":::

1. Depois que o processo de implantação for disparado e concluído, você poderá ver um pop-up com a confirmação de que ele foi implantado com êxito. Você também pode verificar o status na janela de saída.

   :::image type="content" source="../assets/images/deploy-teams-app-cloud-vs/VS-deploy-popup.png" alt-text="implantar no pop-up de nuvem":::

Depois que o projeto é implantado com êxito no Azure, há diferentes maneiras de visualizar seu aplicativo no Kit de Ferramentas do Teams:

1. Selecione **Pacote do****Aplicativo Zip do Kit** >  de Ferramentas **do** Project  >  Teams para gerar o pacote de aplicativos do Teams.
1. Selecione a **opção Local** ou **Para o Azure e** carregue no cliente do Teams.

   :::image type="content" source="../assets/images/deploy-teams-app-cloud-vs/vs-deploy-ZipApp-package.png" alt-text="Gerar pacote de aplicativos do Teams":::

  **Para visualizar seu aplicativo no cliente do Teams**

3. Selecione **Projeto**.
4. Selecione **o Kit de Ferramentas do Teams**.
5. Selecione **Visualizar no Teams**.

   :::image type="content" source="../assets/images/deploy-teams-app-cloud-vs/vs-deploy-preview-teams1.png" alt-text="Visualizar o aplicativo Teams no cliente do Teams":::

A outra maneira de visualizar seu aplicativo:

1. Clique com o botão direito do mouse **no projeto MyTeamsApp1** no painel Gerenciador de Soluções segurança.
1. Selecione **o Kit de Ferramentas do Teams**.
1. Selecione **Visualizar no Teams** para iniciar o aplicativo Teams no navegador da Web.

   :::image type="content" source="../assets/images/deploy-teams-app-cloud-vs/vs-deploy-preview-teams.png" alt-text="Visualizar o aplicativo teams no navegador da Web":::

   > [!NOTE]
   > As mesmas opções de menu estão disponíveis no menu Projeto.

## <a name="see-also"></a>Confira também

* [Criar um novo aplicativo teams no Visual Studio](create-new-teams-app-for-Visual-Studio.md)
* [Provisionar recursos de nuvem usando o Visual Studio](provision-cloud-resources.md)
* [Editar manifesto do aplicativo Teams usando o Visual Studio](VS-TeamsFx-preview-and-customize-app-manifest.md)
* [Depurar seu aplicativo teams localmente usando o Visual Studio](debug-teams-app-visual-studio.md)
