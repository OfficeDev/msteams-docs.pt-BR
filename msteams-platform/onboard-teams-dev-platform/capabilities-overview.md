---
title: Noções básicas sobre recursos de aplicativos do teams
author: heath-hamilton
description: ''
ms.topic: overview
ms.author: heath-hamilton
ms.openlocfilehash: 580d75b648bde1caf0e85647c89635804c91fb70
ms.sourcegitcommit: 9fbc701a9a039ecdc360aefbe86df52b9c3593f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/12/2020
ms.locfileid: "46651848"
---
# <a name="understanding-teams-app-capabilities"></a>Noções básicas sobre recursos de aplicativos do teams

Os *recursos* são os pontos de extensão para a criação de aplicativos na plataforma do Microsoft Teams.

Há várias maneiras de estender o cliente do Microsoft Teams, portanto, todos os aplicativos são exclusivos: alguns têm apenas um recurso (como um webhook), enquanto outros têm alguns para fornecer opções aos usuários. Por exemplo, seu aplicativo pode exibir dados em um local central (Tab) e apresentar as mesmas informações por meio de uma interface de conversação (bot).

O aplicativo do Microsoft Teams pode ter um ou todos os seguintes recursos principais:

* [Guias](../tabs/what-are-tabs.md)
* [Extensões de Mensagens](../messaging-extensions/what-are-messaging-extensions.md)
* [Webhooks e conectores](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)
* [Bots](../bots/what-are-bots.md)

O aplicativo também pode aproveitar as vantagens de recursos avançados, como a [API REST do Microsoft Graph](../graph-api/rsc/resource-specific-consent.md).

Veja a ilustração a seguir para ter uma ideia de quais recursos fornecerão os recursos que você deseja em seu aplicativo.

![Mapa mental que ilustra o que são os recursos do teams app](doc-links/images/capabilities-overview.png)

## <a name="doing-whats-best-for-your-users"></a>Como fazer o melhor para os seus usuários

À medida que você se familiarizar com o desenvolvimento de aplicativos do Teams, começará a entender seus sutilezas. Há mais de uma maneira de Compilar determinados recursos (como coletar entradas do usuário). Por exemplo, você pode inserir um formulário baseado na Web em uma guia usando um `<iframe>` . Você também pode fazer isso em uma guia usando um módulo de tarefa, uma Convenção de interface do usuário do Microsoft Teams, para uma experiência mais nativa que os usuários possam preferir.

Escolher a combinação certa de recursos e convenções, controles e elementos da interface do usuário é a primeira [compreensão dos casos de uso do público](../concepts/design/understand-use-cases.md).

## <a name="learn-more"></a>Saiba mais

* [Iniciar o planejamento do aplicativo](../concepts/extensibility-points.md)
