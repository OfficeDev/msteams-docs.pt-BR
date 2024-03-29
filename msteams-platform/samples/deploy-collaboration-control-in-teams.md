---
title: Implantar um aplicativo com controles de colaboração no Microsoft Teams
author: surbhigupta
description: Neste módulo, saiba como implantar seu aplicativo com o controle colaboração no Microsoft Teams e como permitir que outras pessoas usem seu aplicativo.
ms.localizationpriority: medium
ms.author: v-npaladugu
ms.topic: conceptual
ms.openlocfilehash: 816dd8052cdfb13ab83bfc34ae2a99a16f9f9569
ms.sourcegitcommit: f2ac771cbd608e872604e9ac8ffec2d08f55ee1a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68373035"
---
# <a name="deploy-collaboration-controls-to-microsoft-teams"></a>Implantar controles de colaboração no Microsoft Teams

Atualmente, os controles de colaboração funcionam melhor no Microsoft Teams. Você pode criar um novo aplicativo que pode ser inserido dentro do aplicativo Teams como um aplicativo pessoal e um aplicativo guia.

> [!NOTE]
> Atualmente, os controles de colaboração estão disponíveis apenas na versão [prévia do desenvolvedor público](~/resources/dev-preview/developer-preview-intro.md).

## <a name="configure-the-app-for-teams"></a>Configurar o aplicativo para o Teams

