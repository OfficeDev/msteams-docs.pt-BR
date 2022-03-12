---
title: Obter contexto para sua guia
description: Descrever como obter o contexto do usuário para suas guias
ms.localizationpriority: medium
ms.topic: how-to
keywords: Contexto do usuário das guias equipes
ms.openlocfilehash: b991a9703faedd3b849287abd5aef2d42e1baf9e
ms.sourcegitcommit: 8a0ffd21c800eecfcd6d1b5c4abd8c107fcf3d33
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2022
ms.locfileid: "63453681"
---
# <a name="get-context-for-your-tab"></a>Obtenha contexto para sua guia

Sua guia requer informações contextuais para exibir conteúdo relevante:

* Informações básicas sobre o usuário, equipe ou empresa.
* Informações de localidade e tema.
* Leia o `entityId` ou `subEntityId` que identifica o que está nesta guia.

## <a name="user-context"></a>Contexto do usuário

O contexto sobre o usuário, a equipe ou a empresa pode ser especialmente útil quando:

* Você cria ou associa recursos em seu aplicativo com o usuário ou a equipe especificado.
* Você inicia um fluxo de autenticação do Microsoft Azure Active Directory (Azure AD) ou de outro provedor de identidade e não exige que o usuário insira seu nome de usuário novamente.

Para obter mais informações, [consulte authenticate a user in your Microsoft Teams](~/concepts/authentication/authentication.md).

> [!IMPORTANT]
> Embora essas informações do usuário possam ajudar a fornecer uma experiência de usuário suave, você não deve usá-la como prova de identidade.  Por exemplo, um invasor pode carregar sua página em um navegador e renderizar informações ou solicitações prejudiciais.

## <a name="access-context-information"></a>Informações de contexto de acesso

Você pode acessar informações de contexto de duas maneiras:

* Inserir valores de espaço reservado de URL.
* Use o [Microsoft Teams SDK do cliente JavaScript](/javascript/api/overview/msteams-client).

### <a name="get-context-by-inserting-url-placeholder-values"></a>Obter contexto inserindo valores de espaço reservado de URL

Usar espaços reservados em sua configuração ou URLs de conteúdo. O Microsoft Teams substitui os espaços reservados pelos valores relevantes ao determinar a configuração real ou o URL do conteúdo. Os espaço reservados disponíveis incluem todos os campos no [objeto de](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true) contexto. Os marcadores de posição comuns incluem o seguinte:

* {entityId}: ID fornecida para o item nesta guia quando a [guia é configurada](~/tabs/how-to/create-tab-pages/configuration-page.md) pela primeira vez. 
* {subEntityId}: A ID fornecida ao gerar um [link profundo](~/concepts/build-and-test/deep-links.md) para um item específico nesta guia. Isso deve ser usado para restaurar para um estado específico dentro de uma entidade; por exemplo, rolar para ou ativar uma parte específica do conteúdo.
* {loginHint}: Um valor adequado como uma dica de logon para o Azure AD. Geralmente, esse é o nome de logon do usuário atual em seu locatário.
* {userPrincipalName}: o Nome principal do usuário atual no locatário atual.
* {userObjectId}: A ID do objeto do Azure AD do usuário atual no locatário atual.
* {theme}: O tema atual da interface do usuário (UI), como `default`, `dark`ou `contrast`.
* {groupId}: A ID do grupo Office 365 no qual a guia reside.
* {tid}: ID do locatário do Azure AD do usuário atual.
* {locale}: a localidade atual do usuário formatada como languageId-countryId(en-us).

> [!NOTE]
> O espaço reservado `{upn}` anterior agora está preterido. Para compatibilidade com versões anteriores, é atualmente um sinônimo para `{loginHint}`.

Por exemplo, em seu manifesto de tabulação, você definiu o `configURL` atributo como `"https://www.contoso.com/config?name={loginHint}&tenant={tid}&group={groupId}&theme={theme}"`, o usuário in-lo como , tem os seguintes atributos:

* Seu nome de usuário **é user@example.com**.
* A ID do locatário da empresa é **e2653c-etc**.
* Eles são membros do grupo Office 365 com id **00209384-etc**.
* O usuário definiu seu Teams como **escuro**.

Quando eles configuram a guia, Teams chama a seguinte URL:

`https://www.contoso.com/config?name=user@example.com&tenant=e2653c-etc&group=00209384-etc&theme=dark`

