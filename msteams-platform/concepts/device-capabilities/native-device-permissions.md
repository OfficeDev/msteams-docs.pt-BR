---
title: Solicitar permissões de dispositivo para a guia do Microsoft Teams
description: Como atualizar seu manifesto de aplicativo para solicitar acesso a recursos nativos que geralmente exigem o consentimento do usuário
keywords: desenvolvimento de guias do teams
ms.openlocfilehash: d6c66525ab0e81f0632df5e2c323926279e38a8e
ms.sourcegitcommit: 50571f5c6afc86177c4fe1032fe13366a7b706dd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2020
ms.locfileid: "49576866"
---
# <a name="request-device-permissions-for-your-microsoft-teams-tab"></a><span data-ttu-id="5ac39-104">Solicitar permissões de dispositivo para a guia do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="5ac39-104">Request device permissions for your Microsoft Teams tab</span></span>

<span data-ttu-id="5ac39-105">Você pode querer enriquecer sua guia com recursos que exigem o acesso de funcionalidade de dispositivo nativo, como:</span><span class="sxs-lookup"><span data-stu-id="5ac39-105">You might want to enrich your tab with features that require access native device functionality like:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="5ac39-106">Câmara</span><span class="sxs-lookup"><span data-stu-id="5ac39-106">Camera</span></span>
> * <span data-ttu-id="5ac39-107">Microfone</span><span class="sxs-lookup"><span data-stu-id="5ac39-107">Microphone</span></span>
> * <span data-ttu-id="5ac39-108">Local</span><span class="sxs-lookup"><span data-stu-id="5ac39-108">Location</span></span>
> * <span data-ttu-id="5ac39-109">Notificações</span><span class="sxs-lookup"><span data-stu-id="5ac39-109">Notifications</span></span>

