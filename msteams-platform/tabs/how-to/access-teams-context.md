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
# <a name="get-context-for-your-microsoft-teams-tab"></a><span data-ttu-id="3bcbc-104">Obter contexto para a guia do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="3bcbc-104">Get context for your Microsoft Teams tab</span></span>

<span data-ttu-id="3bcbc-105">Sua guia pode exigir informações contextuais para exibir conteúdo relevante.</span><span class="sxs-lookup"><span data-stu-id="3bcbc-105">Your tab might require contextual information to display relevant content.</span></span>

* <span data-ttu-id="3bcbc-106">Sua guia pode precisar de informações básicas sobre o usuário, a equipe ou a empresa.</span><span class="sxs-lookup"><span data-stu-id="3bcbc-106">Your tab might need basic information about the user, team, or company.</span></span>
* <span data-ttu-id="3bcbc-107">Sua guia pode precisar de informações de localidade e tema.</span><span class="sxs-lookup"><span data-stu-id="3bcbc-107">Your tab might need locale and theme information.</span></span>
* <span data-ttu-id="3bcbc-108">Sua guia pode precisar ler o `entityId` ou `subEntityId` que identifica o que está nesta guia.</span><span class="sxs-lookup"><span data-stu-id="3bcbc-108">Your tab might need to read the `entityId` or `subEntityId` that identifies what is in this tab.</span></span>

## <a name="user-context"></a><span data-ttu-id="3bcbc-109">Contexto de usuário</span><span class="sxs-lookup"><span data-stu-id="3bcbc-109">User context</span></span>

<span data-ttu-id="3bcbc-110">O contexto sobre o usuário, a equipe ou a empresa pode ser especialmente útil quando</span><span class="sxs-lookup"><span data-stu-id="3bcbc-110">Context about the user, team or company can be especially useful when</span></span>

* <span data-ttu-id="3bcbc-111">Você precisa criar ou associar recursos em seu aplicativo com o usuário ou equipe especificado.</span><span class="sxs-lookup"><span data-stu-id="3bcbc-111">You need to create or associate resources in your app with the specified user or team.</span></span>
* <span data-ttu-id="3bcbc-112">Você deseja iniciar um fluxo de autenticação no Azure Active Directory ou outro provedor de identidade e não quer exigir que o usuário insira o nome de usuário novamente.</span><span class="sxs-lookup"><span data-stu-id="3bcbc-112">You want to initiate an authentication flow against Azure Active Directory or other identity provider, and you don't want to require the user to enter their username again.</span></span> <span data-ttu-id="3bcbc-113">(Para obter mais informações sobre como autenticar na guia Microsoft Teams, confira [autenticar um usuário em sua guia do Microsoft Teams](~/concepts/authentication/authentication.md).)</span><span class="sxs-lookup"><span data-stu-id="3bcbc-113">(For more information on authenticating within your Microsoft Teams tab, see [Authenticate a user in your Microsoft Teams tab](~/concepts/authentication/authentication.md).)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3bcbc-114">Embora essas informações do usuário possam ajudar a fornecer uma experiência de usuário tranqüila, você *não* deve usá-la como prova de identidade.</span><span class="sxs-lookup"><span data-stu-id="3bcbc-114">Although this user information can help provide a smooth user experience, you should *not* use it as proof of identity.</span></span> <span data-ttu-id="3bcbc-115">Por exemplo, um invasor pode carregar sua página em um "navegador inválido" e fornecer qualquer informação que desejar.</span><span class="sxs-lookup"><span data-stu-id="3bcbc-115">For example, an attacker could you load your page in a "bad browser" and provide it with any information they want.</span></span>

## <a name="accessing-context"></a><span data-ttu-id="3bcbc-116">Contexto de acesso</span><span class="sxs-lookup"><span data-stu-id="3bcbc-116">Accessing context</span></span>

<span data-ttu-id="3bcbc-117">Você pode acessar informações de contexto de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="3bcbc-117">You can access context information in two ways:</span></span>

