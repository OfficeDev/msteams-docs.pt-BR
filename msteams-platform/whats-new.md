---
title: Novidades
description: Descreve todos os novos recursos de desenvolvedor no Microsoft Teams
ms.topic: reference
keywords: teams o que há de novo mais recente
ms.openlocfilehash: 298305f11788963817ddacfabbc052297d3eaabe
ms.sourcegitcommit: b50f6d68482cad43a60642a9947d1be17809a7df
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2021
ms.locfileid: "51634527"
---
# <a name="whats-new-for-developers-in-microsoft-teams"></a>Novidades para desenvolvedores no Microsoft Teams

>[!TIP]
> Confira soluções de exemplo para cenários de equipe comuns no catálogo de modelos [**de aplicativos do Teams**](samples/app-templates.md)! O catálogo é alfabético e as adições mais novas são marcadas com uma ☆.

## <a name="change-log"></a>Log de Alterações

O log de alterações lista as alterações na plataforma do Microsoft Teams e neste conjunto de documentos. Às vezes, as entradas podem ser usadas para chamar a atenção para um novo recurso que é simplesmente de interesse para os desenvolvedores do Teams.

| **Date** | **Anotações** | **Tópicos alterados** |
| -------- | --------- | ------------------ |
|04/08/2021| O recurso de personalização do aplicativo agora está disponível na visualização do desenvolvedor.|[Visão geral do aplicativo de equipes](concepts/design/design-teams-app-overview.md#app-customization)de [design, visão geral](concepts/build-and-test/app-studio-overview.md#connectors)do estúdio do aplicativo e [esquema de manifesto](resources/schema/manifest-schema-dev-preview.md) |
|03/18/2021|Aviso: atualize para a versão **4.10** ou acima do SDK da Estrutura de Bots conforme começamos com o processo de deprecação para `TeamsInfo.getMembers` e `TeamsInfo.GetMembersAsync` . | [Alterações na API de bot para membros da Equipe/Chat](resources/team-chat-member-api-changes.md) |
|03/05/2021|Aviso: as guias não terão mais margens ao redor de suas experiências. Os desenvolvedores de guias devem revisar e atualizar seus aplicativos. | [Removendo margens de tabulação](resources/removing-tab-margins.md) |
|03/05/2021 | O escopo de instalação padrão e a funcionalidade de grupo estão na visualização do desenvolvedor.| [Escopo de instalação padrão e funcionalidade de grupo](concepts/deploy-and-publish/apps-upload.md#add-a-default-install-scope-and-group-capability) |
|03/05/2021|Reordenar guias de aplicativo pessoal|[Reordenar a guia de chat em aplicativos pessoais](tabs/how-to/create-tab-pages/content-page.md#reorder-static-personal-tabs)|
|03/04/2021|Mascaramento de informações em cartões adaptáveis está na visualização do desenvolvedor.| [Mascaramento de informações em cartões adaptáveis](task-modules-and-cards/cards/cards-format.md#information-masking-in-adaptive-cards) |
|02/19/2021|Novo: adicionados recursos de localização. <br/> Atualização: Informações de recursos de localização são adicionadas na visão geral dos recursos do dispositivo, permissões de dispositivo nativas, integração de recursos de mídia e arquivos de recursos de QR ou scanner de código de barras.|[Visão](concepts/device-capabilities/device-capabilities-overview.md)geral , [Solicitar permissões de dispositivo,](concepts/device-capabilities/native-device-permissions.md) [Integrar](concepts/device-capabilities/mobile-camera-image-permissions.md)recursos de mídia, [Integrar a QR](concepts/device-capabilities/qr-barcode-scanner-capability.md)ou o recurso de scanner de código de barras, [Integrar recursos de localização](concepts/device-capabilities/location-capability.md) |
|02/18/2021|Novo: adicionado o recurso de QR ou scanner de código de barras. <br/> Atualização: as informações de recurso de QR ou scanner de código de barras são adicionadas na visão geral dos recursos do dispositivo, permissões de dispositivo nativas e integração de arquivos de recursos de mídia.|[Visão](concepts/device-capabilities/device-capabilities-overview.md)geral , [Solicitar permissões de dispositivo,](concepts/device-capabilities/native-device-permissions.md) [Integrar recursos de mídia,](concepts/device-capabilities/mobile-camera-image-permissions.md) [Integrar a QR ou o](concepts/device-capabilities/qr-barcode-scanner-capability.md) recurso de scanner de código de barras |
|02/09/2021|Novo: visão geral dos recursos do dispositivo adicionado. <br/> Atualização: As informações de funcionalidade do microfone são adicionadas às permissões do dispositivo nativo e integram arquivos de recursos de mídia.|[Visão](concepts/device-capabilities/device-capabilities-overview.md)geral , [Solicitar permissões de dispositivo,](concepts/device-capabilities/native-device-permissions.md) [Integrar recursos de mídia](concepts/device-capabilities/mobile-camera-image-permissions.md)|
|11/30/2020|Novo: integração da plataforma de identidade com o Teams Toolkit e Visual Studio Código para guias|[Autenticação de login único com o Teams Toolkit e Visual Studio Código para guias](toolkit/visual-studio-code-tab-sso.md)|
|11/16/2020|Manifesto do aplicativo do Teams atualizado para a versão 1.8|[Referência: esquema de manifesto para o Microsoft Teams](resources/schema/manifest-schema.md)|
|11/10/2020|Diretrizes de design de bot do Teams|[Diretrizes de design de bot](bots/design/bots.md)|
|9/30/2020|Agora há suporte para o envio e recebimento de arquivos para bots em dispositivos móveis.|[Enviar e receber arquivos por meio de seu bot](resources/bot-v3/bots-files.md)|
|09/22/2020|Novas diretrizes "Começar com o Teams"|[Criar sua primeira visão geral do aplicativo do Teams](build-your-first-app/build-first-app-overview.md)|
|9/18/2020|Suporte para aplicativos do Teams em reunião (Visualização de Versão)|[Criar aplicativos para reuniões e aplicativos do Teams](apps-in-teams-meetings/create-apps-for-teams-meetings.md) [em reuniões do Teams](apps-in-teams-meetings/teams-apps-in-meetings.md)|
|8/19/2020|Importar mensagens do Teams com o Microsoft Graph|[Importar mensagens de plataforma de terceiros para o Teams usando o Microsoft Graph](graph-api/import-messages/import-external-messages-to-teams.md)
| 08/12/2020 |Suporte a Cartões Adaptáveis no webhook de entrada movido para GA.|[Envie cartões adaptáveis usando um webhook de entrada](~/webhooks-and-connectors/how-to/connectors-using.md#send-adaptive-cards-using-an-incoming-webhook) |
|08/10/2020|Começar a criar aplicativos do Teams com o Visual Studio Toolkit.|[Criar aplicativos com o Microsoft Teams Toolkit e Visual Studio Código](toolkit/visual-studio-overview.md) |
|08/06/2020|Suporte para autenticação SSO de guias|[Desenvolver uma guia SSO do Microsoft Teams](tabs/how-to/authentication/auth-aad-sso.md#develop-an-sso-microsoft-teams-tab) |
|07/27/2020 | Bots e mensagens proativos do Graph (Visualização Pública)|[Habilitar a instalação proativa de bots e mensagens proativas no Teams com o Microsoft Graph](graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md)|
| 07/22/2020 |Atualizações de funcionalidade de dispositivo móvel.|[Solicitar permissões de dispositivo para a guia Microsoft Teams](concepts/device-capabilities/native-device-permissions.md) |
|07/20/2020|Ferramenta de Validação de Aplicativos do Teams para envios do AppSource.|[Ferramenta de Validação de Aplicativos do Teams](concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#teams-app-validation-tool)
|07/15/2020|Criar um assistente virtual para o Teams|[Assistente Virtual do Microsoft Teams](samples/virtual-assistant.md)|
|07/14/2020|Navegando em uma documentação de indicador de carregamento nativo|[Mostrando um indicador de carregamento nativo](tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator)
|07/01/2020|Começar a criar aplicativos do Teams com Visual Studio código Toolkit.|[Criar aplicativos com o Microsoft Teams Toolkit e Visual Studio Código](toolkit/visual-studio-code-overview.md) |
|07/01/2020|Login único para guias GA para clientes da Web e da área de trabalho do Teams|[Single Sign-On (SSO)](tabs/how-to/authentication/auth-aad-sso.md)|
|06/05/2020| Esquema de manifesto atualizado para a versão 1.7| [Referência: esquema de manifesto para o Microsoft Teams](resources/schema/manifest-schema.md)|
| 05/20/2020 | Permissões de consentimento específicas de recursos usando APIs do Microsoft Graph estão na visualização do desenvolvedor. |[Consentimento específico do recurso (RSC) — Visualização do Desenvolvedor](graph-api/rsc/resource-specific-consent.md) |
|5/18/2020|Integrar agentes virtuais do Power com o Teams|[Integrar um chatbot de Agentes Virtuais do Power com o Microsoft Teams](bots/how-to/add-power-virtual-agents-bot-to-teams.md)|
|04/01/2020|Integrar sistemas WFM com o Conector de Turnos para o Teams|[Microsoft Teams desloca conectores WFM](samples/shifts-wfm-connectors.md)
| 03/24/2020 | Adicionado suporte para recuperar um único membro de uma conversa e suporte adicional para recuperar membros pagedos. | [Obter o contexto do Teams para o seu bot](~/bots/how-to/get-teams-context.md)
| 12/26/2019 | O parâmetro em cargas enviadas a um bot não é mais criptografado, permitindo que você use esse valor para construir `replyToId` links profundos para essas mensagens. As cargas de mensagens incluem os valores criptografados no parâmetro. `legacy.replyToId`.  |
| 11/5/2019 | O login único usando o SDK JavaScript do Teams em uma página de conteúdo da Web está na visualização do desenvolvedor. | [Logon único](tabs/how-to/authentication/auth-aad-sso.md) |
| 10/31/2019 | Bots de conversa e documentação de extensão de mensagens atualizada para refletir o SDK da Estrutura de Bots 4.6. A documentação do SDK v3 está disponível na seção Recursos. | Toda a documentação de bot e extensão de mensagens. |
| 10/31/2019 | Nova estrutura de documentação e refatoria de artigos principais. Informe quaisquer links mortos ou 404s criando um Problema do GitHub. | Todos eles! |
| 9/13/2019 | O bot de solicitação é instalado a partir da extensão de mensagens baseada em ação. | [Iniciar ações com extensões de mensagens](resources/messaging-extension-v3/create-extensions.md#request-to-install-your-conversational-bot)
| 8/28/2019 | Suporte para canais privados em guias e conectores. | [Obter contexto para sua guia](tabs/how-to/access-teams-context.md#retrieving-context-in-private-channels) |
| 06/20/2019 | Compartilhe um site externo, de um site externo, em um canal do Teams. | [Compartilhar com o Teams](~/share-to-teams.md) |
| 05/25/2019 | Responder com a mensagem bot do módulo de tarefa. | [Responder com mensagem bot do módulo de tarefa](resources/messaging-extension-v3/create-extensions.md#respond-with-an-adaptive-card-message-sent-from-a-bot) |
| 05/25/2019 | Bots em chats de grupo. | [Interagir com um bot no chat de grupo ou canal](~/concepts/bots/bot-conversations/bots-conv-channel.md) |
| 05/20/2019 | Localização do manifesto do aplicativo. | [Localização de aplicativos](~/publishing/apps-localization.md) |
| 05/20/2019 | Ações de mensagem. | [Ações de mensagem](resources/messaging-extension-v3/create-extensions.md#action-type-message-extensions) |
| 05/20/2019 | Link desfraldado (visualizações de URL personalizadas). | [Desenrolamento de link](messaging-extensions/how-to/link-unfurling.md)|
| 05/06/2019 | Programa de certificação de aplicativos para aplicativos da loja. | [Certificação de Aplicativos](~/publishing/application-certification.md) |
| 05/06/2019 | Modelos de aplicativo agora estão disponíveis. | [Modelos de aplicativo](~/samples/app-templates.md) |
| 04/23/2019 | Extensões de Mensagens baseadas em ação agora estão disponíveis. | [Extensões de Mensagens baseadas em ação](~/concepts/messaging-extensions/create-extensions.md) |
| 02/18/2019 | A criação de links profundos para chat privado está fora da visualização do desenvolvedor e disponível. | [Vinculação profunda a um chat](concepts/build-and-test/deep-links.md#deep-linking-to-a-chat) |
| 01/23/2019 | Surfacing SKU and licenceType information in the tab context. | [Contexto de tabulação](~/concepts/tabs/tabs-context.md) |
| 11/12/2018 | As guias no chat em grupo agora estão disponíveis na versão lançada do Teams e foram movidas para fora da visualização do desenvolvedor. Como parte desse trabalho, a seção guias foi reformulada para maior clareza.| [Guias configuráveis](~/concepts/tabs/tabs-configurable.md) |
| 11/11/2018 | O início do Nó JS e do .NET/C# foi atualizado para usar o App Studio no Teams, e uma nova seção foi adicionada para hospedar aplicativos do Teams baseados em nó no Azure. | Começar a trabalhar na plataforma microsoft teams com [C#/.NET](~/get-started/get-started-dotnet-app-studio.md)e App Studio , Começar a plataforma do Microsoft Teams com [o Node JS](~/get-started/get-started-nodejs-app-studio.md)e o App Studio , hospedar seu aplicativo [Node Teams no Azure](~/get-started/get-started-nodejs-in-azure.md)|
| 11/09/2018 | Agora você pode criar links profundos para chats privados entre usuários. | [Vinculação profunda a um chat](concepts/build-and-test/deep-links.md#deep-linking-to-a-chat) |
| 11/08/2018 | O SharePoint Framework 1.7 enviou e com ele um novo recurso para usar a guia microsoft teams como uma web part da Estrutura do SharePoint. | [Guias no SharePoint](~/concepts/tabs/tabs-in-sharepoint.md) |
| 11/05/2018 | O recurso "módulo de tarefa" foi lançado. Um módulo de tarefa permite que você crie experiências pop-up modais em seu aplicativo teams, a partir de bots e guias. Dentro do pop-up, você pode executar seu próprio código HTML/JavaScript personalizado, mostrar um widget baseado como um vídeo do YouTube ou do Microsoft Stream ou exibir um cartão `<iframe>` [Adaptável](https://docs.microsoft.com/adaptive-cards/). | [Visão geral do](~/concepts/task-modules/task-modules-overview.md)módulo de tarefas , [módulo de tarefa em guias](~/concepts/task-modules/task-modules-tabs.md), módulo de tarefa em  [bots](~/concepts/task-modules/task-modules-bots.md) |
| 10/05/2018 | As informações de formatação para cartões foram atualizadas e testadas nos clientes desktop, iOS e Android para o Teams. | [Cartões,](~/concepts/cards/cards.md) [formatação de cartão](~/concepts/cards/cards-format.md) |
| 09/24/2018 | As APIs de chamadas e reuniões online do Microsoft Graph foram lançadas para beta, e os aplicativos do Teams agora podem interagir com os usuários de maneiras ricas usando voz e vídeo. | [Bots de](~/concepts/calls-and-meetings/registering-calling-bot.md)chamadas e reuniões online, conceitos de mídia em tempo [real,](~/concepts/calls-and-meetings/real-time-media-concepts.md)Registro de um [bot](~/concepts/calls-and-meetings/registering-calling-bot.md)de chamada, [Depuração](~/concepts/calls-and-meetings/debugging-local-testing-calling-meeting-bots.md)e teste local, mídia hospedada por [aplicativo,](~/concepts/calls-and-meetings/requirements-considerations-application-hosted-media-bots.md)Manipulação de notificações de chamada [de entrada](~/concepts/calls-and-meetings/call-notifications.md) |
| 09/11/2018 | As páginas de configuração de tabulação agora são significativamente mais altas. | [Design de tabulação](tabs/design/tabs.md) |
| 08/15/2018 | Cartões adaptáveis agora são suportados no Teams.|[Ações de cartão adaptáveis no Teams](task-modules-and-cards/cards/cards-reference.md#adaptive-card) |
| 08/10/2018 | O suporte ao cliente para DevTools foi documentado para o Developer Preview.| [DevTools para o cliente de área de trabalho do Microsoft Teams](~/resources/dev-preview/developer-preview-tools.md)|
| 08/08/2018 | As extensões de mensagens agora suportam vários comandos. Esse recurso foi lançado no Developer Preview e agora é lançado para todos os usuários.| [composeExtensions.commands](~/resources/schema/manifest-schema.md#composeextensionscommands)|
| 08/07/2018 | A configuração em linha agora é suportada em Conectores. A documentação conectores também foi revisada e expandida para maior clareza.| [Conectores](~/concepts/connectors/connectors.md)|
| 08/06/2018 | Seu bot agora pode enviar e receber arquivos.| [Enviar e receber arquivos por meio de seu bot](~/concepts/bots/bots-files.md)|
| 07/27/2018 | A visualização do desenvolvedor agora dá suporte a vários comandos em extensões de mensagens. | [Extensões de mensagens foram estendidas](~/resources/dev-preview/developer-preview-features.md)|
| 07/23/2018 | Informações sobre a re-certificação de aplicativos foram adicionadas à seção Publicação. |[Permissões de manifesto](resources/schema/manifest-schema.md#permissions)|
| 07/16/2018 | Na visualização do desenvolvedor, mais espaço foi alocado para a página de configuração de tabulação. | [A página de configuração de tabulação é significativamente mais alta](tabs/design/tabs.md)|
| 07/12/2018 | Informações sobre o acesso de convidados. | [Acesso para convidado no Microsoft Teams](https://docs.microsoft.com/microsoftteams/guest-access#guest-access-overview)|
| 06/07/2018 | Foram adicionadas informações de pré-lançamento para o Catálogo de Aplicativos de Locatários do Microsoft Teams. | [Publicar seu aplicativo do Microsoft Teams](~/publishing/apps-publish.md)|
| 05/31/2018 | A visualização do desenvolvedor do Teams (anel 3.6) foi atualizada para incluir a capacidade de adicionar bots e guias ao chat em grupo. | [Recursos na visualização do desenvolvedor](~/resources/dev-preview/developer-preview-features.md), [esquema de visualização do desenvolvedor](~/resources/schema/manifest-schema-dev-preview.md)|
| 05/29/2018 | Cartões adaptáveis agora são suportados no Teams nas [ações de cartão adaptáveis no Teams](task-modules-and-cards/cards/cards-reference.md). |
| 05/29/2018 | Se você estiver usando a visualização [do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md), seu bot poderá enviar e receber arquivos.| [Enviar e receber arquivos por meio de seu bot](~/concepts/bots/bots-files.md), Recursos na [Visualização de Desenvolvedor Público para o Microsoft Teams](~/resources/dev-preview/developer-preview-features.md)|
| 04/17/2018 | replyToID foi adicionado à carga para as `Invoke` ações `MessageBack` de cartão e. Isso é especialmente útil se você precisar atualizar a mensagem de onde a ação do cartão veio. | [Ações de cartão](~/concepts/cards/cards-actions.md)|
| 04/12/2018 | Este tópico foi adicionado para acompanhar as alterações na interface de programação do Teams e neste conjunto de documentação. | [Novidades](~/whats-new.md)|
| 04/10/2018 | As URLs de autenticação alteradas para usar consistentemente a ID do locatário no caminho. | [Fluxo de autenticação para guias,](~/concepts/authentication/auth-flow-tab.md) [autenticação de guia AAD](~/concepts/authentication/auth-tab-AAD.md)|
| 04/06/2018 | Foram adicionadas diretrizes de design para usar a Caixa de Comando. |[Caixa de comando](~/resources/design/framework/command-box.md)|
| 04/02/2018 | Usando bots para enviar notificações para seu aplicativo. |[Bots somente de notificação](~/concepts/bots/bots-notification-only.md)|
| 03/27/2018 | Documentação expandida para mensagens proativas. |[Iniciar uma conversa](./concepts/bots/bot-conversations/bots-conv-proactive.md)|
| 03/15/2018 | Documentação refatorada para cartões. |[Cartões,](~/concepts/cards/cards.md) [Ações de cartão,](~/concepts/cards/cards-actions.md) [formatação de cartão,](~/concepts/cards/cards-format.md) [referência de cartão](~/concepts/cards/cards-reference.md)|
| 03/03/2018 | Adicionada documentação para o Teams App Studio. |[Desenvolver rapidamente aplicativos com o Teams App Studio](~/get-started/get-started-app-studio.md), usando a biblioteca de controle no App [Studio](~/get-started/app-studio-component-library.md)|
| 02/27/2018 | Adicionado código de exemplo para demonstrar o método AsTeamsChannelAccounts(). |[Obter contexto para o bot](~/concepts/bots/bots-context.md)|
| 02/05/2018 | Foram adicionados tópicos para começar a usar C#. |[Introdução à plataforma do Microsoft Teams com C#/.NET](./get-started/get-started-dotnet-app-studio.md)|

## <a name="submit-your-questions-bugs-feature-requests-and-contributions"></a>Enviar suas perguntas, bugs, solicitações de recursos e contribuições

Escutamos a comunidade de desenvolvedores em [vários canais.](feedback.md)
