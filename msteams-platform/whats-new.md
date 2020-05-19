---
title: Novidades
description: Descreve todos os novos recursos de desenvolvedor no Microsoft Teams
keywords: Teams novidades mais recentes
ms.openlocfilehash: de3366594d58996b689fc3d50f41a70ff80facee
ms.sourcegitcommit: 28af65730884b788ff77a4ec4032219380df8b70
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "44281829"
---
# <a name="whats-new-for-developers-in-microsoft-teams"></a>O que há de novo para desenvolvedores no Microsoft Teams

## <a name="change-log"></a>Log de Alterações

O log de alterações lista as alterações na plataforma do Microsoft Teams e no conjunto de documentos. Às vezes, as entradas podem ser usadas para chamar a atenção para um novo recurso que é simplesmente de interesse para desenvolvedores do teams.

| **Date** | **Anotações** | **Tópicos alterados** |
| -------- | --------- | ------------------ |
| 03/24/2020 | Adicionado suporte para recuperar um único membro de uma conversa e suporte adicional para recuperar Membros paginados. | [Obter o contexto do Teams para o seu bot](~/bots/how-to/get-teams-context.md)
| 12/26/2019 | O `replyToId` parâmetro em cargas enviadas a um bot não é mais criptografado, permitindo que você use esse valor para construir o deeplinks a essas mensagens. As cargas de mensagens incluem os valores criptografados no parâmetro `legacy.replyToId` .  |
| 11/5/2019 | O logon único usando o SDK do teams JavaScript em uma página de conteúdo da Web está em visualização do desenvolvedor | [Logon único](tabs/how-to/authentication/auth-aad-sso.md) |
| 10/31/2019 | Documentação de bots e de mensagens de emails de conversa atualizada para refletir o SDK da estrutura de bot 4,6. A documentação do SDK do v3 está disponível na seção recursos. | Toda documentação de bot e de extensão de mensagens. |
| 10/31/2019 | Nova estrutura de documentação e refatoração de artigo principal. Informe os links inativos ou 404 criando um problema do GitHub | Todos eles! |
| 9/13/2019 | O bot de solicitação é instalado a partir da extensão de mensagens baseada na ação | [Iniciar ações com extensões de mensagens](resources/messaging-extension-v3/create-extensions.md#request-to-install-your-conversational-bot)
| 8/28/2019 | Suporte para canais privados em guias e conectores | [Obter contexto para a guia](tabs/how-to/access-teams-context.md#retrieving-context-in-private-channels) |
| 06/20/2019 | Compartilhar um site externo de um site externo em um canal do teams | [Compartilhar com o Teams](~/share-to-teams.md) |
| 05/25/2019 | Responder com mensagem de bot do módulo de tarefas | [Responder com mensagem de bot do módulo de tarefas](resources/messaging-extension-v3/create-extensions.md#respond-with-an-adaptive-card-message-sent-from-a-bot) |
| 05/25/2019 | Bots em bate-papos em grupo | [Interagir com um bot em um chat de grupo ou canal](~/concepts/bots/bot-conversations/bots-conv-channel.md) |
| 05/20/2019 | Localização do manifesto do aplicativo | [Localização do aplicativo](~/publishing/apps-localization.md) |
| 05/20/2019 | Ações de mensagem | [Ações de mensagem](resources/messaging-extension-v3/create-extensions.md#action-type-message-extensions) |
| 05/20/2019 | Link Unfurling (visualizações de URL personalizadas) | [Desenrolamento de link](messaging-extensions/how-to/link-unfurling.md)|
| 05/06/2019 | Programa de certificação de aplicativos para aplicativos de armazenamento | [Certificação de aplicativos](~/publishing/application-certification.md) |
| 05/06/2019 | Os modelos de aplicativos já estão disponíveis. | [Modelos de aplicativos](~/samples/app-templates.md) |
| 04/23/2019 | Extensões de mensagens baseadas em ação agora estão disponíveis | [Extensões de mensagem baseadas em ação](~/concepts/messaging-extensions/create-extensions.md) |
| 02/18/2019 | A criação de links detalhados para o chat privado está fora do Developer Preview e disponível | [Vinculação profunda a um chat](concepts/build-and-test/deep-links.md#deep-linking-to-a-chat) |
| 01/23/2019 | Revelar informações de SKU e de licenciamento no contexto da guia | [Contexto da guia](~/concepts/tabs/tabs-context.md) |
| 11/12/2018 | As guias no chat de grupo agora estão disponíveis na versão de lançamento do Teams e foram movidas para a visualização do desenvolvedor. Como parte desse trabalho, a seção Tabs foi reformulada para maior clareza.| [Guias configuráveis](~/concepts/tabs/tabs-configurable.md) |
| 11/11/2018 | A introdução ao node JS e ao .NET/C# foi atualizada para usar o app Studio no Teams e uma nova seção foi adicionada ao Hospedagem de aplicativos de equipes baseados em nós no Azure. | [Introdução à plataforma do Microsoft Teams com o C#/.net e o app Studio](~/get-started/get-started-dotnet-app-studio.md), [introdução à plataforma do Microsoft Teams com o nó js e o app Studio](~/get-started/get-started-nodejs-app-studio.md), [hospedam o seu aplicativo do nó Teams no Azure](~/get-started/get-started-nodejs-in-azure.md)|
| 11/09/2018 | Agora você pode criar links detalhados para chats privados entre usuários. | [Vinculação profunda a um chat](concepts/build-and-test/deep-links.md#deep-linking-to-a-chat) |
| 11/08/2018 | A estrutura do SharePoint 1,7 foi fornecida e com uma nova funcionalidade para usar a guia Microsoft Teams como uma Web Part da estrutura do SharePoint. | [Guias no SharePoint](~/concepts/tabs/tabs-in-sharepoint.md) |
| 11/05/2018 | O recurso "módulo de tarefa" foi lançado. Um módulo de tarefa permite que você crie experiências pop-up restritas em seu aplicativo do Microsoft Teams, dos bots e das guias. Dentro do pop-up, você pode executar seu próprio código HTML/JavaScript personalizado, mostrar um `<iframe>` widget baseado em um YouTube ou Microsoft Stream Video, ou exibir um [cartão adaptável](https://docs.microsoft.com/adaptive-cards/). | [Visão geral do módulo de tarefa](~/concepts/task-modules/task-modules-overview.md), [módulo de tarefa em guias](~/concepts/task-modules/task-modules-tabs.md), [módulo de tarefa em bots](~/concepts/task-modules/task-modules-bots.md) |
| 10/05/2018 | As informações de formatação de cartões foram atualizadas e testadas nos clientes de desktop, iOS e Android para o Microsoft Teams. | [Cartões](~/concepts/cards/cards.md), [formatação de cartão](~/concepts/cards/cards-format.md) |
| 09/24/2018 | As chamadas e as APIs de reuniões online para o Microsoft Graph foram lançadas para a versão beta, e os aplicativos do teams agora podem interagir com os usuários de formas sofisticadas usando voz e vídeo. | [Chamadas e bots de reuniões online](~/concepts/calls-and-meetings/registering-calling-bot.md), [conceitos de mídia em tempo real](~/concepts/calls-and-meetings/real-time-media-concepts.md), [registro de um bot de chamada](~/concepts/calls-and-meetings/registering-calling-bot.md), [depuração e teste local](~/concepts/calls-and-meetings/debugging-local-testing-calling-meeting-bots.md), [mídia hospedada por aplicativos](~/concepts/calls-and-meetings/requirements-considerations-application-hosted-media-bots.md), [tratamento de notificações de chamadas de entrada](~/concepts/calls-and-meetings/call-notifications.md) |
| 09/11/2018 | As páginas de configuração da guia agora são significativamente mais altas. | [Design da guia](tabs/design/tabs.md) |
| 08/15/2018 | Os cartões adaptáveis agora têm suporte no Microsoft Teams.|[Ações de cartão adaptável no Microsoft Teams](task-modules-and-cards/cards/cards-reference.md#adaptive-card) |
| 08/10/2018 | O suporte do cliente para o DevTools foi documentado para visualização do desenvolvedor.| [DevTools para o cliente do Microsoft Teams desktop](~/resources/dev-preview/developer-preview-tools.md)|
| 08/08/2018 | Agora, as extensões de mensagens dão suporte a vários comandos. Este recurso foi visualizado no desenvolvedor e agora é lançado para todos os usuários.| [composeExtensions. Commands](~/resources/schema/manifest-schema.md#composeextensionscommands)|
| 08/07/2018 | A configuração embutida agora tem suporte em conectores. A documentação dos conectores também foi revisada e expandida para fins de clareza| [Conectores](~/concepts/connectors/connectors.md)|
| 08/06/2018 | Agora, seu bot pode enviar e receber arquivos.| [Enviar e receber arquivos através do bot](~/concepts/bots/bots-files.md)|
| 07/27/2018 | A visualização do desenvolvedor agora oferece suporte a vários comandos no Messaging Extensions. | [Extensões de mensagens foram estendidas](~/resources/dev-preview/developer-preview-features.md)|
| 07/23/2018 | As informações sobre a nova certificação do aplicativo foram adicionadas à seção publicação. |[Permissões de manifesto](resources/schema/manifest-schema.md#permissions)|
| 07/16/2018 | Na visualização do desenvolvedor, mais espaço foi alocado para a página de configuração da guia. | [A página de configuração da guia é significativamente mais alta](tabs/design/tabs.md#configuration-page-height)|
| 07/12/2018 | Informações sobre o acesso de convidados. | [Acesso para convidado no Microsoft Teams](https://docs.microsoft.com/microsoftteams/guest-access#guest-access-overview)|
| 06/07/2018 | Foram adicionadas informações de pré-lançamento para o catálogo de aplicativos do Microsoft Teams locatário. | [Publicar seu aplicativo do Microsoft Teams](~/publishing/apps-publish.md)|
| 05/31/2018 | O Microsoft Teams Developer Preview (Ring 3,6) foi atualizado para incluir a capacidade de adicionar bots e guias ao chat de grupo. | [Recursos na visualização do desenvolvedor](~/resources/dev-preview/developer-preview-features.md), [esquema de visualização do desenvolvedor](~/resources/schema/manifest-schema-dev-preview.md)|
| 05/29/2018 | Os cartões adaptáveis agora têm suporte no Microsoft Teams nas [ações de cartão adaptável no Teams](task-modules-and-cards/cards/cards-reference.md) |
| 05/29/2018 | Se você estiver usando a [visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md), seu bot agora poderá enviar e receber arquivos.| [Enviar e receber arquivos por meio do bot](~/concepts/bots/bots-files.md), [recursos no Public Developer Preview for Microsoft Teams](~/resources/dev-preview/developer-preview-features.md)|
| 04/17/2018 | replyToID foi adicionado à carga para as `Invoke` `MessageBack` ações e cartão. Isso é especialmente útil se você precisar atualizar a mensagem de que a ação do cartão veio. | [Ações de cartão](~/concepts/cards/cards-actions.md)|
| 04/12/2018 | Adicionou este tópico para controlar as alterações na interface de programação do Teams e este conjunto de documentação. | [Novidades](~/whats-new.md)|
| 04/10/2018 | As URLs de autenticação foram alteradas para usar consistentemente a ID do locatário no caminho. | [Fluxo de autenticação para guias](~/concepts/authentication/auth-flow-tab.md), [autenticação da guia AAD](~/concepts/authentication/auth-tab-AAD.md)|
| 04/06/2018 | Adicionadas diretrizes de design para usar a caixa de comando. |[Caixa de comando](~/resources/design/framework/command-box.md)|
| 04/02/2018 | Usando bots para enviar notificações para seu aplicativo. |[Bots somente de notificação](~/concepts/bots/bots-notification-only.md)|
| 03/27/2018 | Documentação expandida para mensagens proativas. |[Iniciar uma conversa](./concepts/bots/bot-conversations/bots-conv-proactive.md)|
| 03/15/2018 | Documentação Refatorada para cartões. |[Cartões](~/concepts/cards/cards.md), [ações de cartão](~/concepts/cards/cards-actions.md), [formatação de cartão](~/concepts/cards/cards-format.md), [referência de cartão](~/concepts/cards/cards-reference.md)|
| 03/03/2018 | Foi adicionada a documentação para o Teams app Studio. |[Desenvolver aplicativos rapidamente com o Teams app Studio](~/get-started/get-started-app-studio.md), [usando a biblioteca de controle no app Studio](~/get-started/app-studio-component-library.md)|
| 02/27/2018 | Adicionado um código de exemplo para demonstrar o método AsTeamsChannelAccounts (). |[Obter contexto para o bot](~/concepts/bots/bots-context.md)|
| 02/05/2018 | Adicionados tópicos para introdução ao uso do C#. |[Introdução à plataforma do Microsoft Teams com C#/.NET](./get-started/get-started-dotnet-app-studio.md)|

## <a name="submit-your-questions-bugs-feature-requests-and-contributions"></a>Enviar perguntas, bugs, solicitações de recursos e contribuições

Ouvimos a comunidade de desenvolvedores em [vários canais](feedback.md).
