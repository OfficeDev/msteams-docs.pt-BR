---
title: Adicionar ações de cartão em um bot
description: Neste módulo, saiba o que são ações de cartão no Microsoft Teams, tipos de ação e como usá-las em seus bots
ms.localizationpriority: medium
ms.topic: conceptual
ms.openlocfilehash: 77f2631ae55f5794567d83233e1311d935cefabc
ms.sourcegitcommit: c3601696cced9aadc764f1e734646ee7711f154c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2022
ms.locfileid: "68833174"
---
# <a name="card-actions"></a>Ações do cartão

Os cartões usados por bots e extensões de mensagem no Teams são compatíveis com os seguintes tipos de atividade [`CardAction`](/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments#process-events-within-rich-cards):

> [!NOTE]
> As ações `CardAction` são diferentes das `potentialActions` para Cartões conectores do Office 365 quando usadas de conectores.

| Digitar | Ação |
| --- | --- |
| `openUrl` | Abre uma URL no navegador padrão. |
| `messageBack` | Envia uma mensagem e conteúdo para o bot do usuário que selecionou o botão ou tocou no cartão. Envia uma mensagem separada para o fluxo de chat. |
| `imBack`| Envia uma mensagem para o bot do usuário que selecionou o botão ou tocou no cartão. Essa mensagem do usuário para o bot é visível para todos os participantes da conversa. |
| `invoke` | Envia uma mensagem e conteúdo para o bot do usuário que selecionou o botão ou tocou no cartão. Essa mensagem não está visível. |
| `signin` | Inicia o fluxo OAuth, permitindo que os bots se conectem com serviços seguros. |

> [!NOTE]
>
>* O Teams não dá suporte aos tipos `CardAction` não listados na tabela anterior.
>* O Teams não dá suporte à propriedade `potentialActions`.
>* As ações de cartão são diferentes das [ações sugeridas](/azure/bot-service/bot-builder-howto-add-suggested-actions?view=azure-bot-service-4.0&tabs=javascript#suggest-action-using-button&preserve-view=true) no Bot Framework ou Serviço de Bot do Azure.
>* Se você estiver usando uma ação de cartão como parte de uma extensão de mensagem, as ações não funcionarão até que o cartão seja enviado ao canal. As ações não funcionam enquanto o cartão está na caixa de mensagem de redação.

## <a name="action-type-openurl"></a>Tipo de ação openUrl

O tipo de ação `openUrl` especifica uma URL a ser iniciada no navegador padrão.

> [!NOTE]
>
> * O bot não recebe nenhum aviso em qual botão foi selecionado.
> * Não há suporte para nomes de máquina com números na URL.

Com `openUrl`, você pode criar uma ação com as seguintes propriedades:

| Propriedade | Descrição |
| --- | --- |
| `title` | Aparece como o rótulo do botão. |
| `value` | Esse campo deve conter uma URL completa e corretamente formada. |

# <a name="json"></a>[JSON](#tab/json)

O código a seguir mostra um exemplo do tipo de ação `openUrl` em JSON:

```json
{
    "type": "openUrl",
    "title": "Tabs in Teams",
    "value": "https://msdn.microsoft.com/microsoft-teams/tabs"
}
```

# <a name="c"></a>[C#](#tab/csharp)

O código a seguir mostra um exemplo do tipo de ação `openUrl` tipo em C#:

```csharp
var button = new CardAction()
{
    Type = ActionTypes.OpenUrl,
    Title = "Tabs in Teams",
    Value = "https://learn.microsoft.com/microsoftteams/platform/"
};
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

O código a seguir mostra um exemplo do tipo de ação `openUrl`em JavaScript:

```javascript
CardFactory.actions([
{
    type: 'openUrl',
    title: 'Tabs in Teams',
    value: 'https://learn.microsoft.com/microsoftteams/platform/'
}])
```

---

## <a name="action-type-messageback"></a>Tipo de ação messageBack

Com `messageBack`, você pode criar uma ação totalmente personalizada com as seguintes propriedades:

| Propriedade | Descrição |
| --- | --- |
| `title` | Aparece como o rótulo do botão. |
| `displayText` | Opcional. Usado pelo usuário no fluxo de chat quando a ação é executada. Este texto não é enviado para o bot. |
| `value` | Enviado ao bot quando a ação é executada. Você pode codificar o contexto para a ação, como identificadores exclusivos ou um objeto JSON. |
| `text` | Enviado ao bot quando a ação é executada. Use essa propriedade para simplificar o desenvolvimento de bots. Seu código pode verificar uma única propriedade de nível superior para expedir a lógica do bot. |

A flexibilidade de `messageBack` significa que seu código não pode deixar uma mensagem de usuário visível no histórico simplesmente por não usar `displayText`.

# <a name="json"></a>[JSON](#tab/json)

O código a seguir mostra um exemplo do tipo de ação `messageBack` em JSON:

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

A propriedade `value` pode ser uma cadeia de caracteres JSON serializada ou um objeto JSON.

# <a name="c"></a>[C#](#tab/csharp)

O código a seguir mostra um exemplo do tipo de ação `messageBack` tipo em C#:

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

O código a seguir mostra um exemplo do tipo de ação `messageBack`em JavaScript:

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

`replyToId` contém a ID da mensagem de origem da ação do cartão. Use-o se quiser atualizar a mensagem.

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

A ação `imBack` aciona uma mensagem de retorno para o bot, como se o usuário a tivesse digitado em uma mensagem de chat normal. O usuário e todos os outros usuários em um canal podem ver a resposta do botão.

Com `imBack`, você pode criar uma ação com as seguintes propriedades:

| Propriedade | Descrição |
| --- | --- |
| `title` | Aparece como o rótulo do botão. |
| `value` | Esse campo deve conter a cadeia de caracteres de texto usada no chat e, portanto, enviada de volta para o bot. Esse é o texto da mensagem que você processa no bot para executar a lógica desejada. |

> [!NOTE]
> O campo `value` é uma cadeia de caracteres simples. Não há suporte para formatação ou caracteres ocultos.

# <a name="json"></a>[JSON](#tab/json)

O código a seguir mostra um exemplo do tipo de ação `imBack` em JSON:

```json
{
    "type": "imBack",
    "title": "More",
    "value": "Show me more"
}
```

# <a name="c"></a>[C#](#tab/csharp)

O código a seguir mostra um exemplo do tipo de ação `imBack` tipo em C#:

```csharp
var button = new CardAction()
{
    Type = ActionTypes.ImBack,
    Title = "More",
    Value = "Show me more"
};
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

O código a seguir mostra um exemplo do tipo de ação `imBack`em JavaScript:

```javascript
CardFactory.actions([
{
    type: "imBack",
    title: "More",
    value: "Show me more"
}])
```

---

## <a name="action-type-invoke"></a>Invocação de tipo de ação

A ação `invoke` é usada para invocar [módulos de tarefa](~/task-modules-and-cards/task-modules/task-modules-bots.md).

A ação `invoke` contém três propriedades, `type`, `title`e `value`.

Com `invoke`, você pode criar uma ação com as seguintes propriedades:

| Propriedade | Descrição |
| --- | --- |
| `title` | Aparece como o rótulo do botão. |
| `value` | Essa propriedade pode conter uma cadeia de caracteres, um objeto JSON com cadeia de caracteres ou um objeto JSON. |

# <a name="json"></a>[JSON](#tab/json)

O código a seguir mostra um exemplo do tipo de ação `invoke`em JSON:

```json
{
    "type": "invoke",
    "title": "Option 1",
    "value": {
        "option": "opt1"
    }
}
```

Quando um usuário seleciona o botão, o bot recebe o objeto `value` com algumas informações adicionais.

> [!NOTE]
> O tipo de atividade é `invoke` em vez de `message` que é `activity.Type == "invoke"`.

# <a name="c"></a>[C#](#tab/csharp)

O código a seguir mostra um exemplo do tipo de ação `invoke` tipo em C#:

```csharp
var button = new CardAction()
{
    Title = "Option 1",
    Type = "invoke",
    Value = "{\"option\": \"opt1\"}"
};
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

O código a seguir mostra um exemplo do tipo de ação `invoke`no Node.js:

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

A propriedade de nível superior `replyToId` contém a ID da mensagem de origem da ação do cartão. Use-o se quiser atualizar a mensagem.

O código a seguir mostra um exemplo de mensagem de invocação de entrada:

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

## <a name="action-type-signin"></a>Entrada de tipo de ação

O tipo de ação `signin` inicia um fluxo OAuth que permite que os bots se conectem com serviços seguros. Para obter mais informações, consulte [fluxos de autenticação em bots](~/bots/how-to/authentication/auth-flow-bot.md).

O Teams também dá suporte a [Ações de Cartões Adaptáveis](#adaptive-cards-actions) que são usadas apenas por Cartões Adaptáveis.

# <a name="json"></a>[JSON](#tab/json)

O código a seguir mostra um exemplo do tipo de ação `signin` em JSON:

```json
{
"type": "signin",
"title": "Click me for signin",
"value": "https://signin.com"
}
```

# <a name="c"></a>[C#](#tab/csharp)

O código a seguir mostra um exemplo do tipo de ação `signin` tipo em C#:

```csharp
var button = new CardAction()
{
    Type = ActionTypes.Signin,
    Title = "Click me for signin",
    Value = "https://signin.com"
};
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

O código a seguir mostra um exemplo do tipo de ação `signin` em JavaScript:

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

Os Cartões Adaptáveis dão suporte a quatro tipos de ação:

* [Action.OpenUrl](http://adaptivecards.io/explorer/Action.OpenUrl.html)
* [Action.Submit](http://adaptivecards.io/explorer/Action.Submit.html)
* [Action.ShowCard](http://adaptivecards.io/explorer/Action.ShowCard.html)
* [Action.Execute](/adaptive-cards/authoring-cards/universal-action-model#actionexecute)

Você também pode modificar a carga do Cartão Adaptável `Action.Submit` para dar suporte a ações de Bot Framework existentes usando uma propriedade `msteams` no objeto `data` de `Action.Submit`. A próxima seção fornece detalhes sobre como usar ações existentes do Bot Framework com Cartões Adaptáveis.

> [!NOTE]
>* Adicionar `msteams` a dados com uma Bot Framework não funciona com um módulo de tarefa de Cartão Adaptável.
> 
>* Não há suporte para primário ou desctutivo `ActionStyle` no Microsoft Teams. 

### <a name="adaptive-cards-with-messageback-action"></a>Cartões Adaptáveis com a ação messageBack

Para incluir uma ação`messageBack` com um Cartão Adaptável, inclua os seguintes detalhes no objeto `msteams`:

> [!NOTE]
> Você pode incluir propriedades ocultas adicionais no objeto `data`, se necessário.

| Propriedade | Descrição |
| --- | --- |
| `type` | Definido como `messageBack` |
| `displayText` | Opcional. Usado pelo usuário no fluxo de chat quando a ação é executada. Este texto não é enviado para o bot. |
| `value` | Enviado ao bot quando a ação é executada. Você pode codificar o contexto para a ação, como identificadores exclusivos ou um objeto JSON. |
| `text` | Enviado ao bot quando a ação é executada. Use essa propriedade para simplificar o desenvolvimento de bots. Seu código pode verificar uma única propriedade de nível superior para expedir a lógica do bot. |

O código a seguir mostra um exemplo de Cartões Adaptáveis com a ação `messageBack`:

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

### <a name="adaptive-cards-with-imback-action"></a>Cartões Adaptáveis com a ação imBack

Para incluir uma ação `imBack` com um Cartão Adaptável, inclua os seguintes detalhes no objeto`msteams`:

> [!NOTE]
> Você pode incluir propriedades ocultas adicionais no objeto `data`, se necessário.

| Propriedade | Descrição |
| --- | --- |
| `type` | Definido como `imBack` |
| `value` | Cadeia de caracteres que precisa ser ecoada novamente no chat. |

O código a seguir mostra um exemplo de Cartões Adaptáveis com a ação `imBack`:

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

### <a name="adaptive-cards-with-signin-action"></a>Cartões Adaptáveis com a ação de entrada

Para incluir uma ação `signin` com um Cartão Adaptável, inclua os seguintes detalhes no objeto `msteams`:

> [!NOTE]
> Você pode incluir propriedades ocultas adicionais no objeto `data`, se necessário.

| Propriedade | Descrição |
| --- | --- |
| `type` | Definido como `signin`. |
| `value` | Defina como a URL para a qual você deseja redirecionar.  |

O código a seguir mostra um exemplo de Cartões Adaptáveis com ação `signin`:

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

### <a name="adaptive-cards-with-invoke-action"></a>Cartões Adaptáveis com a ação de invocação

Para incluir uma ação `invoke` com um Cartão Adaptável, inclua os seguintes detalhes no objeto `msteams`:

> [!NOTE]
> Você pode incluir propriedades ocultas adicionais no objeto `data`, se necessário.

| Propriedade | Descrição |
| --- | --- |
| `type` | Definido como `task/fetch`. |
| `data` | Defina o valor.  |

O código a seguir mostra um exemplo de Cartões Adaptáveis com a ação `invoke`:

```json
{
  "type": "Action.Submit",
  "title": "submit",
  "data": {
    "msteams": {
        "type": "task/fetch"
    }
  }
}
```

O código a seguir mostra um exemplo de Cartões Adaptáveis com a ação `invoke` com dados de conteúdo adicionais:

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

## <a name="code-samples"></a>Exemplos de código

|S.no|Cartão| description|.NET|JavaScript|Python|Java|
|:--|:--|:--------------------------------------------------------|-----|------------|-----|----------------------------|
|1|Usando cartões|Apresenta todos os tipos de cartão, incluindo miniatura, áudio, mídia etc. Baseia-se em Receber usuário + bot de vários prompts apresentando um cartão com botões na mensagem de boas-vindas que roteiam para a caixa de diálogo apropriada.|[View](https://github.com/microsoft/BotBuilder-Samples/blob/main/samples/csharp_dotnetcore/06.using-cards)|[View](https://github.com/microsoft/BotBuilder-Samples/blob/main/samples/javascript_nodejs/06.using-cards)|[View](https://github.com/microsoft/BotBuilder-Samples/blob/main/samples/python/06.using-cards)|[Exibir](https://github.com/microsoft/BotBuilder-Samples/blob/main/samples/java_springboot/06.using-cards)|
|2|Cartões adaptáveis|Demonstra como a caixa de diálogo de várias voltas pode usar um cartão para obter a entrada do usuário para nome e idade.|[View](https://github.com/microsoft/BotBuilder-Samples/blob/main/samples/csharp_dotnetcore/07.using-adaptive-cards)|[View](https://github.com/microsoft/BotBuilder-Samples/blob/main/samples/javascript_nodejs/07.using-adaptive-cards)|[View](https://github.com/microsoft/BotBuilder-Samples/blob/main/samples/python/07.using-adaptive-cards)|[Exibir](https://github.com/microsoft/BotBuilder-Samples/blob/main/samples/java_springboot/07.using-adaptive-cards)|

> [!NOTE]
> Não há suporte para elementos de mídia para cartão adaptável no Teams

## <a name="next-step"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Ações Universais para Cartões Adaptáveis](../cards/Universal-actions-for-adaptive-cards/Overview.md)

## <a name="see-also"></a>Confira também

* [Referência de cartões](./cards-reference.md)
* [Usar módulos de tarefas dos bots](~/task-modules-and-cards/task-modules/task-modules-bots.md)
* [Cartões adaptáveis nos bots](../../bots/how-to/conversations/conversation-messages.md#adaptive-cards)
* [Ações Universais para Cartões Adaptáveis](~/task-modules-and-cards/cards/universal-actions-for-adaptive-cards/overview.md)
* [Comentários de preenchimento do formulário](~/bots/how-to/conversations/conversation-messages.md#form-completion-feedback)
