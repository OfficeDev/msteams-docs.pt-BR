---
title: Integrar QR ou capacidade de leitura de código de barras
author: Rajeshwari-v
description: Como usar o SDK do cliente JavaScript do Teams para aproveitar o recurso de QR ou scanner de código de barras
keywords: camera media qr code qrcode bar barcode scanner scan capabilities native device permissions
localization_priority: Normal
ms.topic: conceptual
ms.author: surbhigupta
ms.openlocfilehash: ede791a6cd566a0fc725a04e0b615ae1b8eeb0eb
ms.sourcegitcommit: a732789190f59ec1f3699e8ad2f06387e8fe1458
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2021
ms.locfileid: "52058338"
---
# <a name="integrate-qr-or-barcode-scanner-capability"></a><span data-ttu-id="c3eb6-104">Integrar QR ou capacidade de leitura de código de barras</span><span class="sxs-lookup"><span data-stu-id="c3eb6-104">Integrate QR or barcode scanner capability</span></span> 

<span data-ttu-id="c3eb6-105">Este documento orienta você sobre como integrar o recurso de QR ou scanner de código de barras.</span><span class="sxs-lookup"><span data-stu-id="c3eb6-105">This document guides you on how to integrate the QR or barcode scanner capability.</span></span> 

<span data-ttu-id="c3eb6-106">Código de barras é um método de representação de dados em um formulário visual e acessível por máquina.</span><span class="sxs-lookup"><span data-stu-id="c3eb6-106">Barcode is a method of representing data in a visual and machine-readable form.</span></span> <span data-ttu-id="c3eb6-107">O código de barras contém informações sobre um produto, como um tipo, tamanho, fabricante e País de origem na forma de barras e espaços.</span><span class="sxs-lookup"><span data-stu-id="c3eb6-107">The barcode contains information about a product, such as a type, size, manufacturer, and Country of origin in the form of bars and spaces.</span></span> <span data-ttu-id="c3eb6-108">O código é lido usando o scanner óptico em sua câmera de dispositivo nativa.</span><span class="sxs-lookup"><span data-stu-id="c3eb6-108">The code is read using the optical scanner on your native device camera.</span></span> <span data-ttu-id="c3eb6-109">Para uma experiência colaborativa mais rica, você pode integrar o recurso de QR ou scanner de código de barras fornecido na plataforma Teams com seu aplicativo do Teams.</span><span class="sxs-lookup"><span data-stu-id="c3eb6-109">For a richer collaborative experience, you can integrate the QR or barcode scanner capability provided in the Teams platform with your Teams app.</span></span>   

<span data-ttu-id="c3eb6-110">Você pode usar o [SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)do cliente JavaScript do Microsoft Teams, que fornece as ferramentas necessárias para que seu aplicativo acesse os recursos de dispositivo [nativo do usuário.](native-device-permissions.md)</span><span class="sxs-lookup"><span data-stu-id="c3eb6-110">You can use [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true), which provides the tools necessary for your app to access the user’s [native device capabilities](native-device-permissions.md).</span></span> <span data-ttu-id="c3eb6-111">Use a `scanBarCode` API para integrar o recurso de scanner ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c3eb6-111">Use the `scanBarCode` API to integrate the scanner capability within your app.</span></span> 

## <a name="advantage-of-integrating-qr-or-barcode-scanner-capability"></a><span data-ttu-id="c3eb6-112">Vantagem de integrar a QR ou o recurso de scanner de código de barras</span><span class="sxs-lookup"><span data-stu-id="c3eb6-112">Advantage of integrating QR or barcode scanner capability</span></span>

<span data-ttu-id="c3eb6-113">A seguir estão as vantagens da integração dos recursos de QR ou scanner de código de barras:</span><span class="sxs-lookup"><span data-stu-id="c3eb6-113">Following are the advantages of integration of QR or barcode scanner capabilities:</span></span> 

