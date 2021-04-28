---
title: Testar permissões de consentimento específicas do recurso no Teams
description: Detalhes do teste de consentimento específico do recurso no Teams usando Postman
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: tutorial
keywords: Autorização do teams OAuth SSO AAD rsc Postman Graph
ms.openlocfilehash: 7f67df35954cd29810c387d05215eeec476a4ed4
ms.sourcegitcommit: a732789190f59ec1f3699e8ad2f06387e8fe1458
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2021
ms.locfileid: "52058324"
---
# <a name="test-resource-specific-consent-permissions-in-teams"></a><span data-ttu-id="056ca-104">Testar permissões de consentimento específicas do recurso no Teams</span><span class="sxs-lookup"><span data-stu-id="056ca-104">Test resource-specific consent permissions in Teams</span></span>

<span data-ttu-id="056ca-105">O RSC (consentimento específico de recursos) é uma integração da API do Microsoft Teams e do Graph que permite que seu aplicativo use pontos de extremidade da API para gerenciar equipes específicas dentro de uma organização.</span><span class="sxs-lookup"><span data-stu-id="056ca-105">Resource-specific consent (RSC) is a Microsoft Teams and Graph API integration that enables your app to use API endpoints to manage specific teams within an organization.</span></span> <span data-ttu-id="056ca-106">Para obter mais informações, consulte Consentimento específico do recurso [(RSC) — API do Microsoft Teams Graph](resource-specific-consent.md).</span><span class="sxs-lookup"><span data-stu-id="056ca-106">For more information, see [Resource-specific consent (RSC) — Microsoft Teams Graph API](resource-specific-consent.md).</span></span>

