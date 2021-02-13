---
title: O que são os módulos de tarefas?
author: clearab
description: Adicione experiências pop-up modais para coletar ou exibir informações aos usuários de seus aplicativos do Microsoft Teams.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: d92da7e6def6d66efd2f94600b7b8f8847553701
ms.sourcegitcommit: e3b6bc31059ec77de5fbef9b15c17d358abbca0f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/12/2021
ms.locfileid: "50231656"
---
# <a name="what-are-task-modules"></a>O que são os módulos de tarefas?

Os módulos de tarefa permitem que você crie experiências de pop-up modais em seu aplicativo do Teams. Dentro do pop-up, você pode executar seu próprio código HTML/JavaScript personalizado, mostrar um widget baseado como um vídeo do YouTube ou do Microsoft Stream ou exibir um `<iframe>` [cartão adaptável.](/adaptive-cards/) Eles são especialmente úteis para iniciar e concluir tarefas ou exibir informações completas, como vídeos ou painéis do Power BI. Uma experiência pop-up geralmente é mais natural para os usuários que iniciam e concluim tarefas em comparação com uma guia ou uma experiência de bot baseada em conversa.

Os módulos de tarefas são construídos com base nas guias do Microsoft Teams; eles são essencialmente uma guia dentro de uma janela pop-up. Eles usam o mesmo SDK, portanto, se você criou uma guia, já está 90% da maneira de poder criar um módulo de tarefa.

Os módulos de tarefa podem ser invocados de três maneiras:

