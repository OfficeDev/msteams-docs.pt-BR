---
author: heath-hamilton
description: Práticas recomendadas para integração de aplicativos Web existentes com o Microsoft Teams
ms.author: v-heha
ms.date: 08/26/2020
ms.topic: conceptual
title: Integrar um aplicativo Web ao Microsoft Teams
ms.openlocfilehash: e7d4f74526f7a71fe33d5a70d9ed60be960adefc
ms.sourcegitcommit: 1aa0b172931d0f81db346452788c41dc4a6717b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48210096"
---
# <a name="integrate-web-apps-with-teams"></a>Integrar aplicativos Web com o Microsoft Teams

Você tem um aplicativo Web que você acha que se encaixaria naturalmente com os recursos sociais e colaborativos do teams? Essas diretrizes podem ajudá-lo a entender como integrar os seguintes tipos de aplicativos:

* **Aplicativos autônomos**: pode ser um aplicativo de página única ou um aplicativo grande e complexo que você deseja que as pessoas usem alguns aspectos do no Teams.
* **Aplicativos de colaboração**: um aplicativo já criado para os recursos sociais e colaborativos inerentes ao Microsoft Teams.
* **SharePoint**: uma página do SharePoint que você deseja retonar no Microsoft Teams.

Para cada diretriz, você pode ver se ele se aplica ao cenário de integração.

## <a name="get-to-know-teams-platform-capabilities"></a>Conheça os recursos da plataforma do Microsoft Teams

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração, SharePoint *

O aplicativo do Microsoft Teams pode incluir recursos que os usuários desejam e podem esperar ao colaborar, mas você pode não estar familiarizado com a terminologia de desenvolvimento do Microsoft Teams.

|Recursos comuns do aplicativo   |Recursos da plataforma do teams   |
|----------|-----------|
|Página da Web, Home Page ou WebView  |[Guias](../tabs/what-are-tabs.md)  |
|Compartilhar atalhos e extensões  |[Extensões de Mensagens](../messaging-extensions/what-are-messaging-extensions.md)  |
|Atalhos e extensões de ação  |[Extensões de Mensagens](../messaging-extensions/what-are-messaging-extensions.md)  |
|Chatbots  |[Bots](../bots/what-are-bots.md) |
|Notificações de canal  |[Bots](../bots/what-are-bots.md)<br/>[WebHooks de entrada](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)<br/>[Conectores de Office 365](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)  |
|Serviços externos de mensagem  |[Bots](../bots/what-are-bots.md)<br/>[WebHooks de saída](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)  |
|Modais  |[Módulos de tarefas](../task-modules-and-cards/what-are-task-modules.md)  |
|Cartões ricos em conteúdo  |[Cartões adaptáveis](../task-modules-and-cards/what-are-cards.md)  |

## <a name="determine-a-subset-of-functionality"></a>Determinar um subconjunto de funcionalidades

***Cenários de integração**: aplicativos autônomos *

A integração de todos os recursos de um aplicativo existente no Teams geralmente leva a uma experiência de usuário forçada ou não natural, especialmente em aplicativos maiores. Convém começar com os recursos mais impactados e aqueles que se integram mais naturalmente com o Microsoft Teams. Lembre-se de que você sempre pode permitir que os usuários iniciem o aplicativo principal e acessem seu conjunto completo de recursos.

Antes de começar qualquer trabalho técnico, faça alguns planejamentos para seu aplicativo do Microsoft Teams:

1. [Mapeie os casos de uso do aplicativo para os recursos da plataforma do Microsoft Teams](../concepts/design/map-use-cases.md).
1. [Determine os pontos de entrada do seu aplicativo](../concepts/extensibility-points.md). É para uso pessoal, colaboração ou ambos?

## <a name="understand-sharepoint-requirements-and-options"></a>Entender as opções e os requisitos do SharePoint

***Cenários de integração**: SharePoint *

