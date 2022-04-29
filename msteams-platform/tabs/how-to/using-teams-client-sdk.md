---
title: Criando guias e outras experiências hospedadas com o SDK do cliente JavaScript
author: heath-hamilton
ms.author: surbhigupta
description: Visão geral do SDK do cliente JavaScript do Microsoft Teams, que pode ajudá-lo a criar experiências de aplicativo do Teams hospedadas em um <iframe>. Inclui funções básicas, namespace de autenticação e namespace de configurações.
ms.localizationpriority: high
keywords: equipes guias grupo canal configurável estático SDK JavaScript pessoal
ms.topic: conceptual
ms.openlocfilehash: f4204555e57c270ad03a7a01d5b231d63b72296a
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111889"
---
# <a name="building-tabs-and-other-hosted-experiences-with-the-microsoft-teams-javascript-client-sdk"></a>Criando guias e outras experiências hospedadas com o SDK do cliente JavaScript do Microsoft Teams

O SDK do cliente JavaScript do Microsoft Teams pode ajudá-lo a criar experiências hospedadas no Teams, o que significa exibir o conteúdo do aplicativo em um iframe.

O SDK é útil para desenvolver aplicativos com qualquer um dos seguintes recursos do Teams:

* [Guias](../../tabs/what-are-tabs.md)
* [Módulos de tarefas](../../task-modules-and-cards/what-are-task-modules.md)

