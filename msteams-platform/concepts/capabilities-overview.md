---
title: Compreender os recursos do aplicativo
author: heath-hamilton
description: Teams de aplicativos explicados
ms.topic: conceptual
localization_priority: Normal
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: f8e44496154f3df638737bd91d1ee983f7791414
ms.sourcegitcommit: 6a41c529a423c81a184c7a79125dbaaed0179788
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/26/2021
ms.locfileid: "53585974"
---
# <a name="understand-microsoft-teams-app-capabilities"></a>Compreender Microsoft Teams recursos do aplicativo

Extensibilidade ou pontos de entrada são maneiras diferentes nas quais um aplicativo pode se manifesto para um usuário. Por exemplo, um usuário pode interagir com um aplicativo em uma guia de tela para fazer uma atividade ou pode optar por fazer o mesmo usando um bot de conversa. Os vários recursos usados para criar seu aplicativo Teams permitem que você aumente seu escopo de uso.

Há várias maneiras de estender Teams, portanto, cada aplicativo é exclusivo. Alguns têm apenas um recurso, como um webhook, enquanto outros têm mais de um recurso para dar aos usuários várias opções. Por exemplo, seu aplicativo pode exibir dados em  um local central, ou seja, a guia e apresentar essas mesmas informações por meio de uma interface de conversa, ou seja, o **bot**.

## <a name="app-capabilities"></a>Recursos do aplicativo

Seu Teams app tem um ou todos os seguintes recursos principais:

* [Guias](../tabs/what-are-tabs.md)
* [Extensões de Mensagens](../messaging-extensions/what-are-messaging-extensions.md)
* [Bots](../bots/what-are-bots.md)
* [Webhooks e conectores](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)

Seu aplicativo também pode tirar proveito dos recursos avançados, como a [API do Microsoft Graph para Teams](/graph/teams-concept-overview).

A ilustração a seguir fornece uma ideia de quais recursos fornecerão os recursos que você deseja em seu aplicativo:

:::image type="content" source="../assets/images/capabilities-overview.png" alt-text="Mapeie ilustrando quais são Teams de aplicativos.":::

## <a name="always-consider-your-user"></a>Sempre considere seu usuário

À medida que você se familiariza com Teams desenvolvimento de aplicativos, você compreende seus principais fundamentos. Você entende que há mais de uma maneira de criar determinados recursos. Nesses cenários, considere como você pode fornecer uma experiência mais nativa ao usuário.
Por exemplo, você pode coletar a entrada do usuário em um formulário criado como uma guia no aplicativo. Você também pode fazer isso usando um módulo de tarefa sem alternar exibições e interromper o fluxo de trabalho do usuário. É importante escolher pontos de extensão que forneçam menor desvio do fluxo regular de trabalho de um usuário.

## <a name="see-also"></a>Confira também

[Criar aplicativos para Teams](../overview.md) 
 [Criar seu primeiro Microsoft Teams app](../build-your-first-app/build-first-app-overview.md)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Pontos de entrada do aplicativo Teams](../concepts/extensibility-points.md)
