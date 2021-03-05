---
title: Integrar recursos de localização
description: Como usar o SDK do cliente JavaScript do Teams para aproveitar os recursos de localização
keywords: permissões de dispositivo nativo de recursos de mapa de localização
ms.author: lajanuar
ms.openlocfilehash: fccf39c37c785be716bfff26907f9184c0d9beec
ms.sourcegitcommit: 5cb3453e918bec1173899e7591b48a48113cf8f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2021
ms.locfileid: "50449600"
---
# <a name="integrate-location-capabilities"></a>Integrar recursos de localização 

Este documento orienta você sobre como integrar os recursos de localização do dispositivo nativo ao seu aplicativo do Teams.  

Você pode usar o [SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)do cliente JavaScript do Microsoft Teams, que fornece as ferramentas necessárias para que seu aplicativo acesse os recursos de dispositivo [nativo do usuário.](native-device-permissions.md) Use as APIs de local, como [getLocation](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_) e [showLocation,](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#showLocation_Location___error__SdkError__status__boolean_____void_) para integrar os recursos ao seu aplicativo. 

## <a name="advantages-of-integrating-location-capabilities"></a>Vantagens da integração de recursos de localização

A principal vantagem da integração de recursos de localização em seus aplicativos do Teams é que ele permite que os desenvolvedores de aplicativo web na plataforma Teams aproveitem a funcionalidade de local com o SDK do cliente JavaScript do Microsoft Teams. 

Exemplos a seguir mostram como a integração dos recursos de localização é usada em diferentes cenários:
* Em uma fábrica, o supervisor pode acompanhar a participação dos funcionários solicitando que eles tire uma selfie nas proximidades da fábrica e compartilhe-a por meio do aplicativo especificado. Os dados de local também são capturados e enviados junto com a imagem.
* Os recursos de localização permitem que a equipe de manutenção de um provedor de serviços compartilhe dados de saúde autênticos de torres de celular com o gerenciamento. O gerenciamento pode comparar qualquer incompatibilidade entre as informações de local capturadas e os dados enviados pela equipe de manutenção.

Para integrar recursos de local, você deve atualizar o arquivo de manifesto do aplicativo e chamar as APIs. Para uma integração eficaz, você deve ter uma boa compreensão dos [trechos](#code-snippets) de código para chamar as APIs de local. É importante se familiarizar com os erros de resposta [da API](#error-handling) para lidar com os erros em seu aplicativo do Teams.

> [!NOTE] 
> Atualmente, o suporte do Microsoft Teams para recursos de localização só está disponível para clientes móveis.

## <a name="update-manifest"></a>Manifesto de atualização

Atualize seu aplicativo do Teams [manifest.jsno](../../resources/schema/manifest-schema.md#devicepermissions) arquivo adicionando a propriedade `devicePermissions` e especificando `geolocation` . Ele permite que seu aplicativo peça permissões de requisito dos usuários antes de começar a usar os recursos de localização.

``` json
"devicePermissions": [
    "geolocation",
],
```

> [!NOTE]
> O **prompt de Permissões de** Solicitação é exibido automaticamente quando uma API relevante do Teams é iniciada. Para obter mais informações, consulte [request device permissions](native-device-permissions.md).

## <a name="location-apis"></a>APIs de localização

Você deve usar o seguinte conjunto de APIs para habilitar os recursos de localização do dispositivo:

| API      | Descrição   |
| --- | --- |
|[getLocation](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_) | Fornece o local do dispositivo atual do usuário ou abre o se picker de localização nativo e retorna o local escolhido pelo usuário. |
|[showLocation](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#showLocation) | Mostra o local no mapa |

> [!NOTE]

> A `getLocation()` API acompanha as seguintes configurações de [entrada](https://docs.microsoft.com/en-us/javascript/api/@microsoft/teams-js/locationprops?view=msteams-client-js-latest)e `allowChooseLocation` `showMap` . <br/> Se o valor for `allowChooseLocation` *verdadeiro,* os usuários poderão escolher qualquer local de sua escolha.<br/>  Se o valor for *falso,* os usuários não poderão alterar o local atual.<br/> Se o valor for `showMap` *false*, o local atual será buscado sem exibir o mapa. `showMap` será ignorado se `allowChooseLocation` estiver definido como *true*. 

**Experiência do aplicativo Web para recursos de localização** 
 ![ experiência do aplicativo web para recursos de localização](../../assets/images/tabs/location-capability.png)

## <a name="error-handling"></a>Tratamento de erros

Certifique-se de lidar com esses erros adequadamente em seu aplicativo do Teams. A tabela a seguir lista os códigos de erro e as condições nas quais os erros são gerados: 

|Código de erro |  Nome do erro     | Condition|
| --------- | --------------- | -------- |
| **100** | NOT_SUPPORTED_ON_PLATFORM | A API não tem suporte na plataforma atual.|
| **500** | INTERNAL_ERROR | Erro interno é encontrado durante a execução da operação necessária.|
| **1000** | PERMISSION_DENIED |As permissões de local negadas pelo usuário para o Aplicativo do Teams ou para o aplicativo Web .|
| **4000** | INVALID_ARGUMENTS | A API é invocada com argumentos obrigatórios errados ou insuficientes.|
| **8000** | USER_ABORT |O usuário cancelou a operação.|
| **9000** | OLD_PLATFORM | O usuário está em uma com build de plataforma antiga onde a implementação da API não está presente. A atualização da com build deve resolver o problema.|

## <a name="code-snippets"></a>Trechos de código

**Chamando `getLocation` a API para recuperar o local:**

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

**Chamando `showLocation` a API para exibir o local:**

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

## <a name="see-also"></a>Confira também

> [!div class="nextstepaction"]
> [Integrar recursos de mídia no Teams](mobile-camera-image-permissions.md)

> [!div class="nextstepaction"]
> [Integrar a QR ou o recurso de scanner de código de barras no Teams](qr-barcode-scanner-capability.md)