---
title: Colaborar no TeamsFx Project usando o Kit de Ferramentas do Teams
author: yanjiang
description: Neste artigo, saiba como colaborar no TeamsFx Project usando o Kit de Ferramentas do Teams e colaborar com outros desenvolvedores.
ms.author: rentu
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: e9ae53530cc38ebbb02664e080f5420a0b6f4cc6
ms.sourcegitcommit: c7fbb789b9654e9b8238700460b7ae5b2a58f216
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66485472"
---
# <a name="collaborate-on-teams-project-using-teams-toolkit"></a>Colaborar no projeto do Teams usando o Kit de Ferramentas do Teams

Vários desenvolvedores podem trabalhar juntos para depurar, provisionar e implantar para o mesmo projeto TeamsFx, mas isso requer a definição manual das permissões corretas do Aplicativo Teams e do aplicativo Microsoft Azure Active Directory (Azure AD). O Kit de Ferramentas do Teams dá suporte ao recurso de colaboração para permitir que os desenvolvedores e o proprietário do projeto convidem outros desenvolvedores ou colaboradores para o projeto TeamsFx para depurar, provisionar e implantar o mesmo projeto teamsFx.

## <a name="prerequisites"></a>Pré-requisitos

* Assinatura do Microsoft 365.
* Azure com assinatura válida.
  
  Para obter mais informações sobre contas diferentes, consulte [preparar contas para criar o aplicativo Teams](accounts.md).

* [Instalar o Kit de Ferramentas do Teams](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) versão v3.0.0+

> [!TIP]
> Verifique se você tem um projeto de aplicativo do Teams aberto Visual Studio Code.

## <a name="collaborate-with-other-developers"></a>Colaborar com outros desenvolvedores

As listas a seguir nos orientam a entender o processo de colaboração e sua limitação:

* Como proprietário do projeto

  > [!NOTE]
  > Antes de adicionar colaboradores para um ambiente, o proprietário do projeto precisa [provisionar](provision.md) o projeto primeiro.

  1. Na **seção AMBIENTE** do Kit de Ferramentas do Teams, selecione **colaboradores**. Ele exibe as opções Adicionar Proprietários do Aplicativo **Microsoft 365 Teams (com o aplicativo Azure AD)** e listar proprietários do aplicativo **Microsoft 365 Teams (com o aplicativo Azure AD),** conforme mostrado nas seguintes imagens:

     :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/add collaborators.png" alt-text="Colaboradores":::

  2. Selecione **Adicionar Proprietários do Aplicativo Microsoft 365 Teams (com Azure AD App)** e adicione outro endereço de email da conta do Microsoft 365 como colaborador. A conta a ser adicionada deve estar no mesmo locatário que o proprietário do projeto para depuração remota, conforme mostrado na imagem:

     :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview-1.png" alt-text="add envi":::

  3. Para exibir colaboradores no ambiente atual, selecione Listar Proprietários do Aplicativo **Microsoft 365 Teams (com o aplicativo Azure AD),** em seguida, os colaboradores são listados no canal de saída, conforme mostrado na imagem a seguir:

     :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/list of collaborators.png" alt-text="list":::

  4. Enviar por push o projeto para o GitHub

     > [!NOTE]
     > Os colaboradores recém-adicionados não recebem nenhuma notificação. O proprietário do projeto precisa notificar o colaborador.

* Como colaborador do projeto

  1. Clone o projeto do GitHub.
  2. Faça logon na conta do Microsoft 365.
  3. Faça logon na conta do Azure, ela tem permissão de colaborador para todos os recursos do Azure, que são usados no projeto.
  4. Para visualizar o aplicativo Teams, implante o projeto no modo remoto.
  5. Inicie remotamente para ter uma visualização do aplicativo Teams.

     > [!NOTE]
     > Os colaboradores devem fazer logon usando a conta que o proprietário do projeto adiciona no mesmo locatário com o proprietário do projeto. Para obter mais informações, consulte [compilar e executar seu aplicativo Teams em um ambiente remoto](/microsoftteams/platform/sbs-gs-javascript?tabs=vscode%2Cvsc%2Cviscode%2Cvcode&tutorial-step=3&branch).

### <a name="limitations"></a>Limitações

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
   > * As permissões relacionadas ao Azure devem ser definidas manualmente pelo administrador da assinatura do Azure portal do Azure. A conta do Azure deve ter função de colaborador para a assinatura para que os desenvolvedores possam trabalhar juntos para provisionar e implantar o projeto TeamsFx.

## <a name="see-also"></a>Confira também

* [Provisionar recursos de nuvem](provision.md)
* [Implantar o aplicativo Teams na nuvem](deploy.md)
* [Gerenciar vários ambientes](TeamsFx-multi-env.md)
