---
title: Solicitar permissões de dispositivo para seu Microsoft Teams aplicativo
keywords: teams apps capabilities permissions device native scan qr barcode image audio video
description: Como atualizar o manifesto do aplicativo para solicitar acesso a recursos nativos que geralmente exigem o consentimento do usuário, como verificação de qr, código de barras, imagem, áudio, recursos de vídeo
ms.localizationpriority: medium
ms.topic: how-to
ms.openlocfilehash: 5269aed130714bc9afbe97b170d955d79d79abc8
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65103303"
---
# <a name="request-device-permissions-for-your-microsoft-teams-app"></a>Solicitar permissões de dispositivo para seu Microsoft Teams aplicativo

Você pode enriquecer seu Teams com recursos nativos do dispositivo, como câmera, microfone e local. Este documento orienta você sobre como solicitar o consentimento do usuário e acessar as permissões nativas do dispositivo.

> [!NOTE]
>
> * Para integrar recursos de mídia ao seu Microsoft Teams móvel, consulte [Integrar recursos de mídia](mobile-camera-image-permissions.md).
> * Para integrar a funcionalidade de scanner de código de barras ou QR em seu aplicativo móvel Microsoft Teams, consulte Integrar a [funcionalidade de QR](qr-barcode-scanner-capability.md) ou scanner de código de barras Teams.
> * Para integrar as funcionalidades de localização Microsoft Teams aplicativo móvel, consulte [Integrar funcionalidades de localização](location-capability.md).

## <a name="native-device-permissions"></a>Permissões de dispositivo nativo

Você deve solicitar as permissões do dispositivo para acessar as funcionalidades nativas do dispositivo. As permissões de dispositivo funcionam da mesma forma para todas as construções de aplicativo, como guias, módulos de tarefa ou extensões de mensagem. O usuário deve ir para a página de permissões Teams configurações para gerenciar permissões de dispositivo.
Ao acessar os recursos do dispositivo, você pode criar experiências mais avançadas Teams plataforma, como:

* Capturar e exibir imagens.
* Verificar QR ou código de barras.
* Grave e compartilhe vídeos curtos.
* Grave os memorandos de áudio e salve-os para uso posterior.
* Use as informações de localização do usuário para exibir informações relevantes.

> [!NOTE]
> * Atualmente, o Teams não dá suporte a permissões de dispositivo para aplicativos de várias janelas, guias e o painel lateral da reunião.
> * As permissões do dispositivo são diferentes no navegador. Para obter mais informações, consulte [permissões de dispositivo do navegador](browser-device-permissions.md).

## <a name="access-device-permissions"></a>Acessar permissões de dispositivo

