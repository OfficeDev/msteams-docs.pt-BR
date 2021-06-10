---
title: Preparar o locatário do Microsoft 365
description: Como começar a usar Teams no Microsoft 365
ms.topic: how-to
localization_priority: Normal
keywords: Configurar Microsoft 365 locatário Teams carregamento
ms.openlocfilehash: 45d6dfb57fd2faa5bb303aac1dff86be142d0dc2
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019941"
---
# <a name="prepare-your-microsoft-365-tenant"></a><span data-ttu-id="e3e05-104">Preparar o locatário do Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="e3e05-104">Prepare your Microsoft 365 tenant</span></span>

<span data-ttu-id="e3e05-105">Microsoft 365 assinantes podem desenvolver aplicativos para Microsoft Teams com um dos seguintes planos:</span><span class="sxs-lookup"><span data-stu-id="e3e05-105">Microsoft 365 subscribers can develop apps for Microsoft Teams with one of the following plans:</span></span>

* <span data-ttu-id="e3e05-106">Básica</span><span class="sxs-lookup"><span data-stu-id="e3e05-106">Basic</span></span>
* <span data-ttu-id="e3e05-107">Padrão</span><span class="sxs-lookup"><span data-stu-id="e3e05-107">Standard</span></span>
* <span data-ttu-id="e3e05-108">Enterprise E1, E3 e E5</span><span class="sxs-lookup"><span data-stu-id="e3e05-108">Enterprise E1, E3, and E5</span></span>
* <span data-ttu-id="e3e05-109">Desenvolvedor</span><span class="sxs-lookup"><span data-stu-id="e3e05-109">Developer</span></span>
* <span data-ttu-id="e3e05-110">Education, Education Plus e Education E5</span><span class="sxs-lookup"><span data-stu-id="e3e05-110">Education, Education Plus, and Education E5</span></span>

