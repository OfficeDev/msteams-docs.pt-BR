---
title: O que são os módulos de tarefas?
author: clearab
description: Adicionar experiências pop-up modais para coletar ou exibir informações aos usuários de seus Microsoft Teams aplicativos
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

Os módulos de tarefas permitem que você crie experiências pop-up modais em seu aplicativo Teams. Dentro do pop-up, você pode executar seu próprio código HTML/JavaScript personalizado, mostrar um widget baseado como um vídeo do YouTube ou do Microsoft Stream ou exibir um `<iframe>` [cartão Adaptável](/adaptive-cards/). Eles são especialmente úteis para iniciar e concluir tarefas ou exibir informações ricas, como vídeos ou Power BI painéis. Uma experiência pop-up geralmente é mais natural para usuários iniciando e concluindo tarefas em comparação com uma guia ou uma experiência de bot baseada em conversa.

Os módulos de tarefas são construídos com base nas Microsoft Teams guias; eles são essencialmente uma guia dentro de uma janela pop-up. Eles usam o mesmo SDK, portanto, se você criou uma guia, já é 90% do caminho para poder criar um módulo de tarefa.

Módulos de tarefa podem ser invocados de três maneiras:

* **Canal ou guias** pessoais : Usando o SDK de guias Microsoft Teams você pode invocar módulos de tarefas de botões, links ou menus em sua guia. Isso é abordado em [detalhes aqui.](~/task-modules-and-cards/task-modules/task-modules-tabs.md)
* **Bots**: Botões nos [cartões enviados](~/task-modules-and-cards/cards/cards-reference.md) do bot. Isso é particularmente útil quando você não precisa de todos em um canal para ver o que está fazendo com um bot. Por exemplo, ao fazer com que os usuários respondam a uma votação em um canal, não é útil ver um registro da votação que está sendo criada. [Isso é abordado em detalhes aqui.](~/task-modules-and-cards/task-modules/task-modules-bots.md)
* **Fora do Teams de um link profundo:** você também pode criar URLs para invocar um módulo de tarefa de qualquer lugar. [Isso é abordado em detalhes aqui.](#task-module-deep-link-syntax)

## <a name="task-module-looks-like"></a>O módulo de tarefas tem a aparência

Veja a aparência de um módulo de tarefa quando invocado de um bot (sem retângulos coloridos e círculos numerados, claro):

![Exemplo do Módulo de Tarefa](~/assets/images/task-module/task-module-example.png)

Vamos passar por isso:

1. O ícone do seu [ `color` aplicativo](~/resources/schema/manifest-schema.md#icons).
1. O nome do seu [ `short` aplicativo](~/resources/schema/manifest-schema.md#name).
1. O título do módulo de tarefa especificado na `title` propriedade do [objeto TaskInfo](#the-taskinfo-object).
1. O botão fechar/cancelar do módulo de tarefas. Se o usuário pressionar isso, seu aplicativo receberá um `err` evento conforme descrito [aqui](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-submitting-the-result-of-a-task-module).
    > [!Note]
    > No momento, não é possível detectar esse evento quando um módulo de tarefa é invocado de um bot.
1. O retângulo azul será o local em que sua página da Web será exibida se você estiver carregando sua própria página da Web usando a propriedade `url` [do objeto TaskInfo](#the-taskinfo-object). Mais detalhes estão na seção [de redação do módulo](#task-module-sizing) de tarefas abaixo.
1. Se você estiver exibindo um cartão Adaptável por meio da propriedade do objeto TaskInfo, o preenchimento será adicionado para você, caso contrário, você precisará lidar `card` com isso por conta [própria](#task-module-css-for-htmljavascript-task-modules). [](#the-taskinfo-object)
1. Os botões de cartão adaptáveis serão renderizar aqui. Se você estiver usando sua própria página, deverá criar seus próprios botões.

## <a name="overview-of-invoking-and-dismissing-task-modules"></a>Visão geral de invocar e descartar módulos de tarefa

Os módulos de tarefa podem ser invocados de guias, bots ou links profundos e o que aparece em um pode ser HTML ou um cartão Adaptável, portanto, há muita flexibilidade em termos de como eles são invocados e como lidar com o resultado da interação de um usuário. A tabela abaixo resume como isso funciona:

| **Invocado por meio de...** | **O módulo de tarefa é HTML/JavaScript** | **Módulo de tarefa é cartão adaptável** |
| --- | --- | --- |
| **JavaScript em uma guia** | 1. Use a função SDK do Teams cliente `tasks.startTask()` com uma função de retorno de chamada `submitHandler(err, result)` opcional. <br/><br/> 2. No código do módulo de tarefas, quando o usuário terminar, chame a função Teams SDK com um `tasks.submitTask()` `result` objeto como parâmetro. Se um `submitHandler` retorno de chamada foi especificado em , Teams chama como um `tasks.startTask()` `result` parâmetro.<br/><br/> 3. Se houve um erro ao invocar , a `tasks.startTask()` função é chamada com uma cadeia de `submitHandler` `err` caracteres. <br/><br/> 4. Você também pode especificar um ao chamar - nesse `completionBotId` caso é enviado para o `teams.startTask()` `result` bot. | 1. Chame a função SDK do cliente Teams com um objeto TaskInfo e contenha o JSON para o cartão adaptável a ser mostrar no `tasks.startTask()` [](#the-taskinfo-object) `TaskInfo.card` pop-up do módulo de tarefas. <br/><br/> 2. Se um retorno de chamada foi especificado em , Teams chama-o com uma cadeia de caracteres se houver um erro ao invocar ou se o usuário fechar o `submitHandler` pop-up do módulo de tarefa usando o X na parte superior `tasks.startTask()` `err` `tasks.startTask()` direita. <br/><br/> 3. Se o usuário pressionar um botão Action.Submit, seu `data` objeto será retornado como o valor de `result` . |
| **Botão de cartão bot** | 1. Botões de cartão bot, dependendo do tipo de botão, podem invocar módulos de tarefa de duas maneiras: uma URL de link profundo ou enviando uma `task/fetch` mensagem. Confira abaixo como funcionam as URLs de link profundo. <br/><br/> 2. Se a ação do botão for ( tipo de botão para cartões adaptáveis), um evento (um HTTP POST sob as cobertas) será enviado para o bot e o bot responderá ao POST com `type` `task/fetch` HTTP `Action.Submit` `task/fetch invoke` 200 e ao corpo da resposta contendo um wrapper ao redor do [objeto TaskInfo.](#the-taskinfo-object) Isso é explicado em detalhes ao [invocar um módulo de tarefa por meio de tarefa/busca.](~/task-modules-and-cards/task-modules/task-modules-bots.md#invoking-a-task-module-through-taskfetch)<br/><br/> 3. Teams exibe o módulo de tarefa; quando o usuário for concluído, chame a função Teams SDK `tasks.submitTask()` com um objeto como `result` parâmetro. <br/><br/> 4. O bot recebe uma `task/submit invoke` mensagem que contém o `result` objeto. Você tem três maneiras diferentes de responder à mensagem: fazendo nada (a tarefa concluída com êxito), exibindo uma mensagem para o usuário em uma janela pop-up ou invocando outra janela de módulo de tarefa (ou seja, criando uma experiência como `task/submit` assistente). Essas três opções são mais discutidas [na discussão detalhada sobre tarefa/envio.](~/task-modules-and-cards/task-modules/task-modules-bots.md#the-flexibility-of-tasksubmit) | 1. Como botões em cartões da Estrutura de Bot, os botões em cartões adaptáveis suportam duas maneiras de invocar módulos de tarefa: URLs de link profundo com botões e usando `Action.openUrl` `task/fetch` `Action.Submit` botões. <br/><br/> 2. Os módulos de tarefa com cartões adaptáveis funcionam de forma muito semelhante à ocorrência HTML/JavaScript (consulte à esquerda). A principal diferença é que, como não há JavaScript quando você está usando cartões Adaptáveis, não há como chamar `tasks.submitTask()` . Em vez disso, Teams o objeto de e retorna-o como a carga do `data` `Action.Submit` `task/submit` evento, conforme descrito [aqui](~/task-modules-and-cards/task-modules/task-modules-bots.md#the-flexibility-of-tasksubmit). |
| **URL de link profundo** <br/>[Sintaxe de URL](#task-module-deep-link-syntax) | 1. Teams invoca o módulo de tarefa; a URL que aparece dentro `<iframe>` do especificado no parâmetro do link `url` profundo. Não há `submitHandler` retorno de chamada. <br/><br/> 2. Dentro do JavaScript da página no módulo de tarefas, chame para fechar com um objeto como um parâmetro, o mesmo que ao invocá-lo de uma guia ou um botão de cartão `tasks.submitTask()` `result` de bot. No entanto, a lógica de conclusão é ligeiramente diferente. Se sua lógica de conclusão reside no cliente (ou seja, se não houver bot), não há retorno de chamada, portanto, qualquer lógica de conclusão deve estar no código anterior à chamada `submitHandler` para `tasks.submitTask()` . Os erros de invocação são relatados apenas por meio do console. Se você tiver um bot, poderá especificar um parâmetro no `completionBotId` link profundo para enviar o objeto por meio de um `result` `task/submit` evento. | 1. Teams invoca o módulo de tarefa; o corpo do cartão JSON do cartão Adaptável é especificado como um valor codificado por URL do parâmetro `card` do link profundo. <br/><br/> 2. O usuário fecha o módulo de tarefa clicando no X no canto superior direito do módulo de tarefa ou pressionando `Action.Submit` um botão no cartão. Como não há para chamar, você deve ter um bot para enviar o valor dos campos `submitHandler` de cartão adaptáveis para. Você usa o parâmetro no link profundo para especificar o bot para o qual `completionBotId` enviar os dados por meio de um `task/submit invoke` evento. |

## <a name="the-taskinfo-object"></a>O objeto TaskInfo

O `TaskInfo` objeto contém os metadados de um módulo de tarefa. A definição do objeto está abaixo. Você **deve** definir um `url` iFrame incorporado ou para um Cartão `card` Adaptável.

| Atributo | Tipo | Descrição |
| --- | --- | --- |
| `title` | string | Aparece abaixo do nome do aplicativo e à direita do ícone do aplicativo. |
| `height` | número ou cadeia de caracteres | Pode ser um número que representa a altura do módulo de tarefas em pixels `small` ou `medium` , ou `large` . [Confira abaixo como a altura e a largura são manipuladas.](#task-module-sizing) |
| `width` | número ou cadeia de caracteres | Pode ser um número que representa a largura do módulo de tarefa em pixels `small` ou `medium` , ou `large` . [Confira abaixo como a altura e a largura são manipuladas.](#task-module-sizing) |
| `url` | cadeia de caracteres | A URL da página carregada como um `<iframe>` dentro do módulo de tarefa. O domínio da URL deve estar na matriz [validDomains](~/resources/schema/manifest-schema.md#validdomains) do aplicativo no manifesto do aplicativo. |
| `card` | Cartão adaptável ou um anexo de cartão de bot de cartão adaptável | O JSON do cartão Adaptável a ser exibido no módulo de tarefa. Se você estiver invocando de um bot, precisará usar o JSON de cartão adaptável em um objeto Bot `attachment` Framework. Em uma guia, você usará apenas um Cartão Adaptável. [Veja um exemplo.](#adaptive-card-or-adaptive-card-bot-card-attachment) |
| `fallbackUrl` | cadeia de caracteres | Se um cliente não suportar o recurso de módulo de tarefa, essa URL será aberta em uma guia do navegador. |
| `completionBotId` | cadeia de caracteres | Especifica uma ID de aplicativo bot para enviar o resultado da interação do usuário com o módulo de tarefa para. Se especificado, o bot receberá um `task/submit invoke` evento com um objeto JSON na carga de eventos. |

> [!NOTE]
> O recurso de módulo de tarefa exige que os domínios de todas as URLs que você deseja carregar sejam incluídos na matriz no manifesto `validDomains` do aplicativo.

## <a name="task-module-sizing"></a>Ressarção do módulo de tarefas

Usar inteiros para `TaskInfo.width` e `TaskInfo.height` definirá a altura e a largura em pixels. No entanto, dependendo do tamanho da janela e da resolução da tela da equipe, eles serão reduzidos proporcionalmente, mantendo a taxa de proporção (largura/altura).

Se e são , ou o tamanho do retângulo vermelho na imagem acima é uma proporção do espaço `TaskInfo.width` `TaskInfo.height` `"small"` `"medium"` `"large"` disponível: 20%, 50%, 60% para e `width` 20%, 50%, 66% para `height` .

Os módulos de tarefa invocados de uma guia podem ser resized dinamicamente. Depois de chamar, você pode chamar onde as propriedades de altura e largura no objeto newSize estão em conformidade com `tasks.startTask()` `tasks.updateTask(newSize)` a especificação TaskInfo (ex. `{ height: 'medium', width: 'medium' }`).

## <a name="task-module-css-for-htmljavascript-task-modules"></a>Módulo de tarefas CSS para módulos de tarefa HTML/JavaScript

Os módulos de tarefa baseados em HTML/JavaScript têm acesso a toda a área do módulo de tarefa abaixo do header. Embora isso ofereça uma grande flexibilidade, se você quiser que o preenchimento em torno das bordas se alinhe com os elementos do header e evite barras de rolagem desnecessárias, você precisará fornecer o CSS correto. Aqui estão alguns exemplos para alguns casos de uso.

### <a name="example-1---youtube-video"></a>Exemplo 1 - vídeo do YouTube

O YouTube oferece a capacidade de inserir vídeos em páginas da Web. Usando uma página da Web de stub simples, é fácil mostrar isso em um módulo de tarefa:

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

O CSS tem esta aparência:

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

Você também pode usar a mesma abordagem para inserir um PowerApp. Como a altura/largura de qualquer PowerApp individual é personalizável, talvez seja necessário ajustar a altura e a largura para alcançar a apresentação desejada.

![PowerApp de Gerenciamento de Ativos](~/assets/images/task-module/powerapp-example.png)

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

## <a name="adaptive-card-or-adaptive-card-bot-card-attachment"></a>Cartão adaptável ou anexo de cartão bot adaptável

Conforme mencionado acima, dependendo de como você está invocando seu, você precisará usar um cartão Adaptável ou um anexo de cartão de bot de cartão adaptável (que é apenas um cartão adaptável envolvido em um objeto `card` attachment).

Ao invocar de uma guia, você precisará usar um cartão adaptável. Veja um exemplo muito simples:

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

Ao invocar de um bot, você precisará usar um anexo de cartão de bot de cartão adaptável, como no exemplo abaixo:

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

Você precisará lembrar se está invocando um módulo de tarefa contendo um cartão Adaptável de um bot ou de uma guia.

## <a name="task-module-deep-link-syntax"></a>Sintaxe de link profundo do módulo de tarefas

Um link profundo do módulo de tarefas é apenas uma serialização do objeto [TaskInfo](#the-taskinfo-object) com duas outras informações e, opcionalmente, `APP_ID` o `BOT_APP_ID` :

`https://teams.microsoft.com/l/task/APP_ID?url=<TaskInfo.url>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID`

`https://teams.microsoft.com/l/task/APP_ID?card=<TaskInfo.card>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID`

Consulte [o objeto TaskInfo](#the-taskinfo-object) para os tipos de dados e valores para `<TaskInfo.url>` , , , e `<TaskInfo.card>` `<TaskInfo.height>` `<TaskInfo.width>` `<TaskInfo.title>` .

> [!TIP]
> Certifique-se de codificar a URL do link profundo, especialmente ao usar o `card` parâmetro (por [ `encodeURI()` ](https://www.w3schools.com/jsref/jsref_encodeURI.asp)exemplo, a função de JavaScript ).

Aqui estão as informações sobre `APP_ID` `BOT_APP_ID` e:

| Valor | Tipo | Obrigatório? | Descrição |
| --- | --- | --- | --- |
| `APP_ID` | string | Sim | A [id](~/resources/schema/manifest-schema.md#id) do aplicativo invocando o módulo de tarefa. A [matriz validDomains](~/resources/schema/manifest-schema.md#validdomains) no manifesto deve `APP_ID` conter o domínio para se estiver na `url` `url` URL. (A ID do aplicativo já é conhecida quando um módulo de tarefa é invocado de uma guia ou um bot, por isso ele não está incluído em `TaskInfo` .) |
| `BOT_APP_ID` | string | Não | Se um valor for especificado, o objeto será enviado por meio de uma `completionBotId` mensagem para o bot `result` `task/submit invoke` especificado. `BOT_APP_ID` deve ser especificado como um bot no manifesto do aplicativo, ou seja, você não pode simplesmente enviá-lo para qualquer bot. |

Observe que ele é válido para e para ser o mesmo e, em muitos casos, será se um aplicativo tiver um bot, pois é recomendável usá-lo como ID de um aplicativo se houver `APP_ID` `BOT_APP_ID` um.

## <a name="keyboard-and-accessibility-guidelines"></a>Diretrizes de teclado e acessibilidade

Com módulos de tarefa baseados em HTML/JavaScript, é sua responsabilidade garantir que o módulo de tarefas do aplicativo possa ser usado com um teclado. Os programas de leitor de tela também dependem da capacidade de navegar usando o teclado. Por uma questão prática, isso significa duas coisas:

1. Usando o [atributo tabindex](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/tabindex) em suas marcas HTML para controlar quais elementos podem ser focalizados e se/onde ele participa da navegação sequencial do teclado (geralmente com as teclas <kbd>Tab</kbd> e <kbd>Shift-Tab).</kbd>
2. Manipulando <kbd>a chave Esc</kbd> no JavaScript para o módulo de tarefas. Aqui está um exemplo de código mostrando como fazer isso:

  ```javascript
  // Handle the Esc key
  document.onkeyup = function(event) {
  if ((event.key === 27) || (event.key === "Escape")) {
    microsoftTeams.submitTask(null); // this will return an err object to the completionHandler()
    }
  }
  ```

Microsoft Teams garantirá que a navegação do teclado funcione corretamente do header do módulo de tarefas para o HTML e vice-versa.

## <a name="code-sample"></a>Exemplo de código
|**Exemplo de nome** | **Descrição** | **.NET** | **Node.js**|
|----------------|-----------------|--------------|----------------|
|Exemplo de módulo de tarefa (Bots-V4) | Exemplos para a criação de módulos de tarefa. |[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/nodejs)| 
|Exemplo de módulo de tarefa (Guias + Bots-V3) | Exemplos para a criação de módulos de tarefa. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/54.teams-task-module)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/54.teams-task-module)|

## <a name="see-also"></a>Confira também

* [Solicitar permissões do dispositivo](../concepts/device-capabilities/native-device-permissions.md)
* [Integrar recursos de mídia](../concepts/device-capabilities/mobile-camera-image-permissions.md)
* [Integrar a QR ou o recurso de scanner de código de barras Teams](../concepts/device-capabilities/qr-barcode-scanner-capability.md)
* [Integrar recursos de localização Teams](../concepts/device-capabilities/location-capability.md)
