---
title: Permitir que seu aplicativo seja personalizado
author: heath-hamilton
description: Entenda como Teams administradores podem personalizar seu aplicativo para sua organização.
localization_priority: Normal
ms.author: surbhigupta
ms.topic: overview
ms.openlocfilehash: bf1b43629c87dd4123520c634772e5dea14e0bb5
ms.sourcegitcommit: 64c1cf2a268ef101a519bc31d171618d0f6cd12a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/13/2021
ms.locfileid: "52915080"
---
# <a name="enable-your-microsoft-teams-app-to-be-customized"></a><span data-ttu-id="de390-103">Permitir que seu Microsoft Teams aplicativo seja personalizado</span><span class="sxs-lookup"><span data-stu-id="de390-103">Enable your Microsoft Teams app to be customized</span></span>

<span data-ttu-id="de390-104">Você pode permitir que os clientes personalizem alguns aspectos do seu aplicativo Microsoft Teams no centro de Teams de administração.</span><span class="sxs-lookup"><span data-stu-id="de390-104">You can allow customers to customize some aspects of your Microsoft Teams app in the Teams admin center.</span></span> <span data-ttu-id="de390-105">Esse recurso só é suportado para aplicativos publicados no Teams store.</span><span class="sxs-lookup"><span data-stu-id="de390-105">This feature is supported only for apps published to the Teams store.</span></span> <span data-ttu-id="de390-106">Aplicativos e aplicativos com sideload publicados para uma organização não podem ser personalizados.</span><span class="sxs-lookup"><span data-stu-id="de390-106">Sideloaded apps and apps published for an org can't be customized.</span></span>

<span data-ttu-id="de390-107">Alguns exemplos possíveis desse recurso incluem:</span><span class="sxs-lookup"><span data-stu-id="de390-107">Some possible examples of this feature include:</span></span>

* <span data-ttu-id="de390-108">Alterar a cor de destaque do aplicativo para corresponder à marca de uma organização.</span><span class="sxs-lookup"><span data-stu-id="de390-108">Changing the app's accent color to match an org's brand.</span></span>
* <span data-ttu-id="de390-109">Atualizando o nome do aplicativo da *Contoso* para *o Agente Contoso*, que é o nome que os usuários da organização verão.</span><span class="sxs-lookup"><span data-stu-id="de390-109">Updating the app name from *Contoso* to *Contoso Agent*, which is the name users in the org will see.</span></span> <span data-ttu-id="de390-110">(Observação: os usuários adicionando um conector a um chat ou canal ainda verão o nome original do aplicativo, *Contoso*.)</span><span class="sxs-lookup"><span data-stu-id="de390-110">(Note: Users adding a connector to a chat or a channel will still see the original app name, *Contoso*.)</span></span>

<span data-ttu-id="de390-111">Você pode habilitar esse recurso no Portal do [Desenvolvedor para Teams](https://dev.teams.microsoft.com/home).</span><span class="sxs-lookup"><span data-stu-id="de390-111">You can enable this feature in the [Developer Portal for Teams](https://dev.teams.microsoft.com/home).</span></span> <span data-ttu-id="de390-112">Isso configura , que não estão disponíveis em versões anteriores `configurableProperties` a 1,10 do manifesto Teams aplicativo.</span><span class="sxs-lookup"><span data-stu-id="de390-112">This configures `configurableProperties`, which aren't available in versions prior to 1.10 of the Teams app manifest.</span></span>

## <a name="test-your-app"></a><span data-ttu-id="de390-113">Testar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="de390-113">Test your app</span></span>

<span data-ttu-id="de390-114">Não é possível testar esse recurso durante o desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="de390-114">You cannot test this feature during development.</span></span> <span data-ttu-id="de390-115">A personalização do aplicativo não é suportada para sideload ou publicação no catálogo de aplicativos de uma organização.</span><span class="sxs-lookup"><span data-stu-id="de390-115">App customization is not supported for sideloading or publishing to an organization's app catalog.</span></span>

## <a name="user-considerations"></a><span data-ttu-id="de390-116">Considerações do usuário</span><span class="sxs-lookup"><span data-stu-id="de390-116">User considerations</span></span>

<span data-ttu-id="de390-117">Como o editor de aplicativos, forneça as seguintes informações aos clientes em Teams administradores:</span><span class="sxs-lookup"><span data-stu-id="de390-117">As the app publisher, provide the following information to customers in Teams admins:</span></span>
* <span data-ttu-id="de390-118">Inclua uma observação recomendando testar alterações de personalização em um Teams de teste antes de fazer alterações em seu ambiente de produção.</span><span class="sxs-lookup"><span data-stu-id="de390-118">Include a note recommending to test customization changes in a Teams test tenant before making changes in their production environment.</span></span> 
* <span data-ttu-id="de390-119">Forneça práticas recomendadas para personalizar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="de390-119">Provide best practices for how to customize your app.</span></span>

## <a name="see-also"></a><span data-ttu-id="de390-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="de390-120">See also</span></span>

* [<span data-ttu-id="de390-121">Personalizar aplicativos no Teams de administração</span><span class="sxs-lookup"><span data-stu-id="de390-121">Customize apps in the Teams admin center</span></span>](/MicrosoftTeams/customize-apps)
