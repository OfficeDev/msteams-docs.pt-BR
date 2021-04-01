---
title: Criar aplicativos para a plataforma Microsoft Teams
author: heath-hamilton
description: Obter uma visão geral de como os desenvolvedores podem estender os recursos do Microsoft Teams com aplicativos personalizados.
ms.topic: overview
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: e40d2b0d8b0d12e6275b97f79d103310d22f9720
ms.sourcegitcommit: 3bd2627b7a334568f61ccc606395e3d89aa521d9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/31/2021
ms.locfileid: "51475925"
---
# <a name="build-apps-for-microsoft-teams"></a>Crie aplicativos para o Microsoft Teams

Os aplicativos do Microsoft Teams trazem informações importantes, ferramentas comuns e processos confiáveis para onde as pessoas coletam, aprendem e trabalham cada vez mais.

Aplicativos são como você estende o Teams para se ajustar às suas necessidades. Crie algo novo para o Teams ou integre um aplicativo existente.

> [!div class="nextstepaction"]
> [Iniciar aqui](build-your-first-app/build-first-app-overview.md)

## <a name="what-are-teams-apps"></a>O que são aplicativos do Teams?

Os aplicativos do Teams são uma combinação de [recursos](concepts/capabilities-overview.md) e [pontos de entrada.](concepts/extensibility-points.md) Por exemplo, as pessoas podem conversar com o bot (recurso) do seu *aplicativo* em um *canal* (ponto de entrada).

Alguns aplicativos são simples (notificações de envio), enquanto outros são complexos (gerenciar registros de pacientes). Ao planejar seu aplicativo, lembre-se de que o Teams é um hub de colaboração. Os melhores aplicativos do Teams ajudam as pessoas a se expressarem e trabalharem melhor juntas.

:::row:::
   :::column span="":::

### <a name="tabs"></a>Guias

**Obter informações de forma mais conveniente:** às vezes, você só precisa tornar as coisas mais fáceis de encontrar. Exibe uma página da Web importante em [uma guia](tabs/what-are-tabs.md), que fornece uma experiência da Web de tela inteira para conteúdo estático e dinâmico no Teams.

:::image type="content" source="assets/images/overview-tabs.png" alt-text="Representação conceitual de como as guias são no cliente do Teams." border="false":::

   :::column-end:::

   :::column span="":::

### <a name="bots"></a>Bots

**Transformar palavras em ações**: as conversas geralmente resultam na necessidade de fazer algo (gerar um pedido, revisar meu código, verificar o status do tíquete, etc.). Um [bot](bots/what-are-bots.md) pode dar início a esses tipos de fluxos de trabalho dentro do Teams.

:::image type="content" source="assets/images/overview-bots.png" alt-text="Representação conceitual de como os bots são no cliente do Teams." border="false":::

   :::column-end:::

:::row-end:::

:::row:::

   :::column span="":::

### <a name="messaging-extensions"></a>Extensões de mensagens

**Facilita a multitarefa**: Com extensões de mensagens, você pode compartilhar rapidamente informações [externas](messaging-extensions/what-are-messaging-extensions.md)em uma conversa. Você também pode agir em uma mensagem, como criar um tíquete de ajuda com base no conteúdo de uma postagem de canal.

:::image type="content" source="assets\images\overview-messaging.png" alt-text="Representação conceitual de como são as extensões de mensagens no cliente do Teams." border="false":::

   :::column-end:::

   :::column span="":::

### <a name="webhooks"></a>Webhooks

**Comunicar-se com aplicativos** externos : [Webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) de entrada são uma maneira simples de enviar notificações automaticamente de outro aplicativo para um canal do Teams. Com [webhooks de saída](webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks), mensagem seu serviço Web com um @mention.

:::image type="content" source="assets/images/overview-connectors.png" alt-text="Representação conceitual de como os conectores são no cliente do Teams." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
   :::column-end:::
:::row-end:::

### <a name="microsoft-graph-for-teams"></a>Microsoft Graph para Teams

**Use dados do Teams**: A [API do Microsoft Graph](https://docs.microsoft.com/graph/teams-concept-overview) para Teams fornece acesso a informações sobre equipes, canais, usuários e mensagens que podem ajudá-lo a criar ou aprimorar recursos para seu aplicativo.

:::image type="content" source="assets/images/overview-graph.png" alt-text="Representação conceitual da API do Microsoft Graph para o Teams." border="false":::

   :::column-end:::
   :::column span="":::

:::row:::
   :::column span="2":::
   :::column-end:::
:::row-end:::

## <a name="build-solutions-for-microsoft-teams-apps"></a>Criar soluções para aplicativos do Microsoft Teams
 
A Microsoft oferece um livro de aparência extensibilidade, uma biblioteca de cenários para aplicativos do Teams organizados pelo setor. Este livro ajuda você a criar aplicativos na plataforma teams e a entender diferentes cenários possíveis usando vários recursos de plataforma do Teams. Os cenários do look book começam com um problema de negócios, as personas envolvidas com seus desafios e terminam com uma solução de aplicativo do Teams que aborda as necessidades comerciais.

Cada cenário nesta biblioteca é acompanhado por um conjunto de simulações de conceito de design de alta fidelidade, que podem servir de inspiração para projetar seus aplicativos e melhorar a experiência do usuário. Além disso, o look book destaca as práticas recomendadas de design e arquitetura seguidas na criação de cada aplicativo. Para obter mais informações, consulte o livro de aparência extensibilidade. Para obter mais informações, consulte [extensibility look book](https://adoption.microsoft.com/extensibility-look-book/scenarios/). 

## <a name="start-building"></a>Iniciar a criação

Familiarize-se rapidamente com a criação do Teams criando um aplicativo simples e adicionando alguns recursos comumente usados.

> [!div class="nextstepaction"]
> [Crie seu primeiro aplicativo agora](build-your-first-app/build-first-app-overview.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="integrate-with-teams"></a>Integrar com o Teams

Mesclar os recursos que os usuários adoram sobre um aplicativo Web, serviço ou sistema existente com os recursos colaborativos do Teams.

> [!div class="nextstepaction"]
> [Integrar um aplicativo existente](samples/integrating-web-apps.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="a-little-code-goes-a-long-way"></a>Um pouco de código é muito longo

Você não precisa ser um programador especializado para criar um ótimo aplicativo do Teams. Experimente uma das várias soluções de código baixo.

> [!div class="nextstepaction"]
> [Criar um aplicativo de código baixo](samples/teams-low-code-solutions.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

## <a name="resources"></a>Recursos

* [Adicionar um botão Compartilhar para o Teams ao seu site](concepts/build-and-test/share-to-teams.md)
* [Projetar seu aplicativo do Teams](concepts/design/design-teams-app-overview.md)
* [SDK do cliente JavaScript do Microsoft Teams](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true)
* SDK da Estrutura de Bots para [JavaScript](https://github.com/Microsoft/botbuilder-js) e [.NET](https://github.com/Microsoft/botbuilder-dotnet/)
* [Publicar seu aplicativo do Teams](concepts/deploy-and-publish/overview.md)
