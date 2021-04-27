---
title: Usando módulos de tarefa em bots do Microsoft Teams
description: Como usar módulos de tarefa com bots do Microsoft Teams, incluindo cartões da Estrutura de Bot, cartões adaptáveis e links profundos
localization_priority: Normal
ms.topic: how-to
keywords: bots de equipes de módulos de tarefa
ms.openlocfilehash: 948af0c71acb20f4d84fa25ba79618045dad9da7
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020272"
---
# <a name="using-task-modules-from-microsoft-teams-bots"></a><span data-ttu-id="8fa2a-104">Usando módulos de tarefas de bots do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="8fa2a-104">Using task modules from Microsoft Teams bots</span></span>

<span data-ttu-id="8fa2a-105">Os módulos de tarefa podem ser invocados de bots do Microsoft Teams usando botões em cartões adaptáveis e cartões de Estrutura de Bot (Hero, Thumbnail e Office 365 Connector).</span><span class="sxs-lookup"><span data-stu-id="8fa2a-105">Task modules can be invoked from Microsoft Teams bots using buttons on Adaptive cards and Bot Framework cards (Hero, Thumbnail, and Office 365 Connector).</span></span> <span data-ttu-id="8fa2a-106">Os módulos de tarefas geralmente são uma experiência de usuário melhor do que várias etapas de conversa em que você, como desenvolvedor, precisa controlar o estado do bot e permitir que o usuário interrompa/cancele a sequência.</span><span class="sxs-lookup"><span data-stu-id="8fa2a-106">Task modules are often a better user experience than multiple conversation steps where you as a developer have to keep track of bot state and allow the user to interrupt/cancel the sequence.</span></span>

<span data-ttu-id="8fa2a-107">Há duas maneiras de invocar módulos de tarefa:</span><span class="sxs-lookup"><span data-stu-id="8fa2a-107">There are two ways of invoking task modules:</span></span>

