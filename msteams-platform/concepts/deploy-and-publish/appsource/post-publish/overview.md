---
title: Publicar publicação
description: O que fazer após a publicação do aplicativo
keywords: publicar o Microsoft Teams postar certificado de atualização
ms.openlocfilehash: d2cc6c5427c5b4f7320f0ec2e022f2c69467a33d
ms.sourcegitcommit: 9fd61042e8be513c2b2bd8a33ab5e9e6498d65c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/20/2020
ms.locfileid: "46819151"
---
# <a name="maintain-and-support-your-published-app"></a><span data-ttu-id="1f805-104">Manter e dar suporte ao seu aplicativo publicado</span><span class="sxs-lookup"><span data-stu-id="1f805-104">Maintain and support your published app</span></span> 

<span data-ttu-id="1f805-105">Depois que o aplicativo é aprovado e listado no catálogo de aplicativos públicos, você pode aumentar seu alcance, concluindo o programa de conformidade do aplicativo Microsoft 365 ou adicionando um botão de download no seu site.</span><span class="sxs-lookup"><span data-stu-id="1f805-105">After your app is approved and listed in the public app catalog, you can increase your reach by completing the Microsoft 365 App Compliance Program or by adding a download button on your website.</span></span>

## <a name="microsoft-365-certified"></a><span data-ttu-id="1f805-106">Certificado pela Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="1f805-106">Microsoft 365 Certified</span></span>

