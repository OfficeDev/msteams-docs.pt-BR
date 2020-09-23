---
title: Noções básicas sobre recursos de aplicativos do teams
author: heath-hamilton
description: Recursos do teams app explicados
ms.topic: conceptual
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: e7a6fe61fa5c74547ce20cc895afdd044f35e512
ms.sourcegitcommit: 1aa0b172931d0f81db346452788c41dc4a6717b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48210097"
---
# <a name="understanding-teams-app-capabilities"></a>Noções básicas sobre recursos de aplicativos do teams

Os *recursos* são os pontos de extensão para a criação de aplicativos na plataforma do Microsoft Teams.

Há várias maneiras de estender o Microsoft Teams, portanto, todos os aplicativos são exclusivos: alguns têm apenas um recurso (como um webhook), enquanto outros têm alguns para fornecer opções aos usuários. Por exemplo, seu aplicativo pode exibir dados em um local central (Tab) e apresentar as mesmas informações por meio de uma interface de conversação (bot).

O aplicativo do Microsoft Teams pode ter um ou todos os seguintes recursos principais:

* [Guias](../tabs/what-are-tabs.md)
* [Extensões de Mensagens](../messaging-extensions/what-are-messaging-extensions.md)
* [Bots](../bots/what-are-bots.md)
* [Webhooks e conectores](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)

O aplicativo também pode aproveitar as vantagens de recursos avançados, como a [API do Microsoft Graph para Teams](https://docs.microsoft.com/graph/teams-concept-overview).

Veja a ilustração a seguir para ter uma ideia de quais recursos fornecerão os recursos que você deseja em seu aplicativo.

:::image type="content" source="../assets/images/capabilities-overview.png" alt-text="Mapa mental que ilustra o que são os recursos do teams app.":::

## <a name="doing-whats-best-for-your-users"></a>Como fazer o melhor para os seus usuários

À medida que você se familiarizar com o desenvolvimento de aplicativos do Teams, começará a entender seus sutilezas. Há mais de uma maneira de Compilar determinados recursos (como coletar entradas do usuário). Por exemplo, você pode inserir um formulário baseado na Web em uma guia usando um `<iframe>` . Você também pode fazer isso em uma guia usando um módulo de tarefa, uma Convenção de interface do usuário do Microsoft Teams, para uma experiência mais nativa que os usuários possam preferir.

A escolha dos recursos e design certos é para baixo na [compreensão inicial dos casos de uso do público](../concepts/design/understand-use-cases.md).
