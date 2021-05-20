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
# <a name="device-capabilities"></a>Funcionalidades de dispositivo

Microsoft Teams plataforma está continuamente melhorando os recursos do desenvolvedor alinhando-se com experiências de primeira parte incorporadas. A plataforma aprimorada Teams permite que os parceiros integrem recursos de dispositivos, como câmera, QR ou scanner de código de barras, galeria de fotos, microfone e localização com seus aplicativos web. Essa integração reduz a barreira ao desenvolvimento de aplicativos, acelera o ciclo de desenvolvimento e cria novos cenários ou casos de uso para a comunidade de desenvolvedores.

## <a name="native-device-capabilities"></a>Recursos de dispositivos nativos

Um dispositivo móvel ou desktop tem dispositivos integrados, como uma câmera e microfone, chamados recursos. Você pode acessar os seguintes recursos do dispositivo no celular ou desktop através de APIs dedicadas disponíveis em [Microsoft Teams SDK cliente JavaScript](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true):
* Recursos de mídia, como
    * câmera
    * microfone
    * Galeria
    * QR ou scanner de código de barras
* Local

Depois de ter acesso aos recursos do dispositivo, você pode integrá-los com Teams plataforma para melhorar a experiência colaborativa. 

## <a name="request-device-permissions"></a>Solicitar permissões do dispositivo

Use as ferramentas presentes no [Microsoft Teams cliente JavaScript SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) para solicitar as [permissões necessárias](native-device-permissions.md) para acessar os recursos do dispositivo nativo. Embora o acesso a esses recursos seja padrão em navegadores da Web modernos, você deve informar Teams sobre os recursos que você está usando atualizando seu manifesto de aplicativo. Esta atualização permite que você solicite permissões enquanto seu aplicativo é executado em Teams clientes móveis ou desktop.
 
 ## <a name="integrate-device-capabilities"></a>Integrar recursos de dispositivos

Depois de obter acesso aos recursos do dispositivo, use Teams APIs de recursos de mídia para [integrar recursos de mídia](mobile-camera-image-permissions.md) com Teams plataforma para melhorar a experiência do usuário. Esses recursos integrados permitem que seu aplicativo:

* Capturar e compartilhar imagens.
* Digitalize QR ou código de barras usando [controle de scanner](qr-barcode-scanner-capability.md).
* Grave áudio através do microfone.
* Compartilhar localização usando [o localizador](location-capability.md)de localização .
