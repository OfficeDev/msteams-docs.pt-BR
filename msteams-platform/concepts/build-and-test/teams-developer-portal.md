---
title: Gerenciar seus aplicativos com o Portal do Desenvolvedor
description: Saiba como configurar, distribuir e gerenciar seus aplicativos usando o Portal do Desenvolvedor para Microsoft Teams.
keywords: iniciando equipes do portal do desenvolvedor
ms.localizationpriority: medium
ms.topic: overview
ms.author: surbhigupta
ms.openlocfilehash: 03fd1f75363f303a33a8349f88e13e3444316fc3
ms.sourcegitcommit: 4abb9ca0b0e9661c7e2e329d9f10bad580e7d8f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64464779"
---
# <a name="manage-your-apps-with-the-developer-portal-for-microsoft-teams"></a>Gerencie seus aplicativos com o Portal do Desenvolvedor do Microsoft Teams

O <a href="https://dev.teams.microsoft.com" target="_blank">Portal do Desenvolvedor para Teams</a> é a principal ferramenta para configurar, distribuir e gerenciar seus Microsoft Teams aplicativos. Com o Portal do Desenvolvedor, você pode colaborar com colegas em seu aplicativo, configurar ambientes de tempo de execução e muito mais.

:::image type="content" source="../../assets/images/tdp/tdp_home_1.png" alt-text="Captura de tela mostrando a home page do Portal do Desenvolvedor para Teams.":::

> [!NOTE]
> Atualmente, o Portal do Desenvolvedor não está disponível para locatários Nuvem da Comunidade Governamental (GCC), GCC-High ou Departamento de Defesa (DOD).

## <a name="register-an-app"></a>Registrar um aplicativo

O Portal do Desenvolvedor fornece algumas maneiras de registrar um Teams aplicativo:

* Registrar um aplicativo novo
* Importar um pacote de aplicativo existente

> [!NOTE]
> Se você criar um aplicativo usando o [Microsoft Teams Toolkit para](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) Visual Studio Code, poderá gerenciar esse aplicativo no Portal do Desenvolvedor.

## <a name="set-up-an-environment"></a>Configurar um ambiente

Você pode configurar ambientes e variáveis globais para ajudar a fazer a transição do aplicativo do tempo de execução local para a produção. As variáveis globais são usadas em todos os ambientes.

Para configurar um ambiente:

1. No Portal do Desenvolvedor, selecione o aplicativo em que você está trabalhando.
2. Vá até a **página Ambientes** e selecione **+ Adicionar um ambiente**.
3. Selecione **+ Adicionar uma variável** para criar variáveis de configuração para seu ambiente.

Para usar variáveis:

Use os nomes de variáveis em vez de valores codificados para definir as configurações do aplicativo.

1. Insira `{{` em qualquer campo no Portal do Desenvolvedor. Um menu suspenso com todas as variáveis que você criou para o ambiente escolhido juntamente com as variáveis globais é exibido.  
1. Antes de baixar o pacote do aplicativo (por exemplo, ao se preparar para publicar no Teams store), selecione o ambiente que você deseja usar. As configurações do aplicativo são atualizadas automaticamente com base no ambiente.

## <a name="identify-app-owners"></a>Identificar proprietários de aplicativos

Cada aplicativo inclui uma página **Proprietários** , onde você pode compartilhar o registro do aplicativo com colegas em sua organização. A **função Colaborador** tem as mesmas permissões que a **função Owner** , exceto a capacidade de excluir um aplicativo.

## <a name="configure-your-apps-capabilities-and-other-important-metadata"></a>Configurar os recursos do aplicativo e outros metadados importantes

Um Teams app é um aplicativo Web. Como todos os aplicativos Web, seu código-fonte normalmente é desenvolvido em um IDE ou editor de código e hospedado em algum lugar na nuvem (como o Azure).

Para instalar e renderizar seu aplicativo Teams, você deve incluir um conjunto de configurações que Teams reconhece. Isso tradicionalmente foi feito por meio da criação de um manifesto de aplicativo, um arquivo JSON que contém todos os metadados que Teams precisa para exibir o conteúdo do aplicativo. O Portal do Desenvolvedor abstrai esse processo e inclui novos recursos e ferramentas para ajudá-lo a ter mais êxito.

## <a name="test-your-app-directly-in-teams"></a>Teste seu aplicativo diretamente no Teams

O Portal do Desenvolvedor oferece opções para testar e depurar seu aplicativo:

* Na página **Visão** geral, você pode ver um instantâneo de se as configurações do seu aplicativo são validadas em Teams casos de teste da loja.
* O **botão Visualizar no Teams** permite iniciar seu aplicativo rapidamente no cliente Teams para depuração.

## <a name="distribute-your-app"></a>Distribuir seu aplicativo

No Portal do Desenvolvedor, use o botão **Distribuir** para baixar um pacote de aplicativos, publicar em sua organização ou publicar no Teams store.

Para obter mais informações, consulte [distribute your Teams app](~/concepts/deploy-and-publish/apps-publish-overview.md).

## <a name="use-tools-to-create-app-features"></a>Usar ferramentas para criar recursos de aplicativo

O Portal do Desenvolvedor também inclui ferramentas para ajudá-lo a criar alguns recursos principais de Teams aplicativos. Algumas dessas ferramentas incluem:

* **Estúdio de cena**: Projetar [cenas personalizadas do modo Juntos](~/apps-in-teams-meetings/teams-together-mode.md) para Teams reuniões.
* **Editor de Cartões Adaptáveis**: Crie e visualize Cartões Adaptáveis para incluir com seus aplicativos.
* **plataforma de identidade da Microsoft**: registre seus aplicativos com Azure Active Directory para ajudar os usuários a entrar e fornecer acesso a APIs.

## <a name="see-also"></a>Confira também

[Incluir uma oferta SaaS com seu aplicativo Microsoft Teams](~/concepts/deploy-and-publish/appsource/prepare/include-saas-offer.md)
