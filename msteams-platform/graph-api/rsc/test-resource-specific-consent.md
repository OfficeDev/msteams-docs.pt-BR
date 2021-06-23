---
title: Testar permissões de consentimento específicas do recurso Teams
description: Detalhes do teste de consentimento específico do recurso em Teams usando Postman
localization_priority: Normal
author: akjo
ms.author: lajanuar
ms.topic: tutorial
keywords: autorização do teams OAuth SSO AAD rsc Postman Graph
ms.openlocfilehash: 92c6d5d96c103fb5e0da6afd91357b5887b2ba10
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069081"
---
# <a name="test-resource-specific-consent-permissions-in-teams"></a><span data-ttu-id="1cf67-104">Testar permissões de consentimento específicas do recurso Teams</span><span class="sxs-lookup"><span data-stu-id="1cf67-104">Test resource-specific consent permissions in Teams</span></span>

> [!NOTE]
> <span data-ttu-id="1cf67-105">O consentimento específico do recurso para o escopo de chat está disponível apenas na [visualização do desenvolvedor](../../resources/dev-preview/developer-preview-intro.md) público.</span><span class="sxs-lookup"><span data-stu-id="1cf67-105">Resource-specific consent for chat scope is available in [public developer preview](../../resources/dev-preview/developer-preview-intro.md) only.</span></span>

<span data-ttu-id="1cf67-106">O RSC (consentimento específico de recursos) é uma integração de API Microsoft Teams e Graph que permite que seu aplicativo use pontos de extremidade da API para gerenciar recursos específicos, equipes ou chats, dentro de uma organização.</span><span class="sxs-lookup"><span data-stu-id="1cf67-106">Resource-specific consent (RSC) is a Microsoft Teams and Graph API integration that enables your app to use API endpoints to manage specific resources—either teams or chats—within an organization.</span></span> <span data-ttu-id="1cf67-107">Para obter mais informações, consulte [Resource-specific consent (RSC) — Microsoft Teams Graph API](resource-specific-consent.md).</span><span class="sxs-lookup"><span data-stu-id="1cf67-107">For more information, see [Resource-specific consent (RSC) — Microsoft Teams Graph API](resource-specific-consent.md).</span></span>

