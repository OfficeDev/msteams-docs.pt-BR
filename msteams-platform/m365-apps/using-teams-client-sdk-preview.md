---
title: Versão prévia do SDK do cliente JavaScript do Microsoft Teams v2
description: Entender as alterações que virão com a versão prévia do SDK do cliente JavaScript do Microsoft Teams v2
ms.date: 11/15/2021
ms.topic: conceptual
ms.custom: m365apps
ms.localizationpriority: high
ms.openlocfilehash: 91f012821efacd0f0ff6032703d0520d5bd469e0
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111693"
---
# <a name="microsoft-teams-javascript-client-sdk-v2-preview"></a>Versão prévia do SDK do cliente JavaScript do Microsoft Teams v2

Com a versão prévia do [SDK do cliente JavaScript v2 do Microsoft Teams](/javascript/api/overview/msteams-client?view=msteams-client-js-beta&preserve-view=true), o SDK do Teams existente (`@microsoft/teams-js``TeamsJS`ou simplesmente) foi refatorado para permitir aos desenvolvedores do Teams a capacidade de [estender os aplicativos do Teams para execução no Outlook e Office](overview.md). De uma perspectiva funcional, o SDK do TeamsJS v2 Preview (`@microsoft/teams-js@next`) é um superconjunto do SDK atual do TeamsJS, ele dá suporte à funcionalidade de aplicativo Teams existente ao adicionar a capacidade de hospedar aplicativos Teams no Outlook e Office.

Há duas alterações significativas na Versão Prévia do SDK do TeamsJS v2 que seu código precisará levar em conta para ser executado em outros aplicativos Microsoft 365:

* [**As funções de retorno de chamada agora retornam objetos Promise.**](#callbacks-converted-to-promises) Todas as funções existentes com um parâmetro de retorno de chamada foram modernizada para retornar um objeto JavaScript [Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) para melhor manipulação de operações assíncronas e legibilidade de código.

* [**As APIs agora estão organizadas em *funcionalidades*.**](#apis-organized-into-capabilities) Você pode considerar os recursos como agrupamentos lógicos de APIs que fornecem funcionalidade semelhante, como `authentication`, `calendar`, `mail`, `monetization`, `meeting`e `sharing`.

 Você pode usar a [extensão do kit de ferramentas do Teams](https://aka.ms/teams-toolkit) para Microsoft Visual Studio Code para simplificar o processo de atualização para seu aplicativo Teams, conforme descrito na seção a seguir.

> [!NOTE]
> Habilitar um aplicativo Teams existente para ser executado Outlook e Office requer ambos:
>
> 1. Dependência no ou `@microsoft/teams-js@2.0.0-beta.1` posterior e
> 2. Modificar o código do aplicativo existente de acordo com as alterações necessárias descritas neste documento.
>
> Se você referenciar `@microsoft/teams-js@2.0.0-beta.1` (ou posterior) de um aplicativo Teams existente, verá avisos de substituição se o código chamar APIs que foram alteradas. Uma camada de conversão de API (mapeamento do SDK atual para visualizar chamadas à API do SDK) é fornecida para permitir que os aplicativos Teams existentes continuem trabalhando no Teams até que eles possam atualizar o código para trabalhar com a versão prévia do SDK do TeamsJS v2. Depois de atualizar o código com as alterações descritas neste artigo, sua guia pessoal também será executada no Outlook e Office.

## <a name="updating-to-the-teams-client-sdk-v2-preview"></a>Atualizando para a versão prévia do SDK do cliente do Teams v2

A maneira mais fácil de atualizar seu Teams para usar a versão prévia do SDK do TeamsJS v2 é usar a [ extensão do kit de ferramentas do Teams](https://aka.ms/teams-toolkit) para Visual Studio Code. Esta seção orientará você pelas etapas para fazer isso. Se você preferir atualizar manualmente seu código, consulte os [Retornos de Chamada convertidos em promessas](#callbacks-converted-to-promises) e [APIs organizadas em seções de funcionalidades](#apis-organized-into-capabilities) para obter mais detalhes sobre as alterações de API necessárias.

### <a name="1-install-the-latest-teams-toolkit-visual-studio-code-extension"></a>1. Instale a extensão mais recente do kit de ferramentas do Teams Visual Studio Code

No *Marketplace de Extensões do Visual Studio Code, pesquise* por **kit de ferramentas do Teams** e instale a versão `2.10.0` ou posterior. O kit de ferramentas fornece dois comandos para auxiliar o processo:

1. Um comando para atualizar o esquema de manifesto
1. Um comando para atualizar suas referências do SDK e sites de chamada

A seguir estão as duas principais atualizações que você precisará para executar um aplicativo Teams guia pessoal em outros aplicativos do Microsoft 365: ''

### <a name="2-updating-the-manifest"></a>2. Atualizando o manifesto

# <a name="teams-toolkit"></a>[Kit de ferramentas do Teams](#tab/manifest-teams-toolkit)

1. Abra a *paleta de comandos*: `Ctrl+Shift+P`
1. Execute **Teams: atualize o manifesto do Teams para dar suporte ao aplicativos Outlook e Office** e selecione o arquivo de manifesto do aplicativo. As alterações serão feitas no local.

# <a name="manual-steps"></a>[Etapas manuais](#tab/manifest-manual)

Abra o Teams manifesto do aplicativo e atualize o `$schema` e `manifestVersion` com os seguintes valores:

```json
{
    "$schema" : "https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json",
    "manifestVersion" : "m365DevPreview"
}
```

---

Se você usou o kit de ferramentas do Teams para criar seu aplicativo pessoal, também poderá usá-lo para validar as alterações no arquivo de manifesto e identificar erros. Abra a paleta de comandos `Ctrl+Shift+P` e localize o **Teams: valide o arquivo de manifesto** ou selecione a opção no menu Implantação do Kit de Ferramentas do Teams (procure o ícone do Teams no lado esquerdo do Visual Studio Code).

:::image type="content" source="images/toolkit-validate-manifest-file.png" alt-text="Opção &quot;Validar arquivo de manifesto&quot; do Kit de Ferramentas do Teams no menu &quot;Implantação&quot;":::

### <a name="2-update-sdk-references"></a>2. Atualizar referências do SDK

Para ser executado Outlook e Office, seu aplicativo precisará depender do [pacote npm](https://www.npmjs.com/package/@microsoft/teams-js/v/2.0.0-beta.1) `@microsoft/teams-js@2.0.0-beta.1` (ou de uma versão *beta* posterior). Para executar essas etapas manualmente e para obter mais informações sobre as alterações de API, consulte as seções a seguir sobre [retornos de chamada convertidos em promessas](#callbacks-converted-to-promises) e [APIs organizadas em funcionalidades](#apis-organized-into-capabilities).

1. Verifique se você tem [kit de ferramentas do Teams](https://aka.ms/teams-toolkit) `v2.10.0` ou posterior
1. Abra a *paleta de comandos*: `Ctrl+Shift+P`
1. Execute o comando `Teams: Upgrade Teams JS SDK references to support Outlook and Office apps`.

Após a conclusão, o utilitário terá atualizado seu arquivo `package.json` com a dependência do TeamsJS SDK v2 Preview (`@microsoft/teams-js@2.0.0-beta.1` ou posterior), e seus arquivos `*.js/.ts` e `*.jsx/.tsx` serão atualizados com:

> [!div class="checklist"]
>
> * `package.json` referências ao SDK do TeamsJS v2 Preview
> * Instruções de importação para a versão prévia do SDK do TeamsJS v2
> * [Chamadas de função, enumeração e interface](#apis-organized-into-capabilities) para a versão prévia do SDK do TeamsJS v2
> * `TODO` lembretes de comentário para examinar áreas que podem ser afetadas por [alterações de contexto ](#updates-to-the-context-interface)
> * `TODO` lembretes de comentário para garantir que a [conversão em funções de promessas](#callbacks-converted-to-promises) de funções de estilo de retorno de chamada tenha ido bem em cada site de chamada que a ferramenta encontrou

> [!IMPORTANT]
> O código dentro de arquivos html não é suportado pelas ferramentas de atualização e exigirá alterações manuais.

## <a name="callbacks-converted-to-promises"></a>Retornos de chamada convertidos em promessas

APIs do Teams que anteriormente levavam um parâmetro de retorno de chamada foram atualizadas para retornar um objeto JavaScript [Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise). Elas incluem as seguintes APIs:

```js
app.getContext, app.initialize, appInstallDialog.openAppInstallDialog, authentication.authenticate, authentication.getAuthToken, authentication.getUser, authentication.registerAuthenticationHandlers was removed to support using Promises, calendar.openCalendarItem, calendar.composeMeeting, call.startCall, core.executeDeepLink, location.getLocation, location.showLocation, mail.openMailItem, mail.composeMail, media.captureImage, media.getMedia, media.selectMedia, media.viewImages, media.scanBarCode, meeting.getAppContentStageSharingCapabilities, meeting.getAuthenticationTokenForAnonymousUser, meeting.getIncomingClientAudioState, meeting.getLiveStreamState, meeting.getMeetingDetails, meeting.requestStartLiveStreaming, meeting.requestStopLiveStreaming, meeting.shareAppContentToStage, meeting.stopSharingAppContentToStage, meeting.toggleIncomingClientAudio, meeting.getAppContentStageSharingState, pages.backStack.navigateBack, pages.navigateCrossDomain, pages.navigateToTab, pages.tabs.getMruTabInstances, pages.tabs.getTabInstances, pages.config.setConfig, pages.config.getConfig, people.selectPeople, ChildAppWindow.postMessage, ParentAppWindow.postMessage
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
> Quando você atualiza seu código para a Versão Prévia do SDK do TeamsJS v2 usando o [kit de ferramentas do Teams](#updating-to-the-teams-client-sdk-v2-preview), `TODO` as atualizações necessárias são sinalizadas para você com comentários no código do cliente.

## <a name="apis-organized-into-capabilities"></a>APIs organizadas em funcionalidades

Uma *funcionalidade é* um agrupamento lógico de APIs que fornecem funcionalidade semelhante. Você pode pensar em Microsoft Teams, Outlook e Office, como hosts. Um host dá suporte a uma determinada funcionalidade se ele dá suporte a todas as APIs definidas dentro dessa funcionalidade. Um host não pode implementar parcialmente uma funcionalidade.  Os recursos podem ser baseados em recursos ou conteúdo, como diálogo *ou* *autenticação*. Também há recursos para tipos de aplicativo, como *guias/páginas* ou *bots* e outros agrupamentos.

Na Versão Prévia do SDK do TeamsJS v2, as APIs são definidas como funções em um namespace JavaScript cujo nome corresponde à funcionalidade necessária. Se um aplicativo estiver em execução em um host que dê suporte à funcionalidade de caixa de diálogo, o aplicativo poderá chamar APIs com segurança, como `dialog.open` (além de outras APIs relacionadas à caixa de diálogo definidas no namespace). Enquanto isso, se um aplicativo tentar chamar uma API que não tem suporte nesse host, a API gerará uma exceção.

### <a name="differentiate-your-app-experience"></a>Diferenciar sua experiência de aplicativo

Você pode verificar o suporte de host de uma determinada funcionalidade em runtime chamando a função `isSupported()` nessa funcionalidade (namespace). Ele retornará `true` se tiver suporte e `false`, caso contrário, e você poderá ajustar o comportamento do aplicativo conforme apropriado. Isso permite que seu aplicativo ilumine a interface do usuário e a funcionalidade em hosts que dão suporte a ele, enquanto continua a ser executado para hosts que não têm.

O nome do host no qual seu aplicativo está sendo executado é exposto como uma propriedade *hostName* na interface de contexto (`app.Context.app.host.name`), que pode ser consultada em runtime chamando `getContext`. Ele também está disponível como um valor de `{hostName}`[espaço reservado de URL](../tabs/how-to/access-teams-context.md#get-context-by-inserting-url-placeholder-values). A prática recomendada é usar o mecanismo *hostName* com moderação:

* **Não** suponha que determinada funcionalidade esteja ou não esteja disponível em um host com base no valor da propriedade *hostName*. Em vez disso, verifique se há suporte para funcionalidades (`isSupported`).
* **Não** use *hostName* para enviar chamadas à API. Em vez disso, verifique se há suporte para funcionalidades (`isSupported`).
* **Use** *hostName* para diferenciar o tema do seu aplicativo com base no host em que ele está sendo executado. Por exemplo, você pode usar Microsoft Teams púrpura como a cor de destaque principal ao executar em Teams e Outlook azul ao executar em Outlook.
* **Use** *hostName* para diferenciar as mensagens mostradas para o usuário com base no host em que ele está sendo executado. Por exemplo, mostre *Gerenciar suas tarefas no Office* ao executar no Office na Web e *Gerenciar suas tarefas no Teams* ao executar no Microsoft Teams.

### <a name="namespaces"></a>Namespaces

A Versão Prévia do SDK do TeamsJS v2 organiza APIs em *funcionalidades* por meio de namespaces. Vários novos namespaces de importância específica são *aplicativo*, *páginas*, *caixa de diálogo* e *teamsCore*.

#### <a name="app-namespace"></a>*namespace* do aplicativo

O namespace `app` contém APIs de nível superior necessárias para o uso geral do aplicativo, entre Microsoft Teams, Office e Outlook. Todas as APIs de vários outros namespaces do TeamsJS foram movidas para o namespace `app` no SDK do TeamsJS v2 Preview:

| Namespace original `global (window)` | Novo namespace `app` |
| - | - |
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

#### <a name="core-namespace"></a>*namespace* principal

O namespace `core` inclui funcionalidade para links profundos.

| Namespace original `publicAPIs` | Novo namespace `core` |
| - | - |
| `shareDeepLink` | `core.shareDeepLink` |
| `executeDeepLink` | `core.executeDeepLink` |

#### <a name="pages-namespace"></a>*namespace* de páginas

O namespace `pages` inclui a funcionalidade para executar e navegar em páginas da Web em vários clientes do Microsoft 365, incluindo Teams, Office e Outlook. Ele também inclui vários sub-recursos, implementados como sub-namespaces.

| Namespace original `global (window)` | Novo namespace `pages` |
| - | - |
| `setFrameContext` | `pages.setCurrentFrame` (renomeado) |
| `initializeWithFrameContext` | `pages.initializeWithFrameContext` |
| `registerFullScreenHandler` | `pages.registerFullScreenHandler` |
| `navigateCrossDomain` | `pages.navigateCrossDomain` |
| `returnFocus` | `pages.returnFocus` |

##### <a name="pagestabs"></a>*pages.tabs*

| Namespace original `global (window)` | Novo namespace `pages.tabs` |
| - | - |
| `getTabInstances` |  `pages.tabs.getTabInstances` |
| `getMruTabInstances` | `pages.tabs.getMruTabInstances` |
| `navigateToTab` | `pages.tabs.navigateToTab` |

| Namespace original `navigation` | Novo namespace `pages.tabs` |
| - | - |
| `navigation.navigateToTab` | `pages.tabs.navigateToTab` |

##### <a name="pagesconfig"></a>*pages.config*

| Namespace original `settings` | Novo namespace `pages.config`  |
| - | - |
| `settings.setSettings` | `pages.config.setConfig` (renomeado)
| `settings.getSettings` | `pages.config.getConfig` (renomeado)
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
| `registerEnterSettingsHandler` | `pages.config.registerChangeConfigHandler` (renomeado)

##### <a name="pagesbackstack"></a>*pages.backStack*

| Namespace original `navigation` | Novo namespace `pages.backStack`  |
| - | - |
| `navigation.navigateBack` | `pages.backStack.navigateBack`

| Namespace original `global (window)` | Novo namespace `pages.backStack`  |
| - | - |
| `registerBackButtonHandler` | `pages.backStack.registerBackButtonHandler`

##### <a name="pagesappbutton"></a>*pages.appButton*

| Namespace original `global (window)` | Novo namespace `pages.appButton`  |
| - | - |
| `registerAppButtonClickHandler` | `pages.appButton.onClick` (renomeado)
| `registerAppButtonHoverEnterHandler` | `pages.appButton.onHoverEnter` (renomeado)
| `registerAppButtonHoverLeaveEnter` | `pages.appButton.onHoverLeave` (renomeado)
| `FrameContext` interface | `pages.appButton.FrameInfo` (renomeado)) |

#### <a name="dialog-namespace"></a>*namespace* da caixa de diálogo

O namespace de *tarefas* do TeamsJS foi renomeada para *caixa de diálogo* e as seguintes APIs foram renomeadas:

| Namespace original `tasks` | Novo namespace `dialog`  |
| - | - |
| `tasks.startTask` | `dialog.open` (renomeado) |
| `tasks.submitTasks` | `dialog.submit` (renomeado) |
| `tasks.updateTasks` | `dialog.resize` (renomeado) |
| `tasks.TaskModuleDimension` enumeração | `dialog.DialogDimension` (renomeado) |
| `tasks.TaskInfo` interface | `dialog.DialogInfo` (renomeado) |

#### <a name="teamscore-namespace"></a>*namespace* do teamsCore

Para generalizar o SDK do TeamsJS para executar outros hosts do Microsoft 365, como Office e Outlook, a funcionalidade específica do Teams (originalmente no namespace *global*) foi movida para um namespace do *teamsCore*:

| Namespace original `global (window)` | Novo namespace `teamsCore`  |
| - | - |
| `enablePrintCapability` | `teamsCore.enablePrintCapability`
| `print` | `teamsCore.print`
| `registerOnLoadHandler` | `teamsCore.registerOnLoadHandler`
| `registerBeforeUnloadHandler` | `teamsCore.registerBeforeUnloadHandler`
| `registerFocusEnterHandler` | `teamsCore.registerFocusEnterHandler`

### <a name="updates-to-the-context-interface"></a>Atualizações para a interface de *Contexto*

A `Context` interface foi movida para o namespace `app` e atualizada para agrupar propriedades semelhantes para obter melhor escalabilidade à medida que é executada no Outlook e Office, além de Teams.

Uma nova propriedade `app.Context.app.host.name` foi adicionada para habilitar guias pessoais para diferenciar a experiência do usuário, dependendo do aplicativo host.

Você também pode visualizar as alterações examinando a função  [`transformLegacyContextToAppContext`](https://github.com/OfficeDev/microsoft-teams-library-js/blob/2.0-preview/packages/teams-js/src/public/app.ts) na origem da Versão Prévia do SDK do TeamsJS v2.

| Nome original na interface `Context` | Novo local em `app.Context` |
| - | - |
| `appIconPosition` | `app.Context.app.iconPositionVertical` |
| `appLaunchId`| *NÃO NO SDK do cliente Teams v2 Versão Prévia* |
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

## <a name="next-steps"></a>Próximas etapas

Você também pode saber mais sobre alterações interruptivas no log de alterações na [Prévia do SDK do TeamsJS v2](https://github.com/OfficeDev/microsoft-teams-library-js/blob/2.0-preview/packages/teams-js/CHANGELOG.md) e na Referência da API de Versão Prévia do [SDK v2 do TeamsJS](/javascript/api/overview/msteams-client?view=msteams-client-js-beta&preserve-view=true).

Quando estiver pronto para testar seus aplicativos Teams em execução Outlook e Office, confira:

> [!div class="nextstepaction"]
> [Estender seu aplicativo do Teams entre o Microsoft 365](overview.md)
