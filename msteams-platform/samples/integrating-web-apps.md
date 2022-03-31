---
author: heath-hamilton
description: Práticas recomendadas ou considerações para integrar aplicativos Web existentes com Microsoft Teams
ms.author: surbhigupta
ms.date: 08/26/2020
ms.localizationpriority: medium
ms.topic: conceptual
title: Considerações para a integração do Microsoft Teams
ms.openlocfilehash: f545acf25cc6b54a92dc8c7556b348394379abc5
ms.sourcegitcommit: 52af681132e496a57b18f468c5b73265a49a5f44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/31/2022
ms.locfileid: "64590735"
---
# <a name="considerations-for-teams-integration"></a>Considerações para a integração do Microsoft Teams

Você pode tornar os aplicativos Web adequados Teams recursos sociais e colaborativos, integrando-os corretamente com Teams.
  
Os diferentes tipos de aplicativos que você pode integrar com Teams são:

* **Aplicativos autônomos**: um aplicativo autônomo é um aplicativo de página única ou grande e complexo. O usuário pode usar alguns aspectos dele no Teams.
* **Aplicativos de** colaboração: um aplicativo já criado para os recursos sociais e colaborativos inerentes Teams.
* **SharePoint**: uma página de SharePoint que você deseja que seja Teams.

Você pode mapear e seguir a diretriz apropriada aplicável ao seu cenário de integração.
Este documento fornece uma visão geral dos recursos Teams, requisitos de ponto de compartilhamento para armazenamento de arquivos e dados, requisitos de API, autenticação e vinculação profunda do seu aplicativo com Teams.

## <a name="get-to-know-teams-platform-capabilities"></a>Conheça os recursos Teams plataforma

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração, SharePoint*

Seu Teams app deve incluir recursos colaborativos necessários e esperados. Para trabalhar com a integração de aplicativos, é importante se familiarizar com Teams de desenvolvimento.

|Recursos comuns do aplicativo   |Teams plataforma   |
|----------|-----------|
|Página da Web incorporada, homepage ou webview  |[Guias](../tabs/what-are-tabs.md)  |
|Compartilhar atalhos e extensões  |[Extensões de Mensagens](../messaging-extensions/what-are-messaging-extensions.md)  |
|Atalhos de ação e extensões  |[Extensões de Mensagens](../messaging-extensions/what-are-messaging-extensions.md)  |
|Chatbots |[Bots](../bots/what-are-bots.md) |
|Notificações de canal  |[Bots](../bots/what-are-bots.md)<br/>[Webhooks de entrada](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)<br/>[Conectores de Office 365](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)  |
|Serviços externos de mensagens  |[Bots](../bots/what-are-bots.md)<br/>[Webhooks de saída](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)  |
|Modals  |[Módulos de tarefas](../task-modules-and-cards/what-are-task-modules.md)  |
|Cartões ricos em conteúdo  |[Cartões Adaptáveis](../task-modules-and-cards/what-are-cards.md)  |

## <a name="determine-a-subset-of-functionality"></a>Determinar um subconjunto de funcionalidade

***Cenários de integração**: aplicativos autônomos*

A integração de todos os recursos de um aplicativo existente Teams geralmente leva a uma experiência de usuário forçada ou não natural, especialmente em aplicativos maiores. Comece com os recursos mais impactados e aqueles que se integram mais naturalmente com Teams. Você pode permitir que os usuários lancem o aplicativo principal e acessem seu conjunto completo de recursos.

A seguir estão os pré-requisitos para integrar seu aplicativo com Teams.

1. [Mapeie os casos de uso do aplicativo para Teams de plataforma](../concepts/design/map-use-cases.md).
1. [Determine os pontos de entrada do aplicativo](../concepts/extensibility-points.md). É para uso pessoal, para colaboração ou para ambos?

## <a name="understand-sharepoint-requirements-and-options"></a>Compreender SharePoint requisitos e opções

***Cenários de integração**: SharePoint*

Para integrar uma página de [SharePoint existente](/sharepoint/dev/general-development/overview-of-the-sharepoint-page-model) como uma guia Teams, considere o seguinte:

* Deve ser uma página *SharePoint* online moderna.
* Somente guias pessoais são suportadas. Você não pode integrar sua página como uma guia de canal.

Como alternativa, você pode criar uma guia Teams [usando a Estrutura do SharePoint](/sharepoint/dev/spfx/integrate-with-teams-introduction).

## <a name="aim-towards-multitenancy"></a>Visar a multitenência

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração, SharePoint*

Se seu aplicativo for usado por várias organizações, considere hospedagem multitenente. Ele torna seu produto escalonável e simplifica a distribuição.

## <a name="review-your-apis"></a>Revisar suas APIs

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração*

As APIs e estruturas de dados do aplicativo devem dar suporte ao aplicativo durante a integração com Teams. Para estender o suporte, você deve aumentar as APIs e estruturas de dados com informações contextuais sobre o Teams para mapeamento de [identidade, suporte](../concepts/authentication/configure-identity-provider.md) a links profundos e incorporação do [Microsoft Graph](/graph/teams-concept-overview). [](../concepts/build-and-test/deep-links.md)

