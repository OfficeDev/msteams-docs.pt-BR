---
title: Usando módulos de tarefa nos bots do Microsoft Teams
description: Como usar módulos de tarefas com bots do Microsoft Teams, incluindo cartões de estrutura de bot, cartões adaptáveis e links de fundo.
keywords: robôs da equipe de módulos de tarefa
ms.openlocfilehash: 32fb6a4aa0a8bf2297a4f60331dc5c6c6aceb4e2
ms.sourcegitcommit: 214eccbadb7f3a67236b79a041ef487b7bf6dfbd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "44800992"
---
# <a name="using-task-modules-from-microsoft-teams-bots"></a><span data-ttu-id="f7955-104">Usando módulos de tarefa dos bots do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="f7955-104">Using task modules from Microsoft Teams bots</span></span>

<span data-ttu-id="f7955-105">Os módulos de tarefa podem ser invocados de bots do Microsoft Teams usando botões em cartões adaptáveis e cartões de estrutura de bot (herói, thumbnail e Office 365 Connector).</span><span class="sxs-lookup"><span data-stu-id="f7955-105">Task modules can be invoked from Microsoft Teams bots using buttons on Adaptive cards and Bot Framework cards (Hero, Thumbnail, and Office 365 Connector).</span></span> <span data-ttu-id="f7955-106">Os módulos de tarefas costumam ser uma melhor experiência do usuário do que várias etapas de conversa em que você como desenvolvedor precisa manter o controle do estado do bot e permitir que o usuário interrompa/cancele a sequência.</span><span class="sxs-lookup"><span data-stu-id="f7955-106">Task modules are often a better user experience than multiple conversation steps where you as a developer have to keep track of bot state and allow the user to interrupt/cancel the sequence.</span></span>

<span data-ttu-id="f7955-107">Há duas maneiras de chamar módulos de tarefa:</span><span class="sxs-lookup"><span data-stu-id="f7955-107">There are two ways of invoking task modules:</span></span>

