---
author: heath-hamilton
description: Práticas recomendadas para integrar aplicativos Web existentes com o Microsoft Teams
ms.author: v-heha
ms.date: 08/26/2020
ms.topic: conceptual
title: Integrar um aplicativo Web com o Microsoft Teams
ms.openlocfilehash: 4671d2277d5eb7c035421c51b1714eccaac06a31
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696483"
---
# <a name="integrate-web-apps-with-teams"></a>Integrar aplicativos Web com o Teams

Você tem um aplicativo Web que você acha que se ajustaria naturalmente aos recursos sociais e colaborativos do Teams? Essas diretrizes podem ajudá-lo a entender como integrar os seguintes tipos de aplicativos:

* **Aplicativos autônomos**: pode ser um aplicativo de página única ou um aplicativo complexo grande que você deseja que as pessoas usem alguns aspectos no Teams.
* **Aplicativos de** colaboração : um aplicativo já criado para os recursos sociais e colaborativos inerentes ao Teams.
* **SharePoint**: uma página do SharePoint que você deseja aparecer no Teams.

Para cada diretriz, você pode ver se ela é aplicável ao seu cenário de integração.

## <a name="get-to-know-teams-platform-capabilities"></a>Conheça os recursos da plataforma Teams

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração, SharePoint*

Seu aplicativo do Teams pode incluir recursos que os usuários querem e podem esperar ao colaborar, mas você pode não estar familiarizado com a terminologia de desenvolvimento do Teams.

|Recursos comuns do aplicativo   |Recursos da plataforma Teams   |
|----------|-----------|
|Página da Web incorporada, homepage ou webview  |[Guias](../tabs/what-are-tabs.md)  |
|Compartilhar atalhos e extensões  |[Extensões de Mensagens](../messaging-extensions/what-are-messaging-extensions.md)  |
|Atalhos de ação e extensões  |[Extensões de Mensagens](../messaging-extensions/what-are-messaging-extensions.md)  |
|Chatbots  |[Bots](../bots/what-are-bots.md) |
|Notificações de canal  |[Bots](../bots/what-are-bots.md)<br/>[Webhooks de entrada](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)<br/>[Conectores de Office 365](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)  |
|Serviços externos de mensagens  |[Bots](../bots/what-are-bots.md)<br/>[Webhooks de saída](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)  |
|Modals  |[Módulos de tarefas](../task-modules-and-cards/what-are-task-modules.md)  |
|Cartões ricos em conteúdo  |[Cartões Adaptáveis](../task-modules-and-cards/what-are-cards.md)  |

## <a name="determine-a-subset-of-functionality"></a>Determinar um subconjunto de funcionalidade

***Cenários de integração**: aplicativos autônomos*

A integração de todos os recursos de um aplicativo existente ao Teams geralmente leva a uma experiência de usuário forçada ou não natural, especialmente em aplicativos maiores. Considere começar com os recursos mais impactáveis e aqueles que se integrarão mais naturalmente com o Teams. Lembre-se de que você sempre pode permitir que os usuários lancem o aplicativo principal e acessem seu conjunto completo de recursos.

Antes de começar qualquer trabalho técnico, faça algum planejamento para seu aplicativo do Teams:

1. [Mapeie os casos de uso do](../concepts/design/map-use-cases.md)aplicativo para os recursos da plataforma teams.
1. [Determine os pontos de entrada do aplicativo.](../concepts/extensibility-points.md) É para uso pessoal, colaboração ou ambos?

## <a name="understand-sharepoint-requirements-and-options"></a>Entender os requisitos e opções do SharePoint

***Cenários de integração**: SharePoint*

