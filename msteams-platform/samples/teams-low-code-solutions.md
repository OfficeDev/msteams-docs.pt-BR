---
title: Criar aplicativos personalizados de baixo código para Microsoft Teams
author: surbhigupta
description: Detalhar as soluções de código disponíveis da Microsoft para Teams
ms.localizationpriority: medium
ms.author: lajanuar
ms.topic: conceptual
ms.openlocfilehash: 77e3f3cbd8e5de53748b64b5006df259b2164e4f
ms.sourcegitcommit: 72de146d11e81fd9777374dd3915ad290fd07d82
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2021
ms.locfileid: "59360666"
---
# <a name="create-low-code-custom-apps-for-microsoft-teams"></a>Criar aplicativos personalizados de baixo código para Microsoft Teams

Microsoft Teams é extensível e adaptável. Isso significa que você pode criar aplicativos personalizados para Teams que atendem às necessidades distintas de seus usuários. Os aplicativos personalizados de código baixo economizam tempo, fornecem soluções rápidas e atendem à mesma demanda que os aplicativos criados do zero. Este documento fornece uma visão geral do Microsoft Power Platform, Power Virtual Agents chatbot e Assistente Virtual.

As plataformas de código baixo fornecem uma abordagem intuitiva para o desenvolvimento de software com o mínimo ou nenhuma codificação para criar aplicativos e processos. Eles permitem que os desenvolvedores sem experiência criem aplicativos personalizados facilmente com pouca ou nenhuma codificação e desenvolvedores profissionais desenvolvam e implantem o aplicativo rapidamente. Essas plataformas consistem em uma interface visual, conectores para serviços de back-end e um sistema de gerenciamento de ciclo de vida de aplicativos integrado para criar, depurar, implantar e manter aplicativos. A Plataforma do Microsoft Power é o gateway inovador para criar rapidamente Teams aplicativos compatíveis usando atributos de código baixos.

## <a name="teams-and-microsoft-power-platform"></a>Teams Microsoft Power Platform

O Microsoft Power Platform combina quatro tecnologias robustas da Microsoft, como Power BI, Power Apps, Power Automate, anteriormente Microsoft Flow e Power Virtual Agents em uma plataforma de aplicativos poderosa. Essas tecnologias permitem criar soluções, automatizar processos, analisar dados e criar agentes virtuais em um ambiente unificado e integrado:

:::image type="content" source="../assets/images/power-platform-and-teams/ms-power-platform.png" alt-text="Serviços de plataforma de energia":::

> [!NOTE]
> Você não deve usar o Microsoft Power Platform para criar aplicativos que devem ser publicados na Teams de aplicativos. Os aplicativos da Plataforma Microsoft Power só podem ser publicados no armazenamento de aplicativos de uma organização.

### <a name="-teams-and-power-bi"></a>✔ Teams e Power BI

