---
title: Preparar o locatário do Office 365
description: Como começar a usar o Microsoft Teams no Office 365
keywords: Configurar o carregamento do Office 365 locatário Teams
ms.openlocfilehash: 62cd640196631f50c72762253ff1bd75a143337d
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672816"
---
# <a name="prepare-your-office-365-tenant"></a><span data-ttu-id="a5fb4-104">Preparar o locatário do Office 365</span><span class="sxs-lookup"><span data-stu-id="a5fb4-104">Prepare your Office 365 tenant</span></span>

<span data-ttu-id="a5fb4-105">Para desenvolver aplicativos para o Microsoft Teams, você precisa ser um [cliente do Office 365 com um dos planos a seguir](https://products.office.com/business/compare-more-office-365-for-business-plans).</span><span class="sxs-lookup"><span data-stu-id="a5fb4-105">To develop apps for Microsoft Teams, you need to be an [Office 365 customer with one of the following plans](https://products.office.com/business/compare-more-office-365-for-business-plans).</span></span>

* <span data-ttu-id="a5fb4-106">Business Essentials</span><span class="sxs-lookup"><span data-stu-id="a5fb4-106">Business Essentials</span></span>
* <span data-ttu-id="a5fb4-107">Business Premium</span><span class="sxs-lookup"><span data-stu-id="a5fb4-107">Business Premium</span></span>
* <span data-ttu-id="a5fb4-108">Enterprise E1, E3 e e5</span><span class="sxs-lookup"><span data-stu-id="a5fb4-108">Enterprise E1, E3, and E5</span></span>
* <span data-ttu-id="a5fb4-109">Developer</span><span class="sxs-lookup"><span data-stu-id="a5fb4-109">Developer</span></span>
* <span data-ttu-id="a5fb4-110">Education, Education Plus e Education e5</span><span class="sxs-lookup"><span data-stu-id="a5fb4-110">Education, Education Plus, and Education E5</span></span>

<span data-ttu-id="a5fb4-111">O Microsoft Teams também estará disponível para clientes que compraram o E4 antes da sua aposentadoria.</span><span class="sxs-lookup"><span data-stu-id="a5fb4-111">Microsoft Teams will also be available to customers who purchased E4 prior to its retirement.</span></span>

## <a name="just-need-a-development-environment"></a><span data-ttu-id="a5fb4-112">Precisa apenas de um ambiente de desenvolvimento?</span><span class="sxs-lookup"><span data-stu-id="a5fb4-112">Just need a development environment?</span></span>

<span data-ttu-id="a5fb4-113">Se você não tiver uma conta do Office 365, você poderá se inscrever no [programa de desenvolvedor do office 365](https://dev.office.com/devprogram) para obter um 90 *gratuito* de dias (pode ser renovado por enquanto estiver usando-o para a atividade de desenvolvimento) para o locatário do desenvolvedor do Office 365.</span><span class="sxs-lookup"><span data-stu-id="a5fb4-113">If you don't currently have an Office 365 account, you can sign up for the [Office 365 Developer program](https://dev.office.com/devprogram) to get a *free* 90 days (can be renewed for as long as you're using it for development activity) Office 365 Developer Tenant.</span></span> <span data-ttu-id="a5fb4-114">Essa conta só pode ser usada para fins de teste.</span><span class="sxs-lookup"><span data-stu-id="a5fb4-114">This account can only be used for testing purposes.</span></span> <span data-ttu-id="a5fb4-115">Confira mais informações sobre [como configurar suas contas de teste](https://support.office.com/article/Add-users-individually-or-in-bulk-to-Office-365-Admin-Help-1970f7d6-03b5-442f-b385-5880b9c256ec?ui=en-US&rs=en-US&ad=US).</span><span class="sxs-lookup"><span data-stu-id="a5fb4-115">See more information on [setting up your test accounts](https://support.office.com/article/Add-users-individually-or-in-bulk-to-Office-365-Admin-Help-1970f7d6-03b5-442f-b385-5880b9c256ec?ui=en-US&rs=en-US&ad=US).</span></span>

## <a name="enable-microsoft-teams-for-your-organization"></a><span data-ttu-id="a5fb4-116">Habilitar o Microsoft Teams para sua organização</span><span class="sxs-lookup"><span data-stu-id="a5fb4-116">Enable Microsoft Teams for your organization</span></span>

<span data-ttu-id="a5fb4-117">Se o Microsoft Teams ainda não estiver habilitado para sua organização, você precisará fazer isso primeiro.</span><span class="sxs-lookup"><span data-stu-id="a5fb4-117">If Microsoft Teams is not yet enabled for your organization, you'll need to do that first.</span></span> <span data-ttu-id="a5fb4-118">Confira nossa orientação detalhada para [habilitar o Microsoft Teams para sua organização](/microsoftteams/how-to-roll-out-teams).</span><span class="sxs-lookup"><span data-stu-id="a5fb4-118">Take a look at our detailed guidance for [enabling Teams for your organization](/microsoftteams/how-to-roll-out-teams).</span></span>

## <a name="enable-custom-teams-apps-and-turn-on-custom-app-uploading"></a><span data-ttu-id="a5fb4-119">Habilitar aplicativos personalizados do Teams e ativar o carregamento de aplicativos personalizados</span><span class="sxs-lookup"><span data-stu-id="a5fb4-119">Enable custom Teams apps and turn on custom app uploading</span></span>

> <span data-ttu-id="a5fb4-120">Observação: se você estiver usando uma organização de desenvolvedor do O365 para criar seu aplicativo, essas configurações já devem estar configuradas para permitir que você crie, carregue e teste seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a5fb4-120">Note: If you're using an O365 Developer Organization to build your app, these settings should already be configured to allow you to build, upload and test your app.</span></span>

<span data-ttu-id="a5fb4-121">Há três configurações envolvidas na habilitação de aplicativos personalizados e carregamento de aplicativos personalizados:</span><span class="sxs-lookup"><span data-stu-id="a5fb4-121">There are three settings involved in enabling custom apps and custom app uploading:</span></span>

* <span data-ttu-id="a5fb4-122">**Configuração de aplicativo personalizado para toda** a organização-essa configuração habilita ou desabilita aplicativos personalizados para sua organização.</span><span class="sxs-lookup"><span data-stu-id="a5fb4-122">**Org-wide custom app setting** - This setting either enables or disables custom apps for your organization.</span></span> <span data-ttu-id="a5fb4-123">Ele precisa estar ativado.</span><span class="sxs-lookup"><span data-stu-id="a5fb4-123">It needs to be on.</span></span> 
* <span data-ttu-id="a5fb4-124">**Configuração de aplicativo personalizado de equipe** -essa configuração é para cada equipe individual no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="a5fb4-124">**Team custom app setting** - This setting is for each individual team inside Microsoft Teams.</span></span> <span data-ttu-id="a5fb4-125">Se você quiser instalar o aplicativo para uma equipe específica, será necessário que ele esteja ativado para essa equipe.</span><span class="sxs-lookup"><span data-stu-id="a5fb4-125">If you want to install your app for a specific team, this will need to be on for that team.</span></span>
* <span data-ttu-id="a5fb4-126">**Política de aplicativo personalizada de usuário** -este conjunto de configurações controla as permissões para um usuário individual.</span><span class="sxs-lookup"><span data-stu-id="a5fb4-126">**User custom app policy** - This set of settings controls the permissions for an individual user.</span></span> <span data-ttu-id="a5fb4-127">Será necessário habilitá-lo para pessoas que você deseja carregar aplicativos personalizados.</span><span class="sxs-lookup"><span data-stu-id="a5fb4-127">You'll need to enable this for individuals you want to upload custom apps.</span></span>

<span data-ttu-id="a5fb4-128">Para obter informações completas sobre como essas configurações interagem, confira [gerenciar políticas e configurações personalizadas de aplicativos no Microsoft Teams](/MicrosoftTeams/teams-custom-app-policies-and-settings).</span><span class="sxs-lookup"><span data-stu-id="a5fb4-128">For complete information on how these settings interact see [Manage custom app policies and settings in Microsoft Teams](/MicrosoftTeams/teams-custom-app-policies-and-settings).</span></span>
