---
title: Usando módulos de tarefa em Microsoft Teams guias
description: Explica como invocar módulos de tarefas Teams guias usando o SDK do cliente Microsoft Teams cliente
localization_priority: Normal
ms.topic: how-to
keywords: task modules teams tabs client sdk
ms.openlocfilehash: 5e85fd0662b8a15d6b98d9c2d2dfa5137b05fa39
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019521"
---
# <a name="using-task-modules-in-tabs"></a><span data-ttu-id="c2f8d-104">Usando módulos de tarefas em guias</span><span class="sxs-lookup"><span data-stu-id="c2f8d-104">Using task modules in tabs</span></span>

<span data-ttu-id="c2f8d-105">Adicionar um módulo de tarefa à sua guia pode simplificar muito a experiência do usuário para todos os fluxos de trabalho que exigem entrada de dados.</span><span class="sxs-lookup"><span data-stu-id="c2f8d-105">Adding a task module to your tab can greatly simplify your user's experience for any workflows that require data input.</span></span> <span data-ttu-id="c2f8d-106">Os módulos de tarefa permitem coletar suas entradas em um pop-up Teams com conhecimento de Teams.</span><span class="sxs-lookup"><span data-stu-id="c2f8d-106">Task modules allow you to gather their input in a Teams-aware popup.</span></span> <span data-ttu-id="c2f8d-107">Um bom exemplo disso é editar cartões do Planner; você pode usar módulos de tarefa para criar uma experiência semelhante.</span><span class="sxs-lookup"><span data-stu-id="c2f8d-107">A good example of this is editing Planner cards; you can use task modules to create a similar experience.</span></span>

<span data-ttu-id="c2f8d-108">Para dar suporte ao recurso de módulo de tarefa, duas novas funções foram adicionadas [ao SDK do](/javascript/api/overview/msteams-client)cliente Microsoft Teams :</span><span class="sxs-lookup"><span data-stu-id="c2f8d-108">To support the task module feature, two new functions were added to the [Microsoft Teams client SDK](/javascript/api/overview/msteams-client):</span></span>

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

<span data-ttu-id="c2f8d-109">Vamos ver como cada um deles funciona.</span><span class="sxs-lookup"><span data-stu-id="c2f8d-109">Let's see how each of them work.</span></span>

## <a name="invoking-a-task-module-from-a-tab"></a><span data-ttu-id="c2f8d-110">Invocando um módulo de tarefa de uma guia</span><span class="sxs-lookup"><span data-stu-id="c2f8d-110">Invoking a task module from a tab</span></span>

<span data-ttu-id="c2f8d-111">Para invocar um módulo de tarefa de uma guia, use `microsoftTeams.tasks.startTask()` passar um [objeto TaskInfo](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) e uma função `submitHandler` de retorno de chamada opcional.</span><span class="sxs-lookup"><span data-stu-id="c2f8d-111">To invoke a task module from a tab use `microsoftTeams.tasks.startTask()` passing a [TaskInfo object](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) and an optional `submitHandler` callback function.</span></span> <span data-ttu-id="c2f8d-112">Conforme descrito anteriormente, há dois casos a considerar:</span><span class="sxs-lookup"><span data-stu-id="c2f8d-112">As described earlier, there are two cases to consider:</span></span>

