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
# <a name="get-context-for-your-microsoft-teams-tab"></a><span data-ttu-id="3947a-104">Obter contexto para a guia Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="3947a-104">Get context for your Microsoft Teams tab</span></span>

<span data-ttu-id="3947a-105">Sua guia deve exigir informações contextuais para exibir conteúdo relevante:</span><span class="sxs-lookup"><span data-stu-id="3947a-105">Your tab must require contextual information to display relevant content:</span></span>

* <span data-ttu-id="3947a-106">Informações básicas sobre o usuário, equipe ou empresa.</span><span class="sxs-lookup"><span data-stu-id="3947a-106">Basic information about the user, team, or company.</span></span>
* <span data-ttu-id="3947a-107">Informações de localidade e tema.</span><span class="sxs-lookup"><span data-stu-id="3947a-107">Locale and theme information.</span></span>
* <span data-ttu-id="3947a-108">Leia `entityId` o ou `subEntityId` que identifica o que está nesta guia.</span><span class="sxs-lookup"><span data-stu-id="3947a-108">Read the `entityId` or `subEntityId` that identifies what is in this tab.</span></span>

## <a name="user-context"></a><span data-ttu-id="3947a-109">Contexto do usuário</span><span class="sxs-lookup"><span data-stu-id="3947a-109">User context</span></span>

<span data-ttu-id="3947a-110">O contexto sobre o usuário, a equipe ou a empresa pode ser especialmente útil quando:</span><span class="sxs-lookup"><span data-stu-id="3947a-110">Context about the user, team or company can be especially useful when:</span></span>

* <span data-ttu-id="3947a-111">Você cria ou associa recursos em seu aplicativo com o usuário ou a equipe especificado.</span><span class="sxs-lookup"><span data-stu-id="3947a-111">You create or associate resources in your app with the specified user or team.</span></span>
* <span data-ttu-id="3947a-112">Você inicia um fluxo de autenticação Azure Active Directory ou outro provedor de identidade e não deseja exigir que o usuário insira seu nome de usuário novamente.</span><span class="sxs-lookup"><span data-stu-id="3947a-112">You initiate an authentication flow against Azure Active Directory or other identity provider, and you don't want to require the user to enter their username again.</span></span> <span data-ttu-id="3947a-113">Para obter mais informações sobre a autenticação em sua guia Microsoft Teams, consulte Autenticar um usuário [em sua guia Microsoft Teams.](~/concepts/authentication/authentication.md)</span><span class="sxs-lookup"><span data-stu-id="3947a-113">For more information on authenticating within your Microsoft Teams tab, see [Authenticate a user in your Microsoft Teams tab](~/concepts/authentication/authentication.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3947a-114">Embora essas informações do usuário possam ajudar a fornecer uma experiência tranquila ao usuário, você deve *não* usá-lo como prova de identidade.</span><span class="sxs-lookup"><span data-stu-id="3947a-114">Although this user information can help provide a smooth user experience, you should *not* use it as proof of identity.</span></span> <span data-ttu-id="3947a-115">Por exemplo, um invasor pode carregar sua página em um "navegador ruim" e processar informações ou solicitações prejudiciais.</span><span class="sxs-lookup"><span data-stu-id="3947a-115">For example, an attacker could load your page in a "bad browser" and render harmful information or requests.</span></span>

## <a name="accessing-context"></a><span data-ttu-id="3947a-116">Acessando o contexto</span><span class="sxs-lookup"><span data-stu-id="3947a-116">Accessing context</span></span>

<span data-ttu-id="3947a-117">Você pode acessar informações de contexto de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="3947a-117">You can access context information in two ways:</span></span>

* <span data-ttu-id="3947a-118">Inserir valores de espaço reservado de URL.</span><span class="sxs-lookup"><span data-stu-id="3947a-118">Insert URL placeholder values.</span></span>
* <span data-ttu-id="3947a-119">Use o [Microsoft Teams SDK do](/javascript/api/overview/msteams-client)cliente JavaScript .</span><span class="sxs-lookup"><span data-stu-id="3947a-119">Use the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client).</span></span>

