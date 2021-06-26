---
title: Invocar e descartar módulos de tarefa
description: Invocar e descartar módulos de tarefa.
author: surbhigupta12
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: a23d5cee3f13967772a4b58ed973bf08906e36a6
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140765"
---
# <a name="invoke-and-dismiss-task-modules"></a><span data-ttu-id="6050a-103">Invocar e descartar módulos de tarefa</span><span class="sxs-lookup"><span data-stu-id="6050a-103">Invoke and dismiss task modules</span></span>

<span data-ttu-id="6050a-104">Os módulos de tarefa podem ser invocados de guias, bots ou links profundos.</span><span class="sxs-lookup"><span data-stu-id="6050a-104">Task modules can be invoked from tabs, bots, or deep links.</span></span> <span data-ttu-id="6050a-105">A resposta pode ser em HTML, JavaScript ou como um Cartão Adaptável.</span><span class="sxs-lookup"><span data-stu-id="6050a-105">The response can be either in HTML, JavaScript, or as an Adaptive Card.</span></span> <span data-ttu-id="6050a-106">Há muita flexibilidade em termos de como os módulos de tarefa são invocados e como lidar com a resposta da interação do usuário.</span><span class="sxs-lookup"><span data-stu-id="6050a-106">There is a lot of flexibility in terms of how task modules are invoked and how to deal with the response of the user's interaction.</span></span> <span data-ttu-id="6050a-107">A tabela a seguir resume como isso funciona:</span><span class="sxs-lookup"><span data-stu-id="6050a-107">The following table summarizes how this works:</span></span>

