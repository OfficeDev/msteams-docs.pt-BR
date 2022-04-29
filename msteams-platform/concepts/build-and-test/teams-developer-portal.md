---
title: Gerencie seus aplicativos com o Portal do Desenvolvedor
description: Saiba como configurar, distribuir e gerenciar seus aplicativos usando o Portal do Desenvolvedor para o Microsoft Teams.
keywords: introdução às equipes do portal do desenvolvedor
ms.localizationpriority: high
ms.topic: overview
ms.author: surbhigupta
ms.openlocfilehash: f55ecd7e44760a353a6058e004ea3cf6cdb769b2
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111791"
---
# <a name="manage-your-apps-with-the-developer-portal-for-microsoft-teams"></a>Gerencie seus aplicativos com o Portal do Desenvolvedor do Microsoft Teams

O <a href="https://dev.teams.microsoft.com" target="_blank">Portal do Desenvolvedor para Teams</a> é a principal ferramenta para configurar, distribuir e gerenciar seus aplicativos do Microsoft Teams. Com o Portal do Desenvolvedor, você pode colaborar com colegas em seu aplicativo, configurar ambientes de runtime e muito mais.

:::image type="content" source="../../assets/images/tdp/tdp_home_1.png" alt-text="Captura de tela mostrando a página inicial do Portal do Desenvolvedor para Teams.":::

> [!NOTE]
>
> * Atualmente, Portal do Desenvolvedor está disponível para locatários Nuvem da Comunidade Governamental (GCC), GCC-High ou DOD (Departamento de Defesa).
> * No entanto, você pode usar um locatário regular para criar um aplicativo no Portal do Desenvolvedor, baixar o aplicativo e carregar o aplicativo usando [Microsoft Graph](/graph/api/teamsapp-publish?view=graph-rest-1.0&tabs=http&preserve-view=true) para uma nuvem nacional. Para obter mais informações, consulte [Implantações de nuvem nacional](/graph/deployments).

## <a name="register-an-app"></a>Registrar um aplicativo

A Portal do Desenvolvedor fornece algumas maneiras de registrar um aplicativo do Teams:

* Registrar um novo aplicativo
* Importar um pacote de aplicativo existente

> [!NOTE]
> Se você criar um aplicativo usando o [Kit de ferramentas do Teams para Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension), poderá gerenciar esse aplicativo no Portal do Desenvolvedor.

## <a name="set-up-an-environment"></a>Configurar um ambiente

Você pode configurar ambientes e variáveis globais para ajudar a fazer a transição do aplicativo do runtime local para a produção. As variáveis globais são usadas em todos os ambientes.

Para configurar um ambiente:

1. Na Portal do Desenvolvedor, selecione o aplicativo no qual você está trabalhando.
2. Vá para a página **Ambientes** e selecione **+ Adicionar um ambiente**.
3. Selecione **+ Adicionar uma variável** para criar variáveis de configuração para seu ambiente.

Para usar variáveis:

Use os nomes de variáveis em vez de valores embutidos em código para definir as configurações do aplicativo.

1. Insira `{{` em qualquer campo no Portal do Desenvolvedor. Uma lista suspensa com todas as variáveis que você criou para o ambiente escolhido juntamente com as variáveis globais é exibida.  
1. Antes de baixar o pacote do aplicativo (por exemplo, ao se preparar para publicar na loja do Teams), selecione o ambiente que você deseja usar. As configurações do aplicativo são atualizadas automaticamente com base no ambiente.

## <a name="identify-app-owners"></a>Identificar proprietários de aplicativos

Cada aplicativo inclui uma página de **Proprietários**, onde você pode compartilhar o registro do aplicativo com colegas em sua organização. A função **Colaborador** tem as mesmas permissões que a função **Proprietário**, exceto a capacidade de excluir um aplicativo.

## <a name="configure-your-apps-capabilities-and-other-important-metadata"></a>Configurar os recursos do aplicativo e outros metadados importantes

Um aplicativo teams é um aplicativo Web. Como todos os aplicativos Web, seu código-fonte normalmente é desenvolvido em um IDE ou editor de código e hospedado em algum lugar na nuvem (como o Azure).

Para instalar e renderizar seu aplicativo no Teams, você deve incluir um conjunto de configurações que o Teams reconhece. Tradicionalmente, isso é feito criando um manifesto do aplicativo, um arquivo JSON que contém todos os metadados que o Teams precisa para exibir o conteúdo do aplicativo. A Portal do Desenvolvedor abstrai esse processo e inclui novos recursos e ferramentas para ajudá-lo a ter mais sucesso.

## <a name="test-your-app-directly-in-teams"></a>Testar seu aplicativo diretamente no Teams

O Portal do Desenvolvedor fornece opções para testar e depurar seu aplicativo:

* Na página **Visão geral**, você pode ver um instantâneo de se as configurações do aplicativo são validadas em casos de teste da loja do Teams.
* O botão **Visualização no Teams** permite que você inicie seu aplicativo rapidamente no cliente do Teams para depuração.

## <a name="distribute-your-app"></a>Distribuir seu aplicativo

No Portal do Desenvolvedor, use o botão **Distribuir** para baixar um pacote do aplicativo, publicar em sua organização ou publicar na loja do Teams.

Para obter mais informações, consulte [distribuir seu aplicativo Teams](~/concepts/deploy-and-publish/apps-publish-overview.md).

## <a name="use-tools-to-create-app-features"></a>Usar ferramentas para criar recursos de aplicativo

O Portal do Desenvolvedor também inclui ferramentas para ajudá-lo a criar alguns dos principais recursos dos aplicativos do Teams. Algumas dessas ferramentas incluem:

* **Estúdio de cena**: crie [cenas personalizadas do Modo Juntos](~/apps-in-teams-meetings/teams-together-mode.md) para reuniões do Teams.
* **Editor de Cartões Adaptáveis**: crie e visualize Cartões Adaptáveis para incluir com seus aplicativos.
* **Gerenciamento da plataforma de identidade da Microsoft**: registre seus aplicativos com o Azure Active Directory para ajudar os usuários a entrar e fornecer acesso às APIs.

## <a name="see-also"></a>Confira também

[Incluir uma oferta SaaS com seu aplicativo Microsoft Teams](~/concepts/deploy-and-publish/appsource/prepare/include-saas-offer.md)
