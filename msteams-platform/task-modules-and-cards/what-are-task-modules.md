---
title: O que são os módulos de tarefas?
author: clearab
description: Adicione experiências de Popup modais para coletar ou exibir informações para seus usuários de seus aplicativos do Microsoft Teams.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 44d4e308614763b9da36c2abb7dd150778484c56
ms.sourcegitcommit: 50571f5c6afc86177c4fe1032fe13366a7b706dd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2020
ms.locfileid: "49576852"
---
# <a name="what-are-task-modules"></a>O que são os módulos de tarefas?

Os módulos de tarefas permitem que você crie experiências pop-up restritas em seu aplicativo do Microsoft Teams. Dentro do pop-up, você pode executar seu próprio código HTML/JavaScript personalizado, mostrar um `<iframe>` widget baseado em um YouTube ou Microsoft Stream Video ou exibir um [cartão adaptável](/adaptive-cards/). Eles são especialmente úteis para iniciar e concluir tarefas ou exibir informações ricas, como vídeos ou painéis do Power BI. Uma experiência de pop-up geralmente é mais natural para usuários que iniciam e concluem tarefas comparadas a uma guia ou uma experiência de bot baseada em conversas.

Os módulos de tarefas são criados na base das guias do Microsoft Teams; Eles são essencialmente uma guia dentro de uma janela pop-up. Eles usam o mesmo SDK, portanto, se você tiver criado uma guia, já terá 90% da maneira de poder criar um módulo de tarefa.

Os módulos de tarefa podem ser invocados de três maneiras:

