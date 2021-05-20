---
title: Construindo guias e outras experiências hospedadas com o Cliente JavaScript SDK
author: heath-hamilton
ms.author: surbhigupta
description: Visão geral do Microsoft Teams SDK cliente JavaScript, que pode ajudá-lo a construir Teams experiências de aplicativos hospedadas em um <iframe>.
localization_priority: Normal
keywords: equipes guias canal de grupo configurável estático SDK JavaScript pessoal
ms.topic: conceptual
ms.openlocfilehash: d3dfadda7f2a56e32ecf8e5b67df3b9831c52739
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566653"
---
# <a name="building-tabs-and-other-hosted-experiences-with-the-microsoft-teams-javascript-client-sdk"></a>Construindo guias e outras experiências hospedadas com o Microsoft Teams cliente JavaScript SDK

O Microsoft Teams cliente JavaScript SDK pode ajudá-lo a criar experiências hospedadas em Teams, o que significa exibir o conteúdo do seu aplicativo em um iframe.

O SDK é útil para desenvolver aplicativos com qualquer um dos seguintes recursos Teams:

* [Guias](../../tabs/what-are-tabs.md)
* [Módulos de tarefas](../../task-modules-and-cards/what-are-task-modules.md)

Por exemplo, o SDK pode fazer sua [guia reagir às alterações de tema](../../build-your-first-app/build-personal-tab.md) que seus usuários fazem no Teams cliente.

## <a name="getting-started"></a>Introdução

Faça um dos seguintes, dependendo de suas preferências de desenvolvimento:

* [Instale o SDK com npm ou Yarn](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)

## <a name="common-sdk-functions"></a>Funções SDK comuns

Consulte as tabelas a seguir para entender as funções SDK comumente usadas. A [documentação de referência do SDK](/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true) fornece informações mais abrangentes:


### <a name="basic-functions"></a>Funções básicas