* <span data-ttu-id="f7955-108">**Um novo tipo de mensagem de chamada `task/fetch` .**</span><span class="sxs-lookup"><span data-stu-id="f7955-108">**A new kind of invoke message `task/fetch`.**</span></span> <span data-ttu-id="f7955-109">Usando a `invoke` [ação cartão](~/task-modules-and-cards/cards/cards-actions.md#invoke) para cartões de estrutura de bot ou a `Action.Submit` [ação de cartão](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) para cartões adaptáveis, com `task/fetch` o módulo de tarefa (uma URL ou um cartão adaptável) é buscada dinamicamente no bot.</span><span class="sxs-lookup"><span data-stu-id="f7955-109">Using the `invoke` [card action](~/task-modules-and-cards/cards/cards-actions.md#invoke) for Bot Framework cards, or the `Action.Submit` [card action](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) for Adaptive cards, with `task/fetch`, the task module (either a URL or an Adaptive card) is fetched dynamically from your bot.</span></span>
* <span data-ttu-id="f7955-110">**URLs de link profundo.**</span><span class="sxs-lookup"><span data-stu-id="f7955-110">**Deep link URLs.**</span></span> <span data-ttu-id="f7955-111">Usando a [sintaxe de link profundo para módulos de tarefa](~/task-modules-and-cards/what-are-task-modules.md#task-module-deep-link-syntax), você pode usar a `openUrl` [ação cartão](~/task-modules-and-cards/cards/cards-actions.md#openurl) para cartões de estrutura de bot ou a `Action.OpenUrl` [ação de cartão](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) para cartões adaptáveis, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="f7955-111">Using the [deep link syntax for task modules](~/task-modules-and-cards/what-are-task-modules.md#task-module-deep-link-syntax), you can use the `openUrl` [card action](~/task-modules-and-cards/cards/cards-actions.md#openurl) for Bot Framework cards or the `Action.OpenUrl` [card action](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) for Adaptive cards, respectively.</span></span> <span data-ttu-id="f7955-112">Com URLs de link profundo, a URL do módulo de tarefa ou corpo de cartão adaptável é obviamente conhecido com antecedência, evitando uma viagem de ida e volta ao servidor em relação a `task/fetch` .</span><span class="sxs-lookup"><span data-stu-id="f7955-112">With deep link URLs, the task module URL or Adaptive card body is obviously known in advance, avoiding a server round-trip relative to `task/fetch`.</span></span>

>[!IMPORTANT]
><span data-ttu-id="f7955-113">Para garantir comunicações seguras, cada `url` `fallbackUrl` uma e deve implementar o protocolo de criptografia HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f7955-113">To ensure secure communications, each `url` and `fallbackUrl` must implement the HTTPS encryption protocol.</span></span>

## <a name="invoking-a-task-module-via-taskfetch"></a><span data-ttu-id="f7955-114">Invocar um módulo de tarefa por meio de tarefa/busca</span><span class="sxs-lookup"><span data-stu-id="f7955-114">Invoking a task module via task/fetch</span></span>

<span data-ttu-id="f7955-115">Quando o `value` objeto da `invoke` ação do cartão ou `Action.Submit` é inicializado da forma adequada (explicado em mais detalhes abaixo), quando um usuário pressiona o botão, uma `invoke` mensagem é enviada ao bot.</span><span class="sxs-lookup"><span data-stu-id="f7955-115">When the `value` object of the `invoke` card action or `Action.Submit` is initialized in the proper way (explained in more detail below), when a user presses the button an `invoke` message is sent to the bot.</span></span> <span data-ttu-id="f7955-116">Na resposta HTTP para a `invoke` mensagem, há um [objeto TaskInfo](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) incorporado em um objeto envoltório, que o Teams usa para exibir o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="f7955-116">In the HTTP response to the `invoke` message, there's a [TaskInfo object](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) embedded in a wrapper object, which Teams uses to display the task module.</span></span>

![solicitação/resposta de tarefa/busca](~/assets/images/task-module/task-module-invoke-request-response.png)

<span data-ttu-id="f7955-118">Vamos examinar cada etapa mais detalhadamente:</span><span class="sxs-lookup"><span data-stu-id="f7955-118">Let's look at each step in a bit more detail:</span></span>

1. <span data-ttu-id="f7955-119">Este exemplo mostra um cartão de herói da estrutura de bot com uma `invoke` [ação de cartão](~/task-modules-and-cards/cards/cards-actions.md#invoke)de "comprar".</span><span class="sxs-lookup"><span data-stu-id="f7955-119">This example shows a Bot Framework Hero card with a "Buy" `invoke` [card action](~/task-modules-and-cards/cards/cards-actions.md#invoke).</span></span> <span data-ttu-id="f7955-120">O valor da `type` propriedade é `task/fetch` : o restante do `value` objeto pode ser o que você quiser.</span><span class="sxs-lookup"><span data-stu-id="f7955-120">The value of the `type` property is `task/fetch` - the rest of the `value` object can be whatever you like.</span></span>
2. <span data-ttu-id="f7955-121">O bot recebe a `invoke` mensagem http post.</span><span class="sxs-lookup"><span data-stu-id="f7955-121">The bot receives the `invoke` HTTP POST message.</span></span>
3. <span data-ttu-id="f7955-122">O bot cria um objeto Response e o retorna no corpo da resposta POST com um código de resposta HTTP 200.</span><span class="sxs-lookup"><span data-stu-id="f7955-122">The bot creates a response object and returns it in the body of the POST response with an HTTP 200 response code.</span></span> <span data-ttu-id="f7955-123">O esquema de respostas é descrito [abaixo na discussão sobre a tarefa/envio](#the-flexibility-of-tasksubmit), mas o importante a ser lembrado agora é que o corpo da resposta http contém um [objeto TaskInfo](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) incorporado em um objeto envoltório, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="f7955-123">The schema for responses is described [below in the discussion on task/submit](#the-flexibility-of-tasksubmit), but the important thing to remember now is that the body of the HTTP response contains a [TaskInfo object](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) embedded in a wrapper object, e.g.:</span></span>

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

    <span data-ttu-id="f7955-124">O `task/fetch` evento e sua resposta para bots é semelhante, conceitualmente, à `microsoftTeams.tasks.startTask()` função no SDK do cliente.</span><span class="sxs-lookup"><span data-stu-id="f7955-124">The `task/fetch` event and its response for bots is similar, conceptually, to the `microsoftTeams.tasks.startTask()` function in the client SDK.</span></span>
4. <span data-ttu-id="f7955-125">O Microsoft Teams exibe o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="f7955-125">Microsoft Teams displays the task module.</span></span>

## <a name="submitting-the-result-of-a-task-module"></a><span data-ttu-id="f7955-126">Enviando o resultado de um módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="f7955-126">Submitting the result of a task module</span></span>

<span data-ttu-id="f7955-127">Quando o usuário termina com o módulo de tarefa, o envio do resultado para o bot é semelhante [à forma como funciona com guias](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-submitting-the-result-of-a-task-module), mas há algumas diferenças, portanto, é descrito aqui.</span><span class="sxs-lookup"><span data-stu-id="f7955-127">When the user is finished with the task module, submitting the result back to the bot is similar [to the way it works with tabs](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-submitting-the-result-of-a-task-module), but there are a few differences, so it's described here too.</span></span>

* <span data-ttu-id="f7955-128">**HTML/JavaScript ( `TaskInfo.url` )**.</span><span class="sxs-lookup"><span data-stu-id="f7955-128">**HTML/JavaScript (`TaskInfo.url`)**.</span></span> <span data-ttu-id="f7955-129">Depois de validar o que o usuário inseriu, chame a `microsoftTeams.tasks.submitTask()` função do SDK (mencionada em diante como `submitTask()` para fins de legibilidade).</span><span class="sxs-lookup"><span data-stu-id="f7955-129">Once you've validated what the user has entered, you call the `microsoftTeams.tasks.submitTask()` SDK function (referred to hereafter as `submitTask()` for readability purposes).</span></span> <span data-ttu-id="f7955-130">Você pode chamar `submitTask()` sem qualquer parâmetro se quiser que o Microsoft Teams feche o módulo de tarefa, mas a maior parte do tempo desejará passar um objeto ou uma cadeia de caracteres para o seu `submitHandler` .</span><span class="sxs-lookup"><span data-stu-id="f7955-130">You can call `submitTask()` without any parameters if you just want Teams to close the task module, but most of the time you'll want to pass an object or a string to your `submitHandler`.</span></span> <span data-ttu-id="f7955-131">Basta passá-lo como o primeiro parâmetro `result` .</span><span class="sxs-lookup"><span data-stu-id="f7955-131">Simply pass it as the first parameter, `result`.</span></span> <span data-ttu-id="f7955-132">O Microsoft Teams invocará `submitHandler` : `err` será `null` e `result` será o objeto/cadeia de caracteres que você deseja `submitTask()` .</span><span class="sxs-lookup"><span data-stu-id="f7955-132">Teams will invoke `submitHandler`: `err` will be `null` and `result` will be the object/string you passed to `submitTask()`.</span></span> <span data-ttu-id="f7955-133">Se você chamar `submitTask()` com um `result` parâmetro, você **deve** passar um `appId` ou uma matriz de `appId` cadeias de caracteres: isso permite que as equipes validem que o aplicativo enviando o resultado é o mesmo que invocar o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="f7955-133">If you do call `submitTask()` with a `result` parameter, you **must** pass an `appId` or an array of `appId` strings: this allows Teams to validate that the app sending the result is the same one which invoked the task module.</span></span> <span data-ttu-id="f7955-134">O bot receberá uma `task/submit` mensagem `result` , incluindo as descritas [abaixo](#payload-of-taskfetch-and-tasksubmit-messages).</span><span class="sxs-lookup"><span data-stu-id="f7955-134">Your bot will receive a `task/submit` message including `result` as described [below](#payload-of-taskfetch-and-tasksubmit-messages).</span></span>
* <span data-ttu-id="f7955-135">**Cartão adaptável ( `TaskInfo.card` )**.</span><span class="sxs-lookup"><span data-stu-id="f7955-135">**Adaptive card (`TaskInfo.card`)**.</span></span> <span data-ttu-id="f7955-136">O corpo do cartão adaptável (conforme preenchido pelo usuário) será enviado ao bot por meio de uma `task/submit` mensagem quando o usuário pressionar qualquer `Action.Submit` botão.</span><span class="sxs-lookup"><span data-stu-id="f7955-136">The Adaptive card body (as filled in by the user) will be sent to the bot via a `task/submit` message when the user presses any `Action.Submit` button.</span></span>

## <a name="the-flexibility-of-tasksubmit"></a><span data-ttu-id="f7955-137">A flexibilidade de tarefa/envio</span><span class="sxs-lookup"><span data-stu-id="f7955-137">The flexibility of task/submit</span></span>

<span data-ttu-id="f7955-138">Na seção anterior, você aprendeu que quando o usuário termina com um módulo de tarefa invocado de um bot, o bot sempre recebe uma `task/submit invoke` mensagem.</span><span class="sxs-lookup"><span data-stu-id="f7955-138">In the previous section, you learned that when the user finishes with a task module invoked from a bot, the bot always receives a `task/submit invoke` message.</span></span> <span data-ttu-id="f7955-139">Como desenvolvedor, você tem várias opções ao *responder* à `task/submit` mensagem:</span><span class="sxs-lookup"><span data-stu-id="f7955-139">As a developer, you have several options when *responding* to the `task/submit` message:</span></span>

| <span data-ttu-id="f7955-140">Resposta de corpo HTTP</span><span class="sxs-lookup"><span data-stu-id="f7955-140">HTTP Body Response</span></span>                      | <span data-ttu-id="f7955-141">Cenário</span><span class="sxs-lookup"><span data-stu-id="f7955-141">Scenario</span></span>                                |
| --------------------------------------- | --------------------------------------- |
| <span data-ttu-id="f7955-142">Nenhum (ignorar a `task/submit` mensagem)</span><span class="sxs-lookup"><span data-stu-id="f7955-142">None (ignore the `task/submit` message)</span></span> | <span data-ttu-id="f7955-143">A resposta mais simples é nenhuma resposta.</span><span class="sxs-lookup"><span data-stu-id="f7955-143">The simplest response is no response at all.</span></span> <span data-ttu-id="f7955-144">O bot não precisa responder quando o usuário termina com o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="f7955-144">Your bot is not required to respond when the user is finished with the task module.</span></span> |
| <pre>{<br/>  "task": {<br/>    "type": "message",<br/>    "value": "Message text"<br/>  }<br/>}</pre> | <span data-ttu-id="f7955-145">O Microsoft Teams exibirá o valor de `value` em uma caixa de mensagem pop-up.</span><span class="sxs-lookup"><span data-stu-id="f7955-145">Teams will display the value of `value` in a popup message box.</span></span> |
| <pre>{<br/>  "task": {<br/>    "type": "continue",<br/>    "value": &lt;TaskInfo object&gt;<br/>  }<br/>}</pre> | <span data-ttu-id="f7955-146">Permite que você "encadear" sequências de cartões adaptáveis juntos em uma experiência de assistente/várias etapas.</span><span class="sxs-lookup"><span data-stu-id="f7955-146">Allows you to "chain" sequences of Adaptive cards together in a wizard/multi-step experience.</span></span> <span data-ttu-id="f7955-147">_Observe que o encadeamento de cartões adaptáveis em uma sequência é um cenário avançado e não está documentado aqui. No entanto, o aplicativo de exemplo Node.js dá suporte a ele e como ele funciona está documentado no [arquivo readme.MD](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs#implementation-notes)._</span><span class="sxs-lookup"><span data-stu-id="f7955-147">_Note that chaining Adaptive cards into a sequence is an advanced scenario and not documented here. The Node.js sample app supports it, however, and how it works is documented in [its README.md file](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs#implementation-notes)._</span></span> |

## <a name="payload-of-taskfetch-and-tasksubmit-messages"></a><span data-ttu-id="f7955-148">Carga das mensagens de tarefa/busca e de tarefa/envio</span><span class="sxs-lookup"><span data-stu-id="f7955-148">Payload of task/fetch and task/submit messages</span></span>

<span data-ttu-id="f7955-149">Esta seção define o esquema do que seu bot recebe quando recebe um `task/fetch` objeto de `task/submit` estrutura ou bot `Activity` .</span><span class="sxs-lookup"><span data-stu-id="f7955-149">This section defines the schema of what your bot receives when it receives a `task/fetch` or `task/submit` Bot Framework `Activity` object.</span></span> <span data-ttu-id="f7955-150">O nível superior importante aparece abaixo:</span><span class="sxs-lookup"><span data-stu-id="f7955-150">The important top-level appear below:</span></span>

| <span data-ttu-id="f7955-151">Propriedade</span><span class="sxs-lookup"><span data-stu-id="f7955-151">Property</span></span> | <span data-ttu-id="f7955-152">Descrição</span><span class="sxs-lookup"><span data-stu-id="f7955-152">Description</span></span>                          |
| -------- | ------------------------------------ |
| `type`   | <span data-ttu-id="f7955-153">Sempre será`invoke`</span><span class="sxs-lookup"><span data-stu-id="f7955-153">Will always be `invoke`</span></span>              |
| `name`   | <span data-ttu-id="f7955-154">Um `task/fetch` ou`task/submit`</span><span class="sxs-lookup"><span data-stu-id="f7955-154">Either `task/fetch` or `task/submit`</span></span> |
| `value`  | <span data-ttu-id="f7955-155">A carga definida pelo desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="f7955-155">The developer-defined payload.</span></span> <span data-ttu-id="f7955-156">Normalmente, a estrutura do `value` objeto espelha o que foi enviado do teams.</span><span class="sxs-lookup"><span data-stu-id="f7955-156">Normally the structure of the `value` object mirrors what was sent from Teams.</span></span> <span data-ttu-id="f7955-157">Nesse caso, no entanto, é diferente porque queremos oferecer suporte à busca dinâmica ( `task/fetch` ) da estrutura de bot () `value` e ações de cartão adaptável `Action.Submit` ( `data` ), e precisamos de uma maneira de comunicar `context` as equipes ao bot, além do que foi incluído no `value` / `data` .</span><span class="sxs-lookup"><span data-stu-id="f7955-157">In this case, however, it's different because we want to support dynamic fetch (`task/fetch`) from both Bot Framework (`value`) and Adaptive card `Action.Submit` actions (`data`), and we need a way to communicate Teams `context` to the bot in addition to what was included in `value`/`data`.</span></span><br/><br/><span data-ttu-id="f7955-158">Fazemos isso combinando os dois em um objeto pai:</span><span class="sxs-lookup"><span data-stu-id="f7955-158">We do this by combining the two into a parent object:</span></span><br/><br/><pre>{<br/>  "context": {<br/>    "theme": "default" &vert; "dark" &vert; "contrast",<br/>  },<br/>  "data": [value field from Bot Framework card] &vert; [data field from Adaptive Card] <br/>}</pre>  |

## <a name="example-receiving-and-responding-to-taskfetch-and-tasksubmit-invoke-messages---nodejs"></a><span data-ttu-id="f7955-159">Exemplo: recebimento e resposta a mensagens/busca e tarefas/envio de invocação de tarefas-Node.js</span><span class="sxs-lookup"><span data-stu-id="f7955-159">Example: Receiving and responding to task/fetch and task/submit invoke messages - Node.js</span></span>

> [!NOTE]
> <span data-ttu-id="f7955-160">O código de exemplo abaixo foi modificado entre a visualização técnica e a versão final desse recurso: o esquema da `task/fetch` solicitação foi alterado para acompanhar o que foi [documentado na seção anterior](#payload-of-taskfetch-and-tasksubmit-messages).</span><span class="sxs-lookup"><span data-stu-id="f7955-160">The sample code below was modified between Technical Preview and final release of this feature: the schema of the `task/fetch` request changed to follow what was [documented in the previous section](#payload-of-taskfetch-and-tasksubmit-messages).</span></span> <span data-ttu-id="f7955-161">Ou seja, a documentação estava correta, mas a implementação não foi.</span><span class="sxs-lookup"><span data-stu-id="f7955-161">That is, the documentation was correct but the implementation was not.</span></span> <span data-ttu-id="f7955-162">Consulte os `// for Technical Preview [...]` comentários abaixo para saber o que foi alterado.</span><span class="sxs-lookup"><span data-stu-id="f7955-162">See the `// for Technical Preview [...]` comments below for what changed.</span></span>

```typescript
// Handle requests and responses for a "Custom Form" and an "Adaptive card" task module.
// Assumes request is coming from an Adaptive card Action.Submit button that has a "taskModule" property indicating what to invoke
private async onInvoke(event: builder.IEvent, cb: (err: Error, body: any, status?: number) => void): Promise<void> {
    let invokeType = (event as any).name;
    let invokeValue = (event as any).value;
    if (invokeType === undefined) {
        invokeType = null;
    }
    switch (invokeType) {
        case "task/fetch": {
            if (invokeValue !== undefined && invokeValue.data.taskModule === "customform") { // for Technical Preview, was invokeValue.taskModule
                // Return the specified task module response to the bot
                let fetchTemplate: any = {
                    "task": {
                        "type": "continue",
                        "value": {
                            "title": "Custom Form",
                            "height": 510,
                            "width": 430,
                            "fallbackUrl": "https://contoso.com/teamsapp/customform",
                            "url": "https://contoso.com/teamsapp/customform",
                        }
                    }
                };
                cb(null, fetchTemplate, 200);
            };
            if (invokeValue !== undefined && invokeValue.data.taskModule === "adaptivecard") { // for Technical Preview, was invokeValue.taskModule
                let adaptiveCard = {
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
                };
                // Return the specified task module response to the bot
                let fetchTemplate: any = {
                    "task": {
                        "type": "continue",
                        "value": {
                            "title": "Ninja Cat",
                            "height": "small",
                            "width": "small",
                            "card": {
                                contentType: "application/vnd.microsoft.card.adaptive",
                                content: adaptiveCard,
                            }
                        }
                    }
                };
                cb(null, fetchTemplate, 200);
            };
            break;
        }
        case "task/submit": {
            if (invokeValue.data !== undefined) {
                // It's a valid task module response
                let submitResponse: any = {
                    "task": {
                        "type": "message",
                        "value": "Task complete!",
                    }
                };
                cb(null, fetchTemplates.submitMessageResponse, 200)
            }
        }
    }
}
```

<span data-ttu-id="f7955-163">*Consulte também*, [código de exemplo do módulo de tarefa do Microsoft Teams —](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs/blob/master/src/TeamsBot.ts) amostras de NodeJS e [bot Framework](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).</span><span class="sxs-lookup"><span data-stu-id="f7955-163">*See also*, [Microsoft Teams task module sample code — nodejs](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs/blob/master/src/TeamsBot.ts) and  [Bot Framework samples](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).</span></span>

## <a name="example-receiving-and-responding-to-taskfetch-and-tasksubmit-invoke-messages---c"></a><span data-ttu-id="f7955-164">Exemplo: recebendo e respondendo a tarefas/buscar e/enviar mensagens de invocação-C #</span><span class="sxs-lookup"><span data-stu-id="f7955-164">Example: Receiving and responding to task/fetch and task/submit invoke messages - C#</span></span>

<span data-ttu-id="f7955-165">Nos bots do C#, `invoke` as mensagens são processadas por um `HttpResponseMessage()` controlador que processa uma `Activity` mensagem.</span><span class="sxs-lookup"><span data-stu-id="f7955-165">In C# bots, `invoke` messages are processed by an `HttpResponseMessage()` controller processing an `Activity` message.</span></span> <span data-ttu-id="f7955-166">As `task/fetch` solicitações e as `task/submit` respostas são JSON.</span><span class="sxs-lookup"><span data-stu-id="f7955-166">The `task/fetch` and `task/submit` requests and responses are JSON.</span></span> <span data-ttu-id="f7955-167">No C#, não é tão conveniente lidar com o JSON bruto como está em Node.js, portanto, você precisa de classes de wrapper para lidar com a serialização de e para JSON.</span><span class="sxs-lookup"><span data-stu-id="f7955-167">In C#, it's not as convenient to deal with raw JSON as it is in Node.js, so you need wrapper classes to handle the serialization to and from JSON.</span></span> <span data-ttu-id="f7955-168">Ainda não há suporte direto para isso no SDK do Microsoft Teams [C#](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) , mas você pode ver um exemplo de como essas classes de wrapper simples seriam parecidas no [aplicativo de exemplo C#](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Models/TaskModel.cs).</span><span class="sxs-lookup"><span data-stu-id="f7955-168">There's no direct support for this in the Microsoft Teams [C# SDK](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) yet, but you can see an example of what these simple wrapper classes would look like in the [C# sample app](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Models/TaskModel.cs).</span></span>

<span data-ttu-id="f7955-169">Veja a seguir um exemplo de código em C# para tratamento `task/fetch` e `task/submit` mensagens usando essas classes de wrapper ( `TaskInfo` , `TaskEnvelope` ) extratos da [amostra](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs):</span><span class="sxs-lookup"><span data-stu-id="f7955-169">Below is example code in C# for handling `task/fetch` and `task/submit` messages using these wrapper classes (`TaskInfo`, `TaskEnvelope`), excerpted from the [sample](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs):</span></span>

```csharp
private HttpResponseMessage HandleInvokeMessages(Activity activity)
{
    var activityValue = activity.Value.ToString();
    if (activity.Name == "task/fetch")
    {
        var action = Newtonsoft.Json.JsonConvert.DeserializeObject<Models.BotFrameworkCardValue<string>>(activityValue);

        Models.TaskInfo taskInfo = GetTaskInfo(action.Data);
        Models.TaskEnvelope taskEnvelope = new Models.TaskEnvelope
        {
            Task = new Models.Task()
            {
                Type = Models.TaskType.Continue,
                TaskInfo = taskInfo
            }
        };
        return Request.CreateResponse(HttpStatusCode.OK, taskEnvelope);
    }
    else if (activity.Name == "task/submit")
    {
        ConnectorClient connector = new ConnectorClient(new Uri(activity.ServiceUrl));
        Activity reply = activity.CreateReply("Received = " + activity.Value.ToString());
        connector.Conversations.ReplyToActivity(reply);
    }
    return new HttpResponseMessage(HttpStatusCode.Accepted);
}

// Helper function for building the TaskInfo object based on the incoming request
private static Models.TaskInfo GetTaskInfo(string actionInfo)
{
    Models.TaskInfo taskInfo = new Models.TaskInfo();
    switch (actionInfo)
    {
        case TaskModuleIds.YouTube:
            taskInfo.Url = taskInfo.FallbackUrl = ApplicationSettings.BaseUrl + "/" + TaskModuleIds.YouTube;
            SetTaskInfo(taskInfo, TaskModuleUIConstants.YouTube);
            break;
        case TaskModuleIds.PowerApp:
            taskInfo.Url = taskInfo.FallbackUrl = ApplicationSettings.BaseUrl + "/" + TaskModuleIds.PowerApp;
            SetTaskInfo(taskInfo, TaskModuleUIConstants.PowerApp);
            break;
        case TaskModuleIds.CustomForm:
            taskInfo.Url = taskInfo.FallbackUrl = ApplicationSettings.BaseUrl + "/" + TaskModuleIds.CustomForm;
            SetTaskInfo(taskInfo, TaskModuleUIConstants.CustomForm);
            break;
        case TaskModuleIds.AdaptiveCard:
            taskInfo.Card = AdaptiveCardHelper.GetAdaptiveCard();
            SetTaskInfo(taskInfo, TaskModuleUIConstants.AdaptiveCard);
            break;
        default:
            break;
    }
    return taskInfo;
}
```

<span data-ttu-id="f7955-170">Não mostrado no exemplo acima é a `SetTaskInfo()` função, que define as `height` Propriedades, `width` e `title` do `TaskInfo` objeto para cada caso.</span><span class="sxs-lookup"><span data-stu-id="f7955-170">Not shown in the above example is the `SetTaskInfo()` function, which sets the `height`, `width`, and `title` properties of the `TaskInfo` object for each case.</span></span> <span data-ttu-id="f7955-171">Este é o [código-fonte do SetTaskInfo ()](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs).</span><span class="sxs-lookup"><span data-stu-id="f7955-171">Here's the [source code for SetTaskInfo()](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs).</span></span>

### <a name="bot-framework-card-actions-vs-adaptive-card-actionsubmit-actions"></a><span data-ttu-id="f7955-172">Ações de cartão de estrutura de bot versus ação de cartão adaptável. enviar ações</span><span class="sxs-lookup"><span data-stu-id="f7955-172">Bot Framework card actions vs. Adaptive card Action.Submit actions</span></span>

<span data-ttu-id="f7955-173">O esquema para as ações do cartão de estrutura de bot é um pouco diferente das ações de cartão adaptável `Action.Submit` .</span><span class="sxs-lookup"><span data-stu-id="f7955-173">The schema for Bot Framework card actions is slightly different from Adaptive card `Action.Submit` actions.</span></span> <span data-ttu-id="f7955-174">Como resultado, a maneira de invocar módulos de tarefa é um pouco diferente: o `data` objeto no `Action.Submit` contém um `msteams` objeto para que ele não interfira com outras propriedades no cartão.</span><span class="sxs-lookup"><span data-stu-id="f7955-174">As a result, the way to invoke task modules is slightly different too: the `data` object in `Action.Submit` contains an `msteams` object so it won't interfere with other properties in the card.</span></span> <span data-ttu-id="f7955-175">A tabela a seguir mostra um exemplo de cada:</span><span class="sxs-lookup"><span data-stu-id="f7955-175">The following table shows an example of each:</span></span>

| <span data-ttu-id="f7955-176">Ação do cartão de estrutura de bot</span><span class="sxs-lookup"><span data-stu-id="f7955-176">Bot Framework card action</span></span>                              | <span data-ttu-id="f7955-177">Ação de cartão adaptável. Submit</span><span class="sxs-lookup"><span data-stu-id="f7955-177">Adaptive card Action.Submit action</span></span>                     |
| ------------------------------------------------------ | ------------------------------------------------------ |
| <pre>{<br/>  "type": "invoke",<br/>  "title": "Buy",<br/>  "value": {<br/>    "type": "task/fetch",<br/>    &lt;...&gt;<br/>  }<br/>}</pre> | <pre>{<br/>  "type": "Action.Submit",<br/>  "id": "btnBuy",<br/>  "title": "Buy",<br/>  "data": {<br/>    &lt;...&gt;,<br/>    "msteams": {<br/>      "type": "task/fetch"<br/>    }<br/>  }<br/>}</pre>  |
