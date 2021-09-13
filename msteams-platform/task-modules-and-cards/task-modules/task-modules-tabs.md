---
title: Usar Módulos de Tarefa em Microsoft Teams guias
description: Explica como invocar módulos de tarefas Teams guias usando o SDK Microsoft Teams cliente.
ms.localizationpriority: medium
ms.topic: how-to
keywords: task modules teams tabs client sdk
ms.openlocfilehash: 0f6c1569a1aa18921df4635bdbaab505526c1e2e
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59155394"
---
# <a name="use-task-modules-in-tabs"></a>Usar módulos de tarefas nas guias

Adicione um módulo de tarefa à sua guia para simplificar a experiência do usuário para todos os fluxos de trabalho que exigem entrada de dados. Os módulos de tarefas permitem que você reúna suas entradas em um pop-up Teams-Aware Microsoft. Um bom exemplo disso é editar cartões do Planner. Você pode usar módulos de tarefa para criar uma experiência semelhante.

Para dar suporte ao recurso de módulo de tarefa, duas novas funções são adicionadas [ao SDK do](/javascript/api/overview/msteams-client)cliente Teams cliente . O código a seguir mostra um exemplo dessas duas funções:

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

* O valor de `TaskInfo.url` é definido como uma URL. A janela do módulo de tarefas é exibida `TaskModule.url` e carregada como uma dentro `<iframe>` dela. JavaScript nessa página chama `microsoftTeams.initialize()` . Se houver uma função na página e houver um erro ao invocar , será invocado com definido como a cadeia de caracteres de erro indicando `submitHandler` `microsoftTeams.tasks.startTask()` o `submitHandler` `err` mesmo. Para obter mais informações, consulte [erros de invocação do módulo de tarefas](#task-module-invocation-errors).
* O valor de `taskInfo.card` é [json para um Cartão Adaptável.](~/task-modules-and-cards/task-modules/invoking-task-modules.md#adaptive-card-or-adaptive-card-bot-card-attachment) Não há nenhuma função JavaScript a ser chamada quando o usuário fecha ou pressiona um `submitHandler` botão no Cartão Adaptável. A única maneira de receber o que o usuário entrou é passando o resultado para um bot. Para usar um módulo de tarefa cartão adaptável de uma guia, seu aplicativo deve incluir um bot para obter qualquer resposta do usuário.

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

O `submitHandler` é muito simples e ecoa o valor de ou para o `err` `result` console.

## <a name="submit-the-result-of-a-task-module"></a>Enviar o resultado de um módulo de tarefa

A `submitHandler` função reside na página da Web e é usada com `TaskInfo.url` `TaskInfo.url` . Se houver um erro ao invocar o módulo de tarefa, sua função será imediatamente invocada com uma cadeia de caracteres indicando `submitHandler` `err` que erro [ocorreu](#task-module-invocation-errors). A função também é chamada com uma cadeia de caracteres quando o usuário seleciona X no canto superior direito do módulo `submitHandler` de tarefa para o `err` fechar.

Se não houver nenhum erro de invocação e o usuário não selecionar X para descartá-lo, o usuário escolherá um botão quando terminar. Dependendo se é uma URL ou um Cartão Adaptável no módulo de tarefas, as próximas seções fornecem detalhes sobre o que ocorre.

### <a name="html-or-javascript-taskinfourl"></a>HTML ou JavaScript `TaskInfo.url`

Depois de validar as entradas do usuário, chame a `microsoftTeams.tasks.submitTask()` função SDK conhecida como `submitTask()` . Chame sem parâmetros se você quiser apenas `submitTask()` Teams fechar o módulo de tarefa. Você pode passar um objeto ou uma cadeia de caracteres para seu `submitHandler` .

Passe o resultado como o primeiro parâmetro. Teams invoca onde `submitHandler` `err` está `null` e é o objeto `result` ou cadeia de caracteres que você passou para `submitTask()` . Se você chamar `submitTask()` com um `result` parâmetro, deverá passar uma ou uma `appId` matriz de `appId` cadeias de caracteres. Isso permite Teams validar se o aplicativo que envia o resultado é igual ao módulo de tarefa invocado.

### <a name="adaptive-card-taskinfocard"></a>Cartão Adaptável `TaskInfo.card`

Quando você invoca o módulo de tarefa com um e o usuário seleciona um botão, os valores no cartão são retornados como `submitHandler` `Action.Submit` o valor de `result` . Se o usuário selecionar a tecla Esc ou X na parte superior direita, `err` será retornado em vez disso. Se seu aplicativo contiver um bot além de uma guia, você pode simplesmente incluir o bot como o `appId` `completionBotId` valor do `TaskInfo` objeto. O corpo do Cartão Adaptável conforme preenchido pelo usuário é enviado para o bot usando uma mensagem quando o usuário `task/submit invoke` seleciona um `Action.Submit` botão. O esquema do objeto que você recebe é muito semelhante ao esquema recebido para [tarefas/buscas e mensagens de tarefa/envio.](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages) A única diferença é que o esquema do objeto JSON é um objeto Cartão Adaptável em vez de um objeto que contém um objeto Card Adaptável como quando cartões adaptáveis são usados com [bots](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages).

A próxima seção fornece um exemplo de envio do resultado de um módulo de tarefa.

## <a name="example-of-submitting-the-result-of-a-task-module"></a>Exemplo de envio do resultado de um módulo de tarefa

Para obter mais informações, consulte o [formulário HTML no módulo de tarefa](#example-of-invoking-a-task-module). O código a seguir fornece um exemplo de onde o formulário é definido:

```html
<form method="POST" id="customerForm" action="/register" onSubmit="return validateForm()">
```

Há cinco campos neste formulário, mas, para este exemplo, apenas três valores são `name` necessários, `email` , e `favoriteBook` .

O código a seguir fornece um exemplo da `validateForm()` função que chama `submitTask()` :

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

A tabela a seguir fornece os valores possíveis `err` que podem ser recebidos por seu `submitHandler` :

| Problema | Mensagem de erro que é o valor de `err` |
| ------- | ------------------------------ |
| Valores para ambos `TaskInfo.url` `TaskInfo.card` e foram especificados. | Os valores para cartão e URL foram especificados. Um ou outro, mas não ambos, são permitidos. |
| Nem `TaskInfo.url` `TaskInfo.card` especificado. | Você deve especificar um valor para cartão ou URL. |
| Inválido `appId` . | ID de aplicativo inválida. |
| Botão X selecionado pelo usuário, fechando-o. | O usuário cancelou ou fechou o módulo de tarefa. |

## <a name="code-sample"></a>Exemplo de código

|Nome do exemplo | Descrição | .NET | Node.js|
|----------------|-----------------|--------------|----------------|
|Guias de exemplo de módulo de tarefa e bots-V3 | Exemplos para a criação de módulos de tarefa. |[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/csharp)|[Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/nodejs)| 

## <a name="see-also"></a>Confira também

[Invocar e ignorar módulos de tarefas](~/task-modules-and-cards/task-modules/invoking-task-modules.md)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Usando módulos de tarefas de bots](~/task-modules-and-cards/task-modules/task-modules-bots.md)
