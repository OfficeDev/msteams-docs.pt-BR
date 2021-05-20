---
title: Usando módulos de tarefa em Microsoft Teams bots
description: Como usar módulos de tarefa com bots Microsoft Teams, incluindo cartões Bot Framework, cartões adaptativos e links profundos
localization_priority: Normal
ms.topic: how-to
keywords: módulos de tarefa equipes bots
ms.openlocfilehash: bfaf3dfe791c1736aeb418e2689e513908f04534
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566562"
---
# <a name="using-task-modules-from-microsoft-teams-bots"></a><span data-ttu-id="42d10-104">Usando módulos de tarefas de bots Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="42d10-104">Using task modules from Microsoft Teams bots</span></span>

<span data-ttu-id="42d10-105">Os módulos de tarefa podem ser invocados a partir de bots Microsoft Teams usando botões em placas adaptativas e cartões Bot Framework (Hero, Miniatura e Office 365 Conector).</span><span class="sxs-lookup"><span data-stu-id="42d10-105">Task modules can be invoked from Microsoft Teams bots using buttons on Adaptive cards and Bot Framework cards (Hero, Thumbnail, and Office 365 Connector).</span></span> <span data-ttu-id="42d10-106">Os módulos de tarefa são muitas vezes uma melhor experiência do usuário do que várias etapas de conversação onde você, como desenvolvedor, tem que acompanhar o estado do bot e permitir que o usuário interrompa/cancele a sequência.</span><span class="sxs-lookup"><span data-stu-id="42d10-106">Task modules are often a better user experience than multiple conversation steps where you as a developer have to keep track of bot state and allow the user to interrupt/cancel the sequence.</span></span>

<span data-ttu-id="42d10-107">Existem duas maneiras de invocar módulos de tarefa:</span><span class="sxs-lookup"><span data-stu-id="42d10-107">There are two ways of invoking task modules:</span></span>

