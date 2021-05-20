---
title: Crie aplicativos personalizados de código baixo para Microsoft Teams
author: laujan
description: Detalhe as soluções de código disponíveis da Microsoft para Teams
localization_priority: Normal
ms.author: lajanuar
ms.topic: conceptual
ms.openlocfilehash: a5615c5b70e21ea1bcade3dc46c6a2b5b3bc4f92
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566205"
---
# <a name="create-low-code-custom-apps-for-microsoft-teams"></a>Crie aplicativos personalizados de código baixo para Microsoft Teams

Microsoft Teams é extensível e adaptável. Isso significa que você pode criar aplicativos personalizados para Teams que atendam às necessidades distintas de seus usuários. Os aplicativos personalizados de baixo código economizam tempo, fornecem soluções rápidas e atendem à demanda do que os aplicativos criados do zero. Este documento fornece uma visão geral da Microsoft Power Platform, Power Virtual Agents chatbot e Virtual Assistant.

Plataformas de código baixo fornecem uma abordagem intuitiva para o desenvolvimento de software e requerem pouca ou nenhuma codificação para construir aplicativos e processos. Eles permitem que os desenvolvedores sem experiência, construam aplicativos personalizados facilmente com pouca ou nenhuma codificação, e desenvolvedores profissionais desenvolvam e implantem o aplicativo rapidamente. Essas plataformas consistem em uma interface visual, conectores para backend services e um sistema de gerenciamento de ciclo de vida de aplicativos incorporado para construir, depurar, implantar e manter aplicativos. O Microsoft Power Platform é o gateway inovador para criar rapidamente aplicativos compatíveis Teams usando atributos de código baixo.

## <a name="teams-and-microsoft-power-platform"></a>Teams e Microsoft Power Platform

A Microsoft Power Platform combina quatro tecnologias robustas da Microsoft, como Power BI, Power Apps, Power Automate, anteriormente Microsoft Flow e Power Virtual Agents em uma poderosa plataforma de aplicativos. Essas tecnologias permitem que você construa soluções, automatize processos, analise dados e crie agentes virtuais em um ambiente unificado e integrado:

:::image type="content" source="../assets/images/power-platform-and-teams/ms-power-platform.png" alt-text="Serviços de plataforma de energia":::

> [!NOTE]
> Você não deve usar a Microsoft Power Platform para criar aplicativos que serão publicados na loja de aplicativos Teams. Os aplicativos da Microsoft Power Platform podem ser publicados apenas na loja de aplicativos de uma organização.

### <a name="-teams-and-power-bi"></a>✔ Teams e Power BI

