---
title: Funcionalidades do dispositivo – Visão geral
author: Rajeshwari-v
description: Saiba como integrar recursos de dispositivo nativos, como câmera, imagem, mídia, microfone, código QR e muito mais com Microsoft Teams aplicativo.
ms.author: surbhigupta
ms.localizationpriority: medium
ms.topic: overview
ms.openlocfilehash: 8d5c288e35ef18ada9ff93390ff745798ba3b01c
ms.sourcegitcommit: eeaa8cbb10b9dfa97e9c8e169e9940ddfe683a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2022
ms.locfileid: "65757028"
---
# <a name="device-capabilities"></a>Funcionalidades de dispositivo

A plataforma Microsoft Teams está aprimorando continuamente os recursos do desenvolvedor, alinhando-se com experiências internas. A plataforma aprimorada do Teams permite que os parceiros integrem recursos de dispositivo, como câmera, QR ou scanner de código de barras, galeria de fotos, microfone e localização com seus aplicativos Web. Essa integração reduz a barreira para o desenvolvimento de aplicativos, acelera o ciclo de desenvolvimento e cria novos cenários ou casos de uso para a comunidade de desenvolvedores.

As permissões do dispositivo são diferentes no navegador. Anteriormente, o navegador manipula como conceder permissões de acesso e agora essas permissões são tratadas no Microsoft Teams. Para obter mais informações, consulte [Permissões de navegador da Web do dispositivo](browser-device-permissions.md).

## <a name="native-device-capabilities"></a>Funcionalidades nativas do dispositivo

Uma área de trabalho ou móvel tem dispositivos internos, como câmera e microfone, chamados de funcionalidades. Você pode acessar os seguintes recursos de dispositivo em dispositivos móveis ou desktop por meio de APIs dedicadas disponíveis no [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true):

* Recursos de mídia, como
  * Câmera
  * Microfone
  * Galeria
  * Scanner de QR ou código de barras
* Local

Depois de obter acesso aos recursos do dispositivo, você pode integrá-los à plataforma Teams para aprimorar a experiência colaborativa.

## <a name="request-device-permissions"></a>Solicitar permissões do dispositivo

Use as ferramentas presentes no [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) para solicitar as [permissões](native-device-permissions.md) necessárias para acessar os recursos nativos do dispositivo. Embora o acesso a esses recursos seja padrão em navegadores da Web modernos, você deve informar o Teams sobre os recursos que está usando atualizando o manifesto do aplicativo. Essa atualização permite que você solicite permissões enquanto seu aplicativo é executado em clientes móveis ou de área de trabalho do Teams.

## <a name="integrate-device-capabilities"></a>Integrar as funcionalidades do dispositivo

Depois de obter acesso aos recursos do dispositivo, use as APIs de funcionalidade de mídia do Teams para [Integrar recursos de mídia](mobile-camera-image-permissions.md) com a plataforma Teams para aprimorar a experiência do usuário. Esses recursos integrados permitem que seu aplicativo:

* Capturar e compartilhar imagens.
* Digitalize o QR ou código de barras usando [controle de scanner](qr-barcode-scanner-capability.md).
* Grave áudio por meio do microfone.
* Compartilhe a localização [seletor de localização](location-capability.md).

Além disso, você pode integrar o controle [seletor de pessoas](people-picker-capability.md) nativas do Teams que permite que os usuários pesquisem e selecionem pessoas na experiência do aplicativo Web.
