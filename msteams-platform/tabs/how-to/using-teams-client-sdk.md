---
title: Usar o SDK do cliente do Teams
author: laujan
description: Como usar o SDK do teams Client para adicionar a funcionalidade de reconhecimento de equipes às suas guias personalizadas
keywords: guias do teams o canal de grupo do SDK do JavaScript pessoal
ms.topic: conceptual
ms.openlocfilehash: 07903d766ac67f2dbc9fc09268618ac5c2ae33c2
ms.sourcegitcommit: 1525db0515ab310a91939d85dbbfb7e887537849
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2020
ms.locfileid: "45091295"
---
# <a name="using-the-teams-client-sdk"></a>Usar o SDK do cliente do Teams

A **biblioteca JavaScript** do **cliente JavaScript do teams** e do Microsoft Teams é parte da [plataforma de desenvolvedor do Microsoft Teams](/microsoftteams/platform/) e oferece ferramentas e processos para facilitar a criação de aplicativos do teams. O SDK do teams Client é distribuído como um pacote do NPM. A versão mais recente pode ser encontrada aqui: <https://www.npmjs.com/package/@microsoft/teams-js> . A biblioteca do teams está localizada em <https://github.com/OfficeDev/microsoft-teams-library-js> .

A tabela a seguir descreve as funções da biblioteca do teams normalmente usadas no desenvolvimento de guias:

## <a name="teams-sdk-public-api"></a>API pública do teams SDK 

