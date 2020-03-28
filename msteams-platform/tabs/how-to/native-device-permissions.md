---
title: Solicitar permissões de dispositivo para a guia do Microsoft Teams
description: Como atualizar seu manifesto de aplicativo para solicitar acesso a recursos nativos que geralmente exigem o consentimento do usuário
keywords: desenvolvimento de guias do teams
ms.openlocfilehash: e9dc6c6f177e3a87e2846bcb836cc38601c9a50e
ms.sourcegitcommit: b13b38a104946c32cd5245a7af706070e534927d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/28/2020
ms.locfileid: "43034033"
---
# <a name="request-device-permissions-for-your-microsoft-teams-tab"></a><span data-ttu-id="12adc-104">Solicitar permissões de dispositivo para a guia do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="12adc-104">Request device permissions for your Microsoft Teams tab</span></span>

<span data-ttu-id="12adc-105">Você pode querer enriquecer sua guia com recursos que exigem o acesso de funcionalidade de dispositivo nativo, como:</span><span class="sxs-lookup"><span data-stu-id="12adc-105">You might want to enrich your tab with features that require access native device functionality like:</span></span>

* <span data-ttu-id="12adc-106">Câmara</span><span class="sxs-lookup"><span data-stu-id="12adc-106">Camera</span></span>
* <span data-ttu-id="12adc-107">Microfone</span><span class="sxs-lookup"><span data-stu-id="12adc-107">Microphone</span></span>
* <span data-ttu-id="12adc-108">Local</span><span class="sxs-lookup"><span data-stu-id="12adc-108">Location</span></span>
* <span data-ttu-id="12adc-109">Notificações</span><span class="sxs-lookup"><span data-stu-id="12adc-109">Notifications</span></span>

![Tela de configurações de permissões de dispositivo](~/assets/images/tabs/device-permissions.png)

> [!IMPORTANT]
>
> <span data-ttu-id="12adc-111">Atualmente, a funcionalidade de dispositivo nativo não é suportada para guias em clientes móveis.</span><span class="sxs-lookup"><span data-stu-id="12adc-111">Native device functionality is currently not supported for tabs on mobile clients.</span></span>
>
> <span data-ttu-id="12adc-112">Atualmente, a API de localização geográfica não tem suporte total em todos os clientes de desktop.</span><span class="sxs-lookup"><span data-stu-id="12adc-112">The geolocation API is currently not fully supported on all desktop clients.</span></span>

## <a name="device-permissions"></a><span data-ttu-id="12adc-113">Permissões de dispositivos</span><span class="sxs-lookup"><span data-stu-id="12adc-113">Device permissions</span></span>

<span data-ttu-id="12adc-114">O acesso às permissões de dispositivo de um usuário permite que você construa experiências muito mais ricas, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="12adc-114">Accessing a user’s device permissions allows you to build much richer experiences, for example:</span></span>

* <span data-ttu-id="12adc-115">Gravar e compartilhar vídeos curtos</span><span class="sxs-lookup"><span data-stu-id="12adc-115">Record and share short videos</span></span>
* <span data-ttu-id="12adc-116">Gravar memorandos de áudio curtos e salvá-los para mais tarde</span><span class="sxs-lookup"><span data-stu-id="12adc-116">Record short audio memos and save them for later</span></span>
* <span data-ttu-id="12adc-117">Usar informações de local de usuário para exibir informações relevantes</span><span class="sxs-lookup"><span data-stu-id="12adc-117">Use user location information to display relevant information</span></span>

<span data-ttu-id="12adc-118">Embora o acesso a esses recursos seja padrão nos navegadores da Web mais modernos, você precisa permitir que as equipes saibam quais recursos você gostaria de usar atualizando o manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="12adc-118">While access to these features are standard in most modern web browsers, you need to let Teams know which features you’d like to use by updating your app manifest.</span></span> <span data-ttu-id="12adc-119">Isso permitirá que você solicite permissões, da mesma forma que faria em um navegador, enquanto seu aplicativo está sendo executado no cliente de área de trabalho do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="12adc-119">This will allow you to ask for permissions, the same way you would in a browser, while your app is running on the Teams desktop client.</span></span>

## <a name="properties"></a><span data-ttu-id="12adc-120">Propriedades</span><span class="sxs-lookup"><span data-stu-id="12adc-120">Properties</span></span>

<span data-ttu-id="12adc-121">Atualize o seu aplicativo `manifest.json` adicionando `devicePermissions` e especificando quais das cinco Propriedades você gostaria de usar em seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="12adc-121">Update your app's `manifest.json` by adding `devicePermissions` and specifying which of the five properties you’d like to use in your application:</span></span>

``` json
"devicePermissions": [
    "media",
    "geolocation",
    "notifications",
    "midi",
    "openExternal"
],
```

<span data-ttu-id="12adc-122">Cada propriedade permitirá que o usuário solicite o consentimento dele</span><span class="sxs-lookup"><span data-stu-id="12adc-122">Each property will allow you to prompt the user to ask for their consent</span></span>

