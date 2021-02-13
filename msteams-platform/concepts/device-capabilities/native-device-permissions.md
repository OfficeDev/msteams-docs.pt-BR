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
# <a name="request-device-permissions-for-your-microsoft-teams-app"></a><span data-ttu-id="6925e-104">Solicitar permissões de dispositivo para seu aplicativo microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="6925e-104">Request device permissions for your Microsoft Teams app</span></span>

<span data-ttu-id="6925e-105">Você pode enriquecer seu aplicativo teams com recursos nativos do dispositivo, como câmera, microfone e localização.</span><span class="sxs-lookup"><span data-stu-id="6925e-105">You can enrich your Teams app with native device capabilities, such as camera, microphone, and location.</span></span> <span data-ttu-id="6925e-106">Este documento orienta você sobre como solicitar o consentimento do usuário e acessar as permissões do dispositivo nativo.</span><span class="sxs-lookup"><span data-stu-id="6925e-106">This document guides you on how to request user consent and access the native device permissions.</span></span>

> [!NOTE]
> <span data-ttu-id="6925e-107">Para integrar recursos de mídia ao seu aplicativo móvel do Microsoft Teams, confira [Integrar recursos de mídia.](mobile-camera-image-permissions.md)</span><span class="sxs-lookup"><span data-stu-id="6925e-107">To integrate media capabilities within your Microsoft Teams mobile app, see [Integrate media capabilities](mobile-camera-image-permissions.md).</span></span>

## <a name="native-device-permissions"></a><span data-ttu-id="6925e-108">Permissões de dispositivo nativo</span><span class="sxs-lookup"><span data-stu-id="6925e-108">Native device permissions</span></span>

<span data-ttu-id="6925e-109">Você deve solicitar as permissões do dispositivo para acessar as funcionalidades nativas do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="6925e-109">You must request the device permissions to access native device capabilities.</span></span> <span data-ttu-id="6925e-110">As permissões de dispositivo funcionam da mesma forma para todas as construções de aplicativo, como guias, módulos de tarefa ou extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="6925e-110">The device permissions work similarly for all app constructs, such as tabs, task modules, or messaging extensions.</span></span> <span data-ttu-id="6925e-111">O usuário deve ir para a página de permissões nas configurações do Teams para gerenciar as permissões do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="6925e-111">The user must go to the permissions page in Teams settings to manage device permissions.</span></span>
<span data-ttu-id="6925e-112">Ao acessar os recursos do dispositivo, você pode criar experiências mais completas na plataforma do Teams, como:</span><span class="sxs-lookup"><span data-stu-id="6925e-112">By accessing the device capabilities, you can build richer experiences on the Teams platform, such as:</span></span>
* <span data-ttu-id="6925e-113">Capturar e exibir imagens.</span><span class="sxs-lookup"><span data-stu-id="6925e-113">Capture and view images.</span></span>
* <span data-ttu-id="6925e-114">Grave e compartilhe vídeos curtos.</span><span class="sxs-lookup"><span data-stu-id="6925e-114">Record and share short videos.</span></span>
* <span data-ttu-id="6925e-115">Grave memorandos de áudio e salve-os para uso posterior.</span><span class="sxs-lookup"><span data-stu-id="6925e-115">Record audio memos and save them for later use.</span></span>
* <span data-ttu-id="6925e-116">Use as informações de local do usuário para exibir informações relevantes.</span><span class="sxs-lookup"><span data-stu-id="6925e-116">Use the location information of the user to display relevant information.</span></span>

## <a name="access-device-permissions"></a><span data-ttu-id="6925e-117">Acessar permissões de dispositivo</span><span class="sxs-lookup"><span data-stu-id="6925e-117">Access device permissions</span></span>