> [!NOTE]
> * <span data-ttu-id="e3e05-111">Para obter mais informações sobre Microsoft 365 assinaturas, consulte [planos](https://products.office.com/business/compare-more-office-365-for-business-plans).</span><span class="sxs-lookup"><span data-stu-id="e3e05-111">For more information on Microsoft 365 subscriptions, see [plans](https://products.office.com/business/compare-more-office-365-for-business-plans).</span></span>
> * <span data-ttu-id="e3e05-112">Teams também está disponível para clientes que assinaram o E4 antes de sua [aposentadoria.](https://support.office.com//article/important-information-for-office-365-enterprise-e4-customers-f9572348-43a2-43fa-a3d8-3b6c9c042147)</span><span class="sxs-lookup"><span data-stu-id="e3e05-112">Teams is also available to customers who subscribed to E4 prior to its [retirement](https://support.office.com//article/important-information-for-office-365-enterprise-e4-customers-f9572348-43a2-43fa-a3d8-3b6c9c042147).</span></span>

## <a name="create-your-development-environment"></a><span data-ttu-id="e3e05-113">Criar seu ambiente de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="e3e05-113">Create your development environment</span></span>

<span data-ttu-id="e3e05-114">Se você não tiver uma conta Microsoft 365, você deve se inscrever para uma assinatura Microsoft 365 programa de [desenvolvedor.](https://developer.microsoft.com/microsoft-365/dev-program)</span><span class="sxs-lookup"><span data-stu-id="e3e05-114">If you do not have a Microsoft 365 account, you must sign up for a [Microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program) subscription.</span></span> <span data-ttu-id="e3e05-115">A assinatura é gratuita por 90 dias e continua a ser renovada desde que você a use para atividades de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="e3e05-115">The subscription is free for 90 days and continues to renew as long as you are using it for development activity.</span></span> <span data-ttu-id="e3e05-116">Se você tiver uma assinatura Visual Studio Enterprise ou Professional, ambos os programas incluirão uma assinatura Microsoft 365 [desenvolvedor gratuita.](https://aka.ms/MyVisualStudioBenefits)</span><span class="sxs-lookup"><span data-stu-id="e3e05-116">If you have a Visual Studio Enterprise or Professional subscription, both programs include a free Microsoft 365 [developer subscription](https://aka.ms/MyVisualStudioBenefits).</span></span> <span data-ttu-id="e3e05-117">Ele está ativo enquanto sua assinatura Visual Studio está ativa.</span><span class="sxs-lookup"><span data-stu-id="e3e05-117">It is active as long as your Visual Studio subscription is active.</span></span> <span data-ttu-id="e3e05-118">Para obter mais informações, [consulte configurar uma assinatura Microsoft 365 desenvolvedor.](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started)</span><span class="sxs-lookup"><span data-stu-id="e3e05-118">For more information, see [set up a Microsoft 365 developer subscription](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started).</span></span>

## <a name="enable-teams-for-your-organization"></a><span data-ttu-id="e3e05-119">Habilitar Teams para sua organização</span><span class="sxs-lookup"><span data-stu-id="e3e05-119">Enable Teams for your organization</span></span>

<span data-ttu-id="e3e05-120">Enable Teams for your organization and for more information, see [enableing Teams for your organization](/microsoftteams/enable-features-office-365).</span><span class="sxs-lookup"><span data-stu-id="e3e05-120">Enable Teams for your organization and for more information, see [enabling Teams for your organization](/microsoftteams/enable-features-office-365).</span></span>

## <a name="enable-custom-teams-apps-and-turn-on-custom-app-uploading"></a><span data-ttu-id="e3e05-121">Habilitar Teams aplicativos personalizados e ativar o carregamento personalizado de aplicativos</span><span class="sxs-lookup"><span data-stu-id="e3e05-121">Enable custom Teams apps and turn on custom app uploading</span></span>

<span data-ttu-id="e3e05-122">**Para ativar o carregamento ou sideload de aplicativos personalizados para seu locatário de desenvolvedor**</span><span class="sxs-lookup"><span data-stu-id="e3e05-122">**To turn on the custom app uploading or sideloading for your developer tenant**</span></span>

1. <span data-ttu-id="e3e05-123">Entre no centro [de administração Microsoft 365 com](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) suas credenciais de administrador.</span><span class="sxs-lookup"><span data-stu-id="e3e05-123">Sign in to [Microsoft 365 admin center](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) with your admin credentials.</span></span>

2. <span data-ttu-id="e3e05-124">Selecione **Mostrar todos os**  >  **Teams**.</span><span class="sxs-lookup"><span data-stu-id="e3e05-124">Select **Show All** > **Teams**.</span></span>

    ![Menu centro de administração](~/assets/images/prepare-test-tenant/admin-center.png)

    > [!Note]
    > <span data-ttu-id="e3e05-126">Pode levar até 24 horas para que a opção **Teams** apareça.</span><span class="sxs-lookup"><span data-stu-id="e3e05-126">It can take up to 24 hours for the **Teams** option to appear.</span></span> <span data-ttu-id="e3e05-127">Você pode [carregar seu aplicativo personalizado em um ambiente Teams para](/microsoftteams/upload-custom-apps#validate) teste e validação nesse momento.</span><span class="sxs-lookup"><span data-stu-id="e3e05-127">You can [upload your custom app to a Teams environment](/microsoftteams/upload-custom-apps#validate) for testing and validation in that time.</span></span>

3. <span data-ttu-id="e3e05-128">Navegue **até Teams configuração**  >  **de**  >  **aplicativos Global**.</span><span class="sxs-lookup"><span data-stu-id="e3e05-128">Navigate to **Teams apps** > **Setup Policies** > **Global**.</span></span>

   ![Ativar o exibição de sideload](~/assets/images/prepare-test-tenant/turn-on-sideload.png)

4. <span data-ttu-id="e3e05-130">Alterne **Upload aplicativos personalizados** para a **posição** On.</span><span class="sxs-lookup"><span data-stu-id="e3e05-130">Toggle **Upload custom apps** to the **On** position.</span></span>

5. <span data-ttu-id="e3e05-131">Selecione **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="e3e05-131">Select **Save**.</span></span> <span data-ttu-id="e3e05-132">Seu locatário de teste pode permitir o sideload de aplicativo personalizado.</span><span class="sxs-lookup"><span data-stu-id="e3e05-132">Your test tenant can permit custom app sideloading.</span></span>

    > [!Note]
    > <span data-ttu-id="e3e05-133">Pode levar até 24 horas para que o sideload seja ativo.</span><span class="sxs-lookup"><span data-stu-id="e3e05-133">It can take up to 24 hours for the sideloading to be active.</span></span> <span data-ttu-id="e3e05-134">Nesse ínterim, você pode usar **o upload para \<your tenant>** testar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e3e05-134">In the interim, you can use **upload for \<your tenant>** to test your app.</span></span> <span data-ttu-id="e3e05-135">Para carregar o arquivo .zip pacote do aplicativo, consulte [upload custom apps](/microsoftteams/upload-custom-apps#upload).</span><span class="sxs-lookup"><span data-stu-id="e3e05-135">To upload the .zip package file of the app, see [upload custom apps](/microsoftteams/upload-custom-apps#upload).</span></span>

    ![Upload de aplicativo](~/assets/images/prepare-test-tenant/upload-for-contoso.png)

<span data-ttu-id="e3e05-137">Para obter informações completas sobre como essas configurações interagem, consulte [manage custom app policies and settings in Teams](https://docs.microsoft.com/microsoftteams/teams-custom-app-policies-and-settings) and manage app setup policies in [Teams](https://docs.microsoft.com/microsoftteams/teams-app-setup-policies).</span><span class="sxs-lookup"><span data-stu-id="e3e05-137">For complete information on how these settings interact, see [manage custom app policies and settings in Teams](https://docs.microsoft.com/microsoftteams/teams-custom-app-policies-and-settings) and [manage app setup policies in Teams](https://docs.microsoft.com/microsoftteams/teams-app-setup-policies).</span></span>

## <a name="next-step"></a><span data-ttu-id="e3e05-138">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="e3e05-138">Next step</span></span>

> [!div class="nextstepaction"] 
> [<span data-ttu-id="e3e05-139">Escolher uma configuração de teste</span><span class="sxs-lookup"><span data-stu-id="e3e05-139">Choose a test setup</span></span>](~/concepts/build-and-test/debug.md)

