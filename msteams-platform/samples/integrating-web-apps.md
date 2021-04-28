---
author: heath-hamilton
description: Práticas recomendadas para integrar aplicativos Web existentes com o Microsoft Teams
ms.author: v-heha
ms.date: 08/26/2020
localization_priority: Normal
ms.topic: conceptual
title: Aplicativos Web
ms.openlocfilehash: 0cc4c8bbecb51056e579478de64a5f4e73199674
ms.sourcegitcommit: a732789190f59ec1f3699e8ad2f06387e8fe1458
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2021
ms.locfileid: "52058688"
---
# <a name="web-apps"></a>Aplicativos Web 

Você pode tornar os aplicativos Web adequados aos recursos sociais e colaborativos do Teams, integrando-os corretamente com o Teams.
  
Os diferentes tipos de aplicativos que você pode integrar com o Teams são:
* **Aplicativos autônomos**: um aplicativo autônomo é um aplicativo de página única ou grande e complexo. O usuário pode usar alguns aspectos dele no Teams.
* **Aplicativos de** colaboração : um aplicativo já criado para os recursos sociais e colaborativos inerentes ao Teams.
* **SharePoint**: uma página do SharePoint que você deseja aparecer no Teams.

Você pode mapear e seguir a diretriz apropriada aplicável ao seu cenário de integração.
Este documento fornece uma visão geral dos recursos do Teams, requisitos de ponto de compartilhamento para armazenamento de arquivos e dados, requisitos de API, autenticação e vínculo profundo do seu aplicativo com o Teams.
 
## <a name="get-to-know-teams-platform-capabilities"></a>Conheça os recursos da plataforma Teams

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração, SharePoint*

Seu aplicativo do Teams deve incluir recursos colaborativos necessários e esperados. Para trabalhar com a integração de aplicativos, é importante familiarizar-se com a terminologia de desenvolvimento do Teams.

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

A integração de todos os recursos de um aplicativo existente ao Teams geralmente leva a uma experiência de usuário forçada ou não natural, especialmente em aplicativos maiores. Comece com os recursos mais impactáveis e aqueles que se integram mais naturalmente ao Teams. Você pode permitir que os usuários lancem o aplicativo principal e acessem seu conjunto completo de recursos.

**Pré-requisitos para integrar seu aplicativo ao Teams** A seguir estão os pré-requisitos para integrar seu aplicativo ao Teams. 

1. [Mapeie os casos de uso do](../concepts/design/map-use-cases.md)aplicativo para os recursos da plataforma teams.
1. [Determine os pontos de entrada do aplicativo.](../concepts/extensibility-points.md) É para uso pessoal, colaboração ou ambos?

## <a name="understand-sharepoint-requirements-and-options"></a>Entender os requisitos e opções do SharePoint

***Cenários de integração**: SharePoint*

