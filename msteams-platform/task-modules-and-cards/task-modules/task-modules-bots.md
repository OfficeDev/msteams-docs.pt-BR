---
title: Usando módulos de tarefa nos bots do Microsoft Teams
description: Como usar módulos de tarefas com bots do Microsoft Teams, incluindo cartões de estrutura de bot, cartões adaptáveis e links de fundo.
keywords: robôs da equipe de módulos de tarefa
ms.openlocfilehash: 1400fec0ef86448f8632018c7675999b6b1881a0
ms.sourcegitcommit: 64acd30eee8af5fe151e9866c13226ed3f337c72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2020
ms.locfileid: "49346718"
---
# <a name="using-task-modules-from-microsoft-teams-bots"></a><span data-ttu-id="33718-104">Usando módulos de tarefa dos bots do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="33718-104">Using task modules from Microsoft Teams bots</span></span>

<span data-ttu-id="33718-105">Os módulos de tarefa podem ser invocados de bots do Microsoft Teams usando botões em cartões adaptáveis e cartões de estrutura de bot (herói, thumbnail e Office 365 Connector).</span><span class="sxs-lookup"><span data-stu-id="33718-105">Task modules can be invoked from Microsoft Teams bots using buttons on Adaptive cards and Bot Framework cards (Hero, Thumbnail, and Office 365 Connector).</span></span> <span data-ttu-id="33718-106">Os módulos de tarefas costumam ser uma melhor experiência do usuário do que várias etapas de conversa em que você como desenvolvedor precisa manter o controle do estado do bot e permitir que o usuário interrompa/cancele a sequência.</span><span class="sxs-lookup"><span data-stu-id="33718-106">Task modules are often a better user experience than multiple conversation steps where you as a developer have to keep track of bot state and allow the user to interrupt/cancel the sequence.</span></span>

<span data-ttu-id="33718-107">Há duas maneiras de chamar módulos de tarefa:</span><span class="sxs-lookup"><span data-stu-id="33718-107">There are two ways of invoking task modules:</span></span>

