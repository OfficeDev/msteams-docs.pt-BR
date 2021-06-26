---
title: Usar Módulos de Tarefa em Microsoft Teams bots
description: Como usar módulos de tarefa com Microsoft Teams bots, incluindo cartões da Estrutura de Bot, cartões adaptáveis e links profundos.
localization_priority: Normal
ms.topic: how-to
keywords: bots de equipes de módulos de tarefa
ms.openlocfilehash: 5d9aa2b651a4c99cee75aada62a4d1176a589d79
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140303"
---
# <a name="use-task-modules-from-bots"></a><span data-ttu-id="1677c-104">Usar módulos de tarefas de bots</span><span class="sxs-lookup"><span data-stu-id="1677c-104">Use task modules from bots</span></span>

<span data-ttu-id="1677c-105">Os módulos de tarefa podem ser invocados Microsoft Teams bots usando botões em Cartões Adaptáveis e cartões de Estrutura de Bot que são hero, miniatura e conector Office 365 Bot.</span><span class="sxs-lookup"><span data-stu-id="1677c-105">Task modules can be invoked from Microsoft Teams bots using buttons on Adaptive Cards and Bot Framework cards that is hero, thumbnail, and Office 365 Connector.</span></span> <span data-ttu-id="1677c-106">Os módulos de tarefas geralmente são uma experiência de usuário melhor do que várias etapas de conversa.</span><span class="sxs-lookup"><span data-stu-id="1677c-106">Task modules are often a better user experience than multiple conversation steps.</span></span> <span data-ttu-id="1677c-107">Acompanhe o estado do bot e permita que o usuário interrompa ou cancele a sequência.</span><span class="sxs-lookup"><span data-stu-id="1677c-107">Keep track of bot state and allow the user to interrupt or cancel the sequence.</span></span>

<span data-ttu-id="1677c-108">Há duas maneiras de invocar módulos de tarefa:</span><span class="sxs-lookup"><span data-stu-id="1677c-108">There are two ways of invoking task modules:</span></span>

