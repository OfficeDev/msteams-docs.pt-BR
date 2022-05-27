---
title: Obter contexto para sua guia
description: Descrever como obter o contexto do usuário para suas guias
ms.localizationpriority: medium
ms.topic: how-to
keywords: Contexto do usuário das guias equipes
ms.openlocfilehash: 0539f1dc3f31a2b068e80b4ff12b93a26e09b766
ms.sourcegitcommit: eeaa8cbb10b9dfa97e9c8e169e9940ddfe683a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2022
ms.locfileid: "65757357"
---
# <a name="get-context-for-your-tab"></a>Obtenha contexto para sua guia

Sua guia requer informações contextuais para exibir conteúdo relevante:

* Informações básicas sobre o usuário, a equipe ou a empresa.
* Informações de localidade e tema.
* Leia o `entityId` ou `subEntityId` que identifica o que está nessa guia.

[!INCLUDE [sdk-include](~/includes/sdk-include.md)]

## <a name="user-context"></a>Contexto do usuário

O contexto sobre o usuário, a equipe ou a empresa pode ser especialmente útil quando:

* Você cria ou associa recursos em seu aplicativo ao usuário ou à equipe especificado.
* Você inicia um fluxo de autenticação Microsoft Azure Active Directory (Azure AD) ou outro provedor de identidade e não exige que o usuário insira seu nome de usuário novamente.

Para obter mais informações, [consulte autenticar um usuário em seu Microsoft Teams](~/concepts/authentication/authentication.md).

> [!IMPORTANT]
> Embora essas informações do usuário possam ajudar a fornecer uma experiência de usuário suave, você não deve usá-la como prova de identidade.  Por exemplo, um invasor pode carregar sua página em um navegador e renderizar informações ou solicitações prejudiciais.

## <a name="access-context-information"></a>Acessar informações de contexto

Você pode acessar informações de contexto de duas maneiras:

* Inserir valores de espaço reservado de URL.
* Use o [Microsoft Teams SDK do cliente JavaScript](/javascript/api/overview/msteams-client).

### <a name="get-context-by-inserting-url-placeholder-values"></a>Obter contexto inserindo valores de espaço reservado de URL

Usar espaços reservados em sua configuração ou URLs de conteúdo. O Microsoft Teams substitui os espaços reservados pelos valores relevantes ao determinar a configuração real ou o URL do conteúdo. Os espaços reservados disponíveis incluem todos os campos no objeto [de](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-1.12.1&preserve-view=true) contexto. Os marcadores de posição comuns incluem o seguinte:

* {entityId}: ID fornecida para o item nesta guia quando a [guia é configurada](~/tabs/how-to/create-tab-pages/configuration-page.md) pela primeira vez. 
* {subEntityId}: a ID que você forneceu ao gerar um [link](~/concepts/build-and-test/deep-links.md) profundo para um item específico nessa guia. Isso deve ser usado para restaurar para um estado específico dentro de uma entidade; por exemplo, rolar para ou ativar uma parte específica do conteúdo.
* {loginHint}: um valor adequado como uma dica de logon para Azure AD. Geralmente, esse é o nome de logon do usuário atual em seu locatário inicial.
* {userPrincipalName}: o Nome UPN do usuário atual no locatário atual.
* {userObjectId}: a ID Azure AD objeto do usuário atual no locatário atual.
* {theme}: o tema da interface do usuário atual, como `default`, `dark`ou `contrast`.
* {groupId}: a ID do grupo Office 365 no qual a guia reside.
* {tid}: ID do locatário do Azure AD do usuário atual.
* {locale}: a localidade atual do usuário formatada como languageId-countryId(en-us).

> [!NOTE]
> O espaço reservado `{upn}` anterior agora está preterido. Para compatibilidade com versões anteriores, é atualmente um sinônimo para `{loginHint}`.

Por exemplo, no manifesto da guia para o qual você definiu `configURL` `"https://www.contoso.com/config?name={loginHint}&tenant={tid}&group={groupId}&theme={theme}"`o atributo, o usuário conectado tem os seguintes atributos:

* O nome de usuário é **user@example.com**.
* A ID do locatário da empresa **é e2653c-etc**.
* Eles são membros do grupo Office 365 com a ID **00209384-etc**.
* O usuário definiu o tema Teams como **escuro**.

Quando eles configuram a guia, Teams chama a seguinte URL:

`https://www.contoso.com/config?name=user@example.com&tenant=e2653c-etc&group=00209384-etc&theme=dark`

### <a name="get-context-by-using-the-microsoft-teams-javascript-library"></a>Obter contexto usando a biblioteca Microsoft Teams JavaScript

