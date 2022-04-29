---
title: Usar módulos de tarefa nas guias do Microsoft Teams
description: Explica como invocar módulos de tarefa das guias do Teams e enviar seu resultado usando o SDK do cliente do Microsoft Teams. Ele inclui exemplos de código.
ms.localizationpriority: high
ms.topic: how-to
keywords: módulos de tarefas guias teams cliente sdk
ms.openlocfilehash: eb199842a60832e6eb77575a7438cc9f52db6e09
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111224"
---
# <a name="use-task-modules-in-tabs"></a>Usar módulos de tarefas nas guias

Adicione um módulo de tarefa à guia para simplificar a experiência do usuário para todos os fluxos de trabalho que exigem entrada de dados. Os módulos de tarefa permitem coletar suas entradas em um pop-up com reconhecimento do Microsoft Teams. Um bom exemplo disso é editar cartões do Planner. Você pode usar módulos de tarefa para criar uma experiência semelhante.

Para dar suporte ao recurso de módulo de tarefa, duas novas funções são adicionadas ao [SDK do cliente Teams](/javascript/api/overview/msteams-client). O código a seguir mostra um exemplo dessas duas funções:

```typescript
microsoftTeams.tasks.startTask(
    taskInfo: TaskInfo,
    submitHandler?: (err: string, result: string | any) => void
): void;

microsoftTeams.tasks.submitTask(
    result?: string | any,
    appIds?: string | string[]
): void;
```

Você pode ver como a invocação de um módulo de tarefa de uma guia e o envio do resultado de um módulo de tarefa funciona.

## <a name="invoke-a-task-module-from-a-tab"></a>Invocar um módulo de tarefa de uma guia

Para invocar um módulo de tarefa de uma guia, use `microsoftTeams.tasks.startTask()`passando um [objeto TaskInfo](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object) e uma função de retorno de chamada `submitHandler` opcional. Existem dois casos a serem considerados:

* O valor de `TaskInfo.url` é definido como uma URL. A janela do módulo de tarefa é exibida e `TaskModule.url` é carregado como um `<iframe>` dentro dela. O JavaScript nessa página chama `microsoftTeams.initialize()`. Se houver uma função `submitHandler` na página e houver um erro ao invocar `microsoftTeams.tasks.startTask()`, em seguida, `submitHandler` é invocado com `err` definido como a cadeia de caracteres de erro que indica o mesmo. Para obter mais informações, consulte [erros de invocação do módulo de tarefas](#task-module-invocation-errors).
* O valor de `taskInfo.card` é o [JSON para um cartão adaptável](~/task-modules-and-cards/task-modules/invoking-task-modules.md#adaptive-card-or-adaptive-card-bot-card-attachment). Não há nenhuma função javaScript `submitHandler` para chamar quando o usuário fechar ou pressionar um botão no Cartão Adaptável. A única maneira de receber o que o usuário inseriu é passando o resultado para um bot. Para usar um módulo de tarefa cartão adaptável de uma guia, seu aplicativo deve incluir um bot para obter qualquer resposta do usuário.

A próxima seção fornece um exemplo de invocação de um módulo de tarefa.

## <a name="example-of-invoking-a-task-module"></a>Exemplo de invocação de um módulo de tarefa

A imagem a seguir exibe o módulo de tarefa:

:::image type="content" source="../../assets/images/task-module/task-module-custom-form.png" alt-text="Formulário personalizado do módulo de tarefa":::

O código a seguir é adaptado do [exemplo de módulo de tarefa](~/task-modules-and-cards/task-modules/invoking-task-modules.md#code-sample):

```javascript
let taskInfo = {
    title: null,
    height: null,
    width: null,
    url: null,
    card: null,
    fallbackUrl: null,
    completionBotId: null,
};

taskInfo.url = "https://contoso.com/teamsapp/customform";
taskInfo.title = "Custom Form";
taskInfo.height = 510;
taskInfo.width = 430;
submitHandler = (err, result) => {
    console.log(`Submit handler - err: ${err}`);
    console.log(`Submit handler - result\rName: ${result.name}\rEmail: ${result.email}\rFavorite book: ${result.favoriteBook}`);
};
microsoftTeams.tasks.startTask(taskInfo, submitHandler);
```

O `submitHandler` é muito simples e ecoa o valor de `err` ou `result` no console.

## <a name="submit-the-result-of-a-task-module"></a>Enviar o resultado de um módulo de tarefa

A função `submitHandler` reside na página da Web `TaskInfo.url` e é usada com `TaskInfo.url`. Se houver um erro ao invocar o módulo de tarefa, sua função `submitHandler` será invocada imediatamente com uma cadeia de caracteres `err` indicando qual [erro ocorreu](#task-module-invocation-errors). A função `submitHandler` também é chamada com uma cadeia de caracteres `err` quando o usuário seleciona X no canto superior direito do módulo de tarefa para fechar.

Se não houver nenhum erro de invocação e o usuário não selecionar X para ignorá-lo, o usuário escolherá um botão quando terminar. Dependendo se é uma URL ou um Cartão Adaptável no módulo de tarefa, as próximas seções fornecem detalhes sobre o que ocorre.

### <a name="html-or-javascript-taskinfourl"></a>HTML ou JavaScript `TaskInfo.url`

Depois de validar as entradas do usuário, chame a função do SDK `microsoftTeams.tasks.submitTask()` conhecida como `submitTask()`. Chame `submitTask()` sem parâmetros se quiser apenas que o Teams feche o módulo de tarefa. Você pode passar um objeto ou uma cadeia de caracteres para o `submitHandler`.

Passe o resultado como o primeiro parâmetro. O Teams invoca `submitHandler` em que `err` é `null` e `result` é o objeto ou cadeia de caracteres que você passou para `submitTask()`. Se você chamar `submitTask()` com um parâmetro `result`, você deve passar um `appId` ou uma matriz de cadeias de caracteres `appId`. Isso permite que o Teams valide se o aplicativo que envia o resultado é igual ao módulo de tarefa invocado.

### <a name="adaptive-card-taskinfocard"></a>Cartão adaptável `TaskInfo.card`

Quando você invoca o módulo de tarefa com um botão `submitHandler` e o usuário seleciona um botão `Action.Submit`, os valores no cartão são retornados como o valor de `result`. Se o usuário selecionar a tecla Esc ou X no canto superior direito, `err` será retornado. Se seu aplicativo contiver um bot além de uma guia, você poderá simplesmente incluir o `appId` do bot como o valor de `completionBotId` no objeto `TaskInfo`. O corpo do Cartão adaptável conforme preenchido pelo usuário é enviado ao bot usando uma mensagem `task/submit invoke` quando o usuário seleciona um botão `Action.Submit`. O esquema para o objeto que você recebe é muito semelhante ao [esquema recebido para tarefa/busca e tarefa/envio de mensagens](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages). A única diferença é que o esquema do objeto JSON é um objeto cartão adaptável em vez de um objeto que contém um objeto cartão adaptável como [quando Cartões adaptáveis são usados com bots](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages).

A próxima seção fornece um exemplo de envio do resultado de um módulo de tarefa.

## <a name="example-of-submitting-the-result-of-a-task-module"></a>Exemplo de envio do resultado de um módulo de tarefa

Para obter mais informações, consulte [formulário HTML no módulo de tarefa](#example-of-invoking-a-task-module). O código a seguir fornece um exemplo de onde o formulário é definido:

```html
<form method="POST" id="customerForm" action="/register" onSubmit="return validateForm()">
```

Há cinco campos neste formulário, mas, para este exemplo, apenas três valores são necessários, `name`, `email` e `favoriteBook`.

O código a seguir fornece um exemplo da função `validateForm()` que chama `submitTask()`:

```javascript
function validateForm() {
    var customerInfo = {
        name: document.forms["customerForm"]["name"].value,
        email: document.forms["customerForm"]["email"].value,
        favoriteBook: document.forms["customerForm"]["favoriteBook"].value
    }
    microsoftTeams.tasks.submitTask(customerInfo, "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx");
    return true;
}
```

A próxima seção fornece problemas de invocação de módulo de tarefa e suas mensagens de erro.

## <a name="task-module-invocation-errors"></a>Erros de invocação do módulo de tarefa

A tabela a seguir fornece os valores possíveis de `err` que podem ser recebidos pelo `submitHandler`:

| Problema | Mensagem de erro que é o valor de `err` |
| ------- | ------------------------------ |
| Valores para `TaskInfo.url` e `TaskInfo.card` foram especificados. | Valores para o cartão e a URL foram especificados. Um ou outro, mas não ambos, são permitidos. |
| Nem `TaskInfo.url` nem `TaskInfo.card` especificados. | Você deve especificar um valor para o cartão ou a URL. |
| `appId` inválido | ID do aplicativo inválida. |
| O usuário selecionou o botão X, fechando-o. | O usuário cancelou ou fechou o módulo de tarefa. |

## <a name="code-sample"></a>Exemplo de código

|Nome do exemplo | Descrição | .NET | Node.js|
|----------------|-----------------|--------------|----------------|
|Guias de exemplo do módulo de tarefa e bots-V3 | Exemplos para criar módulos de tarefa. |[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/nodejs)|

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Usanso módulos de tarefas de bots](~/task-modules-and-cards/task-modules/task-modules-bots.md)

## <a name="see-also"></a>Confira também

[Invocar e ignorar módulos de tarefas](~/task-modules-and-cards/task-modules/invoking-task-modules.md)
