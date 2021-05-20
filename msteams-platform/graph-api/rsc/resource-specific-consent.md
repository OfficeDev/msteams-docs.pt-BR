---
title: Consentimento específico de recursos em Teams
description: Descreve o consentimento específico de recursos em Teams e como fazer proveito disso.
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: reference
keywords: equipes autorização OAuth SSO AAD rsc Graph
ms.openlocfilehash: dabe0c33013fbb398eee7bf00ac2881cd86e6bc5
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566121"
---
# <a name="resource-specific-consent-rsc"></a><span data-ttu-id="7376b-104">Consentimento específico para recursos (RSC)</span><span class="sxs-lookup"><span data-stu-id="7376b-104">Resource-specific consent (RSC)</span></span>

<span data-ttu-id="7376b-105">O RSC (Resource-Specific Consent, consentimento específico para recursos) é uma integração de API Microsoft Teams e microsoft Graph que permite que seu aplicativo use pontos finais de API para gerenciar equipes específicas dentro de uma organização.</span><span class="sxs-lookup"><span data-stu-id="7376b-105">Resource-specific consent (RSC) is a Microsoft Teams and Microsoft Graph API integration that enables your app to use API endpoints to manage specific teams within an organization.</span></span> <span data-ttu-id="7376b-106">O modelo de permissões de consentimento específico para recursos (RSC) permite que *os proprietários de equipe* concedam consentimento para um aplicativo acessar e/ou modificar os dados de uma equipe.</span><span class="sxs-lookup"><span data-stu-id="7376b-106">The resource-specific consent (RSC) permissions model enables *team owners* to grant consent for an application to access and/or modify a team's data.</span></span> <span data-ttu-id="7376b-107">As permissões RSC granulares, Teams específicas, definem o que um aplicativo pode fazer dentro de uma equipe específica:</span><span class="sxs-lookup"><span data-stu-id="7376b-107">The granular, Teams-specific, RSC permissions define what an application can do within a specific team:</span></span>

## <a name="resource-specific-permissions"></a><span data-ttu-id="7376b-108">Permissões específicas de recursos</span><span class="sxs-lookup"><span data-stu-id="7376b-108">Resource-specific permissions</span></span>

