---
title: Solicitar permissões de dispositivo para seu aplicativo do Microsoft Teams
keywords: Permissões de recursos de aplicativos do teams
description: Como atualizar o manifesto do aplicativo para solicitar acesso a recursos nativos que geralmente exigem consentimento do usuário
ms.topic: how-to
ms.openlocfilehash: 60c28e1170e8bbdf664145bde7f7de585bd55a45
ms.sourcegitcommit: 6ff8d1244ac386641ebf9401804b8df3854b02dc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/18/2021
ms.locfileid: "50294744"
---
# <a name="request-device-permissions-for-your-microsoft-teams-app"></a><span data-ttu-id="ab008-104">Solicitar permissões de dispositivo para seu aplicativo do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="ab008-104">Request device permissions for your Microsoft Teams app</span></span>

<span data-ttu-id="ab008-105">Você pode enriquecer seu aplicativo do Teams com recursos de dispositivo nativos, como câmera, microfone e local.</span><span class="sxs-lookup"><span data-stu-id="ab008-105">You can enrich your Teams app with native device capabilities, such as camera, microphone, and location.</span></span> <span data-ttu-id="ab008-106">Este documento orienta você sobre como solicitar o consentimento do usuário e acessar as permissões de dispositivo nativo.</span><span class="sxs-lookup"><span data-stu-id="ab008-106">This document guides you on how to request user consent and access the native device permissions.</span></span>

> [!NOTE]
> * <span data-ttu-id="ab008-107">Para integrar recursos de mídia ao seu aplicativo móvel do Microsoft Teams, consulte [Integrar recursos de mídia.](mobile-camera-image-permissions.md)</span><span class="sxs-lookup"><span data-stu-id="ab008-107">To integrate media capabilities within your Microsoft Teams mobile app, see [Integrate media capabilities](mobile-camera-image-permissions.md).</span></span>
> * <span data-ttu-id="ab008-108">Para integrar a QR ou o recurso de scanner de código de barras no aplicativo móvel do Microsoft Teams, consulte Integrar o recurso de scanner de código de barras ou [QR no Teams](qr-barcode-scanner-capability.md)</span><span class="sxs-lookup"><span data-stu-id="ab008-108">To integrate QR or barcode scanner capability within your Microsoft Teams mobile app, see [Integrate QR or barcode scanner capability in Teams](qr-barcode-scanner-capability.md)</span></span>

## <a name="native-device-permissions"></a><span data-ttu-id="ab008-109">Permissões de dispositivo nativo</span><span class="sxs-lookup"><span data-stu-id="ab008-109">Native device permissions</span></span>

<span data-ttu-id="ab008-110">Você deve solicitar as permissões de dispositivo para acessar recursos de dispositivo nativos.</span><span class="sxs-lookup"><span data-stu-id="ab008-110">You must request the device permissions to access native device capabilities.</span></span> <span data-ttu-id="ab008-111">As permissões de dispositivo funcionam da mesma forma para todas as construções de aplicativo, como guias, módulos de tarefa ou extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="ab008-111">The device permissions work similarly for all app constructs, such as tabs, task modules, or messaging extensions.</span></span> <span data-ttu-id="ab008-112">O usuário deve ir para a página permissões nas configurações do Teams para gerenciar permissões de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="ab008-112">The user must go to the permissions page in Teams settings to manage device permissions.</span></span>
<span data-ttu-id="ab008-113">Ao acessar os recursos do dispositivo, você pode criar experiências mais ricas na plataforma do Teams, como:</span><span class="sxs-lookup"><span data-stu-id="ab008-113">By accessing the device capabilities, you can build richer experiences on the Teams platform, such as:</span></span>
* <span data-ttu-id="ab008-114">Capturar e exibir imagens.</span><span class="sxs-lookup"><span data-stu-id="ab008-114">Capture and view images.</span></span>
* <span data-ttu-id="ab008-115">Verificar QR ou código de barras.</span><span class="sxs-lookup"><span data-stu-id="ab008-115">Scan QR or barcode.</span></span>
* <span data-ttu-id="ab008-116">Grave e compartilhe vídeos curtos.</span><span class="sxs-lookup"><span data-stu-id="ab008-116">Record and share short videos.</span></span>
* <span data-ttu-id="ab008-117">Grave memorandos de áudio e salve-os para uso posterior.</span><span class="sxs-lookup"><span data-stu-id="ab008-117">Record audio memos and save them for later use.</span></span>
* <span data-ttu-id="ab008-118">Use as informações de local do usuário para exibir informações relevantes.</span><span class="sxs-lookup"><span data-stu-id="ab008-118">Use the location information of the user to display relevant information.</span></span>