Por exemplo, o SDK pode fazer com que sua [guia reaja às alterações de tema](../../build-your-first-app/build-personal-tab.md#3-update-your-tab-theme) que seus usuários fazem no cliente do Teams.

## <a name="getting-started"></a>Introdução

Siga um destes procedimentos, dependendo de suas preferências de desenvolvimento:

* [Instalar o SDK com npm ou Yarn](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)
* [Clone o SDK (GitHub)](https://github.com/OfficeDev/microsoft-teams-library-js)

## <a name="common-sdk-functions"></a>Funções comuns do SDK

Consulte as tabelas a seguir para entender as funções do SDK comumente usadas. A [documentação de referência do SDK](/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true) fornece informações mais abrangentes.

### <a name="basic-functions"></a>Funções básicas

| Função  | Descrição          | Documentação|
| -----     | -----     | -----    |
| `microsoftTeams.initialize()` | Inicializa o SDK. Essa função deve ser chamada antes de qualquer outra chamada do SDK.|[função](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#@microsoft-teams-js-microsoftteams-initialize&preserve-view=true)|
|`microsoftTeams.getContext(callback: (context: Context)`| Obtém o estado atual em que a página está sendo executada. O retorno de chamada recupera o objeto **Context**.|[função](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest&preserve-view=true)<br/>[objeto de contexto](/javascript/api/@microsoft/teams-js/@microsoft.teams-js?view=msteams-client-js-latest&preserve-view=true)|
| `microsoftTeams.initializeWithContext({contentUrl: string, websiteUrl: string})` | Inicializa a biblioteca do Teams e define o [contexto de quadro](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true) da guia dependendo de contentUrl e websiteUrl. Isso garante que a funcionalidade go-to-website/reload funcione na URL correta.|[função](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#@microsoft-teams-js-microsoftteams-initializewithframecontext&preserve-view=true)|
| `microsoftTeams.setFrameContext({contentUrl: string, websiteUrl: string})` | Define o [contexto de frame](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true) da guia dependendo de contentUrl e websiteUrl. Isso garante que a funcionalidade go-to-website/reload funcione na URL correta.|[função](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#@microsoft-teams-js-microsoftteams-setframecontext&preserve-view=true)|
| `microsoftTeams.registerFullScreenHandler(handler: (isFullScreen: Boolean)` |O manipulador que é registrado quando o usuário alterna a exibição de tela inteira/janela de uma guia.|[função](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#@microsoft-teams-js-microsoftteams-registerfullscreenhandler&preserve-view=true)<br/>[Boolean](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#@microsoft-teams-js-microsoftteams-registerfullscreenhandler&preserve-view=true)|
|`microsoftTeams.registerChangeSettingsHandler()` |O manipulador que é registrado quando o usuário seleciona o botão **Configurações** para reconfigurar uma guia.|[função](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest&preserve-view=true)|
| `microsoftTeams.getTabInstances(callback: (tabInfo: TabInformation),tabInstanceParameters?: TabInstanceParameters,)` |Obtém as guias de propriedade do aplicativo. O retorno de chamada recupera o objeto **TabInformation**. O objeto **TabInstanceParameters** é um parâmetro opcional.|[função](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#@microsoft-teams-js-microsoftteams-gettabinstances&preserve-view=true)<br/>[tabInfo obj](/javascript/api/@microsoft/teams-js/microsoftteams.tabinformation?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.getMruTabInstances(callback: (tabInfo: TabInformation),tabInstanceParameters?: TabInstanceParameters)`|Obtém as guias usadas mais recentemente para o usuário. O retorno de chamada recupera o objeto **TabInformation**. O objeto **TabInstanceParameters** é um parâmetro opcional.|[função](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#@microsoft-teams-js-microsoftteams-getmrutabinstances&preserve-view=true)<br/>[tabInfo obj](/javascript/api/@microsoft/teams-js/microsoftteams.tabinformation?view=msteams-client-js-latest&preserve-view=true)<br/>[tabInstance obj](/javascript/api/@microsoft/teams-js/microsoftteams.tabinstanceparameters?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.shareDeepLink(deepLinkParameters: DeepLinkParameters)`|Usa o objeto **DeepLinkParameters** como entrada e compartilha uma caixa de diálogo de link direto que um usuário pode usar para navegar até o conteúdo *dentro da guia*.|[função](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#@microsoft-teams-js-microsoftteams-sharedeeplink&preserve-view=true)<br/>[deepLink obj](/javascript/api/@microsoft/teams-js/microsoftteams.deeplinkparameters?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.executeDeepLink(deepLink: string, onComplete?: (status: Boolean, reason?: string))`|Usa um **deepLink** necessário como entrada e direciona o usuário para um URL ou aciona uma ação do cliente, como abrir ou instalar um aplicativo *no Teams*.|[função](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#@microsoft-teams-js-microsoftteams-executedeeplink&preserve-view=true)|
|`microsoftTeams.navigateToTab(tabInstance: TabInstance, onComplete?: (status: Boolean, reason?: string))`|Recebe o objeto **TabInstance** como entrada e navega para uma instância de guia especificada.|[função](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#@microsoft-teams-js-microsoftteams-navigatetotab&preserve-view=true)<br/>[tabInstance obj](/javascript/api/@microsoft/teams-js/microsoftteams.tabinstance?view=msteams-client-js-latest&preserve-view=true)|

### <a name="authentication-namespace"></a>Namespace de autenticação

| Função  | Descrição          | Documentação|
| -----     | -----     | -----    |
|`microsoftTeams.authentication.authenticate(authenticateParameters?: AuthenticateParameters)`|Inicia uma solicitação de autenticação que abre uma nova janela com os parâmetros fornecidos pelo chamador. Os valores de entrada opcionais são definidos pelo objeto **AuthenticateParameters**.|[função](/javascript/api/@microsoft/teams-js/microsoftteams.authentication?view=msteams-client-js-latest&preserve-view=true)<br/>[auth obj](/javascript/api/@microsoft/teams-js/microsoftteams.authentication.authenticateparameters?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.authentication.notifySuccess(result?: string, callbackUrl?: string)`|Notifica o quadro que iniciou a solicitação de autenticação que a solicitação foi bem-sucedida e fecha a janela de autenticação|[função](/javascript/api/@microsoft/teams-js/microsoftteams.authentication?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.authentication.notifyFailure(reason?: string, callbackUrl?: string)`|Notifica o quadro que iniciou a solicitação de autenticação que a solicitação falhou e fecha a janela de autenticação.|[função](/javascript/api/@microsoft/teams-js/microsoftteams.authentication?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.authentication.getAuthToken(authTokenRequest: AuthTokenRequest)`|Envie uma solicitação para emitir o token do Azure Active Directory em nome do aplicativo. O token pode ser adquirido do cache, se não tiver expirado. Caso contrário, uma solicitação é enviada ao Azure Active Directory para obter um novo token.|[função](/javascript/api/@microsoft/teams-js/microsoftteams.authentication?view=msteams-client-js-latest#@microsoft-teams-js-microsoftteams-authentication-getauthtoken&preserve-view=true)|

### <a name="settings-namespace"></a>Namespace de configurações

| Função  | Descrição          | Documentação|
| -----     | -----     | -----    |
|`microsoftTeams.settings.setValidityState(validityState: Boolean)`|O valor inicial é falso. Ativa o botão **Salvar** ou **Remover** quando o estado de validade é verdadeiro.|[função](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.settings.getSettings(callback: (instanceSettings: Settings)`|Obtém as configurações da instância atual. O retorno de chamada recupera o objeto **Configurações**.|[função](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true)<br/>[configurações obj](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.settings.setSettings(instanceSettings: Settings, onComplete?: (status: Boolean, reason?: string)`|Define as configurações para a instância atual. As configurações válidas são definidas pelo objeto **Configurações**.|[função](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true)<br/>[configurações obj](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.settings.registerOnSaveHandler(handler: (evt: SaveEvent)`|O manipulador que é registrado quando o usuário seleciona o botão **Salvar**. Esse manipulador deve ser usado para criar ou atualizar o recurso subjacente que alimenta o conteúdo.|[função](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.settings.registerOnRemoveHandler(handler: (evt: RemoveEvent)`|O manipulador que é registrado quando o usuário seleciona o botão **Remover**. Esse manipulador deve ser usado para remover o recurso subjacente que alimenta o conteúdo.|[função](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true)|

### <a name="task-modules-namespace"></a>Espaço de nomes dos módulos de tarefa

| Função  | Descrição          | Documentação|
| -----     | -----     | -----    |
|`microsoftTeams.tasks.startTask(taskInfo: TaskInfo, submitHandler?: (err: string, result: string)`|Recebe o objeto **TaskInfo** como entrada e permite que um aplicativo abra o módulo de tarefa. O opcional **submitHandler** é registrado quando o módulo de tarefa é concluído. |[função](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest&preserve-view=true)<br/>[taskInfo obj](/javascript/api/@microsoft/teams-js/microsoftteams.taskinfo?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.tasks.submitTask(result?: string | object, appIds?: string | string[])`|Envia o módulo de tarefa. O parâmetro **resultado** cadeia de caracteres opcional é o resultado enviado ao bot ou ao aplicativo e normalmente é um objeto JSON ou serialização; O parâmetro opcional **appIds** cadeia de caracteres ou matriz de cadeia de caracteres auxilia na validação de que a chamada se originou da mesma appId que a que invocou o módulo de tarefa.|[função](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#@microsoft-teams-js-microsoftteams-tasks-submittask&preserve-view=true)|
