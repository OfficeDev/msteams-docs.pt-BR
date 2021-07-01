---
title: Integrar a funcionalidade do Se picker de pessoas
author: Rajeshwari-v
description: Como usar Teams SDK do cliente JavaScript para integrar o recurso de Selador de Pessoas
keywords: controle do se picker de pessoas
ms.topic: conceptual
localization_priority: Normal
ms.author: surbhigupta
ms.openlocfilehash: 8399eeb1a088e4b60c466d51c223b9405ebf1711
ms.sourcegitcommit: 059d22c436ee9b07a61561ff71e03e1c23ff40b8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/30/2021
ms.locfileid: "53211629"
---
# <a name="integrate-people-picker-capability"></a><span data-ttu-id="da549-104">Integrar a funcionalidade do Se picker de pessoas</span><span class="sxs-lookup"><span data-stu-id="da549-104">Integrate People Picker capability</span></span> 

<span data-ttu-id="da549-105">O Seletor de Pessoas é um controle para pesquisar e selecionar pessoas.</span><span class="sxs-lookup"><span data-stu-id="da549-105">People Picker is a control to search and select people.</span></span> <span data-ttu-id="da549-106">Esse é um recurso nativo disponível na Teams plataforma.</span><span class="sxs-lookup"><span data-stu-id="da549-106">This is a native capability available in Teams platform.</span></span> <span data-ttu-id="da549-107">Você pode integrar Teams controle de entrada nativo do People Picker com seus aplicativos Web.</span><span class="sxs-lookup"><span data-stu-id="da549-107">You can integrate Teams native People Picker input control with your web apps.</span></span> <span data-ttu-id="da549-108">Você pode selecionar entre uma seleção única ou várias e configurações, como limitar a pesquisa em um chat, canais ou em toda a organização.</span><span class="sxs-lookup"><span data-stu-id="da549-108">You can select between single or multi selection, and configurations, such as limiting search within a chat, channels, or across the entire organization.</span></span>

<span data-ttu-id="da549-109">Você pode usar [Microsoft Teams SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)do cliente JavaScript , que fornece API para integrar o recurso `selectPeople` People Picker no seu aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="da549-109">You can use [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true), which provides `selectPeople` API to integrate the People Picker capability within your web app.</span></span> 

## <a name="advantages-of-integrating-people-picker-capability"></a><span data-ttu-id="da549-110">Vantagens da integração da funcionalidade do Se picker de pessoas</span><span class="sxs-lookup"><span data-stu-id="da549-110">Advantages of integrating People Picker capability</span></span>

* <span data-ttu-id="da549-111">O controle People Picker funciona em todas as Teams, como módulo de tarefa, chat, canal, guia de reunião e aplicativo pessoal.</span><span class="sxs-lookup"><span data-stu-id="da549-111">The People Picker control works in all of Teams surfaces, such as task module, a chat, channel, meeting tab, and personal app.</span></span>
* <span data-ttu-id="da549-112">Esse controle permite que você pesquise e selecione usuários em um chat, canal ou toda a organização.</span><span class="sxs-lookup"><span data-stu-id="da549-112">This control allows you to search for and select users within a chat, channel, or the entire organization.</span></span>
*  <span data-ttu-id="da549-113">A funcionalidade People Picker ajuda com cenários que envolvem atribuição de tarefas, marcação e notificação de um usuário.</span><span class="sxs-lookup"><span data-stu-id="da549-113">The People Picker capability helps with scenarios involving task assignment, tagging, notifying a user.</span></span> 
* <span data-ttu-id="da549-114">Você pode usar esse controle prontamente disponível em seu aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="da549-114">You can use this readily available control in your web app.</span></span> <span data-ttu-id="da549-115">Economiza o esforço e o tempo significativamente para criar esse controle por conta própria.</span><span class="sxs-lookup"><span data-stu-id="da549-115">It saves the effort and time significantly to build such a control on your own.</span></span>

