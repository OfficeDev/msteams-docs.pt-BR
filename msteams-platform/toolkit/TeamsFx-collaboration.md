---
title: Colaborar no TeamsFx Project usando Teams Toolkit
author: yanjiang
description: Colaborar no TeamsFx Project usando Teams Toolkit
ms.author: rentu
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: af96227df93bb2c236607791e3870b1882d2da5f
ms.sourcegitcommit: 90587b1ec04bf20d716ed6feb8ccca4313e87f8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/10/2022
ms.locfileid: "62518370"
---
# <a name="collaborate-on-teams-project-using-teams-toolkit"></a>Colabore Teams projeto usando Teams Toolkit

Vários desenvolvedores podem trabalhar juntos para depurar, provisionar e implantar para o mesmo projeto TeamsFx, mas exige a definição manual das permissões corretas do Teams App e Microsoft Azure Active Directory (Azure AD) App.Teams Toolkit  oferece suporte ao recurso de colaboração para permitir que desenvolvedores e proprietários do projeto convidem outros desenvolvedores ou colaboradores para o projeto TeamsFx para depurar, provisionar e implantar o mesmo projeto TeamsFx.

## <a name="prerequisites"></a>Pré-requisitos

* Pré-requisitos da conta

    Para provisionar recursos de nuvem, você deve ter as seguintes contas. Para obter mais informações, consulte Prepare [accounts to build Teams app](accounts.md).

  * Assinatura do Microsoft 365
  * Azure com assinatura válida

* [Instale Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) versão v3.0.0+.

> [!TIP]
> Verifique se você tem um projeto Teams aplicativo aberto Microsoft Visual Studio código.

## <a name="collaborate-with-other-developers"></a>Colaborar com outros desenvolvedores

A lista a seguir nos orienta a entender o processo de colaboração e suas limitações:

### <a name="as-project-owner"></a>Como proprietário do projeto

> [!NOTE]
> Antes de adicionar colaboradores para um ambiente, o proprietário do projeto precisa [provisionar](provision.md) o projeto primeiro.

* Na **seção AMBIENTE** no Teams Toolkit, selecione **colaboradores**. Ele exibe as opções Adicionar Microsoft 365 Teams App (com proprietários do aplicativo **do Microsoft Azure Active Directory (Azure AD)** e **Listar Microsoft 365 Teams App (com o Azure AD App) Proprietários**, conforme mostrado nas seguintes imagens:

  :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/add collaborators.png" alt-text="colaboradores":::

* Selecione **Adicionar Microsoft 365 Teams App (com o aplicativo Microsoft Azure Active Directory (Azure AD) Proprietários e** adicione outro endereço de email de Microsoft 365 conta como colaborador. A conta a ser adicionada deve estar no mesmo locatário que o proprietário do projeto para depuração remota, conforme mostrado na imagem:

  :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview-1.png" alt-text="add envi":::

* Para exibir colaboradores no ambiente atual, selecione Listar Microsoft 365 Teams App (com proprietários do aplicativo Microsoft Azure Active Directory **(Azure AD)** e, em seguida, os colaboradores são listados no canal de saída, conforme mostrado na imagem a seguir:

  :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/list of collaborators.png" alt-text="list":::

* Pressione o projeto para GitHub.

> [!NOTE]
> O colaborador recém-adicionado não recebe nenhuma notificação. Project proprietário precisa notificar o colaborador.

### <a name="as-project-collaborator"></a>Como colaborador do projeto

* Clone o projeto de GitHub.
* Faça logoff na Microsoft 365 conta.
* Faça logoff na conta do Azure, que tem permissão de colaborador para todos os recursos do Azure que estão sendo usados neste projeto.
* Para visualizar seu Teams, implante o projeto no controle remoto.
* Iniciar remoto para ter uma visualização do Teams app.

Para obter mais informações, [consulte build and run your Teams app in remote environment](/microsoftteams/platform/sbs-gs-javascript?tabs=vscode%2Cvsc%2Cviscode%2Cvcode&tutorial-step=3&branch).

> [!NOTE]
> Os colaboradores devem fazer logoff usando a conta adicionada pelo proprietário do projeto, que está sob o mesmo locatário com o proprietário do projeto.

### <a name="limitation"></a>Limitação

Não é possível remover colaboradores diretamente da Teams Toolkit extensão. Execute as seguintes etapas para remover os colaboradores manualmente:

  1. Vá para Teams Portal do Desenvolvedor e selecione seu aplicativo Teams por nome ou ID do aplicativo.
  2. Selecione **Proprietários** no painel esquerdo.
  3. Selecione e remova o colaborador.
  4. Vá para [Azure Active Directory](https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredApps), selecione Registro **de** aplicativo no painel esquerdo e encontre seu aplicativo Microsoft Azure Active Directory (Azure AD).
  5. Selecione **Proprietários** no painel esquerdo Microsoft Azure Active Directory página de gerenciamento de aplicativos (Azure AD).
  6. Selecione e remova o colaborador.

> [!NOTE]
> * O colaborador adicionado ao seu projeto não receberá nenhuma notificação. Project proprietário precisa notificar o colaborador offline.
> * As permissões relacionadas ao Azure devem ser definidas manualmente pelo administrador de assinatura do Azure Microsoft Azure portal. A conta do Azure deve ter função de colaborador para a assinatura para que os desenvolvedores possam trabalhar juntos para provisionar e implantar o projeto TeamsFx.

## <a name="see-also"></a>Confira também

* [Provisionar recursos de nuvem](provision.md)
* [Implantar o aplicativo Teams na nuvem](deploy.md)
* [Gerenciar vários ambientes](TeamsFx-multi-env.md)