* <span data-ttu-id="33718-108">**Um novo tipo de mensagem de chamada `task/fetch` .**</span><span class="sxs-lookup"><span data-stu-id="33718-108">**A new kind of invoke message `task/fetch`.**</span></span> <span data-ttu-id="33718-109">Usando a `invoke` [ação cartão](~/task-modules-and-cards/cards/cards-actions.md#invoke) para cartões de estrutura de bot ou a `Action.Submit` [ação de cartão](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) para cartões adaptáveis, com `task/fetch` o módulo de tarefa (uma URL ou um cartão adaptável) é buscada dinamicamente no bot.</span><span class="sxs-lookup"><span data-stu-id="33718-109">Using the `invoke` [card action](~/task-modules-and-cards/cards/cards-actions.md#invoke) for Bot Framework cards, or the `Action.Submit` [card action](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) for Adaptive cards, with `task/fetch`, the task module (either a URL or an Adaptive card) is fetched dynamically from your bot.</span></span>
* <span data-ttu-id="33718-110">**URLs de link profundo.**</span><span class="sxs-lookup"><span data-stu-id="33718-110">**Deep link URLs.**</span></span> <span data-ttu-id="33718-111">Usando a [sintaxe de link profundo para módulos de tarefa](~/task-modules-and-cards/what-are-task-modules.md#task-module-deep-link-syntax), você pode usar a `openUrl` [ação cartão](~/task-modules-and-cards/cards/cards-actions.md#openurl) para cartões de estrutura de bot ou a `Action.OpenUrl` [ação de cartão](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) para cartões adaptáveis, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="33718-111">Using the [deep link syntax for task modules](~/task-modules-and-cards/what-are-task-modules.md#task-module-deep-link-syntax), you can use the `openUrl` [card action](~/task-modules-and-cards/cards/cards-actions.md#openurl) for Bot Framework cards or the `Action.OpenUrl` [card action](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) for Adaptive cards, respectively.</span></span> <span data-ttu-id="33718-112">Com URLs de link profundo, a URL do módulo de tarefa ou corpo de cartão adaptável é obviamente conhecido com antecedência, evitando uma viagem de ida e volta ao servidor em relação a `task/fetch` .</span><span class="sxs-lookup"><span data-stu-id="33718-112">With deep link URLs, the task module URL or Adaptive card body is obviously known in advance, avoiding a server round-trip relative to `task/fetch`.</span></span>

>[!IMPORTANT]
><span data-ttu-id="33718-113">Para garantir comunicações seguras, cada `url` `fallbackUrl` uma e deve implementar o protocolo de criptografia HTTPS.</span><span class="sxs-lookup"><span data-stu-id="33718-113">To ensure secure communications, each `url` and `fallbackUrl` must implement the HTTPS encryption protocol.</span></span>

## <a name="invoking-a-task-module-via-taskfetch"></a><span data-ttu-id="33718-114">Invocar um módulo de tarefa por meio de tarefa/busca</span><span class="sxs-lookup"><span data-stu-id="33718-114">Invoking a task module via task/fetch</span></span>

<span data-ttu-id="33718-115">Quando o `value` objeto da `invoke` ação do cartão ou `Action.Submit` é inicializado da forma adequada (explicado em mais detalhes abaixo), quando um usuário pressiona o botão, uma `invoke` mensagem é enviada ao bot.</span><span class="sxs-lookup"><span data-stu-id="33718-115">When the `value` object of the `invoke` card action or `Action.Submit` is initialized in the proper way (explained in more detail below), when a user presses the button an `invoke` message is sent to the bot.</span></span> <span data-ttu-id="33718-116">Na resposta HTTP para a `invoke` mensagem, há um [objeto TaskInfo](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) incorporado em um objeto envoltório, que o Teams usa para exibir o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="33718-116">In the HTTP response to the `invoke` message, there's a [TaskInfo object](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) embedded in a wrapper object, which Teams uses to display the task module.</span></span>

![solicitação/resposta de tarefa/busca](~/assets/images/task-module/task-module-invoke-request-response.png)

<span data-ttu-id="33718-118">Vamos examinar cada etapa mais detalhadamente:</span><span class="sxs-lookup"><span data-stu-id="33718-118">Let's look at each step in a bit more detail:</span></span>

1. <span data-ttu-id="33718-119">Este exemplo mostra um cartão de herói da estrutura de bot com uma `invoke` [ação de cartão](~/task-modules-and-cards/cards/cards-actions.md#invoke)de "comprar".</span><span class="sxs-lookup"><span data-stu-id="33718-119">This example shows a Bot Framework Hero card with a "Buy" `invoke` [card action](~/task-modules-and-cards/cards/cards-actions.md#invoke).</span></span> <span data-ttu-id="33718-120">O valor da `type` propriedade é `task/fetch` : o restante do `value` objeto pode ser o que você quiser.</span><span class="sxs-lookup"><span data-stu-id="33718-120">The value of the `type` property is `task/fetch` - the rest of the `value` object can be whatever you like.</span></span>
2. <span data-ttu-id="33718-121">O bot recebe a `invoke` mensagem http post.</span><span class="sxs-lookup"><span data-stu-id="33718-121">The bot receives the `invoke` HTTP POST message.</span></span>
3. <span data-ttu-id="33718-122">O bot cria um objeto Response e o retorna no corpo da resposta POST com um código de resposta HTTP 200.</span><span class="sxs-lookup"><span data-stu-id="33718-122">The bot creates a response object and returns it in the body of the POST response with an HTTP 200 response code.</span></span> <span data-ttu-id="33718-123">O esquema de respostas é descrito [abaixo na discussão sobre a tarefa/envio](#the-flexibility-of-tasksubmit), mas o importante a ser lembrado agora é que o corpo da resposta http contém um [objeto TaskInfo](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) incorporado em um objeto envoltório, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="33718-123">The schema for responses is described [below in the discussion on task/submit](#the-flexibility-of-tasksubmit), but the important thing to remember now is that the body of the HTTP response contains a [TaskInfo object](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) embedded in a wrapper object, e.g.:</span></span>

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

    <span data-ttu-id="33718-124">O `task/fetch` evento e sua resposta para bots é semelhante, conceitualmente, à `microsoftTeams.tasks.startTask()` função no SDK do cliente.</span><span class="sxs-lookup"><span data-stu-id="33718-124">The `task/fetch` event and its response for bots is similar, conceptually, to the `microsoftTeams.tasks.startTask()` function in the client SDK.</span></span>
4. <span data-ttu-id="33718-125">O Microsoft Teams exibe o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="33718-125">Microsoft Teams displays the task module.</span></span>

## <a name="submitting-the-result-of-a-task-module"></a><span data-ttu-id="33718-126">Enviando o resultado de um módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="33718-126">Submitting the result of a task module</span></span>

<span data-ttu-id="33718-127">Quando o usuário termina com o módulo de tarefa, o envio do resultado para o bot é semelhante [à forma como funciona com guias](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-submitting-the-result-of-a-task-module), mas há algumas diferenças, portanto, é descrito aqui.</span><span class="sxs-lookup"><span data-stu-id="33718-127">When the user is finished with the task module, submitting the result back to the bot is similar [to the way it works with tabs](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-submitting-the-result-of-a-task-module), but there are a few differences, so it's described here too.</span></span>

* <span data-ttu-id="33718-128">**HTML/JavaScript ( `TaskInfo.url` )**.</span><span class="sxs-lookup"><span data-stu-id="33718-128">**HTML/JavaScript (`TaskInfo.url`)**.</span></span> <span data-ttu-id="33718-129">Depois de validar o que o usuário inseriu, chame a `microsoftTeams.tasks.submitTask()` função do SDK (mencionada em diante como `submitTask()` para fins de legibilidade).</span><span class="sxs-lookup"><span data-stu-id="33718-129">Once you've validated what the user has entered, you call the `microsoftTeams.tasks.submitTask()` SDK function (referred to hereafter as `submitTask()` for readability purposes).</span></span> <span data-ttu-id="33718-130">Você pode chamar `submitTask()` sem qualquer parâmetro se quiser que o Microsoft Teams feche o módulo de tarefa, mas a maior parte do tempo desejará passar um objeto ou uma cadeia de caracteres para o seu `submitHandler` .</span><span class="sxs-lookup"><span data-stu-id="33718-130">You can call `submitTask()` without any parameters if you just want Teams to close the task module, but most of the time you'll want to pass an object or a string to your `submitHandler`.</span></span> <span data-ttu-id="33718-131">Basta passá-lo como o primeiro parâmetro `result` .</span><span class="sxs-lookup"><span data-stu-id="33718-131">Simply pass it as the first parameter, `result`.</span></span> <span data-ttu-id="33718-132">O Microsoft Teams invocará `submitHandler` : `err` será `null` e `result` será o objeto/cadeia de caracteres que você deseja `submitTask()` .</span><span class="sxs-lookup"><span data-stu-id="33718-132">Teams will invoke `submitHandler`: `err` will be `null` and `result` will be the object/string you passed to `submitTask()`.</span></span> <span data-ttu-id="33718-133">Se você chamar `submitTask()` com um `result` parâmetro, você **deve** passar um `appId` ou uma matriz de `appId` cadeias de caracteres: isso permite que as equipes validem que o aplicativo enviando o resultado é o mesmo que invocar o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="33718-133">If you do call `submitTask()` with a `result` parameter, you **must** pass an `appId` or an array of `appId` strings: this allows Teams to validate that the app sending the result is the same one which invoked the task module.</span></span> <span data-ttu-id="33718-134">O bot receberá uma `task/submit` mensagem `result` , incluindo as descritas [abaixo](#payload-of-taskfetch-and-tasksubmit-messages).</span><span class="sxs-lookup"><span data-stu-id="33718-134">Your bot will receive a `task/submit` message including `result` as described [below](#payload-of-taskfetch-and-tasksubmit-messages).</span></span>
* <span data-ttu-id="33718-135">**Cartão adaptável ( `TaskInfo.card` )**.</span><span class="sxs-lookup"><span data-stu-id="33718-135">**Adaptive card (`TaskInfo.card`)**.</span></span> <span data-ttu-id="33718-136">O corpo do cartão adaptável (conforme preenchido pelo usuário) será enviado ao bot por meio de uma `task/submit` mensagem quando o usuário pressionar qualquer `Action.Submit` botão.</span><span class="sxs-lookup"><span data-stu-id="33718-136">The Adaptive card body (as filled in by the user) will be sent to the bot via a `task/submit` message when the user presses any `Action.Submit` button.</span></span>

## <a name="the-flexibility-of-tasksubmit"></a><span data-ttu-id="33718-137">A flexibilidade de tarefa/envio</span><span class="sxs-lookup"><span data-stu-id="33718-137">The flexibility of task/submit</span></span>

<span data-ttu-id="33718-138">Na seção anterior, você aprendeu que quando o usuário termina com um módulo de tarefa invocado de um bot, o bot sempre recebe uma `task/submit invoke` mensagem.</span><span class="sxs-lookup"><span data-stu-id="33718-138">In the previous section, you learned that when the user finishes with a task module invoked from a bot, the bot always receives a `task/submit invoke` message.</span></span> <span data-ttu-id="33718-139">Como desenvolvedor, você tem várias opções ao *responder* à `task/submit` mensagem:</span><span class="sxs-lookup"><span data-stu-id="33718-139">As a developer, you have several options when *responding* to the `task/submit` message:</span></span>

| <span data-ttu-id="33718-140">Resposta de corpo HTTP</span><span class="sxs-lookup"><span data-stu-id="33718-140">HTTP Body Response</span></span>                      | <span data-ttu-id="33718-141">Cenário</span><span class="sxs-lookup"><span data-stu-id="33718-141">Scenario</span></span>                                |
| --------------------------------------- | --------------------------------------- |
| <span data-ttu-id="33718-142">Nenhum (ignorar a `task/submit` mensagem)</span><span class="sxs-lookup"><span data-stu-id="33718-142">None (ignore the `task/submit` message)</span></span> | <span data-ttu-id="33718-143">A resposta mais simples é nenhuma resposta.</span><span class="sxs-lookup"><span data-stu-id="33718-143">The simplest response is no response at all.</span></span> <span data-ttu-id="33718-144">O bot não precisa responder quando o usuário termina com o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="33718-144">Your bot is not required to respond when the user is finished with the task module.</span></span> |
| <pre>{<br/>  "task": {<br/>    "type": "message",<br/>    "value": "Message text"<br/>  }<br/>}</pre> | <span data-ttu-id="33718-145">O Microsoft Teams exibirá o valor de `value` em uma caixa de mensagem pop-up.</span><span class="sxs-lookup"><span data-stu-id="33718-145">Teams will display the value of `value` in a popup message box.</span></span> |
| <pre>{<br/>  "task": {<br/>    "type": "continue",<br/>    "value": &lt;TaskInfo object&gt;<br/>  }<br/>}</pre> | <span data-ttu-id="33718-146">Permite que você "encadear" sequências de cartões adaptáveis juntos em uma experiência de assistente/várias etapas.</span><span class="sxs-lookup"><span data-stu-id="33718-146">Allows you to "chain" sequences of Adaptive cards together in a wizard/multi-step experience.</span></span> <span data-ttu-id="33718-147">_Observe que o encadeamento de cartões adaptáveis em uma sequência é um cenário avançado e não está documentado aqui. No entanto, o aplicativo de exemplo Node.js dá suporte a ele e como ele funciona está documentado no [arquivo readme.MD](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs#implementation-notes)._</span><span class="sxs-lookup"><span data-stu-id="33718-147">_Note that chaining Adaptive cards into a sequence is an advanced scenario and not documented here. The Node.js sample app supports it, however, and how it works is documented in [its README.md file](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs#implementation-notes)._</span></span> |

## <a name="payload-of-taskfetch-and-tasksubmit-messages"></a><span data-ttu-id="33718-148">Carga das mensagens de tarefa/busca e de tarefa/envio</span><span class="sxs-lookup"><span data-stu-id="33718-148">Payload of task/fetch and task/submit messages</span></span>

<span data-ttu-id="33718-149">Esta seção define o esquema do que seu bot recebe quando recebe um `task/fetch` objeto de `task/submit` estrutura ou bot `Activity` .</span><span class="sxs-lookup"><span data-stu-id="33718-149">This section defines the schema of what your bot receives when it receives a `task/fetch` or `task/submit` Bot Framework `Activity` object.</span></span> <span data-ttu-id="33718-150">O nível superior importante aparece abaixo:</span><span class="sxs-lookup"><span data-stu-id="33718-150">The important top-level appear below:</span></span>

| <span data-ttu-id="33718-151">Propriedade</span><span class="sxs-lookup"><span data-stu-id="33718-151">Property</span></span> | <span data-ttu-id="33718-152">Descrição</span><span class="sxs-lookup"><span data-stu-id="33718-152">Description</span></span>                          |
| -------- | ------------------------------------ |
| `type`   | <span data-ttu-id="33718-153">Sempre será `invoke`</span><span class="sxs-lookup"><span data-stu-id="33718-153">Will always be `invoke`</span></span>              |
| `name`   | <span data-ttu-id="33718-154">Um `task/fetch` ou `task/submit`</span><span class="sxs-lookup"><span data-stu-id="33718-154">Either `task/fetch` or `task/submit`</span></span> |
| `value`  | <span data-ttu-id="33718-155">A carga definida pelo desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="33718-155">The developer-defined payload.</span></span> <span data-ttu-id="33718-156">Normalmente, a estrutura do `value` objeto espelha o que foi enviado do teams.</span><span class="sxs-lookup"><span data-stu-id="33718-156">Normally the structure of the `value` object mirrors what was sent from Teams.</span></span> <span data-ttu-id="33718-157">Nesse caso, no entanto, é diferente porque queremos oferecer suporte à busca dinâmica ( `task/fetch` ) da estrutura de bot () `value` e ações de cartão adaptável `Action.Submit` ( `data` ), e precisamos de uma maneira de comunicar `context` as equipes ao bot, além do que foi incluído no `value` / `data` .</span><span class="sxs-lookup"><span data-stu-id="33718-157">In this case, however, it's different because we want to support dynamic fetch (`task/fetch`) from both Bot Framework (`value`) and Adaptive card `Action.Submit` actions (`data`), and we need a way to communicate Teams `context` to the bot in addition to what was included in `value`/`data`.</span></span><br/><br/><span data-ttu-id="33718-158">Fazemos isso combinando os dois em um objeto pai:</span><span class="sxs-lookup"><span data-stu-id="33718-158">We do this by combining the two into a parent object:</span></span><br/><br/><pre>{<br/>  "context": {<br/>    "theme": "default" &vert; "dark" &vert; "contrast",<br/>  },<br/>  "data": [value field from Bot Framework card] &vert; [data field from Adaptive Card] <br/>}</pre>  |

## <a name="example-receiving-and-responding-to-taskfetch-and-tasksubmit-invoke-messages---nodejs"></a><span data-ttu-id="33718-159">Exemplo: recebimento e resposta a mensagens/busca e tarefas/envio de invocação de tarefas-Node.js</span><span class="sxs-lookup"><span data-stu-id="33718-159">Example: Receiving and responding to task/fetch and task/submit invoke messages - Node.js</span></span>

> [!NOTE]
> <span data-ttu-id="33718-160">O código de exemplo abaixo foi modificado entre a visualização técnica e a versão final desse recurso: o esquema da `task/fetch` solicitação foi alterado para acompanhar o que foi [documentado na seção anterior](#payload-of-taskfetch-and-tasksubmit-messages).</span><span class="sxs-lookup"><span data-stu-id="33718-160">The sample code below was modified between Technical Preview and final release of this feature: the schema of the `task/fetch` request changed to follow what was [documented in the previous section](#payload-of-taskfetch-and-tasksubmit-messages).</span></span> <span data-ttu-id="33718-161">Ou seja, a documentação estava correta, mas a implementação não foi.</span><span class="sxs-lookup"><span data-stu-id="33718-161">That is, the documentation was correct but the implementation was not.</span></span> <span data-ttu-id="33718-162">Consulte os `// for Technical Preview [...]` comentários abaixo para saber o que foi alterado.</span><span class="sxs-lookup"><span data-stu-id="33718-162">See the `// for Technical Preview [...]` comments below for what changed.</span></span>

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

*See also*, [Microsoft Teams task module sample code — nodejs](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs/blob/master/src/TeamsBot.ts) and  [Bot Framework samples](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).
```
## <a name="example-receiving-and-responding-to-taskfetch-and-tasksubmit-invoke-messages---c"></a><span data-ttu-id="33718-163">Exemplo: recebendo e respondendo a tarefas/buscar e/enviar mensagens de invocação-C #</span><span class="sxs-lookup"><span data-stu-id="33718-163">Example: Receiving and responding to task/fetch and task/submit invoke messages - C#</span></span>

<span data-ttu-id="33718-164">Nos bots do C#, `invoke` as mensagens são processadas por um `HttpResponseMessage()` controlador que processa uma `Activity` mensagem.</span><span class="sxs-lookup"><span data-stu-id="33718-164">In C# bots, `invoke` messages are processed by an `HttpResponseMessage()` controller processing an `Activity` message.</span></span> <span data-ttu-id="33718-165">As `task/fetch` solicitações e as `task/submit` respostas são JSON.</span><span class="sxs-lookup"><span data-stu-id="33718-165">The `task/fetch` and `task/submit` requests and responses are JSON.</span></span> <span data-ttu-id="33718-166">No C#, não é tão conveniente lidar com o JSON bruto como está em Node.js, portanto, você precisa de classes de wrapper para lidar com a serialização de e para JSON.</span><span class="sxs-lookup"><span data-stu-id="33718-166">In C#, it's not as convenient to deal with raw JSON as it is in Node.js, so you need wrapper classes to handle the serialization to and from JSON.</span></span> <span data-ttu-id="33718-167">Ainda não há suporte direto para isso no SDK do Microsoft Teams [C#](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) , mas você pode ver um exemplo de como essas classes de wrapper simples seriam parecidas no [aplicativo de exemplo C#](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Models/TaskModel.cs).</span><span class="sxs-lookup"><span data-stu-id="33718-167">There's no direct support for this in the Microsoft Teams [C# SDK](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) yet, but you can see an example of what these simple wrapper classes would look like in the [C# sample app](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Models/TaskModel.cs).</span></span>

<span data-ttu-id="33718-168">Veja a seguir um exemplo de código em C# para tratamento `task/fetch` e `task/submit` mensagens usando essas classes de wrapper ( `TaskInfo` , `TaskEnvelope` ) extratos da [amostra](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs):</span><span class="sxs-lookup"><span data-stu-id="33718-168">Below is example code in C# for handling `task/fetch` and `task/submit` messages using these wrapper classes (`TaskInfo`, `TaskEnvelope`), excerpted from the [sample](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs):</span></span>

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
```
## <a name="example-receiving-and-responding-to-taskfetch-and-tasksubmit-invoke-messages---python"></a><span data-ttu-id="33718-169">Exemplo: recebendo e respondendo mensagens de tarefa/busca e tarefa/envio de chamadas-Python</span><span class="sxs-lookup"><span data-stu-id="33718-169">Example: Receiving and responding to task/fetch and task/submit invoke messages - Python</span></span>
```
async def on_teams_task_module_fetch(
        self, turn_context: TurnContext, task_module_request: TaskModuleRequest
    ) -> TaskModuleResponse:
        """
        Called when the user selects an options from the displayed HeroCard or
        AdaptiveCard.  The result is the action to perform.
        """

        card_task_fetch_value = task_module_request.data["data"]

        task_info = TaskModuleTaskInfo()
        if card_task_fetch_value == TaskModuleIds.YOUTUBE:
            # Display the YouTube.html page
            task_info.url = task_info.fallback_url = (
                self.__base_url + "/" + TaskModuleIds.YOUTUBE + ".html"
            )
            TeamsTaskModuleBot.__set_task_info(task_info, TaskModuleUIConstants.YOUTUBE)
        elif card_task_fetch_value == TaskModuleIds.CUSTOM_FORM:
            # Display the CustomForm.html page, and post the form data back via
            # on_teams_task_module_submit.
            task_info.url = task_info.fallback_url = (
                self.__base_url + "/" + TaskModuleIds.CUSTOM_FORM + ".html"
            )
            TeamsTaskModuleBot.__set_task_info(
                task_info, TaskModuleUIConstants.CUSTOM_FORM
            )
        elif card_task_fetch_value == TaskModuleIds.ADAPTIVE_CARD:
            # Display an AdaptiveCard to prompt user for text, and post it back via
            # on_teams_task_module_submit.
            task_info.card = TeamsTaskModuleBot.__create_adaptive_card_attachment()
            TeamsTaskModuleBot.__set_task_info(
                task_info, TaskModuleUIConstants.ADAPTIVE_CARD
            )

        return TaskModuleResponseFactory.to_task_module_response(task_info)

    async def on_teams_task_module_submit(
        self, turn_context: TurnContext, task_module_request: TaskModuleRequest
    ) -> TaskModuleResponse:
        """
        Called when data is being returned from the selected option (see `on_teams_task_module_fetch').
        """

        # Echo the users input back.  In a production bot, this is where you'd add behavior in
        # response to the input.
        await turn_context.send_activity(
            MessageFactory.text(
                f"on_teams_task_module_submit: {json.dumps(task_module_request.data)}"
            )
        )

        message_response = TaskModuleMessageResponse(value="Thanks!")
        return TaskModuleResponse(task=message_response)

Not shown in the above example is the `SetTaskInfo()` function, which sets the `height`, `width`, and `title` properties of the `TaskInfo` object for each case. Here's the [source code for SetTaskInfo()](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs).
```
### <a name="bot-framework-card-actions-vs-adaptive-card-actionsubmit-actions"></a><span data-ttu-id="33718-170">Ações de cartão de estrutura de bot versus ação de cartão adaptável. enviar ações</span><span class="sxs-lookup"><span data-stu-id="33718-170">Bot Framework card actions vs. Adaptive card Action.Submit actions</span></span>

<span data-ttu-id="33718-171">O esquema para as ações do cartão de estrutura de bot é um pouco diferente das ações de cartão adaptável `Action.Submit` .</span><span class="sxs-lookup"><span data-stu-id="33718-171">The schema for Bot Framework card actions is slightly different from Adaptive card `Action.Submit` actions.</span></span> <span data-ttu-id="33718-172">Como resultado, a maneira de invocar módulos de tarefa é um pouco diferente: o `data` objeto no `Action.Submit` contém um `msteams` objeto para que ele não interfira com outras propriedades no cartão.</span><span class="sxs-lookup"><span data-stu-id="33718-172">As a result, the way to invoke task modules is slightly different too: the `data` object in `Action.Submit` contains an `msteams` object so it won't interfere with other properties in the card.</span></span> <span data-ttu-id="33718-173">A tabela a seguir mostra um exemplo de cada:</span><span class="sxs-lookup"><span data-stu-id="33718-173">The following table shows an example of each:</span></span>

| <span data-ttu-id="33718-174">Ação do cartão de estrutura de bot</span><span class="sxs-lookup"><span data-stu-id="33718-174">Bot Framework card action</span></span>                              | <span data-ttu-id="33718-175">Ação de cartão adaptável. Submit</span><span class="sxs-lookup"><span data-stu-id="33718-175">Adaptive card Action.Submit action</span></span>                     |
| ------------------------------------------------------ | ------------------------------------------------------ |
| <pre>{<br/>  "type": "invoke",<br/>  "title": "Buy",<br/>  "value": {<br/>    "type": "task/fetch",<br/>    &lt;...&gt;<br/>  }<br/>}</pre> | <pre>{<br/>  "type": "Action.Submit",<br/>  "id": "btnBuy",<br/>  "title": "Buy",<br/>  "data": {<br/>    &lt;...&gt;,<br/>    "msteams": {<br/>      "type": "task/fetch"<br/>    }<br/>  }<br/>}</pre>  |