### <a name="get-context-by-using-the-microsoft-teams-javascript-library"></a>Obter contexto usando a biblioteca Microsoft Teams JavaScript

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

## <a name="retrieve-context-in-private-channels"></a>Recuperar contexto em canais privados

Quando sua página de conteúdo é carregada em um canal privado, `getContext` os dados recebidos da chamada são ofuscados para proteger a privacidade do canal.

Os campos a seguir são alterados quando sua página de conteúdo está em um canal privado:

* `groupId`: Indefinido para canais privados
* `teamId`: De acordo com o threadId do canal privado
* `teamName`: De acordo com o nome do canal privado
* `teamSiteUrl`: De acordo com a URL de um site SharePoint exclusivo para o canal privado
* `teamSitePath`: De acordo com o caminho de um site SharePoint exclusivo para o canal privado
* `teamSiteDomain`: De acordo com o domínio de um domínio de site SharePoint exclusivo para o canal privado

Se sua página fizer uso de qualquer um desses valores, `channelType` `Private` o valor do campo deverá ser para determinar se sua página é carregada em um canal privado e pode responder adequadamente.

## <a name="retrieve-context-in-microsoft-teams-connect-shared-channels"></a>Recuperar contexto em Microsoft Teams Conexão canais compartilhados

> [!NOTE]
> Atualmente, Microsoft Teams Conexão canais compartilhados estão apenas na [visualização do](../../resources/dev-preview/developer-preview-intro.md) desenvolvedor.

Quando sua página de conteúdo é carregada em um canal Microsoft Teams Conexão compartilhado, `getContext` os dados recebidos da chamada são alterados devido à lista exclusiva de usuários em canais compartilhados.

Os campos a seguir são alterados quando sua página de conteúdo está em um canal compartilhado:

* `groupId`: Não definido para canais compartilhados.
* `teamId`: De acordo com a `threadId` equipe, o canal é compartilhado para o usuário atual. Se o usuário tiver acesso a várias equipes, o `teamId` será definido como a equipe que hospeda (cria) o canal compartilhado.
* `teamName`: De acordo com o nome da equipe, o canal é compartilhado para o usuário atual. Se o usuário tiver acesso a várias equipes, o `teamName` será definido como a equipe que hospeda (cria) o canal compartilhado.
* `teamSiteUrl`: De acordo com a URL de um site SharePoint exclusivo para o canal compartilhado.
* `teamSitePath`: De acordo com o caminho de um site SharePoint exclusivo para o canal compartilhado.
* `teamSiteDomain`: De acordo com o domínio de um domínio de site SharePoint exclusivo para o canal compartilhado.

Além dessas alterações de campo, há dois novos campos disponíveis para canais compartilhados:

* `hostTeamGroupId`: De acordo com o `groupId` associado à equipe de hospedagem ou à equipe que criou o canal compartilhado. A propriedade pode fazer com que Graph chamadas de API da Microsoft recuperem a associação do canal compartilhado.
* `hostTeamTenantId`: De acordo com o `tenantId` associado à equipe de hospedagem ou à equipe que criou o canal compartilhado. A propriedade pode ser referenciada com a ID `tid` `getContext` de locatário do usuário atual encontrada no campo de para determinar se o usuário é interno ou externo ao locatário da equipe de hospedagem.

Se sua página fizer uso de qualquer um desses valores, `channelType` `Shared` o valor do campo deverá ser para determinar se sua página é carregada em um canal compartilhado e pode responder adequadamente.

## <a name="handle-theme-change"></a>Manipular a alteração de tema

Você pode registrar seu aplicativo para ser informado se o tema mudar chamando `microsoftTeams.registerOnThemeChangeHandler(function(theme) { /* ... */ })`.

O `theme` argumento na função é uma cadeia de caracteres com um valor `default`de , `dark`ou `contrast`.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Criar guias com Cartões Adaptáveis](~/tabs/how-to/build-adaptive-card-tabs.md)

## <a name="see-also"></a>Confira também

* [Diretrizes de design de tabulação](../../tabs/design/tabs.md)
* [Teams guias](~/tabs/what-are-tabs.md)
* [Criar uma guia pessoal](~/tabs/how-to/create-personal-tab.md)
* [Criar um canal ou uma guia de grupo](~/tabs/how-to/create-channel-group-tab.md)
* [Usar módulos de tarefas nas guias](~/task-modules-and-cards/task-modules/task-modules-tabs.md)
