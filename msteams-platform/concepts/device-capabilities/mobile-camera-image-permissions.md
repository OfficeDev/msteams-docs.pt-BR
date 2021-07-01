---
title: Integrar recursos de mídia
author: Rajeshwari-v
description: Como usar Teams SDK do cliente JavaScript para habilitar recursos de mídia
keywords: mídia de permissões nativas de dispositivo de recursos de microfone de imagem da câmera
ms.topic: conceptual
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: 22d4a791e83cf36f18b75a3846865835b0ee024f
ms.sourcegitcommit: 059d22c436ee9b07a61561ff71e03e1c23ff40b8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/30/2021
ms.locfileid: "53211622"
---
# <a name="integrate-media-capabilities"></a><span data-ttu-id="2f8e6-104">Integrar recursos de mídia</span><span class="sxs-lookup"><span data-stu-id="2f8e6-104">Integrate media capabilities</span></span> 

<span data-ttu-id="2f8e6-105">Você pode integrar recursos de dispositivo nativo, como a **câmera** e o **microfone** com seu Teams app.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-105">You can integrate native device capabilities, such as the **camera** and **microphone** with your Teams app.</span></span> <span data-ttu-id="2f8e6-106">Para integração, você pode usar [Microsoft Teams SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)do cliente JavaScript , que fornece as ferramentas necessárias para seu aplicativo acessar as permissões de dispositivo [de um usuário.](native-device-permissions.md)</span><span class="sxs-lookup"><span data-stu-id="2f8e6-106">For integration, you can use [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true), that provides the tools necessary for your app to access a user’s [device permissions](native-device-permissions.md).</span></span> <span data-ttu-id="2f8e6-107">Use APIs de funcionalidade de mídia adequadas  para  integrar os recursos do dispositivo, como câmera e microfone com a plataforma Teams no seu aplicativo móvel Microsoft Teams, e crie uma experiência mais rica.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-107">Use suitable media capability APIs to integrate the device capabilities, such as **camera** and **microphone** with the Teams platform within your Microsoft Teams mobile app, and build a richer experience.</span></span> 

## <a name="advantage-of-integrating-media-capabilities"></a><span data-ttu-id="2f8e6-108">Vantagem da integração de recursos de mídia</span><span class="sxs-lookup"><span data-stu-id="2f8e6-108">Advantage of integrating media capabilities</span></span>

<span data-ttu-id="2f8e6-109">A principal vantagem da integração de recursos de dispositivo em seus aplicativos Teams é que ele utiliza controles Teams nativos para fornecer uma experiência rica e imersiva aos seus usuários.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-109">The main advantage of integrating device capabilities in your Teams apps is it leverages native Teams controls to provide a rich and immersive experience to your users.</span></span>
<span data-ttu-id="2f8e6-110">Para integrar recursos de mídia, você deve atualizar o arquivo de manifesto do aplicativo e chamar as APIs de recurso de mídia.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-110">To integrate media capabilities you must update the app manifest file and call the media capability APIs.</span></span> 