* <span data-ttu-id="42d10-108">**Um novo tipo de mensagem de `task/fetch` invocação.**</span><span class="sxs-lookup"><span data-stu-id="42d10-108">**A new kind of invoke message `task/fetch`.**</span></span> <span data-ttu-id="42d10-109">Usando a `invoke` [ação](~/task-modules-and-cards/cards/cards-actions.md#invoke) do cartão para cartões Bot Framework ou a `Action.Submit` [ação](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) do cartão para cartões Adaptive, com `task/fetch` , o módulo de tarefa (uma URL ou uma placa Adaptive) é obtido dinamicamente do seu bot.</span><span class="sxs-lookup"><span data-stu-id="42d10-109">Using the `invoke` [card action](~/task-modules-and-cards/cards/cards-actions.md#invoke) for Bot Framework cards, or the `Action.Submit` [card action](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) for Adaptive cards, with `task/fetch`, the task module (either a URL or an Adaptive card) is fetched dynamically from your bot.</span></span>
* <span data-ttu-id="42d10-110">**URLs de ligação profunda.**</span><span class="sxs-lookup"><span data-stu-id="42d10-110">**Deep link URLs.**</span></span> <span data-ttu-id="42d10-111">Usando a [sintaxe de link profundo para módulos de tarefa,](~/task-modules-and-cards/what-are-task-modules.md#task-module-deep-link-syntax)você pode usar a `openUrl` [ação](~/task-modules-and-cards/cards/cards-actions.md#openurl) do cartão para cartões Bot Framework ou `Action.OpenUrl` [a ação](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) do cartão para cartões Adaptativos, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="42d10-111">Using the [deep link syntax for task modules](~/task-modules-and-cards/what-are-task-modules.md#task-module-deep-link-syntax), you can use the `openUrl` [card action](~/task-modules-and-cards/cards/cards-actions.md#openurl) for Bot Framework cards or the `Action.OpenUrl` [card action](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) for Adaptive cards, respectively.</span></span> <span data-ttu-id="42d10-112">Com URLs de link profundo, a URL do módulo de tarefa ou o corpo de cartão adaptável é obviamente conhecido com antecedência, evitando uma ida e volta de servidor em relação a `task/fetch` .</span><span class="sxs-lookup"><span data-stu-id="42d10-112">With deep link URLs, the task module URL or Adaptive card body is obviously known in advance, avoiding a server round-trip relative to `task/fetch`.</span></span>

>[!IMPORTANT]
><span data-ttu-id="42d10-113">Para garantir comunicações seguras, cada um `url` e deve implementar o protocolo de criptografia `fallbackUrl` HTTPS.</span><span class="sxs-lookup"><span data-stu-id="42d10-113">To ensure secure communications, each `url` and `fallbackUrl` must implement the HTTPS encryption protocol.</span></span>

## <a name="invoking-a-task-module-through-taskfetch"></a><span data-ttu-id="42d10-114">Invocando um módulo de tarefa através de tarefa/busca</span><span class="sxs-lookup"><span data-stu-id="42d10-114">Invoking a task module through task/fetch</span></span>

<span data-ttu-id="42d10-115">Quando o `value` objeto da ação do `invoke` cartão ou `Action.Submit` é inicializado da maneira adequada (explicado com mais detalhes abaixo), quando um usuário pressiona o botão uma `invoke` mensagem é enviada para o bot.</span><span class="sxs-lookup"><span data-stu-id="42d10-115">When the `value` object of the `invoke` card action or `Action.Submit` is initialized in the proper way (explained in more detail below), when a user presses the button an `invoke` message is sent to the bot.</span></span> <span data-ttu-id="42d10-116">Na resposta HTTP à `invoke` mensagem, há um [objeto TaskInfo](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) incorporado em um objeto invólucro, que Teams usa para exibir o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="42d10-116">In the HTTP response to the `invoke` message, there's a [TaskInfo object](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) embedded in a wrapper object, which Teams uses to display the task module.</span></span>

![tarefa/buscar solicitação/resposta](~/assets/images/task-module/task-module-invoke-request-response.png)

<span data-ttu-id="42d10-118">Vamos olhar cada passo com um pouco mais de detalhes:</span><span class="sxs-lookup"><span data-stu-id="42d10-118">Let's look at each step in a bit more detail:</span></span>

1. <span data-ttu-id="42d10-119">Este exemplo mostra um cartão Bot Framework Hero com uma `invoke` [ação de cartão "Comprar".](~/task-modules-and-cards/cards/cards-actions.md#invoke)</span><span class="sxs-lookup"><span data-stu-id="42d10-119">This example shows a Bot Framework Hero card with a "Buy" `invoke` [card action](~/task-modules-and-cards/cards/cards-actions.md#invoke).</span></span> <span data-ttu-id="42d10-120">O valor da `type` propriedade é - o resto do objeto pode ser o que você `task/fetch` `value` quiser.</span><span class="sxs-lookup"><span data-stu-id="42d10-120">The value of the `type` property is `task/fetch` - the rest of the `value` object can be whatever you like.</span></span>
1. <span data-ttu-id="42d10-121">O bot recebe a `invoke` mensagem HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="42d10-121">The bot receives the `invoke` HTTP POST message.</span></span>
1. <span data-ttu-id="42d10-122">O bot cria um objeto de resposta e o devolve no corpo da resposta POST com um código de resposta HTTP 200.</span><span class="sxs-lookup"><span data-stu-id="42d10-122">The bot creates a response object and returns it in the body of the POST response with an HTTP 200 response code.</span></span> <span data-ttu-id="42d10-123">O esquema de respostas é descrito [abaixo na discussão sobre tarefa/envio,](#the-flexibility-of-tasksubmit)mas o importante a ser lembrado agora é que o corpo da resposta HTTP contém um objeto [TaskInfo](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) incorporado em um objeto invólucro.</span><span class="sxs-lookup"><span data-stu-id="42d10-123">The schema for responses is described [below in the discussion on task/submit](#the-flexibility-of-tasksubmit), but the important thing to remember now is that the body of the HTTP response contains a [TaskInfo object](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) embedded in a wrapper object.</span></span> <span data-ttu-id="42d10-124">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="42d10-124">For example:</span></span>

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

    <span data-ttu-id="42d10-125">O `task/fetch` evento e sua resposta para bots é semelhante, conceitualmente, à função no `microsoftTeams.tasks.startTask()` SDK cliente.</span><span class="sxs-lookup"><span data-stu-id="42d10-125">The `task/fetch` event and its response for bots is similar, conceptually, to the `microsoftTeams.tasks.startTask()` function in the client SDK.</span></span>
1. <span data-ttu-id="42d10-126">Microsoft Teams exibe o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="42d10-126">Microsoft Teams displays the task module.</span></span>

## <a name="submitting-the-result-of-a-task-module"></a><span data-ttu-id="42d10-127">Submeter o resultado de um módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="42d10-127">Submitting the result of a task module</span></span>

<span data-ttu-id="42d10-128">Quando o usuário termina com o módulo de tarefa, enviar o resultado de volta para o bot é semelhante [à maneira como ele funciona com guias,](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-submitting-the-result-of-a-task-module)mas há algumas diferenças, por isso é descrito aqui também.</span><span class="sxs-lookup"><span data-stu-id="42d10-128">When the user is finished with the task module, submitting the result back to the bot is similar [to the way it works with tabs](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-submitting-the-result-of-a-task-module), but there are a few differences, so it's described here too.</span></span>

* <span data-ttu-id="42d10-129">**HTML/JavaScript ( `TaskInfo.url` )**.</span><span class="sxs-lookup"><span data-stu-id="42d10-129">**HTML/JavaScript (`TaskInfo.url`)**.</span></span> <span data-ttu-id="42d10-130">Depois de validar o que o usuário inseriu, você chama a `microsoftTeams.tasks.submitTask()` função SDK (referida para fins de `submitTask()` leitura).</span><span class="sxs-lookup"><span data-stu-id="42d10-130">Once you've validated what the user has entered, you call the `microsoftTeams.tasks.submitTask()` SDK function (referred to hereafter as `submitTask()` for readability purposes).</span></span> <span data-ttu-id="42d10-131">Você pode ligar `submitTask()` sem parâmetros se quiser Teams fechar o módulo de tarefa, mas na maioria das vezes você vai querer passar um objeto ou uma string para o seu `submitHandler` .</span><span class="sxs-lookup"><span data-stu-id="42d10-131">You can call `submitTask()` without any parameters if you just want Teams to close the task module, but most of the time you'll want to pass an object or a string to your `submitHandler`.</span></span> <span data-ttu-id="42d10-132">Basta passá-lo como o primeiro parâmetro, `result` .</span><span class="sxs-lookup"><span data-stu-id="42d10-132">Simply pass it as the first parameter, `result`.</span></span> <span data-ttu-id="42d10-133">Teams invocará `submitHandler` : `err` será e será `null` o `result` objeto/string para o que você passou `submitTask()` .</span><span class="sxs-lookup"><span data-stu-id="42d10-133">Teams will invoke `submitHandler`: `err` will be `null` and `result` will be the object/string you passed to `submitTask()`.</span></span> <span data-ttu-id="42d10-134">Se você ligar `submitTask()` com um `result` parâmetro, você **deve** passar por uma ou uma série `appId` de `appId` strings: isso permite que Teams validar que o aplicativo que envia o resultado é o mesmo que invocou o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="42d10-134">If you do call `submitTask()` with a `result` parameter, you **must** pass an `appId` or an array of `appId` strings: this allows Teams to validate that the app sending the result is the same one which invoked the task module.</span></span> <span data-ttu-id="42d10-135">Seu bot receberá uma `task/submit` mensagem, incluindo `result` como descrito [abaixo](#payload-of-taskfetch-and-tasksubmit-messages).</span><span class="sxs-lookup"><span data-stu-id="42d10-135">Your bot will receive a `task/submit` message including `result` as described [below](#payload-of-taskfetch-and-tasksubmit-messages).</span></span>
* <span data-ttu-id="42d10-136">**Cartão adaptativo ( `TaskInfo.card` )**.</span><span class="sxs-lookup"><span data-stu-id="42d10-136">**Adaptive card (`TaskInfo.card`)**.</span></span> <span data-ttu-id="42d10-137">O corpo do cartão adaptável (preenchido pelo usuário) será enviado ao bot através de uma `task/submit` mensagem quando o usuário pressionar qualquer `Action.Submit` botão.</span><span class="sxs-lookup"><span data-stu-id="42d10-137">The Adaptive card body (as filled in by the user) will be sent to the bot via a `task/submit` message when the user presses any `Action.Submit` button.</span></span>

## <a name="the-flexibility-of-tasksubmit"></a><span data-ttu-id="42d10-138">A flexibilidade da tarefa/envio</span><span class="sxs-lookup"><span data-stu-id="42d10-138">The flexibility of task/submit</span></span>

<span data-ttu-id="42d10-139">Na seção anterior, você aprendeu que quando o usuário termina com um módulo de tarefa invocado a partir de um bot, o bot sempre recebe uma `task/submit invoke` mensagem.</span><span class="sxs-lookup"><span data-stu-id="42d10-139">In the previous section, you learned that when the user finishes with a task module invoked from a bot, the bot always receives a `task/submit invoke` message.</span></span> <span data-ttu-id="42d10-140">Como desenvolvedor, você tem várias opções ao *responder* à `task/submit` mensagem:</span><span class="sxs-lookup"><span data-stu-id="42d10-140">As a developer, you have several options when *responding* to the `task/submit` message:</span></span>

| <span data-ttu-id="42d10-141">Resposta do corpo HTTP</span><span class="sxs-lookup"><span data-stu-id="42d10-141">HTTP Body Response</span></span>                      | <span data-ttu-id="42d10-142">Cenário</span><span class="sxs-lookup"><span data-stu-id="42d10-142">Scenario</span></span>                                |
| --------------------------------------- | --------------------------------------- |
| <span data-ttu-id="42d10-143">Nenhum (ignore a `task/submit` mensagem)</span><span class="sxs-lookup"><span data-stu-id="42d10-143">None (ignore the `task/submit` message)</span></span> | <span data-ttu-id="42d10-144">A resposta mais simples não é nenhuma resposta.</span><span class="sxs-lookup"><span data-stu-id="42d10-144">The simplest response is no response at all.</span></span> <span data-ttu-id="42d10-145">O bot não é obrigado a responder quando o usuário terminar com o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="42d10-145">Your bot is not required to respond when the user is finished with the task module.</span></span> |
| <pre>{<br/>  "task": {<br/>    "type": "message",<br/>    "value": "Message text"<br/>  }<br/>}</pre> | <span data-ttu-id="42d10-146">Teams exibirá o valor de uma caixa de `value` mensagens pop-up.</span><span class="sxs-lookup"><span data-stu-id="42d10-146">Teams will display the value of `value` in a popup message box.</span></span> |
| <pre>{<br/>  "task": {<br/>    "type": "continue",<br/>    "value": &lt;TaskInfo object&gt;<br/>  }<br/>}</pre> | <span data-ttu-id="42d10-147">Permite que você "acorrente" sequências de cartões adaptativos em uma experiência assistente/várias etapas.</span><span class="sxs-lookup"><span data-stu-id="42d10-147">Allows you to "chain" sequences of Adaptive cards together in a wizard/multi-step experience.</span></span> <span data-ttu-id="42d10-148">_Observe que encadear placas adaptativas em uma sequência é um cenário avançado e não documentado aqui. O aplicativo de amostra Node.js suporta, no entanto, e como ele funciona é documentado em [seu arquivo README.md](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs#implementation-notes)._</span><span class="sxs-lookup"><span data-stu-id="42d10-148">_Note that chaining Adaptive cards into a sequence is an advanced scenario and not documented here. The Node.js sample app supports it, however, and how it works is documented in [its README.md file](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs#implementation-notes)._</span></span> |

## <a name="payload-of-taskfetch-and-tasksubmit-messages"></a><span data-ttu-id="42d10-149">Carga útil de mensagens de tarefa/busca e tarefa/envio</span><span class="sxs-lookup"><span data-stu-id="42d10-149">Payload of task/fetch and task/submit messages</span></span>

<span data-ttu-id="42d10-150">Esta seção define o esquema do que o bot recebe quando recebe um `task/fetch` objeto ou `task/submit` Bot `Activity` Framework.</span><span class="sxs-lookup"><span data-stu-id="42d10-150">This section defines the schema of what your bot receives when it receives a `task/fetch` or `task/submit` Bot Framework `Activity` object.</span></span> <span data-ttu-id="42d10-151">O importante nível superior aparece abaixo:</span><span class="sxs-lookup"><span data-stu-id="42d10-151">The important top-level appear below:</span></span>

| <span data-ttu-id="42d10-152">Propriedade</span><span class="sxs-lookup"><span data-stu-id="42d10-152">Property</span></span> | <span data-ttu-id="42d10-153">Descrição</span><span class="sxs-lookup"><span data-stu-id="42d10-153">Description</span></span>                          |
| -------- | ------------------------------------ |
| `type`   | <span data-ttu-id="42d10-154">Sempre será `invoke`</span><span class="sxs-lookup"><span data-stu-id="42d10-154">Will always be `invoke`</span></span>              |
| `name`   | <span data-ttu-id="42d10-155">Ou `task/fetch``task/submit`</span><span class="sxs-lookup"><span data-stu-id="42d10-155">Either `task/fetch` or `task/submit`</span></span> |
| `value`  | <span data-ttu-id="42d10-156">A carga definida pelo desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="42d10-156">The developer-defined payload.</span></span> <span data-ttu-id="42d10-157">Normalmente, a estrutura do `value` objeto espelha o que foi enviado de Teams.</span><span class="sxs-lookup"><span data-stu-id="42d10-157">Normally the structure of the `value` object mirrors what was sent from Teams.</span></span> <span data-ttu-id="42d10-158">Neste caso, porém, é diferente porque queremos apoiar a busca dinâmica ( `task/fetch` ) tanto das ações do Bot Framework ( ) quanto do cartão `value` adaptável ( ), e precisamos `Action.Submit` de uma maneira de comunicar Teams ao `data` `context` bot, além `value` / `data` do que foi incluído em .</span><span class="sxs-lookup"><span data-stu-id="42d10-158">In this case, however, it's different because we want to support dynamic fetch (`task/fetch`) from both Bot Framework (`value`) and Adaptive card `Action.Submit` actions (`data`), and we need a way to communicate Teams `context` to the bot in addition to what was included in `value`/`data`.</span></span><br/><br/><span data-ttu-id="42d10-159">Fazemos isso combinando os dois em um objeto pai:</span><span class="sxs-lookup"><span data-stu-id="42d10-159">We do this by combining the two into a parent object:</span></span><br/><br/><pre>{<br/>  "context": {<br/>    "theme": "default" &vert; "dark" &vert; "contrast",<br/>  },<br/>  "data": [value field from Bot Framework card] &vert; [data field from Adaptive Card] <br/>}</pre>  |

## <a name="example-receiving-and-responding-to-taskfetch-and-tasksubmit-invoke-messages---nodejs"></a><span data-ttu-id="42d10-160">Exemplo: Receber e responder a mensagens de busca e busca de tarefas e envios de tarefas - Node.js</span><span class="sxs-lookup"><span data-stu-id="42d10-160">Example: Receiving and responding to task/fetch and task/submit invoke messages - Node.js</span></span>

> [!NOTE]
> <span data-ttu-id="42d10-161">O código de amostra abaixo foi modificado entre a Visualização Técnica e a versão final deste recurso: o esquema da `task/fetch` solicitação mudou para seguir o que estava documentado na [seção anterior](#payload-of-taskfetch-and-tasksubmit-messages).</span><span class="sxs-lookup"><span data-stu-id="42d10-161">The sample code below was modified between Technical Preview and final release of this feature: the schema of the `task/fetch` request changed to follow what was [documented in the previous section](#payload-of-taskfetch-and-tasksubmit-messages).</span></span> <span data-ttu-id="42d10-162">Ou seja, a documentação estava correta, mas a implementação não foi.</span><span class="sxs-lookup"><span data-stu-id="42d10-162">That is, the documentation was correct but the implementation was not.</span></span> <span data-ttu-id="42d10-163">Veja os `// for Technical Preview [...]` comentários abaixo para o que mudou.</span><span class="sxs-lookup"><span data-stu-id="42d10-163">See the `// for Technical Preview [...]` comments below for what changed.</span></span>

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

## <a name="example-receiving-and-responding-to-taskfetch-and-tasksubmit-invoke-messages---c"></a><span data-ttu-id="42d10-164">Exemplo: Receber e responder a mensagens de busca e busca de tarefas e envios de tarefas - C #</span><span class="sxs-lookup"><span data-stu-id="42d10-164">Example: Receiving and responding to task/fetch and task/submit invoke messages - C#</span></span>

<span data-ttu-id="42d10-165">Em bots C#, `invoke` as mensagens são processadas por um `HttpResponseMessage()` controlador processando uma `Activity` mensagem.</span><span class="sxs-lookup"><span data-stu-id="42d10-165">In C# bots, `invoke` messages are processed by an `HttpResponseMessage()` controller processing an `Activity` message.</span></span> <span data-ttu-id="42d10-166">Os `task/fetch` `task/submit` pedidos e respostas são JSON.</span><span class="sxs-lookup"><span data-stu-id="42d10-166">The `task/fetch` and `task/submit` requests and responses are JSON.</span></span> <span data-ttu-id="42d10-167">Em C#, não é tão conveniente lidar com JSON cru como é em Node.js, então você precisa de aulas de invólucro para lidar com a serialização de e para JSON.</span><span class="sxs-lookup"><span data-stu-id="42d10-167">In C#, it's not as convenient to deal with raw JSON as it is in Node.js, so you need wrapper classes to handle the serialization to and from JSON.</span></span> <span data-ttu-id="42d10-168">Ainda não há suporte direto para isso no Microsoft Teams [C# SDK,](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) mas você pode ver um exemplo de como essas classes simples de invólucro seriam no [aplicativo de amostra C#](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Models/TaskModel.cs).</span><span class="sxs-lookup"><span data-stu-id="42d10-168">There's no direct support for this in the Microsoft Teams [C# SDK](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) yet, but you can see an example of what these simple wrapper classes would look like in the [C# sample app](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Models/TaskModel.cs).</span></span>

<span data-ttu-id="42d10-169">Abaixo está o código de exemplo em C# para manuseio `task/fetch` e `task/submit` mensagens usando essas classes de invólucro ( `TaskInfo` , , `TaskEnvelope` exceto da [amostra](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs):</span><span class="sxs-lookup"><span data-stu-id="42d10-169">Below is example code in C# for handling `task/fetch` and `task/submit` messages using these wrapper classes (`TaskInfo`, `TaskEnvelope`), excerpted from the [sample](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs):</span></span>

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

<span data-ttu-id="42d10-170">Não mostrado no exemplo acima é a `SetTaskInfo()` função, que define o `height` , e propriedades do objeto para cada `width` `title` `TaskInfo` caso.</span><span class="sxs-lookup"><span data-stu-id="42d10-170">Not shown in the above example is the `SetTaskInfo()` function, which sets the `height`, `width`, and `title` properties of the `TaskInfo` object for each case.</span></span> <span data-ttu-id="42d10-171">Aqui está o [código-fonte do SetTaskInfo().](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs)</span><span class="sxs-lookup"><span data-stu-id="42d10-171">Here's the [source code for SetTaskInfo()](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs).</span></span>

### <a name="bot-framework-card-actions-vs-adaptive-card-actionsubmit-actions"></a><span data-ttu-id="42d10-172">Ações do cartão Bot Framework vs. Ação de cartão adaptativo.Enviar ações</span><span class="sxs-lookup"><span data-stu-id="42d10-172">Bot Framework card actions vs. Adaptive card Action.Submit actions</span></span>

<span data-ttu-id="42d10-173">O esquema para as ações do cartão Bot Framework é ligeiramente diferente das ações de cartão `Action.Submit` Adaptive.</span><span class="sxs-lookup"><span data-stu-id="42d10-173">The schema for Bot Framework card actions is slightly different from Adaptive card `Action.Submit` actions.</span></span> <span data-ttu-id="42d10-174">Como resultado, a maneira de invocar módulos de tarefa também é ligeiramente diferente: o `data` objeto em contém um objeto para que ele não `Action.Submit` `msteams` interfira com outras propriedades no cartão.</span><span class="sxs-lookup"><span data-stu-id="42d10-174">As a result, the way to invoke task modules is slightly different too: the `data` object in `Action.Submit` contains an `msteams` object so it won't interfere with other properties in the card.</span></span> <span data-ttu-id="42d10-175">A tabela a seguir mostra um exemplo de cada um:</span><span class="sxs-lookup"><span data-stu-id="42d10-175">The following table shows an example of each:</span></span>

| <span data-ttu-id="42d10-176">Ação do cartão Bot Framework</span><span class="sxs-lookup"><span data-stu-id="42d10-176">Bot Framework card action</span></span>                              | <span data-ttu-id="42d10-177">Ação de cartão adaptativo.Enviar ação</span><span class="sxs-lookup"><span data-stu-id="42d10-177">Adaptive card Action.Submit action</span></span>                     |
| ------------------------------------------------------ | ------------------------------------------------------ |
| <pre>{<br/>  "type": "invoke",<br/>  "title": "Buy",<br/>  "value": {<br/>    "type": "task/fetch",<br/>    &lt;...&gt;<br/>  }<br/>}</pre> | <pre>{<br/>  "type": "Action.Submit",<br/>  "id": "btnBuy",<br/>  "title": "Buy",<br/>  "data": {<br/>    &lt;...&gt;,<br/>    "msteams": {<br/>      "type": "task/fetch"<br/>    }<br/>  }<br/>}</pre>  |

## <a name="see-also"></a><span data-ttu-id="42d10-178">Confira também</span><span class="sxs-lookup"><span data-stu-id="42d10-178">See also</span></span>

* [<span data-ttu-id="42d10-179">Microsoft Teams código de amostra do módulo de tarefas — nodejs</span><span class="sxs-lookup"><span data-stu-id="42d10-179">Microsoft Teams task module sample code — nodejs</span></span>](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs/blob/master/src/TeamsBot.ts)
* <span data-ttu-id="42d10-180">[Amostras do Bot Framework](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).</span><span class="sxs-lookup"><span data-stu-id="42d10-180">[Bot Framework samples](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).</span></span>