<span data-ttu-id="da549-116">Você deve chamar a `selectPeople` API para integrar o controle Se picker de pessoas em seu Teams app.</span><span class="sxs-lookup"><span data-stu-id="da549-116">You must call the `selectPeople` API to integrate People Picker control in your Teams app.</span></span> <span data-ttu-id="da549-117">Para uma integração eficaz, você deve ter uma compreensão do [trecho de código](#code-snippet) para chamar a API.</span><span class="sxs-lookup"><span data-stu-id="da549-117">For effective integration, you must have an understanding of [code snippet](#code-snippet) for calling the API.</span></span> <span data-ttu-id="da549-118">É importante se familiarizar com os erros de resposta [da API](#error-handling) para lidar com os erros em seu aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="da549-118">It is important to familiarize yourself with the [API response errors](#error-handling) to handle the errors in your web app.</span></span>

> [!NOTE] 
> <span data-ttu-id="da549-119">Atualmente, o Microsoft Teams para o recurso People Picker está disponível apenas para clientes móveis.</span><span class="sxs-lookup"><span data-stu-id="da549-119">Currently, Microsoft Teams support for People Picker capability is available for mobile clients only.</span></span>

## <a name="selectpeople-api"></a><span data-ttu-id="da549-120">`selectPeople` API</span><span class="sxs-lookup"><span data-stu-id="da549-120">`selectPeople` API</span></span> 

<span data-ttu-id="da549-121">`selectPeople`A API permite que você adicione Teams nativos `People Picker input control` aos seus aplicativos Web.</span><span class="sxs-lookup"><span data-stu-id="da549-121">`selectPeople` API enables you to add Teams native `People Picker input control` to your web apps.</span></span>  
<span data-ttu-id="da549-122">A descrição da API é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="da549-122">The API description is as follows:</span></span>

| <span data-ttu-id="da549-123">API</span><span class="sxs-lookup"><span data-stu-id="da549-123">API</span></span>      | <span data-ttu-id="da549-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="da549-124">Description</span></span>  |
| --- | --- |
|<span data-ttu-id="da549-125">**selectPeople**</span><span class="sxs-lookup"><span data-stu-id="da549-125">**selectPeople**</span></span>|<span data-ttu-id="da549-126">Inicia um Seletor de Pessoas e permite que o usuário pesquise e selecione uma ou mais pessoas na lista.</span><span class="sxs-lookup"><span data-stu-id="da549-126">Launches a People Picker and allows the user to search and select one or more people from the list.</span></span><br/><br/><span data-ttu-id="da549-127">Essa API retorna a ID, o nome e o endereço de email dos usuários selecionados para o aplicativo Web de chamada.</span><span class="sxs-lookup"><span data-stu-id="da549-127">This API returns the ID, name and email address of selected users to the calling web app.</span></span><br/><br/><span data-ttu-id="da549-128">No caso de um aplicativo pessoal, o controle pesquisa em toda a organização.</span><span class="sxs-lookup"><span data-stu-id="da549-128">In case of a personal app, the control searches across the organization.</span></span> <span data-ttu-id="da549-129">Se o aplicativo for adicionado a um chat ou canal, o contexto de pesquisa será configurado dependendo do cenário.</span><span class="sxs-lookup"><span data-stu-id="da549-129">If the app is added to a chat or channel, then the search context is configured depending on the scenario.</span></span> <span data-ttu-id="da549-130">A pesquisa é restrita dentro dos membros desse chat, canal ou disponibilizado em toda a organização.</span><span class="sxs-lookup"><span data-stu-id="da549-130">The search is restricted within the members of that chat, channel, or made available across the organization.</span></span>|

<span data-ttu-id="da549-131">A `selectPeople` API acompanha as seguintes configurações de entrada:</span><span class="sxs-lookup"><span data-stu-id="da549-131">The `selectPeople` API comes along with following input configurations:</span></span>

|<span data-ttu-id="da549-132">Parâmetro Configuration</span><span class="sxs-lookup"><span data-stu-id="da549-132">Configuration parameter</span></span>|<span data-ttu-id="da549-133">Tipo</span><span class="sxs-lookup"><span data-stu-id="da549-133">Type</span></span>|<span data-ttu-id="da549-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="da549-134">Description</span></span>| <span data-ttu-id="da549-135">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="da549-135">Default value</span></span>|
|-----|------|--------------|------|
|`title`| <span data-ttu-id="da549-136">String</span><span class="sxs-lookup"><span data-stu-id="da549-136">String</span></span>| <span data-ttu-id="da549-137">É um parâmetro opcional.</span><span class="sxs-lookup"><span data-stu-id="da549-137">It is an optional parameter.</span></span> <span data-ttu-id="da549-138">Ele define o título para o controle People Picker.</span><span class="sxs-lookup"><span data-stu-id="da549-138">It sets title for the People Picker control.</span></span> | <span data-ttu-id="da549-139">Selecionar pessoas</span><span class="sxs-lookup"><span data-stu-id="da549-139">Select people</span></span>|
|`setSelected`|<span data-ttu-id="da549-140">String</span><span class="sxs-lookup"><span data-stu-id="da549-140">String</span></span>| <span data-ttu-id="da549-141">É um parâmetro opcional.</span><span class="sxs-lookup"><span data-stu-id="da549-141">It is an optional parameter.</span></span> <span data-ttu-id="da549-142">Você deve passar as IDs do AAD das pessoas a serem pré-selecionadas.</span><span class="sxs-lookup"><span data-stu-id="da549-142">You must pass AAD IDs of the people to be preselected.</span></span> <span data-ttu-id="da549-143">Esse parâmetro pré-seleciona as pessoas ao iniciar o controle People Picker.</span><span class="sxs-lookup"><span data-stu-id="da549-143">This parameter preselects people while launching the People Picker control.</span></span> <span data-ttu-id="da549-144">Em caso de seleção única, apenas o primeiro usuário válido é pré-populado ignorando o restante.</span><span class="sxs-lookup"><span data-stu-id="da549-144">In case of single selection, only the first valid user is prepopulated ignoring the rest.</span></span> |<span data-ttu-id="da549-145">Nulo</span><span class="sxs-lookup"><span data-stu-id="da549-145">Null</span></span>| 
|`openOrgWideSearchInChatOrChannel`|<span data-ttu-id="da549-146">Booleano</span><span class="sxs-lookup"><span data-stu-id="da549-146">Boolean</span></span> | <span data-ttu-id="da549-147">É um parâmetro opcional.</span><span class="sxs-lookup"><span data-stu-id="da549-147">It is an optional parameter.</span></span> <span data-ttu-id="da549-148">Quando é definido como true, ele inicia o People Picker no escopo de toda a organização, mesmo que o aplicativo seja adicionado a um chat ou canal.</span><span class="sxs-lookup"><span data-stu-id="da549-148">When it is set to true, it launches the People Picker in organization wide scope even if the app is added to a chat or channel.</span></span> |<span data-ttu-id="da549-149">Falso</span><span class="sxs-lookup"><span data-stu-id="da549-149">False</span></span>|
|`singleSelect`|<span data-ttu-id="da549-150">Booleano</span><span class="sxs-lookup"><span data-stu-id="da549-150">Boolean</span></span>|<span data-ttu-id="da549-151">É um parâmetro opcional.</span><span class="sxs-lookup"><span data-stu-id="da549-151">It is an optional parameter.</span></span> <span data-ttu-id="da549-152">Quando ele é definido como true, ele inicia o Seletor de Pessoas restringindo a seleção somente a um usuário.</span><span class="sxs-lookup"><span data-stu-id="da549-152">When it is set to true, it launches the People Picker restricting the selection to one user only.</span></span> |<span data-ttu-id="da549-153">Falso</span><span class="sxs-lookup"><span data-stu-id="da549-153">False</span></span>|

<span data-ttu-id="da549-154">A imagem a seguir mostra a experiência do recurso People Picker em um aplicativo Web de exemplo:</span><span class="sxs-lookup"><span data-stu-id="da549-154">The following image depicts the experience of People Picker capability in a sample web app:</span></span>

![Experiência do aplicativo Web do recurso People Picker](../../assets/images/tabs/people-picker-control-capability.png)

### <a name="code-snippet"></a><span data-ttu-id="da549-156">Trecho de código</span><span class="sxs-lookup"><span data-stu-id="da549-156">Code snippet</span></span>

<span data-ttu-id="da549-157">**Chamada `selectPeople` API** para selecionar pessoas de uma lista:</span><span class="sxs-lookup"><span data-stu-id="da549-157">**Calling `selectPeople` API** to select people from a list:</span></span>

```javascript
 microsoftTeams.people.selectPeople((error: microsoftTeams.SdkError, people: microsoftTeams.people.PeoplePickerResult[]) => 
 {
    if (error) 
    {
        if (error.message) 
           {
             alert(" ErrorCode: " + error.errorCode + error.message);
           }
            else 
            {
              alert(" ErrorCode: " + error.errorCode);
            }
      }
    if (people)
     {
            output(" People length: " + people.length + " " + JSON.stringify(people));
      }
  });
```

## <a name="error-handling"></a><span data-ttu-id="da549-158">Tratamento de erros</span><span class="sxs-lookup"><span data-stu-id="da549-158">Error handling</span></span>

<span data-ttu-id="da549-159">Certifique-se de lidar com os erros adequadamente em seu aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="da549-159">You must ensure to handle the errors appropriately in your web app.</span></span> <span data-ttu-id="da549-160">A tabela a seguir lista os códigos de erro e as condições nas quais os erros são gerados:</span><span class="sxs-lookup"><span data-stu-id="da549-160">The following table lists the error codes and the conditions under which the errors are generated:</span></span> 

|<span data-ttu-id="da549-161">Código de erro</span><span class="sxs-lookup"><span data-stu-id="da549-161">Error code</span></span> |  <span data-ttu-id="da549-162">Nome do erro</span><span class="sxs-lookup"><span data-stu-id="da549-162">Error name</span></span>     | <span data-ttu-id="da549-163">Condition</span><span class="sxs-lookup"><span data-stu-id="da549-163">Condition</span></span>|
| --------- | --------------- | -------- |
| <span data-ttu-id="da549-164">**100**</span><span class="sxs-lookup"><span data-stu-id="da549-164">**100**</span></span> | <span data-ttu-id="da549-165">NOT_SUPPORTED_ON_PLATFORM</span><span class="sxs-lookup"><span data-stu-id="da549-165">NOT_SUPPORTED_ON_PLATFORM</span></span> | <span data-ttu-id="da549-166">A API não tem suporte na plataforma atual.</span><span class="sxs-lookup"><span data-stu-id="da549-166">API is not supported on the current platform.</span></span>|
| <span data-ttu-id="da549-167">**500**</span><span class="sxs-lookup"><span data-stu-id="da549-167">**500**</span></span> | <span data-ttu-id="da549-168">INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="da549-168">INTERNAL_ERROR</span></span> | <span data-ttu-id="da549-169">Erro interno é encontrado ao iniciar o Selador de Pessoas.</span><span class="sxs-lookup"><span data-stu-id="da549-169">Internal error is encountered while launching People Picker.</span></span>|
| <span data-ttu-id="da549-170">**4000**</span><span class="sxs-lookup"><span data-stu-id="da549-170">**4000**</span></span> | <span data-ttu-id="da549-171">INVALID_ARGUMENTS</span><span class="sxs-lookup"><span data-stu-id="da549-171">INVALID_ARGUMENTS</span></span> | <span data-ttu-id="da549-172">A API é invocada com argumentos obrigatórios errados ou insuficientes.</span><span class="sxs-lookup"><span data-stu-id="da549-172">API is invoked with wrong or insufficient mandatory arguments.</span></span>|
| <span data-ttu-id="da549-173">**8000**</span><span class="sxs-lookup"><span data-stu-id="da549-173">**8000**</span></span> | <span data-ttu-id="da549-174">USER_ABORT</span><span class="sxs-lookup"><span data-stu-id="da549-174">USER_ABORT</span></span> |<span data-ttu-id="da549-175">O usuário cancelou a operação.</span><span class="sxs-lookup"><span data-stu-id="da549-175">User cancelled the operation.</span></span>|
| <span data-ttu-id="da549-176">**9000**</span><span class="sxs-lookup"><span data-stu-id="da549-176">**9000**</span></span> | <span data-ttu-id="da549-177">OLD_PLATFORM</span><span class="sxs-lookup"><span data-stu-id="da549-177">OLD_PLATFORM</span></span> | <span data-ttu-id="da549-178">O usuário está em uma com build de plataforma antiga onde a implementação da API não está presente.</span><span class="sxs-lookup"><span data-stu-id="da549-178">User is on old platform build where implementation of the API is not present.</span></span>  <span data-ttu-id="da549-179">Atualizar a com build resolve o problema.</span><span class="sxs-lookup"><span data-stu-id="da549-179">Upgrading the build resolves the issue.</span></span>|

## <a name="see-also"></a><span data-ttu-id="da549-180">Confira também</span><span class="sxs-lookup"><span data-stu-id="da549-180">See also</span></span>

* [<span data-ttu-id="da549-181">Integrar recursos de mídia no Teams</span><span class="sxs-lookup"><span data-stu-id="da549-181">Integrate media capabilities in Teams</span></span>](mobile-camera-image-permissions.md)
* [<span data-ttu-id="da549-182">Integrar o código de QR ou o recurso de scanner de código de barras Teams</span><span class="sxs-lookup"><span data-stu-id="da549-182">Integrate QR code or barcode scanner capability in Teams</span></span>](qr-barcode-scanner-capability.md)
* [<span data-ttu-id="da549-183">Integrar recursos de localização Teams</span><span class="sxs-lookup"><span data-stu-id="da549-183">Integrate location capabilities in Teams</span></span>](location-capability.md)