Para integrar uma página existente do [SharePoint](https://docs.microsoft.com/MicrosoftTeams/teams-standalone-static-tabs-using-spo-sites) como uma guia do Teams, considere o seguinte:

* Deve ser uma página *moderna do* SharePoint online.
* Somente guias pessoais são suportadas. Você não pode integrar sua página como uma guia de canal.

Como alternativa, você pode criar uma guia do Teams [usando a Estrutura do SharePoint](https://docs.microsoft.com/sharepoint/dev/spfx/integrate-with-teams-introduction).

## <a name="aim-towards-multi-tenancy"></a>Aponte para multi-enancy

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração, SharePoint*

Se seu aplicativo for usado por várias organizações, considere a hospedagem de vários locatários que torna seu produto escalonável e simplifique muito a distribuição.

## <a name="review-your-apis"></a>Revisar suas APIs

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração*

Você deve fazer com que as APIs e estruturas de dados existentes do seu aplicativo suportem o aplicativo ao se integrar ao Teams. Para estender o suporte, você deve aumentar as APIs e estruturas de dados com informações contextuais sobre o Teams para mapeamento de [identidade,](../concepts/authentication/configure-identity-provider.md)suporte [a links](../concepts/build-and-test/deep-links.md)profundos e [incorporação do Microsoft Graph.](https://docs.microsoft.com/graph/teams-concept-overview)

Saiba mais sobre como obter contexto para sua [guia](../tabs/how-to/access-teams-context.md) ou [bot](../bots/how-to/get-teams-context.md)do Teams.

## <a name="understand-authentication-options"></a>Compreender opções de autenticação

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração, SharePoint*

O Azure Active Directory (AD) é o provedor de identidade do Teams. Se seu aplicativo usa um provedor de identidade diferente, você deve fazer um exercício de mapeamento de identidade ou combinar com o Azure AD.

O Teams tem mecanismos de SSO (login único) com o Azure AD para aplicativos de terceiros. Ele também fornece as diretrizes para fluxos de autenticação para outros provedores de identidade usando padrões como OAuth e Open ID Connect, conhecidos como OIDC.

Para páginas do SharePoint, você só pode usar o SSO e não pode adicionar outra ID do Azure AD se quiser que o SSO funcione para outro aplicativo, pois a ID é o aplicativo do SharePoint.

Saiba mais sobre [autenticação no Teams](../concepts/authentication/authentication.md).

## <a name="follow-teams-design-guidelines"></a>Siga as diretrizes de design do Teams

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração*

Certifique-se de [seguir as diretrizes de design do Teams](../concepts/design/understand-use-cases.md) para tornar seu aplicativo nativo ao Teams. Não é possível migrar um conteúdo de aplicativo existente para uma guia do Teams. Para obter mais informações sobre o design do aplicativo, consulte [Fluent Design System](https://fluentsite.z22.web.core.windows.net/).

## <a name="maximize-deep-linking"></a>Maximizar o vínculo profundo

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração, SharePoint*

Você pode criar links para informações e recursos no Teams. Use [links profundos](../concepts/build-and-test/deep-links.md) para vincular seu aplicativo com o Teams à medida que eles vinculam várias partes de um aplicativo para uma experiência do Teams mais nativa.

## <a name="be-smart-when-messaging-users"></a>Ser inteligente ao enviar mensagens aos usuários

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração, SharePoint*

Use um [bot](../bots/what-are-bots.md) no aplicativo do Teams para conversas com vários threads, pois oferece mais flexibilidade do que um [webhook.](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)

Os bots também permitem que você envie mensagens **proativas** para usuários ou canais individuais. As mensagens proativas são mensagens não proativas disparadas por um evento externo e não uma mensagem enviada a um bot. Por exemplo, seu bot envia uma mensagem de boas-vindas quando ele é instalado ou um novo usuário ins junta um canal. 

O envio de mensagens proativas requer identificadores específicos do Teams. Você pode capturar as informações buscando dados de lista [ou](../bots/how-to/get-teams-context.md#fetch-the-roster-or-user-profile)perfil de usuário, [assinando](../bots/how-to/conversations/subscribe-to-conversation-events.md)eventos de conversa ou usando [o Microsoft Graph](https://docs.microsoft.com/graph/teams-proactive-messaging).

Não spam usuários com mensagens excessivas. Se a funcionalidade do Teams for compatível com ele, os usuários poderão configurar as configurações de notificação para seu aplicativo.   
A seguir está um exemplo de uma mensagem de notificação: Não me envie mensagens **não prompadas.**

## <a name="use-sharepoint-for-file-and-data-storage"></a>Usar o SharePoint para armazenamento de arquivos e dados

***Cenários de integração:** Aplicativos autônomos, aplicativos de colaboração, páginas do SharePoint*

Quando uma equipe é criada, um conjunto de sites do [SharePoint](https://docs.microsoft.com/microsoftteams/sharepoint-onedrive-interact) também é provisionado para dar suporte ao armazenamento de arquivos e dados para essa equipe. Seu aplicativo deve aproveitar esse recurso se ele interagir com arquivos. Use o conjunto de sites para armazenar dados brutos em Listas do SharePoint e excel.

## <a name="see-also"></a>Confira também

- [Integrar aplicativos Web](~/samples/integrate-web-apps-overview.md)
