---
title: Obter contexto para a guia
description: Descreve como obter o contexto de usuário para suas guias
keywords: contexto de usuário de guias do teams
ms.openlocfilehash: 8c94c4fd895896186ddda20bfaafd1d6ccdc1e73
ms.sourcegitcommit: 64acd30eee8af5fe151e9866c13226ed3f337c72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2020
ms.locfileid: "49346795"
---
# <a name="get-context-for-your-microsoft-teams-tab"></a><span data-ttu-id="89f32-104">Obter contexto para a guia do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="89f32-104">Get context for your Microsoft Teams tab</span></span>

<span data-ttu-id="89f32-105">Sua guia pode exigir informações contextuais para exibir conteúdo relevante.</span><span class="sxs-lookup"><span data-stu-id="89f32-105">Your tab might require contextual information to display relevant content.</span></span>

* <span data-ttu-id="89f32-106">Sua guia pode precisar de informações básicas sobre o usuário, a equipe ou a empresa.</span><span class="sxs-lookup"><span data-stu-id="89f32-106">Your tab might need basic information about the user, team, or company.</span></span>
* <span data-ttu-id="89f32-107">Sua guia pode precisar de informações de localidade e tema.</span><span class="sxs-lookup"><span data-stu-id="89f32-107">Your tab might need locale and theme information.</span></span>
* <span data-ttu-id="89f32-108">Sua guia pode precisar ler o `entityId` ou `subEntityId` que identifica o que está nesta guia.</span><span class="sxs-lookup"><span data-stu-id="89f32-108">Your tab might need to read the `entityId` or `subEntityId` that identifies what is in this tab.</span></span>

## <a name="user-context"></a><span data-ttu-id="89f32-109">Contexto de usuário</span><span class="sxs-lookup"><span data-stu-id="89f32-109">User context</span></span>

<span data-ttu-id="89f32-110">O contexto sobre o usuário, a equipe ou a empresa pode ser especialmente útil quando</span><span class="sxs-lookup"><span data-stu-id="89f32-110">Context about the user, team or company can be especially useful when</span></span>

* <span data-ttu-id="89f32-111">Você precisa criar ou associar recursos em seu aplicativo com o usuário ou equipe especificado.</span><span class="sxs-lookup"><span data-stu-id="89f32-111">You need to create or associate resources in your app with the specified user or team.</span></span>
* <span data-ttu-id="89f32-112">Você deseja iniciar um fluxo de autenticação no Azure Active Directory ou outro provedor de identidade e não quer exigir que o usuário insira o nome de usuário novamente.</span><span class="sxs-lookup"><span data-stu-id="89f32-112">You want to initiate an authentication flow against Azure Active Directory or other identity provider, and you don't want to require the user to enter their username again.</span></span> <span data-ttu-id="89f32-113">(Para obter mais informações sobre como autenticar na guia Microsoft Teams, confira [autenticar um usuário em sua guia do Microsoft Teams](~/concepts/authentication/authentication.md).)</span><span class="sxs-lookup"><span data-stu-id="89f32-113">(For more information on authenticating within your Microsoft Teams tab, see [Authenticate a user in your Microsoft Teams tab](~/concepts/authentication/authentication.md).)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="89f32-114">Embora essas informações do usuário possam ajudar a fornecer uma experiência de usuário tranqüila, você *não* deve usá-la como prova de identidade.</span><span class="sxs-lookup"><span data-stu-id="89f32-114">Although this user information can help provide a smooth user experience, you should *not* use it as proof of identity.</span></span> <span data-ttu-id="89f32-115">Por exemplo, um invasor pode carregar sua página em um "navegador inválido" e fornecer qualquer informação que desejar.</span><span class="sxs-lookup"><span data-stu-id="89f32-115">For example, an attacker could you load your page in a "bad browser" and provide it with any information they want.</span></span>

## <a name="accessing-context"></a><span data-ttu-id="89f32-116">Contexto de acesso</span><span class="sxs-lookup"><span data-stu-id="89f32-116">Accessing context</span></span>

