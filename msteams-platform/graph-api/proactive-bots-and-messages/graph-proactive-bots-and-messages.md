---
title: Usar o Microsoft Graph autorizar a instalação proativa de bots e mensagens no Teams
description: Descreve mensagens proativas no Teams e como implementar.
localization_priority: Normal
author: akjo
ms.author: lajanuar
ms.topic: Overview
keywords: Instalação proativa de chat de mensagens do teams Graph
ms.openlocfilehash: 0ece7d3ec3a9e00774ff2f529f7c38bc1932469d
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069091"
---
# <a name="proactive-installation-of-apps-using-graph-api-to-send-messages"></a><span data-ttu-id="ff525-104">Instalação proativa de aplicativos usando Graph API para enviar mensagens</span><span class="sxs-lookup"><span data-stu-id="ff525-104">Proactive installation of apps using Graph API to send messages</span></span>

>[!IMPORTANT]
> <span data-ttu-id="ff525-105">O Microsoft Graph e Microsoft Teams visualizações públicas estão disponíveis para acesso antecipado e comentários.</span><span class="sxs-lookup"><span data-stu-id="ff525-105">Microsoft Graph and Microsoft Teams public previews are available for early access and feedback.</span></span> <span data-ttu-id="ff525-106">Embora essa versão tenha passado por testes abrangentes, ela não se destina a ser usada na produção.</span><span class="sxs-lookup"><span data-stu-id="ff525-106">Although this release has undergone extensive testing, it is not intended for use in production.</span></span>

## <a name="proactive-messaging-in-teams"></a><span data-ttu-id="ff525-107">Mensagens proativas em Teams</span><span class="sxs-lookup"><span data-stu-id="ff525-107">Proactive messaging in Teams</span></span>

<span data-ttu-id="ff525-108">As mensagens proativas são iniciadas por bots para iniciar conversas com um usuário.</span><span class="sxs-lookup"><span data-stu-id="ff525-108">Proactive messages are initiated by bots to start conversations with a user.</span></span> <span data-ttu-id="ff525-109">Eles servem a muitas finalidades, incluindo o envio de mensagens de boas-vindas, a realização de pesquisas ou sondagens e a transmissão de notificações em toda a organização.</span><span class="sxs-lookup"><span data-stu-id="ff525-109">They serve many purposes including sending welcome messages, conducting surveys or polls, and broadcasting organization-wide notifications.</span></span> <span data-ttu-id="ff525-110">As mensagens proativas Teams podem ser entregues como conversas **ad hoc** ou **baseadas em** diálogo:</span><span class="sxs-lookup"><span data-stu-id="ff525-110">Proactive messages in Teams can be delivered as either **ad-hoc** or **dialog-based** conversations:</span></span>

|<span data-ttu-id="ff525-111">Tipo de mensagem</span><span class="sxs-lookup"><span data-stu-id="ff525-111">Message Type</span></span> | <span data-ttu-id="ff525-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="ff525-112">Description</span></span> |
|----------------|-------------- |
|<span data-ttu-id="ff525-113">Mensagem proativa ad hoc</span><span class="sxs-lookup"><span data-stu-id="ff525-113">Ad-hoc proactive message</span></span>| <span data-ttu-id="ff525-114">O bot interjectes uma mensagem sem interromper o fluxo de conversa.</span><span class="sxs-lookup"><span data-stu-id="ff525-114">The bot interjects a message without interrupting the conversation flow.</span></span>|
|<span data-ttu-id="ff525-115">Mensagem proativa baseada em caixa de diálogo</span><span class="sxs-lookup"><span data-stu-id="ff525-115">Dialog-based proactive message</span></span> | <span data-ttu-id="ff525-116">O bot cria um novo thread de caixa de diálogo, assume o controle de uma conversa, entrega a mensagem proativa, fecha e retorna o controle para a caixa de diálogo anterior.</span><span class="sxs-lookup"><span data-stu-id="ff525-116">The bot creates a new dialog thread, takes control of a conversation, delivers the proactive message, closes, and returns control to the previous dialog.</span></span>|

