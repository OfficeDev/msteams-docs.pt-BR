---
title: Usar o Microsoft Graph para autorizar a instalação proativa de bots e mensagens no Teams
description: Descreve mensagens proativas no Teams e como implementar.
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: Overview
keywords: Instalação proativa de chat de mensagens do teams Graph
ms.openlocfilehash: 4f9c1c2e73fc89d37792e59153affc398bb87044
ms.sourcegitcommit: 3bd2627b7a334568f61ccc606395e3d89aa521d9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/31/2021
ms.locfileid: "51475932"
---
# <a name="proactive-installation-of-apps-using-graph-api-and-send-messages"></a><span data-ttu-id="b9395-104">Instalação proativa de aplicativos usando a API do Graph e enviar mensagens</span><span class="sxs-lookup"><span data-stu-id="b9395-104">Proactive installation of apps using Graph API and send messages</span></span>

>[!IMPORTANT]
> <span data-ttu-id="b9395-105">As visualizações públicas do Microsoft Graph e do Microsoft Teams estão disponíveis para acesso antecipado e comentários.</span><span class="sxs-lookup"><span data-stu-id="b9395-105">Microsoft Graph and Microsoft Teams public previews are available for early access and feedback.</span></span> <span data-ttu-id="b9395-106">Embora essa versão tenha passado por testes abrangentes, ela não se destina a ser usada na produção.</span><span class="sxs-lookup"><span data-stu-id="b9395-106">Although this release has undergone extensive testing, it is not intended for use in production.</span></span>

## <a name="proactive-messaging-in-teams"></a><span data-ttu-id="b9395-107">Mensagens proativas no Teams</span><span class="sxs-lookup"><span data-stu-id="b9395-107">Proactive messaging in Teams</span></span>

<span data-ttu-id="b9395-108">As mensagens proativas são iniciadas por bots para iniciar conversas com um usuário.</span><span class="sxs-lookup"><span data-stu-id="b9395-108">Proactive messages are initiated by bots to start conversations with a user.</span></span> <span data-ttu-id="b9395-109">Eles servem a muitas finalidades, incluindo o envio de mensagens de boas-vindas, a realização de pesquisas ou sondagens e a transmissão de notificações em toda a organização.</span><span class="sxs-lookup"><span data-stu-id="b9395-109">They serve many purposes including sending welcome messages, conducting surveys or polls, and broadcasting organization-wide notifications.</span></span> <span data-ttu-id="b9395-110">As mensagens proativas no Teams podem ser entregues como conversas **ad hoc** ou **baseadas em** diálogo:</span><span class="sxs-lookup"><span data-stu-id="b9395-110">Proactive messages in Teams can be delivered as either **ad-hoc** or **dialog-based** conversations:</span></span>

|<span data-ttu-id="b9395-111">Tipo de mensagem</span><span class="sxs-lookup"><span data-stu-id="b9395-111">Message Type</span></span> | <span data-ttu-id="b9395-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="b9395-112">Description</span></span> |
|----------------|-------------- |
|<span data-ttu-id="b9395-113">Mensagem proativa ad hoc</span><span class="sxs-lookup"><span data-stu-id="b9395-113">Ad-hoc proactive message</span></span>| <span data-ttu-id="b9395-114">O bot interjectes uma mensagem sem interromper o fluxo de conversa.</span><span class="sxs-lookup"><span data-stu-id="b9395-114">The bot interjects a message without interrupting the conversation flow.</span></span>|
|<span data-ttu-id="b9395-115">Mensagem proativa baseada em caixa de diálogo</span><span class="sxs-lookup"><span data-stu-id="b9395-115">Dialog-based proactive message</span></span> | <span data-ttu-id="b9395-116">O bot cria um novo thread de caixa de diálogo, assume o controle de uma conversa, entrega a mensagem proativa, fecha e retorna o controle para a caixa de diálogo anterior.</span><span class="sxs-lookup"><span data-stu-id="b9395-116">The bot creates a new dialog thread, takes control of a conversation, delivers the proactive message, closes, and returns control to the previous dialog.</span></span>|

