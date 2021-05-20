---
title: Use o Microsoft Graph para autorizar a instalação e a troca de mensagens proativas de bots em Teams
description: Descreve mensagens proativas em Teams e como implementar.
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: Overview
keywords: equipes de instalação de chat de mensagens proativas Graph
ms.openlocfilehash: 06b50e5ab8594c257959430383bab5e355af4e06
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566149"
---
# <a name="proactive-installation-of-apps-using-graph-api-and-send-messages"></a><span data-ttu-id="8feba-104">Instalação proativa de aplicativos usando a API do Graph e enviar mensagens</span><span class="sxs-lookup"><span data-stu-id="8feba-104">Proactive installation of apps using Graph API and send messages</span></span>

>[!IMPORTANT]
> <span data-ttu-id="8feba-105">As Graph da Microsoft e Microsoft Teams visualizações públicas estão disponíveis para acesso antecipado e feedback.</span><span class="sxs-lookup"><span data-stu-id="8feba-105">Microsoft Graph and Microsoft Teams public previews are available for early access and feedback.</span></span> <span data-ttu-id="8feba-106">Embora esta versão tenha sido submetida a testes extensivos, não se destina a ser usada na produção.</span><span class="sxs-lookup"><span data-stu-id="8feba-106">Although this release has undergone extensive testing, it is not intended for use in production.</span></span>

## <a name="proactive-messaging-in-teams"></a><span data-ttu-id="8feba-107">Mensagens proativas em Teams</span><span class="sxs-lookup"><span data-stu-id="8feba-107">Proactive messaging in Teams</span></span>

<span data-ttu-id="8feba-108">Mensagens proativas são iniciadas por bots para iniciar conversas com um usuário.</span><span class="sxs-lookup"><span data-stu-id="8feba-108">Proactive messages are initiated by bots to start conversations with a user.</span></span> <span data-ttu-id="8feba-109">Eles servem a muitos propósitos, incluindo o envio de mensagens de boas-vindas, a realização de pesquisas ou pesquisas e a transmissão de notificações em toda a organização.</span><span class="sxs-lookup"><span data-stu-id="8feba-109">They serve many purposes including sending welcome messages, conducting surveys or polls, and broadcasting organization-wide notifications.</span></span> <span data-ttu-id="8feba-110">Mensagens proativas em Teams podem ser entregues como conversas **baseadas em** **ad-hoc** ou dialogas:</span><span class="sxs-lookup"><span data-stu-id="8feba-110">Proactive messages in Teams can be delivered as either **ad-hoc** or **dialog-based** conversations:</span></span>

|<span data-ttu-id="8feba-111">Tipo de mensagem</span><span class="sxs-lookup"><span data-stu-id="8feba-111">Message Type</span></span> | <span data-ttu-id="8feba-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="8feba-112">Description</span></span> |
|----------------|-------------- |
|<span data-ttu-id="8feba-113">Mensagem proativa ad-hoc</span><span class="sxs-lookup"><span data-stu-id="8feba-113">Ad-hoc proactive message</span></span>| <span data-ttu-id="8feba-114">O bot interjece uma mensagem sem interromper o fluxo de conversa.</span><span class="sxs-lookup"><span data-stu-id="8feba-114">The bot interjects a message without interrupting the conversation flow.</span></span>|
|<span data-ttu-id="8feba-115">Mensagem proativa baseada em diálogo</span><span class="sxs-lookup"><span data-stu-id="8feba-115">Dialog-based proactive message</span></span> | <span data-ttu-id="8feba-116">O bot cria um novo segmento de diálogo, assume o controle de uma conversa, entrega a mensagem proativa, fecha e retorna o controle ao diálogo anterior.</span><span class="sxs-lookup"><span data-stu-id="8feba-116">The bot creates a new dialog thread, takes control of a conversation, delivers the proactive message, closes, and returns control to the previous dialog.</span></span>|

