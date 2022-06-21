---
title: Integrar recursos de mídia
author: Rajeshwari-v
description: Saiba como usar o Teams SDK do cliente JavaScript para habilitar recursos de mídia usando exemplos de código e também aprender a vantagem de integrar recursos de mídia.
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: lajanuar
ms.openlocfilehash: 366c58ac283e687f8a297b8701b932f99550574e
ms.sourcegitcommit: 7bbb7caf729a00b267ceb8af7defffc91903d945
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/21/2022
ms.locfileid: "66190233"
---
# <a name="integrate-media-capabilities"></a>Integrar recursos de mídia

Você pode integrar recursos nativos de dispositivo, como câmera e microfone ao Teams aplicativo. Para integração, você pode usar [Microsoft Teams SDK do cliente JavaScript](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) que fornece as ferramentas necessárias para seu aplicativo acessar as permissões de [dispositivo de um usuário](native-device-permissions.md). Use APIs de funcionalidade de mídia adequadas para integrar os recursos do dispositivo, como câmera e microfone à plataforma Teams em seu aplicativo Microsoft Teams, e crie uma experiência mais rica. A funcionalidade de mídia está disponível para Teams web, área de trabalho e dispositivos móveis. Para integrar recursos de mídia, você deve atualizar o arquivo de manifesto do aplicativo e chamar as APIs de funcionalidade de mídia.

