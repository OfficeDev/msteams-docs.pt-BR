---
title: Gerenciar seus aplicativos com o Portal do Desenvolvedor
description: Saiba como gerenciar seus aplicativos usando o Portal do Desenvolvedor para Microsoft Teams.
keywords: iniciando equipes do portal do desenvolvedor
ms.localizationpriority: medium
ms.topic: overview
ms.author: surbhigupta
ms.openlocfilehash: 84f3e5724adf3256fff3086158345fc3777513bb
ms.sourcegitcommit: 6573881f7e69d8e5ec8861f54df84e7d519f0511
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2021
ms.locfileid: "60096568"
---
# <a name="manage-your-apps-with-the-developer-portal-for-microsoft-teams"></a>Gerenciar seus aplicativos com o Portal do Desenvolvedor para Microsoft Teams

O <a href="https://dev.teams.microsoft.com" target="_blank">Portal do Desenvolvedor para Teams</a> é a principal ferramenta para configurar, distribuir e gerenciar seus Microsoft Teams aplicativos. Com o Portal do Desenvolvedor, você pode colaborar com colegas em seu aplicativo, configurar ambientes de tempo de execução e muito mais.

:::image type="content" source="../../assets/images/tdp/tdp_home_1.png" alt-text="Captura de tela mostrando a home page do Portal do Desenvolvedor para Teams.":::

## <a name="register-an-app"></a>Registrar um aplicativo

Você pode registrar seu aplicativo Teams no Portal do Desenvolvedor com as seguintes maneiras:

* Registrar um novo aplicativo
* Importar um pacote de aplicativo existente

> [!NOTE]
> Se você criar um aplicativo usando o [Microsoft Teams Toolkit para](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension)Visual Studio Code , poderá gerenciar esse aplicativo no Portal do Desenvolvedor.

## <a name="set-up-an-environment"></a>Configurar um ambiente

Você pode configurar ambientes e variáveis globais para ajudar na transição do aplicativo do tempo de execução local para a produção. As variáveis globais são usadas em todos os ambientes.

**Para configurar um ambiente**

1. No Portal do Desenvolvedor, selecione o aplicativo em que você está trabalhando.
2. Vá para **Ambientes e** selecione **+ Adicionar um ambiente**.
3. Selecione **+ Adicionar uma variável** para criar variáveis de configuração para seu ambiente.

**Para usar variáveis**

Use os nomes de variáveis em vez de valores codificados para definir as configurações do aplicativo.

1. Insira `{{` em qualquer campo no Portal do Desenvolvedor. Um menu suspenso com todas as variáveis que você criou para o ambiente escolhido juntamente com as variáveis globais é exibido.  
1. Antes de baixar o pacote do aplicativo (por exemplo, ao se preparar para publicar no Teams store), selecione o ambiente que você deseja usar. As configurações do aplicativo são atualizadas automaticamente com base no ambiente. 

## <a name="identify-app-owners"></a>Identificar proprietários de aplicativos

Cada aplicativo inclui **Proprietários**, onde você pode compartilhar seu registro de aplicativo com colegas em sua organização. A **função Colaborador** tem as mesmas permissões que a função **Owner,** exceto a capacidade de excluir um aplicativo.

## <a name="configure-your-apps-capabilities-and-other-important-metadata"></a>Configurar os recursos do aplicativo e outros metadados importantes

Um Teams app é um aplicativo Web. Como todos os aplicativos Web, seu código-fonte normalmente é desenvolvido em um IDE ou editor de código e hospedado em algum lugar na nuvem (como o Azure).

Para instalar e renderizar seu aplicativo Teams, você deve incluir um conjunto de configurações que Teams reconhece. Isso tradicionalmente foi feito com a criação de um manifesto de aplicativo, um arquivo JSON que contém todos os metadados que Teams precisa para exibir o conteúdo do aplicativo. O Portal do Desenvolvedor abstrai esse processo e inclui novos recursos e ferramentas para ajudá-lo a ter mais êxito.

### <a name="basic-app-configuration"></a>Configuração básica do aplicativo 

**Informações básicas do aplicativo:** Os usuários veem na página de detalhes do aplicativo no Teams, como ID do aplicativo, nomes de aplicativos, descrições, informações do desenvolvedor, versão, URLs de aplicativo e ID da Rede do Microsoft Partner.

**Identidade visual:** Os aplicativos exigem ícone de cor e de contorno no formato PNG. Para publicar seu aplicativo no Teams, os ícones devem atender aos requisitos de tamanho específicos.