<span data-ttu-id="2f8e6-111">Para uma integração eficaz, você deve ter uma boa compreensão dos trechos de código para chamar as [respectivas](#code-snippets) APIs, que permitem que você use recursos de mídia nativa.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-111">For effective integration, you must have a good understanding of [code snippets](#code-snippets) for calling the respective APIs, which allow you to use native media capabilities.</span></span>

<span data-ttu-id="2f8e6-112">É importante se familiarizar com os erros de resposta da [API](#error-handling) para lidar com os erros em seu Teams app.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-112">It is important to familiarize yourself with the [API response errors](#error-handling) to handle the errors in your Teams app.</span></span>

> [!NOTE] 
> * <span data-ttu-id="2f8e6-113">Atualmente, o Microsoft Teams suporte para recursos de mídia está disponível apenas para clientes móveis.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-113">Currently, Microsoft Teams support for media capabilities is available for mobile clients only.</span></span>   
> * <span data-ttu-id="2f8e6-114">Atualmente, o Teams não dá suporte a permissões de dispositivo para aplicativos de várias janelas, guias e o sidepanel de reunião.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-114">Currently, Teams does not support device permissions for multi window apps, tabs, and the meeting sidepanel.</span></span>    

## <a name="update-manifest"></a><span data-ttu-id="2f8e6-115">Manifesto de atualização</span><span class="sxs-lookup"><span data-stu-id="2f8e6-115">Update manifest</span></span>

<span data-ttu-id="2f8e6-116">Atualize seu Teams aplicativo [manifest.jsno](../../resources/schema/manifest-schema.md#devicepermissions) arquivo adicionando a propriedade `devicePermissions` e especificando `media` .</span><span class="sxs-lookup"><span data-stu-id="2f8e6-116">Update your Teams app [manifest.json](../../resources/schema/manifest-schema.md#devicepermissions) file by adding the `devicePermissions` property and specifying `media`.</span></span> <span data-ttu-id="2f8e6-117">Ele permite que seu aplicativo peça permissões de requisito dos  usuários antes de começar a usar a câmera para capturar a  imagem, abra a galeria para selecionar uma imagem para enviar como um anexo ou use o microfone para gravar a conversa.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-117">It allows your app to ask for requisite permissions from users before they start using  the **camera** to capture the image, open the gallery to select an image to submit as an attachment, or use the **microphone** to record the conversation.</span></span> <span data-ttu-id="2f8e6-118">A atualização do manifesto do aplicativo é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="2f8e6-118">The update for app manifest is as follows:</span></span>

``` json
"devicePermissions": [
    "media",
],
```

> [!NOTE]
> <span data-ttu-id="2f8e6-119">O **prompt De Permissões de** Solicitação é exibido automaticamente quando uma API Teams relevante é iniciada.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-119">The **Request Permissions** prompt is automatically displayed when a relevant Teams API is initiated.</span></span> <span data-ttu-id="2f8e6-120">Para obter mais informações, consulte [Solicitar permissões de dispositivo](native-device-permissions.md).</span><span class="sxs-lookup"><span data-stu-id="2f8e6-120">For more information, see [Request device permissions](native-device-permissions.md).</span></span>

## <a name="media-capability-apis"></a><span data-ttu-id="2f8e6-121">APIs de funcionalidade de mídia</span><span class="sxs-lookup"><span data-stu-id="2f8e6-121">Media capability APIs</span></span>

<span data-ttu-id="2f8e6-122">As [APIs selectMedia](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true), [getMedia](/javascript/api/@microsoft/teams-js/microsoftteams.media.mediachunk?view=msteams-client-js-latest&preserve-view=true)e [viewImages](/javascript/api/@microsoft/teams-js/microsoftteams.media.imageuri?view=msteams-client-js-latest&preserve-view=true) permitem que você use recursos de mídia nativa da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="2f8e6-122">The [selectMedia](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true), [getMedia](/javascript/api/@microsoft/teams-js/microsoftteams.media.mediachunk?view=msteams-client-js-latest&preserve-view=true), and [viewImages](/javascript/api/@microsoft/teams-js/microsoftteams.media.imageuri?view=msteams-client-js-latest&preserve-view=true) APIs enable you to use native media capabilities as follows:</span></span>

* <span data-ttu-id="2f8e6-123">Use o microfone **nativo** para permitir que os usuários **gravem áudio** (gravar 10 minutos de conversa) do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-123">Use the native **microphone** to allow users to **record audio** (record 10 minutes of conversation) from the device.</span></span>
* <span data-ttu-id="2f8e6-124">Use o controle **de câmera nativo** para permitir que os usuários **capturem e anexem imagens** em movimento.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-124">Use native **camera control** to allow users to **capture and attach images** on the go.</span></span>
* <span data-ttu-id="2f8e6-125">Use o suporte **de galeria nativa** para permitir que os usuários **selecionem imagens de dispositivo** como anexos.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-125">Use native **gallery support** to allow users to **select device images** as attachments.</span></span>
* <span data-ttu-id="2f8e6-126">Use o **controle do visualizador de imagem nativo** para visualizar várias **imagens** ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-126">Use native **image viewer control** to **preview multiple images** at one time.</span></span>
* <span data-ttu-id="2f8e6-127">Suporte **a transferência de imagem grande** (de 1 MB a 50 MB) através da ponte SDK.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-127">Support **large image transfer** (from 1 MB to 50 MB) through the SDK bridge.</span></span>
* <span data-ttu-id="2f8e6-128">Suporte **aos recursos avançados de imagem** que permitem que os usuários visualizem e editem imagens:</span><span class="sxs-lookup"><span data-stu-id="2f8e6-128">Support **advanced image capabilities** allowing users to preview and edit images:</span></span>
  * <span data-ttu-id="2f8e6-129">Examinar documento, quadro de trabalho e cartões de visita pela câmera.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-129">Scan document, whiteboard, and business cards  through the camera.</span></span>
  
> [!IMPORTANT]
> * <span data-ttu-id="2f8e6-130">As APIs , e podem ser invocadas de várias superfícies Teams, como módulos de `selectMedia` `getMedia` `viewImages` tarefas, guias e aplicativos pessoais.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-130">The `selectMedia`, `getMedia`, and `viewImages` APIs can be invoked from multiple Teams surfaces, such as task modules, tabs, and personal apps.</span></span> <span data-ttu-id="2f8e6-131">Para obter mais detalhes, consulte [Pontos de entrada para Teams aplicativos](../extensibility-points.md).</span><span class="sxs-lookup"><span data-stu-id="2f8e6-131">For more details, see [Entry points for Teams apps](../extensibility-points.md).</span></span>
> * <span data-ttu-id="2f8e6-132">`selectMedia` A API foi estendida para dar suporte a propriedades de microfone e áudio.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-132">`selectMedia` API has been extended to support microphone and audio properties.</span></span>

<span data-ttu-id="2f8e6-133">Você deve usar o seguinte conjunto de APIs para habilitar os recursos de mídia do dispositivo:</span><span class="sxs-lookup"><span data-stu-id="2f8e6-133">You must use the following set of APIs to enable your device's media capabilities:</span></span>

| <span data-ttu-id="2f8e6-134">API</span><span class="sxs-lookup"><span data-stu-id="2f8e6-134">API</span></span>      | <span data-ttu-id="2f8e6-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="2f8e6-135">Description</span></span>   |
| --- | --- |
| <span data-ttu-id="2f8e6-136">[**selectMedia**](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true) (**Câmera)**</span><span class="sxs-lookup"><span data-stu-id="2f8e6-136">[**selectMedia**](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true) (**Camera)**</span></span>| <span data-ttu-id="2f8e6-137">Essa API permite que os usuários **capturem ou selecionem mídia da** câmera do dispositivo e a retornem ao aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-137">This API allows users to **capture or select media from the device camera** and return it to the web-app.</span></span> <span data-ttu-id="2f8e6-138">Os usuários podem editar, cortar, girar, anotar ou desenhar imagens antes do envio.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-138">The users can edit, crop, rotate, annotate, or draw over images before submission.</span></span> <span data-ttu-id="2f8e6-139">Em resposta a , o aplicativo Web recebe as IDs de mídia de imagens selecionadas e `selectMedia` uma miniatura da mídia selecionada.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-139">In response to `selectMedia`, the web-app receives the media IDs of selected images and a thumbnail of the selected media.</span></span> <span data-ttu-id="2f8e6-140">Essa API pode ser configurada ainda mais por meio da [configuração ImageProps.](/javascript/api/@microsoft/teams-js/microsoftteams.media.imageprops?view=msteams-client-js-latest&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="2f8e6-140">This API can be further configured through the [ImageProps](/javascript/api/@microsoft/teams-js/microsoftteams.media.imageprops?view=msteams-client-js-latest&preserve-view=true) configuration.</span></span> |
| <span data-ttu-id="2f8e6-141">[**selectMedia**](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true) (**Microfone**)</span><span class="sxs-lookup"><span data-stu-id="2f8e6-141">[**selectMedia**](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true) (**Microphone**)</span></span>| <span data-ttu-id="2f8e6-142">De definir [o mediaType](/javascript/api/@microsoft/teams-js/microsoftteams.media.mediatype?view=msteams-client-js-latest&preserve-view=true) como `4` na API para acessar o recurso de `selectMedia` microfone.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-142">Set the [mediaType](/javascript/api/@microsoft/teams-js/microsoftteams.media.mediatype?view=msteams-client-js-latest&preserve-view=true) to `4` in `selectMedia` API for accessing microphone  capability.</span></span> <span data-ttu-id="2f8e6-143">Essa API também permite que os usuários gravem áudio do microfone do dispositivo e retornem clipes gravados para o aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-143">This API also allows users to record audio from the device microphone and return recorded clips to the web-app.</span></span> <span data-ttu-id="2f8e6-144">Os usuários podem pausar, gravar e reproduzir a visualização de gravação antes do envio.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-144">The users can pause, re-record, and play recording preview before submission.</span></span> <span data-ttu-id="2f8e6-145">Em resposta a **selectMedia**, o aplicativo Web recebe IDs de mídia da gravação de áudio selecionada.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-145">In response to **selectMedia**, the web-app receives media IDs of the selected audio recording.</span></span> <br/> <span data-ttu-id="2f8e6-146">Use `maxDuration` , se você precisar configurar uma duração em minutos para gravar a conversa.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-146">Use `maxDuration`, if you require to configure a duration in minutes for recording the conversation.</span></span> <span data-ttu-id="2f8e6-147">A duração atual da gravação é de 10 minutos, após o qual a gravação é encerrada.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-147">The current duration for recording is 10 minutes, after which the recording terminates.</span></span>  |
| [<span data-ttu-id="2f8e6-148">**getMedia**</span><span class="sxs-lookup"><span data-stu-id="2f8e6-148">**getMedia**</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams.media.mediachunk?view=msteams-client-js-latest&preserve-view=true)| <span data-ttu-id="2f8e6-149">Essa API recupera a mídia capturada pela API em `selectMedia` partes, independentemente do tamanho da mídia.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-149">This API retrieves the media captured by `selectMedia` API in chunks, irrespective of the media size.</span></span> <span data-ttu-id="2f8e6-150">Essas partes são montadas e enviadas de volta para o aplicativo Web como um arquivo ou blob.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-150">These chunks are assembled and sent back to the web app as a file or blob.</span></span> <span data-ttu-id="2f8e6-151">A quebra de mídia em partes menores facilita a transferência de arquivos grandes.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-151">Breaking of media into smaller chunks facilitates large file transfer.</span></span> |
| [<span data-ttu-id="2f8e6-152">**viewImages**</span><span class="sxs-lookup"><span data-stu-id="2f8e6-152">**viewImages**</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams.media.imageuri?view=msteams-client-js-latest&preserve-view=true)| <span data-ttu-id="2f8e6-153">Essa API permite que o usuário veja imagens no modo de tela inteira como uma lista rolável.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-153">This API enables the user to view images in  full-screen mode as a scrollable list.</span></span>|

<span data-ttu-id="2f8e6-154">A imagem a seguir mostra a experiência do aplicativo Web da `selectMedia` API para funcionalidade de imagem:</span><span class="sxs-lookup"><span data-stu-id="2f8e6-154">The following image depicts web app experience of `selectMedia` API for image capability:</span></span>

![câmera de dispositivo e experiência de imagem Teams](../../assets/images/tabs/image-capability.png)

<span data-ttu-id="2f8e6-156">A imagem a seguir mostra a experiência do aplicativo Web da `selectMedia` API para funcionalidade de microfone:</span><span class="sxs-lookup"><span data-stu-id="2f8e6-156">The following image depicts web app experience of `selectMedia` API for microphone capability:</span></span>

![experiência do aplicativo web para funcionalidade de microfone](../../assets/images/tabs/microphone-capability.png)

## <a name="error-handling"></a><span data-ttu-id="2f8e6-158">Tratamento de erros</span><span class="sxs-lookup"><span data-stu-id="2f8e6-158">Error handling</span></span>

<span data-ttu-id="2f8e6-159">Certifique-se de lidar com esses erros adequadamente em seu Teams app.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-159">You must ensure to handle these errors appropriately in your Teams app.</span></span> <span data-ttu-id="2f8e6-160">A tabela a seguir lista os códigos de erro e as condições nas quais os erros são gerados:</span><span class="sxs-lookup"><span data-stu-id="2f8e6-160">The following table lists the error codes and the conditions under which the errors are generated:</span></span> 

|<span data-ttu-id="2f8e6-161">Código de erro</span><span class="sxs-lookup"><span data-stu-id="2f8e6-161">Error code</span></span> |  <span data-ttu-id="2f8e6-162">Nome do erro</span><span class="sxs-lookup"><span data-stu-id="2f8e6-162">Error name</span></span>     | <span data-ttu-id="2f8e6-163">Condition</span><span class="sxs-lookup"><span data-stu-id="2f8e6-163">Condition</span></span>|
| --------- | --------------- | -------- |
| <span data-ttu-id="2f8e6-164">**100**</span><span class="sxs-lookup"><span data-stu-id="2f8e6-164">**100**</span></span> | <span data-ttu-id="2f8e6-165">NOT_SUPPORTED_ON_PLATFORM</span><span class="sxs-lookup"><span data-stu-id="2f8e6-165">NOT_SUPPORTED_ON_PLATFORM</span></span> | <span data-ttu-id="2f8e6-166">A API não tem suporte na plataforma atual.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-166">API is not supported on the current platform.</span></span>|
| <span data-ttu-id="2f8e6-167">**404**</span><span class="sxs-lookup"><span data-stu-id="2f8e6-167">**404**</span></span> | <span data-ttu-id="2f8e6-168">FILE_NOT_FOUND</span><span class="sxs-lookup"><span data-stu-id="2f8e6-168">FILE_NOT_FOUND</span></span> | <span data-ttu-id="2f8e6-169">O arquivo especificado não é encontrado no local determinado.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-169">File specified is not found in the given location.</span></span>|
| <span data-ttu-id="2f8e6-170">**500**</span><span class="sxs-lookup"><span data-stu-id="2f8e6-170">**500**</span></span> | <span data-ttu-id="2f8e6-171">INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="2f8e6-171">INTERNAL_ERROR</span></span> | <span data-ttu-id="2f8e6-172">Erro interno é encontrado durante a execução da operação necessária.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-172">Internal error is encountered while performing the required operation.</span></span>|
| <span data-ttu-id="2f8e6-173">**1000**</span><span class="sxs-lookup"><span data-stu-id="2f8e6-173">**1000**</span></span> | <span data-ttu-id="2f8e6-174">PERMISSION_DENIED</span><span class="sxs-lookup"><span data-stu-id="2f8e6-174">PERMISSION_DENIED</span></span> |<span data-ttu-id="2f8e6-175">A permissão é negada pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-175">Permission is denied by the user.</span></span>|
| <span data-ttu-id="2f8e6-176">**3000**</span><span class="sxs-lookup"><span data-stu-id="2f8e6-176">**3000**</span></span> | <span data-ttu-id="2f8e6-177">NO_HW_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="2f8e6-177">NO_HW_SUPPORT</span></span> | <span data-ttu-id="2f8e6-178">O hardware subjacente não dá suporte à funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-178">Underlying hardware does not support the capability.</span></span>|
| <span data-ttu-id="2f8e6-179">**4000**</span><span class="sxs-lookup"><span data-stu-id="2f8e6-179">**4000**</span></span>| <span data-ttu-id="2f8e6-180">INVALID_ARGUMENTS</span><span class="sxs-lookup"><span data-stu-id="2f8e6-180">INVALID_ARGUMENTS</span></span> | <span data-ttu-id="2f8e6-181">Um ou mais argumentos são inválidos.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-181">One or more arguments are invalid.</span></span>|
|  <span data-ttu-id="2f8e6-182">**8000**</span><span class="sxs-lookup"><span data-stu-id="2f8e6-182">**8000**</span></span> | <span data-ttu-id="2f8e6-183">USER_ABORT</span><span class="sxs-lookup"><span data-stu-id="2f8e6-183">USER_ABORT</span></span> |<span data-ttu-id="2f8e6-184">O usuário aborta a operação.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-184">User aborts the operation.</span></span>|
| <span data-ttu-id="2f8e6-185">**9000**</span><span class="sxs-lookup"><span data-stu-id="2f8e6-185">**9000**</span></span>| <span data-ttu-id="2f8e6-186">OLD_PLATFORM</span><span class="sxs-lookup"><span data-stu-id="2f8e6-186">OLD_PLATFORM</span></span> | <span data-ttu-id="2f8e6-187">O código da plataforma está desatualizado e não implementa essa API.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-187">Platform code is outdated and does not implement this API.</span></span>|
| <span data-ttu-id="2f8e6-188">**10000**</span><span class="sxs-lookup"><span data-stu-id="2f8e6-188">**10000**</span></span>| <span data-ttu-id="2f8e6-189">SIZE_EXCEEDED</span><span class="sxs-lookup"><span data-stu-id="2f8e6-189">SIZE_EXCEEDED</span></span> |  <span data-ttu-id="2f8e6-190">O valor de retorno é muito grande e excedeu os limites de tamanho da plataforma.</span><span class="sxs-lookup"><span data-stu-id="2f8e6-190">Return value is too big and has exceeded the platform size boundaries.</span></span>|

## <a name="code-snippets"></a><span data-ttu-id="2f8e6-191">Trechos de código</span><span class="sxs-lookup"><span data-stu-id="2f8e6-191">Code snippets</span></span>

<span data-ttu-id="2f8e6-192">**Chamada `selectMedia` API** para capturar imagens usando câmera:</span><span class="sxs-lookup"><span data-stu-id="2f8e6-192">**Calling `selectMedia` API** for capturing images using camera:</span></span>

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

<span data-ttu-id="2f8e6-193">**Chamada `getMedia` API** para recuperar grandes mídias em partes:</span><span class="sxs-lookup"><span data-stu-id="2f8e6-193">**Calling `getMedia` API** to retrieve large media in chunks:</span></span>

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

<span data-ttu-id="2f8e6-194">**Chamada `viewImages` API por ID retornada pela `selectMedia` API**:</span><span class="sxs-lookup"><span data-stu-id="2f8e6-194">**Calling `viewImages` API by ID returned by `selectMedia` API**:</span></span>

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

<span data-ttu-id="2f8e6-195">**Chamada `viewImages` API por URL**:</span><span class="sxs-lookup"><span data-stu-id="2f8e6-195">**Calling `viewImages` API by URL**:</span></span>

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

<span data-ttu-id="2f8e6-196">**Chamada `selectMedia` e `getMedia` APIs para gravação de áudio por microfone:**</span><span class="sxs-lookup"><span data-stu-id="2f8e6-196">**Calling `selectMedia` and `getMedia` APIs for recording audio through microphone**:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2f8e6-197">Confira também</span><span class="sxs-lookup"><span data-stu-id="2f8e6-197">See also</span></span>

* [<span data-ttu-id="2f8e6-198">Integrar a QR ou o recurso de scanner de código de barras Teams</span><span class="sxs-lookup"><span data-stu-id="2f8e6-198">Integrate QR or barcode scanner capability in Teams</span></span>](qr-barcode-scanner-capability.md)
* [<span data-ttu-id="2f8e6-199">Integrar recursos de localização Teams</span><span class="sxs-lookup"><span data-stu-id="2f8e6-199">Integrate location capabilities in Teams</span></span>](location-capability.md)
* [<span data-ttu-id="2f8e6-200">Integrar a funcionalidade do Se picker de pessoas no Teams</span><span class="sxs-lookup"><span data-stu-id="2f8e6-200">Integrate People Picker capability in Teams</span></span>](people-picker-capability.md)

