---
title: Plataforma de desenvolvedor do teams
author: clearab
description: Visão geral de como os desenvolvedores podem estender e personalizar os recursos do Microsoft Teams usando a plataforma do teams.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 4af4d34ffa4581be6e69f6233d3eb356aa6a2a08
ms.sourcegitcommit: 52732714105fac07c331cd31e370a9685f45d3e1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2020
ms.locfileid: "46874881"
---
# <a name="building-for-microsoft-teams"></a>Criando o Microsoft Teams

Os aplicativos do Microsoft Teams trazem informações importantes, ferramentas comuns e processos confiáveis para o local em que as pessoas coletam, aprendem e funcionam cada vez.

Os aplicativos são como estender o Microsoft Teams para atender às suas necessidades. Você pode criar algo novo para o Microsoft Teams ou simplesmente integrar recursos em seus aplicativos e serviços favoritos.

## <a name="what-can-teams-apps-do"></a>O que os aplicativos do teams podem fazer?

As pessoas descobrem e usam aplicativos do teams por meio de um conjunto de [recursos](capabilities-overview.md)de plataforma.

Alguns aplicativos são simples (notificações de envio), enquanto outros são complexos (exibir registros de pacientes). Ao planejar seu aplicativo, lembre-se de que o Microsoft Teams é um hub de colaboração. Os melhores aplicativos do teams ajudam as pessoas a se expressarem e trabalhem melhor juntos.

### <a name="get-information-more-conveniently"></a>Obter informações de forma mais conveniente

Às vezes, você só precisa tornar tudo mais fácil de encontrar. Exibir uma página da Web importante em uma [guia](doc-links/what-are-tabs.md), que oferece uma experiência de tela inteira para conteúdo estático e dinâmico no Teams.

![Representação conceitual da aparência das guias no cliente do teams.](doc-links/images/overview-tabs.png)

### <a name="share-links-without-switching-context"></a>Compartilhar links sem alternar contexto

Receba informações em uma conversa e nunca deixe o Microsoft Teams. Por exemplo, com [extensões de mensagens](doc-links/what-are-messaging-extensions.md) você pode compartilhar conteúdo rico e facilmente digestible de um sistema externo usando a caixa de composição de mensagem.

![Representação conceitual da aparência das extensões de mensagens no cliente do teams](doc-links\images\overview-messaging.png)

### <a name="turn-words-into-actions"></a>Transformar palavras em ações

As conversas geralmente resultam na necessidade de algo (criar um pedido, examinar meu código, etc.). Um [bot](doc-links/what-are-bots.md) pode disparar esses tipos de fluxos de trabalho no Microsoft Teams.

![Representação conceitual da aparência dos bots no cliente do teams](doc-links/images/overview-bots.png)

### <a name="communicate-with-external-apps-and-services"></a>Comunicar-se com aplicativos e serviços externos

Os [WebHooks de entrada](doc-links/what-are-webhooks-and-connectors.md#incoming-webhooks) são uma maneira simples de enviar alertas automaticamente de outro aplicativo para um canal ou chat do Microsoft Teams. Com os [WebHooks de saída](doc-links/what-are-webhooks-and-connectors.md#outgoing-webhooks), você pode enviar uma mensagem ao seu serviço Web com um @mention.

![Representação conceitual da aparência dos conectores no cliente do teams.](doc-links/images/overview-connectors.png)

### <a name="utilize-teams-data"></a>Usar dados do teams

A [API REST do Microsoft Graph para Teams](https://docs.microsoft.com/graph/teams-concept-overview) fornece acesso a informações sobre equipes, canais, usuários e mensagens que podem ajudá-lo a criar ou aprimorar recursos para seu aplicativo.

!["Representação conceitual da API REST do Microsoft Graph para Teams](doc-links/images/overview-graph.png)
  
## <a name="start-building"></a>Começar a criar

   Familiarize-se rapidamente com a compilação para o Microsoft Teams criando um aplicativo simples e adicionando alguns recursos usados com frequência.

   > [!div class="nextstepaction"]
   > [Criar seu primeiro aplicativo agora](build-your-first-app/build-real-world-app.md)

### <a name="bring-it-all-together"></a>Reunir tudo

   Simplifique os processos e fluxos de trabalho para os usuários, combinando os aplicativos Web favoritos da sua organização, serviços e sistemas com recursos colaborativos do teams.

   > [!div class="nextstepaction"]
   > [Integrar um aplicativo existente](doc-links/integrating-web-apps.md)

### <a name="trust-the-process"></a>Confiar no processo

   Entenda todo o processo de desenvolvimento da plataforma do teams para planejar, projetar, criar e publicar um aplicativo para sua organização ou qualquer pessoa com eficácia.

   > [!div class="nextstepaction"]
   > [Iniciar o planejamento do aplicativo](doc-links/extensibility-points.md)

### <a name="no-code-no-worries"></a>Nenhum código, sem preocupação

   Você não precisa ser um programador para compilar um ótimo aplicativo. Criar um aplicativo do teams com pouco ou nenhum código usando a plataforma de alimentação da Microsoft.

   > [!div class="nextstepaction"]
   > [Importar um aplicativo de plataforma de energia](doc-links/importing-custom-microsoft-apps.md)

## <a name="resources"></a>Recursos

* [Adicionar um botão compartilhar ao Teams ao seu site](doc-links/share-to-teams.md)
* [Sistema de design de interface do usuário fluente](https://fluentsite.z22.web.core.windows.net/)
* [SDK do cliente JavaScript do Microsoft Teams](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest)
* [SDK da estrutura de bot para JavaScript](https://github.com/Microsoft/botbuilder-js) e [SDK da estrutura de bot para .net](https://github.com/Microsoft/botbuilder-dotnet/)
