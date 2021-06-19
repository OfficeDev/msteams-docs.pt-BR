---
title: Consentimento específico do recurso em Teams
description: Descreve o consentimento específico do recurso em Teams e como tirar proveito dele.
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: reference
keywords: autorização do teams OAuth SSO AAD rsc Graph
ms.openlocfilehash: 31e3dd0c33e548acd35d86492718875d45931d0b
ms.sourcegitcommit: 60a8d314e4fb48f6789d79dbc2f69321aaff99d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2021
ms.locfileid: "53022975"
---
# <a name="resource-specific-consent-rsc"></a><span data-ttu-id="3f856-104">Consentimento específico do recurso (RSC)</span><span class="sxs-lookup"><span data-stu-id="3f856-104">Resource-specific consent (RSC)</span></span>

> [!NOTE]
> <span data-ttu-id="3f856-105">O consentimento específico do recurso para o escopo de chat está disponível apenas na [visualização do desenvolvedor](../../resources/dev-preview/developer-preview-intro.md) público.</span><span class="sxs-lookup"><span data-stu-id="3f856-105">Resource-specific consent for chat scope is available in [public developer preview](../../resources/dev-preview/developer-preview-intro.md) only.</span></span>

<span data-ttu-id="3f856-106">O RSC (consentimento específico de recurso) é uma integração da API Microsoft Teams e do Microsoft Graph que permite que seu aplicativo use pontos de extremidade da API para gerenciar recursos específicos, equipes ou chats, dentro de uma organização.</span><span class="sxs-lookup"><span data-stu-id="3f856-106">Resource-specific consent (RSC) is a Microsoft Teams and Microsoft Graph API integration that enables your app to use API endpoints to manage specific resources—either teams or chats—within an organization.</span></span> <span data-ttu-id="3f856-107">O modelo de permissões de consentimento específico do recurso (RSC) permite que *proprietários* de equipe e proprietários de *chat* concedam consentimento para que um aplicativo acesse e/ou modifique os dados de uma equipe e os dados de um chat, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="3f856-107">The resource-specific consent (RSC) permissions model enables *team owners* and *chat owners* to grant consent for an application to access and/or modify a team's data and a chat's data, respectively.</span></span> <span data-ttu-id="3f856-108">As permissões RSC granulares definem o que um aplicativo pode fazer em um recurso específico:</span><span class="sxs-lookup"><span data-stu-id="3f856-108">The granular RSC permissions define what an application can do within a specific resource:</span></span>

## <a name="resource-specific-permissions"></a><span data-ttu-id="3f856-109">Permissões específicas de recursos</span><span class="sxs-lookup"><span data-stu-id="3f856-109">Resource-specific permissions</span></span>

### <a name="resource-specific-permissions-for-a-team"></a><span data-ttu-id="3f856-110">Permissões específicas de recursos para uma equipe</span><span class="sxs-lookup"><span data-stu-id="3f856-110">Resource-specific permissions for a team</span></span>
|<span data-ttu-id="3f856-111">Permissão de aplicativo</span><span class="sxs-lookup"><span data-stu-id="3f856-111">Application permission</span></span>| <span data-ttu-id="3f856-112">Ação</span><span class="sxs-lookup"><span data-stu-id="3f856-112">Action</span></span> |
| ----- | ----- |
|<span data-ttu-id="3f856-113">TeamSettings.Read.Group</span><span class="sxs-lookup"><span data-stu-id="3f856-113">TeamSettings.Read.Group</span></span> | <span data-ttu-id="3f856-114">Obter as configurações dessa equipe.</span><span class="sxs-lookup"><span data-stu-id="3f856-114">Get this team's settings.</span></span>|
|<span data-ttu-id="3f856-115">TeamSettings.ReadWrite.Group</span><span class="sxs-lookup"><span data-stu-id="3f856-115">TeamSettings.ReadWrite.Group</span></span>|<span data-ttu-id="3f856-116">Atualize as configurações dessa equipe.</span><span class="sxs-lookup"><span data-stu-id="3f856-116">Update this team's settings.</span></span>|
|<span data-ttu-id="3f856-117">ChannelSettings.Read.Group</span><span class="sxs-lookup"><span data-stu-id="3f856-117">ChannelSettings.Read.Group</span></span>|<span data-ttu-id="3f856-118">Obter nomes de canal dessa equipe, descrições de canal e configurações de canal.</span><span class="sxs-lookup"><span data-stu-id="3f856-118">Get this team's channel names, channel descriptions, and channel settings.</span></span>|
|<span data-ttu-id="3f856-119">ChannelSettings.ReadWrite.Group</span><span class="sxs-lookup"><span data-stu-id="3f856-119">ChannelSettings.ReadWrite.Group</span></span>|<span data-ttu-id="3f856-120">Atualize os nomes de canal dessa equipe, descrições de canal e configurações de canal.</span><span class="sxs-lookup"><span data-stu-id="3f856-120">Update this team's channel names, channel descriptions, and channel settings.</span></span>|
|<span data-ttu-id="3f856-121">Channel.Create.Group</span><span class="sxs-lookup"><span data-stu-id="3f856-121">Channel.Create.Group</span></span>|<span data-ttu-id="3f856-122">Criar canais nesta equipe.</span><span class="sxs-lookup"><span data-stu-id="3f856-122">Create channels in this team.</span></span> |
|<span data-ttu-id="3f856-123">Channel.Delete.Group</span><span class="sxs-lookup"><span data-stu-id="3f856-123">Channel.Delete.Group</span></span>|<span data-ttu-id="3f856-124">Exclua canais nesta equipe.</span><span class="sxs-lookup"><span data-stu-id="3f856-124">Delete channels in this team.</span></span> |
|<span data-ttu-id="3f856-125">ChannelMessage.Read.Group</span><span class="sxs-lookup"><span data-stu-id="3f856-125">ChannelMessage.Read.Group</span></span> |<span data-ttu-id="3f856-126">Receba as mensagens de canal dessa equipe.</span><span class="sxs-lookup"><span data-stu-id="3f856-126">Get this team's channel messages.</span></span> |
|<span data-ttu-id="3f856-127">TeamsAppInstallation.Read.Group</span><span class="sxs-lookup"><span data-stu-id="3f856-127">TeamsAppInstallation.Read.Group</span></span>|<span data-ttu-id="3f856-128">Obter uma lista dos aplicativos instalados dessa equipe.</span><span class="sxs-lookup"><span data-stu-id="3f856-128">Get a list of this team's installed apps.</span></span>|
|<span data-ttu-id="3f856-129">TeamsTab.Read.Group</span><span class="sxs-lookup"><span data-stu-id="3f856-129">TeamsTab.Read.Group</span></span>|<span data-ttu-id="3f856-130">Obter uma lista das guias dessa equipe.</span><span class="sxs-lookup"><span data-stu-id="3f856-130">Get a list of this team's tabs.</span></span>|
|<span data-ttu-id="3f856-131">TeamsTab.Create.Group</span><span class="sxs-lookup"><span data-stu-id="3f856-131">TeamsTab.Create.Group</span></span>|<span data-ttu-id="3f856-132">Criar guias nesta equipe.</span><span class="sxs-lookup"><span data-stu-id="3f856-132">Create tabs in this team.</span></span> |
|<span data-ttu-id="3f856-133">TeamsTab.ReadWrite.Group</span><span class="sxs-lookup"><span data-stu-id="3f856-133">TeamsTab.ReadWrite.Group</span></span>|<span data-ttu-id="3f856-134">Atualize as guias desta equipe.</span><span class="sxs-lookup"><span data-stu-id="3f856-134">Update this team's tabs.</span></span> |
|<span data-ttu-id="3f856-135">TeamsTab.Delete.Group</span><span class="sxs-lookup"><span data-stu-id="3f856-135">TeamsTab.Delete.Group</span></span>|<span data-ttu-id="3f856-136">Excluir as guias dessa equipe.</span><span class="sxs-lookup"><span data-stu-id="3f856-136">Delete this team's tabs.</span></span> |
|<span data-ttu-id="3f856-137">TeamMember.Read.Group</span><span class="sxs-lookup"><span data-stu-id="3f856-137">TeamMember.Read.Group</span></span>|<span data-ttu-id="3f856-138">Obter os membros dessa equipe.</span><span class="sxs-lookup"><span data-stu-id="3f856-138">Get this team's members.</span></span> |

