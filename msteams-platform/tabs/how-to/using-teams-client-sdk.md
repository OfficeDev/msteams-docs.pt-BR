---
title: Criando guias e outras experiências hospedadas com o SDK do cliente JavaScript do Microsoft Teams
author: heath-hamilton
ms.author: surbhigupta
description: Neste módulo, Conheça o SDK do cliente JavaScript do Microsoft Teams, que pode ajudar você a criar experiências de aplicativo hospedadas em um <iframe> no Teams, no Office e no Outlook.
ms.localizationpriority: high
ms.topic: conceptual
ms.openlocfilehash: 1909df76b3cc61f0d93e4efe40e02b99dc3de730
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66144212"
---
# <a name="building-tabs-and-other-hosted-experiences-with-the-microsoft-teams-javascript-client-sdk"></a>Criando guias e outras experiências hospedadas com o SDK do cliente JavaScript do Microsoft Teams

O SDK do cliente JavaScript do Microsoft Teams pode ajudá-lo a criar experiências hospedadas no Teams, no Office e no Outlook, onde o conteúdo do aplicativo está hospedado em um [iframe](https://developer.mozilla.org/docs/Web/HTML/Element/iframe). O SDK é útil para desenvolver aplicativos com qualquer um dos seguintes recursos do Teams:

* [Guias](../../tabs/what-are-tabs.md)
* [Diálogos (módulos de tarefa)](../../task-modules-and-cards/what-are-task-modules.md)

A partir da versão `2.0.0`, o SDK do cliente Teams existente (`@microsoft/teams-js`, ou simplesmente `TeamsJS`) foi reconfigurado para permitir que [aplicativos do Teams sejam executados no Outlook e no Office](/microsoftteams/platform/m365-apps/overview), além do Microsoft Teams. De uma perspectiva funcional, a versão mais recente do TeamsJS dá suporte a todas as funcionalidades existentes do aplicativo Teams (v.1.x.x) enquanto adiciona a capacidade opcional de hospedar aplicativos do Teams no Outlook e no Office.

Aqui estão as diretrizes de controle de versão atuais para vários cenários de aplicativo:

[!INCLUDE [pre-release-label](~/includes/teamjs-version-details.md)]

O restante deste artigo explicará a estrutura e as atualizações mais recentes do SDK do cliente JavaScript do Teams.

### <a name="microsoft-365-support-running-teams-apps-in-office-and-outlook"></a>Suporte do Microsoft 365 (executando aplicativos do Teams no Office e no Outlook)

O TeamsJS v.2.0 introduz a capacidade de determinados tipos de aplicativos do Teams serem executados em todo o ecossistema do Microsoft 365. Atualmente, outros hosts Microsoft 365 aplicativos (incluindo o Office e o Outlook) para aplicativos do Teams dão suporte a um subconjunto dos tipos de aplicativos e funcionalidades que você pode criar para a plataforma teams. Esse suporte se expandirá ao longo do tempo. Para obter um resumo do suporte de host para aplicativos do Teams, consulte [Estender aplicativos do Teams no Microsoft 365](../../m365-apps/overview.md).

A tabela a seguir lista as guias e os recursos de diálogos do Teams (módulos de tarefa) (namespaces públicos) com suporte expandido para execução em outros hosts do Microsoft 365.

> [!TIP]
> Você pode verificar o suporte de host de uma determinada funcionalidade em runtime chamando a função `isSupported()` nessa funcionalidade (namespace).

|Recursos | Suporte do host | Observações |
|-----------|--------------|-------|
| aplicativo | Teams, Outlook, Office | Namespace que representa a inicialização e o ciclo de vida do aplicativo. |
| appInitialization| | Depreciado. Substituído pelo namespace `app`. |
| appInstallDialog | Teams||
| autenticação | Teams, Outlook, Office | |
| calendar | Teams, Outlook ||
| call | Teams||
| chat |Teams||
| caixa de diálogo | Teams, Outlook, Office | Namespace que representa diálogos (anteriormente denominados *módulos de tarefas*. Consulte as anotações [Caixas de Diálogo](#dialogs). |
| localização |Teams| Consulte as anotações em [Permissões do aplicativo](#app-permissions).|
| email | Outlook (somente área de trabalho do Windows)||
| mídia |Teams| Consulte as anotações em [Permissões do aplicativo](#app-permissions).|
| páginas | Teams, Outlook, Office | Namespace que representa a navegação de página. Consulte as anotações em [Vinculação profunda](#deep-linking). |
| people |Teams||
| settings || Depreciado. Substituído por `pages.config`.|
| compartilhamento | Teams||
| tarefas | | Depreciado. Substituído pela funcionalidade `dialog`. Consulte as anotações em [Caixas de Diálogo](#dialogs).|
| teamsCore | Teams | Namespace que contém a funcionalidade específica do Teams.|
| video | Teams||

#### <a name="app-permissions"></a>Permissões de aplicativos

Os recursos do aplicativo que exigem que o usuário conceda [permissões de dispositivo](../../concepts/device-capabilities/device-capabilities-overview.md) (como *localização*) ainda não têm suporte para aplicativos em execução fora do Teams. No momento, não há como verificar as permissões do aplicativo em Configurações ou no cabeçalho do aplicativo ao executar no Outlook ou no Office. Se um aplicativo do Teams em execução no Office ou no Outlook chamar uma API teamsJS (ou HTML5) que dispare permissões de dispositivo, essa API gera um erro e não exibe uma caixa de diálogo do sistema solicitando o consentimento do usuário.

Por enquanto, as diretrizes atuais são modificar seu código para detectar a falha:

* Verifique [isSupported()](#differentiate-your-app-experience) em um recurso antes de usá-lo. `media`, `meeting` e `files` ainda não dão suporte a chamadas *isSupported* e ainda não funcionam fora do Teams.
* Capture e manipule erros ao chamar APIs TeamsJS e HTML5.

Quando uma API não tem suporte ou gera um erro, adiciona lógica para falhar normalmente ou fornece uma solução alternativa. Por exemplo:

* Direcione o usuário para o site do seu aplicativo.
* Direcione o usuário a usar o aplicativo no Teams para concluir o fluxo.
* Notifique o usuário de que a funcionalidade ainda não está disponível.

Além disso, a prática recomendada é garantir que o manifesto do aplicativo especifique apenas as permissões de dispositivo que ele está usando.

#### <a name="deep-linking"></a>Link profundo

Antes do TeamsJS versão 2.0, todos os cenários de vinculação profunda eram tratados usando o `shareDeepLink` (para gerar um link *para* uma parte específica do seu aplicativo) e `executeDeepLink` (para navegar até um deeplink *de* ou *dentro* do seu aplicativo). O TeamsJS v.2.0 apresenta uma nova API, `navigateToApp`, para navegar até páginas (e subpáginas) dentro de um aplicativo de maneira consistente entre hosts de aplicativos (Office e Outlook, além do Teams). Aqui estão as diretrizes atualizadas para cenários de vinculação profunda:

##### <a name="deep-links-into-your-app"></a>Links profundos para seu aplicativo

Use `pages.shareDeepLink` (conhecido como *shareDeepLink* antes do TeamsJS v.2.0) para gerar e exibir um link copiável para o usuário compartilhar. Quando clicado, um usuário será solicitado a instalar o aplicativo se ele ainda não estiver instalado para o host do aplicativo (especificado no caminho do link).

##### <a name="navigation-within-your-app"></a>Navegação em seu aplicativo

Use a nova API `pages.navigateToApp` para navegar em seu aplicativo dentro do aplicativo de hospedagem.

Essa API fornece o equivalente a navegar para um link profundo (da forma como o agora preterido *executeDeepLink* era usado antes) sem exigir que seu aplicativo construa uma URL ou gerencie diferentes formatos de link profundo para hosts de aplicativos diferentes.

##### <a name="deep-links-out-of-your-app"></a>Links profundos fora do seu aplicativo

Para links profundos do seu aplicativo para várias áreas do host atual, use as APIs fortemente tipadas fornecidas pelo SDK do TeamsJS. Por exemplo, use a funcionalidade *Calendário* para abrir uma caixa de diálogo de agendamento ou item de calendário do seu aplicativo.

Para links profundos do seu aplicativo para outros aplicativos em execução no mesmo host, use `pages.navigateToApp`.

Para qualquer outro cenário de vinculação profunda externa, você pode usar o `app.openLink`, que fornece funcionalidade semelhante à agora preterida (começando no TeamsJS v.2.0) API *executeDeepLink*.

#### <a name="dialogs"></a>Caixas de Diálogo

A partir da versão 2.0 do TeamsJS, o conceito de [módulo de tarefa](../../task-modules-and-cards/what-are-task-modules.md) da plataforma do Teams foi renomeado *Caixa de diálogo* para melhor consistência com os conceitos existentes em todo o ecossistema dos desenvolvedores do Microsoft 365. Da mesma forma, o namespace `tasks` foi preterido em favor do novo namespace `dialog`.

Essa nova funcionalidade de caixa de diálogo é dividida em um recurso principal (`dialog`) para dar suporte a diálogos baseados em HTML e uma subfuncionalidade, `dialog.bot`, para desenvolvimento de diálogo baseado em bot.

O recurso de caixa de diálogo ainda não dá suporte a [caixas de diálogo de cartão adaptável](../../task-modules-and-cards/task-modules/design-teams-task-modules.md). Os diálogos baseados em cartão adaptável ainda precisam ser invocados usando `tasks.startTask()`.

A função `dialog.open` atualmente só funciona para abrir caixas de diálogo baseadas em HTMl, e retorna uma função de retorno de chamada (`PostMessageChannel`) que você pode usar para passar mensagens (`ChildAppWindow.postMessage`) para a caixa de diálogo recém-aberta.  `dialog.open` retorna um retorno de chamada (em vez de uma Promessa) porque não requer que a execução do aplicativo pause aguardando o fechamento da caixa de diálogo (fornecendo assim mais flexibilidade para vários padrões de interação do usuário).

## <a name="whats-new-in-teamsjs-version-20"></a>Novidades no TeamsJS versão 2.0

Há duas alterações significativas entre as versões do TeamsJS 1.x.x e a v.2.0.0 e posterior:

* [**As funções de retorno de chamada agora retornam objetos Promise.**](#callbacks-converted-to-promises) Todas as funções existentes com um parâmetro de retorno de chamada no TeamsJS v.1.12 foram modernizada para retornar um objeto JavaScript [Promessa](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) para melhor manipulação de operações assíncronas e legibilidade de código.

* [**As APIs agora estão organizadas em *funcionalidades*.**](#apis-organized-into-capabilities) Você pode considerar os recursos como agrupamentos lógicos de APIs que fornecem funcionalidade semelhante, como `authentication`, `dialog`, `chat` e `calendar`. Cada namespace representa uma funcionalidade separada.

> [!TIP]
> Você pode usar a [extensão Kit de ferramentas do Teams](https://aka.ms/teams-toolkit) para Microsoft Visual Studio Code para simplificar o [TeamsJS v.2.0](#updating-to-the-teams-client-sdk-v200) para um aplicativo do Teams existente.

### <a name="backwards-compatibility"></a>Compatibilidade com versões anteriores

Depois de começar a referenciar `@microsoft/teams-js@2.0.0` (ou posterior) a partir de um aplicativo existente do Teams, você verá avisos de substituição para todas as APIs de chamada de código que foram alteradas.

Uma camada de tradução de API (mapeando o SDK v.1 para chamadas à API do SDK v.2) é fornecida para permitir que os aplicativos existentes do Teams continuem trabalhando no Teams até que eles possam atualizar o código do aplicativo para usar os padrões de API do TeamsJS v.2.

#### <a name="teams-only-apps"></a>Aplicativos apenas Teams

Mesmo que você pretenda que seu aplicativo seja executado apenas no Teams (e não no Office e no Outlook), a prática recomendada é começar a referenciar o TeamsJS mais recente (*v.2.0* ou posterior) assim que possível, para se beneficiar das melhorias mais recentes, novos recursos e suporte (até mesmo para aplicativos apenas Teams). O TeamsJS v.1.12 continuará a ter suporte, mas nenhum novo recurso ou melhoria será adicionado.

Quando você conseguir, a próxima etapa será [atualizar o código do aplicativo](#2-update-sdk-references) existente com as alterações descritas neste artigo. Enquanto isso, a camada de conversão de API v.1 a v.2 fornece compatibilidade com versões anteriores, garantindo que seu aplicativo do Teams existente continue funcionando no TeamsJS versão 2.0.

#### <a name="teams-apps-running-across-microsoft-365"></a>Aplicativos do Teams em execução no Microsoft 365

Habilitar um aplicativo do Teams existente para ser executado Outlook e Office requer o seguinte:

1. Dependência do TeamsJS versão 2.0 ( `@microsoft/teams-js@2.0`) ou posterior,

2. [Modificar o código do aplicativo existente](#2-update-sdk-references) de acordo com as alterações necessárias descritas neste documento.

3. [Atualizar o manifesto do aplicativo](#3-update-the-manifest-optional) para a versão 1.13 ou posterior.

Para obter mais informações, consulte [Estender aplicativos do Teams no Microsoft 365](../../m365-apps/overview.md).

### <a name="callbacks-converted-to-promises"></a>Retornos de chamada convertidos em promessas

As APIs do Teams que anteriormente levavam um parâmetro de retorno de chamada foram atualizadas para retornar um objeto JavaScript [Promessa](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise). Isso inclui as seguintes APIs:

```js
app.getContext, app.initialize, appInstallDialog.openAppInstallDialog, app.openLink, authentication.authenticate, authentication.getAuthToken, authentication.getUser, authentication.registerAuthenticationHandlers was removed to support using Promises, calendar.openCalendarItem, calendar.composeMeeting, call.startCall, chat.getChatMembers, conversations.openConversation, location.getLocation, location.showLocation, mail.openMailItem, mail.composeMail, pages.backStack.navigateBack, pages.navigateCrossDomain, pages.navigateToTab, pages.tabs.getMruTabInstances, pages.tabs.getTabInstances, pages.getConfig, pages.config.setConfig, pages.backStack.navigateBack, people.selectPeople, teams.fullTrust.getConfigSetting, teams.fullTrust.joinedTeams.getUserJoinedTeams
```

Você precisará atualizar a maneira como seu código chama qualquer uma dessas APIs para usar o Promises. Por exemplo, se o código estiver chamando uma API Teams como esta:

# <a name="javascript"></a>[JavaScript](#tab/javascript)

Este código:

```js
import microsoftTeams from "@microsoft/teams-js";

microsoftTeams.getContext((context) => { /* ... */ });
```

Precisa ser atualizado para:

```js
import { app, Context } from "@microsoft/teams-js";

app.getContext().then((context) => {
    /*...*/
});
```

... ou o padrão `async/await` equivalente:

```js
import { app, Context } from "@microsoft/teams-js";

async function example() {
  const context = await app.getContext();
  /*...*/
}
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

Este código:

```TypeScript
import * as microsoftTeams from "@microsoft/teams-js";

microsoftTeams.getContext((context: microsoftTeams.Context) => {
  /* ... */
});
```

Precisa ser atualizado para:

```TypeScript
import { app, Context } from "@microsoft/teams-js";

app.getContext().then((context: Context) => {
    /*...*/
});
```

... ou o padrão `async/await` equivalente:

```TypeScript
import { app, Context } from "@microsoft/teams-js";

async function example() {
  const context: Context = await app.getContext();
  /*...*/
}
```

---

> [!TIP]
> Quando você usa o [Kit de ferramentas do Teams para atualizar para o TeamsJS v.2.0](#updating-to-the-teams-client-sdk-v200), as atualizações necessárias são sinalizadas para você com `TODO` comentários no código do cliente.

### <a name="apis-organized-into-capabilities"></a>APIs organizadas em funcionalidades

Uma *funcionalidade é* um agrupamento lógico de APIs que fornecem funcionalidade semelhante. Você pode pensar no Microsoft Teams, no Outlook e no Office, como hosts do seu aplicativo de guia. Um host dá suporte a uma determinada funcionalidade se ele dá suporte a todas as APIs definidas dentro dessa funcionalidade. Um host não pode implementar parcialmente uma funcionalidade. Os recursos podem ser baseados em recursos ou conteúdo, como diálogo *autenticação* ou *caixa de diálogo*. Também há recursos para tipos de aplicativo, como *páginas* e outros agrupamentos.

Na Versão Prévia do SDK do TeamsJS v2.0, as APIs são definidas como funções em um namespace JavaScript cujo nome corresponde à funcionalidade necessária. Se um aplicativo estiver em execução em um host que dê suporte à funcionalidade *caixa de diálogo*, o aplicativo poderá chamar APIs com segurança, como `dialog.open` (além de outras APIs relacionadas à caixa de diálogo definidas no namespace). Se um aplicativo tentar chamar uma API que não tem suporte nesse host, a API gera uma exceção. Para verificar se o host atual que está executando seu aplicativo dá suporte a uma determinada funcionalidade, chame a função [isSupported()](#differentiate-your-app-experience) de seu namespace.

#### <a name="differentiate-your-app-experience"></a>Diferenciar sua experiência de aplicativo

Você pode verificar o suporte de host de uma determinada funcionalidade em runtime chamando a função `isSupported()` nessa funcionalidade (namespace). Ela retornará `true` se tiver suporte e `false`, caso contrário, e você poderá ajustar o comportamento do aplicativo conforme apropriado. Isso permite que seu aplicativo ilumine a interface do usuário e a funcionalidade em hosts que dão suporte a ele, enquanto continua a ser executado para hosts que não têm.

O nome do host no qual seu aplicativo está sendo executado é exposto como uma propriedade *hostName* na interface de contexto (`app.Context.app.host.name`), que pode ser consultada em runtime chamando `getContext`. Ele também está disponível como `{hostName}`[um valor de espaço reservado de URL](./access-teams-context.md#get-context-by-inserting-url-placeholder-values). A prática recomendada é usar o mecanismo *hostName* com moderação:

* **Não** suponha que determinada funcionalidade esteja ou não esteja disponível em um host com base no valor da propriedade *hostName*. Em vez disso, verifique se a funcionalidade tem suporte (`isSupported`).
* **Não** use *hostName* para enviar chamadas à API. Em vez disso, verifique se há suporte para funcionalidades (`isSupported`).
* **Use** *hostName* para diferenciar o tema do seu aplicativo com base no host em que ele está sendo executado. Por exemplo, você pode usar Microsoft Teams púrpura como a cor de destaque principal ao executar em Teams e Outlook azul ao executar em Outlook.
* **Use** *hostName* para diferenciar as mensagens mostradas para o usuário com base no host em que ele está sendo executado. Por exemplo, mostre *Gerenciar suas tarefas no Office* ao executar no Office na Web e *Gerenciar suas tarefas no Teams* ao executar no Microsoft Teams.

#### <a name="namespaces"></a>Namespaces

A partir do TeamsJS v.2.0, as APIs são organizadas em *funcionalidades* por meio de namespaces. Vários novos namespaces de importância específica são *aplicativo*, *páginas*, *caixa de diálogo* e *teamsCore*.

##### <a name="app-namespace"></a>*namespace* do aplicativo

O namespace `app` contém APIs de nível superior necessárias para o uso geral do aplicativo, entre Microsoft Teams, Office e Outlook. Todas as APIs de vários outros namespaces do TeamsJS foram movidas para o namespace `app` a partir do TeamsJS v2.0:

| Namespace original `global (window)` | Novo namespace `app` |
| - | - |
| `executeDeepLink` | `app.openLink` (renomeado) |
| `initialize` | `app.initialize` |
| `getContext` | `app.getContext` |
| `registerOnThemeChangeHandler` | `app.registerOnThemeChangeHandler` |

| Namespace original `appInitialization` | Novo namespace `app` |
| - | - |
| `appInitialization.notifyAppLoaded` | `app.notifyAppLoaded` |
| `appInitialization.notifySuccess` | `app.notifySuccess` |
| `appInitialization.notifyFailure` | `app.notifyFailure` |
| `appInitialization.notifyExpectedFailure` | `app.notifyExpectedFailure` |
| `appInitialization.FailedReason` enumeração | `app.FailedReason` |
| `appInitialization.ExpectedFailureReason` enumeração | `app.ExpectedFailureReason` |
| `appInitialization.IFailedRequest` enumeração | `app.IFailedRequest` |
| `appInitialization.IExpectedFailureRequest` enumeração | `app.IExpectedFailureRequest` |

##### <a name="pages-namespace"></a>*namespace* de páginas

O namespace `pages` inclui a funcionalidade para executar e navegar em páginas da Web em vários clientes do Microsoft 365, incluindo Teams, Office e Outlook. Ele também inclui vários sub-recursos, implementados como sub-namespaces.

| Namespace original `global (window)` | Novo namespace `pages` |
| - | - |
| `setFrameContext` | `pages.setCurrentFrame` (renomeado) |
| `initializeWithFrameContext` | `pages.initializeWithFrameContext` |
| `registerFocusEnterHandler` | `pages.registerFocusEnterHandler`
| `registerFullScreenHandler` | `pages.registerFullScreenHandler` |
| `navigateCrossDomain` | `pages.navigateCrossDomain` |
| `returnFocus` | `pages.returnFocus` |
| `shareDeepLink` | `pages.shareDeepLink` |

| Namespace original `settings` | Novo namespace `pages`  |
| - | - |
| `settings.getSettings` | `pages.getConfig` (renomeado)

###### <a name="pagestabs"></a>*pages.tabs*

| Namespace original `global (window)` | Novo namespace `pages.tabs` |
| - | - |
| `getTabInstances` |  `pages.tabs.getTabInstances` |
| `getMruTabInstances` | `pages.tabs.getMruTabInstances` |

| Namespace original `navigation` | Novo namespace `pages.tabs` |
| - | - |
| `navigation.navigateToTab` | `pages.tabs.navigateToTab` |

###### <a name="pagesconfig"></a>*pages.config*

| Namespace original `settings` | Novo namespace `pages.config`  |
| - | - |
| `settings.setSettings` | `pages.config.setConfig` (renomeado)
| `settings.setValidityState`| `pages.config.setValidityState`
| `settings.initialize` | `pages.config.initialize`
| `settings.registerOnSaveHandler`| `pages.config.registerOnSaveHandler`
| `settings.registerOnRemoveHandler` | `pages.config.registerOnRemoveHandler`
| `settings.Settings` interface | `pages.config.Config` (renomeado)
| `settings.SaveEvent` interface | `pages.config.SaveEvent` (renomeado)
| `settings.RemoveEvent` interface | `pages.config.RemoveEvent` (renomeado)
| `settings.SaveParameters` interface | `pages.config.SaveParameters` (renomeado)
| `settings.SaveEventImpl` interface | `pages.config.SaveEventImpl` (renomeado)

| Namespace original `global (window)` | Novo namespace `pages.config` |
| - | - |
| `registerChangeConfigHandler` | `pages.config.registerChangeConfigHandler` (renomeado)

###### <a name="pagesbackstack"></a>*pages.backStack*

| Namespace original `navigation` | Novo namespace `pages.backStack`  |
| - | - |
| `navigation.navigateBack` | `pages.backStack.navigateBack`

| Namespace original `global (window)` | Novo namespace `pages.backStack`  |
| - | - |
| `registerBackButtonHandler` | `pages.backStack.registerBackButtonHandler`

###### <a name="pagesappbutton"></a>*pages.appButton*

| Namespace original `global (window)` | Novo namespace `pages.appButton`  |
| - | - |
| `registerAppButtonClickHandler` | `pages.appButton.onClick` (renomeado)
| `registerAppButtonHoverEnterHandler` | `pages.appButton.onHoverEnter` (renomeado)
| `registerAppButtonHoverLeaveEnter` | `pages.appButton.onHoverLeave` (renomeado)
| `FrameContext` interface | `pages.appButton.FrameInfo` (renomeado)) |

##### <a name="dialog-namespace"></a>*namespace* da caixa de diálogo

O namespace de *tarefas* do TeamsJS foi renomeada para *caixa de diálogo* e as seguintes APIs foram renomeadas:

| Namespace original `tasks` | Novo namespace `dialog`  |
| - | - |
| `tasks.startTask` | `dialog.open` (renomeado) |
| `tasks.submitTasks` | `dialog.submit` (renomeado) |
| `tasks.updateTasks` | `dialog.update.resize` (renomeado) |
| `tasks.TaskModuleDimension` enumeração | `dialog.DialogDimension` (renomeado) |
| `tasks.TaskInfo` interface | `dialog.DialogInfo` (renomeado) |

Além disso, essa funcionalidade foi dividida em uma funcionalidade principal (`dialog`) para dar suporte a diálogos baseados em HTML e uma subfuncionalidade para diálogos baseados em bot, `dialog.bot`.

##### <a name="teamscore-namespace"></a>*namespace* do teamsCore

Para generalizar o SDK do TeamsJS para executar outros hosts do Microsoft 365, como Office e Outlook, a funcionalidade específica do Teams (originalmente no namespace *global*) foi movida para um namespace do *teamsCore*:

| Namespace original `global (window)` | Novo namespace `teamsCore`  |
| - | - |
| `enablePrintCapability` | `teamsCore.enablePrintCapability`
| `print` | `teamsCore.print`
| `registerOnLoadHandler` | `teamsCore.registerOnLoadHandler`
| `registerBeforeUnloadHandler` | `teamsCore.registerBeforeUnloadHandler`

#### <a name="updates-to-the-context-interface"></a>Atualizações para a interface de *Contexto*

A `Context` interface foi movida para o namespace `app` e atualizada para agrupar propriedades semelhantes para obter melhor escalabilidade à medida que é executada no Outlook e Office, além de Teams.

Uma nova propriedade `app.Context.app.host.name` foi adicionada para habilitar guias pessoais para diferenciar a experiência do usuário, dependendo do aplicativo host.

Você também pode visualizar as alterações examinando a função `transformLegacyContextToAppContext` na [origem do TeamsJS v2.0](https://github.com/OfficeDev/microsoft-teams-library-js/blob/main/packages/teams-js/src/public/app.ts) (arquivo *app.ts* file).

| Nome original na interface `Context` | Novo local em `app.Context` |
| - | - |
| `appIconPosition` | `app.Context.app.iconPositionVertical` |
| `appLaunchId`| *NÃO EXISTE NO TeamsJS v.2.0* |
| `appSessionId` | `app.Context.app.sessionId`|
| `channelId`| `app.Context.channel.id` |
| `channelName`| `app.Context.channel.displayName`|
| `channelRelativeUrl` | `app.Context.channel.relativeUrl`|
| `channelType`| `app.Context.channel.membershipType` |
| `chatId` | `app.Context.chat.id`|
| `defaultOneNoteSectionId`| `app.Context.channel.defaultOneNoteSectionId`|
| `entityId` | `app.Context.page.id`|
| `frameContext` | `app.Context.page.frameContext`|
| `groupId`| `app.Context.team.groupId` |
| `hostClientType` | `app.Context.app.host.clientType`|
| `hostTeamGroupId`| `app.Context.channel.ownerGroupId` |
| `hostTeamTenantId` | `app.Context.channel.ownerTenantId`|
| `isCallingAllowed` | `app.Context.user.isCallingAllowed`|
| `isFullScreen` | `app.Context.page.isFullScreen`|
| `isMultiWindow`| `app.Context.page.isMultiWindow` |
| `isPSTNCallingAllowed` | `app.Context.user.isPSTNCallingAllowed`|
| `isTeamArchived` | `app.Context.team.isArchived`|
| `locale` | `app.Context.app.locale` |
| `loginHint`| `app.Context.user.loginHint` |
| `meetingId`| `app.Context.meeting.id` |
| `osLocaleInfo` | `app.Context.app.osLocaleInfo` |
| `parentMessageId`| `app.Context.app.parentMessageId`|
| `ringId` | `app.Context.app.host.ringId`|
| `sessionId`| `app.Context.app.host.sessionId` |
| `sourceOrigin` | `app.Context.page.sourceOrigin`|
| `subEntityId`| `app.Context.page.subPageId` |
| `teamId` | `app.Context.team.internalId`|
| `teamSiteDomain` | `app.Context.sharepointSite.domain`|
| `teamSitePath` | `app.Context.sharepointSite.path`|
| `teamSiteUrl`| `app.Context.sharepointSite.url` |
| `teamTemplateId` | `app.Context.team.templateId`|
| `teamType` | `app.Context.team.type`|
| `tenantSKU`| `app.Context.user.tenant.teamsSku` |
| `tid`| `app.Context.user.tenant.id` |
| `upn` | `app.Context.user.userPrincipalName` |
|`userClickTime`| `app.Context.app.userClickTime`|
| `userFileOpenPreference` | `app.Context.app.userFileOpenPreference` |
| `userLicenseType`| `app.Context.user.licenseType` |
| `userObjectId` | `app.Context.user.id`|
| `userTeamRole` | `app.Context.team.userRole`|
| `userDisplayName` | `app.Context.user.displayName` |
| N/D | `app.Context.app.host.name`|

## <a name="updating-to-the-teams-client-sdk-v200"></a>Como atualizar para a versão prévia do SDK do cliente do Teams v2.0.0

A maneira mais fácil de atualizar seu Teams para usar a versão prévia do SDK do TeamsJS v2.0 é usar a [ extensão Kit de ferramentas do Teams](https://aka.ms/teams-toolkit) para Visual Studio Code. Esta seção orientará você pelas etapas para fazer isso. Se você preferir atualizar manualmente seu código, consulte os [Retornos de Chamada convertidos em promessas](#callbacks-converted-to-promises) e [APIs organizadas em seções de funcionalidades](#apis-organized-into-capabilities) para obter mais detalhes sobre as alterações de API necessárias.

### <a name="1-install-the-latest-teams-toolkit-visual-studio-code-extension"></a>1. Instale a extensão mais recente do kit de ferramentas do Teams Visual Studio Code

No *Marketplace de Extensões do Visual Studio Code, pesquise* por **kit de ferramentas do Teams** e instale a versão `2.10.0` ou posterior.

### <a name="2-update-sdk-references"></a>2. Atualizar referências do SDK

Para ser executado Outlook e Office, seu aplicativo precisará depender do [pacote npm](https://www.npmjs.com/package/@microsoft/teams-js/v/2.0.0) `@microsoft/teams-js@2.0.0` (ou posterior). Para executar essas etapas manualmente e para obter mais informações sobre as alterações de API, consulte as seções a seguir sobre [retornos de chamada convertidos em promessas](#callbacks-converted-to-promises) e [APIs organizadas em funcionalidades](#apis-organized-into-capabilities).

1. Verifique se você tem [kit de ferramentas do Teams](https://aka.ms/teams-toolkit) `v.2.10.0` ou posterior
1. Abra a *paleta de comandos*: `Ctrl+Shift+P`
1. Execute o comando `Teams: Upgrade Teams JS SDK references to support Outlook and Office apps`.

Após a conclusão, o utilitário terá atualizado seu arquivo `package.json` com a dependência do TeamsJS SDK v2.0 (`@microsoft/teams-js@2.0.0` ou posterior), e seus arquivos `*.js/.ts` e `*.jsx/.tsx` serão atualizados com:

> [!div class="checklist"]
>
> * `package.json` referências ao TeamsJS v.2.0
> * Instruções de importação para TeamsJS v.2.0
> * [Função, enumeração e chamadas de interface](#apis-organized-into-capabilities) para o TeamsJS v.2.0
> * `TODO` lembretes de comentário para examinar áreas que podem ser afetadas por [alterações de contexto ](#updates-to-the-context-interface)
> * `TODO` lembretes de comentário para [converter funções de retorno de chamada em promessas](#callbacks-converted-to-promises)

> [!IMPORTANT]
> O código dentro de arquivos html não é suportado pelas ferramentas de atualização e exigirá alterações manuais.

### <a name="3-update-the-manifest-optional"></a>3. Atualizar o manifesto (opcional)

Se você estiver atualizando um aplicativo do Teams para ser executado no Office e no Outlook, também precisará atualizar o manifesto do aplicativo para a versão 1.13 ou posterior. Você pode fazer isso facilmente com o Kit de ferramentas do Teams ou manualmente.

# <a name="teams-toolkit"></a>[Kit de ferramentas do Teams](#tab/manifest-teams-toolkit)

1. Abra a *paleta de comandos*: `Ctrl+Shift+P`
1. Execute o comando **Teams: atualizar o manifesto do Teams para dar suporte a aplicativos do Outlook e do Office** e selecione o arquivo de manifesto do aplicativo. As alterações serão feitas no local.

# <a name="manual-steps"></a>[Etapas manuais](#tab/manifest-manual)

Abra o Teams manifesto do aplicativo e atualize o `$schema` e `manifestVersion` com os seguintes valores:

```json
{
    "$schema" : "https://developer.microsoft.com/json-schemas/teams/v1.13/MicrosoftTeams.schema.json",
    "manifestVersion" : "1.13"
}
```

---

Se você usou o kit de ferramentas do Teams para criar seu aplicativo pessoal, também poderá usá-lo para validar as alterações no arquivo de manifesto e identificar erros. Abra a paleta de comandos `Ctrl+Shift+P` e localize o **Teams: valide o arquivo de manifesto** ou selecione a opção no menu Implantação do Kit de Ferramentas do Teams (procure o ícone do Teams no lado esquerdo do Visual Studio Code).

:::image type="content" source="../../m365-apps/images/toolkit-validate-manifest-file.png" alt-text="Opção &quot;Validar arquivo de manifesto&quot; do Kit de Ferramentas do Teams no menu &quot;Implantação&quot;":::

## <a name="next-steps"></a>Próximas etapas

* Use a [referência do TeamsJS](/javascript/api/overview/msteams-client) para começar a usar o SDK do cliente JavaScript do Microsoft Teams.
* Examine o [log de alterações](https://github.com/OfficeDev/microsoft-teams-library-js/blob/main/packages/teams-js/CHANGELOG.md) para obter as atualizações mais recentes do TeamsJS.
