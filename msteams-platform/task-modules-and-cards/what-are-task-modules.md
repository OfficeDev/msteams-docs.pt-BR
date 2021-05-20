---
title: O que são os módulos de tarefas?
author: clearab
description: Adicione experiências popup modais para coletar ou exibir informações aos seus usuários a partir de seus aplicativos de Microsoft Teams
localization_priority: Normal
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 23157e30ce25c2dfa1c21e7f5c4ddd4f735b660f
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566835"
---
# <a name="task-modules"></a>Módulos de tarefas

Os módulos de tarefas permitem que você crie experiências pop-up modais em seu aplicativo Teams. Dentro do popup você pode executar seu próprio código HTML/JavaScript personalizado, mostrar um `<iframe>` widget baseado em um youTube ou vídeo Microsoft Stream ou exibir uma [placa Adaptive](/adaptive-cards/). Eles são especialmente úteis para iniciar e completar tarefas ou exibir informações ricas, como vídeos ou Power BI dashboards. Uma experiência pop-up é muitas vezes mais natural para os usuários que iniciam e completam tarefas em comparação com uma guia ou uma experiência de bot baseada em conversas.

Os módulos de tarefas se baseiam na base de guias Microsoft Teams; eles são essencialmente uma guia dentro de uma janela pop-up. Eles usam o mesmo SDK, então se você construiu uma guia você já está 90% do caminho para ser capaz de criar um módulo de tarefa.

Módulos de tarefa podem ser invocados de três maneiras:

