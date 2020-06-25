---
title: Publicar publicação
description: O que fazer após a publicação do aplicativo
keywords: publicar o Microsoft Teams postar certificado de atualização
ms.openlocfilehash: 77b74d77546de0ae93b0ae39aec925d2e3dec2cf
ms.sourcegitcommit: fdc50183f3f4bec9e4b83bcfe5e016b591402f7c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/24/2020
ms.locfileid: "44867088"
---
# <a name="maintain-and-support-your-published-app"></a><span data-ttu-id="d92e1-104">Manter e dar suporte ao aplicativo publicado</span><span class="sxs-lookup"><span data-stu-id="d92e1-104">Maintain and support your published app</span></span> 

<span data-ttu-id="d92e1-105">Depois que o aplicativo é aprovado e listado no catálogo de aplicativos públicos, você pode aumentar seu alcance obtendo a certificação do aplicativo ou adicionando um botão de download ao seu site.</span><span class="sxs-lookup"><span data-stu-id="d92e1-105">After your app is approved and listed in the public app catalog, you can increase your reach by achieving app certification, or adding a download button your website.</span></span>

## <a name="application-certificate"></a><span data-ttu-id="d92e1-106">Certificado de aplicativo</span><span class="sxs-lookup"><span data-stu-id="d92e1-106">Application Certificate</span></span>

