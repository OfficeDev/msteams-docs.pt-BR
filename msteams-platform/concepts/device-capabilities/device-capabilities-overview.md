---
title: Funcionalidades do dispositivo – Visão geral
author: Rajeshwari-v
description: Saiba como integrar recursos de dispositivo nativos, como localização e mídia (câmera, microfone, galeria, QR ou scanner de código de barras) com o aplicativo Microsoft Teams.
ms.author: surbhigupta
ms.localizationpriority: medium
ms.topic: overview
ms.openlocfilehash: 04ae1a0b21c12ef7dda5d4bf8dfa799ac5726d15
ms.sourcegitcommit: 75d0072c021609af33ce584d671f610d78b3aaef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2022
ms.locfileid: "68100564"
---
# <a name="device-capabilities"></a>Funcionalidades de dispositivo

A plataforma Microsoft Teams está aprimorando continuamente os recursos do desenvolvedor, alinhando-se com experiências internas. A plataforma aprimorada do Teams permite que os parceiros integrem recursos de dispositivo, como câmera, QR ou scanner de código de barras, galeria de fotos, microfone e localização com seus aplicativos Web. Essa integração reduz a barreira para o desenvolvimento de aplicativos, acelera o ciclo de desenvolvimento e cria novos cenários ou casos de uso para a comunidade de desenvolvedores.

As permissões do dispositivo são diferentes no navegador. Anteriormente, o navegador manipulava como conceder permissões de acesso e agora essas permissões são tratadas no Teams. Para obter mais informações, consulte [Permissões de navegador da Web do dispositivo](browser-device-permissions.md).

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

Depois de obter acesso aos recursos do dispositivo, use as APIs de funcionalidade de mídia do Teams para [Integrar recursos de mídia](media-capabilities.md) com a plataforma Teams para aprimorar a experiência do usuário. Esses recursos integrados permitem que seu aplicativo:

* Capturar e compartilhar imagens.
* Digitalize o QR ou código de barras usando [controle de scanner](qr-barcode-scanner-capability.md).
* Grave áudio por meio do microfone.
* Compartilhe a localização [seletor de localização](location-capability.md).

Além disso, você pode integrar o controle [seletor de pessoas](people-picker-capability.md) nativas do Teams que permite que os usuários pesquisem e selecionem pessoas na experiência do aplicativo Web.

## <a name="code-sample"></a>Exemplo de código

| Nome de exemplo           | Descrição | Node.js    |
|:---------------------|:--------------|:---------|
|Permissões de dispositivos | Descreve como demonstrar o aplicativo de exemplo de guia do Teams para permissões de dispositivo. |[View](<https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-device-permissions/nodejs>)|
