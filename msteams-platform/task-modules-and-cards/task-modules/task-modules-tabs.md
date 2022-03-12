---
title: Usar Módulos de Tarefa em Microsoft Teams guias
description: Explica como invocar módulos de tarefas Teams guias e enviar seus resultados usando o SDK Microsoft Teams cliente. Inclui exemplos de código.
ms.localizationpriority: medium
ms.topic: how-to
keywords: task modules teams tabs client sdk
ms.openlocfilehash: 43b58a4f8ec1176c2d931f130a33c6610a078187
ms.sourcegitcommit: 8a0ffd21c800eecfcd6d1b5c4abd8c107fcf3d33
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2022
ms.locfileid: "63453639"
---
# <a name="use-task-modules-in-tabs"></a>Usar módulos de tarefas nas guias

Adicione um módulo de tarefa à sua guia para simplificar a experiência do usuário para todos os fluxos de trabalho que exigem entrada de dados. Os módulos de tarefas permitem que você reúna suas entradas em um pop-up Teams-Aware Microsoft. Um bom exemplo disso é editar cartões do Planner. Você pode usar módulos de tarefa para criar uma experiência semelhante.

Para dar suporte ao recurso de módulo de tarefa, duas novas funções são adicionadas [ao SDK Teams cliente](/javascript/api/overview/msteams-client). O código a seguir mostra um exemplo dessas duas funções:

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

Você pode ver como invocar um módulo de tarefa de uma guia e enviar o resultado de um módulo de tarefa funciona.

## <a name="invoke-a-task-module-from-a-tab"></a>Invocar um módulo de tarefa de uma guia

Para invocar um módulo de tarefa de uma guia, use `microsoftTeams.tasks.startTask()` passar um [objeto TaskInfo](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object) e uma função `submitHandler` de retorno de chamada opcional. Há dois casos a considerar:

* O valor de `TaskInfo.url` é definido como uma URL. A janela do módulo de tarefas é exibida `TaskModule.url` e carregada como `<iframe>` uma dentro dela. JavaScript nessa página chama `microsoftTeams.initialize()`. Se houver uma função `microsoftTeams.tasks.startTask()`na página e houver um erro ao invocar , `err` `submitHandler` será invocado com definido como a `submitHandler` cadeia de caracteres de erro indicando o mesmo. Para obter mais informações, consulte [erros de invocação do módulo de tarefas](#task-module-invocation-errors).
* O valor de `taskInfo.card` é [json para um Cartão Adaptável](~/task-modules-and-cards/task-modules/invoking-task-modules.md#adaptive-card-or-adaptive-card-bot-card-attachment). Não há nenhuma função JavaScript `submitHandler` a ser chamada quando o usuário fecha ou pressiona um botão no Cartão Adaptável. A única maneira de receber o que o usuário entrou é passando o resultado para um bot. Para usar um módulo de tarefa cartão adaptável de uma guia, seu aplicativo deve incluir um bot para obter qualquer resposta do usuário.

A próxima seção fornece um exemplo de invocação de um módulo de tarefa.

## <a name="example-of-invoking-a-task-module"></a>Exemplo de invocação de um módulo de tarefa

A imagem a seguir exibe o módulo de tarefa:

![Módulo de Tarefa - Formulário Personalizado](~/assets/images/task-module/task-module-custom-form.png)

O código a seguir é adaptado do [exemplo do módulo de tarefas](~/task-modules-and-cards/task-modules/invoking-task-modules.md#code-sample):

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

O `submitHandler` é muito simples e ecoa o valor de `err` ou `result` para o console.

## <a name="submit-the-result-of-a-task-module"></a>Enviar o resultado de um módulo de tarefa

A `submitHandler` função reside na página `TaskInfo.url` da Web e é usada com `TaskInfo.url`. Se houver um erro ao invocar o módulo de tarefa, `submitHandler` sua função será imediatamente invocada `err` com uma cadeia de caracteres indicando qual [erro ocorreu](#task-module-invocation-errors). A `submitHandler` função também é chamada com uma `err` cadeia de caracteres quando o usuário seleciona X no canto superior direito do módulo de tarefa para o fechar.

Se não houver nenhum erro de invocação e o usuário não selecionar X para descartá-lo, o usuário escolherá um botão quando terminar. Dependendo se é uma URL ou um Cartão Adaptável no módulo de tarefas, as próximas seções fornecem detalhes sobre o que ocorre.

### <a name="html-or-javascript-taskinfourl"></a>HTML ou JavaScript `TaskInfo.url`

Depois de validar as entradas do usuário, chame a função `microsoftTeams.tasks.submitTask()` SDK conhecida como `submitTask()`. Chame `submitTask()` sem parâmetros se você quiser apenas Teams fechar o módulo de tarefa. Você pode passar um objeto ou uma cadeia de caracteres para seu `submitHandler`.

Passe o resultado como o primeiro parâmetro. Teams invoca onde está e é o objeto ou cadeia de caracteres `submitHandler` que você passou para `submitTask()`.`result` `null` `err` Se você chamar `submitTask()` com um `result` parâmetro, deverá passar uma `appId` ou uma matriz de cadeias de `appId` caracteres. Isso permite Teams validar se o aplicativo que envia o resultado é igual ao módulo de tarefa invocado.

### <a name="adaptive-card-taskinfocard"></a>Cartão Adaptável `TaskInfo.card`

Quando você invoca o módulo de tarefa com um `submitHandler` e o usuário seleciona um botão, os valores no cartão são retornados `Action.Submit` como o valor de `result`. Se o usuário selecionar a tecla Esc ou X na parte superior direita, `err` será retornado em vez disso. Se seu aplicativo contiver um bot além de uma guia, `appId` você pode simplesmente incluir o bot como o valor `completionBotId` do objeto `TaskInfo` . O corpo do Cartão Adaptável conforme preenchido pelo usuário é enviado para o bot `task/submit invoke` usando uma mensagem quando o usuário seleciona um `Action.Submit` botão. O esquema do objeto recebido é muito semelhante ao esquema recebido para mensagens [de tarefa/busca e tarefa/envio](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages). A única diferença é que o esquema do objeto JSON é um objeto Cartão Adaptável em vez de um objeto que contém um objeto Cartão Adaptável como quando cartões [adaptáveis](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages) são usados com bots.

A próxima seção fornece um exemplo de envio do resultado de um módulo de tarefa.

## <a name="example-of-submitting-the-result-of-a-task-module"></a>Exemplo de envio do resultado de um módulo de tarefa

Para obter mais informações, consulte o [formulário HTML no módulo de tarefa](#example-of-invoking-a-task-module). O código a seguir fornece um exemplo de onde o formulário é definido:

```html
<form method="POST" id="customerForm" action="/register" onSubmit="return validateForm()">
```

Há cinco campos neste formulário, mas, para este exemplo, apenas três valores são necessários, `name`, `email`e `favoriteBook`.

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

A próxima seção fornece problemas de invocação do módulo de tarefas e suas mensagens de erro.

## <a name="task-module-invocation-errors"></a>Erros de invocação do módulo de tarefa

A tabela a seguir fornece os valores possíveis `err` que podem ser recebidos por seu `submitHandler`:

| Problema | Mensagem de erro que é o valor de `err` |
| ------- | ------------------------------ |
| Valores para ambos `TaskInfo.url` e `TaskInfo.card` foram especificados. | Os valores para cartão e URL foram especificados. Um ou outro, mas não ambos, são permitidos. |
| Nem `TaskInfo.url` especificado `TaskInfo.card` . | Você deve especificar um valor para cartão ou URL. |
| Inválido `appId`. | ID de aplicativo inválida. |
| Botão X selecionado pelo usuário, fechando-o. | O usuário cancelou ou fechou o módulo de tarefa. |

## <a name="code-sample"></a>Exemplo de código

|Nome do exemplo | Descrição | .NET | Node.js|
|----------------|-----------------|--------------|----------------|
|Guias de exemplo de módulo de tarefa e bots-V3 | Exemplos para a criação de módulos de tarefa. |[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/nodejs)|

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Usando módulos de tarefas de bots](~/task-modules-and-cards/task-modules/task-modules-bots.md)

## <a name="see-also"></a>Confira também

[Invocar e ignorar módulos de tarefas](~/task-modules-and-cards/task-modules/invoking-task-modules.md)
