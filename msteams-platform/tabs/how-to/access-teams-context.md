---
title: Obter contexto para a guia
description: Descreve como obter o contexto de usuário para suas guias
keywords: contexto de usuário de guias do teams
ms.openlocfilehash: 01919999e38d6b659f014b0f05b76d3f332db9ab
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672462"
---
# <a name="get-context-for-your-microsoft-teams-tab"></a>Obter contexto para a guia do Microsoft Teams

Sua guia pode exigir informações contextuais para exibir conteúdo relevante.

* Sua guia pode precisar de informações básicas sobre o usuário, a equipe ou a empresa.
* Sua guia pode precisar de informações de localidade e tema.
* Sua guia pode precisar ler o `entityId` ou `subEntityId` que identifica o que está nesta guia.

## <a name="user-context"></a>Contexto de usuário

O contexto sobre o usuário, a equipe ou a empresa pode ser especialmente útil quando

* Você precisa criar ou associar recursos em seu aplicativo com o usuário ou equipe especificado.
* Você deseja iniciar um fluxo de autenticação no Azure Active Directory ou outro provedor de identidade e não quer exigir que o usuário insira o nome de usuário novamente. (Para obter mais informações sobre como autenticar na guia Microsoft Teams, confira [autenticar um usuário em sua guia do Microsoft Teams](~/concepts/authentication/authentication.md).)

> [!IMPORTANT]
> Embora essas informações do usuário possam ajudar a fornecer uma experiência de usuário tranqüila, você *não* deve usá-la como prova de identidade. Por exemplo, um invasor pode carregar sua página em um "navegador inválido" e fornecer qualquer informação que desejar.

## <a name="accessing-context"></a>Contexto de acesso

Você pode acessar informações de contexto de duas maneiras:

* Inserir valores de espaço reservado de URL
* Usar o [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client)

### <a name="getting-context-by-inserting-url-placeholder-values"></a>Obtendo contexto inserindo valores de espaço reservado de URL

Use espaços reservados em suas configurações ou URLs de conteúdo. O Microsoft Teams substitui os espaços reservados pelos valores relevantes ao determinar a configuração real ou a URL de conteúdo para navegar. Os espaços reservados disponíveis incluem todos os campos no objeto [Context](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest) . Os espaços reservados comuns incluem o seguinte:

* {EntityId}: a ID que você forneceu para o item nesta guia quando [configura a guia](~/tabs/how-to/create-tab-pages/configuration-page.md)pela primeira vez.
* {subentityid}: a ID que você forneceu ao gerar um [link profundo](~/concepts/build-and-test/deep-links.md) para um item específico _dentro_ dessa guia. Isso deve ser usado para restaurar um estado específico dentro de uma entidade; por exemplo, rolar ou ativar uma parte específica do conteúdo.
* {loginHint}: um valor adequado como uma dica de logon para o Azure AD. Em geral, esse é o nome de logon do usuário atual em seu locatário inicial.
* {userPrincipalName}: o nome principal de usuário do usuário atual, no locatário atual.
* {userobjectid}: a ID de objeto do Azure AD do usuário atual, no locatário atual.
* {Theme}: o tema atual da interface do `default`usuário `dark`, como `contrast`, ou.
* {GroupId}: a ID do grupo do Office 365 em que a guia reside.
* {tid}: a ID do locatário do Azure AD do usuário atual.
* {locale}: a localidade atual do usuário formatada como LanguageID-countryId (por exemplo, en-US).

>[!NOTE]
>O espaço `{upn}` reservado anterior agora é preterido. Para compatibilidade com versões anteriores, no momento é sinônimo `{loginHint}`de.

Por exemplo, suponha que, em seu manifesto de guia `configURL` , você defina o atributo como

`"https://www.contoso.com/config?name={loginHint}&tenant={tid}&group={groupId}&theme={theme}"`

E o usuário conectado tem os seguintes atributos:

* O nome de usuário é ' user@example.com '
* A ID de locatário da empresa é ' e2653c-etc '
* Eles são membros do grupo do Office 365 com a ID ' 00209384-etc '
* O usuário definiu o tema da equipe como ' escuro '

Ao configurar sua guia, o Teams chama esta URL:

`https://www.contoso.com/config?name=user@example.com&tenant=e2653c-etc&group=00209384-etc&theme=dark`

### <a name="getting-context-by-using-the-microsoft-teams-javascript-library"></a>Obtendo contexto usando a biblioteca JavaScript do Microsoft Teams

Você também pode recuperar as informações listadas acima usando o [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client) chamando `microsoftTeams.getContext(function(context) { /* ... */ })`.

A variável de contexto se parecerá com o exemplo a seguir.

```json
{
    "teamId": "The Microsoft Teams ID in the format 19:[id]@thread.skype",
    "teamName": "The name of the current team",
    "channelId": "The channel ID in the format 19:[id]@thread.skype",
    "channelName": "The name of the current channel",
    "chatId": "The chat ID in the in the format 19:[id]@thread.skype",
    "locale": "The current locale of the user formatted as languageId-countryId (for example, en-us)",
    "entityId": "The developer-defined unique ID for the entity this content points to",
    "subEntityId": "The developer-defined unique ID for the sub-entity this content points to",
    "loginHint": "A value suitable as a login hint for Azure AD. This is usually the login name of the current user, in their home tenant",
    "userPrincipalName": "The User Principal Name of the current user, in the current tenant",
    "userObjectId": "The Azure AD object id of the current user, in the current tenant",
    "tid": "The Azure AD tenant ID of the current user",
    "groupId": "Guid identifying the current O365 Group ID",
    "theme": "The current UI theme: default | dark | contrast",
    "isFullScreen": "Indicates whether the tab is in full-screen mode",
    "userLicenseType": "Indicates the user licence type in the given SKU (for example, student or teacher)",
    "tenantSKU": "Indicates the SKU category of the tenant (for example, EDU)",
    "channelType": "microsoftTeams.ChannelType.Private | microsoftTeams.ChannelType.Regular"
}
```

## <a name="retrieving-context-in-private-channels"></a>Recuperando contexto em canais privados

> [!Note]
> Os canais privados estão atualmente na visualização do desenvolvedor privado.

Quando a página de conteúdo é carregada em um canal privado, os dados recebidos da `getContext` chamada serão ofuscados para proteger a privacidade do canal. Os campos a seguir são alterados quando a página de conteúdo está em um canal privado. Se a página utiliza qualquer um dos valores abaixo, você precisará verificar o campo para determinar `channelType` se a página está carregada em um canal privado e responder de forma adequada.

* `groupId`-Undefined para canais privados
* `teamId`-Definir o threadId do canal privado
* `teamName`-Definir o nome do canal privado
* `teamSiteUrl`-Definir como a URL de um site distinto exclusivo do SharePoint para o canal privado
* `teamSitePath`-Definir como o caminho de um site exclusivo do SharePoint distinto para o canal privado
* `teamSiteDomain`-Definir para o domínio de um domínio de site do SharePoint distinto e exclusivo para o canal privado

## <a name="theme-change-handling"></a>Tratamento de alterações de temas

Você pode registrar seu aplicativo para ser informado se o tema for alterado por `microsoftTeams.registerOnThemeChangeHandler(function(theme) { /* ... */ })`chamada.

O `theme` argumento na função será uma cadeia de caracteres com um valor de `default`, `dark`ou `contrast`.