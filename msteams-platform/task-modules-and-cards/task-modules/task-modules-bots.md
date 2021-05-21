---
title: Usando módulos de tarefa em Microsoft Teams bots
description: Como usar módulos de tarefa com Microsoft Teams bots, incluindo cartões da Estrutura de Bot, cartões adaptáveis e links profundos
localization_priority: Normal
ms.topic: how-to
keywords: bots de equipes de módulos de tarefa
ms.openlocfilehash: bfaf3dfe791c1736aeb418e2689e513908f04534
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566562"
---
# <a name="using-task-modules-from-microsoft-teams-bots"></a>Usando módulos de tarefas Microsoft Teams bots

Os módulos de tarefa podem ser invocados Microsoft Teams bots usando botões em cartões adaptáveis e cartões de Estrutura de Bot (Hero, Thumbnail e Office 365 Connector). Os módulos de tarefas geralmente são uma experiência de usuário melhor do que várias etapas de conversa em que você, como desenvolvedor, precisa controlar o estado do bot e permitir que o usuário interrompa/cancele a sequência.

Há duas maneiras de invocar módulos de tarefa:

* **Um novo tipo de mensagem de `task/fetch` invocação.** Usar a ação de cartão para cartões da Estrutura de Bot ou a ação de cartão para cartões adaptáveis, com , o módulo de tarefa (uma URL ou um cartão `invoke` [](~/task-modules-and-cards/cards/cards-actions.md#invoke) `Action.Submit` [](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) adaptável) é buscado dinamicamente no `task/fetch` bot.
* **URLs de link profundo.** Usando a sintaxe de link profundo para [módulos](~/task-modules-and-cards/what-are-task-modules.md#task-module-deep-link-syntax)de tarefa, você pode usar a ação de cartão para cartões da Estrutura de Bot ou a ação de cartão para cartões `openUrl` [](~/task-modules-and-cards/cards/cards-actions.md#openurl) `Action.OpenUrl` [](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) adaptáveis, respectivamente. Com URLs de link profundo, a URL do módulo de tarefas ou o corpo do cartão adaptável é obviamente conhecido antecipadamente, evitando uma ida e volta do servidor em relação a `task/fetch` .

>[!IMPORTANT]
>Para garantir comunicações seguras, cada `url` um deles e deve implementar o protocolo de criptografia `fallbackUrl` HTTPS.

## <a name="invoking-a-task-module-through-taskfetch"></a>Invocar um módulo de tarefa por meio de tarefa/busca

Quando o objeto da ação do cartão ou é inicializado da maneira adequada (explicado em mais detalhes abaixo), quando um usuário pressiona o botão, uma mensagem é enviada `value` `invoke` para o `Action.Submit` `invoke` bot. Na resposta HTTP à mensagem, há um objeto TaskInfo inserido em um objeto wrapper, que Teams usa para `invoke` exibir o módulo de tarefa. [](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object)

![solicitação/resposta de tarefa/busca](~/assets/images/task-module/task-module-invoke-request-response.png)

Vamos ver cada etapa em um pouco mais de detalhes:

1. Este exemplo mostra um cartão Herói da Estrutura de Bot com uma ação de `invoke` [cartão "Comprar".](~/task-modules-and-cards/cards/cards-actions.md#invoke) O valor da `type` propriedade é - o restante do objeto pode ser o que você `task/fetch` `value` quiser.
1. O bot recebe a `invoke` mensagem HTTP POST.
1. O bot cria um objeto de resposta e o retorna no corpo da resposta POST com um código de resposta HTTP 200. O esquema para respostas é descrito abaixo na discussão sobre [tarefa/envio](#the-flexibility-of-tasksubmit), mas o importante a ser lembrado agora é que o corpo da resposta HTTP contém um objeto [TaskInfo](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) inserido em um objeto wrapper. Por exemplo:

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

    O `task/fetch` evento e sua resposta para bots é semelhante, conceitualmente, à função no `microsoftTeams.tasks.startTask()` SDK do cliente.
1. Microsoft Teams exibe o módulo de tarefa.

## <a name="submitting-the-result-of-a-task-module"></a>Enviando o resultado de um módulo de tarefa

Quando o usuário é concluído com o módulo de tarefa, enviar o resultado de volta para o bot é semelhante à maneira como ele funciona com guias [,](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-submitting-the-result-of-a-task-module)mas há algumas diferenças, portanto, ele também é descrito aqui.

* **HTML/JavaScript ( `TaskInfo.url` )**. Depois de validar o que o usuário instalou, você chama a função SDK (referida a seguir como para fins de capacidade `microsoftTeams.tasks.submitTask()` `submitTask()` de leitura). Você pode chamar sem qualquer parâmetro se quiser apenas Teams fechar o módulo de tarefa, mas na maioria das vezes você vai querer passar um objeto ou uma cadeia de caracteres para seu `submitTask()` `submitHandler` . Basta passá-lo como o primeiro parâmetro, `result` . Teams `submitHandler` invocará : `err` será e será o `null` objeto/cadeia de `result` caracteres que você passou para `submitTask()` . Se você fizer uma chamada com um parâmetro, deverá passar uma ou uma matriz de cadeias de `submitTask()` `result` caracteres:  isso permite Teams validar que o aplicativo que está enviando o resultado é o mesmo que invocou o módulo de `appId` `appId` tarefa. Seu bot receberá uma `task/submit` mensagem, incluindo `result` conforme descrito [abaixo](#payload-of-taskfetch-and-tasksubmit-messages).
* **Cartão adaptável ( `TaskInfo.card` )**. O corpo do cartão adaptável (conforme preenchido pelo usuário) será enviado para o bot por meio de uma mensagem quando o usuário `task/submit` pressionar qualquer `Action.Submit` botão.

## <a name="the-flexibility-of-tasksubmit"></a>A flexibilidade de tarefa/envio

Na seção anterior, você aprendeu que quando o usuário termina com um módulo de tarefa invocado de um bot, o bot sempre recebe uma `task/submit invoke` mensagem. Como desenvolvedor, você tem várias opções ao *responder* à `task/submit` mensagem:

| Resposta de corpo HTTP                      | Cenário                                |
| --------------------------------------- | --------------------------------------- |
| Nenhum (ignore a `task/submit` mensagem) | A resposta mais simples não é nenhuma resposta. Seu bot não é necessário para responder quando o usuário terminar com o módulo de tarefa. |
| <pre>{<br/>  "task": {<br/>    "type": "message",<br/>    "value": "Message text"<br/>  }<br/>}</pre> | Teams exibirá o valor de `value` em uma caixa de mensagem pop-up. |
| <pre>{<br/>  "task": {<br/>    "type": "continue",<br/>    "value": &lt;TaskInfo object&gt;<br/>  }<br/>}</pre> | Permite que você "encadee" sequências de cartões adaptáveis juntos em uma experiência de assistente/várias etapas. _Observe que a encadeamento de cartões adaptáveis em uma sequência é um cenário avançado e não documentado aqui. O Node.js de exemplo oferece suporte a ele, no entanto, e como ele funciona está documentado em [seu arquivo README.md .](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs#implementation-notes)_ |

## <a name="payload-of-taskfetch-and-tasksubmit-messages"></a>Carga de mensagens de tarefa/busca e tarefa/envio

Esta seção define o esquema do que seu bot recebe quando recebe um `task/fetch` objeto `task/submit` Ou Bot `Activity` Framework. O nível superior importante aparece abaixo:

| Propriedade | Descrição                          |
| -------- | ------------------------------------ |
| `type`   | Sempre será `invoke`              |
| `name`   | Ou `task/fetch``task/submit` |
| `value`  | A carga definida pelo desenvolvedor. Normalmente, a estrutura do `value` objeto espelha o que foi enviado de Teams. Nesse caso, no entanto, é diferente porque queremos dar suporte à busca dinâmica ( ) tanto das ações de Bot Framework ( ) quanto de cartão adaptável ( ), e precisamos de uma maneira de comunicar Teams ao `task/fetch` `value` `Action.Submit` `data` `context` bot, `value` / além do `data` que foi incluído em .<br/><br/>Fazemos isso combinando os dois em um objeto pai:<br/><br/><pre>{<br/>  "context": {<br/>    "theme": "default" &vert; "dark" &vert; "contrast",<br/>  },<br/>  "data": [value field from Bot Framework card] &vert; [data field from Adaptive Card] <br/>}</pre>  |

## <a name="example-receiving-and-responding-to-taskfetch-and-tasksubmit-invoke-messages---nodejs"></a>Exemplo: receber e responder a mensagens de invocação de tarefa/busca e tarefa/envio - Node.js

> [!NOTE]
> O código de exemplo abaixo foi modificado entre a Visualização Técnica e a versão final deste recurso: o esquema da solicitação foi alterado para seguir o que foi `task/fetch` [documentado na seção anterior](#payload-of-taskfetch-and-tasksubmit-messages). Ou seja, a documentação estava correta, mas a implementação não estava. Consulte os `// for Technical Preview [...]` comentários abaixo para saber o que mudou.

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

## <a name="example-receiving-and-responding-to-taskfetch-and-tasksubmit-invoke-messages---c"></a>Exemplo: receber e responder a mensagens de invocação de tarefa/busca e tarefa/envio - C #

No C# bots, `invoke` as mensagens são processadas por um `HttpResponseMessage()` controlador que processa uma `Activity` mensagem. As `task/fetch` `task/submit` solicitações e e respostas são JSON. No C#, não é tão conveniente lidar com JSON bruto como está no Node.js, portanto, você precisa de classes de wrapper para manipular a serialização de e para JSON. Ainda não há suporte direto para isso no [SDK](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) do Microsoft Teams C#, mas você pode ver um exemplo de como essas classes simples de wrapper seriam no aplicativo de exemplo [C#](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Models/TaskModel.cs).

Veja a seguir o exemplo de código C# para manipulação e mensagens usando essas classes de `task/fetch` `task/submit` wrapper ( `TaskInfo` , ), `TaskEnvelope` trechos do [exemplo](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs):

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

Não mostrada no exemplo acima é a `SetTaskInfo()` função, que define `height` as propriedades , e do objeto para cada `width` `title` `TaskInfo` caso. Aqui está o [código-fonte para SetTaskInfo()](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs).

### <a name="bot-framework-card-actions-vs-adaptive-card-actionsubmit-actions"></a>Ações de cartão da Estrutura de Bot vs. Ações de cartão adaptáveis.Enviar ações

O esquema para ações de cartão da Estrutura de Bot é ligeiramente diferente das ações de cartão `Action.Submit` adaptáveis. Como resultado, a maneira de invocar módulos de tarefa também é ligeiramente diferente: o objeto contém um objeto para que ele não interfira com outras propriedades `data` `Action.Submit` no `msteams` cartão. A tabela a seguir mostra um exemplo de cada um:

| Ação de cartão da Estrutura de Bot                              | Ação Action.Submit do cartão adaptável                     |
| ------------------------------------------------------ | ------------------------------------------------------ |
| <pre>{<br/>  "type": "invoke",<br/>  "title": "Buy",<br/>  "value": {<br/>    "type": "task/fetch",<br/>    &lt;...&gt;<br/>  }<br/>}</pre> | <pre>{<br/>  "type": "Action.Submit",<br/>  "id": "btnBuy",<br/>  "title": "Buy",<br/>  "data": {<br/>    &lt;...&gt;,<br/>    "msteams": {<br/>      "type": "task/fetch"<br/>    }<br/>  }<br/>}</pre>  |

## <a name="see-also"></a>Confira também

* [Microsoft Teams código de exemplo do módulo de tarefa — nodejs](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs/blob/master/src/TeamsBot.ts)
* [Exemplos de Estrutura de Bot](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).