---
title: Solicitar permissões de dispositivo para a guia do Microsoft Teams
description: Como atualizar seu manifesto de aplicativo para solicitar acesso a recursos nativos que geralmente exigem o consentimento do usuário
keywords: desenvolvimento de guias do teams
ms.openlocfilehash: 454466ff17ecf275f6ae6c7413df8e117335f3c8
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672454"
---
# <a name="request-device-permissions-for-your-microsoft-teams-tab"></a><span data-ttu-id="482ae-104">Solicitar permissões de dispositivo para a guia do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="482ae-104">Request device permissions for your Microsoft Teams tab</span></span>

<span data-ttu-id="482ae-105">Você pode querer enriquecer sua guia com recursos que exigem o acesso de funcionalidade de dispositivo nativo, como:</span><span class="sxs-lookup"><span data-stu-id="482ae-105">You might want to enrich your tab with features that require access native device functionality like:</span></span>

* <span data-ttu-id="482ae-106">Câmara</span><span class="sxs-lookup"><span data-stu-id="482ae-106">Camera</span></span>
* <span data-ttu-id="482ae-107">Microfone</span><span class="sxs-lookup"><span data-stu-id="482ae-107">Microphone</span></span>
* <span data-ttu-id="482ae-108">Locais</span><span class="sxs-lookup"><span data-stu-id="482ae-108">Location</span></span>
* <span data-ttu-id="482ae-109">Notificações</span><span class="sxs-lookup"><span data-stu-id="482ae-109">Notifications</span></span>

![Tela de configurações de permissões de dispositivo](~/assets/images/tabs/device-permissions.png)

