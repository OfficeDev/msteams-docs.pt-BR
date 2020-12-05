---
title: Recursos de câmera e imagem no Teams
description: Como usar o SDK de cliente do Microsoft Teams para habilitar recursos nativos de câmera e imagem
keywords: recursos de imagem de câmera permissões de dispositivo nativo
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: d0ca4dc9c289ec525aa99ea0e156a9f91f5b5d4a
ms.sourcegitcommit: 50571f5c6afc86177c4fe1032fe13366a7b706dd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2020
ms.locfileid: "49576867"
---
# <a name="camera-and-image-capabilities-in-teams"></a><span data-ttu-id="cbfe2-104">Recursos de câmera e imagem no Teams</span><span class="sxs-lookup"><span data-stu-id="cbfe2-104">Camera and image capabilities in Teams</span></span>

>[!IMPORTANT]
>
> * <span data-ttu-id="cbfe2-105">No momento, o suporte do teams para recursos de câmera e imagem só está disponível para clientes móveis.</span><span class="sxs-lookup"><span data-stu-id="cbfe2-105">At present, Teams support for camera and image capabilities is only available for mobile clients.</span></span>
>* <span data-ttu-id="cbfe2-106">As `selectMedia` `getMedia` APIs, e `viewImages` podem ser chamadas de várias superfícies de equipes, como módulos de tarefas, guias e aplicativos pessoais.</span><span class="sxs-lookup"><span data-stu-id="cbfe2-106">The `selectMedia`, `getMedia`, and `viewImages` APIs can be invoked from multiple Teams surfaces such as task modules, tabs, and personal apps.</span></span> <span data-ttu-id="cbfe2-107">Para obter mais detalhes, _consulte_ [pontos de entrada para aplicativos do teams](../extensibility-points.md)</span><span class="sxs-lookup"><span data-stu-id="cbfe2-107">For more details, _see_ [Entry points for Teams apps](../extensibility-points.md)</span></span>

