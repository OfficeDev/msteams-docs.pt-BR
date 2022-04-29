---
title: Solicitar permissões de dispositivo para seu aplicativo do Microsoft Teams
keywords: 'recursos de aplicativos do teams permissões de dispositivo escanear qt código de barra nativo imagem áudio vídeo '
description: Como atualizar o manifesto do aplicativo para solicitar acesso a recursos nativos que geralmente exigem o consentimento do usuário, como escanear qr, código de barras, imagem, áudio, recursos de vídeo
ms.localizationpriority: high
ms.topic: how-to
ms.openlocfilehash: cccf527c3abf3a1674b2d1350dd15633ba35c7a8
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111959"
---
# <a name="request-device-permissions-for-your-microsoft-teams-app"></a>Solicitar permissões de dispositivo para seu aplicativo do Microsoft Teams

Você pode enriquecer seu aplicativo Teams com recursos nativos do dispositivo, como câmera, microfone e localização. Este documento orienta você sobre como solicitar o consentimento do usuário e acessar as permissões do dispositivo nativo.

> [!NOTE]
>
> * Para integrar recursos de mídia em seu aplicativo móvel do Microsoft Teams, consulte [Integrar funcionalidades de mídia](mobile-camera-image-permissions.md).
> * Para integrar a funcionalidade de leitor de código de barras ou QR em seu aplicativo móvel do Microsoft Teams, consulte [Integrar funcionalidade de leitor QR ou de código de barras no Teams](qr-barcode-scanner-capability.md).
> * Para integrar recursos de mídia em seu aplicativo móvel do Microsoft Teams, consulte [Integrar funcionalidades de mídia](location-capability.md).

## <a name="native-device-permissions"></a>Permissões de dispositivo nativo

Você deve solicitar as permissões do dispositivo para acessar as funcionalidades nativas do dispositivo. As permissões do dispositivo funcionam da mesma forma para todos os constructos de aplicativo, como guias, módulos de tarefa ou extensões de mensagem. O usuário deve ir para a página de permissões nas configurações do Teams para gerenciar permissões de dispositivo.
Ao acessar os recursos do dispositivo, você pode criar experiências mais avançadas na plataforma do Teams, como:

* Capturar e exibir imagens.
* Digitalizar código QR ou de barras.
* Gravar e compartilhe vídeos curtos.
* Gravar memorandos de áudio e salvá-los para uso posterior.
* Usar as informações de localização do usuário para exibir informações relevantes.

> [!NOTE]
> * Atualmente, o Teams não dá suporte a permissões de dispositivo para aplicativos de várias janelas, guias e o painel lateral da reunião.
> * As permissões do dispositivo são diferentes no navegador. Para obter mais informações, consulte [Permissões de browser do dispositivo](browser-device-permissions.md).

## <a name="access-device-permissions"></a>Acesse Permissões de acesso

