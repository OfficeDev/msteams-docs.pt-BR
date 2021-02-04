---
title: Preparar seu locatário do Microsoft 365
description: Como começar a usar o Teams no Microsoft 365
ms.topic: how-to
keywords: Configurar o carregamento do Microsoft 365 tenant Teams
ms.openlocfilehash: 50765271b93edd380d1c23672289b618baf1d346
ms.sourcegitcommit: 55a4246e62d69d631a63bdd33de34f1b62cc0132
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2021
ms.locfileid: "50093940"
---
# <a name="prepare-your-microsoft-365-tenant"></a><span data-ttu-id="b0074-104">Preparar seu locatário do Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="b0074-104">Prepare your Microsoft 365 tenant</span></span>

<span data-ttu-id="b0074-105">Se você for assinante do Microsoft 365, poderá desenvolver aplicativos para o Microsoft Teams com um dos seguintes [planos:](https://products.office.com/business/compare-more-office-365-for-business-plans)</span><span class="sxs-lookup"><span data-stu-id="b0074-105">If you are a Microsoft 365 subscriber, you can develop apps for Microsoft Teams with one of the following [plans](https://products.office.com/business/compare-more-office-365-for-business-plans):</span></span>

* <span data-ttu-id="b0074-106">Básica</span><span class="sxs-lookup"><span data-stu-id="b0074-106">Basic</span></span>
* <span data-ttu-id="b0074-107">Padrão</span><span class="sxs-lookup"><span data-stu-id="b0074-107">Standard</span></span>
* <span data-ttu-id="b0074-108">Enterprise E1, E3 e E5</span><span class="sxs-lookup"><span data-stu-id="b0074-108">Enterprise E1, E3, and E5</span></span>
* <span data-ttu-id="b0074-109">Developer</span><span class="sxs-lookup"><span data-stu-id="b0074-109">Developer</span></span>
* <span data-ttu-id="b0074-110">Education, Education Plus e Education E5</span><span class="sxs-lookup"><span data-stu-id="b0074-110">Education, Education Plus, and Education E5</span></span>

<span data-ttu-id="b0074-111">O Microsoft Teams também estará disponível para os clientes que assinaram o E4 antes da sua [baixa.](https://support.office.com//article/important-information-for-office-365-enterprise-e4-customers-f9572348-43a2-43fa-a3d8-3b6c9c042147)</span><span class="sxs-lookup"><span data-stu-id="b0074-111">Microsoft Teams will also be available to customers who subscribed to E4 prior to its [retirement](https://support.office.com//article/important-information-for-office-365-enterprise-e4-customers-f9572348-43a2-43fa-a3d8-3b6c9c042147).</span></span>

## <a name="just-need-a-development-environment"></a><span data-ttu-id="b0074-112">Só precisa de um ambiente de desenvolvimento?</span><span class="sxs-lookup"><span data-stu-id="b0074-112">Just need a development environment?</span></span>

<span data-ttu-id="b0074-113">Se você não tiver uma conta do Microsoft 365 no momento, inscreva-se para uma assinatura do Programa para Desenvolvedores do [Microsoft 365.](https://developer.microsoft.com/microsoft-365/dev-program)</span><span class="sxs-lookup"><span data-stu-id="b0074-113">If you don't currently have a Microsoft 365 account, you can sign up for a [Microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program) subscription.</span></span> <span data-ttu-id="b0074-114">Ele é gratuito *por* 90 dias e será renovado continuamente, desde que você o esteja usando para atividades de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="b0074-114">It's *free* for 90 days and will continually renew as long as you're using it for development activity.</span></span> <span data-ttu-id="b0074-115">Se você tiver uma assinatura do Visual Studio *Enterprise* ou *Professional,* ambos os programas incluirão uma assinatura gratuita de desenvolvedor do Microsoft 365, ativa durante a vida de sua assinatura do Visual Studio. [](https://aka.ms/MyVisualStudioBenefits)</span><span class="sxs-lookup"><span data-stu-id="b0074-115">If you have a Visual Studio *Enterprise* or *Professional* subscription, both programs include a free Microsoft 365 [developer subscription](https://aka.ms/MyVisualStudioBenefits), active for the life of your Visual Studio subscription.</span></span> <span data-ttu-id="b0074-116">*Confira* [Configurar uma assinatura de desenvolvedor do Microsoft 365.](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started)</span><span class="sxs-lookup"><span data-stu-id="b0074-116">*See* [Set up a Microsoft 365 developer subscription](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started).</span></span>

## <a name="enable-microsoft-teams-for-your-organization"></a><span data-ttu-id="b0074-117">Habilitar o Microsoft Teams para sua organização</span><span class="sxs-lookup"><span data-stu-id="b0074-117">Enable Microsoft Teams for your organization</span></span> 

<span data-ttu-id="b0074-118">Se o Microsoft Teams não tiver sido habilitado para sua organização, você precisará fazer isso primeiro.</span><span class="sxs-lookup"><span data-stu-id="b0074-118">If Microsoft Teams has not been enabled for your organization, you'll need to do that first.</span></span> <span data-ttu-id="b0074-119">Dê uma olhada em nossas orientações detalhadas para [habilenciar o Teams para sua organização.](/microsoftteams/enable-features-office-365)</span><span class="sxs-lookup"><span data-stu-id="b0074-119">Take a look at our detailed guidance for [enabling Teams for your organization](/microsoftteams/enable-features-office-365).</span></span>

## <a name="enable-custom-teams-apps-and-turn-on-custom-app-uploading"></a><span data-ttu-id="b0074-120">Habilitar aplicativos personalizados do Teams e ativar o carregamento de aplicativos personalizados</span><span class="sxs-lookup"><span data-stu-id="b0074-120">Enable custom Teams apps and turn on custom app uploading</span></span>

<span data-ttu-id="b0074-121">Adquira o sideload de aplicativo personalizado para seu locatário de desenvolvedor da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="b0074-121">Turn on custom app sideloading for your developer tenant as follows:</span></span>

1. <span data-ttu-id="b0074-122">Entre no [Centro de administração do Microsoft 365](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) com sua credencial de administrador.</span><span class="sxs-lookup"><span data-stu-id="b0074-122">Login to [Microsoft 365 admin center](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) with your admin credential.</span></span> 

2. <span data-ttu-id="b0074-123">Selecione **Mostrar Todas as**  -->  **Equipes.**</span><span class="sxs-lookup"><span data-stu-id="b0074-123">Select **Show All** --> **Teams**.</span></span> 

![imagem do menu do centro de administração](~/assets/images/prepare-test-tenant/admin-center.png)

> [!Note] 
> <span data-ttu-id="b0074-125">Pode levar até 24 horas para que a opção "Teams" apareça.</span><span class="sxs-lookup"><span data-stu-id="b0074-125">It can take up to 24 hours for the "Teams" option to appear.</span></span> <span data-ttu-id="b0074-126">Durante o ínterim, você [pode carregar seu aplicativo personalizado em um ambiente do Teams](/microsoftteams/upload-custom-apps#validate) para teste e validação.</span><span class="sxs-lookup"><span data-stu-id="b0074-126">During interim, you can [Upload your custom app to a Teams environment](/microsoftteams/upload-custom-apps#validate) for testing and validation.</span></span>

3. <span data-ttu-id="b0074-127">Navegue até Políticas de Instalação de **Aplicativos** do Teams  -->    -->  **Global (padrão em toda a organização)**</span><span class="sxs-lookup"><span data-stu-id="b0074-127">Navigate to **Teams apps** --> **Setup Policies** --> **Global(Org-wide default)**</span></span>  

![ativar o sideload view](~/assets/images/prepare-test-tenant/turn-on-sideload.png)

4. <span data-ttu-id="b0074-129">Alterne **o carregamento de aplicativos** **personalizados para a posição** on.</span><span class="sxs-lookup"><span data-stu-id="b0074-129">Toggle **upload custom apps** to the **on** position.</span></span>

5. <span data-ttu-id="b0074-130">Selecione **Salvar** para salvar as alterações.</span><span class="sxs-lookup"><span data-stu-id="b0074-130">Select **Save** to save the changes.</span></span>

<span data-ttu-id="b0074-131">Isso é tudo.</span><span class="sxs-lookup"><span data-stu-id="b0074-131">That's it!</span></span> <span data-ttu-id="b0074-132">Seu locatário de teste agora permitirá o sideload de aplicativo personalizado.</span><span class="sxs-lookup"><span data-stu-id="b0074-132">Your test tenant will now allow custom app sideloading.</span></span>

> [!Note] 
> <span data-ttu-id="b0074-133">Pode levar até 24 horas para que o sideload seja habilitado.</span><span class="sxs-lookup"><span data-stu-id="b0074-133">It can take up to 24 hours before sideloading is enabled.</span></span> <span data-ttu-id="b0074-134">Durante o ínterim, você pode **usar o carregamento para \<your tenant>** testar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b0074-134">During interim, you can use **upload for \<your tenant>** to test your app.</span></span>

![exibição do aplicativo de updload](~/assets/images/prepare-test-tenant/upload-for-contoso.png)

<span data-ttu-id="b0074-136">Para obter informações completas sobre como essas configurações interagem, confira , Gerenciar políticas e configurações de [aplicativos personalizados](https://docs.microsoft.com/microsoftteams/teams-custom-app-policies-and-settings) no Microsoft Teams e gerenciar políticas de configuração de aplicativos [no Microsoft Teams.](https://docs.microsoft.com/microsoftteams/teams-app-setup-policies)</span><span class="sxs-lookup"><span data-stu-id="b0074-136">For complete information on how these settings interact, *See*, [Manage custom app policies and settings in Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-custom-app-policies-and-settings) and [Manage app setup policies in Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-app-setup-policies).</span></span>