| <span data-ttu-id="12adc-123">Propriedade</span><span class="sxs-lookup"><span data-stu-id="12adc-123">Property</span></span>      | <span data-ttu-id="12adc-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="12adc-124">Description</span></span>   |
| --- | --- |
| <span data-ttu-id="12adc-125">mídia</span><span class="sxs-lookup"><span data-stu-id="12adc-125">media</span></span>         | <span data-ttu-id="12adc-126">permissão para usar câmera, microfone e alto-falantes</span><span class="sxs-lookup"><span data-stu-id="12adc-126">permission to use the camera, microphone and speakers</span></span> |
| <span data-ttu-id="12adc-127">localização geográfica</span><span class="sxs-lookup"><span data-stu-id="12adc-127">geolocation</span></span>   | <span data-ttu-id="12adc-128">permissão para retornar o local do usuário</span><span class="sxs-lookup"><span data-stu-id="12adc-128">permission to return the user's location</span></span>      |
| <span data-ttu-id="12adc-129">por</span><span class="sxs-lookup"><span data-stu-id="12adc-129">notifications</span></span> | <span data-ttu-id="12adc-130">permissão para enviar as notificações de usuário</span><span class="sxs-lookup"><span data-stu-id="12adc-130">permission to send the user notifications</span></span>      |
| <span data-ttu-id="12adc-131">Midi</span><span class="sxs-lookup"><span data-stu-id="12adc-131">midi</span></span>          | <span data-ttu-id="12adc-132">permissão para enviar e receber informações de Midi de um instrumento musical digital</span><span class="sxs-lookup"><span data-stu-id="12adc-132">permission to send and receive midi information from a digital musical instrument</span></span>   |
| <span data-ttu-id="12adc-133">openExternal</span><span class="sxs-lookup"><span data-stu-id="12adc-133">openExternal</span></span>  | <span data-ttu-id="12adc-134">permissão para abrir links em aplicativos externos</span><span class="sxs-lookup"><span data-stu-id="12adc-134">permission to open links in external applications</span></span>  |

## <a name="checking-permissions-from-your-tab"></a><span data-ttu-id="12adc-135">Verificando permissões na sua guia</span><span class="sxs-lookup"><span data-stu-id="12adc-135">Checking permissions from your tab</span></span>

<span data-ttu-id="12adc-136">Depois de adicionar `devicePermissions` o manifesto do aplicativo, você poderá verificar as permissões usando a API "permissões" do HTML5 sem causar um aviso.</span><span class="sxs-lookup"><span data-stu-id="12adc-136">Once you’ve added `devicePermissions` to your app manifest, you can check permissions using the HTML5 “permissions” API without causing a prompt.</span></span>

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

## <a name="prompting-the-user"></a><span data-ttu-id="12adc-137">Avisar o usuário</span><span class="sxs-lookup"><span data-stu-id="12adc-137">Prompting the user</span></span>

<span data-ttu-id="12adc-138">Para mostrar um prompt para obter consentimento para acessar permissões de dispositivo, você precisará aproveitar a API HTML5 apropriada.</span><span class="sxs-lookup"><span data-stu-id="12adc-138">In order to show a prompt to get consent to access device permissions you need to leverage the appropriate HTML5 API.</span></span> <span data-ttu-id="12adc-139">Por exemplo, para solicitar que o usuário acesse a câmera que você precisa chamar`getUserMedia`</span><span class="sxs-lookup"><span data-stu-id="12adc-139">For example, in order to prompt the user to access their camera you need to call `getUserMedia`</span></span>

```Javascript
navigator.mediaDevices.getUserMedia({ audio: true, video: true });
```

<span data-ttu-id="12adc-140">A localização geográfica mostrará um prompt de permissão ao chamar`getCurrentPosition`</span><span class="sxs-lookup"><span data-stu-id="12adc-140">Geolocation will  show a permission prompt when you call `getCurrentPosition`</span></span>

```Javascript
navigator.geolocation.getCurrentPosition(function (position) { /*... */ });
```

<span data-ttu-id="12adc-141">As notificações solicitarão o usuário quando você ligar`requestPermission`</span><span class="sxs-lookup"><span data-stu-id="12adc-141">Notifications will prompt the user when you call `requestPermission`</span></span>

```Javascript
Notification.requestPermission(function(result) { /* ... */ });
```

![Prompt de permissões de dispositivo de guias](~/assets/images/tabs/device-permissions-prompt.png)

## <a name="permission-behavior-across-login-sessions"></a><span data-ttu-id="12adc-143">Comportamento de permissão nas sessões de logon</span><span class="sxs-lookup"><span data-stu-id="12adc-143">Permission behavior across login sessions</span></span>

<span data-ttu-id="12adc-144">As permissões de dispositivo nativo são armazenadas por sessão de logon.</span><span class="sxs-lookup"><span data-stu-id="12adc-144">Native device permissions are stored per login session.</span></span> <span data-ttu-id="12adc-145">Isso significa que, se você fizer logon em outra instância do Microsoft Teams (por exemplo, em outro computador), suas permissões de dispositivo de suas sessões anteriores não estarão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="12adc-145">This means that if you log into another instance of Teams (ex: on another computer), your device permissions from your previous sessions will not be available.</span></span> <span data-ttu-id="12adc-146">Em vez disso, você precisará consentir novamente as permissões de dispositivo para a nova sessão de logon.</span><span class="sxs-lookup"><span data-stu-id="12adc-146">Instead, you will need to re-consent to device permissions for the new login session.</span></span> <span data-ttu-id="12adc-147">Isso também significa que, se você fizer logout de equipes (ou mudar locatários dentro do Teams), suas permissões de dispositivo serão excluídas para essa sessão de logon anterior.</span><span class="sxs-lookup"><span data-stu-id="12adc-147">This also means, if you log out of Teams (or switch tenants inside of Teams), your device permissions will be deleted for that previous login session.</span></span> <span data-ttu-id="12adc-148">Tenha isso em mente ao desenvolver permissões de dispositivo nativo: os recursos nativos que você concorda para são apenas para sua sessão de login _atual_ .</span><span class="sxs-lookup"><span data-stu-id="12adc-148">Please keep this in mind when developing native device permissions: the native capabilities you consent to are only for your _current_ login session.</span></span>
