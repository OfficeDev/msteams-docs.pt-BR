---
title: Usando módulos de tarefas nas guias do Microsoft Teams
description: Explica como invocar módulos de tarefas das guias do Teams usando o SDK de cliente do Microsoft Teams.
keywords: task modules teams tabs client sdk
ms.openlocfilehash: 3f1da4d5eec31638d69adc01a45831534d015f41
ms.sourcegitcommit: 5cb3453e918bec1173899e7591b48a48113cf8f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2021
ms.locfileid: "50449553"
---
# <a name="using-task-modules-in-tabs"></a>Usando módulos de tarefas em guias

Adicionar um módulo de tarefa à sua guia pode simplificar muito a experiência do usuário para todos os fluxos de trabalho que exigem entrada de dados. Os módulos de tarefas permitem coletar suas entradas em um pop-up com conhecimento do Teams. Um bom exemplo disso é editar cartões do Planner; você pode usar módulos de tarefa para criar uma experiência semelhante.

Para dar suporte ao recurso de módulo de tarefa, duas novas funções foram adicionadas ao [SDK do cliente do Microsoft Teams:](/javascript/api/overview/msteams-client)

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

Vamos ver como cada um deles funciona.

## <a name="invoking-a-task-module-from-a-tab"></a>Invocando um módulo de tarefa de uma guia

Para invocar um módulo de tarefa de uma guia, use `microsoftTeams.tasks.startTask()` passar um [objeto TaskInfo](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) e uma função `submitHandler` de retorno de chamada opcional. Conforme descrito anteriormente, há dois casos a considerar:

1. O valor de `TaskInfo.url` é definido como uma URL. A janela do módulo de tarefas é exibida `TaskModule.url` e carregada como uma dentro `<iframe>` dela. JavaScript nessa página deve chamar `microsoftTeams.initialize()` . Se houver uma função na página e houver um erro ao invocar , será invocado com definido como a cadeia de caracteres de erro indicando o erro `submitHandler` `microsoftTeams.tasks.startTask()` conforme descrito `submitHandler` `err` [abaixo](#task-module-invocation-errors).
1. O valor de `taskInfo.card` é [o JSON para um cartão Adaptável.](~/task-modules-and-cards/what-are-task-modules.md#adaptive-card-or-adaptive-card-bot-card-attachment) Nesse caso, obviamente, não há nenhuma função JavaScript a ser chamada quando o usuário fecha ou pressiona um botão no cartão Adaptável; a única maneira de receber o que o usuário entrou é passando o resultado para um `submitHandler` bot. Para usar um módulo de tarefa de cartão adaptável de uma guia, seu aplicativo deve incluir um bot para obter informações de volta do usuário. Isso é explicado abaixo.

## <a name="example-invoking-a-task-module"></a>Exemplo: Invocando um módulo de tarefa

O código a seguir é adaptado do [exemplo do módulo de tarefas](~/task-modules-and-cards/what-are-task-modules.md#code-sample). Veja a aparência do módulo de tarefas:

![Módulo de Tarefa - Formulário Personalizado](~/assets/images/task-module/task-module-custom-form.png)

O `submitHandler` é muito simples; ele apenas ecoa o valor de `err` ou para o `result` console:

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

## <a name="submitting-the-result-of-a-task-module"></a>Enviando o resultado de um módulo de tarefa

A `submitHandler` função é usada com `TaskInfo.url` . A `submitHandler` função reside na página da `TaskInfo.url` Web. Se houver um erro ao invocar o módulo de tarefa, sua função será imediatamente invocada com uma cadeia de caracteres indicando `submitHandler` `err` qual erro [ocorreu](#task-module-invocation-errors). A função também é chamada com uma cadeia de caracteres quando o usuário `submitHandler` pressiona o X no canto superior direito do módulo de `err` tarefa.

Se não houver nenhum erro de invocação e o usuário não pressionar X para descartá-lo, o usuário pressionará um botão quando terminar. Dependendo se for uma URL ou um cartão adaptável no módulo de tarefas, veja o que acontece:

### <a name="htmljavascript-taskinfourl"></a>HTML/JavaScript ( `TaskInfo.url` )

Depois de validar o que o usuário instalou, você chama a função SDK (conhecida a seguir como para fins de capacidade `microsoftTeams.tasks.submitTask()` `submitTask()` de leitura). Você pode chamar sem qualquer parâmetro se quiser que o Teams feche o módulo de tarefa, mas na maioria das vezes você vai querer passar um objeto ou uma cadeia de caracteres para `submitTask()` seu `submitHandler` .

Passe o resultado como o primeiro parâmetro. O Teams `submitHandler` invocará onde `err` estará e será o `null` `result` objeto/cadeia de caracteres que você passou para `submitTask()` . Se você fizer uma chamada com um parâmetro, deverá passar uma ou uma matriz de cadeias de `submitTask()` `result`  `appId` caracteres: isso permite ao Teams validar que o aplicativo que está enviando o resultado é o mesmo que invocou o módulo `appId` de tarefa.

### <a name="adaptive-card-taskinfocard"></a>Cartão adaptável ( `TaskInfo.card` )

Se você invocar o módulo de tarefa com um , quando o usuário pressionar um botão, os valores no cartão serão retornados como `submitHandler` `Action.Submit` o valor de `result` . Se o usuário pressionar o botão Esc ou pressionar o X, `err` será retornado em vez disso. Como alternativa, se seu aplicativo contiver um bot além de uma guia, você pode simplesmente incluir o bot como o `appId` `completionBotId` valor do `TaskInfo` objeto. O corpo do cartão adaptável (conforme preenchido pelo usuário) será enviado para o bot por meio de uma mensagem quando o usuário `task/submit invoke` pressionar um `Action.Submit` botão. O esquema do objeto recebido é muito semelhante ao esquema recebido para mensagens [de tarefa/busca e tarefa/envio;](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages) a única diferença é que o esquema do objeto JSON é um  objeto de cartão Adaptável em vez de um objeto que contém um objeto de cartão adaptável como quando cartões adaptáveis são usados com [bots](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages).

## <a name="example-submitting-the-result-of-a-task-module"></a>Exemplo: enviar o resultado de um módulo de tarefa

[Lembre-se do formulário no módulo de tarefa acima](#example-invoking-a-task-module) com um formulário HTML. Aqui é onde o formulário é definido:

```html
<form method="POST" id="customerForm" action="/register" onSubmit="return validateForm()">
```

Há cinco campos neste formulário, mas estamos interessados apenas nos valores de três deles para este exemplo: `name` `email` , e `favoriteBook` .

Aqui está a `validateForm()` função que chama `submitTask()` :

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

## <a name="task-module-invocation-errors"></a>Erros de invocação de módulo de tarefa

Aqui estão os valores possíveis `err` dos que podem ser recebidos pelo seu `submitHandler` :

| Problema | Mensagem de erro (valor `err` de ) |
| ------- | ------------------------------ |
| Valores para ambos `TaskInfo.url` `TaskInfo.card` e foram especificados. | "Os valores para cartão e url foram especificados. Um ou outro, mas não ambos, são permitidos." |
| Nem `TaskInfo.url` `TaskInfo.card` especificado. | "Você deve especificar um valor para cartão ou url." |
| Inválido `appId` . | "AppId inválido". |
| O usuário pressionou o botão X, fechando-o. | "O usuário cancelou/fechou o módulo de tarefa." |
