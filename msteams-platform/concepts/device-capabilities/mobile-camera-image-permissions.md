---
title: Integrar recursos de mídia
author: Rajeshwari-v
description: Saiba como usar o SDK do cliente JavaScript do Teams para habilitar recursos de mídia usando exemplos de código
keywords: api de mídia de permissões nativas do dispositivo de recursos do microfone da imagem da câmera
ms.topic: conceptual
ms.localizationpriority: high
ms.author: lajanuar
ms.openlocfilehash: c9b31bf6fe97446bfbccdd1861612ec938733f88
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111259"
---
# <a name="integrate-media-capabilities"></a>Integrar recursos de mídia

Você pode integrar funcionalidades nativas do dispositivo, como o **câmera** e **microfone** com seu aplicativo Teams. Para integração, você pode usar o [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true), que fornece as ferramentas necessárias para que seu aplicativo acesse as permissões de [dispositivo](native-device-permissions.md) do usuário. Use APIs de funcionalidade de mídia adequadas para integrar os recursos do dispositivo, como **câmera** e **microfone** com a plataforma Teams em seu aplicativo móvel do Microsoft Teams e crie uma experiência mais avançada.

## <a name="advantage-of-integrating-media-capabilities"></a>Vantagem da integração de recursos de mídia

A principal vantagem da integração de recursos de dispositivo em seus aplicativos do Teams é que ele aproveita os controles nativos do Teams para fornecer uma experiência avançada e imersiva aos seus usuários.
Para integrar recursos de mídia, você deve atualizar o arquivo de manifesto do aplicativo e chamar as APIs de funcionalidade de mídia.

