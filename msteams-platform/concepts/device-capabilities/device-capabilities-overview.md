---
title: Visão geral dos recursos do dispositivo
description: Visão geral dos recursos nativos do dispositivo.
keywords: permissões nativas de dispositivo nativo de recursos de microfone de imagem da câmera
ms.topic: overview
ms.openlocfilehash: 8b2f92cb4586d646bde02742883122bb009847ea
ms.sourcegitcommit: e3b6bc31059ec77de5fbef9b15c17d358abbca0f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/12/2021
ms.locfileid: "50232843"
---
# <a name="device-capabilities"></a><span data-ttu-id="8bcd4-104">Funcionalidades de dispositivo</span><span class="sxs-lookup"><span data-stu-id="8bcd4-104">Device capabilities</span></span> 

<span data-ttu-id="8bcd4-105">A plataforma Do Microsoft Teams está aprimorando continuamente os recursos do desenvolvedor de acordo com as experiências de terceiros.</span><span class="sxs-lookup"><span data-stu-id="8bcd4-105">Microsoft Teams platform is continuously enhancing developer capabilities aligning with built-in first-party experiences.</span></span> <span data-ttu-id="8bcd4-106">A plataforma aprimorada do Teams permite que os parceiros integrem recursos do dispositivo, como câmera, galeria de fotos, microfone e local, com seus aplicativos Web.</span><span class="sxs-lookup"><span data-stu-id="8bcd4-106">The enhanced Teams platform allows partners to integrate device capabilities, such as camera, photo gallery, microphone, and location, with their web apps.</span></span> <span data-ttu-id="8bcd4-107">Essa integração reduz a barreira para o desenvolvimento de aplicativos, acelera o ciclo de desenvolvimento e cria novos cenários ou casos de uso para a comunidade de desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="8bcd4-107">This integration reduces the barrier to app development, speeds-up development-cycle, and creates new scenarios or use-cases for the developer community.</span></span>

## <a name="native-device-capabilities"></a><span data-ttu-id="8bcd4-108">Recursos nativos do dispositivo</span><span class="sxs-lookup"><span data-stu-id="8bcd4-108">Native device capabilities</span></span>

<span data-ttu-id="8bcd4-109">Um dispositivo móvel ou desktop tem dispositivos integrados, como câmera e microfone, chamados de funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="8bcd4-109">A mobile or desktop device has built-in devices, such as a camera and microphone, called capabilities.</span></span> <span data-ttu-id="8bcd4-110">Você pode acessar os seguintes recursos de dispositivo em dispositivo móvel ou desktop por meio de APIs dedicadas disponíveis no [SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)do cliente JavaScript do Microsoft Teams:</span><span class="sxs-lookup"><span data-stu-id="8bcd4-110">You can access the following device capabilities on mobile or desktop through dedicated APIs available in [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true):</span></span>
* <span data-ttu-id="8bcd4-111">Recursos de mídia, como</span><span class="sxs-lookup"><span data-stu-id="8bcd4-111">Media capabilities, such as</span></span>
    * <span data-ttu-id="8bcd4-112">Câmera</span><span class="sxs-lookup"><span data-stu-id="8bcd4-112">Camera</span></span>
    * <span data-ttu-id="8bcd4-113">Microfone</span><span class="sxs-lookup"><span data-stu-id="8bcd4-113">Microphone</span></span>
    * <span data-ttu-id="8bcd4-114">Galeria</span><span class="sxs-lookup"><span data-stu-id="8bcd4-114">Gallery</span></span>
* <span data-ttu-id="8bcd4-115">Localização</span><span class="sxs-lookup"><span data-stu-id="8bcd4-115">Location</span></span>

<span data-ttu-id="8bcd4-116">Depois de obter acesso aos recursos do dispositivo, você pode integrá-los à plataforma do Teams para aprimorar a experiência colaborativa.</span><span class="sxs-lookup"><span data-stu-id="8bcd4-116">After getting access to the device capabilities, you can integrate them with Teams platform to enhance the collaborative experience.</span></span> 

## <a name="request-device-permissions"></a><span data-ttu-id="8bcd4-117">Solicitar permissões do dispositivo</span><span class="sxs-lookup"><span data-stu-id="8bcd4-117">Request device permissions</span></span>

<span data-ttu-id="8bcd4-118">Use as ferramentas presentes no [SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) do cliente [](native-device-permissions.md) JavaScript do Microsoft Teams para solicitar as permissões necessárias para acessar os recursos nativos do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="8bcd4-118">Use the tools present in [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) to  request the required  [permissions](native-device-permissions.md) for  accessing the native device capabilities.</span></span> <span data-ttu-id="8bcd4-119">Embora o acesso a esses recursos seja padrão em navegadores da Web modernos, você deve informar o Teams sobre os recursos que está usando atualizando o manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8bcd4-119">While access to these capabilities is standard in modern web browsers, you must inform Teams about the capabilities that you are using by updating your app manifest.</span></span> <span data-ttu-id="8bcd4-120">Essa atualização permite que você solicite permissões enquanto seu aplicativo é executado em clientes móveis ou da área de trabalho do Teams.</span><span class="sxs-lookup"><span data-stu-id="8bcd4-120">This update allows you to request permissions while your app runs on Teams mobile or desktop clients.</span></span>
 
 ## <a name="integrate-device-capabilities"></a><span data-ttu-id="8bcd4-121">Integrar recursos do dispositivo</span><span class="sxs-lookup"><span data-stu-id="8bcd4-121">Integrate device capabilities</span></span>

<span data-ttu-id="8bcd4-122">Depois de obter acesso aos recursos do dispositivo, use **as APIs** de recursos de mídia do Teams para integrar os recursos com a plataforma do Teams para melhorar a experiência do usuário. [](mobile-camera-image-permissions.md)</span><span class="sxs-lookup"><span data-stu-id="8bcd4-122">After getting access to device capabilities,use **Teams media capability APIs** to [integrate the capabilities](mobile-camera-image-permissions.md) with Teams platform to enhance the user experience.</span></span> <span data-ttu-id="8bcd4-123">Esses recursos integrados permitem que seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="8bcd4-123">These integrated capabilities allow your app to:</span></span>

* <span data-ttu-id="8bcd4-124">Capturar e compartilhar imagens</span><span class="sxs-lookup"><span data-stu-id="8bcd4-124">Capture and share images</span></span>
* <span data-ttu-id="8bcd4-125">Gravar áudio por meio do microfone</span><span class="sxs-lookup"><span data-stu-id="8bcd4-125">Record audio through microphone</span></span>
* <span data-ttu-id="8bcd4-126">Compartilhar as informações de localização</span><span class="sxs-lookup"><span data-stu-id="8bcd4-126">Share the location information</span></span>