[A](/power-bi/collaborate-share/service-embed-report-microsoft-teams) [guia Power BI](https://powerbi.microsoft.com/blog/announcing-new-power-bi-tab-for-microsoft-teams/) para Microsoft Teams adiciona suporte para relatórios no espaço de trabalho Teams e permite que os [](/power-bi/collaborate-share/service-collaborate-microsoft-teams) usuários compartilhem conteúdo interativo Power BI e colaborem com outras pessoas em canais e chats Teams. Você pode criar conteúdo Power BI do [aplicativo](/power-bi/collaborate-share/service-create-distribute-apps) do zero e distribuí-lo como um aplicativo ou criar um aplicativo de modelo [em Power BI](/power-bi/connect-data/service-template-apps-create). Além disso, use o novo [aplicativo Power BI no Teams](https://go.microsoft.com/fwlink/?linkid=2143643) para trazer toda Power BI de serviço básico para Teams.

### <a name="-teams-and-power-apps"></a>✔ Teams e Power Apps

Com [Power Apps](/powerapps/powerapps-overview), você pode criar aplicativos de negócios que se conectam aos seus dados de negócios e são adaptados às necessidades da sua organização.  Power Apps uma ampla variedade de cenários de aplicativos para resolver desafios de negócios por meio de [aplicativos de tela.](/powerapps/maker/#canvas-apps) Após a criação, você pode exportar o aplicativo do portal do criador Power Apps e [incorporar em Microsoft Teams](/power-platform/admin/embed-app-teams).

O novo [Power Apps no](https://go.microsoft.com/fwlink/?linkid=2143374) Teams fornece uma experiência integrada para os criadores de aplicativos criarem e editarem aplicativos e fluxos de trabalho dentro Teams. Eles podem publicar e compartilhar rapidamente os aplicativos aos membros da equipe. Os membros podem usar os aplicativos sem precisar alternar entre vários aplicativos e serviços.

### <a name="-teams-and-power-automate"></a>✔ Teams e Power Automate

Você pode [criar fluxos para automatizar tarefas](https://flow.microsoft.com/connectors/shared_teams/microsoft-teams/) de trabalho repetitivas diretamente no ambiente Teams com o aplicativo [Power Automate no Teams](/power-automate/flows-teams). Você pode [disparar um fluxo de qualquer mensagem](/power-automate/trigger-flow-teams-message) no Microsoft Teams e usar Cartões [Adaptáveis em](/power-automate/create-adaptive-cards)Power Automate . Além disso, você pode criar fluxos para personalizar e adicionar mais valor Microsoft Teams dentro do novo aplicativo Power Apps [no](https://go.microsoft.com/fwlink/?linkid=2143539) Teams.

### <a name="-teams-and-power-virtual-agents"></a>✔ Teams e Power Virtual Agents

[Power Virtual Agents](/power-virtual-agents/fundamentals-what-is-power-virtual-agents) é uma solução sem código, de interface gráfica guiada, baseada na Plataforma do Microsoft Power e na Estrutura de Bots. Ele capacita todos os membros da sua equipe a criar e manter chatbots ricos e conversacionais que se integram facilmente à plataforma Teams. Todo o conteúdo Power Virtual Agents renderiza naturalmente em Teams e Power Virtual Agents bots se envolvem com usuários na tela de chat Teams nativa. Você pode [integrar seu Power Virtual Agents chatbot para](/power-virtual-agents/publication-add-bot-to-microsoft-teams) Teams através do portal Power Virtual Agents [portal](https://powervirtualagents.microsoft.com).

Use o novo [Power Virtual Agents no Teams,](https://aka.ms/pva-teams-docs) para criar, gerenciar e publicar chatbots de conversação facilmente de dentro Teams. Você pode compartilhar seus bots com outras pessoas em sua organização para conversar e obter respostas para suas perguntas.

### <a name="-virtual-assistant-for-teams"></a>✔ Assistente Virtual para Teams

Assistente Virtual é um modelo de código aberto da Microsoft que permite que você crie uma solução de conversação robusta, mantendo o controle total da experiência do usuário, da identidade visual organizacional e dos dados necessários. Você pode configurar seu assistente virtual para [integração com o Teams ambiente](https://microsoft.github.io/botframework-solutions/clients-and-channels/tutorials/enable-teams/1-intro). 

### <a name="-power-platform-learn-modules"></a>✔ módulos do Power Platform Learn

|  Tópico  |  Links  |
|:---------|:----------------------|
|Power BI|[Power BI para Criadores de Aplicativos](/learn/browse/?expanded=power-platform&products=power-bi&roles=maker)</br>[Power BI para desenvolvedores](/learn/browse/?expanded=power-platform&products=power-bi&roles=developer)|
|Power Apps|[Power Apps para Criadores de Aplicativos](/learn/browse/?products=power-apps&roles=maker)</br>[Power Apps para desenvolvedores](/learn/browse/?products=power-apps)|
|Power Automate|[Power Automate para Criadores de Aplicativos](/learn/browse/?expanded=power-platform&products=power-automate&roles=maker)</br>[Power Automate para desenvolvedores](/learn/browse/?expanded=power-platform&products=power-automate&roles=developer)|
|Agentes virtuais do Power|[Power Virtual Agents para desenvolvedores e criadores de aplicativos](/learn/browse/?products=power-virtual-agents&expanded=power-platform&roles=maker)|

### <a name="-project-oakdale-preview"></a>✔ Project Oakdale (visualização)

> [!NOTE]
> Project **Oakdale** é renomeada para project **Dataverse para Teams**.

[Project Oakdale](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/teams-is-shaping-the-future-of-work-with-low-code-features-to/ba-p/1507180
) é uma nova plataforma de dados de baixo código que será Microsoft Teams. Ele permite que os desenvolvedores criem Teams soluções da Plataforma Power diretamente no Teams. Para obter mais informações sobre Project Oakdale, [consulte Teams Blog Microsoft Project Oakdale](https://powerapps.microsoft.com/blog/introducing-project-oakdale-a-new-low-code-data-platform-for-microsoft-teams).

### <a name="-microsoft-blog-insights"></a>✔ do Microsoft Blog

[Uma olhada mais de perto nos recursos da plataforma de dados em Project Oakdale](https://powerapps.microsoft.com/blog/a-closer-look-at-data-platform-capabilities-in-project-oakdale/)

[Anunciando as atualizações do Power Platform e Teams para ajudar os clientes a se adaptarem ao trabalho remoto](https://cloudblogs.microsoft.com/powerplatform/2020/05/19/announcing-power-platform-and-teams-updates-to-help-customers-adapt-to-remote-work/)

[Teams está moldando o futuro do trabalho com recursos de código baixo para aprimorar seu espaço de trabalho digital](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/teams-is-shaping-the-future-of-work-with-low-code-features-to/ba-p/1507180)

### <a name="-managing-power-platform-apps"></a>✔ gerenciar aplicativos da Plataforma Power

> [!div class="nextstepaction"]
> [Gerenciar aplicativos da Plataforma Microsoft Power no Microsoft Teams de administração](/microsoftteams/manage-power-platform-apps)

## <a name="see-also"></a>Confira também

[Integrar aplicativos Web](~/samples/integrate-web-apps-overview.md)
