---
title: Integrar recursos de mídia
description: Como usar o SDK do cliente JavaScript do Teams para habilitar recursos de mídia
keywords: mídia de permissões nativas de dispositivo de recursos de microfone de imagem da câmera
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 4876b4de9340cc2bd27a14e363954573ea42f05d
ms.sourcegitcommit: 6ff8d1244ac386641ebf9401804b8df3854b02dc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/18/2021
ms.locfileid: "50294737"
---
# <a name="integrate-media-capabilities"></a>Integrar recursos de mídia 

Este documento orienta você sobre como integrar recursos de mídia. Essa integração combina os recursos de dispositivo nativo, como a **câmera** e **o microfone com** a plataforma do Teams.  

Você pode usar o [SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)do cliente JavaScript do Microsoft Teams, que fornece as ferramentas necessárias para que seu aplicativo acesse as permissões de dispositivo [de um usuário.](native-device-permissions.md) Use **APIs** de funcionalidade de mídia adequadas para  integrar  os recursos de dispositivo nativo, como a câmera e o microfone com a plataforma teams no seu aplicativo móvel do Microsoft Teams, e crie uma experiência mais rica. 

## <a name="advantage-of-integrating-media-capabilities"></a>Vantagem da integração de recursos de mídia

A principal vantagem da integração de recursos de dispositivo em seus aplicativos do Teams é que ele aproveita controles nativos do Teams para oferecer uma experiência rica e imersiva aos usuários.
Para integrar recursos de mídia, você deve atualizar o arquivo de manifesto do aplicativo e chamar as APIs de recurso de mídia. 

