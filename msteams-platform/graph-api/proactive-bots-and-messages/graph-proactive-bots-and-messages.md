---
title: Usar o Microsoft Graph para habilitar a instalação proativa de bot e mensagens no Microsoft Teams
description: Descreve as mensagens pró-ativas no Microsoft Teams e como implementar o.
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: Overview
keywords: Gráfico de instalação do chat de mensagens pró-ativas do teams
ms.openlocfilehash: 735dbfa39222f312b4f3714b5c009dfd1bf28b05
ms.sourcegitcommit: 1b909fb9ccf6cdd84ed0d8f9ea0463243a802a23
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "45434493"
---
# <a name="enable-proactive-bot-installation-and-proactive-messaging-in-teams-with-microsoft-graph-public-preview"></a><span data-ttu-id="f2118-104">Habilitar instalação de bot proativo e mensagens pró-ativas no Teams com o Microsoft Graph (visualização pública)</span><span class="sxs-lookup"><span data-stu-id="f2118-104">Enable proactive bot installation and proactive messaging in Teams with Microsoft Graph (Public Preview)</span></span>

>[!IMPORTANT]
> <span data-ttu-id="f2118-105">As visualizações públicas do Microsoft Graph estão disponíveis para acesso antecipado e comentários.</span><span class="sxs-lookup"><span data-stu-id="f2118-105">Microsoft Graph public previews are available for early-access and feedback.</span></span> <span data-ttu-id="f2118-106">Embora este lançamento tenha transcorrido testes extensivos, ele não se destina ao uso em produção.</span><span class="sxs-lookup"><span data-stu-id="f2118-106">Although this release has undergone extensive testing, it is not intended for use in production.</span></span>

## <a name="proactive-messaging-in-teams"></a><span data-ttu-id="f2118-107">Mensagens pró-ativas no Teams</span><span class="sxs-lookup"><span data-stu-id="f2118-107">Proactive messaging in Teams</span></span>

<span data-ttu-id="f2118-108">As mensagens pró-ativas são iniciadas por bots para iniciar conversas com um usuário.</span><span class="sxs-lookup"><span data-stu-id="f2118-108">Proactive messages are initiated by bots to start conversations with a users.</span></span> <span data-ttu-id="f2118-109">Eles atendem a vários propósitos, incluindo o envio de mensagens de boas-vindas, condução de pesquisas ou sondas e transmissão de notificações em toda a organização.</span><span class="sxs-lookup"><span data-stu-id="f2118-109">They serve many purposes including sending welcome messages, conducting surveys or polls, and broadcasting organization-wide notifications.</span></span>  <span data-ttu-id="f2118-110">As mensagens pró-ativas no Microsoft Teams podem ser fornecidas como conversas **ad-hoc** ou **baseadas em diálogo** :</span><span class="sxs-lookup"><span data-stu-id="f2118-110">Proactive messages in Teams can be delivered as either **ad-hoc** or **dialog-based** conversations:</span></span>

|<span data-ttu-id="f2118-111">Tipo de mensagem</span><span class="sxs-lookup"><span data-stu-id="f2118-111">Message Type</span></span> | <span data-ttu-id="f2118-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="f2118-112">Description</span></span> |
|----------------|-------------- |
|<span data-ttu-id="f2118-113">Mensagem pró-ativa ad-hoc</span><span class="sxs-lookup"><span data-stu-id="f2118-113">Ad-hoc proactive message</span></span>| <span data-ttu-id="f2118-114">O bot interjects uma mensagem sem interromper o fluxo de conversa.</span><span class="sxs-lookup"><span data-stu-id="f2118-114">The bot interjects a message without interrupting the conversation flow.</span></span>|
|<span data-ttu-id="f2118-115">Mensagem proativa baseada em caixa de diálogo</span><span class="sxs-lookup"><span data-stu-id="f2118-115">Dialog-based proactive message</span></span> | <span data-ttu-id="f2118-116">O bot cria um novo encadeamento de caixa de diálogo, assume o controle de uma conversa, entrega a mensagem proativa, fecha e retorna o controle para a caixa de diálogo anterior.</span><span class="sxs-lookup"><span data-stu-id="f2118-116">The bot creates a new dialog thread, takes control of a conversation, delivers the proactive message, closes, and returns control to the previous dialog.</span></span>|

