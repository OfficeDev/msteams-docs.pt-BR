---
title: Integrar QR ou capacidade de leitura de código de barras
author: Rajeshwari-v
description: Como usar Teams SDK do cliente JavaScript para aproveitar a funcionalidade de QR ou scanner de código de barras
keywords: camera media qr code qrcode bar barcode scanner scan capabilities native device permissions
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: surbhigupta
ms.openlocfilehash: c21408ccbca6cd12d37d2066cf50f3468b669012
ms.sourcegitcommit: af1d0a4041ce215e7863ac12c71b6f1fa3e3ba81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2021
ms.locfileid: "60887996"
---
# <a name="integrate-qr-or-barcode-scanner-capability"></a>Integrar QR ou capacidade de leitura de código de barras

Código de barras é um método de representação de dados em um formulário visual e acessível por máquina. O código de barras contém informações sobre um produto, como um tipo, tamanho, fabricante e País de origem na forma de barras e espaços. O código é lido usando o scanner óptico em sua câmera de dispositivo nativa. Para uma experiência colaborativa mais rica, você pode integrar o recurso de QR ou scanner de código de barras fornecido na plataforma Teams com seu aplicativo Teams de código de barras.   

Você pode usar [Microsoft Teams SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)do cliente JavaScript , que fornece as ferramentas necessárias para que seu aplicativo acesse os recursos de dispositivo [nativo do usuário.](native-device-permissions.md) Use a API [scanBarCode](/javascript/api/@microsoft/teams-js/microsoftteams.media?view=msteams-client-js-latest&preserve-view=true#scanBarCode__error__SdkError__decodedText__string_____void__BarCodeConfig_) para integrar o recurso de scanner ao seu aplicativo.

## <a name="advantage-of-integrating-qr-or-barcode-scanner-capability"></a>Vantagem de integrar a QR ou o recurso de scanner de código de barras

A seguir estão as vantagens da integração dos recursos de QR ou scanner de código de barras: 

* A integração permite que os desenvolvedores de aplicativo web na plataforma Teams aproveitem a funcionalidade de verificação de QR ou código de barras com Teams SDK do cliente JavaScript.
* Com esse recurso, o usuário só precisa alinhar uma QR ou código de barras em um quadro no centro da interface do usuário do scanner e o código é verificado automaticamente. Os dados armazenados são compartilhados de volta com o aplicativo Web de chamada. Isso evita o inconveniente e os erros humanos de inserir códigos de produto longos ou outras informações relevantes manualmente.

Para integrar a QR ou o recurso de scanner de código de barras, você deve atualizar o arquivo de manifesto do aplicativo e chamar a API [scanBarCode.](/javascript/api/@microsoft/teams-js/microsoftteams.media?view=msteams-client-js-latest&preserve-view=true#scanBarCode__error__SdkError__decodedText__string_____void__BarCodeConfig_) Para uma integração eficaz, você [](#code-snippet) deve ter uma boa compreensão do trecho de código para chamar a API [scanBarCode,](/javascript/api/@microsoft/teams-js/microsoftteams.media?view=msteams-client-js-latest&preserve-view=true#scanBarCode__error__SdkError__decodedText__string_____void__BarCodeConfig_) que permite usar a QR nativa ou a funcionalidade de scanner de código de barras. A API fornece um erro para um padrão de código de barras sem suporte.
É importante se familiarizar com os erros de resposta da [API](#error-handling) para lidar com os erros em seu Teams app.

> [!NOTE] 
> Atualmente, Microsoft Teams suporte para QR ou recurso de scanner de código de barras está disponível apenas para clientes móveis.

## <a name="update-manifest"></a>Manifesto de atualização

Atualize seu Teams arquivo [manifest.json](../../resources/schema/manifest-schema.md#devicepermissions) do aplicativo adicionando a `devicePermissions` propriedade e especificando `media` . Ele permite que seu aplicativo peça permissões de requisito dos usuários antes de começar a usar o recurso de QR ou scanner de código de barras. A atualização do manifesto do aplicativo é a seguinte:

``` json
"devicePermissions": [
    "media",
],
```

> [!NOTE]
> O **prompt De Permissões de** Solicitação é exibido automaticamente quando uma API Teams relevante é iniciada. Para obter mais informações, consulte [Solicitar permissões de dispositivo](native-device-permissions.md).

## <a name="scanbarcode-api"></a>ScanBarCode API

A API [scanBarCode](/javascript/api/@microsoft/teams-js/microsoftteams.media?view=msteams-client-js-latest&preserve-view=true#scanBarCode__error__SdkError__decodedText__string_____void__BarCodeConfig_) invoca o controle de scanner que permite ao usuário examinar diferentes tipos de código de barras e retorna o resultado como uma cadeia de caracteres.

Para personalizar a experiência de verificação de código de barras, a configuração [opcional do código de barras](/javascript/api/@microsoft/teams-js/microsoftteams.media.barcodeconfig?view=msteams-client-js-latest&preserve-view=true) é passada como entrada para a API [scanBarCode.](/javascript/api/@microsoft/teams-js/microsoftteams.media?view=msteams-client-js-latest&preserve-view=true#scanBarCode__error__SdkError__decodedText__string_____void__BarCodeConfig_) Você pode especificar o intervalo de tempo de verificação em segundos usando `timeOutIntervalInSec` . Seu valor padrão é 30 segundos e o valor máximo é 60 segundos.

A **API scanBarCode()** dá suporte aos seguintes tipos de código de barras:

| Tipo de código de barras | Suportado no Android | Suportado no iOS |
| ---------- | ---------- | ------------ |
| Codebar | Sim | Não |
| Código 39 | Sim | Sim | 
| Código 93 | Sim | Sim |
| Código 128 | Sim | Sim |
| EAN-13 | Sim | Sim |
| EAN-8 | Sim | Sim |
| ITF | Não | Sim |
| Código QR | Sim | Sim |
| RSS expandido | Sim | Não |
| RSS-14 | Sim | Não |
| UPC-A | Sim | Sim |
| UPC-E | Sim | Sim |

A imagem a seguir mostra a experiência do aplicativo Web da capacidade de QR ou scanner de código de barras:

![experiência do aplicativo web para o recurso de scanner de código de barras ou qr](../../assets/images/tabs/qr-barcode-scanner-capability.png)

## <a name="error-handling"></a>Tratamento de erros

Certifique-se de lidar com esses erros adequadamente em seu Teams app. A tabela a seguir lista os códigos de erro e as condições nas quais os erros são gerados: 

|Código de erro |  Nome do erro     | Condição|
| --------- | --------------- | -------- |
| **100** | NOT_SUPPORTED_ON_PLATFORM | A API não tem suporte na plataforma atual.|
| **500** | INTERNAL_ERROR | Erro interno é encontrado durante a execução da operação necessária.|
| **1000** | PERMISSION_DENIED |A permissão é negada pelo usuário.|
| **3000** | NO_HW_SUPPORT | O hardware subjacente não dá suporte à funcionalidade.|
| **4000** | INVALID_ARGUMENTS | Um ou mais argumentos são inválidos.|
| **8000** | USER_ABORT |O usuário aborta a operação.|
| **8001** | OPERATION_TIMED_OUT | Não foi possível detectar o código de barras no intervalo de tempo determinado.|
| **9000** | OLD_PLATFORM | O código da plataforma está desatualizado e não implementa essa API.|

## <a name="code-snippet"></a>Trecho de código

**Chamada `ScanBarCode()` API** para verificação de QR ou código de barras usando câmera:

```javascript
const config: microsoftTeams.media.BarCodeConfig = {
  timeOutIntervalInSec: 30};
microsoftTeams.media.scanBarCode((error: microsoftTeams.SdkError, decodedText: string) => {
  if (error) {
    if (error.message) {
      output(" ErrorCode: " + error.errorCode + error.message);
    } else {
      output(" ErrorCode: " + error.errorCode);
    }
  } else if (decodedText) {
    output(decodedText);
  }
}, config);
```

## <a name="see-also"></a>Confira também

* [Integrar recursos de mídia no Teams](mobile-camera-image-permissions.md)
* [Integrar recursos de localização Teams](location-capability.md)
* [Integrar o Se picker de pessoas no Teams](people-picker-capability.md)
