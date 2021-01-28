---
title: Solicitar permissões de dispositivo para sua guia
description: Como atualizar o manifesto do aplicativo para solicitar acesso a recursos nativos que geralmente exigem consentimento do usuário
ms.topic: how-to
keywords: desenvolvimento de guias do Teams
ms.openlocfilehash: a2893fb2905584eac4b398287d431f406c23b12b
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014527"
---
# <a name="request-device-permissions-for-your-microsoft-teams-tab"></a><span data-ttu-id="7c1a4-104">Solicitar permissões de dispositivo para sua guia do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="7c1a4-104">Request device permissions for your Microsoft Teams tab</span></span>

<span data-ttu-id="7c1a4-105">Talvez você queira enriquecer sua guia com recursos que exigem acesso à funcionalidade nativa do dispositivo, como:</span><span class="sxs-lookup"><span data-stu-id="7c1a4-105">You might want to enrich your tab with features that require access to native device functionality like:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="7c1a4-106">Câmera</span><span class="sxs-lookup"><span data-stu-id="7c1a4-106">Camera</span></span>
> * <span data-ttu-id="7c1a4-107">Microfone</span><span class="sxs-lookup"><span data-stu-id="7c1a4-107">Microphone</span></span>
> * <span data-ttu-id="7c1a4-108">Localização</span><span class="sxs-lookup"><span data-stu-id="7c1a4-108">Location</span></span>
> * <span data-ttu-id="7c1a4-109">Notificações</span><span class="sxs-lookup"><span data-stu-id="7c1a4-109">Notifications</span></span>

> [!NOTE]
> <span data-ttu-id="7c1a4-110">Para integrar recursos de câmera e imagem ao seu aplicativo móvel do Microsoft Teams, confira as funcionalidades de [câmera e imagem no Teams.](../../concepts/device-capabilities/mobile-camera-image-permissions.md)</span><span class="sxs-lookup"><span data-stu-id="7c1a4-110">To integrate camera and image capabilities within your Microsoft Teams mobile app, see [Camera and image capabilities in Teams.](../../concepts/device-capabilities/mobile-camera-image-permissions.md)</span></span>

