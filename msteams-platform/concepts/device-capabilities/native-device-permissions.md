---
title: Solicitar permissões de dispositivo para a guia do Microsoft Teams
description: Como atualizar seu manifesto de aplicativo para solicitar acesso a recursos nativos que geralmente exigem o consentimento do usuário
keywords: desenvolvimento de guias do teams
ms.openlocfilehash: 6be183d2610616f3bd3bdf32554976322193c132
ms.sourcegitcommit: d0e71ea63af2f67eba75ba283ec46cc7cdf87d75
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/24/2020
ms.locfileid: "49731976"
---
# <a name="request-device-permissions-for-your-microsoft-teams-tab"></a>Solicitar permissões de dispositivo para a guia do Microsoft Teams

Você pode querer enriquecer sua guia com recursos que exigem acesso à funcionalidade de dispositivo nativo, como:

> [!div class="checklist"]
>
> * Câmara
> * Microfone
> * Local
> * Notificações

[!Note] Para integrar os recursos de câmera e imagem no seu aplicativo móvel do Microsoft Teams, consulte [recursos de câmera e imagem no Teams.](../../concepts/device-capabilities/mobile-camera-image-permissions.md)

> [!IMPORTANT]
>
> * No presente, o cliente do teams Mobile só dá suporte ao acesso a `camera` ,, `gallery` `mic` e `location` a recursos nativos do dispositivo e está disponível em todas as construções de aplicativos, incluindo guias. </br>
> * Suporte para `camera` , `gallery` e `mic` é habilitado por meio da [**API selectMedia**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true). Para captura de imagem única, você pode usar a [**API captureImage**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true).
> * O suporte para `location` é habilitado por meio da [**API getLocation**](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true). É recomendável usar esta API como a [**API de geolocalização**](../../resources/schema/manifest-schema.md#devicepermissions) não é totalmente suportada em todos os clientes de desktop.

## <a name="device-permissions"></a>Permissões de dispositivos

O acesso às permissões de dispositivo de um usuário permite que você construa experiências muito mais ricas, por exemplo:

* Gravar e compartilhar vídeos curtos
* Gravar memorandos de áudio curtos e salvá-los para mais tarde
* Usar informações de local de usuário para exibir informações relevantes

Embora o acesso a esses recursos seja padrão nos navegadores da Web mais modernos, você precisa permitir que as equipes saibam quais recursos você gostaria de usar atualizando o manifesto do aplicativo. Isso permitirá que você solicite permissões, da mesma forma que faria em um navegador, enquanto seu aplicativo está sendo executado no cliente de área de trabalho do Microsoft Teams.

## <a name="manage-permissions"></a>Gerenciar permissões

# <a name="desktop"></a>[Desktop](#tab/desktop)

1. Abra o Microsoft Teams.
1. No canto superior direito da janela, selecione o ícone do seu perfil.
1. Selecione   ->  **permissões** de configurações no menu suspenso.
1. Escolha as configurações desejadas.

![Tela de configurações da área de trabalho de permissões de dispositivo](../../assets/images/tabs/device-permissions.png)

# <a name="mobile"></a>[Mobile](#tab/mobile)

1. Abra o Microsoft Teams.
1. Vá até **configurações** de  ->  **permissões do aplicativo**.
1. Selecione o aplicativo para o qual você precisa escolher as configurações.
1. Escolha as configurações desejadas.

![Tela de configurações móveis de permissões de dispositivo](../../assets/images/tabs/MobilePermissions.png)

---

## <a name="properties"></a>Propriedades

Atualize o seu aplicativo `manifest.json` adicionando `devicePermissions` e especificando quais das cinco Propriedades você gostaria de usar em seu aplicativo:

``` json
"devicePermissions": [
    "media",
    "geolocation",
    "notifications",
    "midi",
    "openExternal"
],
```
> [!Note]
>
> A mídia também é usada para permissões de câmera no celular.

Cada propriedade permitirá que o usuário solicite o consentimento deles:

| Propriedade      | Descrição   |
| --- | --- |
| corre         | permissão para usar a câmera, microfone, alto-falantes e galeria de mídia do Access |
| localização geográfica   | permissão para retornar o local do usuário      |
| por | permissão para enviar as notificações de usuário      |
| Midi          | permissão para enviar e receber informações de Midi de um instrumento musical digital   |
| openExternal  | permissão para abrir links em aplicativos externos  |

## <a name="checking-permissions-from-your-tab"></a>Verificando permissões na sua guia

Depois de adicionar o `devicePermissions` manifesto do aplicativo, você poderá verificar as permissões usando a API "permissões" do HTML5 sem causar um aviso.

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

## <a name="prompting-the-user"></a>Avisar o usuário

Para mostrar um prompt para obter consentimento para acessar permissões de dispositivo, você precisará aproveitar a API de HTML5 ou Teams apropriada. 

Por exemplo, para solicitar que o usuário acesse seu local, você precisará chamar `getCurrentPosition` :

```Javascript
navigator.geolocation.getCurrentPosition(function (position) { /*... */ });
```

Para usar a câmera na área de trabalho ou na Web, o Microsoft Teams mostrará um prompt de permissão quando você ligar `getUserMedia` :

```Javascript
navigator.mediaDevices.getUserMedia({ audio: true, video: true });
```

Para capturar a imagem em dispositivos móveis, o Microsoft Teams Mobile solicitará permissão ao chamar `captureImage()` :

```Javascript
microsoftTeams.media.captureImage((error: microsoftTeams.SdkError, files: microsoftTeams.media.File[]) => {
  /* ... */
});
```

As notificações solicitarão o usuário quando você ligar `requestPermission` :

```Javascript
Notification.requestPermission(function(result) { /* ... */ });
```

Para usar a Galeria de fotos da câmera ou do Access, o Teams Mobile solicitará permissão ao chamar `selectMedia()` :

```JavaScript
microsoftTeams.media.selectMedia({ maxMediaCount: 10, mediaType: microsoftTeams.media.MediaType.Image }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
  /* ... */
});
```

Para usar o MIC, o Teams Mobile solicitará permissão ao chamar `selectMedia()` :

```JavaScript 
microsoftTeams.media.selectMedia({ maxMediaCount: 1, mediaType: microsoftTeams.media.MediaType.Audio }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
  /* ... */
});
```

Para solicitar que o usuário Compartilhe o local na interface de mapa, o Teams Mobile solicitará permissão ao chamar `getLocation()` :

```JavaScript 
microsoftTeams.location.getLocation({ allowChooseLocation: true, showMap: true }, (error: microsoftTeams.SdkError, location: microsoftTeams.location.Location) => {
  /* ... *
/});
```

# <a name="desktop"></a>[Desktop](#tab/desktop)

![Guias de permissões de dispositivo de área de trabalho](~/assets/images/tabs/device-permissions-prompt.png)

# <a name="mobile"></a>[Mobile](#tab/mobile)

![Prompt de permissões de dispositivo móvel de guias](../../assets/images/tabs/MobileLocationPermission.png)


## <a name="permission-behavior-across-login-sessions"></a>Comportamento de permissão nas sessões de logon

As permissões de dispositivo nativo são armazenadas para cada sessão de logon. Isso significa que, se você fizer logon em outra instância do Teams (por exemplo, em outro computador), as permissões do dispositivo de suas sessões anteriores não estarão disponíveis. Em vez disso, você precisará consentir novamente as permissões de dispositivo para a nova sessão de logon. Isso também significa que, se você fizer logout de equipes (ou mudar locatários dentro do Teams), suas permissões de dispositivo serão excluídas para essa sessão de logon anterior. Tenha isso em mente ao desenvolver permissões de dispositivo nativo: os recursos nativos que você concorda para são apenas para sua sessão de login _atual_ .
