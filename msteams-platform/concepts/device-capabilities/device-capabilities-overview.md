---
title: Visão geral dos recursos do dispositivo
description: Visão geral dos recursos de dispositivo nativo.
keywords: camera image media microphone mic qr code qrcode bar code barcode barcode scan capabilities native device permissions
ms.topic: overview
ms.openlocfilehash: 03ce0267f7160772e30ec88de2c29f81886b5280
ms.sourcegitcommit: 6ff8d1244ac386641ebf9401804b8df3854b02dc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/18/2021
ms.locfileid: "50294723"
---
# <a name="device-capabilities"></a>Funcionalidades de dispositivo 

A plataforma do Microsoft Teams está aprimorando continuamente os recursos de desenvolvedor alinhando com experiências de primeira parte. A plataforma do Teams aprimorada permite que os parceiros integrem recursos de dispositivo, como câmera, QR ou scanner de código de barras, galeria de fotos, microfone e local com seus aplicativos Web. Essa integração reduz a barreira ao desenvolvimento de aplicativos, acelera o ciclo de desenvolvimento e cria novos cenários ou casos de uso para a comunidade de desenvolvedores.

## <a name="native-device-capabilities"></a>Recursos de dispositivo nativo

Um dispositivo móvel ou desktop tem dispositivos integrados, como uma câmera e um microfone, chamados de recursos. Você pode acessar os seguintes recursos de dispositivo em dispositivo móvel ou desktop por meio de APIs dedicadas disponíveis no [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true):
* Recursos de mídia, como
    * Câmera
    * Microfone
    * Galeria
    * QR ou scanner de código de barras
* Localização

Depois de obter acesso aos recursos do dispositivo, você pode integrá-los à plataforma do Teams para aprimorar a experiência colaborativa. 

## <a name="request-device-permissions"></a>Solicitar permissões do dispositivo

Use as ferramentas presentes no [SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) do cliente [](native-device-permissions.md) JavaScript do Microsoft Teams para solicitar as permissões necessárias para acessar os recursos do dispositivo nativo. Embora o acesso a esses recursos seja padrão em navegadores da Web modernos, você deve informar o Teams sobre os recursos que você está usando atualizando o manifesto do aplicativo. Essa atualização permite que você solicite permissões enquanto seu aplicativo é executado em clientes móveis ou de área de trabalho do Teams.
 
 ## <a name="integrate-device-capabilities"></a>Integrar recursos de dispositivo

Depois de obter acesso aos recursos do dispositivo, use APIs de recursos de mídia do Teams para integrar recursos de mídia com a plataforma do Teams para aprimorar a experiência do usuário. [](mobile-camera-image-permissions.md) Esses recursos integrados permitem que seu aplicativo:

* Capturar e compartilhar imagens
* Verificar QR ou código de barras usando o [controle de scanner](qr-barcode-scanner-capability.md)
* Gravar áudio por microfone
* Compartilhar as informações de local