O aplicativo que você criou [na criação de](~/samples/app-with-collaboration-controls.md#create-a-model-driven-application) um aplicativo controlado por modelo tem apenas um único painel esquerdo e não há comandos complexos. Portanto, antes de adicionar seu aplicativo ao Teams, você pode ocultar o painel esquerdo e tornar a exibição de cabeçalho mais compreensível.

> [!NOTE]
> Não habilite as etapas a seguir se quiser exibir o painel esquerdo e o cabeçalho de alta densidade para seus usuários.

Para fazer isso, usaremos as novas configurações **de aplicativo** do Power Apps.

1. Vá para **Soluções** no painel esquerdo.

1. Vá para a parte inferior da lista de soluções e selecione **a solução padrão**.

1. Pesquise e selecione **Definição de configuração**.

     :::image type="content" source="../assets/images/collaboration-control/settings-defnition.png" alt-text="A captura de tela mostra a pesquisa e a definição de definição no Power Apps.":::

1. Pesquise e **selecione Ocultar a barra de** navegação na lista de definições de configurações. Isso oculta o painel esquerdo em seu aplicativo.

     :::image type="content" source="../assets/images/collaboration-control/hide-the-nav-bar.png" alt-text="A captura de tela mostra como selecionar ocultar a barra de navegação.":::

1. No canto inferior direito do aplicativo no painel de edição, há uma seção intitulitada **Configurando valores de aplicativo**. Se você criou seu aplicativo usando o designer de aplicativo moderno, seu aplicativo aparecerá na lista. Selecione **Novo valor de aplicativo** em seu aplicativo.

1. Altere o valor de **Não** para **Sim.**

     :::image type="content" source="../assets/images/collaboration-control/value-to-yes.png" alt-text="A captura de tela exibe a lista suspensa para selecionar o valor de alteração como sim.":::

1. Selecione **Salvar.**

1. Pesquise e **selecione o cabeçalho da página de alta** densidade do aplicativo na lista de definições de configurações e repita o processo.

     :::image type="content" source="../assets/images/collaboration-control/density-page-header.png" alt-text="A captura de tela mostra como selecionar o cabeçalho da página de alta densidade do aplicativo.":::

1. Selecione **Voltar para soluções**.

     :::image type="content" source="../assets/images/collaboration-control/default-solution.png" alt-text="A captura de tela mostra a solução padrão.":::

1. Selecione **Publicar todas as personalizações** para publicar todo o trabalho que você concluiu.

     :::image type="content" source="../assets/images/collaboration-control/publish-cusomization.png" alt-text="Publique todas as personalizações.":::

## <a name="add-the-app-to-microsoft-teams-app-catalog"></a>Adicionar o aplicativo ao catálogo de aplicativos do Microsoft Teams

Conforme as configurações são definidas, agora você pode adicionar o aplicativo ao Microsoft Teams. Para começar, navegue até a  página Aplicativos no portal do Criador do Power Apps e localize o aplicativo que você criou e selecione elipse **...**.

Para adicionar o aplicativo ao Teams, selecione **Adicionar ao Teams**.

:::image type="content" source="../assets/images/collaboration-control/add-to-teams.png" alt-text="Adicionar ao Teams.":::

Selecionar **Adicionar ao Teams** abre uma caixa de diálogo em que você pode examinar os detalhes e selecionar Baixar **aplicativo, que** salva o manifesto do aplicativo Microsoft Teams em seu dispositivo.

:::image type="content" source="../assets/images/collaboration-control/colab-manager-inspection.png" alt-text="A captura de tela é um exemplo que mostra a inspeção do gerenciador de colaboração.":::

Para carregar seu aplicativo no Teams, consulte [carregar seu aplicativo no Team](~/concepts/deploy-and-publish/apps-upload.md).

## <a name="enable-others-to-use-your-application"></a>Permitir que outras pessoas usem seu aplicativo

A seguir são necessários para permitir que os usuários executem os aplicativos Collaboration Manager implantados usando os controles de colaboração:

* Criar uma equipe de colaboração
* Adicionar membros à equipe
* Criar uma função de segurança
* Atribuir funções de segurança aos membros da equipe

### <a name="create-a-collaboration-team"></a>Criar uma equipe de colaboração

1. Entre no [centro de administração do Power Platform](https://admin.powerplatform.microsoft.com/environments).

     1. Selecione o ambiente em que o aplicativo está implantado.
     1. Selecione **Permissões de Usuários** > **de** + **Configurações**.
     1. Selecione **Teams**.

1. Selecione o **botão + Criar** equipe na parte superior da página.

1. Adicione todos os campos obrigatórios:
     1. **Nome da equipe:** Verifique se o nome é exclusivo dentro da unidade de negócios.
     1. **Descrição:** Insira uma descrição da equipe.
     1. **Unidade de negócios:** Selecione uma unidade de negócios na lista suspensa.
     1. **Administrador:** Pesquise o usuário em sua organização que você deseja atribuir como administrador inserindo caracteres.
     1. **Tipo de equipe:** Selecione o tipo de equipe. As etapas a seguir pressupõem que você selecionou Proprietário na lista suspensa. Os outros tipos de equipe (equipe do Microsoft 365 e Microsoft Azure Active Directory equipe) preenchem automaticamente os membros da equipe do Azure Active Directory.

         :::image type="content" source="../assets/images/collaboration-control/new-team.png" alt-text="Captura de tela para selecionar o novo tipo de equipe.":::

     1. Certifique-se de anotar o nome da equipe. Você precisará disso mais tarde para atribuir essa equipe como o proprietário de um registro.

     1. Selecione **Avançar.**

### <a name="add-members-to-the-team"></a>Adicionar membros à equipe

> [!NOTE]
> Não será necessário adicionar membros à equipe se o tipo de equipe for o Azure Active Directory ou o Microsoft 365.

1. Selecione uma equipe e, em seguida, **selecione Gerenciar membros da equipe**.

1. Para adicionar novos membros da equipe, selecione **+ Adicionar membros da equipe** e escolha os usuários de sua organização para adicionar.

     :::image type="content" source="../assets/images/collaboration-control/add-team-members.png" alt-text="A captura de tela descreve como adicionar membros da equipe.":::

1. Para excluir um membro da equipe, selecione o usuário e escolha **Remover**.

### <a name="create-a-security-role"></a>Criar uma função de segurança

1. Selecione **Permissões de** > **Usuários de** + **Configurações** no ambiente em que o aplicativo está implantado.

1. Selecione **Funções de segurança**.

     :::image type="content" source="../assets/images/collaboration-control/users-permission.png" alt-text="Captura de tela exibida para adicionar novos membros da equipe à permissão de usuários.":::

1. Selecione em **Nova função** no canto superior esquerdo da página, que agora abre uma nova página.

1. Na guia **Detalhes**, forneça um nome para sua função de segurança.

1. Vá para **a guia Entidades Personalizadas** .

     1. Conce permissões de organização (círculo verde completo) para cada uma das entidades de **colaboração, Mapa** de **Colaboração,** Metadados de Colaboração e Raiz **de Colaboração**.

         :::image type="content" source="../assets/images/collaboration-control/collab-map.png" alt-text="Captura de tela que mostra como criar uma função de segurança no mapa de colaboração.":::

1. Selecione **Salvar** e **Fechar**.

### <a name="assign-security-roles"></a>Atribuir funções de segurança

1. Selecione **Permissões de** > **Usuários de** + **Configurações** no ambiente em que o aplicativo está implantado.

1. Selecione **o Teams**, selecione a equipe que você criou na [criação de uma equipe de Colaboração](#create-a-collaboration-team).

1. Escolha **Gerenciar funções de segurança** no cabeçalho.

     :::image type="content" source="../assets/images/collaboration-control/edit-team.png" alt-text="Captura de tela que exibe o mapa de colaboração, os metadados de colaboração e a raiz da colaboração. para editar equipe.":::

1. Selecione as funções [criadas em uma função de segurança](#create-a-security-role).

1. Selecione **Salvar**.

Para obter mais informações sobre privilégios de função, consulte [configurar a segurança do usuário em um ambiente](/power-platform/admin/database-security).