| Função  | Descrição          | Documentação|
| -----     | -----     | -----    | -----        |
| `microsoftTeams.initialize()` | Inicializa a biblioteca do teams. Essa função deve ser chamada antes de qualquer outra chamada de SDK.|[função](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#initialize-any-)|
|`microsoftTeams.getContext(callback: (context: Context)`| Obtém o estado atual no qual a página está sendo executada. O retorno de chamada recupera o objeto **Context** .|[função](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#getcontext--context--context-----void-)<br/>[obj de contexto](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest)|
| `microsoftTeams.initializeWithContext({contentUrl: string, websiteUrl: string})` | Inicializa a biblioteca do Teams e define o [contexto do quadro](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest) da guia, dependendo do contentUrl e do websiteUrl. Isso garante que a funcionalidade de ir para site/recarregar opere na URL correta.|[função](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#initializewithframecontext-framecontext--------void--string---)|
| `microsoftTeams.setFrameContext({contentUrl: string, websiteUrl: string})` | Define o contexto do [quadro](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest) da guia, dependendo do contentUrl e do websiteUrl. Isso garante que a funcionalidade de ir para site/recarregar opere na URL correta.|[função](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#setframecontext-framecontext-)|
| `microsoftTeams.registerFullScreenHandler(handler: (isFullScreen: boolean)` |O manipulador que é registrado quando o usuário alterna o modo de exibição de tela inteira de uma guia.|[função](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#registerfullscreenhandler--isfullscreen--boolean-----void-)<br/>[boolean](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest#isfullscreen)|
|`microsoftTeams.registerChangeSettingsHandler()` |O manipulador que é registrado quando o usuário seleciona o botão **configurações** habilitadas para reconfigurar uma guia.|[função](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#registerchangesettingshandler-------void-)|
| `microsoftTeams.getTabInstances(callback: (tabInfo: TabInformation),tabInstanceParameters?: TabInstanceParameters,)` |Obtém as guias pertencentes ao aplicativo. O retorno de chamada recupera o objeto **TabInformation** . O objeto **TabInstanceParameters** é um parâmetro opcional.|[função](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#gettabinstances--tabinfo--tabinformation-----void--tabinstanceparameters-)<br/>[tabInfo obj](/javascript/api/@microsoft/teams-js/microsoftteams.tabinformation?view=msteams-client-js-latest)|
|`microsoftTeams.getMruTabInstances(callback: (tabInfo: TabInformation),tabInstanceParameters?: TabInstanceParameters)`|Obtém as guias usadas mais recentemente para o usuário. O retorno de chamada recupera o objeto **TabInformation** . O objeto **TabInstanceParameters** é um parâmetro opcional.|[função](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#getmrutabinstances--tabinfo--tabinformation-----void--tabinstanceparameters-)<br/>[tabInfo obj](/javascript/api/@microsoft/teams-js/microsoftteams.teaminformation?view=msteams-client-js-latest)<br/>[tabInstance obj](/javascript/api/@microsoft/teams-js/microsoftteams.tabinstanceparameters?view=msteams-client-js-latest)|
|`microsoftTeams.shareDeepLink(deepLinkParameters: DeepLinkParameters)`|Pega o objeto **DeepLinkParameters** como entrada e compartilha uma caixa de diálogo de link profundo que um usuário pode usar para navegar até *o conteúdo na guia*.|[função](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#sharedeeplink-deeplinkparameters-)<br/>[obj do deepLink](/javascript/api/@microsoft/teams-js/microsoftteams.deeplinkparameters?view=msteams-client-js-latest)|
|`microsoftTeams.executeDeepLink(deepLink: string, onComplete?: (status: boolean, reason?: string))`|Usa um **deepLink** necessário como entrada e navega o usuário para uma URL ou dispara uma ação de cliente, como abrir ou instalar um aplicativo *no Microsoft Teams*.|[função](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#executedeeplink-string---status--boolean--reason---string-----void-)|
|`microsoftTeams.navigateToTab(tabInstance: TabInstance, onComplete?: (status: boolean, reason?: string))`|Pega o objeto **TabInstance** como entrada e navega para uma instância de tabulação especificada.|[função](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#navigatetotab-tabinstance-)<br/>[tabInstance obj](/javascript/api/@microsoft/teams-js/microsoftteams.tabinstance?view=msteams-client-js-latest)|

## <a name="authentication-namespace"></a>Namespace de autenticação

| Função  | Descrição          | Documentação|
| -----     | -----     | -----    | -----        |
|`microsoftTeams.authentication.authenticate(authenticateParameters?: AuthenticateParameters)`|Inicia uma solicitação de autenticação que abre uma nova janela com os parâmetros fornecidos pelo chamador. Os valores de entrada opcionais são definidos pelo objeto **authenticateparameters** .|[função](/javascript/api/@microsoft/teams-js/microsoftteams.authentication?view=msteams-client-js-latest#authenticate-authenticateparameters-)<br/>[obj de autenticação](/javascript/api/@microsoft/teams-js/microsoftteams.authentication.authenticateparameters?view=msteams-client-js-latest)|
|`microsoftTeams.authentication.notifySuccess(result?: string, callbackUrl?: string)`|Notifica o quadro que iniciou a solicitação de autenticação que a solicitação foi bem-sucedida e fecha a janela de autenticação|[função](/javascript/api/@microsoft/teams-js/microsoftteams.authentication?view=msteams-client-js-latest#notifysuccess-string--string-)|
|`microsoftTeams.authentication.notifyFailure(reason?: string, callbackUrl?: string)`|Notifica o quadro que iniciou a solicitação de autenticação que a solicitação falhou e fecha a janela de autenticação.|[função](/javascript/api/@microsoft/teams-js/microsoftteams.authentication?view=msteams-client-js-latest#notifyfailure-string--string-)|

## <a name="settings-namespace"></a>Namespace de configurações

| Função  | Descrição          | Documentação|
| -----     | -----     | -----    | -----        |
|`microsoftTeams.settings.setValidityState(validityState: boolean)`|O valor inicial é false. Ativa o botão **salvar** ou **remover** quando o estado de validade é true.|[função](/javascript/api/@microsoft/teams-js/microsoftteams.settings?view=msteams-client-js-latest#setvaliditystate-boolean-)|
|`microsoftTeams.settings.getSettings(callback: (instanceSettings: Settings)`|Obtém as configurações da instância atual. O retorno de chamada recupera o objeto **Settings** .|[função](/javascript/api/@microsoft/teams-js/microsoftteams.settings?view=msteams-client-js-latest#getsettings--instancesettings--settings-----void-)<br/>[configurações obj](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest)|
|`microsoftTeams.settings.setSettings(instanceSettings: Settings, onComplete?: (status: boolean, reason?: string)`|Configura as definições para a instância atual. As configurações válidas são definidas pelo objeto **Settings** .|[função](/javascript/api/@microsoft/teams-js/microsoftteams.settings?view=msteams-client-js-latest#setsettings-settings-)<br/>[configurações obj](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest)|
|`microsoftTeams.settings.registerOnSaveHandler(handler: (evt: SaveEvent)`|O manipulador que é registrado quando o usuário seleciona o botão **salvar** . Esse manipulador deve ser usado para criar ou atualizar o recurso subjacente que alimentará o conteúdo.|[função](/javascript/api/@microsoft/teams-js/microsoftteams.settings?view=msteams-client-js-latest#registeronsavehandler--evt--saveevent-----void-)|
|`microsoftTeams.settings.registerOnRemoveHandler(handler: (evt: RemoveEvent)`|O manipulador que é registrado quando o usuário seleciona o botão **remover** . Esse manipulador deve ser usado para remover o recurso subjacente que força o conteúdo.|[função](/javascript/api/@microsoft/teams-js/microsoftteams.settings?view=msteams-client-js-latest#registeronremovehandler--evt--removeevent-----void-)|

## <a name="tasks-namespace"></a>Namespace de tarefas

| Função  | Descrição          | Documentação|
| -----     | -----     | -----    | -----        |
|`microsoftTeams.tasks.startTask(taskInfo: TaskInfo, submitHandler?: (err: string, result: string)`|Obtém o objeto **TaskInfo** como entrada e permite que um aplicativo Abra o módulo de tarefa. O **submitHandler** opcional é registrado quando o módulo de tarefa é concluído. |[função](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#starttask-taskinfo---err--string--result--string-----void-)<br/>[taskInfo obj](/javascript/api/@microsoft/teams-js/microsoftteams.taskinfo?view=msteams-client-js-latest)|
|`microsoftTeams.tasks.submitTask(result?: string | object, appIds?: string | string[])`|Envia o módulo de tarefa. O parâmetro de cadeia de caracteres de **resultado** opcional é o resultado enviado para o bot ou o aplicativo e, em geral, é um objeto ou serialização JSON; A cadeia de caracteres **AppID** opcional ou o parâmetro de matriz de cadeia de caracteres ajuda a validar que a chamada originou da mesma AppID que o módulo de tarefa que o chamou.|[função](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---)|
