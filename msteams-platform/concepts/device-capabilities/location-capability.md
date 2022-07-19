---
title: Integrar os recursos de localização
author: Rajeshwari-v
description: Saiba como usar o SDK do cliente JavaScript do Teams para aproveitar os recursos de localização usando trechos de Código e amostras.
ms.topic: conceptual
ms.localizationpriority: high
ms.author: surbhigupta
ms.openlocfilehash: 8290e78e9ea1baf87ce89642cd4f4f51b5f3c63d
ms.sourcegitcommit: 79d525c0be309200e930cdd942bc2c753d0b718c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/19/2022
ms.locfileid: "66842014"
---
# <a name="integrate-location-capabilities"></a>Integrar os recursos de localização

Você pode integrar os recursos de localização do dispositivo nativo ao aplicativo do Teams.  

Você pode usar o [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true), que fornece as ferramentas necessárias para que seu aplicativo para acessar [os recursos de dispositivo nativo](native-device-permissions.md) do usuário. Use as APIs de localização, como [getLocation](/javascript/api/@microsoft/teams-js/location.locationprops) e [showLocation](/javascript/api/@microsoft/teams-js/location.locationprops?), para integrar os recursos em seu aplicativo.

[!INCLUDE [sdk-include](~/includes/sdk-include.md)]

## <a name="advantages-of-integrating-location-capabilities"></a>Vantagens da integração de recursos de localização

A principal vantagem da integração de recursos de localização em seus aplicativos do Teams é que ele permite que os desenvolvedores de aplicativos Web na plataforma do Teams aproveitem a funcionalidade de localização com o SDK do cliente JavaScript do Microsoft Teams.

Os exemplos a seguir mostram como a integração de recursos de localização é usada em cenários diferentes:

* Em uma fábrica, o supervisor pode acompanhar a participação dos trabalhadores solicitando que eles tirem uma selfie nas proximidades da fábrica e compartilhe-a por meio do aplicativo especificado. Os dados de localização também são capturados e enviados junto com a imagem.
* As funcionalidades de localização permitem que a equipe de manutenção de um provedor de serviços compartilhe dados de integridade autênticos das torres de celular com o gerenciamento. O gerenciamento pode comparar qualquer incompatibilidade entre as informações de localização capturadas e os dados enviados pela equipe de manutenção.

