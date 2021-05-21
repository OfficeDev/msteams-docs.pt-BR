---
title: Consentimento específico do recurso em Teams
description: Descreve o consentimento específico do recurso em Teams e como tirar proveito dele.
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: reference
keywords: autorização do teams OAuth SSO AAD rsc Graph
ms.openlocfilehash: dabe0c33013fbb398eee7bf00ac2881cd86e6bc5
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566121"
---
# <a name="resource-specific-consent-rsc"></a><span data-ttu-id="d811d-104">Consentimento específico do recurso (RSC)</span><span class="sxs-lookup"><span data-stu-id="d811d-104">Resource-specific consent (RSC)</span></span>

<span data-ttu-id="d811d-105">O RSC (consentimento específico de recurso) é uma integração Microsoft Teams api do Microsoft Graph que permite que seu aplicativo use pontos de extremidade da API para gerenciar equipes específicas dentro de uma organização.</span><span class="sxs-lookup"><span data-stu-id="d811d-105">Resource-specific consent (RSC) is a Microsoft Teams and Microsoft Graph API integration that enables your app to use API endpoints to manage specific teams within an organization.</span></span> <span data-ttu-id="d811d-106">O modelo de permissões de consentimento específico do recurso (RSC) permite que os *proprietários* da equipe concedam consentimento para que um aplicativo acesse e/ou modifique os dados de uma equipe.</span><span class="sxs-lookup"><span data-stu-id="d811d-106">The resource-specific consent (RSC) permissions model enables *team owners* to grant consent for an application to access and/or modify a team's data.</span></span> <span data-ttu-id="d811d-107">As permissões RSC granulares, Teams específicas do RSC definem o que um aplicativo pode fazer em uma equipe específica:</span><span class="sxs-lookup"><span data-stu-id="d811d-107">The granular, Teams-specific, RSC permissions define what an application can do within a specific team:</span></span>

## <a name="resource-specific-permissions"></a><span data-ttu-id="d811d-108">Permissões específicas de recursos</span><span class="sxs-lookup"><span data-stu-id="d811d-108">Resource-specific permissions</span></span>