Veja como obter contexto para sua guia Teams [ou](../tabs/how-to/access-teams-context.md) [bot](../bots/how-to/get-teams-context.md).

## <a name="understand-authentication-options"></a>Compreender opções de autenticação

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração, SharePoint*

Azure Active Directory é o provedor de identidade para Teams. Se seu aplicativo usa um provedor de identidade diferente, você deve fazer um exercício de mapeamento de identidade ou combinar com Microsoft Azure Active Directory (Azure AD).

Teams tem mecanismos de SSO (login único) com o Azure AD para aplicativos de terceiros. Ele também fornece as diretrizes para fluxos de autenticação para outros provedores de identidade usando padrões como OAuth e Open ID Conexão, conhecidos como OIDC.

> [!IMPORTANT]
> Atualmente, aplicativos de terceiros estão disponíveis no Nuvem da Comunidade Governamental (GCC), mas não estão disponíveis para GCC-High e Departamento de Defesa (DOD). Aplicativos de terceiros são desligados por padrão para GCC. Para ativar aplicativos de terceiros para GCC, consulte [manage app permission policies](/microsoftteams/teams-app-permission-policies) and [manage apps](/microsoftteams/manage-apps).

Para SharePoint páginas, você só pode usar o SSO e não pode adicionar outra ID do Azure AD se quiser que o SSO funcione para outro aplicativo, pois a ID é o aplicativo SharePoint.

Saiba mais sobre [autenticação Teams](../concepts/authentication/authentication.md).

## <a name="follow-teams-design-guidelines"></a>Siga Teams de design

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração*

Certifique-se [de seguir Teams de design](../concepts/design/understand-use-cases.md) para tornar seu aplicativo nativo Teams. Não é possível migrar um conteúdo de aplicativo existente para uma Teams guia. Para obter mais informações sobre o design do aplicativo, [consulte Sistema Fluent Design](https://fluentsite.z22.web.core.windows.net/).

## <a name="maximize-deep-linking"></a>Maximizar o vínculo profundo

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração, SharePoint*

Você pode criar links de informações e recursos no Teams. Use [links profundos](../concepts/build-and-test/deep-links.md) para vincular seu aplicativo com Teams à medida que eles vinculam várias partes de um aplicativo para uma experiência mais Teams nativa.

## <a name="be-smart-when-messaging-users"></a>Ser inteligente ao enviar mensagens aos usuários

***Cenários de integração**: aplicativos autônomos, aplicativos de colaboração, SharePoint*

Use um [bot](../bots/what-are-bots.md) em seu aplicativo Teams para conversa com vários threads, pois oferece mais flexibilidade do que um [webhook](../webhooks-and-connectors/what-are-webhooks-and-connectors.md).

Os bots também permitem que você envie mensagens **proativas** para usuários ou canais individuais. As mensagens proativas são mensagens não proativas disparadas por um evento externo e não uma mensagem enviada a um bot. Por exemplo, seu bot envia uma mensagem de boas-vindas quando ele é instalado ou um novo usuário ins junta um canal.

O envio de mensagens proativas requer Teams identificadores específicos. Você pode capturar as informações buscando dados [de lista ou](../bots/how-to/get-teams-context.md#fetch-the-roster-or-user-profile) perfil de usuário, [assinando](../bots/how-to/conversations/subscribe-to-conversation-events.md) eventos de conversa ou usando o [Microsoft Graph](/microsoftteams/platform/graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages?context=graph/context#proactive-messaging-in-teams).

Não spam usuários com mensagens excessivas. Se a Teams de usuário for compatível com ele, os usuários poderão configurar as configurações de notificação para seu aplicativo.
A seguir está um exemplo de uma mensagem de notificação: **Não me envie mensagens não prompadas**.

## <a name="use-sharepoint-for-file-and-data-storage"></a>Usar SharePoint para armazenamento de arquivos e dados

***Cenários de integração:** Aplicativos autônomos, aplicativos de colaboração, SharePoint páginas*

Quando uma equipe é criada, um [conjunto de sites](/microsoftteams/sharepoint-onedrive-interact) SharePoint também é provisionado para dar suporte ao armazenamento de arquivos e dados para essa equipe. Seu aplicativo deve aproveitar esse recurso se ele interagir com arquivos. Use o conjunto de sites para armazenar dados brutos em SharePoint Listas e Microsoft Excel.

## <a name="see-also"></a>Confira também

* [Integrar aplicativos Web](~/samples/integrate-web-apps-overview.md)
* [Soluções de código baixo e sem código para Microsoft Teams](~/samples/teams-low-code-solutions.md)
* [Criar um botão compartilhar para o Teams](../concepts/build-and-test/share-to-teams.md)
* [Atributos de cookie SameSite](~/resources/samesite-cookie-update.md)
* [Integrar Power Virtual Agents chatbot](~/bots/how-to/add-power-virtual-agents-bot-to-teams.md)
