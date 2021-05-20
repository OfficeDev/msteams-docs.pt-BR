---
title: Crie aplicativos para a plataforma Microsoft Teams
author: heath-hamilton
description: Obtenha uma visão geral de como os desenvolvedores podem estender Microsoft Teams recursos com aplicativos personalizados.
ms.topic: overview
localization_priority: Normal
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: 8724b669476b11aa8cb1aca6d9586fc7ea42587d
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566506"
---
# <a name="build-apps-for-microsoft-teams"></a>Crie aplicativos para o Microsoft Teams

Microsoft Teams aplicativos trazem informações-chave, ferramentas comuns e processos confiáveis para onde as pessoas cada vez mais se reúnem, aprendem e trabalham.

Aplicativos são como você estende Teams para atender às suas necessidades. Crie algo novo para Teams ou integre um aplicativo existente.

> [!div class="nextstepaction"]
> [Iniciar aqui](build-your-first-app/build-first-app-overview.md)

## <a name="what-are-teams-apps"></a>O que são aplicativos Teams?

Teams aplicativos são uma combinação de [recursos](concepts/capabilities-overview.md) e pontos de [entrada.](concepts/extensibility-points.md) Por exemplo, as pessoas podem conversar com *o bot* (capability) do seu aplicativo em um *canal* (ponto de entrada).

Alguns aplicativos são simples (enviar notificações), enquanto outros são complexos (gerenciar registros de pacientes). Ao planejar seu aplicativo, lembre-se que Teams é um hub de colaboração. Os melhores aplicativos Teams ajudam as pessoas a se expressarem e trabalharem melhor juntas.

:::row:::
   :::column span="":::

### <a name="tabs"></a>Guias

**Obtenha informações mais convenientemente**: Às vezes você só precisa tornar as coisas mais fáceis de encontrar. Exibir uma página importante da web em uma [guia](tabs/what-are-tabs.md), que fornece uma experiência web em tela cheia para conteúdo estático e dinâmico em Teams.

:::image type="content" source="assets/images/overview-tabs.png" alt-text="Representação conceitual de como são as guias no Teams cliente." border="false":::

   :::column-end:::

   :::column span="":::

### <a name="bots"></a>Bots

**Transforme palavras em ações**: Muitas vezes as conversas resultam na necessidade de fazer algo (gerar um pedido, revisar meu código, verificar o status do bilhete e assim por diante). Um [bot](bots/what-are-bots.md) pode iniciar esse tipo de fluxos de trabalho dentro Teams.

:::image type="content" source="assets/images/overview-bots.png" alt-text="Representação conceitual de como os bots se parecem no Teams cliente." border="false":::

   :::column-end:::

:::row-end:::

:::row:::

   :::column span="":::

### <a name="messaging-extensions"></a>Extensões de mensagens

**Facilite a multitarefa**: Com [extensões de mensagens,](messaging-extensions/what-are-messaging-extensions.md)você pode compartilhar rapidamente informações externas em uma conversa. Você também pode agir em uma mensagem, como criar um bilhete de ajuda com base no conteúdo de um post de canal.

:::image type="content" source="assets\images\overview-messaging.png" alt-text="Representação conceitual de como são as extensões de mensagens no Teams cliente." border="false":::

   :::column-end:::

   :::column span="":::

### <a name="webhooks"></a>Webhooks

**Comunique-se com aplicativos externos**: [Webhooks recebidos](webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) são uma maneira simples de enviar automaticamente notificações de outro aplicativo para um canal Teams. Com [webhooks de saída,](webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks)envie uma mensagem ao seu serviço web com um @mention.

:::image type="content" source="assets/images/overview-connectors.png" alt-text="Representação conceitual de como os conectores se parecem no Teams cliente." border="false":::

   :::column-end:::
:::row-end:::

:::row:::

   :::column span="":::

### <a name="microsoft-graph-for-teams"></a>Microsoft Graph para Teams

**Utilize dados Teams**: A [API de Graph microsoft para Teams](/graph/teams-concept-overview) fornece acesso a informações sobre equipes, canais, usuários e mensagens que podem ajudá-lo a criar ou aprimorar recursos para o seu aplicativo.

:::image type="content" source="assets/images/overview-graph.png" alt-text="Representação conceitual da API microsoft Graph para Teams." border="false":::

   :::column-end:::

   :::column span="":::
   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="start-building"></a>Comece a construir

Familiarize-se rapidamente com a construção de Teams, configurando seu ambiente e criando um aplicativo simples.

> [!div class="nextstepaction"]
> [Desenvolver seu primeiro aplicativo](build-your-first-app/build-first-app-overview.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="integrate-with-teams"></a>Integrar com o Teams

Misture os recursos que os usuários adoram sobre um aplicativo, serviço ou sistema web existente com os recursos colaborativos de Teams.

> [!div class="nextstepaction"]
> [Integre um aplicativo existente](samples/integrating-web-apps.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="a-little-code-goes-a-long-way"></a>Um pequeno código vai longe

Você não precisa ser um programador especialista para construir um ótimo aplicativo de Teams. Experimente uma das várias soluções de código baixo.

> [!div class="nextstepaction"]
> [Crie um aplicativo de código baixo](samples/teams-low-code-solutions.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="get-ideas-for-your-app"></a>Obtenha ideias para o seu aplicativo

Procurando inspiração para desenvolvimento de aplicativos? Navegue pela nossa lista de cenários do mundo real e soluções do setor com conceito de alta fidelidade simula para entender as várias maneiras Teams aplicativos podem ajudar seus usuários.

> [!div class="nextstepaction"]
> [Veja cenários de aplicativos](https://adoption.microsoft.com/extensibility-look-book/scenarios/)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

## <a name="see-also"></a>Confira também

* [Adicione um botão Compartilhar a Teams ao seu site](concepts/build-and-test/share-to-teams.md)
* [Projete seu aplicativo de Teams](concepts/design/design-teams-app-overview.md)
* [Microsoft Teams Cliente JavaScript SDK](/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true)
* Bot Framework SDK para [JavaScript](https://github.com/Microsoft/botbuilder-js) e [.NET](https://github.com/Microsoft/botbuilder-dotnet/)
* [Distribua seu aplicativo de Teams](concepts/deploy-and-publish/apps-publish-overview.md)
