---
author: heath-hamilton
description: Práticas recomendadas ou considerações para integrar aplicativos Web existentes com o Microsoft Teams
ms.author: surbhigupta
ms.date: 08/26/2020
ms.localizationpriority: high
ms.topic: conceptual
title: Considerações para a integração do Microsoft Teams
ms.openlocfilehash: 2e1d749a34d0dec2a38e84e57aa6147c791264c1
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111658"
---
# <a name="considerations-for-teams-integration"></a>Considerações para a integração do Microsoft Teams

Você pode tornar os aplicativos Web adequados aos recursos sociais e colaborativos do Teams, integrando-os corretamente com o Teams.
  
Os diferentes tipos de aplicativos que você pode integrar ao Teams são os seguintes:

* **Aplicativos autônomos**: um aplicativo autônomo é um aplicativo de página única ou grande e complexo. O usuário pode usar alguns aspectos dele no Teams.
* **Aplicativos de colaboração**: um aplicativo já criado para os recursos sociais e colaborativos inerentes ao Teams.
* **Sharepoint**: uma página do SharePoint que você deseja exibir no Teams.

Você pode mapear e seguir as diretrizes apropriadas aplicáveis ao seu cenário de integração.
Este documento fornece uma visão geral dos recursos do Teams, requisitos de ponto de compartilhamento para armazenamento de arquivos e dados, requisitos de API, autenticação e vinculação profunda de seu aplicativo com o Teams.

## <a name="get-to-know-teams-platform-capabilities"></a>Conheça os recursos da plataforma Teams

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração, SharePoint*

Seu aplicativo Teams deve incluir recursos colaborativos necessários e esperados. Para trabalhar com a integração de aplicativos, é importante se familiarizar com a terminologia de desenvolvimento do Teams.

|Recursos comuns do aplicativo   |Funcionalidades da plataforma Teams   |
|----------|-----------|
|Página da Web inserida, página inicial ou modo de exibição da Web  |[Guias](../tabs/what-are-tabs.md)  |
|Compartilhar atalhos e extensões  |[Extensões de mensagens](../messaging-extensions/what-are-messaging-extensions.md)  |
|Atalhos e extensões de ação  |[Extensões de mensagens](../messaging-extensions/what-are-messaging-extensions.md)  |
|Chatbots |[Bots](../bots/what-are-bots.md) |
|Notificação de canal  |[Bots](../bots/what-are-bots.md)<br/>[Webhooks recebidos](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)<br/>[Conectores de Office 365](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)  |
|Serviços externos de mensagem  |[Bots](../bots/what-are-bots.md)<br/>[Webhooks de saída](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)  |
|Modais  |[Módulos de tarefas](../task-modules-and-cards/what-are-task-modules.md)  |
|Cartões com conteúdo avançado  |[Cartões Adaptáveis](../task-modules-and-cards/what-are-cards.md)  |

## <a name="determine-a-subset-of-functionality"></a>Determinar um subconjunto de funcionalidade

***Cenários de integração**: aplicativos autônomos*

A integração de todos os recursos de um aplicativo existente ao Teams geralmente leva a uma experiência de usuário forçada ou não natural, especialmente em aplicativos maiores. Comece com os recursos mais impactante e aqueles que se integram mais naturalmente ao Teams. Você pode permitir que os usuários iniciem o aplicativo principal e acessem seu conjunto completo de recursos.

A seguir estão os pré-requisitos para integrar seu aplicativo ao Teams.

1. [Mapear os casos de uso do seu aplicativo para recursos de plataforma do Teams](../concepts/design/map-use-cases.md).
1. [Determinar os pontos de entrada do aplicativo](../concepts/extensibility-points.md). É para uso pessoal, para colaboração ou para ambos?

## <a name="understand-sharepoint-requirements-and-options"></a>Entenda os requisitos e as opções do SharePoint

***Cenários de integração**: SharePoint*

Para integrar uma [página do SharePoint](/sharepoint/dev/general-development/overview-of-the-sharepoint-page-model) como uma guia do Teams, você deve considerar o seguinte:

* Ele deve ser uma página online *moderna* do SharePoint.
* Há suporte apenas para guias pessoais. Você não pode integrar sua página como uma guia de canal.

Como alternativa, você pode criar uma guia do Teams [usando a estrutura do SharePoint](/sharepoint/dev/spfx/integrate-with-teams-introduction).

## <a name="aim-towards-multitenancy"></a>Vise a multilocação

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração, SharePoint*

Se seu aplicativo for usado por várias organizações, considere a hospedagem multilocatário. Ele torna seu produto escalonável e simplifica a distribuição.

## <a name="review-your-apis"></a>Examine suas APIs

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração*

As APIs e estruturas de dados do aplicativo devem dar suporte ao aplicativo durante a integração com o Teams. Para estender o suporte, você deve aumentar as APIs e estruturas de dados com informações contextuais sobre o Teams para [mapeamento de identidade](../concepts/authentication/configure-identity-provider.md), [suporte a link profundo](../concepts/build-and-test/deep-links.md) e [incorporar o Microsoft Graph](/graph/teams-concept-overview).

