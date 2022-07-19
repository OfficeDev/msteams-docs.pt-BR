---
title: Obter contexto para sua guia
description: Neste módulo, saiba como obter o contexto do usuário para suas guias, contexto do usuário e informações de contexto do Access
ms.localizationpriority: medium
ms.topic: how-to
ms.openlocfilehash: 63bbc9c0e5f20e293f9230000597860e3f053274
ms.sourcegitcommit: 79d525c0be309200e930cdd942bc2c753d0b718c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/19/2022
ms.locfileid: "66841719"
---
# <a name="get-context-for-your-tab"></a>Obtenha contexto para sua guia

Sua guia requer informações contextuais para exibir conteúdo relevante:

* Informações básicas sobre o usuário, a equipe ou a empresa.
* Informações de localidade e tema.
* O `page.id` e `page.subPageId` que identificam o que está nessa guia (conhecido `entityId` como e `subEntityId` antes do TeamsJS v.2.0.0).

[!INCLUDE [sdk-include](~/includes/sdk-include.md)]

## <a name="user-context"></a>Contexto do usuário

O contexto sobre o usuário, a equipe ou a empresa pode ser especialmente útil quando:

* Você cria ou associa recursos em seu aplicativo ao usuário ou à equipe especificado.
* Você inicia um fluxo de autenticação Microsoft Azure Active Directory (Azure AD) ou outro provedor de identidade e não exige que o usuário insira seu nome de usuário novamente.

Para obter mais informações, [consulte autenticar um usuário no Microsoft Teams](~/concepts/authentication/authentication.md).

> [!IMPORTANT]
> Embora essas informações do usuário possam ajudar a fornecer uma experiência de usuário suave, você não deve usá-la como prova de identidade.  Por exemplo, um invasor pode carregar sua página em um navegador e renderizar informações ou solicitações prejudiciais.

## <a name="access-context-information"></a>Acessar informações de contexto

Você pode acessar informações de contexto de duas maneiras:

