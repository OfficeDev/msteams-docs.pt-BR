---
title: Mantendo e dando suporte ao seu aplicativo publicado
description: O que fazer depois de publicar seu aplicativo
ms.topic: how-to
keywords: teams post publish update certification app update manifest
ms.openlocfilehash: ce63b840307f7e12a5cd05a1c67aed017cf6199b
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014324"
---
# <a name="maintain-and-support-your-published-app"></a><span data-ttu-id="e238c-104">Manter e dar suporte ao seu aplicativo publicado</span><span class="sxs-lookup"><span data-stu-id="e238c-104">Maintain and support your published app</span></span> 

<span data-ttu-id="e238c-105">Depois que seu aplicativo for aprovado e listado no catálogo de aplicativos público, você poderá aumentar seu alcance concluindo o Programa de Conformidade de Aplicativos do Microsoft 365 ou adicionando um botão de download ao seu site.</span><span class="sxs-lookup"><span data-stu-id="e238c-105">After your app is approved and listed in the public app catalog, you can increase your reach by completing the Microsoft 365 App Compliance Program or by adding a download button on your website.</span></span>

## <a name="microsoft-365-certified"></a><span data-ttu-id="e238c-106">Microsoft 365 Certified</span><span class="sxs-lookup"><span data-stu-id="e238c-106">Microsoft 365 Certified</span></span>

