---
title: Usando módulos de tarefas nas guias do Microsoft Teams
description: Explica como invocar módulos de tarefas de guias do Microsoft Teams usando o SDK do cliente do Microsoft Teams.
keywords: guias da equipe de módulos de tarefas SDK do cliente
ms.openlocfilehash: e10958195713f338a9b5e0a0672d8b6a29da9264
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672887"
---
# <a name="using-task-modules-in-tabs"></a>Usando módulos de tarefas em guias

Adicionar um módulo de tarefa à sua guia pode simplificar bastante a experiência do usuário para qualquer fluxo de trabalho que exija a entrada de dados. Os módulos de tarefas permitem coletar a entrada em um pop-up que reconhece equipes. Um bom exemplo disso é a edição de cartões do Planner; Você pode usar módulos de tarefa para criar uma experiência semelhante.

Para dar suporte ao recurso de módulo de tarefa, duas novas funções foram adicionadas ao [SDK do cliente do Microsoft Teams](/javascript/api/overview/msteams-client):

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

## <a name="invoking-a-task-module-from-a-tab"></a>Invocar um módulo de tarefa a partir de uma guia

Para invocar um módulo de tarefa a partir `microsoftTeams.tasks.startTask()` de uma guia, use a passagem `submitHandler` de um [objeto TaskInfo](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) e uma função de retorno de chamada opcional. Conforme descrito anteriormente, há dois casos que devem ser considerados:

1. O valor de `TaskInfo.url` é definido como uma URL. A janela módulo de tarefas aparece `TaskModule.url` e é carregada como `<iframe>` dentro dela. O JavaScript nessa página deve chamar `microsoftTeams.initialize()`. Se houver `submitHandler` uma função na página e houver um erro ao invocar `microsoftTeams.tasks.startTask()`, a chamada `submitHandler` será `err` definida como a cadeia de caracteres de erro indicando o erro, conforme descrito [abaixo](#task-module-invocation-errors).
1. O valor de `taskInfo.card` é o [JSON para um cartão adaptável](~/task-modules-and-cards/what-are-task-modules.md#adaptive-card-or-adaptive-card-bot-card-attachment). Nesse caso, obviamente, não há nenhuma função `submitHandler` JavaScript a ser chamada quando o usuário fecha ou pressiona um botão no cartão adaptável; a única maneira de receber o que o usuário inseriu é passando o resultado para um bot. Para usar um módulo de tarefa de cartão adaptável de uma guia, seu aplicativo deve incluir um bot para obter qualquer informação do usuário. Isso é explicado abaixo.

## <a name="example-invoking-a-task-module"></a>Exemplo: invocação de um módulo de tarefa

O código a seguir é adaptado da [amostra do módulo de tarefa](~/task-modules-and-cards/what-are-task-modules.md#task-module-samples). Veja a seguir como é o módulo de tarefas:

![Módulo de tarefa-formulário personalizado](~/assets/images/task-module/task-module-custom-form.png)

O `submitHandler` é muito simples; Ele apenas ecoa o valor de `err` ou `result` para o console:

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

A `submitHandler` função é usada com `TaskInfo.url`o. A `submitHandler` função reside na página `TaskInfo.url` da Web. Se houver um erro ao invocar o módulo de tarefa, `submitHandler` sua função será invocada imediatamente com `err` uma cadeia de caracteres indicando qual [erro ocorreu](#task-module-invocation-errors). A `submitHandler` função também é chamada com uma `err` cadeia de caracteres quando o usuário pressiona o X no canto superior direito do módulo de tarefa.

Se não houver um erro de invocação e o usuário não pressionar X para descartar, o usuário pressionará um botão quando terminar. Dependendo se é uma URL ou um cartão adaptável no módulo de tarefa, veja o que acontece:

### <a name="htmljavascript-taskinfourl"></a>HTML/JavaScript (`TaskInfo.url`)

Depois de validar o que o usuário inseriu, você chama `microsoftTeams.tasks.submitTask()` a função do SDK (mencionada `submitTask()` em diante para fins de legibilidade). Você pode chamar `submitTask()` sem qualquer parâmetro se quiser que o Microsoft Teams feche o módulo de tarefa, mas a maior parte do tempo desejará passar um objeto ou uma cadeia `submitHandler`de caracteres para o seu.

Passe seu resultado como o primeiro parâmetro. O `submitHandler` Microsoft Teams `err` invocará `null` onde `result` será e será o objeto/cadeia de caracteres `submitTask()`que você passa para. Se você chamar `submitTask()` `result` com um parâmetro, você **deve** passar um `appId` ou uma matriz de cadeias de `appId` caracteres: isso permite que as equipes validem que o aplicativo enviando o resultado é o mesmo que invocar o módulo de tarefa.

### <a name="adaptive-card-taskinfocard"></a>Cartão adaptável (`TaskInfo.card`)

Se você chamou o módulo de tarefa com `submitHandler`um, quando o usuário pressiona um `Action.Submit` botão, os valores no cartão serão retornados como o valor de `result`. Se o usuário pressionar o botão ESC ou pressionar o X, `err` será retornado. Como alternativa, se seu aplicativo contiver um bot além de uma guia, você pode simplesmente incluir `appId` o bot como o valor de `completionBotId` no `TaskInfo` objeto. O corpo do cartão adaptável (conforme preenchido pelo usuário) será enviado ao bot através de uma `task/submit invoke` mensagem quando o usuário pressiona um `Action.Submit` botão. O esquema para o objeto que você recebe é muito semelhante ao [esquema que você recebe para tarefas/busca e mensagens/envio](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages); a única diferença é que o esquema do objeto JSON é um objeto Card adaptável, em vez de um objeto *que contém* um objeto Card adaptável como [quando os cartões adaptáveis são usados com bots](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages).

## <a name="example-submitting-the-result-of-a-task-module"></a>Exemplo: enviando o resultado de um módulo de tarefa

Relembre o [formulário no módulo de tarefa acima](#example-invoking-a-task-module) com um formulário HTML. Veja onde o formulário está definido:

```html
<form method="POST" id="customerForm" action="/register" onSubmit="return validateForm()">
```

Há cinco campos neste formulário, mas estamos interessados apenas nos valores de três deles para este exemplo: `name`, `email`e. `favoriteBook`

Aqui está a `validateForm()` função que chama `submitTask()`:

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

Estes são os possíveis valores `err` que podem ser recebidos pelo: `submitHandler`

| Problema | Mensagem de erro (valor `err`de) |
| ------- | ------------------------------ |
| Valores para ambos `TaskInfo.url` e `TaskInfo.card` foram especificados. | "Os valores para o cartão e a URL foram especificados. Uma ou outra, mas não ambas, são permitidas. " |
| `TaskInfo.url` Nem `TaskInfo.card` especificado. | "Você deve especificar um valor para o cartão ou a URL". |
| Inválido `appId`. | "AppId inválido". |
| Botão X pressionando o usuário, fechando-o. | "O usuário cancelou/fechou o módulo de tarefas". |