> [!IMPORTANT]
>
> * <span data-ttu-id="7c1a4-111">No momento, o cliente móvel do Teams só dá suporte ao acesso a , e por meio de recursos de dispositivo nativo e está disponível em todas as construções de `camera` `gallery` `mic` `location` aplicativo, incluindo guias.</span><span class="sxs-lookup"><span data-stu-id="7c1a4-111">At present, Teams mobile client only supports access to `camera`, `gallery`, `mic`, and `location` through native device capabilities and is available on all app constructs including tabs.</span></span> </br>
> * <span data-ttu-id="7c1a4-112">Suporte para `camera` , e é habilitado por meio de `gallery` `mic` [**selectMedia API**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="7c1a4-112">Support for `camera`, `gallery`, and `mic` is enabled through [**selectMedia API**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true).</span></span> <span data-ttu-id="7c1a4-113">Para captura de imagem única, você pode usar [**captureImage API**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="7c1a4-113">For single image capture you may use [**captureImage API**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true).</span></span>
> * <span data-ttu-id="7c1a4-114">O suporte `location` para é habilitado por meio da API [**getLocation**](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="7c1a4-114">Support for `location` is enabled through [**getLocation API**](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true).</span></span> <span data-ttu-id="7c1a4-115">É recomendável que você use essa API como API [**de geolocalização**](../../resources/schema/manifest-schema.md#devicepermissions) atualmente não é totalmente suportada em todos os clientes da área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="7c1a4-115">It's recommended you use this API as [**geolocation API**](../../resources/schema/manifest-schema.md#devicepermissions) is currently not fully supported on all desktop clients.</span></span>

## <a name="device-permissions"></a><span data-ttu-id="7c1a4-116">Permissões de dispositivos</span><span class="sxs-lookup"><span data-stu-id="7c1a4-116">Device permissions</span></span>

<span data-ttu-id="7c1a4-117">Acessar as permissões de dispositivo de um usuário permite que você crie experiências muito mais completas, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="7c1a4-117">Accessing a user’s device permissions allows you to build much richer experiences, for example:</span></span>

* <span data-ttu-id="7c1a4-118">Gravar e compartilhar vídeos curtos</span><span class="sxs-lookup"><span data-stu-id="7c1a4-118">Record and share short videos</span></span>
* <span data-ttu-id="7c1a4-119">Grave memorandos de áudio curtos e salve-os para mais tarde</span><span class="sxs-lookup"><span data-stu-id="7c1a4-119">Record short audio memos and save them for later</span></span>
* <span data-ttu-id="7c1a4-120">Usar informações de localização do usuário para exibir informações relevantes</span><span class="sxs-lookup"><span data-stu-id="7c1a4-120">Use user location information to display relevant information</span></span>

<span data-ttu-id="7c1a4-121">Embora o acesso a esses recursos seja padrão na maioria dos navegadores da Web modernos, você precisa permitir que o Teams saiba quais recursos você gostaria de usar atualizando o manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7c1a4-121">While access to these features is standard in most modern web browsers, you need to let Teams know which features you’d like to use by updating your app manifest.</span></span> <span data-ttu-id="7c1a4-122">Isso permitirá que você peça permissões, da mesma forma que faria em um navegador, enquanto seu aplicativo é executado no cliente de área de trabalho do Teams.</span><span class="sxs-lookup"><span data-stu-id="7c1a4-122">This will allow you to ask for permissions, the same way you would in a browser, while your app is running on the Teams desktop client.</span></span>

## <a name="manage-permissions"></a><span data-ttu-id="7c1a4-123">Gerenciar permissões</span><span class="sxs-lookup"><span data-stu-id="7c1a4-123">Manage permissions</span></span>

# <a name="desktop"></a>[<span data-ttu-id="7c1a4-124">Desktop</span><span class="sxs-lookup"><span data-stu-id="7c1a4-124">Desktop</span></span>](#tab/desktop)

1. <span data-ttu-id="7c1a4-125">Abra o Teams.</span><span class="sxs-lookup"><span data-stu-id="7c1a4-125">Open Teams.</span></span>
1. <span data-ttu-id="7c1a4-126">No canto superior direito da janela, selecione o ícone de perfil.</span><span class="sxs-lookup"><span data-stu-id="7c1a4-126">In the upper right corner of the window, select your profile icon.</span></span>
1. <span data-ttu-id="7c1a4-127">Selecione **Permissões de**  ->  **Configurações** no menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="7c1a4-127">Select **Settings** -> **Permissions** from the drop-down menu.</span></span>
1. <span data-ttu-id="7c1a4-128">Escolha as configurações desejadas.</span><span class="sxs-lookup"><span data-stu-id="7c1a4-128">Choose your desired settings.</span></span>

![Tela de configurações da área de trabalho de permissões do dispositivo](../../assets/images/tabs/device-permissions.png)

# <a name="mobile"></a>[<span data-ttu-id="7c1a4-130">Mobile</span><span class="sxs-lookup"><span data-stu-id="7c1a4-130">Mobile</span></span>](#tab/mobile)

1. <span data-ttu-id="7c1a4-131">Abra o Teams.</span><span class="sxs-lookup"><span data-stu-id="7c1a4-131">Open Teams.</span></span>
1. <span data-ttu-id="7c1a4-132">Vá para **Configurações**  ->  **de Permissões do Aplicativo.**</span><span class="sxs-lookup"><span data-stu-id="7c1a4-132">Go to **Settings** -> **App Permissions**.</span></span>
1. <span data-ttu-id="7c1a4-133">Selecione o aplicativo para o qual você precisa escolher as configurações.</span><span class="sxs-lookup"><span data-stu-id="7c1a4-133">Select the app you need to choose settings for.</span></span>
1. <span data-ttu-id="7c1a4-134">Escolha as configurações desejadas.</span><span class="sxs-lookup"><span data-stu-id="7c1a4-134">Choose your desired settings.</span></span>

![Tela de configurações móveis de permissões do dispositivo](../../assets/images/tabs/MobilePermissions.png)

---

## <a name="properties"></a><span data-ttu-id="7c1a4-136">Propriedades</span><span class="sxs-lookup"><span data-stu-id="7c1a4-136">Properties</span></span>

<span data-ttu-id="7c1a4-137">Atualize seus aplicativos `manifest.json` adicionando e especificando quais das cinco propriedades você gostaria `devicePermissions` de usar em seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="7c1a4-137">Update your app's `manifest.json` by adding `devicePermissions` and specifying which of the five properties you’d like to use in your application:</span></span>

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
> <span data-ttu-id="7c1a4-138">A mídia também é usada para permissões de câmera em dispositivos móveis.</span><span class="sxs-lookup"><span data-stu-id="7c1a4-138">Media is also used for camera permissions on mobile.</span></span>

<span data-ttu-id="7c1a4-139">Cada propriedade permitirá que você peça ao usuário que peça seu consentimento:</span><span class="sxs-lookup"><span data-stu-id="7c1a4-139">Each property will allow you to prompt the user to ask for their consent:</span></span>

| <span data-ttu-id="7c1a4-140">Propriedade</span><span class="sxs-lookup"><span data-stu-id="7c1a4-140">Property</span></span>      | <span data-ttu-id="7c1a4-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="7c1a4-141">Description</span></span>   |
| --- | --- |
| <span data-ttu-id="7c1a4-142">mídia</span><span class="sxs-lookup"><span data-stu-id="7c1a4-142">media</span></span>         | <span data-ttu-id="7c1a4-143">permissão para usar a câmera, o microfone, os alto-falantes e a galeria de mídia de acesso</span><span class="sxs-lookup"><span data-stu-id="7c1a4-143">permission to use the camera, microphone, speakers, and access media gallery</span></span> |
| <span data-ttu-id="7c1a4-144">geolocalização</span><span class="sxs-lookup"><span data-stu-id="7c1a4-144">geolocation</span></span>   | <span data-ttu-id="7c1a4-145">permissão para retornar a localização do usuário</span><span class="sxs-lookup"><span data-stu-id="7c1a4-145">permission to return the user's location</span></span>      |
| <span data-ttu-id="7c1a4-146">notifications</span><span class="sxs-lookup"><span data-stu-id="7c1a4-146">notifications</span></span> | <span data-ttu-id="7c1a4-147">permissão para enviar as notificações do usuário</span><span class="sxs-lookup"><span data-stu-id="7c1a4-147">permission to send the user notifications</span></span>      |
| <span data-ttu-id="7c1a4-148">midi</span><span class="sxs-lookup"><span data-stu-id="7c1a4-148">midi</span></span>          | <span data-ttu-id="7c1a4-149">permissão para enviar e receber informações midi de um instrumento digital de música</span><span class="sxs-lookup"><span data-stu-id="7c1a4-149">permission to send and receive midi information from a digital musical instrument</span></span>   |
| <span data-ttu-id="7c1a4-150">openExternal</span><span class="sxs-lookup"><span data-stu-id="7c1a4-150">openExternal</span></span>  | <span data-ttu-id="7c1a4-151">permissão para abrir links em aplicativos externos</span><span class="sxs-lookup"><span data-stu-id="7c1a4-151">permission to open links in external applications</span></span>  |

## <a name="checking-permissions-from-your-tab"></a><span data-ttu-id="7c1a4-152">Verificando permissões na guia</span><span class="sxs-lookup"><span data-stu-id="7c1a4-152">Checking permissions from your tab</span></span>

<span data-ttu-id="7c1a4-153">Depois de adicionar ao manifesto do aplicativo, você pode verificar permissões usando `devicePermissions` a API de "permissões" HTML5 sem causar um prompt.</span><span class="sxs-lookup"><span data-stu-id="7c1a4-153">Once you’ve added `devicePermissions` to your app manifest, you can check permissions using the HTML5 “permissions” API without causing a prompt.</span></span>

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

## <a name="prompting-the-user"></a><span data-ttu-id="7c1a4-154">Solicitar ao usuário</span><span class="sxs-lookup"><span data-stu-id="7c1a4-154">Prompting the user</span></span>

<span data-ttu-id="7c1a4-155">Para mostrar uma solicitação para obter consentimento para acessar as permissões do dispositivo, você precisa aproveitar o HTML5 apropriado ou a API do Teams.</span><span class="sxs-lookup"><span data-stu-id="7c1a4-155">To show a prompt to get consent to access device permissions you need to leverage the appropriate HTML5 or Teams API.</span></span> 

<span data-ttu-id="7c1a4-156">Por exemplo, para solicitar que o usuário acesse sua localização, você precisa `getCurrentPosition` chamar:</span><span class="sxs-lookup"><span data-stu-id="7c1a4-156">For example, to prompt the user to access their location you need to call `getCurrentPosition`:</span></span>

```Javascript
navigator.geolocation.getCurrentPosition(function (position) { /*... */ });
```

<span data-ttu-id="7c1a4-157">Para usar a câmera na área de trabalho ou na Web, o Teams mostrará um prompt de permissão quando você `getUserMedia` chamar:</span><span class="sxs-lookup"><span data-stu-id="7c1a4-157">To use the camera on desktop or web, Teams will show a permission prompt when you call `getUserMedia`:</span></span>

```Javascript
navigator.mediaDevices.getUserMedia({ audio: true, video: true });
```

<span data-ttu-id="7c1a4-158">Para capturar a imagem em dispositivos móveis, o Teams Mobile solicitará permissão quando você `captureImage()` chamar:</span><span class="sxs-lookup"><span data-stu-id="7c1a4-158">To capture the image on mobile, Teams mobile will ask for permission when you call `captureImage()`:</span></span>

```Javascript
microsoftTeams.media.captureImage((error: microsoftTeams.SdkError, files: microsoftTeams.media.File[]) => {
  /* ... */
});
```

<span data-ttu-id="7c1a4-159">As notificações solicitarão ao usuário quando você `requestPermission` chamar:</span><span class="sxs-lookup"><span data-stu-id="7c1a4-159">Notifications will prompt the user when you call `requestPermission`:</span></span>

```Javascript
Notification.requestPermission(function(result) { /* ... */ });
```

<span data-ttu-id="7c1a4-160">Para usar a câmera ou acessar a galeria de fotos, o dispositivo móvel do Teams solicitará permissão quando você `selectMedia()` chamar:</span><span class="sxs-lookup"><span data-stu-id="7c1a4-160">To use camera or access photo gallery, Teams mobile will ask permission when you call `selectMedia()`:</span></span>

```JavaScript
microsoftTeams.media.selectMedia({ maxMediaCount: 10, mediaType: microsoftTeams.media.MediaType.Image }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
  /* ... */
});
```

<span data-ttu-id="7c1a4-161">Para usar o mic, o dispositivo móvel do Teams solicitará permissão quando você `selectMedia()` chamar:</span><span class="sxs-lookup"><span data-stu-id="7c1a4-161">To use mic, Teams mobile will ask permission when you call `selectMedia()`:</span></span>

```JavaScript 
microsoftTeams.media.selectMedia({ maxMediaCount: 1, mediaType: microsoftTeams.media.MediaType.Audio }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
  /* ... */
});
```

<span data-ttu-id="7c1a4-162">Para solicitar que o usuário compartilhe o local na interface do mapa, o dispositivo móvel do Teams solicitará permissão quando você `getLocation()` chamar:</span><span class="sxs-lookup"><span data-stu-id="7c1a4-162">To prompt user to share location on map interface, Teams mobile will ask permission when you call `getLocation()`:</span></span>

```JavaScript 
microsoftTeams.location.getLocation({ allowChooseLocation: true, showMap: true }, (error: microsoftTeams.SdkError, location: microsoftTeams.location.Location) => {
  /* ... *
/});
```

# <a name="desktop"></a>[<span data-ttu-id="7c1a4-163">Desktop</span><span class="sxs-lookup"><span data-stu-id="7c1a4-163">Desktop</span></span>](#tab/desktop)

![Prompt de permissões do dispositivo da área de trabalho de guias](~/assets/images/tabs/device-permissions-prompt.png)

# <a name="mobile"></a>[<span data-ttu-id="7c1a4-165">Mobile</span><span class="sxs-lookup"><span data-stu-id="7c1a4-165">Mobile</span></span>](#tab/mobile)

![Prompt de permissões de dispositivo móvel de guias](../../assets/images/tabs/MobileLocationPermission.png)


## <a name="permission-behavior-across-login-sessions"></a><span data-ttu-id="7c1a4-167">Comportamento de permissão em sessões de logon</span><span class="sxs-lookup"><span data-stu-id="7c1a4-167">Permission behavior across login sessions</span></span>

<span data-ttu-id="7c1a4-168">As permissões nativas do dispositivo são armazenadas para cada sessão de logon.</span><span class="sxs-lookup"><span data-stu-id="7c1a4-168">Native device permissions are stored for every login session.</span></span> <span data-ttu-id="7c1a4-169">Isso significa que se você fizer logon em outra instância do Teams (por exemplo, em outro computador), as permissões do dispositivo de suas sessões anteriores não estarão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="7c1a4-169">It means that if you log into another instance of Teams (ex: on another computer), your device permissions from your previous sessions will not be available.</span></span> <span data-ttu-id="7c1a4-170">Em vez disso, você precisará concordar com as permissões do dispositivo para a nova sessão de logon.</span><span class="sxs-lookup"><span data-stu-id="7c1a4-170">Instead, you will need to re-consent to device permissions for the new login session.</span></span> <span data-ttu-id="7c1a4-171">Isso também significa que, se você sair do Teams (ou mudar de locatário dentro do Teams), suas permissões de dispositivo serão excluídas para essa sessão de logon anterior.</span><span class="sxs-lookup"><span data-stu-id="7c1a4-171">It also means, if you log out of Teams (or switch tenants inside of Teams), your device permissions will be deleted for that previous login session.</span></span> <span data-ttu-id="7c1a4-172">Lembre-se disso ao desenvolver permissões de dispositivo nativas: as funcionalidades nativas que você consentir são apenas para sua _sessão de_ logon atual.</span><span class="sxs-lookup"><span data-stu-id="7c1a4-172">Please keep this in mind when developing native device permissions: the native capabilities you consent to are only for your _current_ login session.</span></span>
