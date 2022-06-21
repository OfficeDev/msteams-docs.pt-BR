---
title: Integrar QR ou capacidade de leitura de código de barras
author: Rajeshwari-v
description: Saiba como usar Teams SDK do cliente JavaScript para aproveitar a funcionalidade de scanner de código de barras ou QR e conhecer os benefícios da integração da capacidade do scanner de código de barras ou QR.
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: surbhigupta
ms.openlocfilehash: d9dc35002398be047f4cd84d7600b3d149677bd3
ms.sourcegitcommit: 7bbb7caf729a00b267ceb8af7defffc91903d945
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/21/2022
ms.locfileid: "66189626"
---
# <a name="integrate-qr-or-barcode-scanner-capability"></a>Integrar QR ou capacidade de leitura de código de barras

Código de barras é um método de representação de dados em um formato visual e legível por computador. O código de barras contém informações sobre um produto, como um tipo, tamanho, fabricante e País de origem na forma de barras e espaços. O código é lido usando o scanner óptico na câmera nativa do dispositivo. Para obter uma experiência colaborativa mais avançada, você pode integrar a funcionalidade de scanner de código de barras ou QR fornecida na plataforma Teams ao seu aplicativo Teams.

Você pode usar o [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true), que fornece as ferramentas necessárias para que seu aplicativo acesse os [recursos do dispositivo nativo do usuário](native-device-permissions.md). Use a API [scanBarCode](/javascript/api/@microsoft/teams-js/microsoftteams.media?view=msteams-client-js-latest&preserve-view=true#scanBarCode__error__SdkError__decodedText__string_____void__BarCodeConfig_) para integrar o recurso de scanner em seu aplicativo.

## <a name="advantage-of-integrating-qr-or-barcode-scanner-capability"></a>Vantagem de integrar a funcionalidade do scanner de código de barras ou QR

A seguir estão as vantagens da integração dos recursos de QR ou scanner de código de barras:

* A integração permite que os desenvolvedores de aplicativos Web na plataforma Teams aproveitem a funcionalidade de verificação de QR ou código de barras com o SDK do cliente JavaScript do Teams.
* Com esse recurso, o usuário só precisa alinhar um QR ou código de barras dentro de um quadro no centro da interface do usuário do scanner e o código é verificado automaticamente. Os dados armazenados são compartilhados novamente com o aplicativo Web de chamada. Isso evita o inconveniente e os erros humanos de inserir códigos de produto longos ou outras informações relevantes manualmente.

Para integrar o recurso de scanner de código de barras ou QR, você deve atualizar o arquivo de manifesto do aplicativo e chamar a API [scanBarCode](/javascript/api/@microsoft/teams-js/microsoftteams.media?view=msteams-client-js-latest&preserve-view=true#scanBarCode__error__SdkError__decodedText__string_____void__BarCodeConfig_). Para uma integração eficaz, você deve ter um bom entendimento do [trecho de código](#code-snippet) para chamar a API [scanBarCode](/javascript/api/@microsoft/teams-js/microsoftteams.media?view=msteams-client-js-latest&preserve-view=true#scanBarCode__error__SdkError__decodedText__string_____void__BarCodeConfig_), que permite usar o recurso de scanner de código de barras ou QR nativo. A API fornece um erro para um padrão de código de barras sem suporte.
É importante se familiarizar com os [erros de resposta da API](#error-handling) para lidar com os erros no seu aplicativo do Teams.

> [!NOTE]
> Atualmente, o suporte do Microsoft Teams para o recurso QR ou scanner de código de barras está disponível apenas para clientes móveis.

## <a name="update-manifest"></a>Atualizar manifesto

Atualize o arquivo [manifest.json](../../resources/schema/manifest-schema.md#devicepermissions) de seu aplicativo Teams adicionando a propriedade `devicePermissions` e especificando `media`. Ele permite que seu aplicativo solicite permissões necessárias aos usuários antes de começar a usar a funcionalidade de scanner de código de barras ou QR. A atualização para o manifesto do aplicativo é a seguinte:

``` json
"devicePermissions": [
    "media",
],
```

> [!NOTE]
> O prompt de **Solicitar Permissões** é exibido automaticamente quando uma API do Teams relevante é iniciada. Para obter mais informações, consulte [Solicitar permissões de dispositivo](native-device-permissions.md).

## <a name="scanbarcode-api"></a>ScanBarCode API

A API [scanBarCode](/javascript/api/@microsoft/teams-js/microsoftteams.media?view=msteams-client-js-latest&preserve-view=true#scanBarCode__error__SdkError__decodedText__string_____void__BarCodeConfig_) invoca o controle de scanner que permite que o usuário digitalize diferentes tipos de código de barras e retorna o resultado como uma cadeia de caracteres.

Para personalizar a experiência de verificação de código de barras, [configuração de código de barras](/javascript/api/@microsoft/teams-js/microsoftteams.media.barcodeconfig?view=msteams-client-js-latest&preserve-view=true) é passada como entrada para a API [scanBarCode](/javascript/api/@microsoft/teams-js/microsoftteams.media?view=msteams-client-js-latest&preserve-view=true#scanBarCode__error__SdkError__decodedText__string_____void__BarCodeConfig_). Você pode especificar o intervalo de tempo limite da verificação em segundos usando `timeOutIntervalInSec`. Seu valor padrão é 30 segundos e o valor máximo é de 60 segundos.

A API **scanBarCode()** dá suporte aos seguintes tipos de código de barras:

| Tipo de Código de Barras | Com suporte no Android | Com suporte no iOS |
| ---------- | ---------- | ------------ |
| Barra de código | Sim | Não |
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

A imagem a seguir descreve a experiência do aplicativo da web com o recurso de scanner de código de barras ou QR:

![experiência de aplicativo da web para capacidade de scanner de código de barras ou qr](../../assets/images/tabs/qr-barcode-scanner-capability.png)

## <a name="error-handling"></a>Tratamento de erros

Você deve garantir que lide com esses erros adequadamente em seu aplicativo do Teams. A tabela a seguir lista os códigos de erro e as condições sob quais os erros são gerados:

|Código de erro |  Nome do erro     | Condição|
| --------- | --------------- | -------- |
| **100** | NÃO_SUPORTADO_NA_PLATAFORMA | A API não é compatível com a plataforma atual.|
| **500** | INTERNAL_ERROR | Erro interno encontrado durante a execução da operação necessária.|
| **1.000** | PERMISSION_DENIED |A permissão foi negada pelo usuário.|
| **3000** | NO_HW_SUPPORT | O hardware subjacente não dá suporte à funcionalidade.|
| **4000** | ARGUMENTOS_INVÁLIDOS | Um ou mais argumentos são inválidos.|
| **8000** | ABORTAR_USUÁRIO |O usuário anula a operação.|
| **8001** | OPERATION_TIMED_OUT | Não foi possível detectar o código de barras no intervalo de tempo especificado.|
| **9000** | ANTIGA_PLATAFORMA | O código da plataforma está desatualizado e não implementa essa API.|

## <a name="code-snippet"></a>Trecho de código

**Chamada `ScanBarCode()` API** para verificação de QR ou código de barras usando a câmera:

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

* [Integrar recursos de mídia](media-capabilities.md)
* [Integrar funcionalidades de localização no Teams](location-capability.md)
* [Integrar Seletor de Pessoas no Teams](people-picker-capability.md)
