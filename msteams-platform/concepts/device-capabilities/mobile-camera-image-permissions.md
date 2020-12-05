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
# <a name="camera-and-image-capabilities-in-teams"></a>Recursos de câmera e imagem no Teams

>[!IMPORTANT]
>
> * No momento, o suporte do teams para recursos de câmera e imagem só está disponível para clientes móveis.
>* As `selectMedia` `getMedia` APIs, e `viewImages` podem ser chamadas de várias superfícies de equipes, como módulos de tarefas, guias e aplicativos pessoais. Para obter mais detalhes, _consulte_ [pontos de entrada para aplicativos do teams](../extensibility-points.md)

Você pode usar o  [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)para integrar facilmente os recursos de imagem e câmera no seu aplicativo móvel do Microsoft Teams. O SDK fornece as ferramentas necessárias para que seu aplicativo acesse as [permissões de dispositivo](native-device-permissions.md?tabs=desktop#device-permissions) de um usuário e crie uma experiência mais rica.

As APIs [selectMedia](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true), [getmedia](/javascript/api/@microsoft/teams-js/_media?view=msteams-client-js-latest#getMedia__error__SdkError__blob__Blob_____void_&preserve-view=true)e [viewImages](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#viewImages_ImageUri_____error___SdkError_____void_&preserve-view=true) permitem que você use recursos de câmera/imagem nativos da seguinte maneira:

* Use o **controle de câmera** nativo para permitir que os usuários **capturem e anexem imagens** no go.
* Use o **suporte da Galeria** nativa para permitir que os usuários **selecionem imagens de dispositivos** como anexos.
* Use o **controle** nativo do Visualizador de imagens para **Visualizar várias imagens** de uma só vez.
* Suporte para **transferência de imagem grande** (até 50 MB) por meio da ponte do SDK
* Suporte a **recursos avançados de imagem** , permitindo que os usuários visualizem e editem imagens:
  * Digitalize documentos, quadros de comunicações, cartões de visita, etc., através da câmera.
  * Corte e gire as imagens.
  * Adicione texto, tinta ou anotação à mão livre à imagem.

## <a name="get-started"></a>Introdução

Atualize seu aplicativo do Microsoft Teams [manifest.jsno](../../resources/schema/manifest-schema.md#devicepermissions) arquivo adicionando a `devicePermissions`  propriedade e especificando `media` . Isso permite que seu aplicativo solicite permissões de requisitos dos usuários finais antes de usar a câmera para capturar a imagem ou abrir a galeria para selecionar uma imagem a ser enviada como um anexo.

``` json
"devicePermissions": [
    "media",
],
```

> [!NOTE]
> O prompt _solicitar permissões_ é exibido automaticamente quando uma API de equipe relevante é iniciada. Para obter mais detalhes, *consulte* [Request Device Permissions](native-device-permissions.md).

## <a name="using-camera-and-image-capability-apis"></a>Usando APIs de capacidade de imagem e câmera

Você pode usar o seguinte conjunto de APIs para habilitar recursos de câmera e dispositivo de imagem:

| API      | Descrição   |
| --- | --- |
| [**selectMedia**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest&branch=master#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true)| Essa API permite que os usuários **capturem ou selecionem mídia de um dispositivo nativo** e retornem ao aplicativo Web. Os usuários podem optar por editar, cortar, girar, anotar ou desenhar imagens antes do envio. Em resposta a **selectMedia**, o aplicativo Web receberá IDs de mídia de imagens selecionadas e poderá receber uma miniatura da mídia selecionada. |
| [**getmedia**](/javascript/api/@microsoft/teams-js/_media?view=msteams-client-js-latest&branch=master#getMedia__error__SdkError__blob__Blob_____void_&preserve-view=true)| Essa API recupera a mídia em partes independentemente do tamanho. Esses blocos são montados e enviados de volta ao aplicativo Web como um arquivo/BLOB. Com esta API, uma imagem é quebrada em partes menores para facilitar a transferência de imagem grande. |
| [**viewImages**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#viewImages_ImageUri_____error___SdkError_____void_&preserve-view=true)| Essa API permite que o usuário visualize imagens no modo de tela inteira como uma lista rolável.|

**Experiência do aplicativo Web para a API** 
 ![ do selectMedia experiência de imagem e câmera de dispositivos no Microsoft Teams](../../assets/images/tabs/image-capability-screenshot.jpg)

## <a name="error-handling"></a>Tratamento de erros

Você deve entender os códigos de erro de resposta da API e tratá-los adequadamente. Veja a seguir uma lista de códigos de erro que podem ser retornados pela plataforma:

|Código de erro |  Nome do erro     | Condition|
| --- | --- | --- |
| **100** | NOT_SUPPORTED_ON_PLATFORM | API não tem suporte na plataforma atual.|
| **404** | FILE_NOT_FOUND | O arquivo especificado não foi encontrado no local especificado.|
| **500** | INTERNAL_ERROR | Erro interno encontrado ao executar a operação necessária.|
| **1000** | PERMISSION_DENIED |Permissões negadas pelo usuário.|
| **2000** |NETWORK_ERROR | Problema de rede.|
| **3000** | NO_HW_SUPPORT | O hardware subjacente não dá suporte ao recurso.|
| **4000**| INVALID_ARGUMENTS | Um ou mais argumentos são inválidos.|
| **5000** | UNAUTHORIZED_USER_OPERATION | O usuário não está autorizado a concluir esta operação.|
| **6000** |INSUFFICIENT_RESOURCES | A operação não pôde ser concluída devido a recursos insuficientes.|
|**7000** | THROTTLE | A plataforma limitou a solicitação porque a API foi invocada com frequência.|
|  **8000** | USER_ABORT |O usuário anulou a operação.|
| **9000**| OLD_PLATFORM | O código da plataforma está desatualizado e não implementa essa API.|
| **10000**| SIZE_EXCEEDED |  O valor de retorno é muito grande e excedeu os limites de tamanho de plataforma.|

## <a name="sample-code-snippets"></a>Trechos de código de exemplo

**API de chamada `selectMedia`**

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

**API de chamada `getMedia`**

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

**Chamar `viewImages`  a API por ID**

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

**Chamar a API viewImages por URL**

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