Você pode integrar uma [página existente do SharePoint](https://docs.microsoft.com/MicrosoftTeams/teams-standalone-static-tabs-using-spo-sites) como uma guia Teams. Lembre-se do seguinte:

* Deve ser uma página *moderna* do SharePoint Online
* Só há suporte para guias pessoais (você não pode integrar sua página como uma guia de canal)

Como alternativa, você pode criar uma guia Teams [usando a estrutura do SharePoint](https://docs.microsoft.com/sharepoint/dev/spfx/integrate-with-teams-introduction).

## <a name="aim-towards-multi-tenancy"></a>Direcionar para a multilocação

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração, SharePoint *

Se seu aplicativo for usado por várias organizações, considere a hospedagem de vários locatários que tornaria seu produto escalonável e simplifique muito a distribuição.

## <a name="review-your-apis"></a>Revise suas APIs

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração *

Não presuma que as APIs e estruturas de dados existentes do aplicativo oferecem suporte completo ao aplicativo, quando integradas ao Microsoft Teams. Talvez seja necessário aumentá-las com informações contextuais sobre o [mapeamento de identidades](../concepts/authentication/configure-identity-provider.md), o [suporte de link profundo](../concepts/build-and-test/deep-links.md)e a [incorporação do Microsoft Graph](https://docs.microsoft.com/graph/teams-concept-overview).

Saiba mais sobre como obter contexto para a [guia](../tabs/how-to/access-teams-context.md) ou [bot](../bots/how-to/get-teams-context.md)do Microsoft Teams.

## <a name="understand-authentication-options"></a>Entender as opções de autenticação

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração, SharePoint *

O Azure Active Directory (AD) é o provedor de identidade para o Microsoft Teams. Se seu aplicativo usa um provedor de identidade diferente, você deve fazer um exercício de mapeamento de identidade ou federar o Azure AD.

O Microsoft Teams tem mecanismos de logon único (SSO) com o Azure AD para aplicativos de terceiros e orientações para o fluxo de autenticação para outros provedores de identidade usando padrões como OAuth e OIDC (Open ID Connect).

Para páginas do SharePoint, você só pode usar SSO e não pode adicionar outra ID do Azure AD se quiser que o SSO funcione para outro aplicativo (pois a ID é o aplicativo do SharePoint).

Saiba mais sobre [autenticação no Microsoft Teams](../concepts/authentication/authentication.md).

## <a name="follow-teams-design-guidelines"></a>Siga as diretrizes de design do Microsoft Teams

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração *

Em geral, seu aplicativo deve se sentir natural no Microsoft Teams. Você pode pensar em migrar o conteúdo do aplicativo existente para uma guia do teams é suficiente, mas é altamente recomendável que seu aplicativo siga as [diretrizes de design de equipes](../concepts/design/understand-use-cases.md). Consulte também: [sistema de design fluente](https://fluentsite.z22.web.core.windows.net/).

## <a name="maximize-deep-linking"></a>Maximizar vinculação profunda

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração, SharePoint *

Quase tudo no Microsoft Teams pode ser vinculado diretamente a um [link profundo](../concepts/build-and-test/deep-links.md). Seu aplicativo deve maximizar o uso desses, incluindo a vinculação de mensagens específicas e o conteúdo da guia. Os links profundos podem realmente unir vários pedaços de um aplicativo para uma experiência mais nativa da equipe.

## <a name="be-smart-when-messaging-users"></a>Ser inteligente quando os usuários de mensagens

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração, SharePoint *

Considere os tipos de mensagens que seu aplicativo da equipe pode enviar agora e a longo prazo. Se você acha que seu aplicativo já terá uma conversa com vários encadeamentos, um [bot](../bots/what-are-bots.md) poderá oferecer mais flexibilidade do que um [webhook](../webhooks-and-connectors/what-are-webhooks-and-connectors.md).

Os bots também permitem que você envie *mensagens pró-ativas* para usuários ou canais individuais. Essas são mensagens não solicitadas disparadas por um evento externo e não uma mensagem enviada a um bot. (Por exemplo, seu bot pode enviar uma mensagem de boas-vindas quando é instalado ou um novo usuário ingressa em um canal.) 

O envio de mensagens pró-ativas requer identificadores específicos do teams — você pode capturar essas informações [buscando a lista ou os dados do perfil do usuário](../bots/how-to/get-teams-context.md#fetching-the-roster-or-user-profile), [inscrevendo-se em eventos de conversa](../bots/how-to/conversations/subscribe-to-conversation-events.md)ou usando [o Microsoft Graph](https://docs.microsoft.com/graph/teams-proactive-messaging).

Tenha cuidado para não enviar spam a usuários com mensagens excessivas. Se o recurso Teams oferecer suporte, considere permitir que os usuários configurem as configurações de notificação para seu aplicativo (por exemplo, "não enviar mensagens não solicitadas).

## <a name="use-sharepoint-for-file-and-data-storage"></a>Usar o SharePoint para armazenamento de arquivos e dados

***Cenários de integração:** Aplicativos autônomos, aplicativos de colaboração, páginas do SharePoint*

Quando uma equipe é criada, um [conjunto de sites do SharePoint](https://docs.microsoft.com/microsoftteams/sharepoint-onedrive-interact) também é provisionado para dar suporte ao armazenamento de arquivos e dados para essa equipe. Seu aplicativo pode e deve aproveitar esse recurso se ele interage com arquivos. Você também pode usar o conjunto de sites para armazenar dados brutos em listas do SharePoint e no Excel.