|<span data-ttu-id="7376b-109">Permissão de aplicativo</span><span class="sxs-lookup"><span data-stu-id="7376b-109">Application permission</span></span>| <span data-ttu-id="7376b-110">Action</span><span class="sxs-lookup"><span data-stu-id="7376b-110">Action</span></span> |
| ----- | ----- |
|<span data-ttu-id="7376b-111">TeamSettings.Read.Group</span><span class="sxs-lookup"><span data-stu-id="7376b-111">TeamSettings.Read.Group</span></span> | <span data-ttu-id="7376b-112">Pegue as configurações para esta equipe.</span><span class="sxs-lookup"><span data-stu-id="7376b-112">Get the settings for this team.</span></span>|
|<span data-ttu-id="7376b-113">TeamSettings.ReadWrite.Group</span><span class="sxs-lookup"><span data-stu-id="7376b-113">TeamSettings.ReadWrite.Group</span></span>|<span data-ttu-id="7376b-114">Atualizar as configurações para esta equipe.</span><span class="sxs-lookup"><span data-stu-id="7376b-114">Update the settings for this team.</span></span>|
|<span data-ttu-id="7376b-115">ChannelSettings.Read.Group</span><span class="sxs-lookup"><span data-stu-id="7376b-115">ChannelSettings.Read.Group</span></span>|<span data-ttu-id="7376b-116">Obtenha os nomes do canal, as descrições do canal e as configurações do canal para esta equipe.</span><span class="sxs-lookup"><span data-stu-id="7376b-116">Get the channel names, channel descriptions, and channel settings for this team.</span></span>|
|<span data-ttu-id="7376b-117">ChannelSettings.ReadWrite.Group</span><span class="sxs-lookup"><span data-stu-id="7376b-117">ChannelSettings.ReadWrite.Group</span></span>|<span data-ttu-id="7376b-118">Atualize os nomes dos canais, as descrições dos canais e as configurações do canal para esta equipe.</span><span class="sxs-lookup"><span data-stu-id="7376b-118">Update the channel names, channel descriptions, and channel settings for this team.</span></span>|
|<span data-ttu-id="7376b-119">Channel.Create.Group</span><span class="sxs-lookup"><span data-stu-id="7376b-119">Channel.Create.Group</span></span>|<span data-ttu-id="7376b-120">Criar canais nesta equipe.</span><span class="sxs-lookup"><span data-stu-id="7376b-120">Create channels in this team.</span></span>|
|<span data-ttu-id="7376b-121">Channel.Delete.Group</span><span class="sxs-lookup"><span data-stu-id="7376b-121">Channel.Delete.Group</span></span>|<span data-ttu-id="7376b-122">Exclua canais nesta equipe.</span><span class="sxs-lookup"><span data-stu-id="7376b-122">Delete channels in this team.</span></span>|
|<span data-ttu-id="7376b-123">ChannelMessage.Read.Group</span><span class="sxs-lookup"><span data-stu-id="7376b-123">ChannelMessage.Read.Group</span></span> |<span data-ttu-id="7376b-124">Pegue as mensagens do canal desta equipe.</span><span class="sxs-lookup"><span data-stu-id="7376b-124">Get this team's channel messages.</span></span>|
|<span data-ttu-id="7376b-125">TeamsAppInstallation.Read.Group</span><span class="sxs-lookup"><span data-stu-id="7376b-125">TeamsAppInstallation.Read.Group</span></span>|<span data-ttu-id="7376b-126">Obtenha uma lista dos aplicativos instalados desta equipe.</span><span class="sxs-lookup"><span data-stu-id="7376b-126">Get a list of this team's installed apps.</span></span>|
|<span data-ttu-id="7376b-127">TeamsTab.Read.Group</span><span class="sxs-lookup"><span data-stu-id="7376b-127">TeamsTab.Read.Group</span></span>|<span data-ttu-id="7376b-128">Pegue uma lista das guias deste time.</span><span class="sxs-lookup"><span data-stu-id="7376b-128">Get a list of this team's tabs.</span></span>|
|<span data-ttu-id="7376b-129">TeamsTab.Create.Group</span><span class="sxs-lookup"><span data-stu-id="7376b-129">TeamsTab.Create.Group</span></span>|<span data-ttu-id="7376b-130">Criar guias nesta equipe.</span><span class="sxs-lookup"><span data-stu-id="7376b-130">Create tabs in this team.</span></span>|
|<span data-ttu-id="7376b-131">TeamsTab.ReadWrite.Group</span><span class="sxs-lookup"><span data-stu-id="7376b-131">TeamsTab.ReadWrite.Group</span></span>|<span data-ttu-id="7376b-132">Atualize as guias desta equipe.</span><span class="sxs-lookup"><span data-stu-id="7376b-132">Update this team's tabs.</span></span>|
|<span data-ttu-id="7376b-133">TeamsTab.Delete.Group</span><span class="sxs-lookup"><span data-stu-id="7376b-133">TeamsTab.Delete.Group</span></span>|<span data-ttu-id="7376b-134">Excluir as guias dessa equipe.</span><span class="sxs-lookup"><span data-stu-id="7376b-134">Delete this team's tabs.</span></span>|
|<span data-ttu-id="7376b-135">TeamMember.Read.Group</span><span class="sxs-lookup"><span data-stu-id="7376b-135">TeamMember.Read.Group</span></span>|<span data-ttu-id="7376b-136">Pegue os membros da equipe.</span><span class="sxs-lookup"><span data-stu-id="7376b-136">Get this team's members.</span></span>|