<span data-ttu-id="89f32-117">Você pode acessar informações de contexto de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="89f32-117">You can access context information in two ways:</span></span>

* <span data-ttu-id="89f32-118">Inserir valores de espaço reservado de URL</span><span class="sxs-lookup"><span data-stu-id="89f32-118">Insert URL placeholder values</span></span>
* <span data-ttu-id="89f32-119">Usar o [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client)</span><span class="sxs-lookup"><span data-stu-id="89f32-119">Use the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client)</span></span>

### <a name="getting-context-by-inserting-url-placeholder-values"></a><span data-ttu-id="89f32-120">Obtendo contexto inserindo valores de espaço reservado de URL</span><span class="sxs-lookup"><span data-stu-id="89f32-120">Getting context by inserting URL placeholder values</span></span>

<span data-ttu-id="89f32-121">Use espaços reservados em suas configurações ou URLs de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="89f32-121">Use placeholders in your configuration or content URLs.</span></span> <span data-ttu-id="89f32-122">O Microsoft Teams substitui os espaços reservados pelos valores relevantes ao determinar a configuração real ou a URL de conteúdo para navegar.</span><span class="sxs-lookup"><span data-stu-id="89f32-122">Microsoft Teams replaces the placeholders with the relevant values when determining the actual configuration or content URL to navigate to.</span></span> <span data-ttu-id="89f32-123">Os espaços reservados disponíveis incluem todos os campos no objeto [Context](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest) .</span><span class="sxs-lookup"><span data-stu-id="89f32-123">The available placeholders include all fields on the [Context](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest) object.</span></span> <span data-ttu-id="89f32-124">Os espaços reservados comuns incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="89f32-124">Common placeholders include the following:</span></span>

* <span data-ttu-id="89f32-125">{EntityId}: a ID que você forneceu para o item nesta guia quando [configura a guia](~/tabs/how-to/create-tab-pages/configuration-page.md)pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="89f32-125">{entityId}: The ID you supplied for the item in this tab when first [configuring the tab](~/tabs/how-to/create-tab-pages/configuration-page.md).</span></span>
* <span data-ttu-id="89f32-126">{subentityid}: a ID que você forneceu ao gerar um [link profundo](~/concepts/build-and-test/deep-links.md) para um item específico _dentro_ dessa guia. Isso deve ser usado para restaurar um estado específico dentro de uma entidade; por exemplo, rolar ou ativar uma parte específica do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="89f32-126">{subEntityId}: The ID you supplied when generating a [deep link](~/concepts/build-and-test/deep-links.md) for a specific item _within_ this tab. This should be used to restore to a specific state within an entity; for example, scrolling to or activating a specific piece of content.</span></span>
* <span data-ttu-id="89f32-127">{loginHint}: um valor adequado como uma dica de logon para o Azure AD. Em geral, esse é o nome de logon do usuário atual em seu locatário inicial.</span><span class="sxs-lookup"><span data-stu-id="89f32-127">{loginHint}: A value suitable as a login hint for Azure AD.This is usually the login name of the current user, in their home tenant.</span></span>
* <span data-ttu-id="89f32-128">{userPrincipalName}: o nome principal de usuário do usuário atual, no locatário atual.</span><span class="sxs-lookup"><span data-stu-id="89f32-128">{userPrincipalName}: The User Principal Name of the current user, in the current tenant.</span></span>
* <span data-ttu-id="89f32-129">{userobjectid}: a ID de objeto do Azure AD do usuário atual, no locatário atual.</span><span class="sxs-lookup"><span data-stu-id="89f32-129">{userObjectId}: The Azure AD object ID of the current user, in the current tenant.</span></span>
* <span data-ttu-id="89f32-130">{Theme}: o tema atual da interface do usuário, como `default` , `dark` ou `contrast` .</span><span class="sxs-lookup"><span data-stu-id="89f32-130">{theme}: The current UI theme such as `default`, `dark`, or `contrast`.</span></span>
* <span data-ttu-id="89f32-131">{GroupId}: a ID do grupo do Office 365 em que a guia reside.</span><span class="sxs-lookup"><span data-stu-id="89f32-131">{groupId}: The ID of the Office 365 Group in which the tab resides.</span></span>
* <span data-ttu-id="89f32-132">{tid}: a ID do locatário do Azure AD do usuário atual.</span><span class="sxs-lookup"><span data-stu-id="89f32-132">{tid}: The Azure AD tenant ID of the current user.</span></span>
* <span data-ttu-id="89f32-133">{locale}: a localidade atual do usuário formatada como LanguageID-countryId (por exemplo, en-US).</span><span class="sxs-lookup"><span data-stu-id="89f32-133">{locale}: The current locale of the user formatted as languageId-countryId (for example, en-us).</span></span>
* <span data-ttu-id="89f32-134">{osLocaleInfo}: informações de localidade mais detalhadas do sistema operacional do usuário, se disponíveis.</span><span class="sxs-lookup"><span data-stu-id="89f32-134">{osLocaleInfo}: More detailed locale info from the user's OS if available.</span></span> <span data-ttu-id="89f32-135">Pode ser usado em conjunto com:</span><span class="sxs-lookup"><span data-stu-id="89f32-135">Can be used together with:</span></span>
    * <span data-ttu-id="89f32-136">o pacote @microsoft do/Globe NPM para garantir que seu aplicativo respeite a data do sistema operacional do usuário e</span><span class="sxs-lookup"><span data-stu-id="89f32-136">the @microsoft/globe NPM package to ensure your app respects the user's OS date and</span></span>
    * <span data-ttu-id="89f32-137">configuração de formato de hora.</span><span class="sxs-lookup"><span data-stu-id="89f32-137">time format configuration.</span></span>