|<span data-ttu-id="d811d-109">Permissão de aplicativo</span><span class="sxs-lookup"><span data-stu-id="d811d-109">Application permission</span></span>| <span data-ttu-id="d811d-110">Ação</span><span class="sxs-lookup"><span data-stu-id="d811d-110">Action</span></span> |
| ----- | ----- |
|<span data-ttu-id="d811d-111">TeamSettings.Read.Group</span><span class="sxs-lookup"><span data-stu-id="d811d-111">TeamSettings.Read.Group</span></span> | <span data-ttu-id="d811d-112">Obter as configurações dessa equipe.</span><span class="sxs-lookup"><span data-stu-id="d811d-112">Get the settings for this team.</span></span>|
|<span data-ttu-id="d811d-113">TeamSettings.ReadWrite.Group</span><span class="sxs-lookup"><span data-stu-id="d811d-113">TeamSettings.ReadWrite.Group</span></span>|<span data-ttu-id="d811d-114">Atualizar as configurações para esta equipe.</span><span class="sxs-lookup"><span data-stu-id="d811d-114">Update the settings for this team.</span></span>|
|<span data-ttu-id="d811d-115">ChannelSettings.Read.Group</span><span class="sxs-lookup"><span data-stu-id="d811d-115">ChannelSettings.Read.Group</span></span>|<span data-ttu-id="d811d-116">Obter os nomes de canal, descrições de canal e configurações de canal para essa equipe.</span><span class="sxs-lookup"><span data-stu-id="d811d-116">Get the channel names, channel descriptions, and channel settings for this team.</span></span>|
|<span data-ttu-id="d811d-117">ChannelSettings.ReadWrite.Group</span><span class="sxs-lookup"><span data-stu-id="d811d-117">ChannelSettings.ReadWrite.Group</span></span>|<span data-ttu-id="d811d-118">Atualize os nomes de canal, descrições de canal e configurações de canal para essa equipe.</span><span class="sxs-lookup"><span data-stu-id="d811d-118">Update the channel names, channel descriptions, and channel settings for this team.</span></span>|
|<span data-ttu-id="d811d-119">Channel.Create.Group</span><span class="sxs-lookup"><span data-stu-id="d811d-119">Channel.Create.Group</span></span>|<span data-ttu-id="d811d-120">Criar canais nesta equipe.</span><span class="sxs-lookup"><span data-stu-id="d811d-120">Create channels in this team.</span></span>|
|<span data-ttu-id="d811d-121">Channel.Delete.Group</span><span class="sxs-lookup"><span data-stu-id="d811d-121">Channel.Delete.Group</span></span>|<span data-ttu-id="d811d-122">Exclua canais nesta equipe.</span><span class="sxs-lookup"><span data-stu-id="d811d-122">Delete channels in this team.</span></span>|
|<span data-ttu-id="d811d-123">ChannelMessage.Read.Group</span><span class="sxs-lookup"><span data-stu-id="d811d-123">ChannelMessage.Read.Group</span></span> |<span data-ttu-id="d811d-124">Receba as mensagens de canal dessa equipe.</span><span class="sxs-lookup"><span data-stu-id="d811d-124">Get this team's channel messages.</span></span>|
|<span data-ttu-id="d811d-125">TeamsAppInstallation.Read.Group</span><span class="sxs-lookup"><span data-stu-id="d811d-125">TeamsAppInstallation.Read.Group</span></span>|<span data-ttu-id="d811d-126">Obter uma lista dos aplicativos instalados dessa equipe.</span><span class="sxs-lookup"><span data-stu-id="d811d-126">Get a list of this team's installed apps.</span></span>|
|<span data-ttu-id="d811d-127">TeamsTab.Read.Group</span><span class="sxs-lookup"><span data-stu-id="d811d-127">TeamsTab.Read.Group</span></span>|<span data-ttu-id="d811d-128">Obter uma lista das guias dessa equipe.</span><span class="sxs-lookup"><span data-stu-id="d811d-128">Get a list of this team's tabs.</span></span>|
|<span data-ttu-id="d811d-129">TeamsTab.Create.Group</span><span class="sxs-lookup"><span data-stu-id="d811d-129">TeamsTab.Create.Group</span></span>|<span data-ttu-id="d811d-130">Criar guias nesta equipe.</span><span class="sxs-lookup"><span data-stu-id="d811d-130">Create tabs in this team.</span></span>|
|<span data-ttu-id="d811d-131">TeamsTab.ReadWrite.Group</span><span class="sxs-lookup"><span data-stu-id="d811d-131">TeamsTab.ReadWrite.Group</span></span>|<span data-ttu-id="d811d-132">Atualize as guias desta equipe.</span><span class="sxs-lookup"><span data-stu-id="d811d-132">Update this team's tabs.</span></span>|
|<span data-ttu-id="d811d-133">TeamsTab.Delete.Group</span><span class="sxs-lookup"><span data-stu-id="d811d-133">TeamsTab.Delete.Group</span></span>|<span data-ttu-id="d811d-134">Excluir as guias dessa equipe.</span><span class="sxs-lookup"><span data-stu-id="d811d-134">Delete this team's tabs.</span></span>|
|<span data-ttu-id="d811d-135">TeamMember.Read.Group</span><span class="sxs-lookup"><span data-stu-id="d811d-135">TeamMember.Read.Group</span></span>|<span data-ttu-id="d811d-136">Obter os membros dessa equipe.</span><span class="sxs-lookup"><span data-stu-id="d811d-136">Get this team's members.</span></span>|

>[!NOTE]
><span data-ttu-id="d811d-137">Permissões específicas de recursos estão disponíveis apenas para Teams aplicativos instalados no cliente Teams e atualmente não fazem parte do portal Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="d811d-137">Resource-specific permissions are only available to Teams apps installed on the Teams client and are currently not part of the Azure Active Directory portal.</span></span>