git-issue-clarify-the-full-set-of-values-any-context-object-property-can-take Você também pode recuperar as informações listadas acima usando o [SDK](/javascript/api/overview/msteams-client) `microsoftTeams.getContext(function(context) { /* ... */ })`do cliente JavaScript do Microsoft Teams chamando .

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
    "userLicenseType": "The license type for the current user. Possible values are E1, E3, and E5 enterprise plans",
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

Você também pode recuperar as informações listadas acima usando [Microsoft Teams SDK do cliente JavaScript](/javascript/api/overview/msteams-client) chamando a `app.getContext()` função. Para obter informações adicionais, consulte as propriedades da [interface de contexto](/javascript/api/@microsoft/teams-js/app.context?view=msteams-client-js-latest&preserve-view=true).


## <a name="retrieve-context-in-private-channels"></a>Recuperar contexto em canais privados

Quando sua página de conteúdo é carregada em um canal privado, `getContext` os dados recebidos da chamada são ofuscados para proteger a privacidade do canal.

Os campos a seguir são alterados quando sua página de conteúdo está em um canal privado:

* `groupId`: indefinido para canais privados
* `teamId`: definido como o threadId do canal privado
* `teamName`: definido como o nome do canal privado
* `teamSiteUrl`: defina como a URL de um site SharePoint distinto para o canal privado
* `teamSitePath`: defina como o caminho de um site SharePoint distinto para o canal privado
* `teamSiteDomain`: definido como o domínio de um domínio de site SharePoint exclusivo para o canal privado

Se sua página usa qualquer um desses valores, `channelType` `Private` o valor do campo deve ser determinar se sua página é carregada em um canal privado e pode responder adequadamente.

## <a name="retrieve-context-in-microsoft-teams-connect-shared-channels"></a>Recuperar contexto em Conexão Microsoft Teams canais compartilhados

> [!NOTE]
> Atualmente, os Conexão Microsoft Teams compartilhados estão apenas na versão [prévia do](../../resources/dev-preview/developer-preview-intro.md) desenvolvedor.

Quando sua página de conteúdo é carregada em um canal Conexão Microsoft Teams compartilhado, `getContext` os dados recebidos da chamada são alterados devido à lista exclusiva de usuários em canais compartilhados.

Os campos a seguir são alterados quando sua página de conteúdo está em um canal compartilhado:

* `groupId`: indefinido para canais compartilhados.
* `teamId`: definido como o `threadId` da equipe, o canal é compartilhado para o usuário atual. Se o usuário tiver acesso a várias equipes, ele `teamId` será definido como a equipe que hospeda (cria) o canal compartilhado.
* `teamName`: definido como o nome da equipe, o canal é compartilhado para o usuário atual. Se o usuário tiver acesso a várias equipes, ele `teamName` será definido como a equipe que hospeda (cria) o canal compartilhado.
* `teamSiteUrl`: defina como a URL de um site SharePoint distinto para o canal compartilhado.
* `teamSitePath`: defina como o caminho de um site SharePoint exclusivo e distinto para o canal compartilhado.
* `teamSiteDomain`: defina como o domínio de um domínio de site SharePoint exclusivo para o canal compartilhado.

Além dessas alterações de campo, há dois novos campos disponíveis para canais compartilhados:

* `hostTeamGroupId`: defina como o `groupId` associado à equipe de hospedagem ou à equipe que criou o canal compartilhado. A propriedade pode fazer com que as chamadas API do Graph Microsoft recuperem a associação do canal compartilhado.
* `hostTeamTenantId`: defina como o `tenantId` associado à equipe de hospedagem ou à equipe que criou o canal compartilhado. A propriedade pode ser referenciada cruzadamente com a ID `tid` `getContext` de locatário do usuário atual encontrada no campo para determinar se o usuário é interno ou externo ao locatário da equipe de hospedagem.

Se sua página usa qualquer um desses valores, `channelType` `Shared` o valor do campo deve ser determinar se a página é carregada em um canal compartilhado e pode responder adequadamente.

> [!NOTE]
> Sempre que um usuário reinicia ou recarrega o cliente web ou da área de trabalho do Teams, uma nova sessionID é criada, que é controlada por uma sessão do Teams, enquanto que, quando um usuário sai dos aplicativos do Teams e o recarrega na plataforma Teams, uma nova sessionID de aplicativo é criada, que é controlada pela sessão de aplicativo.

## <a name="handle-theme-change"></a>Manipular alteração de tema

Você pode registrar seu aplicativo para ser informado se o tema for alterado chamando `app.registerOnThemeChangeHandler(function(theme) { /* ... */ })`.

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