## <a name="proactive-app-installation-in-teams"></a><span data-ttu-id="ff525-117">Instalação proativa de aplicativos Teams</span><span class="sxs-lookup"><span data-stu-id="ff525-117">Proactive app installation in Teams</span></span>

<span data-ttu-id="ff525-118">Antes que o bot possa enviar mensagens proativas a um usuário, ele deve ser instalado como um aplicativo pessoal ou em uma equipe em que o usuário seja membro.</span><span class="sxs-lookup"><span data-stu-id="ff525-118">Before your bot can proactively message a user, it must be installed either as a personal app or in a team where the user is a member.</span></span> <span data-ttu-id="ff525-119">Às vezes, você precisa enviar mensagens proativas aos usuários que não tenham instalado ou interagido anteriormente com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ff525-119">At times, you need to proactively message users that have not installed or previously interacted with your app.</span></span> <span data-ttu-id="ff525-120">Por exemplo, a necessidade de enviar informações vitais para todos em sua organização.</span><span class="sxs-lookup"><span data-stu-id="ff525-120">For example, the need to message vital information to everyone in your organization.</span></span> <span data-ttu-id="ff525-121">Para esses cenários, você pode usar a API do Microsoft Graph para instalar proativamente seu bot para seus usuários.</span><span class="sxs-lookup"><span data-stu-id="ff525-121">For such scenarios, you can use the Microsoft Graph API to proactively install your bot for your users.</span></span>

## <a name="permissions"></a><span data-ttu-id="ff525-122">Permissões</span><span class="sxs-lookup"><span data-stu-id="ff525-122">Permissions</span></span>

<span data-ttu-id="ff525-123">Permissões de tipo de recurso do Microsoft Graph [TeamsAppInstallation](/graph/api/resources/teamsappinstallation?view=graph-rest-1.0&preserve-view=true) ajudam você a gerenciar o ciclo de vida de instalação do aplicativo para todos os escopos de usuário (pessoal) ou equipe (canal) na plataforma Microsoft Teams:</span><span class="sxs-lookup"><span data-stu-id="ff525-123">Microsoft Graph [teamsAppInstallation resource type](/graph/api/resources/teamsappinstallation?view=graph-rest-1.0&preserve-view=true) permissions helps you to manage your app's installation lifecycle for all user (personal) or team (channel) scopes within the Microsoft Teams platform:</span></span>

|<span data-ttu-id="ff525-124">Permissão de aplicativo</span><span class="sxs-lookup"><span data-stu-id="ff525-124">Application permission</span></span> | <span data-ttu-id="ff525-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="ff525-125">Description</span></span>|
|------------------|---------------------|
|`TeamsAppInstallation.ReadWriteSelfForUser.All`|<span data-ttu-id="ff525-126">Permite que um Teams aplicativo leia, instale, atualize e desinstale a si mesmo para qualquer usuário **,** sem entrar ou usar anteriormente.</span><span class="sxs-lookup"><span data-stu-id="ff525-126">Allows a Teams app to read, install, upgrade, and uninstall itself for any **user**, without prior sign in or use.</span></span>|
|`TeamsAppInstallation.ReadWriteSelfForTeam.All`|<span data-ttu-id="ff525-127">Permite que um Teams aplicativo leia, instale, atualize e desinstale-se em qualquer equipe **,** sem entrar ou usar anteriormente.</span><span class="sxs-lookup"><span data-stu-id="ff525-127">Allows a Teams app to read, install, upgrade, and uninstall itself in any **team**, without prior sign in or use.</span></span>|