* <span data-ttu-id="3bcbc-118">Inserir valores de espaço reservado de URL</span><span class="sxs-lookup"><span data-stu-id="3bcbc-118">Insert URL placeholder values</span></span>
* <span data-ttu-id="3bcbc-119">Usar o [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client)</span><span class="sxs-lookup"><span data-stu-id="3bcbc-119">Use the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client)</span></span>

### <a name="getting-context-by-inserting-url-placeholder-values"></a><span data-ttu-id="3bcbc-120">Obtendo contexto inserindo valores de espaço reservado de URL</span><span class="sxs-lookup"><span data-stu-id="3bcbc-120">Getting context by inserting URL placeholder values</span></span>

<span data-ttu-id="3bcbc-121">Use espaços reservados em suas configurações ou URLs de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="3bcbc-121">Use placeholders in your configuration or content URLs.</span></span> <span data-ttu-id="3bcbc-122">O Microsoft Teams substitui os espaços reservados pelos valores relevantes ao determinar a configuração real ou a URL de conteúdo para navegar.</span><span class="sxs-lookup"><span data-stu-id="3bcbc-122">Microsoft Teams replaces the placeholders with the relevant values when determining the actual configuration or content URL to navigate to.</span></span> <span data-ttu-id="3bcbc-123">Os espaços reservados disponíveis incluem todos os campos no objeto [Context](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest) .</span><span class="sxs-lookup"><span data-stu-id="3bcbc-123">The available placeholders include all fields on the [Context](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest) object.</span></span> <span data-ttu-id="3bcbc-124">Os espaços reservados comuns incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="3bcbc-124">Common placeholders include the following:</span></span>

* <span data-ttu-id="3bcbc-125">{EntityId}: a ID que você forneceu para o item nesta guia quando [configura a guia](~/tabs/how-to/create-tab-pages/configuration-page.md)pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="3bcbc-125">{entityId}: The ID you supplied for the item in this tab when first [configuring the tab](~/tabs/how-to/create-tab-pages/configuration-page.md).</span></span>
* <span data-ttu-id="3bcbc-126">{subentityid}: a ID que você forneceu ao gerar um [link profundo](~/concepts/build-and-test/deep-links.md) para um item específico _dentro_ dessa guia. Isso deve ser usado para restaurar um estado específico dentro de uma entidade; por exemplo, rolar ou ativar uma parte específica do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="3bcbc-126">{subEntityId}: The ID you supplied when generating a [deep link](~/concepts/build-and-test/deep-links.md) for a specific item _within_ this tab. This should be used to restore to a specific state within an entity; for example, scrolling to or activating a specific piece of content.</span></span>
* <span data-ttu-id="3bcbc-127">{loginHint}: um valor adequado como uma dica de logon para o Azure AD. Em geral, esse é o nome de logon do usuário atual em seu locatário inicial.</span><span class="sxs-lookup"><span data-stu-id="3bcbc-127">{loginHint}: A value suitable as a login hint for Azure AD.This is usually the login name of the current user, in their home tenant.</span></span>
* <span data-ttu-id="3bcbc-128">{userPrincipalName}: o nome principal de usuário do usuário atual, no locatário atual.</span><span class="sxs-lookup"><span data-stu-id="3bcbc-128">{userPrincipalName}: The User Principal Name of the current user, in the current tenant.</span></span>
* <span data-ttu-id="3bcbc-129">{userobjectid}: a ID de objeto do Azure AD do usuário atual, no locatário atual.</span><span class="sxs-lookup"><span data-stu-id="3bcbc-129">{userObjectId}: The Azure AD object ID of the current user, in the current tenant.</span></span>
* <span data-ttu-id="3bcbc-130">{Theme}: o tema atual da interface do `default`usuário `dark`, como `contrast`, ou.</span><span class="sxs-lookup"><span data-stu-id="3bcbc-130">{theme}: The current UI theme such as `default`, `dark`, or `contrast`.</span></span>
* <span data-ttu-id="3bcbc-131">{GroupId}: a ID do grupo do Office 365 em que a guia reside.</span><span class="sxs-lookup"><span data-stu-id="3bcbc-131">{groupId}: The ID of the Office 365 Group in which the tab resides.</span></span>
* <span data-ttu-id="3bcbc-132">{tid}: a ID do locatário do Azure AD do usuário atual.</span><span class="sxs-lookup"><span data-stu-id="3bcbc-132">{tid}: The Azure AD tenant ID of the current user.</span></span>
* <span data-ttu-id="3bcbc-133">{locale}: a localidade atual do usuário formatada como LanguageID-countryId (por exemplo, en-US).</span><span class="sxs-lookup"><span data-stu-id="3bcbc-133">{locale}: The current locale of the user formatted as languageId-countryId (for example, en-us).</span></span>