<span data-ttu-id="e238c-107">O Programa de Conformidade de Aplicativos do [Microsoft 365](./application-certification.md)é uma abordagem de três camadas para segurança e conformidade de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="e238c-107">The [Microsoft 365 App Compliance Program](./application-certification.md), is a three tier approach to app security and compliance.</span></span> <span data-ttu-id="e238c-108">Cada camada se baseia na próxima – oferecendo um programa em camadas para atender às necessidades do cliente.</span><span class="sxs-lookup"><span data-stu-id="e238c-108">Each tier builds upon the next – offering a layered program to meet your customer’s needs.</span></span> <span data-ttu-id="e238c-109">Você pode saber mais sobre a postura de segurança e conformidade dos aplicativos do Teams visitando a página [de conformidade.](https://docs.microsoft.com/microsoft-365-app-certification/teams/teams-apps)</span><span class="sxs-lookup"><span data-stu-id="e238c-109">You can learn more about the security and compliance posture of Teams apps by visiting the [compliance page](https://docs.microsoft.com/microsoft-365-app-certification/teams/teams-apps).</span></span>

## <a name="add-a-download-button-to-your-product-site"></a><span data-ttu-id="e238c-110">Adicionar um botão de download ao site do produto</span><span class="sxs-lookup"><span data-stu-id="e238c-110">Add a download button to your product site</span></span>

<span data-ttu-id="e238c-111">Se seu aplicativo estiver na loja global do Microsoft Teams, você poderá gerar um link para seu site que inicia o Teams e mostra uma caixa de diálogo de consentimento e instalação para que os usuários adicionem o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e238c-111">If your app is in the Microsoft Teams global store, you can generate a link for your website that launches Teams and shows a consent and installation dialog for users to add the app.</span></span>
<span data-ttu-id="e238c-112">O formato é:  `https://teams.microsoft.com/l/app/<appId>` onde appID é o GUID declarado no manifesto enviado.</span><span class="sxs-lookup"><span data-stu-id="e238c-112">The format is:  `https://teams.microsoft.com/l/app/<appId>` where appID is the GUID they declare in the submitted manifest.</span></span>
<span data-ttu-id="e238c-113">Exemplo: `https://teams.microsoft.com/l/app/49e6f432-d79c-49e8-94f7-89b94f3672fd` é o link para instalar o Trello.</span><span class="sxs-lookup"><span data-stu-id="e238c-113">Example: `https://teams.microsoft.com/l/app/49e6f432-d79c-49e8-94f7-89b94f3672fd` is the link to install Trello.</span></span>

## <a name="updating-your-existing-teams-app"></a><span data-ttu-id="e238c-114">Atualizando seu aplicativo existente do Teams</span><span class="sxs-lookup"><span data-stu-id="e238c-114">Updating your existing Teams app</span></span>

* <span data-ttu-id="e238c-115">Não use o *botão Adicionar um novo aplicativo* para resubmitir seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e238c-115">Do not use the *Add a new app* button to resubmit your app.</span></span> <span data-ttu-id="e238c-116">Use o lado do aplicativo na guia Visão geral.</span><span class="sxs-lookup"><span data-stu-id="e238c-116">Use the tile for your app on the Overview tab instead.</span></span>
* <span data-ttu-id="e238c-117">A appId no manifesto atualizado deve ser a mesma do manifesto atual, com um número de versão incrementado.</span><span class="sxs-lookup"><span data-stu-id="e238c-117">The appId in the updated manifest should be the same as in the current manifest, with an incremented version number.</span></span>
* <span data-ttu-id="e238c-118">Incremente seu número de versão no manifesto se você fizer alterações no envio, incluindo o nome do aplicativo ou quaisquer metadados no manifesto.</span><span class="sxs-lookup"><span data-stu-id="e238c-118">Increment your version number in the manifest if you make any changes to your submission including app name or any metadata in the manifest.</span></span>
* <span data-ttu-id="e238c-119">Envios atualizados são necessários para passar por um novo processo de revisão e validação.</span><span class="sxs-lookup"><span data-stu-id="e238c-119">Updated submissions are required to undergo a new review and validation process.</span></span>

## <a name="app-updates-and-the-user-consent-flow"></a><span data-ttu-id="e238c-120">Atualizações de aplicativos e o fluxo de consentimento do usuário</span><span class="sxs-lookup"><span data-stu-id="e238c-120">App updates and the user consent flow</span></span>

<span data-ttu-id="e238c-121">Quando um usuário instala seu aplicativo, uma das primeiras coisas que ele faz é consentir em dar ao aplicativo permissão para acessar os serviços e informações que o aplicativo precisa para fazer seu trabalho.</span><span class="sxs-lookup"><span data-stu-id="e238c-121">When a user installs your application one of the first things they do is consent to give the app permission to access the services and information that the app needs to do its job.</span></span> <span data-ttu-id="e238c-122">Na maioria dos casos, depois que você concluir uma atualização de aplicativo, a nova versão aparecerá automaticamente para os usuários finais.</span><span class="sxs-lookup"><span data-stu-id="e238c-122">In most cases, after you complete an app update the new version will automatically appear for end users.</span></span> <span data-ttu-id="e238c-123">No entanto, há algumas atualizações no manifesto do [aplicativo teams](../../../../resources/schema/manifest-schema.md) que exigem a aceitação do usuário para ser concluída e podem disparar esse comportamento de consentimento outra vez:</span><span class="sxs-lookup"><span data-stu-id="e238c-123">However, there are some updates to the [Teams app manifest](../../../../resources/schema/manifest-schema.md) that require user acceptance to complete and can re-trigger this consent behavior:</span></span>

 >[!div class="checklist"]
>
> * <span data-ttu-id="e238c-124">Um bot foi adicionado ou removido.</span><span class="sxs-lookup"><span data-stu-id="e238c-124">A bot was added or removed.</span></span>
> * <span data-ttu-id="e238c-125">O valor exclusivo de um bot `botId` existente foi alterado.</span><span class="sxs-lookup"><span data-stu-id="e238c-125">An existing bot's unique `botId` value changed.</span></span>
> * <span data-ttu-id="e238c-126">O valor booliana de um bot `isNotificationOnly` existente foi alterado.</span><span class="sxs-lookup"><span data-stu-id="e238c-126">An existing bot's `isNotificationOnly` boolean value changed.</span></span>
> * <span data-ttu-id="e238c-127">O valor booliana de um bot `supportsFiles` existente foi alterado.</span><span class="sxs-lookup"><span data-stu-id="e238c-127">An existing bot's `supportsFiles` boolean value changed.</span></span>
> * <span data-ttu-id="e238c-128">Uma extensão de mensagens ( `composeExtensions` ) foi adicionada ou removida.</span><span class="sxs-lookup"><span data-stu-id="e238c-128">A messaging extension (`composeExtensions`) was added or removed.</span></span>
> * <span data-ttu-id="e238c-129">Um novo conector foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="e238c-129">A new connector was added.</span></span>
> * <span data-ttu-id="e238c-130">Uma nova guia estática/pessoal foi adicionada.</span><span class="sxs-lookup"><span data-stu-id="e238c-130">A new static/personal tab was added.</span></span>
> * <span data-ttu-id="e238c-131">Uma nova guia de grupo/canal configurável foi adicionada.</span><span class="sxs-lookup"><span data-stu-id="e238c-131">A new configurable group/channel tab was added.</span></span>
> * <span data-ttu-id="e238c-132">Os `webApplicationInfo` valores foram alterados.</span><span class="sxs-lookup"><span data-stu-id="e238c-132">The `webApplicationInfo` values changed.</span></span>
>

### <a name="images-of-user-consent-flow"></a><span data-ttu-id="e238c-133">Imagens do fluxo de consentimento do usuário:</span><span class="sxs-lookup"><span data-stu-id="e238c-133">Images of user consent flow:</span></span>

<span data-ttu-id="e238c-134">**Configurar um conector —** Essa tela será exibida somente para usuários do Teams.</span><span class="sxs-lookup"><span data-stu-id="e238c-134">**Set up a connector** —  This screen will appear only for Teams users.</span></span>

![Configuração de fluxo de consentimento de um diagrama de conector](../../../../assets/images/connector-teams-consentflow.png)

<span data-ttu-id="e238c-136">**Fluxo de consentimento do** usuário - Essa tela é comum para escopo pessoal e de grupo.</span><span class="sxs-lookup"><span data-stu-id="e238c-136">**User consent flow** - This screen is common for both personal and group scope.</span></span> <span data-ttu-id="e238c-137">Aqui, marque a **caixa de seleção Consentimento em nome da** sua organização e escolha **Aceitar**.</span><span class="sxs-lookup"><span data-stu-id="e238c-137">Here, select the **Consent on behalf of your organization** checkbox and choose **Accept**.</span></span>

![Diagrama de permissões](../../../../assets/images/user-consent-flow.png)
