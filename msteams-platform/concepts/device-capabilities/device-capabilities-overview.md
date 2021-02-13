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
# <a name="device-capabilities"></a>Funcionalidades de dispositivo 

A plataforma Do Microsoft Teams está aprimorando continuamente os recursos do desenvolvedor de acordo com as experiências de terceiros. A plataforma aprimorada do Teams permite que os parceiros integrem recursos do dispositivo, como câmera, galeria de fotos, microfone e local, com seus aplicativos Web. Essa integração reduz a barreira para o desenvolvimento de aplicativos, acelera o ciclo de desenvolvimento e cria novos cenários ou casos de uso para a comunidade de desenvolvedores.

## <a name="native-device-capabilities"></a>Recursos nativos do dispositivo

Um dispositivo móvel ou desktop tem dispositivos integrados, como câmera e microfone, chamados de funcionalidades. Você pode acessar os seguintes recursos de dispositivo em dispositivo móvel ou desktop por meio de APIs dedicadas disponíveis no [SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)do cliente JavaScript do Microsoft Teams:
* Recursos de mídia, como
    * Câmera
    * Microfone
    * Galeria
* Localização

Depois de obter acesso aos recursos do dispositivo, você pode integrá-los à plataforma do Teams para aprimorar a experiência colaborativa. 

## <a name="request-device-permissions"></a>Solicitar permissões do dispositivo

Use as ferramentas presentes no [SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) do cliente [](native-device-permissions.md) JavaScript do Microsoft Teams para solicitar as permissões necessárias para acessar os recursos nativos do dispositivo. Embora o acesso a esses recursos seja padrão em navegadores da Web modernos, você deve informar o Teams sobre os recursos que está usando atualizando o manifesto do aplicativo. Essa atualização permite que você solicite permissões enquanto seu aplicativo é executado em clientes móveis ou da área de trabalho do Teams.
 
 ## <a name="integrate-device-capabilities"></a>Integrar recursos do dispositivo

Depois de obter acesso aos recursos do dispositivo, use **as APIs** de recursos de mídia do Teams para integrar os recursos com a plataforma do Teams para melhorar a experiência do usuário. [](mobile-camera-image-permissions.md) Esses recursos integrados permitem que seu aplicativo:

* Capturar e compartilhar imagens
* Gravar áudio por meio do microfone
* Compartilhar as informações de localização


