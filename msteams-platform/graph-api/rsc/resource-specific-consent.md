---
title: Consentimento específico do recurso no Teams
description: Descreve o consentimento específico do recurso no Teams e como tirar proveito dele.
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: reference
keywords: autorização do teams OAuth SSO AAD rsc Graph
ms.openlocfilehash: cf57637dac91fae14473a831e76f868f458d8f27
ms.sourcegitcommit: f5ee3fa5ef6126d9bf845948d27d9067b3bbb994
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2021
ms.locfileid: "51596214"
---
# <a name="resource-specific-consent-rsc"></a><span data-ttu-id="df411-104">Consentimento específico do recurso (RSC)</span><span class="sxs-lookup"><span data-stu-id="df411-104">Resource-specific consent (RSC)</span></span>

<span data-ttu-id="df411-105">O RSC (consentimento específico de recursos) é uma integração da API do Microsoft Teams e do Microsoft Graph que permite que seu aplicativo use pontos de extremidade da API para gerenciar equipes específicas dentro de uma organização.</span><span class="sxs-lookup"><span data-stu-id="df411-105">Resource-specific consent (RSC) is a Microsoft Teams and Microsoft Graph API integration that enables your app to use API endpoints to manage specific teams within an organization.</span></span> <span data-ttu-id="df411-106">O modelo de permissões de consentimento específico do recurso (RSC) permite que os *proprietários* da equipe concedam consentimento para que um aplicativo acesse e/ou modifique os dados de uma equipe.</span><span class="sxs-lookup"><span data-stu-id="df411-106">The resource-specific consent (RSC) permissions model enables *team owners* to grant consent for an application to access and/or modify a team's data.</span></span> <span data-ttu-id="df411-107">As permissões RSC granulares, específicas do Teams definem o que um aplicativo pode fazer em uma equipe específica:</span><span class="sxs-lookup"><span data-stu-id="df411-107">The granular, Teams-specific, RSC permissions define what an application can do within a specific team:</span></span>

## <a name="resource-specific-permissions"></a><span data-ttu-id="df411-108">Permissões específicas de recursos</span><span class="sxs-lookup"><span data-stu-id="df411-108">Resource-specific permissions</span></span>