1. <span data-ttu-id="c2f8d-113">O valor de `TaskInfo.url` é definido como uma URL.</span><span class="sxs-lookup"><span data-stu-id="c2f8d-113">The value of `TaskInfo.url` is set to a URL.</span></span> <span data-ttu-id="c2f8d-114">A janela do módulo de tarefas é exibida `TaskModule.url` e carregada como uma dentro `<iframe>` dela.</span><span class="sxs-lookup"><span data-stu-id="c2f8d-114">The task module window appears and `TaskModule.url` is loaded as an `<iframe>` inside it.</span></span> <span data-ttu-id="c2f8d-115">JavaScript nessa página deve chamar `microsoftTeams.initialize()` .</span><span class="sxs-lookup"><span data-stu-id="c2f8d-115">JavaScript on that page should call `microsoftTeams.initialize()`.</span></span> <span data-ttu-id="c2f8d-116">Se houver uma função na página e houver um erro ao invocar , será invocado com definido como a cadeia de caracteres de erro indicando o erro `submitHandler` `microsoftTeams.tasks.startTask()` conforme descrito `submitHandler` `err` [abaixo](#task-module-invocation-errors).</span><span class="sxs-lookup"><span data-stu-id="c2f8d-116">If there is a `submitHandler` function on the page and there is an error when invoking `microsoftTeams.tasks.startTask()`, then `submitHandler` is invoked with `err` set to the error string indicating the error as described [below](#task-module-invocation-errors).</span></span>
1. <span data-ttu-id="c2f8d-117">O valor de `taskInfo.card` é [o JSON para um cartão Adaptável.](~/task-modules-and-cards/what-are-task-modules.md#adaptive-card-or-adaptive-card-bot-card-attachment)</span><span class="sxs-lookup"><span data-stu-id="c2f8d-117">The value of `taskInfo.card` is the [JSON for an Adaptive card](~/task-modules-and-cards/what-are-task-modules.md#adaptive-card-or-adaptive-card-bot-card-attachment).</span></span> <span data-ttu-id="c2f8d-118">Nesse caso, obviamente, não há nenhuma função JavaScript a ser chamada quando o usuário fecha ou pressiona um botão no cartão Adaptável; a única maneira de receber o que o usuário entrou é passando o resultado para um `submitHandler` bot.</span><span class="sxs-lookup"><span data-stu-id="c2f8d-118">In this case there's obviously not any JavaScript `submitHandler` function to call when the user closes or presses a button on the Adaptive card; the only way to receive what the user entered is by passing the result to a bot.</span></span> <span data-ttu-id="c2f8d-119">Para usar um módulo de tarefa de cartão adaptável de uma guia, seu aplicativo deve incluir um bot para obter informações de volta do usuário.</span><span class="sxs-lookup"><span data-stu-id="c2f8d-119">To use an Adaptive card task module from a tab your app must include a bot to get any information back from the user.</span></span> <span data-ttu-id="c2f8d-120">Isso é explicado abaixo.</span><span class="sxs-lookup"><span data-stu-id="c2f8d-120">This is explained below.</span></span>

## <a name="example-invoking-a-task-module"></a><span data-ttu-id="c2f8d-121">Exemplo: Invocando um módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="c2f8d-121">Example: Invoking a task module</span></span>

<span data-ttu-id="c2f8d-122">O código a seguir é adaptado do [exemplo do módulo de tarefas](~/task-modules-and-cards/what-are-task-modules.md#code-sample).</span><span class="sxs-lookup"><span data-stu-id="c2f8d-122">The code below is adapted from [the task module sample](~/task-modules-and-cards/what-are-task-modules.md#code-sample).</span></span> <span data-ttu-id="c2f8d-123">Veja a aparência do módulo de tarefas:</span><span class="sxs-lookup"><span data-stu-id="c2f8d-123">Here's what the task module looks like:</span></span>

![Módulo de Tarefa - Formulário Personalizado](~/assets/images/task-module/task-module-custom-form.png)

<span data-ttu-id="c2f8d-125">O `submitHandler` é muito simples; ele apenas ecoa o valor de `err` ou para o `result` console:</span><span class="sxs-lookup"><span data-stu-id="c2f8d-125">The `submitHandler` is very simple; it just echoes the value of `err` or `result` to the console:</span></span>

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

## <a name="submitting-the-result-of-a-task-module"></a><span data-ttu-id="c2f8d-126">Enviando o resultado de um módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="c2f8d-126">Submitting the result of a task module</span></span>

<span data-ttu-id="c2f8d-127">A `submitHandler` função é usada com `TaskInfo.url` .</span><span class="sxs-lookup"><span data-stu-id="c2f8d-127">The `submitHandler` function is used with `TaskInfo.url`.</span></span> <span data-ttu-id="c2f8d-128">A `submitHandler` função reside na página da `TaskInfo.url` Web.</span><span class="sxs-lookup"><span data-stu-id="c2f8d-128">The `submitHandler` function resides in the `TaskInfo.url` web page.</span></span> <span data-ttu-id="c2f8d-129">Se houver um erro ao invocar o módulo de tarefa, sua função será imediatamente invocada com uma cadeia de caracteres indicando `submitHandler` `err` qual erro [ocorreu](#task-module-invocation-errors).</span><span class="sxs-lookup"><span data-stu-id="c2f8d-129">If there's an error when invoking the task module your `submitHandler` function will be immediately invoked with an `err` string indicating which [error occurred](#task-module-invocation-errors).</span></span> <span data-ttu-id="c2f8d-130">A função também é chamada com uma cadeia de caracteres quando o usuário `submitHandler` pressiona o X no canto superior direito do módulo de `err` tarefa.</span><span class="sxs-lookup"><span data-stu-id="c2f8d-130">The `submitHandler` function is also called with an `err` string when the user presses the X at the upper right of task module.</span></span>

<span data-ttu-id="c2f8d-131">Se não houver nenhum erro de invocação e o usuário não pressionar X para descartá-lo, o usuário pressionará um botão quando terminar.</span><span class="sxs-lookup"><span data-stu-id="c2f8d-131">If there's no invocation error and the user doesn't press X to dismiss it, the user presses a button when finished.</span></span> <span data-ttu-id="c2f8d-132">Dependendo se for uma URL ou um cartão adaptável no módulo de tarefas, veja o que acontece:</span><span class="sxs-lookup"><span data-stu-id="c2f8d-132">Depending on whether it's a URL or an Adaptive card in the task module, here's what happens:</span></span>

### <a name="htmljavascript-taskinfourl"></a><span data-ttu-id="c2f8d-133">HTML/JavaScript ( `TaskInfo.url` )</span><span class="sxs-lookup"><span data-stu-id="c2f8d-133">HTML/JavaScript (`TaskInfo.url`)</span></span>

<span data-ttu-id="c2f8d-134">Depois de validar o que o usuário instalou, você chama a função SDK (conhecida a seguir como para fins de capacidade `microsoftTeams.tasks.submitTask()` `submitTask()` de leitura).</span><span class="sxs-lookup"><span data-stu-id="c2f8d-134">Once you've validated what the user has entered you call the `microsoftTeams.tasks.submitTask()` SDK function (referred to hereafter as `submitTask()` for readability purposes).</span></span> <span data-ttu-id="c2f8d-135">Você pode chamar sem qualquer parâmetro se quiser apenas Teams fechar o módulo de tarefa, mas na maioria das vezes você vai querer passar um objeto ou uma cadeia de caracteres para seu `submitTask()` `submitHandler` .</span><span class="sxs-lookup"><span data-stu-id="c2f8d-135">You can call `submitTask()` without any parameters if you just want Teams to close the task module, but most of the time you'll want to pass an object or a string to your `submitHandler`.</span></span>

<span data-ttu-id="c2f8d-136">Passe o resultado como o primeiro parâmetro.</span><span class="sxs-lookup"><span data-stu-id="c2f8d-136">Pass your result as the first parameter.</span></span> <span data-ttu-id="c2f8d-137">Teams `submitHandler` invocará onde `err` estará e será o `null` objeto/cadeia de `result` caracteres que você passou para `submitTask()` .</span><span class="sxs-lookup"><span data-stu-id="c2f8d-137">Teams will invoke `submitHandler` where `err` will be `null` and `result` will be the object/string you passed to `submitTask()`.</span></span> <span data-ttu-id="c2f8d-138">Se você fizer uma chamada com um parâmetro, deverá passar uma ou uma matriz de cadeias de `submitTask()` `result` caracteres:  isso permite Teams validar que o aplicativo que está enviando o resultado é o mesmo que invocou o módulo de `appId` `appId` tarefa.</span><span class="sxs-lookup"><span data-stu-id="c2f8d-138">If you do call `submitTask()` with a `result` parameter, you **must** pass an `appId` or an array of `appId` strings: this allows Teams to validate that the app sending the result is the same one which invoked the task module.</span></span>

### <a name="adaptive-card-taskinfocard"></a><span data-ttu-id="c2f8d-139">Cartão adaptável ( `TaskInfo.card` )</span><span class="sxs-lookup"><span data-stu-id="c2f8d-139">Adaptive card (`TaskInfo.card`)</span></span>

<span data-ttu-id="c2f8d-140">Se você invocar o módulo de tarefa com um , quando o usuário pressionar um botão, os valores no cartão serão retornados como `submitHandler` `Action.Submit` o valor de `result` .</span><span class="sxs-lookup"><span data-stu-id="c2f8d-140">If you invoked the task module with a `submitHandler`, when the user presses an `Action.Submit` button the values in the card will be returned as the value of `result`.</span></span> <span data-ttu-id="c2f8d-141">Se o usuário pressionar o botão Esc ou pressionar o X, `err` será retornado em vez disso.</span><span class="sxs-lookup"><span data-stu-id="c2f8d-141">If the user presses the Esc button or presses the X, `err` will be returned instead.</span></span> <span data-ttu-id="c2f8d-142">Como alternativa, se seu aplicativo contiver um bot além de uma guia, você pode simplesmente incluir o bot como o `appId` `completionBotId` valor do `TaskInfo` objeto.</span><span class="sxs-lookup"><span data-stu-id="c2f8d-142">Alternatively, if your app contains a bot in addition to a tab you can simply include the `appId` of the bot as the value of `completionBotId` in the `TaskInfo` object.</span></span> <span data-ttu-id="c2f8d-143">O corpo do cartão adaptável (conforme preenchido pelo usuário) será enviado para o bot por meio de uma mensagem quando o usuário `task/submit invoke` pressionar um `Action.Submit` botão.</span><span class="sxs-lookup"><span data-stu-id="c2f8d-143">The Adaptive card body (as filled in by the user) will be sent to the bot via a `task/submit invoke` message when the user presses an `Action.Submit` button.</span></span> <span data-ttu-id="c2f8d-144">O esquema do objeto recebido é muito semelhante ao esquema recebido para mensagens [de tarefa/busca e tarefa/envio;](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages) a única diferença é que o esquema do objeto JSON é um  objeto de cartão Adaptável em vez de um objeto que contém um objeto de cartão adaptável como quando cartões adaptáveis são usados com [bots](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages).</span><span class="sxs-lookup"><span data-stu-id="c2f8d-144">The schema for the object you receive is very similar to [the schema you receive for task/fetch and task/submit messages](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages); the only difference is that the schema of the JSON object is an Adaptive card object as opposed to an object *containing* an Adaptive card object as [when Adaptive cards are used with bots](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages).</span></span>

## <a name="example-submitting-the-result-of-a-task-module"></a><span data-ttu-id="c2f8d-145">Exemplo: enviar o resultado de um módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="c2f8d-145">Example: submitting the result of a task module</span></span>

<span data-ttu-id="c2f8d-146">[Lembre-se do formulário no módulo de tarefa acima](#example-invoking-a-task-module) com um formulário HTML.</span><span class="sxs-lookup"><span data-stu-id="c2f8d-146">Recall the [form in the task module above](#example-invoking-a-task-module) with an HTML form.</span></span> <span data-ttu-id="c2f8d-147">Aqui é onde o formulário é definido:</span><span class="sxs-lookup"><span data-stu-id="c2f8d-147">Here's where the form is defined:</span></span>

```html
<form method="POST" id="customerForm" action="/register" onSubmit="return validateForm()">
```

<span data-ttu-id="c2f8d-148">Há cinco campos neste formulário, mas estamos interessados apenas nos valores de três deles para este exemplo: `name` `email` , e `favoriteBook` .</span><span class="sxs-lookup"><span data-stu-id="c2f8d-148">There are five fields on this form but we're only interested in the values of three of them for this example: `name`, `email`, and `favoriteBook`.</span></span>

<span data-ttu-id="c2f8d-149">Aqui está a `validateForm()` função que chama `submitTask()` :</span><span class="sxs-lookup"><span data-stu-id="c2f8d-149">Here's the `validateForm()` function that calls `submitTask()`:</span></span>

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

## <a name="task-module-invocation-errors"></a><span data-ttu-id="c2f8d-150">Erros de invocação do módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="c2f8d-150">Task module invocation errors</span></span>

<span data-ttu-id="c2f8d-151">Aqui estão os valores possíveis `err` dos que podem ser recebidos pelo seu `submitHandler` :</span><span class="sxs-lookup"><span data-stu-id="c2f8d-151">Here are the possible values of `err` that can be received by your `submitHandler`:</span></span>

| <span data-ttu-id="c2f8d-152">Problema</span><span class="sxs-lookup"><span data-stu-id="c2f8d-152">Problem</span></span> | <span data-ttu-id="c2f8d-153">Mensagem de erro (valor `err` de )</span><span class="sxs-lookup"><span data-stu-id="c2f8d-153">Error message (value of `err`)</span></span> |
| ------- | ------------------------------ |
| <span data-ttu-id="c2f8d-154">Valores para ambos `TaskInfo.url` `TaskInfo.card` e foram especificados.</span><span class="sxs-lookup"><span data-stu-id="c2f8d-154">Values for both `TaskInfo.url` and `TaskInfo.card` were specified.</span></span> | <span data-ttu-id="c2f8d-155">"Os valores para cartão e url foram especificados.</span><span class="sxs-lookup"><span data-stu-id="c2f8d-155">"Values for both card and url were specified.</span></span> <span data-ttu-id="c2f8d-156">Um ou outro, mas não ambos, são permitidos."</span><span class="sxs-lookup"><span data-stu-id="c2f8d-156">One or the other, but not both, are allowed."</span></span> |
| <span data-ttu-id="c2f8d-157">Nem `TaskInfo.url` `TaskInfo.card` especificado.</span><span class="sxs-lookup"><span data-stu-id="c2f8d-157">Neither `TaskInfo.url` nor `TaskInfo.card` specified.</span></span> | <span data-ttu-id="c2f8d-158">"Você deve especificar um valor para cartão ou url."</span><span class="sxs-lookup"><span data-stu-id="c2f8d-158">"You must specify a value for either card or url."</span></span> |
| <span data-ttu-id="c2f8d-159">Inválido `appId` .</span><span class="sxs-lookup"><span data-stu-id="c2f8d-159">Invalid `appId`.</span></span> | <span data-ttu-id="c2f8d-160">"AppId inválido".</span><span class="sxs-lookup"><span data-stu-id="c2f8d-160">"Invalid appId."</span></span> |
| <span data-ttu-id="c2f8d-161">O usuário pressionou o botão X, fechando-o.</span><span class="sxs-lookup"><span data-stu-id="c2f8d-161">User pressed X button, closing it.</span></span> | <span data-ttu-id="c2f8d-162">"O usuário cancelou/fechou o módulo de tarefa."</span><span class="sxs-lookup"><span data-stu-id="c2f8d-162">"User cancelled/closed the task module."</span></span> |