> [!IMPORTANT]
> <span data-ttu-id="482ae-111">Atualmente, a funcionalidade de dispositivo nativo não é suportada para guias em clientes móveis, mas o suporte completo estará disponível em breve.</span><span class="sxs-lookup"><span data-stu-id="482ae-111">Native device functionality is currently not supported for tabs on mobile clients but full support is coming soon.</span></span> <span data-ttu-id="482ae-112">Para se preparar para essa alteração, você deve seguir as [orientações para guias em celular](~/tabs/design/tabs-mobile.md) ao criar suas guias.</span><span class="sxs-lookup"><span data-stu-id="482ae-112">To prepare for this change you should follow the [guidance for tabs on mobile](~/tabs/design/tabs-mobile.md) when creating your tabs.</span></span> <span data-ttu-id="482ae-113">Os aplicativos pessoais (guias estáticas) estão disponíveis atualmente na [visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md).</span><span class="sxs-lookup"><span data-stu-id="482ae-113">Personal apps (static tabs) are currently available in [developer preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>
>
> <span data-ttu-id="482ae-114">Quando o suporte completo para guias é liberado:</span><span class="sxs-lookup"><span data-stu-id="482ae-114">When full support for tabs is released:</span></span>
>
> * <span data-ttu-id="482ae-115">Todas as guias sempre estarão disponíveis em dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="482ae-115">All tabs will always be available on mobile</span></span>
> * <span data-ttu-id="482ae-116">O `contentUrl` **será carregado no cliente do Mobile Teams**.</span><span class="sxs-lookup"><span data-stu-id="482ae-116">Your `contentUrl` **will be loaded in the mobile Teams client**.</span></span>
> * <span data-ttu-id="482ae-117">Para guias de canal/grupo, os usuários ainda podem abrir sua guia em um navegador separado `websiteUrl`por meio de `contentUrl` seu, no entanto, seu primeiro será carregado.</span><span class="sxs-lookup"><span data-stu-id="482ae-117">For channel/group tabs, users can still open your tab in a separate browser via your `websiteUrl`, however your `contentUrl` will be loaded first.</span></span>  

## <a name="device-permissions"></a><span data-ttu-id="482ae-118">Permissões de dispositivos</span><span class="sxs-lookup"><span data-stu-id="482ae-118">Device permissions</span></span>

<span data-ttu-id="482ae-119">O acesso às permissões de dispositivo de um usuário permite que você construa experiências muito mais ricas, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="482ae-119">Accessing a user’s device permissions allows you to build much richer experiences, for example:</span></span>

* <span data-ttu-id="482ae-120">Gravar e compartilhar vídeos curtos</span><span class="sxs-lookup"><span data-stu-id="482ae-120">Record and share short videos</span></span>
* <span data-ttu-id="482ae-121">Gravar memorandos de áudio curtos e salvá-los para mais tarde</span><span class="sxs-lookup"><span data-stu-id="482ae-121">Record short audio memos and save them for later</span></span>
* <span data-ttu-id="482ae-122">Usar informações de local de usuário para exibir informações relevantes</span><span class="sxs-lookup"><span data-stu-id="482ae-122">Use user location information to display relevant information</span></span>

<span data-ttu-id="482ae-123">Embora o acesso a esses recursos seja padrão nos navegadores da Web mais modernos, você precisa permitir que as equipes saibam quais recursos você gostaria de usar atualizando o manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="482ae-123">While access to these features are standard in most modern web browsers, you need to let Teams know which features you’d like to use by updating your app manifest.</span></span> <span data-ttu-id="482ae-124">Isso permitirá que você solicite permissões, da mesma forma que faria em um navegador, enquanto seu aplicativo está sendo executado no cliente de área de trabalho do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="482ae-124">This will allow you to ask for permissions, the same way you would in a browser, while your app is running on the Teams desktop client.</span></span>

## <a name="properties"></a><span data-ttu-id="482ae-125">Propriedades</span><span class="sxs-lookup"><span data-stu-id="482ae-125">Properties</span></span>

<span data-ttu-id="482ae-126">Atualize o seu aplicativo `manifest.json` adicionando `devicePermissions` e especificando quais das cinco Propriedades você gostaria de usar em seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="482ae-126">Update your app's `manifest.json` by adding `devicePermissions` and specifying which of the five properties you’d like to use in your application:</span></span>

``` json
"devicePermissions": [
    "media",
    "geolocation",
    "notifications",
    "midi",
    "openExternal"
],
```

<span data-ttu-id="482ae-127">Cada propriedade permitirá que o usuário solicite o consentimento dele</span><span class="sxs-lookup"><span data-stu-id="482ae-127">Each property will allow you to prompt the user to ask for their consent</span></span>

| <span data-ttu-id="482ae-128">Propriedade</span><span class="sxs-lookup"><span data-stu-id="482ae-128">Property</span></span>      | <span data-ttu-id="482ae-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="482ae-129">Description</span></span>   |
| --- | --- |
| <span data-ttu-id="482ae-130">corre</span><span class="sxs-lookup"><span data-stu-id="482ae-130">media</span></span>         | <span data-ttu-id="482ae-131">permissão para usar câmera, microfone e alto-falantes</span><span class="sxs-lookup"><span data-stu-id="482ae-131">permission to use the camera, microphone and speakers</span></span> |
| <span data-ttu-id="482ae-132">localização geográfica</span><span class="sxs-lookup"><span data-stu-id="482ae-132">geolocation</span></span>   | <span data-ttu-id="482ae-133">permissão para retornar o local do usuário</span><span class="sxs-lookup"><span data-stu-id="482ae-133">permission to return the user's location</span></span>      |
| <span data-ttu-id="482ae-134">por</span><span class="sxs-lookup"><span data-stu-id="482ae-134">notifications</span></span> | <span data-ttu-id="482ae-135">permissão para enviar as notificações de usuário</span><span class="sxs-lookup"><span data-stu-id="482ae-135">permission to send the user notifications</span></span>      |
| <span data-ttu-id="482ae-136">Midi</span><span class="sxs-lookup"><span data-stu-id="482ae-136">midi</span></span>          | <span data-ttu-id="482ae-137">permissão para enviar e receber informações de Midi de um instrumento musical digital</span><span class="sxs-lookup"><span data-stu-id="482ae-137">permission to send and receive midi information from a digital musical instrument</span></span>   |
| <span data-ttu-id="482ae-138">openExternal</span><span class="sxs-lookup"><span data-stu-id="482ae-138">openExternal</span></span>  | <span data-ttu-id="482ae-139">permissão para abrir links em aplicativos externos</span><span class="sxs-lookup"><span data-stu-id="482ae-139">permission to open links in external applications</span></span>  |

## <a name="checking-permissions-from-your-tab"></a><span data-ttu-id="482ae-140">Verificando permissões na sua guia</span><span class="sxs-lookup"><span data-stu-id="482ae-140">Checking permissions from your tab</span></span>

<span data-ttu-id="482ae-141">Depois de adicionar `devicePermissions` o manifesto do aplicativo, você poderá verificar as permissões usando a API "permissões" do HTML5 sem causar um aviso.</span><span class="sxs-lookup"><span data-stu-id="482ae-141">Once you’ve added `devicePermissions` to your app manifest, you can check permissions using the HTML5 “permissions” API without causing a prompt.</span></span>

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

## <a name="prompting-the-user"></a><span data-ttu-id="482ae-142">Avisar o usuário</span><span class="sxs-lookup"><span data-stu-id="482ae-142">Prompting the user</span></span>

<span data-ttu-id="482ae-143">Para mostrar um prompt para obter consentimento para acessar permissões de dispositivo, você precisará aproveitar a API HTML5 apropriada.</span><span class="sxs-lookup"><span data-stu-id="482ae-143">In order to show a prompt to get consent to access device permissions you need to leverage the appropriate HTML5 API.</span></span> <span data-ttu-id="482ae-144">Por exemplo, para solicitar que o usuário acesse a câmera que você precisa chamar`getUserMedia`</span><span class="sxs-lookup"><span data-stu-id="482ae-144">For example, in order to prompt the user to access their camera you need to call `getUserMedia`</span></span>

```Javascript
navigator.mediaDevices.getUserMedia({ audio: true, video: true });
```

<span data-ttu-id="482ae-145">A localização geográfica mostrará um prompt de permissão ao chamar`getCurrentPosition`</span><span class="sxs-lookup"><span data-stu-id="482ae-145">Geolocation will  show a permission prompt when you call `getCurrentPosition`</span></span>

```Javascript
navigator.geolocation.getCurrentPosition(function (position) { /*... */ });
```

<span data-ttu-id="482ae-146">As notificações solicitarão o usuário quando você ligar`requestPermission`</span><span class="sxs-lookup"><span data-stu-id="482ae-146">Notifications will prompt the user when you call `requestPermission`</span></span>

```Javascript
Notification.requestPermission(function(result) { /* ... */ });
```

![Prompt de permissões de dispositivo de guias](~/assets/images/tabs/device-permissions-prompt.png)