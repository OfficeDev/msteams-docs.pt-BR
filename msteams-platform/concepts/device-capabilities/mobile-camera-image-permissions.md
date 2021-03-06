---
title: Integrar recursos de mídia
author: Rajeshwari-v
description: Como usar Teams SDK do cliente JavaScript para habilitar recursos de mídia
keywords: mídia de permissões nativas de dispositivo de recursos de microfone de imagem da câmera
ms.topic: conceptual
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: 22d4a791e83cf36f18b75a3846865835b0ee024f
ms.sourcegitcommit: 059d22c436ee9b07a61561ff71e03e1c23ff40b8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/30/2021
ms.locfileid: "53211622"
---
# <a name="integrate-media-capabilities"></a>Integrar recursos de mídia 

Você pode integrar recursos de dispositivo nativo, como a **câmera** e o **microfone** com seu Teams app. Para integração, você pode usar [Microsoft Teams SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)do cliente JavaScript , que fornece as ferramentas necessárias para seu aplicativo acessar as permissões de dispositivo [de um usuário.](native-device-permissions.md) Use APIs de funcionalidade de mídia adequadas  para  integrar os recursos do dispositivo, como câmera e microfone com a plataforma Teams no seu aplicativo móvel Microsoft Teams, e crie uma experiência mais rica. 

## <a name="advantage-of-integrating-media-capabilities"></a>Vantagem da integração de recursos de mídia

A principal vantagem da integração de recursos de dispositivo em seus aplicativos Teams é que ele utiliza controles Teams nativos para fornecer uma experiência rica e imersiva aos seus usuários.
Para integrar recursos de mídia, você deve atualizar o arquivo de manifesto do aplicativo e chamar as APIs de recurso de mídia. 