<span data-ttu-id="6925e-118">O [SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) do cliente JavaScript do Microsoft Teams fornece as ferramentas [](#manage-permissions) necessárias para que seu aplicativo móvel do Teams acesse as permissões de dispositivo do usuário e crie uma experiência mais rica.</span><span class="sxs-lookup"><span data-stu-id="6925e-118">The [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) provides the tools necessary for your Teams mobile app to access the user’s [device permissions](#manage-permissions) and build a richer experience.</span></span>

<span data-ttu-id="6925e-119">Embora o acesso a esses recursos seja padrão em navegadores da Web modernos, você deve informar o Teams sobre os recursos que você usa atualizando o manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6925e-119">While access to these features is standard in modern web browsers, you must inform Teams about the features you use by updating your app manifest.</span></span> <span data-ttu-id="6925e-120">Essa atualização permite que você peça permissões enquanto seu aplicativo é executado no cliente da área de trabalho do Teams.</span><span class="sxs-lookup"><span data-stu-id="6925e-120">This update allows you to ask for permissions while your app runs on the Teams desktop client.</span></span>

> [!NOTE] 
> <span data-ttu-id="6925e-121">Atualmente, o suporte do Microsoft Teams para recursos de mídia só está disponível para clientes móveis.</span><span class="sxs-lookup"><span data-stu-id="6925e-121">Currently, Microsoft Teams support for media capabilities is only available for mobile clients.</span></span>

## <a name="manage-permissions"></a><span data-ttu-id="6925e-122">Gerenciar permissões</span><span class="sxs-lookup"><span data-stu-id="6925e-122">Manage permissions</span></span>

<span data-ttu-id="6925e-123">Um usuário pode gerenciar permissões de dispositivo nas  configurações do Teams selecionando **Permissões** Permitir ou Negar para aplicativos específicos.</span><span class="sxs-lookup"><span data-stu-id="6925e-123">A user can manage device permissions in Teams settings by selecting **Allow** or **Deny** permissions to specific apps.</span></span>
 
# <a name="desktop"></a>[<span data-ttu-id="6925e-124">Desktop</span><span class="sxs-lookup"><span data-stu-id="6925e-124">Desktop</span></span>](#tab/desktop)

1. <span data-ttu-id="6925e-125">Abra seu aplicativo do Teams.</span><span class="sxs-lookup"><span data-stu-id="6925e-125">Open your Teams app.</span></span>
1. <span data-ttu-id="6925e-126">Selecione o ícone de perfil no canto superior direito da janela.</span><span class="sxs-lookup"><span data-stu-id="6925e-126">Select your profile icon in the upper right corner of the window.</span></span>
1. <span data-ttu-id="6925e-127">Selecione **Permissões de**  >  **Configurações** no menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="6925e-127">Select **Settings** > **Permissions** from the drop-down menu.</span></span>
1. <span data-ttu-id="6925e-128">Selecione as configurações desejadas.</span><span class="sxs-lookup"><span data-stu-id="6925e-128">Select your desired settings.</span></span>

   ![Tela de configurações da área de trabalho de permissões do dispositivo](../../assets/images/tabs/device-permissions.png)

# <a name="mobile"></a>[<span data-ttu-id="6925e-130">Mobile</span><span class="sxs-lookup"><span data-stu-id="6925e-130">Mobile</span></span>](#tab/mobile)

1. <span data-ttu-id="6925e-131">Abra o Teams.</span><span class="sxs-lookup"><span data-stu-id="6925e-131">Open Teams.</span></span>
1. <span data-ttu-id="6925e-132">Vá para **Configurações**  >  **de Permissões do Aplicativo.**</span><span class="sxs-lookup"><span data-stu-id="6925e-132">Go to **Settings** > **App Permissions**.</span></span>
1. <span data-ttu-id="6925e-133">Selecione o aplicativo para o qual você precisa escolher as configurações.</span><span class="sxs-lookup"><span data-stu-id="6925e-133">Select the app for which you need to choose the settings.</span></span>
1. <span data-ttu-id="6925e-134">Selecione as configurações desejadas.</span><span class="sxs-lookup"><span data-stu-id="6925e-134">Select your desired settings.</span></span>

    ![Tela de configurações móveis de permissões do dispositivo](../../assets/images/tabs/MobilePermissions.png)

---

## <a name="specify-permissions"></a><span data-ttu-id="6925e-136">Especificar permissões</span><span class="sxs-lookup"><span data-stu-id="6925e-136">Specify permissions</span></span>

<span data-ttu-id="6925e-137">Atualize seus aplicativos `manifest.json` adicionando `devicePermissions` e especificando quais das cinco propriedades você usa em seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="6925e-137">Update your app's `manifest.json` by adding `devicePermissions` and specifying which of the five properties that you use in your application:</span></span>

``` json
"devicePermissions": [
    "media",
    "geolocation",
    "notifications",
    "midi",
    "openExternal"
],
```

<span data-ttu-id="6925e-138">Cada propriedade permite que você peça ao usuário que peça seu consentimento:</span><span class="sxs-lookup"><span data-stu-id="6925e-138">Each property allows you to prompt the user to ask for their consent:</span></span>

| <span data-ttu-id="6925e-139">Propriedade</span><span class="sxs-lookup"><span data-stu-id="6925e-139">Property</span></span>      | <span data-ttu-id="6925e-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="6925e-140">Description</span></span>   |
| --- | --- |
| <span data-ttu-id="6925e-141">mídia</span><span class="sxs-lookup"><span data-stu-id="6925e-141">media</span></span>         | <span data-ttu-id="6925e-142">Permissão para usar a câmera, o microfone, os alto-falantes e a galeria de mídia de acesso.</span><span class="sxs-lookup"><span data-stu-id="6925e-142">Permission to use the camera, microphone, speakers, and access media gallery.</span></span> |
| <span data-ttu-id="6925e-143">geolocalização</span><span class="sxs-lookup"><span data-stu-id="6925e-143">geolocation</span></span>   | <span data-ttu-id="6925e-144">Permissão para retornar a localização do usuário.</span><span class="sxs-lookup"><span data-stu-id="6925e-144">Permission to return the user's location.</span></span>      |
| <span data-ttu-id="6925e-145">notifications</span><span class="sxs-lookup"><span data-stu-id="6925e-145">notifications</span></span> | <span data-ttu-id="6925e-146">Permissão para enviar as notificações do usuário.</span><span class="sxs-lookup"><span data-stu-id="6925e-146">Permission to send the user notifications.</span></span>      |
| <span data-ttu-id="6925e-147">midi</span><span class="sxs-lookup"><span data-stu-id="6925e-147">midi</span></span>          | <span data-ttu-id="6925e-148">Permissão para enviar e receber informações MIDI (Interface Digital de Instrumento Digital) de um instrumento digital.</span><span class="sxs-lookup"><span data-stu-id="6925e-148">Permission to send and receive  Musical Instrument Digital Interface (MIDI) information from a digital musical instrument.</span></span>   |
| <span data-ttu-id="6925e-149">openExternal</span><span class="sxs-lookup"><span data-stu-id="6925e-149">openExternal</span></span>  | <span data-ttu-id="6925e-150">Permissão para abrir links em aplicativos externos.</span><span class="sxs-lookup"><span data-stu-id="6925e-150">Permission to open links in external applications.</span></span>  |

## <a name="check-permissions-from-your-app"></a><span data-ttu-id="6925e-151">Verificar permissões do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="6925e-151">Check permissions from your app</span></span>

<span data-ttu-id="6925e-152">Depois de `devicePermissions` adicionar ao manifesto do aplicativo, verifique as permissões usando a API de permissões **HTML5** sem causar um aviso:</span><span class="sxs-lookup"><span data-stu-id="6925e-152">After adding `devicePermissions` to your app manifest, check permissions using the **HTML5 permissions API** without causing a prompt:</span></span>

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

## <a name="use-teams-apis-to-get-device-permissions"></a><span data-ttu-id="6925e-153">Usar APIs do Teams para obter permissões de dispositivo</span><span class="sxs-lookup"><span data-stu-id="6925e-153">Use Teams APIs to get device permissions</span></span>

<span data-ttu-id="6925e-154">Aproveite o HTML5 apropriado ou a API do Teams para exibir uma solicitação de consentimento para acessar as permissões do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="6925e-154">Leverage appropriate HTML5 or Teams API, to display a prompt for getting consent to access device permissions.</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="6925e-155">Suporte para `camera` , e é habilitado por meio de `gallery` `microphone` [**selectMedia API**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="6925e-155">Support for `camera`, `gallery`, and `microphone` is enabled through [**selectMedia API**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true).</span></span> <span data-ttu-id="6925e-156">Use [**a API captureImage**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true) para uma única captura de imagem.</span><span class="sxs-lookup"><span data-stu-id="6925e-156">Use [**captureImage API**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true) for a single image capture.</span></span>
> * <span data-ttu-id="6925e-157">O suporte `location` para é habilitado por meio da API [**getLocation**](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="6925e-157">Support for `location` is enabled through [**getLocation API**](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true).</span></span> <span data-ttu-id="6925e-158">Você deve usar isso para localização, pois a API de geolocalização HTML5 atualmente não é totalmente suportada no cliente de área de `getLocation API` trabalho do Teams.</span><span class="sxs-lookup"><span data-stu-id="6925e-158">You must use this `getLocation API` for location, as HTML5 geolocation API is currently not fully supported on Teams desktop client.</span></span>

<span data-ttu-id="6925e-159">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="6925e-159">For example:</span></span>
 * <span data-ttu-id="6925e-160">Para solicitar que o usuário acesse sua localização, você deve `getCurrentPosition()` chamar:</span><span class="sxs-lookup"><span data-stu-id="6925e-160">To prompt the user to access their location you must call `getCurrentPosition()`:</span></span>

    ```Javascript
    navigator.geolocation.getCurrentPosition    (function (position) { /*... */ });
    ```

 * <span data-ttu-id="6925e-161">Para solicitar que o usuário acesse a câmera na área de trabalho ou na Web, você deve `getUserMedia()` chamar:</span><span class="sxs-lookup"><span data-stu-id="6925e-161">To prompt the user to access their camera on desktop or web you must call `getUserMedia()`:</span></span>

    ```Javascript
    navigator.mediaDevices.getUserMedia({ audio: true, video: true });
    ```

 * <span data-ttu-id="6925e-162">Para capturar a imagem em dispositivos móveis, o Teams Mobile solicita permissão ao `captureImage()` chamar:</span><span class="sxs-lookup"><span data-stu-id="6925e-162">To capture the image on mobile, Teams mobile asks for permission when you call `captureImage()`:</span></span>

    ```Javascript
    microsoftTeams.media.captureImage((error: microsoftTeams.SdkError, files: microsoftTeams.media.File[]) => {
      /* ... */
    });
    ```

 * <span data-ttu-id="6925e-163">As notificações solicitarão ao usuário quando você `requestPermission()` chamar:</span><span class="sxs-lookup"><span data-stu-id="6925e-163">Notifications will prompt the user when you call `requestPermission()`:</span></span>

    ```Javascript
    Notification.requestPermission(function(result) { /* ... */ });
    ```




* <span data-ttu-id="6925e-164">Para usar a câmera ou acessar a galeria de fotos, o dispositivo móvel do Teams solicita permissão ao `selectMedia()` chamar:</span><span class="sxs-lookup"><span data-stu-id="6925e-164">To use the camera or access photo gallery, Teams mobile asks permission when you call `selectMedia()`:</span></span>

    ```JavaScript
    microsoftTeams.media.selectMedia({ maxMediaCount: 10, mediaType: microsoftTeams.media.MediaType.Image }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
      /* ... */
    );
    ```

* <span data-ttu-id="6925e-165">Para usar o microfone, o dispositivo móvel do Teams solicita permissão ao `selectMedia()` chamar:</span><span class="sxs-lookup"><span data-stu-id="6925e-165">To use the microphone, Teams mobile asks permission when you call `selectMedia()`:</span></span>

    ```JavaScript 
    microsoftTeams.media.selectMedia({ maxMediaCount: 1, mediaType: microsoftTeams.media.MediaType.Audio }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
      /* ... */
    });
    ```

* <span data-ttu-id="6925e-166">Para solicitar que o usuário compartilhe o local na interface de mapa, o dispositivo móvel do Teams solicita permissão quando você `getLocation()` chama:</span><span class="sxs-lookup"><span data-stu-id="6925e-166">To prompt the user to share location on the map interface, Teams mobile asks permission when you call `getLocation()`:</span></span>

    ```JavaScript 
    microsoftTeams.location.getLocation({ allowChooseLocation: true, showMap: true }, (error: microsoftTeams.SdkError, location: microsoftTeams.location.Location) => {
      /* ... *
    /});
    ```
# <a name="desktop"></a>[<span data-ttu-id="6925e-167">Desktop</span><span class="sxs-lookup"><span data-stu-id="6925e-167">Desktop</span></span>](#tab/desktop)

   ![Prompt de permissões do dispositivo da área de trabalho de guias](~/assets/images/tabs/device-permissions-prompt.png)

# <a name="mobile"></a>[<span data-ttu-id="6925e-169">Mobile</span><span class="sxs-lookup"><span data-stu-id="6925e-169">Mobile</span></span>](#tab/mobile)

   ![Prompt de permissões de dispositivo móvel de guias](../../assets/images/tabs/MobileLocationPermission.png)

* * * 

## <a name="permission-behavior-across-login-sessions"></a><span data-ttu-id="6925e-171">Comportamento de permissão em sessões de logon</span><span class="sxs-lookup"><span data-stu-id="6925e-171">Permission behavior across login sessions</span></span>

<span data-ttu-id="6925e-172">As permissões do dispositivo são armazenadas para cada sessão de logon.</span><span class="sxs-lookup"><span data-stu-id="6925e-172">Device permissions are stored for every login session.</span></span> <span data-ttu-id="6925e-173">Isso significa que, se você entrar em outra instância do Teams, por exemplo, em outro computador, suas permissões de dispositivo de suas sessões anteriores não estarão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="6925e-173">It means that if you sign in to another instance of Teams, for example, on another computer, your device permissions from your previous sessions are not available.</span></span> <span data-ttu-id="6925e-174">Portanto, você deve consentir outra vez com as permissões de dispositivo para a nova sessão.</span><span class="sxs-lookup"><span data-stu-id="6925e-174">Therefore, you must re-consent to device permissions for the new session.</span></span> <span data-ttu-id="6925e-175">Isso também significa que, se você sair do Teams ou mudar de locatário no Teams, suas permissões de dispositivo serão excluídas da sessão de logon anterior.</span><span class="sxs-lookup"><span data-stu-id="6925e-175">It also means, if you sign out of Teams or switch tenants in Teams, your device permissions are deleted from the previous login session.</span></span>  

> [!NOTE]
> <span data-ttu-id="6925e-176">Quando você consente com as permissões do dispositivo nativo, ele é válido somente para sua _sessão de_ logon atual.</span><span class="sxs-lookup"><span data-stu-id="6925e-176">When you consent to the native device permissions, it is valid only for your _current_ login session.</span></span>

## <a name="next-step"></a><span data-ttu-id="6925e-177">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="6925e-177">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6925e-178">Integrar recursos de mídia no Teams</span><span class="sxs-lookup"><span data-stu-id="6925e-178">Integrate media capabilities in Teams</span></span>](mobile-camera-image-permissions.md)
