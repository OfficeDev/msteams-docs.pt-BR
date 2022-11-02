---
title: Obter contexto para sua guia
description: Aprenda a contextualar para sua guia, contexto de usuário, equipe ou empresa, acessar informações, recuperar contexto em canais privados ou compartilhados e manipular a alteração do tema.
ms.localizationpriority: high
ms.topic: how-to
ms.openlocfilehash: d4dee147da2fd0091e038526ca56d66a9b80f7e5
ms.sourcegitcommit: 9ea9a70d2591bce6b8c980d22014e160f7b45f91
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2022
ms.locfileid: "68820105"
---
# <a name="get-context-for-your-tab"></a>Obtenha contexto para sua guia

Sua guia requer informações contextuais para exibir conteúdo relevante:

* Informações básicas sobre o usuário, a equipe ou a empresa.
* Informações de localidade e tema.
* O `page.id` e `page.subPageId` que identificam o que está nesta guia (conhecido como `entityId` e `subEntityId` anterior ao TeamsJS v.2.0.0).

## <a name="user-context"></a>Contexto do usuário

O contexto sobre o usuário, a equipe ou a empresa pode ser especialmente útil quando:

* Crie ou associe recursos em seu aplicativo com o usuário ou a equipe especificados.
* Você inicia um fluxo de autenticação de Microsoft Azure Active Directory (Azure AD) ou de outro provedor de identidade e não exige que o usuário insira seu nome de usuário novamente.

Para obter mais informações, consulte [autenticar um usuário no Microsoft Teams](~/concepts/authentication/authentication.md).

> [!IMPORTANT]
> Embora essas informações de usuário possam ajudar a fornecer uma experiência suave do usuário, você não deve usá-la como prova de identidade.  Por exemplo, um invasor pode carregar sua página em um navegador e renderizar informações ou solicitações prejudiciais.

## <a name="access-context-information"></a>Informações de contexto de acesso

Você pode acessar informações de contexto de duas maneiras:

