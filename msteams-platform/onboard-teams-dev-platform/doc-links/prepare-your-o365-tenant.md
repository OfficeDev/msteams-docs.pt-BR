---
title: Preparar o ambiente de desenvolvimento do Microsoft Teams
description: Como configurar seu ambiente para desenvolver aplicativos do Teami
keywords: Configurar o desenvolvimento do ambiente de upload do Office 365 locatário Teams
ms.openlocfilehash: 701c6c110026007cf1670e783348bbdbe1aff498
ms.sourcegitcommit: 9fbc701a9a039ecdc360aefbe86df52b9c3593f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/12/2020
ms.locfileid: "46651835"
---
# <a name="prepare-your-development-environment"></a><span data-ttu-id="86944-104">Preparar seu ambiente de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="86944-104">Prepare your development environment</span></span>

<span data-ttu-id="86944-105">Se você é assinante do Office 365, pode desenvolver aplicativos para o Microsoft Teams com um dos seguintes [planos](https://products.office.com/business/compare-more-office-365-for-business-plans):</span><span class="sxs-lookup"><span data-stu-id="86944-105">If you are an Office 365 subscriber, you can develop apps for Microsoft Teams with one of the following [plans](https://products.office.com/business/compare-more-office-365-for-business-plans):</span></span>

* <span data-ttu-id="86944-106">Business Essentials</span><span class="sxs-lookup"><span data-stu-id="86944-106">Business Essentials</span></span>
* <span data-ttu-id="86944-107">Business Premium</span><span class="sxs-lookup"><span data-stu-id="86944-107">Business Premium</span></span>
* <span data-ttu-id="86944-108">Enterprise E1, E3 e e5</span><span class="sxs-lookup"><span data-stu-id="86944-108">Enterprise E1, E3, and E5</span></span>
* <span data-ttu-id="86944-109">Developer</span><span class="sxs-lookup"><span data-stu-id="86944-109">Developer</span></span>
* <span data-ttu-id="86944-110">Education, Education Plus e Education e5</span><span class="sxs-lookup"><span data-stu-id="86944-110">Education, Education Plus, and Education E5</span></span>

<span data-ttu-id="86944-111">O Microsoft Teams também estará disponível para clientes que se inscreveram no E4 antes da sua [aposentadoria](https://support.office.com//article/important-information-for-office-365-enterprise-e4-customers-f9572348-43a2-43fa-a3d8-3b6c9c042147).</span><span class="sxs-lookup"><span data-stu-id="86944-111">Microsoft Teams will also be available to customers who subscribed to E4 prior to its [retirement](https://support.office.com//article/important-information-for-office-365-enterprise-e4-customers-f9572348-43a2-43fa-a3d8-3b6c9c042147).</span></span>

## <a name="just-need-a-development-environment"></a><span data-ttu-id="86944-112">Precisa apenas de um ambiente de desenvolvimento?</span><span class="sxs-lookup"><span data-stu-id="86944-112">Just need a development environment?</span></span>

<span data-ttu-id="86944-113">Se você não tiver uma conta do Office 365, você poderá se inscrever em uma assinatura do [Microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program) .</span><span class="sxs-lookup"><span data-stu-id="86944-113">If you don't currently have an Office 365 account, you can sign up for a [Microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program) subscription.</span></span> <span data-ttu-id="86944-114">É *grátis* por 90 dias e será renovado continuamente, desde que você o esteja usando para a atividade de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="86944-114">It's *free* for 90 days and will continually renew as long as you're using it for development activity.</span></span> <span data-ttu-id="86944-115">Se você tiver uma assinatura do Visual Studio *Enterprise* ou *Professional* , ambos os programas incluirão uma [assinatura](https://aka.ms/MyVisualStudioBenefits)gratuita de desenvolvedor do Microsoft 365, ativa pela vida da sua assinatura do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="86944-115">If you have a Visual Studio *Enterprise* or *Professional* subscription, both programs include a free Microsoft 365 [developer subscription](https://aka.ms/MyVisualStudioBenefits), active for the life of your Visual Studio subscription.</span></span> <span data-ttu-id="86944-116">*Confira* [Configurar uma assinatura de desenvolvedor do Microsoft 365](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started).</span><span class="sxs-lookup"><span data-stu-id="86944-116">*See* [Set up a Microsoft 365 developer subscription](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started).</span></span>

## <a name="enable-microsoft-teams-for-your-organization"></a><span data-ttu-id="86944-117">Habilitar o Microsoft Teams para sua organização</span><span class="sxs-lookup"><span data-stu-id="86944-117">Enable Microsoft Teams for your organization</span></span>

<span data-ttu-id="86944-118">Se o Microsoft Teams não tiver sido habilitado para sua organização, você precisará fazer isso primeiro.</span><span class="sxs-lookup"><span data-stu-id="86944-118">If Microsoft Teams has not been enabled for your organization, you'll need to do that first.</span></span> <span data-ttu-id="86944-119">Confira nossa orientação detalhada para [habilitar o Microsoft Teams para sua organização](https://docs.microsoft.com/microsoftteams/enable-features-office-365).</span><span class="sxs-lookup"><span data-stu-id="86944-119">Take a look at our detailed guidance for [enabling Teams for your organization](https://docs.microsoft.com/microsoftteams/enable-features-office-365).</span></span>

## <a name="enable-custom-teams-apps-and-turn-on-custom-app-uploading"></a><span data-ttu-id="86944-120">Habilitar aplicativos personalizados do Teams e ativar o carregamento de aplicativos personalizados</span><span class="sxs-lookup"><span data-stu-id="86944-120">Enable custom Teams apps and turn on custom app uploading</span></span>

<span data-ttu-id="86944-121">Ative o aplicativo de Sideload personalizado para o seu locatário do desenvolvedor da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="86944-121">Turn on custom app sideloading for your developer tenant as follows:</span></span>

1. <span data-ttu-id="86944-122">Faça logon no [centro de administração do Microsoft 365](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) com sua credencial de administrador.</span><span class="sxs-lookup"><span data-stu-id="86944-122">Login to [Microsoft 365 admin center](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) with your admin credential.</span></span> 

2. <span data-ttu-id="86944-123">Selecione **Mostrar todas as**  -->  **equipes**.</span><span class="sxs-lookup"><span data-stu-id="86944-123">Select **Show All** --> **Teams**.</span></span> 

![imagem do menu de estouro de aplicativos](~/assets/images/prepare-test-tenant/admin-center.png)

3. <span data-ttu-id="86944-125">Navegar para políticas de instalação de **aplicativos do teams**  -->  **Setup Policies**  -->  **global (padrão para toda a organização)**</span><span class="sxs-lookup"><span data-stu-id="86944-125">Navigate to **Teams apps** --> **Setup Policies** --> **Global(Org-wide default)**</span></span>  

![imagem do menu de estouro de aplicativos](~/assets/images/prepare-test-tenant/turn-on-sideload.png)

4. <span data-ttu-id="86944-127">Alternar **carregar aplicativos personalizados** para a posição **ativado** .</span><span class="sxs-lookup"><span data-stu-id="86944-127">Toggle **upload custom apps** to the **on** position.</span></span>

<span data-ttu-id="86944-128">Isso é tudo.</span><span class="sxs-lookup"><span data-stu-id="86944-128">That's it!</span></span> <span data-ttu-id="86944-129">Agora, seu locatário de teste permitirá o Sideload de aplicativos personalizados.</span><span class="sxs-lookup"><span data-stu-id="86944-129">Your test tenant will now allow custom app sideloading.</span></span>

> [!Note] 
> <span data-ttu-id="86944-130">Pode levar até 24 horas antes de o Sideload ser habilitado.</span><span class="sxs-lookup"><span data-stu-id="86944-130">It can take up to 24 hours before sideloading is enabled.</span></span> <span data-ttu-id="86944-131">Durante o interim, você pode usar **upload \<your tenant> para** para testar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="86944-131">During interim, you can use **upload for \<your tenant>** to test your app.</span></span>

![imagem do menu de estouro de aplicativos](~/assets/images/prepare-test-tenant/upload-for-contoso.png)

<span data-ttu-id="86944-133">Para obter informações completas sobre como essas configurações interagem, *consulte*, [gerenciar políticas e configurações personalizadas de aplicativos no Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-custom-app-policies-and-settings) e [gerenciar políticas de instalação de aplicativos no Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-app-setup-policies).</span><span class="sxs-lookup"><span data-stu-id="86944-133">For complete information on how these settings interact, *See*, [Manage custom app policies and settings in Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-custom-app-policies-and-settings) and [Manage app setup policies in Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-app-setup-policies).</span></span>