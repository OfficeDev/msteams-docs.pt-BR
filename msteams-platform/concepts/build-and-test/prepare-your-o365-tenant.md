---
title: Prepare seu locatário do Microsoft 365
description: Como começar a usar o Teams no Microsoft 365
keywords: Configurar o carregamento de Microsoft 365 locatário Teams
ms.openlocfilehash: 67a0342a7e8605097eed53dd1b0bdf273d537c0e
ms.sourcegitcommit: d61f14053fc695bc1956bf50e83956613c19ccca
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/13/2020
ms.locfileid: "48452761"
---
# <a name="prepare-your-microsoft-365-tenant"></a><span data-ttu-id="a19ea-104">Prepare seu locatário do Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="a19ea-104">Prepare your Microsoft 365 tenant</span></span>

<span data-ttu-id="a19ea-105">Se você for assinante do Microsoft 365, poderá desenvolver aplicativos para o Microsoft Teams com um dos seguintes [planos](https://products.office.com/business/compare-more-office-365-for-business-plans):</span><span class="sxs-lookup"><span data-stu-id="a19ea-105">If you are a Microsoft 365 subscriber, you can develop apps for Microsoft Teams with one of the following [plans](https://products.office.com/business/compare-more-office-365-for-business-plans):</span></span>

* <span data-ttu-id="a19ea-106">Básica</span><span class="sxs-lookup"><span data-stu-id="a19ea-106">Basic</span></span>
* <span data-ttu-id="a19ea-107">Padrão</span><span class="sxs-lookup"><span data-stu-id="a19ea-107">Standard</span></span>
* <span data-ttu-id="a19ea-108">Enterprise E1, E3 e e5</span><span class="sxs-lookup"><span data-stu-id="a19ea-108">Enterprise E1, E3, and E5</span></span>
* <span data-ttu-id="a19ea-109">Developer</span><span class="sxs-lookup"><span data-stu-id="a19ea-109">Developer</span></span>
* <span data-ttu-id="a19ea-110">Education, Education Plus e Education e5</span><span class="sxs-lookup"><span data-stu-id="a19ea-110">Education, Education Plus, and Education E5</span></span>

<span data-ttu-id="a19ea-111">O Microsoft Teams também estará disponível para clientes que se inscreveram no E4 antes da sua [aposentadoria](https://support.office.com//article/important-information-for-office-365-enterprise-e4-customers-f9572348-43a2-43fa-a3d8-3b6c9c042147).</span><span class="sxs-lookup"><span data-stu-id="a19ea-111">Microsoft Teams will also be available to customers who subscribed to E4 prior to its [retirement](https://support.office.com//article/important-information-for-office-365-enterprise-e4-customers-f9572348-43a2-43fa-a3d8-3b6c9c042147).</span></span>

## <a name="just-need-a-development-environment"></a><span data-ttu-id="a19ea-112">Precisa apenas de um ambiente de desenvolvimento?</span><span class="sxs-lookup"><span data-stu-id="a19ea-112">Just need a development environment?</span></span>

<span data-ttu-id="a19ea-113">Se você não tiver uma conta do Microsoft 365, você pode se inscrever para uma assinatura do [microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program) .</span><span class="sxs-lookup"><span data-stu-id="a19ea-113">If you don't currently have a Microsoft 365 account, you can sign up for a [Microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program) subscription.</span></span> <span data-ttu-id="a19ea-114">É *grátis* por 90 dias e será renovado continuamente, desde que você o esteja usando para a atividade de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="a19ea-114">It's *free* for 90 days and will continually renew as long as you're using it for development activity.</span></span> <span data-ttu-id="a19ea-115">Se você tiver uma assinatura do Visual Studio *Enterprise* ou *Professional* , ambos os programas incluirão uma [assinatura](https://aka.ms/MyVisualStudioBenefits)gratuita de desenvolvedor do Microsoft 365, ativa pela vida da sua assinatura do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a19ea-115">If you have a Visual Studio *Enterprise* or *Professional* subscription, both programs include a free Microsoft 365 [developer subscription](https://aka.ms/MyVisualStudioBenefits), active for the life of your Visual Studio subscription.</span></span> <span data-ttu-id="a19ea-116">*Confira* [Configurar uma assinatura de desenvolvedor do Microsoft 365](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started).</span><span class="sxs-lookup"><span data-stu-id="a19ea-116">*See* [Set up a Microsoft 365 developer subscription](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started).</span></span>

## <a name="enable-microsoft-teams-for-your-organization"></a><span data-ttu-id="a19ea-117">Habilitar o Microsoft Teams para sua organização</span><span class="sxs-lookup"><span data-stu-id="a19ea-117">Enable Microsoft Teams for your organization</span></span> 

<span data-ttu-id="a19ea-118">Se o Microsoft Teams não tiver sido habilitado para sua organização, você precisará fazer isso primeiro.</span><span class="sxs-lookup"><span data-stu-id="a19ea-118">If Microsoft Teams has not been enabled for your organization, you'll need to do that first.</span></span> <span data-ttu-id="a19ea-119">Confira nossa orientação detalhada para [habilitar o Microsoft Teams para sua organização](/microsoftteams/enable-features-office-365).</span><span class="sxs-lookup"><span data-stu-id="a19ea-119">Take a look at our detailed guidance for [enabling Teams for your organization](/microsoftteams/enable-features-office-365).</span></span>

## <a name="enable-custom-teams-apps-and-turn-on-custom-app-uploading"></a><span data-ttu-id="a19ea-120">Habilitar aplicativos personalizados do Teams e ativar o carregamento de aplicativos personalizados</span><span class="sxs-lookup"><span data-stu-id="a19ea-120">Enable custom Teams apps and turn on custom app uploading</span></span>

<span data-ttu-id="a19ea-121">Ative o aplicativo de Sideload personalizado para o seu locatário do desenvolvedor da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="a19ea-121">Turn on custom app sideloading for your developer tenant as follows:</span></span>

1. <span data-ttu-id="a19ea-122">Faça logon no [centro de administração do Microsoft 365](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) com sua credencial de administrador.</span><span class="sxs-lookup"><span data-stu-id="a19ea-122">Login to [Microsoft 365 admin center](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) with your admin credential.</span></span> 

2. <span data-ttu-id="a19ea-123">Selecione **Mostrar todas as**  -->  **equipes**.</span><span class="sxs-lookup"><span data-stu-id="a19ea-123">Select **Show All** --> **Teams**.</span></span> 

![imagem do menu da central de administração](~/assets/images/prepare-test-tenant/admin-center.png)

> [!Note] 
> <span data-ttu-id="a19ea-125">Pode levar até 24 horas para que a opção "equipes" seja exibida.</span><span class="sxs-lookup"><span data-stu-id="a19ea-125">It can take up to 24 hours for the "Teams" option to appear.</span></span> <span data-ttu-id="a19ea-126">Durante o interim, você pode [carregar seu aplicativo personalizado para um ambiente do teams](/microsoftteams/upload-custom-apps#validate) para teste e validação.</span><span class="sxs-lookup"><span data-stu-id="a19ea-126">During interim, you can [Upload your custom app to a Teams environment](/microsoftteams/upload-custom-apps#validate) for testing and validation.</span></span>

3. <span data-ttu-id="a19ea-127">Navegar para políticas de instalação de **aplicativos do teams**  -->  **Setup Policies**  -->  **global (padrão para toda a organização)**</span><span class="sxs-lookup"><span data-stu-id="a19ea-127">Navigate to **Teams apps** --> **Setup Policies** --> **Global(Org-wide default)**</span></span>  

![ativar o modo de exibição Sideload](~/assets/images/prepare-test-tenant/turn-on-sideload.png)

4. <span data-ttu-id="a19ea-129">Alternar **carregar aplicativos personalizados** para a posição **ativado** .</span><span class="sxs-lookup"><span data-stu-id="a19ea-129">Toggle **upload custom apps** to the **on** position.</span></span>

<span data-ttu-id="a19ea-130">Isso é tudo.</span><span class="sxs-lookup"><span data-stu-id="a19ea-130">That's it!</span></span> <span data-ttu-id="a19ea-131">Agora, seu locatário de teste permitirá o Sideload de aplicativos personalizados.</span><span class="sxs-lookup"><span data-stu-id="a19ea-131">Your test tenant will now allow custom app sideloading.</span></span>

> [!Note] 
> <span data-ttu-id="a19ea-132">Pode levar até 24 horas antes de o Sideload ser habilitado.</span><span class="sxs-lookup"><span data-stu-id="a19ea-132">It can take up to 24 hours before sideloading is enabled.</span></span> <span data-ttu-id="a19ea-133">Durante o interim, você pode usar **upload \<your tenant> para** para testar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a19ea-133">During interim, you can use **upload for \<your tenant>** to test your app.</span></span>

![exibição do aplicativo updload](~/assets/images/prepare-test-tenant/upload-for-contoso.png)

<span data-ttu-id="a19ea-135">Para obter informações completas sobre como essas configurações interagem, *consulte*, [gerenciar políticas e configurações personalizadas de aplicativos no Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-custom-app-policies-and-settings) e [gerenciar políticas de instalação de aplicativos no Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-app-setup-policies).</span><span class="sxs-lookup"><span data-stu-id="a19ea-135">For complete information on how these settings interact, *See*, [Manage custom app policies and settings in Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-custom-app-policies-and-settings) and [Manage app setup policies in Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-app-setup-policies).</span></span>
