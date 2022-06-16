---
title: Colaborar no TeamsFx Project usando Teams Toolkit
author: yanjiang
description: Colaborar no TeamsFx Project usando Teams Toolkit
ms.author: rentu
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 099820252fd83a2d916e8d61f3b83b63291695e9
ms.sourcegitcommit: 5070746e736edb4ae77cd3efcb2ab8bb2e5819a0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/16/2022
ms.locfileid: "66124015"
---
# <a name="collaborate-on-teams-project-using-teams-toolkit"></a>Colaborar no projeto do Teams usando o Kit de Ferramentas do Teams

Vários desenvolvedores podem trabalhar juntos para depurar, provisionar e implantar para o mesmo projeto TeamsFx, mas isso requer a definição manual das permissões corretas do aplicativo Teams e Microsoft Azure Active Directory (Azure AD). Teams Toolkit dá suporte ao recurso de colaboração para permitir que os desenvolvedores e o proprietário do projeto convidem outros desenvolvedores ou colaboradores para o projeto TeamsFx para depurar, provisionar e implantar o mesmo projeto TeamsFx.

## <a name="prerequisites"></a>Pré-requisitos

* Assinatura do Microsoft 365
* Azure com assinatura válida
  
  Para obter mais informações sobre contas diferentes, consulte [preparar contas para criar Teams aplicativo](accounts.md).

* [Instalar Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) versão v3.0.0+

> [!TIP]
> Verifique se você tem um projeto Teams aplicativo aberto no Visual Studio Code.

## <a name="collaborate-with-other-developers"></a>Colaborar com outros desenvolvedores

As listas a seguir nos orientam a entender o processo de colaboração e sua limitação:

* Como proprietário do projeto

  > [!NOTE]
  > Antes de adicionar colaboradores para um ambiente, o proprietário do projeto precisa [provisionar](provision.md) o projeto primeiro.

  1. Na **seção ENVIRONMENT** no Teams Toolkit, selecione **colaboradores**. Ele exibe as opções Adicionar **proprietários do aplicativo Microsoft 365 Teams (com o aplicativo Azure AD)** e listar proprietários do aplicativo **Microsoft 365 Teams (com o aplicativo Azure AD),** conforme mostrado nas seguintes imagens:

     :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/add collaborators.png" alt-text="Colaboradores":::

  2. Selecione **Adicionar Microsoft 365 Teams Aplicativo (com Azure AD App)** e adicione outros Microsoft 365 endereço de email da conta como colaborador. A conta a ser adicionada deve estar no mesmo locatário que o proprietário do projeto para depuração remota, conforme mostrado na imagem:

     :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview-1.png" alt-text="add envi":::

  3. Para exibir colaboradores no ambiente atual, selecione Listar proprietários do aplicativo **Microsoft 365 Teams (com o aplicativo Azure AD)** e, em seguida, os colaboradores serão listados no canal de saída, conforme mostrado na imagem a seguir:

     :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/list of collaborators.png" alt-text="list":::

  4. Enviar por push o projeto para GitHub

     > [!NOTE]
     > Os colaboradores recém-adicionados não recebem nenhuma notificação. O Project proprietário precisa notificar o colaborador.

* Como colaborador do projeto

  1. Clone o projeto do GitHub.
  2. Faça logon Microsoft 365 conta.
  3. Faça logon na conta do Azure, ela tem permissão de colaborador para todos os recursos do Azure, que são usados no projeto.
  4. Para visualizar seu Teams, implante o projeto no modo remoto.
  5. Inicie remotamente para ter uma visualização do Teams aplicativo.

     > [!NOTE]
     > Os colaboradores devem fazer logon usando a conta que o proprietário do projeto adiciona no mesmo locatário com o proprietário do projeto. Para obter mais informações, [consulte compilar e executar seu aplicativo Teams no ambiente remoto](/microsoftteams/platform/sbs-gs-javascript?tabs=vscode%2Cvsc%2Cviscode%2Cvcode&tutorial-step=3&branch).

### <a name="limitations"></a>Limitações

Se você quiser remover colaboradores Teams Toolkit extensão, será necessário removê-los manualmente, pois não é possível removê-los diretamente. Execute as seguintes etapas para remover os colaboradores manualmente:

* Usando o Portal do Desenvolvedor

  * Vá para [Teams Portal do Desenvolvedor](https://dev.teams.microsoft.com/home) e selecione seu aplicativo Teams por nome ou ID do aplicativo.
  * Selecione **Proprietários** no painel esquerdo.
  * Selecione e remova o colaborador.

* Usando Azure Active Directory

  * Vá para [Azure Active Directory](https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredApps), selecione **Registro de** aplicativo no painel esquerdo e localize seu Azure AD Aplicativo.
  * Selecione **Proprietários** no painel esquerdo na Azure AD gerenciamento de aplicativos.
  * Selecione e remova o colaborador.

   > [!NOTE]
   >
   > * O colaborador adicionado ao seu projeto não recebe nenhuma notificação. Project proprietário precisa notificar o colaborador offline.
   > * As permissões relacionadas ao Azure devem ser definidas manualmente pelo administrador da assinatura do Azure portal do Azure. A conta do Azure deve ter função de colaborador para a assinatura para que os desenvolvedores possam trabalhar juntos para provisionar e implantar o projeto TeamsFx.

## <a name="see-also"></a>Confira também

* [Provisionar recursos de nuvem](provision.md)
* [Implantar o aplicativo Teams na nuvem](deploy.md)
* [Gerenciar vários ambientes](TeamsFx-multi-env.md)
