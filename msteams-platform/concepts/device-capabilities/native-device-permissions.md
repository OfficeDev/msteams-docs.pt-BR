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
# <a name="request-device-permissions-for-your-microsoft-teams-app"></a><span data-ttu-id="25800-104">Solicite permissões de dispositivos para o aplicativo Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="25800-104">Request device permissions for your Microsoft Teams app</span></span>

<span data-ttu-id="25800-105">Você pode enriquecer seu aplicativo Teams com recursos nativos de dispositivos, como câmera, microfone e localização.</span><span class="sxs-lookup"><span data-stu-id="25800-105">You can enrich your Teams app with native device capabilities, such as camera, microphone, and location.</span></span> <span data-ttu-id="25800-106">Este documento orienta você sobre como solicitar o consentimento do usuário e acessar as permissões do dispositivo nativo.</span><span class="sxs-lookup"><span data-stu-id="25800-106">This document guides you on how to request user consent and access the native device permissions.</span></span>

> [!NOTE]
> * <span data-ttu-id="25800-107">Para integrar os recursos de mídia dentro do aplicativo móvel Microsoft Teams, consulte [Integrar recursos de mídia](mobile-camera-image-permissions.md).</span><span class="sxs-lookup"><span data-stu-id="25800-107">To integrate media capabilities within your Microsoft Teams mobile app, see [Integrate media capabilities](mobile-camera-image-permissions.md).</span></span>
> * <span data-ttu-id="25800-108">Para integrar o recurso de QR ou scanner de código de barras dentro do aplicativo móvel Microsoft Teams, consulte [integrar qr ou recurso de scanner de código de barras em Teams](qr-barcode-scanner-capability.md).</span><span class="sxs-lookup"><span data-stu-id="25800-108">To integrate QR or barcode scanner capability within your Microsoft Teams mobile app, see [Integrate QR or barcode scanner capability in Teams](qr-barcode-scanner-capability.md).</span></span>
> * <span data-ttu-id="25800-109">Para integrar os recursos de localização dentro do aplicativo móvel Microsoft Teams, consulte [Integrar recursos de localização](location-capability.md).</span><span class="sxs-lookup"><span data-stu-id="25800-109">To integrate location capabilities within your Microsoft Teams mobile app, see [Integrate location capabilities](location-capability.md).</span></span>

## <a name="native-device-permissions"></a><span data-ttu-id="25800-110">Permissões de dispositivos nativos</span><span class="sxs-lookup"><span data-stu-id="25800-110">Native device permissions</span></span>

<span data-ttu-id="25800-111">Você deve solicitar as permissões do dispositivo para acessar recursos de dispositivos nativos.</span><span class="sxs-lookup"><span data-stu-id="25800-111">You must request the device permissions to access native device capabilities.</span></span> <span data-ttu-id="25800-112">As permissões do dispositivo funcionam de forma semelhante para todas as construções de aplicativos, como guias, módulos de tarefa ou extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="25800-112">The device permissions work similarly for all app constructs, such as tabs, task modules, or messaging extensions.</span></span> <span data-ttu-id="25800-113">O usuário deve ir à página de permissões em Teams configurações para gerenciar permissões do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="25800-113">The user must go to the permissions page in Teams settings to manage device permissions.</span></span>
<span data-ttu-id="25800-114">Ao acessar os recursos do dispositivo, você pode construir experiências mais ricas na plataforma Teams, tais como:</span><span class="sxs-lookup"><span data-stu-id="25800-114">By accessing the device capabilities, you can build richer experiences on the Teams platform, such as:</span></span>
* <span data-ttu-id="25800-115">Capturar e visualizar imagens.</span><span class="sxs-lookup"><span data-stu-id="25800-115">Capture and view images.</span></span>
* <span data-ttu-id="25800-116">Digitalize QR ou código de barras.</span><span class="sxs-lookup"><span data-stu-id="25800-116">Scan QR or barcode.</span></span>
* <span data-ttu-id="25800-117">Grave e compartilhe vídeos curtos.</span><span class="sxs-lookup"><span data-stu-id="25800-117">Record and share short videos.</span></span>
* <span data-ttu-id="25800-118">Grave memorandos de áudio e guarde-os para uso posterior.</span><span class="sxs-lookup"><span data-stu-id="25800-118">Record audio memos and save them for later use.</span></span>
* <span data-ttu-id="25800-119">Use as informações de localização do usuário para exibir informações relevantes.</span><span class="sxs-lookup"><span data-stu-id="25800-119">Use the location information of the user to display relevant information.</span></span>

