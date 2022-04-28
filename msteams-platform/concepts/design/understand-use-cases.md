---
title: Noções básicas sobre os casos de uso do seu aplicativo e os recursos do Teams
author: heath-hamilton
description: Neste artigo, conheça os recursos do aplicativo Microsoft Teams, planeje seu aplicativo Teams, entenda o usuário do aplicativo e suas necessidades, entenda os problemas do usuário que seu aplicativo Teams resolveria, planeje a autenticação do usuário e sua experiência de integração.
ms.topic: conceptual
ms.localizationpriority: high
ms.author: anclear
ms.openlocfilehash: dbed78461fd39f4442c67ac7ec7523ca5cc09ba5
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65104375"
---
# <a name="understand-your-use-cases"></a>Compreender os casos de uso

Na estrutura social colaborativa do Teams, há uma ampla variedade de necessidades dos usuários que você pode resolver com um aplicativo do Teams. Por exemplo, um aplicativo que preencha lacunas para alcançar uma colaboração efetiva é uma ótima opção.

O usuário do aplicativo e os requisitos do aplicativo são as diretrizes básicas que determinam todas as opções de aplicativo que você fará. A criação do design do aplicativo, a seleção de recursos, a determinação do ambiente de build e teste e a distribuição de aplicativos seguem os requisitos do usuário do aplicativo.

Se você vai atender aos requisitos do usuário com seu aplicativo, primeiro precisa entender.

- **Entenda o usuário**:
  - Reconheça problemas do usuário e identifique as soluções para alguns problemas comuns que os usuários enfrentam.
  - Crie seu aplicativo Teams encontrando a combinação certa de recursos do Teams para atender às necessidades do usuário.
  - Entenda os casos de uso para saber como um usuário final interage com seu aplicativo.

- **Entenda o problema**: Resolva o problema principal que seu aplicativo deve resolver.

- **Considere integração**: Identifique os aplicativos e serviços que seu aplicativo requer, como autenticação, Microsoft Graph ou aplicativos Web.

## <a name="microsoft-teams-app-features"></a>Recursos do aplicativo Microsoft Teams

Há várias maneiras de estender o Teams para que cada aplicativo seja exclusivo. Os recursos do aplicativo Teams oferecem:

- [Recursos do aplicativo](#app-capabilities)
- [Escopo do aplicativo](#app-scope)

### <a name="app-capabilities"></a>Recursos do aplicativo

As funcionalidades são as principais funcionalidades que você pode criar em seu aplicativo. Eles também são chamados de pontos de entrada ou extensão porque permitem a integração e a interação.

Seus aplicativos do Teams têm um ou todos os seguintes recursos principais:

:::row:::
   :::column span="":::

#### <a name="personal-apps"></a>Aplicativos pessoais

Um [app pessoal](../../concepts/design/personal-apps.md) é um espaço dedicado ou bot para ajudar os usuários a se concentrarem em suas próprias tarefas ou exibir atividades relevantes.

   :::column-end:::

   :::column span="":::

:::image type="content" source="../../assets/images/overview-personal-apps-2021.png" alt-text="Representação conceitual de como são as aplicações pessoais no cliente do Teams." border="false":::

   :::column-end:::

:::row-end:::

:::row:::
   :::column span="":::

#### <a name="tabs"></a>Guias

Exiba seu conteúdo baseado na Web em uma [aba](../../tabs/what-are-tabs.md) em que as pessoas possam discutir e trabalhar em conjunto.

   :::column-end:::

   :::column span="":::

:::image type="content" source="../../assets/images/overview-channel-chat-apps-2021.png" alt-text="Representação conceitual de como são as abas no cliente do Teams." border="false":::

   :::column-end:::

:::row-end:::

:::row:::
   :::column span="":::

#### <a name="bots"></a>Bots

As conversas geralmente resultam na necessidade de fazer algo (gerar um pedido, revisar o código, verificar o status do tíquete e assim por diante). Um [bot](../../bots/what-are-bots.md) pode dar início a este tipo de fluxo de trabalho dentro do Teams.

   :::column-end:::

   :::column span="":::

:::image type="content" source="../../assets/images/overview-bots-2021.png" alt-text="Representação conceitual de como são os bots no cliente do Teams." border="false":::

   :::column-end:::

:::row-end:::

:::row:::

   :::column span="":::

#### <a name="message-extensions"></a>Extensões de mensagens

Com [extensões de mensagens](../../messaging-extensions/what-are-messaging-extensions.md), você pode pesquisar e compartilhar informações externas. Você também pode agir em uma mensagem, como criar um tíquete de ajuda com base no conteúdo de uma postagem de canal.

   :::column-end:::

   :::column span="":::

:::image type="content" source="../../assets/images/overview-messaging-extensions-2021.png" alt-text="Representação conceitual de como são as extensões de mensagens no cliente do Teams." border="false":::

   :::column-end:::
:::row-end:::

:::row:::

   :::column span="":::

#### <a name="meeting-extensions"></a>Extensões de reunião

Há algumas opções para [incorporar seu aplicativo na experiência de chamada do Teams](../../apps-in-teams-meetings/design/designing-apps-in-meetings.md).

   :::column-end:::

   :::column span="":::

:::image type="content" source="../../assets/images/overview-meeting-extensions-2021.png" alt-text="Representação conceitual de como são as extensões de reuniões no cliente do Teams." border="false":::

   :::column-end:::
:::row-end:::

:::row:::

   :::column span="":::

#### <a name="webhooks-and-connectors"></a>Webhooks e conectores

[Webhooks de entrada](../../webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) são uma maneira simples de enviar notificações automaticamente de outro aplicativo para um canal do Teams. Com [webhooks de saída](../../webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks), você pode enviar uma mensagem ao serviço Web com uma @menção.

   :::column-end:::

   :::column span="":::

:::image type="content" source="../../assets/images/overview-connectors.png" alt-text="Representação conceitual de como são os conectores no cliente do Teams." border="false":::

   :::column-end:::
:::row-end:::

:::row:::

   :::column span="":::

#### <a name="microsoft-graph-for-teams"></a>Microsoft Graph para o Teams

A [API do Microsoft Graph para o Teams](/graph/teams-concept-overview) fornece acesso a informações sobre equipes, canais, usuários e mensagens que ajudam você a criar ou aprimorar recursos para seu aplicativo.

   :::column-end:::

   :::column span="":::

:::image type="content" source="../../assets/images/overview-graph.png" alt-text="Representação conceitual do Microsoft Graph API para o Teams." border="false":::

   :::column-end:::
:::row-end:::

> [!NOTE]
> A loja do Teams evoluiu:
>
> Anteriormente, os aplicativos LOB eram atualizados selecionando as reticências no bloco. Com a experiência atualizada da loja do Teams, agora você pode atualizar os aplicativos LOB fazendo logon no [Centro de Administrador do Teams](https://admin.teams.microsoft.com).

### <a name="app-scope"></a>Escopo do aplicativo

Seu aplicativo pode ter um dos seguintes escopos:

- **Experiência de aplicativo pessoal**: Um aplicativo pessoal é um espaço dedicado ou bot para ajudar os usuários a se concentrarem em suas próprias tarefas ou exibir atividades importantes para eles.
- **Experiência de aplicativo compartilhado**: equipe, canal e chat são espaços de colaboração. Os aplicativos nesses contextos estão disponíveis para todos nesse espaço. Os espaços de colaboração normalmente se concentram em fluxos de trabalho para as interações do seu aplicativo ou para desbloquear novas interações sociais.

Um aplicativo pode existir em escopos diferentes. Por exemplo:

- Seu aplicativo pode exibir dados em um local compartilhado central, ou seja, uma guia.
- Ele também pode apresentar essas mesmas informações por meio de uma interface de conversa pessoal, ou seja, um bot.

Um usuário pode interagir com um aplicativo em uma guia de tela para fazer uma atividade ou pode optar por fazer o mesmo usando um bot de conversa.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Mapear seus casos de uso](../../concepts/design/map-use-cases.md)

## <a name="see-also"></a>Confira também

[Integrar recursos do dispositivo](~/concepts/device-capabilities/device-capabilities-overview.md)