### <a name="getting-context-by-inserting-url-placeholder-values"></a><span data-ttu-id="3947a-120">Obter contexto inserindo valores de espaço reservado para URL</span><span class="sxs-lookup"><span data-stu-id="3947a-120">Getting context by inserting URL placeholder values</span></span>

<span data-ttu-id="3947a-121">Usar espaços reservados em sua configuração ou URLs de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="3947a-121">Use placeholders in your configuration or content URLs.</span></span> <span data-ttu-id="3947a-122">O Microsoft Teams substitui os espaços reservados pelos valores relevantes ao determinar a configuração real ou o URL do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="3947a-122">Microsoft Teams replaces the placeholders with the relevant values when determining the actual configuration or content URL.</span></span> <span data-ttu-id="3947a-123">Os marcadores disponíveis incluem todos os campos no objeto [Contexto](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="3947a-123">The available placeholders include all fields on the [Context](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true) object.</span></span> <span data-ttu-id="3947a-124">Os marcadores de posição comuns incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="3947a-124">Common placeholders include the following:</span></span>

* <span data-ttu-id="3947a-125">{entityId}: ID fornecida para o item nesta guia quando a [guia é configurada](~/tabs/how-to/create-tab-pages/configuration-page.md) pela primeira vez. </span><span class="sxs-lookup"><span data-stu-id="3947a-125">{entityId}: The ID you supplied for the item in this tab when first [configuring the tab](~/tabs/how-to/create-tab-pages/configuration-page.md).</span></span>
* <span data-ttu-id="3947a-126">{subEntityId}: ID que você forneceu ao gerar um [link profundo](~/concepts/build-and-test/deep-links.md) para um item específico _dentro de_ esta guia. Isso deve ser usado para restaurar a um estado específico dentro de uma entidade; por exemplo, rolar ou ativar uma parte específica do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="3947a-126">{subEntityId}: The ID you supplied when generating a [deep link](~/concepts/build-and-test/deep-links.md) for a specific item _within_ this tab. This should be used to restore to a specific state within an entity; for example, scrolling to or activating a specific piece of content.</span></span>
* <span data-ttu-id="3947a-127">{loginHint}: um valor adequado como uma dica de login para o Azure AD. Geralmente é o nome de login do usuário atual, na página inicial do locatário.</span><span class="sxs-lookup"><span data-stu-id="3947a-127">{loginHint}: A value suitable as a login hint for Azure AD.This is usually the login name of the current user, in their home tenant.</span></span>
* <span data-ttu-id="3947a-128">{userPrincipalName}: nome principal do usuário do usuário atual, no locatário atual.</span><span class="sxs-lookup"><span data-stu-id="3947a-128">{userPrincipalName}: The User Principal Name of the current user, in the current tenant.</span></span>
* <span data-ttu-id="3947a-129">{userObjectId}: ID de objeto do Azure AD do usuário atual, no locatário atual.</span><span class="sxs-lookup"><span data-stu-id="3947a-129">{userObjectId}: The Azure AD object ID of the current user, in the current tenant.</span></span>
* <span data-ttu-id="3947a-130">{theme}: tema atual da interface do usuário como `default`, `dark`, ou `contrast`.</span><span class="sxs-lookup"><span data-stu-id="3947a-130">{theme}: The current UI theme such as `default`, `dark`, or `contrast`.</span></span>
* <span data-ttu-id="3947a-131">{groupId}: ID do Grupo Office 365 no qual a guia reside</span><span class="sxs-lookup"><span data-stu-id="3947a-131">{groupId}: The ID of the Office 365 Group in which the tab resides.</span></span>
* <span data-ttu-id="3947a-132">{tid}: ID do locatário do Azure AD do usuário atual.</span><span class="sxs-lookup"><span data-stu-id="3947a-132">{tid}: The Azure AD tenant ID of the current user.</span></span>
* <span data-ttu-id="3947a-133">{locale}: a localidade atual do usuário formatada como languageId-countryId.</span><span class="sxs-lookup"><span data-stu-id="3947a-133">{locale}: The current locale of the user formatted as languageId-countryId.</span></span> <span data-ttu-id="3947a-134">Por exemplo, en-us.</span><span class="sxs-lookup"><span data-stu-id="3947a-134">For example, en-us.</span></span>

>[!NOTE]
><span data-ttu-id="3947a-135">O espaço reservado `{upn}` anterior agora está preterido.</span><span class="sxs-lookup"><span data-stu-id="3947a-135">The previous `{upn}` placeholder is now deprecated.</span></span> <span data-ttu-id="3947a-136">Para compatibilidade com versões anteriores, é atualmente um sinônimo para `{loginHint}`.</span><span class="sxs-lookup"><span data-stu-id="3947a-136">For backward compatibility, it is currently a synonym for `{loginHint}`.</span></span>

<span data-ttu-id="3947a-137">Por exemplo, suponha que, no manifesto de tabulação, você de definir o atributo como , o usuário inscreveu `configURL` `"https://www.contoso.com/config?name={loginHint}&tenant={tid}&group={groupId}&theme={theme}"` tenha os seguintes atributos:</span><span class="sxs-lookup"><span data-stu-id="3947a-137">For example, suppose in your tab manifest you set the `configURL` attribute to `"https://www.contoso.com/config?name={loginHint}&tenant={tid}&group={groupId}&theme={theme}"`, the signed-in user has the following attributes:</span></span>

* <span data-ttu-id="3947a-138">Seu nome de usuário é 'user@example.com'.</span><span class="sxs-lookup"><span data-stu-id="3947a-138">Their username is 'user@example.com'.</span></span>
* <span data-ttu-id="3947a-139">A ID do locatário da empresa é 'e2653c-etc'.</span><span class="sxs-lookup"><span data-stu-id="3947a-139">Their company tenant ID is 'e2653c-etc'.</span></span>
* <span data-ttu-id="3947a-140">Eles são membros do grupo Office 365 com id '00209384-etc'.</span><span class="sxs-lookup"><span data-stu-id="3947a-140">They are a member of the Office 365 group with id '00209384-etc'.</span></span>
* <span data-ttu-id="3947a-141">O usuário definiu seu Teams como "escuro".</span><span class="sxs-lookup"><span data-stu-id="3947a-141">The user has set their Teams theme to 'dark'.</span></span>

<span data-ttu-id="3947a-142">Quando eles configuram sua guia, Teams chama a seguinte URL:</span><span class="sxs-lookup"><span data-stu-id="3947a-142">When they configure your tab, Teams calls the following URL:</span></span>

`https://www.contoso.com/config?name=user@example.com&tenant=e2653c-etc&group=00209384-etc&theme=dark`

### <a name="getting-context-by-using-the-microsoft-teams-javascript-library"></a><span data-ttu-id="3947a-143">Obter contexto usando a biblioteca JavaScript do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="3947a-143">Getting context by using the Microsoft Teams JavaScript library</span></span>

<span data-ttu-id="3947a-144">Você também pode recuperar as informações listadas acima usando o [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client) chamando `microsoftTeams.getContext(function(context) { /* ... */ })`.</span><span class="sxs-lookup"><span data-stu-id="3947a-144">You can also retrieve the information listed above using the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client) by calling `microsoftTeams.getContext(function(context) { /* ... */ })`.</span></span>

