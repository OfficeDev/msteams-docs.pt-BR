---
title: Mantendo e dando suporte ao aplicativo publicado
description: O que fazer depois de publicar seu aplicativo
ms.topic: how-to
keywords: teams post publish update certification app update update manifest
ms.openlocfilehash: 8644db5e329e15d77062553eda4a41a36b2740ee
ms.sourcegitcommit: e78c9f51c4538212c53bb6c6a45a09d994896f09
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/05/2021
ms.locfileid: "51585831"
---
# <a name="maintain-and-support-your-published-app"></a><span data-ttu-id="101b8-104">Manter e dar suporte ao seu aplicativo publicado</span><span class="sxs-lookup"><span data-stu-id="101b8-104">Maintain and support your published app</span></span> 

<span data-ttu-id="101b8-105">Depois que seu aplicativo for aprovado e listado no catálogo de aplicativos públicos, você poderá aumentar seu alcance concluindo o Programa de Conformidade de Aplicativos do Microsoft 365 ou adicionando um botão de download em seu site.</span><span class="sxs-lookup"><span data-stu-id="101b8-105">After your app is approved and listed in the public app catalog, you can increase your reach by completing the Microsoft 365 App Compliance Program or by adding a download button on your website.</span></span>

## <a name="microsoft-365-certified"></a><span data-ttu-id="101b8-106">Microsoft 365 Certified</span><span class="sxs-lookup"><span data-stu-id="101b8-106">Microsoft 365 Certified</span></span>