* <span data-ttu-id="1677c-109">Um novo tipo de mensagem de invocação : Usar a ação de cartão para cartões da Estrutura de Bot ou a ação de cartão para cartões adaptáveis, com um módulo de tarefa, uma URL ou um Cartão Adaptável, é buscada `task/fetch` `invoke` [](~/task-modules-and-cards/cards/cards-actions.md#action-type-invoke) `Action.Submit` [](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) `task/fetch` dinamicamente no bot.</span><span class="sxs-lookup"><span data-stu-id="1677c-109">A new kind of invoke message `task/fetch`: Using the `invoke` [card action](~/task-modules-and-cards/cards/cards-actions.md#action-type-invoke) for Bot Framework cards, or the `Action.Submit` [card action](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) for Adaptive cards, with `task/fetch`, task module either a URL or an Adaptive Card, is fetched dynamically from your bot.</span></span>
* <span data-ttu-id="1677c-110">URLs de link profundo: usando a sintaxe de link profundo para [módulos](~/task-modules-and-cards/task-modules/invoking-task-modules.md#task-module-deep-link-syntax)de tarefa, você pode usar a ação de cartão para cartões de Estrutura de Bot ou a ação de cartão para Cartões `openUrl` [](~/task-modules-and-cards/cards/cards-actions.md#action-type-openurl) `Action.OpenUrl` [](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) Adaptáveis, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="1677c-110">Deep link URLs: Using the [deep link syntax for task modules](~/task-modules-and-cards/task-modules/invoking-task-modules.md#task-module-deep-link-syntax), you can use the `openUrl` [card action](~/task-modules-and-cards/cards/cards-actions.md#action-type-openurl) for Bot Framework cards or the `Action.OpenUrl` [card action](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) for Adaptive Cards, respectively.</span></span> <span data-ttu-id="1677c-111">Com URLs de link profundo, a URL do módulo de tarefas ou o corpo do Cartão Adaptável já é conhecido para evitar uma ida e volta do servidor em relação a `task/fetch` .</span><span class="sxs-lookup"><span data-stu-id="1677c-111">With deep link URLs, the task module URL or Adaptive Card body is already known to avoid a server round-trip relative to `task/fetch`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1677c-112">Cada `url` um deles e deve implementar o protocolo de criptografia `fallbackUrl` HTTPS.</span><span class="sxs-lookup"><span data-stu-id="1677c-112">Each `url` and `fallbackUrl` must implement the HTTPS encryption protocol.</span></span>

<span data-ttu-id="1677c-113">A próxima seção fornece detalhes sobre como invocar um módulo de tarefa usando `task/fetch` .</span><span class="sxs-lookup"><span data-stu-id="1677c-113">The next section provides details on invoking a task module using `task/fetch`.</span></span>

## <a name="invoke-a-task-module-using-taskfetch"></a><span data-ttu-id="1677c-114">Invocar um módulo de tarefa usando tarefa/busca</span><span class="sxs-lookup"><span data-stu-id="1677c-114">Invoke a task module using task/fetch</span></span>

<span data-ttu-id="1677c-115">Quando o objeto da ação do cartão ou é inicializado e quando um usuário seleciona o botão, uma mensagem `value` é enviada para o `invoke` `Action.Submit` `invoke` bot.</span><span class="sxs-lookup"><span data-stu-id="1677c-115">When the `value` object of the `invoke` card action or `Action.Submit` is initialized and when a user selects the button, an `invoke` message is sent to the bot.</span></span> <span data-ttu-id="1677c-116">Na resposta HTTP à mensagem, há um objeto TaskInfo inserido em um objeto wrapper, que Teams usa para `invoke` exibir o módulo de tarefa. [](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object)</span><span class="sxs-lookup"><span data-stu-id="1677c-116">In the HTTP response to the `invoke` message, there is a [TaskInfo object](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object) embedded in a wrapper object, which Teams uses to display the task module.</span></span>

![solicitação ou resposta de tarefa/busca](~/assets/images/task-module/task-module-invoke-request-response.png)

<span data-ttu-id="1677c-118">As etapas a seguir fornece o módulo de tarefa chamar usando tarefa/busca:</span><span class="sxs-lookup"><span data-stu-id="1677c-118">The following steps provides the invoke task module using task/fetch:</span></span>

1. <span data-ttu-id="1677c-119">Esta imagem mostra um cartão de herói da Estrutura de Bot com uma **ação comprar** `invoke` [cartão](~/task-modules-and-cards/cards/cards-actions.md#action-type-invoke).</span><span class="sxs-lookup"><span data-stu-id="1677c-119">This image shows a Bot Framework hero card with a **Buy** `invoke` [card action](~/task-modules-and-cards/cards/cards-actions.md#action-type-invoke).</span></span> <span data-ttu-id="1677c-120">O valor da `type` propriedade é e o restante do objeto pode ser de sua `task/fetch` `value` escolha.</span><span class="sxs-lookup"><span data-stu-id="1677c-120">The value of the `type` property is `task/fetch` and the rest of the `value` object can be of your choice.</span></span>
1. <span data-ttu-id="1677c-121">O bot recebe a `invoke` mensagem HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="1677c-121">The bot receives the `invoke` HTTP POST message.</span></span>
1. <span data-ttu-id="1677c-122">O bot cria um objeto de resposta e o retorna no corpo da resposta POST com um código de resposta HTTP 200.</span><span class="sxs-lookup"><span data-stu-id="1677c-122">The bot creates a response object and returns it in the body of the POST response with an HTTP 200 response code.</span></span> <span data-ttu-id="1677c-123">Para obter mais informações sobre o esquema para respostas, consulte [a discussão sobre tarefa/envio.](#the-flexibility-of-tasksubmit)</span><span class="sxs-lookup"><span data-stu-id="1677c-123">For more information on schema for responses, see [the discussion on task/submit](#the-flexibility-of-tasksubmit).</span></span> <span data-ttu-id="1677c-124">O código a seguir fornece um exemplo de corpo da resposta HTTP que contém um [objeto TaskInfo](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object) inserido em um objeto wrapper:</span><span class="sxs-lookup"><span data-stu-id="1677c-124">The following code provides an example of body of the HTTP response that contains a [TaskInfo object](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object) embedded in a wrapper object:</span></span>

    ```json
    {
      "task": {
        "type": "continue",
        "value": {
          "title": "Task module title",
          "height": 500,
          "width": "medium",
          "url": "https://contoso.com/msteams/taskmodules/newcustomer",
          "fallbackUrl": "https://contoso.com/msteams/taskmodules/newcustomer"
        }
      }
    }
    ```

    <span data-ttu-id="1677c-125">O `task/fetch` evento e sua resposta para bots é semelhante à função no `microsoftTeams.tasks.startTask()` SDK do cliente.</span><span class="sxs-lookup"><span data-stu-id="1677c-125">The `task/fetch` event and its response for bots is similar to the `microsoftTeams.tasks.startTask()` function in the client SDK.</span></span>

1. <span data-ttu-id="1677c-126">Microsoft Teams exibe o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="1677c-126">Microsoft Teams displays the task module.</span></span>

<span data-ttu-id="1677c-127">A próxima seção fornece detalhes sobre como enviar o resultado de um módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="1677c-127">The next section provides details on submitting the result of a task module.</span></span>

## <a name="submit-the-result-of-a-task-module"></a><span data-ttu-id="1677c-128">Enviar o resultado de um módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="1677c-128">Submit the result of a task module</span></span>

<span data-ttu-id="1677c-129">Quando o usuário é concluído com o módulo de tarefa, enviar o resultado de volta para o bot é semelhante à maneira como ele funciona com guias.</span><span class="sxs-lookup"><span data-stu-id="1677c-129">When the user is finished with the task module, submitting the result back to the bot is similar to the way it works with tabs.</span></span> <span data-ttu-id="1677c-130">Para obter mais informações, [consulte o exemplo de envio do resultado de um módulo de tarefa](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-of-submitting-the-result-of-a-task-module).</span><span class="sxs-lookup"><span data-stu-id="1677c-130">For more information, see [example of submitting the result of a task module](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-of-submitting-the-result-of-a-task-module).</span></span> <span data-ttu-id="1677c-131">Há algumas diferenças da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="1677c-131">There are a few differences as follows:</span></span>

* <span data-ttu-id="1677c-132">HTML ou JavaScript que é : Depois de validar o que o usuário entrou, você chama a função SDK conhecida a seguir como para fins de capacidade `TaskInfo.url` `microsoftTeams.tasks.submitTask()` de `submitTask()` leitura.</span><span class="sxs-lookup"><span data-stu-id="1677c-132">HTML or JavaScript that is `TaskInfo.url`: Once you have validated what the user has entered, you call the `microsoftTeams.tasks.submitTask()` SDK function referred to hereafter as `submitTask()` for readability purposes.</span></span> <span data-ttu-id="1677c-133">Você pode chamar sem parâmetros se quiser Teams o módulo de tarefa, mas deve passar um objeto ou uma `submitTask()` cadeia de caracteres para seu `submitHandler` .</span><span class="sxs-lookup"><span data-stu-id="1677c-133">You can call `submitTask()` without any parameters if you want Teams to close the task module, but you must pass an object or a string to your `submitHandler`.</span></span> <span data-ttu-id="1677c-134">Passe-o como o primeiro parâmetro, `result` .</span><span class="sxs-lookup"><span data-stu-id="1677c-134">Pass it as the first parameter, `result`.</span></span> <span data-ttu-id="1677c-135">Teams invoca , é , e é o objeto ou cadeia de `submitHandler` `err` `null` `result` caracteres que você passou para `submitTask()` .</span><span class="sxs-lookup"><span data-stu-id="1677c-135">Teams invokes `submitHandler`, `err` is `null`, and `result` is the object or string you passed to `submitTask()`.</span></span> <span data-ttu-id="1677c-136">Se você chamar `submitTask()` com um `result` parâmetro, deverá passar uma ou uma `appId` matriz de `appId` cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1677c-136">If you call `submitTask()` with a `result` parameter, you must pass an `appId` or an array of `appId` strings.</span></span> <span data-ttu-id="1677c-137">Isso permite Teams validar se o aplicativo que está enviando o resultado é o mesmo que invocou o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="1677c-137">This allows Teams to validate that the app sending the result is the same one which invoked the task module.</span></span> <span data-ttu-id="1677c-138">Seu bot recebe uma `task/submit` mensagem incluindo `result` .</span><span class="sxs-lookup"><span data-stu-id="1677c-138">Your bot receives a `task/submit` message including `result`.</span></span> <span data-ttu-id="1677c-139">Para obter mais informações, [consulte carga de e `task/fetch` `task/submit` mensagens](#payload-of-taskfetch-and-tasksubmit-messages).</span><span class="sxs-lookup"><span data-stu-id="1677c-139">For more information, see [payload of `task/fetch` and `task/submit` messages](#payload-of-taskfetch-and-tasksubmit-messages).</span></span>
* <span data-ttu-id="1677c-140">Cartão Adaptável que é : O corpo do Cartão Adaptável conforme preenchido pelo usuário é enviado para o bot por meio de uma mensagem quando o usuário `TaskInfo.card` `task/submit` seleciona qualquer `Action.Submit` botão.</span><span class="sxs-lookup"><span data-stu-id="1677c-140">Adaptive Card that is `TaskInfo.card`: The Adaptive Card body as filled in by the user is sent to the bot through a `task/submit` message when the user selects any `Action.Submit` button.</span></span>

<span data-ttu-id="1677c-141">A próxima seção fornece detalhes sobre a flexibilidade de `task/submit` .</span><span class="sxs-lookup"><span data-stu-id="1677c-141">The next section provides details on the flexibility of `task/submit`.</span></span>

## <a name="the-flexibility-of-tasksubmit"></a><span data-ttu-id="1677c-142">A flexibilidade de tarefa/envio</span><span class="sxs-lookup"><span data-stu-id="1677c-142">The flexibility of task/submit</span></span>

<span data-ttu-id="1677c-143">Quando o usuário termina com um módulo de tarefa invocado de um bot, o bot sempre recebe uma `task/submit invoke` mensagem.</span><span class="sxs-lookup"><span data-stu-id="1677c-143">When the user finishes with a task module invoked from a bot, the bot always receives a `task/submit invoke` message.</span></span> <span data-ttu-id="1677c-144">Você tem várias opções ao responder à `task/submit` mensagem da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="1677c-144">You have several options when responding to the `task/submit` message as follows:</span></span>

| <span data-ttu-id="1677c-145">Resposta de corpo HTTP</span><span class="sxs-lookup"><span data-stu-id="1677c-145">HTTP body response</span></span>                      | <span data-ttu-id="1677c-146">Cenário</span><span class="sxs-lookup"><span data-stu-id="1677c-146">Scenario</span></span>                                |
| --------------------------------------- | --------------------------------------- |
| <span data-ttu-id="1677c-147">Nenhum ignora a `task/submit` mensagem</span><span class="sxs-lookup"><span data-stu-id="1677c-147">None ignore the `task/submit` message</span></span> | <span data-ttu-id="1677c-148">A resposta mais simples não é nenhuma resposta.</span><span class="sxs-lookup"><span data-stu-id="1677c-148">The simplest response is no response at all.</span></span> <span data-ttu-id="1677c-149">Seu bot não é necessário para responder quando o usuário terminar com o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="1677c-149">Your bot is not required to respond when the user is finished with the task module.</span></span> |
| <pre>{<br/>  "task": {<br/>    "type": "message",<br/>    "value": "Message text"<br/>  }<br/>}</pre> | <span data-ttu-id="1677c-150">Teams exibe o valor de `value` em uma caixa de mensagem pop-up.</span><span class="sxs-lookup"><span data-stu-id="1677c-150">Teams displays the value of `value` in a pop-up message box.</span></span> |
| <pre>{<br/>  "task": {<br/>    "type": "continue",<br/>    "value": &lt;TaskInfo object&gt;<br/>  }<br/>}</pre> | <span data-ttu-id="1677c-151">Permite encadear sequências de Cartões Adaptáveis em conjunto em um assistente ou experiência em várias etapas.</span><span class="sxs-lookup"><span data-stu-id="1677c-151">Allows you to chain sequences of Adaptive Cards together in a wizard or multi-step experience.</span></span> |

> [!NOTE]
> <span data-ttu-id="1677c-152">Encadear cartões adaptáveis em uma sequência é um cenário avançado.</span><span class="sxs-lookup"><span data-stu-id="1677c-152">Chaining Adaptive Cards into a sequence is an advanced scenario.</span></span> <span data-ttu-id="1677c-153">O Node.js de exemplo oferece suporte a ele.</span><span class="sxs-lookup"><span data-stu-id="1677c-153">The Node.js sample app supports it.</span></span> <span data-ttu-id="1677c-154">Para obter mais informações, [consulte Microsoft Teams módulo de tarefas Node.js](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs#implementation-notes).</span><span class="sxs-lookup"><span data-stu-id="1677c-154">For more information, see [Microsoft Teams task module Node.js](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs#implementation-notes).</span></span>

<span data-ttu-id="1677c-155">A próxima seção fornece detalhes sobre carga e `task/fetch` `task/submit` mensagens.</span><span class="sxs-lookup"><span data-stu-id="1677c-155">The next section provides details on payload of `task/fetch` and `task/submit` messages.</span></span>

## <a name="payload-of-taskfetch-and-tasksubmit-messages"></a><span data-ttu-id="1677c-156">Carga de mensagens de tarefa/busca e tarefa/envio</span><span class="sxs-lookup"><span data-stu-id="1677c-156">Payload of task/fetch and task/submit messages</span></span>

<span data-ttu-id="1677c-157">Esta seção define o esquema do que seu bot recebe quando recebe um `task/fetch` objeto `task/submit` Ou Bot `Activity` Framework.</span><span class="sxs-lookup"><span data-stu-id="1677c-157">This section defines the schema of what your bot receives when it receives a `task/fetch` or `task/submit` Bot Framework `Activity` object.</span></span> <span data-ttu-id="1677c-158">A tabela a seguir fornece as propriedades de carga e `task/fetch` `task/submit` mensagens:</span><span class="sxs-lookup"><span data-stu-id="1677c-158">The following table provides the properties of payload of `task/fetch` and `task/submit` messages:</span></span>

| <span data-ttu-id="1677c-159">Propriedade</span><span class="sxs-lookup"><span data-stu-id="1677c-159">Property</span></span> | <span data-ttu-id="1677c-160">Descrição</span><span class="sxs-lookup"><span data-stu-id="1677c-160">Description</span></span>                          |
| -------- | ------------------------------------ |
| `type`   | <span data-ttu-id="1677c-161">É sempre `invoke` .</span><span class="sxs-lookup"><span data-stu-id="1677c-161">Is always `invoke`.</span></span>           |
| `name`   | <span data-ttu-id="1677c-162">É ou `task/fetch` `task/submit` .</span><span class="sxs-lookup"><span data-stu-id="1677c-162">Is either `task/fetch` or `task/submit`.</span></span> |
| `value`  | <span data-ttu-id="1677c-163">É a carga definida pelo desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="1677c-163">Is the developer-defined payload.</span></span> <span data-ttu-id="1677c-164">A estrutura do `value` objeto é a mesma que é enviada de Teams.</span><span class="sxs-lookup"><span data-stu-id="1677c-164">The structure of the `value` object is the same as what is sent from Teams.</span></span> <span data-ttu-id="1677c-165">Nesse caso, no entanto, é diferente.</span><span class="sxs-lookup"><span data-stu-id="1677c-165">In this case, however, it is different.</span></span> <span data-ttu-id="1677c-166">Ele requer suporte para busca dinâmica que é `task/fetch` da Estrutura de Bot, que é e `value` ações do Cartão `Action.Submit` Adaptável, que é `data` .</span><span class="sxs-lookup"><span data-stu-id="1677c-166">It requires support for dynamic fetch that is `task/fetch` from both Bot Framework, which is `value` and Adaptive Card `Action.Submit` actions, which is `data`.</span></span> <span data-ttu-id="1677c-167">Uma maneira de comunicar Teams ao bot é necessária, além do `context` que está incluído em ou `value` `data` .</span><span class="sxs-lookup"><span data-stu-id="1677c-167">A way to communicate Teams `context` to the bot is required in addition to what is included in `value` or `data`.</span></span><br/><br/><span data-ttu-id="1677c-168">Combinar 'valor' e 'dados' em um objeto pai:</span><span class="sxs-lookup"><span data-stu-id="1677c-168">Combine 'value' and 'data' into a parent object:</span></span><br/><br/><pre>{<br/>  "context": {<br/>    "theme": "default" &vert; "dark" &vert; "contrast",<br/>  },<br/>  "data": [value field from Bot Framework card] &vert; [data field from Adaptive Card] <br/>}</pre>  |

<span data-ttu-id="1677c-169">A próxima seção fornece um exemplo de recebimento e resposta e `task/fetch` `task/submit` invocação de mensagens Node.js.</span><span class="sxs-lookup"><span data-stu-id="1677c-169">The next section provides an example of receiving and responding to `task/fetch` and `task/submit` invoke messages in Node.js.</span></span>

## <a name="example-of-taskfetch-and-tasksubmit-invoke-messages-in-nodejs-and-c"></a><span data-ttu-id="1677c-170">Exemplo de tarefa/busca e tarefa/envio de mensagens invocadas Node.js e C #</span><span class="sxs-lookup"><span data-stu-id="1677c-170">Example of task/fetch and task/submit invoke messages in Node.js and C#</span></span>

# <a name="nodejs"></a>[<span data-ttu-id="1677c-171">Node.js</span><span class="sxs-lookup"><span data-stu-id="1677c-171">Node.js</span></span>](#tab/nodejs)

```typescript
handleTeamsTaskModuleFetch(context, taskModuleRequest) {
    // Called when the user selects an options from the displayed HeroCard or
    // AdaptiveCard.  The result is the action to perform.

    const cardTaskFetchValue = taskModuleRequest.data.data;
    var taskInfo = {}; // TaskModuleTaskInfo

    if (cardTaskFetchValue === TaskModuleIds.YouTube) {
        // Display the YouTube.html page
        taskInfo.url = taskInfo.fallbackUrl = this.baseUrl + '/' + TaskModuleIds.YouTube + '.html';
        this.setTaskInfo(taskInfo, TaskModuleUIConstants.YouTube);
    } else if (cardTaskFetchValue === TaskModuleIds.CustomForm) {
        // Display the CustomForm.html page, and post the form data back via
        // handleTeamsTaskModuleSubmit.
        taskInfo.url = taskInfo.fallbackUrl = this.baseUrl + '/' + TaskModuleIds.CustomForm + '.html';
        this.setTaskInfo(taskInfo, TaskModuleUIConstants.CustomForm);
    } else if (cardTaskFetchValue === TaskModuleIds.AdaptiveCard) {
        // Display an AdaptiveCard to prompt user for text, and post it back via
        // handleTeamsTaskModuleSubmit.
        taskInfo.card = this.createAdaptiveCardAttachment();
        this.setTaskInfo(taskInfo, TaskModuleUIConstants.AdaptiveCard);
    }

    return TaskModuleResponseFactory.toTaskModuleResponse(taskInfo);
}

async handleTeamsTaskModuleSubmit(context, taskModuleRequest) {
    // Called when data is being returned from the selected option (see `handleTeamsTaskModuleFetch').

    // Echo the users input back.  In a production bot, this is where you'd add behavior in
    // response to the input.
    await context.sendActivity(MessageFactory.text('handleTeamsTaskModuleSubmit: ' + JSON.stringify(taskModuleRequest.data)));

    // Return TaskModuleResponse
    return {
        // TaskModuleMessageResponse
        task: {
            type: 'message',
            value: 'Thanks!'
        }
    };
}

setTaskInfo(taskInfo, uiSettings) {
    taskInfo.height = uiSettings.height;
    taskInfo.width = uiSettings.width;
    taskInfo.title = uiSettings.title;
}
```

# <a name="c"></a>[<span data-ttu-id="1677c-172">C#</span><span class="sxs-lookup"><span data-stu-id="1677c-172">C#</span></span>](#tab/csharp)

```csharp
protected override Task<TaskModuleResponse> OnTeamsTaskModuleFetchAsync(ITurnContext<IInvokeActivity> turnContext, TaskModuleRequest taskModuleRequest, CancellationToken cancellationToken)
{
    var asJobject = JObject.FromObject(taskModuleRequest.Data);
    var value = asJobject.ToObject<CardTaskFetchValue<string>>()?.Data;

    var taskInfo = new TaskModuleTaskInfo();
    switch (value)
    {
        case TaskModuleIds.YouTube:
            taskInfo.Url = taskInfo.FallbackUrl = _baseUrl + "/" + TaskModuleIds.YouTube;
            SetTaskInfo(taskInfo, TaskModuleUIConstants.YouTube);
            break;
        case TaskModuleIds.CustomForm:
            taskInfo.Url = taskInfo.FallbackUrl = _baseUrl + "/" + TaskModuleIds.CustomForm;
            SetTaskInfo(taskInfo, TaskModuleUIConstants.CustomForm);
            break;
        case TaskModuleIds.AdaptiveCard:
            taskInfo.Card = CreateAdaptiveCardAttachment();
            SetTaskInfo(taskInfo, TaskModuleUIConstants.AdaptiveCard);
            break;
        default:
            break;
    }

    return Task.FromResult(taskInfo.ToTaskModuleResponse());
}

protected override async Task<TaskModuleResponse> OnTeamsTaskModuleSubmitAsync(ITurnContext<IInvokeActivity> turnContext, TaskModuleRequest taskModuleRequest, CancellationToken cancellationToken)
{
    var reply = MessageFactory.Text("OnTeamsTaskModuleSubmitAsync Value: " + JsonConvert.SerializeObject(taskModuleRequest));
    await turnContext.SendActivityAsync(reply, cancellationToken);

    return TaskModuleResponseFactory.CreateResponse("Thanks!");
}

private static void SetTaskInfo(TaskModuleTaskInfo taskInfo, UISettings uIConstants)
{
    taskInfo.Height = uIConstants.Height;
    taskInfo.Width = uIConstants.Width;
    taskInfo.Title = uIConstants.Title.ToString();
}
```

---

### <a name="bot-framework-card-actions-vs-adaptive-card-actionsubmit-actions"></a><span data-ttu-id="1677c-173">Ações de cartão da Estrutura de Bot vs. Ação do Cartão Adaptável.Enviar ações</span><span class="sxs-lookup"><span data-stu-id="1677c-173">Bot Framework card actions vs. Adaptive Card Action.Submit actions</span></span>

<span data-ttu-id="1677c-174">O esquema para ações de cartão da Estrutura de Bot é diferente das ações do Cartão Adaptável e a maneira de invocar módulos de `Action.Submit` tarefa também é diferente.</span><span class="sxs-lookup"><span data-stu-id="1677c-174">The schema for Bot Framework card actions is different from Adaptive Card `Action.Submit` actions and the way to invoke task modules is also different.</span></span> <span data-ttu-id="1677c-175">O `data` objeto em contém um objeto para que ele não interfira com outras propriedades no `Action.Submit` `msteams` cartão.</span><span class="sxs-lookup"><span data-stu-id="1677c-175">The `data` object in `Action.Submit` contains an `msteams` object so it does not interfere with other properties in the card.</span></span> <span data-ttu-id="1677c-176">A tabela a seguir mostra um exemplo de cada ação de cartão:</span><span class="sxs-lookup"><span data-stu-id="1677c-176">The following table shows an example of each card action:</span></span>

| <span data-ttu-id="1677c-177">Ação de cartão da Estrutura de Bot</span><span class="sxs-lookup"><span data-stu-id="1677c-177">Bot Framework card action</span></span>                              | <span data-ttu-id="1677c-178">Ação do Cartão Adaptável.Enviar</span><span class="sxs-lookup"><span data-stu-id="1677c-178">Adaptive Card Action.Submit action</span></span>                     |
| ------------------------------------------------------ | ------------------------------------------------------ |
| <pre>{<br/>  "type": "invoke",<br/>  "title": "Buy",<br/>  "value": {<br/>    "type": "task/fetch",<br/>    &lt;...&gt;<br/>  }<br/>}</pre> | <pre>{<br/>  "type": "Action.Submit",<br/>  "id": "btnBuy",<br/>  "title": "Buy",<br/>  "data": {<br/>    &lt;...&gt;,<br/>    "msteams": {<br/>      "type": "task/fetch"<br/>    }<br/>  }<br/>}</pre>  |

## <a name="code-sample"></a><span data-ttu-id="1677c-179">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="1677c-179">Code sample</span></span>

|<span data-ttu-id="1677c-180">Exemplo de nome</span><span class="sxs-lookup"><span data-stu-id="1677c-180">Sample name</span></span> | <span data-ttu-id="1677c-181">Descrição</span><span class="sxs-lookup"><span data-stu-id="1677c-181">Description</span></span> | <span data-ttu-id="1677c-182">.NET</span><span class="sxs-lookup"><span data-stu-id="1677c-182">.NET</span></span> | <span data-ttu-id="1677c-183">Node.js</span><span class="sxs-lookup"><span data-stu-id="1677c-183">Node.js</span></span>|
|----------------|-----------------|--------------|----------------|
|<span data-ttu-id="1677c-184">Exemplo de módulo de tarefa bots-V4</span><span class="sxs-lookup"><span data-stu-id="1677c-184">Task module sample bots-V4</span></span> | <span data-ttu-id="1677c-185">Exemplos para a criação de módulos de tarefa.</span><span class="sxs-lookup"><span data-stu-id="1677c-185">Samples for creating task modules.</span></span> |[<span data-ttu-id="1677c-186">View</span><span class="sxs-lookup"><span data-stu-id="1677c-186">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/54.teams-task-module)|[<span data-ttu-id="1677c-187">View</span><span class="sxs-lookup"><span data-stu-id="1677c-187">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/54.teams-task-module)|

## <a name="see-also"></a><span data-ttu-id="1677c-188">Também consulte</span><span class="sxs-lookup"><span data-stu-id="1677c-188">See also</span></span>

* [<span data-ttu-id="1677c-189">Microsoft Teams exemplo de módulo de tarefa no Node.js</span><span class="sxs-lookup"><span data-stu-id="1677c-189">Microsoft Teams task module sample code in Node.js</span></span>](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs/blob/master/src/TeamsBot.ts)
* [<span data-ttu-id="1677c-190">Exemplos de Estrutura de Bot</span><span class="sxs-lookup"><span data-stu-id="1677c-190">Bot Framework samples</span></span>](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md)