>[!NOTE]
><span data-ttu-id="3bcbc-134">O espaço `{upn}` reservado anterior agora é preterido.</span><span class="sxs-lookup"><span data-stu-id="3bcbc-134">The previous `{upn}` placeholder is now deprecated.</span></span> <span data-ttu-id="3bcbc-135">Para compatibilidade com versões anteriores, no momento é sinônimo `{loginHint}`de.</span><span class="sxs-lookup"><span data-stu-id="3bcbc-135">For backward compatibility, it is currently a synonym for `{loginHint}`.</span></span>

<span data-ttu-id="3bcbc-136">Por exemplo, suponha que, em seu manifesto de guia `configURL` , você defina o atributo como</span><span class="sxs-lookup"><span data-stu-id="3bcbc-136">For example, suppose in your tab manifest you set the `configURL` attribute to</span></span>

`"https://www.contoso.com/config?name={loginHint}&tenant={tid}&group={groupId}&theme={theme}"`

<span data-ttu-id="3bcbc-137">E o usuário conectado tem os seguintes atributos:</span><span class="sxs-lookup"><span data-stu-id="3bcbc-137">And the signed-in user has the following attributes:</span></span>

* <span data-ttu-id="3bcbc-138">O nome de usuário é ' user@example.com '</span><span class="sxs-lookup"><span data-stu-id="3bcbc-138">Their username is 'user@example.com'</span></span>
* <span data-ttu-id="3bcbc-139">A ID de locatário da empresa é ' e2653c-etc '</span><span class="sxs-lookup"><span data-stu-id="3bcbc-139">Their company tenant ID is 'e2653c-etc'</span></span>
* <span data-ttu-id="3bcbc-140">Eles são membros do grupo do Office 365 com a ID ' 00209384-etc '</span><span class="sxs-lookup"><span data-stu-id="3bcbc-140">They are a member of the Office 365 group with id '00209384-etc'</span></span>
* <span data-ttu-id="3bcbc-141">O usuário definiu o tema da equipe como ' escuro '</span><span class="sxs-lookup"><span data-stu-id="3bcbc-141">The user has set their Teams theme to 'dark'</span></span>

<span data-ttu-id="3bcbc-142">Ao configurar sua guia, o Teams chama esta URL:</span><span class="sxs-lookup"><span data-stu-id="3bcbc-142">When they configure your tab, Teams calls this URL:</span></span>

`https://www.contoso.com/config?name=user@example.com&tenant=e2653c-etc&group=00209384-etc&theme=dark`

### <a name="getting-context-by-using-the-microsoft-teams-javascript-library"></a><span data-ttu-id="3bcbc-143">Obtendo contexto usando a biblioteca JavaScript do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="3bcbc-143">Getting context by using the Microsoft Teams JavaScript library</span></span>

<span data-ttu-id="3bcbc-144">Você também pode recuperar as informações listadas acima usando o [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client) chamando `microsoftTeams.getContext(function(context) { /* ... */ })`.</span><span class="sxs-lookup"><span data-stu-id="3bcbc-144">You can also retrieve the information listed above using the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client) by calling `microsoftTeams.getContext(function(context) { /* ... */ })`.</span></span>

<span data-ttu-id="3bcbc-145">A variável de contexto se parecerá com o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="3bcbc-145">The context variable will look like the following example.</span></span>

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

## <a name="retrieving-context-in-private-channels"></a><span data-ttu-id="3bcbc-146">Recuperando contexto em canais privados</span><span class="sxs-lookup"><span data-stu-id="3bcbc-146">Retrieving context in private channels</span></span>