Veja como obter contexto para a [guia](../tabs/how-to/access-teams-context.md) ou [bot](../bots/how-to/get-teams-context.md) do Teams.

## <a name="understand-authentication-options"></a>Entenda as opções de autenticação

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração, SharePoint*

O Azure Active Directory é o provedor de identidade do Teams. Se seu aplicativo usa um provedor de identidade diferente, você deve fazer um exercício de mapeamento de identidade ou combinar com o Microsoft Azure Active Directory (Azure AD).

O Teams tem mecanismos de SSO (logon único) com o Azure AD para aplicativos de terceiros. Ele também fornece as diretrizes para fluxos de autenticação para outros provedores de identidade usando padrões como OAuth e Open ID Connect, conhecidos como OIDC.

> [!IMPORTANT]
> Atualmente, os aplicativos de sideload estão disponíveis no Nuvem da Comunidade Governamental (GCC), mas não estão disponíveis para GCC-High e DoD (Departamento de Defesa). Aplicativos de terceiros são desativados por padrão para GCC. Para ativar aplicativos de terceiros para GCC, consulte [gerenciar políticas de permissão de aplicativo](/microsoftteams/teams-app-permission-policies) e [gerenciar aplicativos](/microsoftteams/manage-apps).

Para páginas do SharePoint, você só poderá usar o SSO e não poderá adicionar outra ID do Azure AD se quiser que o SSO funcione para outro aplicativo, pois a ID é o aplicativo do SharePoint.

Saiba mais sobre [autenticação no Teams](../concepts/authentication/authentication.md).

## <a name="follow-teams-design-guidelines"></a>Siga as diretrizes de design do Teams

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração*

Siga as [Diretrizes de design do Teams](../concepts/design/understand-use-cases.md) para tornar seu aplicativo nativo do Teams. Não é possível migrar um conteúdo de aplicativo existente para uma guia do Teams. Para obter mais informações sobre o design do aplicativo, consulte [Sistema Fluent Design](https://fluentsite.z22.web.core.windows.net/).

## <a name="maximize-deep-linking"></a>Maximizar a vinculação profunda

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração, SharePoint*

Você pode criar links de informações e recursos no Teams. Use [links profundos](../concepts/build-and-test/deep-links.md)para vincular seu aplicativo ao Teams à medida que eles reúnem várias partes de um aplicativo para uma experiência mais nativa do Teams.

## <a name="be-smart-when-messaging-users"></a>Seja inteligente ao enviar mensagens aos usuários

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração, SharePoint*

Use um [bot](../bots/what-are-bots.md) em seu aplicativo do Teams para conversas com vários threaded, pois ele oferece mais flexibilidade do que um [webhook](../webhooks-and-connectors/what-are-webhooks-and-connectors.md).

Os bots também permitem que você envie **mensagens proativas** para usuários ou canais individuais. As mensagens proativas são mensagens não solicitadas disparadas por um evento externo e não uma mensagem enviada a um bot. Por exemplo, seu bot envia uma mensagem de boas-vindas quando ele é instalado ou um novo usuário ingressa em um canal.

O envio de mensagens proativas requer identificadores específicos do Teams. Você pode capturar as informações [buscando lista de participantes ou dados de perfil de usuário](../bots/how-to/get-teams-context.md#fetch-the-roster-or-user-profile), [assinando eventos de conversa](../bots/how-to/conversations/subscribe-to-conversation-events.md)ou usando o [Microsoft Graph](/microsoftteams/platform/graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages?context=graph/context#proactive-messaging-in-teams).

Não gere spam para usuários com mensagens excessivas. Se a funcionalidade do Teams tiver suporte, os usuários poderão definir as configurações de notificação para seu aplicativo.
Veja a seguir um exemplo de uma mensagem de notificação: **Não me enviar mensagens não solicitadas**.

## <a name="use-sharepoint-for-file-and-data-storage"></a>Usar o SharePoint para armazenamento de arquivos e dados

***Integration scenarios:** Aplicativos autônomos, aplicativos de colaboração, páginas do SharePoint*

Quando uma equipe é criada, um [conjunto de sites do SharePoint](/microsoftteams/sharepoint-onedrive-interact) também é provisionado para dar suporte ao armazenamento de arquivos e dados para essa equipe. Seu aplicativo deverá aproveitar esse recurso se ele interagir com arquivos. Use o conjunto de sites para armazenar dados brutos nas Listas do SharePoint e no Microsoft Excel.

## <a name="see-also"></a>Confira também

* [Integrar aplicativos Web](~/samples/integrate-web-apps-overview.md)
* [Soluções sem código e com pouco código para o Microsoft Teams](~/samples/teams-low-code-solutions.md)
* [Compartilhar no Teams a partir de aplicativos Web](~/concepts/build-and-test/share-to-teams-from-web-apps.md)
* [Atributos de cookie SameSite](~/resources/samesite-cookie-update.md)
* [Integrar o chatbot do Power Virtual Agents com o Teams](~/bots/how-to/add-power-virtual-agents-bot-to-teams.md)
