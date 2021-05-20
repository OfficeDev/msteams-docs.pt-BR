---
title: Solicite permissões de dispositivos para o aplicativo Microsoft Teams
keywords: equipes aplicativos capacidades permissões
description: Como atualizar seu manifesto de aplicativo para solicitar acesso a recursos nativos que geralmente requerem o consentimento do usuário
localization_priority: Normal
ms.topic: how-to
ms.openlocfilehash: 34f84285dc883cc474cf1720c42b1699f76c6653
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566177"
---
# <a name="request-device-permissions-for-your-microsoft-teams-app"></a>Solicite permissões de dispositivos para o aplicativo Microsoft Teams

Você pode enriquecer seu aplicativo Teams com recursos nativos de dispositivos, como câmera, microfone e localização. Este documento orienta você sobre como solicitar o consentimento do usuário e acessar as permissões do dispositivo nativo.

> [!NOTE]
> * Para integrar os recursos de mídia dentro do aplicativo móvel Microsoft Teams, consulte [Integrar recursos de mídia](mobile-camera-image-permissions.md).
> * Para integrar o recurso de QR ou scanner de código de barras dentro do aplicativo móvel Microsoft Teams, consulte [integrar qr ou recurso de scanner de código de barras em Teams](qr-barcode-scanner-capability.md).
> * Para integrar os recursos de localização dentro do aplicativo móvel Microsoft Teams, consulte [Integrar recursos de localização](location-capability.md).

## <a name="native-device-permissions"></a>Permissões de dispositivos nativos

Você deve solicitar as permissões do dispositivo para acessar recursos de dispositivos nativos. As permissões do dispositivo funcionam de forma semelhante para todas as construções de aplicativos, como guias, módulos de tarefa ou extensões de mensagens. O usuário deve ir à página de permissões em Teams configurações para gerenciar permissões do dispositivo.
Ao acessar os recursos do dispositivo, você pode construir experiências mais ricas na plataforma Teams, tais como:
* Capturar e visualizar imagens.
* Digitalize QR ou código de barras.
* Grave e compartilhe vídeos curtos.
* Grave memorandos de áudio e guarde-os para uso posterior.
* Use as informações de localização do usuário para exibir informações relevantes.

## <a name="access-device-permissions"></a>Permissões de dispositivos de acesso

