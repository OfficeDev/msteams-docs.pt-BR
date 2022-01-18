---
title: Criar aplicativos para a plataforma Microsoft Teams
author: heath-hamilton
description: Obtenha uma visão geral de como os desenvolvedores podem estender os recursos do Microsoft Teams com aplicativos personalizados.
ms.topic: overview
ms.localizationpriority: high
ms.author: lajanuar
ms.date: 05/24/2021
ms.openlocfilehash: 1a7957c8ea6d889ffe5ab7e40c8a5bb1377b6ca5
ms.sourcegitcommit: 9e448dcdfd78f4278e9600808228e8158d830ef7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2022
ms.locfileid: "62059620"
---
# <a name="build-apps-for-microsoft-teams"></a>Crie aplicativos para o Microsoft Teams

Os aplicativos do Microsoft Teams trazem informações importantes, ferramentas comuns e processos confiáveis para onde as pessoas se reúnem, aprendem e trabalham cada vez mais.

Os aplicativos são como você estende o Teams para atender às suas necessidades. Crie algo novo para o Teams ou integre um aplicativo existente.

> [!div class="nextstepaction"]
> [Iniciar aqui](get-started/get-started-overview.md)

## <a name="what-are-teams-apps"></a>O que são os aplicativos Teams?

Os aplicativos do Teams são uma combinação de [recursos](concepts/capabilities-overview.md). Alguns aplicativos são simples (enviar notificações), enquanto outros são complexos (gerenciar registros de pacientes). Ao planejar seu aplicativo, lembre-se de que o Teams é um hub de colaboração. Os melhores aplicativos do Teams ajudam as pessoas a se expressarem e trabalharem melhor juntas.

### <a name="personal-apps"></a>Aplicativos pessoais

:::row:::
   :::column span="1":::

**Ajuda o foco das pessoas**: Uma [Aplicação pessoal](concepts/design/personal-apps.md) é um espaço dedicado ou bot para ajudar os usuários a se concentrarem em suas próprias tarefas ou exibir atividades importantes para eles.

   :::column-end:::

   :::column span="3":::

:::image type="content" source="assets/images/overview-personal-apps-2021.png" alt-text="Representação conceitual de como são as aplicações pessoais no cliente do Teams." border="false":::

   :::column-end:::

:::row-end:::

### <a name="tabs"></a>Guias

:::row:::
   :::column span="1":::

**Colabore de forma mais conveniente**: Apresente seu conteúdo baseado na web em uma [aba](tabs/what-are-tabs.md) onde as pessoas possam discutir e trabalhar em conjunto.

   :::column-end:::

   :::column span="3":::

:::image type="content" source="assets/images/overview-channel-chat-apps-2021.png" alt-text="Representação conceitual de como são as abas no cliente do Teams." border="false":::

   :::column-end:::

:::row-end:::

### <a name="bots"></a>Bots

:::row:::
   :::column span="1":::

**Transformar palavras em ações**: As conversas frequentemente resultam na necessidade de fazer algo (gerar um pedido, rever meu código, verificar o status do bilhete, e assim por diante). Um [bot](bots/what-are-bots.md) pode dar início a este tipo de fluxo de trabalho dentro do Teams.

   :::column-end:::

   :::column span="3":::

:::image type="content" source="assets/images/overview-bots-2021.png" alt-text="Representação conceitual de como são os bots no cliente do Teams." border="false":::

   :::column-end:::

:::row-end:::

### <a name="messaging-extensions"></a>Extensões de mensagens

:::row:::

   :::column span="1":::

**Facilitar a multitarefa**: Com as [extensões de mensagens](messaging-extensions/what-are-messaging-extensions.md), você pode compartilhar rapidamente informações externas em uma conversa. Você também pode agir em uma mensagem, como criar um tíquete de ajuda com base no conteúdo de uma postagem de canal.

   :::column-end:::

   :::column span="3":::