<span data-ttu-id="3947a-145">A variável de contexto se parece com o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="3947a-145">The context variable looks like the following example:</span></span>

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

## <a name="retrieving-context-in-private-channels"></a><span data-ttu-id="3947a-146">Recuperando contexto em canais privados</span><span class="sxs-lookup"><span data-stu-id="3947a-146">Retrieving context in private channels</span></span>

> [!Note]
> <span data-ttu-id="3947a-147">Canais privados estão atualmente na visualização do desenvolvedor privado.</span><span class="sxs-lookup"><span data-stu-id="3947a-147">Private channels are currently in private developer preview.</span></span>

<span data-ttu-id="3947a-148">Quando sua página de conteúdo é carregada em um canal privado, os dados que você recebe da chamada a `getContext` será ofuscada para proteger a privacidade do canal.</span><span class="sxs-lookup"><span data-stu-id="3947a-148">When your content page is loaded in a private channel, the data you receive from the `getContext` call will be obfuscated to protect the privacy of the channel.</span></span> <span data-ttu-id="3947a-149">Os campos a seguir são alterados quando sua página de conteúdo está em um canal privado.</span><span class="sxs-lookup"><span data-stu-id="3947a-149">The following fields are changed when your content page is in a private channel.</span></span> <span data-ttu-id="3947a-150">Se sua página fizer uso de qualquer um dos valores abaixo, você precisará verificar o `channelType` para determinar se sua página está carregada em um canal privado e responder de forma adequada.</span><span class="sxs-lookup"><span data-stu-id="3947a-150">If your page makes use of any of the values below, you'll need to check the `channelType` field to determine if your page is loaded in a private channel, and respond appropriately.</span></span>

