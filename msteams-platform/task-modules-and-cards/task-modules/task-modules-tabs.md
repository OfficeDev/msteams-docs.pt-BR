---
title: Usar módulos de tarefa Microsoft Teams guias
description: Explica como invocar módulos de tarefas Teams guias e enviar seu resultado usando o SDK do Microsoft Teams cliente. Ele inclui exemplos de código.
ms.localizationpriority: medium
ms.topic: how-to
keywords: SDK do cliente de guias de equipes de módulos de tarefas
ms.openlocfilehash: 63ac1df5b9cdbbba46ba204103a9a5c989b3a323
ms.sourcegitcommit: 3bfd0d2c4d83f306023adb45c8a3f829f7150b1d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65073751"
---
# <a name="use-task-modules-in-tabs"></a>Usar módulos de tarefas nas guias

Adicione um módulo de tarefa à guia para simplificar a experiência do usuário para todos os fluxos de trabalho que exigem entrada de dados. Os módulos de tarefa permitem coletar suas entradas em um pop-up Teams-Aware Microsoft. Um bom exemplo disso é editar cartões do Planner. Você pode usar módulos de tarefa para criar uma experiência semelhante.

Para dar suporte ao recurso de módulo de tarefa, duas novas funções são adicionadas [ao SDK do Teams cliente](/javascript/api/overview/msteams-client). O código a seguir mostra um exemplo dessas duas funções:

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

Para invocar um módulo de tarefa de uma guia, use `microsoftTeams.tasks.startTask()` passar um [objeto TaskInfo e](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object) uma função de `submitHandler` retorno de chamada opcional. Há dois casos a serem considerados:

