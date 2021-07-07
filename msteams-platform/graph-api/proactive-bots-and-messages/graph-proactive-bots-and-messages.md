---
title: Usar o Microsoft Graph autorizar a instalação proativa de bots e mensagens no Teams
description: Descreve mensagens proativas no Teams e como implementar.
localization_priority: Normal
author: akjo
ms.author: lajanuar
ms.topic: Overview
keywords: Instalação proativa de chat de mensagens do teams Graph
ms.openlocfilehash: 0f59a74cc24b7d80dd3afd4aa4369a47d56e4d59
ms.sourcegitcommit: a6253e89cb8c8c34d45b06e08c9668daeebc30a3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/06/2021
ms.locfileid: "53300302"
---
# <a name="proactive-installation-of-apps-using-graph-api-to-send-messages"></a><span data-ttu-id="96d4f-104">Instalação proativa de aplicativos usando Graph API para enviar mensagens</span><span class="sxs-lookup"><span data-stu-id="96d4f-104">Proactive installation of apps using Graph API to send messages</span></span>

>[!IMPORTANT]
> <span data-ttu-id="96d4f-105">O Microsoft Graph e Microsoft Teams visualizações públicas estão disponíveis para acesso antecipado e comentários.</span><span class="sxs-lookup"><span data-stu-id="96d4f-105">Microsoft Graph and Microsoft Teams public previews are available for early access and feedback.</span></span> <span data-ttu-id="96d4f-106">Embora essa versão tenha passado por testes abrangentes, ela não se destina a ser usada na produção.</span><span class="sxs-lookup"><span data-stu-id="96d4f-106">Although this release has undergone extensive testing, it is not intended for use in production.</span></span>

## <a name="proactive-messaging-in-teams"></a><span data-ttu-id="96d4f-107">Mensagens proativas em Teams</span><span class="sxs-lookup"><span data-stu-id="96d4f-107">Proactive messaging in Teams</span></span>

<span data-ttu-id="96d4f-108">As mensagens proativas são iniciadas por bots para iniciar conversas com um usuário.</span><span class="sxs-lookup"><span data-stu-id="96d4f-108">Proactive messages are initiated by bots to start conversations with a user.</span></span> <span data-ttu-id="96d4f-109">Eles servem a muitas finalidades, incluindo o envio de mensagens de boas-vindas, a realização de pesquisas ou sondagens e a transmissão de notificações em toda a organização.</span><span class="sxs-lookup"><span data-stu-id="96d4f-109">They serve many purposes including sending welcome messages, conducting surveys or polls, and broadcasting organization-wide notifications.</span></span> <span data-ttu-id="96d4f-110">As mensagens proativas Teams podem ser entregues como conversas **ad hoc** ou **baseadas em** diálogo:</span><span class="sxs-lookup"><span data-stu-id="96d4f-110">Proactive messages in Teams can be delivered as either **ad-hoc** or **dialog-based** conversations:</span></span>

|<span data-ttu-id="96d4f-111">Tipo de mensagem</span><span class="sxs-lookup"><span data-stu-id="96d4f-111">Message type</span></span> | <span data-ttu-id="96d4f-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="96d4f-112">Description</span></span> |
|----------------|-------------- |
|<span data-ttu-id="96d4f-113">Mensagem proativa ad hoc</span><span class="sxs-lookup"><span data-stu-id="96d4f-113">Ad-hoc proactive message</span></span>| <span data-ttu-id="96d4f-114">O bot interjectes uma mensagem sem interromper o fluxo de conversa.</span><span class="sxs-lookup"><span data-stu-id="96d4f-114">The bot interjects a message without interrupting the conversation flow.</span></span>|
|<span data-ttu-id="96d4f-115">Mensagem proativa baseada em caixa de diálogo</span><span class="sxs-lookup"><span data-stu-id="96d4f-115">Dialog-based proactive message</span></span> | <span data-ttu-id="96d4f-116">O bot cria um novo thread de caixa de diálogo, assume o controle de uma conversa, entrega a mensagem proativa, fecha e retorna o controle para a caixa de diálogo anterior.</span><span class="sxs-lookup"><span data-stu-id="96d4f-116">The bot creates a new dialog thread, takes control of a conversation, delivers the proactive message, closes, and returns control to the previous dialog.</span></span>|