* <span data-ttu-id="89f32-138">{Identificação_da_sessão}: ID exclusiva da sessão atual do teams para uso na correlação de dados de telemetria.</span><span class="sxs-lookup"><span data-stu-id="89f32-138">{sessionId}: Unique ID for the current Teams session for use in correlating telemetry data.</span></span>
* <span data-ttu-id="89f32-139">{channelId}: a ID do Microsoft Teams para o canal ao qual o conteúdo está associado.</span><span class="sxs-lookup"><span data-stu-id="89f32-139">{channelId}: The Microsoft Teams ID for the channel with which the content is associated.</span></span>
* <span data-ttu-id="89f32-140">{channelName}: o nome do canal ao qual o conteúdo está associado.</span><span class="sxs-lookup"><span data-stu-id="89f32-140">{channelName}: The name for the channel with which the content is associated.</span></span>
* <span data-ttu-id="89f32-141">{chatmanager}: o Microsoft Teams ID para o chat com o qual o conteúdo está associado.</span><span class="sxs-lookup"><span data-stu-id="89f32-141">{chatId}: The Microsoft Teams ID for the chat with which the content is associated.</span></span>
* <span data-ttu-id="89f32-142">{URL}: URL de conteúdo desta guia.</span><span class="sxs-lookup"><span data-stu-id="89f32-142">{url}: Content URL of this tab.</span></span>
* <span data-ttu-id="89f32-143">{websiteUrl}: URL do site desta guia.</span><span class="sxs-lookup"><span data-stu-id="89f32-143">{websiteUrl}: Website URL of this tab.</span></span>
* <span data-ttu-id="89f32-144">{favoriteChannelsOnly}: sinalizador que permite selecionar apenas os canais favoritos.</span><span class="sxs-lookup"><span data-stu-id="89f32-144">{favoriteChannelsOnly}: Flag allowing to select favorite channels only.</span></span>
* <span data-ttu-id="89f32-145">{favoriteTeamsOnly}: sinalizador que permite selecionar apenas o Microsoft Teams favoritos.</span><span class="sxs-lookup"><span data-stu-id="89f32-145">{favoriteTeamsOnly}: Flag allowing to select favorite teams only.</span></span>
* <span data-ttu-id="89f32-146">{userTeamRole}: função do usuário atual na equipe.</span><span class="sxs-lookup"><span data-stu-id="89f32-146">{userTeamRole}: Role of current user in the team.</span></span>
* <span data-ttu-id="89f32-147">{teamtype}: o tipo da equipe.</span><span class="sxs-lookup"><span data-stu-id="89f32-147">{teamType}: The type of the team.</span></span>
* <span data-ttu-id="89f32-148">{isTeamLocked}: o status bloqueado da equipe.</span><span class="sxs-lookup"><span data-stu-id="89f32-148">{isTeamLocked}: The locked status of the team.</span></span>
* <span data-ttu-id="89f32-149">{isTeamArchived}: o status arquivado da equipe.</span><span class="sxs-lookup"><span data-stu-id="89f32-149">{isTeamArchived}: The archived status of the team.</span></span>
* <span data-ttu-id="89f32-150">{IsFullScreen}: indica se a guia está no modo de tela inteira.</span><span class="sxs-lookup"><span data-stu-id="89f32-150">{isFullScreen}: Indication whether the tab is in full-screen mode.</span></span>
* <span data-ttu-id="89f32-151">{teamSiteUrl}: o site raiz do SharePoint associado à equipe.</span><span class="sxs-lookup"><span data-stu-id="89f32-151">{teamSiteUrl}: The root SharePoint site associated with the team.</span></span>
* <span data-ttu-id="89f32-152">{teamSiteDomain}: o domínio do site do SharePoint raiz associado à equipe.</span><span class="sxs-lookup"><span data-stu-id="89f32-152">{teamSiteDomain}: The domain of the root SharePoint site associated with the team.</span></span>
* <span data-ttu-id="89f32-153">{teamSitePath}: o caminho relativo para o site do SharePoint associado à equipe.</span><span class="sxs-lookup"><span data-stu-id="89f32-153">{teamSitePath}: The relative path to the SharePoint site associated with the team.</span></span>
* <span data-ttu-id="89f32-154">{channelRelativeUrl}: o caminho relativo para a pasta do SharePoint associada ao canal.</span><span class="sxs-lookup"><span data-stu-id="89f32-154">{channelRelativeUrl}: The relative path to the SharePoint folder associated with the channel.</span></span>
* <span data-ttu-id="89f32-155">{tenantSKU}: o tipo de licença para o locatário do usuário atual.</span><span class="sxs-lookup"><span data-stu-id="89f32-155">{tenantSKU}: The type of license for the current users tenant.</span></span>
* <span data-ttu-id="89f32-156">{ringid}: ID de anel atual.</span><span class="sxs-lookup"><span data-stu-id="89f32-156">{ringId}: Current ring ID.</span></span>
* <span data-ttu-id="89f32-157">{appSessionId}: ID exclusiva da sessão atual para uso na correlação de dados de telemetria.</span><span class="sxs-lookup"><span data-stu-id="89f32-157">{appSessionId}: Unique ID for the current session for use in correlating telemetry data.</span></span>
* <span data-ttu-id="89f32-158">{completionBotId}: especifica uma ID de bot para enviar o resultado da interação do usuário com o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="89f32-158">{completionBotId}: Specifies a bot ID to send the result of the user's interaction with the task module.</span></span>
* <span data-ttu-id="89f32-159">{Conversation}: a ID da conversa.</span><span class="sxs-lookup"><span data-stu-id="89f32-159">{conversationId}: The Id of the conversation.</span></span>
* <span data-ttu-id="89f32-160">{hostClientType}: tipo do cliente host. (Os valores possíveis são: Android, Ios, Web, desktop e Rigel.)</span><span class="sxs-lookup"><span data-stu-id="89f32-160">{hostClientType}: Type of the host client.(Possible values are: android, ios, web, desktop, and rigel.)</span></span>
* <span data-ttu-id="89f32-161">{frameContext}: o contexto em que a URL da guia é carregada (conteúdo, tarefa, configuração, remoção, sidePanel).</span><span class="sxs-lookup"><span data-stu-id="89f32-161">{frameContext}: The context where the tab url is loaded (content, task, setting, remove, sidePanel).</span></span>
* <span data-ttu-id="89f32-162">{SharePoint}: isso só está disponível quando hospedado no SharePoint.</span><span class="sxs-lookup"><span data-stu-id="89f32-162">{sharepoint}: This is only available when hosted in SharePoint.</span></span>
* <span data-ttu-id="89f32-163">{MeetingID}: é usado por guia ao executar no contexto da reunião.</span><span class="sxs-lookup"><span data-stu-id="89f32-163">{meetingId}: It is used by tab when running in meeting context.</span></span>
* <span data-ttu-id="89f32-164">{userlicensetype} O tipo de licença para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="89f32-164">{userLicenseType} The license type for the current user.</span></span>