* O valor de `TaskInfo.url` é definido como uma URL. A janela do módulo de tarefa é exibida `TaskModule.url` e carregada como uma `<iframe>` dentro dela. JavaScript nessa página chama `microsoftTeams.initialize()`. Se houver uma função `microsoftTeams.tasks.startTask()`na página e houver um erro ao invocar, `err` `submitHandler` ele será invocado com definido como a `submitHandler` cadeia de caracteres de erro indicando o mesmo. Para obter mais informações, consulte [erros de invocação de módulo de tarefa](#task-module-invocation-errors).
* O valor de `taskInfo.card` é o [JSON de um Cartão Adaptável](~/task-modules-and-cards/task-modules/invoking-task-modules.md#adaptive-card-or-adaptive-card-bot-card-attachment). Não há nenhuma função JavaScript `submitHandler` a ser chamada quando o usuário fecha ou pressiona um botão no Cartão Adaptável. A única maneira de receber o que o usuário inseriu é passando o resultado para um bot. Para usar um módulo de tarefa cartão adaptável de uma guia, seu aplicativo deve incluir um bot para obter qualquer resposta do usuário.

A próxima seção fornece um exemplo de como invocar um módulo de tarefa.

## <a name="example-of-invoking-a-task-module"></a>Exemplo de invocação de um módulo de tarefa

A imagem a seguir exibe o módulo de tarefa:

:::image type="content" source="../../assets/images/task-module/task-module-custom-form.png" alt-text="Formulário Personalizado do Módulo de Tarefa":::

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

O `submitHandler` é muito simples e ecoa o valor de `err` ou `result` para o console.

## <a name="submit-the-result-of-a-task-module"></a>Enviar o resultado de um módulo de tarefa

A `submitHandler` função reside na página da `TaskInfo.url` Web e é usada com `TaskInfo.url`. Se houver um erro ao invocar o módulo de tarefa, `submitHandler` `err` sua função será invocada imediatamente com uma cadeia de caracteres indicando qual [erro ocorreu](#task-module-invocation-errors). A `submitHandler` função também é chamada com uma cadeia `err` de caracteres quando o usuário seleciona X no canto superior direito do módulo de tarefa para fechar.

Se não houver nenhum erro de invocação e o usuário não selecionar X para ignorá-lo, o usuário escolherá um botão quando terminar. Dependendo se é uma URL ou um Cartão Adaptável no módulo de tarefa, as próximas seções fornecem detalhes sobre o que ocorre.

### <a name="html-or-javascript-taskinfourl"></a>HTML ou JavaScript `TaskInfo.url`

Depois de validar as entradas do usuário, chame a função `microsoftTeams.tasks.submitTask()` SDK conhecida como `submitTask()`. Chame `submitTask()` sem parâmetros se quiser apenas Teams fechar o módulo de tarefa. Você pode passar um objeto ou uma cadeia de caracteres para seu `submitHandler`.

Passe o resultado como o primeiro parâmetro. Teams invoca onde está e é o objeto ou cadeia de caracteres `submitHandler` para o qual você passou`submitTask()`.`result` `null` `err` Se você chamar `submitTask()` com um parâmetro `result` , deverá passar uma `appId` ou uma matriz de cadeias de `appId` caracteres. Isso permite Teams validar se o aplicativo que envia o resultado é o mesmo que o módulo de tarefa invocado.

### <a name="adaptive-card-taskinfocard"></a>Cartão Adaptável `TaskInfo.card`

Quando você invoca o módulo de tarefa com um `submitHandler` e o usuário seleciona um botão, os valores no cartão são retornados `Action.Submit` como o valor de `result`. Se o usuário selecionar a tecla Esc ou X no canto superior direito, `err` será retornado. Se seu aplicativo contiver um bot além de uma guia, `appId` você poderá simplesmente incluir o bot `completionBotId` como o valor do `TaskInfo` objeto. O corpo do Cartão Adaptável, conforme preenchido pelo usuário, é enviado ao bot `task/submit invoke` usando uma mensagem quando o usuário seleciona um `Action.Submit` botão. O esquema do objeto que você recebe é muito semelhante ao esquema que você recebe para mensagens [de tarefa/busca e tarefa/envio](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages). A única diferença é que o esquema do objeto JSON é um objeto cartão adaptável em vez de um objeto que contém um objeto Cartão Adaptável como quando cartões [adaptáveis](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages) são usados com bots.

A próxima seção fornece um exemplo de envio do resultado de um módulo de tarefa.

## <a name="example-of-submitting-the-result-of-a-task-module"></a>Exemplo de envio do resultado de um módulo de tarefa

Para obter mais informações, consulte o [formulário HTML no módulo de tarefa](#example-of-invoking-a-task-module). O código a seguir fornece um exemplo de onde o formulário é definido:

```html
<form method="POST" id="customerForm" action="/register" onSubmit="return validateForm()">
```

Há cinco campos neste formulário, mas, para este exemplo, apenas três valores são necessários, `name`e `email`.`favoriteBook`

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

A tabela a seguir fornece os valores possíveis `err` que podem ser recebidos pelo seu `submitHandler`:

| Problema | Mensagem de erro que é o valor de `err` |
| ------- | ------------------------------ |
| Valores para ambos `TaskInfo.url` e `TaskInfo.card` foram especificados. | Os valores para o cartão e a URL foram especificados. Um ou outro, mas não ambos, são permitidos. |
| Nem `TaskInfo.url` especificado `TaskInfo.card` . | Você deve especificar um valor para o cartão ou a URL. |
| Inválido `appId`. | ID do aplicativo inválida. |
| O usuário selecionou o botão X, fechando-o. | O usuário cancelou ou fechou o módulo de tarefa. |

## <a name="code-sample"></a>Exemplo de código

|Nome do exemplo | Descrição | .NET | Node.js|
|----------------|-----------------|--------------|----------------|
|Guias de exemplo do módulo de tarefa e bots-V3 | Exemplos para criar módulos de tarefa. |[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/nodejs)|

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Usando módulos de tarefa de bots](~/task-modules-and-cards/task-modules/task-modules-bots.md)

## <a name="see-also"></a>Confira também

[Invocar e ignorar módulos de tarefas](~/task-modules-and-cards/task-modules/invoking-task-modules.md)