## <a name="proactive-app-installation-in-teams"></a><span data-ttu-id="8feba-117">Instalação proativa de aplicativos em Teams</span><span class="sxs-lookup"><span data-stu-id="8feba-117">Proactive app installation in Teams</span></span>

<span data-ttu-id="8feba-118">Antes que seu bot possa enviar uma mensagem proativa para um usuário, ele deve ser instalado como um aplicativo pessoal ou em uma equipe onde o usuário é um membro.</span><span class="sxs-lookup"><span data-stu-id="8feba-118">Before your bot can proactively message a user, it must be installed either as a personal app or in a team where the user is a member.</span></span> <span data-ttu-id="8feba-119">Às vezes, você precisa enviar mensagens proativas aos usuários que não instalaram ou interagiram anteriormente com o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8feba-119">At times, you need to proactively message users that have not installed or previously interacted with your app.</span></span> <span data-ttu-id="8feba-120">Por exemplo, a necessidade de enviar informações vitais para todos em sua organização.</span><span class="sxs-lookup"><span data-stu-id="8feba-120">For example, the need to message vital information to everyone in your organization.</span></span> <span data-ttu-id="8feba-121">Para tais cenários, você pode usar a API Graph Microsoft para instalar proativamente seu bot para seus usuários.</span><span class="sxs-lookup"><span data-stu-id="8feba-121">For such scenarios, you can use the Microsoft Graph API to proactively install your bot for your users.</span></span>

## <a name="permissions"></a><span data-ttu-id="8feba-122">Permissões</span><span class="sxs-lookup"><span data-stu-id="8feba-122">Permissions</span></span>

<span data-ttu-id="8feba-123">As permissões de tipo de recurso do Microsoft [Graph AppInstallation](/graph/api/resources/teamsappinstallation?view=graph-rest-1.0&preserve-view=true) ajudam você a gerenciar o ciclo de vida de instalação do seu aplicativo para todos os escopos de usuário (pessoal) ou equipe (canal) dentro da plataforma Microsoft Teams:</span><span class="sxs-lookup"><span data-stu-id="8feba-123">Microsoft Graph [teamsAppInstallation resource type](/graph/api/resources/teamsappinstallation?view=graph-rest-1.0&preserve-view=true) permissions helps you to manage your app's installation lifecycle for all user (personal) or team (channel) scopes within the Microsoft Teams platform:</span></span>

|<span data-ttu-id="8feba-124">Permissão de aplicativo</span><span class="sxs-lookup"><span data-stu-id="8feba-124">Application permission</span></span> | <span data-ttu-id="8feba-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="8feba-125">Description</span></span>|
|------------------|---------------------|
|`TeamsAppInstallation.ReadWriteSelfForUser.All`|<span data-ttu-id="8feba-126">Permite que um aplicativo Teams leia, instale, atualize e desinstale para qualquer **usuário**, sem login ou uso prévio.</span><span class="sxs-lookup"><span data-stu-id="8feba-126">Allows a Teams app to read, install, upgrade, and uninstall itself for any **user**, without prior sign in or use.</span></span>|
|`TeamsAppInstallation.ReadWriteSelfForTeam.All`|<span data-ttu-id="8feba-127">Permite que um aplicativo Teams leia, instale, atualize e desinstale em qualquer **equipe**, sem login ou uso prévio.</span><span class="sxs-lookup"><span data-stu-id="8feba-127">Allows a Teams app to read, install, upgrade, and uninstall itself in any **team**, without prior sign in or use.</span></span>|

