---
title: Usar o Microsoft Graph para habilitar a instalação proativa de bots e mensagens no Teams
description: Descreve as mensagens proativas no Teams e como implementar.
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: Overview
keywords: Instalação proativa de chat de mensagens do Teams Graph
ms.openlocfilehash: 4f26b4d2f4e82fcf50b7a35c46bcd07e5afecf19
ms.sourcegitcommit: b99ed616db734371e4af4594b7e895c5b05737c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2021
ms.locfileid: "50162891"
---
# <a name="enable-proactive-bot-installation-and-proactive-messaging-in-teams-with-microsoft-graph-public-preview"></a><span data-ttu-id="86e07-104">Habilitar a instalação proativa de bots e mensagens proativas no Teams com o Microsoft Graph (Visualização Pública)</span><span class="sxs-lookup"><span data-stu-id="86e07-104">Enable proactive bot installation and proactive messaging in Teams with Microsoft Graph (Public Preview)</span></span>

>[!IMPORTANT]
> <span data-ttu-id="86e07-105">As visualizações públicas do Microsoft Graph e do Microsoft Teams estão disponíveis para acesso antecipado e comentários.</span><span class="sxs-lookup"><span data-stu-id="86e07-105">Microsoft Graph and Microsoft Teams public previews are available for early-access and feedback.</span></span> <span data-ttu-id="86e07-106">Embora esta versão tenha passado por testes extensos, ela não foi destinada ao uso na produção.</span><span class="sxs-lookup"><span data-stu-id="86e07-106">Although this release has undergone extensive testing, it is not intended for use in production.</span></span>

## <a name="proactive-messaging-in-teams"></a><span data-ttu-id="86e07-107">Mensagens proativas no Teams</span><span class="sxs-lookup"><span data-stu-id="86e07-107">Proactive messaging in Teams</span></span>

<span data-ttu-id="86e07-108">As mensagens proativas são iniciadas por bots para iniciar conversas com um usuário.</span><span class="sxs-lookup"><span data-stu-id="86e07-108">Proactive messages are initiated by bots to start conversations with a user.</span></span> <span data-ttu-id="86e07-109">Eles atendem a muitos propósitos, incluindo o envio de mensagens de boas-vindas, a realização de pesquisas ou votações e a transmissão de notificações em toda a organização.</span><span class="sxs-lookup"><span data-stu-id="86e07-109">They serve many purposes including sending welcome messages, conducting surveys or polls, and broadcasting organization-wide notifications.</span></span>  <span data-ttu-id="86e07-110">As mensagens proativas no Teams podem ser entregues como conversas **ad hoc** ou **baseadas em diálogo:**</span><span class="sxs-lookup"><span data-stu-id="86e07-110">Proactive messages in Teams can be delivered as either **ad-hoc** or **dialog-based** conversations:</span></span>

|<span data-ttu-id="86e07-111">Tipo de mensagem</span><span class="sxs-lookup"><span data-stu-id="86e07-111">Message Type</span></span> | <span data-ttu-id="86e07-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="86e07-112">Description</span></span> |
|----------------|-------------- |
|<span data-ttu-id="86e07-113">Mensagem proativa ad hoc</span><span class="sxs-lookup"><span data-stu-id="86e07-113">Ad-hoc proactive message</span></span>| <span data-ttu-id="86e07-114">O bot intercala uma mensagem sem interromper o fluxo da conversa.</span><span class="sxs-lookup"><span data-stu-id="86e07-114">The bot interjects a message without interrupting the conversation flow.</span></span>|
|<span data-ttu-id="86e07-115">Mensagem proativa baseada em caixa de diálogo</span><span class="sxs-lookup"><span data-stu-id="86e07-115">Dialog-based proactive message</span></span> | <span data-ttu-id="86e07-116">O bot cria um novo thread de diálogo, assume o controle de uma conversa, entrega a mensagem proativa, fecha e retorna o controle para a caixa de diálogo anterior.</span><span class="sxs-lookup"><span data-stu-id="86e07-116">The bot creates a new dialog thread, takes control of a conversation, delivers the proactive message, closes, and returns control to the previous dialog.</span></span>|

