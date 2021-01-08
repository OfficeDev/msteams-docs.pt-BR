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
# <a name="request-device-permissions-for-your-microsoft-teams-tab"></a><span data-ttu-id="6960b-104">Solicitar permissões de dispositivo para a guia do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="6960b-104">Request device permissions for your Microsoft Teams tab</span></span>

<span data-ttu-id="6960b-105">Você pode querer enriquecer sua guia com recursos que exigem acesso à funcionalidade de dispositivo nativo, como:</span><span class="sxs-lookup"><span data-stu-id="6960b-105">You might want to enrich your tab with features that require access to native device functionality like:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="6960b-106">Câmara</span><span class="sxs-lookup"><span data-stu-id="6960b-106">Camera</span></span>
> * <span data-ttu-id="6960b-107">Microfone</span><span class="sxs-lookup"><span data-stu-id="6960b-107">Microphone</span></span>
> * <span data-ttu-id="6960b-108">Local</span><span class="sxs-lookup"><span data-stu-id="6960b-108">Location</span></span>
> * <span data-ttu-id="6960b-109">Notificações</span><span class="sxs-lookup"><span data-stu-id="6960b-109">Notifications</span></span>

[!Note] <span data-ttu-id="6960b-110">Para integrar os recursos de câmera e imagem no seu aplicativo móvel do Microsoft Teams, consulte [recursos de câmera e imagem no Teams.](../../concepts/device-capabilities/mobile-camera-image-permissions.md)</span><span class="sxs-lookup"><span data-stu-id="6960b-110">To integrate camera and image capabilities within your Microsoft Teams mobile app, refer [Camera and image capabilities in Teams.](../../concepts/device-capabilities/mobile-camera-image-permissions.md)</span></span>

