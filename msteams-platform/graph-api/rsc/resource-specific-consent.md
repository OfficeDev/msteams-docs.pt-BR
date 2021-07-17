---
title: Habilitar o consentimento específico do recurso Teams
description: Descreve o consentimento específico do recurso em Teams e como tirar proveito dele.
localization_priority: Normal
author: akjo
ms.author: lajanuar
ms.topic: reference
keywords: autorização do teams OAuth SSO AAD rsc Graph
ms.openlocfilehash: ce4076ff8cb9945f3b7dd1a7e809391292ec314a
ms.sourcegitcommit: c145d52b2d4daa7655e6c3ddfa739fa1beeb8d6a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2021
ms.locfileid: "53455217"
---
# <a name="resource-specific-consent"></a><span data-ttu-id="25c30-104">Consentimento específico do recurso</span><span class="sxs-lookup"><span data-stu-id="25c30-104">Resource-specific consent</span></span>

> [!NOTE]
> <span data-ttu-id="25c30-105">O consentimento específico do recurso para o escopo de chat está disponível apenas na [visualização do desenvolvedor](../../resources/dev-preview/developer-preview-intro.md) público.</span><span class="sxs-lookup"><span data-stu-id="25c30-105">Resource-specific consent for chat scope is available in [public developer preview](../../resources/dev-preview/developer-preview-intro.md) only.</span></span>

<span data-ttu-id="25c30-106">O RSC (consentimento específico de recursos) é uma integração de API Microsoft Teams e microsoft Graph que permite que seu aplicativo use pontos de extremidade da API para gerenciar recursos específicos, equipes ou chats, dentro de uma organização.</span><span class="sxs-lookup"><span data-stu-id="25c30-106">Resource-specific consent (RSC) is a Microsoft Teams and Microsoft Graph API integration that enables your app to use API endpoints to manage specific resources, either teams or chats, within an organization.</span></span> <span data-ttu-id="25c30-107">O modelo de permissões RSC permite que *proprietários* de equipe e proprietários de *chat* concedam consentimento para que um aplicativo acesse e modifique os dados de uma equipe e os dados de um chat, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="25c30-107">The RSC permissions model enables *team owners* and *chat owners* to grant consent for an application to access and modify a team's data and a chat's data, respectively.</span></span>

## <a name="resource-specific-permissions"></a><span data-ttu-id="25c30-108">Permissões específicas de recursos</span><span class="sxs-lookup"><span data-stu-id="25c30-108">Resource-specific permissions</span></span>

<span data-ttu-id="25c30-109">As permissões granulares, Teams RSC específicas definem o que um aplicativo pode fazer em um recurso específico.</span><span class="sxs-lookup"><span data-stu-id="25c30-109">The granular, Teams-specific, RSC permissions define what an application can do within a specific resource.</span></span>

### <a name="resource-specific-permissions-for-a-team"></a><span data-ttu-id="25c30-110">Permissões específicas de recursos para uma equipe</span><span class="sxs-lookup"><span data-stu-id="25c30-110">Resource-specific permissions for a team</span></span>

|<span data-ttu-id="25c30-111">Permissão do aplicativo</span><span class="sxs-lookup"><span data-stu-id="25c30-111">Application permission</span></span>| <span data-ttu-id="25c30-112">Action</span><span class="sxs-lookup"><span data-stu-id="25c30-112">Action</span></span> |
| ----- | ----- |
|<span data-ttu-id="25c30-113">TeamSettings.Read.Group</span><span class="sxs-lookup"><span data-stu-id="25c30-113">TeamSettings.Read.Group</span></span> | <span data-ttu-id="25c30-114">Obter as configurações dessa equipe.</span><span class="sxs-lookup"><span data-stu-id="25c30-114">Get this team's settings.</span></span>|
|<span data-ttu-id="25c30-115">TeamSettings.ReadWrite.Group</span><span class="sxs-lookup"><span data-stu-id="25c30-115">TeamSettings.ReadWrite.Group</span></span>|<span data-ttu-id="25c30-116">Atualize as configurações dessa equipe.</span><span class="sxs-lookup"><span data-stu-id="25c30-116">Update this team's settings.</span></span>|
|<span data-ttu-id="25c30-117">ChannelSettings.Read.Group</span><span class="sxs-lookup"><span data-stu-id="25c30-117">ChannelSettings.Read.Group</span></span>|<span data-ttu-id="25c30-118">Obter nomes de canal dessa equipe, descrições de canal e configurações de canal.</span><span class="sxs-lookup"><span data-stu-id="25c30-118">Get this team's channel names, channel descriptions, and channel settings.</span></span>|
|<span data-ttu-id="25c30-119">ChannelSettings.ReadWrite.Group</span><span class="sxs-lookup"><span data-stu-id="25c30-119">ChannelSettings.ReadWrite.Group</span></span>|<span data-ttu-id="25c30-120">Atualize os nomes de canal dessa equipe, descrições de canal e configurações de canal.</span><span class="sxs-lookup"><span data-stu-id="25c30-120">Update this team's channel names, channel descriptions, and channel settings.</span></span>|
|<span data-ttu-id="25c30-121">Channel.Create.Group</span><span class="sxs-lookup"><span data-stu-id="25c30-121">Channel.Create.Group</span></span>|<span data-ttu-id="25c30-122">Criar canais nesta equipe.</span><span class="sxs-lookup"><span data-stu-id="25c30-122">Create channels in this team.</span></span> |
|<span data-ttu-id="25c30-123">Channel.Delete.Group</span><span class="sxs-lookup"><span data-stu-id="25c30-123">Channel.Delete.Group</span></span>|<span data-ttu-id="25c30-124">Exclua canais nesta equipe.</span><span class="sxs-lookup"><span data-stu-id="25c30-124">Delete channels in this team.</span></span> |
|<span data-ttu-id="25c30-125">ChannelMessage.Read.Group</span><span class="sxs-lookup"><span data-stu-id="25c30-125">ChannelMessage.Read.Group</span></span> |<span data-ttu-id="25c30-126">Receba as mensagens de canal dessa equipe.</span><span class="sxs-lookup"><span data-stu-id="25c30-126">Get this team's channel messages.</span></span> |
|<span data-ttu-id="25c30-127">TeamsAppInstallation.Read.Group</span><span class="sxs-lookup"><span data-stu-id="25c30-127">TeamsAppInstallation.Read.Group</span></span>|<span data-ttu-id="25c30-128">Obter uma lista dos aplicativos instalados dessa equipe.</span><span class="sxs-lookup"><span data-stu-id="25c30-128">Get a list of this team's installed apps.</span></span>|
|<span data-ttu-id="25c30-129">TeamsTab.Read.Group</span><span class="sxs-lookup"><span data-stu-id="25c30-129">TeamsTab.Read.Group</span></span>|<span data-ttu-id="25c30-130">Obter uma lista das guias dessa equipe.</span><span class="sxs-lookup"><span data-stu-id="25c30-130">Get a list of this team's tabs.</span></span>|
|<span data-ttu-id="25c30-131">TeamsTab.Create.Group</span><span class="sxs-lookup"><span data-stu-id="25c30-131">TeamsTab.Create.Group</span></span>|<span data-ttu-id="25c30-132">Criar guias nesta equipe.</span><span class="sxs-lookup"><span data-stu-id="25c30-132">Create tabs in this team.</span></span> |
|<span data-ttu-id="25c30-133">TeamsTab.ReadWrite.Group</span><span class="sxs-lookup"><span data-stu-id="25c30-133">TeamsTab.ReadWrite.Group</span></span>|<span data-ttu-id="25c30-134">Atualize as guias desta equipe.</span><span class="sxs-lookup"><span data-stu-id="25c30-134">Update this team's tabs.</span></span> |
|<span data-ttu-id="25c30-135">TeamsTab.Delete.Group</span><span class="sxs-lookup"><span data-stu-id="25c30-135">TeamsTab.Delete.Group</span></span>|<span data-ttu-id="25c30-136">Excluir as guias dessa equipe.</span><span class="sxs-lookup"><span data-stu-id="25c30-136">Delete this team's tabs.</span></span> |
|<span data-ttu-id="25c30-137">TeamMember.Read.Group</span><span class="sxs-lookup"><span data-stu-id="25c30-137">TeamMember.Read.Group</span></span>|<span data-ttu-id="25c30-138">Obter os membros dessa equipe.</span><span class="sxs-lookup"><span data-stu-id="25c30-138">Get this team's members.</span></span> |