Para uma integração eficaz, você deve ter uma boa compreensão dos trechos de código para chamar as [respectivas](#code-snippets) APIs, que permitem que você use recursos de mídia nativa.

É importante se familiarizar com os erros de resposta da [API](#error-handling) para lidar com os erros em seu Teams app.

> [!NOTE] 
> * Atualmente, o Microsoft Teams suporte para recursos de mídia está disponível apenas para clientes móveis.   
> * Atualmente, o Teams não dá suporte a permissões de dispositivo para aplicativos de várias janelas, guias e o sidepanel de reunião.    

## <a name="update-manifest"></a>Manifesto de atualização

Atualize seu Teams aplicativo [manifest.jsno](../../resources/schema/manifest-schema.md#devicepermissions) arquivo adicionando a propriedade `devicePermissions` e especificando `media` . Ele permite que seu aplicativo peça permissões de requisito dos  usuários antes de começar a usar a câmera para capturar a  imagem, abra a galeria para selecionar uma imagem para enviar como um anexo ou use o microfone para gravar a conversa. A atualização do manifesto do aplicativo é a seguinte:

``` json
"devicePermissions": [
    "media",
],
```

> [!NOTE]
> O **prompt De Permissões de** Solicitação é exibido automaticamente quando uma API Teams relevante é iniciada. Para obter mais informações, consulte [Solicitar permissões de dispositivo](native-device-permissions.md).

## <a name="media-capability-apis"></a>APIs de funcionalidade de mídia

As [APIs selectMedia](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true), [getMedia](/javascript/api/@microsoft/teams-js/microsoftteams.media.mediachunk?view=msteams-client-js-latest&preserve-view=true)e [viewImages](/javascript/api/@microsoft/teams-js/microsoftteams.media.imageuri?view=msteams-client-js-latest&preserve-view=true) permitem que você use recursos de mídia nativa da seguinte forma:

* Use o microfone **nativo** para permitir que os usuários **gravem áudio** (gravar 10 minutos de conversa) do dispositivo.
* Use o controle **de câmera nativo** para permitir que os usuários **capturem e anexem imagens** em movimento.
* Use o suporte **de galeria nativa** para permitir que os usuários **selecionem imagens de dispositivo** como anexos.
* Use o **controle do visualizador de imagem nativo** para visualizar várias **imagens** ao mesmo tempo.
* Suporte **a transferência de imagem grande** (de 1 MB a 50 MB) através da ponte SDK.
* Suporte **aos recursos avançados de imagem** que permitem que os usuários visualizem e editem imagens:
  * Examinar documento, quadro de trabalho e cartões de visita pela câmera.
  
> [!IMPORTANT]
> * As APIs , e podem ser invocadas de várias superfícies Teams, como módulos de `selectMedia` `getMedia` `viewImages` tarefas, guias e aplicativos pessoais. Para obter mais detalhes, consulte [Pontos de entrada para Teams aplicativos](../extensibility-points.md).
> * `selectMedia` A API foi estendida para dar suporte a propriedades de microfone e áudio.

Você deve usar o seguinte conjunto de APIs para habilitar os recursos de mídia do dispositivo:

| API      | Descrição   |
| --- | --- |
| [**selectMedia**](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true) (**Câmera)**| Essa API permite que os usuários **capturem ou selecionem mídia da** câmera do dispositivo e a retornem ao aplicativo Web. Os usuários podem editar, cortar, girar, anotar ou desenhar imagens antes do envio. Em resposta a , o aplicativo Web recebe as IDs de mídia de imagens selecionadas e `selectMedia` uma miniatura da mídia selecionada. Essa API pode ser configurada ainda mais por meio da [configuração ImageProps.](/javascript/api/@microsoft/teams-js/microsoftteams.media.imageprops?view=msteams-client-js-latest&preserve-view=true) |
| [**selectMedia**](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true) (**Microfone**)| De definir [o mediaType](/javascript/api/@microsoft/teams-js/microsoftteams.media.mediatype?view=msteams-client-js-latest&preserve-view=true) como `4` na API para acessar o recurso de `selectMedia` microfone. Essa API também permite que os usuários gravem áudio do microfone do dispositivo e retornem clipes gravados para o aplicativo Web. Os usuários podem pausar, gravar e reproduzir a visualização de gravação antes do envio. Em resposta a **selectMedia**, o aplicativo Web recebe IDs de mídia da gravação de áudio selecionada. <br/> Use `maxDuration` , se você precisar configurar uma duração em minutos para gravar a conversa. A duração atual da gravação é de 10 minutos, após o qual a gravação é encerrada.  |
| [**getMedia**](/javascript/api/@microsoft/teams-js/microsoftteams.media.mediachunk?view=msteams-client-js-latest&preserve-view=true)| Essa API recupera a mídia capturada pela API em `selectMedia` partes, independentemente do tamanho da mídia. Essas partes são montadas e enviadas de volta para o aplicativo Web como um arquivo ou blob. A quebra de mídia em partes menores facilita a transferência de arquivos grandes. |
| [**viewImages**](/javascript/api/@microsoft/teams-js/microsoftteams.media.imageuri?view=msteams-client-js-latest&preserve-view=true)| Essa API permite que o usuário veja imagens no modo de tela inteira como uma lista rolável.|

A imagem a seguir mostra a experiência do aplicativo Web da `selectMedia` API para funcionalidade de imagem:

![câmera de dispositivo e experiência de imagem Teams](../../assets/images/tabs/image-capability.png)

A imagem a seguir mostra a experiência do aplicativo Web da `selectMedia` API para funcionalidade de microfone:

![experiência do aplicativo web para funcionalidade de microfone](../../assets/images/tabs/microphone-capability.png)

## <a name="error-handling"></a>Tratamento de erros

Certifique-se de lidar com esses erros adequadamente em seu Teams app. A tabela a seguir lista os códigos de erro e as condições nas quais os erros são gerados: 

|Código de erro |  Nome do erro     | Condition|
| --------- | --------------- | -------- |
| **100** | NOT_SUPPORTED_ON_PLATFORM | A API não tem suporte na plataforma atual.|
| **404** | FILE_NOT_FOUND | O arquivo especificado não é encontrado no local determinado.|
| **500** | INTERNAL_ERROR | Erro interno é encontrado durante a execução da operação necessária.|
| **1000** | PERMISSION_DENIED |A permissão é negada pelo usuário.|
| **3000** | NO_HW_SUPPORT | O hardware subjacente não dá suporte à funcionalidade.|
| **4000**| INVALID_ARGUMENTS | Um ou mais argumentos são inválidos.|
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

* [Integrar a QR ou o recurso de scanner de código de barras Teams](qr-barcode-scanner-capability.md)
* [Integrar recursos de localização Teams](location-capability.md)
* [Integrar a funcionalidade do Se picker de pessoas no Teams](people-picker-capability.md)