* <span data-ttu-id="3947a-151">`groupId`: Indefinido para canais privados</span><span class="sxs-lookup"><span data-stu-id="3947a-151">`groupId`: Undefined for private channels</span></span>
* <span data-ttu-id="3947a-152">`teamId`: De acordo com o threadId do canal privado</span><span class="sxs-lookup"><span data-stu-id="3947a-152">`teamId`: Set to the threadId of the private channel</span></span>
* <span data-ttu-id="3947a-153">`teamName`: De acordo com o nome do canal privado</span><span class="sxs-lookup"><span data-stu-id="3947a-153">`teamName`: Set to the name of the private channel</span></span>
* <span data-ttu-id="3947a-154">`teamSiteUrl`: De acordo com a URL de um site SharePoint exclusivo para o canal privado</span><span class="sxs-lookup"><span data-stu-id="3947a-154">`teamSiteUrl`: Set to the URL of a distinct, unique SharePoint site for the private channel</span></span>
* <span data-ttu-id="3947a-155">`teamSitePath`: De acordo com o caminho de um site SharePoint exclusivo para o canal privado</span><span class="sxs-lookup"><span data-stu-id="3947a-155">`teamSitePath`: Set to the path of a distinct, unique SharePoint site for the private channel</span></span>
* <span data-ttu-id="3947a-156">`teamSiteDomain`: Definir para o domínio de um domínio de site SharePoint exclusivo para o canal privado</span><span class="sxs-lookup"><span data-stu-id="3947a-156">`teamSiteDomain`: Set to the domain of a distinct, unique SharePoint site domain for the private channel</span></span>

> [!Note]
>  <span data-ttu-id="3947a-157">teamSiteUrl também funciona bem para canais padrão.</span><span class="sxs-lookup"><span data-stu-id="3947a-157">teamSiteUrl works well for standard channels also.</span></span>

## <a name="theme-change-handling"></a><span data-ttu-id="3947a-158">Tratamento de alteração de tema</span><span class="sxs-lookup"><span data-stu-id="3947a-158">Theme change handling</span></span>

<span data-ttu-id="3947a-159">Você pode registrar seu aplicativo para ser informado se o tema muda chamando `microsoftTeams.registerOnThemeChangeHandler(function(theme) { /* ... */ })`.</span><span class="sxs-lookup"><span data-stu-id="3947a-159">You can register your app to be told if the theme changes by calling `microsoftTeams.registerOnThemeChangeHandler(function(theme) { /* ... */ })`.</span></span>

<span data-ttu-id="3947a-160">O argumento `theme` na função será uma string com um valor de `default`, `dark`, ou `contrast`.</span><span class="sxs-lookup"><span data-stu-id="3947a-160">The `theme` argument in the function will be a string with a value of `default`, `dark`, or `contrast`.</span></span>