<span data-ttu-id="3f856-139">Para obter mais detalhes, consulte Permissões de consentimento [específicas do](/graph/permissions-reference#team-resource-specific-consent-permissions)recurso de equipe .</span><span class="sxs-lookup"><span data-stu-id="3f856-139">For more details, see [Team resource-specific consent permissions](/graph/permissions-reference#team-resource-specific-consent-permissions).</span></span>

### <a name="resource-specific-permissions-for-a-chat"></a><span data-ttu-id="3f856-140">Permissões específicas de recursos para um chat</span><span class="sxs-lookup"><span data-stu-id="3f856-140">Resource-specific permissions for a chat</span></span>
|<span data-ttu-id="3f856-141">Permissão de aplicativo</span><span class="sxs-lookup"><span data-stu-id="3f856-141">Application permission</span></span>| <span data-ttu-id="3f856-142">Ação</span><span class="sxs-lookup"><span data-stu-id="3f856-142">Action</span></span> |
| ----- | ----- |
| <span data-ttu-id="3f856-143">ChatSettings.Read.Chat</span><span class="sxs-lookup"><span data-stu-id="3f856-143">ChatSettings.Read.Chat</span></span>         | <span data-ttu-id="3f856-144">Obter as configurações desse chat.</span><span class="sxs-lookup"><span data-stu-id="3f856-144">Get this chat's settings.</span></span>                                    |
| <span data-ttu-id="3f856-145">ChatSettings.ReadWrite.Chat</span><span class="sxs-lookup"><span data-stu-id="3f856-145">ChatSettings.ReadWrite.Chat</span></span>    | <span data-ttu-id="3f856-146">Atualize as configurações desse chat.</span><span class="sxs-lookup"><span data-stu-id="3f856-146">Update this chat's settings.</span></span>                          |
| <span data-ttu-id="3f856-147">ChatMessage.Read.Chat</span><span class="sxs-lookup"><span data-stu-id="3f856-147">ChatMessage.Read.Chat</span></span>          | <span data-ttu-id="3f856-148">Receba as mensagens desse chat.</span><span class="sxs-lookup"><span data-stu-id="3f856-148">Get this chat's messages.</span></span>                                    |
| <span data-ttu-id="3f856-149">ChatMember.Read.Chat</span><span class="sxs-lookup"><span data-stu-id="3f856-149">ChatMember.Read.Chat</span></span>           | <span data-ttu-id="3f856-150">Obter membros desse chat.</span><span class="sxs-lookup"><span data-stu-id="3f856-150">Get this chat's members.</span></span>                                     |
| <span data-ttu-id="3f856-151">Chat.Manage.Chat</span><span class="sxs-lookup"><span data-stu-id="3f856-151">Chat.Manage.Chat</span></span>               | <span data-ttu-id="3f856-152">Gerenciar este chat</span><span class="sxs-lookup"><span data-stu-id="3f856-152">Manage this chat.</span></span>                                             |
| <span data-ttu-id="3f856-153">TeamsTab.Read.Chat</span><span class="sxs-lookup"><span data-stu-id="3f856-153">TeamsTab.Read.Chat</span></span>             | <span data-ttu-id="3f856-154">Obter as guias desse chat.</span><span class="sxs-lookup"><span data-stu-id="3f856-154">Get this chat's tabs.</span></span>                                        |
| <span data-ttu-id="3f856-155">TeamsTab.Create.Chat</span><span class="sxs-lookup"><span data-stu-id="3f856-155">TeamsTab.Create.Chat</span></span>           | <span data-ttu-id="3f856-156">Criar as guias neste chat.</span><span class="sxs-lookup"><span data-stu-id="3f856-156">Create tabs in this chat.</span></span>                                     |
| <span data-ttu-id="3f856-157">TeamsTab.Delete.Chat</span><span class="sxs-lookup"><span data-stu-id="3f856-157">TeamsTab.Delete.Chat</span></span>           | <span data-ttu-id="3f856-158">Exclua as guias deste chat.</span><span class="sxs-lookup"><span data-stu-id="3f856-158">Delete this chat's tabs.</span></span>                                      |
| <span data-ttu-id="3f856-159">TeamsTab.ReadWrite.Chat</span><span class="sxs-lookup"><span data-stu-id="3f856-159">TeamsTab.ReadWrite.Chat</span></span>        | <span data-ttu-id="3f856-160">Gerenciar as guias deste chat.</span><span class="sxs-lookup"><span data-stu-id="3f856-160">Manage this chat's tabs.</span></span>                                      |
| <span data-ttu-id="3f856-161">TeamsAppInstallation.Read.Chat</span><span class="sxs-lookup"><span data-stu-id="3f856-161">TeamsAppInstallation.Read.Chat</span></span> | <span data-ttu-id="3f856-162">Obter quais aplicativos estão instalados neste chat.</span><span class="sxs-lookup"><span data-stu-id="3f856-162">Get which apps are installed in this chat.</span></span>                   |
| <span data-ttu-id="3f856-163">OnlineMeeting.ReadBasic.Chat</span><span class="sxs-lookup"><span data-stu-id="3f856-163">OnlineMeeting.ReadBasic.Chat</span></span>   | <span data-ttu-id="3f856-164">Obter propriedades básicas, como nome, agendamento, organizador e link de associação, de uma reunião associada a esse chat.</span><span class="sxs-lookup"><span data-stu-id="3f856-164">Get basic properties—such as name, schedule, organizer, and join link—of a meeting associated with this chat.</span></span> |

<span data-ttu-id="3f856-165">Para obter mais detalhes, consulte [Chat resource-specific consent permissions](/graph/permissions-reference#chat-resource-specific-consent-permissions).</span><span class="sxs-lookup"><span data-stu-id="3f856-165">For more details, see [Chat resource-specific consent permissions](/graph/permissions-reference#chat-resource-specific-consent-permissions).</span></span>

>[!NOTE]
><span data-ttu-id="3f856-166">Permissões específicas de recursos estão disponíveis apenas para Teams aplicativos instalados no cliente Teams e atualmente não fazem parte do portal Active Directory do Azure.</span><span class="sxs-lookup"><span data-stu-id="3f856-166">Resource-specific permissions are only available to Teams apps installed on the Teams client and are currently not part of the Azure Active Directory portal.</span></span>

## <a name="enable-resource-specific-consent-in-your-application"></a><span data-ttu-id="3f856-167">Habilitar o consentimento específico do recurso em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="3f856-167">Enable resource-specific consent in your application</span></span>

<span data-ttu-id="3f856-168">As etapas para habilenciar o RSC em seu aplicativo são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="3f856-168">The steps for enabling RSC in your application are as follows:</span></span>

1. <span data-ttu-id="3f856-169">[Configure as configurações de consentimento no portal Active Directory do Azure .](#configure-consent-settings-in-the-azure-ad-portal)</span><span class="sxs-lookup"><span data-stu-id="3f856-169">[Configure consent settings in the Azure Active Directory portal](#configure-consent-settings-in-the-azure-ad-portal).</span></span>
    1. <span data-ttu-id="3f856-170">[Configure as configurações de consentimento do proprietário do grupo para o RSC em uma equipe.](#configure-group-owner-consent-settings-for-rsc-in-a-team)</span><span class="sxs-lookup"><span data-stu-id="3f856-170">[Configure group owner consent settings for RSC in a team](#configure-group-owner-consent-settings-for-rsc-in-a-team).</span></span>
    1. <span data-ttu-id="3f856-171">[Configurar configurações de consentimento do usuário para RSC em um chat](#configure-user-consent-settings-for-rsc-in-a-chat).</span><span class="sxs-lookup"><span data-stu-id="3f856-171">[Configure user consent settings for RSC in a chat](#configure-user-consent-settings-for-rsc-in-a-chat).</span></span>
1. <span data-ttu-id="3f856-172">[Registre seu aplicativo com plataforma de identidade da Microsoft por meio do portal do Azure AD.](#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal)</span><span class="sxs-lookup"><span data-stu-id="3f856-172">[Register your app with Microsoft identity platform via the Azure AD portal](#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).</span></span>
1. <span data-ttu-id="3f856-173">[Revise suas permissões de aplicativo no portal do Azure AD.](#review-your-application-permissions-in-the-azure-ad-portal)</span><span class="sxs-lookup"><span data-stu-id="3f856-173">[Review your application permissions in the Azure AD portal](#review-your-application-permissions-in-the-azure-ad-portal).</span></span>
1. <span data-ttu-id="3f856-174">[Obtenha um token de acesso da plataforma Microsoft Identity](#obtain-an-access-token-from-the-microsoft-identity-platform).</span><span class="sxs-lookup"><span data-stu-id="3f856-174">[Obtain an access token from the Microsoft Identity platform](#obtain-an-access-token-from-the-microsoft-identity-platform).</span></span>
1. <span data-ttu-id="3f856-175">[Atualize seu Teams de aplicativo .](#update-your-teams-app-manifest)</span><span class="sxs-lookup"><span data-stu-id="3f856-175">[Update your Teams app manifest](#update-your-teams-app-manifest).</span></span>
1. <span data-ttu-id="3f856-176">[Instale seu aplicativo diretamente no Teams](#sideload-your-app-in-teams).</span><span class="sxs-lookup"><span data-stu-id="3f856-176">[Install your app directly in Teams](#sideload-your-app-in-teams).</span></span>
1. <span data-ttu-id="3f856-177">[Verifique se o aplicativo tem permissões RSC adicionadas.](#check-your-app-for-added-rsc-permissions)</span><span class="sxs-lookup"><span data-stu-id="3f856-177">[Check your app for added RSC permissions](#check-your-app-for-added-rsc-permissions).</span></span>
    1. <span data-ttu-id="3f856-178">[Verifique se o aplicativo adicionou permissões RSC em uma equipe](#check-your-app-for-added-rsc-permissions-in-a-team).</span><span class="sxs-lookup"><span data-stu-id="3f856-178">[Check your app for added RSC permissions in a team](#check-your-app-for-added-rsc-permissions-in-a-team).</span></span>
    1. <span data-ttu-id="3f856-179">[Verifique se o aplicativo adicionou permissões RSC em um chat](#check-your-app-for-added-rsc-permissions-in-a-chat).</span><span class="sxs-lookup"><span data-stu-id="3f856-179">[Check your app for added RSC permissions in a chat](#check-your-app-for-added-rsc-permissions-in-a-chat).</span></span>

## <a name="configure-consent-settings-in-the-azure-ad-portal"></a><span data-ttu-id="3f856-180">Configurar configurações de consentimento no portal do Azure AD</span><span class="sxs-lookup"><span data-stu-id="3f856-180">Configure consent settings in the Azure AD portal</span></span>

### <a name="configure-group-owner-consent-settings-for-rsc-in-a-team"></a><span data-ttu-id="3f856-181">Configurar configurações de consentimento do proprietário do grupo para RSC em uma equipe</span><span class="sxs-lookup"><span data-stu-id="3f856-181">Configure group owner consent settings for RSC in a team</span></span>

<span data-ttu-id="3f856-182">Você pode habilitar ou [desabilitar o consentimento do](/azure/active-directory/manage-apps/configure-user-consent-groups?tabs=azure-portal) proprietário do grupo diretamente no portal do Azure:</span><span class="sxs-lookup"><span data-stu-id="3f856-182">You can enable or disable [group owner consent](/azure/active-directory/manage-apps/configure-user-consent-groups?tabs=azure-portal) directly within the Azure portal:</span></span>

> [!div class="checklist"]
>
>- <span data-ttu-id="3f856-183">Entre no [portal do Azure](https://portal.azure.com) como administrador [global/administrador da empresa.](/azure/active-directory/roles/permissions-reference#global-administrator&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="3f856-183">Sign in to the [Azure portal](https://portal.azure.com) as a [Global Administrator/Company Administrator](/azure/active-directory/roles/permissions-reference#global-administrator&preserve-view=true).</span></span>  
 > - <span data-ttu-id="3f856-184">[Selecione](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConsentPoliciesMenuBlade/UserSettings) **Active Directory do Azure**  =>  **Enterprise**  =>  **aplicativos Consentimento e permissões**  =>  **Configurações de consentimento do usuário.**</span><span class="sxs-lookup"><span data-stu-id="3f856-184">[Select](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConsentPoliciesMenuBlade/UserSettings) **Azure Active Directory** => **Enterprise applications** => **Consent and permissions** => **User consent settings**.</span></span>
> - <span data-ttu-id="3f856-185">Habilitar, desabilitar ou limitar o consentimento do usuário com o controle rotulado consentimento do proprietário do grupo para aplicativos que acessam dados **(O** padrão é Permitir o consentimento do proprietário do grupo para todos os proprietários **do grupo**).</span><span class="sxs-lookup"><span data-stu-id="3f856-185">Enable, disable, or limit user consent with the control labeled **Group owner consent for apps accessing data** (The default is **Allow group owner consent for all group owners**).</span></span> <span data-ttu-id="3f856-186">Para que o proprietário da equipe instale um aplicativo usando o RSC, o consentimento do proprietário do grupo deve ser habilitado para esse usuário.</span><span class="sxs-lookup"><span data-stu-id="3f856-186">For a team owner to install an app using RSC, group owner consent must be enabled for that user.</span></span>

![Configuração da equipe rsc do azure](../../assets/images/azure-rsc-team-configuration.png)

<span data-ttu-id="3f856-188">Para habilitar ou desabilitar o consentimento do proprietário do grupo usando o PowerShell, siga as etapas descritas em [Configure group owner consent using PowerShell](/azure/active-directory/manage-apps/configure-user-consent-groups?tabs=azure-powershell).</span><span class="sxs-lookup"><span data-stu-id="3f856-188">To enable or disable group owner consent using PowerShell, follow the steps outlined in [Configure group owner consent using PowerShell](/azure/active-directory/manage-apps/configure-user-consent-groups?tabs=azure-powershell).</span></span>

### <a name="configure-user-consent-settings-for-rsc-in-a-chat"></a><span data-ttu-id="3f856-189">Configurar configurações de consentimento do usuário para RSC em um chat</span><span class="sxs-lookup"><span data-stu-id="3f856-189">Configure user consent settings for RSC in a chat</span></span>

<span data-ttu-id="3f856-190">Você pode habilitar ou [desabilitar o consentimento do](/azure/active-directory/manage-apps/configure-user-consent?tabs=azure-portal) usuário diretamente no portal do Azure:</span><span class="sxs-lookup"><span data-stu-id="3f856-190">You can enable or disable [user consent](/azure/active-directory/manage-apps/configure-user-consent?tabs=azure-portal) directly within the Azure portal:</span></span>

> [!div class="checklist"]
>
>- <span data-ttu-id="3f856-191">Entre no [portal do Azure](https://portal.azure.com) como administrador [global/administrador da empresa.](/azure/active-directory/roles/permissions-reference#global-administrator&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="3f856-191">Sign in to the [Azure portal](https://portal.azure.com) as a [Global Administrator/Company Administrator](/azure/active-directory/roles/permissions-reference#global-administrator&preserve-view=true).</span></span>  
 > - <span data-ttu-id="3f856-192">[Selecione](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConsentPoliciesMenuBlade/UserSettings) **Active Directory do Azure**  =>  **Enterprise**  =>  **aplicativos Consentimento e permissões**  =>  **Configurações de consentimento do usuário.**</span><span class="sxs-lookup"><span data-stu-id="3f856-192">[Select](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConsentPoliciesMenuBlade/UserSettings) **Azure Active Directory** => **Enterprise applications** => **Consent and permissions** => **User consent settings**.</span></span>
> - <span data-ttu-id="3f856-193">Habilitar, desabilitar ou limitar o consentimento do usuário com o controle rotulado Consentimento do usuário para aplicativos **(O** padrão é Permitir o **consentimento do usuário para aplicativos**).</span><span class="sxs-lookup"><span data-stu-id="3f856-193">Enable, disable, or limit user consent with the control labeled **User consent for applications** (The default is **Allow user consent for apps**).</span></span> <span data-ttu-id="3f856-194">Para um membro do chat instalar um aplicativo usando o RSC, o consentimento do usuário deve ser habilitado para esse usuário.</span><span class="sxs-lookup"><span data-stu-id="3f856-194">For a chat member to install an app using RSC, user consent must be enabled for that user.</span></span>

![Configuração de chat rsc do azure](../../assets/images/azure-rsc-chat-configuration.png)

<span data-ttu-id="3f856-196">Para habilitar ou desabilitar o consentimento do usuário usando o PowerShell, siga as etapas descritas em [Configure user consent using PowerShell](/azure/active-directory/manage-apps/configure-user-consent?tabs=azure-powershell).</span><span class="sxs-lookup"><span data-stu-id="3f856-196">To enable or disable user consent using PowerShell, follow the steps outlined in [Configure user consent using PowerShell](/azure/active-directory/manage-apps/configure-user-consent?tabs=azure-powershell).</span></span>


## <a name="register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal"></a><span data-ttu-id="3f856-197">Registrar seu aplicativo com plataforma de identidade da Microsoft por meio do portal do Azure AD</span><span class="sxs-lookup"><span data-stu-id="3f856-197">Register your app with Microsoft identity platform via the Azure AD portal</span></span>

<span data-ttu-id="3f856-198">O Active Directory do Azure portal fornece uma plataforma central para você registrar e configurar seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="3f856-198">The Azure Active Directory portal provides a central platform for you to register and configure your apps.</span></span> <span data-ttu-id="3f856-199">Seu aplicativo deve ser registrado no portal do Azure AD para se integrar ao plataforma de identidade da Microsoft e chamar as APIs Graph Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3f856-199">Your app must be registered in the Azure AD portal to integrate with the Microsoft identity platform and call Microsoft Graph APIs.</span></span> <span data-ttu-id="3f856-200">Para obter mais informações, [consulte Register an application with the plataforma de identidade da Microsoft](/graph/auth-register-app-v2).</span><span class="sxs-lookup"><span data-stu-id="3f856-200">For more information, see [Register an application with the Microsoft identity platform](/graph/auth-register-app-v2).</span></span>

>[!WARNING]
><span data-ttu-id="3f856-201">Uma ID de aplicativo do Azure AD não deve ser compartilhada entre vários Teams aplicativos.</span><span class="sxs-lookup"><span data-stu-id="3f856-201">An Azure AD app ID should not be shared across multiple Teams apps.</span></span> <span data-ttu-id="3f856-202">Deve haver um mapeamento 1:1 entre um aplicativo Teams e um aplicativo do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="3f856-202">There should be a 1:1 mapping between a Teams App and an Azure AD app.</span></span> <span data-ttu-id="3f856-203">As tentativas de instalar vários Teams que estão associados à mesma ID do aplicativo do Azure AD causarão falhas de instalação/tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="3f856-203">Attempts to install multiple Teams apps which are associated with the same Azure AD app ID will cause installation/runtime failures.</span></span>

## <a name="review-your-application-permissions-in-the-azure-ad-portal"></a><span data-ttu-id="3f856-204">Revise suas permissões de aplicativo no portal do Azure AD</span><span class="sxs-lookup"><span data-stu-id="3f856-204">Review your application permissions in the Azure AD portal</span></span>

<span data-ttu-id="3f856-205">Navegue até **a página Registros** do Aplicativo Inicial e selecione seu aplicativo  =>   RSC.</span><span class="sxs-lookup"><span data-stu-id="3f856-205">Navigate to the **Home** => **App registrations** page and select your RSC app.</span></span> <span data-ttu-id="3f856-206">Escolha **permissões de API** na barra de nav esquerda e examine a lista de permissões configuradas para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3f856-206">Choose **API permissions** from the left nav bar and examine the list of configured permissions for your app.</span></span> <span data-ttu-id="3f856-207">Se seu aplicativo fizer apenas chamadas de API RSC Graph, exclua toda a permissão nessa página.</span><span class="sxs-lookup"><span data-stu-id="3f856-207">If your app will only make RSC Graph API calls, delete all the permission on that page.</span></span> <span data-ttu-id="3f856-208">Se seu aplicativo também fizer chamadas não RSC, mantenha essas permissões conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="3f856-208">If your app will also make non-RSC calls, keep those permissions as needed.</span></span>

>[!IMPORTANT]
><span data-ttu-id="3f856-209">O portal do Azure AD não pode ser usado para solicitar permissões RSC.</span><span class="sxs-lookup"><span data-stu-id="3f856-209">The Azure AD portal cannot be used to request RSC permissions.</span></span> <span data-ttu-id="3f856-210">As permissões RSC atualmente são exclusivas Teams aplicativos instalados no cliente Teams e são declaradas no arquivo JSON (manifesto do aplicativo Teams).</span><span class="sxs-lookup"><span data-stu-id="3f856-210">RSC permissions are currently exclusive to Teams applications installed in the Teams client and are declared in the Teams app manifest (JSON) file.</span></span>

## <a name="obtain-an-access-token-from-the-microsoft-identity-platform"></a><span data-ttu-id="3f856-211">Obtenha um token de acesso do plataforma de identidade da Microsoft</span><span class="sxs-lookup"><span data-stu-id="3f856-211">Obtain an access token from the Microsoft identity platform</span></span>

<span data-ttu-id="3f856-212">Para fazer Graph de API, você deve obter um token de acesso para seu aplicativo a partir da plataforma de identidade.</span><span class="sxs-lookup"><span data-stu-id="3f856-212">To make Graph API calls, you must obtain an access token for your app from the identity platform.</span></span> <span data-ttu-id="3f856-213">Para que seu aplicativo possa obter um token do plataforma de identidade da Microsoft, ele deve ser registrado no portal do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="3f856-213">Before your app can get a token from the Microsoft identity platform, it must be registered in the Azure AD portal.</span></span> <span data-ttu-id="3f856-214">O token de acesso contém informações sobre seu aplicativo e as permissões que ele possui para os recursos e APIs disponíveis no Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="3f856-214">The access token contains information about your app and the permissions it has for the resources and APIs available through Microsoft Graph.</span></span>

<span data-ttu-id="3f856-215">Você precisará ter os seguintes valores do processo de registro do Azure AD para recuperar um token de acesso da plataforma de identidade:</span><span class="sxs-lookup"><span data-stu-id="3f856-215">You'll need to have the following values from the Azure AD registration process to retrieve an access token from the identity platform:</span></span>

- <span data-ttu-id="3f856-216">A **ID do aplicativo** atribuída pelo portal de registro do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3f856-216">The **Application ID** assigned by the app registration portal.</span></span> <span data-ttu-id="3f856-217">Se seu aplicativo oferece suporte a SSO (login único), você deve usar a mesma ID do Aplicativo para seu aplicativo e SSO.</span><span class="sxs-lookup"><span data-stu-id="3f856-217">If your app supports single sign-on (SSO) you should use the same Application ID for your app and SSO.</span></span>
- <span data-ttu-id="3f856-218">O  **segredo/senha do cliente** ou um par de chaves públicas/privadas (**Certificado**).</span><span class="sxs-lookup"><span data-stu-id="3f856-218">The  **Client secret/password** or a public/private key pair (**Certificate**).</span></span> <span data-ttu-id="3f856-219">Isso não é necessário para aplicativos nativos.</span><span class="sxs-lookup"><span data-stu-id="3f856-219">This is not required for native apps.</span></span>
- <span data-ttu-id="3f856-220">Um **URI de redirecionamento** (ou URL de resposta) para seu aplicativo receber respostas do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="3f856-220">A **Redirect URI** (or reply URL) for your app to receive responses from Azure AD.</span></span>

 <span data-ttu-id="3f856-221">*Consulte* [Obter acesso em nome de um usuário e](/graph/auth-v2-user?view=graph-rest-1.0#3-get-a-token&preserve-view=true) Obter acesso sem um [usuário](/graph/auth-v2-service)</span><span class="sxs-lookup"><span data-stu-id="3f856-221">*See* [Get access on behalf of a user](/graph/auth-v2-user?view=graph-rest-1.0#3-get-a-token&preserve-view=true) and [Get access without a user](/graph/auth-v2-service)</span></span>

## <a name="update-your-teams-app-manifest"></a><span data-ttu-id="3f856-222">Atualizar seu manifesto Teams aplicativo</span><span class="sxs-lookup"><span data-stu-id="3f856-222">Update your Teams app manifest</span></span>

<span data-ttu-id="3f856-223">As permissões RSC são declaradas no arquivo JSON (manifesto do aplicativo).</span><span class="sxs-lookup"><span data-stu-id="3f856-223">The RSC permissions are declared in your app manifest (JSON) file.</span></span>  <span data-ttu-id="3f856-224">Adicione uma [chave webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) ao manifesto do aplicativo com os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="3f856-224">Add a [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) key to your app manifest with the following values:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="3f856-225">**id**  — sua ID do aplicativo do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="3f856-225">**id**  — your Azure AD app ID.</span></span> <span data-ttu-id="3f856-226">Para obter mais informações, consulte [Register your app in the Azure AD portal](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).</span><span class="sxs-lookup"><span data-stu-id="3f856-226">For more information, see [Register your app in the Azure AD portal](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).</span></span>
> - <span data-ttu-id="3f856-227">**resource**  — qualquer cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="3f856-227">**resource**  — any string.</span></span> <span data-ttu-id="3f856-228">Este campo não tem operação no RSC, mas deve ser adicionado e ter um valor para evitar uma resposta de erro; qualquer cadeia de caracteres fará.</span><span class="sxs-lookup"><span data-stu-id="3f856-228">This field has no operation in RSC, but must be added and have a value to avoid an error response; any string will do.</span></span>
> - <span data-ttu-id="3f856-229">**permissões de aplicativo** — permissões RSC para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3f856-229">**application permissions** — RSC permissions for  your app.</span></span> <span data-ttu-id="3f856-230">Para obter mais informações, consulte [Permissões específicas do recurso](resource-specific-consent.md#resource-specific-permissions).</span><span class="sxs-lookup"><span data-stu-id="3f856-230">For more information, see [Resource-specific Permissions](resource-specific-consent.md#resource-specific-permissions).</span></span>

>
>[!IMPORTANT]
> <span data-ttu-id="3f856-231">As permissões não RSC são armazenadas no portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="3f856-231">Non-RSC permissions are stored in the Azure portal.</span></span> <span data-ttu-id="3f856-232">Não os adicione ao manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3f856-232">Do not add them to the app manifest.</span></span>
>

### <a name="example-for-rsc-in-a-team"></a><span data-ttu-id="3f856-233">Exemplo de RSC em uma equipe</span><span class="sxs-lookup"><span data-stu-id="3f856-233">Example for RSC in a team</span></span>
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

### <a name="example-for-rsc-in-a-chat"></a><span data-ttu-id="3f856-234">Exemplo de RSC em um chat</span><span class="sxs-lookup"><span data-stu-id="3f856-234">Example for RSC in a chat</span></span>
```json
"webApplicationInfo": {
    "id": "XXxxXXXXX-XxXX-xXXX-XXxx-XXXXXXXxxxXX",
    "resource": "https://RscBasedStoreApp",
    "applicationPermissions": [
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

>[!NOTE]
><span data-ttu-id="3f856-235">Se o aplicativo tiver o objetivo de dar suporte à instalação em escopos de equipe e chat, as permissões de equipe e de chat poderão ser especificadas no mesmo manifesto em `applicationPermissions` .</span><span class="sxs-lookup"><span data-stu-id="3f856-235">If the app is meant to support installation in both team and chat scopes, then both team and chat permissions can be specified in the same manifest under `applicationPermissions`.</span></span>

## <a name="sideload-your-app-in-teams"></a><span data-ttu-id="3f856-236">Fazer sideload do aplicativo Teams</span><span class="sxs-lookup"><span data-stu-id="3f856-236">Sideload your app in Teams</span></span>

<span data-ttu-id="3f856-237">Se o administrador Teams permite carregamentos de aplicativos personalizados, você pode [fazer sideload](~/concepts/deploy-and-publish/apps-upload.md) do aplicativo diretamente em uma equipe ou chat específico.</span><span class="sxs-lookup"><span data-stu-id="3f856-237">If your Teams admin allows custom app uploads, you can [sideload your app](~/concepts/deploy-and-publish/apps-upload.md) directly to a specific team or chat.</span></span>

## <a name="check-your-app-for-added-rsc-permissions"></a><span data-ttu-id="3f856-238">Verifique se o aplicativo tem permissões RSC adicionadas</span><span class="sxs-lookup"><span data-stu-id="3f856-238">Check your app for added RSC permissions</span></span>

>[!IMPORTANT]
><span data-ttu-id="3f856-239">As permissões RSC não são atribuídas a um usuário.</span><span class="sxs-lookup"><span data-stu-id="3f856-239">The RSC permissions are not attributed to a user.</span></span> <span data-ttu-id="3f856-240">As chamadas são feitas com permissões de aplicativo, não permissões delegadas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="3f856-240">Calls are made with app permissions, not user delegated permissions.</span></span> <span data-ttu-id="3f856-241">Assim, o aplicativo pode ter permissão para executar ações que o usuário não pode, como excluir uma guia. Você deve analisar a intenção do proprietário da equipe ou do proprietário do chat para o caso de uso antes de fazer chamadas da API RSC.</span><span class="sxs-lookup"><span data-stu-id="3f856-241">Thus, the app may be allowed to perform actions that the user cannot, such as deleting a tab. You should review the team owner's or chat owner's intent for your use case prior to making RSC API calls.</span></span> <span data-ttu-id="3f856-242">Para obter mais informações, [consulte Microsoft Teams visão geral da API](/graph/teams-concept-overview).</span><span class="sxs-lookup"><span data-stu-id="3f856-242">For more information, see [Microsoft Teams API overview](/graph/teams-concept-overview).</span></span>

<span data-ttu-id="3f856-243">Depois que o aplicativo for instalado em um recurso, você poderá usar o [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer) para exibir as permissões que foram concedidas ao aplicativo no recurso:</span><span class="sxs-lookup"><span data-stu-id="3f856-243">Once the app has been installed to a resource, you can use [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer)  to view the permissions that have been granted to the app in the resource:</span></span>

### <a name="check-your-app-for-added-rsc-permissions-in-a-team"></a><span data-ttu-id="3f856-244">Verifique se o aplicativo adicionou permissões RSC em uma equipe</span><span class="sxs-lookup"><span data-stu-id="3f856-244">Check your app for added RSC permissions in a team</span></span>

> [!div class="checklist"]
>
>- <span data-ttu-id="3f856-245">Obter **groupId** da equipe do cliente Teams.</span><span class="sxs-lookup"><span data-stu-id="3f856-245">Get the team's **groupId** from the Teams client.</span></span>
> - <span data-ttu-id="3f856-246">No cliente Teams, selecione **Teams** na barra de nav da extrema esquerda.</span><span class="sxs-lookup"><span data-stu-id="3f856-246">In the Teams client, select **Teams** from the far left nav bar.</span></span>
> - <span data-ttu-id="3f856-247">Selecione a equipe onde o aplicativo está instalado no menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="3f856-247">Select the team where the app is installed from the drop-down menu.</span></span>
> - <span data-ttu-id="3f856-248">Selecione o **ícone Mais opções** (&#8943;).</span><span class="sxs-lookup"><span data-stu-id="3f856-248">Select the **More options** icon (&#8943;).</span></span>
> - <span data-ttu-id="3f856-249">Selecione **Obter link para a equipe**.</span><span class="sxs-lookup"><span data-stu-id="3f856-249">Select **Get link to team**.</span></span>
> - <span data-ttu-id="3f856-250">Copie e salve o **valor groupId** da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="3f856-250">Copy and save the **groupId** value from the string.</span></span>
> - <span data-ttu-id="3f856-251">Faça **logoff Graph Explorer**.</span><span class="sxs-lookup"><span data-stu-id="3f856-251">Log into **Graph Explorer**.</span></span>
> - <span data-ttu-id="3f856-252">Faça uma **chamada GET** para o seguinte ponto de extremidade: `https://graph.microsoft.com/beta/teams/{teamGroupId}/permissionGrants` .</span><span class="sxs-lookup"><span data-stu-id="3f856-252">Make a **GET** call to the following endpoint: `https://graph.microsoft.com/beta/teams/{teamGroupId}/permissionGrants`.</span></span> <span data-ttu-id="3f856-253">O `clientAppId` campo na resposta será mapeado para o especificado no manifesto Teams `webApplicationInfo.id` aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3f856-253">The `clientAppId` field in the response will map to the `webApplicationInfo.id` specified in the Teams app manifest.</span></span>
  <span data-ttu-id="3f856-254">![Graph resposta do explorer à chamada GET para permissões RSC de equipe.](../../assets/images/team-graph-permissions.png)</span><span class="sxs-lookup"><span data-stu-id="3f856-254">![Graph explorer response to GET call for team RSC permissions.](../../assets/images/team-graph-permissions.png)</span></span>

<span data-ttu-id="3f856-255">Para obter informações sobre como obter detalhes sobre aplicativos instalados em uma equipe específica, consulte Obter os nomes e outros detalhes dos aplicativos instalados na [equipe especificada](/graph/api/team-list-installedapps#example-2-get-the-names-and-other-details-of-installed-apps).</span><span class="sxs-lookup"><span data-stu-id="3f856-255">For information about how to get details about apps installed in a specific team, see [Get the names and other details of apps installed in the specified team](/graph/api/team-list-installedapps#example-2-get-the-names-and-other-details-of-installed-apps).</span></span>

### <a name="check-your-app-for-added-rsc-permissions-in-a-chat"></a><span data-ttu-id="3f856-256">Verifique se o aplicativo tem permissões RSC adicionadas em um chat</span><span class="sxs-lookup"><span data-stu-id="3f856-256">Check your app for added RSC permissions in a chat</span></span>

> [!div class="checklist"]
>
>- <span data-ttu-id="3f856-257">Obter a ID do thread de chat do cliente Teams *Web.*</span><span class="sxs-lookup"><span data-stu-id="3f856-257">Get the chat thread ID from the Teams *web* client.</span></span>
> - <span data-ttu-id="3f856-258">No cliente Teams Web, selecione **Chat** na barra de nav da extrema esquerda.</span><span class="sxs-lookup"><span data-stu-id="3f856-258">In the Teams web client, select **Chat** from the far left nav bar.</span></span>
> - <span data-ttu-id="3f856-259">Selecione o chat em que o aplicativo está instalado no menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="3f856-259">Select the chat where the app is installed from the drop-down menu.</span></span>
> - <span data-ttu-id="3f856-260">Copie a URL da Web e salve a ID do thread de chat da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="3f856-260">Copy the web URL and save the chat thread ID from the string.</span></span>
<span data-ttu-id="3f856-261">![ID do thread de chat da URL da Web.](../../assets/images/chat-thread-id.png)</span><span class="sxs-lookup"><span data-stu-id="3f856-261">![Chat thread id from web URL.](../../assets/images/chat-thread-id.png)</span></span>
> - <span data-ttu-id="3f856-262">Faça **logoff Graph Explorer**.</span><span class="sxs-lookup"><span data-stu-id="3f856-262">Log into **Graph Explorer**.</span></span>
> - <span data-ttu-id="3f856-263">Faça uma **chamada GET** para o seguinte ponto de extremidade: `https://graph.microsoft.com/beta/chats/{chatId}/permissionGrants` .</span><span class="sxs-lookup"><span data-stu-id="3f856-263">Make a **GET** call to the following endpoint: `https://graph.microsoft.com/beta/chats/{chatId}/permissionGrants`.</span></span> <span data-ttu-id="3f856-264">O `clientAppId` campo na resposta será mapeado para o especificado no manifesto Teams `webApplicationInfo.id` aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3f856-264">The `clientAppId` field in the response will map to the `webApplicationInfo.id` specified in the Teams app manifest.</span></span>
  <span data-ttu-id="3f856-265">![Graph resposta do explorer à chamada GET para permissões RSC de chat.](../../assets/images/chat-graph-permissions.png)</span><span class="sxs-lookup"><span data-stu-id="3f856-265">![Graph explorer response to GET call for chat RSC permissions.](../../assets/images/chat-graph-permissions.png)</span></span>

<span data-ttu-id="3f856-266">Para obter informações sobre como obter detalhes sobre aplicativos instalados em um chat específico, consulte Obter os nomes e outros detalhes dos aplicativos instalados [no chat especificado](/graph/api/chat-list-installedapps#example-2-get-the-names-and-other-details-of-apps-installed-in-the-specified-chat).</span><span class="sxs-lookup"><span data-stu-id="3f856-266">For information about how to get details about apps installed in a specific chat, see [Get the names and other details of apps installed in the specified chat](/graph/api/chat-list-installedapps#example-2-get-the-names-and-other-details-of-apps-installed-in-the-specified-chat).</span></span>

## <a name="code-sample"></a><span data-ttu-id="3f856-267">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="3f856-267">Code sample</span></span>
| <span data-ttu-id="3f856-268">**Exemplo de nome**</span><span class="sxs-lookup"><span data-stu-id="3f856-268">**Sample name**</span></span> | <span data-ttu-id="3f856-269">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="3f856-269">**Description**</span></span> | <span data-ttu-id="3f856-270">**.NET**</span><span class="sxs-lookup"><span data-stu-id="3f856-270">**.NET**</span></span> |<span data-ttu-id="3f856-271">**Node.js**</span><span class="sxs-lookup"><span data-stu-id="3f856-271">**Node.js**</span></span> |
|-----------------|-----------------|----------------|----------------|
| <span data-ttu-id="3f856-272">Consentimento Específico do Recurso (RSC)</span><span class="sxs-lookup"><span data-stu-id="3f856-272">Resource Specific Consent (RSC)</span></span> | <span data-ttu-id="3f856-273">Use RSC para chamar Graph APIs.</span><span class="sxs-lookup"><span data-stu-id="3f856-273">Use RSC to call Graph APIs.</span></span> | [<span data-ttu-id="3f856-274">View</span><span class="sxs-lookup"><span data-stu-id="3f856-274">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-rsc/csharp)|[<span data-ttu-id="3f856-275">View</span><span class="sxs-lookup"><span data-stu-id="3f856-275">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-rsc/nodeJs)|



## <a name="see-also"></a><span data-ttu-id="3f856-276">Confira também</span><span class="sxs-lookup"><span data-stu-id="3f856-276">See also</span></span>
 
* [<span data-ttu-id="3f856-277">Testar permissões de consentimento específicas do recurso Teams</span><span class="sxs-lookup"><span data-stu-id="3f856-277">Test resource-specific consent permissions in Teams</span></span>](test-resource-specific-consent.md)
* [<span data-ttu-id="3f856-278">Consentimento específico do recurso no Microsoft Teams para administradores</span><span class="sxs-lookup"><span data-stu-id="3f856-278">Resource-specific consent in Microsoft Teams for admins</span></span>](/MicrosoftTeams/resource-specific-consent)


