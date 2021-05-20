---
author: heath-hamilton
description: Melhores práticas para integrar aplicativos web existentes com Microsoft Teams
ms.author: v-heha
ms.date: 08/26/2020
localization_priority: Normal
ms.topic: conceptual
title: Aplicativos Web
ms.openlocfilehash: 6783a05079f876cf3c2475a0ad5ca0e1f6687fc4
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566219"
---
# <a name="web-apps"></a>Aplicativos Web 

Você pode tornar os aplicativos web adequados com os recursos sociais e colaborativos da Teams, integrando-os adequadamente com Teams.
  
Os diferentes tipos de aplicativos que você pode integrar com Teams são os seguintes:
* **Aplicativos autônomos**: Um aplicativo autônomo é um aplicativo de uma única página ou grande e complexo. O usuário pode usar alguns aspectos dele em Teams.
* **Aplicativos de colaboração**: Um aplicativo já construído para os recursos sociais e colaborativos inerentes ao Teams.
* **SharePoint**: Uma página SharePoint que você deseja aparecer em Teams.

Você pode mapear e seguir a diretriz apropriada aplicável ao seu cenário de integração.
Este documento fornece uma visão geral dos recursos de Teams, requisitos de ponto de compartilhamento para armazenamento de arquivos e dados, requisitos de API, autenticação e vinculação profunda do seu aplicativo com Teams.
 
## <a name="get-to-know-teams-platform-capabilities"></a>Conheça Teams recursos da plataforma

***Cenários de integração**: Aplicativos autônomos, aplicativos de colaboração SharePoint*

Seu aplicativo Teams deve incluir recursos colaborativos necessários e esperados. Para trabalhar com integração de aplicativos, é importante familiarizar-se com Teams terminologia de desenvolvimento.

|Recursos comuns do aplicativo   |recursos de plataforma Teams   |
|----------|-----------|
|Página da Web incorporada, página inicial ou webview  |[Guias](../tabs/what-are-tabs.md)  |
|Compartilhar atalhos e extensões  |[Extensões de Mensagens](../messaging-extensions/what-are-messaging-extensions.md)  |
|Atalhos e extensões de ação  |[Extensões de Mensagens](../messaging-extensions/what-are-messaging-extensions.md)  |
|Chatbots  |[Bots](../bots/what-are-bots.md) |
|Notificações de canais  |[Bots](../bots/what-are-bots.md)<br/>[Webhooks de entrada](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)<br/>[Conectores de Office 365](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)  |
|Mensagem serviços externos  |[Bots](../bots/what-are-bots.md)<br/>[Webhooks de saída](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)  |
|Modais  |[Módulos de tarefas](../task-modules-and-cards/what-are-task-modules.md)  |
|Cartões ricos em conteúdo  |[Cartões Adaptáveis](../task-modules-and-cards/what-are-cards.md)  |

## <a name="determine-a-subset-of-functionality"></a>Determine um subconjunto de funcionalidade

***Cenários de integração**: Aplicativos autônomos*

Integrar todos os recursos de um aplicativo existente em Teams muitas vezes leva a uma experiência forçada ou não natural do usuário, particularmente em aplicativos maiores. Comece com as características mais impactantes e aquelas que se integram mais naturalmente com Teams. Você pode permitir que os usuários iniciem o aplicativo principal e acessem seu conjunto completo de recursos.

**Pré-requisitos para integrar seu aplicativo com Teams** A seguir estão os pré-requisitos para integrar seu aplicativo com Teams. 

1. [Mapeie os casos de uso do seu aplicativo para Teams recursos da plataforma](../concepts/design/map-use-cases.md).
1. [Determine os pontos de entrada do seu aplicativo](../concepts/extensibility-points.md). É para uso pessoal, colaboração ou ambos?

## <a name="understand-sharepoint-requirements-and-options"></a>Entenda SharePoint requisitos e opções

***Cenários de integração**: SharePoint*

Para integrar uma [página de SharePoint](/MicrosoftTeams/teams-standalone-static-tabs-using-spo-sites) existente como uma guia Teams, você deve considerar o seguinte:

* Deve ser uma página *moderna* SharePoint online.
* Apenas guias pessoais são suportadas. Você não pode integrar sua página como uma guia de canal.

Alternativamente, você pode construir uma guia Teams [usando o Estrutura do SharePoint](/sharepoint/dev/spfx/integrate-with-teams-introduction).

## <a name="aim-towards-multi-tenancy"></a>Objetivo para multi-locação

***Cenários de integração**: Aplicativos autônomos, aplicativos de colaboração SharePoint*

Se o seu aplicativo for usado por várias organizações, considere a hospedagem multi-inquilinos que torna seu produto escalável e simplifica muito a distribuição.