## <a name="enable-resource-specific-consent-in-your-application"></a><span data-ttu-id="d811d-138">Habilitar o consentimento específico do recurso em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="d811d-138">Enable resource-specific consent in your application</span></span>

<span data-ttu-id="d811d-139">As etapas para habilenciar o RSC em seu aplicativo são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="d811d-139">The steps for enabling RSC in your application are as follows:</span></span>

1. <span data-ttu-id="d811d-140">[Configure as configurações de consentimento do proprietário do grupo no portal Azure Active Directory .](#configure-group-owner-consent-settings-in-the-azure-ad-portal)</span><span class="sxs-lookup"><span data-stu-id="d811d-140">[Configure group owner consent settings in the Azure Active Directory portal](#configure-group-owner-consent-settings-in-the-azure-ad-portal).</span></span>
1. <span data-ttu-id="d811d-141">[Registre seu aplicativo com plataforma de identidade da Microsoft por meio do portal do Azure AD.](#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal)</span><span class="sxs-lookup"><span data-stu-id="d811d-141">[Register your app with Microsoft identity platform via the Azure AD portal](#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).</span></span>
1. <span data-ttu-id="d811d-142">[Revise suas permissões de aplicativo no portal do Azure AD.](#review-your-application-permissions-in-the-azure-ad-portal)</span><span class="sxs-lookup"><span data-stu-id="d811d-142">[Review your application permissions in the Azure AD portal](#review-your-application-permissions-in-the-azure-ad-portal).</span></span>
1. <span data-ttu-id="d811d-143">[Obtenha um token de acesso da plataforma Microsoft Identity](#obtain-an-access-token-from-the-microsoft-identity-platform).</span><span class="sxs-lookup"><span data-stu-id="d811d-143">[Obtain an access token from the Microsoft Identity platform](#obtain-an-access-token-from-the-microsoft-identity-platform).</span></span>
1. <span data-ttu-id="d811d-144">[Atualize seu Teams de aplicativo .](#update-your-teams-app-manifest)</span><span class="sxs-lookup"><span data-stu-id="d811d-144">[Update your Teams app manifest](#update-your-teams-app-manifest).</span></span>
1. <span data-ttu-id="d811d-145">[Instale seu aplicativo diretamente no Teams](#sideload-your-app-in-teams).</span><span class="sxs-lookup"><span data-stu-id="d811d-145">[Install your app directly in Teams](#sideload-your-app-in-teams).</span></span>
1. <span data-ttu-id="d811d-146">[Verifique se o aplicativo tem permissões RSC adicionadas.](#check-your-app-for-added-rsc-permissions)</span><span class="sxs-lookup"><span data-stu-id="d811d-146">[Check your app for added RSC permissions](#check-your-app-for-added-rsc-permissions).</span></span>

## <a name="configure-group-owner-consent-settings-in-the-azure-ad-portal"></a><span data-ttu-id="d811d-147">Configurar configurações de consentimento do proprietário do grupo no portal do Azure AD</span><span class="sxs-lookup"><span data-stu-id="d811d-147">Configure group owner consent settings in the Azure AD portal</span></span>

<span data-ttu-id="d811d-148">Você pode habilitar ou [desabilitar o consentimento do](/azure/active-directory/manage-apps/configure-user-consent-groups?tabs=azure-portal) proprietário do grupo diretamente no portal do Azure:</span><span class="sxs-lookup"><span data-stu-id="d811d-148">You can enable or disable [group owner consent](/azure/active-directory/manage-apps/configure-user-consent-groups?tabs=azure-portal) directly within the Azure portal:</span></span>

> [!div class="checklist"]
>
>- <span data-ttu-id="d811d-149">Entre no [portal do Azure](https://portal.azure.com) como administrador [global/administrador da empresa.](/azure/active-directory/users-groups-roles/directory-assign-admin-roles.md#global-administrator--company-administrator)</span><span class="sxs-lookup"><span data-stu-id="d811d-149">Sign in to the [Azure portal](https://portal.azure.com) as a [Global Administrator/Company Administrator](/azure/active-directory/users-groups-roles/directory-assign-admin-roles.md#global-administrator--company-administrator).</span></span>  
 > - <span data-ttu-id="d811d-150">[Selecione](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConsentPoliciesMenuBlade/UserSettings) **Azure Active Directory**  =>  **Enterprise**  =>  **aplicativos Consentimento e permissões** Configurações de consentimento  =>  **do usuário.**</span><span class="sxs-lookup"><span data-stu-id="d811d-150">[Select](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConsentPoliciesMenuBlade/UserSettings) **Azure Active Directory** => **Enterprise applications** => **Consent and permissions** => **User consent settings**.</span></span>
> - <span data-ttu-id="d811d-151">Habilitar, desabilitar ou limitar o consentimento do usuário com o controle rotulado consentimento do proprietário do grupo para aplicativos que acessam dados **(O** padrão é Permitir o consentimento do proprietário do grupo para todos os proprietários **do grupo**).</span><span class="sxs-lookup"><span data-stu-id="d811d-151">Enable, disable, or limit user consent with the control labeled **Group owner consent for apps accessing data** (The default is **Allow group owner consent for all group owners**).</span></span> <span data-ttu-id="d811d-152">Para que o proprietário da equipe instale um aplicativo usando o RSC, o consentimento do proprietário do grupo deve ser habilitado para esse usuário.</span><span class="sxs-lookup"><span data-stu-id="d811d-152">For a team owner to install an app using RSC, group owner consent must be enabled for that user.</span></span>

![Configuração rsc do azure](../../assets/images/azure-rsc-configuration.png)

<span data-ttu-id="d811d-154">Para habilitar ou desabilitar o consentimento do proprietário do grupo usando o PowerShell, siga as etapas descritas em [Configure group owner consent using PowerShell](/azure/active-directory/manage-apps/configure-user-consent-groups?tabs=azure-powershell).</span><span class="sxs-lookup"><span data-stu-id="d811d-154">To enable or disable group owner consent using PowerShell, follow the steps outlined in [Configure group owner consent using PowerShell](/azure/active-directory/manage-apps/configure-user-consent-groups?tabs=azure-powershell).</span></span>

## <a name="register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal"></a><span data-ttu-id="d811d-155">Registrar seu aplicativo com plataforma de identidade da Microsoft por meio do portal do Azure AD</span><span class="sxs-lookup"><span data-stu-id="d811d-155">Register your app with Microsoft identity platform via the Azure AD portal</span></span>

<span data-ttu-id="d811d-156">O Azure Active Directory portal fornece uma plataforma central para você registrar e configurar seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="d811d-156">The Azure Active Directory portal provides a central platform for you to register and configure your apps.</span></span> <span data-ttu-id="d811d-157">Seu aplicativo deve ser registrado no portal do Azure AD para se integrar ao plataforma de identidade da Microsoft e chamar as APIs Graph Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d811d-157">Your app must be registered in the Azure AD portal to integrate with the Microsoft identity platform and call Microsoft Graph APIs.</span></span> <span data-ttu-id="d811d-158">Para obter mais informações, [consulte Register an application with the plataforma de identidade da Microsoft](/graph/auth-register-app-v2).</span><span class="sxs-lookup"><span data-stu-id="d811d-158">For more information, see [Register an application with the Microsoft identity platform](/graph/auth-register-app-v2).</span></span>

>[!WARNING]
><span data-ttu-id="d811d-159">Não registre vários Teams aplicativos na mesma ID do aplicativo do Azure AD. A id do aplicativo deve ser exclusiva para cada aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d811d-159">Do not register multiple Teams apps to the same Azure AD app id. The app id must be unique for each app.</span></span> <span data-ttu-id="d811d-160">As tentativas de instalar vários aplicativos na mesma ID do aplicativo falharão.</span><span class="sxs-lookup"><span data-stu-id="d811d-160">Attempts to install multiple apps to the same app id will fail.</span></span>

## <a name="review-your-application-permissions-in-the-azure-ad-portal"></a><span data-ttu-id="d811d-161">Revise suas permissões de aplicativo no portal do Azure AD</span><span class="sxs-lookup"><span data-stu-id="d811d-161">Review your application permissions in the Azure AD portal</span></span>

<span data-ttu-id="d811d-162">Navegue até **a página Registros** do Aplicativo Inicial e selecione seu aplicativo  =>   RSC.</span><span class="sxs-lookup"><span data-stu-id="d811d-162">Navigate to the **Home** => **App registrations** page and select your RSC app.</span></span> <span data-ttu-id="d811d-163">Escolha **permissões de API** na barra de nav esquerda e examine a lista de permissões configuradas para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d811d-163">Choose **API permissions** from the left nav bar and examine the list of configured permissions for your app.</span></span> <span data-ttu-id="d811d-164">Se seu aplicativo fizer apenas chamadas de API RSC Graph, exclua toda a permissão nessa página.</span><span class="sxs-lookup"><span data-stu-id="d811d-164">If your app will only make RSC Graph API calls, delete all the permission on that page.</span></span> <span data-ttu-id="d811d-165">Se seu aplicativo também fizer chamadas não RSC, mantenha essas permissões conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="d811d-165">If your app will also make non-RSC calls, keep those permissions as needed.</span></span>

>[!IMPORTANT]
><span data-ttu-id="d811d-166">O portal do Azure AD não pode ser usado para solicitar permissões RSC.</span><span class="sxs-lookup"><span data-stu-id="d811d-166">The Azure AD portal cannot be used to request RSC permissions.</span></span> <span data-ttu-id="d811d-167">As permissões RSC atualmente são exclusivas Teams aplicativos instalados no cliente Teams e são declaradas no arquivo JSON (manifesto do aplicativo).</span><span class="sxs-lookup"><span data-stu-id="d811d-167">RSC permissions are currently exclusive to Teams applications installed in the Teams client and are declared in the app manifest (JSON) file.</span></span>

## <a name="obtain-an-access-token-from-the-microsoft-identity-platform"></a><span data-ttu-id="d811d-168">Obtenha um token de acesso do plataforma de identidade da Microsoft</span><span class="sxs-lookup"><span data-stu-id="d811d-168">Obtain an access token from the Microsoft identity platform</span></span>

<span data-ttu-id="d811d-169">Para fazer Graph de API, você deve obter um token de acesso para seu aplicativo a partir da plataforma de identidade.</span><span class="sxs-lookup"><span data-stu-id="d811d-169">To make Graph API calls, you must obtain an access token for your app from the identity platform.</span></span> <span data-ttu-id="d811d-170">Para que seu aplicativo possa obter um token do plataforma de identidade da Microsoft, ele deve ser registrado no portal do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="d811d-170">Before your app can get a token from the Microsoft identity platform, it must be registered in the Azure AD portal.</span></span> <span data-ttu-id="d811d-171">O token de acesso contém informações sobre seu aplicativo e as permissões que ele possui para os recursos e APIs disponíveis no Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="d811d-171">The access token contains information about your app and the permissions it has for the resources and APIs available through Microsoft Graph.</span></span>

<span data-ttu-id="d811d-172">Você precisará ter os seguintes valores do processo de registro do Azure AD para recuperar um token de acesso da plataforma de identidade:</span><span class="sxs-lookup"><span data-stu-id="d811d-172">You'll need to have the following values from the Azure AD registration process to retrieve an access token from the identity platform:</span></span>

- <span data-ttu-id="d811d-173">A **ID do aplicativo** atribuída pelo portal de registro do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d811d-173">The **Application ID** assigned by the app registration portal.</span></span> <span data-ttu-id="d811d-174">Se seu aplicativo oferece suporte a SSO (login único), você deve usar a mesma ID do Aplicativo para seu aplicativo e SSO.</span><span class="sxs-lookup"><span data-stu-id="d811d-174">If your app supports single sign-on (SSO) you should use the same Application ID for your app and SSO.</span></span>
- <span data-ttu-id="d811d-175">O  **segredo/senha do cliente** ou um par de chaves públicas/privadas (**Certificado**).</span><span class="sxs-lookup"><span data-stu-id="d811d-175">The  **Client secret/password** or a public/private key pair (**Certificate**).</span></span> <span data-ttu-id="d811d-176">Isso não é necessário para aplicativos nativos.</span><span class="sxs-lookup"><span data-stu-id="d811d-176">This is not required for native apps.</span></span>
- <span data-ttu-id="d811d-177">Um **URI de redirecionamento** (ou URL de resposta) para seu aplicativo receber respostas do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="d811d-177">A **Redirect URI** (or reply URL) for your app to receive responses from Azure AD.</span></span>

 <span data-ttu-id="d811d-178">*Consulte* [Obter acesso em nome de um usuário e](/graph/auth-v2-user?view=graph-rest-1.0#3-get-a-token&preserve-view=true) Obter acesso sem um [usuário](/graph/auth-v2-service)</span><span class="sxs-lookup"><span data-stu-id="d811d-178">*See* [Get access on behalf of a user](/graph/auth-v2-user?view=graph-rest-1.0#3-get-a-token&preserve-view=true) and [Get access without a user](/graph/auth-v2-service)</span></span>

## <a name="update-your-teams-app-manifest"></a><span data-ttu-id="d811d-179">Atualizar seu manifesto Teams aplicativo</span><span class="sxs-lookup"><span data-stu-id="d811d-179">Update your Teams app manifest</span></span>

<span data-ttu-id="d811d-180">As permissões RSC são declaradas no arquivo JSON (manifesto do aplicativo).</span><span class="sxs-lookup"><span data-stu-id="d811d-180">The RSC permissions are declared in your app manifest (JSON) file.</span></span>  <span data-ttu-id="d811d-181">Adicione uma [chave webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) ao manifesto do aplicativo com os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="d811d-181">Add a [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) key to your app manifest with the following values:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="d811d-182">**id**  — sua id de aplicativo do Azure AD. Para obter mais informações, consulte [Register your app in the Azure AD portal](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).</span><span class="sxs-lookup"><span data-stu-id="d811d-182">**id**  — your Azure AD app id. For more information, see [Register your app in the Azure AD portal](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).</span></span>
> - <span data-ttu-id="d811d-183">**resource**  — qualquer cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d811d-183">**resource**  — any string.</span></span> <span data-ttu-id="d811d-184">Este campo não tem operação no RSC, mas deve ser adicionado e ter um valor para evitar uma resposta de erro; qualquer cadeia de caracteres fará.</span><span class="sxs-lookup"><span data-stu-id="d811d-184">This field has no operation in RSC, but must be added and have a value to avoid an error response; any string will do.</span></span>
> - <span data-ttu-id="d811d-185">**permissões de aplicativo** — permissões RSC para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d811d-185">**application permissions** — RSC permissions for  your app.</span></span> <span data-ttu-id="d811d-186">Para obter mais informações, consulte [Permissões específicas do recurso](resource-specific-consent.md#resource-specific-permissions).</span><span class="sxs-lookup"><span data-stu-id="d811d-186">For more information, see [Resource-specific Permissions](resource-specific-consent.md#resource-specific-permissions).</span></span>

>
>[!IMPORTANT]
> <span data-ttu-id="d811d-187">As permissões não RSC são armazenadas no portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="d811d-187">Non-RSC permissions are stored in the Azure portal.</span></span> <span data-ttu-id="d811d-188">Não os adicione ao manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d811d-188">Do not add them to the app manifest.</span></span>
>

```json
"webApplicationInfo": {
    "id": "XXxxXXXXX-XxXX-xXXX-XXxx-XXXXXXXxxxXX",
    "resource": "https://RscBasedStoreApp",
    "applicationPermissions": [
      "TeamSettings.Read.Group",
      "ChannelMessage.Read.Group",
      "TeamSettings.Edit.Group",
      "ChannelSettings.ReadWrite.Group",
      "Channel.Create.Group",
      "Channel.Delete.Group",
      "TeamsApp.Read.Group",
      "TeamsTab.Read.Group",
      "TeamsTab.Create.Group",
      "TeamsTab.ReadWrite.Group",
      "TeamsTab.Delete.Group",
      "Member.Read.Group",
      "Owner.Read.Group"
    ]
  }
```

## <a name="sideload-your-app-in-teams"></a><span data-ttu-id="d811d-189">Fazer sideload do aplicativo Teams</span><span class="sxs-lookup"><span data-stu-id="d811d-189">Sideload your app in Teams</span></span>

<span data-ttu-id="d811d-190">Se o administrador Teams permite carregamentos de aplicativos personalizados, você pode [fazer sideload](~/concepts/deploy-and-publish/apps-upload.md) do aplicativo diretamente em uma equipe específica.</span><span class="sxs-lookup"><span data-stu-id="d811d-190">If your Teams admin allows custom app uploads, you can [sideload your app](~/concepts/deploy-and-publish/apps-upload.md) directly to a specific team.</span></span>

## <a name="check-your-app-for-added-rsc-permissions"></a><span data-ttu-id="d811d-191">Verifique se o aplicativo tem permissões RSC adicionadas</span><span class="sxs-lookup"><span data-stu-id="d811d-191">Check your app for added RSC permissions</span></span>

>[!IMPORTANT]
><span data-ttu-id="d811d-192">As permissões RSC não são atribuídas a um usuário.</span><span class="sxs-lookup"><span data-stu-id="d811d-192">The RSC permissions are not attributed to a user.</span></span> <span data-ttu-id="d811d-193">As chamadas são feitas com permissões de aplicativo, não permissões delegadas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="d811d-193">Calls are made with app permissions, not user delegated permissions.</span></span> <span data-ttu-id="d811d-194">Assim, o aplicativo pode ter permissão para executar ações que o usuário não pode, como criar um canal ou excluir uma guia. Você deve analisar a intenção do proprietário da equipe para seu caso de uso antes de fazer chamadas de API RSC.</span><span class="sxs-lookup"><span data-stu-id="d811d-194">Thus, the app may be allowed to perform actions that the user cannot, such as creating a channel or deleting a tab. You should review the team owner's intent for your use case prior to making RSC API calls.</span></span> <span data-ttu-id="d811d-195">Para obter mais informações, [consulte Microsoft Teams visão geral da API](/graph/teams-concept-overview).</span><span class="sxs-lookup"><span data-stu-id="d811d-195">For more information, see [Microsoft Teams API overview](/graph/teams-concept-overview).</span></span>

<span data-ttu-id="d811d-196">Depois que o aplicativo for instalado em uma equipe, você poderá usar o [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer) para exibir as permissões que foram concedidas ao aplicativo em uma equipe:</span><span class="sxs-lookup"><span data-stu-id="d811d-196">Once the app has been installed to a team, you can use [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer)  to view the permissions that have been granted to the app in a team:</span></span>

> [!div class="checklist"]
>
>- <span data-ttu-id="d811d-197">Obter **groupId** da equipe do cliente Teams.</span><span class="sxs-lookup"><span data-stu-id="d811d-197">Get the team's **groupId** from the Teams client.</span></span>
> - <span data-ttu-id="d811d-198">No cliente Teams, selecione **Teams** na barra de nav da extrema esquerda.</span><span class="sxs-lookup"><span data-stu-id="d811d-198">In the Teams client, select **Teams** from the far left nav bar.</span></span>
> - <span data-ttu-id="d811d-199">Selecione a equipe onde o aplicativo está instalado no menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="d811d-199">Select the team where the app is installed from the drop-down menu.</span></span>
> - <span data-ttu-id="d811d-200">Selecione o **ícone Mais opções** (&#8943;).</span><span class="sxs-lookup"><span data-stu-id="d811d-200">Select the **More options** icon (&#8943;).</span></span>
> - <span data-ttu-id="d811d-201">Selecione **Obter link para a equipe**.</span><span class="sxs-lookup"><span data-stu-id="d811d-201">Select **Get link to team**.</span></span>
> - <span data-ttu-id="d811d-202">Copie e salve o **valor groupId** da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d811d-202">Copy and save the **groupId** value from the string.</span></span>
> - <span data-ttu-id="d811d-203">Faça **logoff Graph Explorer**.</span><span class="sxs-lookup"><span data-stu-id="d811d-203">Log into **Graph Explorer**.</span></span>
> - <span data-ttu-id="d811d-204">Faça uma **chamada GET** para o seguinte ponto de extremidade: `https://graph.microsoft.com/beta/groups/{teamGroupId}/permissionGrants` .</span><span class="sxs-lookup"><span data-stu-id="d811d-204">Make a **GET** call to the following endpoint: `https://graph.microsoft.com/beta/groups/{teamGroupId}/permissionGrants`.</span></span> <span data-ttu-id="d811d-205">O campo clientAppId na resposta será mapeado para o appId especificado no manifesto Teams aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d811d-205">The clientAppId field in the response will map to the appId specified in the Teams app manifest.</span></span>
  <span data-ttu-id="d811d-206">![Graph resposta do explorer à chamada GET.](../../assets/images/graph-permissions.png)</span><span class="sxs-lookup"><span data-stu-id="d811d-206">![Graph explorer response to GET call.](../../assets/images/graph-permissions.png)</span></span>

## <a name="code-sample"></a><span data-ttu-id="d811d-207">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="d811d-207">Code sample</span></span>
| <span data-ttu-id="d811d-208">**Exemplo de nome**</span><span class="sxs-lookup"><span data-stu-id="d811d-208">**Sample name**</span></span> | <span data-ttu-id="d811d-209">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="d811d-209">**Description**</span></span> | <span data-ttu-id="d811d-210">**.NET**</span><span class="sxs-lookup"><span data-stu-id="d811d-210">**.NET**</span></span> |<span data-ttu-id="d811d-211">**Node.js**</span><span class="sxs-lookup"><span data-stu-id="d811d-211">**Node.js**</span></span> |
|-----------------|-----------------|----------------|----------------|
| <span data-ttu-id="d811d-212">Consentimento Específico do Recurso (RSC)</span><span class="sxs-lookup"><span data-stu-id="d811d-212">Resource Specific Consent (RSC)</span></span> | <span data-ttu-id="d811d-213">Use RSC para chamar Graph APIs.</span><span class="sxs-lookup"><span data-stu-id="d811d-213">Use RSC to call Graph APIs.</span></span> | [<span data-ttu-id="d811d-214">View</span><span class="sxs-lookup"><span data-stu-id="d811d-214">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-rsc/csharp)|[<span data-ttu-id="d811d-215">View</span><span class="sxs-lookup"><span data-stu-id="d811d-215">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-rsc/nodeJs)|



## <a name="see-also"></a><span data-ttu-id="d811d-216">Confira também</span><span class="sxs-lookup"><span data-stu-id="d811d-216">See also</span></span>
 
* [<span data-ttu-id="d811d-217">Testar permissões de consentimento específicas do recurso Teams</span><span class="sxs-lookup"><span data-stu-id="d811d-217">Test resource-specific consent permissions in Teams</span></span>](test-resource-specific-consent.md)
* [<span data-ttu-id="d811d-218">Consentimento específico do recurso no Microsoft Teams para administradores</span><span class="sxs-lookup"><span data-stu-id="d811d-218">Resource-specific consent in Microsoft Teams for admins</span></span>](/MicrosoftTeams/resource-specific-consent)


