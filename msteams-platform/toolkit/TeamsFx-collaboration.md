---
title: Colaborar no TeamsFx Project usando o Kit de Ferramentas do Teams
author: surbhigupta
description: Neste artigo, saiba como colaborar no TeamsFx Project usando o Kit de Ferramentas do Teams e colaborar com outros desenvolvedores.
ms.author: v-amprasad
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 90ccd073e45649f715751e81835747bfb95d7806
ms.sourcegitcommit: ed7488415f814d0f60faa15ee8ec3d64ee336380
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2022
ms.locfileid: "67616833"
---
# <a name="collaborate-on-teams-project-using-microsoft-teams-toolkit"></a>Colaborar no projeto do Teams usando o Kit de Ferramentas do Microsoft Teams

Vários desenvolvedores podem trabalhar juntos para depurar, provisionar e implantar para o mesmo projeto do TeamsFx, mas isso requer a definição manual das permissões corretas do Teams App e Microsoft Azure Active Directory (Azure AD). O Kit de Ferramentas do Teams dá suporte ao recurso de colaboração para permitir que os desenvolvedores e o proprietário do projeto convidem outros desenvolvedores ou colaboradores para o projeto TeamsFx para depurar, provisionar e implantar o mesmo projeto teamsFx.

## <a name="collaborate-with-other-developers"></a>Colaborar com outros desenvolvedores

As seções a seguir nos orientam a entender o processo de colaboração como proprietário ou colaborador do projeto:

### <a name="as-project-owner"></a>Como proprietário do projeto

  > [!NOTE]
  > Antes de adicionar colaboradores para um ambiente, o proprietário do projeto precisa [provisionar](provision.md) o projeto primeiro.

  1. Selecione **o Kit de Ferramentas do Teams** na barra de atividades.
  
     :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-teams-toolkit.png" alt-text="Selecionar o kit de ferramentas do Teams na barra de atividades":::

  1. Na  seção AMBIENTE, selecione colaboradores, que são exibidos como opção **1** Adicionar Proprietários do Aplicativo **Microsoft 365 Teams (com aplicativo Azure AD)** e **2** Listar Proprietários do Aplicativo **Microsoft 365 Teams (com o aplicativo Azure AD),** conforme mostrado na imagem a seguir:

     :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/add collaborators.png" alt-text="Colaboradores":::

  2. Selecione **Adicionar Proprietários do Aplicativo Microsoft 365 Teams (com Azure AD App)** e adicione outro endereço de email da conta do Microsoft 365 como colaborador. A conta a ser adicionada deve estar no mesmo locatário que o proprietário do projeto para depuração remota, conforme mostrado na imagem:

     :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/add-owner.png" alt-text="Adicionar proprietário do projeto":::

  3. Para exibir colaboradores no ambiente atual, selecione Listar Proprietários do Aplicativo **Microsoft 365 Teams (com o aplicativo Azure AD)** e, em seguida, você poderá ver os colaboradores listados no canal de saída, conforme mostrado na imagem a seguir:

     :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/list of collaborators.png" alt-text="list":::

  4. Envie o projeto por push para o GitHub.

     > [!NOTE]
     > Os colaboradores recém-adicionados não recebem nenhuma notificação. O proprietário do projeto precisa notificar o colaborador.

### <a name="as-project-collaborator"></a>Como colaborador do projeto

  1. Clone o projeto do GitHub.
  2. Faça logon na conta do Microsoft 365.
  3. Faça logon na conta do Azure, ela tem permissão de colaborador para todos os recursos do Azure, que são usados no projeto.
  4. Para visualizar o aplicativo Teams, implante o projeto no modo remoto.
  5. Inicie remotamente para ter uma visualização do aplicativo Teams.

     > [!NOTE]
     > Os colaboradores devem fazer logon usando a conta que o proprietário do projeto adiciona no mesmo locatário com o proprietário do projeto. Para obter mais informações, consulte [compilar e executar seu aplicativo Teams em um ambiente remoto](/microsoftteams/platform/sbs-gs-javascript?tabs=vscode%2Cvsc%2Cviscode%2Cvcode&tutorial-step=3&branch).

## <a name="remove-collaborators"></a>Remover Colaboradores

Se você quiser remover colaboradores da extensão do Kit de Ferramentas do Teams, será necessário removê-los manualmente, pois não é possível removê-los diretamente. Execute as seguintes etapas para remover os colaboradores manualmente:

* Usando o Portal do Desenvolvedor

  * Acesse o [Portal do Desenvolvedor do Teams](https://dev.teams.microsoft.com/home) e selecione seu aplicativo do Teams por nome ou ID do aplicativo.
  * Selecione **Proprietários** no painel esquerdo.
  * Selecione e remova o colaborador.

* Usando o Azure Active Directory

  * Vá para [o Azure Active Directory](https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredApps), selecione **Registro de** aplicativo no painel esquerdo e localize seu Azure AD Aplicativo.
  * Selecione **Proprietários** no painel esquerdo na Azure AD gerenciamento de aplicativos.
  * Selecione e remova o colaborador.

    > [!NOTE]
    >
    > * O colaborador adicionado ao seu projeto não recebe nenhuma notificação. O proprietário do projeto precisa notificar o colaborador offline.
    > * As permissões relacionadas ao Azure devem ser definidas manualmente pelo administrador da assinatura do Azure portal do Azure.
    > * A conta do Azure deve ter função de colaborador para a assinatura para que os desenvolvedores possam trabalhar juntos para provisionar e implantar o projeto TeamsFx.

## <a name="see-also"></a>Confira também

* [Provisionar recursos de nuvem](provision.md)
* [Implantar o aplicativo Teams na nuvem](deploy.md)
* [Gerenciar vários ambientes](TeamsFx-multi-env.md)