Você pode integrar uma página existente do [SharePoint](https://docs.microsoft.com/MicrosoftTeams/teams-standalone-static-tabs-using-spo-sites) como uma guia do Teams. Lembre-se do seguinte:

* Deve ser uma página *moderna* do SharePoint Online
* Somente guias pessoais são suportadas (você não pode integrar sua página como uma guia de canal)

Como alternativa, você pode criar uma guia do Teams [usando a Estrutura do SharePoint](https://docs.microsoft.com/sharepoint/dev/spfx/integrate-with-teams-introduction).

## <a name="aim-towards-multi-tenancy"></a>Aponte para multi-enancy

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração, SharePoint*

Se seu aplicativo for usado por várias organizações, considere a hospedagem de vários locatários que faria com que seu produto fosse escalonável e simplificasse muito a distribuição.

## <a name="review-your-apis"></a>Revisar suas APIs

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração*

Não suponha que as APIs e estruturas de dados existentes do seu aplicativo suportam totalmente o aplicativo quando integrado ao Teams. Talvez seja necessário aumentar isso com informações contextuais sobre o Teams para mapeamento de [identidade,](../concepts/authentication/configure-identity-provider.md)suporte a [vínculos](../concepts/build-and-test/deep-links.md)profundos e [incorporação do Microsoft Graph.](https://docs.microsoft.com/graph/teams-concept-overview)

Saiba mais sobre como obter contexto para sua [guia](../tabs/how-to/access-teams-context.md) ou [bot](../bots/how-to/get-teams-context.md)do Teams.

## <a name="understand-authentication-options"></a>Compreender opções de autenticação

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração, SharePoint*

O Azure Active Directory (AD) é o provedor de identidade do Teams. Se seu aplicativo usa um provedor de identidade diferente, você deve fazer um exercício de mapeamento de identidade ou federar com o Azure AD.

O Teams tem mecanismos de logon único (SSO) com o Azure AD para aplicativos de terceiros e orientações para fluxos de autenticação para outros provedores de identidade usando padrões como OAuth e Open ID Connect (OIDC).

Para páginas do SharePoint, você só pode usar o SSO e não pode adicionar outra ID do Azure AD se quiser que o SSO funcione para outro aplicativo (já que a ID é o aplicativo do SharePoint).

Saiba mais sobre [autenticação no Teams](../concepts/authentication/authentication.md).

## <a name="follow-teams-design-guidelines"></a>Siga as diretrizes de design do Teams

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração*

Em geral, seu aplicativo deve se sentir natural no Teams. Você pode achar que migrar conteúdo de aplicativo existente para uma guia do Teams é suficiente, mas recomendamos que seu aplicativo siga as diretrizes de [design do Teams.](../concepts/design/understand-use-cases.md) Consulte também: [Sistema de Design Fluente](https://fluentsite.z22.web.core.windows.net/).

## <a name="maximize-deep-linking"></a>Maximizar o vínculo profundo

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração, SharePoint*

Quase tudo no Teams pode ser vinculado diretamente a um [link profundo.](../concepts/build-and-test/deep-links.md) Seu aplicativo deve maximizar o uso deles, incluindo vincular mensagens específicas e conteúdo de tabulação. Os links profundos podem realmente unir várias partes de um aplicativo para uma experiência do Teams mais nativa.

## <a name="be-smart-when-messaging-users"></a>Ser inteligente ao enviar mensagens aos usuários

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração, SharePoint*

Considere os tipos de mensagens que seu aplicativo do Teams pode enviar agora e a longo prazo. Se você acha que seu aplicativo terá uma conversa com vários threads, um [bot](../bots/what-are-bots.md) pode oferecer mais flexibilidade do que um [webhook.](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)

Os bots também permitem que você envie mensagens *proativas* para usuários ou canais individuais. Essas são mensagens não prompadas disparadas por um evento externo e não uma mensagem enviada a um bot. (Por exemplo, seu bot pode enviar uma mensagem de boas-vindas quando estiver instalado ou um novo usuário ingressar em um canal.)

O envio de mensagens proativas requer identificadores [específicos](../bots/how-to/conversations/subscribe-to-conversation-events.md)do Teams, você pode capturar essas informações, buscar dados de lista ou perfil de [usuário,](../bots/how-to/get-teams-context.md#fetch-the-roster-or-user-profile)inscrever-se em eventos de conversa ou usar [o Microsoft Graph.](https://docs.microsoft.com/graph/teams-proactive-messaging)

Tenha cuidado para não spam de usuários com mensagens excessivas. Se a funcionalidade do Teams for compatível com ele, considere permitir que os usuários configurem as configurações de notificação para seu aplicativo (por exemplo, "Não me envie mensagens não prompadas.").

## <a name="use-sharepoint-for-file-and-data-storage"></a>Usar o SharePoint para armazenamento de arquivos e dados

***Cenários de integração:** Aplicativos autônomos, aplicativos de colaboração, páginas do SharePoint*

Quando uma equipe é criada, um conjunto de sites do [SharePoint](https://docs.microsoft.com/microsoftteams/sharepoint-onedrive-interact) também é provisionado para dar suporte ao armazenamento de arquivos e dados para essa equipe. Seu aplicativo pode e deve aproveitar esse recurso se ele interagir com arquivos. Você também pode usar o conjunto de sites para armazenar dados brutos em Listas do SharePoint e excel.