O [Microsoft Teams cliente JavaScript SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) fornece as ferramentas necessárias para que seu aplicativo móvel Teams acesse as [permissões](#manage-permissions) do dispositivo do usuário e construa uma experiência mais rica.

Embora o acesso a esses recursos seja padrão em navegadores da Web modernos, você deve informar Teams sobre os recursos que você usa atualizando seu manifesto de aplicativo. Esta atualização permite que você peça permissões enquanto seu aplicativo é executado no Teams cliente de desktop.

> [!NOTE] 
> Atualmente, Microsoft Teams suporte para recursos de mídia e capacidade de scanner de código de barras QR só está disponível para clientes móveis.

## <a name="manage-permissions"></a>Gerenciar permissões

Um usuário pode gerenciar permissões de dispositivos em configurações Teams selecionando **permitir** ou **negar** permissões a aplicativos específicos.
 
# <a name="desktop"></a>[Desktop](#tab/desktop)

1. Abra seu aplicativo de Teams.
1. Selecione seu ícone de perfil no canto superior direito da janela.
1. Selecione **Configurações**  >  **Permissões** no menu suspenso.
1. Selecione as configurações desejadas.

   ![Teste de configurações de desktop de permissões do dispositivo](../../assets/images/tabs/device-permissions.png)

# <a name="mobile"></a>[Mobile](#tab/mobile)

1. Abra Teams.
1. Vá para **Configurações**  >  **Permissões de aplicativos**.
1. Selecione o aplicativo para o qual você precisa escolher as configurações.
1. Selecione as configurações desejadas.

    ![Dispositivo permite tela de configurações móveis](../../assets/images/tabs/MobilePermissions.png)

---

## <a name="specify-permissions"></a>Especificar permissões

Atualize o aplicativo `manifest.json` adicionando `devicePermissions` e especificando quais das cinco propriedades que você usa em seu aplicativo:

``` json
"devicePermissions": [
    "media",
    "geolocation",
    "notifications",
    "midi",
    "openExternal"
],
```

Cada propriedade permite que você solicite ao usuário o seu consentimento:

| Propriedade      | Descrição   |
| --- | --- |
| mídia         | Permissão para usar a câmera, microfone, alto-falantes e galeria de mídia de acesso. |
| geolocalização   | Permissão para retornar a localização do usuário.      |
| Notificações | Permissão para enviar as notificações do usuário.      |
| Midi          | Permissão para enviar e receber informações de Interface Digital de Instrumentos Musicais (MIDI) de um instrumento musical digital.   |
| openExternal  | Permissão para abrir links em aplicativos externos.  |

## <a name="check-permissions-from-your-app"></a>Verifique as permissões do seu aplicativo

Depois de adicionar `devicePermissions` ao seu manifesto de aplicativo, verifique as permissões usando a **API de permissões HTML5** sem causar um prompt:

``` Javascript
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

## <a name="use-teams-apis-to-get-device-permissions"></a>Use Teams APIs para obter permissões de dispositivos

Aproveite a API apropriada HTML5 ou Teams, para exibir um prompt para obter consentimento para acessar permissões de dispositivos.

> [!IMPORTANT]
> * Suporte para `camera` , , e é `gallery` `microphone` habilitado através de [**API selectMedia**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true). Use [**a API captureImage**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true) para uma única captura de imagem.
> * O suporte `location` é ativado através da [**API getLocation**](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true). Você deve usá-lo `getLocation API` para localização, já que a API de geolocalização HTML5 não está totalmente suportada em Teams cliente de desktop.

Por exemplo:
 * Para solicitar que o usuário acesse sua localização, você deve ligar `getCurrentPosition()` para:

    ```Javascript
    navigator.geolocation.getCurrentPosition    (function (position) { /*... */ });
    ```

 * Para solicitar que o usuário acesse sua câmera no desktop ou web, você deve `getUserMedia()` ligar:

    ```Javascript
    navigator.mediaDevices.getUserMedia({ audio: true, video: true });
    ```

 * Para capturar a imagem no celular, Teams celular pede permissão quando você liga `captureImage()` :

    ```Javascript
    microsoftTeams.media.captureImage((error: microsoftTeams.SdkError, files: microsoftTeams.media.File[]) => {
      /* ... */
    });
    ```

 * As notificações solicitarão ao usuário quando você `requestPermission()` ligar:

    ```Javascript
    Notification.requestPermission(function(result) { /* ... */ });
    ```




* Para usar a câmera ou acessar a galeria de fotos, Teams celular pede permissão quando você `selectMedia()` liga:

    ```JavaScript
    microsoftTeams.media.selectMedia({ maxMediaCount: 10, mediaType: microsoftTeams.media.MediaType.Image }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
      /* ... */
    );
    ```

* Para usar o microfone, Teams celular pede permissão quando você `selectMedia()` liga:

    ```JavaScript 
    microsoftTeams.media.selectMedia({ maxMediaCount: 1, mediaType: microsoftTeams.media.MediaType.Audio }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
      /* ... */
    });
    ```

* Para solicitar que o usuário compartilhe a localização na interface do mapa, Teams celular pede permissão quando você liga `getLocation()` :

    ```JavaScript 
    microsoftTeams.location.getLocation({ allowChooseLocation: true, showMap: true }, (error: microsoftTeams.SdkError, location: microsoftTeams.location.Location) => {
      /* ... *
    /});
    ```
# <a name="desktop"></a>[Desktop](#tab/desktop)

   ![Guias de permissões de dispositivos de desktop solicitam](~/assets/images/tabs/device-permissions-prompt.png)

# <a name="mobile"></a>[Mobile](#tab/mobile)

   ![Guias de permissões de dispositivos móveis solicitam](../../assets/images/tabs/MobileLocationPermission.png)

* * * 

## <a name="permission-behavior-across-login-sessions"></a>Comportamento de permissão em sessões de login

As permissões do dispositivo são armazenadas para cada sessão de login. Isso significa que se você fizer login em outra instância de Teams, por exemplo, em outro computador, as permissões do seu dispositivo de suas sessões anteriores não estão disponíveis. Portanto, você deve re consentir com as permissões do dispositivo para a nova sessão. Também significa que, se você sair de Teams ou trocar de inquilinos em Teams, as permissões do dispositivo serão excluídas da sessão de login anterior.  

> [!NOTE]
> Quando você concorda com as permissões do dispositivo nativo, ele é válido apenas para a sua sessão de login _atual._

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Integrar recursos de mídia em Teams](mobile-camera-image-permissions.md)

> [!div class="nextstepaction"]
> [Integre o recurso de QR ou scanner de código de barras em Teams](qr-barcode-scanner-capability.md)

> [!div class="nextstepaction"]
> [Integre os recursos de localização em Teams](location-capability.md)
