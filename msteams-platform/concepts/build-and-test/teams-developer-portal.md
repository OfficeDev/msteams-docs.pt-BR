---
title: Gerencie seus aplicativos com o Portal do Desenvolvedor
description: Saiba como configurar, distribuir e gerenciar seus aplicativos usando o Portal do Desenvolvedor para o Microsoft Teams.
keywords: introdução às equipes do portal do desenvolvedor
ms.localizationpriority: medium
ms.topic: overview
ms.author: surbhigupta
ms.openlocfilehash: c7ca898cd411028dffa6c8a197c78cd796f823e5
ms.sourcegitcommit: a3567e3e1a52b8e3cb2072b037f0e75bd0f12e58
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2022
ms.locfileid: "65439304"
---
# <a name="manage-your-teams-apps-using-developer-portal"></a>Gerenciar seus aplicativos Teams usando o Portal do Desenvolvedor

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

## <a name="analyze-your-apps-usage"></a>Analisar o uso do aplicativo

No Portal do Desenvolvedor para Teams, na página Visão geral,  você pode ver o número total de usuários ativos para seu aplicativo.

> [!NOTE]
> Atualmente, a análise de uso está disponível apenas para novos aplicativos personalizados publicados em sua organização por meio do **Portal** do Desenvolvedor para Teams (antigo App Studio) ou importados para o **Portal** do Desenvolvedor para Teams após abril de 2022. A análise de uso de todos os aplicativos publicados na Teams está disponível no **Partner Center** para obter mais informações sobre Teams [de uso de aplicativos](/office/dev/store/teams-apps-usage).

| Indicador | Definição |
| :-----------------------| :------------------------------------------------------------------------------------------------------|
| *R30 mensal* | A métrica de uso padrão. Ele mostra a contagem de usuários ativos exclusivos que usaram seu aplicativo dentro dessa janela de 30 dias sem interrupção em UTC. |
| *Diariamente* | Ele mostra a contagem de usuários ativos exclusivos que usaram seu aplicativo em um determinado dia em UTC. |

O uso do aplicativo para um determinado dia é refletido dentro de 24 a 48 horas, e os dados de uso para novos aplicativos podem levar de três a cinco dias para refletir nos gráficos.

Você pode exibir o uso do aplicativo e outros insights na **página** Análise. Para acessar a página:

1. Acesse o **[Portal do Desenvolvedor para Teams](https://dev.teams.microsoft.com)**.
1. Selecione **Aplicativos** no painel esquerdo.
1. Selecione o aplicativo necessário na página **Aplicativos** .
1. Selecione **Análise** na Visão **Geral** ou selecione **Exibir detalhes** no **cartão Usuários Ativos (Versão** Prévia).

 :::image type="content" source="../../assets/images/tdp/dev-app-portal.PNG" alt-text="dev-Portal-analytics"lightbox="../../assets/images/tdp/dev-app-portal.PNG":::

Ao explorar métricas individuais nesta página, você pode usar o botão  Filtro para analisar o uso do aplicativo nas seguintes opções de filtro:

* Tipo de agregação: esse filtro permite agrupar as seguintes métricas por uma contagem de usuários distintos ou uma contagem de locatários ou clientes distintos.
* Plataforma
* Sistema operacional
* Área

 :::image type="content" source="../../assets/images/tdp/dev-analytics-filter.PNG" alt-text="Filter":::

Depois de selecionar os filtros desejados, você pode explorar os seguintes widgets individuais:

* [Uso por período de tempo](#usage-by-time-period)
* [Uso por plataforma e sistema operacional](#usage-by-platform-and-os)
* [Uso por estado de retenção](#usage-by-retention-state)
* [Intensidade de uso](#usage-intensity)

### <a name="usage-by-time-period"></a>Uso por período de tempo

O **gráfico Uso por período de** tempo mostra o número de usuários ativos ou locatários que abriram e usaram seu aplicativo em diferentes períodos de tempo.

 :::image type="content" source="../../assets/images/tdp/usage-by-time-period.png" alt-text="Ponto":::

| Indicador | Definição |
| :-----------------------| :------------------------------------------------------------------------------------------------------|
| R30 mensal | Cada ponto de dados representa um determinado período de R30 (30 dias sem interrupção). |
| R28 mensal | Cada ponto de dados representa um determinado período de R28 (28 dias sem interrupção). |
| R7 semanal| Cada ponto de dados representa um determinado período de R7 (7 dias sem interrupção). |
| Diariamente | Cada ponto de dados representa um determinado período de R1 (1 dia sem interrupção). |

### <a name="usage-by-platform-and-os"></a>Uso por plataforma e sistema operacional

O **gráfico** uso por plataforma e sistema operacional mostra o uso ativo do aplicativo em vários pontos de extremidade, como **Windows**, **Mac**, **iOS**, **Android** e **Web**. O mesmo usuário ou locatário pode usar um aplicativo em vários pontos de extremidade. Cada ponto de dados representa um determinado período de R30 (30 dias sem interrupção).

 :::image type="content" source="../../assets/images/tdp/usage-by-platform-OS.png" alt-text="Plataforma":::

### <a name="usage-by-retention-state"></a>Uso por estado de retenção

O **gráfico uso por estado de retenção** permite controlar quatro métricas de retenção ou variação de chave para seu aplicativo ao longo do tempo.

:::image type="content" source="../../assets/images/tdp/usage-by-retention-state.png" alt-text="Retenção":::

| Indicador | Definição |
| :-----------------------| :------------------------------------------------------------------------------------------------------|
| Novos usuários ou locatários | Usuários ativos ou locatários que são novos e não usaram seu aplicativo. |
| Retornando usuários ou locatários | Usuários ativos ou locatários que usaram seu aplicativo durante um determinado período de tempo R30 (sem interrupção de 30 dias) e o período de tempo imediatamente anterior ao R30. |
| Usuários ou locatários ressuscitados | Usuários ativos ou locatários que usaram seu aplicativo uma ou mais vezes antes, mas não no período imediatamente anterior ao R30. |
| Usuários ou locatários decorridos | Usuários ativos ou locatários que não foram vistos durante um determinado período de tempo do R30, mas que foram vistos durante o período imediatamente anterior ao R30. |

### <a name="usage-intensity"></a>Intensidade de uso

O **gráfico de intensidade** de uso mostra as principais métricas de intensidade de uso para seu aplicativo.

 :::image type="content" source="../../assets/images/tdp/usage-intensity.png" alt-text="Intensidade":::

| Indicador | Definição |
| :-----------------------| :------------------------------------------------------------------------------------------------------|
| Dias mediano usados por mês | Os números medianados de dias em que seu aplicativo foi aberto no último período de tempo de R30 (30 dias sem interrupção). |
| % de uso de mais de 5 dias | O percentual de usuários ativos que abriram ou usaram o aplicativo mais de cinco dias no último período de tempo do R30. |
| DAU/MAU | A proporção do número médio de usuários ou locatários exclusivos que usaram seu aplicativo em cada dia dividido pelos Usuários Ativos Mensais para o período de tempo R30 selecionado. |

### <a name="app-dashboard"></a>Painel do aplicativo

A **tabela do painel** Meu Aplicativo mostra os dados mais recentes do R30 (30 dias sem interrupção) para cada uma das métricas nas quatro categorias anteriores e a alteração mês a mês. Use o seletor de tempo no canto superior esquerdo e selecione a data desejada. Você pode ver os dados diários do R30 dos últimos 75 dias e do final do mês R30 por até 12 meses.

Você pode selecionar cada um desses nomes **de métrica** para ver tendências ao longo do tempo.

 :::image type="content" source="../../assets/images/tdp/app-dashboard.png" alt-text="App":::

## <a name="use-tools-to-create-app-features"></a>Usar ferramentas para criar recursos de aplicativo

O Portal do Desenvolvedor também inclui ferramentas para ajudá-lo a criar alguns dos principais recursos dos aplicativos do Teams. Algumas dessas ferramentas incluem:

* **Estúdio de cena**: crie [cenas personalizadas do Modo Juntos](~/apps-in-teams-meetings/teams-together-mode.md) para reuniões do Teams.
* **Editor de Cartões Adaptáveis**: crie e visualize Cartões Adaptáveis para incluir com seus aplicativos.
* **Gerenciamento da plataforma de identidade da Microsoft**: registre seus aplicativos com o Azure Active Directory para ajudar os usuários a entrar e fornecer acesso às APIs.

## <a name="see-also"></a>Confira também

[Incluir uma oferta SaaS com seu aplicativo Microsoft Teams](~/concepts/deploy-and-publish/appsource/prepare/include-saas-offer.md)
