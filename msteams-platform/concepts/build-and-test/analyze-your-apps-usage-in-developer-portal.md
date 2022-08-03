---
title: Analisar o uso do aplicativo no Portal do Desenvolvedor
description: Neste módulo, saiba como analisar o uso do aplicativo no Portal do Desenvolvedor
ms.localizationpriority: medium
ms.topic: overview
ms.author: surbhigupta
ms.openlocfilehash: 43758fdebd1f2e76318880a51d9173469b0ed604
ms.sourcegitcommit: 990a36fb774e614146444d4adaa2c9bcdb835998
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/03/2022
ms.locfileid: "67232363"
---
# <a name="analyze-your-apps-usage-in-developer-portal"></a>Analisar o uso do aplicativo no Portal do Desenvolvedor

No Portal do Desenvolvedor para Teams, na página **Visão** geral, você pode ver o número total de usuários ativos para seu aplicativo.

> [!NOTE]
> Atualmente, a análise de uso está disponível apenas para novos aplicativos personalizados publicados em sua organização por meio do **Portal** do Desenvolvedor para Teams ou importados para o **Portal** do Desenvolvedor para Teams após abril de 2022. A análise de uso de todos os aplicativos publicados na loja do Teams está disponível no **Partner Center** para obter mais informações sobre o relatório de uso de [aplicativos do Teams](/office/dev/store/teams-apps-usage).

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

 :::image type="content" source="../../assets/images/tdp/dev-app-portal.png" alt-text="As capturas de tela mostram a página de análise do aplicativo no Portal do Desenvolvedor."lightbox="../../assets/images/tdp/dev-app-portal.png":::

Ao explorar métricas individuais nesta página, você pode usar o botão  Filtro para analisar o uso do aplicativo nas seguintes opções de filtro:

* Tipo de agregação: esse filtro permite agrupar as seguintes métricas por uma contagem de usuários distintos ou uma contagem de locatários ou clientes distintos.
* Plataforma
* Sistema operacional
* Área

 :::image type="content" source="../../assets/images/tdp/dev-analytics-filter.png" alt-text="As capturas de tela mostram o filtro de página de análise no Portal do Desenvolvedor.":::

Depois de selecionar os filtros desejados, você pode explorar os seguintes widgets individuais:

* [Uso por período de tempo](#usage-by-time-period)
* [Uso por plataforma e sistema operacional](#usage-by-platform-and-os)
* [Uso por estado de retenção](#usage-by-retention-state)
* [Intensidade de uso](#usage-intensity)

## <a name="usage-by-time-period"></a>Uso por período de tempo

O **gráfico Uso por período de** tempo mostra o número de usuários ativos ou locatários que abriram e usaram seu aplicativo em diferentes períodos de tempo.

 :::image type="content" source="../../assets/images/tdp/usage-by-time-period.png" alt-text="As capturas de tela mostram o gráfico de uso por período de tempo para seu aplicativo publicado.":::

| Indicador | Definição |
| :-----------------------| :------------------------------------------------------------------------------------------------------|
| R30 mensal | Cada ponto de dados representa um determinado período de R30 (30 dias sem interrupção). |
| R28 mensal | Cada ponto de dados representa um determinado período de R28 (28 dias sem interrupção). |
| R7 semanal| Cada ponto de dados representa um determinado período de R7 (7 dias sem interrupção). |
| Diariamente | Cada ponto de dados representa um determinado período de R1 (1 dia sem interrupção). |

## <a name="usage-by-platform-and-os"></a>Uso por plataforma e sistema operacional

O **gráfico uso por** plataforma e sistema operacional mostra o uso ativo do aplicativo em vários pontos de extremidade, como **Windows**, **Mac**, **iOS**, **Android** e **Web**. O mesmo usuário ou locatário pode usar um aplicativo em vários pontos de extremidade. Cada ponto de dados representa um determinado período de R30 (30 dias sem interrupção).

 :::image type="content" source="../../assets/images/tdp/usage-by-platform-OS.png" alt-text="As capturas de tela mostram o uso por plataforma e o gráfico do sistema operacional para seu aplicativo publicado.":::

## <a name="usage-by-retention-state"></a>Uso por estado de retenção

O **gráfico uso por estado de retenção** permite controlar quatro métricas de retenção ou variação de chave para seu aplicativo ao longo do tempo.

:::image type="content" source="../../assets/images/tdp/usage-by-retention-state.png" alt-text="As capturas de tela mostram o uso por gráfico de estado de retenção para seu aplicativo publicado.":::

| Indicador | Definição |
| :-----------------------| :------------------------------------------------------------------------------------------------------|
| Novos usuários ou locatários | Usuários ativos ou locatários que são novos e não usaram seu aplicativo. |
| Retornando usuários ou locatários | Usuários ativos ou locatários que usaram seu aplicativo durante um determinado período de tempo R30 (sem interrupção de 30 dias) e o período de tempo imediatamente anterior ao R30. |
| Usuários ou locatários ressuscitados | Usuários ativos ou locatários que usaram seu aplicativo uma ou mais vezes antes, mas não no período imediatamente anterior ao R30. |
| Usuários ou locatários decorridos | Usuários ativos ou locatários que não foram vistos durante um determinado período de tempo do R30, mas que foram vistos durante o período imediatamente anterior ao R30. |

## <a name="usage-intensity"></a>Intensidade de uso

O **gráfico de intensidade** de uso mostra as principais métricas de intensidade de uso para seu aplicativo.

 :::image type="content" source="../../assets/images/tdp/usage-intensity.png" alt-text="As capturas de tela mostram o gráfico de intensidade de uso do aplicativo publicado.":::

| Indicador | Definição |
| :-----------------------| :------------------------------------------------------------------------------------------------------|
| Dias mediano usados por mês | Os números medianados de dias em que seu aplicativo foi aberto no último período de tempo de R30 (30 dias sem interrupção). |
| % de uso de mais de 5 dias | O percentual de usuários ativos que abriram ou usaram o aplicativo mais de cinco dias no último período de tempo do R30. |
| DAU/MAU | A proporção do número médio de usuários ou locatários exclusivos que usaram seu aplicativo em cada dia dividido pelos Usuários Ativos Mensais para o período de tempo R30 selecionado. |

## <a name="app-dashboard"></a>Painel do aplicativo

A **tabela do painel** Meu Aplicativo mostra os dados mais recentes do R30 (30 dias sem interrupção) para cada uma das métricas nas quatro categorias anteriores e a alteração mês a mês. Use o seletor de tempo no canto superior esquerdo e selecione a data desejada. Você pode ver os dados diários do R30 dos últimos 75 dias e do final do mês R30 por até 12 meses.

Você pode selecionar cada um desses nomes **de métrica** para ver tendências ao longo do tempo.

 :::image type="content" source="../../assets/images/tdp/app-dashboard.png" alt-text="As capturas de tela mostram o gráfico de painel do aplicativo para seu aplicativo publicado.":::

## <a name="see-also"></a>Confira também

[Incluir uma oferta SaaS com seu aplicativo Microsoft Teams](~/concepts/deploy-and-publish/appsource/prepare/include-saas-offer.md)
