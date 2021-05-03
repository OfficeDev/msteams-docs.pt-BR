---
title: Solicitar permissões de dispositivo para seu Microsoft Teams app
keywords: Permissões de recursos de aplicativos do teams
description: Como atualizar o manifesto do aplicativo para solicitar acesso a recursos nativos que geralmente exigem consentimento do usuário
localization_priority: Normal
ms.topic: how-to
ms.openlocfilehash: 452840c5809da32a79c231f85cd1de9f8746367a
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019850"
---
# <a name="request-device-permissions-for-your-microsoft-teams-app"></a>Solicitar permissões de dispositivo para seu Microsoft Teams app

Você pode enriquecer seu Teams com recursos de dispositivo nativos, como câmera, microfone e local. Este documento orienta você sobre como solicitar o consentimento do usuário e acessar as permissões de dispositivo nativo.

> [!NOTE]
> * Para integrar recursos de mídia ao seu Microsoft Teams aplicativo móvel, consulte [Integrar recursos de mídia.](mobile-camera-image-permissions.md)
> * Para integrar a QR ou o recurso de scanner de código de barras no seu aplicativo móvel Microsoft Teams, consulte Integrar o recurso de scanner de código de barras ou [QR](qr-barcode-scanner-capability.md) no Teams
> * Para integrar recursos de localização ao Microsoft Teams aplicativo móvel, consulte [Integrar recursos de localização.](location-capability.md)

## <a name="native-device-permissions"></a>Permissões de dispositivo nativo

Você deve solicitar as permissões de dispositivo para acessar recursos de dispositivo nativos. As permissões de dispositivo funcionam da mesma forma para todas as construções de aplicativo, como guias, módulos de tarefa ou extensões de mensagens. O usuário deve ir para a página permissões em Teams para gerenciar permissões de dispositivo.
Ao acessar os recursos do dispositivo, você pode criar experiências mais ricas na plataforma Teams, como:
* Capturar e exibir imagens.
* Verificar QR ou código de barras.
* Grave e compartilhe vídeos curtos.
* Grave memorandos de áudio e salve-os para uso posterior.
* Use as informações de local do usuário para exibir informações relevantes.

## <a name="access-device-permissions"></a>Permissões de dispositivo de acesso

