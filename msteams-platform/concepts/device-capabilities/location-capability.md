---
title: Integrar os recursos de localização
author: Rajeshwari-v
description: Como usar Teams SDK do cliente JavaScript para aproveitar os recursos de localização
keywords: permissões de dispositivo nativo de recursos de mapa de localização
ms.topic: conceptual
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: 55c3c6d82785b46580c3d8553d46a6e5e3a28fb4
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101776"
---
# <a name="integrate-location-capabilities"></a><span data-ttu-id="4e069-104">Integrar os recursos de localização</span><span class="sxs-lookup"><span data-stu-id="4e069-104">Integrate location capabilities</span></span> 

<span data-ttu-id="4e069-105">Este documento orienta você sobre como integrar os recursos de localização do dispositivo nativo ao seu Teams app.</span><span class="sxs-lookup"><span data-stu-id="4e069-105">This document guides you on how to integrate the location capabilities of native device with your Teams app.</span></span>  

<span data-ttu-id="4e069-106">Você pode usar [Microsoft Teams SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)do cliente JavaScript , que fornece as ferramentas necessárias para que seu aplicativo acesse os recursos de dispositivo [nativo do usuário.](native-device-permissions.md)</span><span class="sxs-lookup"><span data-stu-id="4e069-106">You can use [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true), which provides the tools necessary for your app to access the user’s [native device capabilities](native-device-permissions.md).</span></span> <span data-ttu-id="4e069-107">Use as APIs de local, como [getLocation](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true) e [showLocation,](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#showLocation_Location___error__SdkError__status__boolean_____void_&preserve-view=true) para integrar os recursos ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4e069-107">Use the location APIs, such as [getLocation](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true) and [showLocation](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#showLocation_Location___error__SdkError__status__boolean_____void_&preserve-view=true) to integrate the capabilities within your app.</span></span> 

## <a name="advantages-of-integrating-location-capabilities"></a><span data-ttu-id="4e069-108">Vantagens da integração de recursos de localização</span><span class="sxs-lookup"><span data-stu-id="4e069-108">Advantages of integrating location capabilities</span></span>

<span data-ttu-id="4e069-109">A principal vantagem da integração de recursos de localização em seus aplicativos Teams é que ele permite que os desenvolvedores de aplicativos Web na plataforma Teams aproveitem a funcionalidade de local com Microsoft Teams SDK do cliente JavaScript.</span><span class="sxs-lookup"><span data-stu-id="4e069-109">The main advantage of integrating location capabilities in your Teams apps is that it allows web app developers on Teams platform to leverage location functionality with Microsoft Teams JavaScript client SDK.</span></span> 

<span data-ttu-id="4e069-110">Exemplos a seguir mostram como a integração dos recursos de localização é usada em diferentes cenários:</span><span class="sxs-lookup"><span data-stu-id="4e069-110">Following examples show how the integration of location capabilities is used in different scenarios:</span></span>
* <span data-ttu-id="4e069-111">Em uma fábrica, o supervisor pode acompanhar a participação dos funcionários solicitando que eles tire uma selfie nas proximidades da fábrica e compartilhe-a por meio do aplicativo especificado.</span><span class="sxs-lookup"><span data-stu-id="4e069-111">In a factory, the supervisor can track the attendance of workers by asking them to take a selfie in the vicinity of the factory and share it through the specified app.</span></span> <span data-ttu-id="4e069-112">Os dados de local também são capturados e enviados junto com a imagem.</span><span class="sxs-lookup"><span data-stu-id="4e069-112">The location data also gets captured and sent along with the image.</span></span>
* <span data-ttu-id="4e069-113">Os recursos de localização permitem que a equipe de manutenção de um provedor de serviços compartilhe dados de saúde autênticos de torres de celular com o gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="4e069-113">The location capabilities enables the maintenance staff of a service provider to share authentic health data of cellular towers with the management.</span></span> <span data-ttu-id="4e069-114">O gerenciamento pode comparar qualquer incompatibilidade entre as informações de local capturadas e os dados enviados pela equipe de manutenção.</span><span class="sxs-lookup"><span data-stu-id="4e069-114">The management can compare any mismatch between captured location information and the data submitted by maintenance staff.</span></span>

<span data-ttu-id="4e069-115">Para integrar recursos de local, você deve atualizar o arquivo de manifesto do aplicativo e chamar as APIs.</span><span class="sxs-lookup"><span data-stu-id="4e069-115">To integrate location capabilities, you must update the app manifest file and call the APIs.</span></span> <span data-ttu-id="4e069-116">Para uma integração eficaz, você deve ter uma boa compreensão dos [trechos](#code-snippets) de código para chamar as APIs de local.</span><span class="sxs-lookup"><span data-stu-id="4e069-116">For effective integration, you must have a good understanding of [code snippets](#code-snippets) for calling the location APIs.</span></span> <span data-ttu-id="4e069-117">É importante se familiarizar com os erros de resposta da [API](#error-handling) para lidar com os erros em seu Teams app.</span><span class="sxs-lookup"><span data-stu-id="4e069-117">It is important to familiarize yourself with the [API response errors](#error-handling) to handle the errors in your Teams app.</span></span>

> [!NOTE] 
> <span data-ttu-id="4e069-118">Atualmente, o Microsoft Teams suporte para recursos de localização está disponível apenas para clientes móveis.</span><span class="sxs-lookup"><span data-stu-id="4e069-118">Currently, Microsoft Teams support for location capabilities is only available for mobile clients.</span></span>

## <a name="update-manifest"></a><span data-ttu-id="4e069-119">Manifesto de atualização</span><span class="sxs-lookup"><span data-stu-id="4e069-119">Update manifest</span></span>

<span data-ttu-id="4e069-120">Atualize seu Teams aplicativo [manifest.jsno](../../resources/schema/manifest-schema.md#devicepermissions) arquivo adicionando a propriedade `devicePermissions` e especificando `geolocation` .</span><span class="sxs-lookup"><span data-stu-id="4e069-120">Update your Teams app [manifest.json](../../resources/schema/manifest-schema.md#devicepermissions) file by adding the `devicePermissions` property and specifying `geolocation`.</span></span> <span data-ttu-id="4e069-121">Ele permite que seu aplicativo peça permissões de requisito dos usuários antes de começar a usar os recursos de localização.</span><span class="sxs-lookup"><span data-stu-id="4e069-121">It allows your app to ask for requisite permissions from users before they start using the location capabilities.</span></span>

``` json
"devicePermissions": [
    "geolocation",
],
```

> [!NOTE]
> <span data-ttu-id="4e069-122">O **prompt De Permissões de** Solicitação é exibido automaticamente quando uma API Teams relevante é iniciada.</span><span class="sxs-lookup"><span data-stu-id="4e069-122">The **Request Permissions** prompt is automatically displayed when a relevant Teams API is initiated.</span></span> <span data-ttu-id="4e069-123">Para obter mais informações, consulte [request device permissions](native-device-permissions.md).</span><span class="sxs-lookup"><span data-stu-id="4e069-123">For more information, see [request device permissions](native-device-permissions.md).</span></span>

## <a name="location-apis"></a><span data-ttu-id="4e069-124">APIs de localização</span><span class="sxs-lookup"><span data-stu-id="4e069-124">Location APIs</span></span>

<span data-ttu-id="4e069-125">Você deve usar o seguinte conjunto de APIs para habilitar os recursos de localização do dispositivo:</span><span class="sxs-lookup"><span data-stu-id="4e069-125">You must use the following set of APIs to enable your device's location capabilities:</span></span>

| <span data-ttu-id="4e069-126">API</span><span class="sxs-lookup"><span data-stu-id="4e069-126">API</span></span>      | <span data-ttu-id="4e069-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="4e069-127">Description</span></span>   |
| --- | --- |
|[<span data-ttu-id="4e069-128">getLocation</span><span class="sxs-lookup"><span data-stu-id="4e069-128">getLocation</span></span>](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true) | <span data-ttu-id="4e069-129">Fornece o local do dispositivo atual do usuário ou abre o se picker de localização nativo e retorna o local escolhido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="4e069-129">Gives user’s current device location or opens native location picker and returns the location chosen by the user.</span></span> |
|[<span data-ttu-id="4e069-130">showLocation</span><span class="sxs-lookup"><span data-stu-id="4e069-130">showLocation</span></span>](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#showLocation&preserve-view=true) | <span data-ttu-id="4e069-131">Mostra o local no mapa</span><span class="sxs-lookup"><span data-stu-id="4e069-131">Shows location on map</span></span> |

> [!NOTE]

> <span data-ttu-id="4e069-132">A `getLocation()` API acompanha as seguintes configurações de [entrada](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/locationprops?view=msteams-client-js-latest&preserve-view=true)e `allowChooseLocation` `showMap` .</span><span class="sxs-lookup"><span data-stu-id="4e069-132">The `getLocation()` API comes along with following [input configurations](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/locationprops?view=msteams-client-js-latest&preserve-view=true), `allowChooseLocation` and `showMap`.</span></span> <br/> <span data-ttu-id="4e069-133">Se o valor for `allowChooseLocation` *verdadeiro,* os usuários poderão escolher qualquer local de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="4e069-133">If the value of `allowChooseLocation` is *true*, then the users can choose any location of their choice.</span></span><br/>  <span data-ttu-id="4e069-134">Se o valor for *falso,* os usuários não poderão alterar o local atual.</span><span class="sxs-lookup"><span data-stu-id="4e069-134">If the value is *false*, then the users cannot change their current location.</span></span><br/> <span data-ttu-id="4e069-135">Se o valor for `showMap` *false*, o local atual será buscado sem exibir o mapa.</span><span class="sxs-lookup"><span data-stu-id="4e069-135">If the value of `showMap` is *false*, the current location is fetched without displaying the map.</span></span> <span data-ttu-id="4e069-136">`showMap` será ignorado se `allowChooseLocation` estiver definido como *true*.</span><span class="sxs-lookup"><span data-stu-id="4e069-136">`showMap` is ignored if `allowChooseLocation` is set to *true*.</span></span>

<span data-ttu-id="4e069-137">**Experiência do aplicativo Web para recursos de localização** 
 ![ experiência do aplicativo web para recursos de localização](../../assets/images/tabs/location-capability.png)</span><span class="sxs-lookup"><span data-stu-id="4e069-137">**Web app experience for location capabilities**
![web app experience for location capabilities](../../assets/images/tabs/location-capability.png)</span></span>

## <a name="error-handling"></a><span data-ttu-id="4e069-138">Tratamento de erros</span><span class="sxs-lookup"><span data-stu-id="4e069-138">Error handling</span></span>

<span data-ttu-id="4e069-139">Certifique-se de lidar com esses erros adequadamente em seu Teams app.</span><span class="sxs-lookup"><span data-stu-id="4e069-139">You must ensure to handle these errors appropriately in your Teams app.</span></span> <span data-ttu-id="4e069-140">A tabela a seguir lista os códigos de erro e as condições nas quais os erros são gerados:</span><span class="sxs-lookup"><span data-stu-id="4e069-140">The following table lists the error codes and the conditions under which the errors are generated:</span></span> 

|<span data-ttu-id="4e069-141">Código de erro</span><span class="sxs-lookup"><span data-stu-id="4e069-141">Error code</span></span> |  <span data-ttu-id="4e069-142">Nome do erro</span><span class="sxs-lookup"><span data-stu-id="4e069-142">Error name</span></span>     | <span data-ttu-id="4e069-143">Condição</span><span class="sxs-lookup"><span data-stu-id="4e069-143">Condition</span></span>|
| --------- | --------------- | -------- |
| <span data-ttu-id="4e069-144">**100**</span><span class="sxs-lookup"><span data-stu-id="4e069-144">**100**</span></span> | <span data-ttu-id="4e069-145">NOT_SUPPORTED_ON_PLATFORM</span><span class="sxs-lookup"><span data-stu-id="4e069-145">NOT_SUPPORTED_ON_PLATFORM</span></span> | <span data-ttu-id="4e069-146">A API não tem suporte na plataforma atual.</span><span class="sxs-lookup"><span data-stu-id="4e069-146">API is not supported on the current platform.</span></span>|
| <span data-ttu-id="4e069-147">**500**</span><span class="sxs-lookup"><span data-stu-id="4e069-147">**500**</span></span> | <span data-ttu-id="4e069-148">INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="4e069-148">INTERNAL_ERROR</span></span> | <span data-ttu-id="4e069-149">Erro interno é encontrado durante a execução da operação necessária.</span><span class="sxs-lookup"><span data-stu-id="4e069-149">Internal error is encountered while performing the required operation.</span></span>|
| <span data-ttu-id="4e069-150">**1000**</span><span class="sxs-lookup"><span data-stu-id="4e069-150">**1000**</span></span> | <span data-ttu-id="4e069-151">PERMISSION_DENIED</span><span class="sxs-lookup"><span data-stu-id="4e069-151">PERMISSION_DENIED</span></span> |<span data-ttu-id="4e069-152">As permissões de local negadas pelo usuário para o Teams App ou o web-app .</span><span class="sxs-lookup"><span data-stu-id="4e069-152">User denied location permissions to the Teams App or the web-app .</span></span>|
| <span data-ttu-id="4e069-153">**4000**</span><span class="sxs-lookup"><span data-stu-id="4e069-153">**4000**</span></span> | <span data-ttu-id="4e069-154">INVALID_ARGUMENTS</span><span class="sxs-lookup"><span data-stu-id="4e069-154">INVALID_ARGUMENTS</span></span> | <span data-ttu-id="4e069-155">A API é invocada com argumentos obrigatórios errados ou insuficientes.</span><span class="sxs-lookup"><span data-stu-id="4e069-155">API is invoked with wrong or insufficient mandatory arguments.</span></span>|
| <span data-ttu-id="4e069-156">**8000**</span><span class="sxs-lookup"><span data-stu-id="4e069-156">**8000**</span></span> | <span data-ttu-id="4e069-157">USER_ABORT</span><span class="sxs-lookup"><span data-stu-id="4e069-157">USER_ABORT</span></span> |<span data-ttu-id="4e069-158">O usuário cancelou a operação.</span><span class="sxs-lookup"><span data-stu-id="4e069-158">User cancelled the operation.</span></span>|
| <span data-ttu-id="4e069-159">**9000**</span><span class="sxs-lookup"><span data-stu-id="4e069-159">**9000**</span></span> | <span data-ttu-id="4e069-160">OLD_PLATFORM</span><span class="sxs-lookup"><span data-stu-id="4e069-160">OLD_PLATFORM</span></span> | <span data-ttu-id="4e069-161">O usuário está em uma com build de plataforma antiga onde a implementação da API não está presente.</span><span class="sxs-lookup"><span data-stu-id="4e069-161">User is on old platform build where implementation of the API is not present.</span></span> <span data-ttu-id="4e069-162">A atualização da com build deve resolver o problema.</span><span class="sxs-lookup"><span data-stu-id="4e069-162">Upgrading the build should resolve the issue.</span></span>|

## <a name="code-snippets"></a><span data-ttu-id="4e069-163">Trechos de código</span><span class="sxs-lookup"><span data-stu-id="4e069-163">Code snippets</span></span>

<span data-ttu-id="4e069-164">**Chamando `getLocation` a API para recuperar o local:**</span><span class="sxs-lookup"><span data-stu-id="4e069-164">**Calling `getLocation` API to retrieve the location:**</span></span>

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

<span data-ttu-id="4e069-165">**Chamando `showLocation` a API para exibir o local:**</span><span class="sxs-lookup"><span data-stu-id="4e069-165">**Calling `showLocation` API to display the location:**</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4e069-166">Confira também</span><span class="sxs-lookup"><span data-stu-id="4e069-166">See also</span></span>

* [<span data-ttu-id="4e069-167">Integrar recursos de mídia no Teams</span><span class="sxs-lookup"><span data-stu-id="4e069-167">Integrate media capabilities in Teams</span></span>](mobile-camera-image-permissions.md)
* [<span data-ttu-id="4e069-168">Integrar o código de QR ou o recurso de scanner de código de barras Teams</span><span class="sxs-lookup"><span data-stu-id="4e069-168">Integrate QR code or barcode scanner capability in Teams</span></span>](qr-barcode-scanner-capability.md)
