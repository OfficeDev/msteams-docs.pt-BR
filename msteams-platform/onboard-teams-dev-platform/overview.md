---
title: Plataforma de desenvolvedores do Microsoft Teams
author: clearab
description: Visão geral de como os desenvolvedores podem estender e personalizar os recursos do Microsoft Teams usando a plataforma do teams.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 73cbd4f68d8878872147bd412972495de1b5de6e
ms.sourcegitcommit: d3bb4bbcdff9545c9869647dcdbe563a2db868be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2020
ms.locfileid: "47964568"
---
# <a name="building-for-microsoft-teams"></a>Criando o Microsoft Teams

Os aplicativos do Microsoft Teams trazem informações importantes, ferramentas comuns e processos confiáveis para o local em que as pessoas coletam, aprendem e funcionam cada vez.

Os aplicativos são como estender o Microsoft Teams para atender às suas necessidades. Crie uma marca de algo novo para o Microsoft Teams ou integre um aplicativo existente.

## <a name="what-are-teams-apps"></a>O que são aplicativos do teams?

As pessoas descobrem e usam aplicativos do teams por meio de um conjunto de [recursos](capabilities-overview.md)de plataforma.

Alguns aplicativos são simples (notificações de envio), enquanto outros são complexos (exibir registros de pacientes). Ao planejar seu aplicativo, lembre-se de que o Microsoft Teams é um hub de colaboração. Os melhores aplicativos do teams ajudam as pessoas a se expressarem e trabalhem melhor juntos.

:::row:::
   :::column span="":::

### <a name="tabs"></a>Guias

**Obter informações de forma mais conveniente**: às vezes você só precisa fazer coisas mais fáceis de encontrar. Exibir uma página da Web importante em uma [guia](../tabs/what-are-tabs.md), que oferece uma experiência de tela inteira para conteúdo estático e dinâmico no Teams.

:::image type="content" source="doc-links/images/overview-tabs.png" alt-text="Representação conceitual da aparência das guias no cliente do teams." border="false":::

   :::column-end:::
   :::column span="":::

### <a name="messaging-extensions"></a>Extensões de mensagens

Facilitar **a multitarefas**: com [extensões de mensagens](../messaging-extensions/what-are-messaging-extensions.md), você pode compartilhar rapidamente informações externas em uma conversa. Você também pode agir em uma mensagem, como criar um tíquete de ajuda com base no conteúdo de uma postagem de canal.

:::image type="content" source="doc-links/images/overview-messaging.png" alt-text="Representação conceitual da aparência das extensões de mensagens no cliente do teams." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="bots"></a>Bots

**Transforme as palavras em ações**: as conversas freqüentemente resultam na necessidade de fazer algo (gerar um pedido, analisar meu código, verificar o status do tíquete, etc.). Um [bot](../bots/what-are-bots.md) pode disparar esses tipos de fluxos de trabalho no Microsoft Teams.

:::image type="content" source="doc-links/images/overview-bots.png" alt-text="Representação conceitual da aparência dos bots no cliente do teams." border="false":::

   :::column-end:::
   :::column span="":::

### <a name="webhooks"></a>Webhooks

**Comunicar-se com aplicativos externos**: os [WebHooks de entrada](../webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) são uma maneira simples de enviar notificações automaticamente de outro aplicativo para um canal do teams. Com os [WebHooks de saída](../webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks), Message Your Web Service com um @mention.

:::image type="content" source="doc-links/images/overview-connectors.png" alt-text="Representação conceitual da aparência dos conectores no cliente do teams." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="microsoft-graph-for-teams"></a>Microsoft Graph para Teams

**Use os dados do teams**: a [API REST do Microsoft Graph para Teams](https://docs.microsoft.com/graph/teams-concept-overview) fornece acesso a informações sobre equipes, canais, usuários e mensagens que podem ajudá-lo a criar ou aprimorar recursos para seu aplicativo.

:::image type="content" source="doc-links/images/overview-graph.png" alt-text="Representação conceitual da API REST do Microsoft Graph para o Teams." border="false":::

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

## <a name="get-started"></a>Introdução

Entre em nossos primeiros tutoriais de aplicativos, descubra como integrar e importar aplicativos existentes ou reserve um tempo para aprender sobre o ciclo de vida do desenvolvimento de aplicativos do teams.

:::row:::
   :::column span="2":::

### <a name="start-building"></a>Começar a criar

   Familiarize-se rapidamente com a compilação para o Microsoft Teams criando um aplicativo simples e adicionando alguns recursos usados com frequência.

   > [!div class="nextstepaction"]
   > [Criar seu primeiro aplicativo agora](build-your-first-app/building-real-world-app.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

### <a name="integrate-with-teams"></a>Integração com o Teams

   Misturar os recursos que os usuários adoram em um aplicativo Web, serviço ou sistema existente com os recursos de colaboração do teams.

   > [!div class="nextstepaction"]
   > [Integrar um aplicativo existente](migrating-web-apps.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

### <a name="a-little-code-goes-a-long-way"></a>Um pouco de código é muito longo

   Você não precisa ser um programador especialista para criar um grande aplicativo do teams. Tente uma das várias soluções de código baixo.

   > [!div class="nextstepaction"]
   > [Criar um aplicativo de código baixo](low-code-solutions.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

### <a name="trust-the-process"></a>Confiar no processo

   Saiba todo o processo de desenvolvimento de plataforma do teams para planejar, projetar, criar e publicar um aplicativo para sua organização ou qualquer pessoa com eficácia.

   > [!div class="nextstepaction"]
   > [Iniciar o planejamento do aplicativo](../concepts/extensibility-points.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

## <a name="resources"></a>Recursos

* [Adicionar um botão compartilhar ao Teams ao seu site](../concepts/build-and-test/share-to-teams.md)
* [Sistema de design fluente](https://fluentsite.z22.web.core.windows.net/)
* [SDK do JavaScript do Microsoft Teams](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true)
* [SDK da estrutura de bot para JavaScript](https://github.com/Microsoft/botbuilder-js) e [SDK da estrutura de bot para .net](https://github.com/Microsoft/botbuilder-dotnet/)
* [Publicar seu aplicativo em uma organização ou AppSource](../concepts/deploy-and-publish/overview.md)
