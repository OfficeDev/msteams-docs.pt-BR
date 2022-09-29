---
title: Integrar recursos de mídia
author: Rajeshwari-v
description: Saiba como usar o SDK do cliente JavaScript do Teams para habilitar recursos de mídia usando exemplos de código e também aprender a vantagem de integrar recursos de mídia.
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: lajanuar
ms.openlocfilehash: d7bfedc0a439f428287cb1443df2a66fcff670ab
ms.sourcegitcommit: c74e1e12175969c75e112a580949f96d2610c24e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68160633"
---
# <a name="integrate-media-capabilities"></a>Integrar recursos de mídia

Você pode integrar funcionalidades nativas do dispositivo, como câmera e microfone ao aplicativo Teams. Para integração, você pode usar o [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) que fornece as ferramentas necessárias para seu aplicativo acessar as permissões de [dispositivo de um usuário](native-device-permissions.md). Use APIs de funcionalidade de mídia adequadas para integrar os recursos do dispositivo, como câmera e microfone com a plataforma Teams em seu aplicativo Microsoft Teams, e crie uma experiência mais rica. A funcionalidade de mídia está disponível para cliente Web do Teams, área de trabalho e dispositivos móveis. Para integrar recursos de mídia, você deve atualizar o arquivo de manifesto do aplicativo e chamar as APIs de funcionalidade de mídia.