|<span data-ttu-id="df411-109">Permissão de aplicativo</span><span class="sxs-lookup"><span data-stu-id="df411-109">Application permission</span></span>| <span data-ttu-id="df411-110">Ação</span><span class="sxs-lookup"><span data-stu-id="df411-110">Action</span></span> |
| ----- | ----- |
|<span data-ttu-id="df411-111">TeamSettings.Read.Group</span><span class="sxs-lookup"><span data-stu-id="df411-111">TeamSettings.Read.Group</span></span> | <span data-ttu-id="df411-112">Obter as configurações dessa equipe.</span><span class="sxs-lookup"><span data-stu-id="df411-112">Get the settings for this team.</span></span>|
|<span data-ttu-id="df411-113">TeamSettings.ReadWrite.Group</span><span class="sxs-lookup"><span data-stu-id="df411-113">TeamSettings.ReadWrite.Group</span></span>|<span data-ttu-id="df411-114">Atualizar as configurações para esta equipe.</span><span class="sxs-lookup"><span data-stu-id="df411-114">Update the settings for this team.</span></span>|
|<span data-ttu-id="df411-115">ChannelSettings.Read.Group</span><span class="sxs-lookup"><span data-stu-id="df411-115">ChannelSettings.Read.Group</span></span>|<span data-ttu-id="df411-116">Obter os nomes de canal, descrições de canal e configurações de canal para essa equipe.</span><span class="sxs-lookup"><span data-stu-id="df411-116">Get the channel names, channel descriptions, and channel settings for this team.</span></span>|
|<span data-ttu-id="df411-117">ChannelSettings.ReadWrite.Group</span><span class="sxs-lookup"><span data-stu-id="df411-117">ChannelSettings.ReadWrite.Group</span></span>|<span data-ttu-id="df411-118">Atualize os nomes de canal, descrições de canal e configurações de canal para essa equipe.</span><span class="sxs-lookup"><span data-stu-id="df411-118">Update the channel names, channel descriptions, and channel settings for this team.</span></span>|
|<span data-ttu-id="df411-119">Channel.Create.Group</span><span class="sxs-lookup"><span data-stu-id="df411-119">Channel.Create.Group</span></span>|<span data-ttu-id="df411-120">Criar canais nesta equipe.</span><span class="sxs-lookup"><span data-stu-id="df411-120">Create channels in this team.</span></span>|
|<span data-ttu-id="df411-121">Channel.Delete.Group</span><span class="sxs-lookup"><span data-stu-id="df411-121">Channel.Delete.Group</span></span>|<span data-ttu-id="df411-122">Exclua canais nesta equipe.</span><span class="sxs-lookup"><span data-stu-id="df411-122">Delete channels in this team.</span></span>|
|<span data-ttu-id="df411-123">ChannelMessage.Read.Group</span><span class="sxs-lookup"><span data-stu-id="df411-123">ChannelMessage.Read.Group</span></span> |<span data-ttu-id="df411-124">Receba as mensagens de canal dessa equipe.</span><span class="sxs-lookup"><span data-stu-id="df411-124">Get this team's channel messages.</span></span>|
|<span data-ttu-id="df411-125">TeamsAppInstallation.Read.Group</span><span class="sxs-lookup"><span data-stu-id="df411-125">TeamsAppInstallation.Read.Group</span></span>|<span data-ttu-id="df411-126">Obter uma lista dos aplicativos instalados dessa equipe.</span><span class="sxs-lookup"><span data-stu-id="df411-126">Get a list of this team's installed apps.</span></span>|
|<span data-ttu-id="df411-127">TeamsTab.Read.Group</span><span class="sxs-lookup"><span data-stu-id="df411-127">TeamsTab.Read.Group</span></span>|<span data-ttu-id="df411-128">Obter uma lista das guias dessa equipe.</span><span class="sxs-lookup"><span data-stu-id="df411-128">Get a list of this team's tabs.</span></span>|
|<span data-ttu-id="df411-129">TeamsTab.Create.Group</span><span class="sxs-lookup"><span data-stu-id="df411-129">TeamsTab.Create.Group</span></span>|<span data-ttu-id="df411-130">Criar guias nesta equipe.</span><span class="sxs-lookup"><span data-stu-id="df411-130">Create tabs in this team.</span></span>|
|<span data-ttu-id="df411-131">TeamsTab.ReadWrite.Group</span><span class="sxs-lookup"><span data-stu-id="df411-131">TeamsTab.ReadWrite.Group</span></span>|<span data-ttu-id="df411-132">Atualize as guias desta equipe.</span><span class="sxs-lookup"><span data-stu-id="df411-132">Update this team's tabs.</span></span>|
|<span data-ttu-id="df411-133">TeamsTab.Delete.Group</span><span class="sxs-lookup"><span data-stu-id="df411-133">TeamsTab.Delete.Group</span></span>|<span data-ttu-id="df411-134">Excluir as guias dessa equipe.</span><span class="sxs-lookup"><span data-stu-id="df411-134">Delete this team's tabs.</span></span>|
|<span data-ttu-id="df411-135">TeamMember.Read.Group</span><span class="sxs-lookup"><span data-stu-id="df411-135">TeamMember.Read.Group</span></span>|<span data-ttu-id="df411-136">Obter os membros dessa equipe.</span><span class="sxs-lookup"><span data-stu-id="df411-136">Get this team's members.</span></span>|

>[!NOTE]
><span data-ttu-id="df411-137">Permissões específicas de recursos estão disponíveis apenas para aplicativos do Teams instalados no cliente do Teams e atualmente não fazem parte do portal do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="df411-137">Resource-specific permissions are only available to Teams apps installed on the Teams client and are currently not part of the Azure Active Directory portal.</span></span>

