---
title: Compreender os recursos do aplicativo
author: heath-hamilton
description: Recursos de aplicativo do Teams explicados
ms.topic: conceptual
localization_priority: Normal
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: f670f1f7b3db01f89fab4335c33f92e02cad1d9a
ms.sourcegitcommit: a732789190f59ec1f3699e8ad2f06387e8fe1458
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2021
ms.locfileid: "52058485"
---
# <a name="understand-microsoft-teams-app-capabilities"></a>Entender os recursos do aplicativo do Microsoft Teams

Extensibilidade ou pontos de entrada são maneiras diferentes nas quais um aplicativo pode se manifesto para um usuário. Por exemplo, um usuário pode interagir com um aplicativo em uma guia de tela para fazer uma atividade ou pode optar por fazer o mesmo usando um bot de conversa. Os vários recursos usados para criar seu aplicativo do Teams permitem que você aumente seu escopo de uso.

Há várias maneiras de estender o Teams, portanto, cada aplicativo é exclusivo. Alguns têm apenas um recurso, como um webhook, enquanto outros têm mais de um recurso para dar aos usuários várias opções. Por exemplo, seu aplicativo pode exibir dados em  um local central, ou seja, a guia e apresentar essas mesmas informações por meio de uma interface de conversa, ou seja, o **bot**.

## <a name="app-capabilities"></a>Recursos do aplicativo

Seu aplicativo do Teams tem um ou todos os seguintes recursos principais:

* [Guias](../tabs/what-are-tabs.md)
* [Extensões de Mensagens](../messaging-extensions/what-are-messaging-extensions.md)
* [Bots](../bots/what-are-bots.md)
* [Webhooks e conectores](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)

Seu aplicativo também pode tirar proveito dos recursos avançados, como a [API do Microsoft Graph para o Teams.](https://docs.microsoft.com/graph/teams-concept-overview)

A ilustração a seguir fornece uma ideia de quais recursos fornecerão os recursos que você deseja em seu aplicativo.

:::image type="content" source="../assets/images/capabilities-overview.png" alt-text="Mapeie ilustrando quais são os recursos do aplicativo do Teams.":::

## <a name="always-consider-your-user"></a>Sempre considere seu usuário

À medida que você se familiariza com o desenvolvimento de aplicativos do Teams, você compreende seus principais fundamentos. Você entende que há mais de uma maneira de criar determinados recursos. Nesses cenários, considere como você pode fornecer uma experiência mais nativa ao usuário.
Por exemplo, você pode coletar a entrada do usuário em um formulário criado como uma guia no aplicativo. Você também pode fazer isso usando um módulo de tarefa sem alternar exibições e interromper o fluxo de trabalho do usuário. É importante escolher pontos de extensão que forneçam menor desvio do fluxo regular de trabalho de um usuário.

## <a name="see-also"></a>Confira também

- [Criar aplicativos para o Teams](../overview.md)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Pontos de entrada do aplicativo Teams](../concepts/extensibility-points.md)
