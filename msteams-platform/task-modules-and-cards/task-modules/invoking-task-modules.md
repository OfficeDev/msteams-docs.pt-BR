---
title: Invocar e ignorar módulos de tarefas
description: Invocar e descartar módulos de tarefa.
author: surbhigupta12
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: ab6425ae90c04e142e5d69f4a41ff49358731a23
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59155166"
---
# <a name="invoke-and-dismiss-task-modules"></a>Invocar e ignorar módulos de tarefas

Os módulos de tarefa podem ser invocados de guias, bots ou links profundos. A resposta pode ser em HTML, JavaScript ou como um Cartão Adaptável. Há muita flexibilidade em termos de como os módulos de tarefa são invocados e como lidar com a resposta da interação do usuário. A tabela a seguir resume como isso funciona:

| Invocado usando | Módulo de tarefa com HTML ou JavaScript | Módulo de tarefa com Cartão Adaptável |
| --- | --- | --- |
| JavaScript em uma guia | 1. Use a função SDK do Teams cliente `tasks.startTask()` com uma função de retorno de chamada `submitHandler(err, result)` opcional. <br/><br/> 2. No código do módulo de tarefas, quando o usuário tiver executado as ações, chame a função Teams SDK com um objeto `tasks.submitTask()` `result` como parâmetro. Se um `submitHandler` retorno de chamada foi especificado em , Teams chama como um `tasks.startTask()` `result` parâmetro. Se houve um erro ao invocar , a `tasks.startTask()` função será chamada com uma cadeia de `submitHandler` `err` caracteres. <br/><br/> 3. Você também pode especificar um `completionBotId` ao chamar `teams.startTask()` . Em `result` seguida, o é enviado para o bot. | 1. Chame a função SDK do cliente Teams com um objeto TaskInfo e contenha o JSON para o Cartão Adaptável para mostrar no `tasks.startTask()` [](#the-taskinfo-object) `TaskInfo.card` pop-up do módulo de tarefas. <br/><br/> 2. Se um retorno de chamada foi especificado em , Teams chama-o com uma cadeia de caracteres, se houve um erro ao invocar ou se o usuário fechar o `submitHandler` pop-up do módulo de tarefa usando o X na parte superior `tasks.startTask()` `err` `tasks.startTask()` direita. <br/><br/> 3. Se o usuário pressionar um `Action.Submit` botão, seu `data` objeto será retornado como o valor de `result` . |
| Botão de cartão bot | 1. Botões de cartão bot, dependendo do tipo de botão, podem invocar módulos de tarefa de duas maneiras, uma URL de link profundo ou enviando uma `task/fetch` mensagem. <br/><br/> 2. Se a ação do botão for o tipo de botão para Cartões Adaptáveis, um evento que seja `type` um HTTP POST será enviado para o `task/fetch` `Action.Submit` `task/fetch invoke` bot. O bot responde ao POST com HTTP 200 e ao corpo da resposta contendo um wrapper ao redor do [objeto TaskInfo](#the-taskinfo-object). Para obter mais informações, consulte [invocando um módulo de tarefa usando `task/fetch` ](~/task-modules-and-cards/task-modules/task-modules-bots.md#invoke-a-task-module-using-taskfetch). Teams exibe o módulo de tarefa. <br/><br/> 3. Depois que o usuário tiver executado as ações, chame a função Teams SDK com um `tasks.submitTask()` `result` objeto como parâmetro. O bot recebe uma `task/submit invoke` mensagem que contém o `result` objeto. <br/><br/> 4. Você tem três maneiras diferentes de responder à mensagem, não fazendo nada que seja a tarefa concluída com êxito, exibindo uma mensagem para o usuário em uma janela pop-up ou invocando outra janela do módulo de `task/submit` tarefa. Para obter mais informações, [consulte discussão detalhada em `task/submit` ](~/task-modules-and-cards/task-modules/task-modules-bots.md#the-flexibility-of-tasksubmit). | <ul><li> Como botões em cartões de Estrutura de Bot, os botões em Cartões Adaptáveis suportam duas maneiras de invocar módulos de tarefa, urLs de link profundo com botões e `Action.openUrl` `task/fetch` usar `Action.Submit` botões. </li></ul> <br/><br/> <ul><li> Os módulos de tarefa com Cartões Adaptáveis funcionam de forma muito semelhante ao caso HTML ou JavaScript. A principal diferença é que, como não há JavaScript quando você está usando Cartões Adaptáveis, não há como chamar `tasks.submitTask()` . Em vez disso, Teams pega o objeto e o retorna como `data` `Action.Submit` a carga do `task/submit` evento. Para obter mais informações, consulte [flexibilidade de `task/submit` ](~/task-modules-and-cards/task-modules/task-modules-bots.md#the-flexibility-of-tasksubmit). </li></ul> |
| URL de link profundo <br/>[Sintaxe de URL](#task-module-deep-link-syntax) | 1. Teams invoca o módulo de tarefa que é a URL que aparece dentro do especificado no parâmetro `<iframe>` `url` do link profundo. Não há `submitHandler` retorno de chamada. <br/><br/> 2. Dentro do JavaScript da página no módulo de tarefas, chame para fechar com um objeto como um parâmetro, o mesmo que ao invocá-lo de uma guia ou um botão de cartão `tasks.submitTask()` `result` de bot. No entanto, a lógica de conclusão é ligeiramente diferente. Se sua lógica de conclusão reside no cliente que está se não houver bot, não há retorno de chamada, portanto, qualquer lógica de conclusão deve estar no código que precede a `submitHandler` chamada para `tasks.submitTask()` . Os erros de invocação são relatados apenas por meio do console. Se você tiver um bot, poderá especificar um parâmetro no `completionBotId` link profundo para enviar o objeto por meio de um `result` `task/submit` evento. | 1. Teams invoca o módulo de tarefa que é o corpo do cartão JSON do Cartão Adaptável especificado como um valor codificado por URL do parâmetro `card` do link profundo. <br/><br/> 2. O usuário fecha o módulo de tarefa selecionando o X no canto superior direito do módulo de tarefa ou pressionando `Action.Submit` um botão no cartão. Como não há como chamar, o usuário deve ter um bot para enviar o valor `submitHandler` dos campos Cartão Adaptável. O usuário deve usar o `completionBotId` parâmetro no link profundo para especificar o bot para enviar os dados para o uso de um `task/submit invoke` evento. |

A próxima seção especifica o `TaskInfo` objeto que define determinados atributos para um módulo de tarefa.

## <a name="the-taskinfo-object"></a>O objeto TaskInfo

O `TaskInfo` objeto contém os metadados de um módulo de tarefa. Defina `url` o para um iFrame incorporado ou para um Cartão `card` Adaptável. A tabela a seguir fornece a definição de objeto:

| Atributo | Tipo | Descrição |
| --- | --- | --- |
| `title` | string | Esse atributo aparece abaixo do nome do aplicativo e à direita do ícone do aplicativo. |
| `height` | número ou cadeia de caracteres | Esse atributo pode ser um número que representa a altura do módulo de tarefas em pixels `small` ou `medium` , ou `large` . Para obter mais informações, consulte [task module sizing](#task-module-sizing). |
| `width` | número ou cadeia de caracteres | Esse atributo pode ser um número que representa a largura do módulo de tarefa em pixels `small` ou `medium` , ou `large` . Para obter mais informações, consulte [task module sizing](#task-module-sizing). |
| `url` | cadeia de caracteres | Esse atributo é a URL da página carregada como `<iframe>` um dentro do módulo de tarefa. O domínio da URL deve estar na matriz [validDomains](~/resources/schema/manifest-schema.md#validdomains) do aplicativo no manifesto do aplicativo. |
| `card` | Anexo de cartão de bot adaptável ou cartão adaptável | Esse atributo é o JSON do Cartão Adaptável a ser exibido no módulo de tarefa. Se o usuário estiver invocando de um bot, use o JSON de Cartão Adaptável em um objeto Bot `attachment` Framework. Em uma guia, o usuário deve usar um Cartão Adaptável. Para obter mais informações, [consulte Adaptive Card or Adaptive Card bot card attachment](#adaptive-card-or-adaptive-card-bot-card-attachment) |
| `fallbackUrl` | cadeia de caracteres | Esse atributo abre a URL em uma guia do navegador, se um cliente não dá suporte ao recurso de módulo de tarefa. |
| `completionBotId` | cadeia de caracteres | Este atributo especifica uma ID de aplicativo bot para enviar o resultado da interação do usuário com o módulo de tarefa. Se especificado, o bot recebe um `task/submit invoke` evento com um objeto JSON na carga de eventos. |

> [!NOTE]
> O recurso de módulo de tarefa exige que os domínios de todas as URLs que você deseja carregar sejam incluídos na matriz no manifesto `validDomains` do aplicativo.

A próxima seção especifica o tamanho do módulo de tarefas que permite ao usuário definir a altura e a largura do módulo de tarefa.

## <a name="task-module-sizing"></a>Ressarção do módulo de tarefas

Usando inteiros para e , define a altura e a `TaskInfo.width` largura do módulo de tarefa em `TaskInfo.height` pixels. No entanto, dependendo do tamanho da janela e da resolução de tela da equipe, eles são reduzidos proporcionalmente, mantendo a taxa de proporção que é largura ou altura.

Se e são , ou , o tamanho do retângulo vermelho na imagem a seguir é uma proporção do espaço `TaskInfo.width` `TaskInfo.height` `"small"` `"medium"` `"large"` disponível, 20%, 50%, e 60% para e `width` 20%, 50% e 66% para `height` :

![Exemplo de módulo de tarefa](~/assets/images/task-module/task-module-example.png)

Os módulos de tarefa invocados de uma guia podem ser resized dinamicamente. Depois de chamar, você pode chamar onde as propriedades de altura e largura no objeto newSize estão em conformidade com a especificação `tasks.startTask()` `tasks.updateTask(newSize)` TaskInfo, por exemplo `{ height: 'medium', width: 'medium' }` .

A próxima seção fornece exemplos de como incorporar módulos de tarefa em um vídeo do YouTube e um PowerApp.

## <a name="task-module-css-for-html-or-javascript-task-modules"></a>Módulo de tarefas CSS para módulos de tarefa HTML ou JavaScript

Os módulos de tarefa baseados em HTML ou JavaScript têm acesso a toda a área do módulo de tarefa abaixo do header. Embora isso ofereça uma grande flexibilidade, se você quiser que o preenchimento ao redor das bordas se alinhe com os elementos do header e evite barras de rolagem desnecessárias, o usuário deve fornecer o CSS correto. As próximas seções fornecem alguns exemplos para alguns casos de uso.

**Exemplo 1: vídeo do YouTube**

O YouTube oferece a capacidade de inserir vídeos em páginas da Web. É fácil inserir vídeos em páginas da Web em um módulo de tarefa usando uma página da Web de stub simples.

![Vídeo do YouTube](~/assets/images/task-module/youtube-example.png)

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

**Exemplo 2: PowerApp**

O usuário também pode usar a mesma abordagem para inserir um PowerApp. Como a altura ou a largura de qualquer PowerApp individual é personalizável, o usuário pode ajustar a altura e a largura para alcançar a apresentação desejada.

![PowerApp de gerenciamento de ativos](~/assets/images/task-module/powerapp-example.png)

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

A próxima seção fornece detalhes sobre como invocar seu cartão usando o cartão adaptável ou o anexo de cartão de bot adaptável.

## <a name="adaptive-card-or-adaptive-card-bot-card-attachment"></a>Anexo de cartão de bot adaptável ou cartão adaptável

Dependendo de como você está invocando seu , você deve usar um Cartão Adaptável ou um anexo de cartão de bot cartão adaptável, que é um Cartão Adaptável envolvido em um `card` objeto attachment.

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

O código a seguir fornece um exemplo de um anexo de cartão de bot cartão adaptável quando você está invocando de um bot:

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

A próxima seção fornece detalhes sobre a sintaxe de link profundo do módulo de tarefas, incluindo o `TaskInfo` objeto `APP_ID` e `BOT_APP_ID` .

## <a name="task-module-deep-link-syntax"></a>Sintaxe de link profundo do módulo de tarefas

Um link profundo do módulo de tarefas é uma serialização do objeto TaskInfo com os dois outros detalhes a seguir e, `APP_ID` opcionalmente, `BOT_APP_ID` o :

`https://teams.microsoft.com/l/task/APP_ID?url=<TaskInfo.url>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID`

`https://teams.microsoft.com/l/task/APP_ID?card=<TaskInfo.card>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID`

Para os tipos de dados e os valores de autorização `<TaskInfo.url>` para , , , e , consulte o objeto `<TaskInfo.card>` `<TaskInfo.height>` `<TaskInfo.width>` `<TaskInfo.title>` [TaskInfo](#the-taskinfo-object).

> [!TIP]
> A URL codifica o link profundo ao usar o `card` parâmetro, por [ `encodeURI()` ](https://www.w3schools.com/jsref/jsref_encodeURI.asp)exemplo, a função de JavaScript.

A tabela a seguir fornece informações sobre `APP_ID` e `BOT_APP_ID` :

| Valor | Tipo | Obrigatório | Descrição |
| --- | --- | --- | --- |
| `APP_ID` | string | Sim | A [ID](~/resources/schema/manifest-schema.md#id) do aplicativo invocando o módulo de tarefa. A [matriz validDomains](~/resources/schema/manifest-schema.md#validdomains) no manifesto deve `APP_ID` conter o domínio para se estiver na `url` `url` URL. A ID do aplicativo já é conhecida quando um módulo de tarefa é invocado de uma guia ou um bot, por isso ele não está incluído em `TaskInfo` . |
| `BOT_APP_ID` | string | Não | Se um valor `completionBotId` for especificado, o `result` objeto será enviado usando uma mensagem para o bot `task/submit invoke` especificado. `BOT_APP_ID` deve ser especificado como um bot no manifesto do aplicativo, ou seja, você não pode enviá-lo para qualquer bot. |

> [!NOTE]
> `APP_ID` e pode ser o mesmo em muitos casos, se um aplicativo tiver um bot recomendado para usar como ID de um aplicativo se `BOT_APP_ID` houver um.

A próxima seção fornece detalhes sobre como usar um teclado com o módulo de tarefas do aplicativo.

## <a name="keyboard-and-accessibility-guidelines"></a>Diretrizes de teclado e acessibilidade

Com módulos de tarefa baseados em HTML ou JavaScript, você deve garantir que o módulo de tarefas do aplicativo possa ser usado com um teclado. Os programas de leitor de tela também dependem da capacidade de navegar usando o teclado. Isso inclui as duas coisas a seguir:

* Usando o [atributo tabindex](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/tabindex) em suas marcas HTML para controlar quais elementos podem ser focalizados. Além disso, use o atributo tabindex para identificar onde ele participa da navegação sequencial do teclado geralmente com as teclas <kbd>Tab</kbd> e <kbd>Shift-Tab.</kbd>
* Manipulando <kbd>a chave Esc</kbd> no JavaScript para o módulo de tarefas. O código a seguir fornece um exemplo de como manipular a <kbd>chave Esc:</kbd>

    ```javascript
    // Handle the Esc key
    document.onkeyup = function(event) {
    if ((event.key === 27) || (event.key === "Escape")) {
      microsoftTeams.submitTask(null); // this will return an err object to the completionHandler()
      }
    }
    ```

Microsoft Teams garante que a navegação do teclado funcione corretamente do header do módulo de tarefas para o HTML e vice-versa.

## <a name="code-sample"></a>Exemplo de código

|Nome do exemplo | Descrição | .NET | Node.js|
|----------------|-----------------|--------------|----------------|
|Exemplo de módulo de tarefa bots-V4 | Exemplos para a criação de módulos de tarefa. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/54.teams-task-module)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/54.teams-task-module)|
|Guias de exemplo de módulo de tarefa e bots-V3 | Exemplos para a criação de módulos de tarefa. |[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/csharp)|[Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/nodejs)| 

## <a name="see-also"></a>Confira também

* [Solicitar permissões do dispositivo](~/concepts/device-capabilities/native-device-permissions.md)
* [Integrar recursos de mídia](~/concepts/device-capabilities/mobile-camera-image-permissions.md)
* [Integrar a QR ou o recurso de scanner de código de barras Teams](~/concepts/device-capabilities/qr-barcode-scanner-capability.md)
* [Integrar recursos de localização Teams](~/concepts/device-capabilities/location-capability.md)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Usar módulos de tarefas nas guias](~/task-modules-and-cards/task-modules/task-modules-tabs.md)
