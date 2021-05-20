---
title: Recursos do dispositivo - Visão geral
author: Rajeshwari-v
description: Visão geral das capacidades dos dispositivos nativos.
ms.author: surbhigupta
keywords: microfone de mídia da câmera microfone qr code qrcode código barra código código de barras de código de barras mapa de localização mapa de localização recursos de permissões de dispositivo nativo
localization_priority: Normal
ms.topic: overview
ms.openlocfilehash: 8df8341e8996e4bf380575ac59e05325da16bd0d
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566191"
---
# <a name="device-capabilities"></a><span data-ttu-id="31f66-104">Funcionalidades de dispositivo</span><span class="sxs-lookup"><span data-stu-id="31f66-104">Device capabilities</span></span>

<span data-ttu-id="31f66-105">Microsoft Teams plataforma está continuamente melhorando os recursos do desenvolvedor alinhando-se com experiências de primeira parte incorporadas.</span><span class="sxs-lookup"><span data-stu-id="31f66-105">Microsoft Teams platform is continuously enhancing developer capabilities aligning with built-in first-party experiences.</span></span> <span data-ttu-id="31f66-106">A plataforma aprimorada Teams permite que os parceiros integrem recursos de dispositivos, como câmera, QR ou scanner de código de barras, galeria de fotos, microfone e localização com seus aplicativos web.</span><span class="sxs-lookup"><span data-stu-id="31f66-106">The enhanced Teams platform allows partners to integrate device capabilities, such as camera, QR or barcode scanner, photo gallery, microphone, and location with their web apps.</span></span> <span data-ttu-id="31f66-107">Essa integração reduz a barreira ao desenvolvimento de aplicativos, acelera o ciclo de desenvolvimento e cria novos cenários ou casos de uso para a comunidade de desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="31f66-107">This integration reduces the barrier to app development, speeds-up development-cycle, and creates new scenarios or use-cases for the developer community.</span></span>

## <a name="native-device-capabilities"></a><span data-ttu-id="31f66-108">Recursos de dispositivos nativos</span><span class="sxs-lookup"><span data-stu-id="31f66-108">Native device capabilities</span></span>

<span data-ttu-id="31f66-109">Um dispositivo móvel ou desktop tem dispositivos integrados, como uma câmera e microfone, chamados recursos.</span><span class="sxs-lookup"><span data-stu-id="31f66-109">A mobile or desktop device has built-in devices, such as a camera and microphone, called capabilities.</span></span> <span data-ttu-id="31f66-110">Você pode acessar os seguintes recursos do dispositivo no celular ou desktop através de APIs dedicadas disponíveis em [Microsoft Teams SDK cliente JavaScript](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true):</span><span class="sxs-lookup"><span data-stu-id="31f66-110">You can access the following device capabilities on mobile or desktop through dedicated APIs available in [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true):</span></span>
* <span data-ttu-id="31f66-111">Recursos de mídia, como</span><span class="sxs-lookup"><span data-stu-id="31f66-111">Media capabilities, such as</span></span>
    * <span data-ttu-id="31f66-112">câmera</span><span class="sxs-lookup"><span data-stu-id="31f66-112">Camera</span></span>
    * <span data-ttu-id="31f66-113">microfone</span><span class="sxs-lookup"><span data-stu-id="31f66-113">Microphone</span></span>
    * <span data-ttu-id="31f66-114">Galeria</span><span class="sxs-lookup"><span data-stu-id="31f66-114">Gallery</span></span>
    * <span data-ttu-id="31f66-115">QR ou scanner de código de barras</span><span class="sxs-lookup"><span data-stu-id="31f66-115">QR or barcode scanner</span></span>
* <span data-ttu-id="31f66-116">Local</span><span class="sxs-lookup"><span data-stu-id="31f66-116">Location</span></span>

<span data-ttu-id="31f66-117">Depois de ter acesso aos recursos do dispositivo, você pode integrá-los com Teams plataforma para melhorar a experiência colaborativa.</span><span class="sxs-lookup"><span data-stu-id="31f66-117">After getting access to the device capabilities, you can integrate them with Teams platform to enhance the collaborative experience.</span></span> 

## <a name="request-device-permissions"></a><span data-ttu-id="31f66-118">Solicitar permissões do dispositivo</span><span class="sxs-lookup"><span data-stu-id="31f66-118">Request device permissions</span></span>

<span data-ttu-id="31f66-119">Use as ferramentas presentes no [Microsoft Teams cliente JavaScript SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) para solicitar as [permissões necessárias](native-device-permissions.md) para acessar os recursos do dispositivo nativo.</span><span class="sxs-lookup"><span data-stu-id="31f66-119">Use the tools present in [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) to request the required  [permissions](native-device-permissions.md) for accessing the native device capabilities.</span></span> <span data-ttu-id="31f66-120">Embora o acesso a esses recursos seja padrão em navegadores da Web modernos, você deve informar Teams sobre os recursos que você está usando atualizando seu manifesto de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="31f66-120">While access to these capabilities is standard in modern web browsers, you must inform Teams about the capabilities that you are using by updating your app manifest.</span></span> <span data-ttu-id="31f66-121">Esta atualização permite que você solicite permissões enquanto seu aplicativo é executado em Teams clientes móveis ou desktop.</span><span class="sxs-lookup"><span data-stu-id="31f66-121">This update allows you to request permissions while your app runs on Teams mobile or desktop clients.</span></span>
 
 ## <a name="integrate-device-capabilities"></a><span data-ttu-id="31f66-122">Integrar recursos de dispositivos</span><span class="sxs-lookup"><span data-stu-id="31f66-122">Integrate device capabilities</span></span>

<span data-ttu-id="31f66-123">Depois de obter acesso aos recursos do dispositivo, use Teams APIs de recursos de mídia para [integrar recursos de mídia](mobile-camera-image-permissions.md) com Teams plataforma para melhorar a experiência do usuário.</span><span class="sxs-lookup"><span data-stu-id="31f66-123">After getting access to device capabilities, use Teams media capability APIs to [integrate media capabilities](mobile-camera-image-permissions.md) with Teams platform to enhance the user experience.</span></span> <span data-ttu-id="31f66-124">Esses recursos integrados permitem que seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="31f66-124">These integrated capabilities allow your app to:</span></span>

* <span data-ttu-id="31f66-125">Capturar e compartilhar imagens.</span><span class="sxs-lookup"><span data-stu-id="31f66-125">Capture and share images.</span></span>
* <span data-ttu-id="31f66-126">Digitalize QR ou código de barras usando [controle de scanner](qr-barcode-scanner-capability.md).</span><span class="sxs-lookup"><span data-stu-id="31f66-126">Scan QR or barcode using [scanner control](qr-barcode-scanner-capability.md).</span></span>
* <span data-ttu-id="31f66-127">Grave áudio através do microfone.</span><span class="sxs-lookup"><span data-stu-id="31f66-127">Record audio through microphone.</span></span>
* <span data-ttu-id="31f66-128">Compartilhar localização usando [o localizador](location-capability.md)de localização .</span><span class="sxs-lookup"><span data-stu-id="31f66-128">Share location using [location picker](location-capability.md).</span></span>
