---
title: Novidades
description: Descreve todos os novos recursos de desenvolvedor no Microsoft Teams
ms.topic: reference
localization_priority: Normal
keywords: teams o que há de novo mais recente
ms.openlocfilehash: 449df27aaa28b0ba15c98efa78f93f74b8446920
ms.sourcegitcommit: 20e623a82f9676dd036cf6a350dd480885e0ea2c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2021
ms.locfileid: "52300567"
---
# <a name="whats-new-for-developers-in-microsoft-teams"></a>Novidades para desenvolvedores no Microsoft Teams

Descubra Microsoft Teams da plataforma que estão geralmente disponíveis (GA) e na visualização do desenvolvedor.

## <a name="ga-features"></a>Recursos GA

Microsoft Teams da plataforma que estão disponíveis para todos os desenvolvedores de aplicativos.

<br>

<details>

<summary><b>2021</b></summary>

| **Date** | **Anotações** | **Tópicos alterados** |
| -------- | --------- | ------------------ |
|05/07/2021| Links profundos para chamadas de áudio e vídeo no chat. |[Links profundos](concepts/build-and-test/deep-links.md#deep-linking-to-an-audio-or-audio-video-call)
|04/30/2021|Novas diretrizes sobre como publicar aplicativos no Teams store.|[Publique seu aplicativo no Teams,](concepts/deploy-and-publish/appsource/publish.md)Teams [de validação da loja](concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md) |
|04/29/2021 | Novo: Ações universais para cartões adaptáveis. | [Ações Universais para Cartões Adaptáveis](task-modules-and-cards/cards/universal-actions-for-adaptive-cards/overview.md) |
|03/18/2021|Aviso: atualize para a versão 4.10 ou acima do SDK da Estrutura de Bots, conforme começamos com o processo de deprecação para `TeamsInfo.getMembers` e `TeamsInfo.GetMembersAsync` . | [Alterações na API de bot para membros da Equipe/Chat](resources/team-chat-member-api-changes.md) |
|03/05/2021|Aviso: as guias não terão mais margens ao redor de suas experiências. Os desenvolvedores de guias devem revisar e atualizar seus aplicativos. | [Removendo margens de tabulação](resources/removing-tab-margins.md) |
|03/05/2021|O escopo de instalação padrão e a funcionalidade de grupo estão na visualização do desenvolvedor.| [Escopo de instalação padrão e funcionalidade de grupo](concepts/deploy-and-publish/add-default-install-scope.md) |
|03/05/2021|Reordenar guias de aplicativo pessoal|[Reordenar a guia de chat em aplicativos pessoais](tabs/how-to/create-tab-pages/content-page.md#reorder-static-personal-tabs)|
|03/04/2021|Mascaramento de informações em cartões adaptáveis.| [Mascaramento de informações em cartões adaptáveis](task-modules-and-cards/cards/cards-format.md#information-masking-in-adaptive-cards) |
|02/19/2021|Recursos de localização adicionados. <br/> As informações de recursos de localização são adicionadas na visão geral dos recursos do dispositivo, permissões de dispositivo nativas, integração de recursos de mídia e arquivos de recursos de QR ou scanner de código de barras.|[Visão](concepts/device-capabilities/device-capabilities-overview.md)geral , [Solicitar permissões de dispositivo,](concepts/device-capabilities/native-device-permissions.md) [Integrar](concepts/device-capabilities/mobile-camera-image-permissions.md)recursos de mídia, [Integrar a QR](concepts/device-capabilities/qr-barcode-scanner-capability.md)ou o recurso de scanner de código de barras, [Integrar recursos de localização](concepts/device-capabilities/location-capability.md) |
|02/18/2021|Adicionado o recurso de QR ou scanner de código de barras. <br/> As informações de recurso de QR ou scanner de código de barras são adicionadas na visão geral dos recursos do dispositivo, permissões de dispositivo nativas e arquivos de recursos de mídia de integração.|[Visão](concepts/device-capabilities/device-capabilities-overview.md)geral , [Solicitar permissões de dispositivo,](concepts/device-capabilities/native-device-permissions.md) [Integrar recursos de mídia,](concepts/device-capabilities/mobile-camera-image-permissions.md) [Integrar a QR ou o](concepts/device-capabilities/qr-barcode-scanner-capability.md) recurso de scanner de código de barras |
|02/09/2021|Visão geral dos recursos do dispositivo adicionado. <br/> As informações de funcionalidade do microfone são adicionadas às permissões do dispositivo nativo e integram arquivos de recursos de mídia.|[Visão](concepts/device-capabilities/device-capabilities-overview.md)geral , [Solicitar permissões de dispositivo,](concepts/device-capabilities/native-device-permissions.md) [Integrar recursos de mídia](concepts/device-capabilities/mobile-camera-image-permissions.md)|

<br>

</details>

<br>

<details>
  
<summary><b>2020</b></summary>

| **Date** | **Anotações** | **Tópicos alterados** |
| -------- | --------- | ------------------ |
|11/30/2020|Integração da plataforma de identidade com Teams Toolkit e Visual Studio Code para guias|[Autenticação de login único com Teams Toolkit e Visual Studio Code para guias](toolkit/visual-studio-code-tab-sso.md)|
|11/16/2020|Teams manifesto do aplicativo atualizado para a versão 1.8|[Referência: esquema de manifesto para Microsoft Teams](resources/schema/manifest-schema.md)|
|11/10/2020|Teams de design de bot|[Diretrizes de design de bot](bots/design/bots.md)|
|09/30/2020|Agora há suporte para o envio e recebimento de arquivos para bots em dispositivos móveis.|[Enviar e receber arquivos por meio de seu bot](resources/bot-v3/bots-files.md)|
|09/22/2020|Novas informações para começar a Teams desenvolvimento.|[Criar sua primeira visão geral Teams aplicativo](build-your-first-app/build-first-app-overview.md)|
|09/18/2020|Suporte para aplicativos de Teams de reunião (Visualização de Versão).|[Criar aplicativos para Teams reuniões e](apps-in-teams-meetings/create-apps-for-teams-meetings.md) [aplicativos em Teams reuniões](apps-in-teams-meetings/teams-apps-in-meetings.md)|
|08/19/2020|Importe Teams mensagens com o Microsoft Graph.|[Importar mensagens de plataforma de terceiros para o Teams usando o Microsoft Graph](graph-api/import-messages/import-external-messages-to-teams.md)
| 08/12/2020 |Suporte a Cartões Adaptáveis no webhook de entrada movido para GA.|[Envie cartões adaptáveis usando um webhook de entrada](~/webhooks-and-connectors/how-to/connectors-using.md#send-adaptive-cards-using-an-incoming-webhook) |
|08/10/2020|Começar a criar Teams aplicativos com o Visual Studio Toolkit.|[Criar aplicativos com o Microsoft Teams Toolkit e Visual Studio Code](toolkit/visual-studio-overview.md) |
|08/06/2020|Suporte para autenticação SSO de guias.|[Desenvolver uma guia de Microsoft Teams SSO](tabs/how-to/authentication/auth-aad-sso.md#develop-an-sso-microsoft-teams-tab) |
|07/27/2020 | Graph bots e mensagens proativos (Visualização Pública).|[Habilitar a instalação proativa de bots e mensagens proativas Teams com o Microsoft Graph](graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md)|
| 07/22/2020 |Atualizações de funcionalidade de dispositivo móvel.|[Solicitar permissões de dispositivo para sua guia Microsoft Teams de usuário](concepts/device-capabilities/native-device-permissions.md) |
|07/20/2020|Teams App Validation Tool for AppSource submissions.|[Teams Ferramenta de Validação de Aplicativos](concepts/deploy-and-publish/appsource/prepare/submission-checklist.md)
|07/15/2020|Crie um assistente virtual para Teams.|[Assistente Virtual para Microsoft Teams](samples/virtual-assistant.md)|
|07/14/2020|Navegando em uma documentação de indicador de carregamento nativo.|[Mostrando um indicador de carregamento nativo](tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator)
|07/01/2020|Começar a criar Teams aplicativos com o Visual Studio Code Toolkit.|[Criar aplicativos com o Microsoft Teams Toolkit e Visual Studio Code](toolkit/visual-studio-code-overview.md) |
|07/01/2020|Login único para guias GA para clientes Teams web e desktop.|[Single Sign-On (SSO)](tabs/how-to/authentication/auth-aad-sso.md)|
|06/05/2020| Esquema de manifesto atualizado para a versão 1.7.| [Referência: esquema de manifesto para Microsoft Teams](resources/schema/manifest-schema.md)|
|05/18/2020|Integre Power Virtual Agents com Teams.|[Integrar um Power Virtual Agents chatbot com Microsoft Teams](bots/how-to/add-power-virtual-agents-bot-to-teams.md)|
|04/01/2020|Integrar sistemas WFM com o Conector de Turnos para Teams.|[Microsoft Teams Desloca conectores WFM](samples/shifts-wfm-connectors.md)
| 03/24/2020 | Adicionado suporte para recuperar um único membro de uma conversa e suporte adicional para recuperar membros pagedos. | [Obter o contexto do Teams para o seu bot](~/bots/how-to/get-teams-context.md) |

<br>

</details>

<br>

<details>
  
<summary><b>2019</b></summary>

| **Date** | **Anotações** | **Tópicos alterados** |
| -------- | --------- | ------------------ |
| 12/26/2019 | O parâmetro em cargas enviadas a um bot não é mais criptografado, permitindo que você use esse valor para construir `replyToId` links profundos para essas mensagens. As cargas de mensagens incluem os valores criptografados no parâmetro. `legacy.replyToId`.  |
| 11/05/2019 | Login único usando o Teams JavaScript SDK. | [Logon único](tabs/how-to/authentication/auth-aad-sso.md) |
| 10/31/2019 | Bots de conversa e documentação de extensão de mensagens atualizada para refletir o SDK da Estrutura de Bots 4.6. A documentação do SDK v3 está disponível na seção Recursos. | Toda a documentação de bot e extensão de mensagens. |
| 10/31/2019 | Nova estrutura de documentação e refatoria de artigos principais. Informe quaisquer links mortos ou 404s criando um problema GitHub. | Todos eles! |
| 09/13/2019 | O bot de solicitação é instalado a partir da extensão de mensagens baseada em ação. | [Iniciar ações com extensões de mensagens](resources/messaging-extension-v3/create-extensions.md#request-to-install-your-conversational-bot)
| 08/28/2019 | Suporte para canais privados em guias e conectores. | [Obtenha contexto para sua guia](tabs/how-to/access-teams-context.md#retrieving-context-in-private-channels) |
| 06/20/2019 | Compartilhe um site externo, de um site externo, em um Teams canal. | [Compartilhar com Teams](~/share-to-teams.md) |
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

<br>

</details>

<br>

<details>

<summary><b>2018</b></summary>

| **Date** | **Anotações** | **Tópicos alterados** |
| -------- | --------- | ------------------ |
| 11/12/2018 | As guias no chat em grupo agora estão disponíveis na versão lançada do Teams e foram movidas para fora da visualização do desenvolvedor. Como parte desse trabalho, a seção guias foi reformulada para maior clareza.| [Guias configuráveis](~/concepts/tabs/tabs-configurable.md) |
| 11/11/2018 | O início do Nó JS e do .NET/C# foi atualizado para usar o App Studio no Teams, e uma nova seção foi adicionada para hospedar aplicativos Teams baseados em nó no Azure. | Começar Microsoft Teams plataforma Microsoft Teams com [o C#/.NET](~/get-started/get-started-dotnet-app-studio.md)e o App Studio , Iniciar na plataforma Microsoft Teams com [o Node JS](~/get-started/get-started-nodejs-app-studio.md)e o App Studio, hospedar seu aplicativo node Teams no [Azure](~/get-started/get-started-nodejs-in-azure.md)|
| 11/09/2018 | Agora você pode criar links profundos para chats privados entre usuários. | [Vinculação profunda a um chat](concepts/build-and-test/deep-links.md#deep-linking-to-a-chat) |
| 11/08/2018 | Estrutura do SharePoint 1.7 enviou e com ele um novo recurso para usar Microsoft Teams guia como uma web part Estrutura do SharePoint web part. | [Guias no SharePoint](~/concepts/tabs/tabs-in-sharepoint.md) |
| 11/05/2018 | O recurso "módulo de tarefa" foi lançado. Um módulo de tarefa permite que você crie experiências pop-up modais em seu aplicativo Teams, a partir de bots e guias. Dentro do pop-up, você pode executar seu próprio código HTML/JavaScript personalizado, mostrar um widget baseado como um vídeo do YouTube ou do Microsoft Stream ou exibir um cartão `<iframe>` [Adaptável](https://docs.microsoft.com/adaptive-cards/). | [Visão geral do](~/concepts/task-modules/task-modules-overview.md)módulo de tarefas , [módulo de tarefa em guias](~/concepts/task-modules/task-modules-tabs.md), módulo de tarefa em  [bots](~/concepts/task-modules/task-modules-bots.md) |
| 10/05/2018 | As informações de formatação para cartões foram atualizadas e testadas nos clientes desktop, iOS e Android para Teams. | [Cartões,](~/concepts/cards/cards.md) [formatação de cartão](~/concepts/cards/cards-format.md) |
| 09/24/2018 | As APIs de chamadas e reuniões online da Microsoft Graph foram lançadas para a versão beta, e Teams aplicativos agora podem interagir com os usuários de maneiras ricas usando voz e vídeo. | [Bots de](~/concepts/calls-and-meetings/registering-calling-bot.md)chamadas e reuniões online, conceitos de mídia em tempo [real,](~/concepts/calls-and-meetings/real-time-media-concepts.md)Registro de um [bot](~/concepts/calls-and-meetings/registering-calling-bot.md)de chamada, [Depuração](~/concepts/calls-and-meetings/debugging-local-testing-calling-meeting-bots.md)e teste local, mídia hospedada por [aplicativo,](~/concepts/calls-and-meetings/requirements-considerations-application-hosted-media-bots.md)Manipulação de notificações de chamada [de entrada](~/concepts/calls-and-meetings/call-notifications.md) |
| 09/11/2018 | As páginas de configuração de tabulação agora são significativamente mais altas. | [Design de tabulação](tabs/design/tabs.md) |
| 08/15/2018 | Cartões adaptáveis agora são suportados em Teams.|[Ações de cartão adaptáveis em Teams](task-modules-and-cards/cards/cards-reference.md#adaptive-card) |
| 08/10/2018 | Suporte para cliente para DevTools.| [DevTools para o cliente Microsoft Teams desktop](~/resources/dev-preview/developer-preview-tools.md)|
| 08/08/2018 | As extensões de mensagens agora suportam vários comandos. Esse recurso foi lançado no Developer Preview e agora é lançado para todos os usuários.| [composeExtensions.commands](~/resources/schema/manifest-schema.md#composeextensionscommands)|
| 08/07/2018 | A configuração em linha agora é suportada em Conectores. A documentação conectores também foi revisada e expandida para maior clareza.| [Conectores](~/concepts/connectors/connectors.md)|
| 08/06/2018 | Seu bot agora pode enviar e receber arquivos.| [Enviar e receber arquivos por meio de seu bot](~/concepts/bots/bots-files.md)|
| 07/23/2018 | Informações sobre a re-certificação de aplicativos foram adicionadas à seção Publicação. |[Permissões de manifesto](resources/schema/manifest-schema.md#permissions)|
| 07/16/2018 | Mais espaço foi alocado para a página de configuração de tabulação. | [A página de configuração de tabulação é significativamente mais alta](tabs/design/tabs.md)|
| 07/12/2018 | Informações sobre o acesso de convidados. | [Acesso para convidado no Microsoft Teams](https://docs.microsoft.com/microsoftteams/guest-access#guest-access-overview)|
| 06/07/2018 | Foram adicionadas informações Microsoft Teams catálogo de aplicativos de locatários. | [Publicar seu Microsoft Teams app](~/publishing/apps-publish.md)|
| 05/29/2018 | Os cartões adaptáveis são suportados em Teams. | [Ações de cartão adaptáveis em Teams](task-modules-and-cards/cards/cards-reference.md) |
| 04/17/2018 | replyToID foi adicionado à carga para as `Invoke` ações `MessageBack` de cartão e. Isso é especialmente útil se você precisar atualizar a mensagem de onde a ação do cartão veio. | [Ações de cartão](~/concepts/cards/cards-actions.md)|
| 04/12/2018 | Este tópico foi adicionado para acompanhar as alterações na interface Teams de programação e neste conjunto de documentação. | [Novidades](~/whats-new.md)|
| 04/10/2018 | As URLs de autenticação alteradas para usar consistentemente a ID do locatário no caminho. | [Fluxo de autenticação para guias,](~/concepts/authentication/auth-flow-tab.md) [autenticação de guia AAD](~/concepts/authentication/auth-tab-AAD.md)|
| 04/06/2018 | Foram adicionadas diretrizes de design para usar a Caixa de Comando. |[Caixa de comando](~/resources/design/framework/command-box.md)|
| 04/02/2018 | Usando bots para enviar notificações para seu aplicativo. |[Bots somente de notificação](~/concepts/bots/bots-notification-only.md)|
| 03/27/2018 | Documentação expandida para mensagens proativas. |[Iniciar uma conversa](./concepts/bots/bot-conversations/bots-conv-proactive.md)|
| 03/15/2018 | Documentação refatorada para cartões. |[Cartões,](~/concepts/cards/cards.md) [Ações de cartão,](~/concepts/cards/cards-actions.md) [formatação de cartão,](~/concepts/cards/cards-format.md) [referência de cartão](~/concepts/cards/cards-reference.md)|
| 03/03/2018 | Adicionada documentação para Teams App Studio. |[Desenvolver rapidamente aplicativos com Teams App Studio](~/get-started/get-started-app-studio.md), usando a biblioteca de controle no App [Studio](~/get-started/app-studio-component-library.md)|
| 02/27/2018 | Adicionado código de exemplo para demonstrar o método AsTeamsChannelAccounts(). |[Obter contexto para o bot](~/concepts/bots/bots-context.md)|
| 02/05/2018 | Foram adicionados tópicos para começar a usar C#. |[Introdução à plataforma do Microsoft Teams com C#/.NET](./get-started/get-started-dotnet-app-studio.md)|

<br>

</details>

## <a name="developer-preview"></a>Visualização do Desenvolvedor

A visualização do desenvolvedor é um programa público que fornece acesso antecipado a recursos Teams plataforma não lançados.  

| **Date** | **Anotações** | **Tópicos alterados** |
| -------- | --------- | ------------------ |
|04/08/2021| O recurso de personalização do aplicativo agora está disponível na visualização do desenvolvedor.|[Design Teams visão geral do aplicativo,](concepts/design/design-teams-app-overview.md#app-customization) [visão geral do App Studio](concepts/build-and-test/app-studio-overview.md#connectors)e esquema de [manifesto](resources/schema/manifest-schema-dev-preview.md) |
|03/05/2021| As guias não terão mais margens ao redor de suas experiências. Os desenvolvedores de guias devem revisar e atualizar seus aplicativos. | [Removendo margens de tabulação](resources/removing-tab-margins.md) |

Para obter mais informações, consulte [visualização do desenvolvedor público para Teams](~/resources/dev-preview/developer-preview-intro.md).

## <a name="teams-app-template-catalog"></a>Teams de modelos de aplicativo

Junto com novos recursos, também fornecemos modelos de aplicativos prontos para [produção Teams](samples/app-templates.md) que você pode implantar imediatamente ou modificar às suas necessidades. Modelos recém-adicionados são indicados com uma ☆.

## <a name="submit-your-feedback"></a>Enviar seus comentários

Incentivamos Teams desenvolvedores a fazer perguntas, bugs de arquivo, enviar solicitações de recursos e fazer contribuições. Você pode enviar comentários por meio de qualquer [um dos canais disponíveis.](feedback.md)