<span data-ttu-id="d92e1-107">A Microsoft fornece um [programa de certificação de aplicativo](./application-certification.md) que compila suas informações de aplicativo e as apresenta na página de [conformidade e segurança do aplicativo do Microsoft Teams](https://aka.ms/AppCertification).</span><span class="sxs-lookup"><span data-stu-id="d92e1-107">Microsoft provides a [Application Certification program](./application-certification.md) that compiles your app information and presents it on [Microsoft Teams App Security and Compliance Page](https://aka.ms/AppCertification).</span></span> <span data-ttu-id="d92e1-108">Essas informações destinam-se a ajudar os administradores a escolher aplicativos seguros para suas organizações.</span><span class="sxs-lookup"><span data-stu-id="d92e1-108">This information is intended to help admins to choose apps that are safe for their organizations.</span></span>

## <a name="add-a-download-button-to-your-product-site"></a><span data-ttu-id="d92e1-109">Adicionar um botão de download ao seu site do produto</span><span class="sxs-lookup"><span data-stu-id="d92e1-109">Add a download button to your product site</span></span>

<span data-ttu-id="d92e1-110">Se seu aplicativo estiver no Microsoft Teams Store, você poderá gerar um link para o seu site que inicia o Teams e mostra uma caixa de diálogo de consentimento e instalação para que os usuários adicionem o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d92e1-110">If your app is in the Microsoft Teams store, you can generate a link for your website that launches Teams and shows a consent and installation dialog for users to add the app.</span></span>
<span data-ttu-id="d92e1-111">O formato é: `https://teams.microsoft.com/l/app/<appId>` onde AppID é o GUID que eles declaram no manifesto enviado.</span><span class="sxs-lookup"><span data-stu-id="d92e1-111">The format is:  `https://teams.microsoft.com/l/app/<appId>` where appID is the GUID they declare in the submitted manifest.</span></span>
<span data-ttu-id="d92e1-112">Exemplo: `https://teams.microsoft.com/l/app/49e6f432-d79c-49e8-94f7-89b94f3672fd` é o link para instalar o Trello.</span><span class="sxs-lookup"><span data-stu-id="d92e1-112">Example: `https://teams.microsoft.com/l/app/49e6f432-d79c-49e8-94f7-89b94f3672fd` is the link to install Trello.</span></span>

## <a name="updating-your-existing-teams-app"></a><span data-ttu-id="d92e1-113">Atualizando seu aplicativo do teams existente</span><span class="sxs-lookup"><span data-stu-id="d92e1-113">Updating your existing Teams app</span></span>

* <span data-ttu-id="d92e1-114">Não use o botão *Adicionar um novo aplicativo* para reenviar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d92e1-114">Do not use the *Add a new app* button to resubmit your app.</span></span> <span data-ttu-id="d92e1-115">Em vez disso, use o bloco para seu aplicativo na guia Visão geral.</span><span class="sxs-lookup"><span data-stu-id="d92e1-115">Use the tile for your app on the Overview tab instead.</span></span>
* <span data-ttu-id="d92e1-116">O appId no manifesto atualizado deve ser igual ao do manifesto atual, com um número de versão incrementado.</span><span class="sxs-lookup"><span data-stu-id="d92e1-116">The appId in the updated manifest should be the same as in the current manifest, with an incremented version number.</span></span>
* <span data-ttu-id="d92e1-117">Aumente o número da versão no manifesto se você fizer alterações de manifesto no seu envio.</span><span class="sxs-lookup"><span data-stu-id="d92e1-117">Increment your version number in the manifest if you make any manifest changes to your submission.</span></span>
* <span data-ttu-id="d92e1-118">Envios atualizados são necessários para passar por um novo processo de revisão e validação.</span><span class="sxs-lookup"><span data-stu-id="d92e1-118">Updated submissions are required to undergo a new review and validation process.</span></span>

## <a name="app-updates-and-the-user-consent-flow"></a><span data-ttu-id="d92e1-119">Atualizações de aplicativos e o fluxo de consentimento do usuário</span><span class="sxs-lookup"><span data-stu-id="d92e1-119">App updates and the user consent flow</span></span>

<span data-ttu-id="d92e1-120">Quando um usuário instala o aplicativo uma das primeiras coisas que eles fazem é o consentimento para dar permissão ao aplicativo para acessar os serviços e informações de que o aplicativo precisa para realizar o trabalho.</span><span class="sxs-lookup"><span data-stu-id="d92e1-120">When a user installs your application one of the first things they do is consent to give the app permission to access the services and information that the app needs to do its job.</span></span> <span data-ttu-id="d92e1-121">Na maioria dos casos, após concluir uma atualização de aplicativo, a nova versão aparecerá automaticamente para os usuários finais.</span><span class="sxs-lookup"><span data-stu-id="d92e1-121">In most cases, after you complete an app update the new version will automatically appear for end users.</span></span> <span data-ttu-id="d92e1-122">No entanto, há algumas atualizações para o [manifesto do aplicativo do teams](../../../../resources/schema/manifest-schema.md) que exigem a aceitação do usuário para serem concluídas e podem disparar novamente esse comportamento de consentimento:</span><span class="sxs-lookup"><span data-stu-id="d92e1-122">However, there are some updates to the [Teams app manifest](../../../../resources/schema/manifest-schema.md) that require user acceptance to complete and can re-trigger this consent behavior:</span></span>

 >[!div class="checklist"]
>
> * <span data-ttu-id="d92e1-123">Um bot foi adicionado ou removido.</span><span class="sxs-lookup"><span data-stu-id="d92e1-123">A bot was added or removed.</span></span>
> * <span data-ttu-id="d92e1-124">Um valor exclusivo de bot existente `botId` foi alterado.</span><span class="sxs-lookup"><span data-stu-id="d92e1-124">An existing bot's unique `botId` value changed.</span></span>
> * <span data-ttu-id="d92e1-125">Um `isNotificationOnly` valor booliano de bot existente foi alterado.</span><span class="sxs-lookup"><span data-stu-id="d92e1-125">An existing bot's `isNotificationOnly` boolean value changed.</span></span>
> * <span data-ttu-id="d92e1-126">Um `supportsFiles` valor booliano de bot existente foi alterado.</span><span class="sxs-lookup"><span data-stu-id="d92e1-126">An existing bot's `supportsFiles` boolean value changed.</span></span>
> * <span data-ttu-id="d92e1-127">Uma extensão de mensagens ( `composeExtensions` ) foi adicionada ou removida.</span><span class="sxs-lookup"><span data-stu-id="d92e1-127">A messaging extension (`composeExtensions`) was added or removed.</span></span>
> * <span data-ttu-id="d92e1-128">Um novo conector foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="d92e1-128">A new connector was added.</span></span>
> * <span data-ttu-id="d92e1-129">Uma nova guia estática/pessoal foi adicionada.</span><span class="sxs-lookup"><span data-stu-id="d92e1-129">A new static/personal tab was added.</span></span>
> * <span data-ttu-id="d92e1-130">Uma nova guia de grupo/canal configurável foi adicionada.</span><span class="sxs-lookup"><span data-stu-id="d92e1-130">A new configurable group/channel tab was added.</span></span>
> * <span data-ttu-id="d92e1-131">Os `webApplicationInfo` valores foram alterados.</span><span class="sxs-lookup"><span data-stu-id="d92e1-131">The `webApplicationInfo` values changed.</span></span>
>