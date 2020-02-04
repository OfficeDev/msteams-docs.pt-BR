---
title: Usando módulos de tarefas nas guias do Microsoft Teams
description: Explica como invocar módulos de tarefas de guias do Microsoft Teams usando o SDK do cliente do Microsoft Teams.
keywords: guias da equipe de módulos de tarefas SDK do cliente
ms.openlocfilehash: e10958195713f338a9b5e0a0672d8b6a29da9264
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672887"
---
# <a name="using-task-modules-in-tabs"></a><span data-ttu-id="5b152-104">Usando módulos de tarefas em guias</span><span class="sxs-lookup"><span data-stu-id="5b152-104">Using task modules in tabs</span></span>

<span data-ttu-id="5b152-105">Adicionar um módulo de tarefa à sua guia pode simplificar bastante a experiência do usuário para qualquer fluxo de trabalho que exija a entrada de dados.</span><span class="sxs-lookup"><span data-stu-id="5b152-105">Adding a task module to your tab can greatly simplify your user's experience for any workflows that require data input.</span></span> <span data-ttu-id="5b152-106">Os módulos de tarefas permitem coletar a entrada em um pop-up que reconhece equipes.</span><span class="sxs-lookup"><span data-stu-id="5b152-106">Task modules allow you to gather their input in a Teams-aware popup.</span></span> <span data-ttu-id="5b152-107">Um bom exemplo disso é a edição de cartões do Planner; Você pode usar módulos de tarefa para criar uma experiência semelhante.</span><span class="sxs-lookup"><span data-stu-id="5b152-107">A good example of this is editing Planner cards; you can use task modules to create a similar experience.</span></span>

<span data-ttu-id="5b152-108">Para dar suporte ao recurso de módulo de tarefa, duas novas funções foram adicionadas ao [SDK do cliente do Microsoft Teams](/javascript/api/overview/msteams-client):</span><span class="sxs-lookup"><span data-stu-id="5b152-108">To support the task module feature, two new functions were added to the [Microsoft Teams client SDK](/javascript/api/overview/msteams-client):</span></span>

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

<span data-ttu-id="5b152-109">Vamos ver como cada um deles funciona.</span><span class="sxs-lookup"><span data-stu-id="5b152-109">Let's see how each of them work.</span></span>

## <a name="invoking-a-task-module-from-a-tab"></a><span data-ttu-id="5b152-110">Invocar um módulo de tarefa a partir de uma guia</span><span class="sxs-lookup"><span data-stu-id="5b152-110">Invoking a task module from a tab</span></span>

<span data-ttu-id="5b152-111">Para invocar um módulo de tarefa a partir `microsoftTeams.tasks.startTask()` de uma guia, use a passagem `submitHandler` de um [objeto TaskInfo](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) e uma função de retorno de chamada opcional.</span><span class="sxs-lookup"><span data-stu-id="5b152-111">To invoke a task module from a tab use `microsoftTeams.tasks.startTask()` passing a [TaskInfo object](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) and an optional `submitHandler` callback function.</span></span> <span data-ttu-id="5b152-112">Conforme descrito anteriormente, há dois casos que devem ser considerados:</span><span class="sxs-lookup"><span data-stu-id="5b152-112">As described earlier, there are two cases to consider:</span></span>

