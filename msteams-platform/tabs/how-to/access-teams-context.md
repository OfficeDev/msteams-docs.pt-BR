---
title: Obter contexto para sua guia
description: Descrever como obter o contexto do usuário para suas guias
localization_priority: Normal
ms.topic: how-to
keywords: Contexto do usuário das guias equipes
ms.openlocfilehash: 8c91cf5a65f13d9f58f6ae8aa2678266c37338c8
ms.sourcegitcommit: 85a52119df6c4cb4536572e6d2e7407f0e5e8a23
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2021
ms.locfileid: "53179724"
---
# <a name="get-context-for-your-tab"></a><span data-ttu-id="f0d78-104">Obtenha contexto para sua guia</span><span class="sxs-lookup"><span data-stu-id="f0d78-104">Get context for your tab</span></span>

<span data-ttu-id="f0d78-105">Sua guia requer informações contextuais para exibir conteúdo relevante:</span><span class="sxs-lookup"><span data-stu-id="f0d78-105">Your tab requires contextual information to display relevant content:</span></span>

* <span data-ttu-id="f0d78-106">Informações básicas sobre o usuário, equipe ou empresa.</span><span class="sxs-lookup"><span data-stu-id="f0d78-106">Basic information about the user, team, or company.</span></span>
* <span data-ttu-id="f0d78-107">Informações de localidade e tema.</span><span class="sxs-lookup"><span data-stu-id="f0d78-107">Locale and theme information.</span></span>
* <span data-ttu-id="f0d78-108">Leia `entityId` o ou `subEntityId` que identifica o que está nesta guia.</span><span class="sxs-lookup"><span data-stu-id="f0d78-108">Read the `entityId` or `subEntityId` that identifies what is in this tab.</span></span>

## <a name="user-context"></a><span data-ttu-id="f0d78-109">Contexto do usuário</span><span class="sxs-lookup"><span data-stu-id="f0d78-109">User context</span></span>

<span data-ttu-id="f0d78-110">O contexto sobre o usuário, a equipe ou a empresa pode ser especialmente útil quando:</span><span class="sxs-lookup"><span data-stu-id="f0d78-110">Context about the user, team, or company can be especially useful when:</span></span>

* <span data-ttu-id="f0d78-111">Você cria ou associa recursos em seu aplicativo com o usuário ou a equipe especificado.</span><span class="sxs-lookup"><span data-stu-id="f0d78-111">You create or associate resources in your app with the specified user or team.</span></span>
* <span data-ttu-id="f0d78-112">Você inicia um fluxo de autenticação Azure Active Directory (AAD) ou outro provedor de identidade e não exige que o usuário insira seu nome de usuário novamente.</span><span class="sxs-lookup"><span data-stu-id="f0d78-112">You initiate an authentication flow from Azure Active Directory (AAD) or other identity provider, and you do not require the user to enter their username again.</span></span> <span data-ttu-id="f0d78-113">Para obter mais informações, [consulte authenticate a user in your Microsoft Teams tab](~/concepts/authentication/authentication.md).</span><span class="sxs-lookup"><span data-stu-id="f0d78-113">For more information, see [authenticate a user in your Microsoft Teams tab](~/concepts/authentication/authentication.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f0d78-114">Embora essas informações do usuário possam ajudar a fornecer uma experiência de usuário suave, você não deve usá-la como prova de identidade.</span><span class="sxs-lookup"><span data-stu-id="f0d78-114">Although this user information can help provide a smooth user experience, you must not use it as proof of identity.</span></span> <span data-ttu-id="f0d78-115">Por exemplo, um invasor pode carregar sua página em um navegador e renderizar informações ou solicitações prejudiciais.</span><span class="sxs-lookup"><span data-stu-id="f0d78-115">For example, an attacker can load your page in a browser and render harmful information or requests.</span></span>

## <a name="access-context-information"></a><span data-ttu-id="f0d78-116">Informações de contexto de acesso</span><span class="sxs-lookup"><span data-stu-id="f0d78-116">Access context information</span></span>

<span data-ttu-id="f0d78-117">Você pode acessar informações de contexto de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="f0d78-117">You can access context information in two ways:</span></span>

* <span data-ttu-id="f0d78-118">Inserir valores de espaço reservado de URL.</span><span class="sxs-lookup"><span data-stu-id="f0d78-118">Insert URL placeholder values.</span></span>
* <span data-ttu-id="f0d78-119">Use o [Microsoft Teams SDK do](/javascript/api/overview/msteams-client)cliente JavaScript .</span><span class="sxs-lookup"><span data-stu-id="f0d78-119">Use the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client).</span></span>