* <span data-ttu-id="c3eb6-114">A integração permite que os desenvolvedores de aplicativo web na plataforma teams aproveitem a funcionalidade de verificação de QR ou código de barras com o SDK do cliente JavaScript do Teams.</span><span class="sxs-lookup"><span data-stu-id="c3eb6-114">The integration allows web app developers on Teams platform to leverage QR or barcode scanning functionality with Teams JavaScript client SDK.</span></span>
* <span data-ttu-id="c3eb6-115">Com esse recurso, o usuário só precisa alinhar uma QR ou código de barras em um quadro no centro da interface do usuário do scanner e o código é verificado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="c3eb6-115">With this feature, the user only needs to align a QR or barcode within a frame at the center of the scanner UI and the code gets scanned automatically.</span></span> <span data-ttu-id="c3eb6-116">Os dados armazenados são compartilhados de volta com o aplicativo Web de chamada.</span><span class="sxs-lookup"><span data-stu-id="c3eb6-116">The stored data is shared back with the calling web app.</span></span> <span data-ttu-id="c3eb6-117">Isso evita o inconveniente e os erros humanos de inserir códigos de produto longos ou outras informações relevantes manualmente.</span><span class="sxs-lookup"><span data-stu-id="c3eb6-117">This avoids the inconvenience and human-errors of entering lengthy product codes or other relevant information manually.</span></span>