> [!NOTE]
> <span data-ttu-id="056ca-107">Para testar as permissões RSC, o arquivo de manifesto do aplicativo teams deve incluir uma chave **webApplicationInfo** preenchida com os seguintes campos:</span><span class="sxs-lookup"><span data-stu-id="056ca-107">To test the RSC permissions, your Teams app manifest file must include a **webApplicationInfo** key populated with the following fields:</span></span>
>
> - <span data-ttu-id="056ca-108">**id**: Sua ID do aplicativo do Azure AD, consulte [Register your app in the Azure AD portal](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).</span><span class="sxs-lookup"><span data-stu-id="056ca-108">**id**: Your Azure AD app ID, see [Register your app in the Azure AD portal](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).</span></span>
> - <span data-ttu-id="056ca-109">**resource**: Qualquer cadeia de caracteres, consulte a nota em  [Update your Teams app manifest](resource-specific-consent.md#update-your-teams-app-manifest).</span><span class="sxs-lookup"><span data-stu-id="056ca-109">**resource**: Any string, see the note in  [Update your Teams app manifest](resource-specific-consent.md#update-your-teams-app-manifest).</span></span>
> - <span data-ttu-id="056ca-110">**permissões de aplicativo**: permissões RSC para seu aplicativo, consulte [Permissões específicas do recurso](resource-specific-consent.md#resource-specific-permissions).</span><span class="sxs-lookup"><span data-stu-id="056ca-110">**application permissions**: RSC permissions for  your app, see [Resource-specific Permissions](resource-specific-consent.md#resource-specific-permissions).</span></span>

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

> [!IMPORTANT]
> <span data-ttu-id="056ca-111">No manifesto do aplicativo, inclua apenas as permissões RSC que você deseja que seu aplicativo tenha.</span><span class="sxs-lookup"><span data-stu-id="056ca-111">In your app manifest, only include the RSC permissions that you want your app to have.</span></span>

## <a name="test-added-rsc-permissions-using-the-postman-app"></a><span data-ttu-id="056ca-112">Test added RSC permissions using the Postman app</span><span class="sxs-lookup"><span data-stu-id="056ca-112">Test added RSC permissions using the Postman app</span></span>

<span data-ttu-id="056ca-113">Para verificar se as permissões RSC estão sendo acodadas pela carga de solicitação de API, você precisa copiar o código de teste [JSON RSC](test-rsc-json-file.md) para seu ambiente local e atualizar os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="056ca-113">To check whether the RSC permissions are being honored by the API request payload, you need to copy the [RSC JSON test code](test-rsc-json-file.md) into your local environment and update the following values:</span></span>

* <span data-ttu-id="056ca-114">`azureADAppId`: ID do aplicativo do Azure AD do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="056ca-114">`azureADAppId`: Your app's Azure AD app ID.</span></span>
* <span data-ttu-id="056ca-115">`azureADAppSecret`: Sua senha do aplicativo do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="056ca-115">`azureADAppSecret`: Your Azure AD app password.</span></span>
* <span data-ttu-id="056ca-116">`token_scope`: O escopo é necessário para obter um token.</span><span class="sxs-lookup"><span data-stu-id="056ca-116">`token_scope`: The scope is required to get a token.</span></span> <span data-ttu-id="056ca-117">definir o valor como https://graph.microsoft.com/.default .</span><span class="sxs-lookup"><span data-stu-id="056ca-117">set the value to https://graph.microsoft.com/.default.</span></span>
* <span data-ttu-id="056ca-118">`teamGroupId`: Você pode obter a ID do grupo de equipe do cliente do Teams da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="056ca-118">`teamGroupId`: You can get the team group id from the Teams client as follows:</span></span>

    1. <span data-ttu-id="056ca-119">No cliente do Teams, selecione **Teams** na barra de navegação à extrema esquerda.</span><span class="sxs-lookup"><span data-stu-id="056ca-119">In the Teams client, select **Teams** from the far left navigation bar.</span></span>
    2. <span data-ttu-id="056ca-120">Selecione a equipe onde o aplicativo está instalado no menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="056ca-120">Select the team where the app is installed from the dropdown menu.</span></span>
    3. <span data-ttu-id="056ca-121">Selecione o **ícone Mais opções** (&#8943;).</span><span class="sxs-lookup"><span data-stu-id="056ca-121">Select the **More options** icon (&#8943;).</span></span>
    4. <span data-ttu-id="056ca-122">Selecione **Obter link para a equipe**.</span><span class="sxs-lookup"><span data-stu-id="056ca-122">Select **Get link to team**.</span></span> 
    5. <span data-ttu-id="056ca-123">Copie e salve o **valor groupId** da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="056ca-123">Copy and save the **groupId** value from the string.</span></span>

### <a name="use-postman"></a><span data-ttu-id="056ca-124">Usar o Postman</span><span class="sxs-lookup"><span data-stu-id="056ca-124">Use Postman</span></span>

1. <span data-ttu-id="056ca-125">Abra o [aplicativo Postman.](https://www.postman.com)</span><span class="sxs-lookup"><span data-stu-id="056ca-125">Open the [Postman](https://www.postman.com) app.</span></span>
2. <span data-ttu-id="056ca-126">Selecione **Importar arquivo**  >    >  **de importação de arquivo** para carregar o arquivo JSON atualizado do seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="056ca-126">Select **File** > **Import** > **Import file** to upload the updated JSON file from your environment.</span></span>  
3. <span data-ttu-id="056ca-127">Selecione a **guia Coleções.**</span><span class="sxs-lookup"><span data-stu-id="056ca-127">Select the **Collections** tab.</span></span> 
4. <span data-ttu-id="056ca-128">Selecione a divisa **>** ao lado do **RSC de teste** para expandir o exibição de detalhes e consulte as solicitações de API.</span><span class="sxs-lookup"><span data-stu-id="056ca-128">Select the chevron **>** next to the **Test RSC** to expand the details view and see the API requests.</span></span>

<span data-ttu-id="056ca-129">Execute toda a coleção de permissões para cada chamada de API.</span><span class="sxs-lookup"><span data-stu-id="056ca-129">Execute the entire permissions collection for each API call.</span></span> <span data-ttu-id="056ca-130">As permissões especificadas no manifesto do aplicativo devem ser bem-sucedidas, enquanto as não especificadas devem falhar com um código de status HTTP 403.</span><span class="sxs-lookup"><span data-stu-id="056ca-130">The permissions that you specified in your app manifest must succeed, while those not specified must fail with an HTTP 403 status code.</span></span> <span data-ttu-id="056ca-131">Verifique todos os códigos de status de resposta para confirmar se o comportamento das permissões RSC em seu aplicativo atendem às expectativas.</span><span class="sxs-lookup"><span data-stu-id="056ca-131">Check all of the response status codes to confirm that the behavior of the RSC permissions in your app meet expectations.</span></span>

> [!NOTE]
> <span data-ttu-id="056ca-132">Para testar chamadas de API DELETE e READ específicas, adicione esses cenários de instância ao arquivo JSON.</span><span class="sxs-lookup"><span data-stu-id="056ca-132">To test specific DELETE and READ API calls, add those instance scenarios to the JSON file.</span></span>

## <a name="test-revoked-rsc-permissions-using-postman"></a><span data-ttu-id="056ca-133">Testar permissões RSC revogadas usando [Postman](https://www.postman.com/)</span><span class="sxs-lookup"><span data-stu-id="056ca-133">Test revoked RSC permissions using [Postman](https://www.postman.com/)</span></span>

1. <span data-ttu-id="056ca-134">Desinstale o aplicativo da equipe específica.</span><span class="sxs-lookup"><span data-stu-id="056ca-134">Uninstall the app from the specific team.</span></span>
2. <span data-ttu-id="056ca-135">Siga as etapas para [Testar as permissões RSC adicionadas usando Postman](#test-added-rsc-permissions-using-the-postman-app).</span><span class="sxs-lookup"><span data-stu-id="056ca-135">Follow the steps for [Test added RSC permissions using Postman](#test-added-rsc-permissions-using-the-postman-app).</span></span>
3. <span data-ttu-id="056ca-136">Verifique todos os códigos de status de resposta para confirmar se as chamadas de API específicas, bem-sucedidas, falharam com um **código de status HTTP 403**.</span><span class="sxs-lookup"><span data-stu-id="056ca-136">Check all the response status codes to confirm that the specific API calls, **succeeded, have failed with an HTTP 403 status code**.</span></span>

## <a name="see-also"></a><span data-ttu-id="056ca-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="056ca-137">See also</span></span>

- [<span data-ttu-id="056ca-138">API e Teams do Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="056ca-138">Microsoft Graph API and Teams</span></span>](/graph/api/resources/teams-api-overview?view=graph-rest-1.0&preserve-view=true)