>[!NOTE]
><span data-ttu-id="89f32-165">O `{upn}` espaço reservado anterior agora é preterido.</span><span class="sxs-lookup"><span data-stu-id="89f32-165">The previous `{upn}` placeholder is now deprecated.</span></span> <span data-ttu-id="89f32-166">Para compatibilidade com versões anteriores, no momento é sinônimo de `{loginHint}` .</span><span class="sxs-lookup"><span data-stu-id="89f32-166">For backward compatibility, it is currently a synonym for `{loginHint}`.</span></span>

<span data-ttu-id="89f32-167">Por exemplo, suponha que, em seu manifesto de guia, você defina o `configURL` atributo como</span><span class="sxs-lookup"><span data-stu-id="89f32-167">For example, suppose in your tab manifest you set the `configURL` attribute to</span></span>

`"https://www.contoso.com/config?name={loginHint}&tenant={tid}&group={groupId}&theme={theme}"`

<span data-ttu-id="89f32-168">E o usuário conectado tem os seguintes atributos:</span><span class="sxs-lookup"><span data-stu-id="89f32-168">And the signed-in user has the following attributes:</span></span>

* <span data-ttu-id="89f32-169">O nome de usuário é ' user@example.com '</span><span class="sxs-lookup"><span data-stu-id="89f32-169">Their username is 'user@example.com'</span></span>
* <span data-ttu-id="89f32-170">A ID de locatário da empresa é ' e2653c-etc '</span><span class="sxs-lookup"><span data-stu-id="89f32-170">Their company tenant ID is 'e2653c-etc'</span></span>
* <span data-ttu-id="89f32-171">Eles são membros do grupo do Office 365 com a ID ' 00209384-etc '</span><span class="sxs-lookup"><span data-stu-id="89f32-171">They are a member of the Office 365 group with id '00209384-etc'</span></span>
* <span data-ttu-id="89f32-172">O usuário definiu o tema da equipe como ' escuro '</span><span class="sxs-lookup"><span data-stu-id="89f32-172">The user has set their Teams theme to 'dark'</span></span>

