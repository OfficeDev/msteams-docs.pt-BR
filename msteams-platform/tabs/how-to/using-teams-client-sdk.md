---
title: Criando guias e outras experiências hospedadas com o SDK do cliente JavaScript
author: heath-hamilton
ms.author: surbhigupta
description: Visão geral do SDK do cliente JavaScript do Microsoft Teams, que pode ajudá-lo a criar experiências de aplicativo do Teams hospedadas em um <iframe>.
localization_priority: Normal
keywords: teams tabs group channel configurble static SDK JavaScript personal
ms.topic: conceptual
ms.openlocfilehash: c3bbdf9b71618148faf9822aaf051b85aecf17fb
ms.sourcegitcommit: 303fc214aa04757779a171337f31a6539f47fd03
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2021
ms.locfileid: "52068721"
---
# <a name="building-tabs-and-other-hosted-experiences-with-the-microsoft-teams-javascript-client-sdk"></a>Criando guias e outras experiências hospedadas com o SDK do cliente JavaScript do Microsoft Teams

O SDK do cliente JavaScript do Microsoft Teams pode ajudá-lo a criar experiências hospedadas no Teams, o que significa exibir o conteúdo do aplicativo em um iframe.

O SDK é útil para desenvolver aplicativos com qualquer um dos seguintes recursos do Teams:

* [Guias](../../tabs/what-are-tabs.md)
* [Módulos de tarefas](../../task-modules-and-cards/what-are-task-modules.md)

Por exemplo, o SDK pode fazer sua [guia reagir](../../build-your-first-app/build-personal-tab.md) às alterações de tema que seus usuários fazem no cliente do Teams.

## <a name="getting-started"></a>Introdução

Faça uma das seguintes coisas dependendo de suas preferências de desenvolvimento:


* [Instalar o SDK com npm ou Yarn](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)

## <a name="common-sdk-functions"></a>Funções SDK comuns


Consulte as tabelas a seguir para entender as funções SDK comumente usadas. A documentação de referência do [SDK](/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true) fornece informações mais abrangentes.


### <a name="basic-functions"></a>Funções básicas

