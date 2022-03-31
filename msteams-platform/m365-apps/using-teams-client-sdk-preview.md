---
title: Microsoft Teams JavaScript client SDK v2 Preview
description: Entenda as alterações que vêm com Microsoft Teams SDK do cliente JavaScript v2 Preview
ms.date: 11/15/2021
ms.topic: conceptual
ms.custom: m365apps
ms.localizationpriority: medium
ms.openlocfilehash: 7aef6fff7e8d68e76f1a9233d3650d3833275bde
ms.sourcegitcommit: 4abb9ca0b0e9661c7e2e329d9f10bad580e7d8f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64464786"
---
# <a name="microsoft-teams-javascript-client-sdk-v2-preview"></a>Microsoft Teams JavaScript client SDK v2 Preview

Com o [SDK do cliente JavaScript v2 Preview do Microsoft Teams](/javascript/api/overview/msteams-client?view=msteams-client-js-beta&preserve-view=true), o SDK do Teams existente (`@microsoft/teams-js`ou `TeamsJS`simplesmente ) foi refatorado para permitir que os desenvolvedores do Teams a capacidade de estender os aplicativos Teams para executar no [Outlook e Office](overview.md). De uma perspectiva funcional, o TeamsJS SDK v2 Preview (`@microsoft/teams-js@next`) é um superconjunto do SDK atual do TeamsJS, ele dá suporte à funcionalidade de aplicativo Teams existente ao adicionar a capacidade de hospedar aplicativos Teams no Outlook e Office.

Há duas alterações significativas no TeamsJS SDK v2 Preview que seu código precisará levar em conta para ser executado em outros aplicativos Microsoft 365:

* [**As funções de retorno de chamada agora retornam objetos Promise.**](#callbacks-converted-to-promises) Todas as funções existentes com um parâmetro de retorno de chamada foram modernizados para retornar um objeto JavaScript [Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) para melhor manipulação de operações assíncronas e capacidade de leitura de código.

* [**As APIs agora estão organizadas em *recursos*.**](#apis-organized-into-capabilities) Você pode pensar em recursos como agrupações lógicas de APIs que fornecem funcionalidades semelhantes, `authentication`como , `calendar`, `mail`, `monetization`, , `meeting`e `sharing`.

 Você pode usar [a extensão Teams Toolkit código](https://aka.ms/teams-toolkit) Microsoft Visual Studio para simplificar o processo de atualização para seu aplicativo Teams, conforme descrito na seção a seguir.

> [!NOTE]
> Habilenciar um aplicativo Teams existente para ser executado Outlook e Office requer ambos:
>
> 1. Dependência do ou `@microsoft/teams-js@2.0.0-beta.1` posterior e
> 2. Modificar o código do aplicativo existente de acordo com as alterações necessárias descritas neste documento.
>
> Se você referenciar `@microsoft/teams-js@2.0.0-beta.1` (ou posterior) de um aplicativo Teams existente, você verá avisos de depreciação se seu código chamar APIs que foram alteradas. Uma camada de conversão de API (mapeamento do SDK atual para visualizar chamadas de API SDK) é fornecida para permitir que aplicativos Teams existentes continuem trabalhando no Teams até que eles sejam capazes de atualizar o código para trabalhar com o SDK do TeamsJS v2 Preview. Depois de atualizar seu código com as alterações descritas neste artigo, sua guia pessoal também será Outlook e Office.

## <a name="updating-to-the-teams-client-sdk-v2-preview"></a>Atualizando para o Teams cliente SDK v2 Preview

A maneira mais fácil de atualizar seu aplicativo Teams para usar o TeamsJS SDK v2 Preview é usar [a extensão Teams Toolkit para](https://aka.ms/teams-toolkit) Visual Studio Code. Esta seção o fará passar pelas etapas para fazer isso. Se você preferir atualizar manualmente seu código, consulte Os [Retornos de Chamada convertidos em promessas](#callbacks-converted-to-promises) e [APIs](#apis-organized-into-capabilities) organizados em seções de recursos para obter mais detalhes sobre as alterações de API necessárias.

### <a name="1-install-the-latest-teams-toolkit-visual-studio-code-extension"></a>1. Instale a extensão de Teams Toolkit Visual Studio Code mais recente

No Visual Studio Code *Do Marketplace de Extensões*, pesquise **por** Teams Toolkit e instale a versão `2.10.0` ou posterior. O kit de ferramentas fornece dois comandos para ajudar no processo:

1. Um comando para atualizar seu esquema de manifesto
1. Um comando para atualizar suas referências SDK e sites de chamada

A seguir estão as duas principais atualizações que você precisará para executar um Teams guia pessoal em outros aplicativos Microsoft 365: ''

### <a name="2-updating-the-manifest"></a>2. Atualizando o manifesto

# <a name="teams-toolkit"></a>[Kit de ferramentas do Teams](#tab/manifest-teams-toolkit)

1. Abra a *paleta Comando*: `Ctrl+Shift+P`
1. Execute **Teams: atualize Teams manifesto para dar suporte Outlook e Office aplicativos** e selecione o arquivo de manifesto do aplicativo. As alterações serão feitas no local.

# <a name="manual-steps"></a>[Etapas manuais](#tab/manifest-manual)

Abra seu Teams de aplicativo e atualize o `$schema` e `manifestVersion` com os seguintes valores:

```json
{
    "$schema" : "https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json",
    "manifestVersion" : "m365DevPreview"
}
```

---

Se você usou Teams Toolkit para criar seu aplicativo pessoal, você também pode usá-lo para validar as alterações no arquivo de manifesto e identificar quaisquer erros. Abra a paleta `Ctrl+Shift+P` de comandos e encontre **Teams:** Valide o arquivo de manifesto ou selecione a opção no menu Implantação do Teams Toolkit (procure o ícone Teams no lado esquerdo do Visual Studio Code).

:::image type="content" source="images/toolkit-validate-manifest-file.png" alt-text="Teams Toolkit opção &quot;Validar arquivo de manifesto&quot; no menu 'Implantação'":::

### <a name="2-update-sdk-references"></a>2. Atualizar referências do SDK

Para ser executado em Outlook e Office, seu aplicativo precisará depender do [pacote npm](https://www.npmjs.com/package/@microsoft/teams-js/v/2.0.0-beta.1) `@microsoft/teams-js@2.0.0-beta.1` (ou de uma versão *beta* posterior). Para executar essas etapas manualmente e para obter mais informações sobre as alterações na API, consulte as seções a seguir sobre [Retornos de Chamada convertidos em promessas](#callbacks-converted-to-promises) e [APIs organizadas em recursos](#apis-organized-into-capabilities).

1. Verifique se você tem [Teams Toolkit](https://aka.ms/teams-toolkit) `v2.10.0` ou posterior
1. Abra a *paleta Comando*: `Ctrl+Shift+P`
1. Executar o comando `Teams: Upgrade Teams JS SDK references to support Outlook and Office apps`

Após a conclusão, o utilitário `package.json` atualizará seu arquivo com a dependência do TeamsJS SDK v2 Preview (`@microsoft/teams-js@2.0.0-beta.1` ou posterior) e seus arquivos e serão atualizados `*.js/.ts` `*.jsx/.tsx` com:

> [!div class="checklist"]
>
> * `package.json` referências ao TeamsJS SDK v2 Preview
> * Instruções de importação do SDK do TeamsJS v2 Preview
> * [Chamadas de Função, Enum e Interface](#apis-organized-into-capabilities) para TeamsJS SDK v2 Preview
> * `TODO` lembretes de comentário para revisar áreas que podem ser afetadas por alterações [de interface de](#updates-to-the-context-interface) contexto
> * `TODO` lembretes de comentário para garantir que as funções de conversão para [promessas](#callbacks-converted-to-promises) de funções de estilo de retorno de chamada foram bem em todos os sites de chamada encontrados pela ferramenta

> [!IMPORTANT]
> O código dentro de arquivos html não é suportado pela ferramenta de atualização e exigirá alterações manuais.

## <a name="callbacks-converted-to-promises"></a>Retornos de chamada convertidos em promessas

Teams APIs que anteriormente tinham um parâmetro de retorno de chamada foram atualizadas para retornar um objeto JavaScript [Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise). Elas incluem as seguintes APIs:

```js
app.getContext, app.initialize, appInstallDialog.openAppInstallDialog, authentication.authenticate, authentication.getAuthToken, authentication.getUser, authentication.registerAuthenticationHandlers was removed to support using Promises, calendar.openCalendarItem, calendar.composeMeeting, call.startCall, core.executeDeepLink, location.getLocation, location.showLocation, mail.openMailItem, mail.composeMail, media.captureImage, media.getMedia, media.selectMedia, media.viewImages, media.scanBarCode, meeting.getAppContentStageSharingCapabilities, meeting.getAuthenticationTokenForAnonymousUser, meeting.getIncomingClientAudioState, meeting.getLiveStreamState, meeting.getMeetingDetails, meeting.requestStartLiveStreaming, meeting.requestStopLiveStreaming, meeting.shareAppContentToStage, meeting.stopSharingAppContentToStage, meeting.toggleIncomingClientAudio, meeting.getAppContentStageSharingState, pages.backStack.navigateBack, pages.navigateCrossDomain, pages.navigateToTab, pages.tabs.getMruTabInstances, pages.tabs.getTabInstances, pages.config.setConfig, pages.config.getConfig, people.selectPeople, ChildAppWindow.postMessage, ParentAppWindow.postMessage
```

Você precisará atualizar a maneira como seu código chama qualquer uma dessas APIs para usar o Promises. Por exemplo, se seu código estiver chamando uma API Teams como esta:

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
> Quando você atualiza seu código para o TeamsJS SDK v2 Preview usando [Teams Toolkit,](#updating-to-the-teams-client-sdk-v2-preview)`TODO` as atualizações necessárias são sinalizadas para você com comentários no código do cliente.

## <a name="apis-organized-into-capabilities"></a>APIs organizadas em recursos

Um *recurso é* um grupo lógico de APIs que fornecem funcionalidade semelhante. Você pode pensar em Microsoft Teams, Outlook e Office, como hosts. Um host dá suporte a um determinado recurso se ele oferece suporte a todas as APIs definidas dentro desse recurso. Um host não pode implementar parcialmente um recurso.  Os recursos podem ser baseados em recursos ou conteúdo, como *caixa de diálogo* ou *autenticação*. Também há recursos para tipos de aplicativos, como *guias/páginas* ou *bots*, e outros agrupamentos.

No TeamsJS SDK v2 Preview, AS APIs são definidas como funções em um namespace JavaScript cujo nome corresponde ao recurso necessário. Se um aplicativo estiver em execução em um host que oferece suporte ao recurso de caixa de diálogo, o aplicativo poderá chamar com segurança APIs `dialog.open` como (além de outras APIs relacionadas à caixa de diálogo definidas no namespace). Enquanto isso, se um aplicativo tentar chamar uma API que não tem suporte nesse host, a API lançará uma exceção.

### <a name="differentiate-your-app-experience"></a>Diferenciar sua experiência de aplicativo

Você pode verificar se há suporte para host de um determinado `isSupported()` recurso em tempo de execução chamando a função nesse recurso (namespace). Ele retornará `true` se tiver suporte e `false` , se não for, e você poderá ajustar o comportamento do aplicativo conforme apropriado. Isso permite que seu aplicativo acente a interface do usuário e a funcionalidade em hosts que o suportam, enquanto continua a ser executado para hosts que não o suportam.

O nome do host em que seu aplicativo está sendo executado é exposto como uma propriedade *hostName* na interface context (`app.Context.app.host.name`), que pode ser consultada em tempo de execução chamando `getContext`. Ele também está disponível como um valor `{hostName}` [de espaço reservado de URL](../tabs/how-to/access-teams-context.md#get-context-by-inserting-url-placeholder-values). A prática prática é usar o *mecanismo hostName* com moderação:

* **Não suponha que** determinada funcionalidade está ou não disponível em um host com base no *valor da propriedade hostName* . Em vez disso, verifique se há suporte para funcionalidades (`isSupported`).
* **Não use hostName** *para* realizar chamadas de API. Em vez disso, verifique se há suporte para funcionalidades (`isSupported`).
* **Use** *hostName* para diferenciar o tema do seu aplicativo com base no host em que está sendo executado. Por exemplo, você pode usar Microsoft Teams roxo como a cor de destaque principal ao executar em Teams e Outlook azul ao executar em Outlook.
* **Use** *hostName* para diferenciar mensagens mostradas para o usuário com base no host em que ele está sendo executado. Por exemplo, mostre *Gerenciar* suas tarefas em Office ao executar no Office na Web e *Gerenciar* suas tarefas no Teams ao executar em Microsoft Teams.

### <a name="namespaces"></a>Namespaces

O TeamsJS SDK v2 Preview organiza APIs em *recursos* por meio de namespaces. Vários novos namespaces de particular importância são *app*, *pages*, *dialog* e *teamsCore*.

#### <a name="app-namespace"></a>*namespace do* aplicativo

O `app` namespace contém APIs de nível superior necessárias para o uso geral do aplicativo, entre Microsoft Teams, Office e Outlook. Todas as APIs de vários outros namespaces TeamsJS foram movidas `app` para o namespace no TeamsJS SDK v2 Preview:

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
| `appInitialization.FailedReason` enum | `app.FailedReason` |
| `appInitialization.ExpectedFailureReason` enum | `app.ExpectedFailureReason` |
| `appInitialization.IFailedRequest` enum | `app.IFailedRequest` |
| `appInitialization.IExpectedFailureRequest` enum | `app.IExpectedFailureRequest` |

#### <a name="core-namespace"></a>*namespace* principal

O `core` namespace inclui funcionalidade para links profundos.

| Namespace original `publicAPIs` | Novo namespace `core` |
| - | - |
| `shareDeepLink` | `core.shareDeepLink` |
| `executeDeepLink` | `core.executeDeepLink` |

#### <a name="pages-namespace"></a>*namespace de* páginas

O `pages` namespace inclui funcionalidades para executar e navegar páginas da Web em vários clientes Microsoft 365, incluindo Teams, Office e Outlook. Ele também inclui vários sub-recursos, implementados como sub-namespaces.

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

#### <a name="dialog-namespace"></a>*namespace de caixa* de diálogo

O namespace *de tarefas do* TeamsJS foi renomeado para *caixa* de diálogo e as SEGUINTES APIs foram renomeadas:

| Namespace original `tasks` | Novo namespace `dialog`  |
| - | - |
| `tasks.startTask` | `dialog.open` (renomeado) |
| `tasks.submitTasks` | `dialog.submit` (renomeado) |
| `tasks.updateTasks` | `dialog.resize` (renomeado) |
| `tasks.TaskModuleDimension` enum | `dialog.DialogDimension` (renomeado) |
| `tasks.TaskInfo` interface | `dialog.DialogInfo` (renomeado) |

#### <a name="teamscore-namespace"></a>*namespace teamsCore*

Para generalizar o SDK do TeamsJS para executar outros hosts Microsoft 365, como Office e Outlook, a funcionalidade específica do Teams (originalmente no namespace *global*) foi movida para um namespace *teamsCore*:

| Namespace original `global (window)` | Novo namespace `teamsCore`  |
| - | - |
| `enablePrintCapability` | `teamsCore.enablePrintCapability`
| `print` | `teamsCore.print`
| `registerOnLoadHandler` | `teamsCore.registerOnLoadHandler`
| `registerBeforeUnloadHandler` | `teamsCore.registerBeforeUnloadHandler`
| `registerFocusEnterHandler` | `teamsCore.registerFocusEnterHandler`

### <a name="updates-to-the-context-interface"></a>Atualizações para a interface *context*

A `Context` interface foi movida `app` para o namespace e atualizada para agrupar propriedades semelhantes para melhor escalabilidade à medida que é executado em Outlook e Office, além de Teams.

Uma nova propriedade `app.Context.app.host.name` foi adicionada para habilitar guias pessoais para diferenciar a experiência do usuário, dependendo do aplicativo host.

Você também pode visualizar as alterações revendo a  [`transformLegacyContextToAppContext`](https://github.com/OfficeDev/microsoft-teams-library-js/blob/2.0-preview/packages/teams-js/src/public/app.ts) função na origem do TeamsJS SDK v2 Preview.

| Nome original na `Context` interface | Novo local em `app.Context` |
| - | - |
| `appIconPosition` | `app.Context.app.iconPositionVertical` |
| `appLaunchId`| *NOT IN Teams client SDK v2 Preview* |
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

Você também pode saber mais sobre como quebrar alterações no [changelog do TeamsJS SDK v2 Preview](https://github.com/OfficeDev/microsoft-teams-library-js/blob/2.0-preview/packages/teams-js/CHANGELOG.md) e na Referência da API de Visualização do [SDK v2 do TeamsJS](/javascript/api/overview/msteams-client?view=msteams-client-js-beta&preserve-view=true).

Quando estiver pronto para testar seus aplicativos Teams em execução em Outlook e Office, consulte:

> [!div class="nextstepaction"]
> [Estender seu Teams aplicativo de Microsoft 365](overview.md)