## <a name="access-device-permissions"></a><span data-ttu-id="25800-120">Permissões de dispositivos de acesso</span><span class="sxs-lookup"><span data-stu-id="25800-120">Access device permissions</span></span>

<span data-ttu-id="25800-121">O [Microsoft Teams cliente JavaScript SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) fornece as ferramentas necessárias para que seu aplicativo móvel Teams acesse as [permissões](#manage-permissions) do dispositivo do usuário e construa uma experiência mais rica.</span><span class="sxs-lookup"><span data-stu-id="25800-121">The [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) provides the tools necessary for your Teams mobile app to access the user’s [device permissions](#manage-permissions) and build a richer experience.</span></span>

<span data-ttu-id="25800-122">Embora o acesso a esses recursos seja padrão em navegadores da Web modernos, você deve informar Teams sobre os recursos que você usa atualizando seu manifesto de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="25800-122">While access to these features is standard in modern web browsers, you must inform Teams about the features you use by updating your app manifest.</span></span> <span data-ttu-id="25800-123">Esta atualização permite que você peça permissões enquanto seu aplicativo é executado no Teams cliente de desktop.</span><span class="sxs-lookup"><span data-stu-id="25800-123">This update allows you to ask for permissions while your app runs on the Teams desktop client.</span></span>

> [!NOTE] 
> <span data-ttu-id="25800-124">Atualmente, Microsoft Teams suporte para recursos de mídia e capacidade de scanner de código de barras QR só está disponível para clientes móveis.</span><span class="sxs-lookup"><span data-stu-id="25800-124">Currently, Microsoft Teams support for media capabilities and QR barcode scanner capability is only available for mobile clients.</span></span>

## <a name="manage-permissions"></a><span data-ttu-id="25800-125">Gerenciar permissões</span><span class="sxs-lookup"><span data-stu-id="25800-125">Manage permissions</span></span>

<span data-ttu-id="25800-126">Um usuário pode gerenciar permissões de dispositivos em configurações Teams selecionando **permitir** ou **negar** permissões a aplicativos específicos.</span><span class="sxs-lookup"><span data-stu-id="25800-126">A user can manage device permissions in Teams settings by selecting **Allow** or **Deny** permissions to specific apps.</span></span>
 
# <a name="desktop"></a>[<span data-ttu-id="25800-127">Desktop</span><span class="sxs-lookup"><span data-stu-id="25800-127">Desktop</span></span>](#tab/desktop)

1. <span data-ttu-id="25800-128">Abra seu aplicativo de Teams.</span><span class="sxs-lookup"><span data-stu-id="25800-128">Open your Teams app.</span></span>
1. <span data-ttu-id="25800-129">Selecione seu ícone de perfil no canto superior direito da janela.</span><span class="sxs-lookup"><span data-stu-id="25800-129">Select your profile icon in the upper right corner of the window.</span></span>
1. <span data-ttu-id="25800-130">Selecione **Configurações**  >  **Permissões** no menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="25800-130">Select **Settings** > **Permissions** from the drop-down menu.</span></span>
1. <span data-ttu-id="25800-131">Selecione as configurações desejadas.</span><span class="sxs-lookup"><span data-stu-id="25800-131">Select your desired settings.</span></span>

   ![Teste de configurações de desktop de permissões do dispositivo](../../assets/images/tabs/device-permissions.png)

# <a name="mobile"></a>[<span data-ttu-id="25800-133">Mobile</span><span class="sxs-lookup"><span data-stu-id="25800-133">Mobile</span></span>](#tab/mobile)

1. <span data-ttu-id="25800-134">Abra Teams.</span><span class="sxs-lookup"><span data-stu-id="25800-134">Open Teams.</span></span>
1. <span data-ttu-id="25800-135">Vá para **Configurações**  >  **Permissões de aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="25800-135">Go to **Settings** > **App Permissions**.</span></span>
1. <span data-ttu-id="25800-136">Selecione o aplicativo para o qual você precisa escolher as configurações.</span><span class="sxs-lookup"><span data-stu-id="25800-136">Select the app for which you need to choose the settings.</span></span>
1. <span data-ttu-id="25800-137">Selecione as configurações desejadas.</span><span class="sxs-lookup"><span data-stu-id="25800-137">Select your desired settings.</span></span>

    ![Dispositivo permite tela de configurações móveis](../../assets/images/tabs/MobilePermissions.png)

---

## <a name="specify-permissions"></a><span data-ttu-id="25800-139">Especificar permissões</span><span class="sxs-lookup"><span data-stu-id="25800-139">Specify permissions</span></span>

<span data-ttu-id="25800-140">Atualize o aplicativo `manifest.json` adicionando `devicePermissions` e especificando quais das cinco propriedades que você usa em seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="25800-140">Update your app's `manifest.json` by adding `devicePermissions` and specifying which of the five properties that you use in your application:</span></span>

``` json
"devicePermissions": [
    "media",
    "geolocation",
    "notifications",
    "midi",
    "openExternal"
],
```

<span data-ttu-id="25800-141">Cada propriedade permite que você solicite ao usuário o seu consentimento:</span><span class="sxs-lookup"><span data-stu-id="25800-141">Each property allows you to prompt the user to ask for their consent:</span></span>

| <span data-ttu-id="25800-142">Propriedade</span><span class="sxs-lookup"><span data-stu-id="25800-142">Property</span></span>      | <span data-ttu-id="25800-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="25800-143">Description</span></span>   |
| --- | --- |
| <span data-ttu-id="25800-144">mídia</span><span class="sxs-lookup"><span data-stu-id="25800-144">media</span></span>         | <span data-ttu-id="25800-145">Permissão para usar a câmera, microfone, alto-falantes e galeria de mídia de acesso.</span><span class="sxs-lookup"><span data-stu-id="25800-145">Permission to use the camera, microphone, speakers, and access media gallery.</span></span> |
| <span data-ttu-id="25800-146">geolocalização</span><span class="sxs-lookup"><span data-stu-id="25800-146">geolocation</span></span>   | <span data-ttu-id="25800-147">Permissão para retornar a localização do usuário.</span><span class="sxs-lookup"><span data-stu-id="25800-147">Permission to return the user's location.</span></span>      |
| <span data-ttu-id="25800-148">Notificações</span><span class="sxs-lookup"><span data-stu-id="25800-148">notifications</span></span> | <span data-ttu-id="25800-149">Permissão para enviar as notificações do usuário.</span><span class="sxs-lookup"><span data-stu-id="25800-149">Permission to send the user notifications.</span></span>      |
| <span data-ttu-id="25800-150">Midi</span><span class="sxs-lookup"><span data-stu-id="25800-150">midi</span></span>          | <span data-ttu-id="25800-151">Permissão para enviar e receber informações de Interface Digital de Instrumentos Musicais (MIDI) de um instrumento musical digital.</span><span class="sxs-lookup"><span data-stu-id="25800-151">Permission to send and receive  Musical Instrument Digital Interface (MIDI) information from a digital musical instrument.</span></span>   |
| <span data-ttu-id="25800-152">openExternal</span><span class="sxs-lookup"><span data-stu-id="25800-152">openExternal</span></span>  | <span data-ttu-id="25800-153">Permissão para abrir links em aplicativos externos.</span><span class="sxs-lookup"><span data-stu-id="25800-153">Permission to open links in external applications.</span></span>  |

## <a name="check-permissions-from-your-app"></a><span data-ttu-id="25800-154">Verifique as permissões do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="25800-154">Check permissions from your app</span></span>

<span data-ttu-id="25800-155">Depois de adicionar `devicePermissions` ao seu manifesto de aplicativo, verifique as permissões usando a **API de permissões HTML5** sem causar um prompt:</span><span class="sxs-lookup"><span data-stu-id="25800-155">After adding `devicePermissions` to your app manifest, check permissions using the **HTML5 permissions API** without causing a prompt:</span></span>

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

## <a name="use-teams-apis-to-get-device-permissions"></a><span data-ttu-id="25800-156">Use Teams APIs para obter permissões de dispositivos</span><span class="sxs-lookup"><span data-stu-id="25800-156">Use Teams APIs to get device permissions</span></span>

<span data-ttu-id="25800-157">Aproveite a API apropriada HTML5 ou Teams, para exibir um prompt para obter consentimento para acessar permissões de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="25800-157">Leverage appropriate HTML5 or Teams API, to display a prompt for getting consent to access device permissions.</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="25800-158">Suporte para `camera` , , e é `gallery` `microphone` habilitado através de [**API selectMedia**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="25800-158">Support for `camera`, `gallery`, and `microphone` is enabled through [**selectMedia API**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true).</span></span> <span data-ttu-id="25800-159">Use [**a API captureImage**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true) para uma única captura de imagem.</span><span class="sxs-lookup"><span data-stu-id="25800-159">Use [**captureImage API**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true) for a single image capture.</span></span>
> * <span data-ttu-id="25800-160">O suporte `location` é ativado através da [**API getLocation**](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="25800-160">Support for `location` is enabled through [**getLocation API**](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true).</span></span> <span data-ttu-id="25800-161">Você deve usá-lo `getLocation API` para localização, já que a API de geolocalização HTML5 não está totalmente suportada em Teams cliente de desktop.</span><span class="sxs-lookup"><span data-stu-id="25800-161">You must use this `getLocation API` for location, as HTML5 geolocation API is currently not fully supported on Teams desktop client.</span></span>

<span data-ttu-id="25800-162">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="25800-162">For example:</span></span>
 * <span data-ttu-id="25800-163">Para solicitar que o usuário acesse sua localização, você deve ligar `getCurrentPosition()` para:</span><span class="sxs-lookup"><span data-stu-id="25800-163">To prompt the user to access their location you must call `getCurrentPosition()`:</span></span>

    ```Javascript
    navigator.geolocation.getCurrentPosition    (function (position) { /*... */ });
    ```

 * <span data-ttu-id="25800-164">Para solicitar que o usuário acesse sua câmera no desktop ou web, você deve `getUserMedia()` ligar:</span><span class="sxs-lookup"><span data-stu-id="25800-164">To prompt the user to access their camera on desktop or web you must call `getUserMedia()`:</span></span>

    ```Javascript
    navigator.mediaDevices.getUserMedia({ audio: true, video: true });
    ```

 * <span data-ttu-id="25800-165">Para capturar a imagem no celular, Teams celular pede permissão quando você liga `captureImage()` :</span><span class="sxs-lookup"><span data-stu-id="25800-165">To capture the image on mobile, Teams mobile asks for permission when you call `captureImage()`:</span></span>

    ```Javascript
    microsoftTeams.media.captureImage((error: microsoftTeams.SdkError, files: microsoftTeams.media.File[]) => {
      /* ... */
    });
    ```

 * <span data-ttu-id="25800-166">As notificações solicitarão ao usuário quando você `requestPermission()` ligar:</span><span class="sxs-lookup"><span data-stu-id="25800-166">Notifications will prompt the user when you call `requestPermission()`:</span></span>

    ```Javascript
    Notification.requestPermission(function(result) { /* ... */ });
    ```




* <span data-ttu-id="25800-167">Para usar a câmera ou acessar a galeria de fotos, Teams celular pede permissão quando você `selectMedia()` liga:</span><span class="sxs-lookup"><span data-stu-id="25800-167">To use the camera or access photo gallery, Teams mobile asks permission when you call `selectMedia()`:</span></span>

    ```JavaScript
    microsoftTeams.media.selectMedia({ maxMediaCount: 10, mediaType: microsoftTeams.media.MediaType.Image }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
      /* ... */
    );
    ```

* <span data-ttu-id="25800-168">Para usar o microfone, Teams celular pede permissão quando você `selectMedia()` liga:</span><span class="sxs-lookup"><span data-stu-id="25800-168">To use the microphone, Teams mobile asks permission when you call `selectMedia()`:</span></span>

    ```JavaScript 
    microsoftTeams.media.selectMedia({ maxMediaCount: 1, mediaType: microsoftTeams.media.MediaType.Audio }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
      /* ... */
    });
    ```

* <span data-ttu-id="25800-169">Para solicitar que o usuário compartilhe a localização na interface do mapa, Teams celular pede permissão quando você liga `getLocation()` :</span><span class="sxs-lookup"><span data-stu-id="25800-169">To prompt the user to share location on the map interface, Teams mobile asks permission when you call `getLocation()`:</span></span>

    ```JavaScript 
    microsoftTeams.location.getLocation({ allowChooseLocation: true, showMap: true }, (error: microsoftTeams.SdkError, location: microsoftTeams.location.Location) => {
      /* ... *
    /});
    ```
# <a name="desktop"></a>[<span data-ttu-id="25800-170">Desktop</span><span class="sxs-lookup"><span data-stu-id="25800-170">Desktop</span></span>](#tab/desktop)

   ![Guias de permissões de dispositivos de desktop solicitam](~/assets/images/tabs/device-permissions-prompt.png)

# <a name="mobile"></a>[<span data-ttu-id="25800-172">Mobile</span><span class="sxs-lookup"><span data-stu-id="25800-172">Mobile</span></span>](#tab/mobile)

   ![Guias de permissões de dispositivos móveis solicitam](../../assets/images/tabs/MobileLocationPermission.png)

* * * 

## <a name="permission-behavior-across-login-sessions"></a><span data-ttu-id="25800-174">Comportamento de permissão em sessões de login</span><span class="sxs-lookup"><span data-stu-id="25800-174">Permission behavior across login sessions</span></span>

<span data-ttu-id="25800-175">As permissões do dispositivo são armazenadas para cada sessão de login.</span><span class="sxs-lookup"><span data-stu-id="25800-175">Device permissions are stored for every login session.</span></span> <span data-ttu-id="25800-176">Isso significa que se você fizer login em outra instância de Teams, por exemplo, em outro computador, as permissões do seu dispositivo de suas sessões anteriores não estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="25800-176">It means that if you sign in to another instance of Teams, for example, on another computer, your device permissions from your previous sessions are not available.</span></span> <span data-ttu-id="25800-177">Portanto, você deve re consentir com as permissões do dispositivo para a nova sessão.</span><span class="sxs-lookup"><span data-stu-id="25800-177">Therefore, you must re-consent to device permissions for the new session.</span></span> <span data-ttu-id="25800-178">Também significa que, se você sair de Teams ou trocar de inquilinos em Teams, as permissões do dispositivo serão excluídas da sessão de login anterior.</span><span class="sxs-lookup"><span data-stu-id="25800-178">It also means, if you sign out of Teams or switch tenants in Teams, your device permissions are deleted from the previous login session.</span></span>  

> [!NOTE]
> <span data-ttu-id="25800-179">Quando você concorda com as permissões do dispositivo nativo, ele é válido apenas para a sua sessão de login _atual._</span><span class="sxs-lookup"><span data-stu-id="25800-179">When you consent to the native device permissions, it is valid only for your _current_ login session.</span></span>

## <a name="next-steps"></a><span data-ttu-id="25800-180">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="25800-180">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="25800-181">Integrar recursos de mídia em Teams</span><span class="sxs-lookup"><span data-stu-id="25800-181">Integrate media capabilities in Teams</span></span>](mobile-camera-image-permissions.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="25800-182">Integre o recurso de QR ou scanner de código de barras em Teams</span><span class="sxs-lookup"><span data-stu-id="25800-182">Integrate QR or barcode scanner capability in Teams</span></span>](qr-barcode-scanner-capability.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="25800-183">Integre os recursos de localização em Teams</span><span class="sxs-lookup"><span data-stu-id="25800-183">Integrate location capabilities in Teams</span></span>](location-capability.md)
