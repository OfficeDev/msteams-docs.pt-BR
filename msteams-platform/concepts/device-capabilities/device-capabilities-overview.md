---
title: Recursos do dispositivo - Visão geral
author: Rajeshwari-v
description: Visão geral dos recursos de dispositivo nativo.
ms.author: surbhigupta
keywords: câmera imagem microfone microfone de microfone qr code qrcode barra de código de barras código de barras de verificação do scanner de localização de mapa de recursos nativos do dispositivo permissões de dispositivo
localization_priority: Normal
ms.topic: overview
ms.openlocfilehash: 7d214e5011abdc83d2f6b5b49c2261359259035e
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020748"
---
# <a name="device-capabilities---overview"></a>Recursos do dispositivo - Visão geral

A plataforma do Microsoft Teams está aprimorando continuamente os recursos de desenvolvedor alinhando com experiências de primeira parte. A plataforma do Teams aprimorada permite que os parceiros integrem recursos de dispositivo, como câmera, QR ou scanner de código de barras, galeria de fotos, microfone e local com seus aplicativos Web. Essa integração reduz a barreira ao desenvolvimento de aplicativos, acelera o ciclo de desenvolvimento e cria novos cenários ou casos de uso para a comunidade de desenvolvedores.

## <a name="native-device-capabilities"></a>Recursos de dispositivo nativo

Um dispositivo móvel ou desktop tem dispositivos integrados, como uma câmera e um microfone, chamados de recursos. Você pode acessar os seguintes recursos de dispositivo em dispositivo móvel ou desktop por meio de APIs dedicadas disponíveis no [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true):
* Recursos de mídia, como
    * Câmera
    * Microfone
    * Galeria
    * QR ou scanner de código de barras
* Local

Depois de obter acesso aos recursos do dispositivo, você pode integrá-los à plataforma do Teams para aprimorar a experiência colaborativa. 

## <a name="request-device-permissions"></a>Solicitar permissões do dispositivo

Use as ferramentas presentes no [SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) do cliente [](native-device-permissions.md) JavaScript do Microsoft Teams para solicitar as permissões necessárias para acessar os recursos do dispositivo nativo. Embora o acesso a esses recursos seja padrão em navegadores da Web modernos, você deve informar o Teams sobre os recursos que você está usando atualizando o manifesto do aplicativo. Essa atualização permite que você solicite permissões enquanto seu aplicativo é executado em clientes móveis ou de área de trabalho do Teams.
 
 ## <a name="integrate-device-capabilities"></a>Integrar recursos de dispositivo

Depois de obter acesso aos recursos do dispositivo, use APIs de recursos de mídia do Teams para integrar recursos de mídia com a plataforma do Teams para aprimorar a experiência do usuário. [](mobile-camera-image-permissions.md) Esses recursos integrados permitem que seu aplicativo:

* Capturar e compartilhar imagens
* Verificar QR ou código de barras usando o [controle de scanner](qr-barcode-scanner-capability.md)
* Gravar áudio por microfone
* Compartilhar local usando [o se picker de localização](location-capability.md).