### <a name="get-context-by-inserting-url-placeholder-values"></a><span data-ttu-id="f0d78-120">Obter contexto inserindo valores de espaço reservado de URL</span><span class="sxs-lookup"><span data-stu-id="f0d78-120">Get context by inserting URL placeholder values</span></span>

<span data-ttu-id="f0d78-121">Usar espaços reservados em sua configuração ou URLs de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="f0d78-121">Use placeholders in your configuration or content URLs.</span></span> <span data-ttu-id="f0d78-122">O Microsoft Teams substitui os espaços reservados pelos valores relevantes ao determinar a configuração real ou o URL do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="f0d78-122">Microsoft Teams replaces the placeholders with the relevant values when determining the actual configuration or content URL.</span></span> <span data-ttu-id="f0d78-123">Os espaço reservados disponíveis incluem todos os campos no [objeto de](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true) contexto.</span><span class="sxs-lookup"><span data-stu-id="f0d78-123">The available placeholders include all fields on the [context](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true) object.</span></span> <span data-ttu-id="f0d78-124">Os marcadores de posição comuns incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f0d78-124">Common placeholders include the following:</span></span>

* <span data-ttu-id="f0d78-125">{entityId}: ID fornecida para o item nesta guia quando a [guia é configurada](~/tabs/how-to/create-tab-pages/configuration-page.md) pela primeira vez. </span><span class="sxs-lookup"><span data-stu-id="f0d78-125">{entityId}: The ID you supplied for the item in this tab when first [configuring the tab](~/tabs/how-to/create-tab-pages/configuration-page.md).</span></span>
* <span data-ttu-id="f0d78-126">{subEntityId}: A ID fornecida ao gerar um [link profundo](~/concepts/build-and-test/deep-links.md) para um item específico nesta guia. Isso deve ser usado para restaurar para um estado específico dentro de uma entidade; por exemplo, rolar para ou ativar uma parte específica do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="f0d78-126">{subEntityId}: The ID you supplied when generating a [deep link](~/concepts/build-and-test/deep-links.md) for a specific item within this tab. This must be used to restore to a specific state within an entity; for example, scrolling to or activating a specific piece of content.</span></span>
* <span data-ttu-id="f0d78-127">{loginHint}: Um valor adequado como uma dica de logon para a AAD.</span><span class="sxs-lookup"><span data-stu-id="f0d78-127">{loginHint}: A value suitable as a login hint for AAD.</span></span> <span data-ttu-id="f0d78-128">Geralmente, esse é o nome de logon do usuário atual em seu locatário.</span><span class="sxs-lookup"><span data-stu-id="f0d78-128">This is usually the login name of the current user in their home tenant.</span></span>
* <span data-ttu-id="f0d78-129">{userPrincipalName}: o Nome principal do usuário atual no locatário atual.</span><span class="sxs-lookup"><span data-stu-id="f0d78-129">{userPrincipalName}: The User Principal Name of the current user in the current tenant.</span></span>
* <span data-ttu-id="f0d78-130">{userObjectId}: A ID do objeto AAD do usuário atual no locatário atual.</span><span class="sxs-lookup"><span data-stu-id="f0d78-130">{userObjectId}: The AAD object ID of the current user in the current tenant.</span></span>
* <span data-ttu-id="f0d78-131">{theme}: O tema atual da interface do usuário (UI), como `default` , `dark` ou `contrast` .</span><span class="sxs-lookup"><span data-stu-id="f0d78-131">{theme}: The current user interface (UI) theme such as `default`, `dark`, or `contrast`.</span></span>
* <span data-ttu-id="f0d78-132">{groupId}: A ID do grupo Office 365 no qual a guia reside.</span><span class="sxs-lookup"><span data-stu-id="f0d78-132">{groupId}: The ID of the Office 365 group in which the tab resides.</span></span>
* <span data-ttu-id="f0d78-133">{tid}: A ID do locatário do AAD do usuário atual.</span><span class="sxs-lookup"><span data-stu-id="f0d78-133">{tid}: The AAD tenant ID of the current user.</span></span>
* <span data-ttu-id="f0d78-134">{locale}: a localidade atual do usuário formatada como languageId-countryId.</span><span class="sxs-lookup"><span data-stu-id="f0d78-134">{locale}: The current locale of the user formatted as languageId-countryId.</span></span> <span data-ttu-id="f0d78-135">Por exemplo, en-us.</span><span class="sxs-lookup"><span data-stu-id="f0d78-135">For example, en-us.</span></span>