> [!IMPORTANT]
>
> * <span data-ttu-id="6960b-111">No presente, o cliente do teams Mobile só dá suporte ao acesso a `camera` ,, `gallery` `mic` e `location` a recursos nativos do dispositivo e está disponível em todas as construções de aplicativos, incluindo guias.</span><span class="sxs-lookup"><span data-stu-id="6960b-111">At present, Teams mobile client only supports access to `camera`, `gallery`, `mic`, and `location` through native device capabilities and is available on all app constructs including tabs.</span></span> </br>
> * <span data-ttu-id="6960b-112">Suporte para `camera` , `gallery` e `mic` é habilitado por meio da [**API selectMedia**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="6960b-112">Support for `camera`, `gallery`, and `mic` is enabled through [**selectMedia API**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true).</span></span> <span data-ttu-id="6960b-113">Para captura de imagem única, você pode usar a [**API captureImage**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="6960b-113">For single image capture you may use [**captureImage API**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true).</span></span>
> * <span data-ttu-id="6960b-114">O suporte para `location` é habilitado por meio da [**API getLocation**](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="6960b-114">Support for `location` is enabled through [**getLocation API**](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true).</span></span> <span data-ttu-id="6960b-115">É recomendável usar esta API como a [**API de geolocalização**](../../resources/schema/manifest-schema.md#devicepermissions) não é totalmente suportada em todos os clientes de desktop.</span><span class="sxs-lookup"><span data-stu-id="6960b-115">It's recommended you use this API as [**geolocation API**](../../resources/schema/manifest-schema.md#devicepermissions) is currently not fully supported on all desktop clients.</span></span>

## <a name="device-permissions"></a><span data-ttu-id="6960b-116">Permissões de dispositivos</span><span class="sxs-lookup"><span data-stu-id="6960b-116">Device permissions</span></span>

<span data-ttu-id="6960b-117">O acesso às permissões de dispositivo de um usuário permite que você construa experiências muito mais ricas, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="6960b-117">Accessing a user’s device permissions allows you to build much richer experiences, for example:</span></span>

* <span data-ttu-id="6960b-118">Gravar e compartilhar vídeos curtos</span><span class="sxs-lookup"><span data-stu-id="6960b-118">Record and share short videos</span></span>
* <span data-ttu-id="6960b-119">Gravar memorandos de áudio curtos e salvá-los para mais tarde</span><span class="sxs-lookup"><span data-stu-id="6960b-119">Record short audio memos and save them for later</span></span>
* <span data-ttu-id="6960b-120">Usar informações de local de usuário para exibir informações relevantes</span><span class="sxs-lookup"><span data-stu-id="6960b-120">Use user location information to display relevant information</span></span>

<span data-ttu-id="6960b-121">Embora o acesso a esses recursos seja padrão nos navegadores da Web mais modernos, você precisa permitir que as equipes saibam quais recursos você gostaria de usar atualizando o manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6960b-121">While access to these features is standard in most modern web browsers, you need to let Teams know which features you’d like to use by updating your app manifest.</span></span> <span data-ttu-id="6960b-122">Isso permitirá que você solicite permissões, da mesma forma que faria em um navegador, enquanto seu aplicativo está sendo executado no cliente de área de trabalho do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="6960b-122">This will allow you to ask for permissions, the same way you would in a browser, while your app is running on the Teams desktop client.</span></span>

## <a name="manage-permissions"></a><span data-ttu-id="6960b-123">Gerenciar permissões</span><span class="sxs-lookup"><span data-stu-id="6960b-123">Manage permissions</span></span>

# <a name="desktop"></a>[<span data-ttu-id="6960b-124">Desktop</span><span class="sxs-lookup"><span data-stu-id="6960b-124">Desktop</span></span>](#tab/desktop)

1. <span data-ttu-id="6960b-125">Abra o Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="6960b-125">Open Teams.</span></span>
1. <span data-ttu-id="6960b-126">No canto superior direito da janela, selecione o ícone do seu perfil.</span><span class="sxs-lookup"><span data-stu-id="6960b-126">In the upper right corner of the window, select your profile icon.</span></span>
1. <span data-ttu-id="6960b-127">Selecione   ->  **permissões** de configurações no menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="6960b-127">Select **Settings** -> **Permissions** from the drop-down menu.</span></span>
1. <span data-ttu-id="6960b-128">Escolha as configurações desejadas.</span><span class="sxs-lookup"><span data-stu-id="6960b-128">Choose your desired settings.</span></span>

![Tela de configurações da área de trabalho de permissões de dispositivo](../../assets/images/tabs/device-permissions.png)

# <a name="mobile"></a>[<span data-ttu-id="6960b-130">Mobile</span><span class="sxs-lookup"><span data-stu-id="6960b-130">Mobile</span></span>](#tab/mobile)

1. <span data-ttu-id="6960b-131">Abra o Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="6960b-131">Open Teams.</span></span>
1. <span data-ttu-id="6960b-132">Vá até **configurações** de  ->  **permissões do aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="6960b-132">Go to **Settings** -> **App Permissions**.</span></span>
1. <span data-ttu-id="6960b-133">Selecione o aplicativo para o qual você precisa escolher as configurações.</span><span class="sxs-lookup"><span data-stu-id="6960b-133">Select the app you need to choose settings for.</span></span>
1. <span data-ttu-id="6960b-134">Escolha as configurações desejadas.</span><span class="sxs-lookup"><span data-stu-id="6960b-134">Choose your desired settings.</span></span>

![Tela de configurações móveis de permissões de dispositivo](../../assets/images/tabs/MobilePermissions.png)

---

## <a name="properties"></a><span data-ttu-id="6960b-136">Propriedades</span><span class="sxs-lookup"><span data-stu-id="6960b-136">Properties</span></span>

<span data-ttu-id="6960b-137">Atualize o seu aplicativo `manifest.json` adicionando `devicePermissions` e especificando quais das cinco Propriedades você gostaria de usar em seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="6960b-137">Update your app's `manifest.json` by adding `devicePermissions` and specifying which of the five properties you’d like to use in your application:</span></span>

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
> <span data-ttu-id="6960b-138">A mídia também é usada para permissões de câmera no celular.</span><span class="sxs-lookup"><span data-stu-id="6960b-138">Media is also used for camera permissions on mobile.</span></span>

<span data-ttu-id="6960b-139">Cada propriedade permitirá que o usuário solicite o consentimento deles:</span><span class="sxs-lookup"><span data-stu-id="6960b-139">Each property will allow you to prompt the user to ask for their consent:</span></span>

| <span data-ttu-id="6960b-140">Propriedade</span><span class="sxs-lookup"><span data-stu-id="6960b-140">Property</span></span>      | <span data-ttu-id="6960b-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="6960b-141">Description</span></span>   |
| --- | --- |
| <span data-ttu-id="6960b-142">corre</span><span class="sxs-lookup"><span data-stu-id="6960b-142">media</span></span>         | <span data-ttu-id="6960b-143">permissão para usar a câmera, microfone, alto-falantes e galeria de mídia do Access</span><span class="sxs-lookup"><span data-stu-id="6960b-143">permission to use the camera, microphone, speakers, and access media gallery</span></span> |
| <span data-ttu-id="6960b-144">localização geográfica</span><span class="sxs-lookup"><span data-stu-id="6960b-144">geolocation</span></span>   | <span data-ttu-id="6960b-145">permissão para retornar o local do usuário</span><span class="sxs-lookup"><span data-stu-id="6960b-145">permission to return the user's location</span></span>      |
| <span data-ttu-id="6960b-146">por</span><span class="sxs-lookup"><span data-stu-id="6960b-146">notifications</span></span> | <span data-ttu-id="6960b-147">permissão para enviar as notificações de usuário</span><span class="sxs-lookup"><span data-stu-id="6960b-147">permission to send the user notifications</span></span>      |
| <span data-ttu-id="6960b-148">Midi</span><span class="sxs-lookup"><span data-stu-id="6960b-148">midi</span></span>          | <span data-ttu-id="6960b-149">permissão para enviar e receber informações de Midi de um instrumento musical digital</span><span class="sxs-lookup"><span data-stu-id="6960b-149">permission to send and receive midi information from a digital musical instrument</span></span>   |
| <span data-ttu-id="6960b-150">openExternal</span><span class="sxs-lookup"><span data-stu-id="6960b-150">openExternal</span></span>  | <span data-ttu-id="6960b-151">permissão para abrir links em aplicativos externos</span><span class="sxs-lookup"><span data-stu-id="6960b-151">permission to open links in external applications</span></span>  |

## <a name="checking-permissions-from-your-tab"></a><span data-ttu-id="6960b-152">Verificando permissões na sua guia</span><span class="sxs-lookup"><span data-stu-id="6960b-152">Checking permissions from your tab</span></span>

<span data-ttu-id="6960b-153">Depois de adicionar o `devicePermissions` manifesto do aplicativo, você poderá verificar as permissões usando a API "permissões" do HTML5 sem causar um aviso.</span><span class="sxs-lookup"><span data-stu-id="6960b-153">Once you’ve added `devicePermissions` to your app manifest, you can check permissions using the HTML5 “permissions” API without causing a prompt.</span></span>

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

## <a name="prompting-the-user"></a><span data-ttu-id="6960b-154">Avisar o usuário</span><span class="sxs-lookup"><span data-stu-id="6960b-154">Prompting the user</span></span>

<span data-ttu-id="6960b-155">Para mostrar um prompt para obter consentimento para acessar permissões de dispositivo, você precisará aproveitar a API de HTML5 ou Teams apropriada.</span><span class="sxs-lookup"><span data-stu-id="6960b-155">To show a prompt to get consent to access device permissions you need to leverage the appropriate HTML5 or Teams API.</span></span> 

<span data-ttu-id="6960b-156">Por exemplo, para solicitar que o usuário acesse seu local, você precisará chamar `getCurrentPosition` :</span><span class="sxs-lookup"><span data-stu-id="6960b-156">For example, to prompt the user to access their location you need to call `getCurrentPosition`:</span></span>

```Javascript
navigator.geolocation.getCurrentPosition(function (position) { /*... */ });
```

<span data-ttu-id="6960b-157">Para usar a câmera na área de trabalho ou na Web, o Microsoft Teams mostrará um prompt de permissão quando você ligar `getUserMedia` :</span><span class="sxs-lookup"><span data-stu-id="6960b-157">To use the camera on desktop or web, Teams will show a permission prompt when you call `getUserMedia`:</span></span>

```Javascript
navigator.mediaDevices.getUserMedia({ audio: true, video: true });
```

<span data-ttu-id="6960b-158">Para capturar a imagem em dispositivos móveis, o Microsoft Teams Mobile solicitará permissão ao chamar `captureImage()` :</span><span class="sxs-lookup"><span data-stu-id="6960b-158">To capture the image on mobile, Teams mobile will ask for permission when you call `captureImage()`:</span></span>

```Javascript
microsoftTeams.media.captureImage((error: microsoftTeams.SdkError, files: microsoftTeams.media.File[]) => {
  /* ... */
});
```

<span data-ttu-id="6960b-159">As notificações solicitarão o usuário quando você ligar `requestPermission` :</span><span class="sxs-lookup"><span data-stu-id="6960b-159">Notifications will prompt the user when you call `requestPermission`:</span></span>

```Javascript
Notification.requestPermission(function(result) { /* ... */ });
```

<span data-ttu-id="6960b-160">Para usar a Galeria de fotos da câmera ou do Access, o Teams Mobile solicitará permissão ao chamar `selectMedia()` :</span><span class="sxs-lookup"><span data-stu-id="6960b-160">To use camera or access photo gallery, Teams mobile will ask permission when you call `selectMedia()`:</span></span>

```JavaScript
microsoftTeams.media.selectMedia({ maxMediaCount: 10, mediaType: microsoftTeams.media.MediaType.Image }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
  /* ... */
});
```

<span data-ttu-id="6960b-161">Para usar o MIC, o Teams Mobile solicitará permissão ao chamar `selectMedia()` :</span><span class="sxs-lookup"><span data-stu-id="6960b-161">To use mic, Teams mobile will ask permission when you call `selectMedia()`:</span></span>

```JavaScript 
microsoftTeams.media.selectMedia({ maxMediaCount: 1, mediaType: microsoftTeams.media.MediaType.Audio }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
  /* ... */
});
```

<span data-ttu-id="6960b-162">Para solicitar que o usuário Compartilhe o local na interface de mapa, o Teams Mobile solicitará permissão ao chamar `getLocation()` :</span><span class="sxs-lookup"><span data-stu-id="6960b-162">To prompt user to share location on map interface, Teams mobile will ask permission when you call `getLocation()`:</span></span>

```JavaScript 
microsoftTeams.location.getLocation({ allowChooseLocation: true, showMap: true }, (error: microsoftTeams.SdkError, location: microsoftTeams.location.Location) => {
  /* ... *
/});
```

# <a name="desktop"></a>[<span data-ttu-id="6960b-163">Desktop</span><span class="sxs-lookup"><span data-stu-id="6960b-163">Desktop</span></span>](#tab/desktop)

![Guias de permissões de dispositivo de área de trabalho](~/assets/images/tabs/device-permissions-prompt.png)

# <a name="mobile"></a>[<span data-ttu-id="6960b-165">Mobile</span><span class="sxs-lookup"><span data-stu-id="6960b-165">Mobile</span></span>](#tab/mobile)

![Prompt de permissões de dispositivo móvel de guias](../../assets/images/tabs/MobileLocationPermission.png)


## <a name="permission-behavior-across-login-sessions"></a><span data-ttu-id="6960b-167">Comportamento de permissão nas sessões de logon</span><span class="sxs-lookup"><span data-stu-id="6960b-167">Permission behavior across login sessions</span></span>

<span data-ttu-id="6960b-168">As permissões de dispositivo nativo são armazenadas para cada sessão de logon.</span><span class="sxs-lookup"><span data-stu-id="6960b-168">Native device permissions are stored for every login session.</span></span> <span data-ttu-id="6960b-169">Isso significa que, se você fizer logon em outra instância do Teams (por exemplo, em outro computador), as permissões do dispositivo de suas sessões anteriores não estarão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="6960b-169">It means that if you log into another instance of Teams (ex: on another computer), your device permissions from your previous sessions will not be available.</span></span> <span data-ttu-id="6960b-170">Em vez disso, você precisará consentir novamente as permissões de dispositivo para a nova sessão de logon.</span><span class="sxs-lookup"><span data-stu-id="6960b-170">Instead, you will need to re-consent to device permissions for the new login session.</span></span> <span data-ttu-id="6960b-171">Isso também significa que, se você fizer logout de equipes (ou mudar locatários dentro do Teams), suas permissões de dispositivo serão excluídas para essa sessão de logon anterior.</span><span class="sxs-lookup"><span data-stu-id="6960b-171">It also means, if you log out of Teams (or switch tenants inside of Teams), your device permissions will be deleted for that previous login session.</span></span> <span data-ttu-id="6960b-172">Tenha isso em mente ao desenvolver permissões de dispositivo nativo: os recursos nativos que você concorda para são apenas para sua sessão de login _atual_ .</span><span class="sxs-lookup"><span data-stu-id="6960b-172">Please keep this in mind when developing native device permissions: the native capabilities you consent to are only for your _current_ login session.</span></span>