Para uma integração eficaz, você deve ter uma boa compreensão de [Trechos de código](#code-snippets) para chamar as respectivas APIs, que permitem que você use recursos de mídia nativa.

É importante se familiarizar com os [Erros de resposta da API](#error-handling) para lidar com os erros em seu aplicativo Teams.

> [!NOTE]
>
> * Atualmente, o suporte do Microsoft Teams para recursos de mídia está disponível apenas para clientes móveis.
> * Atualmente, o Teams não dá suporte a permissões de dispositivo para aplicativos de várias janelas, guias e o painel lateral da reunião.
> * As permissões do dispositivo são diferentes no navegador. Para obter mais informações, consulte [Permissões de navegador da Web do dispositivo](browser-device-permissions.md).

## <a name="update-manifest"></a>Atualizar manifesto

Atualize o arquivo [manifest.json](../../resources/schema/manifest-schema.md#devicepermissions) de seu aplicativo Teams adicionando a propriedade `devicePermissions` e especificando `media`. Ele permite que seu aplicativo solicite as permissões necessárias dos usuários antes que eles comecem a usar a **câmera** para capturar a imagem, abra a galeria para selecionar uma imagem para enviar como anexo ou use o **microfone** para gravar a conversa. A atualização para o manifesto do aplicativo é a seguinte:

``` json
"devicePermissions": [
    "media",
],
```

> [!NOTE]
> O prompt de **solicitar permissões** é exibido automaticamente quando uma API do Teams relevante é iniciada. Para obter mais informações, consulte [Solicitar permissões de dispositivo](native-device-permissions.md).

## <a name="media-capability-apis"></a>APIs de funcionalidade de mídia

As APIs [selectMedia](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true), [getMedia](/javascript/api/@microsoft/teams-js/microsoftteams.media.mediachunk?view=msteams-client-js-latest&preserve-view=true) e [viewImages](/javascript/api/@microsoft/teams-js/microsoftteams.media.imageuri?view=msteams-client-js-latest&preserve-view=true) permitem que você use recursos de mídia nativa da seguinte forma:

* Use o **microfone** para permitir que os usuários **gravem áudio** (grave 10 minutos de conversa) do dispositivo.
* Use o **controle da câmera** nativo para permitir que os usuários **capturem e anexem imagens** em movimento.
* Use o **suporte da galeria** nativo para permitir que os usuários **selecionem imagens do dispositivo** como anexos.
* Use o **controle do visualizador de imagens** nativo para **visualizar várias imagens** ao mesmo tempo.
* Suporta **transferência de imagens grandes** (de 1 MB a 50 MB) por meio da ponte SDK.
* O suporte a **recursos avançados de imagem** permite que os usuários visualizem e editem imagens:
  * Digitalize documentos, quadros de comunicações e cartões de visita pela câmera.
  
> [!IMPORTANT]
>
> * As APIs `selectMedia`, `getMedia` e `viewImages` podem ser invocadas de várias superfícies do Teams, como módulos de tarefas, guias e aplicativos pessoais. Para obter mais detalhes, consulte [Pontos de entrada para aplicativos do Teams](../extensibility-points.md).
> * `selectMedia` API foi estendida para dar suporte às propriedades de microfone e áudio.

Você deve usar o seguinte conjunto de APIs para habilitar os recursos de mídia do seu dispositivo:

| API      | Descrição   |
| --- | --- |
| [**selectMedia**](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true) (**Camera)**| Essa API permite que os usuários **capturem ou selecionem a mídia da câmera do dispositivo** e retorne-a ao aplicativo Web. Os usuários podem editar, cortar, girar, anotar ou desenhar imagens antes do envio. Em resposta a `selectMedia`, o aplicativo Web recebe as IDs de mídia das imagens selecionadas e uma miniatura da mídia selecionada. Essa API pode ser configurada ainda mais por meio da configuração [ImageProps](/javascript/api/@microsoft/teams-js/microsoftteams.media.imageprops?view=msteams-client-js-latest&preserve-view=true). |
| [**selectMedia**](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true) (**Microphone**)| Defina [mediaType](/javascript/api/@microsoft/teams-js/microsoftteams.media.mediatype?view=msteams-client-js-latest&preserve-view=true) como `4` na API `selectMedia` para acessar a funcionalidade do microfone. Essa API também permite que os usuários gravem áudio do microfone do dispositivo e retornem clipes gravados para o aplicativo Web. Os usuários podem pausar, gravar novamente e reproduzir a visualização da gravação antes do envio. Em resposta a **selectMedia**, o aplicativo Web recebe IDs de mídia da gravação de áudio selecionada. <br/> Use `maxDuration` se precisar configurar uma duração em minutos para gravar a conversa. A duração atual da gravação é de 10 minutos, após o qual a gravação é encerrada.  |
| [**getMedia**](/javascript/api/@microsoft/teams-js/microsoftteams.media.mediachunk?view=msteams-client-js-latest&preserve-view=true)| Essa API recupera a mídia capturada pela API `selectMedia` em partes, independentemente do tamanho da mídia. Essas partes são montados e enviados de volta para o aplicativo Web como um arquivo ou blob. Dividir mídia em partes menores facilita a transferência de arquivos grandes. |
| [**viewImages**](/javascript/api/@microsoft/teams-js/microsoftteams.media.imageuri?view=msteams-client-js-latest&preserve-view=true)| Essa API permite que o usuário exiba imagens no modo de tela inteira como uma lista rolável.|

A imagem a seguir ilustra a experiência do aplicativo Web `selectMedia` API para funcionalidade de imagem:

![experiência de imagem e câmera do dispositivo no Teams](../../assets/images/tabs/image-capability.png)

A imagem a seguir ilustra a experiência do aplicativo Web `selectMedia` API para funcionalidade de microfone:

![experiência do aplicativo Web para funcionalidade de microfone](../../assets/images/tabs/microphone-capability.png)

## <a name="error-handling"></a>Tratamento de erros

Você deve certificar-se de lidar com esses erros adequadamente em seu aplicativo teams. A tabela a seguir lista os códigos de erro e as condições sob as quais os erros são gerados:

|Código de erro |  Nome do erro     | Condição|
| --------- | --------------- | -------- |
| **100** | NÃO_SUPORTADO_NA_PLATAFORMA | A API não é suportada na plataforma atual.|
| **404** | FILE_NOT_FOUND | O arquivo especificado não foi encontrado no local especificado.|
| **500** | INTERNAL_ERROR | Erro interno ao executar a operação necessária.|
| **1000** | PERMISSION_DENIED |A permissão foi negada pelo usuário.|
| **3000** | NO_HW_SUPPORT | O hardware subjacente não dá suporte à funcionalidade.|
| **4000**| ARGUMENTOS_INVÁLIDOS | Um ou mais argumentos são inválidos.|
|  **8000** | ABORTAR_USUÁRIO |O usuário anula a operação.|
| **9000**| ANTIGA_PLATAFORMA | O código da plataforma está desatualizado e não implementa essa API.|
| **10000**| SIZE_EXCEEDED |  O valor retornado é muito grande e excedeu os limites de tamanho da plataforma.|

## <a name="code-snippets"></a>Trechos de código

**Chamando `selectMedia` API** para capturar imagens usando a câmera:

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

**Chamando `getMedia` API** para recuperar mídia grande em partes:

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

**Chamando `viewImages` API por ID retornada por `selectMedia` API**:

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

**Chamando `viewImages` API por URL**:

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

**Chamando `selectMedia` e `getMedia` APIs para gravação de áudio por meio do microfone**:

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

* [Integrar o recurso de leitor de código QR ou de barras no Teams](qr-barcode-scanner-capability.md)
* [Integrar funcionalidades de localização no Teams](location-capability.md)
* [Integrar Seletor de Pessoas no Teams](people-picker-capability.md)
* [Requisitos e considerações para bots de mídia hospedados em aplicativos](~/bots/calls-and-meetings/requirements-considerations-application-hosted-media-bots.md)