Para uma integração eficaz, você deve ter uma boa compreensão dos [snippets](#code-snippets) de código para chamar as respectivas APIs, o que permite usar recursos de mídia nativa. É importante se familiarizar com os [erros de resposta da API](#error-handling) para lidar com os erros no seu aplicativo do Teams.

## <a name="advantages"></a>Vantagens

A vantagem de integrar recursos de dispositivo aos seus aplicativos do Teams é que ele usa controles nativos do Teams para fornecer uma experiência avançada e imersiva para seus usuários. Os cenários a seguir mostram as vantagens dos recursos de mídia:

* Permitir que o usuário capture as simulações aproximadas desenhadas em um quadro de comunicações físico por meio de seu telefone celular e use as imagens capturadas como opções de votação no chat em grupo do Teams.

* Permitir que o usuário grave uma mensagem de áudio e anexe-a a um tíquete de incidente.

* Permitir que o usuário digitalize os documentos físicos do smartphone para fazer uma solicitação de seguro de carro.

* Permitir que o usuário grave um vídeo em um site de trabalho e carregue-o para participação.

> [!NOTE]
>
> * Atualmente, o Teams não dá suporte a permissões de dispositivo na janela de chat pop-out, nas guias e no painel lateral da reunião.</br>
> * As permissões do dispositivo são diferentes no navegador. Para saber mais, consulte [permissões de dispositivo do navegador](browser-device-permissions.md).
> * O prompt de permissões de solicitação é exibido automaticamente no celular quando uma API relevante do Teams é iniciada. Para mais informações, consulte [solicitar permissões de dispositivos](native-device-permissions.md).

## <a name="update-manifest"></a>Atualizar manifesto

Atualize seu aplicativo do Teams do arquivo [ manifest.json do](../../resources/schema/manifest-schema.md#devicepermissions) adicionando a `devicePermissions` propriedade e especificando `media`. Ele permite que seu aplicativo solicite as permissões necessárias dos usuários antes que eles comecem a usar a câmera para capturar a imagem, abra a galeria para selecionar uma imagem para enviar como anexo ou use o microfone para gravar a conversa. A atualização para o manifesto do aplicativo é a seguinte:

``` json
"devicePermissions": [
    "media",
],
```

## <a name="media-capability-apis"></a>APIs de funcionalidade de mídia

As APIs [selectMedia](/javascript/api/@microsoft/teams-js/media#@microsoft-teams-js-media-selectmedia), [getMedia](/javascript/api/@microsoft/teams-js/media.media#@microsoft-teams-js-media-media-getmedia) e [viewImages](/javascript/api/@microsoft/teams-js/media#@microsoft-teams-js-media-viewimages) permitem que você use recursos de mídia nativa da seguinte forma:

* Use o **microfone** para permitir que os usuários **gravem áudio** (grave 10 minutos de conversa) do dispositivo.
* Use o **controle de** câmera nativo para permitir  que os usuários capturem e anexem imagens e capturem **vídeos (** gravem até 5 minutos de vídeo) em qualquer lugar.
* Use o **suporte da galeria** nativo para permitir que os usuários **selecionem imagens do dispositivo** como anexos.
* Use o **controle do visualizador de imagens** nativo para **visualizar várias imagens** ao mesmo tempo.
* Suporta **transferência de imagens grandes** (de 1 MB a 50 MB) por meio da ponte SDK.
* Suporte **a recursos avançados de imagem** , permitindo que os usuários visualizem e editem imagens.
* Digitalize documentos, quadro de comunicações e cartões de visita pela câmera.
  
> [!IMPORTANT]
>
> * As APIs `selectMedia`, `getMedia` e `viewImages` podem ser invocadas de várias superfícies do Teams, como módulos de tarefas, guias e aplicativos pessoais. Para obter mais informações, consulte [Pontos de entrada para aplicativos do Teams](../extensibility-points.md).</br>
> * `selectMedia` A API dá suporte a funcionalidades de câmera e microfone por meio de configurações de entrada diferentes.
> * A `selectMedia` API para acessar a funcionalidade de microfone dá suporte apenas a clientes móveis.

A tabela a seguir lista o conjunto de APIs para habilitar os recursos de mídia do dispositivo:

| API      | Descrição   |
| --- | --- |
| [**selectMedia**](/javascript/api/@microsoft/teams-js/media#@microsoft-teams-js-media-selectmedia) (**Camera)**| Essa API permite que os usuários **capturem ou selecionem a mídia da câmera do dispositivo** e retorne-a ao aplicativo Web. Os usuários podem editar, cortar, girar, anotar ou desenhar imagens antes do envio. Em resposta a `selectMedia`, o aplicativo Web recebe as IDs de mídia das imagens selecionadas e uma miniatura da mídia selecionada. Essa API pode ser configurada ainda mais por meio da configuração [ImageProps](/javascript/api/@microsoft/teams-js/media.imageprops). |
| [**selectMedia**](/javascript/api/@microsoft/teams-js/media#@microsoft-teams-js-media-selectmedia) (**Microphone**)| Defina [o mediaType](/javascript/api/@microsoft/teams-js/media.mediatype) como `4` (Áudio) na `selectMedia` API para acessar a funcionalidade do microfone. Essa API também permite que os usuários gravem áudio do microfone do dispositivo e retornem clipes gravados para o aplicativo Web. Os usuários podem pausar, gravar novamente e reproduzir a visualização da gravação antes do envio. Em resposta a **selectMedia**, o aplicativo Web recebe IDs de mídia das gravações de áudio selecionadas. <br/> Use `maxDuration`, se você precisar configurar uma duração em minutos para gravar a conversa. A duração atual da gravação é de 10 minutos, após o qual a gravação é encerrada.  |
| [**getMedia**](/javascript/api/@microsoft/teams-js/media.media#@microsoft-teams-js-media-media-getmedia)| Essa API recupera a mídia capturada pela API `selectMedia` em partes, independentemente do tamanho da mídia. Essas partes são montados e enviados de volta para o aplicativo Web como um arquivo ou blob. Dividir mídia em partes menores facilita a transferência de arquivos grandes. |
| [**viewImages**](/javascript/api/@microsoft/teams-js/media#@microsoft-teams-js-media-viewimages)| Essa API permite que o usuário exiba imagens no modo de tela inteira como uma lista rolável.|

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

A imagem a seguir ilustra a experiência do aplicativo Web da `selectMedia` API para a funcionalidade de imagem:

:::image type="content" source="~/assets/images/tabs/media-capability-mobile2.png" alt-text="A ilustração mostra a funcionalidade de imagem para dispositivos móveis.":::

> [!NOTE]
> Em dispositivos com a versão do Android abaixo de 7, `selectMedia` a API inicia a experiência de câmera nativa do Android em vez da experiência de câmera nativa do Teams.

A imagem a seguir ilustra a experiência do aplicativo Web da `selectMedia` API para o recurso de microfone:

:::image type="content" source="~/assets/images/tabs/microphone-capability.png" alt-text="A ilustração mostra a funcionalidade de microfone para dispositivos móveis.":::

# <a name="desktop"></a>[Desktop](#tab/desktop)

A imagem a seguir ilustra a experiência do aplicativo Web da `selectMedia` API para a funcionalidade de imagem:

:::image type="content" source="~/assets/images/tabs/media-capability-desktop1.png" alt-text="A ilustração mostra a funcionalidade de mídia para área de trabalho.":::

---

## <a name="error-handling"></a>Tratamento de erros

Certifique-se de lidar com esses erros adequadamente em seu aplicativo teams. A tabela a seguir lista os códigos de erro e as descrições sob as quais os erros são gerados:

|Código de erro |  Nome do erro     | Descrição|
| --------- | --------------- | -------- |
| **100** | NÃO_SUPORTADO_NA_PLATAFORMA | A API não é compatível com a plataforma atual.|
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

* Chame `selectMedia` a API para capturar vídeos usando a câmera:

  * Capturando vídeos com `fullscreen: true`:

       `fullscreen: true` abre a câmera no modo de gravação de vídeo. Ele fornece uma opção para usar a câmera frontal e traseira e também fornece outros atributos, conforme mencionado no exemplo a seguir:

       ```javascript
        
         const defaultLensVideoProps: microsoftTeams.media.VideoProps = {
             sources: [microsoftTeams.media.Source.Camera, microsoftTeams.media.Source.Gallery],
             startMode: microsoftTeams.media.CameraStartMode.Video,
             cameraSwitcher: true,
             maxDuration: 30
        }
         const defaultLensVideoMediaInput: microsoftTeams.media.MediaInputs = {
             mediaType: microsoftTeams.media.MediaType.Video,
             maxMediaCount: 6,
             videoProps: defaultLensVideoProps
        }
       ```

  * Capturando vídeos com `fullscreen: false`:

       `fullscreen: false` abre a câmera no modo de gravação de vídeo e usa apenas a câmera frontal. Normalmente é `fullscreen: false` usado quando o usuário deseja gravar vídeo durante a leitura de conteúdo na tela do dispositivo.

       Esse modo também dá suporte `isStopButtonVisible: true` a um botão parar na tela que permite que o usuário interrompa a gravação. Se `isStopButtonVisible: false`, a gravação pode ser interrompida chamando a API mediaController ou quando a duração da gravação tiver atingido `maxDuration` o tempo especificado.

       A seguir está um exemplo para interromper a gravação com `maxDuration` o tempo especificado:

       ```javascript
          const defaultNativeVideoProps: microsoftTeams.media.VideoProps = {
             maxDuration: 30,
             isFullScreenMode: false,
             isStopButtonVisible: false,
             videoController: new microsoftTeams.media.VideoController(videoControllerCallback)
         }
          const defaultNativeVideoMediaInput: microsoftTeams.media.MediaInputs = {
             mediaType: microsoftTeams.media.MediaType.Video,
             maxMediaCount: 1,
             videoProps: defaultNativeVideoProps
         }
       ```

       A seguir está um exemplo para interromper a gravação chamando a API mediaController:

       ```javascript
          const defaultNativeVideoProps: microsoftTeams.media.VideoProps = {
             videoController.stop(),
             isFullScreenMode: false,
             isStopButtonVisible: false,
             videoController: new microsoftTeams.media.VideoController(videoControllerCallback)
         }
          const defaultNativeVideoMediaInput: microsoftTeams.media.MediaInputs = {
             mediaType: microsoftTeams.media.MediaType.Video,
             maxMediaCount: 1,
             videoProps: defaultNativeVideoProps
         }
       ```

* Chame `selectMedia` a API para capturar imagens e vídeo usando a câmera:

  Isso permite que os usuários selecionem entre capturar uma imagem ou um vídeo.

    ```javascript
    
      const defaultVideoAndImageProps: microsoftTeams.media.VideoAndImageProps = {
        sources: [microsoftTeams.media.Source.Camera, microsoftTeams.media.Source.Gallery],
        startMode: microsoftTeams.media.CameraStartMode.Photo,
        ink: true,
        cameraSwitcher: true,
        textSticker: true,
        enableFilter: true,
        maxDuration: 30
      }
    
      const defaultVideoAndImageMediaInput: microsoftTeams.media.MediaInputs = {
        mediaType: microsoftTeams.media.MediaType.VideoAndImage,
        maxMediaCount: 6,
        videoAndImageProps: defaultVideoAndImageProps
      }
    
      let videoControllerCallback: microsoftTeams.media.VideoControllerCallback = {
        onRecordingStarted() {
          console.log('onRecordingStarted Callback Invoked');
        },
      };
    
      microsoftTeams.media.selectMedia(defaultVideoAndImageMediaInput, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
        if (error) {
            if (error.message) {
                alert(" ErrorCode: " + error.errorCode + error.message);
            } else {
                alert(" ErrorCode: " + error.errorCode);
            }
        }
        
        var videoElement = document.createElement("video");
        attachments[0].getMedia((error: microsoftTeams.SdkError, blob: Blob) => {
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
        videoElement.setAttribute("src", ("data:" + audioResult.mimeType + ";base64," + audioResult.preview));
        audioResult.getMedia((error: microsoftTeams.SdkError, blob: Blob) => {
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
    });
    ```

## <a name="file-download-on-teams-mobile"></a>Download de arquivo no teams mobile

Você pode configurar um aplicativo para permitir que os usuários baixem arquivos do modo de exibição da Web para seus dispositivos móveis.

>[!NOTE]
> O download de arquivos só tem suporte no cliente móvel do Android Teams e somente arquivos não autenticados podem ser baixados.

Para habilitar, siga as etapas:

1. Atualize o arquivo [manifest.json do](../../resources/schema/manifest-schema.md#devicepermissions) aplicativo Teams adicionando a `devicePermissions` propriedade e especificando `media` conforme mostrado no manifesto [de atualização](#update-manifest).

2. Use o seguinte formato e adicione o atributo de download HMTL à página da Web:

    ```html
    <a href="path_to_file" download="download">Download</a>
    ```

## <a name="see-also"></a>Confira também

* [Integrar o recurso de leitor de código QR ou de barras no Teams](qr-barcode-scanner-capability.md)
* [Integrar funcionalidades de localização no Teams](location-capability.md)
* [Integrar o Seletor de Pessoas](people-picker-capability.md)
* [Requisitos e considerações para bots de mídia hospedados em aplicativos](~/bots/calls-and-meetings/requirements-considerations-application-hosted-media-bots.md)