:::image type="content" source="assets/images/overview-messaging-extensions-2021.png" alt-text="Representação conceitual de como são as extensões de mensagens no cliente do Teams." border="false":::

   :::column-end:::
:::row-end:::

### <a name="meeting-extensions"></a>Extensões de reunião

:::row:::

   :::column span="1":::

**Criar aplicativos para reuniões**: Existem algumas opções para [incorporar seu aplicativo na experiência de chamada do Teams](apps-in-teams-meetings/design/designing-apps-in-meetings.md).

   :::column-end:::

   :::column span="3":::

:::image type="content" source="assets/images/overview-meeting-extensions-2021.png" alt-text="Representação conceitual de como são as extensões de reuniões no cliente do Teams." border="false":::

   :::column-end:::
:::row-end:::

### <a name="webhooks-and-connectors"></a>Webhooks e conectores

:::row:::

   :::column span="":::

**Comunique-se com aplicativos externos**: [Os webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) recebidos são uma forma simples de enviar automaticamente notificações de outro aplicativo para um canal do Teams. Com os [webhooks de saída](webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks), envie uma mensagem a seu serviço web com uma @menção.

   :::column-end:::

   :::column span="":::

:::image type="content" source="assets/images/overview-connectors.png" alt-text="Representação conceitual de como são os conectores no cliente do Teams." border="false":::

   :::column-end:::
:::row-end:::

### <a name="microsoft-graph-for-teams"></a>Microsoft Graph para o Teams

:::row:::

   :::column span="":::

**Utilizar os dados do Teams**: O [Microsoft Graph API para Teams](/graph/teams-concept-overview) fornece acesso a informações sobre equipes, canais, usuários e mensagens que podem ajudá-lo a criar ou aprimorar recursos para seu aplicativo (como, por exemplo, notificações ricas).

   :::column-end:::

   :::column span="":::

:::image type="content" source="assets/images/overview-graph.png" alt-text="Representação conceitual do Microsoft Graph API para o Teams." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="start-building"></a>Começar criar

Familiarize-se rapidamente com a criação do Teams configurando seu ambiente e criando um aplicativo simples.

> [!div class="nextstepaction"]
> [Desenvolver seu primeiro aplicativo](get-started/get-started-overview.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="integrate-with-teams"></a>Integrar com o Teams

Combine os recursos que os usuários adoram em um aplicativo Web, serviço ou sistema existente com os recursos colaborativos do Teams.

> [!div class="nextstepaction"]
> [Integrar um aplicativo existente](samples/integrating-web-apps.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="a-little-code-goes-a-long-way"></a>Um código pequeno é muito longo

Você não precisa ser um programador especialista para criar um ótimo aplicativo do Teams. Experimente uma das várias soluções de pouco código.

> [!div class="nextstepaction"]
> [Criar um app de código-baixo](samples/teams-low-code-solutions.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="get-ideas-for-your-app"></a>Obtenha ideias para seu aplicativo

Procurando inspiração para o desenvolvimento de aplicativos? Navegue pela nossa lista de cenários reais e soluções do setor com simulações de conceito de alta fidelidade para entender as várias maneiras como os aplicativos do Teams podem ajudar seus usuários.

> [!div class="nextstepaction"]
> [Ver cenários de aplicativo](https://adoption.microsoft.com/extensibility-look-book/scenarios/)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

## <a name="test-your-app-running-across-microsoft-365"></a>Testar seu aplicativo em execução em Microsoft 365

Você pode visualizar seus aplicativos do Teams em execução em outras experiências de Microsoft 365 com o SDK do cliente JavaScript do Microsoft Teams v2 Preview.

> [!div class="nextstepaction"]
> [Extender seu aplicativo](m365-apps/overview.md)

## <a name="see-also"></a>Confira também

* [Aplicativos básicos](~/concepts/app-fundamentals-overview.md)
* [Design seu aplicativo do Teams](~/concepts/design/design-teams-app-process.md)
* [ Mapeie seus casos de uso para as capacidades de aplicação do Teams](~/concepts/design/map-use-cases.md)
