---
title: Usar módulos de tarefa em bots do Microsoft Teams
description: Saiba como usar módulos de tarefa com Microsoft Teams bots, incluindo cartões do Bot Framework, cartões adaptáveis e links profundos.
ms.localizationpriority: medium
ms.topic: how-to
ms.openlocfilehash: e7bed83d9f13913b9a72997ac3679f844db3034a
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66142980"
---
# <a name="use-task-modules-from-bots"></a>Usar módulos de tarefas dos bots

Os módulos de tarefa podem ser invocados Microsoft Teams bots usando botões em Cartões Adaptáveis e cartões do Bot Framework que são hero, thumbnail e Office 365 Connector. Os módulos de tarefa geralmente são uma melhor experiência do usuário do que várias etapas de conversa. Acompanhe o estado do bot e permita que o usuário interrompa ou cancele a sequência.

Há duas maneiras de invocar módulos de tarefa:

* Uma nova mensagem de invocação: `invoke` usar a ação de cartão para cartões do Bot Framework [](~/task-modules-and-cards/cards/cards-actions.md#action-type-invoke) `Action.Submit` ou a ação de cartão para cartões adaptáveis, [](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) `task/fetch`com um módulo de tarefa, uma URL ou um Cartão Adaptável, é buscada dinamicamente no bot.`task/fetch`
* URLs de link direto: usando a [sintaxe de link direto para módulos de tarefa](~/task-modules-and-cards/task-modules/invoking-task-modules.md#task-module-deep-link-syntax), você pode usar a `openUrl` [ação de cartão](~/task-modules-and-cards/cards/cards-actions.md#action-type-openurl) para cartões do Bot Framework ou a `Action.OpenUrl` [ação de cartão](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) para Cartões Adaptáveis, respectivamente. Com URLs de link profundo, a URL do módulo de tarefa ou o corpo do Cartão Adaptável já é conhecido por evitar uma viagem de ida e volta do servidor em relação a `task/fetch`.

> [!IMPORTANT]
> Cada `url` e `fallbackUrl` deve implementar o protocolo de criptografia HTTPS.

A próxima seção fornece detalhes sobre como invocar um módulo de tarefa usando `task/fetch`.

## <a name="invoke-a-task-module-using-taskfetch"></a>Invocar um módulo de tarefa usando tarefa/busca

Quando o objeto `value` da ação de cartão `invoke` ou `Action.Submit` é inicializado e quando um usuário seleciona o botão, uma `invoke` mensagem é enviada ao bot. Na resposta HTTP à mensagem`invoke`, há um objeto [TaskInfo](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object) inserido em um objeto wrapper, que Teams usa para exibir o módulo de tarefa.

:::image type="content" source="../../assets/images/task-module/task-module-invoke-request-response.png" alt-text="tarefa/buscar solicitação ou resposta":::

As etapas a seguir fornecem o módulo de tarefa de invocação usando tarefa/busca:

1. Esta imagem mostra um cartão hero Bot Framework com um **comprar** `invoke` [ação de cartão](~/task-modules-and-cards/cards/cards-actions.md#action-type-invoke). O valor da propriedade `type` é `task/fetch` e o restante do objeto `value` pode ser de sua escolha.
1. O bot recebe a mensagem HTTP POST `invoke`.
1. O bot cria um objeto de resposta e o retorna no corpo da resposta POST com um código de resposta HTTP 200. Para obter mais informações sobre o esquema para respostas, consulte [a discussão sobre tarefa/envio](#the-flexibility-of-tasksubmit). O código a seguir fornece um exemplo de corpo da resposta HTTP que contém um objeto [TaskInfo](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object) inserido em um objeto wrapper:

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

    O evento `task/fetch` e sua resposta para bots é semelhante à função `microsoftTeams.tasks.startTask()` no SDK do cliente.

1. O Microsoft Teams exibe o módulo de tarefa.

A próxima seção fornece detalhes sobre como enviar o resultado de um módulo de tarefa.

## <a name="submit-the-result-of-a-task-module"></a>Enviar o resultado de um módulo de tarefa

Quando o usuário é concluído com o módulo de tarefa, enviar o resultado de volta para o bot é semelhante à maneira como ele funciona com guias. Para obter mais informações, consulte [exemplo de enviar o resultado de um módulo de tarefa](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-of-submitting-the-result-of-a-task-module). Há algumas diferenças da seguinte maneira:

* HTML ou JavaScript `TaskInfo.url`, ou seja: depois de validar o que o usuário inseriu, `microsoftTeams.tasks.submitTask()` chame a função do SDK `submitTask()` conhecida daqui em diante como para fins de legibilidade. Você pode chamar `submitTask()` sem parâmetros se quiser que o Teams feche o módulo de tarefa, mas passe um objeto ou uma cadeia de caracteres para seu `submitHandler`. Passe-o como o primeiro parâmetro, `result`. O Teams invoca `submitHandler`, `err` é `null`, e `result` é o objeto ou cadeia de caracteres que você passou para `submitTask()`. Se você chamar `submitTask()` com um parâmetro `result`, você deve passar um `appId` ou uma matriz de cadeias de caracteres `appId`. Isso permite Teams validar se o aplicativo que envia o resultado é o mesmo, que invocou o módulo de tarefa. Seu bot recebe uma mensagem `task/submit` incluindo `result`. Para obter mais informações, consulte [conteúdo de `task/fetch` e `task/submit`](#payload-of-taskfetch-and-tasksubmit-messages).
* Cartão Adaptável que é `TaskInfo.card`: o corpo do Cartão Adaptável preenchido pelo usuário é enviado ao bot por meio de um `task/submit` quando o usuário seleciona qualquer botão `Action.Submit`.

A próxima seção fornece detalhes sobre a flexibilidade de `task/submit`.

## <a name="the-flexibility-of-tasksubmit"></a>A flexibilidade da tarefa/envio

Quando o usuário termina com um módulo de tarefa invocado de um bot, o bot sempre recebe uma mensagem `task/submit invoke`. Você tem várias opções ao responder à mensagem `task/submit` da seguinte maneira:

| Resposta do corpo HTTP                      | Cenário                                |
| --------------------------------------- | --------------------------------------- |
| Nenhum ignora a `task/submit` mensagem | A resposta mais simples não é nenhuma resposta. O bot não precisa responder quando o usuário terminar o módulo de tarefa. |
| <pre>{<br/>  "task": {<br/>    "type": "message",<br/>    "value": "Message text"<br/>  }<br/>}</pre> | O Teams exibe o valor de `value` em uma caixa de mensagem pop-up. |
| <pre>{<br/>  "task": {<br/>    "type": "continue",<br/>    "value": &lt;TaskInfo object&gt;<br/>  }<br/>}</pre> | Permite encadear sequências de Cartões Adaptáveis em uma experiência de assistente ou de várias etapas. |

> [!NOTE]
> O encadeamento Cartões Adaptáveis em uma sequência é um cenário avançado. O aplicativo de exemplo Node.js dá suporte a ele. Para obter mais informações, consulte [ Módulo de tarefa Node.js do Microsoft Teams](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs#implementation-notes).

A próxima seção fornece detalhes sobre o conteúdo das mensagens `task/fetch` e `task/submit`.

## <a name="payload-of-taskfetch-and-tasksubmit-messages"></a>Conteúdo de tarefa/busca e tarefa/envio de mensagens

Esta seção define o esquema do que seu bot recebe quando recebe um objeto `task/fetch` ou `task/submit` Bot Framework `Activity`. A tabela a seguir fornece as propriedades de conteúdo das mensagens `task/fetch` e `task/submit`:

| Propriedade | Descrição                          |
| -------- | ------------------------------------ |
| `type`   | É sempre `invoke`.           |
| `name`   | É `task/fetch` ou `task/submit`. |
| `value`  | É a carga definida pelo desenvolvedor. A estrutura do objeto `value` é igual ao que é enviado do Teams. Nesse caso, no entanto, é diferente. Ele requer suporte para uma pesquisa dinâmica que é `task/fetch` de ambos os Bot Framework, que é `value` e as ações `Action.Submit`, que são `data`. Uma maneira de comunicar o Teams `context` ao bot é necessária além do que está incluído no `value` ou `data`.<br/><br/>Combine 'value' e 'data' em um objeto pai:<br/><br/><pre>{<br/>  "context": {<br/>    "theme": "default" &vert; "dark" &vert; "contrast",<br/>  },<br/>  "data": [value field from Bot Framework card] &vert; [data field from Adaptive Card] <br/>}</pre>  |

A próxima seção fornece um exemplo de recebimento e resposta a `task/fetch` e `task/submit` invocam mensagens no Node.js.

## <a name="example-of-taskfetch-and-tasksubmit-invoke-messages-in-nodejs-and-c"></a>Exemplo de tarefa/busca e tarefa/envio de mensagens de invocação em Node.js e C#

# <a name="nodejs"></a>[Node.js](#tab/nodejs)

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

# <a name="c"></a>[C#](#tab/csharp)

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

### <a name="bot-framework-card-actions-vs-adaptive-card-actionsubmit-actions"></a>Bot Framework ações do cartão vs. Ação do Cartão Adaptável.Enviar ações

O esquema para ações de cartão Bot Framework é diferente das ações `Action.Submit` e a maneira de invocar módulos de tarefa também é diferente. O `data` objeto em `Action.Submit` contém um `msteams` objeto para que ele não interfira com outras propriedades no cartão. A tabela a seguir mostra um exemplo de cada ação de cartão:

| Bot Framework ação do cartão                              | Ação De Cartão Adaptável.Enviar ação                     |
| ------------------------------------------------------ | ------------------------------------------------------ |
| <pre>{<br/>  "type": "invoke",<br/>  "title": "Buy",<br/>  "value": {<br/>    "type": "task/fetch",<br/>    &lt;...&gt;<br/>  }<br/>}</pre> | <pre>{<br/>  "type": "Action.Submit",<br/>  "id": "btnBuy",<br/>  "title": "Buy",<br/>  "data": {<br/>    &lt;...&gt;,<br/>    "msteams": {<br/>      "type": "task/fetch"<br/>    }<br/>  }<br/>}</pre>  |

## <a name="code-sample"></a>Exemplo de código

|Nome do exemplo | Descrição | .NET | Node.js|
|----------------|-----------------|--------------|----------------|
|Bots de exemplo do módulo de tarefa -V4 | Exemplos para criar módulos de tarefa. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/54.teams-task-module)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/54.teams-task-module)|

## <a name="step-by-step-guide"></a>Guias passo a passo

Siga a [guia passo a passo](../../sbs-botbuilder-taskmodule.yml) para criar e buscar o bot do módulo de tarefa no Teams.

## <a name="see-also"></a>Confira também

* [código de exemplo de módulo de tarefa do Microsoft Teams no Node.js](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs/blob/master/src/TeamsBot.ts)
* [Exemplos do Bot Framework](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md)
