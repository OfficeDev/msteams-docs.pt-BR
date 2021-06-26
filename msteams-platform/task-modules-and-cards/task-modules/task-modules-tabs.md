---
title: Usar Módulos de Tarefa em Microsoft Teams guias
description: Explica como invocar módulos de tarefas Teams guias usando o SDK Microsoft Teams cliente.
localization_priority: Normal
ms.topic: how-to
keywords: task modules teams tabs client sdk
ms.openlocfilehash: 8afd2c93261f28aa7ced4c98d29be27dca35f8b1
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140548"
---
# <a name="use-task-modules-in-tabs"></a><span data-ttu-id="a23cc-104">Usar módulos de tarefa em guias</span><span class="sxs-lookup"><span data-stu-id="a23cc-104">Use task modules in tabs</span></span>

<span data-ttu-id="a23cc-105">Adicione um módulo de tarefa à sua guia para simplificar a experiência do usuário para todos os fluxos de trabalho que exigem entrada de dados.</span><span class="sxs-lookup"><span data-stu-id="a23cc-105">Add a task module to your tab to simplify your user's experience for any workflows that require data input.</span></span> <span data-ttu-id="a23cc-106">Os módulos de tarefas permitem que você reúna suas entradas em um pop-up Teams-Aware Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a23cc-106">Task modules allow you to gather their input in a Microsoft Teams-Aware pop-up.</span></span> <span data-ttu-id="a23cc-107">Um bom exemplo disso é editar cartões do Planner.</span><span class="sxs-lookup"><span data-stu-id="a23cc-107">A good example of this is editing Planner cards.</span></span> <span data-ttu-id="a23cc-108">Você pode usar módulos de tarefa para criar uma experiência semelhante.</span><span class="sxs-lookup"><span data-stu-id="a23cc-108">You can use task modules to create a similar experience.</span></span>

<span data-ttu-id="a23cc-109">Para dar suporte ao recurso de módulo de tarefa, duas novas funções são adicionadas [ao SDK do](/javascript/api/overview/msteams-client)cliente Teams cliente .</span><span class="sxs-lookup"><span data-stu-id="a23cc-109">To support the task module feature, two new functions are added to the [Teams client SDK](/javascript/api/overview/msteams-client).</span></span> <span data-ttu-id="a23cc-110">O código a seguir mostra um exemplo dessas duas funções:</span><span class="sxs-lookup"><span data-stu-id="a23cc-110">The following code shows an example of these two functions:</span></span>

```typescript
microsoftTeams.tasks.startTask(
    taskInfo: TaskInfo,
    submitHandler?: (err: string, result: string | any) => void
): void;

microsoftTeams.tasks.submitTask(
    result?: string | any,
    appIds?: string | string[]
): void;
```

<span data-ttu-id="a23cc-111">Você pode ver como invocar um módulo de tarefa de uma guia e enviar o resultado de um módulo de tarefa funciona.</span><span class="sxs-lookup"><span data-stu-id="a23cc-111">You can see how invoking a task module from a tab and submitting the result of a task module works.</span></span>

## <a name="invoke-a-task-module-from-a-tab"></a><span data-ttu-id="a23cc-112">Invocar um módulo de tarefa de uma guia</span><span class="sxs-lookup"><span data-stu-id="a23cc-112">Invoke a task module from a tab</span></span>

<span data-ttu-id="a23cc-113">Para invocar um módulo de tarefa de uma guia, use `microsoftTeams.tasks.startTask()` passar um [objeto TaskInfo](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object) e uma função `submitHandler` de retorno de chamada opcional.</span><span class="sxs-lookup"><span data-stu-id="a23cc-113">To invoke a task module from a tab use `microsoftTeams.tasks.startTask()` passing a [TaskInfo object](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object) and an optional `submitHandler` callback function.</span></span> <span data-ttu-id="a23cc-114">Há dois casos a considerar:</span><span class="sxs-lookup"><span data-stu-id="a23cc-114">There are two cases to consider:</span></span>

