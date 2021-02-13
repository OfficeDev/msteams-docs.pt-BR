---
title: Solicitar permissões de dispositivo para seu aplicativo microsoft Teams
keywords: permissões de recursos de aplicativos do Teams
description: Como atualizar o manifesto do aplicativo para solicitar acesso a recursos nativos que geralmente exigem consentimento do usuário
ms.topic: how-to
ms.openlocfilehash: 0343754eacbb6088a3e44fa5df8ec90e3b10b076
ms.sourcegitcommit: e3b6bc31059ec77de5fbef9b15c17d358abbca0f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/12/2021
ms.locfileid: "50231607"
---
# <a name="request-device-permissions-for-your-microsoft-teams-app"></a>Solicitar permissões de dispositivo para seu aplicativo microsoft Teams

Você pode enriquecer seu aplicativo teams com recursos nativos do dispositivo, como câmera, microfone e localização. Este documento orienta você sobre como solicitar o consentimento do usuário e acessar as permissões do dispositivo nativo.

> [!NOTE]
> Para integrar recursos de mídia ao seu aplicativo móvel do Microsoft Teams, confira [Integrar recursos de mídia.](mobile-camera-image-permissions.md)

## <a name="native-device-permissions"></a>Permissões de dispositivo nativo

Você deve solicitar as permissões do dispositivo para acessar as funcionalidades nativas do dispositivo. As permissões de dispositivo funcionam da mesma forma para todas as construções de aplicativo, como guias, módulos de tarefa ou extensões de mensagens. O usuário deve ir para a página de permissões nas configurações do Teams para gerenciar as permissões do dispositivo.
Ao acessar os recursos do dispositivo, você pode criar experiências mais completas na plataforma do Teams, como:
* Capturar e exibir imagens.
* Grave e compartilhe vídeos curtos.
* Grave memorandos de áudio e salve-os para uso posterior.
* Use as informações de local do usuário para exibir informações relevantes.

## <a name="access-device-permissions"></a>Acessar permissões de dispositivo

