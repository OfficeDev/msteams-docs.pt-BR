---
title: Manter e dar suporte ao seu aplicativo publicado
description: O que pensar quando sua loja for listada na Teams store e no AppSource.
ms.topic: conceptual
localization_priority: Normal
author: heath-hamilton
ms.author: surbhigupta
ms.openlocfilehash: 57b57e268a4f2eafc14d0372b8b8383e410a80d5
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101748"
---
# <a name="maintain-your-published-microsoft-teams-app"></a><span data-ttu-id="dc403-103">Manter seu aplicativo Microsoft Teams publicado</span><span class="sxs-lookup"><span data-stu-id="dc403-103">Maintain your published Microsoft Teams app</span></span>

<span data-ttu-id="dc403-104">Com seu aplicativo listado na Microsoft Teams, comece a pensar em como você manterá o aplicativo em frente e aumentará os downloads e o uso.</span><span class="sxs-lookup"><span data-stu-id="dc403-104">With your app listed on the Microsoft Teams store, start thinking about how you'll maintain the app going forward and increase downloads and usage.</span></span>

## <a name="publish-updates-to-your-app"></a><span data-ttu-id="dc403-105">Publicar atualizações em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="dc403-105">Publish updates to your app</span></span>

<span data-ttu-id="dc403-106">Você pode enviar alterações ao seu aplicativo (como novos recursos ou até mesmo metadados) no Partner Center.</span><span class="sxs-lookup"><span data-stu-id="dc403-106">You can submit changes to your app (such as new features or even metadata) in Partner Center.</span></span> <span data-ttu-id="dc403-107">Essas alterações exigem um novo processo de revisão.</span><span class="sxs-lookup"><span data-stu-id="dc403-107">These changes requires a new review process.</span></span>

<span data-ttu-id="dc403-108">Verifique o seguinte ao publicar atualizações:</span><span class="sxs-lookup"><span data-stu-id="dc403-108">Ensure the following when publishing updates:</span></span>

* <span data-ttu-id="dc403-109">Não altere a ID do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dc403-109">Don't change your app ID.</span></span>
* <span data-ttu-id="dc403-110">Incremente o número da versão do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dc403-110">Increment your app's version number.</span></span>
* <span data-ttu-id="dc403-111">No Partner Center, não selecione **Adicionar um novo aplicativo** para fazer a atualização.</span><span class="sxs-lookup"><span data-stu-id="dc403-111">In Partner Center, don't select **Add a new app** to do the update.</span></span> <span data-ttu-id="dc403-112">Vá para a página do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dc403-112">Go to your app's page instead.</span></span>

### <a name="app-updates-requiring-user-consent"></a><span data-ttu-id="dc403-113">Atualizações de aplicativo que exigem consentimento do usuário</span><span class="sxs-lookup"><span data-stu-id="dc403-113">App updates requiring user consent</span></span>

<span data-ttu-id="dc403-114">Quando um usuário instala seu aplicativo, ele deve dar ao aplicativo permissão para acessar os serviços e informações que o aplicativo exige para funcionar.</span><span class="sxs-lookup"><span data-stu-id="dc403-114">When a user installs your app, they must give the app permission to access the services and information the app requires to function.</span></span> <span data-ttu-id="dc403-115">Na maioria dos casos, os usuários só têm que fazer isso uma vez e novas versões do aplicativo são instaladas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="dc403-115">In most cases, users only have to do this once and new versions of your app install automatically.</span></span>

<span data-ttu-id="dc403-116">No entanto, se você fizer qualquer uma das seguintes alterações em seu aplicativo, seus usuários existentes devem aceitar outra solicitação de permissão para instalar a atualização:</span><span class="sxs-lookup"><span data-stu-id="dc403-116">If you make any of the following changes to your app, however, your existing users must accept another permission request to install the update:</span></span>

