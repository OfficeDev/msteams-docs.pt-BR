---
title: Preparar seu locatário do Microsoft 365
description: Como começar a usar o Teams no Microsoft 365
ms.topic: how-to
keywords: Configurar o carregamento do Microsoft 365 tenant Teams
ms.openlocfilehash: aa7f994744f8b1c62aa32122a5006cfa0f22d391
ms.sourcegitcommit: 5b3ba227c2e5e6f7a2c629961993f168da6a504d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2021
ms.locfileid: "51634745"
---
# <a name="prepare-your-microsoft-365-tenant"></a><span data-ttu-id="c059f-104">Preparar seu locatário do Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="c059f-104">Prepare your Microsoft 365 tenant</span></span>

<span data-ttu-id="c059f-105">Os assinantes do Microsoft 365 podem desenvolver aplicativos para o Microsoft Teams com um dos seguintes planos:</span><span class="sxs-lookup"><span data-stu-id="c059f-105">Microsoft 365 subscribers can develop apps for Microsoft Teams with one of the following plans:</span></span>

* <span data-ttu-id="c059f-106">Básica</span><span class="sxs-lookup"><span data-stu-id="c059f-106">Basic</span></span>
* <span data-ttu-id="c059f-107">Padrão</span><span class="sxs-lookup"><span data-stu-id="c059f-107">Standard</span></span>
* <span data-ttu-id="c059f-108">Enterprise E1, E3 e E5</span><span class="sxs-lookup"><span data-stu-id="c059f-108">Enterprise E1, E3, and E5</span></span>
* <span data-ttu-id="c059f-109">Developer</span><span class="sxs-lookup"><span data-stu-id="c059f-109">Developer</span></span>
* <span data-ttu-id="c059f-110">Education, Education Plus e Education E5</span><span class="sxs-lookup"><span data-stu-id="c059f-110">Education, Education Plus, and Education E5</span></span>