A [Power BI aba Microsoft Teams](https://powerbi.microsoft.com/blog/announcing-new-power-bi-tab-for-microsoft-teams/) adiciona suporte a relatórios no espaço de trabalho Teams e permite que os usuários [compartilhem conteúdo interativo Power BI](/power-bi/collaborate-share/service-embed-report-microsoft-teams) e colaborem com outros em canais e chats [Teams.](/power-bi/collaborate-share/service-collaborate-microsoft-teams) Você pode criar o conteúdo do [aplicativo Power BI](/power-bi/collaborate-share/service-create-distribute-apps) embalado do zero e distribuí-lo como um aplicativo ou criar um aplicativo de modelo [em Power BI](/connect-data/service-template-apps-create). Além disso, use o novo [aplicativo de Power BI em Teams](https://go.microsoft.com/fwlink/?linkid=2143643) para trazer toda a sua experiência básica de serviço de Power BI para Teams.

### <a name="-teams-and-power-apps"></a>✔ Teams e Power Apps

Com [Power Apps,](/powerapps/powerapps-overview)você pode criar aplicativos de negócios que se conectem aos dados da sua empresa e sejam adaptados às necessidades da sua organização.  Power Apps permitem uma ampla gama de cenários de aplicativos para resolver desafios de negócios através [de aplicativos de tela](/powerapps/maker/#canvas-apps). Após a construção, você pode exportar o aplicativo a partir do portal Power Apps maker e [incorporar em Microsoft Teams](/power-platform/admin/embed-app-teams).

O novo [aplicativo de Power Apps](https://go.microsoft.com/fwlink/?linkid=2143374) em Teams oferece uma experiência integrada para os fabricantes de aplicativos criarem e editarem aplicativos e fluxos de trabalho dentro de Teams. Eles podem publicar e compartilhar rapidamente os aplicativos para os membros da equipe. Os membros podem usar os aplicativos sem ter que alternar entre vários aplicativos e serviços.

### <a name="-teams-and-power-automate"></a>✔ Teams e Power Automate

Você pode [criar fluxos para automatizar tarefas de trabalho repetitivas](https://flow.microsoft.com/connectors/shared_teams/microsoft-teams/) diretamente dentro do ambiente Teams com o [aplicativo Power Automate em Teams](/power-automate/flows-teams). Você pode [acionar um fluxo de qualquer mensagem em Microsoft Teams](/power-automate/trigger-flow-teams-message) e [usar cartões adaptativos dentro de Power Automate](/power-automate/create-adaptive-cards). Além disso, você pode criar fluxos para personalizar e agregar mais valor a Microsoft Teams de dentro do novo [aplicativo de Power Apps](https://go.microsoft.com/fwlink/?linkid=2143539) em Teams.

### <a name="-teams-and-power-virtual-agents"></a>✔ Teams e Power Virtual Agents

[Power Virtual Agents](/power-virtual-agents/fundamentals-what-is-power-virtual-agents) é uma solução de interface gráfica sem código, guiada, construída na Microsoft Power Platform e no Bot Framework. Ele capacita todos os membros de sua equipe a criar e manter chatbots ricos e conversacionais que se integram facilmente com a plataforma Teams. Todo o conteúdo autorizado em Power Virtual Agents renderiza naturalmente em Teams e Power Virtual Agents bots se envolvem com os usuários na tela de bate-papo nativo Teams. Você pode [integrar seu chatbot Power Virtual Agents](/power-virtual-agents/publication-add-bot-to-microsoft-teams) para Teams através do portal [Power Virtual Agents](https://powervirtualagents.microsoft.com).

Use o novo [aplicativo de Power Virtual Agents](https://aka.ms/pva-teams-docs) em Teams, para criar, gerenciar e publicar chatbots conversacionais facilmente de dentro de Teams. Você pode compartilhar seus bots com outras pessoas da sua organização para conversar e obter respostas para suas perguntas.

### <a name="-virtual-assistant-for-teams"></a>assistente virtual ✔ para Teams

Virtual Assistant é um modelo de código aberto da Microsoft que permite criar uma solução de conversação robusta, mantendo o controle total da experiência do usuário, da marca organizacional e dos dados necessários. Você pode configurar seu assistente virtual para [integração no ambiente Teams](https://microsoft.github.io/botframework-solutions/clients-and-channels/tutorials/enable-teams/1-intro). 

### <a name="-power-platform-learn-modules"></a>✔ módulos de aprendizado da plataforma de energia

|  Tópico  |  Links  |
|:---------|:----------------------|
|Power BI|[Power BI para fabricantes de aplicativos](/learn/browse/?expanded=power-platform&products=power-bi&roles=maker)</br>[Power BI para Desenvolvedores](/learn/browse/?expanded=power-platform&products=power-bi&roles=developer)|
|Aplicativos de energia|[Power Apps para fabricantes de aplicativos](/learn/browse/?products=power-apps&roles=maker)</br>[Power Apps para Desenvolvedores](/learn/browse/?products=power-apps)|
|Power Automate|[Power Automate para fabricantes de aplicativos](/learn/browse/?expanded=power-platform&products=power-automate&roles=maker)</br>[Power Automate para Desenvolvedores](/learn/browse/?expanded=power-platform&products=power-automate&roles=developer)|
|Agentes virtuais do Power|[Power Virtual Agents para fabricantes de aplicativos e desenvolvedores](/learn/browse/?products=power-virtual-agents&expanded=power-platform&roles=maker)|

### <a name="-project-oakdale-preview"></a>✔ Project Oakdale (pré-visualização)

> [!NOTE]
> Project **Oakdale** é renomeada para projeto **Dataverse para Teams**.

[Project Oakdale](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/teams-is-shaping-the-future-of-work-with-low-code-features-to/ba-p/1507180
) é uma nova plataforma de dados de código baixo que está prestes a Microsoft Teams. Ele permite que os desenvolvedores criem soluções Teams Power Platform diretamente dentro Teams. Para obter mais informações sobre Project Oakdale, consulte [Teams Blog Microsoft Project Oakdale](https://powerapps.microsoft.com/blog/introducing-project-oakdale-a-new-low-code-data-platform-for-microsoft-teams).

### <a name="-microsoft-blog-insights"></a>✔ insights do Microsoft Blog

[Um olhar mais atento aos recursos da plataforma de dados em Project Oakdale](https://powerapps.microsoft.com/blog/a-closer-look-at-data-platform-capabilities-in-project-oakdale/)

[Anunciar a Plataforma de Energia e Teams atualizações para ajudar os clientes a se adaptarem ao trabalho remoto](https://cloudblogs.microsoft.com/powerplatform/2020/05/19/announcing-power-platform-and-teams-updates-to-help-customers-adapt-to-remote-work/)

[Teams está moldando o futuro do trabalho com recursos de código baixo para melhorar seu espaço de trabalho digital](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/teams-is-shaping-the-future-of-work-with-low-code-features-to/ba-p/1507180)

### <a name="-managing-power-platform-apps"></a>✔ gerenciando aplicativos da plataforma de energia

> [!div class="nextstepaction"]
> [Gerencie aplicativos da Microsoft Power Platform no centro administrativo de Microsoft Teams](/microsoftteams/manage-power-platform-apps)

## <a name="see-also"></a>Confira também

[Integrar aplicativos Web](~/samples/integrate-web-apps-overview.md)