> [!NOTE]
> <span data-ttu-id="1cf67-108">Para testar as permissões RSC, seu arquivo de manifesto do aplicativo Teams deve incluir uma chave **webApplicationInfo** preenchida com os seguintes campos:</span><span class="sxs-lookup"><span data-stu-id="1cf67-108">To test the RSC permissions, your Teams app manifest file must include a **webApplicationInfo** key populated with the following fields:</span></span>
>
> - <span data-ttu-id="1cf67-109">**id**: Sua ID do aplicativo do Azure AD, consulte [Register your app in the Azure AD portal](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).</span><span class="sxs-lookup"><span data-stu-id="1cf67-109">**id**: Your Azure AD app ID, see [Register your app in the Azure AD portal](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).</span></span>
> - <span data-ttu-id="1cf67-110">**resource**: Qualquer cadeia de caracteres, consulte a nota em [Update your Teams app manifest](resource-specific-consent.md#update-your-teams-app-manifest).</span><span class="sxs-lookup"><span data-stu-id="1cf67-110">**resource**: Any string, see the note in  [Update your Teams app manifest](resource-specific-consent.md#update-your-teams-app-manifest).</span></span>
> - <span data-ttu-id="1cf67-111">**permissões de aplicativo**: permissões RSC para seu aplicativo, consulte [Permissões específicas do recurso](resource-specific-consent.md#resource-specific-permissions).</span><span class="sxs-lookup"><span data-stu-id="1cf67-111">**application permissions**: RSC permissions for  your app, see [Resource-specific Permissions](resource-specific-consent.md#resource-specific-permissions).</span></span>

## <a name="example-for-a-team"></a><span data-ttu-id="1cf67-112">Exemplo para uma equipe</span><span class="sxs-lookup"><span data-stu-id="1cf67-112">Example for a team</span></span>
```json
"webApplicationInfo":{
      "id":"XXxxXXXXX-XxXX-xXXX-XXxx-XXXXXXXxxxXX",
      "resource":"https://AnyString",
      "applicationPermissions":[
         "Channel.Create.Group",
         "Channel.Delete.Group",
         "ChannelMessage.Read.Group",
         "ChannelSettings.Read.Group",
         "ChannelSettings.Edit.Group",
         "Member.Read.Group",
         "Owner.Read.Group",
         "TeamsApp.Read.Group",
         "TeamsTab.Read.Group",
         "TeamsTab.Create.Group",
         "TeamsTab.Edit.Group",
         "TeamsTab.Delete.Group",
         "TeamSettings.Read.Group",
         "TeamSettings.Edit.Group"
      ]
   }
```

## <a name="example-for-a-chat"></a><span data-ttu-id="1cf67-113">Exemplo para um chat</span><span class="sxs-lookup"><span data-stu-id="1cf67-113">Example for a chat</span></span>
```json
"webApplicationInfo":{
      "id":"XXxxXXXXX-XxXX-xXXX-XXxx-XXXXXXXxxxXX",
      "resource":"https://AnyString",
      "applicationPermissions":[
          "ChatSettings.Read.Chat",
          "ChatSettings.ReadWrite.Chat",
          "ChatMessage.Read.Chat",
          "ChatMember.Read.Chat",
          "Chat.Manage.Chat",
          "TeamsTab.Read.Chat",
          "TeamsTab.Create.Chat",
          "TeamsTab.Delete.Chat",
          "TeamsTab.ReadWrite.Chat",
          "TeamsAppInstallation.Read.Chat",
          "OnlineMeeting.ReadBasic.Chat"
      ]
   }
```

> [!IMPORTANT]
> <span data-ttu-id="1cf67-114">No manifesto do aplicativo, inclua apenas as permissões RSC que você deseja que seu aplicativo tenha.</span><span class="sxs-lookup"><span data-stu-id="1cf67-114">In your app manifest, only include the RSC permissions that you want your app to have.</span></span>

>[!NOTE]
><span data-ttu-id="1cf67-115">Se o aplicativo tiver o objetivo de dar suporte à instalação em escopos de equipe e chat, as permissões de equipe e de chat poderão ser especificadas no mesmo manifesto em `applicationPermissions` .</span><span class="sxs-lookup"><span data-stu-id="1cf67-115">If the app is meant to support installation in both team and chat scopes, then both team and chat permissions can be specified in the same manifest under `applicationPermissions`.</span></span>

## <a name="test-added-rsc-permissions-to-a-team-using-the-postman-app"></a><span data-ttu-id="1cf67-116">Test added RSC permissions to a team using the Postman app</span><span class="sxs-lookup"><span data-stu-id="1cf67-116">Test added RSC permissions to a team using the Postman app</span></span>

<span data-ttu-id="1cf67-117">Para verificar se as permissões RSC estão sendo acodadas pela carga de solicitação de API, você precisa copiar o código de teste [JSON RSC](test-team-rsc-json-file.md) para a equipe em seu ambiente local e atualizar os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="1cf67-117">To check whether the RSC permissions are being honored by the API request payload, you need to copy the [RSC JSON test code for team](test-team-rsc-json-file.md) into your local environment and update the following values:</span></span>

* <span data-ttu-id="1cf67-118">`azureADAppId`: ID do aplicativo do Azure AD do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1cf67-118">`azureADAppId`: Your app's Azure AD app ID.</span></span>
* <span data-ttu-id="1cf67-119">`azureADAppSecret`: Sua senha do aplicativo do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="1cf67-119">`azureADAppSecret`: Your Azure AD app password.</span></span>
* <span data-ttu-id="1cf67-120">`token_scope`: O escopo é necessário para obter um token.</span><span class="sxs-lookup"><span data-stu-id="1cf67-120">`token_scope`: The scope is required to get a token.</span></span> <span data-ttu-id="1cf67-121">definir o valor como https://graph.microsoft.com/.default .</span><span class="sxs-lookup"><span data-stu-id="1cf67-121">set the value to https://graph.microsoft.com/.default.</span></span>
* <span data-ttu-id="1cf67-122">`teamGroupId`: Você pode obter a ID do grupo de equipe do cliente Teams da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="1cf67-122">`teamGroupId`: You can get the team group id from the Teams client as follows:</span></span>

    1. <span data-ttu-id="1cf67-123">No cliente Teams, selecione **Teams** na barra de navegação à esquerda.</span><span class="sxs-lookup"><span data-stu-id="1cf67-123">In the Teams client, select **Teams** from the far left navigation bar.</span></span>
    2. <span data-ttu-id="1cf67-124">Selecione a equipe onde o aplicativo está instalado no menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="1cf67-124">Select the team where the app is installed from the dropdown menu.</span></span>
    3. <span data-ttu-id="1cf67-125">Selecione o **ícone Mais opções** (&#8943;).</span><span class="sxs-lookup"><span data-stu-id="1cf67-125">Select the **More options** icon (&#8943;).</span></span>
    4. <span data-ttu-id="1cf67-126">Selecione **Obter link para a equipe**.</span><span class="sxs-lookup"><span data-stu-id="1cf67-126">Select **Get link to team**.</span></span> 
    5. <span data-ttu-id="1cf67-127">Copie e salve o **valor groupId** da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1cf67-127">Copy and save the **groupId** value from the string.</span></span>

## <a name="test-added-rsc-permissions-to-a-chat-using-the-postman-app"></a><span data-ttu-id="1cf67-128">Test added RSC permissions to a chat using the Postman app</span><span class="sxs-lookup"><span data-stu-id="1cf67-128">Test added RSC permissions to a chat using the Postman app</span></span>

<span data-ttu-id="1cf67-129">Para verificar se as permissões RSC estão sendo acodadas pela carga de solicitação de API, você precisa copiar o código de teste [JSON RSC](test-chat-rsc-json-file.md) para chats em seu ambiente local e atualizar os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="1cf67-129">To check whether the RSC permissions are being honored by the API request payload, you need to copy the [RSC JSON test code for chats](test-chat-rsc-json-file.md) into your local environment and update the following values:</span></span>

* <span data-ttu-id="1cf67-130">`azureADAppId`: ID do aplicativo do Azure AD do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1cf67-130">`azureADAppId`: Your app's Azure AD app ID.</span></span>
* <span data-ttu-id="1cf67-131">`azureADAppSecret`: Sua senha do aplicativo do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="1cf67-131">`azureADAppSecret`: Your Azure AD app password.</span></span>
* <span data-ttu-id="1cf67-132">`token_scope`: O escopo é necessário para obter um token.</span><span class="sxs-lookup"><span data-stu-id="1cf67-132">`token_scope`: The scope is required to get a token.</span></span> <span data-ttu-id="1cf67-133">definir o valor como https://graph.microsoft.com/.default .</span><span class="sxs-lookup"><span data-stu-id="1cf67-133">set the value to https://graph.microsoft.com/.default.</span></span>
* <span data-ttu-id="1cf67-134">`tenantId`: O nome ou a ID do objeto AAD do locatário.</span><span class="sxs-lookup"><span data-stu-id="1cf67-134">`tenantId`: The name or the AAD Object ID of your tenant.</span></span>
* <span data-ttu-id="1cf67-135">`chatId`: Você pode obter a ID do thread de chat do cliente *Teams Web* da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="1cf67-135">`chatId`: You can get the chat thread id from the Teams *web* client as follows:</span></span>

    1. <span data-ttu-id="1cf67-136">No cliente Teams Web, selecione **Chat** na barra de navegação à extrema esquerda.</span><span class="sxs-lookup"><span data-stu-id="1cf67-136">In the Teams web client, select **Chat** from the far left navigation bar.</span></span>
    2. <span data-ttu-id="1cf67-137">Selecione o chat em que o aplicativo está instalado no menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="1cf67-137">Select the chat where the app is installed from the dropdown menu.</span></span>
    3. <span data-ttu-id="1cf67-138">Copie a URL da Web e salve a ID do thread de chat da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1cf67-138">Copy the web URL and save the chat thread id from the string.</span></span>
<span data-ttu-id="1cf67-139">![ID do thread de chat da URL da Web.](../../assets/images/chat-thread-id.png)</span><span class="sxs-lookup"><span data-stu-id="1cf67-139">![Chat thread id from web URL.](../../assets/images/chat-thread-id.png)</span></span>

### <a name="use-postman"></a><span data-ttu-id="1cf67-140">Usar o Postman</span><span class="sxs-lookup"><span data-stu-id="1cf67-140">Use Postman</span></span>

1. <span data-ttu-id="1cf67-141">Abra o [aplicativo Postman.](https://www.postman.com)</span><span class="sxs-lookup"><span data-stu-id="1cf67-141">Open the [Postman](https://www.postman.com) app.</span></span>
2. <span data-ttu-id="1cf67-142">Selecione **Importar arquivo**  >    >  **de importação de arquivo** para carregar o arquivo JSON atualizado do seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="1cf67-142">Select **File** > **Import** > **Import file** to upload the updated JSON file from your environment.</span></span>  
3. <span data-ttu-id="1cf67-143">Selecione a **guia Coleções.**</span><span class="sxs-lookup"><span data-stu-id="1cf67-143">Select the **Collections** tab.</span></span> 
4. <span data-ttu-id="1cf67-144">Selecione a divisa **>** ao lado do **RSC de teste** para expandir o exibição de detalhes e consulte as solicitações de API.</span><span class="sxs-lookup"><span data-stu-id="1cf67-144">Select the chevron **>** next to the **Test RSC** to expand the details view and see the API requests.</span></span>

<span data-ttu-id="1cf67-145">Execute toda a coleção de permissões para cada chamada de API.</span><span class="sxs-lookup"><span data-stu-id="1cf67-145">Execute the entire permissions collection for each API call.</span></span> <span data-ttu-id="1cf67-146">As permissões especificadas no manifesto do aplicativo devem ser bem-sucedidas, enquanto as não especificadas devem falhar com um código de status HTTP 403.</span><span class="sxs-lookup"><span data-stu-id="1cf67-146">The permissions that you specified in your app manifest must succeed, while those not specified must fail with an HTTP 403 status code.</span></span> <span data-ttu-id="1cf67-147">Verifique todos os códigos de status de resposta para confirmar se o comportamento das permissões RSC em seu aplicativo atendem às expectativas.</span><span class="sxs-lookup"><span data-stu-id="1cf67-147">Check all of the response status codes to confirm that the behavior of the RSC permissions in your app meet expectations.</span></span>

> [!NOTE]
> <span data-ttu-id="1cf67-148">Para testar chamadas de API DELETE e READ específicas, adicione esses cenários de instância ao arquivo JSON.</span><span class="sxs-lookup"><span data-stu-id="1cf67-148">To test specific DELETE and READ API calls, add those instance scenarios to the JSON file.</span></span>

## <a name="test-revoked-rsc-permissions-using-postman"></a><span data-ttu-id="1cf67-149">Testar permissões RSC revogadas usando [Postman](https://www.postman.com/)</span><span class="sxs-lookup"><span data-stu-id="1cf67-149">Test revoked RSC permissions using [Postman](https://www.postman.com/)</span></span>

1. <span data-ttu-id="1cf67-150">Desinstale o aplicativo do recurso específico.</span><span class="sxs-lookup"><span data-stu-id="1cf67-150">Uninstall the app from the specific resource.</span></span>
2. <span data-ttu-id="1cf67-151">Siga as etapas para chat ou equipe:</span><span class="sxs-lookup"><span data-stu-id="1cf67-151">Follow the steps for either chat or team:</span></span> 
    1. <span data-ttu-id="1cf67-152">[Test added RSC permissions to a team using Postman](#test-added-rsc-permissions-to-a-team-using-the-postman-app).</span><span class="sxs-lookup"><span data-stu-id="1cf67-152">[Test added RSC permissions to a team using Postman](#test-added-rsc-permissions-to-a-team-using-the-postman-app).</span></span>
    2. <span data-ttu-id="1cf67-153">[Test added RSC permissions to a chat using Postman](#test-added-rsc-permissions-to-a-chat-using-the-postman-app).</span><span class="sxs-lookup"><span data-stu-id="1cf67-153">[Test added RSC permissions to a chat using Postman](#test-added-rsc-permissions-to-a-chat-using-the-postman-app).</span></span>
3. <span data-ttu-id="1cf67-154">Verifique todos os códigos de status de resposta para confirmar se as chamadas de API **específicas falharam com um código de status HTTP 403.**</span><span class="sxs-lookup"><span data-stu-id="1cf67-154">Check all the response status codes to confirm that the specific API calls **have failed with an HTTP 403 status code**.</span></span>

## <a name="see-also"></a><span data-ttu-id="1cf67-155">Confira também</span><span class="sxs-lookup"><span data-stu-id="1cf67-155">See also</span></span>

[<span data-ttu-id="1cf67-156">API Graph Microsoft e Teams</span><span class="sxs-lookup"><span data-stu-id="1cf67-156">Microsoft Graph API and Teams</span></span>](/graph/api/resources/teams-api-overview?view=graph-rest-1.0&preserve-view=true)

