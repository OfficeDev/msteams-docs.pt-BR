---
title: Noções básicas sobre os recursos do aplicativo teams
author: heath-hamilton
description: Recursos de aplicativo do Teams explicados
ms.topic: conceptual
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: 5336b36b52cf81be414f18ccaaf9e235c079e626
ms.sourcegitcommit: 49d1ecda14042bf3f368b14c1971618fe979b914
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51034702"
---
# <a name="understanding-teams-app-capabilities"></a>Noções básicas sobre os recursos do aplicativo teams

*Os* recursos são os pontos de extensão para a criação de aplicativos na plataforma do Microsoft Teams.

Há várias maneiras de estender o Teams, portanto, cada aplicativo é exclusivo: Alguns têm apenas um recurso (como um webhook), enquanto outras têm algumas para dar opções aos usuários. Por exemplo, seu aplicativo pode exibir dados em um local central (guia) e apresentar essas mesmas informações por meio de uma interface de conversa (bot).

Seu aplicativo do Teams tem um ou todos os seguintes recursos principais:

* [Guias](../tabs/what-are-tabs.md)
* [Extensões de Mensagens](../messaging-extensions/what-are-messaging-extensions.md)
* [Bots](../bots/what-are-bots.md)
* [Webhooks e conectores](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)

Seu aplicativo também pode tirar proveito dos recursos avançados, como a [API do Microsoft Graph para o Teams.](https://docs.microsoft.com/graph/teams-concept-overview)

Confira a ilustração a seguir para obter uma ideia de quais recursos forneceriam os recursos que você deseja em seu aplicativo.

:::image type="content" source="../assets/images/capabilities-overview.png" alt-text="Mapeie ilustrando quais são os recursos do aplicativo do Teams.":::

## <a name="doing-whats-best-for-your-users"></a>Fazendo o que é melhor para seus usuários

Ao se familiarizar com o desenvolvimento de aplicativos do Teams, você começará a entender suas sutilezas. Há mais de uma maneira de criar determinados recursos (como coletar entrada do usuário). Por exemplo, você pode inserir um formulário baseado na Web em uma guia usando um `<iframe>` . Você também pode fazer isso em uma guia usando um módulo de tarefa, uma convenção de interface do usuário do Teams, para uma experiência mais nativa que seus usuários podem preferir.

Escolher os recursos e o design certos se resume a entender primeiro os casos de uso [do seu público.](../concepts/design/understand-use-cases.md)