* **Canal ou guias pessoais.** Usando o SDK de Guias do Microsoft Teams, você pode invocar módulos de tarefas de botões, links ou menus em sua guia. Isso é abordado [em detalhes aqui.](~/task-modules-and-cards/task-modules/task-modules-tabs.md)
* **Bots.** Botões nos [cartões enviados](~/task-modules-and-cards/cards/cards-reference.md) do seu bot. Isso é particularmente útil quando você não precisa de todos em um canal para ver o que está fazendo com um bot. Por exemplo, ao fazer com que os usuários respondam a uma votação em um canal, não é útil ver um registro dessa sondagem sendo criada. [Isso é abordado em detalhes aqui.](~/task-modules-and-cards/task-modules/task-modules-bots.md)
* **Fora do Teams a partir de um link profundo.** Você também pode criar URLs para invocar um módulo de tarefa de qualquer lugar. [Isso é abordado em detalhes aqui.](#task-module-deep-link-syntax)

## <a name="what-a-task-module-looks-like"></a>A aparência de um módulo de tarefa

Veja a aparência de um módulo de tarefa quando invocado de um bot (sem os retângulos coloridos e os círculos numerados, claro):

![Exemplo de módulo de tarefa](~/assets/images/task-module/task-module-example.png)

Vamos falar sobre isso:

1. Ícone do seu [ `color` aplicativo.](~/resources/schema/manifest-schema.md#icons)
2. O nome do seu [ `short` aplicativo.](~/resources/schema/manifest-schema.md#name)
3. O título do módulo de tarefa especificado na `title` propriedade do [objeto TaskInfo](#the-taskinfo-object).
4. O botão fechar/cancelar do módulo de tarefa. Se o usuário pressionar isso, seu aplicativo receberá um `err` evento conforme descrito [aqui.](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-submitting-the-result-of-a-task-module) (**Observação:** atualmente não é possível detectar esse evento quando um módulo de tarefa é invocado de um bot.)
5. O retângulo azul é o local onde sua página da Web é exibida se você estiver carregando sua própria página da Web usando a propriedade `url` do [objeto TaskInfo](#the-taskinfo-object). Mais detalhes estão na seção [de remendamento do módulo](#task-module-sizing) de tarefa abaixo.
6. Se você estiver exibindo um cartão adaptável por meio da propriedade do objeto TaskInfo, o preenchimento é adicionado para você, caso contrário, você precisará lidar com isso por conta `card` [própria.](#task-module-css-for-htmljavascript-task-modules) [](#the-taskinfo-object)
7. Botões de cartão adaptável serão renderizar aqui. Se você estiver usando sua própria página, deverá criar seus próprios botões.

## <a name="overview-of-invoking-and-dismissing-task-modules"></a>Visão geral de como invocar e descartar módulos de tarefa

Os módulos de tarefa podem ser invocados de guias, bots ou links profundos e o que aparece em um pode ser HTML ou um cartão adaptável, portanto, há muita flexibilidade em termos de como eles são invocados e como lidar com o resultado da interação do usuário. A tabela a seguir resume como isso funciona:

| **Invocado por meio de...** | **O módulo de tarefa é HTML/JavaScript** | **O módulo de tarefa é cartão adaptável** |
| --- | --- | --- |
| **JavaScript em uma guia** | 1. Usar a função SDK do cliente Teams `tasks.startTask()` com uma função de retorno de chamada `submitHandler(err, result)` opcional <br/><br/> 2. No código do módulo de tarefa, quando o usuário terminar, chame a função SDK do Teams com um objeto `tasks.submitTask()` `result` como um parâmetro. Se um `submitHandler` retorno de chamada foi especificado, o Teams a chama como um `tasks.startTask()` `result` parâmetro.<br/><br/> 3. Se houver um erro ao invocar, a `tasks.startTask()` função será chamada com uma cadeia de `submitHandler` `err` caracteres. <br/><br/> 4. Você também pode especificar um `completionBotId` ao chamar - nesse `teams.startTask()` `result` caso, é enviado para o bot. | 1. Chame a função do SDK do cliente Teams com um objeto TaskInfo e contendo o JSON do cartão adaptável para mostrar no pop-up do módulo de `tasks.startTask()` [](#the-taskinfo-object) `TaskInfo.card` tarefas. <br/><br/> 2. Se um retorno de chamada foi especificado, o Teams a chamará com uma cadeia de caracteres se houver um erro ao chamar ou se o usuário fechar o `submitHandler` pop-up do módulo de tarefa usando o X no canto superior `tasks.startTask()` `err` `tasks.startTask()` direito. <br/><br/> 3. Se o usuário pressionar um botão Action.Submit, seu `data` objeto será retornado como o valor de `result` . |
| **Botão de cartão bot** | 1. Botões de cartão bot, dependendo do tipo de botão, podem invocar módulos de tarefa de duas maneiras: uma URL de link profundo ou enviando uma `task/fetch` mensagem. Veja abaixo como funcionam as URLs de link profundo. <br/><br/> 2. Se a ação do botão for ( tipo de botão para cartões adaptáveis), um evento (um HTTP POST nos cobertas) será enviado para o bot, e o bot responderá ao POST com `type` `task/fetch` HTTP `Action.Submit` `task/fetch invoke` 200 [](#the-taskinfo-object)e o corpo da resposta contendo um wrapper ao redor do objeto TaskInfo . Isso é explicado em detalhes ao [invocar um módulo de tarefa por meio de tarefa/busca.](~/task-modules-and-cards/task-modules/task-modules-bots.md#invoking-a-task-module-via-taskfetch)<br/><br/> 3. O Teams exibe o módulo de tarefa; quando o usuário terminar, chame a função do SDK do Teams `tasks.submitTask()` com um objeto como `result` parâmetro. <br/><br/> 4. O bot recebe uma `task/submit invoke` mensagem que contém o `result` objeto. Você tem três maneiras diferentes de responder à mensagem: não fazendo nada (a tarefa foi concluída com êxito), exibindo uma mensagem para o usuário em uma janela pop-up ou invocando outra janela do módulo de tarefa (ou seja, criando uma experiência do tipo `task/submit` assistente). Essas três opções são mais discutidas [na discussão detalhada sobre tarefa/envio.](~/task-modules-and-cards/task-modules/task-modules-bots.md#the-flexibility-of-tasksubmit) | 1. Como botões em cartões do Bot Framework, os botões em cartões adaptáveis suportam duas maneiras de invocar módulos de tarefa: URLs de link profundo com botões e usando `Action.openUrl` `task/fetch` `Action.Submit` botões. <br/><br/> 2. Os módulos de tarefa com cartões adaptáveis funcionam de maneira muito semelhante à ocorrência de HTML/JavaScript (veja à esquerda). A principal diferença é que, como não há JavaScript quando você está usando cartões adaptáveis, não há nenhuma maneira de `tasks.submitTask()` chamar. Em vez disso, o Teams pega o objeto e o retorna como a carga `data` `Action.Submit` do `task/submit` evento, conforme descrito [aqui.](~/task-modules-and-cards/task-modules/task-modules-bots.md#the-flexibility-of-tasksubmit) |
| **URL do link profundo** <br/>[Sintaxe da URL](#task-module-deep-link-syntax) | 1. O Teams invoca o módulo de tarefa; a URL que aparece dentro `<iframe>` do especificado no parâmetro do link `url` profundo. Não há retorno `submitHandler` de chamada. <br/><br/> 2. No JavaScript da página no módulo de tarefa, chame para fechar com um objeto como parâmetro, da mesma forma que ao chamá-lo de uma guia ou um botão de cartão `tasks.submitTask()` `result` bot. No entanto, a lógica de conclusão é ligeiramente diferente. Se a lógica de conclusão residir no cliente (ou seja, se não houver bot), não haverá retorno de chamada, portanto, qualquer lógica de conclusão deve estar no código que antecede a `submitHandler` chamada para `tasks.submitTask()` . Os erros de invocação são relatados apenas por meio do console. Se você tiver um bot, poderá especificar um parâmetro no `completionBotId` link profundo para enviar o objeto por meio de um `result` `task/submit` evento. | 1. O Teams invoca o módulo de tarefa; o corpo do cartão JSON do cartão adaptável é especificado como um valor codificado por URL do `card` parâmetro do link profundo. <br/><br/> 2. O usuário fecha o módulo de tarefa clicando no X no canto superior direito do módulo de tarefa ou pressionando `Action.Submit` um botão no cartão. Como não há para chamar, você deve ter um bot para enviar o valor dos `submitHandler` campos de cartão adaptável para. Use o `completionBotId` parâmetro no link profundo para especificar o bot para o qual enviar os dados por meio de um `task/submit invoke` evento. |

> [!NOTE]
> Não há suporte para invocar um módulo de tarefa do JavaScript em dispositivos móveis.

## <a name="the-taskinfo-object"></a>O objeto TaskInfo

O `TaskInfo` objeto contém os metadados de um módulo de tarefa. A definição de objeto está abaixo. Você **deve** definir `url` (para um iFrame incorporado) ou `card` (para um Cartão Adaptável).

| Atributo | Tipo | Descrição |
| --- | --- | --- |
| `title` | string | Aparece abaixo do nome do aplicativo e à direita do ícone do aplicativo |
| `height` | número ou cadeia de caracteres | Pode ser um número que representa a altura do módulo de tarefa em `small` pixels, ou , ou `medium` `large` . [Veja abaixo como a altura e a largura são tratadas.](#task-module-sizing) |
| `width` | número ou cadeia de caracteres | Pode ser um número que representa a largura do módulo de tarefa em `small` pixels, ou , ou `medium` `large` . [Veja abaixo como a altura e a largura são tratadas.](#task-module-sizing) |
| `url` | string | A URL da página carregada como um `<iframe>` dentro do módulo de tarefa. O domínio da URL deve estar na matriz [validDomains](~/resources/schema/manifest-schema.md#validdomains) do aplicativo no manifesto do aplicativo. |
| `card` | Cartão adaptável ou anexo de cartão de bot de cartão adaptável | O JSON para o cartão adaptável aparecer no módulo de tarefa. Se você estiver invocando de um bot, precisará usar o cartão adaptável JSON em um objeto da Estrutura de `attachment` Bot. Em uma guia, você usará apenas um Cartão Adaptável. [Veja um exemplo.](#adaptive-card-or-adaptive-card-bot-card-attachment) |
| `fallbackUrl` | string | Se um cliente não suportar o recurso de módulo de tarefa, essa URL será aberta em uma guia do navegador. |
| `completionBotId` | string | Especifica uma ID de aplicativo de bot para enviar o resultado da interação do usuário com o módulo de tarefa. Se especificado, o bot receberá um `task/submit invoke` evento com um objeto JSON na carga do evento. |

> [!NOTE]
> O recurso de módulo de tarefa exige que os domínios de quaisquer URLs que você deseja carregar sejam incluídos na matriz no `validDomains` manifesto do aplicativo.

## <a name="task-module-sizing"></a>Task module sizing

Usar inteiros para `TaskInfo.width` `TaskInfo.height` e definirá a altura e a largura em pixels. No entanto, dependendo do tamanho da janela e da resolução de tela da equipe, eles serão reduzidos proporcionalmente, mantendo a taxa de proporção (largura/altura).

If `TaskInfo.width` and are , or the size of the red rectangle in the picture above is `TaskInfo.height` a proportion of the `"small"` `"medium"` `"large"` available space: 20%, 50%, 60% for `width` and 20%, 50%, 66% for `height` .

Os módulos de tarefa invocados de uma guia podem ser resized dinamicamente. Depois de chamar, você pode chamar onde as propriedades de altura e largura no objeto newSize estão em conformidade com a especificação `tasks.startTask()` `tasks.updateTask(newSize)` TaskInfo (ex. `{ height: 'medium', width: 'medium' }`).

## <a name="task-module-css-for-htmljavascript-task-modules"></a>CSS do módulo de tarefa para módulos de tarefa HTML/JavaScript

Os módulos de tarefa baseados em HTML/JavaScript têm acesso a toda a área do módulo de tarefa abaixo do header. Embora isso ofereça uma grande flexibilidade, se você quiser que o preenchimento ao redor das bordas se alinhe com os elementos de header e evite barras de rolagem desnecessárias, você precisará fornecer o CSS correto. Aqui estão alguns exemplos para alguns casos de uso.

### <a name="example-1---youtube-video"></a>Exemplo 1 - Vídeo do YouTube

O YouTube oferece a capacidade de incorporar vídeos em páginas da Web. Usando uma página da Web stub simples, é fácil mostrar isso em um módulo de tarefa:

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

Você também pode usar a mesma abordagem para inserir um PowerApp. Como a altura/largura de qualquer PowerApp individual é personalizável, talvez seja necessário ajustar a altura e a largura para obter a apresentação desejada.

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

## <a name="adaptive-card-or-adaptive-card-bot-card-attachment"></a>Cartão adaptável ou anexo de cartão bot de cartão adaptável

Conforme mencionado acima, dependendo de como você está invocando o seu, você precisará usar um cartão adaptável ou um anexo de cartão bot de cartão adaptável (que é apenas um cartão adaptável empacotado em um objeto `card` anexo).

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

Ao invocar um bot, você precisará usar um anexo de cartão bot de cartão adaptável como no exemplo abaixo:

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

Você precisará se lembrar se está invocando um módulo de tarefa contendo um cartão adaptável de um bot ou de uma guia.

## <a name="task-module-deep-link-syntax"></a>Task module deep link syntax

Um link profundo do módulo de tarefa é apenas uma serialização do objeto [TaskInfo](#the-taskinfo-object) com duas outras informações e, opcionalmente, `APP_ID` `BOT_APP_ID` o:

`https://teams.microsoft.com/l/task/APP_ID?url=<TaskInfo.url>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID`

`https://teams.microsoft.com/l/task/APP_ID?card=<TaskInfo.card>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID`

Consulte [o objeto TaskInfo](#the-taskinfo-object) para os tipos de dados e valores que permitem `<TaskInfo.url>` , e `<TaskInfo.card>` `<TaskInfo.height>` `<TaskInfo.width>` `<TaskInfo.title>` .

> [!TIP]
> Certifique-se de codificar a URL do link profundo, especialmente ao usar o `card` parâmetro (por [ `encodeURI()` ](https://www.w3schools.com/jsref/jsref_encodeURI.asp)exemplo, a função do JavaScript).

Aqui estão as informações sobre `APP_ID` `BOT_APP_ID` e:

| Valor | Tipo | Obrigatório? | Descrição |
| --- | --- | --- | --- |
| `APP_ID` | string | Sim | A [id](~/resources/schema/manifest-schema.md#id) do aplicativo que invoca o módulo de tarefa. A [matriz validDomains](~/resources/schema/manifest-schema.md#validdomains) no manifesto `APP_ID` deve conter o domínio se estiver na `url` `url` URL. (A ID do aplicativo já é conhecida quando um módulo de tarefa é invocado de uma guia ou um bot, e é por isso que ele não está incluído em `TaskInfo` .) |
| `BOT_APP_ID` | string | Não | Se um valor `completionBotId` for especificado, o `result` objeto será enviado por meio de uma mensagem para o bot `task/submit invoke` especificado. `BOT_APP_ID` deve ser especificado como um bot no manifesto do aplicativo, ou seja, você não pode simplesmente enviá-lo para qualquer bot. |

Observe que ele é válido para ser o mesmo e, em muitos casos, será se um aplicativo tiver um bot, pois é recomendável usá-lo como ID de um aplicativo, se houver `APP_ID` `BOT_APP_ID` um.

## <a name="keyboard-and-accessibility-guidelines"></a>Diretrizes de teclado e acessibilidade

Com módulos de tarefa baseados em HTML/JavaScript, é sua responsabilidade garantir que o módulo de tarefas do seu aplicativo possa ser usado com um teclado. Programas de leitor de tela também dependem da capacidade de navegar usando o teclado. Na prática, isso significa duas coisas:

1. Usar o atributo [tabindex](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/tabindex) em suas marcas HTML para controlar quais elementos podem ser focalizados e se/onde ele participa da navegação de teclado sequencial (geralmente com as teclas <kbd>Tab</kbd> e <kbd>Shift-Tab).</kbd>
2. Manipulando <kbd>a chave Esc</kbd> no JavaScript para seu módulo de tarefa. Veja um exemplo de código mostrando como fazer isso:

  ```javascript
  // Handle the Esc key
  document.onkeyup = function(event) {
  if ((event.key === 27) || (event.key === "Escape")) {
    microsoftTeams.submitTask(null); // this will return an err object to the completionHandler()
    }
  }
  ```

O Microsoft Teams garantirá que a navegação de teclado funcione corretamente do header do módulo de tarefa para o HTML e vice-versa.

## <a name="task-module-samples"></a>Exemplos de módulo de tarefa

* [Node.js/TypeScript](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs)
* [Exemplo de C#/.NET](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp)

> [!div class="nextstepaction"]
> [Saiba mais: Solicitar permissões de dispositivo](../concepts/device-capabilities/native-device-permissions.md)

> [!div class="nextstepaction"]
> [Saiba mais: Integrar recursos de mídia](../concepts/device-capabilities/mobile-camera-image-permissions.md)