O [SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) do cliente JavaScript do Microsoft Teams fornece as ferramentas [](#manage-permissions) necessárias para que seu aplicativo móvel do Teams acesse as permissões de dispositivo do usuário e crie uma experiência mais rica.

Embora o acesso a esses recursos seja padrão em navegadores da Web modernos, você deve informar o Teams sobre os recursos que você usa atualizando o manifesto do aplicativo. Essa atualização permite que você peça permissões enquanto seu aplicativo é executado no cliente da área de trabalho do Teams.

> [!NOTE] 
> Atualmente, o suporte do Microsoft Teams para recursos de mídia só está disponível para clientes móveis.

## <a name="manage-permissions"></a>Gerenciar permissões

Um usuário pode gerenciar permissões de dispositivo nas  configurações do Teams selecionando **Permissões** Permitir ou Negar para aplicativos específicos.
 
# <a name="desktop"></a>[Desktop](#tab/desktop)

1. Abra seu aplicativo do Teams.
1. Selecione o ícone de perfil no canto superior direito da janela.
1. Selecione **Permissões de**  >  **Configurações** no menu suspenso.
1. Selecione as configurações desejadas.

   ![Tela de configurações da área de trabalho de permissões do dispositivo](../../assets/images/tabs/device-permissions.png)

# <a name="mobile"></a>[Mobile](#tab/mobile)

1. Abra o Teams.
1. Vá para **Configurações**  >  **de Permissões do Aplicativo.**
1. Selecione o aplicativo para o qual você precisa escolher as configurações.
1. Selecione as configurações desejadas.

    ![Tela de configurações móveis de permissões do dispositivo](../../assets/images/tabs/MobilePermissions.png)

---

## <a name="specify-permissions"></a>Especificar permissões

Atualize seus aplicativos `manifest.json` adicionando `devicePermissions` e especificando quais das cinco propriedades você usa em seu aplicativo:

``` json
"devicePermissions": [
    "media",
    "geolocation",
    "notifications",
    "midi",
    "openExternal"
],
```

Cada propriedade permite que você peça ao usuário que peça seu consentimento:

| Propriedade      | Descrição   |
| --- | --- |
| mídia         | Permissão para usar a câmera, o microfone, os alto-falantes e a galeria de mídia de acesso. |
| geolocalização   | Permissão para retornar a localização do usuário.      |
| notifications | Permissão para enviar as notificações do usuário.      |
| midi          | Permissão para enviar e receber informações MIDI (Interface Digital de Instrumento Digital) de um instrumento digital.   |
| openExternal  | Permissão para abrir links em aplicativos externos.  |

## <a name="check-permissions-from-your-app"></a>Verificar permissões do seu aplicativo

Depois de `devicePermissions` adicionar ao manifesto do aplicativo, verifique as permissões usando a API de permissões **HTML5** sem causar um aviso:

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

## <a name="use-teams-apis-to-get-device-permissions"></a>Usar APIs do Teams para obter permissões de dispositivo

Aproveite o HTML5 apropriado ou a API do Teams para exibir uma solicitação de consentimento para acessar as permissões do dispositivo.

> [!IMPORTANT]
> * Suporte para `camera` , e é habilitado por meio de `gallery` `microphone` [**selectMedia API**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true). Use [**a API captureImage**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true) para uma única captura de imagem.
> * O suporte `location` para é habilitado por meio da API [**getLocation**](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true). Você deve usar isso para localização, pois a API de geolocalização HTML5 atualmente não é totalmente suportada no cliente de área de `getLocation API` trabalho do Teams.

Por exemplo:
 * Para solicitar que o usuário acesse sua localização, você deve `getCurrentPosition()` chamar:

    ```Javascript
    navigator.geolocation.getCurrentPosition    (function (position) { /*... */ });
    ```

 * Para solicitar que o usuário acesse a câmera na área de trabalho ou na Web, você deve `getUserMedia()` chamar:

    ```Javascript
    navigator.mediaDevices.getUserMedia({ audio: true, video: true });
    ```

 * Para capturar a imagem em dispositivos móveis, o Teams Mobile solicita permissão ao `captureImage()` chamar:

    ```Javascript
    microsoftTeams.media.captureImage((error: microsoftTeams.SdkError, files: microsoftTeams.media.File[]) => {
      /* ... */
    });
    ```

 * As notificações solicitarão ao usuário quando você `requestPermission()` chamar:

    ```Javascript
    Notification.requestPermission(function(result) { /* ... */ });
    ```




* Para usar a câmera ou acessar a galeria de fotos, o dispositivo móvel do Teams solicita permissão ao `selectMedia()` chamar:

    ```JavaScript
    microsoftTeams.media.selectMedia({ maxMediaCount: 10, mediaType: microsoftTeams.media.MediaType.Image }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
      /* ... */
    );
    ```

* Para usar o microfone, o dispositivo móvel do Teams solicita permissão ao `selectMedia()` chamar:

    ```JavaScript 
    microsoftTeams.media.selectMedia({ maxMediaCount: 1, mediaType: microsoftTeams.media.MediaType.Audio }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
      /* ... */
    });
    ```

* Para solicitar que o usuário compartilhe o local na interface de mapa, o dispositivo móvel do Teams solicita permissão quando você `getLocation()` chama:

    ```JavaScript 
    microsoftTeams.location.getLocation({ allowChooseLocation: true, showMap: true }, (error: microsoftTeams.SdkError, location: microsoftTeams.location.Location) => {
      /* ... *
    /});
    ```
# <a name="desktop"></a>[Desktop](#tab/desktop)

   ![Prompt de permissões do dispositivo da área de trabalho de guias](~/assets/images/tabs/device-permissions-prompt.png)

# <a name="mobile"></a>[Mobile](#tab/mobile)

   ![Prompt de permissões de dispositivo móvel de guias](../../assets/images/tabs/MobileLocationPermission.png)

* * * 

## <a name="permission-behavior-across-login-sessions"></a>Comportamento de permissão em sessões de logon

As permissões do dispositivo são armazenadas para cada sessão de logon. Isso significa que, se você entrar em outra instância do Teams, por exemplo, em outro computador, suas permissões de dispositivo de suas sessões anteriores não estarão disponíveis. Portanto, você deve consentir outra vez com as permissões de dispositivo para a nova sessão. Isso também significa que, se você sair do Teams ou mudar de locatário no Teams, suas permissões de dispositivo serão excluídas da sessão de logon anterior.  

> [!NOTE]
> Quando você consente com as permissões do dispositivo nativo, ele é válido somente para sua _sessão de_ logon atual.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Integrar recursos de mídia no Teams](mobile-camera-image-permissions.md)
