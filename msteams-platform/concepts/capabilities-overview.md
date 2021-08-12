---
title: Compreender os recursos do aplicativo
author: heath-hamilton
description: Teams de aplicativos explicados
ms.topic: conceptual
localization_priority: Normal
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: 7cb2d042c1b666b6047aa910f3e797e2a59a396d2fd87a37f06fadc04e989d85
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/07/2021
ms.locfileid: "57707117"
---
# <a name="understand-microsoft-teams-app-capabilities"></a>Compreender Microsoft Teams recursos do aplicativo

Extensibilidade ou pontos de entrada são maneiras diferentes nas quais um aplicativo pode se manifesto para um usuário. Por exemplo, um usuário pode interagir com um aplicativo em uma guia de tela para fazer uma atividade ou pode optar por fazer o mesmo usando um bot de conversa. Os vários recursos usados para criar seu aplicativo Teams permite que você aumente seu escopo de uso.

Há várias maneiras de estender Teams, portanto, cada aplicativo é exclusivo. Alguns têm apenas um recurso, como um webhook, enquanto outros têm mais de um recurso para dar aos usuários várias opções. Por exemplo, seu aplicativo pode exibir dados em  um local central, ou seja, a guia e apresentar essas mesmas informações por meio de uma interface de conversa, ou seja, o **bot**.

## <a name="app-capabilities"></a>Recursos do aplicativo

Seus Teams aplicativos têm um ou todos os seguintes recursos principais:

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

## <a name="government-community-cloud-gcc"></a>Nuvem Comunitária Governamental (GCC)

Nuvem da Comunidade Governamental é uma cópia do ambiente comercial com foco no governo. O Departamento de Defesa (DOD) e os prestadores de serviços federais são necessários para atender aos requisitos rigorosos de conformidade e segurança cibernética. Para essa finalidade, GCC-High foi criado para atender às necessidades do DOD e dos prestadores de serviços federais. GCC-High é uma cópia da nuvem do DOD, mas existe em seu próprio ambiente soberana. A nuvem do DOD foi criada apenas para o Departamento de Defesa.

A tabela a seguir inclui Teams recursos e disponibilidade para GCC, GCC-Alta e DOD:

| Recursos   | CCG | GCC-High | DOD |
|-------------|---------|
| Teams aplicativos de propriedade como em aplicativos desenvolvidos internamente | ✔️ App será habilitado se tiver GCC. | ✔️ App será habilitado se tiver GCC-High. | ✔️ App está habilitado se tiver DOD. |
| Aplicativos da Microsoft | ✔️ aplicativos Microsoft compatíveis com GCC | ✔️ aplicativos Microsoft compatíveis com GCC-High | ✔️ microsoft apps compatíveis com o DOD |
| Aplicativos 3p ou de terceiros | ✔️ aplicativos de terceiros estão disponíveis. Desabilitado por padrão e o administrador do locatário usa sua própria discrição para habilita-lo. | ❌ | ❌ |
| Bots | ✔️ | ❌ | ❌ |
| Aplicativos de tabulação personalizados ou lob |  ✔️ | ✔️ | ✔️ |
| Sideload de aplicativos | ✔️ | ❌ | ❌ |
| Bots personalizados ou Lob | ✔️ | ❌ | ❌ |
| Extensões de mensagens personalizadas | ❌ | ❌ | ❌ |
| Conectores personalizados | ❌ | ❌ | ❌ |

A lista a seguir ajuda a identificar a disponibilidade de GCC, GCC-Alta e DOD para os recursos:

* Para aplicativos de terceiros, consulte [aplicativos Web](../samples/integrating-web-apps.md) e [extensibilidade de aplicativos de reunião.](../apps-in-teams-meetings/meeting-app-extensibility.md)
* Para bots, consulte build your first [conversational bot for Teams](../get-started/first-app-bot.md), [designing](../bots/design/bots.md)your Teams bot , add [bots to Microsoft Teams apps](../resources/bot-v3/bots-overview.md), and [bots in Teams](../bots/what-are-bots.md).
* Para fazer sideload de aplicativos, consulte enable your Teams app to be [customized](../concepts/design/enable-app-customization.md), distribute your [Microsoft Teams app](../concepts/deploy-and-publish/apps-publish-overview.md), and Upload your app [in Teams](../concepts/deploy-and-publish/apps-upload.md).
* Para conectores personalizados, consulte [create Office 365 connectors for Teams](../webhooks-and-connectors/how-to/connectors-creating.md).

## <a name="see-also"></a>Confira também

[Criar aplicativos para Teams](../overview.md) 
 [Criar seu primeiro Microsoft Teams app](../build-your-first-app/build-first-app-overview.md)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Pontos de entrada do aplicativo Teams](../concepts/extensibility-points.md)
