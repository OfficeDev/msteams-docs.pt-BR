---
title: Pontos de entrada para aplicativos do teams
author: heath-hamilton
description: Descreve como e onde as pessoas usam seu aplicativo no Microsoft Teams.
ms.topic: conceptual
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: 1c68467177fc440993f059133f049f18785374b7
ms.sourcegitcommit: 1aa0b172931d0f81db346452788c41dc4a6717b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48209778"
---
# <a name="entry-points-for-teams-apps"></a>Pontos de entrada para aplicativos do teams

A plataforma de equipe fornece um conjunto flexível de pontos de entrada onde as pessoas podem descobrir e usar seu aplicativo. Seu aplicativo pode ser tão simples quanto a incorporação de um site existente em uma guia pessoal ou um aplicativo multifacetado que os usuários interagem com vários pontos de entrada.

Os aplicativos mais bem-sucedidos se sentem nativos para o Microsoft Teams, portanto, é importante planejar cuidadosamente os pontos de entrada do seu aplicativo.

## <a name="teams-channels-and-group-chats"></a>Equipes, canais e chats de grupo

Equipes, canais e chats de grupo são espaços de colaboração. Os aplicativos que usam esses pontos de entrada estão disponíveis para todos os membros e normalmente se concentram em fluxos de trabalho adicionais ou desbloqueiam as novas interações sociais.

Veja como os recursos de aplicativos do teams são comumente usados em contextos colaborativos:

* As [**guias**](~/tabs/what-are-tabs.md) fornecem uma experiência da Web incorporada em tela cheia configurada para o chat de equipe, canal ou grupo. Todos os membros interagem com o mesmo conteúdo baseado na Web, de forma que uma experiência de aplicativo de página única sem estado seja típica.

* [**As extensões de mensagens**](~/messaging-extensions/what-are-messaging-extensions.md) são atalhos para inserir conteúdo externo em uma conversa ou executar ações em mensagens sem sair do Microsoft Teams. O link Unfurling fornece conteúdo avançado ao compartilhar conteúdo de uma URL comum.

* Os [**bots**](~/bots/what-are-bots.md) interagem com membros da conversa através de chat e respondendo a eventos (como adicionar um novo membro ou renomear um canal). Conversas com um bot nesses contextos são visíveis para todos os membros da equipe, canal ou grupo, portanto, as conversas de bot devem ser relevantes para todos.

* [**WebHooks e conectores**](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md) permitem que um serviço externo publique mensagens em uma conversa e os usuários enviem mensagens para um serviço.

* [**API REST do Microsoft Graph**](https://docs.microsoft.com/graph/teams-concept-overview) para obter dados sobre equipes, canais e chats de grupo para ajudar a automatizar e gerenciar processos de equipes.

## <a name="personal-apps"></a>Aplicativos pessoais

Os [aplicativos pessoais](~/concepts/design/personal-apps.md) se concentram em interações com um único usuário. A experiência desse contexto é exclusiva para cada usuário. Os usuários podem fixar aplicativos pessoais no trilho esquerdo de navegação para acesso rápido.

Veja aqui como os recursos do teams são comumente usados em contextos pessoais:

* Os [**bots**](~/bots/what-are-bots.md) têm conversas de uma em um com um usuário. Os bots que exigem conversas Multiturn ou fornecem notificações relevantes apenas a um usuário específico são mais adequados em contextos pessoais.

* As [**guias**](~/tabs/what-are-tabs.md) fornecem uma experiência Web incorporada em tela inteira que é significativa para usuários individuais.

## <a name="ui-components"></a>Componentes da interface do usuário

Os aplicativos normalmente exibem um ou mais componentes de interface do usuário da equipe padrão. Compilar seu aplicativo usando esses componentes leva a experiências ricas que se sentem nativas para os usuários do Microsoft Teams.

### <a name="cards"></a>Cartões

Os [cartões](~/task-modules-and-cards/what-are-cards.md) são contêineres de interface do usuário definidos por JSON que podem conter texto formatado, mídias, controles (como menus suspensos e botões de opção) e botões que disparam uma ação.

As ações do cartão podem enviar cargas para a API do seu aplicativo, abrir um link, iniciar fluxos de autenticação ou enviar mensagens para conversas. A plataforma do Microsoft Teams suporta vários cartões, incluindo cartões adaptáveis, cartões herói, cartões de miniaturas e muito mais. Você pode combinar conjuntos de cartões e exibi-los em uma lista ou carrossel.

### <a name="task-modules"></a>Módulos de tarefas

Os [módulos de tarefas](~/task-modules-and-cards/what-are-task-modules.md) oferecem experiências modais no Microsoft Teams. Eles são especialmente úteis para iniciar fluxos de trabalho, coletar entradas do usuário ou exibir informações ricas, como vídeos ou painéis do Power BI. Em módulos de tarefa, você pode executar código de front-end personalizado, exibir um `<iframe>` widget ou mostrar um cartão adaptável.

Ao considerar como você deseja criar seu aplicativo, lembre-se de que as modalidades são naturais para que os usuários insiram informações ou concluam tarefas comparadas a uma guia ou uma experiência de bot baseada em conversas.

### <a name="deep-links"></a>Deep links

Seu aplicativo pode criar [links de URL profundas](~/concepts/build-and-test/deep-links.md) para ajudar a navegar pelo seu usuário por meio do seu aplicativo e do cliente do teams. Você pode criar um link profundo para a maioria das entidades no Teams e alguns (como uma nova solicitação de reunião) permitem preencher previamente as informações usando cadeias de caracteres de consulta na URL.

Por exemplo, seu bot de conversa pode enviar uma mensagem para um canal com um link profundo para um módulo de tarefa que resulte em um cartão ser enviado como uma mensagem de um-para-um para um usuário, que por sua vez contém um link profundo para criar uma nova reunião com um usuário específico em uma determinada data/hora. Use links de profunda para se conectar aos vários pontos de extensão disponíveis para seu aplicativo, mantendo sempre o usuário no contexto correto.

### <a name="web-based-content"></a>Conteúdo baseado na Web

[Conteúdo baseado na Web](~/tabs/how-to/create-tab-pages/content-page.md) é uma página da Web que você hospeda, que pode ser incorporada em um módulo de tarefa ou guia.