1. <span data-ttu-id="5b152-113">O valor de `TaskInfo.url` é definido como uma URL.</span><span class="sxs-lookup"><span data-stu-id="5b152-113">The value of `TaskInfo.url` is set to a URL.</span></span> <span data-ttu-id="5b152-114">A janela módulo de tarefas aparece `TaskModule.url` e é carregada como `<iframe>` dentro dela.</span><span class="sxs-lookup"><span data-stu-id="5b152-114">The task module window appears and `TaskModule.url` is loaded as an `<iframe>` inside it.</span></span> <span data-ttu-id="5b152-115">O JavaScript nessa página deve chamar `microsoftTeams.initialize()`.</span><span class="sxs-lookup"><span data-stu-id="5b152-115">JavaScript on that page should call `microsoftTeams.initialize()`.</span></span> <span data-ttu-id="5b152-116">Se houver `submitHandler` uma função na página e houver um erro ao invocar `microsoftTeams.tasks.startTask()`, a chamada `submitHandler` será `err` definida como a cadeia de caracteres de erro indicando o erro, conforme descrito [abaixo](#task-module-invocation-errors).</span><span class="sxs-lookup"><span data-stu-id="5b152-116">If there is a `submitHandler` function on the page and there is an error when invoking `microsoftTeams.tasks.startTask()`, then `submitHandler` is invoked with `err` set to the error string indicating the error as described [below](#task-module-invocation-errors).</span></span>
1. <span data-ttu-id="5b152-117">O valor de `taskInfo.card` é o [JSON para um cartão adaptável](~/task-modules-and-cards/what-are-task-modules.md#adaptive-card-or-adaptive-card-bot-card-attachment).</span><span class="sxs-lookup"><span data-stu-id="5b152-117">The value of `taskInfo.card` is the [JSON for an Adaptive card](~/task-modules-and-cards/what-are-task-modules.md#adaptive-card-or-adaptive-card-bot-card-attachment).</span></span> <span data-ttu-id="5b152-118">Nesse caso, obviamente, não há nenhuma função `submitHandler` JavaScript a ser chamada quando o usuário fecha ou pressiona um botão no cartão adaptável; a única maneira de receber o que o usuário inseriu é passando o resultado para um bot.</span><span class="sxs-lookup"><span data-stu-id="5b152-118">In this case there's obviously not any JavaScript `submitHandler` function to call when the user closes or presses a button on the Adaptive card; the only way to receive what the user entered is by passing the result to a bot.</span></span> <span data-ttu-id="5b152-119">Para usar um módulo de tarefa de cartão adaptável de uma guia, seu aplicativo deve incluir um bot para obter qualquer informação do usuário.</span><span class="sxs-lookup"><span data-stu-id="5b152-119">To use an Adaptive card task module from a tab your app must include a bot to get any information back from the user.</span></span> <span data-ttu-id="5b152-120">Isso é explicado abaixo.</span><span class="sxs-lookup"><span data-stu-id="5b152-120">This is explained below.</span></span>

## <a name="example-invoking-a-task-module"></a><span data-ttu-id="5b152-121">Exemplo: invocação de um módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="5b152-121">Example: Invoking a task module</span></span>

<span data-ttu-id="5b152-122">O código a seguir é adaptado da [amostra do módulo de tarefa](~/task-modules-and-cards/what-are-task-modules.md#task-module-samples).</span><span class="sxs-lookup"><span data-stu-id="5b152-122">The code below is adapted from [the task module sample](~/task-modules-and-cards/what-are-task-modules.md#task-module-samples).</span></span> <span data-ttu-id="5b152-123">Veja a seguir como é o módulo de tarefas:</span><span class="sxs-lookup"><span data-stu-id="5b152-123">Here's what the task module looks like:</span></span>

![Módulo de tarefa-formulário personalizado](~/assets/images/task-module/task-module-custom-form.png)

<span data-ttu-id="5b152-125">O `submitHandler` é muito simples; Ele apenas ecoa o valor de `err` ou `result` para o console:</span><span class="sxs-lookup"><span data-stu-id="5b152-125">The `submitHandler` is very simple; it just echoes the value of `err` or `result` to the console:</span></span>

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

## <a name="submitting-the-result-of-a-task-module"></a><span data-ttu-id="5b152-126">Enviando o resultado de um módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="5b152-126">Submitting the result of a task module</span></span>

<span data-ttu-id="5b152-127">A `submitHandler` função é usada com `TaskInfo.url`o.</span><span class="sxs-lookup"><span data-stu-id="5b152-127">The `submitHandler` function is used with `TaskInfo.url`.</span></span> <span data-ttu-id="5b152-128">A `submitHandler` função reside na página `TaskInfo.url` da Web.</span><span class="sxs-lookup"><span data-stu-id="5b152-128">The `submitHandler` function resides in the `TaskInfo.url` web page.</span></span> <span data-ttu-id="5b152-129">Se houver um erro ao invocar o módulo de tarefa, `submitHandler` sua função será invocada imediatamente com `err` uma cadeia de caracteres indicando qual [erro ocorreu](#task-module-invocation-errors).</span><span class="sxs-lookup"><span data-stu-id="5b152-129">If there's an error when invoking the task module your `submitHandler` function will be immediately invoked with an `err` string indicating which [error occurred](#task-module-invocation-errors).</span></span> <span data-ttu-id="5b152-130">A `submitHandler` função também é chamada com uma `err` cadeia de caracteres quando o usuário pressiona o X no canto superior direito do módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="5b152-130">The `submitHandler` function is also called with an `err` string when the user presses the X at the upper right of task module.</span></span>

<span data-ttu-id="5b152-131">Se não houver um erro de invocação e o usuário não pressionar X para descartar, o usuário pressionará um botão quando terminar.</span><span class="sxs-lookup"><span data-stu-id="5b152-131">If there's no invocation error and the user doesn't press X to dismiss it, the user presses a button when finished.</span></span> <span data-ttu-id="5b152-132">Dependendo se é uma URL ou um cartão adaptável no módulo de tarefa, veja o que acontece:</span><span class="sxs-lookup"><span data-stu-id="5b152-132">Depending on whether it's a URL or an Adaptive card in the task module, here's what happens:</span></span>

### <a name="htmljavascript-taskinfourl"></a><span data-ttu-id="5b152-133">HTML/JavaScript (`TaskInfo.url`)</span><span class="sxs-lookup"><span data-stu-id="5b152-133">HTML/JavaScript (`TaskInfo.url`)</span></span>

<span data-ttu-id="5b152-134">Depois de validar o que o usuário inseriu, você chama `microsoftTeams.tasks.submitTask()` a função do SDK (mencionada `submitTask()` em diante para fins de legibilidade).</span><span class="sxs-lookup"><span data-stu-id="5b152-134">Once you've validated what the user has entered you call the `microsoftTeams.tasks.submitTask()` SDK function (referred to hereafter as `submitTask()` for readability purposes).</span></span> <span data-ttu-id="5b152-135">Você pode chamar `submitTask()` sem qualquer parâmetro se quiser que o Microsoft Teams feche o módulo de tarefa, mas a maior parte do tempo desejará passar um objeto ou uma cadeia `submitHandler`de caracteres para o seu.</span><span class="sxs-lookup"><span data-stu-id="5b152-135">You can call `submitTask()` without any parameters if you just want Teams to close the task module, but most of the time you'll want to pass an object or a string to your `submitHandler`.</span></span>

<span data-ttu-id="5b152-136">Passe seu resultado como o primeiro parâmetro.</span><span class="sxs-lookup"><span data-stu-id="5b152-136">Pass your result as the first parameter.</span></span> <span data-ttu-id="5b152-137">O `submitHandler` Microsoft Teams `err` invocará `null` onde `result` será e será o objeto/cadeia de caracteres `submitTask()`que você passa para.</span><span class="sxs-lookup"><span data-stu-id="5b152-137">Teams will invoke `submitHandler` where `err` will be `null` and `result` will be the object/string you passed to `submitTask()`.</span></span> <span data-ttu-id="5b152-138">Se você chamar `submitTask()` `result` com um parâmetro, você **deve** passar um `appId` ou uma matriz de cadeias de `appId` caracteres: isso permite que as equipes validem que o aplicativo enviando o resultado é o mesmo que invocar o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="5b152-138">If you do call `submitTask()` with a `result` parameter, you **must** pass an `appId` or an array of `appId` strings: this allows Teams to validate that the app sending the result is the same one which invoked the task module.</span></span>

### <a name="adaptive-card-taskinfocard"></a><span data-ttu-id="5b152-139">Cartão adaptável (`TaskInfo.card`)</span><span class="sxs-lookup"><span data-stu-id="5b152-139">Adaptive card (`TaskInfo.card`)</span></span>

<span data-ttu-id="5b152-140">Se você chamou o módulo de tarefa com `submitHandler`um, quando o usuário pressiona um `Action.Submit` botão, os valores no cartão serão retornados como o valor de `result`.</span><span class="sxs-lookup"><span data-stu-id="5b152-140">If you invoked the task module with a `submitHandler`, when the user presses an `Action.Submit` button the values in the card will be returned as the value of `result`.</span></span> <span data-ttu-id="5b152-141">Se o usuário pressionar o botão ESC ou pressionar o X, `err` será retornado.</span><span class="sxs-lookup"><span data-stu-id="5b152-141">If the user presses the Esc button or presses the X, `err` will be returned instead.</span></span> <span data-ttu-id="5b152-142">Como alternativa, se seu aplicativo contiver um bot além de uma guia, você pode simplesmente incluir `appId` o bot como o valor de `completionBotId` no `TaskInfo` objeto.</span><span class="sxs-lookup"><span data-stu-id="5b152-142">Alternatively, if your app contains a bot in addition to a tab you can simply include the `appId` of the bot as the value of `completionBotId` in the `TaskInfo` object.</span></span> <span data-ttu-id="5b152-143">O corpo do cartão adaptável (conforme preenchido pelo usuário) será enviado ao bot através de uma `task/submit invoke` mensagem quando o usuário pressiona um `Action.Submit` botão.</span><span class="sxs-lookup"><span data-stu-id="5b152-143">The Adaptive card body (as filled in by the user) will be sent to the bot via a `task/submit invoke` message when the user presses an `Action.Submit` button.</span></span> <span data-ttu-id="5b152-144">O esquema para o objeto que você recebe é muito semelhante ao [esquema que você recebe para tarefas/busca e mensagens/envio](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages); a única diferença é que o esquema do objeto JSON é um objeto Card adaptável, em vez de um objeto *que contém* um objeto Card adaptável como [quando os cartões adaptáveis são usados com bots](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages).</span><span class="sxs-lookup"><span data-stu-id="5b152-144">The schema for the object you receive is very similar to [the schema you receive for task/fetch and task/submit messages](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages); the only difference is that the schema of the JSON object is an Adaptive card object as opposed to an object *containing* an Adaptive card object as [when Adaptive cards are used with bots](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages).</span></span>

## <a name="example-submitting-the-result-of-a-task-module"></a><span data-ttu-id="5b152-145">Exemplo: enviando o resultado de um módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="5b152-145">Example: submitting the result of a task module</span></span>

<span data-ttu-id="5b152-146">Relembre o [formulário no módulo de tarefa acima](#example-invoking-a-task-module) com um formulário HTML.</span><span class="sxs-lookup"><span data-stu-id="5b152-146">Recall the [form in the task module above](#example-invoking-a-task-module) with an HTML form.</span></span> <span data-ttu-id="5b152-147">Veja onde o formulário está definido:</span><span class="sxs-lookup"><span data-stu-id="5b152-147">Here's where the form is defined:</span></span>

```html
<form method="POST" id="customerForm" action="/register" onSubmit="return validateForm()">
```

<span data-ttu-id="5b152-148">Há cinco campos neste formulário, mas estamos interessados apenas nos valores de três deles para este exemplo: `name`, `email`e. `favoriteBook`</span><span class="sxs-lookup"><span data-stu-id="5b152-148">There are five fields on this form but we're only interested in the values of three of them for this example: `name`, `email`, and `favoriteBook`.</span></span>

<span data-ttu-id="5b152-149">Aqui está a `validateForm()` função que chama `submitTask()`:</span><span class="sxs-lookup"><span data-stu-id="5b152-149">Here's the `validateForm()` function that calls `submitTask()`:</span></span>

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

## <a name="task-module-invocation-errors"></a><span data-ttu-id="5b152-150">Erros de invocação de módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="5b152-150">Task module invocation errors</span></span>

<span data-ttu-id="5b152-151">Estes são os possíveis valores `err` que podem ser recebidos pelo: `submitHandler`</span><span class="sxs-lookup"><span data-stu-id="5b152-151">Here are the possible values of `err` that can be received by your `submitHandler`:</span></span>

| <span data-ttu-id="5b152-152">Problema</span><span class="sxs-lookup"><span data-stu-id="5b152-152">Problem</span></span> | <span data-ttu-id="5b152-153">Mensagem de erro (valor `err`de)</span><span class="sxs-lookup"><span data-stu-id="5b152-153">Error message (value of `err`)</span></span> |
| ------- | ------------------------------ |
| <span data-ttu-id="5b152-154">Valores para ambos `TaskInfo.url` e `TaskInfo.card` foram especificados.</span><span class="sxs-lookup"><span data-stu-id="5b152-154">Values for both `TaskInfo.url` and `TaskInfo.card` were specified.</span></span> | <span data-ttu-id="5b152-155">"Os valores para o cartão e a URL foram especificados.</span><span class="sxs-lookup"><span data-stu-id="5b152-155">"Values for both card and url were specified.</span></span> <span data-ttu-id="5b152-156">Uma ou outra, mas não ambas, são permitidas. "</span><span class="sxs-lookup"><span data-stu-id="5b152-156">One or the other, but not both, are allowed."</span></span> |
| <span data-ttu-id="5b152-157">`TaskInfo.url` Nem `TaskInfo.card` especificado.</span><span class="sxs-lookup"><span data-stu-id="5b152-157">Neither `TaskInfo.url` nor `TaskInfo.card` specified.</span></span> | <span data-ttu-id="5b152-158">"Você deve especificar um valor para o cartão ou a URL".</span><span class="sxs-lookup"><span data-stu-id="5b152-158">"You must specify a value for either card or url."</span></span> |
| <span data-ttu-id="5b152-159">Inválido `appId`.</span><span class="sxs-lookup"><span data-stu-id="5b152-159">Invalid `appId`.</span></span> | <span data-ttu-id="5b152-160">"AppId inválido".</span><span class="sxs-lookup"><span data-stu-id="5b152-160">"Invalid appId."</span></span> |
| <span data-ttu-id="5b152-161">Botão X pressionando o usuário, fechando-o.</span><span class="sxs-lookup"><span data-stu-id="5b152-161">User pressed X button, closing it.</span></span> | <span data-ttu-id="5b152-162">"O usuário cancelou/fechou o módulo de tarefas".</span><span class="sxs-lookup"><span data-stu-id="5b152-162">"User cancelled/closed the task module."</span></span> |