<span data-ttu-id="101b8-107">O Programa de Conformidade de Aplicativos do [Microsoft 365](./application-certification.md)é uma abordagem de três camadas para segurança e conformidade do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="101b8-107">The [Microsoft 365 App Compliance Program](./application-certification.md), is a three tier approach to app security and compliance.</span></span> <span data-ttu-id="101b8-108">Cada camada se acumula na próxima – oferecendo um programa em camadas para atender às necessidades do cliente.</span><span class="sxs-lookup"><span data-stu-id="101b8-108">Each tier builds upon the next – offering a layered program to meet your customer’s needs.</span></span> <span data-ttu-id="101b8-109">Você pode saber mais sobre a postura de segurança e conformidade dos aplicativos do Teams visitando a página [de conformidade](https://docs.microsoft.com/microsoft-365-app-certification/teams/teams-apps).</span><span class="sxs-lookup"><span data-stu-id="101b8-109">You can learn more about the security and compliance posture of Teams apps by visiting the [compliance page](https://docs.microsoft.com/microsoft-365-app-certification/teams/teams-apps).</span></span>

## <a name="add-a-download-button-to-your-product-site"></a><span data-ttu-id="101b8-110">Adicionar um botão de download ao site do produto</span><span class="sxs-lookup"><span data-stu-id="101b8-110">Add a download button to your product site</span></span>

<span data-ttu-id="101b8-111">Se seu aplicativo estiver na loja global do Microsoft Teams, você poderá gerar um link para seu site que inicia o Teams e mostra uma caixa de diálogo de consentimento e instalação para os usuários adicionarem o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="101b8-111">If your app is in the Microsoft Teams global store, you can generate a link for your website that launches Teams and shows a consent and installation dialog for users to add the app.</span></span>
<span data-ttu-id="101b8-112">O formato é:  `https://teams.microsoft.com/l/app/<appId>` onde appID é o GUID declarado no manifesto enviado.</span><span class="sxs-lookup"><span data-stu-id="101b8-112">The format is:  `https://teams.microsoft.com/l/app/<appId>` where appID is the GUID they declare in the submitted manifest.</span></span>
<span data-ttu-id="101b8-113">Exemplo: `https://teams.microsoft.com/l/app/49e6f432-d79c-49e8-94f7-89b94f3672fd` é o link para instalar Trello.</span><span class="sxs-lookup"><span data-stu-id="101b8-113">Example: `https://teams.microsoft.com/l/app/49e6f432-d79c-49e8-94f7-89b94f3672fd` is the link to install Trello.</span></span>

## <a name="updating-your-existing-teams-app"></a><span data-ttu-id="101b8-114">Atualizando seu aplicativo existente do Teams</span><span class="sxs-lookup"><span data-stu-id="101b8-114">Updating your existing Teams app</span></span>

* <span data-ttu-id="101b8-115">Não use o *botão Adicionar um novo aplicativo* para reabrir o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="101b8-115">Do not use the *Add a new app* button to resubmit your app.</span></span> <span data-ttu-id="101b8-116">Use o azulejo para seu aplicativo na guia Visão geral.</span><span class="sxs-lookup"><span data-stu-id="101b8-116">Use the tile for your app on the Overview tab instead.</span></span>
* <span data-ttu-id="101b8-117">O appId no manifesto atualizado deve ser o mesmo do manifesto atual, com um número de versão incrementado.</span><span class="sxs-lookup"><span data-stu-id="101b8-117">The appId in the updated manifest should be the same as in the current manifest, with an incremented version number.</span></span>
* <span data-ttu-id="101b8-118">Incremente seu número de versão no manifesto se você fizer alterações no envio, incluindo o nome do aplicativo ou quaisquer metadados no manifesto.</span><span class="sxs-lookup"><span data-stu-id="101b8-118">Increment your version number in the manifest if you make any changes to your submission including app name or any metadata in the manifest.</span></span>
* <span data-ttu-id="101b8-119">Os envios atualizados são necessários para passar por um novo processo de revisão e validação.</span><span class="sxs-lookup"><span data-stu-id="101b8-119">Updated submissions are required to undergo a new review and validation process.</span></span>

## <a name="app-updates-and-the-user-consent-flow"></a><span data-ttu-id="101b8-120">Atualizações de aplicativos e o fluxo de consentimento do usuário</span><span class="sxs-lookup"><span data-stu-id="101b8-120">App updates and the user consent flow</span></span>

<span data-ttu-id="101b8-121">Quando um usuário instala seu aplicativo, uma das primeiras coisas que ele faz é consentir em dar ao aplicativo permissão para acessar os serviços e informações que o aplicativo precisa para fazer seu trabalho.</span><span class="sxs-lookup"><span data-stu-id="101b8-121">When a user installs your application one of the first things they do is consent to give the app permission to access the services and information that the app needs to do its job.</span></span> <span data-ttu-id="101b8-122">Na maioria dos casos, depois de concluir uma atualização de aplicativo, a nova versão aparecerá automaticamente para usuários finais.</span><span class="sxs-lookup"><span data-stu-id="101b8-122">In most cases, after you complete an app update the new version will automatically appear for end users.</span></span> <span data-ttu-id="101b8-123">No entanto, há algumas atualizações no manifesto do [aplicativo do Teams](../../../../resources/schema/manifest-schema.md) que exigem que a aceitação do usuário seja concluída e podem reacionar esse comportamento de consentimento:</span><span class="sxs-lookup"><span data-stu-id="101b8-123">However, there are some updates to the [Teams app manifest](../../../../resources/schema/manifest-schema.md) that require user acceptance to complete and can re-trigger this consent behavior:</span></span>

 >[!div class="checklist"]
>
> * <span data-ttu-id="101b8-124">Um bot é adicionado ou removido.</span><span class="sxs-lookup"><span data-stu-id="101b8-124">A bot is added or removed.</span></span>
> * <span data-ttu-id="101b8-125">O valor exclusivo de um bot `botId` existente é alterado.</span><span class="sxs-lookup"><span data-stu-id="101b8-125">An existing bot's unique `botId` value is changed.</span></span>
> * <span data-ttu-id="101b8-126">O valor boolano de um `isNotificationOnly` bot existente é alterado.</span><span class="sxs-lookup"><span data-stu-id="101b8-126">An existing bot's `isNotificationOnly` boolean value is changed.</span></span>
> * <span data-ttu-id="101b8-127">O valor booleano ou bot `supportsFiles` `supportsCalling` existente é alterado.</span><span class="sxs-lookup"><span data-stu-id="101b8-127">An existing bot's `supportsFiles` or `supportsCalling` boolean value is changed.</span></span>
> * <span data-ttu-id="101b8-128">Uma extensão de mensagens `composeExtensions` é adicionada ou removida.</span><span class="sxs-lookup"><span data-stu-id="101b8-128">A messaging extension `composeExtensions` is added or removed.</span></span>
> * <span data-ttu-id="101b8-129">Um novo conector é adicionado.</span><span class="sxs-lookup"><span data-stu-id="101b8-129">A new connector is added.</span></span>
> * <span data-ttu-id="101b8-130">Uma nova guia estática ou pessoal é adicionada.</span><span class="sxs-lookup"><span data-stu-id="101b8-130">A new static or personal tab is added.</span></span>
> * <span data-ttu-id="101b8-131">Um novo grupo configurável ou uma guia de canal é adicionado.</span><span class="sxs-lookup"><span data-stu-id="101b8-131">A new configurable group or channel tab is added.</span></span>
> * <span data-ttu-id="101b8-132">As propriedades internas `webApplicationInfo` são alteradas.</span><span class="sxs-lookup"><span data-stu-id="101b8-132">The properties inside `webApplicationInfo` are changed.</span></span> <span data-ttu-id="101b8-133">Para alterações em `webApplicationInfo` , o consentimento só é necessário no escopo do Teams.</span><span class="sxs-lookup"><span data-stu-id="101b8-133">For changes to `webApplicationInfo`, consent is only required in the Teams scope.</span></span>

### <a name="images-of-user-consent-flow"></a><span data-ttu-id="101b8-134">Imagens do fluxo de consentimento do usuário:</span><span class="sxs-lookup"><span data-stu-id="101b8-134">Images of user consent flow:</span></span>

<span data-ttu-id="101b8-135">**Configurar um conector** — essa tela aparecerá somente para usuários do Teams.</span><span class="sxs-lookup"><span data-stu-id="101b8-135">**Set up a connector** —  This screen will appear only for Teams users.</span></span>

![Configuração de fluxo de consentimento um diagrama de conector](../../../../assets/images/connector-teams-consentflow.png)

<span data-ttu-id="101b8-137">**Fluxo de consentimento do usuário** - Essa tela é comum para escopo pessoal e de grupo.</span><span class="sxs-lookup"><span data-stu-id="101b8-137">**User consent flow** - This screen is common for both personal and group scope.</span></span> <span data-ttu-id="101b8-138">Aqui, selecione a **caixa de seleção Consentimento em nome** da sua organização e escolha **Aceitar**.</span><span class="sxs-lookup"><span data-stu-id="101b8-138">Here, select the **Consent on behalf of your organization** checkbox and choose **Accept**.</span></span>

![Diagrama de permissões](../../../../assets/images/user-consent-flow.png)
