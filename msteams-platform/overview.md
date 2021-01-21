---
title: Criar aplicativos para a plataforma do Microsoft Teams
author: heath-hamilton
description: Obter uma visão geral de como os desenvolvedores podem estender os recursos do Microsoft Teams com aplicativos personalizados.
ms.topic: overview
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: 9f043fd5bab441ce88b0e04b4254b925aff25aad
ms.sourcegitcommit: 00c657e3bf57d3b92aca7da941cde47a2eeff4d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "49911881"
---
# <a name="build-apps-for-microsoft-teams"></a>Crie aplicativos para o Microsoft Teams

Os aplicativos do Microsoft Teams trazem informações importantes, ferramentas comuns e processos confiáveis para onde as pessoas se reúnem, aprendem e trabalham cada vez mais.

Os aplicativos são como você estende o Teams para se ajustar às suas necessidades. Crie algo novo para o Teams ou integre um aplicativo existente.

> [!div class="nextstepaction"]
> [Iniciar aqui](build-your-first-app/build-first-app-overview.md)

## <a name="what-are-teams-apps"></a>O que são aplicativos do Teams?

Os aplicativos do Teams são uma combinação [de recursos e](concepts/capabilities-overview.md) pontos de [entrada.](concepts/extensibility-points.md) Por exemplo, as pessoas podem conversar com o *bot* (recurso) do seu aplicativo em um *canal* (ponto de entrada).

Alguns aplicativos são simples (enviar notificações), enquanto outros são complexos (gerenciam registros de pacientes). Ao planejar seu aplicativo, lembre-se de que o Teams é um hub de colaboração. Os melhores aplicativos do Teams ajudam as pessoas a se expressarem e trabalharem melhor juntas.

:::row:::
   :::column span="":::

### <a name="tabs"></a>Guias

**Obter informações de maneira mais conveniente:** às vezes, você só precisa facilitar a sua encontrar. Exibir uma página da Web importante em uma [guia,](tabs/what-are-tabs.md)que fornece uma experiência de tela inteira para conteúdo estático e dinâmico no Teams.

:::image type="content" source="assets/images/overview-tabs.png" alt-text="Representação conceitual da aparência das guias no cliente do Teams." border="false":::

   :::column-end:::

   :::column span="":::

### <a name="bots"></a>Bots

**Transforme palavras em ações:** as conversas geralmente resultam na necessidade de fazer algo (gerar uma ordem, revisar meu código, verificar o status do tíquete etc.). Um [bot](bots/what-are-bots.md) pode dar início a esses tipos de fluxos de trabalho no Teams.

:::image type="content" source="assets/images/overview-bots.png" alt-text="Representação conceitual da aparência dos bots no cliente do Teams." border="false":::

   :::column-end:::

:::row-end:::

:::row:::

   :::column span="":::

### <a name="messaging-extensions"></a>Extensões de mensagens

**Facilitar a multitarefa:** com extensões de mensagens, você pode compartilhar rapidamente informações [externas](messaging-extensions/what-are-messaging-extensions.md)em uma conversa. Você também pode agir em uma mensagem, como criar um tíquete de ajuda com base no conteúdo de uma postagem de canal.

:::image type="content" source="assets\images\overview-messaging.png" alt-text="Representação conceitual da aparência das extensões de mensagens no cliente do Teams." border="false":::

   :::column-end:::

   :::column span="":::

### <a name="webhooks"></a>Webhooks

**Comunicar-se com aplicativos** [externos: os webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) de entrada são uma maneira simples de enviar automaticamente notificações de outro aplicativo para um canal do Teams. Com [webhooks de saída,](webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks)mensagem seu serviço Web com um @mention.

:::image type="content" source="assets/images/overview-connectors.png" alt-text="Representação conceitual da aparência dos conectores no cliente do Teams." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="microsoft-graph-for-teams"></a>Microsoft Graph para Teams

**Utilize dados do Teams:** a API do [Microsoft Graph](https://docs.microsoft.com/graph/teams-concept-overview) para Teams fornece acesso a informações sobre equipes, canais, usuários e mensagens que podem ajudá-lo a criar ou aprimorar recursos para seu aplicativo.

:::image type="content" source="assets/images/overview-graph.png" alt-text="Representação conceitual da API do Microsoft Graph para o Teams." border="false":::

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="start-building"></a>Começar a construir

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

   Combinar os recursos que os usuários gostam de um aplicativo Web, serviço ou sistema existente com os recursos colaborativos do Teams.

   > [!div class="nextstepaction"]
   > [Integrar um aplicativo existente](samples/integrating-web-apps.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="a-little-code-goes-a-long-way"></a>Um pouco de código faz um longo caminho

   Você não precisa ser um programador especializado para criar um ótimo aplicativo do Teams. Experimente uma das várias soluções de código baixo.

   > [!div class="nextstepaction"]
   > [Criar um aplicativo de código baixo](samples/teams-low-code-solutions.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

## <a name="resources"></a>Recursos

* [Adicionar um botão Compartilhar com o Teams ao seu site](concepts/build-and-test/share-to-teams.md)
* [Projetar seu aplicativo teams](concepts/design/design-teams-app-overview.md)
* [SDK do cliente JavaScript do Microsoft Teams](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true)
* SDK do Bot Framework para [JavaScript](https://github.com/Microsoft/botbuilder-js) e [.NET](https://github.com/Microsoft/botbuilder-dotnet/)
* [Publicar seu aplicativo do Teams](concepts/deploy-and-publish/overview.md)
