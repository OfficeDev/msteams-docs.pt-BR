---
title: O que há de novo e atualizado para desenvolvedores no Teams
description: Saiba mais sobre novos recursos de desenvolvedor do Microsoft Teams e atualizações para recursos existentes, anotações de substituição e alterações. Assine o RSS feed para obter as atualizações mais recentes.
ms.topic: reference
ms.localizationpriority: high
zone_pivot_groups: What-new-features
ms.openlocfilehash: 5aad27389416a5e10920ebc00521274fc8f7d907
ms.sourcegitcommit: c74e1e12175969c75e112a580949f96d2610c24e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68160724"
---
# <a name="whats-new-for-developers-in-microsoft-teams"></a>Novidades para desenvolvedores no Microsoft Teams

::: zone pivot="ga-feature"

Descubra os recursos da plataforma Microsoft Teams que estão em GA (disponibilidade geral). Agora você pode obter as atualizações mais recentes da plataforma Teams assinando o RSS feed[![download](~/assets/images/RSSfeeds.png)](https://aka.ms/TeamsPlatformUpdates). Para obter mais informações, consulte [configurar RSS feed](#get-latest-updates).

## <a name="generally-available"></a>Disponível para o público geral

:::row:::
:::column:::

:::image type="icon" source="~/assets/images/general-availabe.png" alt-text="Atualizações para recursos geralmente disponíveis":::

:::column-end:::
:::column span="2":::

Recursos da plataforma Microsoft Teams que estão disponíveis para todos os desenvolvedores de aplicativos.

**Setembro de 2022**

* ***29 de setembro de 2022***: o aplicativo [móvel do Teams agora dá suporte a downloads de arquivos para dispositivos locais.](concepts/device-capabilities/media-capabilities.md#file-download-on-teams-mobile)
* ***29 de setembro de 2022***: Gerar um link profundo para compartilhar [conteúdo para preparar as reuniões.](concepts/build-and-test/deep-links.md#generate-a-deep-link-to-share-content-to-stage-in-meetings)
* ***16 de setembro de 2022***: Cartões Adaptáveis em extensões de mensagem baseadas em pesquisa agora dão [suporte a Ações Universais.](messaging-extensions/how-to/search-commands/universal-actions-for-search-based-message-extensions.md)
* ***06 de setembro de 2022***: introduziu snippets de código para capturar vídeos usando [a câmera por meio da `selectMedia` API.](concepts/device-capabilities/media-capabilities.md#code-snippets)

:::column-end:::
:::row-end:::

<br>
<details>
<summary><b>2022</b></summary>

| **Date** | **Atualizar** | **Encontre aqui** |
| -------- | --------- | ----------------|
| 08/09/2022 | Introduzido o Kit de ferramentas do Teams para Visual Studio 2022 | Ferramentas e SDK > Kit de ferramentas do Teams para Visual Studio > [Visão geral do Kit de ferramentas do Teams para Visual Studio](toolkit/teams-toolkit-overview-visual-studio.md) |
| 03/08/2022 | Compartilhar com o Teams a partir do aplicativo ou guia pessoal | Integrar com o Teams > Compartilhar com o Teams > [Compartilhar com o Teams a partir de aplicativo pessoal ou guia](concepts/build-and-test/share-to-teams-from-personal-app-or-tab.md) |
| 03/08/2022 | Adicionado recurso para recuperar transcrições de reunião no cenário pós-reunião. | Compilar aplicativos para reuniões e chamadas do Teams > Obter transcrições de reunião usando APIs do Graph > [Visão geral](graph-api/meeting-transcripts/overview-transcripts.md) |
| 03/08/2022 | Link desdobrado para compartilhamento com equipes de aplicativos Web | Integrar com o Teams > Compartilhar com o Teams > [Compartilhar com o Teams a partir de aplicativos Web](concepts/build-and-test/share-to-teams-from-web-apps.md) |
| 08/01/2022| Aviso: o Portal do Desenvolvedor agora está em GA e o App Studio foi preterido a partir de 1º de agosto de 2022. | Ferramentas e SDK > [Portal do Desenvolvedor para Teams](concepts/build-and-test/teams-developer-portal.md) |
| 07/28/2022 | Adicionar a imagem de exibição do Teams e o cartão de visita para notificação na reunião| Compilar aplicativos para reuniões e chamadas do Teams > Habilitar e configurar aplicativos para reuniões > [Notificação na reunião](apps-in-teams-meetings/enable-and-configure-your-app-for-teams-meetings.md#in-meeting-notification) |
| 07/28/2022 | Compilar canais compartilhados no Teams | Compilar aplicativos para reuniões e chamadas do Teams > [Canais Compartilhados](concepts/build-and-test/Shared-channels.md) |
| 07/28/2022|Introduzindo o manifesto do aplicativo v1.14| Manifesto do aplicativo > [Esquema do manifesto de aplicativo para Teams](resources/schema/manifest-schema.md)|
| 26/07/2022|Ações sugeridas para bots| Compilar bots > Conversas de bot > [Mensagens em conversas de bot](bots/how-to/conversations/conversation-messages.md#send-suggested-actions)|
| 21/07/2022 | Introduziu o guia passo a passo para enviar notificações de feed de atividades | Projete seu aplicativo > Componentes de interface do usuário > Notificações de feed de atividade > [Enviar notificação de feed de atividade](sbs-graphactivity-feedbroadcast.yml) |
| 08/07/2022| Atualizações para enviar a ID do canal selecionado pelo usuário durante a instalação do aplicativo para bots por meio de eventos de atualização de conversa e instalação |  Compilar bots > Conversas de bot > Eventos de conversa no seu bot do Teams > [Eventos de conversa no seu bot do Teams](bots/how-to/conversations/subscribe-to-conversation-events.md) |
| 16/06/2022 | Recursos de mídia atualizados para dar suporte à área de trabalho e dispositivos móveis| Integrar funcionalidades de dispositivo > [integrar recursos de mídia](concepts/device-capabilities/media-capabilities.md)|
| 08/06/2022 | Comentários opcionais do cartão para mensagem de sucesso| Compilar bots > Conversas de bot > [Mensagens em conversas de bot](~/bots/how-to/conversations/conversation-messages.md#form-completion-feedback)|
| 03/06/2022 | Atualizado Adicionar módulo de autenticação para habilitar o logon único para aplicativo de guia com nova estrutura e procedimentos | Adicionar autenticação > Tabs > [Habilitar logon único em um aplicativo de guia](tabs/how-to/authentication/tab-sso-overview.md) |
| 24/05/2022 | Dicas adicionais para aprovação rápida ao publicar seu aplicativo vinculado a uma oferta de SaaS | Publicar na loja do Teams > Visão geral > [Dicas adicionais para aprovação rápida para publicar seu aplicativo vinculado a uma oferta de SaaS](~/concepts/deploy-and-publish/appsource/publish.md#additional-tips-for-rapid-approval-to-publish-your-app-linked-to-a-saas-offer) |
| 24/05/2022 | Envie para a loja Teams seus aplicativos habilitados para Outlook e Office | Estenda seu aplicativo no Microsoft 365 > [Visão Geral](m365-apps/overview.md) |
| 24/05/2022 | Diretrizes do aplicativo e as novidades do TeamsJS versão 2.0.0| Ferramentas e SDKs > [SDK do cliente JavaScript do Teams](tabs/how-to/using-teams-client-sdk.md)  |
| 24/05/2022 | O Kit de Ferramentas do Teams versão 4.0.0 para Visual Studio Code agora é GA | Ferramentas e SDKs > Kit de Ferramentas do Teams para o Visual Studio Code > <br> •  [Visão geral do Kit de Ferramentas do Teams](toolkit/teams-toolkit-fundamentals.md) <br> • [Criar um bot de comando com JavaScript](toolkit/add-capability.md) <br> • [Criar um bot de notificação com JavaScript](toolkit/add-capability.md) <br> • [Visualizar e personalizar o manifesto do aplicativo Teams](toolkit/TeamsFx-preview-and-customize-app-manifest.md) <br> • [Conectar às APIs existentes](toolkit/add-API-connection.md) <br> • [Adicionar recursos aos seus aplicativos do Teams](toolkit/add-capability.md) <br> • [Adicionar a experiência de logon único](toolkit/add-single-sign-on.md) <br> • [Adicionar recursos de nuvem ao aplicativo do Teams](toolkit/add-resource.md) |
| 24/05/2022 | Apresentado o manifesto do aplicativo versão 1.13 | Manifesto do > [de aplicativo para Microsoft Teams](resources/schema/manifest-schema.md) |
| 24/05/2022|Extensões de Bots e Mensagens no GCC e GCCH| • Planejar seu aplicativo > [Visão Geral](concepts/app-fundamentals-overview.md#government-community-cloud) </br> • Criar bots > [Visão geral](bots/what-are-bots.md) </br> • Criar extensões de mensagem > [Visão geral](messaging-extensions/what-are-messaging-extensions.md) |
|26/04/2022|Comportamento de desinstalação do aplicativo pessoal com o bot | Criar bots > Conversas de bot > [Desinstalar atualizações de comportamento em aplicativos pessoais com bots](bots/how-to/conversations/subscribe-to-conversation-events.md#uninstall-behavior-for-personal-app-with-bot)|
| 04/22/2022 | Teste de visualização para aplicativos monetizados | Monetize seu aplicativo > [Teste de visualização para aplicativos monetizados](concepts/deploy-and-publish/appsource/prepare/test-preview-for-monetized-apps.md)
| 04/22/2022 | Fluxo de compras no aplicativo para a monetização de aplicativos | Monetize seu aplicativo > [Compras no aplicativo](concepts/deploy-and-publish/appsource/prepare/in-app-purchase-flow.md)
| 28/04/2022 | Motivos comuns para falhas na validação do aplicativo | Distribuir seu aplicativo > Publicar na loja do Teams > [Motivos comuns para falha na validação do aplicativo](concepts/deploy-and-publish/appsource/common-reasons-for-app-validation-failure.md)|
| 04/20/2022 |  Configurar pipelines de CI/CD | Ferramentas e SDKs > Conjunto de Ferramentas do Teams para o Visual Studio Code >  [Configurar pipelines de CI/CD ](toolkit/use-CICD-template.md)|
| 19/04/2022 | Carregar seu aplicativo no Microsoft Teams | Distribuir seu aplicativo > [Carregar seu aplicativo](concepts/deploy-and-publish/apps-upload.md)|
| 01/04/2022 | Introdução ao guia passo a passo para criar um bot de conversa do Microsoft Teams| Criar bots > Conversas de bot > Conversas de grupo e canal > [Guia passo a passo para criar bot de conversação do bot](sbs-teams-conversation-bot.yml) |
| 30/03/2022 | Atualizado o módulo de Introdução com o aplicativo Blazor usando guias e bots|  Comece > [Crie seu primeiro aplicativo usando o Blazor](sbs-gs-blazorupdate.yml)|
| 30/03/2022 | Permissões do dispositivo para o navegador | Integrar recursos do dispositivo > [Permissões de dispositivo para o navegador](concepts/device-capabilities/browser-device-permissions.md) |
| 29/03/2022 |Integrar o Seletor de Pessoas | Integrar com o Teams > [Integrar o Seletor de Pessoas](concepts/device-capabilities/people-picker-capability.md)
| 03/23/2022 | Introduziu o guia passo a passo para desdobrar links no Teams usando bot | Criar extensões de mensagem > Adicionar desenrolamento de link > [Desdobrar links no Teams usando o bot](sbs-botbuilder-linkunfurling.yml)|  
| 22/03/2022 | Adicionadas as informações sobre o processo de depuração| • Ferramentas e SDKs> Kit de ferramentas do Teams para Visual Studio Code > [Depurar seu aplicativo do Teams localmente](toolkit/debug-local.md) </br> • Ferramentas e SDKs> Kit de ferramentas do Teams para Visual Studio Code > [Depurar o processo em segundo plano ](toolkit/debug-background-process.md)|
| 14/03/2022 | Introduziu o guia passo a passo para criar e testar um conector no Microsoft Teams | Criar webhooks e conectores > Criar Conectores do Office 365 > [Criar conectores do Teams](sbs-teams-connectors.yml)|
| 10/03/2022 | Informações adicionadas sobre o Moodle LMS e Microsoft 365 plug-ins | Integrar com Teams > Moodle LMS > [Sistema de gerenciamento de aprendizagem Moodle](resources/moodle-overview.md)|  
| 03/03/2022 | Como adicionar autenticação usando provedor OAuth externo| Adicionar autenticação > Guias > [Usar provedores OAuth externos](tabs/how-to/authentication/auth-oauth-provider.md) |
| 25/02/2022 | Apresentado o guia passo a passo para invocar módulos de tarefa no Microsoft Teams| Criar cartões e módulos de tarefas > Criar módulos de tarefa > Usar módulos de tarefa de bots > [Invocar módulo de tarefa do Microsoft Teams](sbs-botbuilder-taskmodule.yml)|
| 24/02/2022| Introduzido o guia passo a passo para criar uma extensão de mensagem baseada em ação | Criar Extensões de Mensagens > Comandos de ação > Definir comandos de ação > [ Criar extensões de mensagens baseada em ação ](sbs-meetingextension-action.yml)|
| 24/02/2022 | Introduzido o guia passo a passo para criar extensões de mensagens baseada em pesquisa | Criar extensões de mensagens > Comandos de pesquisa > Definir comandos de pesquisa > [Criar extensões de mensagens baseada em pesquisa ](sbs-messagingextension-searchcommand.yml)|
| 24/02/2022 | Apresentado guia passo a passo para criar Webhooks de saída | Criar webhooks e conectores > Criar Webhooks de Saída > [Criar Webhooks de Saída](sbs-outgoing-webhooks.yml)|
| 23/02/2022 | Parâmetros de classificação da loja do Microsoft Teams| Distribua seu aplicativo > Publicar na loja do Microsoft Teams > [Parâmetros de classificação da loja do Microsoft Teams](concepts/deploy-and-publish/appsource/post-publish/teams-store-ranking-parameters.md)|
| 18/02/2022 | Apresentado o Glossário extensivo para a Documentação do Desenvolvedor do Microsoft Teams para ajudá-lo a encontrar a definição sobre um termo rapidamente | [Glossário](~/get-started/glossary.md) |
| 18/02/2022 | Atualizado o módulo Visão geral para mapear o aplicativo do Microsoft Teams para metas organizacionais, história do usuário e exploração dos recursos do aplicativo do Microsoft Teams | [Visão geral > Aplicativo Teams adequado](overview.md) |
| 18/02/2022 | Atualizado o módulo conceitos básicos do aplicativo para Planejar seu aplicativo para incluir casos de uso de mapeamento para recursos do Microsoft Teams e lista de verificação de planejamento de aplicativos | [Planejar seu aplicativo > Visão geral](~/concepts/app-fundamentals-overview.md) |
| 17/02/2022 | O que esperar depois de enviar seu aplicativo ou?| Distribuir seu aplicativo > Publicar na loja do Teams > [Visão geral](concepts/deploy-and-publish/appsource/publish.md) |
| 15/02/2022 | Introduzido o guia passo a passo de como fazer upload de arquivos para o Microsoft Teams a partir de um bot | Build bots > Enviar e receber arquivos > [Guia passo a passo de como fazer upload de arquivos para o Microsoft Teams a partir de um bot](sbs-file-handling-in-bot.yml) |
| 02/11/2022 | Estágio de reunião compartilhada| • Criar aplicativos para reuniões do Teams > [Janela de conteúdo compartilhado na reunião](apps-in-teams-meetings/enable-and-configure-your-app-for-teams-meetings.md#shared-meeting-stage) </br> • Crie aplicativos para reuniões do Teams > [Referências da API de aplicativos de reunião](apps-in-teams-meetings/API-references.md) </br> • Manifesto do aplicativo > Visualização pública do desenvolvedor > [Esquema do manifesto de visualização do desenvolvedor](resources/schema/manifest-schema-dev-preview.md)|
| 08/02/2022 | Introdução ao guia passo a passo para criar um bot de Chamada e Reunião| Criar bots > Bots de chamadas e reuniões > Registrar chamadas e o bot de reuniões > [Um guia passo a passo para criar um bot de Chamada e Reunião](sbs-calling-and-meeting.yml) |
| 02/02/2022 | Apresentado o manifesto do aplicativo versão 1.12 | Manifesto do aplicativo > [Esquema do manifesto do aplicativo](resources/schema/manifest-schema.md) |
| 25/01/2022 | API de envio de legendas em tempo real | Crie aplicativos para reuniões do Teams > Referências de API de aplicativos de reunião> [Referências da API de aplicativos de reunião](apps-in-teams-meetings/API-references.md#send-real-time-captions-api)|
| 19/01/2022 | Cartões Adaptáveis de conclusão do formulário | Criar bots > Conversas de bot > Mensagens em conversas de bot > [Comentários sobre a conclusão do formulário](bots/how-to/conversations/conversation-messages.md#form-completion-feedback)|
| 17/01/2022 | Seletor de Pessoas em Cartões Adaptáveis para área de trabalho | Criar cartões e módulos de tarefa > Criar cartões > [Seletor de Pessoas em Cartões Adaptáveis](task-modules-and-cards/cards/people-picker.md)|

</details>
</br>
<details>
<summary><b>Atualizações mais antigas</b></summary>

Explore as atualizações das versões anteriores do GA listadas aqui.

</br>
<details>
<summary><b>2021</b></summary>

| **Date** | **Atualizar** | **Encontre aqui** |
| -------- | --------- | ----------------|
|24/12/2021| Introdução ao guia passo a passo para conceder permissões de dispositivo Tab | Fundamentos do aplicativo > Recursos do dispositivo > [Guia passo a passo para conceder permissões de dispositivo Tab](sbs-tab-device-permissions.yml) |
|23/12/2021| Introduzido o guia passo a passo para criar guias com Cartões Adaptáveis| Adicionar autenticação > Guias > Usar o guia de autenticação SSO > [Passo a passo para criar guias com Cartões Adaptáveis](sbs-tab-with-adaptive-cards.yml) |
|21/12/2021 | Atualizou os módulos Introdução ao JavaScript, C# e Node.js para Teams Toolkit 3.0.0 | • Começar > [criar seu primeiro aplicativo com JavaScript](sbs-gs-javascript.yml) <br> • Começar > [criar seu primeiro aplicativo com C# ou .NET](sbs-gs-csharp.yml) <br> • Começar > [criar seu primeiro aplicativo com Node.js](sbs-gs-nodejs.yml) |
|20/12/2021| Introduzido o guia passo a passo para guias e extensões de mensagens com o Logon Único (SSO) | Adicionar autenticação > Guias > Usar autenticação SSO > [Guia passo a passo com SSO para guias e extensões de mensagens](sbs-tabs-and-messaging-extensions-with-SSO.yml)|
|20/12/2021| Guia passo a passo para criar bolha de conteúdo de reunião | Criar aplicativos para reuniões do Teams > Habilitar e configurar aplicativos para reuniões > [Guia passo a passo para criar bolha de conteúdo de reunião](sbs-meeting-content-bubble.yml) |
|09/12/2021| Introduzido o guia passo a passo para o exibição de estágio de reunião | Crie aplicativos para reuniões do Teams > Habilitar e configurar aplicativos para reuniões > [Guia passo a passo para criar o modo de exibição de estágio de reuniões](sbs-meetings-stage-view.yml)|
|13/12/2021 | Diretrizes introduzidas para aplicativos vinculados à oferta de SaaS | Distribuir seu aplicativo > Publicar na Teams Store > Examinar as diretrizes de validação da loja > [Diretrizes para aplicativos vinculados à oferta de SaaS](concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#apps-linked-to-saas-offer)|
|09/12/2021| Introdução ao guia passo a passo para criar o painel lateral da reunião | Crie aplicativos para reuniões do Teams > Habilitar e configurar aplicativos para reuniões > [Guia passo a passo para criar o painel lateral de reunião no Teams](sbs-meetings-sidepanel.yml)|
|01/12/2021 | Ícone de nova loja introduzido | • Projetar seu aplicativo > Capacidades do aplicativo > [Fazer o design do seu aplicativo pessoal para Microsoft Teams](concepts/design/personal-apps.md)</br> • Projetar seu aplicativo > Componentes da interface do usuário > [Fazer o design do seu aplicativo Microsoft Teams com componentes avançados da interface do usuário](concepts/design/design-teams-app-advanced-ui-components.md) |
|24/11/2021| Introdução ao guia passo a passo para gerar o token de reunião | Crie aplicativos para reuniões do Teams > Habilitar e configurar aplicativos para reuniões > [Guia passo a passo para criar token de reunião no Teams](sbs-meeting-token-generator.yml)|
|17/11/2021| Diretrizes de validação do Microsoft Teams Store atualizadas|[Diretrizes de validação da loja](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md)|
|17/11/2021| Pesquisa de preenchimento automático estático e dinâmico para usuários da área de trabalho e móveis | • Criar cartões e módulos de tarefa > Criar cartões > [Pesquisa de Preenchimento Automático em Cartões Adaptáveis](task-modules-and-cards/cards/dynamic-search.md) </br> • Criar cartões e módulos de tarefa > Criar cartões > Visão geral > [Pesquisa de preenchimento automático em Cartões Adaptáveis](task-modules-and-cards/what-are-cards.md#type-ahead-search-in-adaptive-cards) </br> • Criar cartões e módulos de tarefas > Visão geral > [Cartões e módulos de tarefa](task-modules-and-cards/cards-and-task-modules.md)|
|13/11/2021| Os bots podem ser habilitados para receber todas as mensagens de canal usando o RSC (consentimento específico do recurso) | • Criar bots > Conversas de bot > Mensagens em conversas de bots > [Receber todas as mensagens de canal com RSC](~/bots/how-to/conversations/channel-messages-with-rsc.md) </br> • Criar bots > Conversas de bot > [Visão geral da conversa de bot](~/bots/how-to/conversations/conversation-basics.md) </br> • Criar bots > Conversas de bots > [Conversas de canal e grupo](~/bots/how-to/conversations/channel-and-group-conversations.md) |
|28/10/2021| Monetize seu aplicativo Teams com uma oferta de SaaS transacionável | Distribuir seu aplicativo > Publicar no Teams Store > [Incluir uma oferta SaaS com seu aplicativo do Teams](~/concepts/deploy-and-publish/appsource/prepare/include-saas-offer.md) |
|25/10/2021| Atualizado o módulo Introdução à Documentação do Desenvolvedor do Microsoft Teams com nova estrutura e procedimentos em um guia passo a passo | Começar > [Introdução ao seu primeiro aplicativo do Teams](get-started/get-started-overview.md) |
|20/10/2021| O estágio de reunião agora está disponível em GA | Criar aplicativos para reuniões do Teams > [Habilitar e configurar seus aplicativos para reuniões do Teams](apps-in-teams-meetings/enable-and-configure-your-app-for-teams-meetings.md) |
|20/10/2021| API de Detalhes da Reunião e eventos de reunião do Teams em tempo real | Crie aplicativos para reuniões do Teams [Obtenha a API de detalhes da reunião](apps-in-teams-meetings/API-references.md#get-meeting-details-api) |
|18/10/2021| Link de guias desdobradas e exibição de estágio | Criar guias > [Link de guias desdobradas e exibição de estágio](tabs/tabs-link-unfurling.md) |
|08/10/2021| Novas práticas recomendadas para criar Cartões Adaptáveis | Projetar seu aplicativo > Componentes da interface do usuário > [Fazendo o design de Cartões Adaptáveis para seu aplicativo Teams](task-modules-and-cards/cards/design-effective-cards.md) |
|05/10/2021| Ocultar aplicativo Teams até que o Administrador permita não ocultar o aplicativo | Criar seu aplicativo > [bloquear aplicativos por padrão para os usuários até que um administrador aprove](concepts/design/enable-app-customization.md#block-apps-by-default-for-users-until-an-admin-approves) |
|05/10/2021| Planeje seus aplicativos para Teams em dispositivo móvel | Fundamentos do aplicativo > [Planeje guias responsivas do para Teams celular](concepts/design/plan-responsive-tabs-for-teams-mobile.md) |
|04/10/2021| Novos Portal do Desenvolvedor para o Teams introduzidos para gerenciar seus aplicativos do Teams | Ferramentas e SDK > [Portal do Desenvolvedor para Teams](concepts/build-and-test/teams-developer-portal.md) |
|21/09/2021|O Teams dá suporte à ID de Objeto do Azure Active Directory e AO UPN na menção do usuário para bots e Webhooks de entrada | • Criar cartões e módulos de tarefas > criar cartões > [ID de Objeto do Azure Active Directory e UPN na menção do usuário](task-modules-and-cards/what-are-cards.md#support-for-azure-ad-object-id-and-upn-in-user-mention) </br> • Criar cartões e módulos de tarefas > Criar cartões > [Cartões – Visão geral](task-modules-and-cards/cards/cards-format.md#format-cards-with-markdown) |
|16/08/2021| Suporte para validação de entrada Cartões Adaptáveis (v1.3 para todos os recursos) e Ações Universais (v1.4 para cartões enviados por bot) | • Cartões adaptáveis > Cartões de criação > [Validação de entrada](/adaptive-cards/authoring-cards/input-validation)</br> • Criar cartões e módulos de tarefa > Criar cartões > Ações universais para Cartões Adaptáveis > [Ações Universais para Cartões Adaptáveis v1.4](task-modules-and-cards/cards/universal-actions-for-adaptive-cards/overview.md) |
|30/08/2021| O recurso de cenas do Modo Juntos Personalizado combina os participantes em uma única cena virtual e coloca seus fluxos de vídeo em estações pré-determinadas | Criar aplicativos para reuniões do Teams > [Cenas do modo conferência personalizadas](~/apps-in-teams-meetings/teams-together-mode.md) |
|25/08/2021| Introduzido o guia passo a passo para criar um Teams com SSO (sign-on único) | Adicionar autenticação > Bots > [Guia passo a passo para criar bot do Teams com SSO](sbs-bots-with-sso.yml) |
|19/08/2021| Evento de atualização de instalação recebido ao instalar um bot em um thread de conversa | Criar bots > Conversas de bots > [Evento de atualização de instalação](bots/how-to/conversations/subscribe-to-conversation-events.md#installation-update-event) |
|12/08/2021|Criar guias com Cartões Adaptáveis| Criar guias > [Criar guias com Cartões Adaptáveis](tabs/how-to/build-adaptive-card-tabs.md) |
|08/04/2021|As guias não terão mais margens ao redor de suas experiências | Criar guias > [Remover margens de tabulação](resources/removing-tab-margins.md) |
|08/07/2021|O Teams Mobile adiciona suporte para aplicativos em reuniões | Criar aplicativos para Teams reuniões > [Extensibilidade de aplicativos de reunião](apps-in-teams-meetings/meeting-app-extensibility.md) |
|28/06/2021|Funcionalidade Integrar Seletor de Pessoas | Integrar com o Teams > [Integrar funcionalidade de Seletor de Pessoas](concepts/device-capabilities/people-picker-capability.md) |  
|25/06/2021| Introdução ao guia passo a passo para enviar mensagens proativas | Criar bots > Conversa de bot > Mensagens proativas > [Guia passo a passo para enviar mensagens proativas](sbs-send-proactive.yml) |
|09/06/2021| Exibição de estágio para imagens em Cartões Adaptáveis com `allowExpand` atributo | Criar cartões e módulos de tarefa > Criar cartões > [Modo de exibição de estágio para imagens em Cartões Adaptáveis](task-modules-and-cards/cards/cards-format.md#stage-view-for-images-in-adaptive-cards) |
|31/05/2021| Guias de conversa | Criar guias > [Iniciar e continuar conversas sobre conteúdo em suas guias](~/tabs/how-to/conversational-tabs.md) |
|24/05/2021| Diretrizes de design de aplicativos do Teams atualizadas com padrões móveis | Projetar seu aplicativo > [Design do aplicativo do Teams](~/concepts/design/design-teams-app-overview.md) |
|13/05/2021| Adicionadas informações sobre mConnect e Skooler | Integrar com Teams > Moodle LMS > [Sistema de gerenciamento de aprendizagem Moodle](resources/moodle-overview.md)|
|10/05/2021| Manifesto do aplicativo v1.10 lançado | Manifesto do aplicativo > [Esquema do manifesto](resources/schema/manifest-schema.md) |
|10/05/2021| Novo recurso de personalização de aplicativo | Projetar seu aplicativo > [Habilitar organizações para personalizar seu aplicativo](concepts/design/enable-app-customization.md) |
|07/05/2021| Links profundos para chamadas de áudio e vídeo no chat | Integrar com o Teams > [Links profundos](concepts/build-and-test/deep-links.md#navigate-to-an-audio-or-audio-video-call) |
|30/04/2021|Novas diretrizes sobre como publicar aplicativos na Teams Store | • Publicar na Teams Store > [Publicar seu aplicativo na Teams Store](concepts/deploy-and-publish/appsource/publish.md)</br> • Publicar na Teams Store > [Diretrizes de validação da Teams Store](concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md) |
|29/04/2021 | Suporte para Ações Universais para Cartões Adaptáveis v1.4 | Criar cartões e módulo de tarefa > Criar cartões > Ações Universais para Cartões Adaptáveis > [Ações Universais para Cartões Adaptáveis](task-modules-and-cards/cards/universal-actions-for-adaptive-cards/overview.md) |
|29/04/2021 | Exibições Específicas do Usuário | Criar cartões e módulo de tarefa > criar cartões > ações Universais para Cartões Adaptáveis > [Exibições Específicas do Usuário](task-modules-and-cards/cards/universal-actions-for-adaptive-cards/User-Specific-Views.md) |
|29/04/2021 | Fluxos de Trabalho Sequenciais | Criar cartões e módulo de tarefa > criar cartões > ações Universais para Cartões Adaptáveis > [Fluxos de Trabalho Sequenciais](task-modules-and-cards/cards/universal-actions-for-adaptive-cards/Sequential-Workflows.md) |
|29/04/2021 | Cartões atualizados | Criar cartões e módulo de tarefa > Criar cartões > Ações Universais para Cartões Adaptáveis > [Cartões atualizados](task-modules-and-cards/cards/universal-actions-for-adaptive-cards/Up-To-Date-Views.md) |
|04/08/2021| Recurso de personalização de aplicativo | • Projetar seus aplicativos > [Visão geral do aplicativo de equipes de design](concepts/design/enable-app-customization.md)</br> • Ferramentas e SDKs > [Portal do Desenvolvedor](concepts/build-and-test/teams-developer-portal.md) </br> • Manifesto do aplicativo > Visualização do desenvolvedor público > [Esquema de manifesto](resources/schema/manifest-schema-dev-preview.md) |
|18/03/2021| Aviso: Atualize para a versão 4.10 ou superior do SDK do Bot Framework, pois começamos com o processo de substituição para `TeamsInfo.getMembers` e `TeamsInfo.GetMembersAsync`. | Criar bots > [Mudanças de API de Bot para membros de equipe/chat](resources/team-chat-member-api-changes.md) |
|05/03/2021|Escopo de instalação padrão e funcionalidade de grupo | Distribua seu aplicativo > [Escopo de instalação padrão e funcionalidade de grupo](concepts/deploy-and-publish/add-default-install-scope.md) |
|05/03/2021|Reordenar guias pessoais do aplicativo | Criar guias > [Reordenar a guia de chat em aplicativos pessoais](tabs/how-to/create-personal-tab.md#reorder-static-personal-tabs) |
|04/03/2021|Mascaramento de informações em cartões adaptáveis | Criar cartões e módulos de tarefas > Criar cartões > [Mascaramento de informações em cartões adaptáveis](task-modules-and-cards/cards/cards-format.md#information-masking-in-adaptive-cards) |
|19/02/2021|Recursos de localização adicionados. <br/> As informações de recursos de localização são adicionadas na visão geral dos recursos do dispositivo, nas permissões nativas do dispositivo, na integração dos recursos de mídia e nos arquivos de funcionalidade do scanner de código de barras ou QR | • Conceitos básicos do aplicativo > recursos do dispositivo > [Visão geral](concepts/device-capabilities/device-capabilities-overview.md) </br> • Conceitos básicos do aplicativo > recursos do dispositivo > [Solicitar permissões de dispositivo](concepts/device-capabilities/native-device-permissions.md) </br> • Conceitos básicos do aplicativo > recursos do dispositivo > [Integrar recursos de mídia](concepts/device-capabilities/media-capabilities.md) </br> • Conceitos básicos do aplicativo > recursos do dispositivo > [Integrar funcionalidade de scanner de código de barras ou QR](concepts/device-capabilities/qr-barcode-scanner-capability.md) </br> • Conceitos básicos do aplicativo > recursos do dispositivo > [Integrar recursos de localização](concepts/device-capabilities/location-capability.md) |
|18/02/2021|Adição do recurso de scanner de QR ou código de barras. <br/> As informações de funcionalidade do scanner de código de barras ou QR são adicionadas na visão geral dos recursos do dispositivo, nas permissões nativas do dispositivo e na integração de arquivos de recursos de mídia | • Conceitos básicos do aplicativo > recursos do dispositivo > [Visão geral](concepts/device-capabilities/device-capabilities-overview.md) </br> • Conceitos básicos do aplicativo > recursos do dispositivo > [Solicitar permissões de dispositivo](concepts/device-capabilities/native-device-permissions.md) </br> • Conceitos básicos do aplicativo > recursos do dispositivo > [Integrar recursos de mídia](concepts/device-capabilities/media-capabilities.md) </br> • Conceitos básicos do aplicativo > recursos do dispositivo > [Integrar funcionalidade de scanner de código de barras ou QR](concepts/device-capabilities/qr-barcode-scanner-capability.md) |
|09/02/2021|Visão geral dos recursos de dispositivo adicionados. <br/> As informações de funcionalidade do microfone são adicionadas às permissões do dispositivo nativo e integram arquivos de recursos de mídia |• Conceitos básicos do aplicativo > recursos do dispositivo > [Visão geral](concepts/device-capabilities/device-capabilities-overview.md) </br> • Conceitos básicos do aplicativo > recursos do dispositivo > [Solicitar permissões de dispositivo](concepts/device-capabilities/native-device-permissions.md) </br> • Conceitos básicos do aplicativo > recursos do dispositivo > [Integrar recursos de mídia](concepts/device-capabilities/media-capabilities.md)|

<br>

</details>

<br>

<details>
<summary><b>2020</b></summary>

| **Date** | **Atualizar** | **Encontre aqui** |
| -------- | --------- | ------------------ |
|30/11/2020|Integração da plataforma de identidade com o Teams Toolkit e Visual Studio Code para guias |[Autenticação de logon único com o Kit de Ferramentas do Teams e Visual Studio Code para guias](toolkit/add-single-sign-on.md)|
|16/11/2020|Manifesto do aplicativo Teams atualizado para a versão 1.8.|[Referência: esquema de manifesto para o Microsoft Teams](resources/schema/manifest-schema.md)|
|10/11/2020|Diretrizes de design de bot do Teams |[Diretrizes de design de bot](bots/design/bots.md)|
|30/09/2020|Agora há suporte para o envio e recebimento de arquivos para bots em dispositivos móveis |[Enviar e receber arquivos por meio do seu bot](resources/bot-v3/bots-files.md)|
|22/09/2020|Novas informações para começar a usar o desenvolvimento do Teams |[Criar sua primeira visão geral do aplicativo Teams](build-your-first-app/build-first-app-overview.md)|
|18/09/2020|Suporte para aplicativos do Teams em reunião (Versão Prévia) |[Aplicativos em reuniões do Teams](apps-in-teams-meetings/teams-apps-in-meetings.md)|
|19/08/2020|Importar mensagens do Teams com Microsoft Graph |[Importar mensagens de plataforma de terceiros para o Teams usando o Microsoft Graph](graph-api/import-messages/import-external-messages-to-teams.md)
|12/08/2020 |Cartões Adaptáveis suporte no webhook de entrada movido para GA |[Enviar cartões adaptáveis usando um webhook de entrada](~/webhooks-and-connectors/how-to/connectors-using.md#send-adaptive-cards-using-an-incoming-webhook) |
|10/08/2020|Comece a criar aplicativos do Teams com o Visual Studio Toolkit |[Criar aplicativos com o Kit de Ferramentas do Microsoft Teams e Visual Studio Code](toolkit/visual-studio-overview.md) |
|06/08/2020|Suporte para autenticação de SSO do Tabs |[Desenvolver uma guia SSO do Microsoft Teams](tabs/how-to/authentication/tab-sso-overview.md) |
|27/07/2020 | Mensagens e bots proativos do Graph (Visualização Pública) |[Habilitar a instalação proativa de bots e mensagens proativas no Teams com Microsoft Graph](graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md)|
|22/07/2020 |Atualizações de funcionalidade de dispositivo móvel |[Solicitar permissões de dispositivo para sua guia do Microsoft Teams](concepts/device-capabilities/native-device-permissions.md) |
|20/07/2020|Ferramenta de Validação de Aplicativo do Teams para envios do AppSource |[Ferramenta de Validação de Aplicativo do Teams](concepts/deploy-and-publish/appsource/prepare/submission-checklist.md)
|15/07/2020|Crie um assistente virtual para o Teams |[Assistente Virtual para o Microsoft Teams](samples/virtual-assistant.md)|
|14/07/2020|Exibir uma documentação do indicador de carregamento nativo |[Mostrando um indicador de carregamento nativo](tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator)
|01/07/2020|Comece a criar aplicativos do Teams com o Visual Studio Code Toolkit |[Criar aplicativos com o Kit de Ferramentas do Microsoft Teams e Visual Studio Code](sbs-gs-javascript.yml) |
|01/07/2020|Logon único para guias GA para clientes da Web e da área de trabalho do Teams |[SSO (logon único)](tabs/how-to/authentication/tab-sso-overview.md)|
|05/06/2020| Esquema de manifesto atualizado para a versão 1.7.| [Referência: esquema de manifesto para o Microsoft Teams](resources/schema/manifest-schema.md)|
|18/05/2020|Integrar Power Virtual Agents com o Teams |[Integrar um chatbot Power Virtual Agents com o Microsoft Teams](bots/how-to/add-power-virtual-agents-bot-to-teams.md)|
|01/04/2020|Integrar sistemas WFM ao Shifts Connector for Teams. |[Conectores WFM do Microsoft Teams Shifts](samples/shifts-wfm-connectors.md)
|24/03/2020 | Adicionado suporte para recuperar um único membro de uma conversa e suporte adicional para recuperar membros paginados | [Obter o contexto do Teams para o seu bot](~/bots/how-to/get-teams-context.md) |

<br>

</details>

<br>

<details>
  
<summary><b>2019</b></summary>

| **Date** | **Atualizar** | **Encontre aqui** |
| -------- | --------- | ------------------ |
| 26/12/2019 | The `replyToId` parameter in payloads sent to a bot is no longer encrypted, allowing you to use this value to construct deeplinks to these messages. Message payloads include the encrypted values in the parameter `legacy.replyToId`.  |
| 05/11/2019 | Logon único usando o SDK JavaScript do Teams. | [Logon único](tabs/how-to/authentication/tab-sso-overview.md) |
| 31/10/2019 | Documentação de bots de conversação e extensão de mensagens atualizado para refletir o SDK do Bot Framework 4.6. A documentação do SDK v3 está disponível na seção Recursos. | Toda a documentação do bot e da extensão de mensagem |
| 31/10/2019 | Nova estrutura de documentação e refatoração de artigo principal. Relate links inativos ou 404s criando um Problema do GitHub. | Todos eles! |
| 13/09/2019 | O bot de solicitação é instalado da extensão de mensagem baseada em ação. | [Iniciar ações com extensões de mensagem ](resources/messaging-extension-v3/create-extensions.md#request-to-install-your-conversational-bot)
| 28/08/2019 | Suporte para canais privados em guias e conectores. | [Obtenha contexto para sua guia](tabs/how-to/access-teams-context.md#retrieve-context-in-private-channels) |
| 20/06/2019 | Compartilhe um site externo, de um site externo, em um canal do Teams. | [Compartilhar com o Teams](concepts/build-and-test/share-to-teams-overview.md). |
| 25/05/2019 | Responder com a mensagem do bot do módulo de tarefa. | [Responder com a mensagem de bot do módulo de tarefa](resources/messaging-extension-v3/create-extensions.md#respond-with-an-adaptive-card-message-sent-from-a-bot) |
| 25/05/2019 | Bots em chats em grupo. | [Interagir com um bot no chat em grupo ou no canal](~/concepts/bots/bot-conversations/bots-conv-channel.md) |
| 20/05/2019 | Localização do manifesto do aplicativo. | [Localização de aplicativo](~/publishing/apps-localization.md) |
| 20/05/2019 | Ações de mensagem. | [Ações de mensagem](resources/messaging-extension-v3/create-extensions.md#action-type-message-extensions) |
| 20/05/2019 | Desenrolamento de link (visualizações de URL personalizadas). | [Desenrolamento de link](messaging-extensions/how-to/link-unfurling.md)|
| 06/05/2019 | Programa de Certificação de Aplicativos para aplicativos da loja. | [Certificação de aplicativos](~/concepts/deploy-and-publish/appsource/post-publish/overview.md#complete-microsoft-365-certification) |
| 06/05/2019 | Os Modelos de Aplicativo agora estão disponíveis | [Modelos de aplicativos](~/samples/app-templates.md) |
| 23/04/2019 | As extensões de mensagens baseadas em ação já estão disponíveis. | [Extensões de mensagem baseadas em ação](~/concepts/messaging-extensions/create-extensions.md) |
| 18/02/2019 | Criando links profundos para o chat privado. | [Vinculação profunda a um chat](concepts/build-and-test/deep-links.md#navigate-to-a-chat) |
| 23/01/2019 | Identificando informações de SKU e de tipo de licença no contexto da guia. | [Contexto da guia](~/concepts/tabs/tabs-context.md) |
|
</details>

<br>

<details>
<summary><b>2018</b></summary>

| **Date** | **Atualizar** | **Encontre aqui** |
| -------- | --------- | ------------------ |
| 11/12/2018 | As guias no chat em grupo agora estão disponíveis na versão lançada do Teams. Como parte desse trabalho, a seção de guias foi retrabalhada para maior clareza.| [Guias configuráveis](~/concepts/tabs/tabs-configurable.md) |
| 09/11/2018 | Agora você pode criar links profundos para chats privados entre usuários. | [Vinculação profunda a um chat](concepts/build-and-test/deep-links.md#navigate-to-a-chat) |
| 11/08/2018 | A Estrutura do SharePoint 1.7 enviou e com ela um novo recurso para usar a guia Microsoft Teams como uma Web Part da Estrutura do SharePoint. | [Guias no SharePoint](~/concepts/tabs/tabs-in-sharepoint.md) |
| 05/11/2018 | O recurso **módulo de tarefa** foi lançado. Um módulo de tarefa permite que você crie experiências pop-up modais em seu aplicativo do Teams, a partir de bots e guias. Dentro do pop-up, você pode executar seu próprio código HTML/JavaScript personalizado, mostrar um widget baseado em `<iframe>`, como um vídeo do YouTube ou do Microsoft Stream, ou exibir um [Cartão adaptável](/adaptive-cards/). | [Visão geral do módulo tarefa](~/concepts/task-modules/task-modules-overview.md), [módulo de tarefa em guias](~/concepts/task-modules/task-modules-tabs.md),  [módulo de tarefa em bots](~/concepts/task-modules/task-modules-bots.md) |
| 05/10/2018 | As informações de formatação para cartões foram atualizadas e testadas na área de trabalho, iOS e clientes Android para o Teams. | [Cartões](~/concepts/cards/cards.md), [Formatação de cartão](~/concepts/cards/cards-format.md) |
| 24/09/2018 | As APIs de chamadas e reuniões online Microsoft Graph foram lançadas para beta e os aplicativos do Teams agora podem interagir com os usuários de maneiras avançadas usando voz e vídeo. | [Bots de chamadas e reuniões online](~/concepts/calls-and-meetings/registering-calling-bot.md), [Conceitos de mídia em tempo real](~/concepts/calls-and-meetings/real-time-media-concepts.md), [Registro de um bot de chamada](~/concepts/calls-and-meetings/registering-calling-bot.md), [depuração e teste local](~/concepts/calls-and-meetings/debugging-local-testing-calling-meeting-bots.md), [Mídia hospedada pelo aplicativo](~/concepts/calls-and-meetings/requirements-considerations-application-hosted-media-bots.md), [Tratamento de notificações de chamadas de entrada](~/concepts/calls-and-meetings/call-notifications.md) |
| 11/09/2018 | As páginas de configuração de tabulação agora estão significativamente mais altas. | [Design da guia](tabs/design/tabs.md) |
| 15/08/2018 | Agora há suporte para cartões adaptáveis no Teams.|[Ações de cartão adaptável no Teams](task-modules-and-cards/cards/cards-reference.md#adaptive-card) |
| 10/08/2018 | Suporte ao cliente para DevTools.| [DevTools para o cliente da área de trabalho do Microsoft Teams](~/resources/dev-preview/developer-preview-tools.md)|
| 08/08/2018 | As extensões de mensagens agora suportam vários comandos. | [composeExtensions.commands](~/resources/schema/manifest-schema.md#composeextensionscommands)|
| 07/08/2018 | Agora há suporte para a configuração embutida nos Conectores. A documentação dos Conectores também foi revisada e expandida para maior clareza.| [Conectores](~/concepts/connectors/connectors.md)|
| 06/08/2018 | Seu bot agora pode enviar e receber arquivos. | [Enviar e receber arquivos por meio do seu bot](~/bots/how-to/bots-filesv4.md)|
| 23/07/2018 | Informações sobre a nova certificação de aplicativos foram adicionadas à seção Publicação. |[Permissões de manifesto](resources/schema/manifest-schema.md#permissions)|
| 16/07/2018 | Mais espaço foi alocado para a página de configuração da guia. | [A página de configuração da guia é significativamente mais alta](tabs/design/tabs.md)|
| 12/07/2018 | Informações sobre acesso de convidado. | [Acesso para convidado no Microsoft Teams](/microsoftteams/guest-access#guest-access-overview)|
| 07/06/2018 | Informações para o Catálogo de Aplicativos de Locatários do Microsoft Teams foram adicionadas. | [Publicar seu aplicativo Microsoft Teams](~/publishing/apps-publish.md)|
| 29/05/2018 | Há suporte para cartões adaptáveis no Teams. | [Ações de cartão adaptável no Teams](task-modules-and-cards/cards/cards-reference.md) |
| 17/04/2018 | replyToID foi adicionado ao conteúdo para `Invoke` e `MessageBack` ações de cartão. Isso é especialmente útil se você precisar atualizar a mensagem de origem da ação do cartão. | [Ações do cartão](~/concepts/cards/cards-actions.md)|
| 12/04/2018 | Este tópico foi adicionado para controlar as alterações na interface de programação do Teams e neste conjunto de documentação. | [Novidades](~/whats-new.md)|
| 10/04/2018 | As URLs de autenticação foram alteradas para usar consistentemente a ID de locatário no caminho. | [Fluxo de autenticação para Guias](~/concepts/authentication/auth-flow-tab.md), [Autenticação da Guia do Azure Active Directory](~/concepts/authentication/auth-tab-AAD.md)|
| 06/04/2018 | Foram adicionadas diretrizes de design para usar a Caixa de Comando. |[Caixa de comando](~/resources/design/framework/command-box.md)|
| 02/04/2018 | Usando bots para enviar notificações para seu aplicativo. |[Bots somente de notificação](~/concepts/bots/bots-notification-only.md)|
| 27/03/2018 | Documentação expandida para mensagens proativas. |[Iniciar uma conversa](./concepts/bots/bot-conversations/bots-conv-proactive.md)|
| 15/03/2018 | Documentação refatorada para cartões. |[Cartões](~/concepts/cards/cards.md), [Ações de cartão](~/concepts/cards/cards-actions.md), [Formatação de cartão](~/concepts/cards/cards-format.md), [Referência de cartão](~/concepts/cards/cards-reference.md)|
| 27/02/2018 | Código de exemplo adicionado para demonstrar o método AsTeamsChannelAccounts(). |[Obter contexto para o bot](~/concepts/bots/bots-context.md)|
| 05/02/2018 | Tópicos adicionados para começar a usar C#. |[Introdução à plataforma do Microsoft Teams com C#/.NET](./get-started/get-started-dotnet-app-studio.md)|
|
</details>
</details>
</details>
::: zone-end

::: zone pivot="dev-preview"

Descubra os recursos da plataforma Microsoft Teams que estão na versão prévia do desenvolvedor. Agora você pode obter as atualizações mais recentes da plataforma Teams assinando o RSS feed[![download](~/assets/images/RSSfeeds.png)](https://aka.ms/TeamsPlatformUpdates). Para obter mais informações, consulte [configurar RSS feed](#get-latest-updates).

## <a name="developer-preview"></a>Visualização do Desenvolvedor

:::row:::
:::column:::

:::image type="icon" source="~/assets/images/developer-preview.png" alt-text="Atualizações para recursos disponíveis na versão prévia do desenvolvedor":::

:::column-end:::
:::column span="2":::

A versão prévia do desenvolvedor é um programa público que fornece acesso antecipado a recursos de plataforma do Teams não lançadas.

**Setembro de 2022**

***23 de setembro de 2022: Introdução*** ao suporte ao aplicativo de [reunião para Reuniões de Canal Agendadas.](apps-in-teams-meetings/meeting-app-extensibility.md)

:::column-end:::
:::row-end:::

| **Date** | **Atualizar** | **Encontre aqui** |
| -------- | --------- | ------------------ |
| 08/23/2022 | Compartilhar aplicativos no estágio de reunião do Teams em dispositivos móveis | Criar aplicativos para reuniões e chamadas do Teams > [habilitar e configurar aplicativos para reuniões](/microsoftteams/platform/apps-in-teams-meetings/enable-and-configure-your-app-for-teams-meetings) |
| 08/10/2022 | Aplicativos para reuniões de canal público agendadas | Criar aplicativos para reuniões e chamadas do Teams > [Visão geral](apps-in-teams-meetings/teams-apps-in-meetings.md) |
| 03/08/2022 | Ativar e desativar mudo de APIs para aplicativos na janela de conteúdo compartilhado do Teams | Compilar aplicativos para reuniões e chamadas do Teams > [Referências da API de aplicativos de reunião](/microsoftteams/platform/apps-in-teams-meetings/api-references?tabs=dotnet) |
| 08/02/2022| Controles de colaboração para o Teams| Integrar com o Teams > [Controles de colaboração](samples/collaboration-control.md) |
| 30/06/2022 | Aplicativos para reuniões instantâneas, reuniões individuais e chamadas em grupo| Criar aplicativos para reuniões e chamadas do Teams > [Visão geral](apps-in-teams-meetings/teams-apps-in-meetings.md)|
|24/05/2022| Colaboração aprimorada com o SDK do Live Share | Criar aplicativos para reuniões do Teams > Colaboração aprimorada com o Live Share > [Visão geral](apps-in-teams-meetings/teams-live-share-overview.md) |
| 03/02/2022 | Apresentado o manifesto do aplicativo versão 1.13 | Manifesto do aplicativo > Visualização pública do desenvolvedor > [Esquema do manifesto](resources/schema/manifest-schema-dev-preview.md) |
| 17/01/2022 | Seletor de Pessoas em cartões adaptáveis para dispositivos móveis | Criar cartões e módulos de tarefa > Criar cartões > [Seletor de Pessoas em Cartões Adaptáveis](task-modules-and-cards/cards/people-picker.md)|
| 28/10/2021 |Os bots podem ser habilitados para receber todas as mensagens de canal usando o RSC (consentimento específico do recurso) | • Criar bots > Conversas de bot > [visão geral da conversa de bot](~/bots/how-to/conversations/conversation-basics.md) </br> • Criar bots > Conversas de bot > [conversas em grupo e canal](~/bots/how-to/conversations/channel-and-group-conversations.md) |
| 16/06/2021 | Consentimento específico de recursos para chats | • Utilizar dados do Teams com Microsoft Graph > [Consentimento específico do recurso](graph-api/rsc/resource-specific-consent.md) </br> • Testar seu aplicativo > Microsoft Graph > [Testar permissões de consentimento específicas do recurso no Teams](graph-api/rsc/test-resource-specific-consent.md)|

Para obter mais informações, consulte [prévia do desenvolvedor público para o Teams](~/resources/dev-preview/developer-preview-intro.md).

::: zone-end

::: zone pivot="dep-feature"

Descubra os recursos da plataforma Microsoft Teams que foram preteridos. Agora você pode obter as atualizações mais recentes da plataforma Teams assinando o RSS feed[![download](~/assets/images/RSSfeeds.png)](https://aka.ms/TeamsPlatformUpdates). Para obter mais informações, consulte [configurar RSS feed](#get-latest-updates).

## <a name="deprecated"></a>Preterido

:::row:::
:::column:::

:::image type="icon" source="~/assets/images/deprecated.png" alt-text="Recursos preteridos":::

:::column-end:::
:::column span="2":::

Recursos da plataforma Microsoft Teams que não estão disponíveis.

**Agosto de 2022**

***1º de agosto de 2022***: o App Studio foi preterido, use o [Portal do Desenvolvedor](concepts/build-and-test/teams-developer-portal.md) para Teams.

:::column-end:::
:::row-end:::

::: zone-end

## <a name="teams-app-template-catalog"></a>Catálogo de modelos de aplicativos do Teams

Along with new features, we also provide [production-ready Teams app templates](samples/app-templates.md) that you can deploy right away or modify to your needs. Newly added templates are indicated with a star ☆.

## <a name="submit-your-feedback"></a>Enviar seus comentários

Incentivamos os desenvolvedores do Teams a fazer perguntas, arquivos de bugs, enviar solicitações de recursos e fazer contribuições. Você pode enviar comentários por meio de qualquer um dos [canais disponíveis](feedback.md).

## <a name="get-latest-updates"></a>Obter as atualizações mais recentes

Você pode obter as atualizações mais recentes da plataforma Teams configurando o [RSS feed](https://aka.ms/TeamsPlatformUpdates).

### <a name="to-configure-rss-feed"></a>Para configurar RSS feed

1. Abra o Microsoft Teams.
1. Selecione **Teams** no painel esquerdo.
1. Selecione um canal na equipe.
1. Selecione reticências &#x25CF;&#x25CF;&#x25CF; e, na lista suspensa, selecione **Conectores**.
1. Pesquise **RSS** na caixa de diálogo **Conectores** exibida.
1. Selecione **Configurar**.
1. Insira um nome em **Insira um nome para sua conexão RSS.**.
1. Insira **<https://aka.ms/TeamsPlatformUpdates>** em **Endereço para RSS feed**.
1. Selecione a frequência do feed na lista suspensa **Frequência de mensagem**.
1. Selecione **Salvar**.