> [!Note]
> <span data-ttu-id="3bcbc-147">Os canais privados estão atualmente na visualização do desenvolvedor privado.</span><span class="sxs-lookup"><span data-stu-id="3bcbc-147">Private channels are currently in private developer preview.</span></span>

<span data-ttu-id="3bcbc-148">Quando a página de conteúdo é carregada em um canal privado, os dados recebidos da `getContext` chamada serão ofuscados para proteger a privacidade do canal.</span><span class="sxs-lookup"><span data-stu-id="3bcbc-148">When your content page is loaded in a private channel, the data you receive from the `getContext` call will be obfuscated to protect the privacy of the channel.</span></span> <span data-ttu-id="3bcbc-149">Os campos a seguir são alterados quando a página de conteúdo está em um canal privado.</span><span class="sxs-lookup"><span data-stu-id="3bcbc-149">The following fields are changed when your content page is in a private channel.</span></span> <span data-ttu-id="3bcbc-150">Se a página utiliza qualquer um dos valores abaixo, você precisará verificar o campo para determinar `channelType` se a página está carregada em um canal privado e responder de forma adequada.</span><span class="sxs-lookup"><span data-stu-id="3bcbc-150">If your page makes use of any of the values below, you'll need to check the `channelType` field to determine if your page is loaded in a private channel, and respond appropriately.</span></span>

* <span data-ttu-id="3bcbc-151">`groupId`-Undefined para canais privados</span><span class="sxs-lookup"><span data-stu-id="3bcbc-151">`groupId` - Undefined for private channels</span></span>
* <span data-ttu-id="3bcbc-152">`teamId`-Definir o threadId do canal privado</span><span class="sxs-lookup"><span data-stu-id="3bcbc-152">`teamId` - Set to the threadId of the private channel</span></span>
* <span data-ttu-id="3bcbc-153">`teamName`-Definir o nome do canal privado</span><span class="sxs-lookup"><span data-stu-id="3bcbc-153">`teamName` - Set to the name of the private channel</span></span>
* <span data-ttu-id="3bcbc-154">`teamSiteUrl`-Definir como a URL de um site distinto exclusivo do SharePoint para o canal privado</span><span class="sxs-lookup"><span data-stu-id="3bcbc-154">`teamSiteUrl` - Set to the URL of a distinct, unique SharePoint site for the private channel</span></span>
* <span data-ttu-id="3bcbc-155">`teamSitePath`-Definir como o caminho de um site exclusivo do SharePoint distinto para o canal privado</span><span class="sxs-lookup"><span data-stu-id="3bcbc-155">`teamSitePath` - Set to the path of a distinct, unique SharePoint site for the private channel</span></span>
* <span data-ttu-id="3bcbc-156">`teamSiteDomain`-Definir para o domínio de um domínio de site do SharePoint distinto e exclusivo para o canal privado</span><span class="sxs-lookup"><span data-stu-id="3bcbc-156">`teamSiteDomain` - Set to the domain of a distinct, unique SharePoint site domain for the private channel</span></span>

## <a name="theme-change-handling"></a><span data-ttu-id="3bcbc-157">Tratamento de alterações de temas</span><span class="sxs-lookup"><span data-stu-id="3bcbc-157">Theme change handling</span></span>

<span data-ttu-id="3bcbc-158">Você pode registrar seu aplicativo para ser informado se o tema for alterado por `microsoftTeams.registerOnThemeChangeHandler(function(theme) { /* ... */ })`chamada.</span><span class="sxs-lookup"><span data-stu-id="3bcbc-158">You can register your app to be told if the theme changes by calling `microsoftTeams.registerOnThemeChangeHandler(function(theme) { /* ... */ })`.</span></span>

<span data-ttu-id="3bcbc-159">O `theme` argumento na função será uma cadeia de caracteres com um valor de `default`, `dark`ou `contrast`.</span><span class="sxs-lookup"><span data-stu-id="3bcbc-159">The `theme` argument in the function will be a string with a value of `default`, `dark`, or `contrast`.</span></span>