O [Microsoft Teams SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) do cliente JavaScript fornece as ferramentas necessárias para seu aplicativo móvel Teams acessar as permissões de dispositivo [do](#manage-permissions) usuário e criar uma experiência mais rica.

Embora o acesso a esses recursos seja padrão em navegadores da Web modernos, você deve informar Teams sobre os recursos que você usa atualizando o manifesto do aplicativo. Essa atualização permite que você peça permissões enquanto seu aplicativo é executado no Teams desktop.

> [!NOTE] 
> Atualmente, o Microsoft Teams suporte para recursos de mídia e o recurso de scanner de código de barras QR está disponível apenas para clientes móveis.

## <a name="manage-permissions"></a>Gerenciar permissões

Um usuário pode gerenciar permissões de dispositivo em Teams configurações selecionando **Permitir** ou **Negar** permissões para aplicativos específicos.
 
# <a name="desktop"></a>[Desktop](#tab/desktop)

1. Abra seu Teams aplicativo.
1. Selecione seu ícone de perfil no canto superior direito da janela.
1. Selecione **Configurações**  >  **Permissões** no menu suspenso.
1. Selecione as configurações desejadas.

   ![Tela de configurações da área de trabalho de permissões do dispositivo](../../assets/images/tabs/device-permissions.png)

# <a name="mobile"></a>[Mobile](#tab/mobile)

1. Abra Teams.
1. Vá para **Configurações**  >  **Permissões do Aplicativo.**
1. Selecione o aplicativo para o qual você precisa escolher as configurações.
1. Selecione as configurações desejadas.

    ![Tela de configurações móveis de permissões de dispositivo](../../assets/images/tabs/MobilePermissions.png)

---

## <a name="specify-permissions"></a>Especificar permissões

Atualize o aplicativo adicionando e especificando qual das cinco propriedades `manifest.json` que você usa em seu `devicePermissions` aplicativo:

``` json
"devicePermissions": [
    "media",
    "geolocation",
    "notifications",
    "midi",
    "openExternal"
],
```

Cada propriedade permite solicitar que o usuário peça seu consentimento:

| Propriedade      | Descrição   |
| --- | --- |
| media         | Permissão para usar a câmera, o microfone, os alto-falantes e a galeria de mídia de acesso. |
| geolocalização   | Permissão para retornar a localização do usuário.      |
| notificações | Permissão para enviar as notificações do usuário.      |
| midi          | Permissão para enviar e receber informações de MIDI (Interface Digital de Instrumento Musical) de um instrumento digital.   |
| openExternal  | Permissão para abrir links em aplicativos externos.  |

## <a name="check-permissions-from-your-app"></a>Verificar permissões do seu aplicativo

Depois de `devicePermissions` adicionar ao manifesto do aplicativo, verifique permissões usando a API de permissões **HTML5** sem causar um prompt:

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

## <a name="use-teams-apis-to-get-device-permissions"></a>Usar Teams APIs para obter permissões de dispositivo

Aproveite o HTML5 ou Teams API apropriada, para exibir um prompt para obter consentimento para acessar permissões de dispositivo.

> [!IMPORTANT]
> * Suporte para `camera` , e está habilitado por meio da API `gallery` `microphone` [**selectMedia**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true). Use [**a API captureImage**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true) para uma única captura de imagem.
> * O suporte `location` para é habilitado por meio da API [**getLocation.**](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true) Você deve usá-lo para localização, pois a API de localização geográfica HTML5 não tem suporte total no Teams `getLocation API` de área de trabalho.

Por exemplo:
 * Para solicitar que o usuário acesse sua localização, você deve chamar `getCurrentPosition()` :

    ```Javascript
    navigator.geolocation.getCurrentPosition    (function (position) { /*... */ });
    ```

 * Para solicitar que o usuário acesse sua câmera na área de trabalho ou na Web, você deve chamar `getUserMedia()` :

    ```Javascript
    navigator.mediaDevices.getUserMedia({ audio: true, video: true });
    ```

 * Para capturar a imagem no celular, Teams celular pede permissão quando você chama `captureImage()` :

    ```Javascript
    microsoftTeams.media.captureImage((error: microsoftTeams.SdkError, files: microsoftTeams.media.File[]) => {
      /* ... */
    });
    ```

 * As notificações solicitarão ao usuário quando você chamar `requestPermission()` :

    ```Javascript
    Notification.requestPermission(function(result) { /* ... */ });
    ```




* Para usar a câmera ou a galeria de fotos de acesso, Teams celular pede permissão quando você chama `selectMedia()` :

    ```JavaScript
    microsoftTeams.media.selectMedia({ maxMediaCount: 10, mediaType: microsoftTeams.media.MediaType.Image }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
      /* ... */
    );
    ```

* Para usar o microfone, Teams celular pede permissão quando você chama `selectMedia()` :

    ```JavaScript 
    microsoftTeams.media.selectMedia({ maxMediaCount: 1, mediaType: microsoftTeams.media.MediaType.Audio }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
      /* ... */
    });
    ```

* Para solicitar que o usuário compartilhe o local na interface do mapa, Teams celular pede permissão quando você chama `getLocation()` :

    ```JavaScript 
    microsoftTeams.location.getLocation({ allowChooseLocation: true, showMap: true }, (error: microsoftTeams.SdkError, location: microsoftTeams.location.Location) => {
      /* ... *
    /});
    ```
# <a name="desktop"></a>[Desktop](#tab/desktop)

   ![Guia solicitação de permissões do dispositivo da área de trabalho](~/assets/images/tabs/device-permissions-prompt.png)

# <a name="mobile"></a>[Mobile](#tab/mobile)

   ![Guia solicitação de permissões de dispositivo móvel](../../assets/images/tabs/MobileLocationPermission.png)

* * * 

## <a name="permission-behavior-across-login-sessions"></a>Comportamento de permissão em sessões de logon

As permissões do dispositivo são armazenadas para cada sessão de logon. Isso significa que, se você entrar em outra instância do Teams, por exemplo, em outro computador, as permissões do dispositivo de suas sessões anteriores não estarão disponíveis. Portanto, você deve consentir de novo as permissões de dispositivo para a nova sessão. Isso também significa que, se você sair do Teams ou alternar locatários no Teams, suas permissões de dispositivo serão excluídas da sessão de logon anterior.  

> [!NOTE]
> Quando você consente com as permissões de dispositivo nativo, ela é válida somente para a _sessão de_ logon atual.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Integrar recursos de mídia no Teams](mobile-camera-image-permissions.md)

> [!div class="nextstepaction"]
> [Integrar a QR ou o recurso de scanner de código de barras Teams](qr-barcode-scanner-capability.md)

> [!div class="nextstepaction"]
> [Integrar recursos de localização Teams](location-capability.md)