<span data-ttu-id="ff525-128">Para usar essas permissões, você deve adicionar uma chave [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) ao manifesto do aplicativo com os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="ff525-128">To use these permissions, you must add a [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) key to your app manifest with the following values:</span></span>
> [!div class="checklist"]
> [!div class="checklist"]
>
> * <span data-ttu-id="ff525-129">**id** — sua ID do aplicativo do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="ff525-129">**id** — your Azure AD app ID.</span></span>
> * <span data-ttu-id="ff525-130">**resource** — a URL de recurso do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ff525-130">**resource** — the resource URL for the app.</span></span>
>
>[!NOTE]
>
> * <span data-ttu-id="ff525-131">Seu bot requer permissões de aplicativo e não delegadas pelo usuário, pois a instalação é para outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="ff525-131">Your bot requires application and not user delegated permissions because the installation is for others.</span></span>
>
> * <span data-ttu-id="ff525-132">Um administrador de locatário do Azure AD deve [conceder explicitamente permissões a um aplicativo](/graph/security-authorization#grant-permissions-to-an-application).</span><span class="sxs-lookup"><span data-stu-id="ff525-132">An Azure AD tenant administrator must [explicitly grant permissions to an application](/graph/security-authorization#grant-permissions-to-an-application).</span></span> <span data-ttu-id="ff525-133">Depois que um aplicativo recebe permissões, todos os membros do locatário do Azure AD ganham as permissões concedidas.</span><span class="sxs-lookup"><span data-stu-id="ff525-133">After an application is granted permissions, all members of the Azure AD tenant gain the granted permissions.</span></span>

## <a name="enable-proactive-app-installation-and-messaging"></a><span data-ttu-id="ff525-134">Habilitar a instalação proativa de aplicativos e mensagens</span><span class="sxs-lookup"><span data-stu-id="ff525-134">Enable proactive app installation and messaging</span></span>

> [!IMPORTANT]
><span data-ttu-id="ff525-135">O Microsoft Graph pode instalar apenas aplicativos publicados na loja de aplicativos da sua organização ou no Teams store.</span><span class="sxs-lookup"><span data-stu-id="ff525-135">Microsoft Graph can only install apps published to your organization's app store or the Teams store.</span></span>

### <a name="-create-and-publish-your-proactive-messaging-bot-for-teams"></a><span data-ttu-id="ff525-136">✔ criar e publicar seu bot de mensagens proativo para Teams</span><span class="sxs-lookup"><span data-stu-id="ff525-136">✔ Create and publish your proactive messaging bot for Teams</span></span>

<span data-ttu-id="ff525-137">Para começar, você precisa de um [bot](../../bots/how-to/create-a-bot-for-teams.md) para Teams com recursos [](../../concepts/deploy-and-publish/apps-publish-overview.md#publish-your-app-to-your-org) de mensagens proativos que estão na loja de aplicativos da sua organização ou no Teams [store](../../concepts/deploy-and-publish/apps-publish-overview.md#publish-your-app-to-the-teams-store). [](../../concepts/bots/bot-conversations/bots-conv-proactive.md)</span><span class="sxs-lookup"><span data-stu-id="ff525-137">To get started, you need a [bot for Teams](../../bots/how-to/create-a-bot-for-teams.md) with [proactive messaging](../../concepts/bots/bot-conversations/bots-conv-proactive.md) capabilities that's in your [organization's app store](../../concepts/deploy-and-publish/apps-publish-overview.md#publish-your-app-to-your-org) or the [Teams store](../../concepts/deploy-and-publish/apps-publish-overview.md#publish-your-app-to-the-teams-store).</span></span>

>[!TIP]
> <span data-ttu-id="ff525-138">O modelo de aplicativo [**company Communicator**](../..//samples/app-templates.md#company-communicator) de produção permite mensagens de transmissão e é uma boa base para criar seu aplicativo de bot proativo.</span><span class="sxs-lookup"><span data-stu-id="ff525-138">The production-ready [**Company Communicator**](../..//samples/app-templates.md#company-communicator) app template permits broadcast messaging and is a good foundation for building your proactive bot application.</span></span>

### <a name="-get-the-teamsappid-for-your-app"></a><span data-ttu-id="ff525-139">✔ Obter o `teamsAppId` para seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="ff525-139">✔ Get the `teamsAppId` for your app</span></span>

<span data-ttu-id="ff525-140">**1.** Você precisa do `teamsAppId` para as próximas etapas.</span><span class="sxs-lookup"><span data-stu-id="ff525-140">**1.** You need the `teamsAppId` for the next steps.</span></span>

<span data-ttu-id="ff525-141">O `teamsAppId` pode ser recuperado do catálogo de aplicativos da sua organização:</span><span class="sxs-lookup"><span data-stu-id="ff525-141">The `teamsAppId` can be retrieved from your organization's app catalog:</span></span>

<span data-ttu-id="ff525-142">**Referência Graph página da Microsoft: tipo** [de recurso teamsApp](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="ff525-142">**Microsoft Graph page reference:** [teamsApp resource type](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true)</span></span>

<span data-ttu-id="ff525-143">**Solicitação GET HTTP:**</span><span class="sxs-lookup"><span data-stu-id="ff525-143">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/v1.0/appCatalogs/teamsApps?$filter=externalId eq '{IdFromManifest}'
```

<span data-ttu-id="ff525-144">A solicitação deve retornar um `teamsApp` objeto.</span><span class="sxs-lookup"><span data-stu-id="ff525-144">The request must return a `teamsApp` object.</span></span> <span data-ttu-id="ff525-145">O objeto retornado é a ID de aplicativo gerada pelo catálogo do aplicativo e é diferente da ID fornecida no manifesto do Teams `id` aplicativo:</span><span class="sxs-lookup"><span data-stu-id="ff525-145">The returned object `id` is the app's catalog generated app ID and is different from the ID that you provided in your Teams app manifest:</span></span>

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

<span data-ttu-id="ff525-146">**2.**  Se seu aplicativo já tiver sido carregado ou feito sideload para um usuário no escopo pessoal, você poderá recuperar o `teamsAppId` seguinte:</span><span class="sxs-lookup"><span data-stu-id="ff525-146">**2.**  If your app has already been uploaded or sideloaded for a user in the personal scope, you can retrieve the `teamsAppId` as follows:</span></span>

<span data-ttu-id="ff525-147">**Referência Graph página da Microsoft: listar** [aplicativos instalados para o usuário](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="ff525-147">**Microsoft Graph page reference:** [List apps installed for user](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span></span>

<span data-ttu-id="ff525-148">**Solicitação GET HTTP:**</span><span class="sxs-lookup"><span data-stu-id="ff525-148">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
```

<span data-ttu-id="ff525-149">**3.** Se seu aplicativo tiver sido carregado ou feito sideload para um canal no escopo da equipe, você poderá recuperar `teamsAppId` o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ff525-149">**3.** If your app has been uploaded or sideloaded for a channel in the team scope, you can retrieve the `teamsAppId` as follows:</span></span>

<span data-ttu-id="ff525-150">**Referência Graph página da Microsoft: Listar** [aplicativos em equipe](/graph/api/team-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="ff525-150">**Microsoft Graph page reference:** [List apps in team](/graph/api/team-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span></span>

<span data-ttu-id="ff525-151">**Solicitação GET HTTP:**</span><span class="sxs-lookup"><span data-stu-id="ff525-151">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/v1.0/teams/{team-id}/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
```

>[!TIP]
> <span data-ttu-id="ff525-152">Para restringir a lista de resultados, você pode filtrar em qualquer um dos campos do [**objeto teamsApp.**](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="ff525-152">To narrow the list of results, you can filter on any of the fields of [**teamsApp**](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true) object.</span></span>

### <a name="-determine-whether-your-bot-is-currently-installed-for-a-message-recipient"></a><span data-ttu-id="ff525-153">✔ Determinar se o bot está instalado no momento para um destinatário de mensagem</span><span class="sxs-lookup"><span data-stu-id="ff525-153">✔ Determine whether your bot is currently installed for a message recipient</span></span>

<span data-ttu-id="ff525-154">**Referência Graph página da Microsoft: listar** [aplicativos instalados para o usuário](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="ff525-154">**Microsoft Graph page reference:** [List apps installed for user](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span></span>

<span data-ttu-id="ff525-155">**Solicitação GET HTTP:**</span><span class="sxs-lookup"><span data-stu-id="ff525-155">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

<span data-ttu-id="ff525-156">Essa solicitação retornará uma matriz vazia se o aplicativo não estiver instalado e uma matriz com um único [objeto teamsAppInstallation](/graph/api/resources/teamsappinstallation?view=graph-rest-v1.0&preserve-view=true) se o aplicativo estiver instalado.</span><span class="sxs-lookup"><span data-stu-id="ff525-156">This request returns an empty array if the app is not installed and an array with a single [teamsAppInstallation](/graph/api/resources/teamsappinstallation?view=graph-rest-v1.0&preserve-view=true) object if the app is installed.</span></span>

### <a name="-install-your-app"></a><span data-ttu-id="ff525-157">✔ instalar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="ff525-157">✔ Install your app</span></span>

<span data-ttu-id="ff525-158">**Referência Graph página da Microsoft:** [Instalar aplicativo para usuário](/graph/api/userteamwork-post-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="ff525-158">**Microsoft Graph page reference:** [Install app for user](/graph/api/userteamwork-post-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span></span>

<span data-ttu-id="ff525-159">**Solicitação HTTP POST:**</span><span class="sxs-lookup"><span data-stu-id="ff525-159">**HTTP POST** request:</span></span>

```http
POST https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps
Content-Type: application/json

{
   "teamsApp@odata.bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/{teamsAppId}"
}
```

<span data-ttu-id="ff525-160">Se o usuário tiver Microsoft Teams em execução, a instalação do aplicativo será vista imediatamente.</span><span class="sxs-lookup"><span data-stu-id="ff525-160">If the user has Microsoft Teams running, app installation is seen immediately.</span></span> <span data-ttu-id="ff525-161">Uma reinicialização pode ser necessária para exibir o aplicativo instalado.</span><span class="sxs-lookup"><span data-stu-id="ff525-161">A restart may be required to view the installed app.</span></span>

### <a name="-retrieve-the-conversation-chatid"></a><span data-ttu-id="ff525-162">✔ Recuperar o **chatId da conversa**</span><span class="sxs-lookup"><span data-stu-id="ff525-162">✔ Retrieve the conversation **chatId**</span></span>

<span data-ttu-id="ff525-163">Quando seu aplicativo é instalado para o usuário, o bot recebe uma notificação de evento que contém as informações necessárias `conversationUpdate` [](../../resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) para enviar a mensagem proativa.</span><span class="sxs-lookup"><span data-stu-id="ff525-163">When your app is installed for the user, the bot receives a `conversationUpdate` [event notification](../../resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) that contains the necessary information to send the proactive message.</span></span>

<span data-ttu-id="ff525-164">O `chatId` também pode ser recuperado da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="ff525-164">The `chatId` can also be retrieved as follows:</span></span>

<span data-ttu-id="ff525-165">**Referência Graph página da Microsoft:** [Obter chat](/graph/api/chat-get?view=graph-rest-beta&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="ff525-165">**Microsoft Graph page reference:** [Get chat](/graph/api/chat-get?view=graph-rest-beta&tabs=http&preserve-view=true)</span></span>

<span data-ttu-id="ff525-166">**1.** Você deve precisar do `{teamsAppInstallationId}` seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ff525-166">**1.** You must need your app's `{teamsAppInstallationId}`.</span></span> <span data-ttu-id="ff525-167">Se você não tiver, use o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ff525-167">If you don't have it, use the following:</span></span>

<span data-ttu-id="ff525-168">**Solicitação GET HTTP:**</span><span class="sxs-lookup"><span data-stu-id="ff525-168">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

<span data-ttu-id="ff525-169">A **propriedade id** da resposta é `teamsAppInstallationId` .</span><span class="sxs-lookup"><span data-stu-id="ff525-169">The **id** property of the response is the `teamsAppInstallationId`.</span></span>

<span data-ttu-id="ff525-170">**2.** Faça a seguinte solicitação para buscar `chatId` o :</span><span class="sxs-lookup"><span data-stu-id="ff525-170">**2.** Make the following request to fetch the `chatId`:</span></span>

<span data-ttu-id="ff525-171">**Solicitação GET** HTTP (permissão `TeamsAppInstallation.ReadWriteSelfForUser.All` — ):</span><span class="sxs-lookup"><span data-stu-id="ff525-171">**HTTP GET** request (permission — `TeamsAppInstallation.ReadWriteSelfForUser.All`):</span></span>  

```http
GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps/{teamsAppInstallationId}/chat
```

<span data-ttu-id="ff525-172">A **propriedade id** da resposta é `chatId` .</span><span class="sxs-lookup"><span data-stu-id="ff525-172">The **id** property of the response is the `chatId`.</span></span>

<span data-ttu-id="ff525-173">Você também pode recuperar `chatId` o com a seguinte solicitação, mas ela exige a permissão mais `Chat.Read.All` ampla:</span><span class="sxs-lookup"><span data-stu-id="ff525-173">You can also retrieve the `chatId` with the following request but it requires the broader `Chat.Read.All` permission:</span></span>

<span data-ttu-id="ff525-174">**Solicitação GET** HTTP (permissão `Chat.Read.All` — ):</span><span class="sxs-lookup"><span data-stu-id="ff525-174">**HTTP GET** request (permission — `Chat.Read.All`):</span></span>

```http
GET https://graph.microsoft.com/beta/users/{user-id}/chats?$filter=installedApps/any(a:a/teamsApp/id eq '{teamsAppId}')
```

### <a name="-send-proactive-messages"></a><span data-ttu-id="ff525-175">✔ Enviar mensagens proativas</span><span class="sxs-lookup"><span data-stu-id="ff525-175">✔ Send proactive messages</span></span>

<span data-ttu-id="ff525-176">Seu bot pode [enviar mensagens proativas](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true) depois que o bot for adicionado para um usuário ou uma equipe e tiver recebido todas as informações do usuário.</span><span class="sxs-lookup"><span data-stu-id="ff525-176">Your bot can [send proactive messages](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true) after the bot has been added for a user or a team and has received all the user information.</span></span>

## <a name="see-also"></a><span data-ttu-id="ff525-177">Confira também</span><span class="sxs-lookup"><span data-stu-id="ff525-177">See also</span></span>

* [<span data-ttu-id="ff525-178">**Gerenciar políticas de configuração de aplicativos Microsoft Teams**</span><span class="sxs-lookup"><span data-stu-id="ff525-178">**Manage app setup policies in Microsoft Teams**</span></span>](/MicrosoftTeams/teams-app-setup-policies#create-a-custom-app-setup-policy)
* [<span data-ttu-id="ff525-179">Enviar notificações proativas para usuários SDK v4</span><span class="sxs-lookup"><span data-stu-id="ff525-179">Send proactive notifications to users SDK v4</span></span>](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true)

## <a name="view-additional-code-samples"></a><span data-ttu-id="ff525-180">Exibir exemplos de código adicionais</span><span class="sxs-lookup"><span data-stu-id="ff525-180">View additional code samples</span></span>
>
> [!div class="nextstepaction"]
> [<span data-ttu-id="ff525-181">**Teams exemplos proativos de código de mensagens**</span><span class="sxs-lookup"><span data-stu-id="ff525-181">**Teams proactive messaging code samples**</span></span>](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)