## <a name="proactive-app-installation-in-teams"></a><span data-ttu-id="96d4f-117">Instalação proativa de aplicativos Teams</span><span class="sxs-lookup"><span data-stu-id="96d4f-117">Proactive app installation in Teams</span></span>

<span data-ttu-id="96d4f-118">Antes que o bot possa enviar mensagens proativas a um usuário, ele deve ser instalado como um aplicativo pessoal ou em uma equipe em que o usuário seja membro.</span><span class="sxs-lookup"><span data-stu-id="96d4f-118">Before your bot can proactively message a user, it must be installed either as a personal app or in a team where the user is a member.</span></span> <span data-ttu-id="96d4f-119">Às vezes, você precisa enviar mensagens proativas aos usuários que não tenham instalado ou interagido anteriormente com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="96d4f-119">At times, you need to proactively message users that have not installed or previously interacted with your app.</span></span> <span data-ttu-id="96d4f-120">Por exemplo, a necessidade de enviar informações importantes para todos na sua organização.</span><span class="sxs-lookup"><span data-stu-id="96d4f-120">For example, the need to message important information to everyone in your organization.</span></span> <span data-ttu-id="96d4f-121">Para esses cenários, você pode usar a API do Microsoft Graph para instalar proativamente seu bot para seus usuários.</span><span class="sxs-lookup"><span data-stu-id="96d4f-121">For such scenarios, you can use the Microsoft Graph API to proactively install your bot for your users.</span></span>

## <a name="permissions"></a><span data-ttu-id="96d4f-122">Permissões</span><span class="sxs-lookup"><span data-stu-id="96d4f-122">Permissions</span></span>

<span data-ttu-id="96d4f-123">Permissões de tipo de recurso do Microsoft Graph [TeamsAppInstallation](/graph/api/resources/teamsappinstallation?view=graph-rest-1.0&preserve-view=true) ajudam você a gerenciar o ciclo de vida de instalação do aplicativo para todos os escopos de usuário (pessoal) ou equipe (canal) na plataforma Microsoft Teams:</span><span class="sxs-lookup"><span data-stu-id="96d4f-123">Microsoft Graph [teamsAppInstallation resource type](/graph/api/resources/teamsappinstallation?view=graph-rest-1.0&preserve-view=true) permissions help you to manage your app's installation lifecycle for all user (personal) or team (channel) scopes within the Microsoft Teams platform:</span></span>

|<span data-ttu-id="96d4f-124">Permissão de aplicativo</span><span class="sxs-lookup"><span data-stu-id="96d4f-124">Application permission</span></span> | <span data-ttu-id="96d4f-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="96d4f-125">Description</span></span>|
|------------------|---------------------|
|`TeamsAppInstallation.ReadWriteSelfForUser.All`|<span data-ttu-id="96d4f-126">Permite que um Teams aplicativo leia, instale, atualize e desinstale a si mesmo para qualquer usuário *,* sem entrar ou usar anteriormente.</span><span class="sxs-lookup"><span data-stu-id="96d4f-126">Allows a Teams app to read, install, upgrade, and uninstall itself for any *user*, without prior sign in or use.</span></span>|
|`TeamsAppInstallation.ReadWriteSelfForTeam.All`|<span data-ttu-id="96d4f-127">Permite que um Teams aplicativo leia, instale, atualize e desinstale-se em qualquer equipe *,* sem entrar ou usar anteriormente.</span><span class="sxs-lookup"><span data-stu-id="96d4f-127">Allows a Teams app to read, install, upgrade, and uninstall itself in any *team*, without prior sign in or use.</span></span>|

<span data-ttu-id="96d4f-128">Para usar essas permissões, você deve adicionar uma chave [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) ao manifesto do aplicativo com os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="96d4f-128">To use these permissions, you must add a [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) key to your app manifest with the following values:</span></span>

* <span data-ttu-id="96d4f-129">**id**: Sua Azure Active Directory (AAD) iD do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="96d4f-129">**id**: Your Azure Active Directory (AAD) app ID.</span></span>
* <span data-ttu-id="96d4f-130">**resource**: A URL de recurso do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="96d4f-130">**resource**: The resource URL for the app.</span></span>