O [Microsoft Teams SDK do cliente JavaScript](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) fornece as ferramentas necessárias para seu aplicativo móvel Teams acessar as permissões de dispositivo do usuário e criar [](#manage-permissions) uma experiência mais avançada.

Embora o acesso a esses recursos seja padrão em navegadores da Web modernos, você deve informar Teams sobre os recursos usados atualizando o manifesto do aplicativo. Essa atualização permite que você solicite permissões enquanto seu aplicativo é executado no Teams da área de trabalho.

> [!NOTE]
> Atualmente, o Microsoft Teams suporte para recursos de mídia e a funcionalidade de scanner de código de barras QR só está disponível para clientes móveis.

## <a name="manage-permissions"></a>Gerenciar permissões

Um usuário pode gerenciar permissões de dispositivo em Teams configurações selecionando Permitir ou **Negar permissões para** aplicativos específicos.

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

1. Abra Teams.
1. Vá para **Configurações** >  **Aplicações de Aplicativo**.
1. Selecione o aplicativo para o qual você precisa escolher as configurações.
1. Selecione as configurações desejadas.

    ![Tela de configurações móveis de permissões de dispositivo](../../assets/images/tabs/MobilePermissions.png)

# <a name="desktop"></a>[Desktop](#tab/desktop)

1. Abra seu Teams aplicativo.
1. Selecione o ícone de perfil no canto superior direito da janela.
1. Selecione **Configurações** >  **Permissões** no menu suspenso.
1. Selecione as configurações desejadas.

   ![Tela de configurações da área de trabalho de permissões de dispositivo](~/assets/images/tabs/device-permissions.png)

---

## <a name="specify-permissions"></a>Especificar permissões

Atualize o aplicativo adicionando `manifest.json` e `devicePermissions` especificando quais das cinco propriedades a seguir você usa em seu aplicativo:

``` json
"devicePermissions": [
    "media",
    "geolocation",
    "notifications",
    "midi",
    "openExternal"
],
```

Cada propriedade permite solicitar que o usuário solicite seu consentimento:

| Propriedade      | Descrição   |
| --- | --- |
| Mídia         | Permissão para usar a câmera, o microfone, os alto-falantes e a galeria de mídias de acesso. |
| Geolocalização   | Permissão para retornar a localização do usuário.      |
| Notificações | Permissão para enviar as notificações do usuário.      |
| Midi          | Permissão para enviar e receber informações de MIDI (Musical Instrument Digital Interface) de um instrumento musical digital.   |
| openExternal  | Permissão para abrir links em aplicativos externos.  |

## <a name="check-permissions-from-your-app"></a>Verificar permissões do seu aplicativo

Depois de adicionar `devicePermissions` ao manifesto do aplicativo, verifique as permissões usando a **API de permissões HTML5** sem causar um prompt:

``` JavaScript
// Different query options:
navigator.permissions.query({ name: 'camera' });
navigator.permissions.query({ name: 'microphone' });
navigator.permissions.query({ name: 'geolocation' });
navigator.permissions.query({ name: 'notifications' });
navigator.permissions.query({ name: 'midi', sysex: true });

// Example:
navigator.permissions.query({name:'geolocation'}).then(function(result) {
  if (result.state == 'granted') {
    // Access granted
  } else if (result.state == 'prompt') {
    // Access has not been granted
  }
});
```

## <a name="use-teams-apis-to-get-device-permissions"></a>Usar Teams APIs para obter permissões de dispositivo

Aproveite o HTML5 ou Teams API apropriada para exibir um prompt para obter consentimento para acessar permissões de dispositivo.

> [!IMPORTANT]
>
> * Suporte para `camera`, `gallery`e é `microphone` habilitado por meio [**da API selectMedia**](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true). Use [**a API captureImage**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true) para uma única captura de imagem.
> * O suporte para `location` é habilitado por meio da [**API getLocation**](/javascript/api/@microsoft/teams-js/microsoftteams.location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true). Você deve usar isso para `getLocation API` localização, pois a API de geolocalização HTML5 não tem suporte total no momento Teams de área de trabalho.

Por exemplo:

* Para solicitar que o usuário acesse sua localização, você deve chamar `getCurrentPosition()`:

    ```JavaScript
    navigator.geolocation.getCurrentPosition    (function (position) { /*... */ });
    ```

* Para solicitar que o usuário acesse sua câmera na área de trabalho ou na Web, você deve chamar `getUserMedia()`:

    ```JavaScript
    navigator.mediaDevices.getUserMedia({ audio: true, video: true });
    ```

* Para capturar a imagem no celular, Teams móvel solicita permissão quando você chama`captureImage()`:

    ```JavaScript
            function captureImage() {
            microsoftTeams.media.captureImage((error, files) => {
                // If there's any error, an alert shows the error message/code
                if (error) {
                    if (error.message) {
                        alert(" ErrorCode: " + error.errorCode + error.message);
                    } else {
                        alert(" ErrorCode: " + error.errorCode);
                    }
                } else if (files) {
                    image = files[0].content;
                    // Adding this image string in src attr of image tag will display the image on web page.
                    let imageString = "data:" + item.mimeType + ";base64," + image;
                }
            });
        } 
    ```

* As notificações avisarão o usuário quando você chamar `requestPermission()`:

    ```JavaScript
    Notification.requestPermission(function(result) { /* ... */ });
    ```

* Para usar a câmera ou acessar a galeria de fotos, Teams celular solicita permissão quando você chama`selectMedia()`:

    ```JavaScript
     function selectMedia() {
     microsoftTeams.media.selectMedia(mediaInput, (error, attachments) => {
         // If there's any error, an alert shows the error message/code
         if (error) {
             if (error.message) {
                 alert(" ErrorCode: " + error.errorCode + error.message);
             } else {
                 alert(" ErrorCode: " + error.errorCode);
             }
         } else if (attachments) {
             // creating image array which contains image string for all attached images. 
             const imageArray = attachments.map((item, index) => {
                 return ("data:" + item.mimeType + ";base64," + item.preview)
             })
         }
     });
    } 
  ```

* Para usar o microfone, Teams móvel solicita permissão quando você chama`selectMedia()`:

    ```JavaScript
     function selectMedia() {
     microsoftTeams.media.selectMedia({ maxMediaCount: 1, mediaType: microsoftTeams.media.MediaType.Audio }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
         // If there's any error, an alert shows the error message/code
         if (error) {
             if (error.message) {
                 alert(" ErrorCode: " + error.errorCode + error.message);
             } else {
                 alert(" ErrorCode: " + error.errorCode);
             }
         }

         if (attachments) {
             // taking the first attachment  
             let audioResult = attachments[0];

             // setting audio string which can be used in Video tag
             let audioData = "data:" + audioResult.mimeType + ";base64," + audioResult.preview
         }
     });
     }
    ```

* Para solicitar que o usuário compartilhe o local na interface do mapa, Teams mobile solicita permissão quando você chama`getLocation()`:

    ```JavaScript
     function getLocation() {
     microsoftTeams.location.getLocation({ allowChooseLocation: true, showMap: true }, (error: microsoftTeams.SdkError, location: microsoftTeams.location.Location) => {
         let currentLocation = JSON.stringify(location);
     });
     } 
    ```

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

   ![Prompt de permissões de dispositivo móvel de guias](../../assets/images/tabs/MobileLocationPermission.png)

# <a name="desktop"></a>[Desktop](#tab/desktop)

   ![Prompt de permissões do dispositivo da área de trabalho de guias](~/assets/images/tabs/device-permissions-prompt.png)

---

## <a name="permission-behavior-across-login-sessions"></a>Comportamento de permissão entre sessões de logon

As permissões de dispositivo são armazenadas para cada sessão de logon. Isso significa que, se você entrar em outra instância do Teams, por exemplo, em outro computador, as permissões do dispositivo das sessões anteriores não estarão disponíveis. Portanto, você deve consentir novamente com as permissões de dispositivo para a nova sessão. Isso também significa que, se você sair do Teams ou alternar locatários no Teams, as permissões do dispositivo serão excluídas da sessão de logon anterior.  

> [!NOTE]
> Quando você consente com as permissões de dispositivo nativo, ela é válida somente para a _sessão de logon_ atual.

## <a name="code-sample"></a>Exemplo de código

| **Nome de exemplo** | **Descrição** | **Node.js** |
|---------------|--------------|--------|
|Permissões de dispositivos | Usar Microsoft Teams aplicativo de exemplo de guia para demonstrar permissões de dispositivo |  [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-device-permissions/nodejs) |

## <a name="see-also"></a>Confira também

* [Permissões do dispositivo para o navegador](browser-device-permissions.md)
* [Integrar funcionalidades de mídia no Teams](mobile-camera-image-permissions.md)
* [Integrar a funcionalidade de scanner de código de barras ou QR Teams](qr-barcode-scanner-capability.md)
* [Integrar funcionalidades de localização no Teams](location-capability.md)