<span data-ttu-id="8feba-128">Para usar essas permissões, você deve adicionar uma chave [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) ao seu manifesto de aplicativo com os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="8feba-128">To use these permissions, you must add a [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) key to your app manifest with the following values:</span></span>
> [!div class="checklist"]
> [!div class="checklist"]
>
> * <span data-ttu-id="8feba-129">**id** — seu ID do aplicativo Azure AD.</span><span class="sxs-lookup"><span data-stu-id="8feba-129">**id** — your Azure AD app ID.</span></span>
> * <span data-ttu-id="8feba-130">**recurso** — a URL de recurso para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8feba-130">**resource** — the resource URL for the app.</span></span>
>
>[!NOTE]
>
> * <span data-ttu-id="8feba-131">Seu bot requer aplicação e não permissões delegadas pelo usuário porque a instalação é para outros.</span><span class="sxs-lookup"><span data-stu-id="8feba-131">Your bot requires application and not user delegated permissions because the installation is for others.</span></span>
>
> * <span data-ttu-id="8feba-132">Um administrador de inquilinos do Azure AD deve [conceder explicitamente permissões a um aplicativo](/graph/security-authorization#grant-permissions-to-an-application).</span><span class="sxs-lookup"><span data-stu-id="8feba-132">An Azure AD tenant administrator must [explicitly grant permissions to an application](/graph/security-authorization#grant-permissions-to-an-application).</span></span> <span data-ttu-id="8feba-133">Após uma solicitação ser concedida permissões, todos os membros do inquilino Azure AD ganham as permissões concedidas.</span><span class="sxs-lookup"><span data-stu-id="8feba-133">After an application is granted permissions, all members of the Azure AD tenant gain the granted permissions.</span></span>

## <a name="enable-proactive-app-installation-and-messaging"></a><span data-ttu-id="8feba-134">Habilite a instalação e as mensagens proativas do aplicativo</span><span class="sxs-lookup"><span data-stu-id="8feba-134">Enable proactive app installation and messaging</span></span>

> [!IMPORTANT]
><span data-ttu-id="8feba-135">A Microsoft Graph só pode instalar aplicativos publicados na loja de aplicativos da sua organização ou na loja de Teams.</span><span class="sxs-lookup"><span data-stu-id="8feba-135">Microsoft Graph can only install apps published to your organization's app store or the Teams store.</span></span>

### <a name="-create-and-publish-your-proactive-messaging-bot-for-teams"></a><span data-ttu-id="8feba-136">✔ Crie e publique seu bot de mensagens proativo para Teams</span><span class="sxs-lookup"><span data-stu-id="8feba-136">✔ Create and publish your proactive messaging bot for Teams</span></span>

<span data-ttu-id="8feba-137">Para começar, você precisa de um [bot para Teams](../../bots/how-to/create-a-bot-for-teams.md) com recursos [proativos de mensagens](../../concepts/bots/bot-conversations/bots-conv-proactive.md) que estão na [loja de aplicativos da](../../concepts/deploy-and-publish/apps-publish-overview.md#publish-your-app-to-your-org) sua organização ou na loja [de Teams](../../concepts/deploy-and-publish/apps-publish-overview.md#publish-your-app-to-the-teams-store).</span><span class="sxs-lookup"><span data-stu-id="8feba-137">To get started, you need a [bot for Teams](../../bots/how-to/create-a-bot-for-teams.md) with [proactive messaging](../../concepts/bots/bot-conversations/bots-conv-proactive.md) capabilities that's in your [organization's app store](../../concepts/deploy-and-publish/apps-publish-overview.md#publish-your-app-to-your-org) or the [Teams store](../../concepts/deploy-and-publish/apps-publish-overview.md#publish-your-app-to-the-teams-store).</span></span>

>[!TIP]
> <span data-ttu-id="8feba-138">A empresa pronta para produção [**Communicator**](../..//samples/app-templates.md#company-communicator) modelo de aplicativo permite mensagens de transmissão e é uma boa base para a construção de seu aplicativo de bot proativo.</span><span class="sxs-lookup"><span data-stu-id="8feba-138">The production-ready [**Company Communicator**](../..//samples/app-templates.md#company-communicator) app template permits broadcast messaging and is a good foundation for building your proactive bot application.</span></span>

### <a name="-get-the-teamsappid-for-your-app"></a><span data-ttu-id="8feba-139">✔ Obter o para o `teamsAppId` seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="8feba-139">✔ Get the `teamsAppId` for your app</span></span>

<span data-ttu-id="8feba-140">**1.** Você precisa dos `teamsAppId` próximos passos.</span><span class="sxs-lookup"><span data-stu-id="8feba-140">**1.** You need the `teamsAppId` for the next steps.</span></span>

<span data-ttu-id="8feba-141">O `teamsAppId` pode ser recuperado do catálogo de aplicativos da sua organização:</span><span class="sxs-lookup"><span data-stu-id="8feba-141">The `teamsAppId` can be retrieved from your organization's app catalog:</span></span>

<span data-ttu-id="8feba-142">**Referência de página Graph da Microsoft:** [timesApp tipo de recurso](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="8feba-142">**Microsoft Graph page reference:** [teamsApp resource type](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true)</span></span>

<span data-ttu-id="8feba-143">**HTTP OBTER** solicitação:</span><span class="sxs-lookup"><span data-stu-id="8feba-143">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/v1.0/appCatalogs/teamsApps?$filter=externalId eq '{IdFromManifest}'
```

<span data-ttu-id="8feba-144">O pedido deve retornar um `teamsApp` objeto.</span><span class="sxs-lookup"><span data-stu-id="8feba-144">The request must return a `teamsApp` object.</span></span> <span data-ttu-id="8feba-145">O objeto retornado `id` é o ID do aplicativo gerado pelo catálogo do aplicativo e é diferente do ID que você forneceu no manifesto do aplicativo Teams:</span><span class="sxs-lookup"><span data-stu-id="8feba-145">The returned object `id` is the app's catalog generated app ID and is different from the ID that you provided in your Teams app manifest:</span></span>

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

<span data-ttu-id="8feba-146">**2.**  Se o seu aplicativo já tiver sido carregado ou carregado lateralmente para um usuário no escopo pessoal, você pode recuperar o `teamsAppId` seguinte:</span><span class="sxs-lookup"><span data-stu-id="8feba-146">**2.**  If your app has already been uploaded or sideloaded for a user in the personal scope, you can retrieve the `teamsAppId` as follows:</span></span>

<span data-ttu-id="8feba-147">**Referência de página Graph da Microsoft:** [liste aplicativos instalados para o usuário](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="8feba-147">**Microsoft Graph page reference:** [List apps installed for user](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span></span>

<span data-ttu-id="8feba-148">**HTTP OBTER** solicitação:</span><span class="sxs-lookup"><span data-stu-id="8feba-148">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
```

<span data-ttu-id="8feba-149">**3.** Se o seu aplicativo tiver sido carregado ou carregado lateralmente para um canal no escopo da equipe, você pode recuperar o `teamsAppId` seguinte:</span><span class="sxs-lookup"><span data-stu-id="8feba-149">**3.** If your app has been uploaded or sideloaded for a channel in the team scope, you can retrieve the `teamsAppId` as follows:</span></span>

<span data-ttu-id="8feba-150">**Referência de página Graph da Microsoft:** [liste aplicativos em equipe](/graph/api/team-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="8feba-150">**Microsoft Graph page reference:** [List apps in team](/graph/api/team-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span></span>

<span data-ttu-id="8feba-151">**HTTP OBTER** solicitação:</span><span class="sxs-lookup"><span data-stu-id="8feba-151">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/v1.0/teams/{team-id}/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
```

>[!TIP]
> <span data-ttu-id="8feba-152">Para reduzir a lista de resultados, você pode filtrar em qualquer um dos campos do objeto [**TeamApp.**](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="8feba-152">To narrow the list of results, you can filter on any of the fields of [**teamsApp**](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true) object.</span></span>

### <a name="-determine-whether-your-bot-is-currently-installed-for-a-message-recipient"></a><span data-ttu-id="8feba-153">✔ Determinar se o bot está instalado no momento para um destinatário de mensagens</span><span class="sxs-lookup"><span data-stu-id="8feba-153">✔ Determine whether your bot is currently installed for a message recipient</span></span>

<span data-ttu-id="8feba-154">**Referência de página Graph da Microsoft:** [liste aplicativos instalados para o usuário](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="8feba-154">**Microsoft Graph page reference:** [List apps installed for user](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span></span>

<span data-ttu-id="8feba-155">**HTTP OBTER** solicitação:</span><span class="sxs-lookup"><span data-stu-id="8feba-155">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

<span data-ttu-id="8feba-156">Esta solicitação retorna uma matriz vazia se o aplicativo não estiver instalado e um array com um único objeto [de configuração do TimesAppInstallation](/graph/api/resources/teamsappinstallation?view=graph-rest-v1.0&preserve-view=true) se o aplicativo estiver instalado.</span><span class="sxs-lookup"><span data-stu-id="8feba-156">This request returns an empty array if the app is not installed and an array with a single [teamsAppInstallation](/graph/api/resources/teamsappinstallation?view=graph-rest-v1.0&preserve-view=true) object if the app is installed.</span></span>

### <a name="-install-your-app"></a><span data-ttu-id="8feba-157">✔ Instale seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="8feba-157">✔ Install your app</span></span>

<span data-ttu-id="8feba-158">**Referência de página Graph da Microsoft:** [Instale aplicativo para usuário](/graph/api/userteamwork-post-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="8feba-158">**Microsoft Graph page reference:** [Install app for user](/graph/api/userteamwork-post-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span></span>

<span data-ttu-id="8feba-159">**SOLICITAÇÃO HTTP POST:**</span><span class="sxs-lookup"><span data-stu-id="8feba-159">**HTTP POST** request:</span></span>

```http
POST https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps
Content-Type: application/json

{
   "teamsApp@odata.bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/{teamsAppId}"
}
```

<span data-ttu-id="8feba-160">Se o usuário tiver Microsoft Teams em execução, a instalação do aplicativo será vista imediatamente.</span><span class="sxs-lookup"><span data-stu-id="8feba-160">If the user has Microsoft Teams running, app installation is seen immediately.</span></span> <span data-ttu-id="8feba-161">Uma reinicialização pode ser necessária para visualizar o aplicativo instalado.</span><span class="sxs-lookup"><span data-stu-id="8feba-161">A restart may be required to view the installed app.</span></span>

### <a name="-retrieve-the-conversation-chatid"></a><span data-ttu-id="8feba-162">✔ Recuperar o **chat de** conversa</span><span class="sxs-lookup"><span data-stu-id="8feba-162">✔ Retrieve the conversation **chatId**</span></span>

<span data-ttu-id="8feba-163">Quando seu aplicativo é instalado para o usuário, o bot recebe uma `conversationUpdate` [notificação de evento](../../resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) que contém as informações necessárias para enviar a mensagem proativa.</span><span class="sxs-lookup"><span data-stu-id="8feba-163">When your app is installed for the user, the bot receives a `conversationUpdate` [event notification](../../resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) that contains the necessary information to send the proactive message.</span></span>

<span data-ttu-id="8feba-164">O `chatId` também pode ser recuperado da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="8feba-164">The `chatId` can also be retrieved as follows:</span></span>

<span data-ttu-id="8feba-165">**Referência de página Graph da Microsoft:** [obtenha bate-papo](/graph/api/chat-get?view=graph-rest-beta&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="8feba-165">**Microsoft Graph page reference:** [Get chat](/graph/api/chat-get?view=graph-rest-beta&tabs=http&preserve-view=true)</span></span>

<span data-ttu-id="8feba-166">**1.** Você deve precisar do seu aplicativo `{teamsAppInstallationId}` .</span><span class="sxs-lookup"><span data-stu-id="8feba-166">**1.** You must need your app's `{teamsAppInstallationId}`.</span></span> <span data-ttu-id="8feba-167">Se você não tiver, use o seguinte:</span><span class="sxs-lookup"><span data-stu-id="8feba-167">If you don't have it, use the following:</span></span>

<span data-ttu-id="8feba-168">**HTTP OBTER** solicitação:</span><span class="sxs-lookup"><span data-stu-id="8feba-168">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

<span data-ttu-id="8feba-169">A propriedade de **id** da resposta é o `teamsAppInstallationId` .</span><span class="sxs-lookup"><span data-stu-id="8feba-169">The **id** property of the response is the `teamsAppInstallationId`.</span></span>

<span data-ttu-id="8feba-170">**2.** Faça a seguinte solicitação para buscar `chatId` o:</span><span class="sxs-lookup"><span data-stu-id="8feba-170">**2.** Make the following request to fetch the `chatId`:</span></span>

<span data-ttu-id="8feba-171">**SOLICITAÇÃO HTTP GET** (permissão `TeamsAppInstallation.ReadWriteSelfForUser.All` ):</span><span class="sxs-lookup"><span data-stu-id="8feba-171">**HTTP GET** request (permission — `TeamsAppInstallation.ReadWriteSelfForUser.All`):</span></span>  

```http
GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps/{teamsAppInstallationId}/chat
```

<span data-ttu-id="8feba-172">A propriedade de **id** da resposta é o `chatId` .</span><span class="sxs-lookup"><span data-stu-id="8feba-172">The **id** property of the response is the `chatId`.</span></span>

<span data-ttu-id="8feba-173">Você também pode recuperar a `chatId` seguinte solicitação, mas requer a permissão mais `Chat.Read.All` ampla:</span><span class="sxs-lookup"><span data-stu-id="8feba-173">You can also retrieve the `chatId` with the following request but it requires the broader `Chat.Read.All` permission:</span></span>

<span data-ttu-id="8feba-174">**SOLICITAÇÃO HTTP GET** (permissão `Chat.Read.All` ):</span><span class="sxs-lookup"><span data-stu-id="8feba-174">**HTTP GET** request (permission — `Chat.Read.All`):</span></span>

```http
GET https://graph.microsoft.com/beta/users/{user-id}/chats?$filter=installedApps/any(a:a/teamsApp/id eq '{teamsAppId}')
```

### <a name="-send-proactive-messages"></a><span data-ttu-id="8feba-175">✔ Enviar mensagens proativas</span><span class="sxs-lookup"><span data-stu-id="8feba-175">✔ Send proactive messages</span></span>

<span data-ttu-id="8feba-176">Seu bot pode [enviar mensagens proativas](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true) depois que o bot tiver sido adicionado para um usuário ou uma equipe e tenha recebido todas as informações do usuário.</span><span class="sxs-lookup"><span data-stu-id="8feba-176">Your bot can [send proactive messages](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true) after the bot has been added for a user or a team and has received all the user information.</span></span>

## <a name="see-also"></a><span data-ttu-id="8feba-177">Confira também</span><span class="sxs-lookup"><span data-stu-id="8feba-177">See also</span></span>

* [<span data-ttu-id="8feba-178">**Gerencie políticas de configuração de aplicativos em Microsoft Teams**</span><span class="sxs-lookup"><span data-stu-id="8feba-178">**Manage app setup policies in Microsoft Teams**</span></span>](/MicrosoftTeams/teams-app-setup-policies#create-a-custom-app-setup-policy)
* [<span data-ttu-id="8feba-179">Enviar notificações proativas aos usuários SDK v4</span><span class="sxs-lookup"><span data-stu-id="8feba-179">Send proactive notifications to users SDK v4</span></span>](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true)

## <a name="view-additional-code-samples"></a><span data-ttu-id="8feba-180">Exibir amostras de código adicionais</span><span class="sxs-lookup"><span data-stu-id="8feba-180">View additional code samples</span></span>
>
> [!div class="nextstepaction"]
> [<span data-ttu-id="8feba-181">**Teams amostras de código de mensagens proativas**</span><span class="sxs-lookup"><span data-stu-id="8feba-181">**Teams proactive messaging code samples**</span></span>](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)