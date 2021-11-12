---
title: Pontos de entrada para os aplicativos do Teams
author: heath-hamilton
description: Descreve pontos de entrada para seu aplicativo, como equipe, canal e chat na experiência pessoal e compartilhada do aplicativo
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: lajanuar
ms.openlocfilehash: 2dd2670787c3da9140b5798db3e7d28b30271f70
ms.sourcegitcommit: 781f34af2a95952bf437d0b7236ae995f4e14a08
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2021
ms.locfileid: "60948415"
---
# <a name="entry-points-for-teams-apps"></a>Pontos de entrada para os aplicativos do Teams

A Teams oferece um conjunto flexível de pontos de entrada, como equipe, canal e chat, onde as pessoas podem descobrir e usar seu aplicativo. Seu aplicativo pode ser tão simples quanto incorporar conteúdo existente da Web em uma guia ou um aplicativo com várias facetas com o qual os usuários interagem em vários contextos.
Os aplicativos mais bem-sucedidos são nativos Teams, portanto, escolha os pontos de entrada do aplicativo com cuidado.

## <a name="shared-app-experiences"></a>Experiências de aplicativo compartilhado

Equipe, canal e chat são espaços de colaboração. Os aplicativos nesses contextos estão disponíveis para todos nesse espaço. Os espaços de colaboração geralmente se concentram em fluxos de trabalho adicionais ou desbloqueando novas interações sociais.

A lista a seguir mostra como Teams recursos do aplicativo são comumente usados em contextos colaborativos:

* As [**Guias**](~/tabs/what-are-tabs.md) oferecem uma experiência da Web inserida em tela inteira configurada para a equipe, o canal ou o chat em grupo. Todos os membros interagem com o mesmo conteúdo baseado na Web, portanto, uma experiência de aplicativo de página única sem estado é típica.

* As [**extensões e mensagens**](~/messaging-extensions/what-are-messaging-extensions.md) são atalhos para inserir conteúdo externo em uma conversa ou fazer ações em mensagens sem sair do Teams. [A desarmagem de](~/messaging-extensions/how-to/link-unfurling.md) link fornece conteúdo rico ao compartilhar conteúdo de uma URL comum.

* [**Os bots**](~/bots/what-are-bots.md) interagem com os membros da conversa por meio de chat e respondendo a eventos, como adicionar um novo membro ou renomear um canal. 
   > [!NOTE]
   > As conversas com um bot nesses contextos ficam visíveis para todos os membros da equipe, canal ou grupo, portanto, as conversas bot devem ser relevantes para todos.

* Os [**webhooks e conectores**](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md) permitem que um serviço externo poste mensagens em uma conversa e os usuários enviem mensagens para um serviço.

* A [**API REST do Microsoft Graph**](/graph/teams-concept-overview) para obter dados sobre equipes, canais e chats em grupo para ajudar a automatizar e gerenciar processos do Teams.

## <a name="personal-app-experiences"></a>Experiências de aplicativo pessoal

Os [aplicativos pessoais](../concepts/design/personal-apps.md) se concentram nas interações com um único usuário. A experiência nesse contexto é exclusiva para cada usuário.

A lista a seguir mostra como Teams recursos são comumente usados em contextos pessoais:

* Os [**bots**](~/bots/what-are-bots.md) mantém conversas individuais com um usuário. Bots que exigem conversas de vários turnos ou fornecem notificações relevantes apenas para um usuário específico são mais adequados em aplicativos pessoais.

* [**As guias**](~/tabs/what-are-tabs.md) fornecem uma experiência da Web incorporada em tela inteira que é significativa para o usuário que está olhando para ela.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Compreender casos de uso](../concepts/design/understand-use-cases.md)

## <a name="see-also"></a>Confira também

* [Teams de design de aplicativo](../concepts/design/design-teams-app-overview.md) <br>
* [Criar seu primeiro Microsoft Teams app](../build-your-first-app/build-first-app-overview.md)