<span data-ttu-id="b9395-117">Consulte Enviar [notificações proativas para usuários SDK v4](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="b9395-117">See, [Send proactive notifications to users SDK v4](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true).</span></span>

## <a name="proactive-app-installation-in-teams"></a><span data-ttu-id="b9395-118">Instalação proativa de aplicativos no Teams</span><span class="sxs-lookup"><span data-stu-id="b9395-118">Proactive app installation in Teams</span></span>

<span data-ttu-id="b9395-119">Antes que o bot possa enviar mensagens proativas a um usuário, ele deve ser instalado como um aplicativo pessoal ou em uma equipe em que o usuário seja membro.</span><span class="sxs-lookup"><span data-stu-id="b9395-119">Before your bot can proactively message a user, it must be installed either as a personal app or in a team where the user is a member.</span></span> <span data-ttu-id="b9395-120">Às vezes, você precisa enviar mensagens proativas aos usuários que não tenham instalado ou interagido anteriormente com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b9395-120">At times, you need to proactively message users that have not installed or previously interacted with your app.</span></span> <span data-ttu-id="b9395-121">Por exemplo, a necessidade de enviar informações vitais para todos em sua organização.</span><span class="sxs-lookup"><span data-stu-id="b9395-121">For example, the need to message vital information to everyone in your organization.</span></span> <span data-ttu-id="b9395-122">Para esses cenários, você pode usar a API do Microsoft Graph para instalar proativamente seu bot para seus usuários.</span><span class="sxs-lookup"><span data-stu-id="b9395-122">For such scenarios, you can use the Microsoft Graph API to proactively install your bot for your users.</span></span>

## <a name="permissions"></a><span data-ttu-id="b9395-123">Permissões</span><span class="sxs-lookup"><span data-stu-id="b9395-123">Permissions</span></span>

<span data-ttu-id="b9395-124">Microsoft Graph [teamsAppInstallation Resource type](/graph/api/resources/teamsappinstallation?view=graph-rest-1.0&preserve-view=true) permissions helps you to manage your app's installation lifecycle for all user (personal) or team (channel) scopes within the Microsoft Teams platform:</span><span class="sxs-lookup"><span data-stu-id="b9395-124">Microsoft Graph [teamsAppInstallation resource type](/graph/api/resources/teamsappinstallation?view=graph-rest-1.0&preserve-view=true) permissions helps you to manage your app's installation lifecycle for all user (personal) or team (channel) scopes within the Microsoft Teams platform:</span></span>

|<span data-ttu-id="b9395-125">Permissão de aplicativo</span><span class="sxs-lookup"><span data-stu-id="b9395-125">Application permission</span></span> | <span data-ttu-id="b9395-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="b9395-126">Description</span></span>|
|------------------|---------------------|
|`TeamsAppInstallation.ReadWriteSelfForUser.All`|<span data-ttu-id="b9395-127">Permite que um aplicativo do Teams leia, instale, atualize e desinstale a si mesmo para qualquer usuário **,** sem entrar ou usar previamente.</span><span class="sxs-lookup"><span data-stu-id="b9395-127">Allows a Teams app to read, install, upgrade, and uninstall itself for any **user**, without prior sign in or use.</span></span>|
|`TeamsAppInstallation.ReadWriteSelfForTeam.All`|<span data-ttu-id="b9395-128">Permite que um aplicativo do Teams leia, instale, atualize e desinstale a si mesmo em qualquer equipe **,** sem entrar ou usar previamente.</span><span class="sxs-lookup"><span data-stu-id="b9395-128">Allows a Teams app to read, install, upgrade, and uninstall itself in any **team**, without prior sign in or use.</span></span>|

<span data-ttu-id="b9395-129">Para usar essas permissões, você deve adicionar uma chave [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) ao manifesto do aplicativo com os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="b9395-129">To use these permissions, you must add a [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) key to your app manifest with the following values:</span></span>
> [!div class="checklist"]
> [!div class="checklist"]
>
> * <span data-ttu-id="b9395-130">**id** — sua ID do aplicativo do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="b9395-130">**id** — your Azure AD app ID.</span></span>
> * <span data-ttu-id="b9395-131">**resource** — a URL de recurso do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b9395-131">**resource** — the resource URL for the app.</span></span>
>
>[!NOTE]
>
> * <span data-ttu-id="b9395-132">Seu bot requer permissões de aplicativo e não delegadas pelo usuário, pois a instalação é para outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="b9395-132">Your bot requires application and not user delegated permissions because the installation is for others.</span></span>
>
> * <span data-ttu-id="b9395-133">Um administrador de locatário do Azure AD deve [conceder explicitamente permissões a um aplicativo](/graph/security-authorization#grant-permissions-to-an-application).</span><span class="sxs-lookup"><span data-stu-id="b9395-133">An Azure AD tenant administrator must [explicitly grant permissions to an application](/graph/security-authorization#grant-permissions-to-an-application).</span></span> <span data-ttu-id="b9395-134">Depois que um aplicativo recebe permissões, todos os membros do locatário do Azure AD ganham as permissões concedidas.</span><span class="sxs-lookup"><span data-stu-id="b9395-134">After an application is granted permissions, all members of the Azure AD tenant gain the granted permissions.</span></span>

## <a name="enable-proactive-app-installation-and-messaging"></a><span data-ttu-id="b9395-135">Habilitar a instalação proativa de aplicativos e mensagens</span><span class="sxs-lookup"><span data-stu-id="b9395-135">Enable proactive app installation and messaging</span></span>

 > [!IMPORTANT]
><span data-ttu-id="b9395-136">O Microsoft Graph só pode instalar [](../../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) aplicativos publicados no catálogo de aplicativos da sua organização ou [no AppSource](https://appsource.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="b9395-136">Microsoft Graph can only install apps published within your organization's [app catalog](../../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) or in [AppSource](https://appsource.microsoft.com/).</span></span>

### <a name="-create-and-publish-your-proactive-messaging-bot-for-teams"></a><span data-ttu-id="b9395-137">✔ criar e publicar seu bot de mensagens proativa para o Teams</span><span class="sxs-lookup"><span data-stu-id="b9395-137">✔ Create and publish your proactive messaging bot for Teams</span></span>

<span data-ttu-id="b9395-138">Para começar, você precisa de [](../../concepts/bots/bot-conversations/bots-conv-proactive.md) um bot para [](../../concepts/deploy-and-publish/overview.md) o [Teams](../../bots/how-to/create-a-bot-for-teams.md) com [](../../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) recursos de mensagens proativos publicados no catálogo de aplicativos da sua organização ou no [AppSource](https://appsource.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="b9395-138">To get started, you need a [bot for Teams](../../bots/how-to/create-a-bot-for-teams.md) with [proactive messaging](../../concepts/bots/bot-conversations/bots-conv-proactive.md) capabilities that is [published](../../concepts/deploy-and-publish/overview.md) in your organization's [app catalog](../../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) or in [AppSource](https://appsource.microsoft.com/).</span></span>

>[!TIP]
> <span data-ttu-id="b9395-139">O modelo de aplicativo company pronto para [**Communicator**](../..//samples/app-templates.md#company-communicator) de produção permite mensagens de transmissão e é uma boa base para criar seu aplicativo de bot proativo.</span><span class="sxs-lookup"><span data-stu-id="b9395-139">The production-ready [**Company Communicator**](../..//samples/app-templates.md#company-communicator) app template permits broadcast messaging and is a good foundation for building your proactive bot application.</span></span>

### <a name="-get-the-teamsappid-for-your-app"></a><span data-ttu-id="b9395-140">✔ Obter o `teamsAppId` para seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="b9395-140">✔ Get the `teamsAppId` for your app</span></span>

<span data-ttu-id="b9395-141">**1.** Você precisa do `teamsAppId` para as próximas etapas.</span><span class="sxs-lookup"><span data-stu-id="b9395-141">**1.** You need the `teamsAppId` for the next steps.</span></span>

<span data-ttu-id="b9395-142">O `teamsAppId` pode ser recuperado do catálogo de aplicativos da sua organização:</span><span class="sxs-lookup"><span data-stu-id="b9395-142">The `teamsAppId` can be retrieved from your organization's app catalog:</span></span>

<span data-ttu-id="b9395-143">**Referência de página do Microsoft Graph: tipo** [de recurso teamsApp](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="b9395-143">**Microsoft Graph page reference:** [teamsApp resource type](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true)</span></span>

<span data-ttu-id="b9395-144">**Solicitação GET HTTP:**</span><span class="sxs-lookup"><span data-stu-id="b9395-144">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/v1.0/appCatalogs/teamsApps?$filter=externalId eq '{IdFromManifest}'
```

<span data-ttu-id="b9395-145">A solicitação deve retornar um `teamsApp` objeto.</span><span class="sxs-lookup"><span data-stu-id="b9395-145">The request must return a `teamsApp` object.</span></span> <span data-ttu-id="b9395-146">O objeto retornado é a ID de aplicativo gerada pelo catálogo do aplicativo e é diferente da ID fornecida no manifesto do `id` aplicativo do Teams:</span><span class="sxs-lookup"><span data-stu-id="b9395-146">The returned object `id` is the app's catalog generated app ID and is different from the ID that you provided in your Teams app manifest:</span></span>

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

<span data-ttu-id="b9395-147">**2.**  Se seu aplicativo já tiver sido carregado ou feito sideload para um usuário no escopo pessoal, você poderá recuperar o `teamsAppId` seguinte:</span><span class="sxs-lookup"><span data-stu-id="b9395-147">**2.**  If your app has already been uploaded or sideloaded for a user in the personal scope, you can retrieve the `teamsAppId` as follows:</span></span>

<span data-ttu-id="b9395-148">**Referência de página do Microsoft Graph:** [Listar aplicativos instalados para o usuário](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="b9395-148">**Microsoft Graph page reference:** [List apps installed for user](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span></span>

<span data-ttu-id="b9395-149">**Solicitação GET HTTP:**</span><span class="sxs-lookup"><span data-stu-id="b9395-149">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
```

<span data-ttu-id="b9395-150">**3.** Se seu aplicativo tiver sido carregado ou feito sideload para um canal no escopo da equipe, você poderá recuperar `teamsAppId` o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b9395-150">**3.** If your app has been uploaded or sideloaded for a channel in the team scope, you can retrieve the `teamsAppId` as follows:</span></span>

<span data-ttu-id="b9395-151">**Referência de página do Microsoft Graph:** [Listar aplicativos na equipe](/graph/api/team-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="b9395-151">**Microsoft Graph page reference:** [List apps in team](/graph/api/team-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span></span>

<span data-ttu-id="b9395-152">**Solicitação GET HTTP:**</span><span class="sxs-lookup"><span data-stu-id="b9395-152">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/v1.0/teams/{team-id}/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
```

>[!TIP]
> <span data-ttu-id="b9395-153">Para restringir a lista de resultados, você pode filtrar em qualquer um dos campos do [**objeto teamsApp.**](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="b9395-153">To narrow the list of results, you can filter on any of the fields of [**teamsApp**](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true) object.</span></span>

### <a name="-determine-whether-your-bot-is-currently-installed-for-a-message-recipient"></a><span data-ttu-id="b9395-154">✔ Determinar se o bot está instalado no momento para um destinatário de mensagem</span><span class="sxs-lookup"><span data-stu-id="b9395-154">✔ Determine whether your bot is currently installed for a message recipient</span></span>

<span data-ttu-id="b9395-155">**Referência de página do Microsoft Graph:** [Listar aplicativos instalados para o usuário](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="b9395-155">**Microsoft Graph page reference:** [List apps installed for user](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span></span>

<span data-ttu-id="b9395-156">**Solicitação GET HTTP:**</span><span class="sxs-lookup"><span data-stu-id="b9395-156">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

<span data-ttu-id="b9395-157">Essa solicitação retornará uma matriz vazia se o aplicativo não estiver instalado e uma matriz com um único [objeto teamsAppInstallation](/graph/api/resources/teamsappinstallation?view=graph-rest-v1.0&preserve-view=true) se o aplicativo estiver instalado.</span><span class="sxs-lookup"><span data-stu-id="b9395-157">This request returns an empty array if the app is not installed and an array with a single [teamsAppInstallation](/graph/api/resources/teamsappinstallation?view=graph-rest-v1.0&preserve-view=true) object if the app is installed.</span></span>

### <a name="-install-your-app"></a><span data-ttu-id="b9395-158">✔ instalar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="b9395-158">✔ Install your app</span></span>

<span data-ttu-id="b9395-159">**Referência de página do Microsoft Graph:** [Instalar aplicativo para usuário](/graph/api/userteamwork-post-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="b9395-159">**Microsoft Graph page reference:** [Install app for user](/graph/api/userteamwork-post-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span></span>

<span data-ttu-id="b9395-160">**Solicitação HTTP POST:**</span><span class="sxs-lookup"><span data-stu-id="b9395-160">**HTTP POST** request:</span></span>

```http
POST https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps
Content-Type: application/json

{
   "teamsApp@odata.bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/{teamsAppId}"
}
```

<span data-ttu-id="b9395-161">Se o usuário tiver o Microsoft Teams em execução, a instalação do aplicativo será vista imediatamente.</span><span class="sxs-lookup"><span data-stu-id="b9395-161">If the user has Microsoft Teams running, app installation is seen immediately.</span></span> <span data-ttu-id="b9395-162">Uma reinicialização pode ser necessária para exibir o aplicativo instalado.</span><span class="sxs-lookup"><span data-stu-id="b9395-162">A restart may be required to view the installed app.</span></span>

### <a name="-retrieve-the-conversation-chatid"></a><span data-ttu-id="b9395-163">✔ Recuperar o **chatId da conversa**</span><span class="sxs-lookup"><span data-stu-id="b9395-163">✔ Retrieve the conversation **chatId**</span></span>

<span data-ttu-id="b9395-164">Quando seu aplicativo é instalado para o usuário, o bot recebe uma notificação de evento que contém as informações necessárias `conversationUpdate` [](../../resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) para enviar a mensagem proativa.</span><span class="sxs-lookup"><span data-stu-id="b9395-164">When your app is installed for the user, the bot receives a `conversationUpdate` [event notification](../../resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) that contains the necessary information to send the proactive message.</span></span>

<span data-ttu-id="b9395-165">O `chatId` também pode ser recuperado da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="b9395-165">The `chatId` can also be retrieved as follows:</span></span>

<span data-ttu-id="b9395-166">**Referência de página do Microsoft Graph:** [Obter chat](/graph/api/chat-get?view=graph-rest-beta&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="b9395-166">**Microsoft Graph page reference:** [Get chat](/graph/api/chat-get?view=graph-rest-beta&tabs=http&preserve-view=true)</span></span>

<span data-ttu-id="b9395-167">**1.** Você deve precisar do `{teamsAppInstallationId}` seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b9395-167">**1.** You must need your app's `{teamsAppInstallationId}`.</span></span> <span data-ttu-id="b9395-168">Se você não tiver, use o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b9395-168">If you don't have it, use the following:</span></span>

<span data-ttu-id="b9395-169">**Solicitação GET HTTP:**</span><span class="sxs-lookup"><span data-stu-id="b9395-169">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

<span data-ttu-id="b9395-170">A **propriedade id** da resposta é `teamsAppInstallationId` .</span><span class="sxs-lookup"><span data-stu-id="b9395-170">The **id** property of the response is the `teamsAppInstallationId`.</span></span>

<span data-ttu-id="b9395-171">**2.** Faça a seguinte solicitação para buscar `chatId` o :</span><span class="sxs-lookup"><span data-stu-id="b9395-171">**2.** Make the following request to fetch the `chatId`:</span></span>

<span data-ttu-id="b9395-172">**Solicitação GET** HTTP (permissão `TeamsAppInstallation.ReadWriteSelfForUser.All` — ):</span><span class="sxs-lookup"><span data-stu-id="b9395-172">**HTTP GET** request (permission — `TeamsAppInstallation.ReadWriteSelfForUser.All`):</span></span>  

```http
GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps/{teamsAppInstallationId}/chat
```

<span data-ttu-id="b9395-173">A **propriedade id** da resposta é `chatId` .</span><span class="sxs-lookup"><span data-stu-id="b9395-173">The **id** property of the response is the `chatId`.</span></span>

<span data-ttu-id="b9395-174">Você também pode recuperar `chatId` o com a seguinte solicitação, mas ela exige a permissão mais `Chat.Read.All` ampla:</span><span class="sxs-lookup"><span data-stu-id="b9395-174">You can also retrieve the `chatId` with the following request but it requires the broader `Chat.Read.All` permission:</span></span>

<span data-ttu-id="b9395-175">**Solicitação GET** HTTP (permissão `Chat.Read.All` — ):</span><span class="sxs-lookup"><span data-stu-id="b9395-175">**HTTP GET** request (permission — `Chat.Read.All`):</span></span>

```http
GET https://graph.microsoft.com/beta/users/{user-id}/chats?$filter=installedApps/any(a:a/teamsApp/id eq '{teamsAppId}')
```

### <a name="-send-proactive-messages"></a><span data-ttu-id="b9395-176">✔ Enviar mensagens proativas</span><span class="sxs-lookup"><span data-stu-id="b9395-176">✔ Send proactive messages</span></span>

<span data-ttu-id="b9395-177">Seu bot pode [enviar mensagens proativas](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true) depois que o bot for adicionado para um usuário ou uma equipe e tiver recebido todas as informações do usuário.</span><span class="sxs-lookup"><span data-stu-id="b9395-177">Your bot can [send proactive messages](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true) after the bot has been added for a user or a team and has received all the user information.</span></span>

## <a name="related-topic-for-teams-administrators"></a><span data-ttu-id="b9395-178">Tópico relacionado para administradores do Teams</span><span class="sxs-lookup"><span data-stu-id="b9395-178">Related topic for Teams administrators</span></span>
>
> [!div class="nextstepaction"]
> [<span data-ttu-id="b9395-179">**Gerenciar políticas de configuração de aplicativo no Teams**</span><span class="sxs-lookup"><span data-stu-id="b9395-179">**Manage app setup policies in Microsoft Teams**</span></span>](/MicrosoftTeams/teams-app-setup-policies#create-a-custom-app-setup-policy)

## <a name="view-additional-code-samples"></a><span data-ttu-id="b9395-180">Exibir exemplos de código adicionais</span><span class="sxs-lookup"><span data-stu-id="b9395-180">View additional code samples</span></span>
>
> [!div class="nextstepaction"]
> [<span data-ttu-id="b9395-181">**Exemplos de código de mensagens proativas do Teams**</span><span class="sxs-lookup"><span data-stu-id="b9395-181">**Teams proactive messaging code samples**</span></span>](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)
>
