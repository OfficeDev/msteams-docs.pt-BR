---
title: Solicitar permissões de dispositivo para sua guia do Microsoft Teams
description: Como atualizar o manifesto do aplicativo para solicitar acesso a recursos nativos que geralmente exigem consentimento do usuário
keywords: desenvolvimento de guias do Teams
ms.openlocfilehash: b021ae4ae8b50ddd1f3603f696922c129eb25f10
ms.sourcegitcommit: 84f408aa2854aa7a5cefaa66ce9a373b19e0864a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/18/2021
ms.locfileid: "49886741"
---
# <a name="request-device-permissions-for-your-microsoft-teams-tab"></a>Solicitar permissões de dispositivo para sua guia do Microsoft Teams

Talvez você queira enriquecer sua guia com recursos que exigem acesso à funcionalidade do dispositivo nativo, como:

> [!div class="checklist"]
>
> * Câmera
> * Microfone
> * Local
> * Notificações

> [!NOTE]
> Para integrar recursos de câmera e imagem ao seu aplicativo móvel do Microsoft Teams, confira recursos de [câmera e imagem no Teams.](../../concepts/device-capabilities/mobile-camera-image-permissions.md)

> [!IMPORTANT]
>
> * No momento, o cliente móvel do Teams só dá suporte ao acesso a , e por meio de recursos de dispositivo nativo e está disponível em todas as construções de `camera` `gallery` `mic` `location` aplicativo, incluindo guias. </br>
> * Suporte para `camera` , e é habilitado por meio de `gallery` `mic` [**selectMedia API**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true). Para captura de imagem única, você pode usar [**captureImage API**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true).
> * O suporte `location` para é habilitado por meio da API [**getLocation**](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true). É recomendável que você use essa API como API [**de geolocalização**](../../resources/schema/manifest-schema.md#devicepermissions) atualmente não é totalmente suportada em todos os clientes da área de trabalho.

## <a name="device-permissions"></a>Permissões de dispositivos

Acessar as permissões de dispositivo de um usuário permite que você crie experiências muito mais completas, por exemplo:

* Gravar e compartilhar vídeos curtos
* Grave memorandos de áudio curtos e salve-os para mais tarde
* Usar informações de localização do usuário para exibir informações relevantes

Embora o acesso a esses recursos seja padrão na maioria dos navegadores da Web modernos, você precisa permitir que o Teams saiba quais recursos você gostaria de usar atualizando o manifesto do aplicativo. Isso permitirá que você peça permissões, da mesma forma que faria em um navegador, enquanto seu aplicativo está sendo executado no cliente da área de trabalho do Teams.

## <a name="manage-permissions"></a>Gerenciar permissões

# <a name="desktop"></a>[Desktop](#tab/desktop)

1. Abra o Teams.
1. No canto superior direito da janela, selecione o ícone de perfil.
1. Selecione **Permissões de**  ->  **Configurações** no menu suspenso.
1. Escolha as configurações desejadas.

![Tela de configurações da área de trabalho de permissões do dispositivo](../../assets/images/tabs/device-permissions.png)

# <a name="mobile"></a>[Mobile](#tab/mobile)

1. Abra o Teams.
1. Vá para **Configurações**  ->  **de Permissões do Aplicativo.**
1. Selecione o aplicativo para o qual você precisa escolher as configurações.
1. Escolha as configurações desejadas.

![Tela de configurações móveis de permissões do dispositivo](../../assets/images/tabs/MobilePermissions.png)

---

## <a name="properties"></a>Propriedades

Atualize seus aplicativos `manifest.json` adicionando e especificando quais das cinco propriedades você gostaria `devicePermissions` de usar em seu aplicativo:

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
> A mídia também é usada para permissões de câmera em dispositivos móveis.

Cada propriedade permitirá que você peça ao usuário que peça seu consentimento:

| Propriedade      | Descrição   |
| --- | --- |
| mídia         | permissão para usar a câmera, o microfone, os alto-falantes e a galeria de mídia de acesso |
| geolocalização   | permissão para retornar o local do usuário      |
| notifications | permissão para enviar as notificações do usuário      |
| midi          | permissão para enviar e receber informações midi de um instrumento digital de música   |
| openExternal  | permissão para abrir links em aplicativos externos  |

## <a name="checking-permissions-from-your-tab"></a>Verificando permissões na guia

Depois de adicionar ao manifesto do aplicativo, você pode verificar permissões usando `devicePermissions` a API de "permissões" HTML5 sem causar um prompt.

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

## <a name="prompting-the-user"></a>Solicitar ao usuário

Para mostrar uma solicitação para obter consentimento para acessar as permissões do dispositivo, você precisa aproveitar o HTML5 apropriado ou a API do Teams. 

Por exemplo, para solicitar que o usuário acesse sua localização, você precisa `getCurrentPosition` chamar:

```Javascript
navigator.geolocation.getCurrentPosition(function (position) { /*... */ });
```

Para usar a câmera na área de trabalho ou na Web, o Teams mostrará um prompt de permissão quando você `getUserMedia` chamar:

```Javascript
navigator.mediaDevices.getUserMedia({ audio: true, video: true });
```

Para capturar a imagem em dispositivos móveis, o Teams Mobile solicitará permissão quando você `captureImage()` chamar:

```Javascript
microsoftTeams.media.captureImage((error: microsoftTeams.SdkError, files: microsoftTeams.media.File[]) => {
  /* ... */
});
```

As notificações solicitarão ao usuário quando você `requestPermission` chamar:

```Javascript
Notification.requestPermission(function(result) { /* ... */ });
```

Para usar a câmera ou acessar a galeria de fotos, o dispositivo móvel do Teams solicitará permissão quando você `selectMedia()` chamar:

```JavaScript
microsoftTeams.media.selectMedia({ maxMediaCount: 10, mediaType: microsoftTeams.media.MediaType.Image }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
  /* ... */
});
```

Para usar o mic, o dispositivo móvel do Teams solicitará permissão quando você `selectMedia()` chamar:

```JavaScript 
microsoftTeams.media.selectMedia({ maxMediaCount: 1, mediaType: microsoftTeams.media.MediaType.Audio }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
  /* ... */
});
```

Para solicitar que o usuário compartilhe o local na interface do mapa, o teams Mobile solicitará permissão quando você `getLocation()` chamar:

```JavaScript 
microsoftTeams.location.getLocation({ allowChooseLocation: true, showMap: true }, (error: microsoftTeams.SdkError, location: microsoftTeams.location.Location) => {
  /* ... *
/});
```

# <a name="desktop"></a>[Desktop](#tab/desktop)

![Prompt de permissões do dispositivo da área de trabalho de guias](~/assets/images/tabs/device-permissions-prompt.png)

# <a name="mobile"></a>[Mobile](#tab/mobile)

![Prompt de permissões de dispositivo móvel de guias](../../assets/images/tabs/MobileLocationPermission.png)


## <a name="permission-behavior-across-login-sessions"></a>Comportamento de permissão entre sessões de logon

As permissões nativas do dispositivo são armazenadas para cada sessão de logon. Isso significa que, se você fizer logon em outra instância do Teams (por exemplo, em outro computador), as permissões do dispositivo de suas sessões anteriores não estarão disponíveis. Em vez disso, você precisará concordar com as permissões do dispositivo para a nova sessão de logon. Isso também significa que, se você sair do Teams (ou mudar de locatário dentro do Teams), suas permissões de dispositivo serão excluídas para essa sessão de logon anterior. Lembre-se disso ao desenvolver permissões de dispositivo nativas: as funcionalidades nativas que você consentir são apenas para sua _sessão de_ logon atual.
