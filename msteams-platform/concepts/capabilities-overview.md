---
title: Entenda os recursos do aplicativo
author: heath-hamilton
description: Descrição dos recursos do aplicativo Teams, como Guias, Bots, Extensões de mensagens e Webhooks e conectores; escopo do aplicativo, como aplicativos pessoais e compartilhados
ms.topic: conceptual
ms.localizationpriority: high
ms.author: lajanuar
ms.date: 09/22/2020
keywords: guias bots extensões de mensagens webhooks conectores
ms.openlocfilehash: 53ee8ffb0fdf51b5c4069cc79ff7022dbc46777d
ms.sourcegitcommit: 3d7b34e7032b6d379eca8f580d432b365c8be840
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/18/2022
ms.locfileid: "62897967"
---
# <a name="understand-microsoft-teams-app-features"></a>Entenda os recursos do aplicativo Microsoft Teams

Há várias maneiras de estender o Teams para que cada aplicativo seja exclusivo. Um aplicativo do Teams pode se manifestar para um usuário de diferentes maneiras. Os recursos de um aplicativo do Teams incluem:

- Recursos do aplicativo
- Escopo do aplicativo

Por exemplo, um usuário pode interagir com um aplicativo em uma guia de tela para fazer uma atividade ou pode optar por fazer o mesmo usando um bot de conversa. Você pode usar apenas uma funcionalidade, como um webhook, enquanto outras têm mais de um recurso para oferecer várias opções aos usuários.

Esses recursos pode existir em escopos diferentes. Por exemplo, seu aplicativo pode exibir dados em um local compartilhado central, ou seja, a guia e apresentar essas mesmas informações por meio de uma interface de conversa pessoal, ou seja, o bot.

## <a name="app-capabilities"></a>Recursos do aplicativo

Para poder estender seu aplicativo, você deve entender todos os recursos principais e os pontos de entrada que funcionam em um espaço colaborativo. Você pode experimentar os pontos de extensão para criar seus aplicativos. Componentes importantes do projeto do aplicativo ajudam você a configurar corretamente a página do aplicativo.

Seus aplicativos do Teams têm um ou todos os seguintes recursos principais:

:::row:::
   :::column span="":::
### <a name="personal-apps"></a>Aplicativos pessoais

Um [aplicativo pessoal](../concepts/design/personal-apps.md) é um espaço dedicado ou bot para ajudar os usuários a se concentrarem em suas próprias tarefas ou exibir atividades importantes para eles.

   :::column-end:::

   :::column span="":::

:::image type="content" source="../assets/images/overview-personal-apps-2021.png" alt-text="Representação conceitual de como são as aplicações pessoais no cliente do Teams." border="false":::

   :::column-end:::

:::row-end:::

:::row:::
   :::column span="":::

### <a name="tabs"></a>Guias

Exiba seu conteúdo baseado na Web em uma [aba](../tabs/what-are-tabs.md) em que as pessoas possam discutir e trabalhar em conjunto.

   :::column-end:::

   :::column span="":::

:::image type="content" source="../assets/images/overview-channel-chat-apps-2021.png" alt-text="Representação conceitual de como são as abas no cliente do Teams." border="false":::

   :::column-end:::

:::row-end:::

:::row:::
   :::column span="":::

### <a name="bots"></a>Bots

As conversas geralmente resultam na necessidade de fazer algo (gerar um pedido, revisar meu código, verificar o status do tíquete e assim por diante). Um [bot](../bots/what-are-bots.md) pode dar início a este tipo de fluxo de trabalho dentro do Teams.

   :::column-end:::

   :::column span="":::

:::image type="content" source="../assets/images/overview-bots-2021.png" alt-text="Representação conceitual de como são os bots no cliente do Teams." border="false":::

   :::column-end:::

:::row-end:::

:::row:::

   :::column span="":::

### <a name="messaging-extensions"></a>Extensões de mensagens

Com as [extensões de mensagens](../messaging-extensions/what-are-messaging-extensions.md), você pode compartilhar rapidamente informações externas em uma conversa. Você também pode agir em uma mensagem, como criar um tíquete de ajuda com base no conteúdo de uma postagem de canal.

   :::column-end:::

   :::column span="":::

:::image type="content" source="../assets/images/overview-messaging-extensions-2021.png" alt-text="Representação conceitual de como são as extensões de mensagens no cliente do Teams." border="false":::

   :::column-end:::
:::row-end:::

:::row:::

   :::column span="":::

### <a name="meeting-extensions"></a>Extensões de reunião

Há algumas opções para [incorporar seu aplicativo na experiência de chamada do Teams](../apps-in-teams-meetings/design/designing-apps-in-meetings.md).

   :::column-end:::

   :::column span="":::

:::image type="content" source="../assets/images/overview-meeting-extensions-2021.png" alt-text="Representação conceitual de como são as extensões de reuniões no cliente do Teams." border="false":::

   :::column-end:::
:::row-end:::

:::row:::

   :::column span="":::

### <a name="webhooks-and-connectors"></a>Webhooks e conectores

[Webhooks de entrada](../webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) são uma maneira simples de enviar notificações automaticamente de outro aplicativo para um canal do Teams. Com os [webhooks de saída](../webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks), envie uma mensagem a seu serviço web com uma @menção.

   :::column-end:::

   :::column span="":::

:::image type="content" source="../assets/images/overview-connectors.png" alt-text="Representação conceitual de como são os conectores no cliente do Teams." border="false":::

   :::column-end:::
:::row-end:::

:::row:::

   :::column span="":::

### <a name="microsoft-graph-for-teams"></a>Microsoft Graph para o Teams

A [API do Microsoft Graph para Teams](/graph/teams-concept-overview) fornece acesso a informações sobre equipes, canais, usuários e mensagens que podem ajudá-lo a criar ou aprimorar recursos para seu aplicativo (como, por exemplo, notificações ricas).

   :::column-end:::

> [!NOTE]
> A loja do Teams evoluiu:
> 
> Anteriormente, os aplicativos LOB eram atualizados selecionando as reticências no bloco. Com a experiência atualizada da loja do Teams, agora você pode atualizar os aplicativos LOB fazendo logon no [Centro de Administrador do Teams](https://admin.teams.microsoft.com).

:::image type="content" source="../assets/images/overview-graph.png" alt-text="Representação conceitual do Microsoft Graph API para o Teams." border="false":::

   :::column-end:::
:::row-end:::

## <a name="choose-the-correct-scope-for-your-app"></a>Escolha o escopo correto para o seu aplicativo

Você pode escolher o escopo do aplicativo a partir dos seguintes:

- Experiência de aplicativo pessoal: um aplicativo pessoal é um espaço dedicado ou bot para ajudar os usuários a se concentrarem em suas próprias tarefas ou exibir atividades importantes para eles.
- Experiência de aplicativo compartilhado: equipe, canal e chat são espaços de colaboração. Os aplicativos nesses contextos estão disponíveis para todos nesse espaço. Os espaços de colaboração normalmente se concentram em fluxos de trabalho para as interações do seu aplicativo ou para desbloquear novas interações sociais.

## <a name="see-also"></a>Confira também

* [Criar aplicativos para o Teams](../overview.md)
* [Crie seu primeiro aplicativo do Microsoft Teams ](../build-your-first-app/build-first-app-overview.md)