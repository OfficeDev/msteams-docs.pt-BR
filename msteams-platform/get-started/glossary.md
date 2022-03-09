---
title: 'Documentação do Desenvolvedor do Microsoft Teams: Glossário'
description: Documentação do Desenvolvedor do Microsoft Teams
ms.localizationpriority: high
ms.topic: reference
keywords: Definição de desenvolvedor do Microsoft Teams
ms.openlocfilehash: 25d5cb5828671ffe464b9cd66a5d8de97db5ecbf
ms.sourcegitcommit: 3d7b34e7032b6d379eca8f580d432b365c8be840
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/18/2022
ms.locfileid: "62898072"
---
# <a name="glossary"></a>Glossário

Termos e definições comuns usados na Documentação do Desenvolvedor do Teams.


## <a name="a"></a>A

| Termo | Definição |
| --- | --- |
| [Comando de ação](../messaging-extensions/how-to/action-commands/define-action-command.md) | Um tipo de aplicativo de extensão de mensagens que usa um pop-up para coletar ou exibir informações. <br>**Consulte também**: [Extensão de mensagem](#m); [Comandos de busca](#s) |
| [Cartões Adaptáveis](../task-modules-and-cards/what-are-cards.md) | Um snippet de conteúdo acionável adicionado a uma conversa por um bot ou extensão de mensagens. Use texto, elementos gráficos e botões com essas placas para comunicação avançada. |
| [Usuário anônimo](../apps-in-teams-meetings/meeting-app-extensibility.md#user-types-in-a-meeting) | Um tipo de participante em uma reunião do Teams que não tem uma identidade do Azure AD e não é federado com um locatário. Eles são como usuários externos em uma reunião. <br>**Consulte também**: [Usuário federado](#f) |
| [Catálogo de Aplicativos](../toolkit/publish.md) | Um site que armazena aplicativos do SharePoint e do Office para uso interno de uma organização. <br>**Consulte também**: [SPFx](#s) |
| [Manifesto do aplicativo](../resources/schema/manifest-schema.md) | O manifesto do Teams descreve como o aplicativo se integra ao produto Microsoft Teams. Seu manifesto deve estar de acordo com o [esquema de manifesto](https://developer.microsoft.com/json-schemas/teams/v1.11/MicrosoftTeams.schema.json). |
| [Pacote do aplicativo](../concepts/build-and-test/apps-package.md) | Um pacote de aplicativos do Teams é um arquivo zip que contém o arquivo de manifesto do aplicativo, o ícone de cor e o ícone de estrutura de tópicos. |
| [Permissão de aplicativo](../concepts/device-capabilities/browser-device-permissions.md#enable-apps-device-permissions) | Uma opção em um aplicativo do Teams para habilitar permissões de dispositivo. Ele só estará disponível quando o arquivo de manifesto do aplicativo declarar que o aplicativo precisa de permissões de dispositivo. <br> **Consulte também**: Permissões de dispositivo |
| [Escopo do aplicativo](../concepts/design/app-structure.md) | Uma área no Teams em que as pessoas podem usar seu aplicativo. Os aplicativos podem ter um ou vários escopos, incluindo pessoal, canais, chats e reuniões. Um aplicativo teams pode existir entre escopos. |
| [App Studio](../concepts/build-and-test/app-studio-overview.md) | Um aplicativo para começar a criar ou integrar seus próprios aplicativos do Microsoft Teams. Agora ele evoluiu para Portal do Desenvolvedor. <br> **Consulte também**: [Portal do Desenvolvedor](#d) |
| Bandeja de aplicativos | Uma bandeja de aplicativos localizada na barra inferior de um aplicativo móvel do Teams. Ela coleta todos os aplicativos abertos, mas não usados no momento ou ativos. <br>**Consulte também**: [Teams para dispositivos móveis](#t) |
| [Recurso do Azure](../toolkit/provision.md) | Um serviço que está disponível por meio do Azure que seu aplicativo Teams pode usar para implantação do Azure. Pode ser contas de armazenamento, aplicativos Web, bancos de dados e muito mais. |
| [Azure Active Directory](../tabs/how-to/authentication/auth-tab-aad.md) | É o serviço de gerenciamento de identidades e acesso baseado na nuvem da Microsoft. Ele ajuda os usuários autenticados a acessar recursos internos e externos do Azure. |
| [Autenticação](../concepts/authentication/authentication.md) | Um processo para validar o acesso do usuário para o uso do aplicativo. Isso pode ser feito usando APIs do Microsoft Graph ou autenticação baseada na Web. <br> **Consulte também**: [Provedores de identidade](#i); [SSO](#s) |
| [Fluxo de autenticação](../concepts/authentication/authentication.md#web-based-authentication-flow) | No Teams, há dois fluxos de autenticação para autenticar um usuário para usar um aplicativo: autenticação baseada na Web e fluxo OAuthPrompt. |
|

## <a name="b"></a>B

| Termo | Definição |
| --- | --- |
| [Blazor](../get-started/get-started-overview.md) | Uma estrutura da Web gratuita e de software livre que permite aos desenvolvedores criar aplicativos Web usando C# e HTML. Ele está sendo desenvolvido pela Microsoft. |
| [Bicep](../toolkit/provision.md) | Uma linguagem declarativa, o que significa que os elementos podem aparecer em qualquer ordem. Ao contrário das linguagens imperativas, a ordem dos elementos não afeta como a implantação é processada. |
| [Bot](../bots/what-are-bots.md) | Um bot é um aplicativo que executa tarefas repetitivas programadas. <br> **Consulte também**: [Bot de conversa](#c); [Bot de chat](#c) |
| [Emulador de Bot](../bots/how-to/debug/locally-with-an-ide.md#use-the-bot-emulator) | Um aplicativo da área de trabalho que permite testar e depurar bots localmente ou remotamente. |
| [Bot Framework](../bots/bot-features.md) | Um SDK avançado usado para criar bots usando C#, Java, Python e JavaScript. Se você tiver um bot baseado no Bot Framework, poderá modificá-lo para funcionar no Teams. |
|

## <a name="c"></a>C

| Termo | Definição |
| --- | --- |
| [Bot de chamada](../bots/calls-and-meetings/calls-meetings-bots-overview.md) | Um bot que participa de chamadas de áudio ou vídeo e reuniões online. <br> **Confira também**: [Bot de chat](#c); [Bot de reunião](#m) |
| [Recursos](../toolkit/add-capability.md) | Um recurso do Teams que você pode criar em seu aplicativo para interagir com os usuários do aplicativo. Uma funcionalidade de aplicativo é usada para estender o Teams para atender às suas necessidades de aplicativo. Um aplicativo pode ter um ou mais recursos principais, como tab, bot e extensão de mensagens. <br>**Consulte também**: [Funcionalidade do dispositivo](#d); [Funcionalidade de mídia](#m) |
| [Bot de chat](../bots/how-to/conversations/conversation-basics.md) | Um bot também é conhecido como chatbot ou bot de conversa. É um aplicativo que executa tarefas simples e repetitivas por usuários, como atendimento ao cliente ou equipe de suporte. <br> **Consulte também**: [Bot de conversa](#c) |
| Canal | Um único local para uma equipe compartilhar mensagens, ferramentas e arquivos. Você pode usar um canal para trabalho em equipe e comunicação. <br>**Consulte também**: [Conversa](#c) |
| [Segredo do cliente](../bots/how-to/authentication/add-authentication.md) | O segredo/senha do cliente ou um par de chaves pública ou privada que é Certificado. Não é necessário para aplicativos nativos. <br> **Consulte também**: [Bot](#b) |
| [Recursos de nuvem](../toolkit/add-resource.md) | Um serviço que está disponível na nuvem por meio da Internet que seu aplicativo Teams pode usar. Pode ser contas de armazenamento, aplicativos Web, bancos de dados e muito mais. |
| [Aplicativo de colaboração](../concepts/extensibility-points.md) | Um aplicativo com funcionalidades para um usuário trabalhar em um workspace colaborativo com outros usuários. <br> **Consulte também**: [ Aplicativo autônomo](#s) |
| [Extensão Compose](../resources/schema/manifest-schema.md#composeextensions) | Uma propriedade no manifesto do aplicativo (`composeExtensions`) que se refere à funcionalidade de extensão de mensagens. Ele é usado quando sua extensão precisa ser autenticada ou configurada para continuar. <br>**Consulte também**: [Manifesto do aplicativo](#a); [Extensão de mensagem](#m) |
| [Caixa de comando](../resources/schema/manifest-schema.md) | Um tipo de contexto no manifesto do aplicativo (`commandBox`) que você pode configurar para invocar uma extensão de mensagens na caixa de comando do Teams. |
| [Connector](../webhooks-and-connectors/what-are-webhooks-and-connectors.md) | Os conectores permitem que os usuários se inscrevam para receber notificações e mensagens dos serviços Web. Eles expõem o ponto de extremidade HTTPS do serviço para postar mensagens nos canais do Teams, geralmente na forma de cartões. <br> **Consulte também**: [Webhook](#w) |
| Conversa | Uma série de mensagens enviadas entre o aplicativo Microsoft Teams (guia ou bot) e um ou mais usuários. Uma conversa pode ter três escopos: canal, pessoal e chat em grupo. <br>**Consulte também**: [Chat um a um](#o); [Chat em grupo](#g); [Canal](#c) |
| [Bot de conversa](../bots/how-to/conversations/conversation-messages.md) |  Ele permite que um usuário interaja com seu serviço Web usando texto, cartões interativos e módulos de tarefa. <br>**Consulte também** [Bot de chat](#c) |
|


## <a name="d"></a>D

| Termo | Definição |
| --- | --- |
| [Link profundo](../concepts/build-and-test/deep-links.md) | Em um aplicativo do Teams, você pode criar links profundos para informações e recursos no Teams ou para ajudar o usuário a navegar até o conteúdo em seu aplicativo. |
| [Portal do Desenvolvedor do Teams](../concepts/build-and-test/teams-developer-portal.md) | A principal ferramenta para configurar, distribuir e gerenciar seus aplicativos do Microsoft Teams. Com Portal do Desenvolvedor, você pode colaborar com colegas em seu aplicativo, configurar ambientes de runtime e muito mais. |
| [Pré-visualização do desenvolvedor](../resources/dev-preview/developer-preview-intro.md) | Um programa público para desenvolvedores que fornece acesso antecipado a recursos não lançados no Microsoft Teams. Isso permite que você explore e teste os recursos futuros para uma possível inclusão em seu aplicativo Microsoft Teams. |
| Implantar | Um processo para carregar o código de back-end e front-end para o aplicativo. Na Implantação, o código do aplicativo é copiado para os recursos criados durante o provisionamento. <br>**Consulte também**: [Provisionamento](#p) |
| [Funcionalidades de dispositivo](../concepts/device-capabilities/device-capabilities-overview.md) | Dispositivos internos, como câmera, microfone, scanner de código de barras, galeria de fotos, em um celular ou desktop. Você pode acessar os seguintes recursos de dispositivo em dispositivos móveis ou desktop por meio de APIs dedicadas disponíveis no SDK do cliente JavaScript do Microsoft Teams. <br>**Consulte também**: [Funcionalidade](#c); [Funcionalidade de mídia](#m); [Funcionalidade de localização](#l) |
| [Permissão do aplicativo](../concepts/device-capabilities/browser-device-permissions.md) | Uma configuração de aplicativo do Teams que você pode definir em seu aplicativo. Use-o para solicitar permissão para seu aplicativo acessar e utilizar uma funcionalidade de dispositivo nativo. Você pode gerenciar permissões de dispositivo nas configurações do Teams. <br>**Consulte também**: [Permissões do aplicativo](#a) |
| [Ambiente do desenvolvedor](../toolkit/teamsfx-multi-env.md#create-a-new-environment) | Um tipo de ambiente de desenvolvimento que o Kit de Ferramentas do Teams cria por padrão. Ele representa configurações de ambiente remoto ou de nuvem. Um projeto pode ter vários ambientes remotos. Você pode adicionar mais ambientes de desenvolvimento ao seu projeto usando o Kit de Ferramentas do Teams. <br>**Consulte também** [Ambiente](#e); [Ambiente local](#l) |
| [DevTools](../tabs/how-to/developer-tools.md) | As DevTools do Navegador são usadas para exibir logs do console, exibir ou modificar solicitações de rede de runtime, adicionar pontos de interrupção ao código (JavaScript) e executar a depuração interativa para um aplicativo do Teams. O recurso só estará disponível para clientes desktop e Android depois que a Visualização do Desenvolvedor tiver sido habilitada. |
| [Pesquisa dinâmica](../task-modules-and-cards/cards/dynamic-search.md#dynamic-typeahead-search) | Um recurso de pesquisa para Cartões Adaptáveis que é útil para pesquisar e selecionar dados de grandes conjuntos de dados. Ele ajuda a filtrar as opções à medida que o usuário insere a cadeia de caracteres de pesquisa. <br>**Consulte também**: [Pesquisa estática](#s) |
|


## <a name="e"></a>E

| Termo | Definição |
| --- | --- |
| [Conta de desenvolvedor E5](../toolkit/accounts.md) | Assinatura de desenvolvedor E5 para criar aplicativos para estender Microsoft 365. Você pode adicionar até 25 licenças de usuário, incluindo o administrador, para fins de desenvolvimento apenas.  <br>**Consulte também**: [Conta do Microsoft 365](#m) |
| [Ponto de entrada](../concepts/app-fundamentals-overview.md) | Um ponto de acesso, como equipe, canal e chat, para um aplicativo do Teams em que os usuários podem usar seu aplicativo. |
| [Ambiente](../toolkit/teamsfx-multi-env.md) | Um recurso no Kit de Ferramentas do Teams que permite criar e usar vários ambientes de desenvolvimento para seu projeto de aplicativo. Há dois ambientes de desenvolvimento que o Kit de Ferramentas do Teams cria por padrão, ambiente local e ambiente de desenvolvimento. <br>**Consulte também**: [Ambiente local](#l); [Ambiente de desenvolvimento](#d) |
|


## <a name="f"></a>S

| Termo | Definição |
| --- | --- |
| [Usuário federado](../apps-in-teams-meetings/meeting-app-extensibility.md#user-types-in-a-meeting) | Um tipo de usuário em uma reunião de aplicativo do Teams que é externo e é convidado para a reunião. Este usuário tem credenciais válidas que são federadas por parceiros autorizados do Teams. Eles também são chamados de Usuários externos. <br>**Consulte também**: [Usuário anônimo](#a) |
|

## <a name="g"></a>G

| Termo | Definição |
| --- | --- |
| [API do Graph](../graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md) | O Microsoft Graph é uma API Web RESTful que permite que você acesse os recursos de serviço do Microsoft Cloud. <br>**Consulte também**: [Microsoft Graph Explorer](#m) |
| [Chat em grupo](../resources/bot-v3/bot-conversations/bots-conversations.md) | Um recurso de chat em que um usuário pode conversar com um bot em uma configuração de grupo usando @mencionar para invocar o bot. <br>**Consulte  também**: [Chat um a um](#o); [Bot de chat](#c) |
|


## <a name="i"></a>I

| Termo | Definição |
| --- | --- |
| [Provedor de identidade](../concepts/authentication/configure-identity-provider.md) | Uma entidade que armazena e fornece credenciais para o usuário. Os usuários também podem se registrar com um provedor de identidade.  <br>**Consulte também**: [Autenticação](#a) |
| [Webhook de entrada](../webhooks-and-connectors/how-to/add-incoming-webhook.md) | Ele permite que um aplicativo externo compartilhe conteúdo em canais do Teams. Esses webhooks são usados como ferramentas de acompanhamento e notificação. <br>**Consulte também**: [Webhook](#w); [Webhook de saída](#o) |
| [Experiência de aplicativo na reunião](../apps-in-teams-meetings/meeting-app-extensibility.md#in-meeting-app-experience) | Um estágio do ciclo de vida de reunião do Teams. Com a experiência do aplicativo na reunião, você pode envolver os participantes durante a reunião usando aplicativos e a caixa de diálogo na reunião. <br>**Consulte também**: [Ciclo de vida de reunião](#m) |
|


## <a name="l"></a>L

| Termo | Definição |
| --- | --- |
| [Desenrolamento de link](../messaging-extensions/how-to/link-unfurling.md) | Um recurso usado com extensão de mensagens e reunião para revelar links colados em uma área de mensagem de redação. Os links se expandem para mostrar informações adicionais sobre o link no Cartões Adaptáveis ou no modo de exibição do estágio da reunião. |
| [Ambiente local](../toolkit/teamsfx-multi-env.md#create-a-new-environment) | Um ambiente de desenvolvimento padrão criado pelo Kit de Ferramentas do Teams.  <br>**Consulte tambérm**: [Ambiente](#e); [Ambiente de desenvolvimento](#d) |
| [Workbench local](../sbs-gs-spfx.yml) | A opção padrão para executar e depurar um aplicativo do Teams no Visual Studio Code criado usando SPFx. <br>**Consulte também**: [Workbench](#w); [Workbench do Teams](#t) |
| [Funcionalidade de localização](../concepts/device-capabilities/location-capability.md) | Uma funcionalidade de dispositivo que você pode integrar ao seu aplicativo para saber a localização geográfica do usuário do aplicativo para uma experiência colaborativa aprimorada. Atualmente, esse recurso está disponível apenas para clientes móveis do Teams. <br>**Consute também**: [Funcionalidade](#c); [Funcionalidade de mídia](#m); [Funcionalidade do dispositivo](#d); [Teams para dispositivos móveis](#t) |
| [Aplicativos de baixa codificação](../samples/teams-low-code-solutions.md) | Um aplicativo personalizado do Teams criado do zero usando o Microsoft Power Platform que requer pouca ou nenhuma codificação e pode ser desenvolvido e implantado rapidamente. |
|


## <a name="m"></a>M

| Termo | Definição |
| --- | --- |
| [Funcionalidade de mídia](../concepts/device-capabilities/mobile-camera-image-permissions.md) | Funcionalidades nativas do dispositivo, como câmera e microfone, que você pode integrar ao seu aplicativo Teams. <br>**Consulte também**: [Funcionalidade](#c); [Funcionalidade do dispositivo](#d) |
| [Bot de reunião](../bots/calls-and-meetings/calls-meetings-bots-overview.md) | Bots que interagem com chamadas e reuniões do Teams usando voz, vídeo e compartilhamento de tela em tempo real. <br>**Consulte também**: [Bot de chamada](#c); [Bot de chat](#c) |
| [Ciclo de vida da reunião](../apps-in-teams-meetings/meeting-app-extensibility.md#meeting-lifecycle) | Abrange desde a experiência de aplicativos de pré-reunião, em reunião e pós-reunião. Você pode integrar guias, bots e extensões de mensagens em cada estágio do ciclo de vida da reunião. <br>**Consulte também**: [Experiências em reunião](#i) |
| [Estágio da reunião](../sbs-meetings-stage-view.yml) | Um recurso do aplicativo de extensão de reunião. É um espaço compartilhado acessível a todos os participantes durante a reunião. Ele ajuda os participantes a interagir e colaborar com o conteúdo do aplicativo em tempo real. <br>**Consulte também**: [Exibição do estágio](#s) |
| [Extensão de mensagem](../messaging-extensions/what-are-messaging-extensions.md) | Extensões de mensagens são atalhos para inserir conteúdo do aplicativo ou agir em uma mensagem. Você pode usar uma extensão de mensagens sem sair da conversa. <br>**Consulte também**: [Comandos de pesquisa](#s); [Comandos de ação](#a) |
| [Extensão da reunião](../apps-in-teams-meetings/design/designing-apps-in-meetings.md) | Um aplicativo projetado para ser usado durante o ciclo de vida da reunião para torná-lo mais produtivo, como quadro de comunicações, painel e muito mais. |
| [Conta do Microsoft 365](../toolkit/accounts.md#microsoft-365-account) | Uma conta do Microsoft 365 inclui 25 licenças de usuário, incluindo o administrador, apenas para fins de desenvolvimento. |
| [Programa para desenvolvedores do Microsoft 365](../toolkit/accounts.md#join-microsoft-365-developer-program) | O Programa para desenvolvedores do Microsoft 365 te ajuda a criar aplicativos que estendem o Microsoft 365. |
| [Microsoft Graph Explorer](../graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md) | O caminho para dados e inteligência no Microsoft 365. Fornece um modelo de programação unificado que permite acessar dados no Microsoft 365, Windows 10 e Enterprise Mobility + Security. |
| [Microsoft Teams](../overview.md) | O Microsoft Teams é um software de colaboração em grupo que pode ser usado para ajudar as equipes a trabalharem em conjunto remotamente. |
| [Plataforma do Microsoft Teams](../concepts/app-fundamentals-overview.md) | A plataforma de desenvolvedor do Microsoft Teams facilita que os desenvolvedores integrem seus próprios aplicativos e serviços com o Teams. |
| [Biblioteca de Interface do Usuário do Microsoft Teams](../concepts/design/design-teams-app-ui-templates.md#microsoft-teams-ui-library) | A Biblioteca de Interface do Usuário do Microsoft Teams ajuda você a exibir e testar modelos de interface do usuário individuais do Teams e componentes relacionados em seu navegador. |
| [Kit de Ferramentas de Interface do Usuário do Microsoft Teams](../concepts/design/design-teams-app-ui-templates.md#microsoft-teams-ui-library) | O Kit de Interface do Usuário do Microsoft Teams inclui componentes e padrões projetados especificamente para a criação de aplicativos do Teams. |
|


## <a name="o"></a>O

| Termo | Definição |
| --- | --- |
| [Conector do Office 365](../webhooks-and-connectors/how-to/connectors-creating.md) | Permitem que você crie uma página de configuração personalizada para seu Webhook de entrada e os empacote como parte de um aplicativo do Teams. Você envia mensagens principalmente usando cartões do Conector do Office 365 e tem a capacidade de adicionar um conjunto limitado de ações de cartão a elas. |
| [Webhook de saída](../webhooks-and-connectors/how-to/add-outgoing-webhook.md) | O Webhook de Saída atua como um bot e pesquisa mensagens em canais usando @mencionar. Ele envia notificações para serviços Web externos e responde com mensagens avançadas, que incluem cartões e imagens. <br>**Consulte também**: [Webhook](#w); [Webhook de entrada](#i) |
| [Canal do Outlook](../m365-apps/extend-m365-teams-message-extension.md#add-an-outlook-channel-for-your-bot) | Um recurso do aplicativo de extensão de mensagens do Teams que permite que os usuários interajam com ele do Microsoft Outlook. |
| [Chat um a um](../resources/bot-v3/bot-conversations/bots-conv-personal.md) | Um tipo de chat entre um aplicativo de bot pessoal do Teams e um único usuário. <br>**Consulte também**: [Chat de grupo](#g); [Bot de chat](#c) |
|


## <a name="p"></a>P

| Termo | Definição |
| --- | --- |
| [People Picker](../task-modules-and-cards/cards/people-picker.md) | Um controle nativo na plataforma Teams para pesquisar e selecionar pessoas, que podem ser integradas em aplicativos Web, Cartões Adaptáveis e muito mais. |
| [Aplicativo pessoal](../concepts/design/personal-apps.md) | Um aplicativo pessoal é um aplicativo do Teams com um escopo pessoal. Ele se concentra em interações com um único usuário. Pode ser um bot de conversa para se envolver em conversas um a um com um usuário ou uma guia pessoal fornecendo uma experiência na Web inserida ou ambos. <br>**Consulte também**: [Aplicativo compartilhado](#s) |
| [Agentes virtuais do Power](../bots/how-to/add-power-virtual-agents-bot-to-teams.md) | Uma solução de interface gráfica guiada sem código que capacita todos os membros da sua equipe a criar bots de chat avançados e conversacionais que se integram facilmente à plataforma do Teams. |
| [Mensagens proativas](../bots/how-to/conversations/send-proactive-messages.md) | Uma mensagem enviada por um bot que não está em resposta a uma solicitação de um usuário, como mensagens de boas-vindas, notificações, mensagens agendadas. |
| [Provisão](../toolkit/provision.md) | Um processo que cria recursos no Azure e Microsoft 365 para seu aplicativo, mas nenhum código (HTML, CSS, JavaScript etc.) é copiado para os recursos. É um pré-requisito para a implantação. <br>**Consulte também**: [Implantar](#d) |
|


## <a name="r"></a>R

| Termo | Definição |
| --- | --- |
| [Limitação de taxa](../bots/how-to/rate-limit.md) | Um método para limitar as mensagens a uma determinada frequência máxima para garantir que o número de mensagens seja suficiente e não apareça como spam. |
| [Exibições baseadas em função](../task-modules-and-cards/cards/universal-actions-for-adaptive-cards/user-specific-views.md) | Um recurso de guias em que a experiência de guia pode ser diferente para os usuários, dependendo do nível de permissão. |
| [Permissão RSC](../graph-api/rsc/resource-specific-consent.md) | O recurso de permissão RSC (consentimento específico do recurso) é necessário para os proprietários da equipe permitirem que um aplicativo de bot receba mensagens entre canais em uma equipe sem @mencionado. |
|


## <a name="s"></a>S

| Termo | Definição |
| --- | --- |
| [Comandos de pesquisa](../messaging-extensions/how-to/search-commands/define-search-command.md) | Um tipo de aplicativo de extensão de mensagens que permite aos usuários pesquisar sistemas externos e incluir o resultado da pesquisa em uma mensagem usando um cartão. <br>**Consulte também**: [Extensões de mensagem](#m); [Comandos de ação](#a) |
| [Fluxo de trabalho sequencial](../task-modules-and-cards/cards/universal-actions-for-adaptive-cards/sequential-workflows.md) | Um fluxo de trabalho que permite que um bot execute uma conversa com um usuário com base na resposta do usuário. |
| [Aplicativo compartilhado](../concepts/extensibility-points.md#shared-app-experiences) | Um aplicativo que existe em uma equipe, canal ou chat em que os usuários podem colaborar e interagir. <br>**Consulte também:** Aplicativo pessoal |
| [Site de coleta do SharePoint](../sbs-gs-spfx.yml) | Um site de coleta para aplicativos do SharePoint. Você precisa ter uma conta de administrador para este site antes de implantar seu aplicativo baseado em SPFx no site do SharePoint. <br>**Consulte também**: SPFx |
| [Sideload](../toolkit/publish.md#publish-to-individual-scope-or-sideload-permission) | Um processo em que um aplicativo do Teams é carregado para o cliente do Teams para testá-lo no ambiente do Teams antes de distribuí-lo. |
| [SidePanel](../sbs-meetings-sidepanel.yml) | Um recurso do aplicativo de reunião do Teams que permite personalizar experiências em uma reunião que permite que organizadores e apresentadores tenham um conjunto diferente de exibições e ações. |
| [SPFx](../sbs-gs-spfx.yml) | A Estrutura do SharePoint (SPFx) é um modelo de desenvolvimento para criar soluções do lado do cliente para o Microsoft Teams e o SharePoint. |
| SSO | Acrônimo para logon único, um método de autenticação no qual um usuário precisa entrar em um serviço independente de uma plataforma de software (como o Microsoft 365) apenas uma vez. Em seguida, o usuário pode acessar todos os serviços sem precisar passar pela autenticação novamente. <br>**Consulte também**: [Autenticação](#a) |
| [Modo de exibição de estágio](../sbs-meetings-stage-view.yml) | Um componente de interface do usuário que permite renderizar o conteúdo que é aberto em tela inteira no Teams e fixado como uma guia. Ele é invocado para exibir o conteúdo da Web no Teams. Observe que *não* é a mesma coisa que estágio da reunião. <br>**Consulte também**: [Estágio de reunião](#m) |
| [Aplicativo autônomo](../samples/integrating-web-apps.md) | Um aplicativo de página única ou grande e complexo. O usuário pode usar alguns aspectos dele no Teams. <br>**Consulte também**: [Aplicativo de colaboração](#c) |
| [Pesquisa estática](../task-modules-and-cards/cards/dynamic-search.md) | Um método de pesquisa typeahead que permite que os usuários pesquisem de valores pré-especificados no conteúdo da carga de Cartões adaptáveis. <br>**Consulte também**: [Pesquisa Dinâmica](#d) |
| [Diretrizes de validação da loja](../concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md) | Um conjunto de diretrizes específicas do Teams para validar um aplicativo antes que ele possa ser enviado para a loja do Teams. <br>**Consulte também**: [Teams store](#t) |
|


## <a name="t"></a>T

| Termo | Definição |
| --- | --- |
| [Tab](../tabs/what-are-tabs.md) | As guias são páginas da Web com reconhecimento de Equipes inseridas no Microsoft Teams que apontam para domínios declarados no manifesto. Você pode adicioná-lo dentro de uma equipe, chat em grupo ou aplicativo pessoal. |
| [Chat da guia](../tabs/how-to/conversational-tabs.md) | Um tipo de guia que permite que um usuário tenha uma experiência de conversa focada em guias dinâmicas. |
| [Módulos de tarefas](../task-modules-and-cards/what-are-task-modules.md) | Um recurso do aplicativo Teams para criar pop-up modal para concluir tarefas, exibir vídeos ou dashboard. |
| [Discussão da thread](../tabs/design/tabs.md#thread-discussion) | Uma conversa postada em um canal ou chat entre usuários. <br>**Consulte também** [Canal](#c);[de conversa](#c) |
| [Teams](../overview.md) | O Microsoft Teams é o aplicativo de mensagens mais completo para sua organização. Ele é um espaço de trabalho para reuniões, colaboração e comunicação, compartilhamento de arquivos e aplicativos em tempo real. |
| [Kit de ferramentas do Teams](../toolkit/teams-toolkit-fundamentals.md) | O Kit de Ferramentas do Microsoft Teams permite criar aplicativos personalizados do Teams diretamente no ambiente do Visual Studio Code.  |
| [TeamsFx](../toolkit/teamsfx-cli.md) | O TeamsFx é uma interface de linha de comando baseada em texto que acelera o desenvolvimento de aplicativos do Teams. Ele também é chamado de CLI do TeamsFx.|
| [TeamsFx SDK](../toolkit/teamsfx-sdk.md) | O SDK do TeamsFx é pré-configurado no projeto com scaffolding usando o Kit de Ferramentas do TeamsFx ou a CLI. |
| [Teams para dispositivos móveis](../concepts/design/plan-responsive-tabs-for-teams-mobile.md) | O Microsoft Teams disponível como um aplicativo móvel. |
| [Teams store](../concepts/deploy-and-publish/appsource/publish.md) | Uma página de aterrissagem da loja que leva aplicativos para os usuários em um único lugar. Os aplicativos são categorizados por uso, setor e muito mais. Um aplicativo deve seguir as diretrizes de validação da Store e obter uma aprovação antes que ele seja disponibilizado aos usuários por meio da loja do Teams.  <br>**Consulte também**: [Diretrizes de validação da loja](#s) |
| [Workbench do Teams](../sbs-gs-spfx.yml) | Um workbench no Visual Studio Code usado no build para aplicativos do Teams criados usando o SPFx e o Kit de Ferramentas do Teams. <br>**Consulte também**: [Workbench](#w); [Workbench local](#l) |
|


## <a name="u"></a>U

| Termo | Definição |
| --- | --- |
| [Componentes da Interface de Usuário](../concepts/design/design-teams-app-basic-ui-components.md) | Para o desenvolvimento de aplicativos do Teams, você pode usar componentes da interface do usuário fluente para compilar seu aplicativo do zero. |
| [Modelos de Interface de Usuário ](../concepts/design/design-teams-app-ui-templates.md) | Para o desenvolvimento de aplicativos do Teams, você pode usar modelos de interface do usuário do Teams para projetar seus aplicativos rapidamente. |
| [Ações Universais para Cartões Adaptáveis](../task-modules-and-cards/cards/universal-actions-for-adaptive-cards/overview.md) | Uma maneira de implementar Cartões Adaptáveis em plataformas e aplicativos. Ele usa um bot como um back-end comum para lidar com ações. |
|


## <a name="v"></a>S

| Termo | Definição |
| --- | --- |
| [Assistente Virtual](../samples/virtual-assistant.md) | Um modelo de software livre da Microsoft que permite que você crie uma solução de conversação robusta. |
|


## <a name="w"></a>W

| Termo | Definição |
| --- | --- |
| [URL do site](../tabs/design/tabs-mobile.md) | Uma propriedade no arquivo de manifesto do aplicativo (`websiteUrl`) que vincula o aplicativo ao site da organização ou à página de aterrissagem do produto relevante. É uma configuração obrigatória para o cliente móvel do Teams. <br>**Consulte também**: [Manifesto do aplicativo](#a); [Teams para dispositivos móveis](#t) |
| [Aplicativo Web](../samples/integrate-web-apps-overview.md) | Um aplicativo que é executado em um servidor Web. Ele pode ser integrado à Plataforma do Microsoft Teams. |
| [Webhook](../webhooks-and-connectors/what-are-webhooks-and-connectors.md) | É um recurso de um aplicativo Teams usado para integrá-lo a aplicativos externos. <br>**Consulte também**: Webhook de entrada; webhook de saída |
| [Web Part](../sbs-gs-spfx.yml) | Um componente de interface do usuário usado para criar uma página ou um site em um aplicativo do Teams criado usando o Visual Studio Code e a Estrutura do SharePoint. <br>**Consulte também**: [SPFx](#s) |
| [Workbench](../sbs-gs-spfx.yml) | Interface do usuário geral do Visual Studio Code que abrange componentes da interface do usuário, como barra de título, painel e muito mais. <br>**Consulte também**: [Workbench local](#l); [Workbench do Teams](#t) |

    
## <a name="y"></a>S

| Termo | Definição |
| --- | --- |
| [YoTeams](../get-started/get-started-overview.md) | Um kit de ferramentas de desenvolvimento para a criação de aplicativos do Microsoft Teams com base em TypeScript e node.js. |
|