## <a name="enable-resource-specific-consent-in-your-application"></a><span data-ttu-id="df411-138">Habilitar o consentimento específico do recurso em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="df411-138">Enable resource-specific consent in your application</span></span>

<span data-ttu-id="df411-139">As etapas para habilenciar o RSC em seu aplicativo são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="df411-139">The steps for enabling RSC in your application are as follows:</span></span>

1. <span data-ttu-id="df411-140">[Configure as configurações de consentimento do proprietário do grupo no portal do Azure Active Directory.](#configure-group-owner-consent-settings-in-the-azure-ad-portal)</span><span class="sxs-lookup"><span data-stu-id="df411-140">[Configure group owner consent settings in the Azure Active Directory portal](#configure-group-owner-consent-settings-in-the-azure-ad-portal).</span></span>
1. <span data-ttu-id="df411-141">[Registre seu aplicativo com a plataforma de identidade da Microsoft por meio do portal do Azure AD.](#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal)</span><span class="sxs-lookup"><span data-stu-id="df411-141">[Register your app with Microsoft identity platform via the Azure AD portal](#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).</span></span>
1. <span data-ttu-id="df411-142">[Revise suas permissões de aplicativo no portal do Azure AD.](#review-your-application-permissions-in-the-azure-ad-portal)</span><span class="sxs-lookup"><span data-stu-id="df411-142">[Review your application permissions in the Azure AD portal](#review-your-application-permissions-in-the-azure-ad-portal).</span></span>
1. <span data-ttu-id="df411-143">[Obtenha um token de acesso da plataforma Microsoft Identity](#obtain-an-access-token-from-the-microsoft-identity-platform).</span><span class="sxs-lookup"><span data-stu-id="df411-143">[Obtain an access token from the Microsoft Identity platform](#obtain-an-access-token-from-the-microsoft-identity-platform).</span></span>
1. <span data-ttu-id="df411-144">[Atualize o manifesto do aplicativo do Teams](#update-your-teams-app-manifest).</span><span class="sxs-lookup"><span data-stu-id="df411-144">[Update your Teams app manifest](#update-your-teams-app-manifest).</span></span>
1. <span data-ttu-id="df411-145">[Instale seu aplicativo diretamente no Teams](#install-your-app-directly-in-teams).</span><span class="sxs-lookup"><span data-stu-id="df411-145">[Install your app directly in Teams](#install-your-app-directly-in-teams).</span></span>
1. <span data-ttu-id="df411-146">[Verifique se o aplicativo tem permissões RSC adicionadas.](#check-your-app-for-added-rsc-permissions)</span><span class="sxs-lookup"><span data-stu-id="df411-146">[Check your app for added RSC permissions](#check-your-app-for-added-rsc-permissions).</span></span>

## <a name="configure-group-owner-consent-settings-in-the-azure-ad-portal"></a><span data-ttu-id="df411-147">Configurar configurações de consentimento do proprietário do grupo no portal do Azure AD</span><span class="sxs-lookup"><span data-stu-id="df411-147">Configure group owner consent settings in the Azure AD portal</span></span>

<span data-ttu-id="df411-148">Você pode habilitar ou [desabilitar o consentimento do](/azure/active-directory/manage-apps/configure-user-consent-groups?tabs=azure-portal) proprietário do grupo diretamente no portal do Azure:</span><span class="sxs-lookup"><span data-stu-id="df411-148">You can enable or disable [group owner consent](/azure/active-directory/manage-apps/configure-user-consent-groups?tabs=azure-portal) directly within the Azure portal:</span></span>

> [!div class="checklist"]
>
>- <span data-ttu-id="df411-149">Entre no [portal do Azure](https://portal.azure.com) como administrador [global/administrador da empresa.](/azure/active-directory/users-groups-roles/directory-assign-admin-roles.md#global-administrator--company-administrator)</span><span class="sxs-lookup"><span data-stu-id="df411-149">Sign in to the [Azure portal](https://portal.azure.com) as a [Global Administrator/Company Administrator](/azure/active-directory/users-groups-roles/directory-assign-admin-roles.md#global-administrator--company-administrator).</span></span>  
 > - <span data-ttu-id="df411-150">[Selecione Aplicativos](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConsentPoliciesMenuBlade/UserSettings) **do Azure Active Directory**  =>  **Enterprise** Consentimento e  =>  **permissões**  =>  **Configurações de consentimento do usuário**.</span><span class="sxs-lookup"><span data-stu-id="df411-150">[Select](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConsentPoliciesMenuBlade/UserSettings) **Azure Active Directory** => **Enterprise applications** => **Consent and permissions** => **User consent settings**.</span></span>
> - <span data-ttu-id="df411-151">Habilitar, desabilitar ou limitar o consentimento do usuário com o controle rotulado consentimento do proprietário do grupo para aplicativos que acessam dados **(O** padrão é Permitir o consentimento do proprietário do grupo para todos os proprietários **do grupo**).</span><span class="sxs-lookup"><span data-stu-id="df411-151">Enable, disable, or limit user consent with the control labeled **Group owner consent for apps accessing data** (The default is **Allow group owner consent for all group owners**).</span></span> <span data-ttu-id="df411-152">Para que o proprietário da equipe instale um aplicativo usando o RSC, o consentimento do proprietário do grupo deve ser habilitado para esse usuário.</span><span class="sxs-lookup"><span data-stu-id="df411-152">For a team owner to install an app using RSC, group owner consent must be enabled for that user.</span></span>

![Configuração rsc do azure](../../assets/images/azure-rsc-configuration.png)

<span data-ttu-id="df411-154">Para habilitar ou desabilitar o consentimento do proprietário do grupo usando o PowerShell, siga as etapas descritas em [Configure group owner consent using PowerShell](/azure/active-directory/manage-apps/configure-user-consent-groups?tabs=azure-powershell).</span><span class="sxs-lookup"><span data-stu-id="df411-154">To enable or disable group owner consent using PowerShell, follow the steps outlined in [Configure group owner consent using PowerShell](/azure/active-directory/manage-apps/configure-user-consent-groups?tabs=azure-powershell).</span></span>

## <a name="register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal"></a><span data-ttu-id="df411-155">Registrar seu aplicativo com a plataforma de identidade da Microsoft por meio do portal do Azure AD</span><span class="sxs-lookup"><span data-stu-id="df411-155">Register your app with Microsoft identity platform via the Azure AD portal</span></span>

<span data-ttu-id="df411-156">O portal do Azure Active Directory fornece uma plataforma central para você registrar e configurar seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="df411-156">The Azure Active Directory portal provides a central platform for you to register and configure your apps.</span></span> <span data-ttu-id="df411-157">Seu aplicativo deve ser registrado no portal do Azure AD para se integrar à plataforma de identidade da Microsoft e chamar APIs do Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="df411-157">Your app must be registered in the Azure AD portal to integrate with the Microsoft identity platform and call Microsoft Graph APIs.</span></span> <span data-ttu-id="df411-158">*Consulte* [Registrar um aplicativo com a plataforma de identidade da Microsoft.](/graph/auth-register-app-v2)</span><span class="sxs-lookup"><span data-stu-id="df411-158">*See* [Register an application with the Microsoft identity platform](/graph/auth-register-app-v2).</span></span>

>[!WARNING]
><span data-ttu-id="df411-159">Não registre vários aplicativos do Teams na mesma ID de aplicativo do Azure AD. A id do aplicativo deve ser exclusiva para cada aplicativo.</span><span class="sxs-lookup"><span data-stu-id="df411-159">Do not register multiple Teams apps to the same Azure AD app id. The app id must be unique for each app.</span></span> <span data-ttu-id="df411-160">As tentativas de instalar vários aplicativos na mesma ID do aplicativo falharão.</span><span class="sxs-lookup"><span data-stu-id="df411-160">Attempts to install multiple apps to the same app id will fail.</span></span>

## <a name="review-your-application-permissions-in-the-azure-ad-portal"></a><span data-ttu-id="df411-161">Revise suas permissões de aplicativo no portal do Azure AD</span><span class="sxs-lookup"><span data-stu-id="df411-161">Review your application permissions in the Azure AD portal</span></span>

<span data-ttu-id="df411-162">Navegue até **a página Registros** do Aplicativo Inicial e selecione seu aplicativo  =>   RSC.</span><span class="sxs-lookup"><span data-stu-id="df411-162">Navigate to the **Home** => **App registrations** page and select your RSC app.</span></span> <span data-ttu-id="df411-163">Escolha **permissões de API** na barra de nav esquerda e examine a lista de permissões configuradas para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="df411-163">Choose **API permissions** from the left nav bar and examine the list of configured permissions for your app.</span></span> <span data-ttu-id="df411-164">Se seu aplicativo fizer apenas chamadas de API RSC Graph, exclua toda a permissão nessa página.</span><span class="sxs-lookup"><span data-stu-id="df411-164">If your app will only make RSC Graph API calls, delete all the permission on that page.</span></span> <span data-ttu-id="df411-165">Se seu aplicativo também fizer chamadas não RSC, mantenha essas permissões conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="df411-165">If your app will also make non-RSC calls, keep those permissions as needed.</span></span>

>[!IMPORTANT]
><span data-ttu-id="df411-166">O portal do Azure AD não pode ser usado para solicitar permissões RSC.</span><span class="sxs-lookup"><span data-stu-id="df411-166">The Azure AD portal cannot be used to request RSC permissions.</span></span> <span data-ttu-id="df411-167">No momento, as permissões RSC são exclusivas para aplicativos do Teams instalados no cliente do Teams e são declaradas no arquivo JSON (manifesto do aplicativo).</span><span class="sxs-lookup"><span data-stu-id="df411-167">RSC permissions are currently exclusive to Teams applications installed in the Teams client and are declared in the app manifest (JSON) file.</span></span>

## <a name="obtain-an-access-token-from-the-microsoft-identity-platform"></a><span data-ttu-id="df411-168">Obter um token de acesso da plataforma de identidade da Microsoft</span><span class="sxs-lookup"><span data-stu-id="df411-168">Obtain an access token from the Microsoft identity platform</span></span>

<span data-ttu-id="df411-169">Para fazer chamadas de API do Graph, você deve obter um token de acesso para seu aplicativo a partir da plataforma de identidade.</span><span class="sxs-lookup"><span data-stu-id="df411-169">To make Graph API calls, you must obtain an access token for your app from the identity platform.</span></span> <span data-ttu-id="df411-170">Para que seu aplicativo possa obter um token da plataforma de identidade da Microsoft, ele deve ser registrado no portal do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="df411-170">Before your app can get a token from the Microsoft identity platform, it must be registered in the Azure AD portal.</span></span> <span data-ttu-id="df411-171">O token de acesso contém informações sobre seu aplicativo e as permissões que ele possui para os recursos e APIs disponíveis no Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="df411-171">The access token contains information about your app and the permissions it has for the resources and APIs available through Microsoft Graph.</span></span>

<span data-ttu-id="df411-172">Você precisará ter os seguintes valores do processo de registro do Azure AD para recuperar um token de acesso da plataforma de identidade:</span><span class="sxs-lookup"><span data-stu-id="df411-172">You'll need to have the following values from the Azure AD registration process to retrieve an access token from the identity platform:</span></span>

- <span data-ttu-id="df411-173">A **ID do aplicativo** atribuída pelo portal de registro do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="df411-173">The **Application ID** assigned by the app registration portal.</span></span> <span data-ttu-id="df411-174">Se seu aplicativo oferece suporte a SSO (login único), você deve usar a mesma ID do Aplicativo para seu aplicativo e SSO.</span><span class="sxs-lookup"><span data-stu-id="df411-174">If your app supports single sign-on (SSO) you should use the same Application ID for your app and SSO.</span></span>
- <span data-ttu-id="df411-175">O  **segredo/senha do cliente** ou um par de chaves públicas/privadas (**Certificado**).</span><span class="sxs-lookup"><span data-stu-id="df411-175">The  **Client secret/password** or a public/private key pair (**Certificate**).</span></span> <span data-ttu-id="df411-176">Isso não é necessário para aplicativos nativos.</span><span class="sxs-lookup"><span data-stu-id="df411-176">This is not required for native apps.</span></span>
- <span data-ttu-id="df411-177">Um **URI de redirecionamento** (ou URL de resposta) para seu aplicativo receber respostas do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="df411-177">A **Redirect URI** (or reply URL) for your app to receive responses from Azure AD.</span></span>

 <span data-ttu-id="df411-178">*Consulte* [Obter acesso em nome de um usuário e](/graph/auth-v2-user?view=graph-rest-1.0#3-get-a-token&preserve-view=true) Obter acesso sem um [usuário](/graph/auth-v2-service)</span><span class="sxs-lookup"><span data-stu-id="df411-178">*See* [Get access on behalf of a user](/graph/auth-v2-user?view=graph-rest-1.0#3-get-a-token&preserve-view=true) and [Get access without a user](/graph/auth-v2-service)</span></span>

## <a name="update-your-teams-app-manifest"></a><span data-ttu-id="df411-179">Atualizar o manifesto do aplicativo do Teams</span><span class="sxs-lookup"><span data-stu-id="df411-179">Update your Teams app manifest</span></span>

<span data-ttu-id="df411-180">As permissões RSC são declaradas no arquivo JSON (manifesto do aplicativo).</span><span class="sxs-lookup"><span data-stu-id="df411-180">The RSC permissions are declared in your app manifest (JSON) file.</span></span>  <span data-ttu-id="df411-181">Adicione uma [chave webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) ao manifesto do aplicativo com os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="df411-181">Add a [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) key to your app manifest with the following values:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="df411-182">**id**  — sua id de aplicativo do Azure AD. *Consulte* [Registrar seu aplicativo no portal do Azure AD](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).</span><span class="sxs-lookup"><span data-stu-id="df411-182">**id**  — your Azure AD app id. *See* [Register your app in the Azure AD portal](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).</span></span>
> - <span data-ttu-id="df411-183">**resource**  — qualquer cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="df411-183">**resource**  — any string.</span></span> <span data-ttu-id="df411-184">Este campo não tem operação no RSC, mas deve ser adicionado e ter um valor para evitar uma resposta de erro; qualquer cadeia de caracteres fará.</span><span class="sxs-lookup"><span data-stu-id="df411-184">This field has no operation in RSC, but must be added and have a value to avoid an error response; any string will do.</span></span>
> - <span data-ttu-id="df411-185">**permissões de aplicativo** — permissões RSC para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="df411-185">**application permissions** — RSC permissions for  your app.</span></span> <span data-ttu-id="df411-186">*Consulte* [Permissões específicas do recurso](resource-specific-consent.md#resource-specific-permissions).</span><span class="sxs-lookup"><span data-stu-id="df411-186">*See* [Resource-specific Permissions](resource-specific-consent.md#resource-specific-permissions).</span></span>

>
>[!IMPORTANT]
> <span data-ttu-id="df411-187">As permissões não RSC são armazenadas no portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="df411-187">Non-RSC permissions are stored in the Azure portal.</span></span> <span data-ttu-id="df411-188">Não os adicione ao manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="df411-188">Do not add them to the app manifest.</span></span>
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

## <a name="install-your-app-directly-in-teams"></a><span data-ttu-id="df411-189">Instalar seu aplicativo diretamente no Teams</span><span class="sxs-lookup"><span data-stu-id="df411-189">Install your app directly in Teams</span></span>

<span data-ttu-id="df411-190">Depois de criar seu aplicativo, você pode [carregar seu pacote de aplicativos](../../concepts/deploy-and-publish/apps-upload.md#upload-your-package-into-a-team-using-the-apps-tab) diretamente em uma equipe específica.</span><span class="sxs-lookup"><span data-stu-id="df411-190">Once you've created your app you can [upload your app package](../../concepts/deploy-and-publish/apps-upload.md#upload-your-package-into-a-team-using-the-apps-tab) directly to a specific team.</span></span>  <span data-ttu-id="df411-191">Para fazer isso, a configuração de política **carregar aplicativos** personalizados deve ser habilitada como parte das políticas de configuração de aplicativos personalizadas.</span><span class="sxs-lookup"><span data-stu-id="df411-191">To do so, the **Upload custom apps** policy setting must be enabled as part of the custom app setup policies.</span></span> <span data-ttu-id="df411-192">*Consulte* [Configurações de política de aplicativo personalizadas](/microsoftteams/teams-custom-app-policies-and-settings#custom-app-policy-and-settings).</span><span class="sxs-lookup"><span data-stu-id="df411-192">*See* [Custom app policy settings](/microsoftteams/teams-custom-app-policies-and-settings#custom-app-policy-and-settings).</span></span>

## <a name="check-your-app-for-added-rsc-permissions"></a><span data-ttu-id="df411-193">Verifique se o aplicativo tem permissões RSC adicionadas</span><span class="sxs-lookup"><span data-stu-id="df411-193">Check your app for added RSC permissions</span></span>

>[!IMPORTANT]
><span data-ttu-id="df411-194">As permissões RSC não são atribuídas a um usuário.</span><span class="sxs-lookup"><span data-stu-id="df411-194">The RSC permissions are not attributed to a user.</span></span> <span data-ttu-id="df411-195">As chamadas são feitas com permissões de aplicativo, não permissões delegadas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="df411-195">Calls are made with app permissions, not user delegated permissions.</span></span> <span data-ttu-id="df411-196">Assim, o aplicativo pode ter permissão para executar ações que o usuário não pode, como criar um canal ou excluir uma guia. Você deve analisar a intenção do proprietário da equipe para seu caso de uso antes de fazer chamadas de API RSC.</span><span class="sxs-lookup"><span data-stu-id="df411-196">Thus, the app may be allowed to perform actions that the user cannot, such as creating a channel or deleting a tab. You should review the team owner's intent for your use case prior to making RSC API calls.</span></span> <span data-ttu-id="df411-197">*Consulte Visão* [geral da API do Microsoft Teams](/graph/teams-concept-overview).</span><span class="sxs-lookup"><span data-stu-id="df411-197">*See* [Microsoft Teams API overview](/graph/teams-concept-overview).</span></span>

<span data-ttu-id="df411-198">Depois que o aplicativo for instalado em uma equipe, você poderá usar o [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer)  para exibir as permissões que foram concedidas ao aplicativo em uma equipe:</span><span class="sxs-lookup"><span data-stu-id="df411-198">Once the app has been installed to a team, you can use [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer)  to view the permissions that have been granted to the app in a team:</span></span>

> [!div class="checklist"]
>
>- <span data-ttu-id="df411-199">Obter **groupId** da equipe do cliente teams.</span><span class="sxs-lookup"><span data-stu-id="df411-199">Get the team's **groupId** from the Teams client.</span></span>
> - <span data-ttu-id="df411-200">No cliente teams, selecione **Teams** na barra de nav da extrema esquerda.</span><span class="sxs-lookup"><span data-stu-id="df411-200">In the Teams client, select **Teams** from the far left nav bar.</span></span>
> - <span data-ttu-id="df411-201">Selecione a equipe onde o aplicativo está instalado no menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="df411-201">Select the team where the app is installed from the drop-down menu.</span></span>
> - <span data-ttu-id="df411-202">Selecione o **ícone Mais opções** (&#8943;).</span><span class="sxs-lookup"><span data-stu-id="df411-202">Select the **More options** icon (&#8943;).</span></span>
> - <span data-ttu-id="df411-203">Selecione **Obter link para a equipe**.</span><span class="sxs-lookup"><span data-stu-id="df411-203">Select **Get link to team**.</span></span>
> - <span data-ttu-id="df411-204">Copie e salve o **valor groupId** da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="df411-204">Copy and save the **groupId** value from the string.</span></span>
> - <span data-ttu-id="df411-205">Faça logoff **no Graph Explorer**.</span><span class="sxs-lookup"><span data-stu-id="df411-205">Log into **Graph Explorer**.</span></span>
> - <span data-ttu-id="df411-206">Faça uma **chamada GET** para o seguinte ponto de extremidade: `https://graph.microsoft.com/beta/groups/{teamGroupId}/permissionGrants` .</span><span class="sxs-lookup"><span data-stu-id="df411-206">Make a **GET** call to the following endpoint: `https://graph.microsoft.com/beta/groups/{teamGroupId}/permissionGrants`.</span></span> <span data-ttu-id="df411-207">O campo clientAppId na resposta será mapeado para o appId especificado no manifesto do aplicativo do Teams.</span><span class="sxs-lookup"><span data-stu-id="df411-207">The clientAppId field in the response will map to the appId specified in the Teams app manifest.</span></span>
  <span data-ttu-id="df411-208">![Resposta do explorador de gráfico à chamada GET.](../../assets/images/graph-permissions.png)</span><span class="sxs-lookup"><span data-stu-id="df411-208">![Graph explorer response to GET call.](../../assets/images/graph-permissions.png)</span></span>

## <a name="code-sample"></a><span data-ttu-id="df411-209">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="df411-209">Code sample</span></span>
| <span data-ttu-id="df411-210">**Exemplo de nome**</span><span class="sxs-lookup"><span data-stu-id="df411-210">**Sample name**</span></span> | <span data-ttu-id="df411-211">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="df411-211">**Description**</span></span> | <span data-ttu-id="df411-212">**.NET**</span><span class="sxs-lookup"><span data-stu-id="df411-212">**.NET**</span></span> |<span data-ttu-id="df411-213">**Node.js**</span><span class="sxs-lookup"><span data-stu-id="df411-213">**Node.js**</span></span> |
|-----------------|-----------------|----------------|----------------|
| <span data-ttu-id="df411-214">Consentimento Específico do Recurso (RSC)</span><span class="sxs-lookup"><span data-stu-id="df411-214">Resource Specific Consent (RSC)</span></span> | <span data-ttu-id="df411-215">Use o RSC para chamar APIs do Graph.</span><span class="sxs-lookup"><span data-stu-id="df411-215">Use RSC to call Graph APIs.</span></span> | [<span data-ttu-id="df411-216">View</span><span class="sxs-lookup"><span data-stu-id="df411-216">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-rsc/csharp)|[<span data-ttu-id="df411-217">View</span><span class="sxs-lookup"><span data-stu-id="df411-217">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-rsc/nodeJs)|



## <a name="test-resource-specific-consent"></a><span data-ttu-id="df411-218">Testar o consentimento específico do recurso</span><span class="sxs-lookup"><span data-stu-id="df411-218">Test resource-specific consent</span></span>
 
> [!div class="nextstepaction"]
> [<span data-ttu-id="df411-219">**Testar permissões de consentimento específicas do recurso no Teams**</span><span class="sxs-lookup"><span data-stu-id="df411-219">**Test resource-specific consent permissions in Teams**</span></span>](test-resource-specific-consent.md)
 
## <a name="related-topic-for-teams-administrators"></a><span data-ttu-id="df411-220">Tópico relacionado para administradores do Teams</span><span class="sxs-lookup"><span data-stu-id="df411-220">Related topic for Teams administrators</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="df411-221">**Consentimento específico de recursos no Microsoft Teams para administradores**</span><span class="sxs-lookup"><span data-stu-id="df411-221">**Resource-specific consent in Microsoft Teams for admins**</span></span>](/MicrosoftTeams/resource-specific-consent)
> 

