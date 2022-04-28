---
author: heath-hamilton
description: Práticas recomendadas ou considerações para a integração de aplicativos Web existentes com Microsoft Teams
ms.author: surbhigupta
ms.date: 08/26/2020
ms.localizationpriority: medium
ms.topic: conceptual
title: Considerações sobre a Teams integração
ms.openlocfilehash: bbd5b046d7b1afca5cc3fa5c8afb21a3698f43eb
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65104347"
---
# <a name="considerations-for-teams-integration"></a>Considerações sobre a Teams integração

Você pode tornar os aplicativos Web adequados Teams recursos sociais e colaborativos, integrando-os corretamente com Teams.
  
Os diferentes tipos de aplicativos que você pode integrar ao Teams são os seguintes:

* **Aplicativos autônomos**: um aplicativo autônomo é um aplicativo de página única ou grande e complexo. O usuário pode usar alguns aspectos dele no Teams.
* **Aplicativos de** colaboração: um aplicativo já criado para os recursos sociais e colaborativos inerentes Teams.
* **SharePoint**: uma SharePoint página que você deseja exibir no Teams.

Você pode mapear e seguir as diretrizes apropriadas aplicáveis ao seu cenário de integração.
Este documento fornece uma visão geral de Teams, requisitos de ponto de compartilhamento para armazenamento de arquivos e dados, requisitos de API, autenticação e vinculação profunda de seu aplicativo com Teams.

## <a name="get-to-know-teams-platform-capabilities"></a>Conheça os recursos Teams plataforma

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração, SharePoint*

Seu Teams aplicativo deve incluir recursos colaborativos necessários e esperados. Para trabalhar com a integração de aplicativos, é importante se familiarizar com Teams terminologia de desenvolvimento.

|Recursos comuns do aplicativo   |Teams da plataforma   |
|----------|-----------|
|Página da Web inserida, home page ou modo de exibição da Web  |[Guias](../tabs/what-are-tabs.md)  |
|Compartilhar atalhos e extensões  |[Extensões de mensagem](../messaging-extensions/what-are-messaging-extensions.md)  |
|Atalhos e extensões de ação  |[Extensões de mensagem](../messaging-extensions/what-are-messaging-extensions.md)  |
|Chatbots |[Bots](../bots/what-are-bots.md) |
|Notificações de canal  |[Bots](../bots/what-are-bots.md)<br/>[Webhooks de entrada](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)<br/>[Conectores de Office 365](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)  |
|Serviços externos de mensagem  |[Bots](../bots/what-are-bots.md)<br/>[Webhooks de saída](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)  |
|Modais  |[Módulos de tarefas](../task-modules-and-cards/what-are-task-modules.md)  |
|Cartões com conteúdo avançado  |[Cartões Adaptáveis](../task-modules-and-cards/what-are-cards.md)  |

## <a name="determine-a-subset-of-functionality"></a>Determinar um subconjunto de funcionalidade

***Cenários de integração**: aplicativos autônomos*

A integração de todos os recursos de um aplicativo existente Teams geralmente leva a uma experiência de usuário forçada ou não natural, especialmente em aplicativos maiores. Comece com os recursos mais impactante e aqueles que se integram mais naturalmente ao Teams. Você pode permitir que os usuários iniciem o aplicativo principal e acessem seu conjunto completo de recursos.

A seguir estão os pré-requisitos para integrar seu aplicativo ao Teams.

1. [Mapeie os casos de uso do aplicativo para Teams da plataforma](../concepts/design/map-use-cases.md).
1. [Determine os pontos de entrada do aplicativo](../concepts/extensibility-points.md). É para uso pessoal, para colaboração ou para ambos?

## <a name="understand-sharepoint-requirements-and-options"></a>Entender SharePoint requisitos e opções

***Cenários de integração**: SharePoint*

Para integrar uma página SharePoint [existente](/sharepoint/dev/general-development/overview-of-the-sharepoint-page-model) como uma Teams, considere o seguinte:

* Ele deve ser uma *página SharePoint* online moderna.
* Há suporte apenas para guias pessoais. Não é possível integrar sua página como uma guia de canal.

Como alternativa, você pode criar uma Teams [usando o Estrutura do SharePoint](/sharepoint/dev/spfx/integrate-with-teams-introduction).

## <a name="aim-towards-multitenancy"></a>Visar a multilocação

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração, SharePoint*

Se seu aplicativo for usado por várias organizações, considere a hospedagem multilocatário. Ele torna seu produto escalonável e simplifica a distribuição.

## <a name="review-your-apis"></a>Examinar suas APIs

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração*

As APIs e estruturas de dados do aplicativo devem dar suporte ao aplicativo durante a integração com Teams. Para estender o suporte, você deve aumentar as APIs e estruturas de dados com informações contextuais sobre o Teams para mapeamento de [identidade, suporte](../concepts/authentication/configure-identity-provider.md) a [links](../concepts/build-and-test/deep-links.md) profundos e incorporação do [Microsoft Graph](/graph/teams-concept-overview).