Para integrar os recursos de localização, você deve atualizar o arquivo de manifesto do aplicativo e chamar as APIs. Para uma integração eficaz, você deve ter uma boa compreensão dos [snippets de código](#code-snippets) para chamar as APIs de localização.
É importante se familiarizar com os [erros de resposta da API](#error-handling) para lidar com os erros no seu aplicativo do Teams.

> [!NOTE]
> Atualmente, o suporte do Microsoft Teams para funcionalidades de localização está disponível somente para clientes de dispositivos móveis.

## <a name="update-manifest"></a>Atualizar manifesto

Atualize seu aplicativo do Teams do arquivo [ manifest.json do](../../resources/schema/manifest-schema.md#devicepermissions) adicionando a `devicePermissions` propriedade e especificando `geolocation`. Ele permite que seu aplicativo solicite permissões necessárias aos usuários antes de começar a usar os recursos de localização. A atualização para o manifesto do aplicativo é a seguinte:

``` json
"devicePermissions": [
    "geolocation",
],
```

> [!NOTE]
>
> * O prompt **Permissões de Solicitação** é exibido automaticamente quando uma API do Teams relevante é iniciada. Para mais informações, consulte [solicitar permissões de dispositivos](native-device-permissions.md).
> * As permissões do dispositivo são diferentes no navegador. Para saber mais, consulte [permissões de dispositivo do navegador](browser-device-permissions.md).

## <a name="location-apis"></a>APIs de Localização

Você deve usar o seguinte conjunto de APIs para habilitar os recursos de localização do dispositivo:

| API      | Descrição   |
| --- | --- |
|[getLocation](/javascript/api/@microsoft/teams-js/location.locationprops) | Fornece o local atual do dispositivo do usuário ou abre o seletor de local nativo e retorna o local escolhido pelo usuário. |
|[showLocation](/javascript/api/@microsoft/teams-js/location.locationprops?) | Mostra a localização no mapa. |

> [!NOTE]
> A `getLocation()`API vem com as seguintes [configurações de entrada](/javascript/api/@microsoft/teams-js/microsoftteams.location.locationprops), `allowChooseLocation` e `showMap`. <br/> Se o valor de `allowChooseLocation`for *verdadeiro*, os usuários poderão escolher qualquer localização de sua escolha.<br/>  Se o valor for *falso*, os usuários não poderão alterar o localização atual.<br/> Se o valor de `showMap`for *falso*, a localização atual será buscada sem exibir o mapa. `showMap` será ignorada se `allowChooseLocation` estiver definida omo *verdadeira*.

A imagem a seguir ilustra a experiência do aplicativo Web de funcionalidades de localização:

![experiência do aplicativo Web para recursos de localização](../../assets/images/tabs/location-capability.png)

### <a name="code-snippets"></a>Trechos de código

# <a name="teamsjs-v2"></a>[TeamsJS v2](#tab/teamsjs-v2)

**Chamando `getLocation` a API para recuperar a localização:**

```javascript
import {location} from "@microsoft/teams-js"

let locationProps = {"allowChooseLocation":true,"showMap":true};
if(location.isSupported()) {
    const locationPromise = location.getLocation(locationProps);
    locationPromise.
        then((result) => {output(JSON.stringify(result));}.
        catch((error) => {output(error);});
}
else {/*Handle case where capability isn't supported */}
```

**Chamar `showLocation` a API para exibir a localização:**

```javascript
import {location} from "@microsoft/teams-js"

let location = {"latitude":17,"longitude":17};
if(location.isSupported()) {
    const locationPromise = location.showLocation(location);
    locationPromise.
         then((result) => {/*Successful map display*/}).
         catch((error) => {/*Failed map display*/});
}
else {/*Handle case where capability isn't supported */}
```

# <a name="teamsjs-v1"></a>[TeamsJS v1](#tab/teamsjs-v1)

**Chamando `getLocation` a API para recuperar a localização:**

```javascript
let locationProps = {"allowChooseLocation":true,"showMap":true};
microsoftTeams.location.getLocation(locationProps, (err: microsoftTeams.SdkError, location: microsoftTeams.location.Location) => {
          if (err) {
            output(err);
            return;
          }
          output(JSON.stringify(location));
});
```

**Chamar `showLocation` a API para exibir a localização:**

```javascript
let location = {"latitude":17,"longitude":17};
microsoftTeams.location.showLocation(location, (err: microsoftTeams.SdkError, result: boolean) => {
          if (err) {
            output(err);
            return;
          }
     output(result);
});
```

---

## <a name="error-handling"></a>Tratamento de erros

Você deve garantir que lide com esses erros adequadamente em seu aplicativo do Teams. A tabela a seguir lista os códigos de erro e as condições sob quais os erros são gerados:

|Código de erro |  Nome do erro     | Condição|
| --------- | --------------- | -------- |
| **100** | NÃO_SUPORTADO_NA_PLATAFORMA | A API não é compatível com a plataforma atual.|
| **500** | INTERNAL_ERROR | Erro interno encontrado durante a execução da operação necessária.|
| **1.000** | PERMISSION_DENIED |O usuário negou permissões de localização para o aplicativo do Teams ou o aplicativo Web.|
| **4000** | ARGUMENTOS_INVÁLIDOS | A API foi invocada com argumentos obrigatórios incorretos ou insuficientes.|
| **8000** | ABORTAR_USUÁRIO |O usuário cancelou a operação.|
| **9000** | ANTIGA_PLATAFORMA | O usuário está na build da plataforma antiga onde a implementação da API está ausente. A atualização do build deve resolver o problema.|

### <a name="code-sample"></a>Exemplo de código

|Nome do exemplo | Descrição | C# | Node.js |
|----------------|-----------------|--------------|--------------|
| Localização atual do check-in do aplicativo | Os usuários podem fazer check-in de localização atual e exibir todos os check-ins de localização anteriores.| [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-checkin-location/csharp) | [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-checkin-location/nodejs) |

## <a name="see-also"></a>Confira também

* [Integrar recursos de mídia](media-capabilities.md)
* [Integrar a funcionalidade do código QR ou o verificador de código de barras no Teams](qr-barcode-scanner-capability.md)
* [Integrar o Seletor de Pessoas no Teams](people-picker-capability.md)