## <a name="access-device-permissions"></a><span data-ttu-id="ab008-119">Permissões de dispositivo de acesso</span><span class="sxs-lookup"><span data-stu-id="ab008-119">Access device permissions</span></span>

<span data-ttu-id="ab008-120">O [SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) do cliente JavaScript do Microsoft Teams fornece as ferramentas necessárias para que seu aplicativo móvel do Teams acesse as permissões de dispositivo [do](#manage-permissions) usuário e crie uma experiência mais rica.</span><span class="sxs-lookup"><span data-stu-id="ab008-120">The [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) provides the tools necessary for your Teams mobile app to access the user’s [device permissions](#manage-permissions) and build a richer experience.</span></span>

<span data-ttu-id="ab008-121">Embora o acesso a esses recursos seja padrão em navegadores da Web modernos, você deve informar o Teams sobre os recursos que você usa atualizando o manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ab008-121">While access to these features is standard in modern web browsers, you must inform Teams about the features you use by updating your app manifest.</span></span> <span data-ttu-id="ab008-122">Essa atualização permite que você peça permissões enquanto seu aplicativo é executado no cliente de área de trabalho do Teams.</span><span class="sxs-lookup"><span data-stu-id="ab008-122">This update allows you to ask for permissions while your app runs on the Teams desktop client.</span></span>

> [!NOTE] 
> <span data-ttu-id="ab008-123">Atualmente, o suporte do Microsoft Teams para recursos de mídia e o recurso de scanner de código de barras QR só está disponível para clientes móveis.</span><span class="sxs-lookup"><span data-stu-id="ab008-123">Currently, Microsoft Teams support for media capabilities and QR barcode scanner capability is only available for mobile clients.</span></span>

## <a name="manage-permissions"></a><span data-ttu-id="ab008-124">Gerenciar permissões</span><span class="sxs-lookup"><span data-stu-id="ab008-124">Manage permissions</span></span>

<span data-ttu-id="ab008-125">Um usuário pode gerenciar permissões de dispositivo nas configurações do Teams selecionando **Permitir** ou **Negar** permissões para aplicativos específicos.</span><span class="sxs-lookup"><span data-stu-id="ab008-125">A user can manage device permissions in Teams settings by selecting **Allow** or **Deny** permissions to specific apps.</span></span>
 
# <a name="desktop"></a>[<span data-ttu-id="ab008-126">Desktop</span><span class="sxs-lookup"><span data-stu-id="ab008-126">Desktop</span></span>](#tab/desktop)

1. <span data-ttu-id="ab008-127">Abra seu aplicativo do Teams.</span><span class="sxs-lookup"><span data-stu-id="ab008-127">Open your Teams app.</span></span>
1. <span data-ttu-id="ab008-128">Selecione seu ícone de perfil no canto superior direito da janela.</span><span class="sxs-lookup"><span data-stu-id="ab008-128">Select your profile icon in the upper right corner of the window.</span></span>
1. <span data-ttu-id="ab008-129">Selecione **Configurações**  >  **Permissões** no menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="ab008-129">Select **Settings** > **Permissions** from the drop-down menu.</span></span>
1. <span data-ttu-id="ab008-130">Selecione as configurações desejadas.</span><span class="sxs-lookup"><span data-stu-id="ab008-130">Select your desired settings.</span></span>

   ![Tela de configurações da área de trabalho de permissões do dispositivo](../../assets/images/tabs/device-permissions.png)

# <a name="mobile"></a>[<span data-ttu-id="ab008-132">Mobile</span><span class="sxs-lookup"><span data-stu-id="ab008-132">Mobile</span></span>](#tab/mobile)

1. <span data-ttu-id="ab008-133">Abra o Teams.</span><span class="sxs-lookup"><span data-stu-id="ab008-133">Open Teams.</span></span>
1. <span data-ttu-id="ab008-134">Vá para **Configurações**  >  **Permissões do aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="ab008-134">Go to **Settings** > **App Permissions**.</span></span>
1. <span data-ttu-id="ab008-135">Selecione o aplicativo para o qual você precisa escolher as configurações.</span><span class="sxs-lookup"><span data-stu-id="ab008-135">Select the app for which you need to choose the settings.</span></span>
1. <span data-ttu-id="ab008-136">Selecione as configurações desejadas.</span><span class="sxs-lookup"><span data-stu-id="ab008-136">Select your desired settings.</span></span>

    ![Tela de configurações móveis de permissões de dispositivo](../../assets/images/tabs/MobilePermissions.png)

---

## <a name="specify-permissions"></a><span data-ttu-id="ab008-138">Especificar permissões</span><span class="sxs-lookup"><span data-stu-id="ab008-138">Specify permissions</span></span>

<span data-ttu-id="ab008-139">Atualize o aplicativo adicionando e especificando qual das cinco propriedades `manifest.json` que você usa em seu `devicePermissions` aplicativo:</span><span class="sxs-lookup"><span data-stu-id="ab008-139">Update your app's `manifest.json` by adding `devicePermissions` and specifying which of the five properties that you use in your application:</span></span>

``` json
"devicePermissions": [
    "media",
    "geolocation",
    "notifications",
    "midi",
    "openExternal"
],
```

<span data-ttu-id="ab008-140">Cada propriedade permite solicitar que o usuário peça seu consentimento:</span><span class="sxs-lookup"><span data-stu-id="ab008-140">Each property allows you to prompt the user to ask for their consent:</span></span>

| <span data-ttu-id="ab008-141">Propriedade</span><span class="sxs-lookup"><span data-stu-id="ab008-141">Property</span></span>      | <span data-ttu-id="ab008-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="ab008-142">Description</span></span>   |
| --- | --- |
| <span data-ttu-id="ab008-143">mídia</span><span class="sxs-lookup"><span data-stu-id="ab008-143">media</span></span>         | <span data-ttu-id="ab008-144">Permissão para usar a câmera, o microfone, os alto-falantes e a galeria de mídia de acesso.</span><span class="sxs-lookup"><span data-stu-id="ab008-144">Permission to use the camera, microphone, speakers, and access media gallery.</span></span> |
| <span data-ttu-id="ab008-145">geolocalização</span><span class="sxs-lookup"><span data-stu-id="ab008-145">geolocation</span></span>   | <span data-ttu-id="ab008-146">Permissão para retornar a localização do usuário.</span><span class="sxs-lookup"><span data-stu-id="ab008-146">Permission to return the user's location.</span></span>      |
| <span data-ttu-id="ab008-147">notificações</span><span class="sxs-lookup"><span data-stu-id="ab008-147">notifications</span></span> | <span data-ttu-id="ab008-148">Permissão para enviar as notificações do usuário.</span><span class="sxs-lookup"><span data-stu-id="ab008-148">Permission to send the user notifications.</span></span>      |
| <span data-ttu-id="ab008-149">midi</span><span class="sxs-lookup"><span data-stu-id="ab008-149">midi</span></span>          | <span data-ttu-id="ab008-150">Permissão para enviar e receber informações de MIDI (Interface Digital de Instrumento Musical) de um instrumento digital.</span><span class="sxs-lookup"><span data-stu-id="ab008-150">Permission to send and receive  Musical Instrument Digital Interface (MIDI) information from a digital musical instrument.</span></span>   |
| <span data-ttu-id="ab008-151">openExternal</span><span class="sxs-lookup"><span data-stu-id="ab008-151">openExternal</span></span>  | <span data-ttu-id="ab008-152">Permissão para abrir links em aplicativos externos.</span><span class="sxs-lookup"><span data-stu-id="ab008-152">Permission to open links in external applications.</span></span>  |

## <a name="check-permissions-from-your-app"></a><span data-ttu-id="ab008-153">Verificar permissões do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="ab008-153">Check permissions from your app</span></span>

<span data-ttu-id="ab008-154">Depois de `devicePermissions` adicionar ao manifesto do aplicativo, verifique permissões usando a API de permissões **HTML5** sem causar um prompt:</span><span class="sxs-lookup"><span data-stu-id="ab008-154">After adding `devicePermissions` to your app manifest, check permissions using the **HTML5 permissions API** without causing a prompt:</span></span>

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

## <a name="use-teams-apis-to-get-device-permissions"></a><span data-ttu-id="ab008-155">Usar APIs do Teams para obter permissões de dispositivo</span><span class="sxs-lookup"><span data-stu-id="ab008-155">Use Teams APIs to get device permissions</span></span>

<span data-ttu-id="ab008-156">Aproveite o HTML5 apropriado ou a API do Teams para exibir um prompt para obter consentimento para acessar permissões de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="ab008-156">Leverage appropriate HTML5 or Teams API, to display a prompt for getting consent to access device permissions.</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="ab008-157">Suporte para `camera` , e está habilitado por meio da API `gallery` `microphone` [**selectMedia**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="ab008-157">Support for `camera`, `gallery`, and `microphone` is enabled through [**selectMedia API**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true).</span></span> <span data-ttu-id="ab008-158">Use [**a API captureImage**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true) para uma única captura de imagem.</span><span class="sxs-lookup"><span data-stu-id="ab008-158">Use [**captureImage API**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true) for a single image capture.</span></span>
> * <span data-ttu-id="ab008-159">O suporte `location` para está habilitado por meio da API [**getLocation.**](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="ab008-159">Support for `location` is enabled through [**getLocation API**](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true).</span></span> <span data-ttu-id="ab008-160">Você deve usá-lo para localização, pois a API de localização geográfica HTML5 não tem suporte total no cliente de área de `getLocation API` trabalho do Teams.</span><span class="sxs-lookup"><span data-stu-id="ab008-160">You must use this `getLocation API` for location, as HTML5 geolocation API is currently not fully supported on Teams desktop client.</span></span>

<span data-ttu-id="ab008-161">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="ab008-161">For example:</span></span>
 * <span data-ttu-id="ab008-162">Para solicitar que o usuário acesse sua localização, você deve chamar `getCurrentPosition()` :</span><span class="sxs-lookup"><span data-stu-id="ab008-162">To prompt the user to access their location you must call `getCurrentPosition()`:</span></span>

    ```Javascript
    navigator.geolocation.getCurrentPosition    (function (position) { /*... */ });
    ```

 * <span data-ttu-id="ab008-163">Para solicitar que o usuário acesse sua câmera na área de trabalho ou na Web, você deve chamar `getUserMedia()` :</span><span class="sxs-lookup"><span data-stu-id="ab008-163">To prompt the user to access their camera on desktop or web you must call `getUserMedia()`:</span></span>

    ```Javascript
    navigator.mediaDevices.getUserMedia({ audio: true, video: true });
    ```

 * <span data-ttu-id="ab008-164">Para capturar a imagem no celular, o Teams Mobile pede permissão quando você chama `captureImage()` :</span><span class="sxs-lookup"><span data-stu-id="ab008-164">To capture the image on mobile, Teams mobile asks for permission when you call `captureImage()`:</span></span>

    ```Javascript
    microsoftTeams.media.captureImage((error: microsoftTeams.SdkError, files: microsoftTeams.media.File[]) => {
      /* ... */
    });
    ```

 * <span data-ttu-id="ab008-165">As notificações solicitarão ao usuário quando você chamar `requestPermission()` :</span><span class="sxs-lookup"><span data-stu-id="ab008-165">Notifications will prompt the user when you call `requestPermission()`:</span></span>

    ```Javascript
    Notification.requestPermission(function(result) { /* ... */ });
    ```




* <span data-ttu-id="ab008-166">Para usar a câmera ou a galeria de fotos de acesso, o Teams mobile pede permissão quando você chama `selectMedia()` :</span><span class="sxs-lookup"><span data-stu-id="ab008-166">To use the camera or access photo gallery, Teams mobile asks permission when you call `selectMedia()`:</span></span>

    ```JavaScript
    microsoftTeams.media.selectMedia({ maxMediaCount: 10, mediaType: microsoftTeams.media.MediaType.Image }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
      /* ... */
    );
    ```

* <span data-ttu-id="ab008-167">Para usar o microfone, o teams mobile pede permissão quando você chama `selectMedia()` :</span><span class="sxs-lookup"><span data-stu-id="ab008-167">To use the microphone, Teams mobile asks permission when you call `selectMedia()`:</span></span>

    ```JavaScript 
    microsoftTeams.media.selectMedia({ maxMediaCount: 1, mediaType: microsoftTeams.media.MediaType.Audio }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
      /* ... */
    });
    ```

* <span data-ttu-id="ab008-168">Para solicitar que o usuário compartilhe o local na interface do mapa, o Teams mobile pede permissão quando você chama `getLocation()` :</span><span class="sxs-lookup"><span data-stu-id="ab008-168">To prompt the user to share location on the map interface, Teams mobile asks permission when you call `getLocation()`:</span></span>

    ```JavaScript 
    microsoftTeams.location.getLocation({ allowChooseLocation: true, showMap: true }, (error: microsoftTeams.SdkError, location: microsoftTeams.location.Location) => {
      /* ... *
    /});
    ```
# <a name="desktop"></a>[<span data-ttu-id="ab008-169">Desktop</span><span class="sxs-lookup"><span data-stu-id="ab008-169">Desktop</span></span>](#tab/desktop)

   ![Guia solicitação de permissões do dispositivo da área de trabalho](~/assets/images/tabs/device-permissions-prompt.png)

# <a name="mobile"></a>[<span data-ttu-id="ab008-171">Mobile</span><span class="sxs-lookup"><span data-stu-id="ab008-171">Mobile</span></span>](#tab/mobile)

   ![Guia solicitação de permissões de dispositivo móvel](../../assets/images/tabs/MobileLocationPermission.png)

* * * 

## <a name="permission-behavior-across-login-sessions"></a><span data-ttu-id="ab008-173">Comportamento de permissão em sessões de logon</span><span class="sxs-lookup"><span data-stu-id="ab008-173">Permission behavior across login sessions</span></span>

<span data-ttu-id="ab008-174">As permissões do dispositivo são armazenadas para cada sessão de logon.</span><span class="sxs-lookup"><span data-stu-id="ab008-174">Device permissions are stored for every login session.</span></span> <span data-ttu-id="ab008-175">Isso significa que, se você entrar em outra instância do Teams, por exemplo, em outro computador, as permissões do dispositivo de suas sessões anteriores não estarão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="ab008-175">It means that if you sign in to another instance of Teams, for example, on another computer, your device permissions from your previous sessions are not available.</span></span> <span data-ttu-id="ab008-176">Portanto, você deve consentir de novo as permissões de dispositivo para a nova sessão.</span><span class="sxs-lookup"><span data-stu-id="ab008-176">Therefore, you must re-consent to device permissions for the new session.</span></span> <span data-ttu-id="ab008-177">Isso também significa que, se você sair do Teams ou trocar de locatários no Teams, suas permissões de dispositivo serão excluídas da sessão de logon anterior.</span><span class="sxs-lookup"><span data-stu-id="ab008-177">It also means, if you sign out of Teams or switch tenants in Teams, your device permissions are deleted from the previous login session.</span></span>  

> [!NOTE]
> <span data-ttu-id="ab008-178">Quando você consente com as permissões de dispositivo nativo, ela é válida somente para a _sessão de_ logon atual.</span><span class="sxs-lookup"><span data-stu-id="ab008-178">When you consent to the native device permissions, it is valid only for your _current_ login session.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ab008-179">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="ab008-179">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ab008-180">Integrar recursos de mídia no Teams</span><span class="sxs-lookup"><span data-stu-id="ab008-180">Integrate media capabilities in Teams</span></span>](mobile-camera-image-permissions.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="ab008-181">Integrar a QR ou o recurso de scanner de código de barras no Teams</span><span class="sxs-lookup"><span data-stu-id="ab008-181">Integrate QR or barcode scanner capability in Teams</span></span>](qr-barcode-scanner-capability.md)