Veja como obter contexto para sua guia Teams [ou](../tabs/how-to/access-teams-context.md) [bot](../bots/how-to/get-teams-context.md).

## <a name="understand-authentication-options"></a>Entender as opções de autenticação

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração, SharePoint*

Azure Active Directory é o provedor de identidade para Teams. Se seu aplicativo usar um provedor de identidade diferente, você deverá fazer um exercício de mapeamento de identidade ou combinar com o Microsoft Azure Active Directory (Azure AD).

Teams tem mecanismos de SSO (logon único) com o Azure AD para aplicativos de terceiros. Ele também fornece as diretrizes para fluxos de autenticação para outros provedores de identidade usando padrões como OAuth e Open ID Conexão, conhecidos como OIDC.

> [!IMPORTANT]
> Atualmente, aplicativos de terceiros estão disponíveis no Nuvem da Comunidade Governamental (GCC), mas não estão disponíveis para GCC-High e Departamento de Defesa (DOD). Aplicativos de terceiros são desativados por padrão para GCC. Para ativar aplicativos de terceiros para GCC, consulte gerenciar políticas de permissão [de aplicativo](/microsoftteams/teams-app-permission-policies) e [gerenciar aplicativos](/microsoftteams/manage-apps).

Para SharePoint, você só poderá usar o SSO e não poderá adicionar outra ID do Azure AD se quiser que o SSO funcione para outro aplicativo, pois a ID é o SharePoint aplicativo.

Saiba mais sobre [a autenticação Teams](../concepts/authentication/authentication.md).

## <a name="follow-teams-design-guidelines"></a>Siga Teams de design

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração*

Siga as [diretrizes Teams design para](../concepts/design/understand-use-cases.md) tornar seu aplicativo nativo Teams. Você não pode migrar um conteúdo de aplicativo existente para uma Teams guia. Para obter mais informações sobre o design do aplicativo, [consulte Sistema Fluent Design](https://fluentsite.z22.web.core.windows.net/).

## <a name="maximize-deep-linking"></a>Maximizar a vinculação profunda

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração, SharePoint*

Você pode criar links de informações e recursos no Teams. Use [links profundos](../concepts/build-and-test/deep-links.md) para vincular seu aplicativo Teams à medida que eles vinculam várias partes de um aplicativo para uma experiência mais Teams nativa.

## <a name="be-smart-when-messaging-users"></a>Seja inteligente ao enviar mensagens aos usuários

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração, SharePoint*

Use um [bot](../bots/what-are-bots.md) em seu Teams para conversa multithread, pois ele oferece mais flexibilidade do que um [webhook](../webhooks-and-connectors/what-are-webhooks-and-connectors.md).

Os bots também permitem que você envie mensagens **proativas** para usuários ou canais individuais. As mensagens proativas são mensagens não disparadas por um evento externo e não uma mensagem enviada a um bot. Por exemplo, seu bot envia uma mensagem de boas-vindas quando ele é instalado ou um novo usuário ingressa em um canal.

O envio de mensagens proativas requer Teams identificadores específicos. Você pode capturar as informações buscando [dados](../bots/how-to/get-teams-context.md#fetch-the-roster-or-user-profile) de lista de participação ou perfil de [usuário,](../bots/how-to/conversations/subscribe-to-conversation-events.md) assinando eventos de conversa ou usando o [Microsoft Graph](/microsoftteams/platform/graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages?context=graph/context#proactive-messaging-in-teams).

Não faça spam para usuários com mensagens excessivas. Se a Teams suporte a ele, os usuários poderão definir as configurações de notificação para seu aplicativo.
Veja a seguir um exemplo de uma mensagem de notificação: **não envie mensagens não reproduzadas**.

## <a name="use-sharepoint-for-file-and-data-storage"></a>Usar SharePoint para armazenamento de arquivos e dados

***Cenários de integração:** Aplicativos autônomos, aplicativos de colaboração, SharePoint páginas*

Quando uma equipe é criada, um [conjunto SharePoint site](/microsoftteams/sharepoint-onedrive-interact) também é provisionado para dar suporte ao armazenamento de arquivos e dados para essa equipe. Seu aplicativo deve aproveitar esse recurso se ele interagir com arquivos. Use o conjunto de sites para armazenar dados brutos SharePoint Listas e Microsoft Excel.

## <a name="see-also"></a>Confira também

* [Integrar aplicativos Web](~/samples/integrate-web-apps-overview.md)
* [Soluções de código baixo e sem código para Microsoft Teams](~/samples/teams-low-code-solutions.md)
* [Compartilhar no Teams a partir de aplicativos Web](~/concepts/build-and-test/share-to-teams-from-web-apps.md)
* [Atributos de cookie SameSite](~/resources/samesite-cookie-update.md)
* [Integrar Power Virtual Agents chatbot](~/bots/how-to/add-power-virtual-agents-bot-to-teams.md)