* <span data-ttu-id="a23cc-115">O valor de `TaskInfo.url` é definido como uma URL.</span><span class="sxs-lookup"><span data-stu-id="a23cc-115">The value of `TaskInfo.url` is set to a URL.</span></span> <span data-ttu-id="a23cc-116">A janela do módulo de tarefas é exibida `TaskModule.url` e carregada como uma dentro `<iframe>` dela.</span><span class="sxs-lookup"><span data-stu-id="a23cc-116">The task module window appears and `TaskModule.url` is loaded as an `<iframe>` inside it.</span></span> <span data-ttu-id="a23cc-117">JavaScript nessa página chama `microsoftTeams.initialize()` .</span><span class="sxs-lookup"><span data-stu-id="a23cc-117">JavaScript on that page calls `microsoftTeams.initialize()`.</span></span> <span data-ttu-id="a23cc-118">Se houver uma função na página e houver um erro ao invocar , será invocado com definido como a cadeia de caracteres de erro indicando `submitHandler` `microsoftTeams.tasks.startTask()` o `submitHandler` `err` mesmo.</span><span class="sxs-lookup"><span data-stu-id="a23cc-118">If there is a `submitHandler` function on the page and there is an error when invoking `microsoftTeams.tasks.startTask()`, then `submitHandler` is invoked with `err` set to the error string indicating the same.</span></span> <span data-ttu-id="a23cc-119">Para obter mais informações, consulte [erros de invocação do módulo de tarefas](#task-module-invocation-errors).</span><span class="sxs-lookup"><span data-stu-id="a23cc-119">For more information, see [task module invocation errors](#task-module-invocation-errors).</span></span>
* <span data-ttu-id="a23cc-120">O valor de `taskInfo.card` é [json para um Cartão Adaptável.](~/task-modules-and-cards/task-modules/invoking-task-modules.md#adaptive-card-or-adaptive-card-bot-card-attachment)</span><span class="sxs-lookup"><span data-stu-id="a23cc-120">The value of `taskInfo.card` is the [JSON for an Adaptive Card](~/task-modules-and-cards/task-modules/invoking-task-modules.md#adaptive-card-or-adaptive-card-bot-card-attachment).</span></span> <span data-ttu-id="a23cc-121">Não há nenhuma função JavaScript a ser chamada quando o usuário fecha ou pressiona um `submitHandler` botão no Cartão Adaptável.</span><span class="sxs-lookup"><span data-stu-id="a23cc-121">There is no JavaScript `submitHandler` function to call when the user closes or presses a button on the Adaptive Card.</span></span> <span data-ttu-id="a23cc-122">A única maneira de receber o que o usuário entrou é passando o resultado para um bot.</span><span class="sxs-lookup"><span data-stu-id="a23cc-122">The only way to receive what the user entered is by passing the result to a bot.</span></span> <span data-ttu-id="a23cc-123">Para usar um módulo de tarefa cartão adaptável de uma guia, seu aplicativo deve incluir um bot para obter qualquer resposta do usuário.</span><span class="sxs-lookup"><span data-stu-id="a23cc-123">To use an Adaptive Card task module from a tab, your app must include a bot to get any response from the user.</span></span>

<span data-ttu-id="a23cc-124">A próxima seção fornece um exemplo de invocação de um módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="a23cc-124">The next section gives an example of invoking a task module.</span></span>

## <a name="example-of-invoking-a-task-module"></a><span data-ttu-id="a23cc-125">Exemplo de invocação de um módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="a23cc-125">Example of invoking a task module</span></span>

<span data-ttu-id="a23cc-126">A imagem a seguir exibe o módulo de tarefa:</span><span class="sxs-lookup"><span data-stu-id="a23cc-126">The following image displays the task module:</span></span>

![Módulo de Tarefa - Formulário Personalizado](~/assets/images/task-module/task-module-custom-form.png)

<span data-ttu-id="a23cc-128">O código a seguir é adaptado do [exemplo do módulo de tarefas](~/task-modules-and-cards/task-modules/invoking-task-modules.md#code-sample):</span><span class="sxs-lookup"><span data-stu-id="a23cc-128">The following code is adapted from [the task module sample](~/task-modules-and-cards/task-modules/invoking-task-modules.md#code-sample):</span></span>

```javascript
let taskInfo = {
    title: null,
    height: null,
    width: null,
    url: null,
    card: null,
    fallbackUrl: null,
    completionBotId: null,
};

taskInfo.url = "https://contoso.com/teamsapp/customform";
taskInfo.title = "Custom Form";
taskInfo.height = 510;
taskInfo.width = 430;
submitHandler = (err, result) => {
    console.log(`Submit handler - err: ${err}`);
    console.log(`Submit handler - result\rName: ${result.name}\rEmail: ${result.email}\rFavorite book: ${result.favoriteBook}`);
};
microsoftTeams.tasks.startTask(taskInfo, submitHandler);
```

<span data-ttu-id="a23cc-129">O `submitHandler` é muito simples e ecoa o valor de ou para o `err` `result` console.</span><span class="sxs-lookup"><span data-stu-id="a23cc-129">The `submitHandler` is very simple and it echoes the value of `err` or `result` to the console.</span></span>

## <a name="submit-the-result-of-a-task-module"></a><span data-ttu-id="a23cc-130">Enviar o resultado de um módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="a23cc-130">Submit the result of a task module</span></span>

<span data-ttu-id="a23cc-131">A `submitHandler` função reside na página da Web e é usada com `TaskInfo.url` `TaskInfo.url` .</span><span class="sxs-lookup"><span data-stu-id="a23cc-131">The `submitHandler` function resides in the `TaskInfo.url` web page and is used with `TaskInfo.url`.</span></span> <span data-ttu-id="a23cc-132">Se houver um erro ao invocar o módulo de tarefa, sua função será imediatamente invocada com uma cadeia de caracteres indicando `submitHandler` `err` que erro [ocorreu](#task-module-invocation-errors).</span><span class="sxs-lookup"><span data-stu-id="a23cc-132">If there is an error when invoking the task module, your `submitHandler` function is immediately invoked with an `err` string indicating what [error occurred](#task-module-invocation-errors).</span></span> <span data-ttu-id="a23cc-133">A função também é chamada com uma cadeia de caracteres quando o usuário seleciona X no canto superior direito do módulo `submitHandler` de tarefa para o `err` fechar.</span><span class="sxs-lookup"><span data-stu-id="a23cc-133">The `submitHandler` function is also called with an `err` string when the user selects X at the upper right of the task module to close it.</span></span>

<span data-ttu-id="a23cc-134">Se não houver nenhum erro de invocação e o usuário não selecionar X para descartá-lo, o usuário escolherá um botão quando terminar.</span><span class="sxs-lookup"><span data-stu-id="a23cc-134">If there is no invocation error and the user does not select X to dismiss it, the user chooses a button when finished.</span></span> <span data-ttu-id="a23cc-135">Dependendo se é uma URL ou um Cartão Adaptável no módulo de tarefas, as próximas seções fornecem detalhes sobre o que ocorre.</span><span class="sxs-lookup"><span data-stu-id="a23cc-135">Depending on whether it is a URL or an Adaptive Card in the task module, the next sections provide details on what occurs.</span></span>

### <a name="html-or-javascript-taskinfourl"></a><span data-ttu-id="a23cc-136">HTML ou JavaScript `TaskInfo.url`</span><span class="sxs-lookup"><span data-stu-id="a23cc-136">HTML or JavaScript `TaskInfo.url`</span></span>

<span data-ttu-id="a23cc-137">Depois de validar as entradas do usuário, chame a `microsoftTeams.tasks.submitTask()` função SDK conhecida como `submitTask()` .</span><span class="sxs-lookup"><span data-stu-id="a23cc-137">After validating the user's inputs, call the `microsoftTeams.tasks.submitTask()` SDK function referred to as `submitTask()`.</span></span> <span data-ttu-id="a23cc-138">Chame sem parâmetros se você quiser apenas `submitTask()` Teams fechar o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="a23cc-138">Call `submitTask()` without any parameters if you just want Teams to close the task module.</span></span> <span data-ttu-id="a23cc-139">Você pode passar um objeto ou uma cadeia de caracteres para seu `submitHandler` .</span><span class="sxs-lookup"><span data-stu-id="a23cc-139">You can pass an object or a string to your `submitHandler`.</span></span>

<span data-ttu-id="a23cc-140">Passe o resultado como o primeiro parâmetro.</span><span class="sxs-lookup"><span data-stu-id="a23cc-140">Pass your result as the first parameter.</span></span> <span data-ttu-id="a23cc-141">Teams invoca onde `submitHandler` `err` está `null` e é o objeto `result` ou cadeia de caracteres que você passou para `submitTask()` .</span><span class="sxs-lookup"><span data-stu-id="a23cc-141">Teams invokes `submitHandler` where `err` is `null` and `result` is the object or string you passed to `submitTask()`.</span></span> <span data-ttu-id="a23cc-142">Se você chamar `submitTask()` com um `result` parâmetro, deverá passar uma ou uma `appId` matriz de `appId` cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a23cc-142">If you call `submitTask()` with a `result` parameter, you must pass an `appId` or an array of `appId` strings.</span></span> <span data-ttu-id="a23cc-143">Isso permite Teams validar se o aplicativo que envia o resultado é igual ao módulo de tarefa invocado.</span><span class="sxs-lookup"><span data-stu-id="a23cc-143">This permits Teams to validate that the app sending the result is same as the invoked task module.</span></span>

### <a name="adaptive-card-taskinfocard"></a><span data-ttu-id="a23cc-144">Cartão Adaptável `TaskInfo.card`</span><span class="sxs-lookup"><span data-stu-id="a23cc-144">Adaptive Card `TaskInfo.card`</span></span>

<span data-ttu-id="a23cc-145">Quando você invoca o módulo de tarefa com um e o usuário seleciona um botão, os valores no cartão são retornados como `submitHandler` `Action.Submit` o valor de `result` .</span><span class="sxs-lookup"><span data-stu-id="a23cc-145">When you invoke the task module with a `submitHandler` and the user selects an `Action.Submit` button, the values in the card are returned as the value of `result`.</span></span> <span data-ttu-id="a23cc-146">Se o usuário selecionar a tecla Esc ou X na parte superior direita, `err` será retornado em vez disso.</span><span class="sxs-lookup"><span data-stu-id="a23cc-146">If the user selects the Esc key or X at the top right, `err` is returned instead.</span></span> <span data-ttu-id="a23cc-147">Se seu aplicativo contiver um bot além de uma guia, você pode simplesmente incluir o bot como o `appId` `completionBotId` valor do `TaskInfo` objeto.</span><span class="sxs-lookup"><span data-stu-id="a23cc-147">If your app contains a bot in addition to a tab, you can simply include the `appId` of the bot as the value of `completionBotId` in the `TaskInfo` object.</span></span> <span data-ttu-id="a23cc-148">O corpo do Cartão Adaptável conforme preenchido pelo usuário é enviado para o bot usando uma mensagem quando o usuário `task/submit invoke` seleciona um `Action.Submit` botão.</span><span class="sxs-lookup"><span data-stu-id="a23cc-148">The Adaptive Card body as filled in by the user is sent to the bot using a `task/submit invoke` message when the user selects an `Action.Submit` button.</span></span> <span data-ttu-id="a23cc-149">O esquema do objeto que você recebe é muito semelhante ao esquema recebido para [tarefas/buscas e mensagens de tarefa/envio.](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages)</span><span class="sxs-lookup"><span data-stu-id="a23cc-149">The schema for the object you receive is very similar to [the schema you receive for task/fetch and task/submit messages](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages).</span></span> <span data-ttu-id="a23cc-150">A única diferença é que o esquema do objeto JSON é um objeto Cartão Adaptável em vez de um objeto que contém um objeto Card Adaptável como quando cartões adaptáveis são usados com [bots](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages).</span><span class="sxs-lookup"><span data-stu-id="a23cc-150">The only difference is that the schema of the JSON object is an Adaptive Card object as opposed to an object containing an Adaptive Card object as [when Adaptive cards are used with bots](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages).</span></span>

<span data-ttu-id="a23cc-151">A próxima seção fornece um exemplo de envio do resultado de um módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="a23cc-151">The next section gives an example of submitting the result of a task module.</span></span>

## <a name="example-of-submitting-the-result-of-a-task-module"></a><span data-ttu-id="a23cc-152">Exemplo de envio do resultado de um módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="a23cc-152">Example of submitting the result of a task module</span></span>

<span data-ttu-id="a23cc-153">Para obter mais informações, consulte o [formulário HTML no módulo de tarefa](#example-of-invoking-a-task-module).</span><span class="sxs-lookup"><span data-stu-id="a23cc-153">For more information, see the [HTML form in the task module](#example-of-invoking-a-task-module).</span></span> <span data-ttu-id="a23cc-154">O código a seguir fornece um exemplo de onde o formulário é definido:</span><span class="sxs-lookup"><span data-stu-id="a23cc-154">The following code gives an example of where the form is defined:</span></span>

```html
<form method="POST" id="customerForm" action="/register" onSubmit="return validateForm()">
```

<span data-ttu-id="a23cc-155">Há cinco campos neste formulário, mas, para este exemplo, apenas três valores são `name` necessários, `email` , e `favoriteBook` .</span><span class="sxs-lookup"><span data-stu-id="a23cc-155">There are five fields on this form but for this example only three values are required, `name`, `email`, and `favoriteBook`.</span></span>

<span data-ttu-id="a23cc-156">O código a seguir fornece um exemplo da `validateForm()` função que chama `submitTask()` :</span><span class="sxs-lookup"><span data-stu-id="a23cc-156">The following code gives an example of the `validateForm()` function that calls `submitTask()`:</span></span>

```javascript
function validateForm() {
    var customerInfo = {
        name: document.forms["customerForm"]["name"].value,
        email: document.forms["customerForm"]["email"].value,
        favoriteBook: document.forms["customerForm"]["favoriteBook"].value
    }
    microsoftTeams.tasks.submitTask(customerInfo, "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx");
    return true;
}
```

<span data-ttu-id="a23cc-157">A próxima seção fornece problemas de invocação do módulo de tarefas e suas mensagens de erro.</span><span class="sxs-lookup"><span data-stu-id="a23cc-157">The next section provides task module invocation problems and their error messages.</span></span>

## <a name="task-module-invocation-errors"></a><span data-ttu-id="a23cc-158">Erros de invocação do módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="a23cc-158">Task module invocation errors</span></span>

<span data-ttu-id="a23cc-159">A tabela a seguir fornece os valores possíveis `err` que podem ser recebidos por seu `submitHandler` :</span><span class="sxs-lookup"><span data-stu-id="a23cc-159">The following table provides the possible values of `err` that can be received by your `submitHandler`:</span></span>

| <span data-ttu-id="a23cc-160">Problema</span><span class="sxs-lookup"><span data-stu-id="a23cc-160">Problem</span></span> | <span data-ttu-id="a23cc-161">Mensagem de erro que é o valor de `err`</span><span class="sxs-lookup"><span data-stu-id="a23cc-161">Error message that is value of `err`</span></span> |
| ------- | ------------------------------ |
| <span data-ttu-id="a23cc-162">Valores para ambos `TaskInfo.url` `TaskInfo.card` e foram especificados.</span><span class="sxs-lookup"><span data-stu-id="a23cc-162">Values for both `TaskInfo.url` and `TaskInfo.card` were specified.</span></span> | <span data-ttu-id="a23cc-163">Os valores para cartão e URL foram especificados.</span><span class="sxs-lookup"><span data-stu-id="a23cc-163">Values for both card and URL were specified.</span></span> <span data-ttu-id="a23cc-164">Um ou outro, mas não ambos, são permitidos.</span><span class="sxs-lookup"><span data-stu-id="a23cc-164">One or the other, but not both, are allowed.</span></span> |
| <span data-ttu-id="a23cc-165">Nem `TaskInfo.url` `TaskInfo.card` especificado.</span><span class="sxs-lookup"><span data-stu-id="a23cc-165">Neither `TaskInfo.url` nor `TaskInfo.card` specified.</span></span> | <span data-ttu-id="a23cc-166">Você deve especificar um valor para cartão ou URL.</span><span class="sxs-lookup"><span data-stu-id="a23cc-166">You must specify a value for either card or URL.</span></span> |
| <span data-ttu-id="a23cc-167">Inválido `appId` .</span><span class="sxs-lookup"><span data-stu-id="a23cc-167">Invalid `appId`.</span></span> | <span data-ttu-id="a23cc-168">ID de aplicativo inválida.</span><span class="sxs-lookup"><span data-stu-id="a23cc-168">Invalid app ID.</span></span> |
| <span data-ttu-id="a23cc-169">Botão X selecionado pelo usuário, fechando-o.</span><span class="sxs-lookup"><span data-stu-id="a23cc-169">User selected X button, closing it.</span></span> | <span data-ttu-id="a23cc-170">O usuário cancelou ou fechou o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="a23cc-170">User cancelled or closed the task module.</span></span> |

## <a name="code-sample"></a><span data-ttu-id="a23cc-171">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="a23cc-171">Code sample</span></span>

|<span data-ttu-id="a23cc-172">Exemplo de nome</span><span class="sxs-lookup"><span data-stu-id="a23cc-172">Sample name</span></span> | <span data-ttu-id="a23cc-173">Descrição</span><span class="sxs-lookup"><span data-stu-id="a23cc-173">Description</span></span> | <span data-ttu-id="a23cc-174">.NET</span><span class="sxs-lookup"><span data-stu-id="a23cc-174">.NET</span></span> | <span data-ttu-id="a23cc-175">Node.js</span><span class="sxs-lookup"><span data-stu-id="a23cc-175">Node.js</span></span>|
|----------------|-----------------|--------------|----------------|
|<span data-ttu-id="a23cc-176">Guias de exemplo de módulo de tarefa e bots-V3</span><span class="sxs-lookup"><span data-stu-id="a23cc-176">Task module sample tabs and bots-V3</span></span> | <span data-ttu-id="a23cc-177">Exemplos para a criação de módulos de tarefa.</span><span class="sxs-lookup"><span data-stu-id="a23cc-177">Samples for creating task modules.</span></span> |[<span data-ttu-id="a23cc-178">View</span><span class="sxs-lookup"><span data-stu-id="a23cc-178">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/csharp)|[<span data-ttu-id="a23cc-179">View</span><span class="sxs-lookup"><span data-stu-id="a23cc-179">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/nodejs)| 

## <a name="see-also"></a><span data-ttu-id="a23cc-180">Também consulte</span><span class="sxs-lookup"><span data-stu-id="a23cc-180">See also</span></span>

[<span data-ttu-id="a23cc-181">Invocar e descartar módulos de tarefa</span><span class="sxs-lookup"><span data-stu-id="a23cc-181">Invoke and dismiss task modules</span></span>](~/task-modules-and-cards/task-modules/invoking-task-modules.md)

## <a name="next-step"></a><span data-ttu-id="a23cc-182">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="a23cc-182">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a23cc-183">Usando módulos de tarefas de bots</span><span class="sxs-lookup"><span data-stu-id="a23cc-183">Using task modules from bots</span></span>](~/task-modules-and-cards/task-modules/task-modules-bots.md)