<span data-ttu-id="89f32-173">Ao configurar sua guia, o Teams chama esta URL:</span><span class="sxs-lookup"><span data-stu-id="89f32-173">When they configure your tab, Teams calls this URL:</span></span>

`https://www.contoso.com/config?name=user@example.com&tenant=e2653c-etc&group=00209384-etc&theme=dark`

### <a name="getting-context-by-using-the-microsoft-teams-javascript-library"></a><span data-ttu-id="89f32-174">Obtendo contexto usando a biblioteca JavaScript do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="89f32-174">Getting context by using the Microsoft Teams JavaScript library</span></span>

<span data-ttu-id="89f32-175">Você também pode recuperar as informações listadas acima usando o [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client) chamando `microsoftTeams.getContext(function(context) { /* ... */ })` .</span><span class="sxs-lookup"><span data-stu-id="89f32-175">You can also retrieve the information listed above using the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client) by calling `microsoftTeams.getContext(function(context) { /* ... */ })`.</span></span>

<span data-ttu-id="89f32-176">A variável de contexto se parecerá com o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="89f32-176">The context variable will look like the following example.</span></span>

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

## <a name="retrieving-context-in-private-channels"></a><span data-ttu-id="89f32-177">Recuperando contexto em canais privados</span><span class="sxs-lookup"><span data-stu-id="89f32-177">Retrieving context in private channels</span></span>