* **Guias de canal ou pessoais.** Usando o SDK de guias do Microsoft Teams, você pode chamar módulos de tarefa de botões, links ou menus na sua guia. [isso é abordado em detalhes aqui.](~/task-modules-and-cards/task-modules/task-modules-tabs.md)
* **Robôs.** Botões de [cartões](~/task-modules-and-cards/cards/cards-reference.md) enviados do bot. Isso é particularmente útil quando você não precisa de todos em um canal para ver o que está fazendo com um bot. Por exemplo, quando os usuários respondem a uma pesquisa em um canal, não é extremamente útil ver um registro dessa pesquisa que está sendo criada. [Isso é abordado em detalhes aqui.](~/task-modules-and-cards/task-modules/task-modules-bots.md)
* **Fora do teams de um link profundo.** Você também pode criar URLs para chamar um módulo de tarefa de qualquer lugar. [Isso é abordado em detalhes aqui.](#task-module-deep-link-syntax)

## <a name="what-a-task-module-looks-like"></a>A aparência de um módulo de tarefa

Veja a seguir a aparência de um módulo de tarefa quando invocado de um bot (sem os retângulos coloridos e círculos numerados, naturalmente):

![Exemplo de módulo de tarefa](~/assets/images/task-module/task-module-example.png)

Vamos orientá-lo:

1. O [ `color` ícone](~/resources/schema/manifest-schema.md#icons)do seu aplicativo.
2. O [ `short` nome](~/resources/schema/manifest-schema.md#name)do seu aplicativo.
3. O título do módulo de tarefa especificado na `title` Propriedade do [objeto TaskInfo](#the-taskinfo-object).
4. O botão fechar/cancelar do módulo de tarefa. Se o usuário pressionar isso, seu aplicativo receberá um `err` evento conforme descrito [aqui](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-submitting-the-result-of-a-task-module). (**Observação:** no momento, não é possível detectar esse evento quando um módulo de tarefa é chamado de um bot.)
5. O retângulo azul é o onde sua página da Web aparece se você estiver carregando sua própria página da Web usando a `url` Propriedade do [objeto TaskInfo](#the-taskinfo-object). Mais detalhes estão na seção [tamanho do módulo de tarefas](#task-module-sizing) abaixo.
6. Se você estiver exibindo um cartão adaptável por meio da `card` Propriedade do [objeto TaskInfo](#the-taskinfo-object) , o preenchimento será adicionado para você, caso contrário, você precisará [lidar com isso](#task-module-css-for-htmljavascript-task-modules).
7. Os botões de cartões adaptáveis serão renderizados aqui. Se estiver usando sua própria página, você deve criar seus próprios botões.

## <a name="overview-of-invoking-and-dismissing-task-modules"></a>Visão geral de chamar e descartar módulos de tarefa

Os módulos de tarefa podem ser invocados de guias, bots ou links profundas e o que aparece em um pode ser HTML ou um cartão adaptável, portanto, há muita flexibilidade em termos de como eles são invocados e como lidar com o resultado da interação de um usuário. A tabela a seguir resume como isso funciona:

| **Invocado via...** | **O módulo de tarefa é HTML/JavaScript** | **O módulo de tarefa é um cartão adaptável** |
| --- | --- | --- |
| **JavaScript em uma guia** | 1. Use a função SDK do teams `tasks.startTask()` com uma `submitHandler(err, result)` função de retorno de chamada opcional <br/><br/> 2. no código do módulo de tarefa, quando o usuário terminar, chame a função do SDK do teams `tasks.submitTask()` com um `result` objeto como um parâmetro. Se um `submitHandler` retorno de chamada tiver sido especificado no `tasks.startTask()` , o Teams o chamará `result` como um parâmetro.<br/><br/> 3. se houve um erro ao invocar `tasks.startTask()` , a `submitHandler` função é chamada com uma `err` cadeia de caracteres. <br/><br/> 4. você também pode especificar um `completionBotId` quando chamado `teams.startTask()` -, caso `result` seja enviado ao bot. | 1. chame a função de SDK do cliente do teams `tasks.startTask()` com um [objeto TaskInfo](#the-taskinfo-object) e `TaskInfo.card` que contém o JSON para o cartão adaptável a ser mostrado no pop-up módulo de tarefa. <br/><br/> 2. se um `submitHandler` retorno de chamada tiver sido especificado no `tasks.startTask()` , o Teams o chamará com uma `err` cadeia de caracteres se houver um erro ao invocar `tasks.startTask()` ou se o usuário fechar o pop-up de módulo de tarefa usando o X no canto superior direito. <br/><br/> 3. se o usuário pressiona um botão Action. Submit, seu `data` objeto é retornado como o valor de `result` . |
| **Botão cartão de bot** | 1. os botões de cartão de bot, dependendo do tipo de botão, podem chamar módulos de tarefas de duas maneiras: uma URL de link profundo ou enviando uma `task/fetch` mensagem. Veja abaixo como funcionam as URLs de link profundo. <br/><br/> 2. se a ação do botão `type` for `task/fetch` ( `Action.Submit` tipo de botão para cartões adaptáveis), um `task/fetch invoke` evento (um post http nas capas) será enviado ao bot, e o bot responderá à postagem com http 200 e o corpo da resposta contendo um invólucro em torno do [objeto TaskInfo](#the-taskinfo-object). Isso é explicado em detalhes sobre como [invocar um módulo de tarefa por meio de tarefa/busca](~/task-modules-and-cards/task-modules/task-modules-bots.md#invoking-a-task-module-via-taskfetch).<br/><br/> 3. o Microsoft Teams exibe o módulo de tarefa; Quando o usuário terminar, chame a função SDK do teams `tasks.submitTask()` com um `result` objeto como um parâmetro. <br/><br/> 4. o bot recebe uma `task/submit invoke` mensagem que contém o `result` objeto. Você tem três maneiras diferentes de responder à `task/submit` mensagem: fazendo nada (a tarefa foi concluída com êxito), exibindo uma mensagem para o usuário em uma janela pop-up ou invocando outra janela de módulo de tarefa (ou seja, criando uma experiência parecida com o assistente). Essas três opções são discutidas mais [na discussão detalhada sobre a tarefa/envio](~/task-modules-and-cards/task-modules/task-modules-bots.md#the-flexibility-of-tasksubmit). | 1. como os botões em cartões de estrutura de bot, os botões de cartões adaptáveis dão suporte a duas maneiras de chamar módulos de tarefa: URLs de link profundo com `Action.openUrl` botões e `task/fetch` usando os `Action.Submit` botões. <br/><br/> 2. os módulos de tarefa com cartões adaptáveis funcionam de forma semelhante ao caso HTML/JavaScript (consulte esquerda). A principal diferença é que, como não há JavaScript quando você está usando cartões adaptáveis, não há como chamar `tasks.submitTask()` . Em vez disso, o Microsoft Teams pega o `data` objeto `Action.Submit` e o retorna como a carga de no `task/submit` evento, conforme descrito [aqui](~/task-modules-and-cards/task-modules/task-modules-bots.md#the-flexibility-of-tasksubmit). |
| **URL de link profundo** <br/>[Sintaxe da URL](#task-module-deep-link-syntax) | 1. Teams invoca o módulo de tarefa; a URL que aparece dentro do `<iframe>` especificado no `url` parâmetro do link profundo. Não há nenhum `submitHandler` retorno de chamada. <br/><br/> 2. dentro do JavaScript da página no módulo de tarefa, chame `tasks.submitTask()` para fechá-lo com um `result` objeto como um parâmetro, o mesmo que ao chamá-lo de um botão de guia ou cartão de bot. No entanto, a lógica de conclusão é um pouco diferente. Se a lógica de conclusão residir no cliente (ou seja, se não houver nenhum bot), não há nenhum `submitHandler` retorno de chamada, portanto, qualquer lógica de conclusão deve estar no código que antecede a chamada `tasks.submitTask()` . Erros de invocação são relatados pelo console. Se você tiver um bot, poderá especificar um `completionBotId` parâmetro no link profundo para enviar o `result` objeto por um `task/submit` evento. | 1. Teams invoca o módulo de tarefa; o corpo do cartão JSON do cartão adaptável é especificado como um valor de codificação de URL do `card` parâmetro do link profundo. <br/><br/> 2. o usuário fecha o módulo de tarefa clicando no X no canto superior direito do módulo de tarefa ou pressionando um `Action.Submit` botão no cartão. Como não há `submitHandler` uma chamada, você deve ter um bot para enviar o valor dos campos de cartão adaptável para. Use o `completionBotId` parâmetro no link profundo para especificar o bot para o qual enviar os dados por meio de um `task/submit invoke` evento. |

> [!NOTE]
> Não há suporte para a invocação de um módulo de tarefa do JavaScript no Mobile.

## <a name="the-taskinfo-object"></a>O objeto TaskInfo

O `TaskInfo` objeto contém os metadados de um módulo de tarefa. A definição do objeto está abaixo. Você **deve** definir o `url` (para um iframe incorporado) ou `card` (para um cartão adaptável).

| Atributo | Tipo | Descrição |
| --- | --- | --- |
| `title` | string | Aparece abaixo do nome do aplicativo e à direita do ícone do aplicativo |
| `height` | número ou cadeia de caracteres | Pode ser um número que representa a altura do módulo de tarefa em pixels, ou `small` , `medium` ou `large` . [Veja abaixo como a altura e a largura são manipuladas](#task-module-sizing). |
| `width` | número ou cadeia de caracteres | Pode ser um número que representa a largura do módulo de tarefa em pixels, ou `small` , `medium` ou `large` . [Veja abaixo como a altura e a largura são manipuladas](#task-module-sizing). |
| `url` | cadeia de caracteres | A URL da página carregada como `<iframe>` dentro do módulo de tarefa. O domínio da URL deve estar na [matriz validDomains](~/resources/schema/manifest-schema.md#validdomains) do aplicativo no manifesto do seu aplicativo. |
| `card` | Cartão adaptável ou um anexo de cartão de bot de cartão adaptável | O JSON para o cartão adaptável que aparece no módulo de tarefa. Se você estiver invocando de um bot, precisará usar o cartão de readaptação JSON em um objeto de estrutura de bot `attachment` . Em uma guia, você usará apenas um cartão adaptável. [Veja um exemplo.](#adaptive-card-or-adaptive-card-bot-card-attachment) |
| `fallbackUrl` | cadeia de caracteres | Se um cliente não oferecer suporte ao recurso do módulo de tarefa, essa URL será aberta em uma guia do navegador. |
| `completionBotId` | cadeia de caracteres | Especifica uma ID do aplicativo bot para enviar o resultado da interação do usuário com o módulo de tarefa. Se especificado, o bot receberá um `task/submit invoke` evento com um objeto JSON na carga do evento. |

> [!NOTE]
> O recurso de módulo de tarefa requer que os domínios de qualquer URL que você deseja carregar estejam incluídos na `validDomains` matriz no manifesto do seu aplicativo.

## <a name="task-module-sizing"></a>Dimensionamento do módulo de tarefa

Usando números inteiros para `TaskInfo.width` e `TaskInfo.height` definirá a altura e a largura em pixels. No entanto, dependendo do tamanho da janela da equipe e da resolução de tela, elas serão reduzidas proporcionalmente enquanto mantêm a taxa de proporção (largura/altura).

Se `TaskInfo.width` e `TaskInfo.height` se `"small"` `"medium"` ou `"large"` o tamanho do retângulo vermelho na imagem acima é uma proporção do espaço disponível: 20%, 50%, 60% para `width` e 20%, 50%, 66% para `height` .

Os módulos de tarefa invocados de uma guia podem ser redimensionados dinamicamente. Após a chamada `tasks.startTask()` , você pode chamar `tasks.updateTask(newSize)` onde as propriedades Height e Width no objeto newSize estão de acordo com a especificação TaskInfo (ex. `{ height: 'medium', width: 'medium' }`).

## <a name="task-module-css-for-htmljavascript-task-modules"></a>CSS do módulo de tarefas para módulos de tarefa HTML/JavaScript

Os módulos de tarefa baseados em HTML/JavaScript têm acesso à área inteira do módulo de tarefa abaixo do cabeçalho. Embora isso ofereça uma grande quantidade de flexibilidade, se você quiser que o preenchimento entre as bordas seja alinhado com os elementos de cabeçalho e evite barras de rolagem desnecessárias, será necessário fornecer o CSS correto. Aqui estão alguns exemplos de alguns casos de uso.

### <a name="example-1---youtube-video"></a>Exemplo 1-vídeo do YouTube

O YouTube oferece a capacidade de inserir vídeos em páginas da Web. Usando uma página da Web de stub simples, é fácil mostrar isso em um módulo de tarefa:

![Vídeo do YouTube](~/assets/images/task-module/youtube-example.png)

Este é o HTML desta página, sem o CSS:

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

O CSS tem a seguinte aparência:

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

### <a name="example-2---powerapp"></a>Exemplo 2-PowerApp

Você pode usar a mesma abordagem para incorporar um PowerApp também. Como a altura/largura de qualquer PowerApp individual é personalizável, talvez seja necessário ajustar a altura e a largura para obter a apresentação desejada.

![Gerenciamento de ativos PowerApp](~/assets/images/task-module/powerapp-example.png)

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

## <a name="adaptive-card-or-adaptive-card-bot-card-attachment"></a>Cartão adaptável ou anexo cartão de bot de cartão adaptável

Conforme observamos acima, dependendo de como você está invocando seu `card` , você precisará usar um cartão adaptável ou um anexo de cartão de bot adaptável (que é apenas um cartão adaptável disposto em um objeto Attachment).

Ao invocar a partir de uma guia, você precisará usar um cartão adaptável. Veja um exemplo muito simples:

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

Você precisará se lembrar se está invocando um módulo de tarefa contendo um cartão adaptável de um bot ou de uma guia.

## <a name="task-module-deep-link-syntax"></a>Sintaxe de link profundo do módulo de tarefa

Um link profundo de módulo de tarefa é apenas uma serialização do [objeto TaskInfo](#the-taskinfo-object) com duas outras partes de informação `APP_ID` e, opcionalmente, o `BOT_APP_ID` :

`https://teams.microsoft.com/l/task/APP_ID?url=<TaskInfo.url>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID`

`https://teams.microsoft.com/l/task/APP_ID?card=<TaskInfo.card>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID`

Confira o [objeto TaskInfo](#the-taskinfo-object) para os tipos de dados e os valores permitidos para `<TaskInfo.url>` , `<TaskInfo.card>` , `<TaskInfo.height>` , `<TaskInfo.width>` e `<TaskInfo.title>` .

> [!TIP]
> Certifique-se de que a URL Codifique o link profundo, especialmente ao usar o `card` parâmetro (por exemplo, a [ `encodeURI()` função](https://www.w3schools.com/jsref/jsref_encodeURI.asp)de JavaScript).

Aqui estão as informações sobre `APP_ID` e `BOT_APP_ID` :

| Valor | Tipo | Obrigatório? | Descrição |
| --- | --- | --- | --- |
| `APP_ID` | string | Sim | A [ID](~/resources/schema/manifest-schema.md#id) do aplicativo que chama o módulo de tarefa. A [matriz validDomains](~/resources/schema/manifest-schema.md#validdomains) no manifesto para `APP_ID` deve conter o domínio para `url` se `url` estiver na URL. (O ID do aplicativo já é conhecido quando um módulo de tarefa é invocado de uma guia ou de um bot, que é o motivo pelo qual ele não está incluído no `TaskInfo` .) |
| `BOT_APP_ID` | string | Não | Se um valor for `completionBotId` especificado, o `result` objeto é enviado por meio de uma `task/submit invoke` mensagem para o bot especificado. `BOT_APP_ID` deve ser especificado como um bot no manifesto do aplicativo, ou seja, você não pode simplesmente enviá-lo para qualquer bot. |

Observe que é válido para `APP_ID` e `BOT_APP_ID` ser o mesmo, e em muitos casos será se um aplicativo tiver um bot, pois é recomendável usá-lo como a ID de um aplicativo, se houver um.

## <a name="keyboard-and-accessibility-guidelines"></a>Diretrizes de teclado e acessibilidade

Com módulos de tarefa baseados em HTML/JavaScript, é responsabilidade garantir que o módulo de tarefa do aplicativo possa ser usado com um teclado. Os programas de leitor de tela também dependem da capacidade de navegar usando o teclado. Como uma questão prática, isso significa duas coisas:

1. Usando o [atributo TabIndex](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/tabindex) em suas marcas HTML para controlar quais elementos podem ser focados e se/onde ele participa na navegação de teclado seqüencial (normalmente com as teclas <kbd>Tab</kbd> e <kbd>Shift-Tab</kbd> ).
2. Tratamento da chave <kbd>ESC</kbd> no JavaScript para seu módulo de tarefa. Veja um exemplo de código que mostra como fazer isso:

  ```javascript
  // Handle the Esc key
  document.onkeyup = function(event) {
  if ((event.key === 27) || (event.key === "Escape")) {
    microsoftTeams.submitTask(null); // this will return an err object to the completionHandler()
    }
  }
  ```

O Microsoft Teams garantirá que a navegação pelo teclado funcione corretamente do cabeçalho do módulo de tarefa no HTML e vice-versa.

## <a name="task-module-samples"></a>Amostras de módulo de tarefa

* [ Exemplo deNode.js/TypeScript](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs)
* [Exemplo de/.NET C#](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp)

> [!div class="nextstepaction"]
> [Saiba mais: solicitar permissões de dispositivo](/concepts/device-capabilities/native-device-permissions.md)

> [!div class="nextstepaction"]
>[Saiba mais: permissões da Galeria de câmera e imagem](/concepts/device-capabilities/mobile-camera-image-permissions.md)