| Função  | Descrição          | Documentação|
| -----     | -----     | -----    |
| `microsoftTeams.initialize()` | Inicializa o SDK. Essa função deve ser chamada antes de qualquer outra chamada SDK.|[função](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#initialize-any-&preserve-view=true)|
|`microsoftTeams.getContext(callback: (context: Context)`| Obtém o estado atual no qual a página está sendo executado. O retorno de chamada recupera o **objeto Context.**|[função](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#getcontext--context--context-----void-&preserve-view=true)<br/>[context obj](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true)|
| `microsoftTeams.initializeWithContext({contentUrl: string, websiteUrl: string})` | Inicializa a biblioteca do Teams e define o contexto de quadro da [guia,](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true) dependendo do contentUrl e do siteUrl. Isso garante que a funcionalidade go-to-site/reload opere na URL correta.|[função](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#initializewithframecontext-framecontext--------void--string---&preserve-view=true)|
| `microsoftTeams.setFrameContext({contentUrl: string, websiteUrl: string})` | Define o contexto de quadro da [guia,](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true) dependendo do contentUrl e do siteUrl. Isso garante que a funcionalidade go-to-site/reload opere na URL correta.|[função](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#setframecontext-framecontext-&preserve-view=true)|
| `microsoftTeams.registerFullScreenHandler(handler: (isFullScreen: boolean)` |O manipulador que é registrado quando o usuário alterna o exibição de tela inteira/janela de uma guia.|[função](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#registerfullscreenhandler--isfullscreen--boolean-----void-&preserve-view=true)<br/>[boolean](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#registerFullScreenHandler__isFullScreen__boolean_____void_&preserve-view=true)|
|`microsoftTeams.registerChangeSettingsHandler()` |O manipulador que é registrado quando o usuário seleciona o botão **Configurações** habilitadas para reconfigurar uma guia.|[função](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#registerchangesettingshandler-------void-&preserve-view=true)|
| `microsoftTeams.getTabInstances(callback: (tabInfo: TabInformation),tabInstanceParameters?: TabInstanceParameters,)` |Obtém as guias pertencentes ao aplicativo. O retorno de chamada recupera o **objeto TabInformation.** O **objeto TabInstanceParameters** é um parâmetro opcional.|[função](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#gettabinstances--tabinfo--tabinformation-----void--tabinstanceparameters-&preserve-view=true)<br/>[tabInfo obj](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/tabinformation?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.getMruTabInstances(callback: (tabInfo: TabInformation),tabInstanceParameters?: TabInstanceParameters)`|Obtém as guias usadas mais recentemente para o usuário. O retorno de chamada recupera o **objeto TabInformation.** O **objeto TabInstanceParameters** é um parâmetro opcional.|[função](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#getmrutabinstances--tabinfo--tabinformation-----void--tabinstanceparameters-&preserve-view=true)<br/>[tabInfo obj](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/tabinformation?view=msteams-client-js-latest&preserve-view=true)<br/>[tabInstance obj](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/tabinstanceparameters?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.shareDeepLink(deepLinkParameters: DeepLinkParameters)`|Usa o **objeto DeepLinkParameters** como entrada e compartilha uma caixa de diálogo de link profundo que um usuário pode usar para navegar até o conteúdo *na guia*.|[função](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#sharedeeplink-deeplinkparameters-&preserve-view=true)<br/>[deepLink obj](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/deeplinkparameters?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.executeDeepLink(deepLink: string, onComplete?: (status: boolean, reason?: string))`|Assume um **deepLink** necessário como entrada e navega o usuário para uma URL ou dispara uma ação do cliente, como abrir ou instalar, um aplicativo *no Teams*.|[função](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#executedeeplink-string---status--boolean--reason---string-----void-&preserve-view=true)|
|`microsoftTeams.navigateToTab(tabInstance: TabInstance, onComplete?: (status: boolean, reason?: string))`|Assume o **objeto TabInstance** como entrada e navega até uma instância de guia especificada.|[função](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#navigatetotab-tabinstance-&preserve-view=true)<br/>[tabInstance obj](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/tabinstance?view=msteams-client-js-latest&preserve-view=true)|

### <a name="authentication-namespace"></a>Namespace de autenticação

| Função  | Descrição          | Documentação|
| -----     | -----     | -----    |
|`microsoftTeams.authentication.authenticate(authenticateParameters?: AuthenticateParameters)`|Inicia uma solicitação de autenticação que abre uma nova janela com os parâmetros fornecidos pelo chamador. Os valores de entrada opcionais são definidos pelo **objeto AuthenticateParameters.**|[função](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/authentication?view=msteams-client-js-latest&preserve-view=true)<br/>[auth obj](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/authenticateparameters?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.authentication.notifySuccess(result?: string, callbackUrl?: string)`|Notifica o quadro que iniciou a solicitação de autenticação de que a solicitação foi bem-sucedida e fecha a janela de autenticação|[função](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/authentication?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.authentication.notifyFailure(reason?: string, callbackUrl?: string)`|Notifica o quadro que iniciou a solicitação de autenticação que a solicitação falhou e fecha a janela de autenticação.|[função](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/authentication?view=msteams-client-js-latest&preserve-view=true)|

### <a name="settings-namespace"></a>Namespace de configurações

| Função  | Descrição          | Documentação|
| -----     | -----     | -----    |
|`microsoftTeams.settings.setValidityState(validityState: boolean)`|O valor inicial é false. Ativa o **botão Salvar** ou **Remover** quando o estado de validade for true.|[função](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/settings?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.settings.getSettings(callback: (instanceSettings: Settings)`|Obtém as configurações da instância atual. O retorno de chamada recupera o **objeto Settings.**|[função](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/settings?view=msteams-client-js-latest&preserve-view=true)<br/>[settings obj](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/_settings?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.settings.setSettings(instanceSettings: Settings, onComplete?: (status: boolean, reason?: string)`|Configura as configurações da instância atual. As configurações válidas são **definidas pelo objeto Settings.**|[função](/https://docs.microsoft.com/en-us/javascript/api/@microsoft/teams-js/settings?view=msteams-client-js-latest)<br/>[settings obj](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.settings.registerOnSaveHandler(handler: (evt: SaveEvent)`|O manipulador que é registrado quando o usuário seleciona o **botão Salvar.** Esse manipulador deve ser usado para criar ou atualizar o recurso subjacente que powering o conteúdo.|[função](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/settings?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.settings.registerOnRemoveHandler(handler: (evt: RemoveEvent)`|O manipulador que é registrado quando o usuário seleciona o **botão Remover.** Esse manipulador deve ser usado para remover o recurso subjacente que a energia do conteúdo.|[função](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/settings?view=msteams-client-js-latest&preserve-view=true)|

### <a name="task-modules-namespace"></a>Namespace de módulos de tarefa

| Função  | Descrição          | Documentação|
| -----     | -----     | -----    |
|`microsoftTeams.tasks.startTask(taskInfo: TaskInfo, submitHandler?: (err: string, result: string)`|Assume o **objeto TaskInfo** como entrada e permite que um aplicativo abra o módulo de tarefa. O **submitHandler opcional** é registrado quando o módulo de tarefa é concluído. |[função](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/tasks?view=msteams-client-js-latest&preserve-view=true)<br/>[taskInfo obj](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/taskinfo?view=msteams-client-js-latest&preserve-view=true)|
|`microsoftTeams.tasks.submitTask(result?: string | object, appIds?: string | string[])`|Envia o módulo de tarefa. O parâmetro **de cadeia** de caracteres de resultado opcional é o resultado enviado para o bot ou para o aplicativo e normalmente é um objeto JSON ou serialização; O parâmetro appIds opcional de cadeia de caracteres ou matriz de cadeia de caracteres ajuda na validação de que a chamada se originou da mesma **appId** que a que invocou o módulo de tarefa.|[função](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true)|
