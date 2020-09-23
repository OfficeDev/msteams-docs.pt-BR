---
title: Criar aplicativos para a plataforma do Microsoft Teams
author: heath-hamilton
description: Visão geral de como os desenvolvedores podem estender e personalizar os recursos do Microsoft Teams com aplicativos personalizados.
ms.topic: overview
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: c430add71e7c23a44a552270c5e3c1bacbe650e4
ms.sourcegitcommit: 1aa0b172931d0f81db346452788c41dc4a6717b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48209785"
---
# <a name="build-apps-for-microsoft-teams"></a>Criar aplicativos para o Microsoft Teams

Os aplicativos do Microsoft Teams trazem informações importantes, ferramentas comuns e processos confiáveis para o local em que as pessoas coletam, aprendem e funcionam cada vez.

Os aplicativos são como estender o Microsoft Teams para atender às suas necessidades. Crie uma marca de algo novo para o Microsoft Teams ou integre um aplicativo existente.

## <a name="what-are-teams-apps"></a>O que são aplicativos do teams?

Os aplicativos do teams são uma combinação de [recursos](concepts/capabilities-overview.md) e [pontos de entrada](concepts/extensibility-points.md). Por exemplo, as pessoas podem bater papo com o *bot* do seu aplicativo (recurso) em um *canal* (ponto de entrada).

Alguns aplicativos são simples (notificações de envio), enquanto outros são complexos (gerenciar registros de pacientes). Ao planejar seu aplicativo, lembre-se de que o Microsoft Teams é um hub de colaboração. Os melhores aplicativos do teams ajudam as pessoas a se expressarem e trabalhem melhor juntos.

:::row:::
   :::column span="":::

### <a name="tabs"></a>Guias

**Obter informações de forma mais conveniente**: às vezes você só precisa fazer coisas mais fáceis de encontrar. Exibir uma página da Web importante em uma [guia](tabs/what-are-tabs.md), que oferece uma experiência de tela inteira para conteúdo estático e dinâmico no Teams.

:::image type="content" source="assets/images/overview-tabs.png" alt-text="Representação conceitual da aparência das guias no cliente do teams." border="false":::

   :::column-end:::
   :::column span="":::

### <a name="messaging-extensions"></a>Extensões de mensagens

Facilitar **a multitarefas**: com [extensões de mensagens](messaging-extensions/what-are-messaging-extensions.md), você pode compartilhar rapidamente informações externas em uma conversa. Você também pode agir em uma mensagem, como criar um tíquete de ajuda com base no conteúdo de uma postagem de canal.

:::image type="content" source="assets\images\overview-messaging.png" alt-text="Representação conceitual da aparência das extensões de mensagens no cliente do teams." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="bots"></a>Bots

**Transforme as palavras em ações**: as conversas freqüentemente resultam na necessidade de fazer algo (gerar um pedido, analisar meu código, verificar o status do tíquete, etc.). Um [bot](bots/what-are-bots.md) pode disparar esses tipos de fluxos de trabalho no Microsoft Teams.

:::image type="content" source="assets/images/overview-bots.png" alt-text="Representação conceitual da aparência dos bots no cliente do teams." border="false":::

   :::column-end:::
   :::column span="":::

### <a name="webhooks"></a>Webhooks

**Comunicar-se com aplicativos externos**: os [WebHooks de entrada](webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) são uma maneira simples de enviar notificações automaticamente de outro aplicativo para um canal do teams. Com os [WebHooks de saída](webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks), Message Your Web Service com um @mention.

:::image type="content" source="assets/images/overview-connectors.png" alt-text="Representação conceitual da aparência dos conectores no cliente do teams." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="microsoft-graph-for-teams"></a>Microsoft Graph para Teams

**Use os dados do teams**: a [API do Microsoft Graph para Teams](https://docs.microsoft.com/graph/teams-concept-overview) fornece acesso a informações sobre equipes, canais, usuários e mensagens que podem ajudá-lo a criar ou aprimorar recursos para seu aplicativo.

:::image type="content" source="assets/images/overview-graph.png" alt-text="Representação conceitual da API do Microsoft Graph para Teams." border="false":::

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

## <a name="get-started"></a>Introdução

Vá em com nossos tutoriais de primeiro aplicativo ou descubra como integrar e importar aplicativos existentes.

:::row:::
   :::column span="2":::

### <a name="start-building"></a>Começar a criar

   Familiarize-se rapidamente com a compilação para o Microsoft Teams criando um aplicativo simples e adicionando alguns recursos usados com frequência.

   > [!div class="nextstepaction"]
   > [Criar seu primeiro aplicativo agora](build-your-first-app/build-first-app-overview.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

### <a name="integrate-with-teams"></a>Integração com o Teams

   Misturar os recursos que os usuários adoram em um aplicativo Web, serviço ou sistema existente com os recursos de colaboração do teams.

   > [!div class="nextstepaction"]
   > [Integrar um aplicativo existente](samples/integrating-web-apps.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

### <a name="a-little-code-goes-a-long-way"></a>Um pouco de código é muito longo

   Você não precisa ser um programador especialista para criar um grande aplicativo do teams. Tente uma das várias soluções de código baixo.

   > [!div class="nextstepaction"]
   > [Criar um aplicativo de código baixo](samples/teams-low-code-solutions.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="resources"></a>Recursos

* [Adicionar um botão compartilhar ao Teams ao seu site](concepts/build-and-test/share-to-teams.md)
* [Sistema de design fluente](https://fluentsite.z22.web.core.windows.net/)
* [SDK do cliente JavaScript do Microsoft Teams](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true)
* [SDK da estrutura de bot para JavaScript](https://github.com/Microsoft/botbuilder-js) e [SDK da estrutura de bot para .net](https://github.com/Microsoft/botbuilder-dotnet/)
* [Publicar seu aplicativo em uma organização ou AppSource](concepts/deploy-and-publish/overview.md)