O [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) fornece as ferramentas necessárias para que seu aplicativo móvel do Teams’ acesse as [permissões de dispositivo](#manage-permissions)os usuários e crie uma experiência mais avançada.

Embora o acesso a esses recursos seja padrão em navegadores da Web modernos, você deve informar o Teams sobre os recursos usados atualizando o manifesto do aplicativo. Essa atualização permite que você solicite permissões enquanto seu aplicativo é executado no cliente da área de trabalho do Teams.

> [!NOTE]
> Atualmente, o suporte do Microsoft Teams para recursos de mídia e o recurso de leitor de código de barras e QR só está disponível para clientes móveis.

## <a name="manage-permissions"></a>Gerenciar permissões

Um usuário pode gerenciar permissões de dispositivo nas configurações do Teams selecionando **Permitir** ou **Negar** permissões para aplicativos específicos.

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

1. Abra o Teams.
1. Vá para **Configurações** > **Permissões de aplicativo**.
1. Selecione o aplicativo para o qual você precisa escolher as configurações.
1. Selecione as configurações desejadas.

    ![Tela de configurações móveis de permissões do dispositivo](../../assets/images/tabs/MobilePermissions.png)

# <a name="desktop"></a>[Desktop](#tab/desktop)

1. Abra seu aplicativo do Teams.
1. Selecione o ícone do seu perfil no canto superior direito da janela.
1. Selecione **Configurações** > **Permissões** no menu suspenso.
1. Selecione as configurações desejadas.

   ![Tela de configurações da área de trabalho de permissões do dispositivo](~/assets/images/tabs/device-permissions.png)

---

## <a name="specify-permissions"></a>Especificar permissões

Atualize o `manifest.json` do seu dispositivo adicionando `devicePermissions` e especificando qual das cinco propriedades a seguir você usa em seu aplicativo:

``` json
"devicePermissions": [
    "media",
    "geolocation",
    "notifications",
    "midi",
    "openExternal"
],
```

Cada propriedade permite que você solicite que o usuário solicite seu consentimento:

| Propriedade      | Descrição   |
| --- | --- |
| mídia         | Permissão para usar a câmera, o microfone, os alto-falantes e a galeria de mídia de acesso. |
| Localização geográfica   | Permissão para retornar a localização do usuário.      |
| notificações | Permissão para enviar notificações ao usuário.      |
| midi          | Permissão para enviar e receber informações de MIDI (Interface Digital de Instrumento Musical) de um instrumento musical digital.   |
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

## <a name="use-teams-apis-to-get-device-permissions"></a>Usar APIs do Teams para obter permissões de dispositivo

Aproveite o HTML5 apropriado ou a API do Teams para exibir uma solicitação para obter consentimento para acessar as permissões do dispositivo.

> [!IMPORTANT]
>
> * O suporte para `camera`, `gallery` e `microphone` é habilitado por meio da [**API selectMedia**](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true). Use a [**API captureImage**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true) para uma única captura de imagem.
> * O suporte para `location` é habilitado por meio da [**API getLocation**](/javascript/api/@microsoft/teams-js/microsoftteams.location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true). Você deve usar este `getLocation API` para localização, pois a API de geolocalização HTML5 não tem suporte total no cliente de área de trabalho do Teams.

Por exemplo:

* Para solicitar que o usuário acesse sua localização, você deve chamar `getCurrentPosition()`:

    ```JavaScript
    navigator.geolocation.getCurrentPosition    (function (position) { /*... */ });
    ```

* Para solicitar que o usuário acesse sua câmera na área de trabalho ou na Web, você deve chamar `getUserMedia()`:

    ```JavaScript
    navigator.mediaDevices.getUserMedia({ audio: true, video: true });
    ```

* Para capturar a imagem no celular, o Aplicativo móvel do Teams solicita permissão quando você chama`captureImage()`:

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

* Para usar a câmera ou acessar a galeria de fotos, o Aplicativo móvel do Teams solicita permissão quando você chama `selectMedia()`:

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

* Para usar o microfone, o Aplicativo móvel do Teams solicita permissão quando você chama `selectMedia()`:

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

* Para solicitar que o usuário compartilhe o local na interface do mapa, o Aplicativo móvel do Teams solicita permissão quando você chama `getLocation()`:

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

As permissões do dispositivo são armazenadas para cada sessão de logon. Isso significa que, se você entrar em outra instância do Teams, por exemplo, em outro computador, as permissões do dispositivo das sessões anteriores não estarão disponíveis. Portanto, você deve consentir novamente com as permissões do dispositivo para a nova sessão. Isso também significa que, se você sair do Teams ou mudar de locatário no Teams, as permissões do dispositivo serão excluídas da sessão de logon anterior.  

> [!NOTE]
> Quando você consente com as permissões de dispositivo nativo, ela é válida somente para a sessão de entrada _atual_.

## <a name="code-sample"></a>Exemplo de código

| **Nome de exemplo** | **Descrição** | **Node.js** |
|---------------|--------------|--------|
|Permissões de dispositivos | Usar o aplicativo de exemplo de guia do Microsoft Teams para demonstrar permissões de dispositivo |  [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-device-permissions/nodejs) |

## <a name="see-also"></a>Confira também

* [Permissões do dispositivo para o navegador](browser-device-permissions.md)
* [Integrar funcionalidades de mídia no Teams](mobile-camera-image-permissions.md)
* [Integrar o recurso de leitor de código QR ou de barras no Teams](qr-barcode-scanner-capability.md)
* [Integrar funcionalidades de localização no Teams](location-capability.md)