> [!Note]
> <span data-ttu-id="89f32-178">Os canais privados estão atualmente na visualização do desenvolvedor privado.</span><span class="sxs-lookup"><span data-stu-id="89f32-178">Private channels are currently in private developer preview.</span></span>

<span data-ttu-id="89f32-179">Quando a página de conteúdo é carregada em um canal privado, os dados recebidos da `getContext` chamada serão ofuscados para proteger a privacidade do canal.</span><span class="sxs-lookup"><span data-stu-id="89f32-179">When your content page is loaded in a private channel, the data you receive from the `getContext` call will be obfuscated to protect the privacy of the channel.</span></span> <span data-ttu-id="89f32-180">Os campos a seguir são alterados quando a página de conteúdo está em um canal privado.</span><span class="sxs-lookup"><span data-stu-id="89f32-180">The following fields are changed when your content page is in a private channel.</span></span> <span data-ttu-id="89f32-181">Se a página utiliza qualquer um dos valores abaixo, você precisará verificar o `channelType` campo para determinar se a página está carregada em um canal privado e responder de forma adequada.</span><span class="sxs-lookup"><span data-stu-id="89f32-181">If your page makes use of any of the values below, you'll need to check the `channelType` field to determine if your page is loaded in a private channel, and respond appropriately.</span></span>

* <span data-ttu-id="89f32-182">`groupId` -Undefined para canais privados</span><span class="sxs-lookup"><span data-stu-id="89f32-182">`groupId` - Undefined for private channels</span></span>
* <span data-ttu-id="89f32-183">`teamId` -Definir o threadId do canal privado</span><span class="sxs-lookup"><span data-stu-id="89f32-183">`teamId` - Set to the threadId of the private channel</span></span>
* <span data-ttu-id="89f32-184">`teamName` -Definir o nome do canal privado</span><span class="sxs-lookup"><span data-stu-id="89f32-184">`teamName` - Set to the name of the private channel</span></span>
* <span data-ttu-id="89f32-185">`teamSiteUrl` -Definir como a URL de um site distinto exclusivo do SharePoint para o canal privado</span><span class="sxs-lookup"><span data-stu-id="89f32-185">`teamSiteUrl` - Set to the URL of a distinct, unique SharePoint site for the private channel</span></span>
* <span data-ttu-id="89f32-186">`teamSitePath` -Definir como o caminho de um site exclusivo do SharePoint distinto para o canal privado</span><span class="sxs-lookup"><span data-stu-id="89f32-186">`teamSitePath` - Set to the path of a distinct, unique SharePoint site for the private channel</span></span>
* <span data-ttu-id="89f32-187">`teamSiteDomain` -Definir para o domínio de um domínio de site do SharePoint distinto e exclusivo para o canal privado</span><span class="sxs-lookup"><span data-stu-id="89f32-187">`teamSiteDomain` - Set to the domain of a distinct, unique SharePoint site domain for the private channel</span></span>

## <a name="theme-change-handling"></a><span data-ttu-id="89f32-188">Tratamento de alterações de temas</span><span class="sxs-lookup"><span data-stu-id="89f32-188">Theme change handling</span></span>

<span data-ttu-id="89f32-189">Você pode registrar seu aplicativo para ser informado se o tema for alterado por chamada `microsoftTeams.registerOnThemeChangeHandler(function(theme) { /* ... */ })` .</span><span class="sxs-lookup"><span data-stu-id="89f32-189">You can register your app to be told if the theme changes by calling `microsoftTeams.registerOnThemeChangeHandler(function(theme) { /* ... */ })`.</span></span>

<span data-ttu-id="89f32-190">O `theme` argumento na função será uma cadeia de caracteres com um valor de `default` , `dark` ou `contrast` .</span><span class="sxs-lookup"><span data-stu-id="89f32-190">The `theme` argument in the function will be a string with a value of `default`, `dark`, or `contrast`.</span></span>