* <span data-ttu-id="8fa2a-108">**Um novo tipo de mensagem de `task/fetch` invocação.**</span><span class="sxs-lookup"><span data-stu-id="8fa2a-108">**A new kind of invoke message `task/fetch`.**</span></span> <span data-ttu-id="8fa2a-109">Usar a ação de cartão para cartões da Estrutura de Bot ou a ação de cartão para cartões adaptáveis, com , o módulo de tarefa (uma URL ou um cartão `invoke` [](~/task-modules-and-cards/cards/cards-actions.md#invoke) `Action.Submit` [](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) adaptável) é buscado dinamicamente no `task/fetch` bot.</span><span class="sxs-lookup"><span data-stu-id="8fa2a-109">Using the `invoke` [card action](~/task-modules-and-cards/cards/cards-actions.md#invoke) for Bot Framework cards, or the `Action.Submit` [card action](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) for Adaptive cards, with `task/fetch`, the task module (either a URL or an Adaptive card) is fetched dynamically from your bot.</span></span>
* <span data-ttu-id="8fa2a-110">**URLs de link profundo.**</span><span class="sxs-lookup"><span data-stu-id="8fa2a-110">**Deep link URLs.**</span></span> <span data-ttu-id="8fa2a-111">Usando a sintaxe de link profundo para [módulos](~/task-modules-and-cards/what-are-task-modules.md#task-module-deep-link-syntax)de tarefa, você pode usar a ação de cartão para cartões da Estrutura de Bot ou a ação de cartão para cartões `openUrl` [](~/task-modules-and-cards/cards/cards-actions.md#openurl) `Action.OpenUrl` [](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) adaptáveis, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="8fa2a-111">Using the [deep link syntax for task modules](~/task-modules-and-cards/what-are-task-modules.md#task-module-deep-link-syntax), you can use the `openUrl` [card action](~/task-modules-and-cards/cards/cards-actions.md#openurl) for Bot Framework cards or the `Action.OpenUrl` [card action](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) for Adaptive cards, respectively.</span></span> <span data-ttu-id="8fa2a-112">Com URLs de link profundo, a URL do módulo de tarefas ou o corpo do cartão adaptável é obviamente conhecido antecipadamente, evitando uma ida e volta do servidor em relação a `task/fetch` .</span><span class="sxs-lookup"><span data-stu-id="8fa2a-112">With deep link URLs, the task module URL or Adaptive card body is obviously known in advance, avoiding a server round-trip relative to `task/fetch`.</span></span>

>[!IMPORTANT]
><span data-ttu-id="8fa2a-113">Para garantir comunicações seguras, cada `url` um deles e deve implementar o protocolo de criptografia `fallbackUrl` HTTPS.</span><span class="sxs-lookup"><span data-stu-id="8fa2a-113">To ensure secure communications, each `url` and `fallbackUrl` must implement the HTTPS encryption protocol.</span></span>

## <a name="invoking-a-task-module-via-taskfetch"></a><span data-ttu-id="8fa2a-114">Invocar um módulo de tarefa por meio de tarefa/busca</span><span class="sxs-lookup"><span data-stu-id="8fa2a-114">Invoking a task module via task/fetch</span></span>

<span data-ttu-id="8fa2a-115">Quando o objeto da ação do cartão ou é inicializado da maneira adequada (explicado em mais detalhes abaixo), quando um usuário pressiona o botão, uma mensagem é enviada `value` `invoke` para o `Action.Submit` `invoke` bot.</span><span class="sxs-lookup"><span data-stu-id="8fa2a-115">When the `value` object of the `invoke` card action or `Action.Submit` is initialized in the proper way (explained in more detail below), when a user presses the button an `invoke` message is sent to the bot.</span></span> <span data-ttu-id="8fa2a-116">Na resposta HTTP à mensagem, há um objeto TaskInfo inserido em um objeto wrapper, que o Teams usa para `invoke` exibir o módulo de tarefa. [](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object)</span><span class="sxs-lookup"><span data-stu-id="8fa2a-116">In the HTTP response to the `invoke` message, there's a [TaskInfo object](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) embedded in a wrapper object, which Teams uses to display the task module.</span></span>

![solicitação/resposta de tarefa/busca](~/assets/images/task-module/task-module-invoke-request-response.png)

<span data-ttu-id="8fa2a-118">Vamos ver cada etapa em um pouco mais de detalhes:</span><span class="sxs-lookup"><span data-stu-id="8fa2a-118">Let's look at each step in a bit more detail:</span></span>

1. <span data-ttu-id="8fa2a-119">Este exemplo mostra um cartão Herói da Estrutura de Bot com uma ação de `invoke` [cartão "Comprar".](~/task-modules-and-cards/cards/cards-actions.md#invoke)</span><span class="sxs-lookup"><span data-stu-id="8fa2a-119">This example shows a Bot Framework Hero card with a "Buy" `invoke` [card action](~/task-modules-and-cards/cards/cards-actions.md#invoke).</span></span> <span data-ttu-id="8fa2a-120">O valor da `type` propriedade é - o restante do objeto pode ser o que você `task/fetch` `value` quiser.</span><span class="sxs-lookup"><span data-stu-id="8fa2a-120">The value of the `type` property is `task/fetch` - the rest of the `value` object can be whatever you like.</span></span>
2. <span data-ttu-id="8fa2a-121">O bot recebe a `invoke` mensagem HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="8fa2a-121">The bot receives the `invoke` HTTP POST message.</span></span>
3. <span data-ttu-id="8fa2a-122">O bot cria um objeto de resposta e o retorna no corpo da resposta POST com um código de resposta HTTP 200.</span><span class="sxs-lookup"><span data-stu-id="8fa2a-122">The bot creates a response object and returns it in the body of the POST response with an HTTP 200 response code.</span></span> <span data-ttu-id="8fa2a-123">O esquema para respostas é descrito abaixo na discussão sobre [tarefa/envio](#the-flexibility-of-tasksubmit), mas o importante a ser lembrado agora é que o corpo da resposta HTTP contém um objeto [TaskInfo](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) inserido em um objeto wrapper, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="8fa2a-123">The schema for responses is described [below in the discussion on task/submit](#the-flexibility-of-tasksubmit), but the important thing to remember now is that the body of the HTTP response contains a [TaskInfo object](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) embedded in a wrapper object, e.g.:</span></span>

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

    <span data-ttu-id="8fa2a-124">O `task/fetch` evento e sua resposta para bots é semelhante, conceitualmente, à função no `microsoftTeams.tasks.startTask()` SDK do cliente.</span><span class="sxs-lookup"><span data-stu-id="8fa2a-124">The `task/fetch` event and its response for bots is similar, conceptually, to the `microsoftTeams.tasks.startTask()` function in the client SDK.</span></span>
4. <span data-ttu-id="8fa2a-125">O Microsoft Teams exibe o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="8fa2a-125">Microsoft Teams displays the task module.</span></span>

## <a name="submitting-the-result-of-a-task-module"></a><span data-ttu-id="8fa2a-126">Enviando o resultado de um módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="8fa2a-126">Submitting the result of a task module</span></span>

<span data-ttu-id="8fa2a-127">Quando o usuário é concluído com o módulo de tarefa, enviar o resultado de volta para o bot é semelhante à maneira como ele funciona com guias [,](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-submitting-the-result-of-a-task-module)mas há algumas diferenças, portanto, ele também é descrito aqui.</span><span class="sxs-lookup"><span data-stu-id="8fa2a-127">When the user is finished with the task module, submitting the result back to the bot is similar [to the way it works with tabs](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-submitting-the-result-of-a-task-module), but there are a few differences, so it's described here too.</span></span>

* <span data-ttu-id="8fa2a-128">**HTML/JavaScript ( `TaskInfo.url` )**.</span><span class="sxs-lookup"><span data-stu-id="8fa2a-128">**HTML/JavaScript (`TaskInfo.url`)**.</span></span> <span data-ttu-id="8fa2a-129">Depois de validar o que o usuário instalou, você chama a função SDK (referida a seguir como para fins de capacidade `microsoftTeams.tasks.submitTask()` `submitTask()` de leitura).</span><span class="sxs-lookup"><span data-stu-id="8fa2a-129">Once you've validated what the user has entered, you call the `microsoftTeams.tasks.submitTask()` SDK function (referred to hereafter as `submitTask()` for readability purposes).</span></span> <span data-ttu-id="8fa2a-130">Você pode chamar sem qualquer parâmetro se quiser que o Teams feche o módulo de tarefa, mas na maioria das vezes você vai querer passar um objeto ou uma cadeia de caracteres para `submitTask()` seu `submitHandler` .</span><span class="sxs-lookup"><span data-stu-id="8fa2a-130">You can call `submitTask()` without any parameters if you just want Teams to close the task module, but most of the time you'll want to pass an object or a string to your `submitHandler`.</span></span> <span data-ttu-id="8fa2a-131">Basta passá-lo como o primeiro parâmetro, `result` .</span><span class="sxs-lookup"><span data-stu-id="8fa2a-131">Simply pass it as the first parameter, `result`.</span></span> <span data-ttu-id="8fa2a-132">O Teams invocará `submitHandler` : será e será o `err` `null` objeto/cadeia de `result` caracteres que você passou para `submitTask()` .</span><span class="sxs-lookup"><span data-stu-id="8fa2a-132">Teams will invoke `submitHandler`: `err` will be `null` and `result` will be the object/string you passed to `submitTask()`.</span></span> <span data-ttu-id="8fa2a-133">Se você fizer uma chamada com um parâmetro, deverá passar uma ou uma matriz de cadeias de `submitTask()` `result`  `appId` caracteres: isso permite ao Teams validar que o aplicativo que está enviando o resultado é o mesmo que invocou o módulo `appId` de tarefa.</span><span class="sxs-lookup"><span data-stu-id="8fa2a-133">If you do call `submitTask()` with a `result` parameter, you **must** pass an `appId` or an array of `appId` strings: this allows Teams to validate that the app sending the result is the same one which invoked the task module.</span></span> <span data-ttu-id="8fa2a-134">Seu bot receberá uma `task/submit` mensagem, incluindo `result` conforme descrito [abaixo](#payload-of-taskfetch-and-tasksubmit-messages).</span><span class="sxs-lookup"><span data-stu-id="8fa2a-134">Your bot will receive a `task/submit` message including `result` as described [below](#payload-of-taskfetch-and-tasksubmit-messages).</span></span>
* <span data-ttu-id="8fa2a-135">**Cartão adaptável ( `TaskInfo.card` )**.</span><span class="sxs-lookup"><span data-stu-id="8fa2a-135">**Adaptive card (`TaskInfo.card`)**.</span></span> <span data-ttu-id="8fa2a-136">O corpo do cartão adaptável (conforme preenchido pelo usuário) será enviado para o bot por meio de uma mensagem quando o usuário `task/submit` pressionar qualquer `Action.Submit` botão.</span><span class="sxs-lookup"><span data-stu-id="8fa2a-136">The Adaptive card body (as filled in by the user) will be sent to the bot via a `task/submit` message when the user presses any `Action.Submit` button.</span></span>

## <a name="the-flexibility-of-tasksubmit"></a><span data-ttu-id="8fa2a-137">A flexibilidade de tarefa/envio</span><span class="sxs-lookup"><span data-stu-id="8fa2a-137">The flexibility of task/submit</span></span>

<span data-ttu-id="8fa2a-138">Na seção anterior, você aprendeu que quando o usuário termina com um módulo de tarefa invocado de um bot, o bot sempre recebe uma `task/submit invoke` mensagem.</span><span class="sxs-lookup"><span data-stu-id="8fa2a-138">In the previous section, you learned that when the user finishes with a task module invoked from a bot, the bot always receives a `task/submit invoke` message.</span></span> <span data-ttu-id="8fa2a-139">Como desenvolvedor, você tem várias opções ao *responder* à `task/submit` mensagem:</span><span class="sxs-lookup"><span data-stu-id="8fa2a-139">As a developer, you have several options when *responding* to the `task/submit` message:</span></span>

| <span data-ttu-id="8fa2a-140">Resposta de corpo HTTP</span><span class="sxs-lookup"><span data-stu-id="8fa2a-140">HTTP Body Response</span></span>                      | <span data-ttu-id="8fa2a-141">Cenário</span><span class="sxs-lookup"><span data-stu-id="8fa2a-141">Scenario</span></span>                                |
| --------------------------------------- | --------------------------------------- |
| <span data-ttu-id="8fa2a-142">Nenhum (ignore a `task/submit` mensagem)</span><span class="sxs-lookup"><span data-stu-id="8fa2a-142">None (ignore the `task/submit` message)</span></span> | <span data-ttu-id="8fa2a-143">A resposta mais simples não é nenhuma resposta.</span><span class="sxs-lookup"><span data-stu-id="8fa2a-143">The simplest response is no response at all.</span></span> <span data-ttu-id="8fa2a-144">Seu bot não é necessário para responder quando o usuário terminar com o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="8fa2a-144">Your bot is not required to respond when the user is finished with the task module.</span></span> |
| <pre>{<br/>  "task": {<br/>    "type": "message",<br/>    "value": "Message text"<br/>  }<br/>}</pre> | <span data-ttu-id="8fa2a-145">O Teams exibirá o valor de `value` em uma caixa de mensagem pop-up.</span><span class="sxs-lookup"><span data-stu-id="8fa2a-145">Teams will display the value of `value` in a popup message box.</span></span> |
| <pre>{<br/>  "task": {<br/>    "type": "continue",<br/>    "value": &lt;TaskInfo object&gt;<br/>  }<br/>}</pre> | <span data-ttu-id="8fa2a-146">Permite que você "encadee" sequências de cartões adaptáveis juntos em uma experiência de assistente/várias etapas.</span><span class="sxs-lookup"><span data-stu-id="8fa2a-146">Allows you to "chain" sequences of Adaptive cards together in a wizard/multi-step experience.</span></span> <span data-ttu-id="8fa2a-147">_Observe que a encadeamento de cartões adaptáveis em uma sequência é um cenário avançado e não documentado aqui. O Node.js de exemplo oferece suporte a ele, no entanto, e como ele funciona está documentado em [seu arquivo README.md .](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs#implementation-notes)_</span><span class="sxs-lookup"><span data-stu-id="8fa2a-147">_Note that chaining Adaptive cards into a sequence is an advanced scenario and not documented here. The Node.js sample app supports it, however, and how it works is documented in [its README.md file](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs#implementation-notes)._</span></span> |

## <a name="payload-of-taskfetch-and-tasksubmit-messages"></a><span data-ttu-id="8fa2a-148">Carga de mensagens de tarefa/busca e tarefa/envio</span><span class="sxs-lookup"><span data-stu-id="8fa2a-148">Payload of task/fetch and task/submit messages</span></span>

<span data-ttu-id="8fa2a-149">Esta seção define o esquema do que seu bot recebe quando recebe um `task/fetch` objeto `task/submit` Ou Bot `Activity` Framework.</span><span class="sxs-lookup"><span data-stu-id="8fa2a-149">This section defines the schema of what your bot receives when it receives a `task/fetch` or `task/submit` Bot Framework `Activity` object.</span></span> <span data-ttu-id="8fa2a-150">O nível superior importante aparece abaixo:</span><span class="sxs-lookup"><span data-stu-id="8fa2a-150">The important top-level appear below:</span></span>

| <span data-ttu-id="8fa2a-151">Propriedade</span><span class="sxs-lookup"><span data-stu-id="8fa2a-151">Property</span></span> | <span data-ttu-id="8fa2a-152">Descrição</span><span class="sxs-lookup"><span data-stu-id="8fa2a-152">Description</span></span>                          |
| -------- | ------------------------------------ |
| `type`   | <span data-ttu-id="8fa2a-153">Sempre será `invoke`</span><span class="sxs-lookup"><span data-stu-id="8fa2a-153">Will always be `invoke`</span></span>              |
| `name`   | <span data-ttu-id="8fa2a-154">Ou `task/fetch``task/submit`</span><span class="sxs-lookup"><span data-stu-id="8fa2a-154">Either `task/fetch` or `task/submit`</span></span> |
| `value`  | <span data-ttu-id="8fa2a-155">A carga definida pelo desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="8fa2a-155">The developer-defined payload.</span></span> <span data-ttu-id="8fa2a-156">Normalmente, a estrutura do `value` objeto espelha o que foi enviado do Teams.</span><span class="sxs-lookup"><span data-stu-id="8fa2a-156">Normally the structure of the `value` object mirrors what was sent from Teams.</span></span> <span data-ttu-id="8fa2a-157">Nesse caso, no entanto, é diferente porque queremos dar suporte à busca dinâmica ( ) tanto das ações de Bot Framework ( ) quanto de cartão adaptável ( ), e precisamos de uma maneira de comunicar o Teams ao `task/fetch` `value` `Action.Submit` `data` `context` bot, `value` / além do `data` que foi incluído em .</span><span class="sxs-lookup"><span data-stu-id="8fa2a-157">In this case, however, it's different because we want to support dynamic fetch (`task/fetch`) from both Bot Framework (`value`) and Adaptive card `Action.Submit` actions (`data`), and we need a way to communicate Teams `context` to the bot in addition to what was included in `value`/`data`.</span></span><br/><br/><span data-ttu-id="8fa2a-158">Fazemos isso combinando os dois em um objeto pai:</span><span class="sxs-lookup"><span data-stu-id="8fa2a-158">We do this by combining the two into a parent object:</span></span><br/><br/><pre>{<br/>  "context": {<br/>    "theme": "default" &vert; "dark" &vert; "contrast",<br/>  },<br/>  "data": [value field from Bot Framework card] &vert; [data field from Adaptive Card] <br/>}</pre>  |

## <a name="example-receiving-and-responding-to-taskfetch-and-tasksubmit-invoke-messages---nodejs"></a><span data-ttu-id="8fa2a-159">Exemplo: receber e responder a mensagens de invocação de tarefa/busca e tarefa/envio - Node.js</span><span class="sxs-lookup"><span data-stu-id="8fa2a-159">Example: Receiving and responding to task/fetch and task/submit invoke messages - Node.js</span></span>

> [!NOTE]
> <span data-ttu-id="8fa2a-160">O código de exemplo abaixo foi modificado entre a Visualização Técnica e a versão final deste recurso: o esquema da solicitação foi alterado para seguir o que foi `task/fetch` [documentado na seção anterior](#payload-of-taskfetch-and-tasksubmit-messages).</span><span class="sxs-lookup"><span data-stu-id="8fa2a-160">The sample code below was modified between Technical Preview and final release of this feature: the schema of the `task/fetch` request changed to follow what was [documented in the previous section](#payload-of-taskfetch-and-tasksubmit-messages).</span></span> <span data-ttu-id="8fa2a-161">Ou seja, a documentação estava correta, mas a implementação não estava.</span><span class="sxs-lookup"><span data-stu-id="8fa2a-161">That is, the documentation was correct but the implementation was not.</span></span> <span data-ttu-id="8fa2a-162">Consulte os `// for Technical Preview [...]` comentários abaixo para saber o que mudou.</span><span class="sxs-lookup"><span data-stu-id="8fa2a-162">See the `// for Technical Preview [...]` comments below for what changed.</span></span>

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

<span data-ttu-id="8fa2a-163">*Consulte também*, código de exemplo do módulo de [tarefas do Microsoft Teams — exemplos de nodejs](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs/blob/master/src/TeamsBot.ts) e [Bot Framework.](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md)</span><span class="sxs-lookup"><span data-stu-id="8fa2a-163">*See also*, [Microsoft Teams task module sample code — nodejs](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs/blob/master/src/TeamsBot.ts) and  [Bot Framework samples](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).</span></span>

## <a name="example-receiving-and-responding-to-taskfetch-and-tasksubmit-invoke-messages---c"></a><span data-ttu-id="8fa2a-164">Exemplo: receber e responder a mensagens de invocação de tarefa/busca e tarefa/envio - C #</span><span class="sxs-lookup"><span data-stu-id="8fa2a-164">Example: Receiving and responding to task/fetch and task/submit invoke messages - C#</span></span>

<span data-ttu-id="8fa2a-165">No C# bots, `invoke` as mensagens são processadas por um `HttpResponseMessage()` controlador que processa uma `Activity` mensagem.</span><span class="sxs-lookup"><span data-stu-id="8fa2a-165">In C# bots, `invoke` messages are processed by an `HttpResponseMessage()` controller processing an `Activity` message.</span></span> <span data-ttu-id="8fa2a-166">As `task/fetch` `task/submit` solicitações e e respostas são JSON.</span><span class="sxs-lookup"><span data-stu-id="8fa2a-166">The `task/fetch` and `task/submit` requests and responses are JSON.</span></span> <span data-ttu-id="8fa2a-167">No C#, não é tão conveniente lidar com JSON bruto como está no Node.js, portanto, você precisa de classes de wrapper para manipular a serialização de e para JSON.</span><span class="sxs-lookup"><span data-stu-id="8fa2a-167">In C#, it's not as convenient to deal with raw JSON as it is in Node.js, so you need wrapper classes to handle the serialization to and from JSON.</span></span> <span data-ttu-id="8fa2a-168">Ainda não há suporte direto para isso no Microsoft Teams [C# SDK,](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) mas você pode ver um exemplo de como essas classes simples de wrapper seriam no aplicativo de exemplo [C#](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Models/TaskModel.cs).</span><span class="sxs-lookup"><span data-stu-id="8fa2a-168">There's no direct support for this in the Microsoft Teams [C# SDK](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) yet, but you can see an example of what these simple wrapper classes would look like in the [C# sample app](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Models/TaskModel.cs).</span></span>

<span data-ttu-id="8fa2a-169">Veja a seguir o exemplo de código C# para manipulação e mensagens usando essas classes de `task/fetch` `task/submit` wrapper ( `TaskInfo` , ), `TaskEnvelope` trechos do [exemplo](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs):</span><span class="sxs-lookup"><span data-stu-id="8fa2a-169">Below is example code in C# for handling `task/fetch` and `task/submit` messages using these wrapper classes (`TaskInfo`, `TaskEnvelope`), excerpted from the [sample](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs):</span></span>

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

<span data-ttu-id="8fa2a-170">Não mostrada no exemplo acima é a `SetTaskInfo()` função, que define `height` as propriedades , e do objeto para cada `width` `title` `TaskInfo` caso.</span><span class="sxs-lookup"><span data-stu-id="8fa2a-170">Not shown in the above example is the `SetTaskInfo()` function, which sets the `height`, `width`, and `title` properties of the `TaskInfo` object for each case.</span></span> <span data-ttu-id="8fa2a-171">Aqui está o [código-fonte para SetTaskInfo()](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs).</span><span class="sxs-lookup"><span data-stu-id="8fa2a-171">Here's the [source code for SetTaskInfo()](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs).</span></span>

### <a name="bot-framework-card-actions-vs-adaptive-card-actionsubmit-actions"></a><span data-ttu-id="8fa2a-172">Ações de cartão da Estrutura de Bot vs. Ações de cartão adaptáveis.Enviar ações</span><span class="sxs-lookup"><span data-stu-id="8fa2a-172">Bot Framework card actions vs. Adaptive card Action.Submit actions</span></span>

<span data-ttu-id="8fa2a-173">O esquema para ações de cartão da Estrutura de Bot é ligeiramente diferente das ações de cartão `Action.Submit` adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="8fa2a-173">The schema for Bot Framework card actions is slightly different from Adaptive card `Action.Submit` actions.</span></span> <span data-ttu-id="8fa2a-174">Como resultado, a maneira de invocar módulos de tarefa também é ligeiramente diferente: o objeto contém um objeto para que ele não interfira com outras propriedades `data` `Action.Submit` no `msteams` cartão.</span><span class="sxs-lookup"><span data-stu-id="8fa2a-174">As a result, the way to invoke task modules is slightly different too: the `data` object in `Action.Submit` contains an `msteams` object so it won't interfere with other properties in the card.</span></span> <span data-ttu-id="8fa2a-175">A tabela a seguir mostra um exemplo de cada um:</span><span class="sxs-lookup"><span data-stu-id="8fa2a-175">The following table shows an example of each:</span></span>

| <span data-ttu-id="8fa2a-176">Ação de cartão da Estrutura de Bot</span><span class="sxs-lookup"><span data-stu-id="8fa2a-176">Bot Framework card action</span></span>                              | <span data-ttu-id="8fa2a-177">Ação Action.Submit do cartão adaptável</span><span class="sxs-lookup"><span data-stu-id="8fa2a-177">Adaptive card Action.Submit action</span></span>                     |
| ------------------------------------------------------ | ------------------------------------------------------ |
| <pre>{<br/>  "type": "invoke",<br/>  "title": "Buy",<br/>  "value": {<br/>    "type": "task/fetch",<br/>    &lt;...&gt;<br/>  }<br/>}</pre> | <pre>{<br/>  "type": "Action.Submit",<br/>  "id": "btnBuy",<br/>  "title": "Buy",<br/>  "data": {<br/>    &lt;...&gt;,<br/>    "msteams": {<br/>      "type": "task/fetch"<br/>    }<br/>  }<br/>}</pre>  |