> [!NOTE]
>
> * <span data-ttu-id="96d4f-131">Seu bot requer permissões de aplicativo e não delegadas pelo usuário, pois a instalação é para outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="96d4f-131">Your bot requires application and not user delegated permissions because the installation is for others.</span></span>
>
> * <span data-ttu-id="96d4f-132">Um administrador de locatário do AAD deve [conceder explicitamente permissões a um aplicativo](/graph/security-authorization#grant-permissions-to-an-application).</span><span class="sxs-lookup"><span data-stu-id="96d4f-132">An AAD tenant administrator must [explicitly grant permissions to an application](/graph/security-authorization#grant-permissions-to-an-application).</span></span> <span data-ttu-id="96d4f-133">Depois que o aplicativo recebe permissões, todos os membros do locatário do AAD receberão as permissões concedidas.</span><span class="sxs-lookup"><span data-stu-id="96d4f-133">After the application is granted permissions, all members of the AAD tenant get the granted permissions.</span></span>

## <a name="enable-proactive-app-installation-and-messaging"></a><span data-ttu-id="96d4f-134">Habilitar a instalação proativa de aplicativos e mensagens</span><span class="sxs-lookup"><span data-stu-id="96d4f-134">Enable proactive app installation and messaging</span></span>

> [!IMPORTANT]
> <span data-ttu-id="96d4f-135">O Microsoft Graph pode instalar apenas aplicativos publicados na loja de aplicativos da sua organização ou no Teams store.</span><span class="sxs-lookup"><span data-stu-id="96d4f-135">Microsoft Graph can only install apps published to your organization's app store or the Teams store.</span></span>

### <a name="create-and-publish-your-proactive-messaging-bot-for-teams"></a><span data-ttu-id="96d4f-136">Criar e publicar seu bot de mensagens proativo para Teams</span><span class="sxs-lookup"><span data-stu-id="96d4f-136">Create and publish your proactive messaging bot for Teams</span></span>

<span data-ttu-id="96d4f-137">Para começar, você precisa de um [bot](../../bots/how-to/create-a-bot-for-teams.md) para Teams com recursos [](../../concepts/deploy-and-publish/apps-publish-overview.md#publish-your-app-to-your-org) de mensagens proativos que estão na loja de aplicativos da sua organização ou no Teams [store](../../concepts/deploy-and-publish/apps-publish-overview.md#publish-your-app-to-the-teams-store). [](../../concepts/bots/bot-conversations/bots-conv-proactive.md)</span><span class="sxs-lookup"><span data-stu-id="96d4f-137">To get started, you need a [bot for Teams](../../bots/how-to/create-a-bot-for-teams.md) with [proactive messaging](../../concepts/bots/bot-conversations/bots-conv-proactive.md) capabilities that is in your [organization's app store](../../concepts/deploy-and-publish/apps-publish-overview.md#publish-your-app-to-your-org) or the [Teams store](../../concepts/deploy-and-publish/apps-publish-overview.md#publish-your-app-to-the-teams-store).</span></span>

> [!TIP]
> <span data-ttu-id="96d4f-138">O modelo de aplicativo [*company Communicator*](../..//samples/app-templates.md#company-communicator) de produção permite mensagens de transmissão e é um bom começo para criar seu aplicativo de bot proativo.</span><span class="sxs-lookup"><span data-stu-id="96d4f-138">The production-ready [*Company Communicator*](../..//samples/app-templates.md#company-communicator) app template permits broadcast messaging and is a good start to build your proactive bot application.</span></span>

### <a name="get-the-teamsappid-for-your-app"></a><span data-ttu-id="96d4f-139">Obter o `teamsAppId` para seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="96d4f-139">Get the `teamsAppId` for your app</span></span>

<span data-ttu-id="96d4f-140">Você pode recuperar o `teamsAppId` das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="96d4f-140">You can retrieve the `teamsAppId` in the following ways:</span></span>

* <span data-ttu-id="96d4f-141">No catálogo de aplicativos da sua organização:</span><span class="sxs-lookup"><span data-stu-id="96d4f-141">From your organization's app catalog:</span></span>

    <span data-ttu-id="96d4f-142">**Referência Graph página da Microsoft: tipo** [de recurso teamsApp](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="96d4f-142">**Microsoft Graph page reference:** [teamsApp resource type](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true)</span></span>

    <span data-ttu-id="96d4f-143">**Solicitação GET HTTP:**</span><span class="sxs-lookup"><span data-stu-id="96d4f-143">**HTTP GET** request:</span></span>

    ```http
        GET https://graph.microsoft.com/v1.0/appCatalogs/teamsApps?$filter=externalId eq '{IdFromManifest}'
    ```

    <span data-ttu-id="96d4f-144">A solicitação deve retornar um objeto , que é a ID de aplicativo gerada pelo catálogo `teamsApp` `id` do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="96d4f-144">The request must return a `teamsApp` object `id`, which is the app's catalog generated app ID.</span></span> <span data-ttu-id="96d4f-145">Isso é diferente da ID fornecida no manifesto Teams aplicativo:</span><span class="sxs-lookup"><span data-stu-id="96d4f-145">This is different from the ID that you provided in your Teams app manifest:</span></span>

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

* <span data-ttu-id="96d4f-146">Se seu aplicativo já tiver sido carregado ou feito sideload para um usuário no escopo pessoal:</span><span class="sxs-lookup"><span data-stu-id="96d4f-146">If your app has already been uploaded or sideloaded for a user in personal scope:</span></span>

    <span data-ttu-id="96d4f-147">**Referência Graph página da Microsoft: listar** [aplicativos instalados para o usuário](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="96d4f-147">**Microsoft Graph page reference:** [List apps installed for user](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span></span>

    <span data-ttu-id="96d4f-148">**Solicitação GET HTTP:**</span><span class="sxs-lookup"><span data-stu-id="96d4f-148">**HTTP GET** request:</span></span>

    ```http
    GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
    ```

* <span data-ttu-id="96d4f-149">Se seu aplicativo já tiver sido carregado ou feito sideload para um canal no escopo da equipe:</span><span class="sxs-lookup"><span data-stu-id="96d4f-149">If your app has already been uploaded or sideloaded for a channel in team scope:</span></span>

    <span data-ttu-id="96d4f-150">**Referência Graph página da Microsoft: Listar** [aplicativos em equipe](/graph/api/team-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="96d4f-150">**Microsoft Graph page reference:** [List apps in team](/graph/api/team-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span></span>

    <span data-ttu-id="96d4f-151">**Solicitação GET HTTP:**</span><span class="sxs-lookup"><span data-stu-id="96d4f-151">**HTTP GET** request:</span></span>

    ```http
    GET https://graph.microsoft.com/v1.0/teams/{team-id}/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
    ```

    > [!TIP]
    > <span data-ttu-id="96d4f-152">Para restringir a lista de resultados, você pode filtrar qualquer um dos campos do [**objeto teamsApp.**](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="96d4f-152">To narrow the list of results, you can filter any of the fields of the [**teamsApp**](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true) object.</span></span>

### <a name="determine-whether-your-bot-is-currently-installed-for-a-message-recipient"></a><span data-ttu-id="96d4f-153">Determinar se o bot está instalado no momento para um destinatário de mensagem</span><span class="sxs-lookup"><span data-stu-id="96d4f-153">Determine whether your bot is currently installed for a message recipient</span></span>

<span data-ttu-id="96d4f-154">Você pode determinar se o bot está instalado no momento para um destinatário de mensagem da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="96d4f-154">You can determine whether your bot is currently installed for a message recipient as follows:</span></span>

<span data-ttu-id="96d4f-155">**Referência Graph página da Microsoft: listar** [aplicativos instalados para o usuário](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="96d4f-155">**Microsoft Graph page reference:** [List apps installed for user](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span></span>

<span data-ttu-id="96d4f-156">**Solicitação GET HTTP:**</span><span class="sxs-lookup"><span data-stu-id="96d4f-156">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

<span data-ttu-id="96d4f-157">A solicitação retorna:</span><span class="sxs-lookup"><span data-stu-id="96d4f-157">The request returns:</span></span>

* <span data-ttu-id="96d4f-158">Uma matriz vazia se o aplicativo não estiver instalado.</span><span class="sxs-lookup"><span data-stu-id="96d4f-158">An empty array if the app is not installed.</span></span>
* <span data-ttu-id="96d4f-159">Uma matriz com um único [objeto teamsAppInstallation](/graph/api/resources/teamsappinstallation?view=graph-rest-v1.0&preserve-view=true) se o aplicativo estiver instalado.</span><span class="sxs-lookup"><span data-stu-id="96d4f-159">An array with a single [teamsAppInstallation](/graph/api/resources/teamsappinstallation?view=graph-rest-v1.0&preserve-view=true) object if the app is installed.</span></span>

### <a name="install-your-app"></a><span data-ttu-id="96d4f-160">Instalar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="96d4f-160">Install your app</span></span>

<span data-ttu-id="96d4f-161">Você pode instalar seu aplicativo da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="96d4f-161">You can install your app as follows:</span></span>

<span data-ttu-id="96d4f-162">**Referência Graph página da Microsoft:** [Instalar aplicativo para usuário](/graph/api/userteamwork-post-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="96d4f-162">**Microsoft Graph page reference:** [Install app for user](/graph/api/userteamwork-post-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span></span>

<span data-ttu-id="96d4f-163">**Solicitação HTTP POST:**</span><span class="sxs-lookup"><span data-stu-id="96d4f-163">**HTTP POST** request:</span></span>

```http
POST https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps
Content-Type: application/json

{
   "teamsApp@odata.bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/{teamsAppId}"
}
```

<span data-ttu-id="96d4f-164">Se o usuário tiver Microsoft Teams em execução, a instalação do aplicativo ocorrerá imediatamente.</span><span class="sxs-lookup"><span data-stu-id="96d4f-164">If the user has Microsoft Teams running, app installation occurs immediately.</span></span> <span data-ttu-id="96d4f-165">Uma reinicialização pode ser necessária para exibir o aplicativo instalado.</span><span class="sxs-lookup"><span data-stu-id="96d4f-165">A restart may be required to view the installed app.</span></span>

### <a name="retrieve-the-conversation-chatid"></a><span data-ttu-id="96d4f-166">Recuperar a conversa `chatId`</span><span class="sxs-lookup"><span data-stu-id="96d4f-166">Retrieve the conversation `chatId`</span></span>

<span data-ttu-id="96d4f-167">Quando seu aplicativo é instalado para o usuário, o bot recebe uma notificação de evento que contém as informações necessárias `conversationUpdate` [](../../resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) para enviar a mensagem proativa.</span><span class="sxs-lookup"><span data-stu-id="96d4f-167">When your app is installed for the user, the bot receives a `conversationUpdate` [event notification](../../resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) that contains the necessary information to send the proactive message.</span></span>

<span data-ttu-id="96d4f-168">**Referência Graph página da Microsoft:** [Obter chat](/graph/api/chat-get?view=graph-rest-beta&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="96d4f-168">**Microsoft Graph page reference:** [Get chat](/graph/api/chat-get?view=graph-rest-beta&tabs=http&preserve-view=true)</span></span>

1. <span data-ttu-id="96d4f-169">Você deve ter o `{teamsAppInstallationId}` seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="96d4f-169">You must have your app's `{teamsAppInstallationId}`.</span></span> <span data-ttu-id="96d4f-170">Se você não o tiver, use o seguinte:</span><span class="sxs-lookup"><span data-stu-id="96d4f-170">If you do not have it, use the following:</span></span>

    <span data-ttu-id="96d4f-171">**Solicitação GET HTTP:**</span><span class="sxs-lookup"><span data-stu-id="96d4f-171">**HTTP GET** request:</span></span>

    ```http
    GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
    ```

    <span data-ttu-id="96d4f-172">A **propriedade id** da resposta é `teamsAppInstallationId` .</span><span class="sxs-lookup"><span data-stu-id="96d4f-172">The **id** property of the response is the `teamsAppInstallationId`.</span></span>

1. <span data-ttu-id="96d4f-173">Faça a seguinte solicitação para buscar o `chatId` :</span><span class="sxs-lookup"><span data-stu-id="96d4f-173">Make the following request to fetch the `chatId`:</span></span>

    <span data-ttu-id="96d4f-174">**Solicitação GET** HTTP (permissão `TeamsAppInstallation.ReadWriteSelfForUser.All` — ):</span><span class="sxs-lookup"><span data-stu-id="96d4f-174">**HTTP GET** request (permission — `TeamsAppInstallation.ReadWriteSelfForUser.All`):</span></span>  

    ```http
    GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps/{teamsAppInstallationId}/chat
    ```

    <span data-ttu-id="96d4f-175">A **propriedade id** da resposta é `chatId` .</span><span class="sxs-lookup"><span data-stu-id="96d4f-175">The **id** property of the response is the `chatId`.</span></span>

    <span data-ttu-id="96d4f-176">Você também pode recuperar `chatId` o com a seguinte solicitação, mas ela exige a permissão mais `Chat.Read.All` ampla:</span><span class="sxs-lookup"><span data-stu-id="96d4f-176">You can also retrieve the `chatId` with the following request but it requires the broader `Chat.Read.All` permission:</span></span>

    <span data-ttu-id="96d4f-177">**Solicitação GET** HTTP (permissão `Chat.Read.All` — ):</span><span class="sxs-lookup"><span data-stu-id="96d4f-177">**HTTP GET** request (permission — `Chat.Read.All`):</span></span>

    ```http
    GET https://graph.microsoft.com/beta/users/{user-id}/chats?$filter=installedApps/any(a:a/teamsApp/id eq '{teamsAppId}')
    ```

### <a name="send-proactive-messages"></a><span data-ttu-id="96d4f-178">Enviar mensagens proativas</span><span class="sxs-lookup"><span data-stu-id="96d4f-178">Send proactive messages</span></span>

<span data-ttu-id="96d4f-179">Seu bot pode [enviar mensagens proativas](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true) depois que o bot foi adicionado para um usuário ou uma equipe e recebeu todas as informações do usuário.</span><span class="sxs-lookup"><span data-stu-id="96d4f-179">Your bot can [send proactive messages](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true) after the bot has been added for a user or a team, and has received all the user information.</span></span>

## <a name="code-sample"></a><span data-ttu-id="96d4f-180">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="96d4f-180">Code sample</span></span>

| <span data-ttu-id="96d4f-181">**Exemplo de nome**</span><span class="sxs-lookup"><span data-stu-id="96d4f-181">**Sample Name**</span></span> | <span data-ttu-id="96d4f-182">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="96d4f-182">**Description**</span></span> | <span data-ttu-id="96d4f-183">**.NET**</span><span class="sxs-lookup"><span data-stu-id="96d4f-183">**.NET**</span></span> | <span data-ttu-id="96d4f-184">**Node.js**</span><span class="sxs-lookup"><span data-stu-id="96d4f-184">**Node.js**</span></span> |
|---------------|--------------|--------|-------------|--------|
| <span data-ttu-id="96d4f-185">Instalação proativa do aplicativo e envio de notificações proativas</span><span class="sxs-lookup"><span data-stu-id="96d4f-185">Proactive installation of app and sending proactive notifications</span></span> | <span data-ttu-id="96d4f-186">Este exemplo mostra como você pode usar a instalação proativa do aplicativo para usuários e enviar notificações proativas chamando as APIs Graph Microsoft.</span><span class="sxs-lookup"><span data-stu-id="96d4f-186">This sample shows how you can use proactive installation of app for users and send proactive notifications by calling Microsoft Graph APIs.</span></span> | [<span data-ttu-id="96d4f-187">View</span><span class="sxs-lookup"><span data-stu-id="96d4f-187">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-proactive-installation/csharp) | [<span data-ttu-id="96d4f-188">View</span><span class="sxs-lookup"><span data-stu-id="96d4f-188">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-proactive-installation/nodejs) |

## <a name="see-also"></a><span data-ttu-id="96d4f-189">Confira também</span><span class="sxs-lookup"><span data-stu-id="96d4f-189">See also</span></span>

* [<span data-ttu-id="96d4f-190">**Gerenciar políticas de configuração de aplicativos Microsoft Teams**</span><span class="sxs-lookup"><span data-stu-id="96d4f-190">**Manage app setup policies in Microsoft Teams**</span></span>](/MicrosoftTeams/teams-app-setup-policies#create-a-custom-app-setup-policy)
* [<span data-ttu-id="96d4f-191">Enviar notificações proativas para usuários SDK v4</span><span class="sxs-lookup"><span data-stu-id="96d4f-191">Send proactive notifications to users SDK v4</span></span>](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true)

## <a name="additional-code-samples"></a><span data-ttu-id="96d4f-192">Exemplos de código adicionais</span><span class="sxs-lookup"><span data-stu-id="96d4f-192">Additional code samples</span></span>
>
> [!div class="nextstepaction"]
> [<span data-ttu-id="96d4f-193">**Teams exemplos proativos de código de mensagens**</span><span class="sxs-lookup"><span data-stu-id="96d4f-193">**Teams proactive messaging code samples**</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-proactive-messaging/csharp)