Para uma integração eficaz, você deve ter uma boa compreensão de [Trechos de código](#code-snippets) para chamar as respectivas APIs, que permitem que você use recursos de mídia nativa. É importante se familiarizar com os [Erros de resposta da API](#error-handling) para lidar com os erros em seu aplicativo Teams.

## <a name="advantages"></a>Vantagens

A principal vantagem da integração de recursos de dispositivo em seus aplicativos do Teams é que ele aproveita os controles nativos do Teams para fornecer uma experiência avançada e imersiva aos seus usuários. Os cenários a seguir mostram as vantagens dos recursos de mídia:

* Permitir que o usuário capture as simulações aproximadas desenhadas em um quadro de comunicações físico por meio do telefone celular e use as imagens capturadas como opções de votação Teams chat em grupo.

* Permitir que o usuário grave uma mensagem de áudio e anexe-a a um tíquete de incidente.

* Permitir que o usuário digitalize os documentos físicos do smartphone para fazer uma solicitação de seguro de carro.

> [!NOTE]
>
> * Atualmente, o Teams não dá suporte a permissões de dispositivo na janela pop-out do chat, nas guias e no painel lateral da reunião.</br>
> * As permissões do dispositivo são diferentes no navegador. Para saber mais, consulte [permissões de dispositivo do navegador](browser-device-permissions.md).
> * O prompt de permissões de solicitação é exibido automaticamente no celular quando uma API Teams relevante é iniciada. Para mais informações, consulte [solicitar permissões de dispositivos](native-device-permissions.md).

## <a name="update-manifest"></a>Atualizar manifesto

Atualize seu aplicativo do Teams do arquivo [ manifest.json do](../../resources/schema/manifest-schema.md#devicepermissions) adicionando a `devicePermissions` propriedade e especificando `media`. Ele permite que seu aplicativo solicite as permissões necessárias dos usuários antes que eles comecem a usar a câmera para capturar a imagem, abra a galeria para selecionar uma imagem para enviar como anexo ou use o microfone para gravar a conversa. A atualização para o manifesto do aplicativo é a seguinte:

``` json
"devicePermissions": [
    "media",
],
```

## <a name="media-capability-apis"></a>APIs de funcionalidade de mídia

As APIs [selectMedia](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true), [getMedia](/javascript/api/@microsoft/teams-js/microsoftteams.media.mediachunk?view=msteams-client-js-latest&preserve-view=true) e [viewImages](/javascript/api/@microsoft/teams-js/microsoftteams.media.imageuri?view=msteams-client-js-latest&preserve-view=true) permitem que você use recursos de mídia nativa da seguinte forma:

* Use o **microfone** para permitir que os usuários **gravem áudio** (grave 10 minutos de conversa) do dispositivo.
* Use o **controle da câmera** nativo para permitir que os usuários **capturem e anexem imagens** em movimento.
* Use o **suporte da galeria** nativo para permitir que os usuários **selecionem imagens do dispositivo** como anexos.
* Use o **controle do visualizador de imagens** nativo para **visualizar várias imagens** ao mesmo tempo.
* Suporta **transferência de imagens grandes** (de 1 MB a 50 MB) por meio da ponte SDK.
* Suporte **a recursos avançados de imagem** , permitindo que os usuários visualizem e editem imagens.
* Digitalize documentos, quadro de comunicações e cartões de visita pela câmera.
  
> [!IMPORTANT]
>
> * As APIs `selectMedia`, `getMedia` e `viewImages` podem ser invocadas de várias superfícies do Teams, como módulos de tarefas, guias e aplicativos pessoais. Para obter mais detalhes, consulte [Pontos de entrada para aplicativos do Teams](../extensibility-points.md).</br>
> * `selectMedia` A API dá suporte a funcionalidades de câmera e microfone por meio de configurações de entrada diferentes.
> * A `selectMedia` API para acessar a funcionalidade de microfone dá suporte apenas a clientes móveis.

A tabela a seguir lista o conjunto de APIs para habilitar os recursos de mídia do dispositivo:

| API      | Descrição   |
| --- | --- |
| [**selectMedia**](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true) (**Camera)**| Essa API permite que os usuários **capturem ou selecionem a mídia da câmera do dispositivo** e retorne-a ao aplicativo Web. Os usuários podem editar, cortar, girar, anotar ou desenhar imagens antes do envio. Em resposta a `selectMedia`, o aplicativo Web recebe as IDs de mídia das imagens selecionadas e uma miniatura da mídia selecionada. Essa API pode ser configurada ainda mais por meio da configuração [ImageProps](/javascript/api/@microsoft/teams-js/microsoftteams.media.imageprops?view=msteams-client-js-latest&preserve-view=true). |
| [**selectMedia**](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true) (**Microphone**)| Defina [o mediaType](/javascript/api/@microsoft/teams-js/microsoftteams.media.mediatype?view=msteams-client-js-latest&preserve-view=true) como `4` na `selectMedia` API para acessar a funcionalidade do microfone. Essa API também permite que os usuários gravem áudio do microfone do dispositivo e retornem clipes gravados para o aplicativo Web. Os usuários podem pausar, gravar novamente e reproduzir a visualização da gravação antes do envio. Em resposta a **selectMedia**, o aplicativo Web recebe IDs de mídia da gravação de áudio selecionada. <br/> Use `maxDuration` se precisar configurar uma duração em minutos para gravar a conversa. A duração atual da gravação é de 10 minutos, após o qual a gravação é encerrada.  |
| [**getMedia**](/javascript/api/@microsoft/teams-js/microsoftteams.media.mediachunk?view=msteams-client-js-latest&preserve-view=true)| Essa API recupera a mídia capturada pela API `selectMedia` em partes, independentemente do tamanho da mídia. Essas partes são montados e enviados de volta para o aplicativo Web como um arquivo ou blob. Dividir mídia em partes menores facilita a transferência de arquivos grandes. |
| [**viewImages**](/javascript/api/@microsoft/teams-js/microsoftteams.media.imageuri?view=msteams-client-js-latest&preserve-view=true)| Essa API permite que o usuário exiba imagens no modo de tela inteira como uma lista rolável.|

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

A imagem a seguir ilustra a experiência do aplicativo Web da `selectMedia` API para a funcionalidade de imagem:

:::image type="content" source="~/assets/images/tabs/media-capability-mobile2.png" alt-text="A ilustração mostra a funcionalidade de imagem para dispositivos móveis." border="true":::

> [!NOTE]
>
> Em dispositivos com Android versão inferior a 7, `selectMedia` a API inicia a experiência nativa Android câmera em vez da experiência Teams câmera nativa.

A imagem a seguir ilustra a experiência do aplicativo Web da `selectMedia` API para o recurso de microfone:

:::image type="content" source="~/assets/images/tabs/microphone-capability.png" alt-text="A ilustração mostra a funcionalidade de microfone para dispositivos móveis." border="true":::

# <a name="desktop"></a>[Desktop](#tab/desktop)

A imagem a seguir ilustra a experiência do aplicativo Web da `selectMedia` API para a funcionalidade de imagem:

:::image type="content" source="~/assets/images/tabs/media-capability-desktop1.png" alt-text="A ilustração mostra a funcionalidade de mídia para área de trabalho." border="true":::

---

## <a name="error-handling"></a>Tratamento de erros

Certifique-se de lidar com esses erros adequadamente em seu Teams aplicativo. A tabela a seguir lista os códigos de erro e as descrições sob as quais os erros são gerados:

|Código de erro |  Nome do erro     | Descrição|
| --------- | --------------- | -------- |
| **100** | NÃO_SUPORTADO_NA_PLATAFORMA | A API não é suportada na plataforma atual.|
| **404** | FILE_NOT_FOUND | O arquivo especificado não foi encontrado no local especificado.|
| **500** | INTERNAL_ERROR | Erro interno encontrado durante a execução da operação necessária.|
| **1.000** | PERMISSION_DENIED |A permissão foi negada pelo usuário.|
| **3000** | NO_HW_SUPPORT | O hardware não dá suporte à funcionalidade.|
| **4000**| ARGUMENTOS_INVÁLIDOS | Um ou mais argumentos são inválidos.|
|  **8000** | ABORTAR_USUÁRIO |O usuário anula a operação.|
| **9000**| ANTIGA_PLATAFORMA | O código da plataforma está desatualizado e não implementa essa API.|
| **10000**| SIZE_EXCEEDED |  O valor retornado é muito grande e excedeu os limites de tamanho da plataforma.|

## <a name="code-snippets"></a>Trechos de código

* Chame `selectMedia` a API para capturar imagens usando a câmera:

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

* Chame `getMedia` a API para recuperar uma mídia grande em partes:

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

* Chame `viewImages` a API por ID, que é retornada pela `selectMedia` API:

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

* Chamar `viewImages` API por URL:

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

* Chamada `selectMedia` e `getMedia` APIs para gravação de áudio por meio do microfone:

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
* [Integrar o Seletor de Pessoas](people-picker-capability.md)
* [Requisitos e considerações para bots de mídia hospedados em aplicativos](~/bots/calls-and-meetings/requirements-considerations-application-hosted-media-bots.md)