<span data-ttu-id="25c30-139">Para obter mais detalhes, consulte permissões de consentimento [específicas do](/graph/permissions-reference#teams-resource-specific-consent-permissions)recurso de equipe .</span><span class="sxs-lookup"><span data-stu-id="25c30-139">For more details, see [team resource-specific consent permissions](/graph/permissions-reference#teams-resource-specific-consent-permissions).</span></span>

### <a name="resource-specific-permissions-for-a-chat"></a><span data-ttu-id="25c30-140">Permissões específicas de recursos para um chat</span><span class="sxs-lookup"><span data-stu-id="25c30-140">Resource-specific permissions for a chat</span></span>

<span data-ttu-id="25c30-141">A tabela a seguir fornece permissões específicas de recursos para um chat:</span><span class="sxs-lookup"><span data-stu-id="25c30-141">The following table provides resource-specific permissions for a chat:</span></span>

|<span data-ttu-id="25c30-142">Permissão do aplicativo</span><span class="sxs-lookup"><span data-stu-id="25c30-142">Application permission</span></span>| <span data-ttu-id="25c30-143">Action</span><span class="sxs-lookup"><span data-stu-id="25c30-143">Action</span></span> |
| ----- | ----- |
| <span data-ttu-id="25c30-144">ChatSettings.Read.Chat</span><span class="sxs-lookup"><span data-stu-id="25c30-144">ChatSettings.Read.Chat</span></span>         | <span data-ttu-id="25c30-145">Obter as configurações desse chat.</span><span class="sxs-lookup"><span data-stu-id="25c30-145">Get this chat's settings.</span></span>                                    |
| <span data-ttu-id="25c30-146">ChatSettings.ReadWrite.Chat</span><span class="sxs-lookup"><span data-stu-id="25c30-146">ChatSettings.ReadWrite.Chat</span></span>    | <span data-ttu-id="25c30-147">Atualize as configurações desse chat.</span><span class="sxs-lookup"><span data-stu-id="25c30-147">Update this chat's settings.</span></span>                          |
| <span data-ttu-id="25c30-148">ChatMessage.Read.Chat</span><span class="sxs-lookup"><span data-stu-id="25c30-148">ChatMessage.Read.Chat</span></span>          | <span data-ttu-id="25c30-149">Receba as mensagens desse chat.</span><span class="sxs-lookup"><span data-stu-id="25c30-149">Get this chat's messages.</span></span>                                    |
| <span data-ttu-id="25c30-150">ChatMember.Read.Chat</span><span class="sxs-lookup"><span data-stu-id="25c30-150">ChatMember.Read.Chat</span></span>           | <span data-ttu-id="25c30-151">Obter membros desse chat.</span><span class="sxs-lookup"><span data-stu-id="25c30-151">Get this chat's members.</span></span>                                     |
| <span data-ttu-id="25c30-152">Chat.Manage.Chat</span><span class="sxs-lookup"><span data-stu-id="25c30-152">Chat.Manage.Chat</span></span>               | <span data-ttu-id="25c30-153">Gerenciar este chat</span><span class="sxs-lookup"><span data-stu-id="25c30-153">Manage this chat.</span></span>                                             |
| <span data-ttu-id="25c30-154">TeamsTab.Read.Chat</span><span class="sxs-lookup"><span data-stu-id="25c30-154">TeamsTab.Read.Chat</span></span>             | <span data-ttu-id="25c30-155">Obter as guias desse chat.</span><span class="sxs-lookup"><span data-stu-id="25c30-155">Get this chat's tabs.</span></span>                                        |
| <span data-ttu-id="25c30-156">TeamsTab.Create.Chat</span><span class="sxs-lookup"><span data-stu-id="25c30-156">TeamsTab.Create.Chat</span></span>           | <span data-ttu-id="25c30-157">Criar as guias neste chat.</span><span class="sxs-lookup"><span data-stu-id="25c30-157">Create tabs in this chat.</span></span>                                     |
| <span data-ttu-id="25c30-158">TeamsTab.Delete.Chat</span><span class="sxs-lookup"><span data-stu-id="25c30-158">TeamsTab.Delete.Chat</span></span>           | <span data-ttu-id="25c30-159">Exclua as guias deste chat.</span><span class="sxs-lookup"><span data-stu-id="25c30-159">Delete this chat's tabs.</span></span>                                      |
| <span data-ttu-id="25c30-160">TeamsTab.ReadWrite.Chat</span><span class="sxs-lookup"><span data-stu-id="25c30-160">TeamsTab.ReadWrite.Chat</span></span>        | <span data-ttu-id="25c30-161">Gerenciar as guias deste chat.</span><span class="sxs-lookup"><span data-stu-id="25c30-161">Manage this chat's tabs.</span></span>                                      |
| <span data-ttu-id="25c30-162">TeamsAppInstallation.Read.Chat</span><span class="sxs-lookup"><span data-stu-id="25c30-162">TeamsAppInstallation.Read.Chat</span></span> | <span data-ttu-id="25c30-163">Obter quais aplicativos estão instalados neste chat.</span><span class="sxs-lookup"><span data-stu-id="25c30-163">Get which apps are installed in this chat.</span></span>                   |
| <span data-ttu-id="25c30-164">OnlineMeeting.ReadBasic.Chat</span><span class="sxs-lookup"><span data-stu-id="25c30-164">OnlineMeeting.ReadBasic.Chat</span></span>   | <span data-ttu-id="25c30-165">Obter propriedades básicas, como nome, agendamento, organizador e link de associação de uma reunião associada a esse chat.</span><span class="sxs-lookup"><span data-stu-id="25c30-165">Get basic properties, such as name, schedule, organizer, and join link of a meeting associated with this chat.</span></span> |

<span data-ttu-id="25c30-166">Para obter mais detalhes, consulte [chat resource-specific consent permissions](/graph/permissions-reference#chat-resource-specific-consent-permissions).</span><span class="sxs-lookup"><span data-stu-id="25c30-166">For more details, see [chat resource-specific consent permissions](/graph/permissions-reference#chat-resource-specific-consent-permissions).</span></span>

> [!NOTE]
> <span data-ttu-id="25c30-167">Permissões específicas de recursos estão disponíveis apenas para Teams aplicativos instalados no cliente Teams e atualmente não fazem parte do portal Azure Active Directory (AAD).</span><span class="sxs-lookup"><span data-stu-id="25c30-167">Resource-specific permissions are only available to Teams apps installed on the Teams client and are currently not part of the Azure Active Directory (AAD) portal.</span></span>

## <a name="enable-rsc-in-your-application"></a><span data-ttu-id="25c30-168">Habilitar o RSC em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="25c30-168">Enable RSC in your application</span></span>

1. <span data-ttu-id="25c30-169">[Configurar configurações de consentimento no portal do AAD](#configure-consent-settings-in-the-aad-portal).</span><span class="sxs-lookup"><span data-stu-id="25c30-169">[Configure consent settings in the AAD portal](#configure-consent-settings-in-the-aad-portal).</span></span>
    1. <span data-ttu-id="25c30-170">[Configure as configurações de consentimento do proprietário do grupo para o RSC em uma equipe.](#configure-group-owner-consent-settings-for-rsc-in-a-team)</span><span class="sxs-lookup"><span data-stu-id="25c30-170">[Configure group owner consent settings for RSC in a team](#configure-group-owner-consent-settings-for-rsc-in-a-team).</span></span>
    1. <span data-ttu-id="25c30-171">[Configurar configurações de consentimento do usuário para RSC em um chat](#configure-user-consent-settings-for-rsc-in-a-chat).</span><span class="sxs-lookup"><span data-stu-id="25c30-171">[Configure user consent settings for RSC in a chat](#configure-user-consent-settings-for-rsc-in-a-chat).</span></span>
1. <span data-ttu-id="25c30-172">[Registre seu aplicativo com plataforma de identidade da Microsoft usando o portal do AAD](#register-your-app-with-microsoft-identity-platform-using-the-aad-portal).</span><span class="sxs-lookup"><span data-stu-id="25c30-172">[Register your app with Microsoft identity platform using the AAD portal](#register-your-app-with-microsoft-identity-platform-using-the-aad-portal).</span></span>
1. <span data-ttu-id="25c30-173">[Revise suas permissões de aplicativo no portal do AAD.](#review-your-application-permissions-in-the-aad-portal)</span><span class="sxs-lookup"><span data-stu-id="25c30-173">[Review your application permissions in the AAD portal](#review-your-application-permissions-in-the-aad-portal).</span></span>
1. <span data-ttu-id="25c30-174">[Obtenha um token de acesso da plataforma de identidade](#obtain-an-access-token-from-the-microsoft-identity-platform).</span><span class="sxs-lookup"><span data-stu-id="25c30-174">[Obtain an access token from the identity platform](#obtain-an-access-token-from-the-microsoft-identity-platform).</span></span>
1. <span data-ttu-id="25c30-175">[Atualize seu Teams de aplicativo .](#update-your-teams-app-manifest)</span><span class="sxs-lookup"><span data-stu-id="25c30-175">[Update your Teams app manifest](#update-your-teams-app-manifest).</span></span>
1. <span data-ttu-id="25c30-176">[Instale seu aplicativo diretamente no Teams](#sideload-your-app-in-teams).</span><span class="sxs-lookup"><span data-stu-id="25c30-176">[Install your app directly in Teams](#sideload-your-app-in-teams).</span></span>
1. <span data-ttu-id="25c30-177">[Verifique se o aplicativo tem permissões RSC adicionadas.](#check-your-app-for-added-rsc-permissions)</span><span class="sxs-lookup"><span data-stu-id="25c30-177">[Check your app for added RSC permissions](#check-your-app-for-added-rsc-permissions).</span></span>
    1. <span data-ttu-id="25c30-178">[Verifique se o aplicativo adicionou permissões RSC em uma equipe](#check-your-app-for-added-rsc-permissions-in-a-team).</span><span class="sxs-lookup"><span data-stu-id="25c30-178">[Check your app for added RSC permissions in a team](#check-your-app-for-added-rsc-permissions-in-a-team).</span></span>
    1. <span data-ttu-id="25c30-179">[Verifique se o aplicativo adicionou permissões RSC em um chat](#check-your-app-for-added-rsc-permissions-in-a-chat).</span><span class="sxs-lookup"><span data-stu-id="25c30-179">[Check your app for added RSC permissions in a chat](#check-your-app-for-added-rsc-permissions-in-a-chat).</span></span>

## <a name="configure-consent-settings-in-the-aad-portal"></a><span data-ttu-id="25c30-180">Configurar configurações de consentimento no portal do AAD</span><span class="sxs-lookup"><span data-stu-id="25c30-180">Configure consent settings in the AAD portal</span></span>

### <a name="configure-group-owner-consent-settings-for-rsc-in-a-team"></a><span data-ttu-id="25c30-181">Configurar configurações de consentimento do proprietário do grupo para RSC em uma equipe</span><span class="sxs-lookup"><span data-stu-id="25c30-181">Configure group owner consent settings for RSC in a team</span></span>

<span data-ttu-id="25c30-182">Você pode habilitar ou [desabilitar o consentimento do](/azure/active-directory/manage-apps/configure-user-consent-groups?tabs=azure-portal) proprietário do grupo diretamente no portal do Azure:</span><span class="sxs-lookup"><span data-stu-id="25c30-182">You can enable or disable [group owner consent](/azure/active-directory/manage-apps/configure-user-consent-groups?tabs=azure-portal) directly within the Azure portal:</span></span>

1. <span data-ttu-id="25c30-183">Entre no [portal do Azure](https://portal.azure.com) como Administrador [Global ou Administrador de Empresa.](/azure/active-directory/roles/permissions-reference#global-administrator&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="25c30-183">Sign in to the [Azure portal](https://portal.azure.com) as a [Global Administrator or Company Administrator](/azure/active-directory/roles/permissions-reference#global-administrator&preserve-view=true).</span></span>
1. <span data-ttu-id="25c30-184">Selecione **Azure Active Directory**  >  **Enterprise**  >  **aplicativos Consentimento e permissões**  >  [**Configurações de consentimento do usuário.**](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConsentPoliciesMenuBlade/UserSettings)</span><span class="sxs-lookup"><span data-stu-id="25c30-184">Select **Azure Active Directory** > **Enterprise applications** > **Consent and permissions** > [**User consent settings**](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConsentPoliciesMenuBlade/UserSettings).</span></span>
1. <span data-ttu-id="25c30-185">Habilitar, desabilitar ou limitar o consentimento do usuário com o controle rotulado consentimento do proprietário do grupo **para aplicativos que acessam dados.**</span><span class="sxs-lookup"><span data-stu-id="25c30-185">Enable, disable, or limit user consent with the control labeled **Group owner consent for apps accessing data**.</span></span> <span data-ttu-id="25c30-186">O padrão é **Permitir consentimento do proprietário do grupo para todos os proprietários do grupo.**</span><span class="sxs-lookup"><span data-stu-id="25c30-186">The default is **Allow group owner consent for all group owners**.</span></span> <span data-ttu-id="25c30-187">Para que o proprietário da equipe instale um aplicativo usando o RSC, o consentimento do proprietário do grupo deve ser habilitado para esse usuário.</span><span class="sxs-lookup"><span data-stu-id="25c30-187">For a team owner to install an app using RSC, group owner consent must be enabled for that user.</span></span>

    ![Configuração da equipe RSC do Azure](../../assets/images/azure-rsc-team-configuration.png)

<span data-ttu-id="25c30-189">Além disso, você pode habilitar ou desabilitar o consentimento do proprietário do grupo usando o PowerShell, siga as etapas descritas em configurar o consentimento do proprietário do grupo [usando o PowerShell](/azure/active-directory/manage-apps/configure-user-consent-groups?tabs=azure-powershell).</span><span class="sxs-lookup"><span data-stu-id="25c30-189">In addition, you can enable or disable group owner consent using PowerShell, follow the steps outlined in [configure group owner consent using PowerShell](/azure/active-directory/manage-apps/configure-user-consent-groups?tabs=azure-powershell).</span></span>

### <a name="configure-user-consent-settings-for-rsc-in-a-chat"></a><span data-ttu-id="25c30-190">Configurar configurações de consentimento do usuário para RSC em um chat</span><span class="sxs-lookup"><span data-stu-id="25c30-190">Configure user consent settings for RSC in a chat</span></span>

<span data-ttu-id="25c30-191">Você pode habilitar ou [desabilitar o consentimento do](/azure/active-directory/manage-apps/configure-user-consent?tabs=azure-portal) usuário diretamente no portal do Azure:</span><span class="sxs-lookup"><span data-stu-id="25c30-191">You can enable or disable [user consent](/azure/active-directory/manage-apps/configure-user-consent?tabs=azure-portal) directly within the Azure portal:</span></span>

1. <span data-ttu-id="25c30-192">Entre no [portal do Azure](https://portal.azure.com) como Administrador [Global ou Administrador de Empresa.](/azure/active-directory/roles/permissions-reference#global-administrator&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="25c30-192">Sign in to the [Azure portal](https://portal.azure.com) as a [Global Administrator or Company Administrator](/azure/active-directory/roles/permissions-reference#global-administrator&preserve-view=true).</span></span>
1. <span data-ttu-id="25c30-193">Selecione **Azure Active Directory**  >  **Enterprise**  >  **aplicativos Consentimento e permissões**  >  [**Configurações de consentimento do usuário.**](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConsentPoliciesMenuBlade/UserSettings)</span><span class="sxs-lookup"><span data-stu-id="25c30-193">Select **Azure Active Directory** > **Enterprise applications** > **Consent and permissions** > [**User consent settings**](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConsentPoliciesMenuBlade/UserSettings).</span></span>
1. <span data-ttu-id="25c30-194">Habilitar, desabilitar ou limitar o consentimento do usuário com o controle rotulado **Consentimento do usuário para aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="25c30-194">Enable, disable, or limit user consent with the control labeled **User consent for applications**.</span></span> <span data-ttu-id="25c30-195">O padrão é **Permitir consentimento do usuário para aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="25c30-195">The default is **Allow user consent for apps**.</span></span> <span data-ttu-id="25c30-196">Para um membro do chat instalar um aplicativo usando o RSC, o consentimento do usuário deve ser habilitado para esse usuário.</span><span class="sxs-lookup"><span data-stu-id="25c30-196">For a chat member to install an app using RSC, user consent must be enabled for that user.</span></span>

    ![Configuração de chat RSC do Azure](../../assets/images/azure-rsc-chat-configuration.png)

<span data-ttu-id="25c30-198">Além disso, você pode habilitar ou desabilitar o consentimento do usuário usando o PowerShell, siga as etapas descritas em configurar o consentimento do usuário [usando o PowerShell](/azure/active-directory/manage-apps/configure-user-consent?tabs=azure-powershell).</span><span class="sxs-lookup"><span data-stu-id="25c30-198">In addition, you can enable or disable user consent using PowerShell, follow the steps outlined in [configure user consent using PowerShell](/azure/active-directory/manage-apps/configure-user-consent?tabs=azure-powershell).</span></span>

## <a name="register-your-app-with-microsoft-identity-platform-using-the-aad-portal"></a><span data-ttu-id="25c30-199">Registrar seu aplicativo com plataforma de identidade da Microsoft usando o portal do AAD</span><span class="sxs-lookup"><span data-stu-id="25c30-199">Register your app with Microsoft identity platform using the AAD portal</span></span>

<span data-ttu-id="25c30-200">O portal do AAD fornece uma plataforma central para você registrar e configurar seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="25c30-200">The AAD portal provides a central platform for you to register and configure your apps.</span></span> <span data-ttu-id="25c30-201">Seu aplicativo deve ser registrado no portal do AAD para se integrar à plataforma de identidade e chamar as APIs Graph Microsoft.</span><span class="sxs-lookup"><span data-stu-id="25c30-201">Your app must be registered in the AAD portal to integrate with the identity platform and call Microsoft Graph APIs.</span></span> <span data-ttu-id="25c30-202">Para obter mais informações, [consulte register an application with the identity platform](/graph/auth-register-app-v2).</span><span class="sxs-lookup"><span data-stu-id="25c30-202">For more information, see [register an application with the identity platform](/graph/auth-register-app-v2).</span></span>

> [!WARNING]
> <span data-ttu-id="25c30-203">Uma ID do aplicativo AAD não deve ser compartilhada em vários Teams aplicativos.</span><span class="sxs-lookup"><span data-stu-id="25c30-203">An AAD app ID must not be shared across multiple Teams apps.</span></span> <span data-ttu-id="25c30-204">Deve haver um mapeamento 1:1 entre um aplicativo Teams e um aplicativo AAD.</span><span class="sxs-lookup"><span data-stu-id="25c30-204">There must be a 1:1 mapping between a Teams app and an AAD app.</span></span> <span data-ttu-id="25c30-205">As tentativas de instalar vários Teams que estão associados à mesma ID do aplicativo AAD causarão falhas de instalação ou tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="25c30-205">Attempts to install multiple Teams apps which are associated with the same AAD app ID will cause installation or runtime failures.</span></span>

## <a name="review-your-application-permissions-in-the-aad-portal"></a><span data-ttu-id="25c30-206">Revisar as permissões do aplicativo no portal do AAD</span><span class="sxs-lookup"><span data-stu-id="25c30-206">Review your application permissions in the AAD portal</span></span>

1. <span data-ttu-id="25c30-207">Vá até a página **Registros** do Aplicativo Inicial e selecione seu aplicativo  >   RSC.</span><span class="sxs-lookup"><span data-stu-id="25c30-207">Go to the **Home** > **App registrations** page and select your RSC app.</span></span>
1. <span data-ttu-id="25c30-208">Escolha **permissões de API** no painel esquerdo e vá até a lista de permissões **configuradas** para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="25c30-208">Choose **API permissions** from the left pane and go through the list of **Configured permissions** for your app.</span></span> <span data-ttu-id="25c30-209">Se seu aplicativo fizer apenas chamadas de API RSC Graph, exclua todas as permissões nessa página.</span><span class="sxs-lookup"><span data-stu-id="25c30-209">If your app only makes RSC Graph API calls, delete all the permissions on that page.</span></span> <span data-ttu-id="25c30-210">Se seu aplicativo também fizer chamadas não RSC, mantenha essas permissões conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="25c30-210">If your app also makes non-RSC calls, keep those permissions as required.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="25c30-211">O portal do AAD não pode ser usado para solicitar permissões RSC.</span><span class="sxs-lookup"><span data-stu-id="25c30-211">The AAD portal cannot be used to request RSC permissions.</span></span> <span data-ttu-id="25c30-212">As permissões RSC atualmente são exclusivas Teams aplicativos instalados no cliente Teams e são declaradas no arquivo JSON (manifesto do aplicativo Teams).</span><span class="sxs-lookup"><span data-stu-id="25c30-212">RSC permissions are currently exclusive to Teams applications installed in the Teams client and are declared in the Teams app manifest (JSON) file.</span></span>

## <a name="obtain-an-access-token-from-the-microsoft-identity-platform"></a><span data-ttu-id="25c30-213">Obtenha um token de acesso do plataforma de identidade da Microsoft</span><span class="sxs-lookup"><span data-stu-id="25c30-213">Obtain an access token from the Microsoft identity platform</span></span>

<span data-ttu-id="25c30-214">Para fazer Graph de API, você deve obter um token de acesso para seu aplicativo a partir da plataforma de identidade.</span><span class="sxs-lookup"><span data-stu-id="25c30-214">To make Graph API calls, you must obtain an access token for your app from the identity platform.</span></span> <span data-ttu-id="25c30-215">Para que seu aplicativo possa obter um token da plataforma de identidade, ele deve ser registrado no portal do AAD.</span><span class="sxs-lookup"><span data-stu-id="25c30-215">Before your app can get a token from the identity platform, it must be registered in the AAD portal.</span></span> <span data-ttu-id="25c30-216">O token de acesso contém informações sobre seu aplicativo e as permissões que ele possui para os recursos e APIs disponíveis no Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="25c30-216">The access token contains information about your app and the permissions it has for the resources and APIs available through Microsoft Graph.</span></span>

<span data-ttu-id="25c30-217">Você deve ter os seguintes valores do processo de registro do AAD para recuperar um token de acesso da plataforma de identidade:</span><span class="sxs-lookup"><span data-stu-id="25c30-217">You must have the following values from the AAD registration process to retrieve an access token from the identity platform:</span></span>

- <span data-ttu-id="25c30-218">A **ID do aplicativo** atribuída pelo portal de registro do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="25c30-218">The **Application ID** assigned by the app registration portal.</span></span> <span data-ttu-id="25c30-219">Se seu aplicativo oferece suporte a SSO (login único), você deve usar a mesma ID do Aplicativo para seu aplicativo e SSO.</span><span class="sxs-lookup"><span data-stu-id="25c30-219">If your app supports single sign-on (SSO) you must use the same Application ID for your app and SSO.</span></span>
- <span data-ttu-id="25c30-220">O **segredo/senha do cliente** ou um par de chaves públicas ou privadas que é **Certificate**.</span><span class="sxs-lookup"><span data-stu-id="25c30-220">The **Client secret/password** or a public or private key pair that is **Certificate**.</span></span> <span data-ttu-id="25c30-221">Isso não é necessário para aplicativos nativos.</span><span class="sxs-lookup"><span data-stu-id="25c30-221">This is not required for native apps.</span></span>
- <span data-ttu-id="25c30-222">Um **URI de redirecionamento** ou URL de resposta para seu aplicativo receber respostas do AAD.</span><span class="sxs-lookup"><span data-stu-id="25c30-222">A **Redirect URI** or reply URL for your app to receive responses from AAD.</span></span>

<span data-ttu-id="25c30-223">Para obter mais informações, [consulte obter acesso em nome de um usuário](/graph/auth-v2-user?view=graph-rest-1.0#3-get-a-token&preserve-view=true) e obter acesso sem um [usuário](/graph/auth-v2-service).</span><span class="sxs-lookup"><span data-stu-id="25c30-223">For more information, see [get access on behalf of a user](/graph/auth-v2-user?view=graph-rest-1.0#3-get-a-token&preserve-view=true) and [get access without a user](/graph/auth-v2-service).</span></span>

## <a name="update-your-teams-app-manifest"></a><span data-ttu-id="25c30-224">Atualizar seu manifesto Teams aplicativo</span><span class="sxs-lookup"><span data-stu-id="25c30-224">Update your Teams app manifest</span></span>

<span data-ttu-id="25c30-225">As permissões RSC são declaradas no arquivo JSON do manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="25c30-225">The RSC permissions are declared in your app manifest JSON file.</span></span> <span data-ttu-id="25c30-226">Adicione uma [chave webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) ao manifesto do aplicativo com os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="25c30-226">Add a [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) key to your app manifest with the following values:</span></span>

|<span data-ttu-id="25c30-227">Nome</span><span class="sxs-lookup"><span data-stu-id="25c30-227">Name</span></span>| <span data-ttu-id="25c30-228">Tipo</span><span class="sxs-lookup"><span data-stu-id="25c30-228">Type</span></span> | <span data-ttu-id="25c30-229">Descrição</span><span class="sxs-lookup"><span data-stu-id="25c30-229">Description</span></span>|
|---|---|---|
|`id` |<span data-ttu-id="25c30-230">String</span><span class="sxs-lookup"><span data-stu-id="25c30-230">String</span></span> |<span data-ttu-id="25c30-231">Sua ID do aplicativo AAD.</span><span class="sxs-lookup"><span data-stu-id="25c30-231">Your AAD app ID.</span></span> <span data-ttu-id="25c30-232">Para obter mais informações, [consulte register your app in the AAD portal](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-using-the-aad-portal).</span><span class="sxs-lookup"><span data-stu-id="25c30-232">For more information, see [register your app in the AAD portal](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-using-the-aad-portal).</span></span>|
|`resource`|<span data-ttu-id="25c30-233">String</span><span class="sxs-lookup"><span data-stu-id="25c30-233">String</span></span>| <span data-ttu-id="25c30-234">Este campo não tem operação no RSC, mas deve ser adicionado e ter um valor para evitar uma resposta de erro; qualquer cadeia de caracteres fará.</span><span class="sxs-lookup"><span data-stu-id="25c30-234">This field has no operation in RSC, but must be added and have a value to avoid an error response; any string will do.</span></span>|
|`applicationPermissions`|<span data-ttu-id="25c30-235">Matriz de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="25c30-235">Array of strings</span></span>|<span data-ttu-id="25c30-236">Permissões RSC para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="25c30-236">RSC permissions for  your app.</span></span> <span data-ttu-id="25c30-237">Para obter mais informações, consulte [permissões específicas do recurso](resource-specific-consent.md#resource-specific-permissions).</span><span class="sxs-lookup"><span data-stu-id="25c30-237">For more information, see [resource-specific permissions](resource-specific-consent.md#resource-specific-permissions).</span></span>|

>
> [!IMPORTANT]
> <span data-ttu-id="25c30-238">As permissões não RSC são armazenadas no portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="25c30-238">Non-RSC permissions are stored in the Azure portal.</span></span> <span data-ttu-id="25c30-239">Não os adicione ao manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="25c30-239">Do not add them to the app manifest.</span></span>
>

### <a name="example-for-rsc-in-a-team"></a><span data-ttu-id="25c30-240">Exemplo de RSC em uma equipe</span><span class="sxs-lookup"><span data-stu-id="25c30-240">Example for RSC in a team</span></span>

```json
"webApplicationInfo": {
    "id": "XXxxXXXXX-XxXX-xXXX-XXxx-XXXXXXXxxxXX",
    "resource": "https://RscBasedStoreApp",
    "applicationPermissions": [
      "TeamSettings.Read.Group",
      "ChannelMessage.Read.Group",
      "TeamSettings.ReadWrite.Group",
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

### <a name="example-for-rsc-in-a-chat"></a><span data-ttu-id="25c30-241">Exemplo de RSC em um chat</span><span class="sxs-lookup"><span data-stu-id="25c30-241">Example for RSC in a chat</span></span>

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

> [!NOTE]
> <span data-ttu-id="25c30-242">Se o aplicativo tiver o objetivo de dar suporte à instalação em escopos de equipe e chat, as permissões de equipe e de chat poderão ser especificadas no mesmo manifesto em `applicationPermissions` .</span><span class="sxs-lookup"><span data-stu-id="25c30-242">If the app is meant to support installation in both team and chat scopes, then both team and chat permissions can be specified in the same manifest under `applicationPermissions`.</span></span>

## <a name="sideload-your-app-in-teams"></a><span data-ttu-id="25c30-243">Fazer sideload do aplicativo Teams</span><span class="sxs-lookup"><span data-stu-id="25c30-243">Sideload your app in Teams</span></span>

<span data-ttu-id="25c30-244">Se o administrador Teams permite carregamentos de aplicativos personalizados, você pode [fazer sideload](~/concepts/deploy-and-publish/apps-upload.md) do aplicativo diretamente em uma equipe ou chat específico.</span><span class="sxs-lookup"><span data-stu-id="25c30-244">If your Teams admin allows custom app uploads, you can [sideload your app](~/concepts/deploy-and-publish/apps-upload.md) directly to a specific team or chat.</span></span>

## <a name="check-your-app-for-added-rsc-permissions"></a><span data-ttu-id="25c30-245">Verifique se o aplicativo tem permissões RSC adicionadas</span><span class="sxs-lookup"><span data-stu-id="25c30-245">Check your app for added RSC permissions</span></span>

> [!IMPORTANT]
> <span data-ttu-id="25c30-246">As permissões RSC não são atribuídas a um usuário.</span><span class="sxs-lookup"><span data-stu-id="25c30-246">The RSC permissions are not attributed to a user.</span></span> <span data-ttu-id="25c30-247">As chamadas são feitas com permissões de aplicativo, não permissões delegadas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="25c30-247">Calls are made with app permissions, not user delegated permissions.</span></span> <span data-ttu-id="25c30-248">O aplicativo pode ter permissão para executar ações que o usuário não pode, como excluir uma guia. Você deve revisar a intenção do proprietário da equipe ou do proprietário do chat para seu uso antes de fazer chamadas de API RSC.</span><span class="sxs-lookup"><span data-stu-id="25c30-248">The app can be allowed to perform actions that the user cannot, such as deleting a tab. You must review the team owner's or chat owner's intent for your use before making RSC API calls.</span></span> <span data-ttu-id="25c30-249">Para obter mais informações, [consulte Microsoft Teams visão geral da API](/graph/teams-concept-overview).</span><span class="sxs-lookup"><span data-stu-id="25c30-249">For more information, see [Microsoft Teams API overview](/graph/teams-concept-overview).</span></span>

<span data-ttu-id="25c30-250">Depois que o aplicativo for instalado em um recurso, você poderá usar o [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer) para exibir as permissões que foram concedidas ao aplicativo no recurso.</span><span class="sxs-lookup"><span data-stu-id="25c30-250">After the app has been installed to a resource, you can use [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer) to view the permissions that have been granted to the app in the resource.</span></span>

### <a name="check-your-app-for-added-rsc-permissions-in-a-team"></a><span data-ttu-id="25c30-251">Verifique se o aplicativo adicionou permissões RSC em uma equipe</span><span class="sxs-lookup"><span data-stu-id="25c30-251">Check your app for added RSC permissions in a team</span></span>

1. <span data-ttu-id="25c30-252">Obter groupId da **equipe Teams.**</span><span class="sxs-lookup"><span data-stu-id="25c30-252">Get the team's **groupId** from Teams.</span></span>
1. <span data-ttu-id="25c30-253">Em Teams, selecione **Teams** no painel mais à esquerda.</span><span class="sxs-lookup"><span data-stu-id="25c30-253">In Teams, select **Teams** from the leftmost pane.</span></span>
1. <span data-ttu-id="25c30-254">Selecione a equipe onde o aplicativo deve ser instalado.</span><span class="sxs-lookup"><span data-stu-id="25c30-254">Select the team where the app is to be installed.</span></span>
1. <span data-ttu-id="25c30-255">Selecione as releições &#x25CF;&#x25CF;&#x25CF; para essa equipe.</span><span class="sxs-lookup"><span data-stu-id="25c30-255">Select the ellipses &#x25CF;&#x25CF;&#x25CF; for that team.</span></span>
1. <span data-ttu-id="25c30-256">Selecione **Obter link para a equipe** no menu suspenso da equipe.</span><span class="sxs-lookup"><span data-stu-id="25c30-256">Select **Get link to team** from the team drop-down menu.</span></span>
1. <span data-ttu-id="25c30-257">Copie e salve o **valor groupId** da caixa de diálogo **Obter um link** para a caixa de diálogo pop-up da equipe.</span><span class="sxs-lookup"><span data-stu-id="25c30-257">Copy and save the **groupId** value from the **Get a link to the team** pop-up dialog box.</span></span>
1. <span data-ttu-id="25c30-258">Entre no **Graph Explorer**.</span><span class="sxs-lookup"><span data-stu-id="25c30-258">Sign in to **Graph Explorer**.</span></span>
1. <span data-ttu-id="25c30-259">Faça uma **chamada GET** para este ponto de extremidade: `https://graph.microsoft.com/beta/teams/{teamGroupId}/permissionGrants` .</span><span class="sxs-lookup"><span data-stu-id="25c30-259">Make a **GET** call to this endpoint: `https://graph.microsoft.com/beta/teams/{teamGroupId}/permissionGrants`.</span></span> <span data-ttu-id="25c30-260">O `clientAppId` campo na resposta será mapeado para o especificado no manifesto Teams `webApplicationInfo.id` aplicativo.</span><span class="sxs-lookup"><span data-stu-id="25c30-260">The `clientAppId` field in the response will map to the `webApplicationInfo.id` specified in the Teams app manifest.</span></span>

    ![Graph resposta do explorer a get call for team RSC permissions](../../assets/images/team-graph-permissions.png)

<span data-ttu-id="25c30-262">Para obter mais informações sobre como obter detalhes dos aplicativos instalados em uma equipe específica, consulte obter os nomes e outros detalhes dos aplicativos instalados na [equipe especificada](/graph/api/team-list-installedapps#example-2-get-the-names-and-other-details-of-installed-apps).</span><span class="sxs-lookup"><span data-stu-id="25c30-262">For more information on how to get details of the apps installed in a specific team, see [get the names and other details of apps installed in the specified team](/graph/api/team-list-installedapps#example-2-get-the-names-and-other-details-of-installed-apps).</span></span>

### <a name="check-your-app-for-added-rsc-permissions-in-a-chat"></a><span data-ttu-id="25c30-263">Verifique se o aplicativo tem permissões RSC adicionadas em um chat</span><span class="sxs-lookup"><span data-stu-id="25c30-263">Check your app for added RSC permissions in a chat</span></span>

1. <span data-ttu-id="25c30-264">Obter a ID do thread de chat do cliente Teams *Web.*</span><span class="sxs-lookup"><span data-stu-id="25c30-264">Get the chat thread ID from the Teams *web* client.</span></span>
1. <span data-ttu-id="25c30-265">No cliente Teams Web, selecione **Chat** no painel mais à esquerda.</span><span class="sxs-lookup"><span data-stu-id="25c30-265">In the Teams web client, select **Chat** from the leftmost pane.</span></span>
1. <span data-ttu-id="25c30-266">Selecione o chat em que o aplicativo está instalado no menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="25c30-266">Select the chat where the app is installed from the drop-down menu.</span></span>
1. <span data-ttu-id="25c30-267">Copie a URL da Web e salve a ID do thread de chat da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="25c30-267">Copy the web URL and save the chat thread ID from the string.</span></span>

    ![ID do thread de chat da URL da Web](../../assets/images/chat-thread-id.png)

1. <span data-ttu-id="25c30-269">Entre no **Graph Explorer**.</span><span class="sxs-lookup"><span data-stu-id="25c30-269">Sign in to **Graph Explorer**.</span></span>
1. <span data-ttu-id="25c30-270">Faça uma **chamada GET** para o seguinte ponto de extremidade: `https://graph.microsoft.com/beta/chats/{chatId}/permissionGrants` .</span><span class="sxs-lookup"><span data-stu-id="25c30-270">Make a **GET** call to the following endpoint: `https://graph.microsoft.com/beta/chats/{chatId}/permissionGrants`.</span></span> <span data-ttu-id="25c30-271">O `clientAppId` campo na resposta será mapeado para o especificado no manifesto Teams `webApplicationInfo.id` aplicativo.</span><span class="sxs-lookup"><span data-stu-id="25c30-271">The `clientAppId` field in the response will map to the `webApplicationInfo.id` specified in the Teams app manifest.</span></span>

    ![Graph de explorer para obter chamada para permissões RSC de chat](../../assets/images/chat-graph-permissions.png)

<span data-ttu-id="25c30-273">Para obter mais informações sobre como obter detalhes dos aplicativos instalados em um chat específico, consulte obter os nomes e outros detalhes dos aplicativos instalados no [chat especificado.](/graph/api/chat-list-installedapps#example-2-get-the-names-and-other-details-of-apps-installed-in-the-specified-chat)</span><span class="sxs-lookup"><span data-stu-id="25c30-273">For more information on how to get details of apps installed in a specific chat, see [get the names and other details of apps installed in the specified chat](/graph/api/chat-list-installedapps#example-2-get-the-names-and-other-details-of-apps-installed-in-the-specified-chat).</span></span>

## <a name="code-sample"></a><span data-ttu-id="25c30-274">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="25c30-274">Code sample</span></span>

| <span data-ttu-id="25c30-275">**Nome do exemplo**</span><span class="sxs-lookup"><span data-stu-id="25c30-275">**Sample name**</span></span> | <span data-ttu-id="25c30-276">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="25c30-276">**Description**</span></span> | <span data-ttu-id="25c30-277">**.NET**</span><span class="sxs-lookup"><span data-stu-id="25c30-277">**.NET**</span></span> |<span data-ttu-id="25c30-278">**Node.js**</span><span class="sxs-lookup"><span data-stu-id="25c30-278">**Node.js**</span></span> |
|-----------------|-----------------|----------------|----------------|
| <span data-ttu-id="25c30-279">Resource-Specific Consentimento (RSC)</span><span class="sxs-lookup"><span data-stu-id="25c30-279">Resource-Specific Consent (RSC)</span></span> | <span data-ttu-id="25c30-280">Use RSC para chamar Graph APIs.</span><span class="sxs-lookup"><span data-stu-id="25c30-280">Use RSC to call Graph APIs.</span></span> | [<span data-ttu-id="25c30-281">Exibir</span><span class="sxs-lookup"><span data-stu-id="25c30-281">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-rsc/csharp)|[<span data-ttu-id="25c30-282">Exibir</span><span class="sxs-lookup"><span data-stu-id="25c30-282">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-rsc/nodeJs)|

## <a name="see-also"></a><span data-ttu-id="25c30-283">Confira também</span><span class="sxs-lookup"><span data-stu-id="25c30-283">See also</span></span>
 
* [<span data-ttu-id="25c30-284">Testar permissões de consentimento específicas do recurso Teams</span><span class="sxs-lookup"><span data-stu-id="25c30-284">Test resource-specific consent permissions in Teams</span></span>](test-resource-specific-consent.md)
* [<span data-ttu-id="25c30-285">Consentimento específico do recurso no Microsoft Teams para administradores</span><span class="sxs-lookup"><span data-stu-id="25c30-285">Resource-specific consent in Microsoft Teams for admins</span></span>](/MicrosoftTeams/resource-specific-consent)