| Função  | Descrição          | Documentação|
| -----     | -----     | -----    |
| `microsoftTeams.initialize()` | Inicializa o SDK. Esta função deve ser chamada antes de qualquer outra chamada SDK.|[função](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#initialize-any-&preserve-view=true)|
|`microsoftTeams.getContext(callback: (context: Context)`| Obtém o estado atual em que a página está sendo executado. O retorno de chamada recupera o objeto **Contexto.**|[função](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#getcontext--context--context-----void-&preserve-view=true)<br/>[contexto obj](/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true)|
| `microsoftTeams.initializeWithContext({contentUrl: string, websiteUrl: string})` | Inicializa a biblioteca Teams e define o [contexto](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true) do quadro da guia dependendo do conteúdoUrl e siteUrl. Isso garante que a funcionalidade go-to-site ou recarregar seja operada na URL correta.|[função](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#initializewithframecontext-framecontext--------void--string---&preserve-view=true)|
| `microsoftTeams.setFrameContext({contentUrl: string, websiteUrl: string})` | Define o contexto do [quadro](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true) da guia dependendo do contentUrl e do siteUrl. Isso garante que a funcionalidade go-to-site ou recarregar seja operada na URL correta.|[função](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#setframecontext-framecontext-&preserve-view=true)|
| `microsoftTeams.registerFullScreenHandler(handler: (isFullScreen: boolean)` |O manipulador que é registrado quando o usuário alterna a exibição em tela cheia ou com janelas de uma guia.|[função](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#registerfullscreenhandler--isfullscreen--boolean-----void-&preserve-view=true)<br/>[boolean](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#registerFullScreenHandler__isFullScreen__boolean_____void_&preserve-view=true)|
|`microsoftTeams.registerChangeSettingsHandler()` |O manipulador registrado quando o usuário seleciona o botão **Configurações** habilitado para reconfigurar uma guia.|[função](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#registerchangesettingshandler-------void-&preserve-view=true)|
| `microsoftTeams.getTabInstances(callback: (tabInfo: TabInformation),tabInstanceParameters?: TabInstanceParameters,)` |Obtém as guias de propriedade do aplicativo. O retorno de chamada recupera o objeto **TabInformation.** O objeto **TabInstanceParameters** é um parâmetro opcional.|[função](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#gettabinstances--tabinfo--tabinformation-----void--tabinstanceparameters-&preserve-view=true)<br/>[tabInfo obj](/javascript/api/@microsoft/teams-js/tabinformation?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.getMruTabInstances(callback: (tabInfo: TabInformation),tabInstanceParameters?: TabInstanceParameters)`|Recebe as guias mais usadas recentemente para o usuário. O retorno de chamada recupera o objeto **TabInformation.** O objeto **TabInstanceParameters** é um parâmetro opcional.|[função](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#getmrutabinstances--tabinfo--tabinformation-----void--tabinstanceparameters-&preserve-view=true)<br/>[tabInfo obj](/javascript/api/@microsoft/teams-js/tabinformation?view=msteams-client-js-latest&preserve-view=true)<br/>[tabInstance obj](/javascript/api/@microsoft/teams-js/tabinstanceparameters?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.shareDeepLink(deepLinkParameters: DeepLinkParameters)`|Pega o objeto **DeepLinkParameters** como entrada e compartilha uma caixa de diálogo de link profundo que um usuário pode usar para navegar até o conteúdo *dentro da guia*.|[função](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#sharedeeplink-deeplinkparameters-&preserve-view=true)<br/>[deepLink obj](/javascript/api/@microsoft/teams-js/deeplinkparameters?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.executeDeepLink(deepLink: string, onComplete?: (status: boolean, reason?: string))`|Toma um **deepLink** necessário como entrada e navega pelo usuário para uma URL ou aciona uma ação do cliente — como abrir ou instalar — um aplicativo *dentro de Teams.*|[função](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#executedeeplink-string---status--boolean--reason---string-----void-&preserve-view=true)|
|`microsoftTeams.navigateToTab(tabInstance: TabInstance, onComplete?: (status: boolean, reason?: string))`|Leva o objeto **TabInstance** como entrada e navega para uma instância de guia especificada.|[função](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#navigatetotab-tabinstance-&preserve-view=true)<br/>[tabInstance obj](/javascript/api/@microsoft/teams-js/tabinstance?view=msteams-client-js-latest&preserve-view=true)|

### <a name="authentication-namespace"></a>Espaço de nome de autenticação

| Função  | Descrição          | Documentação|
| -----     | -----     | -----    |
|`microsoftTeams.authentication.authenticate(authenticateParameters?: AuthenticateParameters)`|Inicia uma solicitação de autenticação que abre uma nova janela com os parâmetros fornecidos pelo chamador. Os valores de entrada opcionais são definidos pelo objeto **AuthenticateParameters.**|[função](/javascript/api/@microsoft/teams-js/authentication?view=msteams-client-js-latest&preserve-view=true)<br/>[auth obj](/javascript/api/@microsoft/teams-js/authenticateparameters?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.authentication.notifySuccess(result?: string, callbackUrl?: string)`|Notifica o quadro que iniciou a solicitação de autenticação de que a solicitação foi bem sucedida e fecha a janela de autenticação|[função](/javascript/api/@microsoft/teams-js/authentication?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.authentication.notifyFailure(reason?: string, callbackUrl?: string)`|Notifica o quadro que iniciou a solicitação de autenticação que a solicitação falhou e fecha a janela de autenticação.|[função](/javascript/api/@microsoft/teams-js/authentication?view=msteams-client-js-latest&preserve-view=true)|

### <a name="settings-namespace"></a>espaço de nome Configurações

| Função  | Descrição          | Documentação|
| -----     | -----     | -----    |
|`microsoftTeams.settings.setValidityState(validityState: boolean)`|O valor inicial é falso. Ativa o botão **Salvar** ou **Remover** quando o estado de validade for verdadeiro.|[função](/javascript/api/@microsoft/teams-js/settings?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.settings.getSettings(callback: (instanceSettings: Settings)`|Obtém as configurações para a instância atual. O retorno de chamada recupera o **objeto Configurações.**|[função](/javascript/api/@microsoft/teams-js/settings?view=msteams-client-js-latest&preserve-view=true)<br/>[configurações obj](/javascript/api/@microsoft/teams-js/_settings?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.settings.setSettings(instanceSettings: Settings, onComplete?: (status: boolean, reason?: string)`|Configura as configurações da instância atual. As configurações válidas são definidas pelo **objeto Configurações.**|[função](/javascript/api/@microsoft/teams-js/settings?view=msteams-client-js-latest&preserve-view=true)<br/>[configurações obj](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.settings.registerOnSaveHandler(handler: (evt: SaveEvent)`|O manipulador registrado quando o usuário seleciona o botão **Salvar.** Este manipulador deve ser usado para criar ou atualizar o recurso subjacente que alimenta o conteúdo.|[função](/javascript/api/@microsoft/teams-js/settings?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.settings.registerOnRemoveHandler(handler: (evt: RemoveEvent)`|O manipulador registrado quando o usuário seleciona o botão **Remover.** Este manipulador deve ser usado para remover o recurso subjacente que alimenta o conteúdo.|[função](/javascript/api/@microsoft/teams-js/settings?view=msteams-client-js-latest&preserve-view=true)|

### <a name="task-modules-namespace"></a>Espaço de nome dos módulos de tarefa

| Função  | Descrição          | Documentação|
| -----     | -----     | -----    |
|`microsoftTeams.tasks.startTask(taskInfo: TaskInfo, submitHandler?: (err: string, result: string)`|Toma o objeto **TaskInfo** como entrada e permite que um aplicativo abra o módulo de tarefas. O **envio opcionalHandler** é registrado quando o módulo de tarefa é concluído. |[função](/javascript/api/@microsoft/teams-js/tasks?view=msteams-client-js-latest&preserve-view=true)<br/>[tarefaInfo obj](/javascript/api/@microsoft/teams-js/taskinfo?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.tasks.submitTask(result?: string | object, appIds?: string | string[])`|Envia o módulo de tarefas. O parâmetro de sequência **de resultados** opcionais é o resultado enviado ao bot ou ao aplicativo e é tipicamente um objeto JSON ou serialização; O **parâmetro** de matriz de string ou string array opcional a ajuda a validar que a chamada se originou do mesmo appId que o que invocou o módulo de tarefa.|[função](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true)|
