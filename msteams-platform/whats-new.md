---
title: Novidades
description: Descreve todos os novos recursos de desenvolvedor no Microsoft Teams
ms.topic: reference
keywords: teams what's new latest
ms.openlocfilehash: 49603a9e48cd0a9951c6d9f0132a705770322de4
ms.sourcegitcommit: e3b6bc31059ec77de5fbef9b15c17d358abbca0f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/12/2021
ms.locfileid: "50231649"
---
# <a name="whats-new-for-developers-in-microsoft-teams"></a>Novidades para desenvolvedores no Microsoft Teams

>[!TIP]
> Confira nossos modelos prontos para produção no catálogo [**de Modelos de Aplicativos do Teams.**](samples/app-templates.md) O catálogo está em ordem alfabética e as adições mais novas são marcadas com uma estrela **&#9734;**.

## <a name="change-log"></a>Log de Alterações

O log de alterações lista as alterações feitas na plataforma do Microsoft Teams e neste conjunto de documentos. Às vezes, as entradas podem ser usadas para chamar a atenção para um novo recurso que é simplesmente de interesse para os desenvolvedores do Teams.

| **Date** | **Anotações** | **Tópicos alterados** |
| -------- | --------- | ------------------ |
|02/09/2021|Novo: Visão geral dos recursos adicionados ao dispositivo. <br/> Atualização: as informações de funcionalidade do microfone são adicionadas nas permissões do dispositivo nativo e integram arquivos de recursos de mídia.|[Visão geral,](concepts/device-capabilities/device-capabilities-overview.md) [Solicitar permissões do dispositivo,](concepts/device-capabilities/native-device-permissions.md)Integrar [recursos de mídia](concepts/device-capabilities/mobile-camera-image-permissions.md)|
|11/30/2020|Novo: integração da plataforma de identidade com o Kit de Ferramentas do Teams e o Visual Studio Code para guias|[Autenticação de login único com o Kit de Ferramentas do Teams e o Visual Studio Code para guias](toolkit/visual-studio-code-tab-sso.md)|
|11/16/2020|Manifesto do aplicativo Teams atualizado para a versão 1.8|[Referência: esquema de manifesto para o Microsoft Teams](resources/schema/manifest-schema.md)|
|11/10/2020|Diretrizes de design de bot do Teams|[Diretrizes de design de bot](bots/design/bots.md)|
|9/30/2020|Agora há suporte para o envio e o recebimento de arquivos para bots em dispositivos móveis.|[Enviar e receber arquivos por meio de seu bot](resources/bot-v3/bots-files.md)|
|09/22/2020|Novas diretrizes de "Começar a trabalhar com o Teams"|[Criar sua primeira visão geral do aplicativo Teams](build-your-first-app/build-first-app-overview.md)|
|9/18/2020|Suporte para aplicativos do Teams na reunião (Versão prévia)|[Criar aplicativos para reuniões e aplicativos](apps-in-teams-meetings/create-apps-for-teams-meetings.md) do Teams [em reuniões do Teams](apps-in-teams-meetings/teams-apps-in-meetings.md)|
|8/19/2020|Importar mensagens do Teams com o Microsoft Graph|[Importar mensagens de plataforma de terceiros para o Teams usando o Microsoft Graph](graph-api/import-messages/import-external-messages-to-teams.md)
| 08/12/2020 |Suporte a Cartões Adaptáveis no webhook de entrada movido para GA.|[Envie cartões adaptáveis usando um webhook de entrada](~/webhooks-and-connectors/how-to/connectors-using.md#send-adaptive-cards-using-an-incoming-webhook) |
|08/10/2020|Começar a criar aplicativos do Teams com o Visual Studio Toolkit.|[Criar aplicativos com o Kit de Ferramentas do Microsoft Teams e o Visual Studio Code](toolkit/visual-studio-overview.md) |
|08/06/2020|Suporte para autenticação SSO de Guias|[Desenvolver uma guia SSO do Microsoft Teams](tabs/how-to/authentication/auth-aad-sso.md#develop-an-sso-microsoft-teams-tab) |
|07/27/2020 | Bots e mensagens proativos do Graph (Visualização Pública)|[Habilitar a instalação proativa de bots e mensagens proativas no Teams com o Microsoft Graph](graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md)|
| 07/22/2020 |Atualizações de funcionalidade de dispositivo móvel.|[Solicitar permissões de dispositivo para sua guia do Microsoft Teams](concepts/device-capabilities/native-device-permissions.md) |
|07/20/2020|Ferramenta de Validação de Aplicativos do Teams para envios do AppSource.|[Ferramenta de Validação de Aplicativos do Teams](concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#teams-app-validation-tool)
|07/15/2020|Criar um assistente virtual para o Teams|[Assistente Virtual do Microsoft Teams](samples/virtual-assistant.md)|
|07/14/2020|Como navegar em uma documentação do indicador de carregamento nativo|[Mostrando um indicador de carregamento nativo](tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator)
|07/01/2020|Começar a criar aplicativos do Teams com o Kit de Ferramentas do Visual Studio Code.|[Criar aplicativos com o Kit de Ferramentas do Microsoft Teams e o Visual Studio Code](toolkit/visual-studio-code-overview.md) |
|07/01/2020|Single sign-on for tabs GA for Teams web and desktop clients|[Single Sign-On (SSO)](tabs/how-to/authentication/auth-aad-sso.md)|
|06/05/2020| Esquema de manifesto atualizado para a versão 1.7| [Referência: esquema de manifesto para o Microsoft Teams](resources/schema/manifest-schema.md)|
| 05/20/2020 | Permissões de consentimento específicas de recursos usando APIs do Microsoft Graph estão na visualização do desenvolvedor. |[Consentimento específico do recurso (RSC) — Visualização do Desenvolvedor](graph-api/rsc/resource-specific-consent.md) |
|5/18/2020|Integrar Agentes Virtuais Do Power com o Teams|[Integrar um chatbot de Agentes Virtuais Do Power com o Microsoft Teams](bots/how-to/add-power-virtual-agents-bot-to-teams.md)|
|04/01/2020|Integrar sistemas WFM com o Shifts Connector para o Teams|[Conectores WFM de turnos do Microsoft Teams](samples/shifts-wfm-connectors.md)
| 03/24/2020 | Adicionado suporte para recuperar um único membro de uma conversa e suporte adicional para recuperar membros pagedos. | [Obter o contexto do Teams para o seu bot](~/bots/how-to/get-teams-context.md)
| 12/26/2019 | O parâmetro em cargas enviadas para um bot não é mais criptografado, permitindo que você use esse valor para construir `replyToId` deeplinks para essas mensagens. As cargas de mensagens incluem os valores criptografados no parâmetro. `legacy.replyToId`.  |
| 11/5/2019 | O single sign-on usando o SDK do JavaScript do Teams em uma página de conteúdo da Web está na visualização do desenvolvedor. | [Logon único](tabs/how-to/authentication/auth-aad-sso.md) |
| 10/31/2019 | Documentação de bots de conversa e extensão de mensagens atualizada para refletir o SDK da Estrutura de Bot 4.6. A documentação do SDK v3 está disponível na seção Recursos. | Toda a documentação de extensão de bot e mensagens. |
| 10/31/2019 | Nova estrutura de documentação e refactoração de artigo principal. Informe links sem saída ou 404 por meio da criação de um problema do GitHub. | Todos eles! |
| 9/13/2019 | O bot de solicitação é instalado a partir da extensão de mensagens baseada em ação. | [Iniciar ações com extensões de mensagens](resources/messaging-extension-v3/create-extensions.md#request-to-install-your-conversational-bot)
| 8/28/2019 | Suporte para canais privados em guias e conectores. | [Obtenha contexto para sua guia](tabs/how-to/access-teams-context.md#retrieving-context-in-private-channels) |
| 06/20/2019 | Compartilhe um site externo, de um site externo, em um canal do Teams. | [Compartilhar com o Teams](~/share-to-teams.md) |
| 05/25/2019 | Responder com mensagem de bot do módulo de tarefa. | [Responder com mensagem de bot do módulo de tarefa](resources/messaging-extension-v3/create-extensions.md#respond-with-an-adaptive-card-message-sent-from-a-bot) |
| 05/25/2019 | Bots em chats em grupo. | [Interagir com um bot no chat de grupo ou canal](~/concepts/bots/bot-conversations/bots-conv-channel.md) |
| 05/20/2019 | Localização do manifesto do aplicativo. | [Localização de aplicativos](~/publishing/apps-localization.md) |
| 05/20/2019 | Ações de mensagem. | [Ações de mensagem](resources/messaging-extension-v3/create-extensions.md#action-type-message-extensions) |
| 05/20/2019 | Vincular desesqueamento (visualizações de URL personalizadas). | [Desenrolamento de link](messaging-extensions/how-to/link-unfurling.md)|
| 05/06/2019 | Programa de Certificação de Aplicativos para aplicativos da loja. | [Certificação de Aplicativos](~/publishing/application-certification.md) |
| 05/06/2019 | Os Modelos de Aplicativo agora estão disponíveis. | [Modelos de aplicativo](~/samples/app-templates.md) |
| 04/23/2019 | As Extensões de Mensagens baseadas em Ações agora estão disponíveis. | [Extensões de mensagem baseadas em ação](~/concepts/messaging-extensions/create-extensions.md) |
| 02/18/2019 | Criar links profundos para o chat privado está fora da visualização do desenvolvedor e disponível. | [Vinculação profunda a um chat](concepts/build-and-test/deep-links.md#deep-linking-to-a-chat) |
| 01/23/2019 | Informações de SKU e licenceType de navegação no contexto da guia. | [Contexto da guia](~/concepts/tabs/tabs-context.md) |
| 11/12/2018 | As guias no chat em grupo agora estão disponíveis na versão lançada do Teams e foram movidas da visualização do desenvolvedor. Como parte desse trabalho, a seção de guias foi reformulada para maior clareza.| [Guias configuráveis](~/concepts/tabs/tabs-configurable.md) |
| 11/11/2018 | A iniciação para o Nó JS e para .NET/C# foi atualizada para usar o App Studio no Teams, e uma nova seção foi adicionada sobre a hospedagem de aplicativos do Teams baseados em nós no Azure. | [Get started on the Microsoft Teams platform with C#/.NET and App Studio](~/get-started/get-started-dotnet-app-studio.md),  [Get started on the Microsoft Teams platform with Node JS and App Studio](~/get-started/get-started-nodejs-app-studio.md), [Host your Node Teams app in Azure](~/get-started/get-started-nodejs-in-azure.md)|
| 11/09/2018 | Agora você pode criar links profundos para chats privados entre usuários. | [Vinculação profunda a um chat](concepts/build-and-test/deep-links.md#deep-linking-to-a-chat) |
| 11/08/2018 | A Estrutura do SharePoint 1.7 enviou e com ela um novo recurso para usar a guia Microsoft Teams como uma web part da Estrutura do SharePoint. | [Guias no SharePoint](~/concepts/tabs/tabs-in-sharepoint.md) |
| 11/05/2018 | O recurso "módulo de tarefa" foi lançado. Um módulo de tarefa permite que você crie experiências de pop-up modais em seu aplicativo teams, a partir de bots e guias. Dentro do pop-up, você pode executar seu próprio código HTML/JavaScript personalizado, mostrar um widget baseado como um vídeo do YouTube ou do Microsoft Stream ou exibir um `<iframe>` [cartão adaptável.](https://docs.microsoft.com/adaptive-cards/) | [Visão geral do](~/concepts/task-modules/task-modules-overview.md)módulo de [tarefa, módulo de tarefa em guias](~/concepts/task-modules/task-modules-tabs.md), módulo de tarefa em  [bots](~/concepts/task-modules/task-modules-bots.md) |
| 10/05/2018 | As informações de formatação para cartões foram atualizadas e testadas nos clientes da área de trabalho, do iOS e do Android para o Teams. | [Cartões,](~/concepts/cards/cards.md) [formatação de cartão](~/concepts/cards/cards-format.md) |
| 09/24/2018 | As APIs de chamadas e reuniões online do Microsoft Graph foram lançadas para a versão beta, e os aplicativos do Teams agora podem interagir com os usuários de maneiras ricas usando voz e vídeo. | [Bots](~/concepts/calls-and-meetings/registering-calling-bot.md)de chamadas e reuniões [online, conceitos](~/concepts/calls-and-meetings/registering-calling-bot.md)de mídia em tempo [real,](~/concepts/calls-and-meetings/real-time-media-concepts.md)registro de um bot de chamada, [depuração](~/concepts/calls-and-meetings/debugging-local-testing-calling-meeting-bots.md)e teste local, mídia hospedada pelo [aplicativo,](~/concepts/calls-and-meetings/requirements-considerations-application-hosted-media-bots.md)manipulando notificações de chamada [de entrada](~/concepts/calls-and-meetings/call-notifications.md) |
| 09/11/2018 | As páginas de configuração de tabulação agora são significativamente maiores. | [Design da guia](tabs/design/tabs.md) |
| 08/15/2018 | Agora há suporte para cartões adaptáveis no Teams.|[Ações de cartão adaptáveis no Teams](task-modules-and-cards/cards/cards-reference.md#adaptive-card) |
| 08/10/2018 | O suporte ao cliente para DevTools foi documentado para a Visualização do Desenvolvedor.| [DevTools para o Cliente de Área de Trabalho do Microsoft Teams](~/resources/dev-preview/developer-preview-tools.md)|
| 08/08/2018 | As extensões de mensagens agora são compatíveis com vários comandos. Esse recurso está no Developer Preview e agora é lançado para todos os usuários.| [composeExtensions.commands](~/resources/schema/manifest-schema.md#composeextensionscommands)|
| 08/07/2018 | A configuração em linha agora tem suporte nos Conectores. A documentação dos Conectores também foi revisada e expandida para mais clareza.| [Conectores](~/concepts/connectors/connectors.md)|
| 08/06/2018 | Seu bot agora pode enviar e receber arquivos.| [Enviar e receber arquivos por meio de seu bot](~/concepts/bots/bots-files.md)|
| 07/27/2018 | A visualização do desenvolvedor agora dá suporte a vários comandos em extensões de mensagens. | [Extensões de mensagens foram estendidas](~/resources/dev-preview/developer-preview-features.md)|
| 07/23/2018 | Informações sobre a re-certificação de aplicativos foram adicionadas à seção Publicação. |[Permissões de manifesto](resources/schema/manifest-schema.md#permissions)|
| 07/16/2018 | Na visualização do desenvolvedor, mais espaço foi alocado para a página de configuração da guia. | [A página de configuração da guia é significativamente mais alta](tabs/design/tabs.md)|
| 07/12/2018 | Informações sobre o acesso de convidados. | [Acesso para convidado no Microsoft Teams](https://docs.microsoft.com/microsoftteams/guest-access#guest-access-overview)|
| 06/07/2018 | As informações de pré-lançamento do Catálogo de Aplicativos de Locatários do Microsoft Teams foram adicionadas. | [Publicar seu aplicativo do Microsoft Teams](~/publishing/apps-publish.md)|
| 05/31/2018 | A visualização do desenvolvedor do Teams (anel 3.6) foi atualizada para incluir a capacidade de adicionar bots e guias ao chat em grupo. | [Recursos na visualização do desenvolvedor,](~/resources/dev-preview/developer-preview-features.md) [esquema de visualização do desenvolvedor](~/resources/schema/manifest-schema-dev-preview.md)|
| 05/29/2018 | Agora há suporte para cartões adaptáveis no Teams nas [ações de cartão adaptáveis no Teams.](task-modules-and-cards/cards/cards-reference.md) |
| 05/29/2018 | Se você estiver usando a [visualização do desenvolvedor,](~/resources/dev-preview/developer-preview-intro.md)seu bot agora pode enviar e receber arquivos.| [Enviar e receber arquivos por meio de seu bot](~/concepts/bots/bots-files.md), Recursos na [Visualização pública do desenvolvedor para o Microsoft Teams](~/resources/dev-preview/developer-preview-features.md)|
| 04/17/2018 | replyToID foi adicionado à carga para as `Invoke` ações do cartão e do `MessageBack` cartão. Isso é especialmente útil se você precisar atualizar a mensagem de onde a ação do cartão veio. | [Ações do cartão](~/concepts/cards/cards-actions.md)|
| 04/12/2018 | Este tópico foi adicionado para controlar alterações na interface de programação do Teams e neste conjunto de documentação. | [Novidades](~/whats-new.md)|
| 04/10/2018 | Alterou as URLs de autenticação para usar consistentemente a ID de locatário no caminho. | [Fluxo de autenticação para guias,](~/concepts/authentication/auth-flow-tab.md) [autenticação de guia do AAD](~/concepts/authentication/auth-tab-AAD.md)|
| 04/06/2018 | Diretrizes de design adicionadas para usar a Caixa de Comando. |[Caixa de comando](~/resources/design/framework/command-box.md)|
| 04/02/2018 | Usar bots para enviar notificações para seu aplicativo. |[Bots somente de notificação](~/concepts/bots/bots-notification-only.md)|
| 03/27/2018 | Documentação expandida para mensagens proativas. |[Iniciar uma conversa](./concepts/bots/bot-conversations/bots-conv-proactive.md)|
| 03/15/2018 | Documentação refatorada para cartões. |[Cartões,](~/concepts/cards/cards.md) [ações de cartão,](~/concepts/cards/cards-actions.md) [formatação de cartão,](~/concepts/cards/cards-format.md) [referência de cartão](~/concepts/cards/cards-reference.md)|
| 03/03/2018 | Documentação adicionada para o Teams App Studio. |[Desenvolver rapidamente aplicativos com o Teams App Studio](~/get-started/get-started-app-studio.md), usando a biblioteca de controle no App [Studio](~/get-started/app-studio-component-library.md)|
| 02/27/2018 | Código de exemplo adicionado para demonstrar o método AsTeamsChannelAccounts(). |[Obter contexto para o bot](~/concepts/bots/bots-context.md)|
| 02/05/2018 | Tópicos adicionados para começar a usar C#. |[Introdução à plataforma do Microsoft Teams com C#/.NET](./get-started/get-started-dotnet-app-studio.md)|

## <a name="submit-your-questions-bugs-feature-requests-and-contributions"></a>Envie suas perguntas, bugs, solicitações de recursos e contribuições

Escutamos a comunidade de desenvolvedores em [vários canais.](feedback.md)