<span data-ttu-id="f2118-117">*Ver*, [enviar notificações proativas para os usuários SDK v4](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp)</span><span class="sxs-lookup"><span data-stu-id="f2118-117">*See*, [Send proactive notifications to users SDK v4](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp)</span></span>

## <a name="proactive-app-installation-in-teams"></a><span data-ttu-id="f2118-118">Instalação de aplicativo proativo no Teams</span><span class="sxs-lookup"><span data-stu-id="f2118-118">Proactive app installation in Teams</span></span>

<span data-ttu-id="f2118-119">Antes que o bot possa proativamente mensagens de um usuário, ele precisa ser instalado como um aplicativo pessoal ou em uma equipe onde o usuário é membro.</span><span class="sxs-lookup"><span data-stu-id="f2118-119">Before your bot can proactively message a user, it needs to be installed either as a personal app, or in a team where the user is a member.</span></span> <span data-ttu-id="f2118-120">Às vezes, talvez você precise proativamente usuários de mensagens que _não_ tenham sido instaladas ou previamente interagindo com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f2118-120">At times,  you may need to proactively message users that have _not_ installed or previously interacted with your app.</span></span> <span data-ttu-id="f2118-121">Por exemplo, a necessidade de mensagens vitais para todas as pessoas em sua organização.</span><span class="sxs-lookup"><span data-stu-id="f2118-121">For instance, the need to message vital information to everyone in your organization.</span></span> <span data-ttu-id="f2118-122">Para esses cenários, você pode usar a API do Microsoft Graph para instalar proativamente seu bot para seus usuários.</span><span class="sxs-lookup"><span data-stu-id="f2118-122">For such scenarios, you can use the Microsoft Graph API to proactively install your bot for your users.</span></span>

## <a name="permissions"></a><span data-ttu-id="f2118-123">Permissões</span><span class="sxs-lookup"><span data-stu-id="f2118-123">Permissions</span></span>

<span data-ttu-id="f2118-124">As permissões de [tipo de recurso teamsAppInstallation](/graph/api/resources/teamsappinstallation?view=graph-rest-1.0) do Microsoft Graph permitem que você gerencie o ciclo de vida de instalação de seu aplicativo para todos os escopos de usuário (pessoal) ou de equipe (canal) na plataforma Microsoft Teams:</span><span class="sxs-lookup"><span data-stu-id="f2118-124">Microsoft Graph [teamsAppInstallation resource type](/graph/api/resources/teamsappinstallation?view=graph-rest-1.0) permissions allow you to manage your app's installation lifecycle for all user (personal) or team (channel) scopes within the Microsoft Teams platform:</span></span>

|<span data-ttu-id="f2118-125">Permissão de aplicativo</span><span class="sxs-lookup"><span data-stu-id="f2118-125">Application permission</span></span> | <span data-ttu-id="f2118-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="f2118-126">Description</span></span>|
|------------------|---------------------|
|`TeamsAppInstallation.ReadWriteSelfForUser.All`|<span data-ttu-id="f2118-127">Permite que um aplicativo do teams Leia, instale, atualize e desinstale a si mesmo para qualquer **usuário**, sem entrar ou usar o anterior.</span><span class="sxs-lookup"><span data-stu-id="f2118-127">Allows a Teams app to read, install, upgrade, and uninstall itself for any **user**, without prior sign in or use.</span></span>|
|`TeamsAppInstallation.ReadWriteSelfForTeam.All`|<span data-ttu-id="f2118-128">Permite que o aplicativo de equipes Leia, instale, atualize e desinstale em qualquer **equipe**, sem entrar ou usar o anterior.</span><span class="sxs-lookup"><span data-stu-id="f2118-128">Allows a Teams app to read, install, upgrade, and uninstall itself in any **team**, without prior sign in or use.</span></span>|

<span data-ttu-id="f2118-129">Para usar essas permissões, você deve adicionar uma chave de [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) ao manifesto do aplicativo com os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="f2118-129">To use these permissions, you must add a [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) key to your app manifest with the following values:</span></span>
> [!div class="checklist"]
> [!div class="checklist"]
>
> * <span data-ttu-id="f2118-130">**ID** — sua ID de aplicativo do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="f2118-130">**id**  — your Azure AD app id.</span></span>
> * <span data-ttu-id="f2118-131">**recurso** — a URL do recurso para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f2118-131">**resource** — the resource URL for the app.</span></span>
>

