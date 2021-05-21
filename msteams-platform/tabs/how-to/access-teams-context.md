---
title: Obter contexto para sua guia
description: Descrever como obter o contexto do usuário para suas guias
localization_priority: Normal
ms.topic: how-to
keywords: Contexto do usuário das guias equipes
ms.openlocfilehash: 0d9224a941ae4f6a5ad125c93d5877ec49b6df28
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566863"
---
# <a name="get-context-for-your-microsoft-teams-tab"></a>Obter contexto para a guia Microsoft Teams

Sua guia deve exigir informações contextuais para exibir conteúdo relevante:

* Informações básicas sobre o usuário, equipe ou empresa.
* Informações de localidade e tema.
* Leia `entityId` o ou `subEntityId` que identifica o que está nesta guia.

## <a name="user-context"></a>Contexto do usuário

O contexto sobre o usuário, a equipe ou a empresa pode ser especialmente útil quando:

* Você cria ou associa recursos em seu aplicativo com o usuário ou a equipe especificado.
* Você inicia um fluxo de autenticação Azure Active Directory ou outro provedor de identidade e não deseja exigir que o usuário insira seu nome de usuário novamente. Para obter mais informações sobre a autenticação em sua guia Microsoft Teams, consulte Autenticar um usuário [em sua guia Microsoft Teams.](~/concepts/authentication/authentication.md)

> [!IMPORTANT]
> Embora essas informações do usuário possam ajudar a fornecer uma experiência tranquila ao usuário, você deve *não* usá-lo como prova de identidade. Por exemplo, um invasor pode carregar sua página em um "navegador ruim" e processar informações ou solicitações prejudiciais.

## <a name="accessing-context"></a>Acessando o contexto

Você pode acessar informações de contexto de duas maneiras:

* Inserir valores de espaço reservado de URL.
* Use o [Microsoft Teams SDK do](/javascript/api/overview/msteams-client)cliente JavaScript .

### <a name="getting-context-by-inserting-url-placeholder-values"></a>Obter contexto inserindo valores de espaço reservado para URL

Usar espaços reservados em sua configuração ou URLs de conteúdo. O Microsoft Teams substitui os espaços reservados pelos valores relevantes ao determinar a configuração real ou o URL do conteúdo. Os marcadores disponíveis incluem todos os campos no objeto [Contexto](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true). Os marcadores de posição comuns incluem o seguinte:

* {entityId}: ID fornecida para o item nesta guia quando a [guia é configurada](~/tabs/how-to/create-tab-pages/configuration-page.md) pela primeira vez. 
* {subEntityId}: ID que você forneceu ao gerar um [link profundo](~/concepts/build-and-test/deep-links.md) para um item específico _dentro de_ esta guia. Isso deve ser usado para restaurar a um estado específico dentro de uma entidade; por exemplo, rolar ou ativar uma parte específica do conteúdo.
* {loginHint}: um valor adequado como uma dica de login para o Azure AD. Geralmente é o nome de login do usuário atual, na página inicial do locatário.
* {userPrincipalName}: nome principal do usuário do usuário atual, no locatário atual.
* {userObjectId}: ID de objeto do Azure AD do usuário atual, no locatário atual.
* {theme}: tema atual da interface do usuário como `default`, `dark`, ou `contrast`.
* {groupId}: ID do Grupo Office 365 no qual a guia reside
* {tid}: ID do locatário do Azure AD do usuário atual.
* {locale}: a localidade atual do usuário formatada como languageId-countryId. Por exemplo, en-us.

>[!NOTE]
>O espaço reservado `{upn}` anterior agora está preterido. Para compatibilidade com versões anteriores, é atualmente um sinônimo para `{loginHint}`.

Por exemplo, suponha que, no manifesto de tabulação, você de definir o atributo como , o usuário inscreveu `configURL` `"https://www.contoso.com/config?name={loginHint}&tenant={tid}&group={groupId}&theme={theme}"` tenha os seguintes atributos:

* Seu nome de usuário é 'user@example.com'.
* A ID do locatário da empresa é 'e2653c-etc'.
* Eles são membros do grupo Office 365 com id '00209384-etc'.
* O usuário definiu seu Teams como "escuro".

Quando eles configuram sua guia, Teams chama a seguinte URL:

`https://www.contoso.com/config?name=user@example.com&tenant=e2653c-etc&group=00209384-etc&theme=dark`

### <a name="getting-context-by-using-the-microsoft-teams-javascript-library"></a>Obter contexto usando a biblioteca JavaScript do Microsoft Teams

Você também pode recuperar as informações listadas acima usando o [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client) chamando `microsoftTeams.getContext(function(context) { /* ... */ })`.

A variável de contexto se parece com o exemplo a seguir:

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
    "groupId": "Guid identifying the current O365 Group ID",
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
    "hostClientType": "The type of host client. Possible values are android, ios, web, desktop, rigel",
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
    "defaultOneNoteSectionId": "The OneNote section ID that is linked to the channel"
}
```

## <a name="retrieving-context-in-private-channels"></a>Recuperando contexto em canais privados

> [!Note]
> Canais privados estão atualmente na visualização do desenvolvedor privado.

Quando sua página de conteúdo é carregada em um canal privado, os dados que você recebe da chamada a `getContext` será ofuscada para proteger a privacidade do canal. Os campos a seguir são alterados quando sua página de conteúdo está em um canal privado. Se sua página fizer uso de qualquer um dos valores abaixo, você precisará verificar o `channelType` para determinar se sua página está carregada em um canal privado e responder de forma adequada.

* `groupId`: Indefinido para canais privados
* `teamId`: De acordo com o threadId do canal privado
* `teamName`: De acordo com o nome do canal privado
* `teamSiteUrl`: De acordo com a URL de um site SharePoint exclusivo para o canal privado
* `teamSitePath`: De acordo com o caminho de um site SharePoint exclusivo para o canal privado
* `teamSiteDomain`: Definir para o domínio de um domínio de site SharePoint exclusivo para o canal privado

> [!Note]
>  teamSiteUrl também funciona bem para canais padrão.

## <a name="theme-change-handling"></a>Tratamento de alteração de tema

Você pode registrar seu aplicativo para ser informado se o tema muda chamando `microsoftTeams.registerOnThemeChangeHandler(function(theme) { /* ... */ })`.

O argumento `theme` na função será uma string com um valor de `default`, `dark`, ou `contrast`.