<span data-ttu-id="86e07-117">*Ver*, [Enviar notificações proativas para os usuários SDK v4](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="86e07-117">*See*, [Send proactive notifications to users SDK v4](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true)</span></span>

## <a name="proactive-app-installation-in-teams"></a><span data-ttu-id="86e07-118">Instalação proativa de aplicativos no Teams</span><span class="sxs-lookup"><span data-stu-id="86e07-118">Proactive app installation in Teams</span></span>

<span data-ttu-id="86e07-119">Para que seu bot possa enviar mensagens proativamente a um usuário, ele precisa ser instalado como um aplicativo pessoal ou em uma equipe na qual o usuário é membro.</span><span class="sxs-lookup"><span data-stu-id="86e07-119">Before your bot can proactively message a user, it needs to be installed either as a personal app, or in a team where the user is a member.</span></span> <span data-ttu-id="86e07-120">Às vezes, talvez seja necessário enviar mensagens proativas aos usuários que não _tenham_ instalado ou interagido anteriormente com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="86e07-120">At times,  you may need to proactively message users that have _not_ installed or previously interacted with your app.</span></span> <span data-ttu-id="86e07-121">Por exemplo, a necessidade de enviar informações vitais para todos em sua organização.</span><span class="sxs-lookup"><span data-stu-id="86e07-121">For instance, the need to message vital information to everyone in your organization.</span></span> <span data-ttu-id="86e07-122">Para esses cenários, você pode usar a API do Microsoft Graph para instalar proativamente seu bot para seus usuários.</span><span class="sxs-lookup"><span data-stu-id="86e07-122">For such scenarios, you can use the Microsoft Graph API to proactively install your bot for your users.</span></span>

## <a name="permissions"></a><span data-ttu-id="86e07-123">Permissões</span><span class="sxs-lookup"><span data-stu-id="86e07-123">Permissions</span></span>

<span data-ttu-id="86e07-124">As permissões de tipo de recurso [teamsAppInstallation](/graph/api/resources/teamsappinstallation?view=graph-rest-1.0&preserve-view=true) do Microsoft Graph permitem que você gerencie o ciclo de vida de instalação do aplicativo para todos os escopos de usuário (pessoal) ou equipe (canal) na plataforma do Microsoft Teams:</span><span class="sxs-lookup"><span data-stu-id="86e07-124">Microsoft Graph [teamsAppInstallation resource type](/graph/api/resources/teamsappinstallation?view=graph-rest-1.0&preserve-view=true) permissions allow you to manage your app's installation lifecycle for all user (personal) or team (channel) scopes within the Microsoft Teams platform:</span></span>

|<span data-ttu-id="86e07-125">Permissão de aplicativo</span><span class="sxs-lookup"><span data-stu-id="86e07-125">Application permission</span></span> | <span data-ttu-id="86e07-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="86e07-126">Description</span></span>|
|------------------|---------------------|
|`TeamsAppInstallation.ReadWriteSelfForUser.All`|<span data-ttu-id="86e07-127">Permite que um aplicativo do Teams leia, instale, atualize e se desinstale para qualquer **usuário,** sem antes entrar ou usar.</span><span class="sxs-lookup"><span data-stu-id="86e07-127">Allows a Teams app to read, install, upgrade, and uninstall itself for any **user**, without prior sign in or use.</span></span>|
|`TeamsAppInstallation.ReadWriteSelfForTeam.All`|<span data-ttu-id="86e07-128">Permite que um aplicativo do Teams leia, instale, atualize e se desinstale em qualquer **equipe,** sem antes entrar ou usar.</span><span class="sxs-lookup"><span data-stu-id="86e07-128">Allows a Teams app to read, install, upgrade, and uninstall itself in any **team**, without prior sign in or use.</span></span>|

<span data-ttu-id="86e07-129">Para usar essas permissões, você deve adicionar uma chave [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) ao manifesto do aplicativo com os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="86e07-129">To use these permissions, you must add a [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) key to your app manifest with the following values:</span></span>
> [!div class="checklist"]
> [!div class="checklist"]
>
> * <span data-ttu-id="86e07-130">**id**  — sua ID de aplicativo do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="86e07-130">**id**  — your Azure AD app id.</span></span>
> * <span data-ttu-id="86e07-131">**resource** — a URL do recurso para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="86e07-131">**resource** — the resource URL for the app.</span></span>
>

>[!NOTE]
>
> * <span data-ttu-id="86e07-132">Seu bot requer _permissões delegadas_ _pelo usuário e não_ pelo aplicativo porque a instalação não é para você, mas para outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="86e07-132">Your bot requires _application_ not _user delegated_ permissions because the installation is not for yourself but for others.</span></span>
>
> * <span data-ttu-id="86e07-133">Um administrador de locatários do Azure AD [deve conceder permissões explicitamente a um aplicativo.](/graph/security-authorization#grant-permissions-to-an-application)</span><span class="sxs-lookup"><span data-stu-id="86e07-133">An Azure AD tenant administrator must [explicitly grant permissions to an application](/graph/security-authorization#grant-permissions-to-an-application).</span></span> <span data-ttu-id="86e07-134">Depois que um aplicativo recebe _permissões,_ todos os membros do locatário do Azure AD receberão as permissões concedidas.</span><span class="sxs-lookup"><span data-stu-id="86e07-134">After an application is granted permissions, _all_ members of the Azure AD tenant will gain the granted permissions.</span></span>

## <a name="enable-proactive-app-installation-and-messaging"></a><span data-ttu-id="86e07-135">Habilitar a instalação proativa de aplicativos e mensagens</span><span class="sxs-lookup"><span data-stu-id="86e07-135">Enable proactive app installation and messaging</span></span>

 > [!IMPORTANT]
><span data-ttu-id="86e07-136">O Microsoft Graph só instalará aplicativos publicados no catálogo de [aplicativos](../../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) da sua organização ou no [AppSource.](https://appsource.microsoft.com/)</span><span class="sxs-lookup"><span data-stu-id="86e07-136">Microsoft Graph will only install apps published within your organization's [app catalog](../../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) or in [AppSource](https://appsource.microsoft.com/).</span></span>

### <a name="-create-and-publish-your-proactive-messaging-bot-for-teams"></a><span data-ttu-id="86e07-137">✔ criar e publicar seu bot de mensagens proativo para o Teams</span><span class="sxs-lookup"><span data-stu-id="86e07-137">✔ Create and publish your proactive messaging bot for Teams</span></span>

<span data-ttu-id="86e07-138">Para começar, você precisará de um [](../../concepts/bots/bot-conversations/bots-conv-proactive.md) bot para [](../../concepts/deploy-and-publish/overview.md) o [Teams](../../bots/how-to/create-a-bot-for-teams.md) com [](../../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) recursos proativos de mensagens e publicado no catálogo de aplicativos da sua organização ou no [AppSource.](https://appsource.microsoft.com/)</span><span class="sxs-lookup"><span data-stu-id="86e07-138">To get started, you will need a [bot for Teams](../../bots/how-to/create-a-bot-for-teams.md) with [proactive messaging](../../concepts/bots/bot-conversations/bots-conv-proactive.md) capabilities and  [published](../../concepts/deploy-and-publish/overview.md) in your organization's [app catalog](../../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) or in [AppSource](https://appsource.microsoft.com/).</span></span>

>[!TIP]
> <span data-ttu-id="86e07-139">O modelo de aplicativo [**Communicator da empresa pronto**](../..//samples/app-templates.md#company-communicator) para produção permite a transmissão de mensagens e é uma boa base para criar seu aplicativo de bot proativo.</span><span class="sxs-lookup"><span data-stu-id="86e07-139">The production-ready [**Company Communicator**](../..//samples/app-templates.md#company-communicator) app template enables broadcast messaging and is a good foundation for building your proactive bot application.</span></span>

### <a name="-get-the-teamsappid-for-your-app"></a><span data-ttu-id="86e07-140">✔ obter o `teamsAppId` para seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="86e07-140">✔ Get the `teamsAppId` for your app</span></span>

<span data-ttu-id="86e07-141">**1.** Você precisará das `teamsAppId`  próximas etapas.</span><span class="sxs-lookup"><span data-stu-id="86e07-141">**1.** You will need the `teamsAppId`  for the next steps.</span></span>

<span data-ttu-id="86e07-142">Ele `teamsAppId` pode ser recuperado do catálogo de aplicativos da sua organização:</span><span class="sxs-lookup"><span data-stu-id="86e07-142">The `teamsAppId` can be retrieved from your organization's app catalog:</span></span>

<span data-ttu-id="86e07-143">**Referência de página do Microsoft Graph: tipo** [de recurso teamsApp](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="86e07-143">**Microsoft Graph page reference:** [teamsApp resource type](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true)</span></span>

<span data-ttu-id="86e07-144">**Solicitação HTTP GET:**</span><span class="sxs-lookup"><span data-stu-id="86e07-144">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/v1.0/appCatalogs/teamsApps?$filter=externalId eq '{IdFromManifest}'
```

<span data-ttu-id="86e07-145">A solicitação retornará um `teamsApp`  objeto.</span><span class="sxs-lookup"><span data-stu-id="86e07-145">The request will return a `teamsApp`  object.</span></span> <span data-ttu-id="86e07-146">O objeto retornado é a ID de aplicativo gerada pelo catálogo do aplicativo e é diferente da "id:" que você forneceu no manifesto do `id`  aplicativo do Teams:</span><span class="sxs-lookup"><span data-stu-id="86e07-146">The returned object's `id`  is the app's catalog generated app id and is different from the "id:" that you provided in your Teams app manifest:</span></span>

```json
{
  "value": [
    {
      "id": "b1c5353a-7aca-41b3-830f-27d5218fe0e5",
      "externalId": "f31b1263-ba99-435a-a679-911d24850d7c",
      "name": "Test App",
      "version": "1.0.1",
      "distributionMethod": "Organization"
    }
  ]
}
```

<span data-ttu-id="86e07-147">**2.**  Se o aplicativo já tiver sido carregado ou feito sideload para um usuário no escopo pessoal, você poderá recuperar `teamsAppId` o seguinte:</span><span class="sxs-lookup"><span data-stu-id="86e07-147">**2.**  If your app has already been uploaded or sideloaded for a user in the personal scope, you can retrieve the `teamsAppId` as follows:</span></span>

<span data-ttu-id="86e07-148">**Referência da página do Microsoft Graph:** [Listar aplicativos instalados para o usuário](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="86e07-148">**Microsoft Graph page reference:** [List apps installed for user](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span></span>

<span data-ttu-id="86e07-149">**Solicitação HTTP GET:**</span><span class="sxs-lookup"><span data-stu-id="86e07-149">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
```

<span data-ttu-id="86e07-150">**3.** Se seu aplicativo já tiver sido carregado/sideload para um canal no escopo da equipe, você poderá recuperar `teamsAppId` o seguinte:</span><span class="sxs-lookup"><span data-stu-id="86e07-150">**3.** If your app has already been uploaded/sideloaded for a channel in the team scope, you can retrieve the `teamsAppId` as follows:</span></span>

<span data-ttu-id="86e07-151">**Referência da página do Microsoft Graph: Listar** [aplicativos em equipe](/graph/api/team-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="86e07-151">**Microsoft Graph page reference:** [List apps in team](/graph/api/team-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span></span>

<span data-ttu-id="86e07-152">**Solicitação HTTP GET:**</span><span class="sxs-lookup"><span data-stu-id="86e07-152">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/v1.0/teams/{team-id}/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
```

>[!TIP]
> <span data-ttu-id="86e07-153">Você pode filtrar qualquer um dos campos do objeto [**teamsApp**](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true) para restringir a lista de resultados.</span><span class="sxs-lookup"><span data-stu-id="86e07-153">You can filter on any of the fields of the [**teamsApp**](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true) object to narrow the list of results.</span></span>

### <a name="-determine-whether-your-bot-is-currently-installed-for-a-message-recipient"></a><span data-ttu-id="86e07-154">✔ Determinar se o bot está instalado no momento para um destinatário da mensagem</span><span class="sxs-lookup"><span data-stu-id="86e07-154">✔ Determine whether your bot is currently installed for a message recipient</span></span>

<span data-ttu-id="86e07-155">**Referência da página do Microsoft Graph:** [listar aplicativos instalados para o usuário](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="86e07-155">**Microsoft Graph page reference:** [List apps installed for user](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span></span>

<span data-ttu-id="86e07-156">**Solicitação HTTP GET:**</span><span class="sxs-lookup"><span data-stu-id="86e07-156">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

<span data-ttu-id="86e07-157">Essa solicitação retornará uma matriz vazia se o aplicativo não estiver instalado ou uma matriz com um único objeto [teamsAppInstallation](/graph/api/resources/teamsappinstallation?view=graph-rest-v1.0&preserve-view=true) se ele tiver sido instalado.</span><span class="sxs-lookup"><span data-stu-id="86e07-157">This request will return an empty array if the app is not installed, or an array with a single [teamsAppInstallation](/graph/api/resources/teamsappinstallation?view=graph-rest-v1.0&preserve-view=true) object if it has been installed.</span></span>

### <a name="-install-your-app"></a><span data-ttu-id="86e07-158">✔ instalar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="86e07-158">✔ Install your app</span></span>

<span data-ttu-id="86e07-159">**Referência da página do Microsoft Graph:** [Instalar aplicativo para o usuário](/graph/api/userteamwork-post-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="86e07-159">**Microsoft Graph page reference:** [Install app for user](/graph/api/userteamwork-post-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span></span>

<span data-ttu-id="86e07-160">**Solicitação HTTP POST:**</span><span class="sxs-lookup"><span data-stu-id="86e07-160">**HTTP POST** request:</span></span>

```http
POST https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps
{
   "teamsApp@odata.bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/{teamsAppId}"
}
```

<span data-ttu-id="86e07-161">Se o usuário tiver o Microsoft Teams em execução, ele poderá ver o aplicativo ser instalado imediatamente.</span><span class="sxs-lookup"><span data-stu-id="86e07-161">If the user has Microsoft Teams running, they may see the app install immediately.</span></span> <span data-ttu-id="86e07-162">Como alternativa, uma reinicialização pode ser necessária para ver o aplicativo instalado.</span><span class="sxs-lookup"><span data-stu-id="86e07-162">Alternatively, a restart may be necessary to see the installed app.</span></span>

### <a name="-retrieve-the-conversation-chatid"></a><span data-ttu-id="86e07-163">✔ recuperar o **chatId de conversa**</span><span class="sxs-lookup"><span data-stu-id="86e07-163">✔ Retrieve the conversation **chatId**</span></span>

<span data-ttu-id="86e07-164">Quando seu aplicativo for instalado para o usuário, o bot receberá uma notificação de evento que conterá as informações necessárias para enviar a `conversationUpdate` [](../../resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) mensagem proativa.</span><span class="sxs-lookup"><span data-stu-id="86e07-164">When your app is installed for the user, the bot will receive a `conversationUpdate` [event notification](../../resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) that will contain the necessary information to send the proactive message.</span></span>

<span data-ttu-id="86e07-165">O `chatId` também pode ser recuperado da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="86e07-165">The `chatId` can also be retrieved as follows:</span></span>

<span data-ttu-id="86e07-166">**Referência da página do Microsoft Graph:** [Obter chat](/graph/api/chat-get?view=graph-rest-beta&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="86e07-166">**Microsoft Graph page reference:** [Get chat](/graph/api/chat-get?view=graph-rest-beta&tabs=http&preserve-view=true)</span></span>

<span data-ttu-id="86e07-167">**1.** Você precisará do seu `{teamsAppInstallationId}` aplicativo.</span><span class="sxs-lookup"><span data-stu-id="86e07-167">**1.** You will need your app's `{teamsAppInstallationId}`.</span></span> <span data-ttu-id="86e07-168">Se você não o tiver, use o seguinte:</span><span class="sxs-lookup"><span data-stu-id="86e07-168">If you don't have it, use the following:</span></span>

<span data-ttu-id="86e07-169">**Solicitação HTTP GET:**</span><span class="sxs-lookup"><span data-stu-id="86e07-169">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

<span data-ttu-id="86e07-170">A **propriedade de id** da resposta é o `teamsAppInstallationId` .</span><span class="sxs-lookup"><span data-stu-id="86e07-170">The **id** property of the response is the `teamsAppInstallationId`.</span></span>

<span data-ttu-id="86e07-171">**2.** Faça a solicitação a seguir para buscar `chatId` o:</span><span class="sxs-lookup"><span data-stu-id="86e07-171">**2.** Make the following request to fetch the `chatId`:</span></span>

<span data-ttu-id="86e07-172">**Solicitação HTTP GET** (permissão `TeamsAppInstallation.ReadWriteSelfForUser.All` ):</span><span class="sxs-lookup"><span data-stu-id="86e07-172">**HTTP GET** request (permission — `TeamsAppInstallation.ReadWriteSelfForUser.All`):</span></span>  

```http
 GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps/{teamsAppInstallationId}/chat
```

<span data-ttu-id="86e07-173">A **propriedade de id** da resposta é o `chatId` .</span><span class="sxs-lookup"><span data-stu-id="86e07-173">The **id** property of the response is the `chatId`.</span></span>

<span data-ttu-id="86e07-174">Como alternativa, você pode recuperar o `chatId`  com a solicitação abaixo, mas ela exigirá a permissão `Chat.Read.All` mais ampla:</span><span class="sxs-lookup"><span data-stu-id="86e07-174">Alternately, you can retrieve the `chatId`  with the request below, but it will require the broader `Chat.Read.All` permission:</span></span>

<span data-ttu-id="86e07-175">**Solicitação HTTP GET** (permissão `Chat.Read.All` ):</span><span class="sxs-lookup"><span data-stu-id="86e07-175">**HTTP GET** request (permission — `Chat.Read.All`):</span></span>

```http
GET https://graph.microsoft.com/beta/users/{user-id}/chats?$filter=installedApps/any(a:a/teamsApp/id eq '{teamsAppId}')
```

### <a name="-send-proactive-messages"></a><span data-ttu-id="86e07-176">✔ enviar mensagens proativas</span><span class="sxs-lookup"><span data-stu-id="86e07-176">✔ Send proactive messages</span></span>

<span data-ttu-id="86e07-177">Depois que seu bot tiver sido adicionado a um usuário ou equipe e tiver adquirido as informações de usuário necessárias, ele poderá começar a [enviar mensagens proativas.](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="86e07-177">Once your bot has been added for a user or team and has acquired the necessary user  information, it can begin to [send proactive messages](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true).</span></span>

# <a name="c--net"></a>[<span data-ttu-id="86e07-178">C# / .NET</span><span class="sxs-lookup"><span data-stu-id="86e07-178">C# / .NET</span></span>](#tab/csharp)

<span data-ttu-id="86e07-179">O trecho de código a seguir é dos [Exemplos do Microsoft Bot Framework para C#.](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/16.proactive-messages)</span><span class="sxs-lookup"><span data-stu-id="86e07-179">The following code snippet is from the [Microsoft Bot Framework Samples for C#.](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/16.proactive-messages)</span></span>

```csharp
using System.Collections.Concurrent;
using System.Collections.Generic;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.Bot.Builder;
using Microsoft.Bot.Schema;

namespace Microsoft.BotBuilderSamples
{
    public class ProactiveBot : ActivityHandler
    {
        // Message to send to users when the bot receives a Conversation Update event
        private const string WelcomeMessage = "Welcome to the Proactive Bot sample.  Navigate to http://localhost:3978/api/notify to proactively message everyone who has previously messaged this bot.";

        // Dependency injected dictionary for storing ConversationReference objects used in NotifyController to proactively message users
        private readonly ConcurrentDictionary<string, ConversationReference> _conversationReferences;

        public ProactiveBot(ConcurrentDictionary<string, ConversationReference> conversationReferences)
        {
            _conversationReferences = conversationReferences;
        }

        private void AddConversationReference(Activity activity)
        {
            var conversationReference = activity.GetConversationReference();
            _conversationReferences.AddOrUpdate(conversationReference.User.Id, conversationReference, (key, newValue) => conversationReference);
        }

        protected override Task OnConversationUpdateActivityAsync(ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
        {
            AddConversationReference(turnContext.Activity as Activity);

            return base.OnConversationUpdateActivityAsync(turnContext, cancellationToken);
        }

        protected override async Task OnMembersAddedAsync(IList<ChannelAccount> membersAdded, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
        {
            foreach (var member in membersAdded)
            {
                // Greet anyone that was not the target (recipient) of this message.
                if (member.Id != turnContext.Activity.Recipient.Id)
                {
                    await turnContext.SendActivityAsync(MessageFactory.Text(WelcomeMessage), cancellationToken);
                }
            }
        }

        protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
        {
            AddConversationReference(turnContext.Activity as Activity);

            // Echo back what the user said
            await turnContext.SendActivityAsync(MessageFactory.Text($"You sent '{turnContext.Activity.Text}'"), cancellationToken);
        }
    }
}
```

# <a name="javascript"></a>[<span data-ttu-id="86e07-180">JavaScript</span><span class="sxs-lookup"><span data-stu-id="86e07-180">JavaScript</span></span>](#tab/javascript)

<span data-ttu-id="86e07-181">O trecho de código a seguir é dos Exemplos da [Estrutura de Bot da Microsoft para JavaScript](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/16.proactive-messages).</span><span class="sxs-lookup"><span data-stu-id="86e07-181">The following code snippet is from the [Microsoft Bot Framework Samples for JavaScript](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/16.proactive-messages).</span></span>

```javascript
const { ActivityHandler, TurnContext } = require('botbuilder');

class ProactiveBot extends ActivityHandler {
    constructor(conversationReferences) {
        super();

        // Dependency injected dictionary for storing ConversationReference objects used in NotifyController to proactively message users
        this.conversationReferences = conversationReferences;

        this.onConversationUpdate(async (context, next) => {
            this.addConversationReference(context.activity);

            await next();
        });

        this.onMembersAdded(async (context, next) => {
            const membersAdded = context.activity.membersAdded;
            for (let cnt = 0; cnt < membersAdded.length; cnt++) {
                if (membersAdded[cnt].id !== context.activity.recipient.id) {
                    const welcomeMessage = 'Welcome to the Proactive Bot sample.  Navigate to http://localhost:3978/api/notify to proactively message everyone who has previously messaged this bot.';
                    await context.sendActivity(welcomeMessage);
                }
            }

            // By calling next() you ensure that the next BotHandler is run.
            await next();
        });

        this.onMessage(async (context, next) => {
            this.addConversationReference(context.activity);

            // Echo back what the user said
            await context.sendActivity(`You sent '${ context.activity.text }'`);
            await next();
        });
    }

    addConversationReference(activity) {
        const conversationReference = TurnContext.getConversationReference(activity);
        this.conversationReferences[conversationReference.conversation.id] = conversationReference;
    }
}

module.exports.ProactiveBot = ProactiveBot;

```
---

## <a name="related-topic-for-teams-administrators"></a><span data-ttu-id="86e07-182">Tópico relacionado para administradores do Teams</span><span class="sxs-lookup"><span data-stu-id="86e07-182">Related topic for Teams administrators</span></span>
>
> [!div class="nextstepaction"]
> [<span data-ttu-id="86e07-183">**Gerenciar políticas de configuração de aplicativo no Teams**</span><span class="sxs-lookup"><span data-stu-id="86e07-183">**Manage app setup policies in Microsoft Teams**</span></span>](/MicrosoftTeams/teams-app-setup-policies#create-a-custom-app-setup-policy)

## <a name="view-additional-code-samples"></a><span data-ttu-id="86e07-184">Exibir exemplos de código adicionais</span><span class="sxs-lookup"><span data-stu-id="86e07-184">View additional code samples</span></span>
>
> [!div class="nextstepaction"]
> [<span data-ttu-id="86e07-185">**Exemplos proativos de código de mensagens do Teams**</span><span class="sxs-lookup"><span data-stu-id="86e07-185">**Teams proactive messaging code samples**</span></span>](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)
>