**Recursos: Teams** recursos que você pode incluir em seu aplicativo. Você pode adicionar um ou mais recursos, dependendo dos casos de uso do aplicativo.

**Permissões:** Especifique o que os usuários devem consentir ao usar seu aplicativo.

**Login único:** Configure seu aplicativo para autenticar usuários com SSO (login único).

**Domínios:** Listar todos os domínios que seu aplicativo precisa navegar. Use caracteres curinga para incluir vários subdomas. Por exemplo, `*.example.com`.

### <a name="advanced-app-configuration"></a>Configuração avançada do aplicativo

**Conteúdo do aplicativo:** Configure os recursos opcionais, como, indicador de carregamento e modo de tela inteira para seu aplicativo.

**Personalização do aplicativo:** Selecione as propriedades que Teams administradores podem personalizar sobre seu aplicativo.

**Configurações de primeira parte:** Recursos para aplicativos de primeira parte que vão além da funcionalidade pública.

### <a name="distribute-your-app"></a>Distribuir seu aplicativo

**Pacote do aplicativo:** O pacote app descreve a configuração do aplicativo, os recursos, os recursos necessários e outros atributos importantes. Por exemplo, o esquema de manifesto.

**Voos:** Controle quem recebe atualizações de aplicativos. Por exemplo, você pode liberar uma atualização para os funcionários da Microsoft para identificar e corrigir bugs antes de liberá-lo para o público.

**Publicar na sua organização (Microsoft):** Disponibilizar seu aplicativo para pessoas em sua organização. Depois de aprovado pelo administrador de IT, seu aplicativo será apresentado no Teams em Aplicativos > Criado para sua organização.

**Publicar no Teams store:** A ferramenta de validação de aplicativo verifica seu pacote de aplicativo em relação aos casos de teste que a Microsoft usa ao analisar seu aplicativo. Resolva erros ou avisos e leia a lista de verificação antes de enviar.

## <a name="test-your-app-directly-in-teams"></a>Teste seu aplicativo diretamente no Teams

O Portal do Desenvolvedor oferece opções para testar e depurar seu aplicativo:

* Em **Visão** geral, você pode ver um instantâneo de se as configurações do seu aplicativo são validadas em Teams casos de teste da loja.
* **A visualização Teams** permite iniciar seu aplicativo rapidamente no cliente Teams para depuração.

## <a name="distribute-your-app"></a>Distribuir seu aplicativo

No Portal do Desenvolvedor, use **Distribuir** para baixar um pacote de aplicativos, publicar em sua organização ou publicar no Teams store.

Para obter mais informações, [consulte distribute your Teams app](~/concepts/deploy-and-publish/apps-publish-overview.md).

## <a name="analyze-your-apps-usage"></a>Analisar o uso do seu aplicativo

Em **Visão** geral, você pode ver o número total de usuários ativos para seu aplicativo. Essas métricas estão disponíveis para aplicativos publicados na Teams ou no catálogo de aplicativos de uma organização por meio do Portal do Desenvolvedor e com escopo para a ID do aplicativo.

| Indicador | Definição |
| :-----------------------| :------------------------------------------------------------------------------------------------------|
| *R30 mensal* | A métrica de uso padrão. Ele mostra a contagem de usuários ativos exclusivos, que usaram seu aplicativo nessa janela de 30 dias de rolagem em UTC. |
| *Diariamente* | Mostra a contagem de usuários ativos exclusivos, que usaram seu aplicativo em um determinado dia em UTC. |

O uso mensal e diário é mostrado nos últimos sete dias, 30 e 60 dias. Você deve ver o uso refletido para um determinado dia dentro de 24 a 48 horas. O uso de novos aplicativos pode levar de 3 a 5 dias para ser exibido.

## <a name="use-tools-to-create-app-features"></a>Usar ferramentas para criar recursos de aplicativo

O Portal do Desenvolvedor também inclui ferramentas para ajudá-lo a criar alguns recursos principais de Teams aplicativos. Algumas dessas ferramentas incluem:

* **Estúdio de cena**: Projetar [cenas personalizadas do](~/apps-in-teams-meetings/teams-together-mode.md) modo Juntos para Teams reuniões.
* **Editor de Cartões Adaptáveis**: Crie e visualize Cartões Adaptáveis para incluir com seus aplicativos.
* **plataforma de identidade da Microsoft gerenciamento**: registre seus aplicativos com o Azure Active Directory (Azure AD) para ajudar os usuários a entrar e fornecer acesso a APIs.