> [!IMPORTANT]
>
> * <span data-ttu-id="5ac39-110">Atualmente, o cliente do teams Mobile só oferece suporte `camera` `location`  a recursos de dispositivos nativos e está disponível em todas as construções de aplicativos, incluindo guias.</span><span class="sxs-lookup"><span data-stu-id="5ac39-110">Currently, Teams mobile client only supports `camera` and `location`  through native device capabilities and is available on all app constructs including tabs.</span></span> </br>
> * <span data-ttu-id="5ac39-111">O suporte para `camera` captura de imagem está habilitado pela [**API captureImage**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="5ac39-111">Support for `camera` image capture is enabled by the [**captureImage API**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true).</span></span>
> * <span data-ttu-id="5ac39-112">Atualmente, a [**API de localização geográfica**](../../resources/schema/manifest-schema.md#devicepermissions) não tem suporte total em todos os clientes de desktop.</span><span class="sxs-lookup"><span data-stu-id="5ac39-112">The [**geolocation API**](../../resources/schema/manifest-schema.md#devicepermissions) is currently not fully supported on all desktop clients.</span></span>

## <a name="device-permissions"></a><span data-ttu-id="5ac39-113">Permissões de dispositivos</span><span class="sxs-lookup"><span data-stu-id="5ac39-113">Device permissions</span></span>

<span data-ttu-id="5ac39-114">O acesso às permissões de dispositivo de um usuário permite que você construa experiências muito mais ricas, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="5ac39-114">Accessing a user’s device permissions allows you to build much richer experiences, for example:</span></span>

* <span data-ttu-id="5ac39-115">Gravar e compartilhar vídeos curtos</span><span class="sxs-lookup"><span data-stu-id="5ac39-115">Record and share short videos</span></span>
* <span data-ttu-id="5ac39-116">Gravar memorandos de áudio curtos e salvá-los para mais tarde</span><span class="sxs-lookup"><span data-stu-id="5ac39-116">Record short audio memos and save them for later</span></span>
* <span data-ttu-id="5ac39-117">Usar informações de local de usuário para exibir informações relevantes</span><span class="sxs-lookup"><span data-stu-id="5ac39-117">Use user location information to display relevant information</span></span>

<span data-ttu-id="5ac39-118">Embora o acesso a esses recursos seja padrão nos navegadores da Web mais modernos, você precisa permitir que as equipes saibam quais recursos você gostaria de usar atualizando o manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5ac39-118">While access to these features are standard in most modern web browsers, you need to let Teams know which features you’d like to use by updating your app manifest.</span></span> <span data-ttu-id="5ac39-119">Isso permitirá que você solicite permissões, da mesma forma que faria em um navegador, enquanto seu aplicativo está sendo executado no cliente de área de trabalho do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="5ac39-119">This will allow you to ask for permissions, the same way you would in a browser, while your app is running on the Teams desktop client.</span></span>

## <a name="manage-permissions"></a><span data-ttu-id="5ac39-120">Gerenciar permissões</span><span class="sxs-lookup"><span data-stu-id="5ac39-120">Manage permissions</span></span>

# <a name="desktop"></a>[<span data-ttu-id="5ac39-121">Desktop</span><span class="sxs-lookup"><span data-stu-id="5ac39-121">Desktop</span></span>](#tab/desktop)

1. <span data-ttu-id="5ac39-122">Abra o Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="5ac39-122">Open Teams.</span></span>
1. <span data-ttu-id="5ac39-123">No canto superior direito da janela, selecione o ícone do seu perfil.</span><span class="sxs-lookup"><span data-stu-id="5ac39-123">In the upper right corner of the window, select your profile icon.</span></span>
1. <span data-ttu-id="5ac39-124">Selecione **Settings**  ->  **permissões** de configurações no menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="5ac39-124">Select **Settings** -> **Permissions** from the drop-down menu.</span></span>
1. <span data-ttu-id="5ac39-125">Escolha as configurações desejadas.</span><span class="sxs-lookup"><span data-stu-id="5ac39-125">Choose your desired settings.</span></span>

![Tela de configurações da área de trabalho de permissões de dispositivo](../../assets/images/tabs/device-permissions.png)

# <a name="mobile"></a>[<span data-ttu-id="5ac39-127">Mobile</span><span class="sxs-lookup"><span data-stu-id="5ac39-127">Mobile</span></span>](#tab/mobile)

1. <span data-ttu-id="5ac39-128">Abra o Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="5ac39-128">Open Teams.</span></span>
1. <span data-ttu-id="5ac39-129">No canto superior esquerdo da tela, selecione o ícone de menu &#9776;.</span><span class="sxs-lookup"><span data-stu-id="5ac39-129">In the upper left corner of the screen, select the &#9776; menu icon.</span></span>
1. <span data-ttu-id="5ac39-130">Selecione **configurações** de  ->  **dispositivos**.</span><span class="sxs-lookup"><span data-stu-id="5ac39-130">Select **Settings** -> **Devices**.</span></span>
1. <span data-ttu-id="5ac39-131">Escolha as configurações desejadas.</span><span class="sxs-lookup"><span data-stu-id="5ac39-131">Choose your desired settings.</span></span>

![Tela de configurações móveis de permissões de dispositivo](../../assets/images/tabs/mobile-device-permissions-screen.png)

---

## <a name="properties"></a><span data-ttu-id="5ac39-133">Propriedades</span><span class="sxs-lookup"><span data-stu-id="5ac39-133">Properties</span></span>

<span data-ttu-id="5ac39-134">Atualize o seu aplicativo `manifest.json` adicionando `devicePermissions` e especificando quais das cinco Propriedades você gostaria de usar em seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="5ac39-134">Update your app's `manifest.json` by adding `devicePermissions` and specifying which of the five properties you’d like to use in your application:</span></span>

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
> <span data-ttu-id="5ac39-135">A mídia também é usada para permissões de câmera no celular.</span><span class="sxs-lookup"><span data-stu-id="5ac39-135">Media is also used for camera permissions in mobile.</span></span>

<span data-ttu-id="5ac39-136">Cada propriedade permitirá que o usuário solicite o consentimento dele</span><span class="sxs-lookup"><span data-stu-id="5ac39-136">Each property will allow you to prompt the user to ask for their consent</span></span>

| <span data-ttu-id="5ac39-137">Propriedade</span><span class="sxs-lookup"><span data-stu-id="5ac39-137">Property</span></span>      | <span data-ttu-id="5ac39-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ac39-138">Description</span></span>   |
| --- | --- |
| <span data-ttu-id="5ac39-139">corre</span><span class="sxs-lookup"><span data-stu-id="5ac39-139">media</span></span>         | <span data-ttu-id="5ac39-140">permissão para usar câmera, microfone e alto-falantes</span><span class="sxs-lookup"><span data-stu-id="5ac39-140">permission to use the camera, microphone and speakers</span></span> |
| <span data-ttu-id="5ac39-141">localização geográfica</span><span class="sxs-lookup"><span data-stu-id="5ac39-141">geolocation</span></span>   | <span data-ttu-id="5ac39-142">permissão para retornar o local do usuário</span><span class="sxs-lookup"><span data-stu-id="5ac39-142">permission to return the user's location</span></span>      |
| <span data-ttu-id="5ac39-143">por</span><span class="sxs-lookup"><span data-stu-id="5ac39-143">notifications</span></span> | <span data-ttu-id="5ac39-144">permissão para enviar as notificações de usuário</span><span class="sxs-lookup"><span data-stu-id="5ac39-144">permission to send the user notifications</span></span>      |
| <span data-ttu-id="5ac39-145">Midi</span><span class="sxs-lookup"><span data-stu-id="5ac39-145">midi</span></span>          | <span data-ttu-id="5ac39-146">permissão para enviar e receber informações de Midi de um instrumento musical digital</span><span class="sxs-lookup"><span data-stu-id="5ac39-146">permission to send and receive midi information from a digital musical instrument</span></span>   |
| <span data-ttu-id="5ac39-147">openExternal</span><span class="sxs-lookup"><span data-stu-id="5ac39-147">openExternal</span></span>  | <span data-ttu-id="5ac39-148">permissão para abrir links em aplicativos externos</span><span class="sxs-lookup"><span data-stu-id="5ac39-148">permission to open links in external applications</span></span>  |

## <a name="checking-permissions-from-your-tab"></a><span data-ttu-id="5ac39-149">Verificando permissões na sua guia</span><span class="sxs-lookup"><span data-stu-id="5ac39-149">Checking permissions from your tab</span></span>

<span data-ttu-id="5ac39-150">Depois de adicionar o `devicePermissions` manifesto do aplicativo, você poderá verificar as permissões usando a API "permissões" do HTML5 sem causar um aviso.</span><span class="sxs-lookup"><span data-stu-id="5ac39-150">Once you’ve added `devicePermissions` to your app manifest, you can check permissions using the HTML5 “permissions” API without causing a prompt.</span></span>

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

## <a name="prompting-the-user"></a><span data-ttu-id="5ac39-151">Avisar o usuário</span><span class="sxs-lookup"><span data-stu-id="5ac39-151">Prompting the user</span></span>

<span data-ttu-id="5ac39-152">Para mostrar um prompt para obter consentimento para acessar permissões de dispositivo, você precisa aproveitar a API do HTML5 ou do teams apropriada.</span><span class="sxs-lookup"><span data-stu-id="5ac39-152">In order to show a prompt to get consent to access device permissions you need to leverage the appropriate HTML5 or Teams API.</span></span> <span data-ttu-id="5ac39-153">Por exemplo, para solicitar que o usuário acesse a câmera que você precisa chamar `getCurrentPosition`</span><span class="sxs-lookup"><span data-stu-id="5ac39-153">For example, in order to prompt the user to access their camera you need to call `getCurrentPosition`</span></span>

```Javascript
navigator.geolocation.getCurrentPosition(function (position) { /*... */ });
```

<span data-ttu-id="5ac39-154">Para usar a câmera na área de trabalho ou na Web, o Microsoft Teams mostrará um prompt de permissão ao chamar getUserMedia</span><span class="sxs-lookup"><span data-stu-id="5ac39-154">To use camera on desktop or web, Teams will show a permission prompt when you call getUserMedia</span></span>

```Javascript
navigator.mediaDevices.getUserMedia({ audio: true, video: true });
```

<span data-ttu-id="5ac39-155">Para capturar imagem em dispositivos móveis, o Microsoft Teams solicitará permissão ao chamar captureImage ()</span><span class="sxs-lookup"><span data-stu-id="5ac39-155">To capture image on mobile, Teams mobile will ask for permission when called captureImage()</span></span>

```Typescript
function captureImage(callback: (error: SdkError, files: File[]) => void)
```

<span data-ttu-id="5ac39-156">As notificações solicitarão o usuário quando você ligar `requestPermission`</span><span class="sxs-lookup"><span data-stu-id="5ac39-156">Notifications will prompt the user when you call `requestPermission`</span></span>

```Javascript
Notification.requestPermission(function(result) { /* ... */ });
```

![Prompt de permissões de dispositivo de guias](~/assets/images/tabs/device-permissions-prompt.png)

## <a name="permission-behavior-across-login-sessions"></a><span data-ttu-id="5ac39-158">Comportamento de permissão nas sessões de logon</span><span class="sxs-lookup"><span data-stu-id="5ac39-158">Permission behavior across login sessions</span></span>

<span data-ttu-id="5ac39-159">As permissões de dispositivo nativo são armazenadas por sessão de logon.</span><span class="sxs-lookup"><span data-stu-id="5ac39-159">Native device permissions are stored per login session.</span></span> <span data-ttu-id="5ac39-160">Isso significa que, se você fizer logon em outra instância do Microsoft Teams (por exemplo, em outro computador), suas permissões de dispositivo de suas sessões anteriores não estarão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="5ac39-160">This means that if you log into another instance of Teams (ex: on another computer), your device permissions from your previous sessions will not be available.</span></span> <span data-ttu-id="5ac39-161">Em vez disso, você precisará consentir novamente as permissões de dispositivo para a nova sessão de logon.</span><span class="sxs-lookup"><span data-stu-id="5ac39-161">Instead, you will need to re-consent to device permissions for the new login session.</span></span> <span data-ttu-id="5ac39-162">Isso também significa que, se você fizer logout de equipes (ou mudar locatários dentro do Teams), suas permissões de dispositivo serão excluídas para essa sessão de logon anterior.</span><span class="sxs-lookup"><span data-stu-id="5ac39-162">This also means, if you log out of Teams (or switch tenants inside of Teams), your device permissions will be deleted for that previous login session.</span></span> <span data-ttu-id="5ac39-163">Tenha isso em mente ao desenvolver permissões de dispositivo nativo: os recursos nativos que você concorda para são apenas para sua sessão de login _atual_ .</span><span class="sxs-lookup"><span data-stu-id="5ac39-163">Please keep this in mind when developing native device permissions: the native capabilities you consent to are only for your _current_ login session.</span></span>
