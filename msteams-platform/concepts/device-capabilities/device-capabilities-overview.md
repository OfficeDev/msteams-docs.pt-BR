---
title: Recursos do dispositivo - Visão geral
author: Rajeshwari-v
description: Visão geral dos recursos de dispositivo nativo, como câmera, imagem, mídia, microfone, microfone, código qr e muito mais.
ms.author: surbhigupta
keywords: câmera imagem microfone microfone de microfone qr code qrcode barra de código de barras código de barras de verificação do scanner de localização de mapa de recursos nativos do dispositivo permissões de dispositivo
ms.localizationpriority: medium
ms.topic: overview
ms.openlocfilehash: d51b9532822a6cb9df2f69975722d16da6ee2531
ms.sourcegitcommit: 1ac0bd55adfd49c42cd870dc71ceca3dcac70941
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2021
ms.locfileid: "61041710"
---
# <a name="device-capabilities"></a>Funcionalidades de dispositivo

Microsoft Teams plataforma está aprimorando continuamente os recursos de desenvolvedor alinhando com experiências de primeira parte. A plataforma Teams aprimorada permite que os parceiros integrem recursos de dispositivo, como câmera, QR ou scanner de código de barras, galeria de fotos, microfone e local com seus aplicativos Web. Essa integração reduz a barreira ao desenvolvimento de aplicativos, acelera o ciclo de desenvolvimento e cria novos cenários ou casos de uso para a comunidade de desenvolvedores.

As permissões do dispositivo são diferentes no navegador. Anteriormente, o navegador manipulava como conceder permissões de acesso e agora essas permissões são tratadas Microsoft Teams. Para obter mais informações, consulte [browser device permissions](browser-device-permissions.md).

## <a name="native-device-capabilities"></a>Recursos de dispositivo nativo

Um celular ou desktop tem dispositivos integrados, como câmera e microfone, chamados de recursos. Você pode acessar os seguintes recursos de dispositivo em dispositivo móvel ou desktop por meio de APIs dedicadas disponíveis [Microsoft Teams SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)do cliente JavaScript :
* Recursos de mídia, como
    * Câmera
    * Microfone
    * Galeria
    * QR ou scanner de código de barras
* Localização

Depois de obter acesso aos recursos do dispositivo, você pode integrá-los à plataforma Teams para aprimorar a experiência colaborativa. 

## <a name="request-device-permissions"></a>Solicitar permissões do dispositivo

Use as ferramentas presentes no [Microsoft Teams SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) do cliente [](native-device-permissions.md) JavaScript para solicitar as permissões necessárias para acessar os recursos do dispositivo nativo. Embora o acesso a esses recursos seja padrão em navegadores da Web modernos, você deve informar Teams sobre os recursos que você está usando atualizando o manifesto do aplicativo. Essa atualização permite que você solicite permissões enquanto seu aplicativo é executado Teams clientes móveis ou desktop.
 
 ## <a name="integrate-device-capabilities"></a>Integrar recursos de dispositivo

Depois de obter acesso aos recursos do dispositivo, [](mobile-camera-image-permissions.md) use Teams APIs de recursos de mídia para integrar recursos de mídia com a plataforma Teams para aprimorar a experiência do usuário. Esses recursos integrados permitem que seu aplicativo:

* Capturar e compartilhar imagens.
* Verificar QR ou código de barras usando o [controle de scanner](qr-barcode-scanner-capability.md).
* Gravar áudio por microfone.
* Compartilhar local usando [o se picker de localização](location-capability.md).

Além disso, você pode integrar [](people-picker-capability.md) o controle Teams seletor de pessoas nativas que permite que os usuários pesquisem e selecionem pessoas na experiência do aplicativo Web.