<span data-ttu-id="cbfe2-108">Você pode usar o  [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)para integrar facilmente os recursos de imagem e câmera no seu aplicativo móvel do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="cbfe2-108">You can use the  [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true), to easily integrate camera and image capabilities within your Microsoft Teams mobile app.</span></span> <span data-ttu-id="cbfe2-109">O SDK fornece as ferramentas necessárias para que seu aplicativo acesse as [permissões de dispositivo](native-device-permissions.md?tabs=desktop#device-permissions) de um usuário e crie uma experiência mais rica.</span><span class="sxs-lookup"><span data-stu-id="cbfe2-109">The SDK provides the tools necessary for your app to access a user’s [device permissions](native-device-permissions.md?tabs=desktop#device-permissions) and build a richer experience.</span></span>

<span data-ttu-id="cbfe2-110">As APIs [selectMedia](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true), [getmedia](/javascript/api/@microsoft/teams-js/_media?view=msteams-client-js-latest#getMedia__error__SdkError__blob__Blob_____void_&preserve-view=true)e [viewImages](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#viewImages_ImageUri_____error___SdkError_____void_&preserve-view=true) permitem que você use recursos de câmera/imagem nativos da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="cbfe2-110">The [selectMedia](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true), [getMedia](/javascript/api/@microsoft/teams-js/_media?view=msteams-client-js-latest#getMedia__error__SdkError__blob__Blob_____void_&preserve-view=true), and [viewImages](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#viewImages_ImageUri_____error___SdkError_____void_&preserve-view=true) APIs enable you to use native camera/image capabilities as follows:</span></span>

* <span data-ttu-id="cbfe2-111">Use o **controle de câmera** nativo para permitir que os usuários **capturem e anexem imagens** no go.</span><span class="sxs-lookup"><span data-stu-id="cbfe2-111">Use native **camera control** to allow users to **capture and attach images** on the go.</span></span>
* <span data-ttu-id="cbfe2-112">Use o **suporte da Galeria** nativa para permitir que os usuários **selecionem imagens de dispositivos** como anexos.</span><span class="sxs-lookup"><span data-stu-id="cbfe2-112">Use native **gallery support** to allow users to **select device images** as attachments.</span></span>
* <span data-ttu-id="cbfe2-113">Use o **controle** nativo do Visualizador de imagens para **Visualizar várias imagens** de uma só vez.</span><span class="sxs-lookup"><span data-stu-id="cbfe2-113">Use native **image viewer control** to **preview multiple images** at one time.</span></span>
* <span data-ttu-id="cbfe2-114">Suporte para **transferência de imagem grande** (até 50 MB) por meio da ponte do SDK</span><span class="sxs-lookup"><span data-stu-id="cbfe2-114">Support **large image transfer** (up to 50 MB) via the SDK bridge</span></span>
* <span data-ttu-id="cbfe2-115">Suporte a **recursos avançados de imagem** , permitindo que os usuários visualizem e editem imagens:</span><span class="sxs-lookup"><span data-stu-id="cbfe2-115">Support **advanced image capabilities** allowing users to preview and edit images:</span></span>
  * <span data-ttu-id="cbfe2-116">Digitalize documentos, quadros de comunicações, cartões de visita, etc., através da câmera.</span><span class="sxs-lookup"><span data-stu-id="cbfe2-116">Scan document, whiteboard, business cards, etc., through the camera.</span></span>
  * <span data-ttu-id="cbfe2-117">Corte e gire as imagens.</span><span class="sxs-lookup"><span data-stu-id="cbfe2-117">Crop and rotate the images.</span></span>
  * <span data-ttu-id="cbfe2-118">Adicione texto, tinta ou anotação à mão livre à imagem.</span><span class="sxs-lookup"><span data-stu-id="cbfe2-118">Add text, ink, or freehand annotation to the image.</span></span>

## <a name="get-started"></a><span data-ttu-id="cbfe2-119">Introdução</span><span class="sxs-lookup"><span data-stu-id="cbfe2-119">Get started</span></span>

<span data-ttu-id="cbfe2-120">Atualize seu aplicativo do Microsoft Teams [manifest.jsno](../../resources/schema/manifest-schema.md#devicepermissions) arquivo adicionando a `devicePermissions`  propriedade e especificando `media` .</span><span class="sxs-lookup"><span data-stu-id="cbfe2-120">Update your Teams app [manifest.json](../../resources/schema/manifest-schema.md#devicepermissions) file by adding the `devicePermissions`  property and specifying `media`.</span></span> <span data-ttu-id="cbfe2-121">Isso permite que seu aplicativo solicite permissões de requisitos dos usuários finais antes de usar a câmera para capturar a imagem ou abrir a galeria para selecionar uma imagem a ser enviada como um anexo.</span><span class="sxs-lookup"><span data-stu-id="cbfe2-121">This allows your app to ask for requisite permissions from end-users before they use the camera to capture the image or open the gallery to select an image to submit as an attachment.</span></span>

``` json
"devicePermissions": [
    "media",
],
```

> [!NOTE]
> <span data-ttu-id="cbfe2-122">O prompt _solicitar permissões_ é exibido automaticamente quando uma API de equipe relevante é iniciada.</span><span class="sxs-lookup"><span data-stu-id="cbfe2-122">The _Request Permissions_ prompt is automatically displayed when a relevant Teams API is initiated.</span></span> <span data-ttu-id="cbfe2-123">Para obter mais detalhes, *consulte* [Request Device Permissions](native-device-permissions.md).</span><span class="sxs-lookup"><span data-stu-id="cbfe2-123">For more details, *see* [Request device permissions](native-device-permissions.md).</span></span>

## <a name="using-camera-and-image-capability-apis"></a><span data-ttu-id="cbfe2-124">Usando APIs de capacidade de imagem e câmera</span><span class="sxs-lookup"><span data-stu-id="cbfe2-124">Using camera and image capability APIs</span></span>

<span data-ttu-id="cbfe2-125">Você pode usar o seguinte conjunto de APIs para habilitar recursos de câmera e dispositivo de imagem:</span><span class="sxs-lookup"><span data-stu-id="cbfe2-125">You can use the following set of APIs to enable camera and image device capabilities:</span></span>

| <span data-ttu-id="cbfe2-126">API</span><span class="sxs-lookup"><span data-stu-id="cbfe2-126">API</span></span>      | <span data-ttu-id="cbfe2-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="cbfe2-127">Description</span></span>   |
| --- | --- |
| [<span data-ttu-id="cbfe2-128">**selectMedia**</span><span class="sxs-lookup"><span data-stu-id="cbfe2-128">**selectMedia**</span></span>](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest&branch=master#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true)| <span data-ttu-id="cbfe2-129">Essa API permite que os usuários **capturem ou selecionem mídia de um dispositivo nativo** e retornem ao aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="cbfe2-129">This API allows users to **capture or select media from a native device** and return to the web-app.</span></span> <span data-ttu-id="cbfe2-130">Os usuários podem optar por editar, cortar, girar, anotar ou desenhar imagens antes do envio.</span><span class="sxs-lookup"><span data-stu-id="cbfe2-130">Users may choose to edit, crop, rotate, annotate, or draw over images before submission.</span></span> <span data-ttu-id="cbfe2-131">Em resposta a **selectMedia**, o aplicativo Web receberá IDs de mídia de imagens selecionadas e poderá receber uma miniatura da mídia selecionada.</span><span class="sxs-lookup"><span data-stu-id="cbfe2-131">In response to **selectMedia**, the web-app will receive media ids of selected images and may receive a thumbnail of the selected media.</span></span> |
| [<span data-ttu-id="cbfe2-132">**getmedia**</span><span class="sxs-lookup"><span data-stu-id="cbfe2-132">**getMedia**</span></span>](/javascript/api/@microsoft/teams-js/_media?view=msteams-client-js-latest&branch=master#getMedia__error__SdkError__blob__Blob_____void_&preserve-view=true)| <span data-ttu-id="cbfe2-133">Essa API recupera a mídia em partes independentemente do tamanho.</span><span class="sxs-lookup"><span data-stu-id="cbfe2-133">This API retrieves the media in chunks irrespective of size.</span></span> <span data-ttu-id="cbfe2-134">Esses blocos são montados e enviados de volta ao aplicativo Web como um arquivo/BLOB.</span><span class="sxs-lookup"><span data-stu-id="cbfe2-134">These chunks are assembled and sent back to the web app as a file/blob.</span></span> <span data-ttu-id="cbfe2-135">Com esta API, uma imagem é quebrada em partes menores para facilitar a transferência de imagem grande.</span><span class="sxs-lookup"><span data-stu-id="cbfe2-135">With this API an image is broken into smaller chunks to facilitate large image transfer.</span></span> |
| [<span data-ttu-id="cbfe2-136">**viewImages**</span><span class="sxs-lookup"><span data-stu-id="cbfe2-136">**viewImages**</span></span>](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#viewImages_ImageUri_____error___SdkError_____void_&preserve-view=true)| <span data-ttu-id="cbfe2-137">Essa API permite que o usuário visualize imagens no modo de tela inteira como uma lista rolável.</span><span class="sxs-lookup"><span data-stu-id="cbfe2-137">This API enables the user to view images full-screen mode as a scrollable list.</span></span>|

<span data-ttu-id="cbfe2-138">**Experiência do aplicativo Web para a API** 
 ![ do selectMedia experiência de imagem e câmera de dispositivos no Microsoft Teams](../../assets/images/tabs/image-capability-screenshot.jpg)</span><span class="sxs-lookup"><span data-stu-id="cbfe2-138">**Web app experience for selectMedia API**
![device camera and image experience in Teams](../../assets/images/tabs/image-capability-screenshot.jpg)</span></span>

## <a name="error-handling"></a><span data-ttu-id="cbfe2-139">Tratamento de erros</span><span class="sxs-lookup"><span data-stu-id="cbfe2-139">Error handling</span></span>

<span data-ttu-id="cbfe2-140">Você deve entender os códigos de erro de resposta da API e tratá-los adequadamente.</span><span class="sxs-lookup"><span data-stu-id="cbfe2-140">You should understand the API response error codes and handle them appropriately.</span></span> <span data-ttu-id="cbfe2-141">Veja a seguir uma lista de códigos de erro que podem ser retornados pela plataforma:</span><span class="sxs-lookup"><span data-stu-id="cbfe2-141">Below is a list of error codes that may be returned by the platform:</span></span>

|<span data-ttu-id="cbfe2-142">Código de erro</span><span class="sxs-lookup"><span data-stu-id="cbfe2-142">Error code</span></span> |  <span data-ttu-id="cbfe2-143">Nome do erro</span><span class="sxs-lookup"><span data-stu-id="cbfe2-143">Error Name</span></span>     | <span data-ttu-id="cbfe2-144">Condition</span><span class="sxs-lookup"><span data-stu-id="cbfe2-144">Condition</span></span>|
| --- | --- | --- |
| <span data-ttu-id="cbfe2-145">**100**</span><span class="sxs-lookup"><span data-stu-id="cbfe2-145">**100**</span></span> | <span data-ttu-id="cbfe2-146">NOT_SUPPORTED_ON_PLATFORM</span><span class="sxs-lookup"><span data-stu-id="cbfe2-146">NOT_SUPPORTED_ON_PLATFORM</span></span> | <span data-ttu-id="cbfe2-147">API não tem suporte na plataforma atual.</span><span class="sxs-lookup"><span data-stu-id="cbfe2-147">API not supported in the current platform.</span></span>|
| <span data-ttu-id="cbfe2-148">**404**</span><span class="sxs-lookup"><span data-stu-id="cbfe2-148">**404**</span></span> | <span data-ttu-id="cbfe2-149">FILE_NOT_FOUND</span><span class="sxs-lookup"><span data-stu-id="cbfe2-149">FILE_NOT_FOUND</span></span> | <span data-ttu-id="cbfe2-150">O arquivo especificado não foi encontrado no local especificado.</span><span class="sxs-lookup"><span data-stu-id="cbfe2-150">The file specified was not found on the given location.</span></span>|
| <span data-ttu-id="cbfe2-151">**500**</span><span class="sxs-lookup"><span data-stu-id="cbfe2-151">**500**</span></span> | <span data-ttu-id="cbfe2-152">INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="cbfe2-152">INTERNAL_ERROR</span></span> | <span data-ttu-id="cbfe2-153">Erro interno encontrado ao executar a operação necessária.</span><span class="sxs-lookup"><span data-stu-id="cbfe2-153">Internal error encountered while performing the required operation.</span></span>|
| <span data-ttu-id="cbfe2-154">**1000**</span><span class="sxs-lookup"><span data-stu-id="cbfe2-154">**1000**</span></span> | <span data-ttu-id="cbfe2-155">PERMISSION_DENIED</span><span class="sxs-lookup"><span data-stu-id="cbfe2-155">PERMISSION_DENIED</span></span> |<span data-ttu-id="cbfe2-156">Permissões negadas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="cbfe2-156">Permissions denied by the user.</span></span>|
| <span data-ttu-id="cbfe2-157">**2000**</span><span class="sxs-lookup"><span data-stu-id="cbfe2-157">**2000**</span></span> |<span data-ttu-id="cbfe2-158">NETWORK_ERROR</span><span class="sxs-lookup"><span data-stu-id="cbfe2-158">NETWORK_ERROR</span></span> | <span data-ttu-id="cbfe2-159">Problema de rede.</span><span class="sxs-lookup"><span data-stu-id="cbfe2-159">Network issue.</span></span>|
| <span data-ttu-id="cbfe2-160">**3000**</span><span class="sxs-lookup"><span data-stu-id="cbfe2-160">**3000**</span></span> | <span data-ttu-id="cbfe2-161">NO_HW_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="cbfe2-161">NO_HW_SUPPORT</span></span> | <span data-ttu-id="cbfe2-162">O hardware subjacente não dá suporte ao recurso.</span><span class="sxs-lookup"><span data-stu-id="cbfe2-162">Underlying hardware doesn't support the capability.</span></span>|
| <span data-ttu-id="cbfe2-163">**4000**</span><span class="sxs-lookup"><span data-stu-id="cbfe2-163">**4000**</span></span>| <span data-ttu-id="cbfe2-164">INVALID_ARGUMENTS</span><span class="sxs-lookup"><span data-stu-id="cbfe2-164">INVALID_ARGUMENTS</span></span> | <span data-ttu-id="cbfe2-165">Um ou mais argumentos são inválidos.</span><span class="sxs-lookup"><span data-stu-id="cbfe2-165">One or more arguments is invalid.</span></span>|
| <span data-ttu-id="cbfe2-166">**5000**</span><span class="sxs-lookup"><span data-stu-id="cbfe2-166">**5000**</span></span> | <span data-ttu-id="cbfe2-167">UNAUTHORIZED_USER_OPERATION</span><span class="sxs-lookup"><span data-stu-id="cbfe2-167">UNAUTHORIZED_USER_OPERATION</span></span> | <span data-ttu-id="cbfe2-168">O usuário não está autorizado a concluir esta operação.</span><span class="sxs-lookup"><span data-stu-id="cbfe2-168">User is not authorized to complete this operation.</span></span>|
| <span data-ttu-id="cbfe2-169">**6000**</span><span class="sxs-lookup"><span data-stu-id="cbfe2-169">**6000**</span></span> |<span data-ttu-id="cbfe2-170">INSUFFICIENT_RESOURCES</span><span class="sxs-lookup"><span data-stu-id="cbfe2-170">INSUFFICIENT_RESOURCES</span></span> | <span data-ttu-id="cbfe2-171">A operação não pôde ser concluída devido a recursos insuficientes.</span><span class="sxs-lookup"><span data-stu-id="cbfe2-171">The operation couldn't be completed due to insufficient resources.</span></span>|
|<span data-ttu-id="cbfe2-172">**7000**</span><span class="sxs-lookup"><span data-stu-id="cbfe2-172">**7000**</span></span> | <span data-ttu-id="cbfe2-173">THROTTLE</span><span class="sxs-lookup"><span data-stu-id="cbfe2-173">THROTTLE</span></span> | <span data-ttu-id="cbfe2-174">A plataforma limitou a solicitação porque a API foi invocada com frequência.</span><span class="sxs-lookup"><span data-stu-id="cbfe2-174">The platform throttled the request because the API was invoked too frequently.</span></span>|
|  <span data-ttu-id="cbfe2-175">**8000**</span><span class="sxs-lookup"><span data-stu-id="cbfe2-175">**8000**</span></span> | <span data-ttu-id="cbfe2-176">USER_ABORT</span><span class="sxs-lookup"><span data-stu-id="cbfe2-176">USER_ABORT</span></span> |<span data-ttu-id="cbfe2-177">O usuário anulou a operação.</span><span class="sxs-lookup"><span data-stu-id="cbfe2-177">User aborted the operation.</span></span>|
| <span data-ttu-id="cbfe2-178">**9000**</span><span class="sxs-lookup"><span data-stu-id="cbfe2-178">**9000**</span></span>| <span data-ttu-id="cbfe2-179">OLD_PLATFORM</span><span class="sxs-lookup"><span data-stu-id="cbfe2-179">OLD_PLATFORM</span></span> | <span data-ttu-id="cbfe2-180">O código da plataforma está desatualizado e não implementa essa API.</span><span class="sxs-lookup"><span data-stu-id="cbfe2-180">The platform code is outdated and doesn't implement this API.</span></span>|
| <span data-ttu-id="cbfe2-181">**10000**</span><span class="sxs-lookup"><span data-stu-id="cbfe2-181">**10000**</span></span>| <span data-ttu-id="cbfe2-182">SIZE_EXCEEDED</span><span class="sxs-lookup"><span data-stu-id="cbfe2-182">SIZE_EXCEEDED</span></span> |  <span data-ttu-id="cbfe2-183">O valor de retorno é muito grande e excedeu os limites de tamanho de plataforma.</span><span class="sxs-lookup"><span data-stu-id="cbfe2-183">The return value is too big and has exceeded the platform size boundaries.</span></span>|

## <a name="sample-code-snippets"></a><span data-ttu-id="cbfe2-184">Trechos de código de exemplo</span><span class="sxs-lookup"><span data-stu-id="cbfe2-184">Sample code snippets</span></span>

<span data-ttu-id="cbfe2-185">**API de chamada `selectMedia`**</span><span class="sxs-lookup"><span data-stu-id="cbfe2-185">**Calling `selectMedia` API**</span></span>

```javascript
let imageProp: microsoftTeams.media.ImageProps = {
    sources: [microsoftTeams.media.Source.Camera, microsoftTeams.media.Source.Gallery],
    startMode: microsoftTeams.media.CameraStartMode.Photo,
    ink: false,
    cameraSwitcher: false,
    textSticker: false,
    enableFilter: true,
};
let mediaInput: microsoftTeams.media.MediaInputs = {
    mediaType: microsoftTeams.media.MediaType.Image,
    maxMediaCount: 10,
    imageProps: imageProp
};
microsoftTeams.media.selectMedia(mediaInput, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
    if (error) {
        if (error.message) {
            alert(" ErrorCode: " + error.errorCode + error.message);
        } else {
            alert(" ErrorCode: " + error.errorCode);
        }
    }
    if (attachments) {
        let y = attachments[0];
        img.src = ("data:" + y.mimeType + ";base64," + y.preview);
    }
});
```

<span data-ttu-id="cbfe2-186">**API de chamada `getMedia`**</span><span class="sxs-lookup"><span data-stu-id="cbfe2-186">**Calling `getMedia` API**</span></span>

```javascript
let media: microsoftTeams.media.Media = attachments[0]
media.getMedia((error: microsoftTeams.SdkError, blob: Blob) => {
    if (blob) {
        if (blob.type.includes("image")) {
            img.src = (URL.createObjectURL(blob));
        }
    }
    if (error) {
        if (error.message) {
            alert(" ErrorCode: " + error.errorCode + error.message);
        } else {
            alert(" ErrorCode: " + error.errorCode);
        }
    }
});
```

<span data-ttu-id="cbfe2-187">**Chamar `viewImages`  a API por ID**</span><span class="sxs-lookup"><span data-stu-id="cbfe2-187">**Calling `viewImages`  API by ID**</span></span>

```javascript
view images by id:
    assumption: attachmentArray = select Media API Outputlet uriList = [];
if (attachmentArray && attachmentArray.length > 0) {
    for (let i = 0; i < attachmentArray.length; i++) {
        let file = attachmentArray[i];
        if (file.mimeType.includes("image")) {
            let imageUri = {
                value: file.content,
                type: 1,
            }
            uriList.push(imageUri);
        } else {
            alert("File type is not image");
        }
    }
}
if (uriList.length > 0) {
    microsoftTeams.media.viewImages(uriList, (error: microsoftTeams.SdkError) => {
        if (error) {
            if (error.message) {
                output(" ErrorCode: " + error.errorCode + error.message);
            } else {
                output(" ErrorCode: " + error.errorCode);
            }
        }
    });
} else {
    output("Url list is empty");
}
```

<span data-ttu-id="cbfe2-188">**Chamar a API viewImages por URL**</span><span class="sxs-lookup"><span data-stu-id="cbfe2-188">**Calling viewImages API by URL**</span></span>

```javascript
View Images by URL:
    // Assumption 2 urls, url1 and url2let uriList = [];
    if (URL1 != null && URL1.length > 0) {
        let imageUri = {
            value: URL1,
            type: 2,
        }
        uriList.push(imageUri);
    }
if (URL2 != null && URL2.length > 0) {
    let imageUri = {
        value: URL2,
        type: 2,
    }
    uriList.push(imageUri);
}
if (uriList.length > 0) {
    microsoftTeams.media.viewImages(uriList, (error: microsoftTeams.SdkError) => {
        if (error) {
            if (error.message) {
                output(" ErrorCode: " + error.errorCode + error.message);
            } else {
                output(" ErrorCode: " + error.errorCode);
            }
        }
    });
} else {
    output("Url list is empty");
}
}
```