> [!NOTE]
> <span data-ttu-id="c059f-111">Para obter mais informações sobre assinaturas do Microsoft 365, consulte [planos](https://products.office.com/business/compare-more-office-365-for-business-plans).</span><span class="sxs-lookup"><span data-stu-id="c059f-111">For more information on Microsoft 365 subscriptions, see [plans](https://products.office.com/business/compare-more-office-365-for-business-plans).</span></span>
> 
> <span data-ttu-id="c059f-112">O Microsoft Teams também está disponível para clientes que assinaram o E4 antes de sua [aposentadoria.](https://support.office.com//article/important-information-for-office-365-enterprise-e4-customers-f9572348-43a2-43fa-a3d8-3b6c9c042147)</span><span class="sxs-lookup"><span data-stu-id="c059f-112">Microsoft Teams is also available to customers who subscribed to E4 prior to its [retirement](https://support.office.com//article/important-information-for-office-365-enterprise-e4-customers-f9572348-43a2-43fa-a3d8-3b6c9c042147).</span></span>

## <a name="create-your-development-environment"></a><span data-ttu-id="c059f-113">Criar seu ambiente de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="c059f-113">Create your development environment</span></span>

<span data-ttu-id="c059f-114">Se você não tiver uma conta do Microsoft 365, deverá se inscrever para uma assinatura do Programa de Desenvolvedor [do Microsoft 365.](https://developer.microsoft.com/microsoft-365/dev-program)</span><span class="sxs-lookup"><span data-stu-id="c059f-114">If you do not have a Microsoft 365 account, you must sign up for a [Microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program) subscription.</span></span> <span data-ttu-id="c059f-115">A assinatura é gratuita por 90 dias e continua a ser renovada desde que você a use para atividades de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="c059f-115">The subscription is free for 90 days and continues to renew as long as you are using it for development activity.</span></span> <span data-ttu-id="c059f-116">Se você tiver uma assinatura Visual Studio Enterprise ou Professional, ambos os programas incluirão uma assinatura gratuita de [desenvolvedor do](https://aka.ms/MyVisualStudioBenefits)Microsoft 365 .</span><span class="sxs-lookup"><span data-stu-id="c059f-116">If you have a Visual Studio Enterprise or Professional subscription, both programs include a free Microsoft 365 [developer subscription](https://aka.ms/MyVisualStudioBenefits).</span></span> <span data-ttu-id="c059f-117">Ele está ativo enquanto sua assinatura Visual Studio está ativa.</span><span class="sxs-lookup"><span data-stu-id="c059f-117">It is active for as long as your Visual Studio subscription is active.</span></span> <span data-ttu-id="c059f-118">Para obter mais informações, consulte Configurar uma assinatura de desenvolvedor do [Microsoft 365](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started).</span><span class="sxs-lookup"><span data-stu-id="c059f-118">For more inforamtion, see [Set up a Microsoft 365 developer subscription](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started).</span></span>

## <a name="enable-microsoft-teams-for-your-organization"></a><span data-ttu-id="c059f-119">Habilitar o Microsoft Teams para sua organização</span><span class="sxs-lookup"><span data-stu-id="c059f-119">Enable Microsoft Teams for your organization</span></span>

<span data-ttu-id="c059f-120">Habilita o Microsoft Teams para sua organização e confira nossas diretrizes detalhadas para habilitar o [Teams para sua organização.](/microsoftteams/enable-features-office-365)</span><span class="sxs-lookup"><span data-stu-id="c059f-120">Enable Microsoft Teams for your organization and take a look at our detailed guidance for [enabling Teams for your organization](/microsoftteams/enable-features-office-365).</span></span>

## <a name="enable-custom-teams-apps-and-turn-on-custom-app-uploading"></a><span data-ttu-id="c059f-121">Habilitar aplicativos personalizados do Teams e ativar o carregamento personalizado de aplicativos</span><span class="sxs-lookup"><span data-stu-id="c059f-121">Enable custom Teams apps and turn on custom app uploading</span></span>

<span data-ttu-id="c059f-122">**Para ativar o carregamento ou sideload de aplicativos personalizados para seu locatário de desenvolvedor**</span><span class="sxs-lookup"><span data-stu-id="c059f-122">**To turn on the custom app uploading or sideloading for your developer tenant**</span></span>

1. <span data-ttu-id="c059f-123">Entre no Centro de administração do [Microsoft 365](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) com suas credenciais de administrador.</span><span class="sxs-lookup"><span data-stu-id="c059f-123">Sign in to [Microsoft 365 admin center](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) with your admin credentials.</span></span>

2. <span data-ttu-id="c059f-124">Selecione **Mostrar todas as**  >  **Equipes**.</span><span class="sxs-lookup"><span data-stu-id="c059f-124">Select **Show All** > **Teams**.</span></span>

    ![imagem do menu do centro de administração](~/assets/images/prepare-test-tenant/admin-center.png)

    > [!Note]
    > <span data-ttu-id="c059f-126">Pode levar até 24 horas para que a **opção Teams** apareça.</span><span class="sxs-lookup"><span data-stu-id="c059f-126">It can take up to 24 hours for the **Teams** option to appear.</span></span> <span data-ttu-id="c059f-127">Você pode [carregar seu aplicativo personalizado em um](/microsoftteams/upload-custom-apps#validate) ambiente do Teams para testes e validação nesse momento.</span><span class="sxs-lookup"><span data-stu-id="c059f-127">You can [upload your custom app to a Teams environment](/microsoftteams/upload-custom-apps#validate) for testing and validation in that time.</span></span>

3. <span data-ttu-id="c059f-128">Navegue até **Políticas de Configuração de Aplicativos** do Teams  >    >  **Global**.</span><span class="sxs-lookup"><span data-stu-id="c059f-128">Navigate to **Teams apps** > **Setup Policies** > **Global**.</span></span>

   ![ativar o sideload view](~/assets/images/prepare-test-tenant/turn-on-sideload.png)

4. <span data-ttu-id="c059f-130">Alterne **o carregamento de aplicativos** personalizados para a **posição** on.</span><span class="sxs-lookup"><span data-stu-id="c059f-130">Toggle **upload custom apps** to the **on** position.</span></span>

5. <span data-ttu-id="c059f-131">Selecione **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="c059f-131">Select **Save**.</span></span>
   <span data-ttu-id="c059f-132">Seu locatário de teste pode permitir o sideload de aplicativo personalizado.</span><span class="sxs-lookup"><span data-stu-id="c059f-132">Your test tenant can permit custom app sideloading.</span></span>

    > [!Note]
    > <span data-ttu-id="c059f-133">Pode levar até 24 horas para que o sideload seja ativo.</span><span class="sxs-lookup"><span data-stu-id="c059f-133">It can take up to 24 hours for the sideloading to be active.</span></span> <span data-ttu-id="c059f-134">Durante o ínterim, você pode usar **o upload para \<your tenant>** testar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c059f-134">During interim, you can use **upload for \<your tenant>** to test your app.</span></span>

    ![exibição de aplicativo de updload](~/assets/images/prepare-test-tenant/upload-for-contoso.png)

<span data-ttu-id="c059f-136">Para obter informações completas sobre como essas configurações interagem, consulte [Manage custom app policies and settings in Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-custom-app-policies-and-settings) and Manage app setup policies in Microsoft [Teams](https://docs.microsoft.com/microsoftteams/teams-app-setup-policies).</span><span class="sxs-lookup"><span data-stu-id="c059f-136">For complete information on how these settings interact, see [Manage custom app policies and settings in Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-custom-app-policies-and-settings) and [Manage app setup policies in Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-app-setup-policies).</span></span>

## <a name="next-step"></a><span data-ttu-id="c059f-137">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="c059f-137">Next step</span></span>

> [!div class="nextstepaction"] 
> [<span data-ttu-id="c059f-138">Escolher uma instalação de teste</span><span class="sxs-lookup"><span data-stu-id="c059f-138">Choose a test setup</span></span>](~/concepts/build-and-test/debug.md)
> 