<span data-ttu-id="c3eb6-118">Para integrar a QR ou o recurso de scanner de código de barras, você deve atualizar o arquivo de manifesto do aplicativo e chamar a `scanBarCode` API.</span><span class="sxs-lookup"><span data-stu-id="c3eb6-118">To integrate QR or barcode scanner capability, you must update the app manifest file and call the `scanBarCode` API.</span></span> <span data-ttu-id="c3eb6-119">Para uma integração eficaz, você [](#code-snippet) deve ter uma boa compreensão do trecho de código para chamar a API, o que permite que você use a QR nativa ou a funcionalidade de `scanBarCode` scanner de código de barras.</span><span class="sxs-lookup"><span data-stu-id="c3eb6-119">For effective integration, you must have a good understanding of [code snippet](#code-snippet) for calling the `scanBarCode` API, which allows you to use native QR or barcode scanner capability.</span></span> <span data-ttu-id="c3eb6-120">A API fornece um erro para um padrão de código de barras sem suporte.</span><span class="sxs-lookup"><span data-stu-id="c3eb6-120">The API gives an error for an unsupported barcode standard.</span></span>
<span data-ttu-id="c3eb6-121">É importante se familiarizar com os erros de resposta [da API](#error-handling) para lidar com os erros em seu aplicativo do Teams.</span><span class="sxs-lookup"><span data-stu-id="c3eb6-121">It is important to familiarize yourself with the [API response errors](#error-handling) to handle the errors in your Teams app.</span></span>

> [!NOTE] 
> <span data-ttu-id="c3eb6-122">Atualmente, o suporte do Microsoft Teams para a QR ou o recurso de scanner de código de barras está disponível apenas para clientes móveis.</span><span class="sxs-lookup"><span data-stu-id="c3eb6-122">Currently, Microsoft Teams support for QR or barcode scanner capability is only available for mobile clients.</span></span>

## <a name="update-manifest"></a><span data-ttu-id="c3eb6-123">Manifesto de atualização</span><span class="sxs-lookup"><span data-stu-id="c3eb6-123">Update manifest</span></span>

<span data-ttu-id="c3eb6-124">Atualize seu aplicativo do Teams [manifest.jsno](../../resources/schema/manifest-schema.md#devicepermissions) arquivo adicionando a propriedade `devicePermissions` e especificando `media` .</span><span class="sxs-lookup"><span data-stu-id="c3eb6-124">Update your Teams app [manifest.json](../../resources/schema/manifest-schema.md#devicepermissions) file by adding the `devicePermissions` property and specifying `media`.</span></span> <span data-ttu-id="c3eb6-125">Ele permite que seu aplicativo peça permissões de requisito dos usuários antes de começar a usar o recurso de QR ou scanner de código de barras.</span><span class="sxs-lookup"><span data-stu-id="c3eb6-125">It allows your app to ask for requisite permissions from users before they start using  the QR or barcode scanner capability.</span></span>

``` json
"devicePermissions": [
    "media",
],
```

> [!NOTE]
> <span data-ttu-id="c3eb6-126">O **prompt de Permissões de** Solicitação é exibido automaticamente quando uma API relevante do Teams é iniciada.</span><span class="sxs-lookup"><span data-stu-id="c3eb6-126">The **Request Permissions** prompt is automatically displayed when a relevant Teams API is initiated.</span></span> <span data-ttu-id="c3eb6-127">Para obter mais informações, consulte [Solicitar permissões de dispositivo](native-device-permissions.md).</span><span class="sxs-lookup"><span data-stu-id="c3eb6-127">For more information, see [Request device permissions](native-device-permissions.md).</span></span>

## <a name="scanbarcode-api"></a><span data-ttu-id="c3eb6-128">ScanBarCode API</span><span class="sxs-lookup"><span data-stu-id="c3eb6-128">ScanBarCode API</span></span>

<span data-ttu-id="c3eb6-129">A API invoca o controle de scanner que permite ao usuário examinar diferentes tipos de código de `ScanBarCode` barras e retorna o resultado como uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c3eb6-129">The `ScanBarCode` API invokes scanner control that enables the user to scan different types of barcode, and returns the result as a string.</span></span>

<span data-ttu-id="c3eb6-130">Para personalizar a experiência de verificação de código de barras, a configuração opcional do código de barras é passada como entrada para a `ScanBarCode` API.</span><span class="sxs-lookup"><span data-stu-id="c3eb6-130">To customize the barcode scanning experience, optional barcode configuration is passed as input to `ScanBarCode` API.</span></span> <span data-ttu-id="c3eb6-131">Você pode especificar o intervalo de tempo de verificação em segundos usando `timeOutIntervalInSec` .</span><span class="sxs-lookup"><span data-stu-id="c3eb6-131">You can specify the scan time-out interval in seconds using `timeOutIntervalInSec`.</span></span> <span data-ttu-id="c3eb6-132">Seu valor padrão é 30 segundos e o valor máximo é 60 segundos.</span><span class="sxs-lookup"><span data-stu-id="c3eb6-132">Its default value is 30 seconds and the maximum value is 60 seconds.</span></span>

<span data-ttu-id="c3eb6-133">A **API scanBarCode()** dá suporte aos seguintes tipos de código de barras:</span><span class="sxs-lookup"><span data-stu-id="c3eb6-133">The **scanBarCode()** API supports the following barcode types:</span></span>

| <span data-ttu-id="c3eb6-134">Tipo de código de barras</span><span class="sxs-lookup"><span data-stu-id="c3eb6-134">Barcode Type</span></span> | <span data-ttu-id="c3eb6-135">Suportado no Android</span><span class="sxs-lookup"><span data-stu-id="c3eb6-135">Supported on Android</span></span> | <span data-ttu-id="c3eb6-136">Suportado no iOS</span><span class="sxs-lookup"><span data-stu-id="c3eb6-136">Supported on iOS</span></span> |
| ---------- | ---------- | ------------ |
| <span data-ttu-id="c3eb6-137">Codebar</span><span class="sxs-lookup"><span data-stu-id="c3eb6-137">Codebar</span></span> | <span data-ttu-id="c3eb6-138">Sim</span><span class="sxs-lookup"><span data-stu-id="c3eb6-138">Yes</span></span> | <span data-ttu-id="c3eb6-139">Não</span><span class="sxs-lookup"><span data-stu-id="c3eb6-139">No</span></span> |
| <span data-ttu-id="c3eb6-140">Código 39</span><span class="sxs-lookup"><span data-stu-id="c3eb6-140">Code 39</span></span> | <span data-ttu-id="c3eb6-141">Sim</span><span class="sxs-lookup"><span data-stu-id="c3eb6-141">Yes</span></span> | <span data-ttu-id="c3eb6-142">Sim</span><span class="sxs-lookup"><span data-stu-id="c3eb6-142">Yes</span></span> | 
| <span data-ttu-id="c3eb6-143">Código 93</span><span class="sxs-lookup"><span data-stu-id="c3eb6-143">Code 93</span></span> | <span data-ttu-id="c3eb6-144">Sim</span><span class="sxs-lookup"><span data-stu-id="c3eb6-144">Yes</span></span> | <span data-ttu-id="c3eb6-145">Sim</span><span class="sxs-lookup"><span data-stu-id="c3eb6-145">Yes</span></span> |
| <span data-ttu-id="c3eb6-146">Código 128</span><span class="sxs-lookup"><span data-stu-id="c3eb6-146">Code 128</span></span> | <span data-ttu-id="c3eb6-147">Sim</span><span class="sxs-lookup"><span data-stu-id="c3eb6-147">Yes</span></span> | <span data-ttu-id="c3eb6-148">Sim</span><span class="sxs-lookup"><span data-stu-id="c3eb6-148">Yes</span></span> |
| <span data-ttu-id="c3eb6-149">EAN-13</span><span class="sxs-lookup"><span data-stu-id="c3eb6-149">EAN-13</span></span> | <span data-ttu-id="c3eb6-150">Sim</span><span class="sxs-lookup"><span data-stu-id="c3eb6-150">Yes</span></span> | <span data-ttu-id="c3eb6-151">Sim</span><span class="sxs-lookup"><span data-stu-id="c3eb6-151">Yes</span></span> |
| <span data-ttu-id="c3eb6-152">EAN-8</span><span class="sxs-lookup"><span data-stu-id="c3eb6-152">EAN-8</span></span> | <span data-ttu-id="c3eb6-153">Sim</span><span class="sxs-lookup"><span data-stu-id="c3eb6-153">Yes</span></span> | <span data-ttu-id="c3eb6-154">Sim</span><span class="sxs-lookup"><span data-stu-id="c3eb6-154">Yes</span></span> |
| <span data-ttu-id="c3eb6-155">ITF</span><span class="sxs-lookup"><span data-stu-id="c3eb6-155">ITF</span></span> | <span data-ttu-id="c3eb6-156">Não</span><span class="sxs-lookup"><span data-stu-id="c3eb6-156">No</span></span> | <span data-ttu-id="c3eb6-157">Sim</span><span class="sxs-lookup"><span data-stu-id="c3eb6-157">Yes</span></span> |
| <span data-ttu-id="c3eb6-158">Código QR</span><span class="sxs-lookup"><span data-stu-id="c3eb6-158">QR Code</span></span> | <span data-ttu-id="c3eb6-159">Sim</span><span class="sxs-lookup"><span data-stu-id="c3eb6-159">Yes</span></span> | <span data-ttu-id="c3eb6-160">Sim</span><span class="sxs-lookup"><span data-stu-id="c3eb6-160">Yes</span></span> |
| <span data-ttu-id="c3eb6-161">RSS expandido</span><span class="sxs-lookup"><span data-stu-id="c3eb6-161">RSS Expanded</span></span> | <span data-ttu-id="c3eb6-162">Sim</span><span class="sxs-lookup"><span data-stu-id="c3eb6-162">Yes</span></span> | <span data-ttu-id="c3eb6-163">Não</span><span class="sxs-lookup"><span data-stu-id="c3eb6-163">No</span></span> |
| <span data-ttu-id="c3eb6-164">RSS-14</span><span class="sxs-lookup"><span data-stu-id="c3eb6-164">RSS-14</span></span> | <span data-ttu-id="c3eb6-165">Sim</span><span class="sxs-lookup"><span data-stu-id="c3eb6-165">Yes</span></span> | <span data-ttu-id="c3eb6-166">Não</span><span class="sxs-lookup"><span data-stu-id="c3eb6-166">No</span></span> |
| <span data-ttu-id="c3eb6-167">UPC-A</span><span class="sxs-lookup"><span data-stu-id="c3eb6-167">UPC-A</span></span> | <span data-ttu-id="c3eb6-168">Sim</span><span class="sxs-lookup"><span data-stu-id="c3eb6-168">Yes</span></span> | <span data-ttu-id="c3eb6-169">Sim</span><span class="sxs-lookup"><span data-stu-id="c3eb6-169">Yes</span></span> |
| <span data-ttu-id="c3eb6-170">UPC-E</span><span class="sxs-lookup"><span data-stu-id="c3eb6-170">UPC-E</span></span> | <span data-ttu-id="c3eb6-171">Sim</span><span class="sxs-lookup"><span data-stu-id="c3eb6-171">Yes</span></span> | <span data-ttu-id="c3eb6-172">Sim</span><span class="sxs-lookup"><span data-stu-id="c3eb6-172">Yes</span></span> |

<span data-ttu-id="c3eb6-173">**Experiência do aplicativo Web para `ScanBarCode` API para QR ou experiência de aplicativo** web de recurso de scanner de código de barras para o recurso de scanner de código de barras ou 
 ![ qr](../../assets/images/tabs/qr-barcode-scanner-capability.png)</span><span class="sxs-lookup"><span data-stu-id="c3eb6-173">**Web app experience for `ScanBarCode` API for QR or barcode scanner capability**
![web app experience for qr or barcode scanner capability](../../assets/images/tabs/qr-barcode-scanner-capability.png)</span></span>

## <a name="error-handling"></a><span data-ttu-id="c3eb6-174">Tratamento de erros</span><span class="sxs-lookup"><span data-stu-id="c3eb6-174">Error handling</span></span>

<span data-ttu-id="c3eb6-175">Certifique-se de lidar com esses erros adequadamente em seu aplicativo do Teams.</span><span class="sxs-lookup"><span data-stu-id="c3eb6-175">You must ensure to handle these errors appropriately in your Teams app.</span></span> <span data-ttu-id="c3eb6-176">A tabela a seguir lista os códigos de erro e as condições nas quais os erros são gerados:</span><span class="sxs-lookup"><span data-stu-id="c3eb6-176">The following table lists the error codes and the conditions under which the errors are generated:</span></span> 

|<span data-ttu-id="c3eb6-177">Código de erro</span><span class="sxs-lookup"><span data-stu-id="c3eb6-177">Error code</span></span> |  <span data-ttu-id="c3eb6-178">Nome do erro</span><span class="sxs-lookup"><span data-stu-id="c3eb6-178">Error name</span></span>     | <span data-ttu-id="c3eb6-179">Condição</span><span class="sxs-lookup"><span data-stu-id="c3eb6-179">Condition</span></span>|
| --------- | --------------- | -------- |
| <span data-ttu-id="c3eb6-180">**100**</span><span class="sxs-lookup"><span data-stu-id="c3eb6-180">**100**</span></span> | <span data-ttu-id="c3eb6-181">NOT_SUPPORTED_ON_PLATFORM</span><span class="sxs-lookup"><span data-stu-id="c3eb6-181">NOT_SUPPORTED_ON_PLATFORM</span></span> | <span data-ttu-id="c3eb6-182">A API não tem suporte na plataforma atual.</span><span class="sxs-lookup"><span data-stu-id="c3eb6-182">API is not supported on the current platform.</span></span>|
| <span data-ttu-id="c3eb6-183">**500**</span><span class="sxs-lookup"><span data-stu-id="c3eb6-183">**500**</span></span> | <span data-ttu-id="c3eb6-184">INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="c3eb6-184">INTERNAL_ERROR</span></span> | <span data-ttu-id="c3eb6-185">Erro interno é encontrado durante a execução da operação necessária.</span><span class="sxs-lookup"><span data-stu-id="c3eb6-185">Internal error is encountered while performing the required operation.</span></span>|
| <span data-ttu-id="c3eb6-186">**1000**</span><span class="sxs-lookup"><span data-stu-id="c3eb6-186">**1000**</span></span> | <span data-ttu-id="c3eb6-187">PERMISSION_DENIED</span><span class="sxs-lookup"><span data-stu-id="c3eb6-187">PERMISSION_DENIED</span></span> |<span data-ttu-id="c3eb6-188">A permissão é negada pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="c3eb6-188">Permission is denied by the user.</span></span>|
| <span data-ttu-id="c3eb6-189">**3000**</span><span class="sxs-lookup"><span data-stu-id="c3eb6-189">**3000**</span></span> | <span data-ttu-id="c3eb6-190">NO_HW_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="c3eb6-190">NO_HW_SUPPORT</span></span> | <span data-ttu-id="c3eb6-191">O hardware subjacente não dá suporte à funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="c3eb6-191">Underlying hardware does not support the capability.</span></span>|
| <span data-ttu-id="c3eb6-192">**4000**</span><span class="sxs-lookup"><span data-stu-id="c3eb6-192">**4000**</span></span> | <span data-ttu-id="c3eb6-193">INVALID_ARGUMENTS</span><span class="sxs-lookup"><span data-stu-id="c3eb6-193">INVALID_ARGUMENTS</span></span> | <span data-ttu-id="c3eb6-194">Um ou mais argumentos são inválidos.</span><span class="sxs-lookup"><span data-stu-id="c3eb6-194">One or more arguments are invalid.</span></span>|
| <span data-ttu-id="c3eb6-195">**8000**</span><span class="sxs-lookup"><span data-stu-id="c3eb6-195">**8000**</span></span> | <span data-ttu-id="c3eb6-196">USER_ABORT</span><span class="sxs-lookup"><span data-stu-id="c3eb6-196">USER_ABORT</span></span> |<span data-ttu-id="c3eb6-197">O usuário aborta a operação.</span><span class="sxs-lookup"><span data-stu-id="c3eb6-197">User aborts the operation.</span></span>|
| <span data-ttu-id="c3eb6-198">**8001**</span><span class="sxs-lookup"><span data-stu-id="c3eb6-198">**8001**</span></span> | <span data-ttu-id="c3eb6-199">OPERATION_TIMED_OUT</span><span class="sxs-lookup"><span data-stu-id="c3eb6-199">OPERATION_TIMED_OUT</span></span> | <span data-ttu-id="c3eb6-200">Não foi possível detectar o código de barras no intervalo de tempo determinado.</span><span class="sxs-lookup"><span data-stu-id="c3eb6-200">Could not detect the barcode in the given time interval.</span></span>|
| <span data-ttu-id="c3eb6-201">**9000**</span><span class="sxs-lookup"><span data-stu-id="c3eb6-201">**9000**</span></span> | <span data-ttu-id="c3eb6-202">OLD_PLATFORM</span><span class="sxs-lookup"><span data-stu-id="c3eb6-202">OLD_PLATFORM</span></span> | <span data-ttu-id="c3eb6-203">O código da plataforma está desatualizado e não implementa essa API.</span><span class="sxs-lookup"><span data-stu-id="c3eb6-203">Platform code is outdated and does not implement this API.</span></span>|

## <a name="code-snippet"></a><span data-ttu-id="c3eb6-204">Trecho de código</span><span class="sxs-lookup"><span data-stu-id="c3eb6-204">Code snippet</span></span>

<span data-ttu-id="c3eb6-205">**Chamada `ScanBarCode()` API** para verificação de QR ou código de barras usando câmera:</span><span class="sxs-lookup"><span data-stu-id="c3eb6-205">**Calling `ScanBarCode()` API** for scanning QR or barcode using camera:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c3eb6-206">Confira também</span><span class="sxs-lookup"><span data-stu-id="c3eb6-206">See also</span></span>

- [<span data-ttu-id="c3eb6-207">Integrar recursos de mídia no Teams</span><span class="sxs-lookup"><span data-stu-id="c3eb6-207">Integrate media capabilities in Teams</span></span>](mobile-camera-image-permissions.md)

- [<span data-ttu-id="c3eb6-208">Integrar recursos de localização no Teams</span><span class="sxs-lookup"><span data-stu-id="c3eb6-208">Integrate location capabilities in Teams</span></span>](location-capability.md)