| <span data-ttu-id="6050a-108">Invocado usando</span><span class="sxs-lookup"><span data-stu-id="6050a-108">Invoked using</span></span> | <span data-ttu-id="6050a-109">Módulo de tarefa com HTML ou JavaScript</span><span class="sxs-lookup"><span data-stu-id="6050a-109">Task module with HTML or JavaScript</span></span> | <span data-ttu-id="6050a-110">Módulo de tarefa com Cartão Adaptável</span><span class="sxs-lookup"><span data-stu-id="6050a-110">Task module with Adaptive Card</span></span> |
| --- | --- | --- |
| <span data-ttu-id="6050a-111">JavaScript em uma guia</span><span class="sxs-lookup"><span data-stu-id="6050a-111">JavaScript in a tab</span></span> | <span data-ttu-id="6050a-112">1. Use a função SDK do Teams cliente `tasks.startTask()` com uma função de retorno de chamada `submitHandler(err, result)` opcional.</span><span class="sxs-lookup"><span data-stu-id="6050a-112">1. Use the Teams client SDK function `tasks.startTask()` with an optional `submitHandler(err, result)` callback function.</span></span> <br/><br/> <span data-ttu-id="6050a-113">2. No código do módulo de tarefas, quando o usuário tiver executado as ações, chame a função Teams SDK com um objeto `tasks.submitTask()` `result` como parâmetro.</span><span class="sxs-lookup"><span data-stu-id="6050a-113">2. In the task module code, when the user has performed the actions, call the Teams SDK function `tasks.submitTask()` with a `result` object as a parameter.</span></span> <span data-ttu-id="6050a-114">Se um `submitHandler` retorno de chamada foi especificado em , Teams chama como um `tasks.startTask()` `result` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="6050a-114">If a `submitHandler` callback was specified in `tasks.startTask()`, Teams calls it with `result` as a parameter.</span></span> <span data-ttu-id="6050a-115">Se houve um erro ao invocar , a `tasks.startTask()` função será chamada com uma cadeia de `submitHandler` `err` caracteres.</span><span class="sxs-lookup"><span data-stu-id="6050a-115">If there was an error when invoking `tasks.startTask()`, the `submitHandler` function is called with an `err` string instead.</span></span> <br/><br/> <span data-ttu-id="6050a-116">3. Você também pode especificar um `completionBotId` ao chamar `teams.startTask()` .</span><span class="sxs-lookup"><span data-stu-id="6050a-116">3. You can also specify a `completionBotId` when calling `teams.startTask()`.</span></span> <span data-ttu-id="6050a-117">Em `result` seguida, o é enviado para o bot.</span><span class="sxs-lookup"><span data-stu-id="6050a-117">Then the `result` is sent to the bot instead.</span></span> | <span data-ttu-id="6050a-118">1. Chame a função SDK do cliente Teams com um objeto TaskInfo e contenha o JSON para o Cartão Adaptável para mostrar no `tasks.startTask()` [](#the-taskinfo-object) `TaskInfo.card` pop-up do módulo de tarefas.</span><span class="sxs-lookup"><span data-stu-id="6050a-118">1. Call the Teams client SDK function `tasks.startTask()` with a [TaskInfo object](#the-taskinfo-object) and `TaskInfo.card` containing the JSON for the Adaptive Card to show in the task module pop-up.</span></span> <br/><br/> <span data-ttu-id="6050a-119">2. Se um retorno de chamada foi especificado em , Teams chama-o com uma cadeia de caracteres, se houve um erro ao invocar ou se o usuário fechar o `submitHandler` pop-up do módulo de tarefa usando o X na parte superior `tasks.startTask()` `err` `tasks.startTask()` direita.</span><span class="sxs-lookup"><span data-stu-id="6050a-119">2. If a `submitHandler` callback was specified in `tasks.startTask()`, Teams calls it with an `err` string, if there was an error when invoking `tasks.startTask()` or if the user closes the task module pop-up using the X at the upper right.</span></span> <br/><br/> <span data-ttu-id="6050a-120">3. Se o usuário pressionar um `Action.Submit` botão, seu `data` objeto será retornado como o valor de `result` .</span><span class="sxs-lookup"><span data-stu-id="6050a-120">3. If the user presses an `Action.Submit` button then its `data` object is returned as the value of `result`.</span></span> |
| <span data-ttu-id="6050a-121">Botão de cartão bot</span><span class="sxs-lookup"><span data-stu-id="6050a-121">Bot card button</span></span> | <span data-ttu-id="6050a-122">1. Botões de cartão bot, dependendo do tipo de botão, podem invocar módulos de tarefa de duas maneiras, uma URL de link profundo ou enviando uma `task/fetch` mensagem.</span><span class="sxs-lookup"><span data-stu-id="6050a-122">1. Bot card buttons, depending on the type of button, can invoke task modules in two ways, a deep link URL or by sending a `task/fetch` message.</span></span> <br/><br/> <span data-ttu-id="6050a-123">2. Se a ação do botão for o tipo de botão para Cartões Adaptáveis, um evento que seja `type` um HTTP POST será enviado para o `task/fetch` `Action.Submit` `task/fetch invoke` bot.</span><span class="sxs-lookup"><span data-stu-id="6050a-123">2. If the button's action `type` is `task/fetch` that is `Action.Submit` button type for Adaptive Cards, a `task/fetch invoke` event that is an HTTP POST is sent to the bot.</span></span> <span data-ttu-id="6050a-124">O bot responde ao POST com HTTP 200 e ao corpo da resposta contendo um wrapper ao redor do [objeto TaskInfo](#the-taskinfo-object).</span><span class="sxs-lookup"><span data-stu-id="6050a-124">The bot responds to the POST with HTTP 200 and the response body containing a wrapper around the [TaskInfo object](#the-taskinfo-object).</span></span> <span data-ttu-id="6050a-125">Para obter mais informações, consulte [invocando um módulo de tarefa usando `task/fetch` ](~/task-modules-and-cards/task-modules/task-modules-bots.md#invoke-a-task-module-using-taskfetch).</span><span class="sxs-lookup"><span data-stu-id="6050a-125">For more information, see [invoking a task module using `task/fetch`](~/task-modules-and-cards/task-modules/task-modules-bots.md#invoke-a-task-module-using-taskfetch).</span></span> <span data-ttu-id="6050a-126">Teams exibe o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="6050a-126">Teams displays the task module.</span></span> <br/><br/> <span data-ttu-id="6050a-127">3. Depois que o usuário tiver executado as ações, chame a função Teams SDK com um `tasks.submitTask()` `result` objeto como parâmetro.</span><span class="sxs-lookup"><span data-stu-id="6050a-127">3. After the user has performed the actions, call the Teams SDK function `tasks.submitTask()` with a `result` object as a parameter.</span></span> <span data-ttu-id="6050a-128">O bot recebe uma `task/submit invoke` mensagem que contém o `result` objeto.</span><span class="sxs-lookup"><span data-stu-id="6050a-128">The bot receives a `task/submit invoke` message that contains the `result` object.</span></span> <br/><br/> <span data-ttu-id="6050a-129">4. Você tem três maneiras diferentes de responder à mensagem, não fazendo nada que seja a tarefa concluída com êxito, exibindo uma mensagem para o usuário em uma janela pop-up ou invocando outra janela do módulo de `task/submit` tarefa.</span><span class="sxs-lookup"><span data-stu-id="6050a-129">4. You have three different ways to respond to the `task/submit` message, by doing nothing that is the task completed successfully, by displaying a message to the user in a pop-up window, or by invoking another task module window.</span></span> <span data-ttu-id="6050a-130">Para obter mais informações, [consulte discussão detalhada em `task/submit` ](~/task-modules-and-cards/task-modules/task-modules-bots.md#the-flexibility-of-tasksubmit).</span><span class="sxs-lookup"><span data-stu-id="6050a-130">For more information, see [detailed discussion on `task/submit`](~/task-modules-and-cards/task-modules/task-modules-bots.md#the-flexibility-of-tasksubmit).</span></span> | <ul><li> <span data-ttu-id="6050a-131">Como botões em cartões de Estrutura de Bot, os botões em Cartões Adaptáveis suportam duas maneiras de invocar módulos de tarefa, urLs de link profundo com botões e `Action.openUrl` `task/fetch` usar `Action.Submit` botões.</span><span class="sxs-lookup"><span data-stu-id="6050a-131">Like buttons on Bot Framework cards, buttons on Adaptive Cards support two ways of invoking task modules, deep link URLs with `Action.openUrl` buttons, and `task/fetch` using `Action.Submit` buttons.</span></span> </li></ul> <br/><br/> <ul><li> <span data-ttu-id="6050a-132">Os módulos de tarefa com Cartões Adaptáveis funcionam de forma muito semelhante ao caso HTML ou JavaScript.</span><span class="sxs-lookup"><span data-stu-id="6050a-132">Task modules with Adaptive Cards work very similarly to the HTML or JavaScript case.</span></span> <span data-ttu-id="6050a-133">A principal diferença é que, como não há JavaScript quando você está usando Cartões Adaptáveis, não há como chamar `tasks.submitTask()` .</span><span class="sxs-lookup"><span data-stu-id="6050a-133">The major difference is that since there is no JavaScript when you are using Adaptive Cards, there is no way to call `tasks.submitTask()`.</span></span> <span data-ttu-id="6050a-134">Em vez disso, Teams pega o objeto e o retorna como `data` `Action.Submit` a carga do `task/submit` evento.</span><span class="sxs-lookup"><span data-stu-id="6050a-134">Instead, Teams takes the `data` object from `Action.Submit` and returns it as the payload of the `task/submit` event.</span></span> <span data-ttu-id="6050a-135">Para obter mais informações, consulte [flexibilidade de `task/submit` ](~/task-modules-and-cards/task-modules/task-modules-bots.md#the-flexibility-of-tasksubmit).</span><span class="sxs-lookup"><span data-stu-id="6050a-135">For more information, see [flexibility of `task/submit`](~/task-modules-and-cards/task-modules/task-modules-bots.md#the-flexibility-of-tasksubmit).</span></span> </li></ul> |
| <span data-ttu-id="6050a-136">URL de link profundo</span><span class="sxs-lookup"><span data-stu-id="6050a-136">Deep link URL</span></span> <br/>[<span data-ttu-id="6050a-137">Sintaxe de URL</span><span class="sxs-lookup"><span data-stu-id="6050a-137">URL syntax</span></span>](#task-module-deep-link-syntax) | <span data-ttu-id="6050a-138">1. Teams invoca o módulo de tarefa que é a URL que aparece dentro do especificado no parâmetro `<iframe>` `url` do link profundo.</span><span class="sxs-lookup"><span data-stu-id="6050a-138">1. Teams invokes the task module that is the URL that appears inside the `<iframe>` specified in the `url` parameter of the deep link.</span></span> <span data-ttu-id="6050a-139">Não há `submitHandler` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="6050a-139">There is no `submitHandler` callback.</span></span> <br/><br/> <span data-ttu-id="6050a-140">2. Dentro do JavaScript da página no módulo de tarefas, chame para fechar com um objeto como um parâmetro, o mesmo que ao invocá-lo de uma guia ou um botão de cartão `tasks.submitTask()` `result` de bot.</span><span class="sxs-lookup"><span data-stu-id="6050a-140">2. Within the JavaScript of the page in the task module, call `tasks.submitTask()` to close it with a `result` object as a parameter, the same as when invoking it from a tab or a bot card button.</span></span> <span data-ttu-id="6050a-141">No entanto, a lógica de conclusão é ligeiramente diferente.</span><span class="sxs-lookup"><span data-stu-id="6050a-141">However, completion logic is slightly different.</span></span> <span data-ttu-id="6050a-142">Se sua lógica de conclusão reside no cliente que está se não houver bot, não há retorno de chamada, portanto, qualquer lógica de conclusão deve estar no código que precede a `submitHandler` chamada para `tasks.submitTask()` .</span><span class="sxs-lookup"><span data-stu-id="6050a-142">If your completion logic resides on the client that is if there is no bot, there is no `submitHandler` callback, so any completion logic must be in the code preceding the call to `tasks.submitTask()`.</span></span> <span data-ttu-id="6050a-143">Os erros de invocação são relatados apenas por meio do console.</span><span class="sxs-lookup"><span data-stu-id="6050a-143">Invocation errors are only reported through the console.</span></span> <span data-ttu-id="6050a-144">Se você tiver um bot, poderá especificar um parâmetro no `completionBotId` link profundo para enviar o objeto por meio de um `result` `task/submit` evento.</span><span class="sxs-lookup"><span data-stu-id="6050a-144">If you have a bot, then you can specify a `completionBotId` parameter in the deep link to send the `result` object through a `task/submit` event.</span></span> | <span data-ttu-id="6050a-145">1. Teams invoca o módulo de tarefa que é o corpo do cartão JSON do Cartão Adaptável especificado como um valor codificado por URL do parâmetro `card` do link profundo.</span><span class="sxs-lookup"><span data-stu-id="6050a-145">1. Teams invokes the task module that is the JSON card body of the Adaptive Card that is specified as a URL-encoded value of the `card` parameter of the deep link.</span></span> <br/><br/> <span data-ttu-id="6050a-146">2. O usuário fecha o módulo de tarefa selecionando o X no canto superior direito do módulo de tarefa ou pressionando `Action.Submit` um botão no cartão.</span><span class="sxs-lookup"><span data-stu-id="6050a-146">2. The user closes the task module by selecting the X at the upper right of the task module or by pressing an `Action.Submit` button on the card.</span></span> <span data-ttu-id="6050a-147">Como não há como chamar, o usuário deve ter um bot para enviar o valor `submitHandler` dos campos Cartão Adaptável.</span><span class="sxs-lookup"><span data-stu-id="6050a-147">Since there is no `submitHandler` to call, the user must have a bot to send the value of the Adaptive Card fields.</span></span> <span data-ttu-id="6050a-148">O usuário deve usar o `completionBotId` parâmetro no link profundo para especificar o bot para enviar os dados para o uso de um `task/submit invoke` evento.</span><span class="sxs-lookup"><span data-stu-id="6050a-148">The user must use the `completionBotId` parameter in the deep link to specify the bot to send the data to using a `task/submit invoke` event.</span></span> |

> [!NOTE]
> <span data-ttu-id="6050a-149">Não há suporte para invocar um módulo de tarefa do JavaScript no celular.</span><span class="sxs-lookup"><span data-stu-id="6050a-149">Invoking a task module from JavaScript is not supported on mobile.</span></span>

<span data-ttu-id="6050a-150">A próxima seção especifica o `TaskInfo` objeto que define determinados atributos para um módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="6050a-150">The next section specifies the `TaskInfo` object that defines certain attributes for a task module.</span></span>

## <a name="the-taskinfo-object"></a><span data-ttu-id="6050a-151">O objeto TaskInfo</span><span class="sxs-lookup"><span data-stu-id="6050a-151">The TaskInfo object</span></span>

<span data-ttu-id="6050a-152">O `TaskInfo` objeto contém os metadados de um módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="6050a-152">The `TaskInfo` object contains the metadata for a task module.</span></span> <span data-ttu-id="6050a-153">Defina `url` o para um iFrame incorporado ou para um Cartão `card` Adaptável.</span><span class="sxs-lookup"><span data-stu-id="6050a-153">Define the `url` for an embedded iFrame or `card` for an Adaptive Card.</span></span> <span data-ttu-id="6050a-154">A tabela a seguir fornece a definição de objeto:</span><span class="sxs-lookup"><span data-stu-id="6050a-154">The following table provides the object definition:</span></span>

| <span data-ttu-id="6050a-155">Atributo</span><span class="sxs-lookup"><span data-stu-id="6050a-155">Attribute</span></span> | <span data-ttu-id="6050a-156">Tipo</span><span class="sxs-lookup"><span data-stu-id="6050a-156">Type</span></span> | <span data-ttu-id="6050a-157">Descrição</span><span class="sxs-lookup"><span data-stu-id="6050a-157">Description</span></span> |
| --- | --- | --- |
| `title` | <span data-ttu-id="6050a-158">string</span><span class="sxs-lookup"><span data-stu-id="6050a-158">string</span></span> | <span data-ttu-id="6050a-159">Esse atributo aparece abaixo do nome do aplicativo e à direita do ícone do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6050a-159">This attribute appears below the app name and to the right of the app icon.</span></span> |
| `height` | <span data-ttu-id="6050a-160">número ou cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="6050a-160">number or string</span></span> | <span data-ttu-id="6050a-161">Esse atributo pode ser um número que representa a altura do módulo de tarefas em pixels `small` ou `medium` , ou `large` .</span><span class="sxs-lookup"><span data-stu-id="6050a-161">This attribute can be a number representing the task module's height in pixels, or `small`, `medium`, or `large`.</span></span> <span data-ttu-id="6050a-162">Para obter mais informações, consulte [task module sizing](#task-module-sizing).</span><span class="sxs-lookup"><span data-stu-id="6050a-162">For more information, see [task module sizing](#task-module-sizing).</span></span> |
| `width` | <span data-ttu-id="6050a-163">número ou cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="6050a-163">number or string</span></span> | <span data-ttu-id="6050a-164">Esse atributo pode ser um número que representa a largura do módulo de tarefa em pixels `small` ou `medium` , ou `large` .</span><span class="sxs-lookup"><span data-stu-id="6050a-164">This attribute can be a number representing the task module's width in pixels, or `small`, `medium`, or `large`.</span></span> <span data-ttu-id="6050a-165">Para obter mais informações, consulte [task module sizing](#task-module-sizing).</span><span class="sxs-lookup"><span data-stu-id="6050a-165">For more information, see [task module sizing](#task-module-sizing).</span></span> |
| `url` | <span data-ttu-id="6050a-166">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="6050a-166">string</span></span> | <span data-ttu-id="6050a-167">Esse atributo é a URL da página carregada como `<iframe>` um dentro do módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="6050a-167">This attribute is the URL of the page loaded as an `<iframe>` inside the task module.</span></span> <span data-ttu-id="6050a-168">O domínio da URL deve estar na matriz [validDomains](~/resources/schema/manifest-schema.md#validdomains) do aplicativo no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6050a-168">The URL's domain must be in the app's [validDomains array](~/resources/schema/manifest-schema.md#validdomains) in your app's manifest.</span></span> |
| `card` | <span data-ttu-id="6050a-169">Anexo de cartão de bot adaptável ou cartão adaptável</span><span class="sxs-lookup"><span data-stu-id="6050a-169">Adaptive Card or Adaptive Card bot card attachment</span></span> | <span data-ttu-id="6050a-170">Esse atributo é o JSON do Cartão Adaptável a ser exibido no módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="6050a-170">This attribute is the JSON for the Adaptive Card to appear in the task module.</span></span> <span data-ttu-id="6050a-171">Se o usuário estiver invocando de um bot, use o JSON de Cartão Adaptável em um objeto Bot `attachment` Framework.</span><span class="sxs-lookup"><span data-stu-id="6050a-171">If the user is invoking from a bot, use the Adaptive Card JSON in a Bot Framework `attachment` object.</span></span> <span data-ttu-id="6050a-172">Em uma guia, o usuário deve usar um Cartão Adaptável.</span><span class="sxs-lookup"><span data-stu-id="6050a-172">From a tab, the user must use an Adaptive Card.</span></span> <span data-ttu-id="6050a-173">Para obter mais informações, [consulte Adaptive Card or Adaptive Card bot card attachment](#adaptive-card-or-adaptive-card-bot-card-attachment)</span><span class="sxs-lookup"><span data-stu-id="6050a-173">For more information, see [Adaptive Card or Adaptive Card bot card attachment](#adaptive-card-or-adaptive-card-bot-card-attachment)</span></span> |
| `fallbackUrl` | <span data-ttu-id="6050a-174">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="6050a-174">string</span></span> | <span data-ttu-id="6050a-175">Esse atributo abre a URL em uma guia do navegador, se um cliente não dá suporte ao recurso de módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="6050a-175">This attribute opens the URL in a browser tab, if a client does not support the task module feature.</span></span> |
| `completionBotId` | <span data-ttu-id="6050a-176">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="6050a-176">string</span></span> | <span data-ttu-id="6050a-177">Este atributo especifica uma ID de aplicativo bot para enviar o resultado da interação do usuário com o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="6050a-177">This attribute specifies a bot App ID to send the result of the user's interaction with the task module.</span></span> <span data-ttu-id="6050a-178">Se especificado, o bot recebe um `task/submit invoke` evento com um objeto JSON na carga de eventos.</span><span class="sxs-lookup"><span data-stu-id="6050a-178">If specified, the bot receives a `task/submit invoke` event with a JSON object in the event payload.</span></span> |

> [!NOTE]
> <span data-ttu-id="6050a-179">O recurso de módulo de tarefa exige que os domínios de todas as URLs que você deseja carregar sejam incluídos na matriz no manifesto `validDomains` do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6050a-179">The task module feature requires that the domains of any URLs you want to load are included in the `validDomains` array in your app's manifest.</span></span>

<span data-ttu-id="6050a-180">A próxima seção especifica o tamanho do módulo de tarefas que permite ao usuário definir a altura e a largura do módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="6050a-180">The next section specifies task module sizing that enables the user to set the height and width of the task module.</span></span>

## <a name="task-module-sizing"></a><span data-ttu-id="6050a-181">Ressarção do módulo de tarefas</span><span class="sxs-lookup"><span data-stu-id="6050a-181">Task module sizing</span></span>

<span data-ttu-id="6050a-182">Usando inteiros para e , define a altura e a `TaskInfo.width` largura do módulo de tarefa em `TaskInfo.height` pixels.</span><span class="sxs-lookup"><span data-stu-id="6050a-182">Using integers for `TaskInfo.width` and `TaskInfo.height`, sets the height and width of the task module in pixels.</span></span> <span data-ttu-id="6050a-183">No entanto, dependendo do tamanho da janela e da resolução de tela da equipe, eles são reduzidos proporcionalmente, mantendo a taxa de proporção que é largura ou altura.</span><span class="sxs-lookup"><span data-stu-id="6050a-183">However, depending on the size of the Team's window and screen resolution they are reduced proportionally while maintaining the aspect ratio that is width or height.</span></span>

<span data-ttu-id="6050a-184">Se e são , ou , o tamanho do retângulo vermelho na imagem a seguir é uma proporção do espaço `TaskInfo.width` `TaskInfo.height` `"small"` `"medium"` `"large"` disponível, 20%, 50%, e 60% para e `width` 20%, 50% e 66% para `height` :</span><span class="sxs-lookup"><span data-stu-id="6050a-184">If `TaskInfo.width` and `TaskInfo.height` are `"small"`, `"medium"`, or `"large"`, the size of the red rectangle in the following image is a proportion of the available space, 20%, 50%, and 60% for `width` and 20%, 50%, and 66% for `height`:</span></span>

![Exemplo de módulo de tarefa](~/assets/images/task-module/task-module-example.png)

<span data-ttu-id="6050a-186">Os módulos de tarefa invocados de uma guia podem ser resized dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="6050a-186">Task modules invoked from a tab can be dynamically resized.</span></span> <span data-ttu-id="6050a-187">Depois de chamar, você pode chamar onde as propriedades de altura e largura no objeto newSize estão em conformidade com a especificação `tasks.startTask()` `tasks.updateTask(newSize)` TaskInfo, por exemplo `{ height: 'medium', width: 'medium' }` .</span><span class="sxs-lookup"><span data-stu-id="6050a-187">After calling `tasks.startTask()` you can call `tasks.updateTask(newSize)` where height and width properties on the newSize object conform to the TaskInfo specification, for example `{ height: 'medium', width: 'medium' }`.</span></span>

<span data-ttu-id="6050a-188">A próxima seção fornece exemplos de como incorporar módulos de tarefa em um vídeo do YouTube e um PowerApp.</span><span class="sxs-lookup"><span data-stu-id="6050a-188">The next section provides examples of embedding task modules in a YouTube video and a PowerApp.</span></span>

## <a name="task-module-css-for-html-or-javascript-task-modules"></a><span data-ttu-id="6050a-189">Módulo de tarefas CSS para módulos de tarefa HTML ou JavaScript</span><span class="sxs-lookup"><span data-stu-id="6050a-189">Task module CSS for HTML or JavaScript task modules</span></span>

<span data-ttu-id="6050a-190">Os módulos de tarefa baseados em HTML ou JavaScript têm acesso a toda a área do módulo de tarefa abaixo do header.</span><span class="sxs-lookup"><span data-stu-id="6050a-190">HTML or JavaScript-based task modules have access to the entire area of the task module below the header.</span></span> <span data-ttu-id="6050a-191">Embora isso ofereça uma grande flexibilidade, se você quiser que o preenchimento ao redor das bordas se alinhe com os elementos do header e evite barras de rolagem desnecessárias, o usuário deve fornecer o CSS correto.</span><span class="sxs-lookup"><span data-stu-id="6050a-191">While that offers a great deal of flexibility, if you want padding around the edges to align with the header elements and avoid unnecessary scroll bars, the user must provide the right CSS.</span></span> <span data-ttu-id="6050a-192">As próximas seções fornecem alguns exemplos para alguns casos de uso.</span><span class="sxs-lookup"><span data-stu-id="6050a-192">The next sections provide some examples for a few use cases.</span></span>

<span data-ttu-id="6050a-193">**Exemplo 1: vídeo do YouTube**</span><span class="sxs-lookup"><span data-stu-id="6050a-193">**Example 1: YouTube video**</span></span>

<span data-ttu-id="6050a-194">O YouTube oferece a capacidade de inserir vídeos em páginas da Web.</span><span class="sxs-lookup"><span data-stu-id="6050a-194">YouTube offers the ability to embed videos on web pages.</span></span> <span data-ttu-id="6050a-195">É fácil inserir vídeos em páginas da Web em um módulo de tarefa usando uma página da Web de stub simples.</span><span class="sxs-lookup"><span data-stu-id="6050a-195">It is easy to embed videos on web pages in a task module using a simple stub web page.</span></span>

![Vídeo do YouTube](~/assets/images/task-module/youtube-example.png)

<span data-ttu-id="6050a-197">O código a seguir fornece um exemplo do HTML para a página da Web sem o CSS:</span><span class="sxs-lookup"><span data-stu-id="6050a-197">The following code provides an example of the HTML for the web page without the CSS:</span></span>

```html
<!DOCTYPE html>
<html lang="en">
<head>
  ⋮
</head>
<body>
  <div id="embed-container">
    <iframe width="1000" height="700" src="https://www.youtube.com/embed/rd0Rd8w3FZ0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen=""></iframe>
  </div>
</body>
</html>
```

<span data-ttu-id="6050a-198">O código a seguir fornece um exemplo do CSS:</span><span class="sxs-lookup"><span data-stu-id="6050a-198">The following code provides an example of the CSS:</span></span>

```css
#embed-container iframe {
    position: absolute;
    top: 0;
    left: 0;
    width: 95%;
    height: 95%;
    padding-left: 20px;
    padding-right: 20px;
    padding-top: 10px;
    padding-bottom: 10px;
    border-style: none;
}
```

<span data-ttu-id="6050a-199">**Exemplo 2: PowerApp**</span><span class="sxs-lookup"><span data-stu-id="6050a-199">**Example 2: PowerApp**</span></span>

<span data-ttu-id="6050a-200">O usuário também pode usar a mesma abordagem para inserir um PowerApp.</span><span class="sxs-lookup"><span data-stu-id="6050a-200">The user can use the same approach to embed a PowerApp as well.</span></span> <span data-ttu-id="6050a-201">Como a altura ou a largura de qualquer PowerApp individual é personalizável, o usuário pode ajustar a altura e a largura para alcançar a apresentação desejada.</span><span class="sxs-lookup"><span data-stu-id="6050a-201">As the height or width of any individual PowerApp is customizable, the user can adjust the height and width to achieve the desired presentation.</span></span>

![PowerApp de gerenciamento de ativos](~/assets/images/task-module/powerapp-example.png)

<span data-ttu-id="6050a-203">O código a seguir fornece um exemplo do HTML para PowerApp:</span><span class="sxs-lookup"><span data-stu-id="6050a-203">The following code provides an example of the HTML for PowerApp:</span></span>

```html
<iframe width="720" height="520" src="https://web.powerapps.com/webplayer/iframeapp?source=iframe&screenColor=rgba(104,101,171,1)&appId=/providers/Microsoft.PowerApps/apps/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"></iframe>
```

<span data-ttu-id="6050a-204">O código a seguir fornece um exemplo do CSS:</span><span class="sxs-lookup"><span data-stu-id="6050a-204">The following code provides an example of the CSS:</span></span>

```css
#embed-container iframe {
    position: absolute;
    top: 0;
    left: 0;
    width: 94%;
    height: 95%;
    padding-left: 20px;
    padding-right: 20px;
    padding-top: 10px;
    padding-bottom: 10px;
    border-style: none;
}
```

<span data-ttu-id="6050a-205">A próxima seção fornece detalhes sobre como invocar seu cartão usando o cartão adaptável ou o anexo de cartão de bot adaptável.</span><span class="sxs-lookup"><span data-stu-id="6050a-205">The next section provides details on invoking your card using Adaptive Card or Adaptive Card bot card attachment.</span></span>

## <a name="adaptive-card-or-adaptive-card-bot-card-attachment"></a><span data-ttu-id="6050a-206">Anexo de cartão de bot adaptável ou cartão adaptável</span><span class="sxs-lookup"><span data-stu-id="6050a-206">Adaptive Card or Adaptive Card bot card attachment</span></span>

<span data-ttu-id="6050a-207">Dependendo de como você está invocando seu , você deve usar um Cartão Adaptável ou um anexo de cartão de bot cartão adaptável, que é um Cartão Adaptável envolvido em um `card` objeto attachment.</span><span class="sxs-lookup"><span data-stu-id="6050a-207">Depending on how you are invoking your `card`, you must use either an Adaptive Card or an Adaptive Card bot card attachment, which is an Adaptive Card wrapped in an attachment object.</span></span>

<span data-ttu-id="6050a-208">Quando você está invocando de uma guia, o usuário deve usar um Cartão Adaptável.</span><span class="sxs-lookup"><span data-stu-id="6050a-208">When you are invoking from a tab, the user must use an Adaptive Card.</span></span>

<span data-ttu-id="6050a-209">O código a seguir fornece um exemplo de um Cartão Adaptável:</span><span class="sxs-lookup"><span data-stu-id="6050a-209">The following code provides an example of an Adaptive Card:</span></span>

```json
{
    "type": "AdaptiveCard",
    "body": [
        {
            "type": "TextBlock",
            "text": "Here is a ninja cat:"
        },
        {
            "type": "Image",
            "url": "http://adaptivecards.io/content/cats/1.png",
            "size": "Medium"
        }
    ],
    "version": "1.0"
}
```

<span data-ttu-id="6050a-210">O código a seguir fornece um exemplo de um anexo de cartão de bot cartão adaptável quando você está invocando de um bot:</span><span class="sxs-lookup"><span data-stu-id="6050a-210">The following code provides an example of an Adaptive Card bot card attachment when you are invoking from a bot:</span></span>

```json
{
    "contentType": "application/vnd.microsoft.card.adaptive",
    "content": {
        "type": "AdaptiveCard",
        "body": [
            {
                "type": "TextBlock",
                "text": "Here is a ninja cat:"
            },
            {
                "type": "Image",
                "url": "http://adaptivecards.io/content/cats/1.png",
                "size": "Medium"
            }
        ],
        "version": "1.0"
    }
}
```

<span data-ttu-id="6050a-211">A próxima seção fornece detalhes sobre a sintaxe de link profundo do módulo de tarefas, incluindo o `TaskInfo` objeto `APP_ID` e `BOT_APP_ID` .</span><span class="sxs-lookup"><span data-stu-id="6050a-211">The next section provides details on task module deep link syntax including the `TaskInfo` object and `APP_ID` and `BOT_APP_ID`.</span></span>

## <a name="task-module-deep-link-syntax"></a><span data-ttu-id="6050a-212">Sintaxe de link profundo do módulo de tarefas</span><span class="sxs-lookup"><span data-stu-id="6050a-212">Task module deep link syntax</span></span>

<span data-ttu-id="6050a-213">Um link profundo do módulo de tarefas é uma serialização do objeto TaskInfo com os dois outros detalhes a seguir e, `APP_ID` opcionalmente, `BOT_APP_ID` o :</span><span class="sxs-lookup"><span data-stu-id="6050a-213">A task module deep link is a serialization of the TaskInfo object with the following two other details, `APP_ID` and optionally the `BOT_APP_ID`:</span></span>

`https://teams.microsoft.com/l/task/APP_ID?url=<TaskInfo.url>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID`

`https://teams.microsoft.com/l/task/APP_ID?card=<TaskInfo.card>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID`

<span data-ttu-id="6050a-214">Para os tipos de dados e os valores de autorização `<TaskInfo.url>` para , , , e , consulte o objeto `<TaskInfo.card>` `<TaskInfo.height>` `<TaskInfo.width>` `<TaskInfo.title>` [TaskInfo](#the-taskinfo-object).</span><span class="sxs-lookup"><span data-stu-id="6050a-214">For the data types and allowable values for `<TaskInfo.url>`, `<TaskInfo.card>`, `<TaskInfo.height>`, `<TaskInfo.width>`, and `<TaskInfo.title>`, see [TaskInfo object](#the-taskinfo-object).</span></span>

> [!TIP]
> <span data-ttu-id="6050a-215">A URL codifica o link profundo ao usar o `card` parâmetro, por [ `encodeURI()` ](https://www.w3schools.com/jsref/jsref_encodeURI.asp)exemplo, a função de JavaScript.</span><span class="sxs-lookup"><span data-stu-id="6050a-215">URL encode the deep link when using the `card` parameter, for example, JavaScript's [`encodeURI()` function](https://www.w3schools.com/jsref/jsref_encodeURI.asp).</span></span>

<span data-ttu-id="6050a-216">A tabela a seguir fornece informações sobre `APP_ID` e `BOT_APP_ID` :</span><span class="sxs-lookup"><span data-stu-id="6050a-216">The following table provides information on `APP_ID` and `BOT_APP_ID`:</span></span>

| <span data-ttu-id="6050a-217">Valor</span><span class="sxs-lookup"><span data-stu-id="6050a-217">Value</span></span> | <span data-ttu-id="6050a-218">Tipo</span><span class="sxs-lookup"><span data-stu-id="6050a-218">Type</span></span> | <span data-ttu-id="6050a-219">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="6050a-219">Required</span></span> | <span data-ttu-id="6050a-220">Descrição</span><span class="sxs-lookup"><span data-stu-id="6050a-220">Description</span></span> |
| --- | --- | --- | --- |
| `APP_ID` | <span data-ttu-id="6050a-221">string</span><span class="sxs-lookup"><span data-stu-id="6050a-221">string</span></span> | <span data-ttu-id="6050a-222">Sim</span><span class="sxs-lookup"><span data-stu-id="6050a-222">Yes</span></span> | <span data-ttu-id="6050a-223">A [ID](~/resources/schema/manifest-schema.md#id) do aplicativo invocando o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="6050a-223">The [ID](~/resources/schema/manifest-schema.md#id) of the app invoking the task module.</span></span> <span data-ttu-id="6050a-224">A [matriz validDomains](~/resources/schema/manifest-schema.md#validdomains) no manifesto deve `APP_ID` conter o domínio para se estiver na `url` `url` URL.</span><span class="sxs-lookup"><span data-stu-id="6050a-224">The [validDomains array](~/resources/schema/manifest-schema.md#validdomains) in the manifest for `APP_ID` must contain the domain for `url` if `url` is in the URL.</span></span> <span data-ttu-id="6050a-225">A ID do aplicativo já é conhecida quando um módulo de tarefa é invocado de uma guia ou um bot, por isso ele não está incluído em `TaskInfo` .</span><span class="sxs-lookup"><span data-stu-id="6050a-225">The app ID is already known when a task module is invoked from a tab or a bot, which is why it is not included in `TaskInfo`.</span></span> |
| `BOT_APP_ID` | <span data-ttu-id="6050a-226">string</span><span class="sxs-lookup"><span data-stu-id="6050a-226">string</span></span> | <span data-ttu-id="6050a-227">Não</span><span class="sxs-lookup"><span data-stu-id="6050a-227">No</span></span> | <span data-ttu-id="6050a-228">Se um valor `completionBotId` for especificado, o `result` objeto será enviado usando uma mensagem para o bot `task/submit invoke` especificado.</span><span class="sxs-lookup"><span data-stu-id="6050a-228">If a value for `completionBotId` is specified, the `result` object is sent using a `task/submit invoke` message to the specified bot.</span></span> <span data-ttu-id="6050a-229">`BOT_APP_ID` deve ser especificado como um bot no manifesto do aplicativo, ou seja, você não pode enviá-lo para qualquer bot.</span><span class="sxs-lookup"><span data-stu-id="6050a-229">`BOT_APP_ID` must be specified as a bot in the app's manifest, that is you cannot send it to any bot.</span></span> |

> [!NOTE]
> <span data-ttu-id="6050a-230">`APP_ID` e pode ser o mesmo em muitos casos, se um aplicativo tiver um bot recomendado para usar como ID de um aplicativo se `BOT_APP_ID` houver um.</span><span class="sxs-lookup"><span data-stu-id="6050a-230">`APP_ID` and `BOT_APP_ID` can be the same in many cases, if an app has a recommended bot to use as an app's ID if there is one.</span></span>

<span data-ttu-id="6050a-231">A próxima seção fornece detalhes sobre como usar um teclado com o módulo de tarefas do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6050a-231">The next section provides details on using a keyboard with your app's task module.</span></span>

## <a name="keyboard-and-accessibility-guidelines"></a><span data-ttu-id="6050a-232">Diretrizes de teclado e acessibilidade</span><span class="sxs-lookup"><span data-stu-id="6050a-232">Keyboard and accessibility guidelines</span></span>

<span data-ttu-id="6050a-233">Com módulos de tarefa baseados em HTML ou JavaScript, você deve garantir que o módulo de tarefas do aplicativo possa ser usado com um teclado.</span><span class="sxs-lookup"><span data-stu-id="6050a-233">With HTML or JavaScript-based task modules, you must ensure your app's task module can be used with a keyboard.</span></span> <span data-ttu-id="6050a-234">Os programas de leitor de tela também dependem da capacidade de navegar usando o teclado.</span><span class="sxs-lookup"><span data-stu-id="6050a-234">Screen reader programs also depend on the ability to navigate using the keyboard.</span></span> <span data-ttu-id="6050a-235">Isso inclui as duas coisas a seguir:</span><span class="sxs-lookup"><span data-stu-id="6050a-235">This includes the following two things:</span></span>

* <span data-ttu-id="6050a-236">Usando o [atributo tabindex](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/tabindex) em suas marcas HTML para controlar quais elementos podem ser focalizados.</span><span class="sxs-lookup"><span data-stu-id="6050a-236">Using the [tabindex attribute](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/tabindex) in your HTML tags to control which elements can be focused.</span></span> <span data-ttu-id="6050a-237">Além disso, use o atributo tabindex para identificar onde ele participa da navegação sequencial do teclado geralmente com as teclas <kbd>Tab</kbd> e <kbd>Shift-Tab.</kbd></span><span class="sxs-lookup"><span data-stu-id="6050a-237">Also, use tabindex attribute to identify where it participates in sequential keyboard navigation usually with the <kbd>Tab</kbd> and <kbd>Shift-Tab</kbd> keys.</span></span>
* <span data-ttu-id="6050a-238">Manipulando <kbd>a chave Esc</kbd> no JavaScript para o módulo de tarefas.</span><span class="sxs-lookup"><span data-stu-id="6050a-238">Handling the <kbd>Esc</kbd> key in the JavaScript for your task module.</span></span> <span data-ttu-id="6050a-239">O código a seguir fornece um exemplo de como manipular a <kbd>chave Esc:</kbd></span><span class="sxs-lookup"><span data-stu-id="6050a-239">The following code provides an example of how to handle the <kbd>Esc</kbd> key:</span></span>

    ```javascript
    // Handle the Esc key
    document.onkeyup = function(event) {
    if ((event.key === 27) || (event.key === "Escape")) {
      microsoftTeams.submitTask(null); // this will return an err object to the completionHandler()
      }
    }
    ```

<span data-ttu-id="6050a-240">Microsoft Teams garante que a navegação do teclado funcione corretamente do header do módulo de tarefas para o HTML e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="6050a-240">Microsoft Teams ensures that keyboard navigation works properly from the task module header into your HTML and vice-versa.</span></span>

## <a name="code-sample"></a><span data-ttu-id="6050a-241">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="6050a-241">Code sample</span></span>

|<span data-ttu-id="6050a-242">Exemplo de nome</span><span class="sxs-lookup"><span data-stu-id="6050a-242">Sample name</span></span> | <span data-ttu-id="6050a-243">Descrição</span><span class="sxs-lookup"><span data-stu-id="6050a-243">Description</span></span> | <span data-ttu-id="6050a-244">.NET</span><span class="sxs-lookup"><span data-stu-id="6050a-244">.NET</span></span> | <span data-ttu-id="6050a-245">Node.js</span><span class="sxs-lookup"><span data-stu-id="6050a-245">Node.js</span></span>|
|----------------|-----------------|--------------|----------------|
|<span data-ttu-id="6050a-246">Exemplo de módulo de tarefa bots-V4</span><span class="sxs-lookup"><span data-stu-id="6050a-246">Task module sample bots-V4</span></span> | <span data-ttu-id="6050a-247">Exemplos para a criação de módulos de tarefa.</span><span class="sxs-lookup"><span data-stu-id="6050a-247">Samples for creating task modules.</span></span> |[<span data-ttu-id="6050a-248">View</span><span class="sxs-lookup"><span data-stu-id="6050a-248">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/54.teams-task-module)|[<span data-ttu-id="6050a-249">View</span><span class="sxs-lookup"><span data-stu-id="6050a-249">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/54.teams-task-module)|
|<span data-ttu-id="6050a-250">Guias de exemplo de módulo de tarefa e bots-V3</span><span class="sxs-lookup"><span data-stu-id="6050a-250">Task module sample tabs and bots-V3</span></span> | <span data-ttu-id="6050a-251">Exemplos para a criação de módulos de tarefa.</span><span class="sxs-lookup"><span data-stu-id="6050a-251">Samples for creating task modules.</span></span> |[<span data-ttu-id="6050a-252">View</span><span class="sxs-lookup"><span data-stu-id="6050a-252">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/csharp)|[<span data-ttu-id="6050a-253">View</span><span class="sxs-lookup"><span data-stu-id="6050a-253">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/nodejs)| 

## <a name="see-also"></a><span data-ttu-id="6050a-254">Também consulte</span><span class="sxs-lookup"><span data-stu-id="6050a-254">See also</span></span>

* [<span data-ttu-id="6050a-255">Solicitar permissões do dispositivo</span><span class="sxs-lookup"><span data-stu-id="6050a-255">Request device permissions</span></span>](~/concepts/device-capabilities/native-device-permissions.md)
* [<span data-ttu-id="6050a-256">Integrar recursos de mídia</span><span class="sxs-lookup"><span data-stu-id="6050a-256">Integrate media capabilities</span></span>](~/concepts/device-capabilities/mobile-camera-image-permissions.md)
* [<span data-ttu-id="6050a-257">Integrar a QR ou o recurso de scanner de código de barras Teams</span><span class="sxs-lookup"><span data-stu-id="6050a-257">Integrate QR or barcode scanner capability in Teams</span></span>](~/concepts/device-capabilities/qr-barcode-scanner-capability.md)
* [<span data-ttu-id="6050a-258">Integrar recursos de localização Teams</span><span class="sxs-lookup"><span data-stu-id="6050a-258">Integrate location capabilities in Teams</span></span>](~/concepts/device-capabilities/location-capability.md)

## <a name="next-step"></a><span data-ttu-id="6050a-259">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="6050a-259">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6050a-260">Usar módulos de tarefa em guias</span><span class="sxs-lookup"><span data-stu-id="6050a-260">Use task modules in tabs</span></span>](~/task-modules-and-cards/task-modules/task-modules-tabs.md)