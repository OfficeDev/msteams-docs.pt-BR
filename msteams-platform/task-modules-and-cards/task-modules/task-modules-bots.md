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
# <a name="using-task-modules-from-microsoft-teams-bots"></a>Usando módulos de tarefa dos bots do Microsoft Teams

Os módulos de tarefa podem ser invocados de bots do Microsoft Teams usando botões em cartões adaptáveis e cartões de estrutura de bot (herói, thumbnail e Office 365 Connector). Os módulos de tarefas costumam ser uma melhor experiência do usuário do que várias etapas de conversa em que você como desenvolvedor precisa manter o controle do estado do bot e permitir que o usuário interrompa/cancele a sequência.

Há duas maneiras de chamar módulos de tarefa:

* **Um novo tipo de mensagem de chamada `task/fetch` .** Usando a `invoke` [ação cartão](~/task-modules-and-cards/cards/cards-actions.md#invoke) para cartões de estrutura de bot ou a `Action.Submit` [ação de cartão](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) para cartões adaptáveis, com `task/fetch` o módulo de tarefa (uma URL ou um cartão adaptável) é buscada dinamicamente no bot.
* **URLs de link profundo.** Usando a [sintaxe de link profundo para módulos de tarefa](~/task-modules-and-cards/what-are-task-modules.md#task-module-deep-link-syntax), você pode usar a `openUrl` [ação cartão](~/task-modules-and-cards/cards/cards-actions.md#openurl) para cartões de estrutura de bot ou a `Action.OpenUrl` [ação de cartão](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) para cartões adaptáveis, respectivamente. Com URLs de link profundo, a URL do módulo de tarefa ou corpo de cartão adaptável é obviamente conhecido com antecedência, evitando uma viagem de ida e volta ao servidor em relação a `task/fetch` .

>[!IMPORTANT]
>Para garantir comunicações seguras, cada `url` `fallbackUrl` uma e deve implementar o protocolo de criptografia HTTPS.

## <a name="invoking-a-task-module-via-taskfetch"></a>Invocar um módulo de tarefa por meio de tarefa/busca

Quando o `value` objeto da `invoke` ação do cartão ou `Action.Submit` é inicializado da forma adequada (explicado em mais detalhes abaixo), quando um usuário pressiona o botão, uma `invoke` mensagem é enviada ao bot. Na resposta HTTP para a `invoke` mensagem, há um [objeto TaskInfo](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) incorporado em um objeto envoltório, que o Teams usa para exibir o módulo de tarefa.

![solicitação/resposta de tarefa/busca](~/assets/images/task-module/task-module-invoke-request-response.png)

Vamos examinar cada etapa mais detalhadamente:

1. Este exemplo mostra um cartão de herói da estrutura de bot com uma `invoke` [ação de cartão](~/task-modules-and-cards/cards/cards-actions.md#invoke)de "comprar". O valor da `type` propriedade é `task/fetch` : o restante do `value` objeto pode ser o que você quiser.
2. O bot recebe a `invoke` mensagem http post.
3. O bot cria um objeto Response e o retorna no corpo da resposta POST com um código de resposta HTTP 200. O esquema de respostas é descrito [abaixo na discussão sobre a tarefa/envio](#the-flexibility-of-tasksubmit), mas o importante a ser lembrado agora é que o corpo da resposta http contém um [objeto TaskInfo](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) incorporado em um objeto envoltório, por exemplo:

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

    O `task/fetch` evento e sua resposta para bots é semelhante, conceitualmente, à `microsoftTeams.tasks.startTask()` função no SDK do cliente.
4. O Microsoft Teams exibe o módulo de tarefa.

## <a name="submitting-the-result-of-a-task-module"></a>Enviando o resultado de um módulo de tarefa

Quando o usuário termina com o módulo de tarefa, o envio do resultado para o bot é semelhante [à forma como funciona com guias](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-submitting-the-result-of-a-task-module), mas há algumas diferenças, portanto, é descrito aqui.

* **HTML/JavaScript ( `TaskInfo.url` )**. Depois de validar o que o usuário inseriu, chame a `microsoftTeams.tasks.submitTask()` função do SDK (mencionada em diante como `submitTask()` para fins de legibilidade). Você pode chamar `submitTask()` sem qualquer parâmetro se quiser que o Microsoft Teams feche o módulo de tarefa, mas a maior parte do tempo desejará passar um objeto ou uma cadeia de caracteres para o seu `submitHandler` . Basta passá-lo como o primeiro parâmetro `result` . O Microsoft Teams invocará `submitHandler` : `err` será `null` e `result` será o objeto/cadeia de caracteres que você deseja `submitTask()` . Se você chamar `submitTask()` com um `result` parâmetro, você **deve** passar um `appId` ou uma matriz de `appId` cadeias de caracteres: isso permite que as equipes validem que o aplicativo enviando o resultado é o mesmo que invocar o módulo de tarefa. O bot receberá uma `task/submit` mensagem `result` , incluindo as descritas [abaixo](#payload-of-taskfetch-and-tasksubmit-messages).
* **Cartão adaptável ( `TaskInfo.card` )**. O corpo do cartão adaptável (conforme preenchido pelo usuário) será enviado ao bot por meio de uma `task/submit` mensagem quando o usuário pressionar qualquer `Action.Submit` botão.

## <a name="the-flexibility-of-tasksubmit"></a>A flexibilidade de tarefa/envio

Na seção anterior, você aprendeu que quando o usuário termina com um módulo de tarefa invocado de um bot, o bot sempre recebe uma `task/submit invoke` mensagem. Como desenvolvedor, você tem várias opções ao *responder* à `task/submit` mensagem:

| Resposta de corpo HTTP                      | Cenário                                |
| --------------------------------------- | --------------------------------------- |
| Nenhum (ignorar a `task/submit` mensagem) | A resposta mais simples é nenhuma resposta. O bot não precisa responder quando o usuário termina com o módulo de tarefa. |
| <pre>{<br/>  "task": {<br/>    "type": "message",<br/>    "value": "Message text"<br/>  }<br/>}</pre> | O Microsoft Teams exibirá o valor de `value` em uma caixa de mensagem pop-up. |
| <pre>{<br/>  "task": {<br/>    "type": "continue",<br/>    "value": &lt;TaskInfo object&gt;<br/>  }<br/>}</pre> | Permite que você "encadear" sequências de cartões adaptáveis juntos em uma experiência de assistente/várias etapas. _Observe que o encadeamento de cartões adaptáveis em uma sequência é um cenário avançado e não está documentado aqui. No entanto, o aplicativo de exemplo Node.js dá suporte a ele e como ele funciona está documentado no [arquivo readme.MD](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs#implementation-notes)._ |

## <a name="payload-of-taskfetch-and-tasksubmit-messages"></a>Carga das mensagens de tarefa/busca e de tarefa/envio

Esta seção define o esquema do que seu bot recebe quando recebe um `task/fetch` objeto de `task/submit` estrutura ou bot `Activity` . O nível superior importante aparece abaixo:

| Propriedade | Descrição                          |
| -------- | ------------------------------------ |
| `type`   | Sempre será `invoke`              |
| `name`   | Um `task/fetch` ou `task/submit` |
| `value`  | A carga definida pelo desenvolvedor. Normalmente, a estrutura do `value` objeto espelha o que foi enviado do teams. Nesse caso, no entanto, é diferente porque queremos oferecer suporte à busca dinâmica ( `task/fetch` ) da estrutura de bot () `value` e ações de cartão adaptável `Action.Submit` ( `data` ), e precisamos de uma maneira de comunicar `context` as equipes ao bot, além do que foi incluído no `value` / `data` .<br/><br/>Fazemos isso combinando os dois em um objeto pai:<br/><br/><pre>{<br/>  "context": {<br/>    "theme": "default" &vert; "dark" &vert; "contrast",<br/>  },<br/>  "data": [value field from Bot Framework card] &vert; [data field from Adaptive Card] <br/>}</pre>  |

## <a name="example-receiving-and-responding-to-taskfetch-and-tasksubmit-invoke-messages---nodejs"></a>Exemplo: recebimento e resposta a mensagens/busca e tarefas/envio de invocação de tarefas-Node.js

> [!NOTE]
> O código de exemplo abaixo foi modificado entre a visualização técnica e a versão final desse recurso: o esquema da `task/fetch` solicitação foi alterado para acompanhar o que foi [documentado na seção anterior](#payload-of-taskfetch-and-tasksubmit-messages). Ou seja, a documentação estava correta, mas a implementação não foi. Consulte os `// for Technical Preview [...]` comentários abaixo para saber o que foi alterado.

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
## <a name="example-receiving-and-responding-to-taskfetch-and-tasksubmit-invoke-messages---c"></a>Exemplo: recebendo e respondendo a tarefas/buscar e/enviar mensagens de invocação-C #

Nos bots do C#, `invoke` as mensagens são processadas por um `HttpResponseMessage()` controlador que processa uma `Activity` mensagem. As `task/fetch` solicitações e as `task/submit` respostas são JSON. No C#, não é tão conveniente lidar com o JSON bruto como está em Node.js, portanto, você precisa de classes de wrapper para lidar com a serialização de e para JSON. Ainda não há suporte direto para isso no SDK do Microsoft Teams [C#](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) , mas você pode ver um exemplo de como essas classes de wrapper simples seriam parecidas no [aplicativo de exemplo C#](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Models/TaskModel.cs).

Veja a seguir um exemplo de código em C# para tratamento `task/fetch` e `task/submit` mensagens usando essas classes de wrapper ( `TaskInfo` , `TaskEnvelope` ) extratos da [amostra](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs):

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
## <a name="example-receiving-and-responding-to-taskfetch-and-tasksubmit-invoke-messages---python"></a>Exemplo: recebendo e respondendo mensagens de tarefa/busca e tarefa/envio de chamadas-Python
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
### <a name="bot-framework-card-actions-vs-adaptive-card-actionsubmit-actions"></a>Ações de cartão de estrutura de bot versus ação de cartão adaptável. enviar ações

O esquema para as ações do cartão de estrutura de bot é um pouco diferente das ações de cartão adaptável `Action.Submit` . Como resultado, a maneira de invocar módulos de tarefa é um pouco diferente: o `data` objeto no `Action.Submit` contém um `msteams` objeto para que ele não interfira com outras propriedades no cartão. A tabela a seguir mostra um exemplo de cada:

| Ação do cartão de estrutura de bot                              | Ação de cartão adaptável. Submit                     |
| ------------------------------------------------------ | ------------------------------------------------------ |
| <pre>{<br/>  "type": "invoke",<br/>  "title": "Buy",<br/>  "value": {<br/>    "type": "task/fetch",<br/>    &lt;...&gt;<br/>  }<br/>}</pre> | <pre>{<br/>  "type": "Action.Submit",<br/>  "id": "btnBuy",<br/>  "title": "Buy",<br/>  "data": {<br/>    &lt;...&gt;,<br/>    "msteams": {<br/>      "type": "task/fetch"<br/>    }<br/>  }<br/>}</pre>  |