* Usando [valores de espaço reservado de URL](#get-context-by-inserting-url-placeholder-values).
* Do objeto de contexto do SDK do cliente JavaScript [do](/javascript/api/@microsoft/teams-js/app.context) Microsoft Teams.

### <a name="get-context-by-inserting-url-placeholder-values"></a>Obter contexto inserindo valores de espaço reservado de URL

Usar espaços reservados em sua configuração ou URLs de conteúdo. O Microsoft Teams substitui os espaços reservados pelos valores relevantes ao determinar a configuração real ou o URL do conteúdo. Os espaços reservados disponíveis incluem todos os campos no objeto [de](/javascript/api/@microsoft/teams-js/app.context) contexto. Os espaços reservados comuns incluem as seguintes listas:

* [{page.id}](/javascript/api/@microsoft/teams-js/app.pageinfo#@microsoft-teams-js-app-pageinfo-id): a ID exclusiva definida pelo desenvolvedor para a página definida ao [configurar a página pela primeira vez](~/tabs/how-to/create-tab-pages/configuration-page.md). (Conhecido como anterior `{entityId}` ao TeamsJS v.2.0.0).
* [{page.subPageId}](/javascript/api/@microsoft/teams-js/app.pageinfo#@microsoft-teams-js-app-pageinfo-subpageid): a ID exclusiva definida pelo desenvolvedor para a subpágina que esse conteúdo aponta definido ao gerar um [link](~/concepts/build-and-test/deep-links.md) profundo para um item específico dentro da página. (Conhecido como anterior `{subEntityId}` ao TeamsJS v.2.0.0).
* [{user.loginHint}](/javascript/api/@microsoft/teams-js/app.userinfo#@microsoft-teams-js-app-userinfo-loginhint): um valor adequado como uma dica de logon para Azure AD. Geralmente, esse é o nome de logon do usuário atual em seu locatário inicial. (Conhecido como anterior `{loginHint}` ao TeamsJS v.2.0.0).
* [{user.userPrincipalName}](/javascript/api/@microsoft/teams-js/app.userinfo#@microsoft-teams-js-app-userinfo-userprincipalname): o nome principal do usuário atual no locatário atual. (Conhecido como anterior `{userPrincipalName}` ao TeamsJS v.2.0.0).
* [{user.id}](/javascript/api/@microsoft/teams-js/app.userinfo#@microsoft-teams-js-app-userinfo-id): a ID Azure AD objeto do usuário atual no locatário atual. (Conhecido como anterior `{userObjectId}` ao TeamsJS v.2.0.0).
* [{app.theme}](/javascript/api/@microsoft/teams-js/app.appinfo#@microsoft-teams-js-app-appinfo-theme): o tema da interface do usuário atual, como `default`, `dark`ou `contrast`. (Conhecido como anterior `{theme}` ao TeamsJS v.2.0.0).
* [{team.groupId}](/javascript/api/@microsoft/teams-js/app.teaminfo#@microsoft-teams-js-app-teaminfo-groupid): a ID do grupo Office 365 no qual a guia reside. (Conhecido como anterior `{groupId}` ao TeamsJS v.2.0.0)
* [{user.tenant.id}](/javascript/api/@microsoft/teams-js/app.tenantinfo#@microsoft-teams-js-app-tenantinfo-id): a ID Azure AD locatário do usuário atual. (Conhecido como anterior `{tid}` ao TeamsJS v.2.0.0).
* [{app.locale}](/javascript/api/@microsoft/teams-js/app.appinfo#@microsoft-teams-js-app-appinfo-locale): a localidade atual do usuário formatada como *languageId-countryId*, por exemplo `en-us`. (Conhecido como anterior `{locale}` ao TeamsJS v.2.0.0).

> [!NOTE]
> O espaço reservado `{upn}` anterior agora está preterido. Para compatibilidade com versões anteriores, é atualmente um sinônimo para `{user.loginHint}`.

Por exemplo, no manifesto do aplicativo, se você definir o atributo *tab configurationUrl* como `"https://www.contoso.com/config?name={user.loginHint}&tenant={user.tenant.id}&group={team.groupId}&theme={app.theme}"` e o usuário conectado tiver os seguintes atributos:

* O nome de usuário é **user@example.com**.
* A ID do locatário da empresa **é e2653c-etc**.
* Eles são membros do grupo Office 365 com a ID **00209384-etc**.
* O usuário definiu o tema do Teams como **escuro**.

. . . Em seguida, o Teams chamará a seguinte URL ao configurar a guia:

`https://www.contoso.com/config?name=user@example.com&tenant=e2653c-etc&group=00209384-etc&theme=dark`

### <a name="get-context-by-using-the-microsoft-teams-javascript-library"></a>Obter contexto usando a biblioteca JavaScript do Microsoft Teams

Você também pode recuperar as informações listadas acima usando o [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client) chamando `microsoftTeams.getContext(function(context) { /* ... */ })`.

# <a name="teamsjs-v2"></a>[TeamsJS v2](#tab/teamsjs-v2)

## <a name="typescript"></a>TypeScript

```TypeScript
import { app, Context } from "@microsoft/teams-js";

app.getContext().then((context: Context) => {
    /*...*/
});
```

Padrão `async/await` equivalente:

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

Padrão `async/await` equivalente:

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

A tabela a seguir lista as propriedades de contexto comumente usadas do *objeto de* contexto:

| Nome do TeamsJS v2 | Nome do TeamsJS v1 | Descrição |
|-----------------|-----------------|-------------|
| team.internalId | teamId | A ID do Microsoft Teams para a equipe à qual o conteúdo está associado. |
| team.displayName | teamName | O nome da equipe à qual o conteúdo está associado. |
| channel.id | channelId | A ID do Microsoft Teams para o canal ao qual o conteúdo está associado. |
| channel.displayName | Channelname | O nome do canal ao qual o conteúdo está associado. |
| chat.id | chatId | A ID do Microsoft Teams para o chat ao qual o conteúdo está associado. |
| app.locale | localidade | A localidade atual que o usuário configurou para o aplicativo formatado como languageId-countryId (por exemplo, en-us). |
| page.id | entityId | A ID exclusiva definida pelo desenvolvedor para a página para a qual esse conteúdo aponta. |
| page.subPageId | subEntityId | A ID exclusiva definida pelo desenvolvedor para a subpágina para a qual esse conteúdo aponta. Esse campo deve ser usado para restaurar para um estado específico dentro de uma página, como rolar para ou ativar uma parte específica do conteúdo. |
| user.loginHint | loginHint | Um valor adequado para uso como um login_hint ao autenticar com Azure AD. Como uma parte mal-intencionada pode executar seu conteúdo em um navegador, esse valor deve ser usado apenas como uma dica sobre quem é o usuário e nunca como prova de identidade. Esse campo só estará disponível quando a permissão de identidade for solicitada no manifesto. |
| user.userPrincipalName | Upn | O UPN do usuário atual. Pode ser um UPN autenticado externamente (por exemplo, usuários convidados). Como uma parte mal-intencionada executa seu conteúdo em um navegador, esse valor deve ser usado apenas como uma dica sobre quem é o usuário e nunca como prova de identidade. Esse campo só estará disponível quando a permissão de identidade for solicitada no manifesto. |
| user.id | userObjectId | A Azure AD ID de objeto do usuário atual. Como uma parte mal-intencionada executa seu conteúdo em um navegador, esse valor deve ser usado apenas como uma dica sobre quem é o usuário e nunca como prova de identidade. Esse campo só estará disponível quando a permissão de identidade for solicitada no manifesto. |
| user.tenant.id | Tid | A Azure AD ID de locatário do usuário atual. Como uma parte mal-intencionada pode executar seu conteúdo em um navegador, esse valor deve ser usado apenas como uma dica sobre quem é o usuário e nunca como prova de identidade. Esse campo só estará disponível quando a permissão de identidade for solicitada no manifesto. |
| team.groupId | groupId | A Office 365 de grupo da equipe à qual o conteúdo está associado. Esse campo só estará disponível quando a permissão de identidade for solicitada no manifesto. |
| app.theme  | tema | O tema atual da interface do usuário: padrão, escuro, contraste |
| page.isFullScreen | isFullScreen | Indicação se a página está no modo de tela inteira. |
| team.type | teamType | O tipo da equipe. |
| sharepointSite.teamSiteUrl | teamSiteUrl | O site raiz do SharePoint associado à equipe. |
| sharepointSite.teamSiteDomain | teamSiteDomain | O domínio do site raiz do SharePoint associado à equipe. |
| sharepointSite.teamSitePath | teamSitePath | O caminho relativo para o site do SharePoint associado à equipe. |
| channel.relativeUrl | channelRelativeUrl | O caminho relativo para a pasta do SharePoint associada ao canal. |
| app.host.sessionId | Sessionid | ID exclusiva para a sessão host atual para uso na correlação de dados de telemetria. |
| team.userRole | userTeamRole | A função do usuário na equipe. Como uma parte mal-intencionada pode executar seu conteúdo em um navegador, esse valor deve ser usado apenas como uma dica sobre a função do usuário e nunca como prova de sua função. |
| team.isArchived | isTeamArchived | Indica se a equipe está arquivada. Os aplicativos devem usá-lo como um sinal para evitar alterações no conteúdo associado a equipes arquivadas. |
| app.host.clientType | hostClientType | O tipo do cliente host. Os valores possíveis são: android, ios, Web, desktop, rigel |
| page.frameContext | frameContext | O contexto em que a URL da página é carregada (conteúdo, tarefa, configuração, remover, sidePanel) |
| sharepoint | sharepoint | Contexto do SharePoint. Isso só está disponível quando hospedado no SharePoint. |
| user.tenant.teamsSku | tenantSKU | O tipo de licença para o locatário do usuário atual. Os valores possíveis são enterprise, free, edu, unknown |
| user.licenseType | userLicenseType | O tipo de licença para o usuário atual. Os valores possíveis são planos empresariais E1, E3 e E5 |
| app.parentMessageId | parentMessageId | A ID da mensagem pai da qual este módulo de tarefa foi iniciado. Isso só está disponível em módulos de tarefas iniciados de cartões de bot. |
| app.host.ringId | ringId | ID do anel atual. |
| app.sessionId | appSessionId | ID exclusiva para a sessão host atual para uso na correlação de dados de telemetria. |
| user.isCallingAllowed | isCallingAllowed | Representa se a chamada é permitida para o usuário conectado atual. |
| user.isPSTNCallingAllowed | isPSTNCallingAllowed | Indica se a chamada PSTN é permitida para o usuário atual |
| meeting.id | meetingId | A ID da reunião usada pela guia durante a execução no contexto da reunião. |
| channel.defaultOneNoteSectionId | defaultOneNoteSectionId | A ID da seção do OneNote que está vinculada ao canal. |
| page.isMultiWindow | isMultiWindow | A indicação se a guia está em uma janela pop-out. |

Para obter mais informações, [consulte Atualizações interface *de* contexto e](using-teams-client-sdk.md#updates-to-the-context-interface) a referência da API [de interface](/javascript/api/@microsoft/teams-js/app.context) de contexto.

## <a name="retrieve-context-in-private-channels"></a>Recuperar contexto em canais privados

Quando sua página de conteúdo é carregada em um canal privado, `getContext` os dados recebidos da chamada são ofuscados para proteger a privacidade do canal.

Os campos a seguir são alterados quando sua página de conteúdo está em um canal privado:

* `team.groupId`: indefinido para canais privados
* `team.internalId`: definido como o threadId do canal privado
* `team.displayName`: definido como o nome do canal privado
* `sharepointSite.url`: definido como a URL de um site exclusivo e distinto do SharePoint para o canal privado
* `sharepointSite.path`: defina como o caminho de um site exclusivo e distinto do SharePoint para o canal privado
* `sharepointSite.domain`: definido como o domínio de um domínio de site exclusivo e distinto do SharePoint para o canal privado

Se sua página usa qualquer um desses valores, `channel.membershipType` `Private` o valor do campo deve ser determinar se sua página é carregada em um canal privado e pode responder adequadamente.

## <a name="retrieve-context-in-microsoft-teams-connect-shared-channels"></a>Recuperar contexto em Conexão Microsoft Teams canais compartilhados

> [!NOTE]
> Atualmente, os Conexão Microsoft Teams compartilhados estão apenas na versão [prévia do](../../resources/dev-preview/developer-preview-intro.md) desenvolvedor.

Quando sua página de conteúdo é carregada em um canal Conexão Microsoft Teams compartilhado, `getContext` os dados recebidos da chamada são alterados devido à lista exclusiva de usuários em canais compartilhados.

Os campos a seguir são alterados quando sua página de conteúdo está em um canal compartilhado:

* `team.groupId`: indefinido para canais compartilhados.
* `team.internalId`: definido como o `threadId` da equipe, o canal é compartilhado para o usuário atual. Se o usuário tiver acesso a várias equipes, isso será definido como a equipe que hospeda (cria) o canal compartilhado.
* `team.displayName`: definido como o nome da equipe, o canal é compartilhado para o usuário atual. Se o usuário tiver acesso a várias equipes, isso será definido como a equipe que hospeda (cria) o canal compartilhado.
* `sharepointSite.url`: defina como a URL de um site exclusivo e distinto do SharePoint para o canal compartilhado.
* `sharepointSite.path`: defina como o caminho de um site exclusivo e distinto do SharePoint para o canal compartilhado.
* `sharepointSite.domain`: defina como o domínio de um domínio de site exclusivo e distinto do SharePoint para o canal compartilhado.

Além dessas alterações de campo, há dois novos campos disponíveis para canais compartilhados:

* `hostTeamGroupId`: defina como o `team.groupId` associado à equipe de hospedagem ou à equipe que criou o canal compartilhado. A propriedade pode fazer com que as chamadas API do Graph Microsoft recuperem a associação do canal compartilhado.
* `hostTeamTenantId`: defina como o `channel.ownerTenantId` associado à equipe de hospedagem ou à equipe que criou o canal compartilhado. A propriedade pode ser referenciada de modo cruzado com a ID `user.tenant.id` de locatário do usuário atual encontrada no campo do  objeto de contexto para determinar se o usuário é interno ou externo ao locatário da equipe de hospedagem.

Se sua página usa qualquer um desses valores, `channel.membershipType` `Shared` o valor do campo deve ser determinar se a página é carregada em um canal compartilhado e pode responder adequadamente.

> [!NOTE]
> Sempre que um usuário reinicia ou recarrega a área de trabalho do Teams ou o cliente Web, uma nova sessionID é criada, que é controlada pela sessão do Teams, enquanto que, quando um usuário sai dos aplicativos do Teams e o recarrega na plataforma teams, uma nova sessionID de aplicativo é criada, que é controlada pela sessão de aplicativo.

## <a name="handle-theme-change"></a>Manipular alteração de tema

Você pode registrar seu aplicativo para ser informado se o tema for alterado chamando `microsoftTeams.app.registerOnThemeChangeHandler(function(theme) { /* ... */ })`.

O `theme` argumento na função é uma cadeia de caracteres com um valor `default`de , `dark`ou `contrast`.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Criar guias com Cartões Adaptáveis](~/tabs/how-to/build-adaptive-card-tabs.md)

## <a name="see-also"></a>Confira também

* [Diretrizes de design de guia](../../tabs/design/tabs.md)
* [Guias do Teams](~/tabs/what-are-tabs.md)
* [Criar uma guia pessoal](~/tabs/how-to/create-personal-tab.md)
* [Criar uma guia de canal ou grupo](~/tabs/how-to/create-channel-group-tab.md)
* [Usar módulos de tarefas nas guias](~/task-modules-and-cards/task-modules/task-modules-tabs.md)
