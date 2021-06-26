---
title: Adicionar ações de cartão em um bot
description: Descreve ações de cartão em Microsoft Teams e como usá-las em seus bots
localization_priority: Normal
ms.topic: conceptual
keywords: ações de cartões de bots do teams
ms.openlocfilehash: 1b20ca8003ab74c5dd2860e754024ae64ff94527
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140086"
---
# <a name="card-actions"></a>Ações de cartão

Os cartões usados por bots e extensões de mensagens em Teams suportam os seguintes tipos de [`CardAction`](/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments#process-events-within-rich-cards) atividade:

> [!NOTE]
> As `CardAction` ações diferem `potentialActions` das Office 365 conectores quando usadas de conectores.

| Tipo | Ação |
| --- | --- |
| `openUrl` | Abre uma URL no navegador padrão. |
| `messageBack` | Envia uma mensagem e uma carga para o bot do usuário que selecionou o botão ou tocou no cartão. Envia uma mensagem separada para o fluxo de chat. |
| `imBack`| Envia uma mensagem para o bot do usuário que selecionou o botão ou tapped o cartão. Essa mensagem de usuário para bot é visível para todos os participantes da conversa. |
| `invoke` | Envia uma mensagem e uma carga para o bot do usuário que selecionou o botão ou tocou no cartão. Esta mensagem não está visível. |
| `signin` | Inicia o fluxo OAuth, permitindo que os bots se conectem com serviços seguros. |

> [!NOTE]
>* Teams não dá suporte a `CardAction` tipos não listados na tabela anterior.
>* Teams não dá suporte à `potentialActions` propriedade.
>* As ações de cartão são diferentes [das ações sugeridas](/azure/bot-service/bot-builder-howto-add-suggested-actions?view=azure-bot-service-4.0&tabs=javascript#suggest-action-using-button&preserve-view=true) no Bot Framework ou no Serviço de Bot do Azure. Ações sugeridas não são suportadas Microsoft Teams. Se quiser que os botões apareçam em uma mensagem Teams bot, use um cartão.
>* Se você estiver usando uma ação de cartão como parte de uma extensão de mensagens, as ações não funcionarão até que o cartão seja enviado ao canal. As ações não funcionam enquanto o cartão está na caixa de mensagem de redação.

## <a name="action-type-openurl"></a>Tipo de ação openUrl

`openUrl` tipo de ação especifica uma URL a ser lançada no navegador padrão.

> [!NOTE]
> Seu bot não recebe nenhum aviso sobre qual botão foi selecionado.

Com `openUrl` , você pode criar uma ação com as seguintes propriedades:

| Propriedade | Descrição |
| --- | --- |
| `title` | Aparece como o rótulo do botão. |
| `value` | Esse campo deve conter uma URL completa e corretamente formada. |

# <a name="json"></a>[JSON](#tab/json)

O código a seguir mostra um exemplo de `openUrl` tipo de ação em JSON:

```json
{
    "type": "openUrl",
    "title": "Tabs in Teams",
    "value": "https://msdn.microsoft.com/microsoft-teams/tabs"
}
```

# <a name="c"></a>[C#](#tab/csharp)

O código a seguir mostra um exemplo de `openUrl` tipo de ação C#:

```csharp
var button = new CardAction()
{
    Type = ActionTypes.OpenUrl,
    Title = "Tabs in Teams",
    Value = "https://docs.microsoft.com/en-us/microsoftteams/platform/"
};
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

O código a seguir mostra um exemplo de `openUrl` tipo de ação em JavaScript:

```javascript
CardFactory.actions([
{
    type: 'openUrl',
    title: 'Tabs in Teams',
    value: 'https://docs.microsoft.com/en-us/microsoftteams/platform/'
}])
```

---

## <a name="action-type-messageback"></a>Tipo de ação messageBack

Com `messageBack` , você pode criar uma ação totalmente personalizada com as seguintes propriedades:

| Propriedade | Descrição |
| --- | --- |
| `title` | Aparece como o rótulo do botão. |
| `displayText` | Opcional. Usado pelo usuário no fluxo de chat quando a ação é executada. Este texto não é enviado para seu bot. |
| `value` | Enviado ao bot quando a ação é executada. Você pode codificar contexto para a ação, como identificadores exclusivos ou um objeto JSON. |
| `text` | Enviado ao bot quando a ação é executada. Use essa propriedade para simplificar o desenvolvimento de bots. Seu código pode verificar uma única propriedade de nível superior para despachar a lógica do bot. |

A flexibilidade de meios de que seu código não pode deixar uma mensagem de usuário visível no `messageBack` histórico simplesmente não usando `displayText` .

# <a name="json"></a>[JSON](#tab/json)

O código a seguir mostra um exemplo de `messageBack` tipo de ação em JSON:

```json
{
  "buttons": [
    {
    "type": "messageBack",
    "title": "My MessageBack button",
    "displayText": "I clicked this button",
    "text": "User just clicked the MessageBack button",
    "value": "{\"property\": \"propertyValue\" }"
    }
  ]
}
```

A `value` propriedade pode ser uma cadeia de caracteres JSON serializada ou um objeto JSON.

# <a name="c"></a>[C#](#tab/csharp)

O código a seguir mostra um exemplo de `messageBack` tipo de ação C#:

```csharp
var button = new CardAction()
{
    Type = ActionTypes.MessageBack,
    Title = "My MessageBack button",
    DisplayText = "I clicked this button",
    Text = "User just clicked the MessageBack button",
    Value = "{\"property\": \"propertyValue\" }"
};
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

O código a seguir mostra um exemplo de `messageBack` tipo de ação em JavaScript:

```javascript
CardFactory.actions([
{
    type: 'messageBack',
    title: "My MessageBack button",
    displayText: "I clicked this button",
    text: "User just clicked the MessageBack button",
    value: {property: "propertyValue" }
}])
```

---

### <a name="inbound-message-example"></a>Exemplo de mensagem de entrada

`replyToId` contém a ID da mensagem de onde veio a ação do cartão. Use-o se quiser atualizar a mensagem.

O código a seguir mostra um exemplo de mensagem de entrada:

```json
{
   "text":"User just clicked the MessageBack button",
   "value":{
      "property":"propertyValue"
   },
   "type":"message",
   "timestamp":"2017-06-22T22:38:47.407Z",
   "id":"f:5261769396935243054",
   "channelId":"msteams",
   "serviceUrl":"https://smba.trafficmanager.net/amer-client-ss.msg/",
   "from":{
      "id":"29:102jd210jd010icsoaeclaejcoa9ue09u",
      "name":"John Smith"
   },
   "conversation":{
      "id":"19:malejcou081i20ojmlcau0@thread.skype;messageid=1498171086622"
   },
   "recipient":{
      "id":"28:76096e45-119f-4736-859c-6dfff54395f7",
      "name":"MyBot"
   },
   "entities":[
      {
        "locale": "en-US",
        "country": "US",
        "platform": "Windows",
        "timezone": "America/Los_Angeles",
        "type": "clientInfo" 
      }
   ],
   "channelData":{
      "channel":{
         "id":"19:malejcou081i20ojmlcau0@thread.skype"
      },
      "team":{
         "id":"19:12d021jdoijsaeoaue0u@thread.skype"
      },
      "tenant":{
         "id":"bec8e231-67ad-484e-87f4-3e5438390a77"
      }
   },
        "replyToId": "1575667808184",
}
```

## <a name="action-type-imback"></a>Tipo de ação imBack

A ação dispara uma mensagem de retorno para seu bot, como se o usuário a digitou `imBack` em uma mensagem de chat normal. Seu usuário e todos os outros usuários em um canal podem ver a resposta do botão.

Com `imBack` , você pode criar uma ação com as seguintes propriedades:

| Propriedade | Descrição |
| --- | --- |
| `title` | Aparece como o rótulo do botão. |
| `value` | Esse campo deve conter a cadeia de caracteres de texto usada no chat e, portanto, enviada de volta para o bot. Este é o texto da mensagem que você processa em seu bot para executar a lógica desejada. |

> [!NOTE]
> O `value` campo é uma cadeia de caracteres simples. Não há suporte para formatação ou caracteres ocultos.

# <a name="json"></a>[JSON](#tab/json)

O código a seguir mostra um exemplo de `imBack` tipo de ação em JSON:

```json
{
    "type": "imBack",
    "title": "More",
    "value": "Show me more"
}
```

# <a name="c"></a>[C#](#tab/csharp)

O código a seguir mostra um exemplo de `imBack` tipo de ação C#:

```csharp
var button = new CardAction()
{
    Type = ActionTypes.ImBack,
    Title = "More",
    Value = "Show me more"
};
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

O código a seguir mostra um exemplo de `imBack` tipo de ação em JavaScript:

```javascript
CardFactory.actions([
{
    type: "imBack",
    title: "More",
    value: "Show me more"
}])
```

---

## <a name="action-type-invoke"></a>Tipo de ação invocar

A `invoke` ação é usada para invocar [módulos de tarefa](~/task-modules-and-cards/task-modules/task-modules-bots.md).

A `invoke` ação contém três `type` propriedades, , e `title` `value` .

Com `invoke` , você pode criar uma ação com as seguintes propriedades:

| Propriedade | Descrição |
| --- | --- |
| `title` | Aparece como o rótulo do botão. |
| `value` | Essa propriedade pode conter uma cadeia de caracteres, um objeto JSON stringified ou um objeto JSON. |

# <a name="json"></a>[JSON](#tab/json)

O código a seguir mostra um exemplo de `invoke` tipo de ação em JSON:

```json
{
    "type": "invoke",
    "title": "Option 1",
    "value": {
        "option": "opt1"
    }
}
```

Quando um usuário seleciona o botão, seu bot recebe o `value` objeto com algumas informações adicionais.

> [!NOTE]
> O tipo de atividade `invoke` é, em vez `message` disso, `activity.Type == "invoke"` é .

# <a name="c"></a>[C#](#tab/csharp)

O código a seguir mostra um exemplo de `invoke` tipo de ação C#:

```csharp
var button = new CardAction()
{
    Title = "Option 1",
    Type = "invoke",
    Value = "{\"option\": \"opt1\"}"
};
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

O código a seguir mostra um exemplo de `invoke` tipo de ação Node.js:

```javascript
CardFactory.actions([
{
    type: "invoke",
    title: "Option 1",
    value: {
        option: "opt1"
    }
}])
```

---

### <a name="example-of-incoming-invoke-message"></a>Exemplo de mensagem de invocação de entrada

A propriedade de nível superior contém a ID da mensagem de onde a `replyToId` ação do cartão veio. Use-o se quiser atualizar a mensagem.

O código a seguir mostra um exemplo de mensagem de chamada de entrada:

```json
{
    "type": "invoke",
    "value": {
        "option": "opt1"
    },
    "timestamp": "2017-02-10T04:11:19.614Z",
    "localTimestamp": "2017-02-09T21:11:19.614-07:00",
    "id": "f:6894910862892785420",
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/",
    "from": {
        "id": "29:1Eniglq0-uVL83xNB9GU6w_G5a4SZF0gcJLprZzhtEbel21G_5h-
    NgoprRw45mP0AXUIZVeqrsIHSYV4ntgfVJQ",
        "name": "John Doe"
    },
    "conversation": {
        "id": "19:97b1ec61-45bf-453c-9059-6e8984e0cef4_8d88f59b-ae61-4300-bec0-caace7d28446@unq.gbl.spaces"
    },
    "recipient": {
        "id": "28:8d88f59b-ae61-4300-bec0-caace7d28446",
        "name": "MyBot"
    },
    "entities": [
        {
            "locale": "en-US",
            "country": "US",
            "platform": "Web",
            "type": "clientInfo"
        }
    ],
    "channelData": {
        "channel": {
            "id": "19:dc5ba12695be4eb7bf457cad6b4709eb@thread.skype"
        },
        "team": {
            "id": "19:712c61d0ef384e5fa681ba90ca943398@thread.skype"
        },
        "tenant": {
            "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    },
    "replyToId": "1575667808184"
}
```

## <a name="action-type-signin"></a>Signin do tipo de ação

`signin` tipo de ação inicia um fluxo OAuth que permite que os bots se conectem com serviços seguros. Para obter mais informações, consulte [fluxo de autenticação em bots](~/bots/how-to/authentication/auth-flow-bot.md).

Teams também oferece suporte [a ações de Cartões Adaptáveis](#adaptive-cards-actions) que são usadas apenas por Cartões Adaptáveis.

# <a name="json"></a>[JSON](#tab/json)

O código a seguir mostra um exemplo de `signin` tipo de ação em JSON:

```json
{
"type": "signin",
"title": "Click me for signin",
"value": "https://signin.com"
}
```

# <a name="c"></a>[C#](#tab/csharp)

O código a seguir mostra um exemplo de `signin` tipo de ação C#:

```csharp
var button = new CardAction()
{
    Type = ActionTypes.Signin,
    Title = "Click me for signin",
    Value = "https://signin.com"
};
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

O código a seguir mostra um exemplo de `signin` tipo de ação em JavaScript:

```javascript
CardFactory.actions([
{
    type: "signin",
    title: "Click me for signin",
    value: "https://signin.com"
}])
```

---

## <a name="adaptive-cards-actions"></a>Ações de Cartões Adaptáveis

Os Cartões Adaptáveis suportam quatro tipos de ação:

* [Action.OpenUrl](http://adaptivecards.io/explorer/Action.OpenUrl.html)
* [Action.Submit](http://adaptivecards.io/explorer/Action.Submit.html)
* [Action.ShowCard](http://adaptivecards.io/explorer/Action.ShowCard.html)
* [Action.Exebonito](/adaptive-cards/authoring-cards/universal-action-model#actionexecute)

Você também pode modificar a carga cartão adaptável para dar suporte a ações existentes da Estrutura de Bot usando uma propriedade `Action.Submit` `msteams` no objeto de `data` `Action.Submit` . A próxima seção fornece detalhes sobre como usar ações da Estrutura de Bot existentes com Cartões Adaptáveis.

> [!NOTE]
> Adicionar aos dados com uma ação da Estrutura de Bot não funciona com um módulo de tarefa `msteams` cartão adaptável.

### <a name="adaptive-cards-with-messageback-action"></a>Cartões Adaptáveis com ação messageBack

Para incluir uma `messageBack` ação com um Cartão Adaptável, inclua os seguintes detalhes no `msteams` objeto:

> [!NOTE]
> Você pode incluir propriedades ocultas adicionais no `data` objeto, se necessário.

| Propriedade | Descrição |
| --- | --- |
| `type` | Definir como `messageBack` . |
| `displayText` | Opcional. Usado pelo usuário no fluxo de chat quando a ação é executada. Este texto não é enviado para seu bot. |
| `value` | Enviado ao bot quando a ação é executada. Você pode codificar contexto para a ação, como identificadores exclusivos ou um objeto JSON. |
| `text` | Enviado ao bot quando a ação é executada. Use essa propriedade para simplificar o desenvolvimento de bots. Seu código pode verificar uma única propriedade de nível superior para despachar a lógica do bot. |

O código a seguir mostra um exemplo de Cartões Adaptáveis com `messageBack` ação:

```json
{
  "type": "Action.Submit",
  "title": "Click me for messageBack",
  "data": {
    "msteams": {
        "type": "messageBack",
        "displayText": "I clicked this button",
        "text": "text to bots",
        "value": "{\"bfKey\": \"bfVal\", \"conflictKey\": \"from value\"}"
    }
  }
}
```

### <a name="adaptive-cards-with-imback-action"></a>Cartões Adaptáveis com ação imBack

Para incluir uma `imBack` ação com um Cartão Adaptável, inclua os seguintes detalhes no `msteams` objeto:

> [!NOTE]
> Você pode incluir propriedades ocultas adicionais no `data` objeto, se necessário.

| Propriedade | Descrição |
| --- | --- |
| `type` | Definir como `imBack` . |
| `value` | Cadeia de caracteres que precisa ser ecoada novamente no chat. |

O código a seguir mostra um exemplo de Cartões Adaptáveis com `imBack` ação:

```json
{
  "type": "Action.Submit",
  "title": "Click me for imBack",
  "data": {
    "msteams": {
        "type": "imBack",
        "value": "Text to reply in chat"
    }
  }
}
```

### <a name="adaptive-cards-with-signin-action"></a>Cartões Adaptáveis com ação de signin

Para incluir uma `signin` ação com um Cartão Adaptável, inclua os seguintes detalhes no `msteams` objeto:

> [!NOTE]
> Você pode incluir propriedades ocultas adicionais no `data` objeto, se necessário.

| Propriedade | Descrição |
| --- | --- |
| `type` | Definir como `signin` . |
| `value` | De acordo com a URL para a qual você deseja redirecionar.  |

O código a seguir mostra um exemplo de Cartões Adaptáveis com `signin` ação:

```json
{
  "type": "Action.Submit",
  "title": "Click me for signin",
  "data": {
    "msteams": {
        "type": "signin",
        "value": "https://signin.com"
    }
  }
}
```

### <a name="adaptive-cards-with-invoke-action"></a>Cartões Adaptáveis com ação de invocação

Para incluir uma `invoke` ação com um Cartão Adaptável, inclua os seguintes detalhes no `msteams` objeto:

> [!NOTE]
> Você pode incluir propriedades ocultas adicionais no `data` objeto, se necessário.

| Propriedade | Descrição |
| --- | --- |
| `type` | Definir como `task/fetch` . |
| `data` | De definir o valor.  |

O código a seguir mostra um exemplo de Cartões Adaptáveis com `invoke` ação:

```json
{
  "type": "Action.Submit",
  "title": "submit"
  "data": {
    "msteams": {
        "type": "task/fetch"
    }
  }
}
```

O código a seguir mostra um exemplo de Cartões Adaptáveis com `invoke` ação com dados de carga adicionais:

```json
{
  "type": "Action.Submit",
  "title": "submit"
  "data": {
    "msteams": {
        "type": "task/fetch"
    },
    "Value1": "some value"
  }
}
```

## <a name="see-also"></a>Também consulte

[Referência de cartões](./cards-reference.md)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Ações Universais para Cartões Adaptáveis](../cards/Universal-actions-for-adaptive-cards/Overview.md)
