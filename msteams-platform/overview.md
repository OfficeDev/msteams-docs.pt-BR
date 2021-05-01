---
title: Criar aplicativos para a Microsoft Teams plataforma
author: heath-hamilton
description: Obter uma visão geral de como os desenvolvedores podem estender Microsoft Teams recursos com aplicativos personalizados.
ms.topic: overview
localization_priority: Normal
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: 69c36cf5f925bdb9802e7ec081a7765187a06128
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101839"
---
# <a name="build-apps-for-microsoft-teams"></a>Crie aplicativos para o Microsoft Teams

Microsoft Teams aplicativos trazem informações importantes, ferramentas comuns e processos confiáveis para onde as pessoas coletam, aprendem e trabalham cada vez mais.

Aplicativos são como você estende Teams para se ajustar às suas necessidades. Crie algo novo para Teams ou integre um aplicativo existente.

> [!div class="nextstepaction"]
> [Iniciar aqui](build-your-first-app/build-first-app-overview.md)

## <a name="what-are-teams-apps"></a>O que Teams aplicativos?

Teams aplicativos são uma combinação de [recursos e](concepts/capabilities-overview.md) pontos [de entrada.](concepts/extensibility-points.md) Por exemplo, as pessoas podem conversar com o bot (recurso) do seu *aplicativo* em um *canal* (ponto de entrada).

Alguns aplicativos são simples (notificações de envio), enquanto outros são complexos (gerenciar registros de pacientes). Ao planejar seu aplicativo, lembre-se de que Teams é um hub de colaboração. A melhor Teams aplicativos ajudam as pessoas a se expressarem e trabalharem melhor juntas.

:::row:::
   :::column span="":::

### <a name="tabs"></a>Guias

**Obter informações de forma mais conveniente:** às vezes, você só precisa tornar as coisas mais fáceis de encontrar. Exibe uma página da Web importante em uma [guia](tabs/what-are-tabs.md), que fornece uma experiência da Web de tela inteira para conteúdo estático e dinâmico Teams.

:::image type="content" source="assets/images/overview-tabs.png" alt-text="Representação conceitual de como as guias são no cliente Teams cliente." border="false":::

   :::column-end:::

   :::column span="":::

### <a name="bots"></a>Bots

**Transformar palavras em ações**: as conversas geralmente resultam na necessidade de fazer algo (gerar um pedido, revisar meu código, verificar o status do tíquete e assim por diante). Um [bot](bots/what-are-bots.md) pode dar início a esses tipos de fluxos de trabalho dentro Teams.

:::image type="content" source="assets/images/overview-bots.png" alt-text="Representação conceitual de como os bots são no Teams cliente." border="false":::

   :::column-end:::

:::row-end:::

:::row:::

   :::column span="":::

### <a name="messaging-extensions"></a>Extensões de mensagens

**Facilita a multitarefa**: Com extensões de mensagens, você pode compartilhar rapidamente informações [externas](messaging-extensions/what-are-messaging-extensions.md)em uma conversa. Você também pode agir em uma mensagem, como criar um tíquete de ajuda com base no conteúdo de uma postagem de canal.

:::image type="content" source="assets\images\overview-messaging.png" alt-text="Representação conceitual de como são as extensões de mensagens no cliente Teams de mensagens." border="false":::

   :::column-end:::

   :::column span="":::

### <a name="webhooks"></a>Webhooks

**Comunicar-se com aplicativos** [externos: os webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) de entrada são uma maneira simples de enviar notificações automaticamente de outro aplicativo para um Teams canal. Com [webhooks de saída](webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks), mensagem seu serviço Web com um @mention.

:::image type="content" source="assets/images/overview-connectors.png" alt-text="Representação conceitual de como os conectores são no Teams cliente." border="false":::

   :::column-end:::
:::row-end:::

:::row:::

   :::column span="":::

### <a name="microsoft-graph-for-teams"></a>Microsoft Graph para Teams

**Utilize Teams** dados : [a API](https://docs.microsoft.com/graph/teams-concept-overview) do Microsoft Graph para Teams fornece acesso a informações sobre equipes, canais, usuários e mensagens que podem ajudá-lo a criar ou aprimorar recursos para seu aplicativo.

:::image type="content" source="assets/images/overview-graph.png" alt-text="Representação conceitual da API Graph microsoft para Teams." border="false":::

   :::column-end:::

   :::column span="":::
   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="start-building"></a>Iniciar a criação

Familiarize-se rapidamente com a criação para Teams configurando seu ambiente e criando um aplicativo simples.

> [!div class="nextstepaction"]
> [Desenvolver seu primeiro aplicativo](build-your-first-app/build-first-app-overview.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="integrate-with-teams"></a>Integrar com o Teams

Mesclar os recursos que os usuários adoram sobre um aplicativo Web, serviço ou sistema existente com os recursos colaborativos Teams.

> [!div class="nextstepaction"]
> [Integrar um aplicativo existente](samples/integrating-web-apps.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="a-little-code-goes-a-long-way"></a>Um pouco de código é muito longo

Você não precisa ser um programador especialista para criar um aplicativo Teams excelente. Experimente uma das várias soluções de código baixo.

> [!div class="nextstepaction"]
> [Criar um aplicativo de código baixo](samples/teams-low-code-solutions.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="get-ideas-for-your-app"></a>Obter ideias para seu aplicativo

Procurando inspiração para desenvolvimento de aplicativos? Navegue pela nossa lista de cenários reais e soluções do setor com simulações de conceito de alta fidelidade para entender as várias maneiras Teams aplicativos podem ajudar seus usuários.

> [!div class="nextstepaction"]
> [Consulte cenários de aplicativo](https://adoption.microsoft.com/extensibility-look-book/scenarios/)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

## <a name="see-also"></a>Confira também

* [Adicionar um botão Compartilhar para Teams seu site](concepts/build-and-test/share-to-teams.md)
* [Projetar seu Teams aplicativo](concepts/design/design-teams-app-overview.md)
* [Microsoft Teams SDK do cliente JavaScript](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true)
* SDK da Estrutura de Bots para [JavaScript](https://github.com/Microsoft/botbuilder-js) e [.NET](https://github.com/Microsoft/botbuilder-dotnet/)
* [Distribuir seu Teams app](concepts/deploy-and-publish/apps-publish-overview.md)