* <span data-ttu-id="dc403-117">Adicionar ou remover um bot.</span><span class="sxs-lookup"><span data-stu-id="dc403-117">Add or remove a bot.</span></span>
* <span data-ttu-id="dc403-118">Altere a ID do bot.</span><span class="sxs-lookup"><span data-stu-id="dc403-118">Change the bot ID.</span></span>
* <span data-ttu-id="dc403-119">Modificar a configuração de notificação one-way de um bot.</span><span class="sxs-lookup"><span data-stu-id="dc403-119">Modify a bot's one-way notification configuration.</span></span>
* <span data-ttu-id="dc403-120">Modifique o suporte de um bot para carregar e baixar arquivos.</span><span class="sxs-lookup"><span data-stu-id="dc403-120">Modify a bot's support for uploading and downloading files.</span></span>
* <span data-ttu-id="dc403-121">Adicione ou remova uma extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="dc403-121">Add or remove a messaging extension.</span></span>
* <span data-ttu-id="dc403-122">Adicione uma guia pessoal.</span><span class="sxs-lookup"><span data-stu-id="dc403-122">Add a personal tab.</span></span>
* <span data-ttu-id="dc403-123">Adicione um canal e uma guia de grupo.</span><span class="sxs-lookup"><span data-stu-id="dc403-123">Add a channel and group tab.</span></span>
* <span data-ttu-id="dc403-124">Adicione um conector.</span><span class="sxs-lookup"><span data-stu-id="dc403-124">Add a connector.</span></span>
* <span data-ttu-id="dc403-125">Modificar configurações relacionadas ao seu Azure Active Directory (registro do aplicativo do Azure AD).</span><span class="sxs-lookup"><span data-stu-id="dc403-125">Modify configurations related to your Azure Active Directory (Azure AD) app registration.</span></span> <span data-ttu-id="dc403-126">Para obter mais informações, consulte [`webApplicationInfo`](~/resources/schema/manifest-schema.md#webapplicationinfo) .</span><span class="sxs-lookup"><span data-stu-id="dc403-126">For more information, see [`webApplicationInfo`](~/resources/schema/manifest-schema.md#webapplicationinfo).</span></span>

## <a name="fix-issues-with-your-published-app"></a><span data-ttu-id="dc403-127">Corrigir problemas com seu aplicativo publicado</span><span class="sxs-lookup"><span data-stu-id="dc403-127">Fix issues with your published app</span></span>

<span data-ttu-id="dc403-128">A Microsoft executa testes diários de automação em aplicativos listados no Teams store.</span><span class="sxs-lookup"><span data-stu-id="dc403-128">Microsoft runs daily automation tests on apps listed on the Teams store.</span></span> <span data-ttu-id="dc403-129">Se os problemas com seu aplicativo são identificados, entraremos em contato com um relatório detalhado sobre como reproduzir os problemas e recomendações para resolvê-los.</span><span class="sxs-lookup"><span data-stu-id="dc403-129">If issues with your app are identified, we contact you with a detailed report on how to reproduce the issues and recommendations to resolve them.</span></span> <span data-ttu-id="dc403-130">Se você não puder corrigir os problemas em uma linha do tempo afirmada, a listagem do aplicativo poderá ser removida da loja.</span><span class="sxs-lookup"><span data-stu-id="dc403-130">If you can't fix the problems within a stated timeline, your app listing may be removed from the store.</span></span>

## <a name="promote-your-app-on-another-site"></a><span data-ttu-id="dc403-131">Promover seu aplicativo em outro site</span><span class="sxs-lookup"><span data-stu-id="dc403-131">Promote your app on another site</span></span>

<span data-ttu-id="dc403-132">Quando seu aplicativo é listado na Teams, você pode criar um link que inicia Teams e exibe uma caixa de diálogo para instalar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dc403-132">When your app is listed in the Teams store, you can create a link that launches Teams and displays a dialog to install your app.</span></span> <span data-ttu-id="dc403-133">Você pode incluir esse link, por exemplo, com um botão de download na página de marketing do produto.</span><span class="sxs-lookup"><span data-stu-id="dc403-133">You could include this link, for example, with a download button on your product's marketing page.</span></span>

<span data-ttu-id="dc403-134">Crie o link usando a seguinte URL anexada à ID do aplicativo: `https://teams.microsoft.com/l/app/<your-app-id>` .</span><span class="sxs-lookup"><span data-stu-id="dc403-134">Create the link using the following URL appended with your app ID: `https://teams.microsoft.com/l/app/<your-app-id>`.</span></span>

## <a name="complete-microsoft-365-certification"></a><span data-ttu-id="dc403-135">Concluir Microsoft 365 Certificação</span><span class="sxs-lookup"><span data-stu-id="dc403-135">Complete Microsoft 365 Certification</span></span>

<span data-ttu-id="dc403-136">[Microsoft 365 Certificação](/microsoft-365-app-certification/docs/certification) oferece garantias de que os dados e a privacidade são adequadamente protegidos e protegidos quando um Aplicativo do Office ou um Aplicativo do Office de terceiros é instalado em seu ecossistema Microsoft 365 de terceiros.</span><span class="sxs-lookup"><span data-stu-id="dc403-136">[Microsoft 365 Certification](/microsoft-365-app-certification/docs/certification) offers assurances that data and privacy are adequately secured and protected when a third-party Office app or add-in is installed in your Microsoft 365 ecosystem.</span></span> <span data-ttu-id="dc403-137">A certificação confirma que seu aplicativo é compatível com tecnologias da Microsoft, compatível com as práticas recomendadas de segurança do aplicativo na nuvem e com suporte da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="dc403-137">Certification confirms that your app is compatible with Microsoft technologies, compliant with cloud app security best practices, and supported by Microsoft.</span></span>

## <a name="see-also"></a><span data-ttu-id="dc403-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="dc403-138">See also</span></span>

* [<span data-ttu-id="dc403-139">Monetize seu aplicativo por meio do Marketplace Comercial da Microsoft</span><span class="sxs-lookup"><span data-stu-id="dc403-139">Monetize your app through Microsoft Commercial Marketplace</span></span>](/office/dev/store/monetize-addins-through-microsoft-commercial-marketplace)
