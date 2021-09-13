---
title: Usar Módulos de Tarefa em Microsoft Teams bots
description: Como usar módulos de tarefa com Microsoft Teams bots, incluindo cartões da Estrutura de Bot, cartões adaptáveis e links profundos.
ms.localizationpriority: medium
ms.topic: how-to
keywords: bots de equipes de módulos de tarefa
ms.openlocfilehash: a548f0d0ae3853f447ba55409bf9edbecced4e60
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59155459"
---
# <a name="use-task-modules-from-bots"></a>Usar módulos de tarefas dos bots

Os módulos de tarefa podem ser invocados Microsoft Teams bots usando botões em Cartões Adaptáveis e cartões de Estrutura de Bot que são hero, miniatura e conector Office 365 Bot. Os módulos de tarefas geralmente são uma experiência de usuário melhor do que várias etapas de conversa. Acompanhe o estado do bot e permita que o usuário interrompa ou cancele a sequência.

Há duas maneiras de invocar módulos de tarefa:

* Um novo tipo de mensagem de invocação : Usar a ação de cartão para cartões da Estrutura de Bot ou a ação de cartão para cartões adaptáveis, com um módulo de tarefa, uma URL ou um Cartão Adaptável, é buscada `task/fetch` `invoke` [](~/task-modules-and-cards/cards/cards-actions.md#action-type-invoke) `Action.Submit` [](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) `task/fetch` dinamicamente no bot.
* URLs de link profundo: usando a sintaxe de link profundo para [módulos](~/task-modules-and-cards/task-modules/invoking-task-modules.md#task-module-deep-link-syntax)de tarefa, você pode usar a ação de cartão para cartões de Estrutura de Bot ou a ação de cartão para Cartões `openUrl` [](~/task-modules-and-cards/cards/cards-actions.md#action-type-openurl) `Action.OpenUrl` [](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) Adaptáveis, respectivamente. Com URLs de link profundo, a URL do módulo de tarefas ou o corpo do Cartão Adaptável já é conhecido para evitar uma ida e volta do servidor em relação a `task/fetch` .

> [!IMPORTANT]
> Cada `url` um deles e deve implementar o protocolo de criptografia `fallbackUrl` HTTPS.

A próxima seção fornece detalhes sobre como invocar um módulo de tarefa usando `task/fetch` .

## <a name="invoke-a-task-module-using-taskfetch"></a>Invocar um módulo de tarefa usando tarefa/busca

Quando o objeto da ação do cartão ou é inicializado e quando um usuário seleciona o botão, uma mensagem `value` é enviada para o `invoke` `Action.Submit` `invoke` bot. Na resposta HTTP à mensagem, há um objeto TaskInfo inserido em um objeto wrapper, que Teams usa para `invoke` exibir o módulo de tarefa. [](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object)

![solicitação ou resposta de tarefa/busca](~/assets/images/task-module/task-module-invoke-request-response.png)

As etapas a seguir fornece o módulo de tarefa chamar usando tarefa/busca:

1. Esta imagem mostra um cartão de herói da Estrutura de Bot com uma **ação comprar** `invoke` [cartão](~/task-modules-and-cards/cards/cards-actions.md#action-type-invoke). O valor da `type` propriedade é e o restante do objeto pode ser de sua `task/fetch` `value` escolha.
1. O bot recebe a `invoke` mensagem HTTP POST.
1. O bot cria um objeto de resposta e o retorna no corpo da resposta POST com um código de resposta HTTP 200. Para obter mais informações sobre o esquema para respostas, consulte [a discussão sobre tarefa/envio.](#the-flexibility-of-tasksubmit) O código a seguir fornece um exemplo de corpo da resposta HTTP que contém um [objeto TaskInfo](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object) inserido em um objeto wrapper:

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

    O `task/fetch` evento e sua resposta para bots é semelhante à função no `microsoftTeams.tasks.startTask()` SDK do cliente.

1. Microsoft Teams exibe o módulo de tarefa.

A próxima seção fornece detalhes sobre como enviar o resultado de um módulo de tarefa.

## <a name="submit-the-result-of-a-task-module"></a>Enviar o resultado de um módulo de tarefa

Quando o usuário é concluído com o módulo de tarefa, enviar o resultado de volta para o bot é semelhante à maneira como ele funciona com guias. Para obter mais informações, [consulte o exemplo de envio do resultado de um módulo de tarefa](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-of-submitting-the-result-of-a-task-module). Há algumas diferenças da seguinte forma:

* HTML ou JavaScript que é : Depois de validar o que o usuário entrou, você chama a função SDK conhecida a seguir como para fins de capacidade `TaskInfo.url` `microsoftTeams.tasks.submitTask()` de `submitTask()` leitura. Você pode chamar sem parâmetros se quiser Teams o módulo de tarefa, mas deve passar um objeto ou uma `submitTask()` cadeia de caracteres para seu `submitHandler` . Passe-o como o primeiro parâmetro, `result` . Teams invoca , é , e é o objeto ou cadeia de `submitHandler` `err` `null` `result` caracteres que você passou para `submitTask()` . Se você chamar `submitTask()` com um `result` parâmetro, deverá passar uma ou uma `appId` matriz de `appId` cadeias de caracteres. Isso permite Teams validar se o aplicativo que está enviando o resultado é o mesmo que invocou o módulo de tarefa. Seu bot recebe uma `task/submit` mensagem incluindo `result` . Para obter mais informações, [consulte carga de e `task/fetch` `task/submit` mensagens](#payload-of-taskfetch-and-tasksubmit-messages).
* Cartão Adaptável que é : O corpo do Cartão Adaptável conforme preenchido pelo usuário é enviado para o bot por meio de uma mensagem quando o usuário `TaskInfo.card` `task/submit` seleciona qualquer `Action.Submit` botão.

A próxima seção fornece detalhes sobre a flexibilidade de `task/submit` .

## <a name="the-flexibility-of-tasksubmit"></a>A flexibilidade de tarefa/envio

Quando o usuário termina com um módulo de tarefa invocado de um bot, o bot sempre recebe uma `task/submit invoke` mensagem. Você tem várias opções ao responder à `task/submit` mensagem da seguinte forma:

| Resposta de corpo HTTP                      | Cenário                                |
| --------------------------------------- | --------------------------------------- |
| Nenhum ignora a `task/submit` mensagem | A resposta mais simples não é nenhuma resposta. Seu bot não é necessário para responder quando o usuário terminar com o módulo de tarefa. |
| <pre>{<br/>  "task": {<br/>    "type": "message",<br/>    "value": "Message text"<br/>  }<br/>}</pre> | Teams exibe o valor de `value` em uma caixa de mensagem pop-up. |
| <pre>{<br/>  "task": {<br/>    "type": "continue",<br/>    "value": &lt;TaskInfo object&gt;<br/>  }<br/>}</pre> | Permite encadear sequências de Cartões Adaptáveis em conjunto em um assistente ou experiência em várias etapas. |

> [!NOTE]
> Encadear cartões adaptáveis em uma sequência é um cenário avançado. O Node.js de exemplo oferece suporte a ele. Para obter mais informações, [consulte Microsoft Teams módulo de tarefas Node.js](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs#implementation-notes).

A próxima seção fornece detalhes sobre carga e `task/fetch` `task/submit` mensagens.

## <a name="payload-of-taskfetch-and-tasksubmit-messages"></a>Carga de mensagens de tarefa/busca e tarefa/envio

Esta seção define o esquema do que seu bot recebe quando recebe um `task/fetch` objeto `task/submit` Ou Bot `Activity` Framework. A tabela a seguir fornece as propriedades de carga e `task/fetch` `task/submit` mensagens:

| Propriedade | Descrição                          |
| -------- | ------------------------------------ |
| `type`   | É sempre `invoke` .           |
| `name`   | É ou `task/fetch` `task/submit` . |
| `value`  | É a carga definida pelo desenvolvedor. A estrutura do `value` objeto é a mesma que é enviada de Teams. Nesse caso, no entanto, é diferente. Ele requer suporte para busca dinâmica que é `task/fetch` da Estrutura de Bot, que é e `value` ações do Cartão `Action.Submit` Adaptável, que é `data` . Uma maneira de comunicar Teams ao bot é necessária, além do `context` que está incluído em ou `value` `data` .<br/><br/>Combinar 'valor' e 'dados' em um objeto pai:<br/><br/><pre>{<br/>  "context": {<br/>    "theme": "default" &vert; "dark" &vert; "contrast",<br/>  },<br/>  "data": [value field from Bot Framework card] &vert; [data field from Adaptive Card] <br/>}</pre>  |

A próxima seção fornece um exemplo de recebimento e resposta e `task/fetch` `task/submit` invocação de mensagens Node.js.

## <a name="example-of-taskfetch-and-tasksubmit-invoke-messages-in-nodejs-and-c"></a>Exemplo de tarefa/busca e tarefa/envio de mensagens invocadas Node.js e C #

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

### <a name="bot-framework-card-actions-vs-adaptive-card-actionsubmit-actions"></a>Ações de cartão da Estrutura de Bot vs. Ação do Cartão Adaptável.Enviar ações

O esquema para ações de cartão da Estrutura de Bot é diferente das ações do Cartão Adaptável e a maneira de invocar módulos de `Action.Submit` tarefa também é diferente. O `data` objeto em contém um objeto para que ele não interfira com outras propriedades no `Action.Submit` `msteams` cartão. A tabela a seguir mostra um exemplo de cada ação de cartão:

| Ação de cartão da Estrutura de Bot                              | Ação do Cartão Adaptável.Enviar                     |
| ------------------------------------------------------ | ------------------------------------------------------ |
| <pre>{<br/>  "type": "invoke",<br/>  "title": "Buy",<br/>  "value": {<br/>    "type": "task/fetch",<br/>    &lt;...&gt;<br/>  }<br/>}</pre> | <pre>{<br/>  "type": "Action.Submit",<br/>  "id": "btnBuy",<br/>  "title": "Buy",<br/>  "data": {<br/>    &lt;...&gt;,<br/>    "msteams": {<br/>      "type": "task/fetch"<br/>    }<br/>  }<br/>}</pre>  |

## <a name="code-sample"></a>Exemplo de código

|Nome do exemplo | Descrição | .NET | Node.js|
|----------------|-----------------|--------------|----------------|
|Exemplo de módulo de tarefa bots-V4 | Exemplos para a criação de módulos de tarefa. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/54.teams-task-module)|[Exibir](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/54.teams-task-module)|

## <a name="see-also"></a>Confira também

* [Microsoft Teams exemplo de módulo de tarefa no Node.js](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs/blob/master/src/TeamsBot.ts)
* [Exemplos de Estrutura de Bot](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md)
