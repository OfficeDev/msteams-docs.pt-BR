---
title: Consentimento específico do recurso no Teams
description: Descreve o consentimento específico do recurso no Microsoft Teams e como aproveitar isso.
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: Overview
keywords: Gráfico de autorização do AAD SSO do Microsoft Teams
ms.openlocfilehash: bf449b338e8c0f42dfef776e533fb6b5ff591529
ms.sourcegitcommit: 1b909fb9ccf6cdd84ed0d8f9ea0463243a802a23
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "45434500"
---
# <a name="resource-specific-consent-rsc--developer-preview"></a><span data-ttu-id="b82f6-104">Consentimento específico de recurso (RSC) — visualização do desenvolvedor</span><span class="sxs-lookup"><span data-stu-id="b82f6-104">Resource-specific consent (RSC) — Developer Preview</span></span>

>[!NOTE]

><span data-ttu-id="b82f6-105">As permissões de consentimento específicas do recurso estão disponíveis nos clientes da área de trabalho e da Web após a visualização do desenvolvedor ter sido habilitada.</span><span class="sxs-lookup"><span data-stu-id="b82f6-105">The resource-specific consent permissions are available in desktop and web clients after Developer Preview has been enabled.</span></span> <span data-ttu-id="b82f6-106">Veja [como habilitar a visualização do desenvolvedor](../../resources/dev-preview/developer-preview-intro.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="b82f6-106">See [How do I enable Developer Preview](../../resources/dev-preview/developer-preview-intro.md) for more information.</span></span>

<span data-ttu-id="b82f6-107">O consentimento específico de recurso (RSC) é uma integração da API do Microsoft Teams e do Graph que permite que seu aplicativo use pontos de extremidade da API para gerenciar equipes específicas dentro de uma organização.</span><span class="sxs-lookup"><span data-stu-id="b82f6-107">Resource-specific consent (RSC) is a Microsoft Teams and Graph API integration that enables your app to use API endpoints to manage specific teams within an organization.</span></span> <span data-ttu-id="b82f6-108">O modelo de permissões de consentimento específico de recurso (RSC) permite que os *proprietários de equipe* concedam a permissão para um aplicativo acessar e/ou modificar os dados de uma equipe.</span><span class="sxs-lookup"><span data-stu-id="b82f6-108">The resource-specific consent (RSC) permissions model enables *team owners* to grant consent for an application to access and/or modify a team's data.</span></span> <span data-ttu-id="b82f6-109">As permissões do tipo granular, específicas de equipes, de RSC definem o que um aplicativo pode fazer dentro de uma equipe específica:</span><span class="sxs-lookup"><span data-stu-id="b82f6-109">The granular, Teams-specific, RSC permissions define what an application can do within a specific team:</span></span>

## <a name="resource-specific-permissions"></a><span data-ttu-id="b82f6-110">Permissões específicas do recurso</span><span class="sxs-lookup"><span data-stu-id="b82f6-110">Resource-specific permissions</span></span>

|<span data-ttu-id="b82f6-111">Permissão de aplicativo</span><span class="sxs-lookup"><span data-stu-id="b82f6-111">Application permission</span></span>| <span data-ttu-id="b82f6-112">Action</span><span class="sxs-lookup"><span data-stu-id="b82f6-112">Action</span></span> |
| ----- | ----- |
|<span data-ttu-id="b82f6-113">TeamSettings.Read.Group</span><span class="sxs-lookup"><span data-stu-id="b82f6-113">TeamSettings.Read.Group</span></span> | <span data-ttu-id="b82f6-114">Obter as configurações da equipe.</span><span class="sxs-lookup"><span data-stu-id="b82f6-114">Get the settings for this team.</span></span>|
|<span data-ttu-id="b82f6-115">TeamSettings. Edit. Group</span><span class="sxs-lookup"><span data-stu-id="b82f6-115">TeamSettings.Edit.Group</span></span>|<span data-ttu-id="b82f6-116">Atualize as configurações da equipe.</span><span class="sxs-lookup"><span data-stu-id="b82f6-116">Update the settings for this team.</span></span>|
|<span data-ttu-id="b82f6-117">ChannelSettings.Read.Group</span><span class="sxs-lookup"><span data-stu-id="b82f6-117">ChannelSettings.Read.Group</span></span>|<span data-ttu-id="b82f6-118">Obtenha os nomes de canal, as descrições de canal e as configurações de canal para esta equipe.</span><span class="sxs-lookup"><span data-stu-id="b82f6-118">Get the channel names, channel descriptions, and channel settings for this team.</span></span>|
|<span data-ttu-id="b82f6-119">ChannelSettings.Edit.Group</span><span class="sxs-lookup"><span data-stu-id="b82f6-119">ChannelSettings.Edit.Group</span></span>|<span data-ttu-id="b82f6-120">Atualize os nomes de canal, as descrições de canal e as configurações de canal para essa equipe.</span><span class="sxs-lookup"><span data-stu-id="b82f6-120">Update the channel names, channel descriptions, and channel settings for this team.</span></span>|
|<span data-ttu-id="b82f6-121">Channel.Create.Group</span><span class="sxs-lookup"><span data-stu-id="b82f6-121">Channel.Create.Group</span></span>|<span data-ttu-id="b82f6-122">Criar canais nesta equipe.</span><span class="sxs-lookup"><span data-stu-id="b82f6-122">Create channels in this team.</span></span>|
|<span data-ttu-id="b82f6-123">Channel.Delete.Group</span><span class="sxs-lookup"><span data-stu-id="b82f6-123">Channel.Delete.Group</span></span>|<span data-ttu-id="b82f6-124">Excluir canais nesta equipe.</span><span class="sxs-lookup"><span data-stu-id="b82f6-124">Delete channels in this team.</span></span>|
|<span data-ttu-id="b82f6-125">ChannelMessage.Read.Group</span><span class="sxs-lookup"><span data-stu-id="b82f6-125">ChannelMessage.Read.Group</span></span> |<span data-ttu-id="b82f6-126">Obtenha as mensagens do canal da equipe.</span><span class="sxs-lookup"><span data-stu-id="b82f6-126">Get this team's channel messages.</span></span>|
|<span data-ttu-id="b82f6-127">TeamsApp.Read.Group</span><span class="sxs-lookup"><span data-stu-id="b82f6-127">TeamsApp.Read.Group</span></span>|<span data-ttu-id="b82f6-128">Obtenha uma lista dos aplicativos instalados pela equipe.</span><span class="sxs-lookup"><span data-stu-id="b82f6-128">Get a list of this team's installed apps.</span></span>|
|<span data-ttu-id="b82f6-129">TeamsTab.Read.Group</span><span class="sxs-lookup"><span data-stu-id="b82f6-129">TeamsTab.Read.Group</span></span>|<span data-ttu-id="b82f6-130">Obtenha uma lista das guias da equipe.</span><span class="sxs-lookup"><span data-stu-id="b82f6-130">Get a list of this team's tabs.</span></span>|
|<span data-ttu-id="b82f6-131">TeamsTab.Create.Group</span><span class="sxs-lookup"><span data-stu-id="b82f6-131">TeamsTab.Create.Group</span></span>|<span data-ttu-id="b82f6-132">Criar guias nesta equipe.</span><span class="sxs-lookup"><span data-stu-id="b82f6-132">Create tabs in this team.</span></span>|
|<span data-ttu-id="b82f6-133">TeamsTab.Edit.Group</span><span class="sxs-lookup"><span data-stu-id="b82f6-133">TeamsTab.Edit.Group</span></span>|<span data-ttu-id="b82f6-134">Atualize as guias da equipe.</span><span class="sxs-lookup"><span data-stu-id="b82f6-134">Update this team's tabs.</span></span>|
|<span data-ttu-id="b82f6-135">TeamsTab.Delete.Group</span><span class="sxs-lookup"><span data-stu-id="b82f6-135">TeamsTab.Delete.Group</span></span>|<span data-ttu-id="b82f6-136">Excluir as guias dessa equipe.</span><span class="sxs-lookup"><span data-stu-id="b82f6-136">Delete this team's tabs.</span></span>|
|<span data-ttu-id="b82f6-137">Member.Read.Group</span><span class="sxs-lookup"><span data-stu-id="b82f6-137">Member.Read.Group</span></span>|<span data-ttu-id="b82f6-138">Obter membros da equipe.</span><span class="sxs-lookup"><span data-stu-id="b82f6-138">Get this team's members.</span></span>|
|<span data-ttu-id="b82f6-139">Owner.Read.Group</span><span class="sxs-lookup"><span data-stu-id="b82f6-139">Owner.Read.Group</span></span>|<span data-ttu-id="b82f6-140">Obter os proprietários da equipe.</span><span class="sxs-lookup"><span data-stu-id="b82f6-140">Get this team's owners.</span></span>|

>[!NOTE]
><span data-ttu-id="b82f6-141">As permissões específicas do recurso estão disponíveis apenas para aplicativos do teams instalados no cliente do Teams e atualmente não fazem parte do portal do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="b82f6-141">Resource-specific permissions are only available to Teams apps installed on the Teams client and are currently not part of the Azure Active Directory portal.</span></span>

## <a name="enable-resource-specific-consent-in-your-application"></a><span data-ttu-id="b82f6-142">Habilitar o consentimento específico do recurso em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="b82f6-142">Enable resource-specific consent in your application</span></span>

<span data-ttu-id="b82f6-143">As etapas para habilitar o RSC no aplicativo são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="b82f6-143">The steps for enabling RSC in your application are as follows:</span></span>

1. <span data-ttu-id="b82f6-144">[Defina as configurações de consentimento do proprietário do grupo no portal do Azure Active Directory](#configure-group-owner-consent-settings-in-the-azure-ad-portal).</span><span class="sxs-lookup"><span data-stu-id="b82f6-144">[Configure group owner consent settings in the Azure Active Directory portal](#configure-group-owner-consent-settings-in-the-azure-ad-portal).</span></span>
1. <span data-ttu-id="b82f6-145">[Registre seu aplicativo com a plataforma de identidade da Microsoft por meio do portal do Azure ad](#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).</span><span class="sxs-lookup"><span data-stu-id="b82f6-145">[Register your app with Microsoft identity platform via the Azure AD portal](#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).</span></span>
1. [<span data-ttu-id="b82f6-146">Revisar as permissões do aplicativo no portal do Azure AD</span><span class="sxs-lookup"><span data-stu-id="b82f6-146">Review your application permissions in the Azure AD portal</span></span>](#review-your-application-permissions-in-the-azure-ad-portal)
1. <span data-ttu-id="b82f6-147">[Obter um token de acesso da plataforma de identidade da Microsoft](#obtain-an-access-token-from-the-microsoft-identity-platform).</span><span class="sxs-lookup"><span data-stu-id="b82f6-147">[Obtain an access token from the Microsoft Identity platform](#obtain-an-access-token-from-the-microsoft-identity-platform).</span></span>
1. <span data-ttu-id="b82f6-148">[Atualize o manifesto do aplicativo do Microsoft Teams](#update-your-teams-app-manifest).</span><span class="sxs-lookup"><span data-stu-id="b82f6-148">[Update your Teams app manifest](#update-your-teams-app-manifest).</span></span>
1. <span data-ttu-id="b82f6-149">[Instale seu aplicativo diretamente no Teams](#install-your-app-directly-in-teams).</span><span class="sxs-lookup"><span data-stu-id="b82f6-149">[Install your app directly in Teams](#install-your-app-directly-in-teams).</span></span>
1. <span data-ttu-id="b82f6-150">[Verifique seu aplicativo para obter permissões de RSC adicionadas](#check-your-app-for-added-rsc-permissions).</span><span class="sxs-lookup"><span data-stu-id="b82f6-150">[Check your app for added RSC permissions](#check-your-app-for-added-rsc-permissions).</span></span>

## <a name="configure-group-owner-consent-settings-in-the-azure-ad-portal"></a><span data-ttu-id="b82f6-151">Definir configurações de consentimento do proprietário do grupo no portal do Azure AD</span><span class="sxs-lookup"><span data-stu-id="b82f6-151">Configure group owner consent settings in the Azure AD portal</span></span>

<span data-ttu-id="b82f6-152">Você pode habilitar ou desabilitar o [consentimento do proprietário do grupo](/azure/active-directory/manage-apps/configure-user-consent#configure-group-owner-consent-to-apps-accessing-group-data) diretamente no portal do Azure:</span><span class="sxs-lookup"><span data-stu-id="b82f6-152">You can enable or disable  [group owner consent](/azure/active-directory/manage-apps/configure-user-consent#configure-group-owner-consent-to-apps-accessing-group-data) directly within the Azure portal:</span></span>

> [!div class="checklist"]
>
>- <span data-ttu-id="b82f6-153">Entre no [portal do Azure](https://portal.azure.com) como um administrador [global/administrador da empresa](/azure/active-directory/users-groups-roles/directory-assign-admin-roles.md#global-administrator--company-administrator).</span><span class="sxs-lookup"><span data-stu-id="b82f6-153">Sign in to the [Azure portal](https://portal.azure.com) as a [Global Administrator/Company Administrator](/azure/active-directory/users-groups-roles/directory-assign-admin-roles.md#global-administrator--company-administrator).</span></span>  
 > - <span data-ttu-id="b82f6-154">Selecione **Azure Active Directory**  => configurações de usuário dos**aplicativos corporativos**do Azure Active Directory  => **User settings**.</span><span class="sxs-lookup"><span data-stu-id="b82f6-154">Select **Azure Active Directory** =>**Enterprise applications** =>**User settings**.</span></span>
> - <span data-ttu-id="b82f6-155">Habilitar, desabilitar ou limitar o consentimento do usuário com o controle rotulado **os usuários podem consentir aos aplicativos que acessam os dados da empresa para os grupos que possuem** (esta funcionalidade é habilitada por padrão).</span><span class="sxs-lookup"><span data-stu-id="b82f6-155">Enable, disable, or limit user consent with the control labeled **Users can consent to apps accessing company data for the groups they own** (This capability is enabled by default).</span></span>

![configuração do Azure RSC](../../assets/images/azure-rsc-configuration.svg)

| <span data-ttu-id="b82f6-157">Valor</span><span class="sxs-lookup"><span data-stu-id="b82f6-157">Value</span></span> | <span data-ttu-id="b82f6-158">Descrição</span><span class="sxs-lookup"><span data-stu-id="b82f6-158">Description</span></span>|
|--- | --- |
|<span data-ttu-id="b82f6-159">Sim</span><span class="sxs-lookup"><span data-stu-id="b82f6-159">Yes</span></span> | <span data-ttu-id="b82f6-160">Habilitar o consentimento específico do grupo para todos os proprietários do grupo.</span><span class="sxs-lookup"><span data-stu-id="b82f6-160">Enable group-specific consent for all group owners.</span></span>|
|<span data-ttu-id="b82f6-161">Não</span><span class="sxs-lookup"><span data-stu-id="b82f6-161">No</span></span> |<span data-ttu-id="b82f6-162">Desabilite o consentimento específico do grupo para todos os usuários.</span><span class="sxs-lookup"><span data-stu-id="b82f6-162">Disable group-specific consent for all users.</span></span>| 
|<span data-ttu-id="b82f6-163">Limite</span><span class="sxs-lookup"><span data-stu-id="b82f6-163">Limited</span></span> | <span data-ttu-id="b82f6-164">Habilitar consentimento específico do grupo para membros de um grupo selecionado.</span><span class="sxs-lookup"><span data-stu-id="b82f6-164">Enable group-specific consent for members of a selected group.</span></span>|

<span data-ttu-id="b82f6-165">Para habilitar ou desabilitar o consentimento de proprietário de grupo no portal do Azure usando o PowerShell, siga as etapas descritas em [Configurar consentimento de proprietário de grupo usando o PowerShell](/azure/active-directory/manage-apps/configure-user-consent#configure-group-owner-consent-using-powershell).</span><span class="sxs-lookup"><span data-stu-id="b82f6-165">To enable or disable group owner consent within the Azure portal using PowerShell, follow the steps outlined in [Configure group owner consent using PowerShell](/azure/active-directory/manage-apps/configure-user-consent#configure-group-owner-consent-using-powershell).</span></span>

## <a name="register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal"></a><span data-ttu-id="b82f6-166">Registrar seu aplicativo com a plataforma de identidade da Microsoft via portal do Azure AD</span><span class="sxs-lookup"><span data-stu-id="b82f6-166">Register your app with Microsoft identity platform via the Azure AD portal</span></span>

<span data-ttu-id="b82f6-167">O portal do Azure Active Directory fornece uma plataforma central para que você registre e configure seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="b82f6-167">The Azure Active Directory portal provides a central platform for you to register and configure your apps.</span></span> <span data-ttu-id="b82f6-168">Seu aplicativo deve ser registrado no portal do Azure AD para integração com as APIs de plataforma de identidade da Microsoft e de gráfico de chamada.</span><span class="sxs-lookup"><span data-stu-id="b82f6-168">Your app must be registered in the Azure AD portal to integrate with the Microsoft identity platform and call Graph APIs.</span></span> <span data-ttu-id="b82f6-169">*Confira* [registrar um aplicativo com a plataforma de identidade da Microsoft](/graph/auth-register-app-v2).</span><span class="sxs-lookup"><span data-stu-id="b82f6-169">*See* [Register an application with the Microsoft identity platform](/graph/auth-register-app-v2).</span></span>

>[!WARNING]
><span data-ttu-id="b82f6-170">Não registre vários aplicativos do teams na mesma ID de aplicativo do Azure AD. A ID do aplicativo deve ser exclusiva para cada aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b82f6-170">Do not register multiple Teams apps to the same Azure AD app id. The app id must be unique for each app.</span></span> <span data-ttu-id="b82f6-171">As tentativas de instalar vários aplicativos para a mesma ID de aplicativos falharão.</span><span class="sxs-lookup"><span data-stu-id="b82f6-171">Attempts to install multiple apps to the same app id will fail.</span></span>

## <a name="review-your-application-permissions-in-the-azure-ad-portal"></a><span data-ttu-id="b82f6-172">Revisar as permissões do aplicativo no portal do Azure AD</span><span class="sxs-lookup"><span data-stu-id="b82f6-172">Review your application permissions in the Azure AD portal</span></span>

<span data-ttu-id="b82f6-173">Navegue até a página registros de aplicativos **residenciais**  =>  **App registrations** e selecione seu aplicativo RSC.</span><span class="sxs-lookup"><span data-stu-id="b82f6-173">Navigate to the **Home** => **App registrations** page and select your RSC app.</span></span> <span data-ttu-id="b82f6-174">Escolha **permissões de API** da barra de navegação à esquerda e examine a lista de permissões configuradas para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b82f6-174">Choose **API permissions** from the left nav bar and examine the list of configured permissions for your app.</span></span> <span data-ttu-id="b82f6-175">Se seu aplicativo fizer apenas chamadas de gráfico RSC, exclua todas as permissões nessa página.</span><span class="sxs-lookup"><span data-stu-id="b82f6-175">If your app will only make RSC Graph calls, delete all the permission on that page.</span></span> <span data-ttu-id="b82f6-176">Se seu aplicativo também fizer chamadas não-RSC, mantenha essas permissões conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="b82f6-176">If your app will also make non-RSC calls, keep those permissions as needed.</span></span>

>[!IMPORTANT]
><span data-ttu-id="b82f6-177">O portal do Azure AD não pode ser usado para solicitar permissões de RSC.</span><span class="sxs-lookup"><span data-stu-id="b82f6-177">The Azure AD portal cannot be used to request RSC permissions.</span></span> <span data-ttu-id="b82f6-178">Atualmente, as permissões de RSC são exclusivas para aplicativos do teams instalados no cliente do Teams e são declaradas no arquivo de manifesto de aplicativo (JSON).</span><span class="sxs-lookup"><span data-stu-id="b82f6-178">RSC permissions are currently exclusive to Teams applications installed in the Teams client and are declared in the app manifest (JSON) file.</span></span>

## <a name="obtain-an-access-token-from-the-microsoft-identity-platform"></a><span data-ttu-id="b82f6-179">Obter um token de acesso da plataforma de identidade da Microsoft</span><span class="sxs-lookup"><span data-stu-id="b82f6-179">Obtain an access token from the Microsoft identity platform</span></span>

<span data-ttu-id="b82f6-180">Para fazer chamadas à API do Graph, você deve obter um token de acesso para seu aplicativo a partir da plataforma de identidade.</span><span class="sxs-lookup"><span data-stu-id="b82f6-180">To make Graph API calls, you must obtain an access token for your app from the identity platform.</span></span> <span data-ttu-id="b82f6-181">Antes que o aplicativo possa obter um token da plataforma de identidade da Microsoft, ele deve ser registrado no portal do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="b82f6-181">Before your app can get a token from the Microsoft identity platform, it must be registered in the Azure AD portal.</span></span> <span data-ttu-id="b82f6-182">O token de acesso contém informações sobre seu aplicativo e as permissões que ele possui para os recursos e APIs disponíveis no Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="b82f6-182">The access token contains information about your app and the permissions it has for the resources and APIs available through Microsoft Graph.</span></span>

<span data-ttu-id="b82f6-183">Você precisará ter os seguintes valores do processo de registro do Azure AD para recuperar um token de acesso da plataforma de identidade:</span><span class="sxs-lookup"><span data-stu-id="b82f6-183">You'll need to have the following values from the Azure AD registration process to retrieve an access token from the identity platform:</span></span>

- <span data-ttu-id="b82f6-184">A **ID do aplicativo** atribuída pelo portal de registro do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b82f6-184">The **Application ID** assigned by the app registration portal.</span></span> <span data-ttu-id="b82f6-185">Se seu aplicativo oferecer suporte a logon único (SSO), você deverá usar a mesma ID de aplicativo para o seu aplicativo e SSO.</span><span class="sxs-lookup"><span data-stu-id="b82f6-185">If your app supports single sign-on (SSO) you should use the same Application ID for your app and SSO.</span></span>
- <span data-ttu-id="b82f6-186">O **segredo do cliente/senha** ou um par de chaves pública/privada (**certificado**).</span><span class="sxs-lookup"><span data-stu-id="b82f6-186">The  **Client secret/password** or a public/private key pair (**Certificate**).</span></span> <span data-ttu-id="b82f6-187">Isso não é necessário para aplicativos nativos.</span><span class="sxs-lookup"><span data-stu-id="b82f6-187">This is not required for native apps.</span></span>
- <span data-ttu-id="b82f6-188">Um **URI de redirecionamento** (ou URL de resposta) para seu aplicativo receber respostas do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="b82f6-188">A **Redirect URI** (or reply URL) for your app to receive responses from Azure AD.</span></span>

 <span data-ttu-id="b82f6-189">*Confira* [obter acesso em nome de um usuário](/graph/auth-v2-user?view=graph-rest-1.0#3-get-a-token) e [obter acesso sem um usuário](/graph/auth-v2-service)</span><span class="sxs-lookup"><span data-stu-id="b82f6-189">*See* [Get access on behalf of a user](/graph/auth-v2-user?view=graph-rest-1.0#3-get-a-token) and [Get access without a user](/graph/auth-v2-service)</span></span>

## <a name="update-your-teams-app-manifest"></a><span data-ttu-id="b82f6-190">Atualizar o manifesto do aplicativo do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="b82f6-190">Update your Teams app manifest</span></span>

<span data-ttu-id="b82f6-191">As permissões de RSC são declaradas no arquivo de manifesto de aplicativo (JSON).</span><span class="sxs-lookup"><span data-stu-id="b82f6-191">The RSC permissions are declared in you app manifest (JSON) file.</span></span>  <span data-ttu-id="b82f6-192">Adicione uma chave [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) ao manifesto do aplicativo com os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="b82f6-192">Add a [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) key to your app manifest with the following values:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="b82f6-193">**ID** — sua ID de aplicativo do Azure AD. *Confira* [registrar seu aplicativo no portal do Azure ad](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).</span><span class="sxs-lookup"><span data-stu-id="b82f6-193">**id**  — your Azure AD app id. *See* [Register your app in the Azure AD portal](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).</span></span>
> - <span data-ttu-id="b82f6-194">**recurso** — qualquer cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b82f6-194">**resource**  — any string.</span></span> <span data-ttu-id="b82f6-195">Este campo não tem nenhuma operação em RSC, mas deve ser adicionado e ter um valor para evitar uma resposta de erro; qualquer cadeia de caracteres fará.</span><span class="sxs-lookup"><span data-stu-id="b82f6-195">This field has no operation in RSC, but must be added and have a value to avoid an error response; any string will do.</span></span>
> - <span data-ttu-id="b82f6-196">**permissões de aplicativo** – permissões de RSC para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b82f6-196">**application permissions** — RSC permissions for  your app.</span></span> <span data-ttu-id="b82f6-197">*Consulte* [permissões específicas do recurso](resource-specific-consent.md#resource-specific-permissions).</span><span class="sxs-lookup"><span data-stu-id="b82f6-197">*See* [Resource-specific Permissions](resource-specific-consent.md#resource-specific-permissions).</span></span>

>
>[!IMPORTANT]
> <span data-ttu-id="b82f6-198">As permissões não RSC são armazenadas no portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="b82f6-198">Non-RSC permissions are stored in the Azure portal.</span></span> <span data-ttu-id="b82f6-199">Não os adicione ao manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b82f6-199">Do not add them to the app manifest.</span></span>
>

```json
"webApplicationInfo": {
    "id": "XXxxXXXXX-XxXX-xXXX-XXxx-XXXXXXXxxxXX",
    "resource": "https://RscBasedStoreApp",
    "applicationPermissions": [
      "TeamSettings.Read.Group",
      "ChannelMessage.Read.Group",
      "TeamSettings.Edit.Group",
      "ChannelSettings.Edit.Group",
      "Channel.Create.Group",
      "Channel.Delete.Group",
      "TeamsApp.Read.Group",
      "TeamsTab.Read.Group",
      "TeamsTab.Create.Group",
      "TeamsTab.Edit.Group",
      "TeamsTab.Delete.Group",
      "Member.Read.Group",
      "Owner.Read.Group"
    ]
  }
```

## <a name="install-your-app-directly-in-teams"></a><span data-ttu-id="b82f6-200">Instalar seu aplicativo diretamente no Teams</span><span class="sxs-lookup"><span data-stu-id="b82f6-200">Install your app directly in Teams</span></span>

<span data-ttu-id="b82f6-201">Depois de criar seu aplicativo, você pode [carregar seu pacote de aplicativos](../../concepts/deploy-and-publish/apps-upload.md#upload-your-package-into-a-team-using-the-apps-tab) diretamente para uma equipe específica.</span><span class="sxs-lookup"><span data-stu-id="b82f6-201">Once you've created your app you can [upload your app package](../../concepts/deploy-and-publish/apps-upload.md#upload-your-package-into-a-team-using-the-apps-tab) directly to a specific team.</span></span>  <span data-ttu-id="b82f6-202">Para fazer isso, a configuração de política **carregar aplicativos personalizados** deve ser habilitada como parte das políticas de configuração de aplicativos personalizados.</span><span class="sxs-lookup"><span data-stu-id="b82f6-202">To do so, the **Upload custom apps** policy setting must be enabled as part of the custom app setup policies.</span></span> <span data-ttu-id="b82f6-203">*Consulte* [configurações de política de aplicativos personalizadas](/microsoftteams/teams-custom-app-policies-and-settings#custom-app-policy-and-settings).</span><span class="sxs-lookup"><span data-stu-id="b82f6-203">*See* [Custom app policy settings](/microsoftteams/teams-custom-app-policies-and-settings#custom-app-policy-and-settings).</span></span>

## <a name="check-your-app-for-added-rsc-permissions"></a><span data-ttu-id="b82f6-204">Verifique seu aplicativo para permissões de RSC adicionadas</span><span class="sxs-lookup"><span data-stu-id="b82f6-204">Check your app for added RSC permissions</span></span>

>[!IMPORTANT]
><span data-ttu-id="b82f6-205">As permissões de RSC não são atribuídas a um usuário.</span><span class="sxs-lookup"><span data-stu-id="b82f6-205">The RSC permissions are not attributed to a user.</span></span> <span data-ttu-id="b82f6-206">As chamadas são feitas com permissões de aplicativo, não permissões delegadas de usuário.</span><span class="sxs-lookup"><span data-stu-id="b82f6-206">Calls are made with app permissions, not user delegated permissions.</span></span> <span data-ttu-id="b82f6-207">Portanto, o aplicativo pode ter permissão para executar ações que o usuário não pode, como criar um canal ou excluir uma guia. Você deve analisar a intenção do proprietário da equipe para seu caso de uso antes de realizar chamadas à API RSC.</span><span class="sxs-lookup"><span data-stu-id="b82f6-207">Thus, the app may be allowed to perform actions that the user cannot, such as creating a channel or deleting a tab. You should review the team owner's intent for your use case prior to making RSC API calls.</span></span> <span data-ttu-id="b82f6-208">*Confira* [visão geral da API do Microsoft Teams](/graph/teams-concept-overview).</span><span class="sxs-lookup"><span data-stu-id="b82f6-208">*See* [Microsoft Teams API overview](/graph/teams-concept-overview).</span></span>

<span data-ttu-id="b82f6-209">Depois que o aplicativo tiver sido instalado em uma equipe, você poderá usar o [Explorador do Graph](https://developer.microsoft.com/graph/graph-explorer) para exibir as permissões que foram concedidas ao aplicativo em uma equipe:</span><span class="sxs-lookup"><span data-stu-id="b82f6-209">Once the app has been installed to a team, you can use [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer)  to view the permissions that have been granted to the app in a team:</span></span>

> [!div class="checklist"]
>
>- <span data-ttu-id="b82f6-210">Obtenha o **GroupId** da equipe do cliente do teams.</span><span class="sxs-lookup"><span data-stu-id="b82f6-210">Get the team's **groupId** from the Teams client.</span></span>
> - <span data-ttu-id="b82f6-211">No cliente do Microsoft Teams, selecione **equipes** na barra de navegação da extrema esquerda.</span><span class="sxs-lookup"><span data-stu-id="b82f6-211">In the Teams client, select **Teams** from the far left nav bar.</span></span>
> - <span data-ttu-id="b82f6-212">Selecione a equipe onde o aplicativo está instalado no menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="b82f6-212">Select the team where the app is installed from the drop-down menu.</span></span>
> - <span data-ttu-id="b82f6-213">Selecione o ícone **mais opções** (&#8943;).</span><span class="sxs-lookup"><span data-stu-id="b82f6-213">Select the **More options** icon (&#8943;).</span></span>
> - <span data-ttu-id="b82f6-214">Selecione **obter link para a equipe**.</span><span class="sxs-lookup"><span data-stu-id="b82f6-214">Select **Get link to team**.</span></span>
> - <span data-ttu-id="b82f6-215">Copie e salve o valor de **GroupId** da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b82f6-215">Copy and save the **groupId** value from the string.</span></span>
> - <span data-ttu-id="b82f6-216">Faça logon no **Explorador do Graph**.</span><span class="sxs-lookup"><span data-stu-id="b82f6-216">Log into **Graph Explorer**.</span></span>
> - <span data-ttu-id="b82f6-217">Faça uma chamada **Get** para o ponto de extremidade a seguir: `https://graph.microsoft.com/beta/groups/{teamGroupId}/permissionGrants` .</span><span class="sxs-lookup"><span data-stu-id="b82f6-217">Make a **GET** call to the following endpoint: `https://graph.microsoft.com/beta/groups/{teamGroupId}/permissionGrants`.</span></span> <span data-ttu-id="b82f6-218">O campo clientAppId na resposta será mapeado para a appId especificada no manifesto do aplicativo Teams.</span><span class="sxs-lookup"><span data-stu-id="b82f6-218">The clientAppId field in the response will map to the appId specified in the Teams app manifest.</span></span>

 ![Resposta do explorador do Graph para obter uma chamada.](../../assets/images/graph-permissions.png)
 
## <a name="test-resource-specific-consent"></a><span data-ttu-id="b82f6-220">Teste o consentimento específico do recurso</span><span class="sxs-lookup"><span data-stu-id="b82f6-220">Test resource-specific consent</span></span>
 
> [!div class="nextstepaction"]
> [<span data-ttu-id="b82f6-221">**Testar permissões de consentimento específicas do recurso no Teams**</span><span class="sxs-lookup"><span data-stu-id="b82f6-221">**Test resource-specific consent permissions in Teams**</span></span>](test-resource-specific-consent.md)
 
## <a name="related-topic-for-teams-administrators"></a><span data-ttu-id="b82f6-222">Tópico relacionado para administradores do teams</span><span class="sxs-lookup"><span data-stu-id="b82f6-222">Related topic for Teams administrators</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b82f6-223">**Consentimento específico do recurso no Microsoft Teams para administradores**</span><span class="sxs-lookup"><span data-stu-id="b82f6-223">**Resource-specific consent in Microsoft Teams for admins**</span></span>](/MicrosoftTeams/resource-specific-consent)
> 
