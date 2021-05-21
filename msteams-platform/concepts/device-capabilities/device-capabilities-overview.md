---
title: Recursos do dispositivo - Visão geral
author: Rajeshwari-v
description: Visão geral dos recursos de dispositivo nativo.
ms.author: surbhigupta
keywords: câmera imagem microfone microfone de microfone qr code qrcode barra de código de barras código de barras de verificação do scanner de localização de mapa de recursos nativos do dispositivo permissões de dispositivo
localization_priority: Normal
ms.topic: overview
ms.openlocfilehash: 8df8341e8996e4bf380575ac59e05325da16bd0d
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566191"
---
# <a name="device-capabilities"></a><span data-ttu-id="9c2d0-104">Funcionalidades de dispositivo</span><span class="sxs-lookup"><span data-stu-id="9c2d0-104">Device capabilities</span></span>

<span data-ttu-id="9c2d0-105">Microsoft Teams plataforma está aprimorando continuamente os recursos de desenvolvedor alinhando com experiências de primeira parte.</span><span class="sxs-lookup"><span data-stu-id="9c2d0-105">Microsoft Teams platform is continuously enhancing developer capabilities aligning with built-in first-party experiences.</span></span> <span data-ttu-id="9c2d0-106">A plataforma Teams aprimorada permite que os parceiros integrem recursos de dispositivo, como câmera, QR ou scanner de código de barras, galeria de fotos, microfone e local com seus aplicativos Web.</span><span class="sxs-lookup"><span data-stu-id="9c2d0-106">The enhanced Teams platform allows partners to integrate device capabilities, such as camera, QR or barcode scanner, photo gallery, microphone, and location with their web apps.</span></span> <span data-ttu-id="9c2d0-107">Essa integração reduz a barreira ao desenvolvimento de aplicativos, acelera o ciclo de desenvolvimento e cria novos cenários ou casos de uso para a comunidade de desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="9c2d0-107">This integration reduces the barrier to app development, speeds-up development-cycle, and creates new scenarios or use-cases for the developer community.</span></span>

## <a name="native-device-capabilities"></a><span data-ttu-id="9c2d0-108">Recursos de dispositivo nativo</span><span class="sxs-lookup"><span data-stu-id="9c2d0-108">Native device capabilities</span></span>

<span data-ttu-id="9c2d0-109">Um dispositivo móvel ou desktop tem dispositivos integrados, como uma câmera e um microfone, chamados de recursos.</span><span class="sxs-lookup"><span data-stu-id="9c2d0-109">A mobile or desktop device has built-in devices, such as a camera and microphone, called capabilities.</span></span> <span data-ttu-id="9c2d0-110">Você pode acessar os seguintes recursos de dispositivo em dispositivo móvel ou desktop por meio de APIs dedicadas disponíveis [Microsoft Teams SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)do cliente JavaScript :</span><span class="sxs-lookup"><span data-stu-id="9c2d0-110">You can access the following device capabilities on mobile or desktop through dedicated APIs available in [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true):</span></span>
* <span data-ttu-id="9c2d0-111">Recursos de mídia, como</span><span class="sxs-lookup"><span data-stu-id="9c2d0-111">Media capabilities, such as</span></span>
    * <span data-ttu-id="9c2d0-112">Câmera</span><span class="sxs-lookup"><span data-stu-id="9c2d0-112">Camera</span></span>
    * <span data-ttu-id="9c2d0-113">Microfone</span><span class="sxs-lookup"><span data-stu-id="9c2d0-113">Microphone</span></span>
    * <span data-ttu-id="9c2d0-114">Galeria</span><span class="sxs-lookup"><span data-stu-id="9c2d0-114">Gallery</span></span>
    * <span data-ttu-id="9c2d0-115">QR ou scanner de código de barras</span><span class="sxs-lookup"><span data-stu-id="9c2d0-115">QR or barcode scanner</span></span>
* <span data-ttu-id="9c2d0-116">Local</span><span class="sxs-lookup"><span data-stu-id="9c2d0-116">Location</span></span>

<span data-ttu-id="9c2d0-117">Depois de obter acesso aos recursos do dispositivo, você pode integrá-los Teams plataforma para aprimorar a experiência colaborativa.</span><span class="sxs-lookup"><span data-stu-id="9c2d0-117">After getting access to the device capabilities, you can integrate them with Teams platform to enhance the collaborative experience.</span></span> 

## <a name="request-device-permissions"></a><span data-ttu-id="9c2d0-118">Solicitar permissões do dispositivo</span><span class="sxs-lookup"><span data-stu-id="9c2d0-118">Request device permissions</span></span>

<span data-ttu-id="9c2d0-119">Use as ferramentas presentes no [Microsoft Teams SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) do cliente [](native-device-permissions.md) JavaScript para solicitar as permissões necessárias para acessar os recursos do dispositivo nativo.</span><span class="sxs-lookup"><span data-stu-id="9c2d0-119">Use the tools present in [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) to request the required  [permissions](native-device-permissions.md) for accessing the native device capabilities.</span></span> <span data-ttu-id="9c2d0-120">Embora o acesso a esses recursos seja padrão em navegadores da Web modernos, você deve informar Teams sobre os recursos que você está usando atualizando o manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9c2d0-120">While access to these capabilities is standard in modern web browsers, you must inform Teams about the capabilities that you are using by updating your app manifest.</span></span> <span data-ttu-id="9c2d0-121">Essa atualização permite que você solicite permissões enquanto seu aplicativo é executado Teams clientes móveis ou desktop.</span><span class="sxs-lookup"><span data-stu-id="9c2d0-121">This update allows you to request permissions while your app runs on Teams mobile or desktop clients.</span></span>
 
 ## <a name="integrate-device-capabilities"></a><span data-ttu-id="9c2d0-122">Integrar recursos de dispositivo</span><span class="sxs-lookup"><span data-stu-id="9c2d0-122">Integrate device capabilities</span></span>

<span data-ttu-id="9c2d0-123">Depois de obter acesso aos recursos do dispositivo, use [](mobile-camera-image-permissions.md) Teams APIs de recursos de mídia para integrar recursos de mídia com Teams plataforma para aprimorar a experiência do usuário.</span><span class="sxs-lookup"><span data-stu-id="9c2d0-123">After getting access to device capabilities, use Teams media capability APIs to [integrate media capabilities](mobile-camera-image-permissions.md) with Teams platform to enhance the user experience.</span></span> <span data-ttu-id="9c2d0-124">Esses recursos integrados permitem que seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="9c2d0-124">These integrated capabilities allow your app to:</span></span>

* <span data-ttu-id="9c2d0-125">Capturar e compartilhar imagens.</span><span class="sxs-lookup"><span data-stu-id="9c2d0-125">Capture and share images.</span></span>
* <span data-ttu-id="9c2d0-126">Verificar QR ou código de barras usando o [controle de scanner](qr-barcode-scanner-capability.md).</span><span class="sxs-lookup"><span data-stu-id="9c2d0-126">Scan QR or barcode using [scanner control](qr-barcode-scanner-capability.md).</span></span>
* <span data-ttu-id="9c2d0-127">Gravar áudio por microfone.</span><span class="sxs-lookup"><span data-stu-id="9c2d0-127">Record audio through microphone.</span></span>
* <span data-ttu-id="9c2d0-128">Compartilhar local usando [o se picker de localização](location-capability.md).</span><span class="sxs-lookup"><span data-stu-id="9c2d0-128">Share location using [location picker](location-capability.md).</span></span>