* Usando [valores de espaço reservado de URL](#get-context-by-inserting-url-placeholder-values).
* No objeto de [contexto](/javascript/api/@microsoft/teams-js/app.context) SDK do cliente JavaScript do Microsoft Teams.

### <a name="get-context-by-inserting-url-placeholder-values"></a>Obter contexto inserindo valores de espaço reservado de URL

Usar espaços reservados em sua configuração ou URLs de conteúdo. O Microsoft Teams substitui os espaços reservados pelos valores relevantes ao determinar a configuração real ou o URL do conteúdo. Os espaços reservados disponíveis incluem todos os campos no objeto [de contexto](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true) . Os espaços reservados comuns incluem as seguintes propriedades:

* [{page.id}](/javascript/api/@microsoft/teams-js/app.pageinfo#@microsoft-teams-js-app-pageinfo-id): A ID exclusiva definida pelo desenvolvedor para a página definida ao [configurar a página](~/tabs/how-to/create-tab-pages/configuration-page.md) pela primeira vez. (Conhecido como `{entityId}` anterior ao TeamsJS v.2.0.0).
* [{page.subPageId}](/javascript/api/@microsoft/teams-js/app.pageinfo#@microsoft-teams-js-app-pageinfo-subpageid): A ID exclusiva definida pelo desenvolvedor para a subpage que esse conteúdo aponta definida ao gerar um [link profundo](~/concepts/build-and-test/deep-links.md) para um item específico na página. (Conhecido como `{subEntityId}` anterior ao TeamsJS v.2.0.0).
* [{user.loginHint}](/javascript/api/@microsoft/teams-js/app.userinfo#@microsoft-teams-js-app-userinfo-loginhint): um valor adequado como uma dica de entrada para Azure AD. Geralmente, esse é o nome de logon do usuário atual em seu locatário doméstico. (Conhecido como `{loginHint}` anterior ao TeamsJS v.2.0.0).
* [{user.userPrincipalName}](/javascript/api/@microsoft/teams-js/app.userinfo#@microsoft-teams-js-app-userinfo-userprincipalname): o nome da entidade de usuário do usuário atual no locatário atual. (Conhecido como `{userPrincipalName}` anterior ao TeamsJS v.2.0.0).
* [{user.id}](/javascript/api/@microsoft/teams-js/app.userinfo#@microsoft-teams-js-app-userinfo-id): A ID do objeto Azure AD do usuário atual no locatário atual. (Conhecido como `{userObjectId}` anterior ao TeamsJS v.2.0.0).
* [{app.theme}](/javascript/api/@microsoft/teams-js/app.appinfo#@microsoft-teams-js-app-appinfo-theme): o tema da interface do usuário (interface do usuário) atual, como `default`, `dark`ou `contrast`. (Conhecido como `{theme}` anterior ao TeamsJS v.2.0.0).
* [{team.groupId}](/javascript/api/@microsoft/teams-js/app.teaminfo#@microsoft-teams-js-app-teaminfo-groupid): A ID do grupo Office 365 no qual a guia reside. (Conhecido como `{groupId}` anterior ao TeamsJS v.2.0.0)
* [{user.tenant.id}](/javascript/api/@microsoft/teams-js/app.tenantinfo#@microsoft-teams-js-app-tenantinfo-id): A ID do locatário Azure AD do usuário atual. (Conhecido como `{tid}` anterior ao TeamsJS v.2.0.0).
* [{app.locale}](/javascript/api/@microsoft/teams-js/app.appinfo#@microsoft-teams-js-app-appinfo-locale): a localidade atual do usuário formatada como *languageId-countryId*, por exemplo `en-us`. (Conhecido como `{locale}` anterior ao TeamsJS v.2.0.0).

> [!NOTE]
> O espaço reservado `{upn}` anterior agora está preterido. Para compatibilidade com versões anteriores, é atualmente um sinônimo para `{user.loginHint}`.

Por exemplo, no manifesto do aplicativo, se você definir o atributo *configurationUrl* da `"https://www.contoso.com/config?name={user.loginHint}&tenant={user.tenant.id}&group={team.groupId}&theme={app.theme}"` guia como e o usuário conectado tiver os seguintes atributos:

* Seu nome de usuário é **user@example.com**.
* A ID do locatário da empresa é **e2653c-etc**.
* Eles são membros do grupo Office 365 com ID **00209384-etc**.
* O usuário definiu seu tema do Teams como **escuro**.

. . . em seguida, o Teams chamará a seguinte URL ao configurar a guia:

`https://www.contoso.com/config?name=user@example.com&tenant=e2653c-etc&group=00209384-etc&theme=dark`

### <a name="get-context-by-using-the-microsoft-teams-javascript-library"></a>Obter contexto usando a biblioteca JavaScript do Microsoft Teams

Você também pode recuperar as informações listadas acima usando o [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client) chamando `microsoftTeams.getContext(function(context) { /* ... */ })`.

O código a seguir fornece um exemplo de variável de contexto:

```json
{
    "teamId": "The Microsoft Teams ID in the format 19:[id]@thread.skype",
    "teamName": "The name of the current team",
    "channelId": "The channel ID in the format 19:[id]@thread.skype",
    "channelName": "The name of the current channel",
    "chatId": "The chat ID in the format 19:[id]@thread.skype",
    "locale": "The current locale of the user formatted as languageId-countryId (for example, en-us)",
    "entityId": "The developer-defined unique ID for the entity this content points to",
    "subEntityId": "The developer-defined unique ID for the sub-entity this content points to",
    "loginHint": "A value suitable as a login hint for Azure AD. This is usually the login name of the current user, in their home tenant",
    "userPrincipalName": "The principal name of the current user, in the current tenant",
    "userObjectId": "The Azure AD object id of the current user, in the current tenant",
    "tid": "The Azure AD tenant ID of the current user",
    "groupId": "Guid identifying the current Office 365 Group ID",
    "theme": "The current UI theme: default | dark | contrast",
    "isFullScreen": "Indicates if the tab is in full-screen",
    "teamType": "The type of team",
    "teamSiteUrl": "The root SharePoint site associated with the team",
    "teamSiteDomain": "The domain of the root SharePoint site associated with the team",
    "teamSitePath": "The relative path to the SharePoint site associated with the team",
    "channelRelativeUrl": "The relative path to the SharePoint folder associated with the channel",
    "sessionId": "The unique ID for the current Teams session for use in correlating telemetry data",
    "userTeamRole": "The user's role in the team",
    "isTeamArchived": "Indicates if team is archived",
    "hostClientType": "The type of host client. Possible values are android, ios, web, desktop, surfaceHub, teamsRoomsAndroid, teamsPhones, teamsDisplays rigel (deprecated, use teamsRoomsWindows instead)",
    "frameContext": "The context where tab URL is loaded (for example, content, task, setting, remove, sidePanel)",
    "sharepoint": "The SharePoint context is available only when hosted in SharePoint",
    "tenantSKU": "The license type for the current user tenant. Possible values are enterprise, free, edu, unknown",
    "userLicenseType": "The license type for the current user",
    "parentMessageId": "The parent message ID from which this task module is launched",
    "ringId": "The current ring ID",
    "appSessionId": "The unique ID for the current session used for correlating telemetry data",
    "isCallingAllowed": "Indicates if calling is allowed for the current logged in user",
    "isPSTNCallingAllowed": "Indicates if PSTN calling is allowed for the current logged in user",
    "meetingId": "The meeting ID used by tab when running in meeting context",
    "defaultOneNoteSectionId": "The OneNote section ID that is linked to the channel",
    "isMultiWindow": "The indication whether the tab is in a pop out window"
}
```

# <a name="teamsjs-v2"></a>[TeamsJS v2](#tab/teamsjs-v2)

## <a name="typescript"></a>TypeScript

```TypeScript
import { app, Context } from "@microsoft/teams-js";

app.getContext().then((context: Context) => {
    /*...*/
});
```

Padrão equivalente `async/await` :

```TypeScript
import { app, Context } from "@microsoft/teams-js";

async function example() {
  const context: Context = await app.getContext();
  /*...*/
}
```

## <a name="javascript"></a>JavaScript

```js
import { app, Context } from "@microsoft/teams-js";

app.getContext().then((context) => {
    /*...*/
});
```

Padrão equivalente `async/await` :

```js
import { app, Context } from "@microsoft/teams-js";

async function example() {
  const context = await app.getContext();
  /*...*/
}
```

# <a name="teamsjs-v1"></a>[TeamsJS v1](#tab/teamsjs-v1)

## <a name="typescript"></a>TypeScript

```TypeScript
import * as microsoftTeams from "@microsoft/teams-js";

microsoftTeams.getContext((context: microsoftTeams.Context) => {
  /* ... */
});
```

## <a name="javascript"></a>JavaScript

```js
import microsoftTeams from "@microsoft/teams-js";

microsoftTeams.getContext((context) => {
  /* ... */ 
});
```

---

A tabela a seguir lista as propriedades de contexto comumente usadas do objeto *de contexto* :

| Nome do TeamsJS v2 | Nome do TeamsJS v1 | Descrição |
|-----------------|-----------------|-------------|
| team.internalId | teamId | A ID do Microsoft Teams para a equipe com a qual o conteúdo está associado. |
| team.displayName | teamName | O nome da equipe com a qual o conteúdo está associado. |
| channel.id | channelId | A ID do Microsoft Teams para o canal com o qual o conteúdo está associado. |
| channel.displayName | Channelname | O nome do canal com o qual o conteúdo está associado. |
| chat.id | chatId | A ID do Microsoft Teams para o chat com o qual o conteúdo está associado. |
| app.locale | localidade | A localidade atual que o usuário configurou para o aplicativo formatada como languageId-countryId (por exemplo, en-us). |
| page.id | entityId | A ID exclusiva definida pelo desenvolvedor para a página à qual esse conteúdo aponta. |
| page.subPageId | subEntityId | A ID exclusiva definida pelo desenvolvedor para a sub-página a que esse conteúdo aponta. Esse campo deve ser usado para restaurar um estado específico em uma página, como rolar para ou ativar um conteúdo específico. |
| user.loginHint | loginHint | Um valor adequado para uso como login_hint ao autenticar com Azure AD. Como uma parte mal-intencionada pode executar seu conteúdo em um navegador, esse valor deve ser usado apenas como uma dica de quem é o usuário e nunca como prova de identidade. Esse campo só está disponível quando a permissão de identidade é solicitada no manifesto. |
| user.userPrincipalName | Upn | O UPN do usuário atual. Isso pode ser um UPN autenticado externamente (por exemplo, usuários convidados). Como uma parte mal-intencionada executa seu conteúdo em um navegador, esse valor deve ser usado apenas como uma dica de quem é o usuário e nunca como prova de identidade. Esse campo só está disponível quando a permissão de identidade é solicitada no manifesto. |
| user.id | userObjectId | A ID do objeto Azure AD do usuário atual. Como uma parte mal-intencionada executa seu conteúdo em um navegador, esse valor deve ser usado apenas como uma dica de quem é o usuário e nunca como prova de identidade. Esse campo só está disponível quando a permissão de identidade é solicitada no manifesto. |
| user.tenant.id | Tid | A Azure AD ID do locatário do usuário atual. Como uma parte mal-intencionada pode executar seu conteúdo em um navegador, esse valor deve ser usado apenas como uma dica de quem é o usuário e nunca como prova de identidade. Esse campo só está disponível quando a permissão de identidade é solicitada no manifesto. |
| team.groupId | groupId | O Office 365 ID do grupo para a equipe com a qual o conteúdo está associado. Esse campo só está disponível quando a permissão de identidade é solicitada no manifesto. |
| app.theme  | tema | O tema atual da interface do usuário: padrão, escuro, contraste |
| page.isFullScreen | isFullScreen | Indicação se a página está no modo de tela inteira. |
| team.type | teamType | O tipo da equipe. |
| sharepointSite.teamSiteUrl | teamSiteUrl | O site raiz do SharePoint associado à equipe. |
| sharepointSite.teamSiteDomain | teamSiteDomain | O domínio do site raiz do SharePoint associado à equipe. |
| sharepointSite.teamSitePath | teamSitePath | O caminho relativo para o site do SharePoint associado à equipe. |
| channel.relativeUrl | channelRelativeUrl | O caminho relativo para a pasta SharePoint associada ao canal. |
| app.host.sessionId | Sessionid | ID exclusiva para a sessão host atual para uso na correlação de dados de telemetria. |
| team.userRole | userTeamRole | A função do usuário na equipe. Como uma parte mal-intencionada pode executar seu conteúdo em um navegador, esse valor deve ser usado apenas como uma dica sobre a função do usuário e nunca como prova de sua função. |
| team.isArchived | isTeamArchived | Indica se a equipe está arquivada. Os aplicativos devem usá-lo como um sinal para evitar alterações no conteúdo associado às equipes arquivadas. |
| app.host.clientType | hostClientType | O tipo do cliente host. Os valores possíveis são: android, ios, Web, desktop, rigel |
| page.frameContext | frameContext | O contexto em que a url da página é carregada (conteúdo, tarefa, configuração, remoção, sidePanel) |
| sharepoint | sharepoint | Contexto do SharePoint. Isso só está disponível quando hospedado no SharePoint. |
| user.tenant.teamsSku | tenantSKU | O tipo de licença para o locatário de usuário atual. Os valores possíveis são enterprise, free, edu, unknown |
| user.licenseType | userLicenseType | O tipo de licença para o usuário atual. Os valores possíveis são planos corporativos E1, E3 e E5 |
| app.parentMessageId | parentMessageId | A ID da mensagem pai da qual este módulo de tarefa foi iniciado. Isso só está disponível em módulos de tarefa iniciados a partir de cartões bot. |
| app.host.ringId | ringId | ID do anel atual. |
| app.sessionId | appSessionId | ID exclusiva para a sessão host atual para uso na correlação de dados de telemetria. |
| user.isCallingAllowed | isCallingAllowed | Representa se a chamada é permitida para o usuário conectado atual. |
| user.isPSTNCallingAllowed | isPSTNCallingAllowed | Indica se a chamada PSTN é permitida para o usuário atual |
| meeting.id | meetingId | A ID da reunião usada por guia ao executar no contexto de reunião. |
| channel.defaultOneNoteSectionId | defaultOneNoteSectionId | A ID da seção do OneNote vinculada ao canal. |
| page.isMultiWindow | isMultiWindow | A indicação se a guia está em uma janela pop out. |

Para obter mais informações, consulte [Atualizações para a interface *context*](using-teams-client-sdk.md#updates-to-the-context-interface) e a referência da API de [interface de contexto](/javascript/api/@microsoft/teams-js/app.context).

## <a name="retrieve-context-in-private-channels"></a>Recuperar contexto em canais privados

> [!NOTE]
> No momento, os canais privados estão apenas na versão prévia do desenvolvedor privado.

Quando sua página de conteúdo é carregada em um canal privado, os dados que você recebe da `getContext` chamada são ofuscados para proteger a privacidade do canal.

Os seguintes campos são alterados quando sua página de conteúdo está em um canal privado:

* `team.groupId`: indefinido para canais privados
* `team.internalId`: Defina como o threadId do canal privado
* `team.displayName`: Definir como o nome do canal privado
* `sharepointSite.url`: Defina como a URL de um site do SharePoint distinto e exclusivo para o canal privado
* `sharepointSite.path`: Defina como o caminho de um site do SharePoint exclusivo e distinto para o canal privado
* `sharepointSite.domain`: Defina como o domínio de um domínio de site do SharePoint distinto e exclusivo para o canal privado

Se sua página usa qualquer um desses valores, o valor do `channel.membershipType` campo deve ser `Private` para determinar se sua página está carregada em um canal privado e pode responder adequadamente.

> [!NOTE]
>`teamSiteUrl` também funciona bem para canais padrão. Se sua página usa qualquer um desses valores, o valor do `channelType` campo deve ser `Shared` para determinar se sua página está carregada em um canal compartilhado e pode responder adequadamente.

## <a name="get-context-in-shared-channels"></a>Obter contexto em canais compartilhados

Quando a UX de conteúdo for carregada em um canal compartilhado, use os dados recebidos da chamada para alterações de `getContext` canal compartilhado. Se a guia fizer uso de qualquer um dos valores a seguir, você deverá preencher o `channelType` campo para determinar se a guia está carregada em um canal compartilhado e responder adequadamente.
Para canais compartilhados, o `groupId` valor é `null`, uma vez que o groupId da equipe de host não reflete com precisão a verdadeira associação do canal compartilhado. Para resolver isso, as `hostTeamGroupID` propriedades e `hostTenantID` são adicionadas recentemente e úteis para fazer chamadas do Microsoft API do Graph para recuperar a associação. `hostTeam` refere-se à Equipe que criou o canal compartilhado. `currentTeam` refere-se à Equipe da qual o usuário atual está acessando o canal compartilhado.

Para obter mais informações sobre esses conceitos, consulte [canais compartilhados](~/concepts/build-and-test/shared-channels.md).

Use as seguintes `getContext` propriedades em canais compartilhados:

| Propriedade | Descrição |
|----------|--------------|
|`channelId`| A propriedade é definida como a ID do thread de canais compartilhados.|
|`channelType`| A propriedade está definida como para `sharedChannel` canais compartilhados.|
|`groupId`|A propriedade é `null` para canais compartilhados.|
|`hostTenantId`| A propriedade foi adicionada recentemente e descreve a ID do locatário do host, útil para comparar com a propriedade de locatário do `tid` usuário atual. |
|`hostTeamGroupId`| A propriedade foi adicionada recentemente e descreve a ID do grupo Azure AD da equipe de host, útil para fazer chamadas do Microsoft API do Graph para recuperar a associação de canal compartilhado. |
|`teamId`|A propriedade foi adicionada recentemente e definida como a ID do thread da equipe compartilhada atual. |
|`teamName`|A propriedade está definida como `teamName`. |
|`teamType`|A propriedade está definida como `teamType`.|
|`teamSiteUrl`|A propriedade descreve o canal `channelSiteUrl`compartilhado .|
|`teamSitePath`| A propriedade descreve o canal `channelSitePath`compartilhado .|
|`teamSiteDomain`| A propriedade descreve o canal `channelSiteDomain`compartilhado .|
|`tenantSKU`| A propriedade descreve o `tenantSKU`.|
|`tid`|  A propriedade descreve a ID do locatário do usuário atual.|
|`userObjectId`|  A propriedade descreve a ID do usuário atual.|
|`userPrincipalName`| A propriedade descreve o UPN do usuário atual.|

Para obter mais informações sobre canais compartilhados, consulte [canais compartilhados](~/concepts/build-and-test/shared-channels.md).

## <a name="handle-theme-change"></a>Manipular alteração de tema

Você pode registrar seu aplicativo para ser informado se o tema for alterado chamando `microsoftTeams.app.registerOnThemeChangeHandler(function(theme) { /* ... */ })`.

O `theme` argumento na função é uma cadeia de caracteres com um valor de `default`, `dark`ou `contrast`.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Criar guias com Cartões Adaptáveis](~/tabs/how-to/build-adaptive-card-tabs.md)

## <a name="see-also"></a>Confira também

* [Compilar guias para o Teams](../what-are-tabs.md)
* [Projete sua guia para o Microsoft Teams](../design/tabs.md)
* [Habilitar o logon único para o aplicativo de guia](authentication/tab-sso-overview.md)
* [Conexão Microsoft Teams canais compartilhados](../../concepts/build-and-test/shared-channels.md)
* [Esquema de manifesto do aplicativo para o Teams](../../resources/schema/manifest-schema.md)
* [Usar módulos de tarefas nas guias](../../task-modules-and-cards/task-modules/task-modules-tabs.md)
