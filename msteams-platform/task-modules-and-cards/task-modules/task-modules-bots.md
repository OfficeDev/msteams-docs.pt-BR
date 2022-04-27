---
title: Usar módulos de tarefa em Microsoft Teams bots
description: Como usar módulos de tarefa com Microsoft Teams bots, incluindo cartões do Bot Framework, cartões adaptáveis e links profundos.
ms.localizationpriority: medium
ms.topic: how-to
keywords: módulos de tarefa equipes bots deep links cartão adaptável
ms.openlocfilehash: 7391f7e0d9da444831b98b4b6b69a97b35298800
ms.sourcegitcommit: 3bfd0d2c4d83f306023adb45c8a3f829f7150b1d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65073765"
---
# <a name="use-task-modules-from-bots"></a>Usar módulos de tarefas dos bots

Os módulos de tarefa podem ser invocados Microsoft Teams bots usando botões em Cartões Adaptáveis e cartões do Bot Framework que são hero, miniatura e conector Office 365. Os módulos de tarefa geralmente são uma experiência de usuário melhor do que várias etapas de conversa. Acompanhe o estado do bot e permita que o usuário interrompa ou cancele a sequência.

Há duas maneiras de invocar módulos de tarefa:

* Um novo tipo de mensagem de invocação: `invoke` [](~/task-modules-and-cards/cards/cards-actions.md#action-type-invoke) usar a ação de cartão para cartões do Bot Framework `Action.Submit` ou a ação de cartão para cartões adaptáveis, [](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) `task/fetch`com um módulo de tarefa, uma URL ou um Cartão Adaptável, é buscada dinamicamente no bot.`task/fetch`
* URLs de link profundo: usando a sintaxe de link profundo para [](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions) [módulos](~/task-modules-and-cards/task-modules/invoking-task-modules.md#task-module-deep-link-syntax) de tarefa, `openUrl` você pode usar a ação de cartão para cartões do Bot Framework [](~/task-modules-and-cards/cards/cards-actions.md#action-type-openurl) `Action.OpenUrl` ou a ação de cartão para Cartões Adaptáveis, respectivamente. Com URLs de link profundo, a URL do módulo de tarefa ou o corpo do Cartão Adaptável já é conhecido por evitar uma viagem de ida e volta do servidor em relação a `task/fetch`.

> [!IMPORTANT]
> Cada `url` um deles `fallbackUrl` e deve implementar o protocolo de criptografia HTTPS.

A próxima seção fornece detalhes sobre como invocar um módulo de tarefa usando `task/fetch`.

## <a name="invoke-a-task-module-using-taskfetch"></a>Invocar um módulo de tarefa usando tarefa/busca

Quando o `value` objeto da ação `invoke` do cartão `Action.Submit` ou é inicializado e quando um usuário seleciona o botão, uma `invoke` mensagem é enviada para o bot. Na resposta HTTP à mensagem`invoke`, há um objeto [TaskInfo](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object) inserido em um objeto wrapper, que Teams usa para exibir o módulo de tarefa.

:::image type="content" source="../../assets/images/task-module/task-module-invoke-request-response.png" alt-text="solicitação ou resposta de tarefa/busca":::

As etapas a seguir fornecem o módulo de tarefa de invocação usando tarefa/busca:

1. Esta imagem mostra um cartão hero do Bot Framework com uma **ação Comprar** `invoke` [cartão](~/task-modules-and-cards/cards/cards-actions.md#action-type-invoke). O valor da propriedade `type` é `task/fetch` e o restante do objeto `value` pode ser de sua escolha.
1. O bot recebe a mensagem `invoke` HTTP POST.
1. O bot cria um objeto de resposta e o retorna no corpo da resposta POST com um código de resposta HTTP 200. Para obter mais informações sobre o esquema para respostas, [consulte a discussão sobre tarefa/envio](#the-flexibility-of-tasksubmit). O código a seguir fornece um exemplo de corpo da resposta HTTP que contém um [objeto TaskInfo](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object) inserido em um objeto wrapper:

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

    O `task/fetch` evento e sua resposta para bots são semelhantes à `microsoftTeams.tasks.startTask()` função no SDK do cliente.

1. Microsoft Teams exibe o módulo de tarefa.

A próxima seção fornece detalhes sobre como enviar o resultado de um módulo de tarefa.

## <a name="submit-the-result-of-a-task-module"></a>Enviar o resultado de um módulo de tarefa

Quando o usuário termina o módulo de tarefa, enviar o resultado de volta para o bot é semelhante à maneira como ele funciona com guias. Para obter mais informações, [consulte o exemplo de envio do resultado de um módulo de tarefa](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-of-submitting-the-result-of-a-task-module). Há algumas diferenças da seguinte maneira:

* HTML ou JavaScript `TaskInfo.url`, ou seja: depois de validar o que o usuário inseriu, `microsoftTeams.tasks.submitTask()` chame a função do SDK `submitTask()` conhecida daqui em diante como para fins de legibilidade. Você pode chamar `submitTask()` sem parâmetros se quiser Teams o módulo de tarefa, mas deve passar um objeto ou uma cadeia de caracteres para seu `submitHandler`. Passe-o como o primeiro parâmetro, `result`. Teams invoca , `err` é e é `null`o `result` objeto ou cadeia de caracteres `submitHandler`para o qual você passou`submitTask()`. Se você chamar `submitTask()` com um parâmetro `result` , deverá passar uma `appId` ou uma matriz de cadeias de `appId` caracteres. Isso permite Teams validar se o aplicativo que envia o resultado é o mesmo que invocou o módulo de tarefa. Seu bot recebe uma mensagem `task/submit` incluindo `result`. Para obter mais informações, [consulte conteúdo e `task/fetch` `task/submit` mensagens](#payload-of-taskfetch-and-tasksubmit-messages).
* Cartão Adaptável: `TaskInfo.card`o corpo do Cartão Adaptável, conforme preenchido pelo usuário, é enviado ao bot `task/submit` por meio de uma mensagem quando o usuário seleciona qualquer `Action.Submit` botão.

A próxima seção fornece detalhes sobre a flexibilidade de `task/submit`.

## <a name="the-flexibility-of-tasksubmit"></a>A flexibilidade da tarefa/envio

Quando o usuário termina com um módulo de tarefa invocado de um bot, o bot sempre recebe uma `task/submit invoke` mensagem. Você tem várias opções ao responder à `task/submit` mensagem da seguinte maneira:

| Resposta do corpo HTTP                      | Cenário                                |
| --------------------------------------- | --------------------------------------- |
| Nenhum ignora a `task/submit` mensagem | A resposta mais simples não é nenhuma resposta. Seu bot não precisa responder quando o usuário terminar com o módulo de tarefa. |
| <pre>{<br/>  "task": {<br/>    "type": "message",<br/>    "value": "Message text"<br/>  }<br/>}</pre> | Teams exibe o valor de uma `value` caixa de mensagem pop-up. |
| <pre>{<br/>  "task": {<br/>    "type": "continue",<br/>    "value": &lt;TaskInfo object&gt;<br/>  }<br/>}</pre> | Permite encadear sequências de Cartões Adaptáveis em conjunto em um assistente ou experiência de várias etapas. |

> [!NOTE]
> O encadeamento de Cartões Adaptáveis em uma sequência é um cenário avançado. O Node.js aplicativo de exemplo é compatível com ele. Para obter mais informações, [consulte Microsoft Teams módulo de tarefa Node.js](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs#implementation-notes).

A próxima seção fornece detalhes sobre o conteúdo e `task/fetch` as `task/submit` mensagens.

## <a name="payload-of-taskfetch-and-tasksubmit-messages"></a>Carga das mensagens de tarefa/busca e tarefa/envio

Esta seção define o esquema do que seu bot recebe quando recebe um `task/fetch` objeto ou `task/submit` Bot Framework `Activity` . A tabela a seguir fornece as propriedades de conteúdo e `task/fetch` `task/submit` mensagens:

| Propriedade | Descrição                          |
| -------- | ------------------------------------ |
| `type`   | É sempre `invoke`.           |
| `name`   | É um ou `task/fetch` `task/submit`. |
| `value`  | É a carga definida pelo desenvolvedor. A estrutura do objeto `value` é a mesma que é enviada de Teams. Nesse caso, no entanto, é diferente. Ele requer suporte para busca dinâmica que é `task/fetch` do Bot Framework, `value` que é e ações de Cartão Adaptável `Action.Submit` , que é `data`. Uma maneira de Teams `context` com o bot é necessária, além do que está incluído em `value` ou `data`.<br/><br/>Combine 'value' e 'data' em um objeto pai:<br/><br/><pre>{<br/>  "context": {<br/>    "theme": "default" &vert; "dark" &vert; "contrast",<br/>  },<br/>  "data": [value field from Bot Framework card] &vert; [data field from Adaptive Card] <br/>}</pre>  |

A próxima seção fornece um exemplo de recebimento e resposta e `task/fetch` invocação `task/submit` de mensagens Node.js.

## <a name="example-of-taskfetch-and-tasksubmit-invoke-messages-in-nodejs-and-c"></a>Exemplo de tarefa/busca e tarefa/enviar mensagens de invocação em Node.js e C #

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

### <a name="bot-framework-card-actions-vs-adaptive-card-actionsubmit-actions"></a>Ações de cartão do Bot Framework versus Ação de Cartão Adaptável.Enviar ações

O esquema para ações de cartão do Bot Framework é diferente das ações de Cartão Adaptável `Action.Submit` e a maneira de invocar módulos de tarefa também é diferente. O `data` objeto em `Action.Submit` contém um `msteams` objeto para que ele não interfira com outras propriedades no cartão. A tabela a seguir mostra um exemplo de cada ação de cartão:

| Ação de cartão do Bot Framework                              | Ação Action.Submit do Cartão Adaptável                     |
| ------------------------------------------------------ | ------------------------------------------------------ |
| <pre>{<br/>  "type": "invoke",<br/>  "title": "Buy",<br/>  "value": {<br/>    "type": "task/fetch",<br/>    &lt;...&gt;<br/>  }<br/>}</pre> | <pre>{<br/>  "type": "Action.Submit",<br/>  "id": "btnBuy",<br/>  "title": "Buy",<br/>  "data": {<br/>    &lt;...&gt;,<br/>    "msteams": {<br/>      "type": "task/fetch"<br/>    }<br/>  }<br/>}</pre>  |

## <a name="code-sample"></a>Exemplo de código

|Nome do exemplo | Descrição | .NET | Node.js|
|----------------|-----------------|--------------|----------------|
|Bots de exemplo do módulo de tarefa -V4 | Exemplos para criar módulos de tarefa. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/54.teams-task-module)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/54.teams-task-module)|

## <a name="step-by-step-guide"></a>Guias passo a passo

Siga o [guia passo a passo para](../../sbs-botbuilder-taskmodule.yml) criar e buscar o bot do módulo de tarefa Teams.

## <a name="see-also"></a>Confira também

* [Microsoft Teams código de exemplo do módulo de tarefa no Node.js](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs/blob/master/src/TeamsBot.ts)
* [Exemplos do Bot Framework](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md)