Para uma integração eficaz, você deve ter uma boa compreensão dos trechos de código para chamar as [respectivas](#code-snippets) APIs, que permitem que você use recursos de mídia nativa.

É importante se familiarizar com os erros de resposta [da API](#error-handling) para lidar com os erros em seu aplicativo do Teams.

> [!NOTE] 
> Atualmente, o suporte do Microsoft Teams para recursos de mídia só está disponível para clientes móveis.

## <a name="update-manifest"></a>Manifesto de atualização

Atualize seu aplicativo do Teams [manifest.jsno](../../resources/schema/manifest-schema.md#devicepermissions) arquivo adicionando a propriedade `devicePermissions` e especificando `media` . Ele permite que seu aplicativo peça permissões de requisito dos  usuários antes de começar a usar a câmera para capturar a  imagem, abra a galeria para selecionar uma imagem para enviar como um anexo ou use o microfone para gravar a conversa.

``` json
"devicePermissions": [
    "media",
],
```

> [!NOTE]
> O **prompt de Permissões de** Solicitação é exibido automaticamente quando uma API relevante do Teams é iniciada. Para obter mais informações, consulte [Solicitar permissões de dispositivo](native-device-permissions.md).

## <a name="media-capability-apis"></a>APIs de funcionalidade de mídia

As [APIs selectMedia](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true), [getMedia](/javascript/api/@microsoft/teams-js/_media?view=msteams-client-js-latest#getMedia__error__SdkError__blob__Blob_____void_&preserve-view=true)e [viewImages](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#viewImages_ImageUri_____error___SdkError_____void_&preserve-view=true) permitem que você use recursos de mídia nativa da seguinte forma:

* Use o microfone **nativo** para permitir que os usuários **gravem áudio** (gravar 10 minutos de conversa) do dispositivo.
* Use o controle **de câmera nativo** para permitir que os usuários **capturem e anexem imagens** em movimento.
* Use o suporte **de galeria nativa** para permitir que os usuários **selecionem imagens de dispositivo** como anexos.
* Use o **controle do visualizador de imagem nativo** para visualizar várias **imagens** ao mesmo tempo.
* Suporte **a transferência de imagem grande** (de 1 MB a 50 MB) através da ponte SDK.
* Suporte **aos recursos avançados de imagem** que permitem que os usuários visualizem e editem imagens:
  * Examinar documento, quadro de trabalho e cartões de visita pela câmera.
  
> [!IMPORTANT]
>*   As APIs , e podem ser invocadas de várias `selectMedia` `getMedia` `viewImages` superfícies do Teams, como módulos de tarefas, guias e aplicativos pessoais. Para obter mais detalhes, consulte [Pontos de entrada para aplicativos do Teams](../extensibility-points.md).
>* `selectMedia` A API foi estendida para dar suporte a propriedades de microfone e áudio.

Você deve usar o seguinte conjunto de APIs para habilitar os recursos de mídia do dispositivo:

| API      | Descrição   |
| --- | --- |
| [**selectMedia**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true) (**Câmera)**| Essa API permite que os usuários **capturem ou selecionem mídia da** câmera do dispositivo e a retornem ao aplicativo Web. Os usuários podem editar, cortar, girar, anotar ou desenhar imagens antes do envio. Em resposta a **selectMedia**, o web-app recebe as IDs de mídia de imagens selecionadas e uma miniatura da mídia selecionada. Essa API pode ser configurada ainda mais por meio da [configuração ImageProps.](/javascript/api/@microsoft/teams-js/imageprops?view=msteams-client-js-latest&preserve-view=true) |
| [**selectMedia**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true) (**Microfone**)| De definir [o mediaType](/javascript/api/@microsoft/teams-js/mediatype?view=msteams-client-js-latest&preserve-view=true) como `4` na API **selectMedia** para acessar o recurso de microfone. Essa API também permite que os usuários gravem áudio do microfone do dispositivo e retornem clipes gravados para o aplicativo Web. Os usuários podem pausar, gravar e reproduzir a visualização de gravação antes do envio. Em resposta a **selectMedia**, o aplicativo Web recebe IDs de mídia da gravação de áudio selecionada. <br/> Use `maxDuration` , se você precisar configurar uma duração em minutos para gravar a conversa. A duração atual da gravação é de 10 minutos, após o qual a gravação é encerrada.  |
| [**getMedia**](/javascript/api/@microsoft/teams-js/_media?view=msteams-client-js-latest#getMedia__error__SdkError__blob__Blob_____void_&preserve-view=true)| Essa API recupera a mídia capturada pela API **selectMedia** em partes, independentemente do tamanho da mídia. Essas partes são montadas e enviadas de volta para o aplicativo Web como um arquivo ou blob. A quebra de mídia em partes menores facilita a transferência de arquivos grandes. |
| [**viewImages**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#viewImages_ImageUri_____error___SdkError_____void_&preserve-view=true)| Essa API permite que o usuário veja imagens no modo de tela inteira como uma lista rolável.|


**Experiência do aplicativo Web para a API SelectMedia para funcionalidade de imagem** 
 ![ experiência de câmera de dispositivo e imagem no Teams](../../assets/images/tabs/image-capability.png)

**Experiência do aplicativo Web para a API selectMedia para funcionalidade de microfone** 
 ![ experiência do aplicativo web para funcionalidade de microfone](../../assets/images/tabs/microphone-capability.png)

## <a name="error-handling"></a>Tratamento de erros

Certifique-se de lidar com esses erros adequadamente em seu aplicativo do Teams. A tabela a seguir lista os códigos de erro e as condições nas quais os erros são gerados: 


|Código de erro |  Nome do erro     | Condition|
| --------- | --------------- | -------- |
| **100** | NOT_SUPPORTED_ON_PLATFORM | A API não tem suporte na plataforma atual.|
| **404** | FILE_NOT_FOUND | O arquivo especificado não é encontrado no local determinado.|
| **500** | INTERNAL_ERROR | Erro interno é encontrado durante a execução da operação necessária.|
| **1000** | PERMISSION_DENIED |A permissão é negada pelo usuário.|
| **2000** |NETWORK_ERROR | Problema de rede.|
| **3000** | NO_HW_SUPPORT | O hardware subjacente não dá suporte à funcionalidade.|
| **4000**| INVALID_ARGUMENTS | Um ou mais argumentos são inválidos.|
| **5000** | UNAUTHORIZED_USER_OPERATION | O usuário não está autorizado a concluir essa operação.|
| **6000** |INSUFFICIENT_RESOURCES | A operação não pôde ser concluída devido a recursos insuficientes.|
|**7000** | THROTTLE | A plataforma acelerou a solicitação à medida que a API era invocada com frequência.|
|  **8000** | USER_ABORT |O usuário aborta a operação.|
| **9000**| OLD_PLATFORM | O código da plataforma está desatualizado e não implementa essa API.|
| **10000**| SIZE_EXCEEDED |  O valor de retorno é muito grande e excedeu os limites de tamanho da plataforma.|

## <a name="code-snippets"></a>Trechos de código

**Chamada `selectMedia` API** para capturar imagens usando câmera:

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

**Chamada `getMedia` API** para recuperar grandes mídias em partes:

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

**Chamada `viewImages` API por ID retornada pela `selectMedia` API**:

```javascript
// View images by id:
// Assumption: attachmentArray = select Media API Output
let uriList = [];
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

**Chamada `viewImages` API por URL**:

```javascript
// View Images by URL:
// Assumption 2 urls, url1 and url2
let uriList = [];
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
```

**Chamada `selectMedia` e `getMedia` APIs para gravação de áudio por microfone:**

```javascript
let mediaInput: microsoftTeams.media.MediaInputs = {
    mediaType: microsoftTeams.media.MediaType.Audio,
    maxMediaCount: 1,
};
microsoftTeams.media.selectMedia(mediaInput, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
    if (error) {
        if (error.message) {
            alert(" ErrorCode: " + error.errorCode + error.message);
        } else {
            alert(" ErrorCode: " + error.errorCode);
        }
    }
    // If you want to directly use the audio file (for smaller file sizes (~4MB))    if (attachments) {
    let audioResult = attachments[0];
    var videoElement = document.createElement("video");
    videoElement.setAttribute("src", ("data:" + y.mimeType + ";base64," + y.preview));
    //To use the audio file via get Media API for bigger audio file sizes greater than 4MB        audioResult.getMedia((error: microsoftTeams.SdkError, blob: Blob) => {
    if (blob) {
        if (blob.type.includes("video")) {
            videoElement.setAttribute("src", URL.createObjectURL(blob));
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

## <a name="see-also"></a>Confira também

> [!div class="nextstepaction"]
> [Integrar a QR ou o recurso de scanner de código de barras no Teams](qr-barcode-scanner-capability.md)