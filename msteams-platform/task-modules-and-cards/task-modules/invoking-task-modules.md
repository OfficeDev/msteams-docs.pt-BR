---
title: Invocar e ignorar módulos de tarefas
description: Saiba mais sobre como invocar e ignorar módulos de tarefa, objeto de informações de tarefa, dimensionamento do módulo de tarefas, sintaxe de link profundo do módulo de tarefa usando exemplos de código
author: surbhigupta12
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: 5685e789dd6f4ad7cc39173e11af15dd9f7360fe
ms.sourcegitcommit: 3bfd0d2c4d83f306023adb45c8a3f829f7150b1d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65073684"
---
# <a name="invoke-and-dismiss-task-modules"></a>Invocar e ignorar módulos de tarefas

Os módulos de tarefa podem ser invocados de guias, bots ou links profundos. A resposta pode ser em HTML, JavaScript ou como um Cartão Adaptável. Há muita flexibilidade em termos de como os módulos de tarefa são invocados e como lidar com a resposta da interação do usuário. A tabela a seguir resume como isso funciona:

| Invocado usando | Módulo de tarefa com HTML ou JavaScript | Módulo de tarefa com Cartão Adaptável |
| --- | --- | --- |
| JavaScript em uma guia | 1. Use a função Teams SDK do cliente com `tasks.startTask()` uma função de retorno de `submitHandler(err, result)` chamada opcional. <br/><br/> 2. No código do módulo de tarefa, quando o usuário tiver executado as ações, chame a função Teams SDK `tasks.submitTask()` `result` com um objeto como parâmetro. Se um `submitHandler` retorno de chamada tiver sido especificado `tasks.startTask()`em , Teams o chamará como `result` um parâmetro. Se houve um erro ao invocar, `submitHandler` a `tasks.startTask()`função será chamada com uma cadeia de `err` caracteres. <br/><br/> 3. Você também pode especificar um ao `completionBotId` chamar `teams.startTask()`. Em seguida, `result` o é enviado para o bot. | 1. Chame a função SDK `tasks.startTask()` do cliente Teams com um objeto [TaskInfo](#the-taskinfo-object) `TaskInfo.card` e contendo o JSON para o Cartão Adaptável a ser exibido no pop-up do módulo de tarefa. <br/><br/> 2. `submitHandler` `tasks.startTask()`Se um retorno de chamada tiver sido especificado em , `err` Teams o chamará com uma cadeia de caracteres, `tasks.startTask()` se houver um erro ao invocar ou se o usuário fechar o pop-up do módulo de tarefa usando o X no canto superior direito. <br/><br/> 3. Se o usuário pressionar um `Action.Submit` botão, seu `data` objeto será retornado como o valor de `result`. |
| Botão cartão de bot | 1. Botões de cartão de bot, dependendo do tipo de botão, podem invocar módulos de tarefa de duas maneiras, uma URL de link profundo ou enviando uma `task/fetch` mensagem. <br/><br/> 2. Se `type` `task/fetch` `Action.Submit` a `task/fetch invoke` ação do botão for o tipo de botão para Cartões Adaptáveis, um evento que é um HTTP POST será enviado para o bot. O bot responde ao POST com HTTP 200 e ao corpo da resposta que contém um wrapper em torno do [objeto TaskInfo](#the-taskinfo-object). Para obter mais informações, [consulte invocar um módulo de tarefa usando `task/fetch`](~/task-modules-and-cards/task-modules/task-modules-bots.md#invoke-a-task-module-using-taskfetch). Teams exibe o módulo de tarefa. <br/><br/> 3. Depois que o usuário executar as ações, chame a função Teams SDK `tasks.submitTask()` `result` com um objeto como um parâmetro. O bot recebe uma mensagem `task/submit invoke` que contém o `result` objeto. <br/><br/> 4. `task/submit` Você tem três maneiras diferentes de responder à mensagem, não fazendo nada que seja a tarefa concluída com êxito, exibindo uma mensagem para o usuário em uma janela pop-up ou invocando outra janela do módulo de tarefa. Para obter mais informações, [consulte a discussão detalhada sobre `task/submit`](~/task-modules-and-cards/task-modules/task-modules-bots.md#the-flexibility-of-tasksubmit). | <ul><li> Assim como os botões em cartões do Bot Framework, os botões nos Cartões Adaptáveis dão suporte a duas maneiras de invocar módulos de tarefa, vincular urLs `Action.openUrl` `task/fetch` `Action.Submit` com botões e usar botões. </li></ul> <br/><br/> <ul><li> Os módulos de tarefa com Cartões Adaptáveis funcionam de maneira muito semelhante ao caso HTML ou JavaScript. A principal diferença é que, como não há Nenhum JavaScript quando você está usando Cartões Adaptáveis, não há como chamar `tasks.submitTask()`. Em vez disso, Teams obtém o `data` objeto `Action.Submit` e o retorna como o conteúdo do `task/submit` evento. Para obter mais informações, consulte [a flexibilidade de `task/submit`](~/task-modules-and-cards/task-modules/task-modules-bots.md#the-flexibility-of-tasksubmit). </li></ul> |
| URL de link profundo <br/>[Sintaxe de URL](#task-module-deep-link-syntax) | 1. Teams invoca o módulo de tarefa que é a URL `<iframe>` `url` que aparece dentro do especificado no parâmetro do link profundo. Não há retorno `submitHandler` de chamada. <br/><br/> 2. Dentro do JavaScript da página no módulo de tarefa, `tasks.submitTask()` `result` chame para fechar com um objeto como um parâmetro, o mesmo que ao chamá-lo de uma guia ou um botão de cartão de bot. No entanto, a lógica de conclusão é ligeiramente diferente. Se a lógica de conclusão residir no cliente ou seja, se não houver nenhum bot, `submitHandler` não haverá retorno de chamada, portanto, qualquer lógica de conclusão deverá estar no código que precede a chamada para `tasks.submitTask()`. Os erros de invocação são relatados apenas por meio do console. Se você tiver um bot, poderá especificar um `completionBotId` parâmetro no link profundo para enviar o `result` objeto por meio de um `task/submit` evento. | 1. Teams invoca o módulo de tarefa que é o corpo do cartão JSON do Cartão Adaptável especificado como um valor codificado em URL `card` do parâmetro do link profundo. <br/><br/> 2. O usuário fecha o módulo de tarefa selecionando o X `Action.Submit` no canto superior direito do módulo de tarefa ou pressionando um botão no cartão. Como não há como `submitHandler` chamar, o usuário deve ter um bot para enviar o valor dos campos cartão adaptável. O usuário deve usar o `completionBotId` parâmetro no link profundo para especificar o bot para enviar os dados usando um `task/submit invoke` evento. |

A próxima seção especifica o objeto `TaskInfo` que define determinados atributos para um módulo de tarefa.

## <a name="the-taskinfo-object"></a>O objeto TaskInfo

O `TaskInfo` objeto contém os metadados de um módulo de tarefa. Defina o `url` para um iFrame inserido ou `card` para um Cartão Adaptável. A tabela a seguir fornece a definição de objeto:

| Atributo | Tipo | Descrição |
| --- | --- | --- |
| `title` | string | Esse atributo aparece abaixo do nome do aplicativo e à direita do ícone do aplicativo. |
| `height` | número ou cadeia de caracteres | Esse atributo pode ser um número que representa a altura do módulo de tarefa `small`em pixels ou , `medium`ou `large`. Para obter mais informações, consulte [o dimensionamento do módulo de tarefas](#task-module-sizing). |
| `width` | número ou cadeia de caracteres | Esse atributo pode ser um número que representa a largura do módulo de tarefa `small`em pixels ou , `medium`ou `large`. Para obter mais informações, consulte [o dimensionamento do módulo de tarefas](#task-module-sizing). |
| `url` | cadeia de caracteres | Esse atributo é a URL da página carregada como um `<iframe>` dentro do módulo de tarefa. O domínio da URL deve estar na matriz [validDomains](~/resources/schema/manifest-schema.md#validdomains) do aplicativo no manifesto do aplicativo. |
| `card` | Anexo de cartão de bot de Cartão Adaptável ou Cartão Adaptável | Esse atributo é o JSON para o Cartão Adaptável aparecer no módulo de tarefa. Se o usuário estiver invocando de um bot, use o JSON do Cartão Adaptável em um objeto do Bot Framework `attachment` . Em uma guia, o usuário deve usar um Cartão Adaptável. Para obter mais informações, [consulte o anexo de cartão de bot cartão adaptável ou cartão adaptável](#adaptive-card-or-adaptive-card-bot-card-attachment) |
| `fallbackUrl` | cadeia de caracteres | Esse atributo abre a URL em uma guia do navegador, se um cliente não dá suporte ao recurso de módulo de tarefa. |
| `completionBotId` | cadeia de caracteres | Esse atributo especifica uma ID do aplicativo de bot para enviar o resultado da interação do usuário com o módulo de tarefa. Se especificado, o bot receberá um `task/submit invoke` evento com um objeto JSON no conteúdo do evento. |

> [!NOTE]
> O recurso de módulo de tarefa requer que os domínios de quaisquer URLs que você deseja carregar sejam incluídos `validDomains` na matriz no manifesto do aplicativo.

A próxima seção especifica o dimensionamento do módulo de tarefa que permite que o usuário defina a altura e a largura do módulo de tarefa.

## <a name="task-module-sizing"></a>Dimensionamento do módulo de tarefas

Usando inteiros para `TaskInfo.width` e `TaskInfo.height`, define a altura e a largura do módulo de tarefa em pixels. No entanto, dependendo do tamanho da janela e da resolução da tela da Equipe, eles são reduzidos proporcionalmente, mantendo a taxa de proporção que é largura ou altura.

Se e são , `"medium"`ou `"large"`, o tamanho do retângulo vermelho na imagem a seguir é uma proporção do espaço disponível, 20%, 50% e 60% `width` para e 20%, 50% e 66% para`height`:`TaskInfo.width` `TaskInfo.height` `"small"`

:::image type="content" source="../../assets/images/task-module/task-module-example.png" alt-text="exemplo de módulo de tarefa":::

Os módulos de tarefa invocados de uma guia podem ser redimensionados dinamicamente. Depois de chamar `tasks.startTask()` , você pode chamar `tasks.updateTask(newSize)` onde as propriedades de altura e largura no objeto newSize estão em conformidade com a especificação TaskInfo, por exemplo `{ height: 'medium', width: 'medium' }`.

A próxima seção fornece exemplos de inserção de módulos de tarefa em um vídeo do YouTube e um PowerApp.

## <a name="task-module-css-for-html-or-javascript-task-modules"></a>Módulo de tarefa CSS para módulos de tarefa HTML ou JavaScript

Os módulos de tarefa baseados em HTML ou JavaScript têm acesso a toda a área do módulo de tarefa abaixo do cabeçalho. Embora isso ofereça muita flexibilidade, se você quiser que o preenchimento ao redor das bordas se alinhe com os elementos de cabeçalho e evite barras de rolagem desnecessárias, o usuário deve fornecer o CSS correto. As próximas seções fornecem alguns exemplos para alguns casos de uso.

### <a name="example-1-youtube-video"></a>Exemplo 1: vídeo do YouTube

O YouTube oferece a capacidade de inserir vídeos em páginas da Web. É fácil inserir vídeos em páginas da Web em um módulo de tarefa usando uma página da Web de stub simples.

:::image type="content" source="../../assets/images/task-module/youtube-example.png" alt-text="Exemplo do Youtube":::

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

A próxima seção fornece detalhes sobre como invocar seu cartão usando o cartão adaptável ou o anexo do cartão de bot do Cartão Adaptável.

## <a name="adaptive-card-or-adaptive-card-bot-card-attachment"></a>Anexo de cartão de bot de Cartão Adaptável ou Cartão Adaptável

Dependendo de como você está invocando `card`seu, você deve usar um Cartão Adaptável ou um anexo de cartão de bot de Cartão Adaptável, que é um Cartão Adaptável encapsulado em um objeto de anexo.

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

A próxima seção fornece detalhes sobre a sintaxe de vínculo profundo do módulo de tarefas, incluindo o `TaskInfo` objeto e `APP_ID` .`BOT_APP_ID`

## <a name="task-module-deep-link-syntax"></a>Sintaxe de link profundo do módulo de tarefas

Um link profundo do módulo de tarefa é uma serialização do objeto TaskInfo com os dois outros detalhes a seguir e, `APP_ID` opcionalmente, o `BOT_APP_ID`seguinte:

`https://teams.microsoft.com/l/task/APP_ID?url=<TaskInfo.url>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID`

`https://teams.microsoft.com/l/task/APP_ID?card=<TaskInfo.card>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID`

Para os tipos de dados e os valores permitidos para `<TaskInfo.url>`, `<TaskInfo.card>`, `<TaskInfo.height>`e `<TaskInfo.width>`, `<TaskInfo.title>`consulte [o objeto TaskInfo](#the-taskinfo-object).

> [!TIP]
> A URL codifica o link profundo ao usar o `card` parâmetro, por exemplo, a função do [`encodeURI()` JavaScript](https://www.w3schools.com/jsref/jsref_encodeURI.asp).

A tabela a seguir fornece informações sobre `APP_ID` e `BOT_APP_ID`:

| Valor | Tipo | Obrigatório | Descrição |
| --- | --- | --- | --- |
| `APP_ID` | string | Sim | A [ID](~/resources/schema/manifest-schema.md#id) do aplicativo que invoca o módulo de tarefa. A [matriz validDomains](~/resources/schema/manifest-schema.md#validdomains) no manifesto deve `APP_ID` conter o domínio para `url` se `url` estiver na URL. A ID do aplicativo já é conhecida quando um módulo de tarefa é invocado de uma guia ou um bot, por isso ele não está incluído em `TaskInfo`. |
| `BOT_APP_ID` | string | Não | Se um valor for `completionBotId` especificado, o `result` objeto será enviado usando uma `task/submit invoke` mensagem para o bot especificado. `BOT_APP_ID` deve ser especificado como um bot no manifesto do aplicativo, ou seja, você não pode enviá-lo para nenhum bot. |

> [!NOTE]
> `APP_ID` e `BOT_APP_ID` pode ser o mesmo em muitos casos, se um aplicativo tiver um bot recomendado para usar como a ID de um aplicativo, se houver um.

A próxima seção fornece detalhes sobre como usar um teclado com o módulo de tarefa do aplicativo.

## <a name="keyboard-and-accessibility-guidelines"></a>Diretrizes de teclado e acessibilidade

Com módulos de tarefas baseados em HTML ou JavaScript, você deve garantir que o módulo de tarefa do aplicativo possa ser usado com um teclado. Os programas de leitor de tela também dependem da capacidade de navegar usando o teclado. Isso inclui as duas coisas a seguir:

* Usar o [atributo tabindex](https://developer.mozilla.org/docs/Web/HTML/Global_attributes/tabindex) em suas marcas HTML para controlar quais elementos podem ser focalizados. Além disso, use o atributo tabindex para identificar onde ele participa da navegação sequencial do teclado geralmente com as teclas <kbd>Tab</kbd> e <kbd>Shift-Tab</kbd> .
* Manipulando <kbd>a chave Esc</kbd> no JavaScript para o módulo de tarefa. O código a seguir fornece um exemplo de como lidar com a <kbd>chave Esc</kbd> :

    ```javascript
    // Handle the Esc key
    document.onkeyup = function(event) {
    if ((event.key === 27) || (event.key === "Escape")) {
      microsoftTeams.submitTask(null); // this will return an err object to the completionHandler()
      }
    }
    ```

Microsoft Teams garante que a navegação por teclado funcione corretamente do cabeçalho do módulo de tarefa para o HTML e vice-versa.

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
* [Integrar recursos de mídia](~/concepts/device-capabilities/mobile-camera-image-permissions.md)
* [Integrar a funcionalidade de scanner de código de barras ou QR Teams](~/concepts/device-capabilities/qr-barcode-scanner-capability.md)
* [Integrar funcionalidades de localização no Teams](~/concepts/device-capabilities/location-capability.md)