## <a name="review-your-apis"></a>Revise suas APIs

***Cenários de integração**: Aplicativos autônomos, aplicativos de colaboração*

Você deve fazer com que as APIs e estruturas de dados existentes do seu aplicativo suportem o aplicativo ao se integrarem ao Teams. Para ampliar o suporte, você deve aumentar as APIs e estruturas de dados com informações contextuais sobre Teams para [mapeamento de identidade,](../concepts/authentication/configure-identity-provider.md) [suporte a links profundos](../concepts/build-and-test/deep-links.md)e [incorporação de Graph Microsoft](/graph/teams-concept-overview).

Saiba mais sobre como obter contexto para sua [Teams aba](../tabs/how-to/access-teams-context.md) ou [bot](../bots/how-to/get-teams-context.md).

## <a name="understand-authentication-options"></a>Entenda as opções de autenticação

***Cenários de integração**: Aplicativos autônomos, aplicativos de colaboração SharePoint*

Azure Active Directory (AD) é o provedor de identidade para Teams. Se o seu aplicativo usa um provedor de identidade diferente, você deve fazer um exercício de mapeamento de identidade ou combinar com o Azure AD.

Teams tem mecanismos de login único (SSO) com O Azure AD para aplicativos de terceiros. Ele também fornece a orientação para fluxos de autenticação para outros provedores de identidade usando padrões como OAuth e Open ID Conexão, conhecido como OIDC.

Para SharePoint páginas, você só pode usar o SSO e não pode adicionar outro ID AZure se quiser que o SSO trabalhe para outro aplicativo, pois o ID é o aplicativo SharePoint.

Saiba mais sobre [autenticação em Teams](../concepts/authentication/authentication.md).

## <a name="follow-teams-design-guidelines"></a>Siga as diretrizes de design Teams

***Cenários de integração**: Aplicativos autônomos, aplicativos de colaboração*

Certifique-se de seguir [Teams diretrizes de design](../concepts/design/understand-use-cases.md) para tornar seu aplicativo nativo para Teams. Você não pode migrar um conteúdo de aplicativo existente para uma guia Teams. Para obter mais informações sobre o design do aplicativo, consulte [Fluent Design System](https://fluentsite.z22.web.core.windows.net/).

## <a name="maximize-deep-linking"></a>Maximizar a ligação profunda

***Cenários de integração**: Aplicativos autônomos, aplicativos de colaboração SharePoint*

Você pode criar links para informações e recursos dentro de Teams. Use [links profundos](../concepts/build-and-test/deep-links.md) para vincular seu aplicativo a Teams, pois eles unem várias peças de um aplicativo para uma experiência mais nativa Teams.

## <a name="be-smart-when-messaging-users"></a>Seja inteligente ao enviar mensagens aos usuários

***Cenários de integração**: Aplicativos autônomos, aplicativos de colaboração SharePoint*

Use um [bot](../bots/what-are-bots.md) em seu aplicativo de Teams para conversas multi-threaded, pois oferece mais flexibilidade do que um [webhook](../webhooks-and-connectors/what-are-webhooks-and-connectors.md).

Os bots também permitem que você envie **mensagens proativas** para usuários ou canais individuais. As mensagens proativas são mensagens não provocadas desencadeadas por um evento externo e não uma mensagem enviada a um bot. Por exemplo, seu bot envia uma mensagem de boas-vindas quando é instalado ou um novo usuário entra em um canal. 

O envio de mensagens proativas requer identificadores específicos de Teams. Você pode capturar as informações [buscando dados de lista ou perfil do usuário, assinando](../bots/how-to/get-teams-context.md#fetch-the-roster-or-user-profile)eventos de [conversação](../bots/how-to/conversations/subscribe-to-conversation-events.md)ou usando [o Microsoft Graph](/graph/teams-proactive-messaging).

Não envie spam aos usuários com mensagens excessivas. Se o recurso Teams o suportar, os usuários podem configurar as configurações de notificação para o seu aplicativo.   
A seguir está um exemplo de uma mensagem de notificação: **Não me envie mensagens sem aviso.**

## <a name="use-sharepoint-for-file-and-data-storage"></a>Use SharePoint para armazenamento de arquivos e dados

***Cenários de integração:** Aplicativos autônomos, aplicativos de colaboração SharePoint páginas*

Quando uma equipe é criada, uma [coleta de SharePoint site](/microsoftteams/sharepoint-onedrive-interact) também é fornecida para suportar o armazenamento de arquivos e dados para essa equipe. Seu aplicativo deve aproveitar esse recurso se ele interagir com arquivos. Use a coleta do site para armazenar dados brutos em SharePoint Lists e Excel.

## <a name="see-also"></a>Confira também

[Integrar aplicativos Web](~/samples/integrate-web-apps-overview.md)
