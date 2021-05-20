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
# <a name="using-task-modules-from-microsoft-teams-bots"></a>Usando módulos de tarefas de bots Microsoft Teams

Os módulos de tarefa podem ser invocados a partir de bots Microsoft Teams usando botões em placas adaptativas e cartões Bot Framework (Hero, Miniatura e Office 365 Conector). Os módulos de tarefa são muitas vezes uma melhor experiência do usuário do que várias etapas de conversação onde você, como desenvolvedor, tem que acompanhar o estado do bot e permitir que o usuário interrompa/cancele a sequência.

Existem duas maneiras de invocar módulos de tarefa:

* **Um novo tipo de mensagem de `task/fetch` invocação.** Usando a `invoke` [ação](~/task-modules-and-cards/cards/cards-actions.md#invoke) do cartão para cartões Bot Framework ou a `Action.Submit` [ação](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) do cartão para cartões Adaptive, com `task/fetch` , o módulo de tarefa (uma URL ou uma placa Adaptive) é obtido dinamicamente do seu bot.
* **URLs de ligação profunda.** Usando a [sintaxe de link profundo para módulos de tarefa,](~/task-modules-and-cards/what-are-task-modules.md#task-module-deep-link-syntax)você pode usar a `openUrl` [ação](~/task-modules-and-cards/cards/cards-actions.md#openurl) do cartão para cartões Bot Framework ou `Action.OpenUrl` [a ação](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) do cartão para cartões Adaptativos, respectivamente. Com URLs de link profundo, a URL do módulo de tarefa ou o corpo de cartão adaptável é obviamente conhecido com antecedência, evitando uma ida e volta de servidor em relação a `task/fetch` .

>[!IMPORTANT]
>Para garantir comunicações seguras, cada um `url` e deve implementar o protocolo de criptografia `fallbackUrl` HTTPS.

## <a name="invoking-a-task-module-through-taskfetch"></a>Invocando um módulo de tarefa através de tarefa/busca

Quando o `value` objeto da ação do `invoke` cartão ou `Action.Submit` é inicializado da maneira adequada (explicado com mais detalhes abaixo), quando um usuário pressiona o botão uma `invoke` mensagem é enviada para o bot. Na resposta HTTP à `invoke` mensagem, há um [objeto TaskInfo](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) incorporado em um objeto invólucro, que Teams usa para exibir o módulo de tarefa.

![tarefa/buscar solicitação/resposta](~/assets/images/task-module/task-module-invoke-request-response.png)

Vamos olhar cada passo com um pouco mais de detalhes:

1. Este exemplo mostra um cartão Bot Framework Hero com uma `invoke` [ação de cartão "Comprar".](~/task-modules-and-cards/cards/cards-actions.md#invoke) O valor da `type` propriedade é - o resto do objeto pode ser o que você `task/fetch` `value` quiser.
1. O bot recebe a `invoke` mensagem HTTP POST.
1. O bot cria um objeto de resposta e o devolve no corpo da resposta POST com um código de resposta HTTP 200. O esquema de respostas é descrito [abaixo na discussão sobre tarefa/envio,](#the-flexibility-of-tasksubmit)mas o importante a ser lembrado agora é que o corpo da resposta HTTP contém um objeto [TaskInfo](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) incorporado em um objeto invólucro. Por exemplo:

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

    O `task/fetch` evento e sua resposta para bots é semelhante, conceitualmente, à função no `microsoftTeams.tasks.startTask()` SDK cliente.
1. Microsoft Teams exibe o módulo de tarefa.

## <a name="submitting-the-result-of-a-task-module"></a>Submeter o resultado de um módulo de tarefa

Quando o usuário termina com o módulo de tarefa, enviar o resultado de volta para o bot é semelhante [à maneira como ele funciona com guias,](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-submitting-the-result-of-a-task-module)mas há algumas diferenças, por isso é descrito aqui também.

* **HTML/JavaScript ( `TaskInfo.url` )**. Depois de validar o que o usuário inseriu, você chama a `microsoftTeams.tasks.submitTask()` função SDK (referida para fins de `submitTask()` leitura). Você pode ligar `submitTask()` sem parâmetros se quiser Teams fechar o módulo de tarefa, mas na maioria das vezes você vai querer passar um objeto ou uma string para o seu `submitHandler` . Basta passá-lo como o primeiro parâmetro, `result` . Teams invocará `submitHandler` : `err` será e será `null` o `result` objeto/string para o que você passou `submitTask()` . Se você ligar `submitTask()` com um `result` parâmetro, você **deve** passar por uma ou uma série `appId` de `appId` strings: isso permite que Teams validar que o aplicativo que envia o resultado é o mesmo que invocou o módulo de tarefa. Seu bot receberá uma `task/submit` mensagem, incluindo `result` como descrito [abaixo](#payload-of-taskfetch-and-tasksubmit-messages).
* **Cartão adaptativo ( `TaskInfo.card` )**. O corpo do cartão adaptável (preenchido pelo usuário) será enviado ao bot através de uma `task/submit` mensagem quando o usuário pressionar qualquer `Action.Submit` botão.

## <a name="the-flexibility-of-tasksubmit"></a>A flexibilidade da tarefa/envio

Na seção anterior, você aprendeu que quando o usuário termina com um módulo de tarefa invocado a partir de um bot, o bot sempre recebe uma `task/submit invoke` mensagem. Como desenvolvedor, você tem várias opções ao *responder* à `task/submit` mensagem:

| Resposta do corpo HTTP                      | Cenário                                |
| --------------------------------------- | --------------------------------------- |
| Nenhum (ignore a `task/submit` mensagem) | A resposta mais simples não é nenhuma resposta. O bot não é obrigado a responder quando o usuário terminar com o módulo de tarefa. |
| <pre>{<br/>  "task": {<br/>    "type": "message",<br/>    "value": "Message text"<br/>  }<br/>}</pre> | Teams exibirá o valor de uma caixa de `value` mensagens pop-up. |
| <pre>{<br/>  "task": {<br/>    "type": "continue",<br/>    "value": &lt;TaskInfo object&gt;<br/>  }<br/>}</pre> | Permite que você "acorrente" sequências de cartões adaptativos em uma experiência assistente/várias etapas. _Observe que encadear placas adaptativas em uma sequência é um cenário avançado e não documentado aqui. O aplicativo de amostra Node.js suporta, no entanto, e como ele funciona é documentado em [seu arquivo README.md](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs#implementation-notes)._ |

## <a name="payload-of-taskfetch-and-tasksubmit-messages"></a>Carga útil de mensagens de tarefa/busca e tarefa/envio

Esta seção define o esquema do que o bot recebe quando recebe um `task/fetch` objeto ou `task/submit` Bot `Activity` Framework. O importante nível superior aparece abaixo:

| Propriedade | Descrição                          |
| -------- | ------------------------------------ |
| `type`   | Sempre será `invoke`              |
| `name`   | Ou `task/fetch``task/submit` |
| `value`  | A carga definida pelo desenvolvedor. Normalmente, a estrutura do `value` objeto espelha o que foi enviado de Teams. Neste caso, porém, é diferente porque queremos apoiar a busca dinâmica ( `task/fetch` ) tanto das ações do Bot Framework ( ) quanto do cartão `value` adaptável ( ), e precisamos `Action.Submit` de uma maneira de comunicar Teams ao `data` `context` bot, além `value` / `data` do que foi incluído em .<br/><br/>Fazemos isso combinando os dois em um objeto pai:<br/><br/><pre>{<br/>  "context": {<br/>    "theme": "default" &vert; "dark" &vert; "contrast",<br/>  },<br/>  "data": [value field from Bot Framework card] &vert; [data field from Adaptive Card] <br/>}</pre>  |

## <a name="example-receiving-and-responding-to-taskfetch-and-tasksubmit-invoke-messages---nodejs"></a>Exemplo: Receber e responder a mensagens de busca e busca de tarefas e envios de tarefas - Node.js

> [!NOTE]
> O código de amostra abaixo foi modificado entre a Visualização Técnica e a versão final deste recurso: o esquema da `task/fetch` solicitação mudou para seguir o que estava documentado na [seção anterior](#payload-of-taskfetch-and-tasksubmit-messages). Ou seja, a documentação estava correta, mas a implementação não foi. Veja os `// for Technical Preview [...]` comentários abaixo para o que mudou.

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

## <a name="example-receiving-and-responding-to-taskfetch-and-tasksubmit-invoke-messages---c"></a>Exemplo: Receber e responder a mensagens de busca e busca de tarefas e envios de tarefas - C #

Em bots C#, `invoke` as mensagens são processadas por um `HttpResponseMessage()` controlador processando uma `Activity` mensagem. Os `task/fetch` `task/submit` pedidos e respostas são JSON. Em C#, não é tão conveniente lidar com JSON cru como é em Node.js, então você precisa de aulas de invólucro para lidar com a serialização de e para JSON. Ainda não há suporte direto para isso no Microsoft Teams [C# SDK,](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) mas você pode ver um exemplo de como essas classes simples de invólucro seriam no [aplicativo de amostra C#](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Models/TaskModel.cs).

Abaixo está o código de exemplo em C# para manuseio `task/fetch` e `task/submit` mensagens usando essas classes de invólucro ( `TaskInfo` , , `TaskEnvelope` exceto da [amostra](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs):

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

Não mostrado no exemplo acima é a `SetTaskInfo()` função, que define o `height` , e propriedades do objeto para cada `width` `title` `TaskInfo` caso. Aqui está o [código-fonte do SetTaskInfo().](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp/blob/master/Microsoft.Teams.Samples.TaskModule.Web/Controllers/MessagesController.cs)

### <a name="bot-framework-card-actions-vs-adaptive-card-actionsubmit-actions"></a>Ações do cartão Bot Framework vs. Ação de cartão adaptativo.Enviar ações

O esquema para as ações do cartão Bot Framework é ligeiramente diferente das ações de cartão `Action.Submit` Adaptive. Como resultado, a maneira de invocar módulos de tarefa também é ligeiramente diferente: o `data` objeto em contém um objeto para que ele não `Action.Submit` `msteams` interfira com outras propriedades no cartão. A tabela a seguir mostra um exemplo de cada um:

| Ação do cartão Bot Framework                              | Ação de cartão adaptativo.Enviar ação                     |
| ------------------------------------------------------ | ------------------------------------------------------ |
| <pre>{<br/>  "type": "invoke",<br/>  "title": "Buy",<br/>  "value": {<br/>    "type": "task/fetch",<br/>    &lt;...&gt;<br/>  }<br/>}</pre> | <pre>{<br/>  "type": "Action.Submit",<br/>  "id": "btnBuy",<br/>  "title": "Buy",<br/>  "data": {<br/>    &lt;...&gt;,<br/>    "msteams": {<br/>      "type": "task/fetch"<br/>    }<br/>  }<br/>}</pre>  |

## <a name="see-also"></a>Confira também

* [Microsoft Teams código de amostra do módulo de tarefas — nodejs](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs/blob/master/src/TeamsBot.ts)
* [Amostras do Bot Framework](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).