<span data-ttu-id="1f805-107">O [programa de conformidade do Microsoft 365 app](./application-certification.md), é uma abordagem de três camadas para a segurança do aplicativo e conformidade.</span><span class="sxs-lookup"><span data-stu-id="1f805-107">The [Microsoft 365 App Compliance Program](./application-certification.md), is a three tier approach to app security and compliance.</span></span> <span data-ttu-id="1f805-108">Cada camada é baseada na próxima – oferecendo um programa em camadas para atender às necessidades do cliente.</span><span class="sxs-lookup"><span data-stu-id="1f805-108">Each tier builds upon the next – offering a layered program to meet your customer’s needs.</span></span> <span data-ttu-id="1f805-109">Você pode saber mais sobre a postura de segurança e conformidade de aplicativos do teams visitando a [página conformidade](https://docs.microsoft.com/microsoft-365-app-certification/teams/teams-apps).</span><span class="sxs-lookup"><span data-stu-id="1f805-109">You can learn more about the security and compliance posture of Teams apps by visiting the [compliance page](https://docs.microsoft.com/microsoft-365-app-certification/teams/teams-apps).</span></span>

## <a name="add-a-download-button-to-your-product-site"></a><span data-ttu-id="1f805-110">Adicionar um botão de download ao seu site do produto</span><span class="sxs-lookup"><span data-stu-id="1f805-110">Add a download button to your product site</span></span>

<span data-ttu-id="1f805-111">Se seu aplicativo estiver no Microsoft Teams Store, você poderá gerar um link para o seu site que inicia o Teams e mostra uma caixa de diálogo de consentimento e instalação para que os usuários adicionem o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1f805-111">If your app is in the Microsoft Teams store, you can generate a link for your website that launches Teams and shows a consent and installation dialog for users to add the app.</span></span>
<span data-ttu-id="1f805-112">O formato é:  `https://teams.microsoft.com/l/app/<appId>` onde AppID é o GUID que eles declaram no manifesto enviado.</span><span class="sxs-lookup"><span data-stu-id="1f805-112">The format is:  `https://teams.microsoft.com/l/app/<appId>` where appID is the GUID they declare in the submitted manifest.</span></span>
<span data-ttu-id="1f805-113">Exemplo: `https://teams.microsoft.com/l/app/49e6f432-d79c-49e8-94f7-89b94f3672fd` é o link para instalar o Trello.</span><span class="sxs-lookup"><span data-stu-id="1f805-113">Example: `https://teams.microsoft.com/l/app/49e6f432-d79c-49e8-94f7-89b94f3672fd` is the link to install Trello.</span></span>

## <a name="updating-your-existing-teams-app"></a><span data-ttu-id="1f805-114">Atualizando seu aplicativo do teams existente</span><span class="sxs-lookup"><span data-stu-id="1f805-114">Updating your existing Teams app</span></span>

* <span data-ttu-id="1f805-115">Não use o botão *Adicionar um novo aplicativo* para reenviar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1f805-115">Do not use the *Add a new app* button to resubmit your app.</span></span> <span data-ttu-id="1f805-116">Em vez disso, use o bloco para seu aplicativo na guia Visão geral.</span><span class="sxs-lookup"><span data-stu-id="1f805-116">Use the tile for your app on the Overview tab instead.</span></span>
* <span data-ttu-id="1f805-117">O appId no manifesto atualizado deve ser igual ao do manifesto atual, com um número de versão incrementado.</span><span class="sxs-lookup"><span data-stu-id="1f805-117">The appId in the updated manifest should be the same as in the current manifest, with an incremented version number.</span></span>
* <span data-ttu-id="1f805-118">Aumente o número da versão no manifesto se você fizer alterações de manifesto no seu envio.</span><span class="sxs-lookup"><span data-stu-id="1f805-118">Increment your version number in the manifest if you make any manifest changes to your submission.</span></span>
* <span data-ttu-id="1f805-119">Envios atualizados são necessários para passar por um novo processo de revisão e validação.</span><span class="sxs-lookup"><span data-stu-id="1f805-119">Updated submissions are required to undergo a new review and validation process.</span></span>

## <a name="app-updates-and-the-user-consent-flow"></a><span data-ttu-id="1f805-120">Atualizações de aplicativos e o fluxo de consentimento do usuário</span><span class="sxs-lookup"><span data-stu-id="1f805-120">App updates and the user consent flow</span></span>

<span data-ttu-id="1f805-121">Quando um usuário instala o aplicativo uma das primeiras coisas que eles fazem é o consentimento para dar permissão ao aplicativo para acessar os serviços e informações de que o aplicativo precisa para realizar o trabalho.</span><span class="sxs-lookup"><span data-stu-id="1f805-121">When a user installs your application one of the first things they do is consent to give the app permission to access the services and information that the app needs to do its job.</span></span> <span data-ttu-id="1f805-122">Na maioria dos casos, após concluir uma atualização de aplicativo, a nova versão aparecerá automaticamente para os usuários finais.</span><span class="sxs-lookup"><span data-stu-id="1f805-122">In most cases, after you complete an app update the new version will automatically appear for end users.</span></span> <span data-ttu-id="1f805-123">No entanto, há algumas atualizações para o [manifesto do aplicativo do teams](../../../../resources/schema/manifest-schema.md) que exigem a aceitação do usuário para serem concluídas e podem disparar novamente esse comportamento de consentimento:</span><span class="sxs-lookup"><span data-stu-id="1f805-123">However, there are some updates to the [Teams app manifest](../../../../resources/schema/manifest-schema.md) that require user acceptance to complete and can re-trigger this consent behavior:</span></span>

 >[!div class="checklist"]
>
> * <span data-ttu-id="1f805-124">Um bot foi adicionado ou removido.</span><span class="sxs-lookup"><span data-stu-id="1f805-124">A bot was added or removed.</span></span>
> * <span data-ttu-id="1f805-125">Um valor exclusivo de bot existente `botId` foi alterado.</span><span class="sxs-lookup"><span data-stu-id="1f805-125">An existing bot's unique `botId` value changed.</span></span>
> * <span data-ttu-id="1f805-126">Um `isNotificationOnly` valor booliano de bot existente foi alterado.</span><span class="sxs-lookup"><span data-stu-id="1f805-126">An existing bot's `isNotificationOnly` boolean value changed.</span></span>
> * <span data-ttu-id="1f805-127">Um `supportsFiles` valor booliano de bot existente foi alterado.</span><span class="sxs-lookup"><span data-stu-id="1f805-127">An existing bot's `supportsFiles` boolean value changed.</span></span>
> * <span data-ttu-id="1f805-128">Uma extensão de mensagens ( `composeExtensions` ) foi adicionada ou removida.</span><span class="sxs-lookup"><span data-stu-id="1f805-128">A messaging extension (`composeExtensions`) was added or removed.</span></span>
> * <span data-ttu-id="1f805-129">Um novo conector foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="1f805-129">A new connector was added.</span></span>
> * <span data-ttu-id="1f805-130">Uma nova guia estática/pessoal foi adicionada.</span><span class="sxs-lookup"><span data-stu-id="1f805-130">A new static/personal tab was added.</span></span>
> * <span data-ttu-id="1f805-131">Uma nova guia de grupo/canal configurável foi adicionada.</span><span class="sxs-lookup"><span data-stu-id="1f805-131">A new configurable group/channel tab was added.</span></span>
> * <span data-ttu-id="1f805-132">Os `webApplicationInfo` valores foram alterados.</span><span class="sxs-lookup"><span data-stu-id="1f805-132">The `webApplicationInfo` values changed.</span></span>
>
