---
title: Invocar e ignorar módulos de tarefas
description: Saiba mais sobre como invocar e ignorar módulos de tarefa, objeto de informações de tarefa, dimensionamento do módulo de tarefas, sintaxe de link profundo do módulo de tarefa usando exemplos de código
author: surbhigupta12
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: 04e27e780c1d2686be2ee73909c2d28bfc19fd23
ms.sourcegitcommit: b4986bf529c74444db67b7ce522b3b0d2c2a8e28
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/16/2022
ms.locfileid: "66130407"
---
# <a name="invoke-and-dismiss-task-modules"></a>Invocar e ignorar módulos de tarefas

Módulos de tarefa podem ser invocados de guias, bots ou links profundos. A resposta pode ser em HTML, JavaScript ou como um Cartão Adaptável. Há várias flexibilidades em termos de como os módulos de tarefa são invocados e como lidar com a resposta da interação do usuário. A tabela a seguir resume como isso funciona:

| Invocado usando | Módulo de tarefa com HTML ou JavaScript | Módulo de tarefa com Cartão Adaptável |
| --- | --- | --- |
| JavaScript em uma guia | 1. Use a função `tasks.startTask()` do SDK do cliente do Teams com uma função de retorno de chamada `submitHandler(err, result)` opcional. <br/><br/> 2. No código do módulo de tarefa, quando o usuário tiver executado as ações, chame a função do SDK do Teams `tasks.submitTask()` com um objeto `result` como parâmetro. Se um retorno de chamada `submitHandler` tiver sido especificado em `tasks.startTask()`, o Teams o chamará com `result` como um parâmetro. Se houver um erro ao invocar `tasks.startTask()`, a função `submitHandler` será chamada com uma cadeia de caracteres `err`. <br/><br/> 3. Você também pode especificar um `completionBotId` ao chamar `teams.startTask()`. Em seguida, `result` é enviado ao bot. | 1. Chame a função `tasks.startTask()` do SDK do cliente do Teams com um [objeto TaskInfo](#the-taskinfo-object) e `TaskInfo.card` contendo o JSON para o cartão adaptável para mostrar no pop-up do módulo de tarefa. <br/><br/> 2. Se um retorno de chamada `submitHandler` tiver sido especificado em `tasks.startTask()`, O Teams a chama com uma cadeia de caracteres `err` se houve um erro ao invocar `tasks.startTask()` ou se o usuário fechar o pop-up do módulo de tarefa usando o X no canto superior direito. <br/><br/> 3. Se o usuário pressionar um botão `Action.Submit` seu objeto `data` será retornado como o valor de `result`. |
| Botão de cartão de bot | 1. Botões de cartão de bot, dependendo do tipo de botão, podem invocar módulos de tarefa de duas maneiras, uma URL de link profundo ou enviando uma mensagem `task/fetch`. <br/><br/> 2. Se a ação do botão `type` for `task/fetch` que é um tipo de botão `Action.Submit` para Cartões Adaptáveis, um `task/fetch invoke` que é um HTTP POST é enviado ao bot. O bot responde ao POST com HTTP 200 e o corpo da resposta contendo um wrapper em torno do [objeto TaskInfo](#the-taskinfo-object). Para obter mais informações, consulte [invocando um módulo de tarefa usando `task/fetch`](~/task-modules-and-cards/task-modules/task-modules-bots.md#invoke-a-task-module-using-taskfetch). O Teams exibe o módulo de tarefa. <br/><br/> 3. Depois que o usuário executar as ações, chame a função do SDK do Teams `tasks.submitTask()` com um objeto `result` como parâmetro. O bot recebe uma mensagem `task/submit invoke` que contém o objeto `result`. <br/><br/> 4. Você tem três maneiras diferentes de responder à mensagem `task/submit`, não fazendo nada que seja a tarefa concluída com êxito, exibindo uma mensagem para o usuário em uma janela pop-up ou invocando outra janela do módulo de tarefa. Para obter mais informações, consulte [discussão detalhada sobre `task/submit`](~/task-modules-and-cards/task-modules/task-modules-bots.md#the-flexibility-of-tasksubmit). | <ul><li> Como botões em Bot Framework, os botões Cartões Adaptáveis dão suporte a duas maneiras de invocar módulos de tarefa, URLs de link profundo com botões `Action.openUrl` e `task/fetch` usando botões `Action.Submit`. </li></ul> <br/><br/> <ul><li> Os módulos de tarefa com Cartões Adaptáveis funcionam de forma semelhante ao caso HTML ou JavaScript. A principal diferença é que, como não há JavaScript quando você está usando Cartões Adaptáveis, não há como chamar `tasks.submitTask()`. Em vez disso, o Teams usa o objeto `data` de `Action.Submit` e o retorna como o conteúdo do evento `task/submit`. Para obter mais informações, consulte [flexibilidade de `task/submit`](~/task-modules-and-cards/task-modules/task-modules-bots.md#the-flexibility-of-tasksubmit). </li></ul> |
| URL de link profundo <br/>[sintaxe do URL](#task-module-deep-link-syntax) | 1. O Teams invoca o módulo de tarefa que é a URL que aparece dentro do parâmetro `<iframe>` especificado no parâmetro `url` do link profundo. Não há retorno `submitHandler` de chamada. <br/><br/> 2. No JavaScript da página no módulo de tarefa, chame `tasks.submitTask()` para fechar com um objeto `result` como um parâmetro, o mesmo que ao invocá-lo de uma guia ou um botão de cartão de bot. No entanto, a lógica de conclusão é ligeiramente diferente. Se a lógica de conclusão residir no cliente ou seja, se não houver nenhum bot, `submitHandler` não haverá retorno de chamada, portanto, qualquer lógica de conclusão deverá estar no código que precede a chamada para `tasks.submitTask()`. Erros de invocação são relatados apenas por meio do console. Se você tiver um bot, poderá especificar um parâmetro `completionBotId` no link profundo para enviar o objeto `result` por meio de um evento `task/submit`. | 1. O Teams invoca o módulo de tarefa que é o corpo do cartão JSON do Cartão Adaptável especificado como um valor codificado em URL do parâmetro `card` do link profundo. <br/><br/> 2. O usuário fecha o módulo de tarefa selecionando o X no canto superior direito do módulo de tarefa ou pressionando um botão `Action.Submit` no cartão. Como não há como chamar `submitHandler` , o usuário deve ter um bot para enviar o valor dos campos cartão adaptável. O usuário deve usar o parâmetro `completionBotId` no link profundo para especificar o bot para enviar os dados usando um evento `task/submit invoke`. |

A próxima seção especifica o objeto `TaskInfo` que define determinados atributos para um módulo de tarefa.

## <a name="the-taskinfo-object"></a>O objeto TaskInfo

O `TaskInfo` contém os metadados de um módulo de tarefa. Defina `url` para um iFrame inserido ou `card` para um Cartão Adaptável. A tabela a seguir fornece a definição de objeto:

| Atributo | Tipo | Descrição |
| --- | --- | --- |
| `title` | string | Esse atributo aparece abaixo do nome do aplicativo e à direita do ícone do aplicativo. |
| `height` | número ou cadeia de caracteres | Esse atributo pode ser um número que representa a altura do módulo de tarefa em pixels ou `small`, `medium` ou `large`. Para obter mais informações, consulte [dimensionamento do módulo de tarefas](#task-module-sizing). |
| `width` | número ou cadeia de caracteres | Esse atributo pode ser um número que representa a largura do módulo de tarefa em pixels ou `small`, `medium` ou `large`. Para obter mais informações, consulte [dimensionamento do módulo de tarefas](#task-module-sizing). |
| `url` | string | Esse atributo é a URL da página carregada como um `<iframe>` dentro do módulo de tarefa. O domínio da URL deve estar na [matriz validDomains](~/resources/schema/manifest-schema.md#validdomains) do aplicativo no manifesto do seu aplicativo. |
| `card` | Cartão Adaptável ou anexo de cartão de bot do Cartão Adaptável | Esse atributo é o JSON para o Cartão Adaptável aparecer no módulo de tarefa. Se o usuário estiver invocando de um bot, use o JSON do Cartão Adaptável em um objeto Bot Framework `attachment`. Em uma guia, o usuário deve usar um Cartão Adaptável. Para obter mais informações, consulte [Cartão Adaptável ou Anexo de cartão de bot de cartão adaptável](#adaptive-card-or-adaptive-card-bot-card-attachment) |
| `fallbackUrl` | string | Esse atributo abre a URL em uma guia do navegador, se um cliente não dá suporte ao recurso de módulo de tarefa. |
| `completionBotId` | string | Esse atributo especifica uma ID do aplicativo de bot para enviar o resultado da interação do usuário com o módulo de tarefa. Se especificado, o bot receberá um evento `task/submit invoke` com um objeto JSON na carga do evento. |

> [!NOTE]
> O recurso de módulo de tarefa requer que os domínios de quaisquer URLs que você deseja carregar sejam incluídos na matriz `validDomains` no manifesto do aplicativo.

A próxima seção especifica o dimensionamento do módulo de tarefa que permite que o usuário defina a altura e a largura do módulo de tarefa.

## <a name="task-module-sizing"></a>Dimensionamento do módulo de tarefas

O uso de inteiros para `TaskInfo.width` e `TaskInfo.height` define a altura e a largura do módulo de tarefa em pixels. No entanto, dependendo do tamanho da janela e da resolução da tela da Equipe, eles são reduzidos proporcionalmente, mantendo a taxa de proporção que é largura ou altura.

Se `TaskInfo.width` e `TaskInfo.height` forem `"small"`, `"medium"` ou `"large"`, o tamanho do retângulo vermelho na imagem a seguir é uma proporção do espaço disponível, 20%, 50% e 60% para `width` e 20%, 50% e 66% para `height`:

:::image type="content" source="../../assets/images/task-module/task-module-example.png" alt-text="exemplo de módulo de tarefa":::

Módulos de tarefa invocados de uma guia podem ser redimensionados dinamicamente. Depois de chamar `tasks.startTask()` você pode chamar `tasks.updateTask(newSize)` em que as propriedades de altura e largura no objeto newSize estão em conformidade com a especificação TaskInfo, por exemplo, `{ height: 'medium', width: 'medium' }`.

A próxima seção fornece exemplos de inserção de módulos de tarefa em um vídeo do YouTube e um PowerApp.

## <a name="task-module-css-for-html-or-javascript-task-modules"></a>Módulo de tarefa CSS para módulos de tarefa HTML ou JavaScript

Os módulos de tarefa baseados em HTML ou JavaScript têm acesso a toda a área do módulo de tarefa abaixo do cabeçalho. Embora isso ofereça uma grande flexibilidade, se você quiser que o preenchimento ao redor das bordas se alinhe com os elementos de cabeçalho e evite barras de rolagem desnecessárias, o usuário deve fornecer o CSS correto. As próximas seções fornecem alguns exemplos para alguns casos de uso.

### <a name="example-1-youtube-video"></a>Exemplo 1: vídeo do YouTube

O YouTube oferece a capacidade de inserir vídeos em páginas da Web. É fácil inserir vídeos em páginas da Web em um módulo de tarefa usando uma página da Web de stub simples.

:::image type="content" source="../../assets/images/task-module/youtube-example.png" alt-text="Exemplo de Youtube":::

O código a seguir fornece um exemplo do HTML para a página da Web sem o CSS:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  ⋮
</head>
<body>
  <div id="embed-container">
    <iframe width="1000" height="700" src="https://www.youtube.com/embed/rd0Rd8w3FZ0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen=""></iframe>
  </div>
</body>
</html>
```

O código a seguir fornece um exemplo do CSS:

```css
#embed-container iframe {
    position: absolute;
    top: 0;
    left: 0;
    width: 95%;
    height: 95%;
    padding-left: 20px;
    padding-right: 20px;
    padding-top: 10px;
    padding-bottom: 10px;
    border-style: none;
}
```

### <a name="example-2-powerapp"></a>Exemplo 2: PowerApp

O usuário também pode usar a mesma abordagem para inserir um PowerApp. Como a altura ou a largura de qualquer PowerApp individual é personalizável, o usuário pode ajustar a altura e a largura para obter a apresentação desejada.

:::image type="content" source="../../assets/images/task-module/powerapp-example.png" alt-text="powerapp":::

O código a seguir fornece um exemplo do HTML para PowerApp:

```html
<iframe width="720" height="520" src="https://web.powerapps.com/webplayer/iframeapp?source=iframe&screenColor=rgba(104,101,171,1)&appId=/providers/Microsoft.PowerApps/apps/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"></iframe>
```

O código a seguir fornece um exemplo do CSS:

```css
#embed-container iframe {
    position: absolute;
    top: 0;
    left: 0;
    width: 94%;
    height: 95%;
    padding-left: 20px;
    padding-right: 20px;
    padding-top: 10px;
    padding-bottom: 10px;
    border-style: none;
}
```

A próxima seção fornece detalhes sobre como invocar seu cartão usando o cartão adaptável ou anexo do cartão de bot do cartão adaptável.

## <a name="adaptive-card-or-adaptive-card-bot-card-attachment"></a>Cartão Adaptável ou anexo de cartão de bot do Cartão Adaptável

Dependendo `card`de como você está invocando seu, você deve usar um Cartão Adaptável ou um anexo de cartão de bot de Cartão Adaptável, que é um Cartão Adaptável encapsulado em um objeto de anexo.

Quando você está invocando de uma guia, o usuário deve usar um Cartão Adaptável.

O código a seguir fornece um exemplo de um Cartão Adaptável:

```json
{
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
}
```

O código a seguir fornece um exemplo de um anexo de cartão de bot de Cartão Adaptável quando você está invocando de um bot:

```json
{
    "contentType": "application/vnd.microsoft.card.adaptive",
    "content": {
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
    }
}
```

A próxima seção fornece detalhes sobre a sintaxe de link profundo do módulo de tarefa, incluindo o objeto `TaskInfo` e `APP_ID` e `BOT_APP_ID`.

## <a name="task-module-deep-link-syntax"></a>Sintaxe de link profundo do módulo de tarefa

Um link profundo do módulo de tarefa é uma serialização do objeto TaskInfo com os dois outros detalhes a seguir, `APP_ID` e, opcionalmente, o `BOT_APP_ID`:

`https://teams.microsoft.com/l/task/APP_ID?url=<TaskInfo.url>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID`

`https://teams.microsoft.com/l/task/APP_ID?card=<TaskInfo.card>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID`

Para os tipos de dados e valores permitidos para `<TaskInfo.url>`, `<TaskInfo.card>`, `<TaskInfo.height>`, `<TaskInfo.width>` e `<TaskInfo.title>`, consulte [objeto TaskInfo](#the-taskinfo-object).

> [!TIP]
> URL codificar o link direto ao usar o parâmetro `card`, por exemplo, a função [`encodeURI()` do JavaScript](https://www.w3schools.com/jsref/jsref_encodeURI.asp).

A tabela a seguir fornece informações sobre `APP_ID` e `BOT_APP_ID`:

| Valor | Tipo | Obrigatório | Descrição |
| --- | --- | --- | --- |
| `APP_ID` | string | Sim | O [ID](~/resources/schema/manifest-schema.md#id) do aplicativo que invoca o módulo de tarefa. A [validDomains](~/resources/schema/manifest-schema.md#validdomains) no manifesto para `APP_ID` deve conter o domínio para `url` se `url` estiver na URL. A ID do aplicativo já é conhecida quando um módulo de tarefa é invocado de uma guia ou um bot, por isso ele não está incluído em `TaskInfo`. |
| `BOT_APP_ID` | string | Não | Se um valor para `completionBotId` for especificado, o objeto `result` será enviado usando uma mensagem `task/submit invoke` para o bot especificado. `BOT_APP_ID` deve ser especificado como um bot no manifesto do aplicativo, ou seja, você não pode enviá-lo para nenhum bot. |

> [!NOTE]
> `APP_ID` e `BOT_APP_ID` pode ser o mesmo em muitos casos, se um aplicativo tiver um bot recomendado para usar como a ID de um aplicativo, se houver um.

A próxima seção fornece detalhes sobre como usar um teclado com o módulo de tarefa do aplicativo.

## <a name="keyboard-and-accessibility-guidelines"></a>Diretrizes de teclado e acessibilidade

Com módulos de tarefa baseados em HTML ou JavaScript, você deve garantir que o módulo de tarefa do aplicativo possa ser usado com um teclado. Os programas de leitor de tela também dependem da capacidade de navegar usando o teclado. Isso inclui as duas coisas a seguir:

* Usando o [atributo tabindex](https://developer.mozilla.org/docs/Web/HTML/Global_attributes/tabindex) em suas marcas HTML para controlar quais elementos podem ser focalizados. Além disso, use o atributo tabindex para identificar onde ele participa da navegação sequencial do teclado geralmente com as teclas <kbd>Tab</kbd> e <kbd>Shift-Tab</kbd>.
* Manipulando a tecla <kbd>Esc</kbd> no JavaScript para o módulo de tarefa. O código a seguir fornece um exemplo de como lidar com a tecla <kbd>Esc</kbd>:

    ```javascript
    // Handle the Esc key
    document.onkeyup = function(event) {
    if ((event.key === 27) || (event.key === "Escape")) {
      microsoftTeams.submitTask(null); // this will return an err object to the completionHandler()
      }
    }
    ```

O Microsoft Teams garante que a navegação por teclado funcione corretamente do cabeçalho do módulo de tarefa para o HTML e vice-versa.

## <a name="code-sample"></a>Exemplo de código

|Nome do exemplo | Descrição | .NET | Node.js|
|----------------|-----------------|--------------|----------------|
|Bots de exemplo do módulo de tarefa -V4 | Exemplos para criar módulos de tarefa. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/54.teams-task-module)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/54.teams-task-module)|
|Guias de exemplo do módulo de tarefa e bots-V3 | Exemplos para criar módulos de tarefa. |[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/nodejs)|

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Usar módulos de tarefas nas guias](~/task-modules-and-cards/task-modules/task-modules-tabs.md)

## <a name="see-also"></a>Confira também

* [Solicitar permissões do dispositivo](~/concepts/device-capabilities/native-device-permissions.md)
* [Integrar recursos de mídia](~/concepts/device-capabilities/media-capabilities.md)
* [Integre o recurso de scanner QR ou de código de barras no Teams](~/concepts/device-capabilities/qr-barcode-scanner-capability.md)
* [Integrar funcionalidades de localização no Teams](~/concepts/device-capabilities/location-capability.md)