> [!NOTE]
> <span data-ttu-id="f0d78-136">O espaço reservado `{upn}` anterior agora está preterido.</span><span class="sxs-lookup"><span data-stu-id="f0d78-136">The previous `{upn}` placeholder is now deprecated.</span></span> <span data-ttu-id="f0d78-137">Para compatibilidade com versões anteriores, é atualmente um sinônimo para `{loginHint}`.</span><span class="sxs-lookup"><span data-stu-id="f0d78-137">For backward compatibility, it is currently a synonym for `{loginHint}`.</span></span>

<span data-ttu-id="f0d78-138">Por exemplo, em seu manifesto de tabulação, você definiu o atributo como , o usuário in-lo como `configURL` , tem os seguintes `"https://www.contoso.com/config?name={loginHint}&tenant={tid}&group={groupId}&theme={theme}"` atributos:</span><span class="sxs-lookup"><span data-stu-id="f0d78-138">For example, in your tab manifest you set the `configURL` attribute to `"https://www.contoso.com/config?name={loginHint}&tenant={tid}&group={groupId}&theme={theme}"`, the signed-in user has the following attributes:</span></span>

* <span data-ttu-id="f0d78-139">Seu nome de usuário **é user@example.com**.</span><span class="sxs-lookup"><span data-stu-id="f0d78-139">Their username is **user@example.com**.</span></span>
* <span data-ttu-id="f0d78-140">A ID do locatário da empresa é **e2653c-etc.**</span><span class="sxs-lookup"><span data-stu-id="f0d78-140">Their company tenant ID is **e2653c-etc**.</span></span>
* <span data-ttu-id="f0d78-141">Eles são membros do grupo Office 365 id **00209384-etc.**</span><span class="sxs-lookup"><span data-stu-id="f0d78-141">They are a member of the Office 365 group with id **00209384-etc**.</span></span>
* <span data-ttu-id="f0d78-142">O usuário definiu seu Teams como **escuro**.</span><span class="sxs-lookup"><span data-stu-id="f0d78-142">The user has set their Teams theme to **dark**.</span></span>

<span data-ttu-id="f0d78-143">Quando eles configuram a guia, Teams chama a seguinte URL:</span><span class="sxs-lookup"><span data-stu-id="f0d78-143">When they configure the tab, Teams calls the following URL:</span></span>

`https://www.contoso.com/config?name=user@example.com&tenant=e2653c-etc&group=00209384-etc&theme=dark`

### <a name="get-context-by-using-the-microsoft-teams-javascript-library"></a><span data-ttu-id="f0d78-144">Obter contexto usando a biblioteca Microsoft Teams JavaScript</span><span class="sxs-lookup"><span data-stu-id="f0d78-144">Get context by using the Microsoft Teams JavaScript library</span></span>

<span data-ttu-id="f0d78-145">Você também pode recuperar as informações listadas acima usando o [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client) chamando `microsoftTeams.getContext(function(context) { /* ... */ })`.</span><span class="sxs-lookup"><span data-stu-id="f0d78-145">You can also retrieve the information listed above using the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client) by calling `microsoftTeams.getContext(function(context) { /* ... */ })`.</span></span>

<span data-ttu-id="f0d78-146">O código a seguir fornece um exemplo de variável de contexto:</span><span class="sxs-lookup"><span data-stu-id="f0d78-146">The following code provides an example of context variable:</span></span>

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

## <a name="retrieve-context-in-private-channels"></a><span data-ttu-id="f0d78-147">Recuperar contexto em canais privados</span><span class="sxs-lookup"><span data-stu-id="f0d78-147">Retrieve context in private channels</span></span>

> [!Note]
> <span data-ttu-id="f0d78-148">Canais privados estão atualmente na visualização do desenvolvedor privado.</span><span class="sxs-lookup"><span data-stu-id="f0d78-148">Private channels are currently in private developer preview.</span></span>

<span data-ttu-id="f0d78-149">Quando sua página de conteúdo é carregada em um canal privado, os dados recebidos da chamada são ofuscados para proteger a privacidade `getContext` do canal.</span><span class="sxs-lookup"><span data-stu-id="f0d78-149">When your content page is loaded in a private channel, the data you receive from the `getContext` call is obfuscated to protect the privacy of the channel.</span></span> <span data-ttu-id="f0d78-150">Os campos a seguir são alterados quando sua página de conteúdo está em um canal privado:</span><span class="sxs-lookup"><span data-stu-id="f0d78-150">The following fields are changed when your content page is in a private channel:</span></span>