>[!NOTE]
>
> * <span data-ttu-id="f2118-132">Seu bot requer permissões _delegadas do usuário_ do _aplicativo_ , pois a instalação não é para você mesmo, mas para outros.</span><span class="sxs-lookup"><span data-stu-id="f2118-132">Your bot requires _application_ not _user delegated_ permissions because the installation is not for yourself but for others.</span></span>
>
> * <span data-ttu-id="f2118-133">Um administrador de locatários do Azure AD deve [conceder explicitamente permissões a um aplicativo](/graph/security-authorization#grant-permissions-to-an-application).</span><span class="sxs-lookup"><span data-stu-id="f2118-133">An Azure AD tenant administrator must [explicitly grant permissions to an application](/graph/security-authorization#grant-permissions-to-an-application).</span></span> <span data-ttu-id="f2118-134">Depois que um aplicativo recebe permissões, _todos_ os membros do locatário do Azure ad obterão as permissões concedidas.</span><span class="sxs-lookup"><span data-stu-id="f2118-134">After an application is granted permissions, _all_ members of the Azure AD tenant will gain the granted permissions.</span></span>

## <a name="enable-proactive-app-installation-and-messaging"></a><span data-ttu-id="f2118-135">Habilitar a instalação e mensagens proativas de aplicativos</span><span class="sxs-lookup"><span data-stu-id="f2118-135">Enable proactive app installation and messaging</span></span>

 > [!IMPORTANT]
><span data-ttu-id="f2118-136">O Microsoft Graph só instalará aplicativos publicados no catálogo de [aplicativos](../../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) da sua organização ou no [AppSource](https://appsource.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="f2118-136">Microsoft Graph will only install apps published within your organization's [app catalog](../../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) or in [AppSource](https://appsource.microsoft.com/).</span></span>

### <a name="-create-and-publish-your-proactive-messaging-bot-for-teams"></a><span data-ttu-id="f2118-137">✔ Criar e publicar seu bot de mensagens pró-ativas para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="f2118-137">✔ Create and publish your proactive messaging bot for Teams</span></span>

<span data-ttu-id="f2118-138">Para começar, você precisará de um [bot para o Microsoft Teams](../../bots/how-to/create-a-bot-for-teams.md) com recursos [proativos de mensagens](../../concepts/bots/bot-conversations/bots-conv-proactive.md) e [publicado](../../concepts/deploy-and-publish/overview.md) no [Catálogo de aplicativos](../../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) da sua organização ou no [AppSource](https://appsource.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="f2118-138">To get started, you will need a [bot for Teams](../../bots/how-to/create-a-bot-for-teams.md) with [proactive messaging](../../concepts/bots/bot-conversations/bots-conv-proactive.md) capabilities and  [published](../../concepts/deploy-and-publish/overview.md) in your organization's [app catalog](../../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) or in [AppSource](https://appsource.microsoft.com/).</span></span>

>[!TIP]
> <span data-ttu-id="f2118-139">O modelo de aplicativo do [**Communicator da empresa**](../..//samples/app-templates.md#company-communicator) pronto para produção permite transmissão de mensagens e é uma boa base para criar seu aplicativo de bot proativo.</span><span class="sxs-lookup"><span data-stu-id="f2118-139">The production-ready [**Company Communicator**](../..//samples/app-templates.md#company-communicator) app template enables broadcast messaging and is a good foundation for building your proactive bot application.</span></span>

### <a name="-get-the-teamsappid-for-your-app"></a><span data-ttu-id="f2118-140">✔ Obter o `teamsAppId` para seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="f2118-140">✔ Get the `teamsAppId` for your app</span></span>

<span data-ttu-id="f2118-141">**1.** você precisará das `teamsAppId` próximas etapas.</span><span class="sxs-lookup"><span data-stu-id="f2118-141">**1.** You will need the `teamsAppId`  for the next steps.</span></span>

<span data-ttu-id="f2118-142">O `teamsAppId` pode ser recuperado do catálogo de aplicativos da sua organização:</span><span class="sxs-lookup"><span data-stu-id="f2118-142">The `teamsAppId` can be retrieved from your organization's app catalog:</span></span>

<span data-ttu-id="f2118-143">**Referência de página do Microsoft Graph:** [tipo de recurso teamsApp](/graph/api/resources/teamsapp?view=graph-rest-1.0)</span><span class="sxs-lookup"><span data-stu-id="f2118-143">**Microsoft Graph page reference:** [teamsApp resource type](/graph/api/resources/teamsapp?view=graph-rest-1.0)</span></span>

<span data-ttu-id="f2118-144">Solicitação **http Get** :</span><span class="sxs-lookup"><span data-stu-id="f2118-144">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/appCatalogs/teamsApps?$filter=externalId eq '{IdFromManifest}'
```

<span data-ttu-id="f2118-145">A solicitação retornará um `teamsApp` objeto.</span><span class="sxs-lookup"><span data-stu-id="f2118-145">The request will return a `teamsApp`  object.</span></span> <span data-ttu-id="f2118-146">O objeto retornado `id` é a ID do aplicativo gerado pelo catálogo do aplicativo e é diferente do "ID:" que você forneceu no manifesto do aplicativo do Microsoft Teams:</span><span class="sxs-lookup"><span data-stu-id="f2118-146">The returned object's `id`  is the app's catalog generated app id and is different from the "id:" that you provided in your Teams app manifest:</span></span>

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

<span data-ttu-id="f2118-147">**2.** se seu aplicativo já foi carregado/suplementos foi feito para um usuário no escopo pessoal, você pode recuperar o da `teamsAppId` seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="f2118-147">**2.**  If your app has already been uploaded/sideloaded for a user in the personal scope, you can retrieve the `teamsAppId` as follows:</span></span>

<span data-ttu-id="f2118-148">**Referência de página do Microsoft Graph:** [listar aplicativos instalados para o usuário](/graph/api/user-list-teamsappinstallation?view=graph-rest-beta&tabs=http)</span><span class="sxs-lookup"><span data-stu-id="f2118-148">**Microsoft Graph page reference:** [List apps installed for user](/graph/api/user-list-teamsappinstallation?view=graph-rest-beta&tabs=http)</span></span>

<span data-ttu-id="f2118-149">Solicitação **http Get** :</span><span class="sxs-lookup"><span data-stu-id="f2118-149">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

<span data-ttu-id="f2118-150">**3.** se seu aplicativo já tiver sido carregado/suplementos foi feito para um canal no escopo da equipe, você poderá recuperar o da `teamsAppId` seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="f2118-150">**3.** If your app has already been uploaded/sideloaded for a channel in the team scope, you can retrieve the `teamsAppId` as follows:</span></span>

<span data-ttu-id="f2118-151">**Referência de página do Microsoft Graph:** [listar aplicativos no Team](/graph/api/teamsappinstallation-list?view=graph-rest-beta&tabs=http)</span><span class="sxs-lookup"><span data-stu-id="f2118-151">**Microsoft Graph page reference:** [List apps in team](/graph/api/teamsappinstallation-list?view=graph-rest-beta&tabs=http)</span></span>

<span data-ttu-id="f2118-152">Solicitação **http Get** :</span><span class="sxs-lookup"><span data-stu-id="f2118-152">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/beta/teams/{team-id}/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{manifestId}'
```

>[!TIP]
> <span data-ttu-id="f2118-153">Você pode filtrar em qualquer um dos campos do objeto [**teamsApp**](/graph/api/resources/teamsapp?view=graph-rest-1.0) para restringir a lista de resultados.</span><span class="sxs-lookup"><span data-stu-id="f2118-153">You can filter on any of the fields of the [**teamsApp**](/graph/api/resources/teamsapp?view=graph-rest-1.0) object to narrow the list of results.</span></span>

### <a name="-determine-whether-your-bot-is-currently-installed-for-a-message-recipient"></a><span data-ttu-id="f2118-154">✔ Determinar se o seu bot está instalado atualmente para um destinatário de mensagem</span><span class="sxs-lookup"><span data-stu-id="f2118-154">✔ Determine whether your bot is currently installed for a message recipient</span></span>

<span data-ttu-id="f2118-155">**Referência de página do Microsoft Graph:** [listar aplicativos instalados para o usuário](/graph/api/user-list-teamsappinstallation?view=graph-rest-beta&tabs=http)</span><span class="sxs-lookup"><span data-stu-id="f2118-155">**Microsoft Graph page reference:** [List apps installed for user](/graph/api/user-list-teamsappinstallation?view=graph-rest-beta&tabs=http)</span></span>

<span data-ttu-id="f2118-156">Solicitação **http Get** :</span><span class="sxs-lookup"><span data-stu-id="f2118-156">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

<span data-ttu-id="f2118-157">Essa solicitação retornará uma matriz vazia se o aplicativo não estiver instalado, ou uma matriz com um único objeto [teamsAppInstallation](/graph/api/resources/teamsappinstallation?view=graph-rest-beta) , se tiver sido instalado.</span><span class="sxs-lookup"><span data-stu-id="f2118-157">This request will return an empty array if the app is not installed, or an array with a single [teamsAppInstallation](/graph/api/resources/teamsappinstallation?view=graph-rest-beta) object if it has been installed.</span></span>

### <a name="-install-your-app"></a><span data-ttu-id="f2118-158">✔ Instalar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="f2118-158">✔ Install your app</span></span>

<span data-ttu-id="f2118-159">**Referência do Microsoft Graph: instalar o** [aplicativo para o usuário](/graph/api/user-add-teamsappinstallation?view=graph-rest-beta&tabs=http)</span><span class="sxs-lookup"><span data-stu-id="f2118-159">**Microsoft Graph reference:** [Install app for user](/graph/api/user-add-teamsappinstallation?view=graph-rest-beta&tabs=http)</span></span>

<span data-ttu-id="f2118-160">Solicitação **http post** :</span><span class="sxs-lookup"><span data-stu-id="f2118-160">**HTTP POST** request:</span></span>

```http
POST https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps
{
   "teamsApp@odata.bind" : "https://graph.microsoft.com/beta/appCatalogs/teamsApps/{teamsAppId}"
}
```

<span data-ttu-id="f2118-161">Se o usuário tiver o Microsoft Teams em execução, ele poderá ver a instalação do aplicativo imediatamente.</span><span class="sxs-lookup"><span data-stu-id="f2118-161">If the user has Microsoft Teams running, they may see the app install immediately.</span></span> <span data-ttu-id="f2118-162">Como alternativa, pode ser necessário reinicializar para ver o aplicativo instalado.</span><span class="sxs-lookup"><span data-stu-id="f2118-162">Alternatively,  a  restart may be necessary to see the installed app.</span></span>

### <a name="-retrieve-the-conversation-chatid"></a><span data-ttu-id="f2118-163">✔ Recuperar o **chat** de conversa</span><span class="sxs-lookup"><span data-stu-id="f2118-163">✔ Retrieve the conversation **chatId**</span></span>

<span data-ttu-id="f2118-164">Quando seu aplicativo for instalado para o usuário, o bot receberá uma `conversationUpdate` [notificação de eventos](../../resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) que conterá as informações necessárias para enviar a mensagem proativa.</span><span class="sxs-lookup"><span data-stu-id="f2118-164">When your app is installed for the user, the bot will receive a `conversationUpdate` [event notification](../../resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) that will contain the necessary information to send the proactive message.</span></span>

<span data-ttu-id="f2118-165">O `chatId` também pode ser recuperado da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="f2118-165">The `chatId` can also be retrieved as follows:</span></span>

<span data-ttu-id="f2118-166">**Referência do Microsoft Graph:** [obter chat](/graph/api/chat-get?view=graph-rest-beta&tabs=http)</span><span class="sxs-lookup"><span data-stu-id="f2118-166">**Microsoft Graph reference:** [Get chat](/graph/api/chat-get?view=graph-rest-beta&tabs=http)</span></span>

<span data-ttu-id="f2118-167">**1.** você precisará do seu aplicativo `{teamsAppInstallationId}` se não o tiver, use o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f2118-167">**1.** You will need your app's `{teamsAppInstallationId}` If you don't have it, use the following:</span></span>

<span data-ttu-id="f2118-168">Solicitação **http Get** :</span><span class="sxs-lookup"><span data-stu-id="f2118-168">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

<span data-ttu-id="f2118-169">A propriedade **ID** da resposta é o `teamsAppInstallationId` .</span><span class="sxs-lookup"><span data-stu-id="f2118-169">The **id** property of the response is the `teamsAppInstallationId`.</span></span>

<span data-ttu-id="f2118-170">**2.** faça a seguinte solicitação para buscar `chatId` :</span><span class="sxs-lookup"><span data-stu-id="f2118-170">**2.** Make the following request to fetch the `chatId`:</span></span>

<span data-ttu-id="f2118-171">Solicitação **http Get** (permissão – `TeamsAppInstallation.ReadWriteSelfForUser.All` ):</span><span class="sxs-lookup"><span data-stu-id="f2118-171">**HTTP GET** request (permission — `TeamsAppInstallation.ReadWriteSelfForUser.All`):</span></span>  

```http
 GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps/{teamsAppInstallationId}/chat
```

<span data-ttu-id="f2118-172">A propriedade **ID** da resposta é o `chatId` .</span><span class="sxs-lookup"><span data-stu-id="f2118-172">The **id** property of the response is the `chatId`.</span></span>

<span data-ttu-id="f2118-173">Como alternativa, você pode recuperar o `chatId` com a solicitação abaixo, mas ele exigirá a permissão mais ampla `Chat.Read.All` :</span><span class="sxs-lookup"><span data-stu-id="f2118-173">Alternately, you can retrieve the `chatId`  with the request below, but it will require the broader `Chat.Read.All` permission:</span></span>

<span data-ttu-id="f2118-174">Solicitação **http Get** (permissão – `Chat.Read.All` ):</span><span class="sxs-lookup"><span data-stu-id="f2118-174">**HTTP GET** request (permission — `Chat.Read.All`):</span></span>

```http
GET https://graph.microsoft.com/beta/users/{user-id}/chats?$filter=installedApps/any(a:a/teamsApp/id eq '{teamsAppId}')
```

### <a name="-send-proactive-messages"></a><span data-ttu-id="f2118-175">✔ Enviar mensagens pró-ativas</span><span class="sxs-lookup"><span data-stu-id="f2118-175">✔ Send proactive messages</span></span>

<span data-ttu-id="f2118-176">Depois que o bot for adicionado para um usuário ou uma equipe e tiver adquirido as informações necessárias do usuário, ele poderá começar a [enviar mensagens pró-ativas](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp).</span><span class="sxs-lookup"><span data-stu-id="f2118-176">Once your bot has been added for a user or team and has acquired the necessary user  information, it can begin to [send proactive messages](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp).</span></span>

# <a name="c--net"></a>[<span data-ttu-id="f2118-177">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="f2118-177">C# / .NET</span></span>](#tab/csharp)

<span data-ttu-id="f2118-178">O trecho de código a seguir é do [Microsoft bot Framework Samples for C#.](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/16.proactive-messages)</span><span class="sxs-lookup"><span data-stu-id="f2118-178">The following code snippet is from the [Microsoft Bot Framework Samples for C#.](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/16.proactive-messages)</span></span>

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

# <a name="javascript"></a>[<span data-ttu-id="f2118-179">JavaScript</span><span class="sxs-lookup"><span data-stu-id="f2118-179">JavaScript</span></span>](#tab/javascript)

<span data-ttu-id="f2118-180">O trecho de código a seguir é proveniente dos [exemplos da Microsoft bot Framework para JavaScript](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/16.proactive-messages).</span><span class="sxs-lookup"><span data-stu-id="f2118-180">The following code snippet is from the [Microsoft Bot Framework Samples for JavaScript](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/16.proactive-messages).</span></span>

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

## <a name="related-topic-for-teams-administrators"></a><span data-ttu-id="f2118-181">Tópico relacionado para administradores do teams</span><span class="sxs-lookup"><span data-stu-id="f2118-181">Related topic for Teams administrators</span></span>
>
> [!div class="nextstepaction"]
> [<span data-ttu-id="f2118-182">**Gerenciar políticas de configuração de aplicativos no Microsoft Teams**</span><span class="sxs-lookup"><span data-stu-id="f2118-182">**Manage app setup policies in Microsoft Teams**</span></span>](/MicrosoftTeams/teams-app-setup-policies#create-a-custom-app-setup-policy)

## <a name="view-additional-code-samples"></a><span data-ttu-id="f2118-183">Exibir exemplos de código adicionais</span><span class="sxs-lookup"><span data-stu-id="f2118-183">View additional code samples</span></span>
>
> [!div class="nextstepaction"]
> [<span data-ttu-id="f2118-184">**Amostras de código de mensagens proativas do teams**</span><span class="sxs-lookup"><span data-stu-id="f2118-184">**Teams proactive messaging code samples**</span></span>](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)
>