* **Canal ou guias pessoais**: Usando o Microsoft Teams Tabs SDK você pode invocar módulos de tarefa a partir de botões, links ou menus em sua guia. [Isso está coberto em detalhes aqui.](~/task-modules-and-cards/task-modules/task-modules-tabs.md)
* **Bots**: Botões em [cartões](~/task-modules-and-cards/cards/cards-reference.md) enviados do seu bot. Isso é particularmente útil quando você não precisa de todos em um canal para ver o que você está fazendo com um bot. Por exemplo, ao fazer com que os usuários respondam a uma votação em um canal, não é útil ver um registro da votação que está sendo criada. [Isso está coberto de detalhes aqui.](~/task-modules-and-cards/task-modules/task-modules-bots.md)
* **Fora de Teams de um link profundo**: Você também pode criar URLs para invocar um módulo de tarefa de qualquer lugar. [Isso está coberto de detalhes aqui.](#task-module-deep-link-syntax)

## <a name="task-module-looks-like"></a>Módulo de tarefas parece

Veja como é um módulo de tarefa quando invocado a partir de um bot (sem os retângulos coloridos e círculos numerados, é claro):

![Exemplo do módulo de tarefas](~/assets/images/task-module/task-module-example.png)

Vamos passar por isso:

1. Ícone do seu aplicativo [ `color` ](~/resources/schema/manifest-schema.md#icons).
1. O [ `short` nome](~/resources/schema/manifest-schema.md#name)do seu aplicativo.
1. O título do módulo de tarefa especificado na `title` propriedade do [objeto TaskInfo](#the-taskinfo-object).
1. O botão de fechamento/cancelamento do módulo de tarefas. Se o usuário pressionar isso, seu aplicativo receberá um `err` evento conforme descrito [aqui](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-submitting-the-result-of-a-task-module).
    > [!Note]
    > No momento, não é possível detectar esse evento quando um módulo de tarefa é invocado a partir de um bot.
1. O retângulo azul é o lugar onde sua página da Web aparece se você estiver carregando sua própria página da Web usando a `url` propriedade do [objeto TaskInfo](#the-taskinfo-object). Mais detalhes estão na seção [de dimensionamento do módulo de tarefa](#task-module-sizing) abaixo.
1. Se você estiver exibindo um cartão Adaptive através `card` da propriedade do objeto [TaskInfo,](#the-taskinfo-object) o preenchimento será adicionado para você, caso contrário, você precisará [lidar com isso sozinho](#task-module-css-for-htmljavascript-task-modules).
1. Os botões de cartão adaptativos serão renderizados aqui. Se você estiver usando sua própria página, você deve criar seus próprios botões.

## <a name="overview-of-invoking-and-dismissing-task-modules"></a>Visão geral de invocar e descartar módulos de tarefas

Os módulos de tarefa podem ser invocados a partir de guias, bots ou links profundos e o que aparece em um pode ser HTML ou um cartão Adaptive, então há muita flexibilidade em termos de como eles são invocados e como lidar com o resultado da interação de um usuário. A tabela abaixo resume como isso funciona:

| **Invocado via...** | **O módulo de tarefas é HTML/JavaScript** | **O módulo de tarefas é cartão adaptável** |
| --- | --- | --- |
| **JavaScript em uma guia** | 1. Use a função SDK do cliente Teams `tasks.startTask()` com uma função opcional de retorno de `submitHandler(err, result)` chamada. <br/><br/> 2. No código do módulo de tarefa, quando o usuário estiver concluído, chame a função Teams SDK `tasks.submitTask()` com um objeto como `result` parâmetro. Se um `submitHandler` retorno de chamada foi especificado em , Teams `tasks.startTask()` chama-o `result` como parâmetro.<br/><br/> 3. Se houve um erro ao `tasks.startTask()` invocar, a função é chamada com uma `submitHandler` `err` sequência. <br/><br/> 4. Você também pode especificar um `completionBotId` ao ligar - nesse caso é enviado para o bot em vez `teams.startTask()` `result` disso. | 1. Ligue para a função Teams cliente SDK `tasks.startTask()` com um [objeto TaskInfo](#the-taskinfo-object) e `TaskInfo.card` contendo o JSON para que a placa Adaptive seja exibida no popup do módulo de tarefa. <br/><br/> 2. Se um `submitHandler` retorno de chamada foi especificado em , Teams o chama com uma `tasks.startTask()` `err` sequência se houve um erro ao invocar `tasks.startTask()` ou se o usuário fecha o popup do módulo de tarefa usando o X no canto superior direito. <br/><br/> 3. Se o usuário pressionar um botão Action.Submit, seu `data` objeto será devolvido como o valor de `result` . |
| **Botão de cartão de bot** | 1. Os botões da placa de bot, dependendo do tipo de botão, podem invocar módulos de tarefa de duas maneiras: uma URL de link profundo ou enviando uma `task/fetch` mensagem. Veja abaixo como as URLs de link profundo funcionam. <br/><br/> 2. Se a ação do botão `type` for `task/fetch` `Action.Submit` (tipo de botão para cartões adaptativos), um `task/fetch invoke` evento (um POST HTTP sob as capas) será enviado para o bot, e o bot responder ao POST com HTTP 200 e o corpo de resposta contendo um invólucro em torno do [objeto TaskInfo](#the-taskinfo-object). Isso é explicado em detalhes [na invocação de um módulo de tarefa via tarefa/busca](~/task-modules-and-cards/task-modules/task-modules-bots.md#invoking-a-task-module-through-taskfetch).<br/><br/> 3. Teams exibe o módulo de tarefa; quando o usuário estiver concluído, chame a função Teams SDK `tasks.submitTask()` com um objeto como `result` parâmetro. <br/><br/> 4. O bot recebe uma `task/submit invoke` mensagem que contém o `result` objeto. Você tem três maneiras diferentes de responder à `task/submit` mensagem: não fazendo nada (a tarefa concluída com sucesso), exibindo uma mensagem para o usuário em uma janela pop-up ou invocando outra janela do módulo de tarefa (ou seja, criando uma experiência semelhante a um assistente). Essas três opções são mais discutidas [na discussão detalhada sobre tarefa/envio](~/task-modules-and-cards/task-modules/task-modules-bots.md#the-flexibility-of-tasksubmit). | 1. Como botões em placas bot framework, os botões em placas adaptativas suportam duas maneiras de invocar módulos de tarefa: URLs de link profundo com `Action.openUrl` botões e `task/fetch` usando `Action.Submit` botões. <br/><br/> 2. Os módulos de tarefa com placas adaptativas funcionam de forma muito semelhante à caixa HTML/JavaScript (ver à esquerda). A grande diferença é que, como não há JavaScript quando você está usando cartões Adaptive, não há como ligar `tasks.submitTask()` . Em vez disso, Teams pega o `data` objeto e o devolve como a carga do `Action.Submit` `task/submit` caso, conforme descrito [aqui.](~/task-modules-and-cards/task-modules/task-modules-bots.md#the-flexibility-of-tasksubmit) |
| **URL de link profundo** <br/>[Sintaxe de URL](#task-module-deep-link-syntax) | 1. Teams invoca o módulo de tarefa; a URL que aparece dentro do `<iframe>` especificado no parâmetro do link `url` profundo. Não há `submitHandler` retorno. <br/><br/> 2. Dentro do JavaScript da página no módulo de tarefa, ligue `tasks.submitTask()` para fechá-lo com um `result` objeto como parâmetro, o mesmo que ao invogá-lo a partir de uma guia ou um botão de cartão de bot. A lógica de conclusão é um pouco diferente, no entanto. Se sua lógica de conclusão reside no cliente (ou seja, se não houver bot) não há `submitHandler` retorno de chamada, portanto, qualquer lógica de conclusão deve estar no código anterior à chamada para `tasks.submitTask()` . Os erros de invocação são relatados apenas através do console. Se você tiver um bot, então você pode especificar um `completionBotId` parâmetro no link profundo para enviar o objeto através de um `result` `task/submit` evento. | 1. Teams invoca o módulo de tarefa; o corpo da placa JSON da placa Adaptive é especificado como um valor codificado por URL do `card` parâmetro do link profundo. <br/><br/> 2. O usuário fecha o módulo de tarefa clicando no X no canto superior direito do módulo de tarefa ou pressionando um `Action.Submit` botão no cartão. Como não há `submitHandler` para chamar, você deve ter um bot para enviar o valor dos campos de cartão Adaptive para. Você usa o `completionBotId` parâmetro no link profundo para especificar o bot para enviar os dados através de um `task/submit invoke` evento. |

## <a name="the-taskinfo-object"></a>O objeto TaskInfo

O `TaskInfo` objeto contém os metadados de um módulo de tarefa. A definição do objeto está abaixo. Você **deve** definir para `url` um iFrame incorporado ou para uma placa `card` adaptativa.

| Atributo | Tipo | Descrição |
| --- | --- | --- |
| `title` | string | Aparece abaixo o nome do aplicativo e à direita do ícone do aplicativo. |
| `height` | número ou cadeia de caracteres | Este pode ser um número representando a altura do módulo de tarefa em pixels, ou `small` `medium` , ou `large` . [Veja abaixo como a altura e a largura são tratadas](#task-module-sizing). |
| `width` | número ou cadeia de caracteres | Este pode ser um número representando a largura do módulo de tarefa em pixels, ou `small` `medium` , ou `large` . [Veja abaixo como a altura e a largura são tratadas](#task-module-sizing). |
| `url` | cadeia de caracteres | A URL da página carregada como um `<iframe>` dentro do módulo de tarefa. O domínio da URL deve estar no [conjunto valido Domínio](~/resources/schema/manifest-schema.md#validdomains) do aplicativo no manifesto do seu aplicativo. |
| `card` | Cartão adaptativo ou um acessório de cartão adaptativo | O JSON para a placa Adaptativa aparecer no módulo de tarefa. Se você estiver invocando de um bot, você precisará usar a placa Adaptive JSON em um objeto Bot `attachment` Framework. A partir de uma guia você usará apenas um Cartão Adaptável. [Aqui está um exemplo.](#adaptive-card-or-adaptive-card-bot-card-attachment) |
| `fallbackUrl` | cadeia de caracteres | Se um cliente não suportar o recurso do módulo de tarefa, essa URL será aberta em uma guia do navegador. |
| `completionBotId` | cadeia de caracteres | Especifica um ID do aplicativo bot para enviar o resultado da interação do usuário com o módulo de tarefa para. Se especificado, o bot receberá um `task/submit invoke` evento com um objeto JSON na carga de eventos. |

> [!NOTE]
> O recurso do módulo de tarefa requer que os domínios de quaisquer URLs que você deseja carregar estejam incluídos `validDomains` no array no manifesto do seu aplicativo.

## <a name="task-module-sizing"></a>Dimensionamento do módulo de tarefas

O uso de inteiros `TaskInfo.width` para e `TaskInfo.height` definirá a altura e largura em pixels. No entanto, dependendo do tamanho da resolução da janela e da tela da Equipe, eles serão reduzidos proporcionalmente, mantendo a proporção (largura/altura).

Se `TaskInfo.width` e são , ou o tamanho do `TaskInfo.height` `"small"` `"medium"` `"large"` retângulo vermelho na imagem acima é uma proporção do espaço disponível: 20%, 50%, 60% para `width` e 20%, 50%, 66% para `height` .

Os módulos de tarefa invocados a partir de uma guia podem ser redimensionados dinamicamente. Depois de `tasks.startTask()` ligar, você pode chamar `tasks.updateTask(newSize)` onde as propriedades de altura e largura no objeto newSize estão de acordo com a especificação TaskInfo (ex. `{ height: 'medium', width: 'medium' }`).

## <a name="task-module-css-for-htmljavascript-task-modules"></a>Módulo de tarefa CSS para módulos de tarefa HTML/JavaScript

Os módulos de tarefa baseados em HTML/JavaScript têm acesso a toda a área do módulo de tarefa abaixo do cabeçalho. Embora isso ofereça muita flexibilidade, se você quiser estofamento ao redor das bordas para se alinhar com os elementos de cabeçalho e evitar barras de rolagem desnecessárias, você precisará fornecer o CSS certo. Aqui estão alguns exemplos para alguns casos de uso.

### <a name="example-1---youtube-video"></a>Exemplo 1 - Vídeo do YouTube

O YouTube oferece a capacidade de incorporar vídeos em páginas da Web. Usando uma página web de stub simples é fácil mostrar isso em um módulo de tarefa:

![Vídeo do YouTube](~/assets/images/task-module/youtube-example.png)

Aqui está o HTML para esta página, sem o CSS:

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

O CSS é assim:

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

### <a name="example-2---powerapp"></a>Exemplo 2 - PowerApp

Você pode usar a mesma abordagem para incorporar um PowerApp também. Como a altura/largura de qualquer PowerApp individual é personalizável, você pode precisar ajustar a altura e largura para alcançar a apresentação desejada.

![PowerApp de gestão de ativos](~/assets/images/task-module/powerapp-example.png)

```html
<iframe width="720" height="520" src="https://web.powerapps.com/webplayer/iframeapp?source=iframe&screenColor=rgba(104,101,171,1)&appId=/providers/Microsoft.PowerApps/apps/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"></iframe>
```

E o CSS é:

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

## <a name="adaptive-card-or-adaptive-card-bot-card-attachment"></a>Cartão adaptativo ou cartão adaptativo do cartão de cartão

Como notamos acima, dependendo de como você está invocando o `card` seu, você precisará usar uma placa Adaptive ou um anexo de cartão adaptável (que é apenas uma placa adaptativa embrulhada em um objeto de anexo).

Quando você estiver invocando de uma guia, você precisará usar um cartão adaptativo. Aqui está um exemplo muito simples:

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

Quando você estiver invocando de um bot, você precisará usar um anexo de cartão adaptável como no exemplo abaixo:

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

Você precisará lembrar se está invocando um módulo de tarefa contendo uma placa Adaptive de um bot ou de uma guia.

## <a name="task-module-deep-link-syntax"></a>Sintaxe de link profundo do módulo de tarefa

Um link profundo do módulo de tarefas é apenas uma serialização do [objeto TaskInfo](#the-taskinfo-object) com duas outras informações `APP_ID` e, opcionalmente, o `BOT_APP_ID` :

`https://teams.microsoft.com/l/task/APP_ID?url=<TaskInfo.url>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID`

`https://teams.microsoft.com/l/task/APP_ID?card=<TaskInfo.card>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID`

Consulte [o objeto TaskInfo](#the-taskinfo-object) para os tipos de dados e valores permitidos para `<TaskInfo.url>` , , , e `<TaskInfo.card>` `<TaskInfo.height>` `<TaskInfo.width>` `<TaskInfo.title>` .

> [!TIP]
> Certifique-se de codificar o link profundo, especialmente ao usar o `card` parâmetro (por exemplo, [ `encodeURI()` função](https://www.w3schools.com/jsref/jsref_encodeURI.asp)JavaScript ).

Aqui estão as informações sobre `APP_ID` `BOT_APP_ID` e:

| Valor | Tipo | Obrigatório? | Descrição |
| --- | --- | --- | --- |
| `APP_ID` | string | Sim | A [id](~/resources/schema/manifest-schema.md#id) do aplicativo invocando o módulo de tarefa. O [array validDomains](~/resources/schema/manifest-schema.md#validdomains) no manifesto `APP_ID` deve conter o domínio para se estiver na `url` `url` URL. (O ID do aplicativo já é conhecido quando um módulo de tarefa é invocado a partir de uma guia ou de um bot, e é por isso que ele não está incluído em `TaskInfo` .) |
| `BOT_APP_ID` | string | Não | Se um valor `completionBotId` for especificado, o `result` objeto será enviado através de uma `task/submit invoke` mensagem para o bot especificado. `BOT_APP_ID` deve ser especificado como um bot no manifesto do aplicativo, ou seja, você não pode simplesmente enviá-lo para qualquer bot. |

Observe que é válido para `APP_ID` e `BOT_APP_ID` ser o mesmo, e em muitos casos será se um aplicativo tem um bot, uma vez que é recomendado usar isso como identificação de um aplicativo se houver um.

## <a name="keyboard-and-accessibility-guidelines"></a>Diretrizes de teclado e acessibilidade

Com módulos de tarefa baseados em HTML/JavaScript, é sua responsabilidade garantir que o módulo de tarefas do seu aplicativo possa ser usado com um teclado. Os programas de leitor de tela também dependem da capacidade de navegar usando o teclado. Como uma questão prática, isso significa duas coisas:

1. Usando o [atributo tabindex](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/tabindex) em suas tags HTML para controlar quais elementos podem ser focados e se/onde ele participa na navegação sequencial do teclado (geralmente com as teclas <kbd>Tab</kbd> e <kbd>Shift-Tab).</kbd>
2. Manuseando a tecla <kbd>Esc</kbd> no JavaScript para o módulo de tarefas. Aqui está uma amostra de código mostrando como fazer isso:

  ```javascript
  // Handle the Esc key
  document.onkeyup = function(event) {
  if ((event.key === 27) || (event.key === "Escape")) {
    microsoftTeams.submitTask(null); // this will return an err object to the completionHandler()
    }
  }
  ```

Microsoft Teams garantirá que a navegação do teclado funcione corretamente a partir do cabeçalho do módulo de tarefa em seu HTML e vice-versa.

## <a name="code-sample"></a>Exemplo de código
|**Nome da amostra** | **Descrição** | **.NET** | **Node.js**|
|----------------|-----------------|--------------|----------------|
|Amostra do módulo de tarefa (Bots-V4) | Amostras para a criação de módulos de tarefas. |[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/nodejs)| 
|Amostra do módulo de tarefa (Tabs + Bots-V3) | Amostras para a criação de módulos de tarefas. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/54.teams-task-module)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/54.teams-task-module)|

## <a name="see-also"></a>Confira também

* [Solicitar permissões do dispositivo](../concepts/device-capabilities/native-device-permissions.md)
* [Integrar recursos de mídia](../concepts/device-capabilities/mobile-camera-image-permissions.md)
* [Integre o recurso de QR ou scanner de código de barras em Teams](../concepts/device-capabilities/qr-barcode-scanner-capability.md)
* [Integre os recursos de localização em Teams](../concepts/device-capabilities/location-capability.md)