>[!NOTE]
><span data-ttu-id="7376b-137">Permissões específicas de recursos só estão disponíveis para Teams aplicativos instalados no Teams cliente e atualmente não fazem parte do portal Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="7376b-137">Resource-specific permissions are only available to Teams apps installed on the Teams client and are currently not part of the Azure Active Directory portal.</span></span>

## <a name="enable-resource-specific-consent-in-your-application"></a><span data-ttu-id="7376b-138">Habilite o consentimento específico de recursos em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="7376b-138">Enable resource-specific consent in your application</span></span>

<span data-ttu-id="7376b-139">As etapas para habilitar o RSC em seu aplicativo são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="7376b-139">The steps for enabling RSC in your application are as follows:</span></span>

1. <span data-ttu-id="7376b-140">[Configure as configurações de consentimento do proprietário do grupo no portal Azure Active Directory](#configure-group-owner-consent-settings-in-the-azure-ad-portal).</span><span class="sxs-lookup"><span data-stu-id="7376b-140">[Configure group owner consent settings in the Azure Active Directory portal](#configure-group-owner-consent-settings-in-the-azure-ad-portal).</span></span>
1. <span data-ttu-id="7376b-141">[Cadastre seu aplicativo com plataforma de identidade da Microsoft através do portal Azure AD](#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).</span><span class="sxs-lookup"><span data-stu-id="7376b-141">[Register your app with Microsoft identity platform via the Azure AD portal](#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).</span></span>
1. <span data-ttu-id="7376b-142">[Revise suas permissões de solicitação no portal Azure AD](#review-your-application-permissions-in-the-azure-ad-portal).</span><span class="sxs-lookup"><span data-stu-id="7376b-142">[Review your application permissions in the Azure AD portal](#review-your-application-permissions-in-the-azure-ad-portal).</span></span>
1. <span data-ttu-id="7376b-143">[Obtenha um token de acesso da plataforma Microsoft Identity](#obtain-an-access-token-from-the-microsoft-identity-platform).</span><span class="sxs-lookup"><span data-stu-id="7376b-143">[Obtain an access token from the Microsoft Identity platform](#obtain-an-access-token-from-the-microsoft-identity-platform).</span></span>
1. <span data-ttu-id="7376b-144">[Atualize seu manifesto de aplicativo Teams](#update-your-teams-app-manifest).</span><span class="sxs-lookup"><span data-stu-id="7376b-144">[Update your Teams app manifest](#update-your-teams-app-manifest).</span></span>
1. <span data-ttu-id="7376b-145">[Instale seu aplicativo diretamente em Teams](#sideload-your-app-in-teams).</span><span class="sxs-lookup"><span data-stu-id="7376b-145">[Install your app directly in Teams](#sideload-your-app-in-teams).</span></span>
1. <span data-ttu-id="7376b-146">[Verifique se o aplicativo tem permissões RSC adicionadas.](#check-your-app-for-added-rsc-permissions)</span><span class="sxs-lookup"><span data-stu-id="7376b-146">[Check your app for added RSC permissions](#check-your-app-for-added-rsc-permissions).</span></span>

## <a name="configure-group-owner-consent-settings-in-the-azure-ad-portal"></a><span data-ttu-id="7376b-147">Configure as configurações de consentimento do proprietário do grupo no portal Azure AD</span><span class="sxs-lookup"><span data-stu-id="7376b-147">Configure group owner consent settings in the Azure AD portal</span></span>

<span data-ttu-id="7376b-148">Você pode ativar ou desativar o [consentimento do proprietário do grupo](/azure/active-directory/manage-apps/configure-user-consent-groups?tabs=azure-portal) diretamente dentro do portal do Azure:</span><span class="sxs-lookup"><span data-stu-id="7376b-148">You can enable or disable [group owner consent](/azure/active-directory/manage-apps/configure-user-consent-groups?tabs=azure-portal) directly within the Azure portal:</span></span>

> [!div class="checklist"]
>
>- <span data-ttu-id="7376b-149">Faça login no [portal Azure](https://portal.azure.com) como [administrador global/administrador da empresa.](/azure/active-directory/users-groups-roles/directory-assign-admin-roles.md#global-administrator--company-administrator)</span><span class="sxs-lookup"><span data-stu-id="7376b-149">Sign in to the [Azure portal](https://portal.azure.com) as a [Global Administrator/Company Administrator](/azure/active-directory/users-groups-roles/directory-assign-admin-roles.md#global-administrator--company-administrator).</span></span>  
 > - <span data-ttu-id="7376b-150">[Selecione](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConsentPoliciesMenuBlade/UserSettings) **Azure Active Directory**  =>  **Enterprise aplicativos**  =>  **Consentir e permissões**  =>  **Configurações de consentimento do usuário**.</span><span class="sxs-lookup"><span data-stu-id="7376b-150">[Select](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConsentPoliciesMenuBlade/UserSettings) **Azure Active Directory** => **Enterprise applications** => **Consent and permissions** => **User consent settings**.</span></span>
> - <span data-ttu-id="7376b-151">Habilite, desabilitar ou limite o consentimento do usuário com o consentimento do proprietário do grupo de controle rotulado **para aplicativos que acessam dados** (O padrão é permitir o consentimento do proprietário do grupo para todos os **proprietários do grupo**).</span><span class="sxs-lookup"><span data-stu-id="7376b-151">Enable, disable, or limit user consent with the control labeled **Group owner consent for apps accessing data** (The default is **Allow group owner consent for all group owners**).</span></span> <span data-ttu-id="7376b-152">Para que um proprietário de equipe instale um aplicativo usando O RSC, o consentimento do proprietário do grupo deve ser ativado para esse usuário.</span><span class="sxs-lookup"><span data-stu-id="7376b-152">For a team owner to install an app using RSC, group owner consent must be enabled for that user.</span></span>

![configuração azure rsc](../../assets/images/azure-rsc-configuration.png)

<span data-ttu-id="7376b-154">Para ativar ou desativar o consentimento do proprietário do grupo usando o PowerShell, siga as etapas descritas no [consentimento do proprietário do grupo Configurar usando o PowerShell](/azure/active-directory/manage-apps/configure-user-consent-groups?tabs=azure-powershell).</span><span class="sxs-lookup"><span data-stu-id="7376b-154">To enable or disable group owner consent using PowerShell, follow the steps outlined in [Configure group owner consent using PowerShell](/azure/active-directory/manage-apps/configure-user-consent-groups?tabs=azure-powershell).</span></span>

## <a name="register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal"></a><span data-ttu-id="7376b-155">Cadastre seu aplicativo com plataforma de identidade da Microsoft através do portal Azure AD</span><span class="sxs-lookup"><span data-stu-id="7376b-155">Register your app with Microsoft identity platform via the Azure AD portal</span></span>

<span data-ttu-id="7376b-156">O portal Azure Active Directory fornece uma plataforma central para você se cadastrar e configurar seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="7376b-156">The Azure Active Directory portal provides a central platform for you to register and configure your apps.</span></span> <span data-ttu-id="7376b-157">Seu aplicativo deve ser cadastrado no portal Azure AD para se integrar com o plataforma de identidade da Microsoft e ligar para a Microsoft Graph APIs.</span><span class="sxs-lookup"><span data-stu-id="7376b-157">Your app must be registered in the Azure AD portal to integrate with the Microsoft identity platform and call Microsoft Graph APIs.</span></span> <span data-ttu-id="7376b-158">Para obter mais informações, consulte [Registrar um aplicativo no plataforma de identidade da Microsoft](/graph/auth-register-app-v2).</span><span class="sxs-lookup"><span data-stu-id="7376b-158">For more information, see [Register an application with the Microsoft identity platform](/graph/auth-register-app-v2).</span></span>

>[!WARNING]
><span data-ttu-id="7376b-159">Não registre vários aplicativos Teams no mesmo id do aplicativo Azure AD. O id do aplicativo deve ser exclusivo para cada aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7376b-159">Do not register multiple Teams apps to the same Azure AD app id. The app id must be unique for each app.</span></span> <span data-ttu-id="7376b-160">As tentativas de instalar vários aplicativos para o mesmo id do aplicativo falharão.</span><span class="sxs-lookup"><span data-stu-id="7376b-160">Attempts to install multiple apps to the same app id will fail.</span></span>

## <a name="review-your-application-permissions-in-the-azure-ad-portal"></a><span data-ttu-id="7376b-161">Revise suas permissões de aplicativo no portal Azure AD</span><span class="sxs-lookup"><span data-stu-id="7376b-161">Review your application permissions in the Azure AD portal</span></span>

<span data-ttu-id="7376b-162">Navegue até a página de registros do **Aplicativo Inicial** e selecione seu aplicativo  =>   RSC.</span><span class="sxs-lookup"><span data-stu-id="7376b-162">Navigate to the **Home** => **App registrations** page and select your RSC app.</span></span> <span data-ttu-id="7376b-163">Escolha permissões de **API** na barra de navegação esquerda e examine a lista de permissões configuradas para o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7376b-163">Choose **API permissions** from the left nav bar and examine the list of configured permissions for your app.</span></span> <span data-ttu-id="7376b-164">Se o seu aplicativo fizer apenas chamadas de API Graph RSC, exclua toda a permissão nessa página.</span><span class="sxs-lookup"><span data-stu-id="7376b-164">If your app will only make RSC Graph API calls, delete all the permission on that page.</span></span> <span data-ttu-id="7376b-165">Se o seu aplicativo também fizer chamadas não-RSC, mantenha essas permissões conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="7376b-165">If your app will also make non-RSC calls, keep those permissions as needed.</span></span>

>[!IMPORTANT]
><span data-ttu-id="7376b-166">O portal Azure AD não pode ser usado para solicitar permissões RSC.</span><span class="sxs-lookup"><span data-stu-id="7376b-166">The Azure AD portal cannot be used to request RSC permissions.</span></span> <span data-ttu-id="7376b-167">As permissões RSC são atualmente exclusivas para Teams aplicativos instalados no Teams cliente e são declaradas no arquivo manifesto do aplicativo (JSON).</span><span class="sxs-lookup"><span data-stu-id="7376b-167">RSC permissions are currently exclusive to Teams applications installed in the Teams client and are declared in the app manifest (JSON) file.</span></span>

## <a name="obtain-an-access-token-from-the-microsoft-identity-platform"></a><span data-ttu-id="7376b-168">Obtenha um token de acesso do plataforma de identidade da Microsoft</span><span class="sxs-lookup"><span data-stu-id="7376b-168">Obtain an access token from the Microsoft identity platform</span></span>

<span data-ttu-id="7376b-169">Para fazer Graph chamadas de API, você deve obter um token de acesso para o seu aplicativo a partir da plataforma de identidade.</span><span class="sxs-lookup"><span data-stu-id="7376b-169">To make Graph API calls, you must obtain an access token for your app from the identity platform.</span></span> <span data-ttu-id="7376b-170">Antes que seu aplicativo possa obter um token do plataforma de identidade da Microsoft, ele deve ser registrado no portal Azure AD.</span><span class="sxs-lookup"><span data-stu-id="7376b-170">Before your app can get a token from the Microsoft identity platform, it must be registered in the Azure AD portal.</span></span> <span data-ttu-id="7376b-171">O token de acesso contém informações sobre seu aplicativo e as permissões que ele possui para os recursos e APIs disponíveis no Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="7376b-171">The access token contains information about your app and the permissions it has for the resources and APIs available through Microsoft Graph.</span></span>

<span data-ttu-id="7376b-172">Você precisará ter os seguintes valores do processo de registro do Azure AD para recuperar um token de acesso da plataforma de identidade:</span><span class="sxs-lookup"><span data-stu-id="7376b-172">You'll need to have the following values from the Azure AD registration process to retrieve an access token from the identity platform:</span></span>

- <span data-ttu-id="7376b-173">O **ID do aplicativo** atribuído pelo portal de registro do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7376b-173">The **Application ID** assigned by the app registration portal.</span></span> <span data-ttu-id="7376b-174">Se o aplicativo suportar um único login (SSO) você deve usar o mesmo ID do aplicativo para o seu aplicativo e SSO.</span><span class="sxs-lookup"><span data-stu-id="7376b-174">If your app supports single sign-on (SSO) you should use the same Application ID for your app and SSO.</span></span>
- <span data-ttu-id="7376b-175">O **cliente secreto/senha** ou um par de chaves públicas/privadas **(Certificado).**</span><span class="sxs-lookup"><span data-stu-id="7376b-175">The  **Client secret/password** or a public/private key pair (**Certificate**).</span></span> <span data-ttu-id="7376b-176">Isso não é necessário para aplicativos nativos.</span><span class="sxs-lookup"><span data-stu-id="7376b-176">This is not required for native apps.</span></span>
- <span data-ttu-id="7376b-177">Um **URI redirecionar** (ou responder URL) para que seu aplicativo receba respostas do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="7376b-177">A **Redirect URI** (or reply URL) for your app to receive responses from Azure AD.</span></span>

 <span data-ttu-id="7376b-178">*Ver* [Obter acesso em nome de um usuário](/graph/auth-v2-user?view=graph-rest-1.0#3-get-a-token&preserve-view=true) e obter acesso sem um [usuário](/graph/auth-v2-service)</span><span class="sxs-lookup"><span data-stu-id="7376b-178">*See* [Get access on behalf of a user](/graph/auth-v2-user?view=graph-rest-1.0#3-get-a-token&preserve-view=true) and [Get access without a user](/graph/auth-v2-service)</span></span>

## <a name="update-your-teams-app-manifest"></a><span data-ttu-id="7376b-179">Atualize seu manifesto de aplicativo de Teams</span><span class="sxs-lookup"><span data-stu-id="7376b-179">Update your Teams app manifest</span></span>

<span data-ttu-id="7376b-180">As permissões RSC são declaradas no arquivo manifesto do aplicativo (JSON).</span><span class="sxs-lookup"><span data-stu-id="7376b-180">The RSC permissions are declared in your app manifest (JSON) file.</span></span>  <span data-ttu-id="7376b-181">Adicione uma tecla [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) ao seu manifesto de aplicativo com os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="7376b-181">Add a [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) key to your app manifest with the following values:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="7376b-182">**id**  — seu id de aplicativo Azure AD. Para obter mais informações, consulte [Cadastrar seu aplicativo no portal Azure AD](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).</span><span class="sxs-lookup"><span data-stu-id="7376b-182">**id**  — your Azure AD app id. For more information, see [Register your app in the Azure AD portal](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).</span></span>
> - <span data-ttu-id="7376b-183">**recurso**  - qualquer string.</span><span class="sxs-lookup"><span data-stu-id="7376b-183">**resource**  — any string.</span></span> <span data-ttu-id="7376b-184">Este campo não tem operação no RSC, mas deve ser adicionado e ter um valor para evitar uma resposta de erro; qualquer corda vai fazer.</span><span class="sxs-lookup"><span data-stu-id="7376b-184">This field has no operation in RSC, but must be added and have a value to avoid an error response; any string will do.</span></span>
> - <span data-ttu-id="7376b-185">**permissões de aplicativos** — Permissões RSC para o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7376b-185">**application permissions** — RSC permissions for  your app.</span></span> <span data-ttu-id="7376b-186">Para obter mais informações, consulte [Permissões específicas de recursos](resource-specific-consent.md#resource-specific-permissions).</span><span class="sxs-lookup"><span data-stu-id="7376b-186">For more information, see [Resource-specific Permissions](resource-specific-consent.md#resource-specific-permissions).</span></span>

>
>[!IMPORTANT]
> <span data-ttu-id="7376b-187">As permissões não-RSC são armazenadas no portal Azure.</span><span class="sxs-lookup"><span data-stu-id="7376b-187">Non-RSC permissions are stored in the Azure portal.</span></span> <span data-ttu-id="7376b-188">Não adicione ao manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7376b-188">Do not add them to the app manifest.</span></span>
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

## <a name="sideload-your-app-in-teams"></a><span data-ttu-id="7376b-189">Carregar lateralmente seu aplicativo em Teams</span><span class="sxs-lookup"><span data-stu-id="7376b-189">Sideload your app in Teams</span></span>

<span data-ttu-id="7376b-190">Se o administrador de Teams permitir uploads personalizados de aplicativos, você pode [carregar seu aplicativo](~/concepts/deploy-and-publish/apps-upload.md) diretamente para uma equipe específica.</span><span class="sxs-lookup"><span data-stu-id="7376b-190">If your Teams admin allows custom app uploads, you can [sideload your app](~/concepts/deploy-and-publish/apps-upload.md) directly to a specific team.</span></span>

## <a name="check-your-app-for-added-rsc-permissions"></a><span data-ttu-id="7376b-191">Verifique se o seu aplicativo tem permissões RSC adicionadas</span><span class="sxs-lookup"><span data-stu-id="7376b-191">Check your app for added RSC permissions</span></span>

>[!IMPORTANT]
><span data-ttu-id="7376b-192">As permissões RSC não são atribuídas a um usuário.</span><span class="sxs-lookup"><span data-stu-id="7376b-192">The RSC permissions are not attributed to a user.</span></span> <span data-ttu-id="7376b-193">As chamadas são feitas com permissões de aplicativos, não com permissões delegadas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="7376b-193">Calls are made with app permissions, not user delegated permissions.</span></span> <span data-ttu-id="7376b-194">Assim, o aplicativo pode ser autorizado a executar ações que o usuário não pode, como criar um canal ou excluir uma guia. Você deve revisar a intenção do proprietário da equipe para o seu caso de uso antes de fazer chamadas de API RSC.</span><span class="sxs-lookup"><span data-stu-id="7376b-194">Thus, the app may be allowed to perform actions that the user cannot, such as creating a channel or deleting a tab. You should review the team owner's intent for your use case prior to making RSC API calls.</span></span> <span data-ttu-id="7376b-195">Para obter mais informações, consulte [Microsoft Teams visão geral da API](/graph/teams-concept-overview).</span><span class="sxs-lookup"><span data-stu-id="7376b-195">For more information, see [Microsoft Teams API overview](/graph/teams-concept-overview).</span></span>

<span data-ttu-id="7376b-196">Uma vez que o aplicativo tenha sido instalado em uma equipe, você pode usar [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer) para visualizar as permissões que foram concedidas ao aplicativo em uma equipe:</span><span class="sxs-lookup"><span data-stu-id="7376b-196">Once the app has been installed to a team, you can use [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer)  to view the permissions that have been granted to the app in a team:</span></span>

> [!div class="checklist"]
>
>- <span data-ttu-id="7376b-197">Pegue o **groupId** da equipe do cliente Teams.</span><span class="sxs-lookup"><span data-stu-id="7376b-197">Get the team's **groupId** from the Teams client.</span></span>
> - <span data-ttu-id="7376b-198">No Teams cliente, selecione **Teams** da barra de navegação de extrema esquerda.</span><span class="sxs-lookup"><span data-stu-id="7376b-198">In the Teams client, select **Teams** from the far left nav bar.</span></span>
> - <span data-ttu-id="7376b-199">Selecione a equipe onde o aplicativo está instalado no menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="7376b-199">Select the team where the app is installed from the drop-down menu.</span></span>
> - <span data-ttu-id="7376b-200">Selecione o ícone **Mais opções** (&#8943;).</span><span class="sxs-lookup"><span data-stu-id="7376b-200">Select the **More options** icon (&#8943;).</span></span>
> - <span data-ttu-id="7376b-201">Selecione **Obter link para equipe**.</span><span class="sxs-lookup"><span data-stu-id="7376b-201">Select **Get link to team**.</span></span>
> - <span data-ttu-id="7376b-202">Copie e salve o valor **do groupId** da string.</span><span class="sxs-lookup"><span data-stu-id="7376b-202">Copy and save the **groupId** value from the string.</span></span>
> - <span data-ttu-id="7376b-203">Faça login **no Graph Explorer**.</span><span class="sxs-lookup"><span data-stu-id="7376b-203">Log into **Graph Explorer**.</span></span>
> - <span data-ttu-id="7376b-204">Faça uma chamada **GET** para o seguinte ponto final: `https://graph.microsoft.com/beta/groups/{teamGroupId}/permissionGrants` .</span><span class="sxs-lookup"><span data-stu-id="7376b-204">Make a **GET** call to the following endpoint: `https://graph.microsoft.com/beta/groups/{teamGroupId}/permissionGrants`.</span></span> <span data-ttu-id="7376b-205">O campo clienteAppId na resposta irá mapear o appId especificado no manifesto do aplicativo Teams.</span><span class="sxs-lookup"><span data-stu-id="7376b-205">The clientAppId field in the response will map to the appId specified in the Teams app manifest.</span></span>
  <span data-ttu-id="7376b-206">![Graph resposta do explorador para receber chamada.](../../assets/images/graph-permissions.png)</span><span class="sxs-lookup"><span data-stu-id="7376b-206">![Graph explorer response to GET call.](../../assets/images/graph-permissions.png)</span></span>

## <a name="code-sample"></a><span data-ttu-id="7376b-207">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="7376b-207">Code sample</span></span>
| <span data-ttu-id="7376b-208">**Nome da amostra**</span><span class="sxs-lookup"><span data-stu-id="7376b-208">**Sample name**</span></span> | <span data-ttu-id="7376b-209">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="7376b-209">**Description**</span></span> | <span data-ttu-id="7376b-210">**.NET**</span><span class="sxs-lookup"><span data-stu-id="7376b-210">**.NET**</span></span> |<span data-ttu-id="7376b-211">**Node.js**</span><span class="sxs-lookup"><span data-stu-id="7376b-211">**Node.js**</span></span> |
|-----------------|-----------------|----------------|----------------|
| <span data-ttu-id="7376b-212">Consentimento específico do recurso (RSC)</span><span class="sxs-lookup"><span data-stu-id="7376b-212">Resource Specific Consent (RSC)</span></span> | <span data-ttu-id="7376b-213">Use o RSC para chamar Graph APIs.</span><span class="sxs-lookup"><span data-stu-id="7376b-213">Use RSC to call Graph APIs.</span></span> | [<span data-ttu-id="7376b-214">View</span><span class="sxs-lookup"><span data-stu-id="7376b-214">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-rsc/csharp)|[<span data-ttu-id="7376b-215">View</span><span class="sxs-lookup"><span data-stu-id="7376b-215">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-rsc/nodeJs)|



## <a name="see-also"></a><span data-ttu-id="7376b-216">Confira também</span><span class="sxs-lookup"><span data-stu-id="7376b-216">See also</span></span>
 
* [<span data-ttu-id="7376b-217">Teste permissões de consentimento específicas para recursos em Teams</span><span class="sxs-lookup"><span data-stu-id="7376b-217">Test resource-specific consent permissions in Teams</span></span>](test-resource-specific-consent.md)
* [<span data-ttu-id="7376b-218">Consentimento específico de recursos em Microsoft Teams para administradores</span><span class="sxs-lookup"><span data-stu-id="7376b-218">Resource-specific consent in Microsoft Teams for admins</span></span>](/MicrosoftTeams/resource-specific-consent)