* <span data-ttu-id="f0d78-151">`groupId`: Indefinido para canais privados</span><span class="sxs-lookup"><span data-stu-id="f0d78-151">`groupId`: Undefined for private channels</span></span>
* <span data-ttu-id="f0d78-152">`teamId`: De acordo com o threadId do canal privado</span><span class="sxs-lookup"><span data-stu-id="f0d78-152">`teamId`: Set to the threadId of the private channel</span></span>
* <span data-ttu-id="f0d78-153">`teamName`: De acordo com o nome do canal privado</span><span class="sxs-lookup"><span data-stu-id="f0d78-153">`teamName`: Set to the name of the private channel</span></span>
* <span data-ttu-id="f0d78-154">`teamSiteUrl`: De acordo com a URL de um site SharePoint exclusivo para o canal privado</span><span class="sxs-lookup"><span data-stu-id="f0d78-154">`teamSiteUrl`: Set to the URL of a distinct, unique SharePoint site for the private channel</span></span>
* <span data-ttu-id="f0d78-155">`teamSitePath`: De acordo com o caminho de um site SharePoint exclusivo para o canal privado</span><span class="sxs-lookup"><span data-stu-id="f0d78-155">`teamSitePath`: Set to the path of a distinct, unique SharePoint site for the private channel</span></span>
* <span data-ttu-id="f0d78-156">`teamSiteDomain`: Definir para o domínio de um domínio de site SharePoint exclusivo para o canal privado</span><span class="sxs-lookup"><span data-stu-id="f0d78-156">`teamSiteDomain`: Set to the domain of a distinct, unique SharePoint site domain for the private channel</span></span>

<span data-ttu-id="f0d78-157">Se sua página fizer uso de qualquer um desses valores, você deverá verificar o campo para determinar se sua página está carregada em um canal privado e `channelType` responder adequadamente.</span><span class="sxs-lookup"><span data-stu-id="f0d78-157">If your page makes use of any of these values, you must check the `channelType` field to determine if your page is loaded in a private channel and respond appropriately.</span></span>

> [!Note]
> <span data-ttu-id="f0d78-158">`teamSiteUrl` também funciona bem para canais padrão.</span><span class="sxs-lookup"><span data-stu-id="f0d78-158">`teamSiteUrl` also works well for standard channels.</span></span>

## <a name="handle-theme-change"></a><span data-ttu-id="f0d78-159">Manipular a alteração de tema</span><span class="sxs-lookup"><span data-stu-id="f0d78-159">Handle theme change</span></span>

<span data-ttu-id="f0d78-160">Você pode registrar seu aplicativo para ser informado se o tema mudar chamando `microsoftTeams.registerOnThemeChangeHandler(function(theme) { /* ... */ })` .</span><span class="sxs-lookup"><span data-stu-id="f0d78-160">You can register your app to be informed if the theme changes by calling `microsoftTeams.registerOnThemeChangeHandler(function(theme) { /* ... */ })`.</span></span>

<span data-ttu-id="f0d78-161">O argumento na função é uma cadeia de caracteres com `theme` um valor de , ou `default` `dark` `contrast` .</span><span class="sxs-lookup"><span data-stu-id="f0d78-161">The `theme` argument in the function is a string with a value of `default`, `dark`, or `contrast`.</span></span>

## <a name="see-also"></a><span data-ttu-id="f0d78-162">Confira também</span><span class="sxs-lookup"><span data-stu-id="f0d78-162">See also</span></span>

* [<span data-ttu-id="f0d78-163">Diretrizes de design de tabulação</span><span class="sxs-lookup"><span data-stu-id="f0d78-163">Tab design guidelines</span></span>](~/tabs/how-to/build-adaptive-card-tabs.md)
* [<span data-ttu-id="f0d78-164">Teams guias</span><span class="sxs-lookup"><span data-stu-id="f0d78-164">Teams tabs</span></span>](~/tabs/what-are-tabs.md)
* [<span data-ttu-id="f0d78-165">Criar uma guia pessoal</span><span class="sxs-lookup"><span data-stu-id="f0d78-165">Create a personal tab</span></span>](~/tabs/how-to/create-personal-tab.md)
* [<span data-ttu-id="f0d78-166">Criar um canal ou uma guia de grupo</span><span class="sxs-lookup"><span data-stu-id="f0d78-166">Create a channel or group tab</span></span>](~/tabs/how-to/create-channel-group-tab.md)

## <a name="next-step"></a><span data-ttu-id="f0d78-167">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="f0d78-167">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f0d78-168">Criar guias com Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="f0d78-168">Build tabs with Adaptive Cards</span></span>](~/tabs/how-to/build-adaptive-card-tabs.md)