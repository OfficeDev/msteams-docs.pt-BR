---
title: Integrar os recursos de localização
author: Rajeshwari-v
description: Como usar Teams cliente JavaScript SDK para aproveitar os recursos de localização
keywords: recursos de mapa de localização permite permissões de dispositivos nativos
ms.topic: conceptual
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: b85f19e74d0a8121dd290fc395c1018178437b3a
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566184"
---
# <a name="integrate-location-capabilities"></a>Integrar os recursos de localização 

Este documento orienta você sobre como integrar os recursos de localização do dispositivo nativo com o aplicativo Teams.  

Você pode usar [Microsoft Teams cliente JavaScript SDK,](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)que fornece as ferramentas necessárias para que seu aplicativo acesse os recursos de [dispositivos nativos](native-device-permissions.md)do usuário . Use as APIs de localização, como [getLocation](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true) e [showLocation](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#showLocation_Location___error__SdkError__status__boolean_____void_&preserve-view=true) para integrar os recursos dentro do seu aplicativo. 

## <a name="advantages-of-integrating-location-capabilities"></a>Vantagens de integrar recursos de localização

A principal vantagem de integrar recursos de localização em seus aplicativos Teams é que ele permite que desenvolvedores de aplicativos web na plataforma Teams aproveitem a funcionalidade de localização com Microsoft Teams cliente JavaScript SDK. 

Exemplos a seguir mostram como a integração dos recursos de localização é usada em diferentes cenários:
* Em uma fábrica, o supervisor pode acompanhar o atendimento dos trabalhadores pedindo-lhes para tirar uma selfie nas proximidades da fábrica e compartilhá-la através do aplicativo especificado. Os dados de localização também são capturados e enviados junto com a imagem.
* Os recursos de localização permitem que a equipe de manutenção de um prestador de serviços compartilhe dados de saúde autênticos de torres celulares com a gestão. O gerenciamento pode comparar qualquer incompatibilidade entre as informações de localização capturadas e os dados enviados pela equipe de manutenção.

Para integrar os recursos de localização, você deve atualizar o arquivo manifesto do aplicativo e chamar as APIs. Para uma integração eficaz, você deve ter uma boa compreensão dos [trechos](#code-snippets) de código para chamar as APIs de localização. É importante se familiarizar com os erros de resposta da [API](#error-handling) para lidar com os erros no aplicativo Teams.

> [!NOTE] 
> Atualmente, Microsoft Teams suporte para recursos de localização só está disponível para clientes móveis.

## <a name="update-manifest"></a>Manifesto de atualização

Atualize seu aplicativo Teams [manifest.jsno](../../resources/schema/manifest-schema.md#devicepermissions) arquivo adicionando a propriedade `devicePermissions` e especificando `geolocation` . Ele permite que seu aplicativo peça permissões necessárias aos usuários antes que eles comecem a usar os recursos de localização.

``` json
"devicePermissions": [
    "geolocation",
],
```

> [!NOTE]
> O prompt **de Permissões de Solicitação** é exibido automaticamente quando uma API Teams relevante é iniciada. Para obter mais informações, consulte [solicitações de permissões do dispositivo](native-device-permissions.md).

## <a name="location-apis"></a>APIs de localização

Você deve usar o seguinte conjunto de APIs para ativar os recursos de localização do seu dispositivo:

| API      | Descrição   |
| --- | --- |
|[obterLocação](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true) | Dá a localização atual do dispositivo do usuário ou abre o localizador nativo e retorna o local escolhido pelo usuário. |
|[showLocation](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#showLocation&preserve-view=true) | Mostra a localização no mapa. |

> [!NOTE]

> A `getLocation()` API vem junto com as [seguintes configurações de entrada,](/javascript/api/@microsoft/teams-js/locationprops?view=msteams-client-js-latest&preserve-view=true) `allowChooseLocation` e `showMap` . <br/> Se o valor `allowChooseLocation` for *verdadeiro,* então os usuários podem escolher qualquer local de sua escolha.<br/>  Se o valor for *falso,* os usuários não podem alterar sua localização atual.<br/> Se o valor `showMap` for *falso,* a localização atual será buscada sem exibir o mapa. `showMap` é ignorado se `allowChooseLocation` for definido como *verdadeiro*.

**Experiência de aplicativo web para recursos** 
 ![ de localização experiência de aplicativo web para recursos de localização](../../assets/images/tabs/location-capability.png)

## <a name="error-handling"></a>Tratamento de erros

Você deve garantir que você manuseie esses erros adequadamente em seu aplicativo Teams. A tabela a seguir lista os códigos de erro e as condições sob as quais os erros são gerados: 

|Código de erro |  Nome de erro     | Condição|
| --------- | --------------- | -------- |
| **100** | NOT_SUPPORTED_ON_PLATFORM | A API não é suportada na plataforma atual.|
| **500** | INTERNAL_ERROR | Erros internos são encontrados durante a execução da operação necessária.|
| **1000** | PERMISSION_DENIED |O usuário negou permissões de localização ao aplicativo Teams ou ao aplicativo web .|
| **4000** | INVALID_ARGUMENTS | A API é invocada com argumentos obrigatórios errados ou insuficientes.|
| **8000** | USER_ABORT |O usuário cancelou a operação.|
| **9000** | OLD_PLATFORM | O usuário está na construção de plataformas antigas onde a implementação da API não está presente. A atualização da compilação deve resolver o problema.|

## <a name="code-snippets"></a>Trechos de código

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

* [Integrar recursos de mídia em Teams](mobile-camera-image-permissions.md)
* [Integre o código QR ou o recurso do scanner de código de barras em Teams](qr-barcode-scanner-capability.md)
