---
title: Adicionar ações de cartão em um bot
description: Descreve as ações do cartão no Microsoft Teams e como usá-las em seus bots
keywords: ações de cartões de bots da equipe
ms.openlocfilehash: 2bee1072405d91cd29d1aa227884516a87d10bde
ms.sourcegitcommit: b9771f8f4be9ac1ff8c85c2d7bd8d5c5408bc653
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/06/2021
ms.locfileid: "49768071"
---
# <a name="card-actions"></a>Ações de cartão

Os cartões usados por bots e extensões de mensagens no Microsoft Teams dão suporte aos seguintes tipos de atividade ( [`CardAction`](/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments#process-events-within-rich-cards) ). Observe que essas ações diferem de `potentialActions` cartões conectores do Office 365 quando usadas de conectores.

| Tipo | Action |
| --- | --- |
| `openUrl` | Abre uma URL no navegador padrão. |
| `messageBack` | Envia uma mensagem e uma carga para o bot (do usuário que clicou no botão ou tocou no cartão) e envia uma mensagem separada para o fluxo de chat. |
| `imBack`| Envia uma mensagem para o bot (do usuário que clicou no botão ou tocou no cartão). Esta mensagem (de usuário para bot) fica visível para todos os participantes da conversa. |
| `invoke` | Envia uma mensagem e uma carga para o bot (do usuário que clicou no botão ou tocou no cartão). Esta mensagem não está visível. |
| `signin` | Inicia o fluxo do OAuth, permitindo que os bots se conectem com serviços seguros. |

> [!NOTE]
>* O Microsoft Teams não dá suporte `CardAction` a tipos não listados na tabela anterior.
>* O Microsoft Teams não oferece suporte à `potentialActions` propriedade.
>* As ações do cartão são diferentes das [ações sugeridas](/azure/bot-service/bot-builder-howto-add-suggested-actions?view=azure-bot-service-4.0&tabs=javascript#suggest-action-using-button&preserve-view=true) no serviço bot Framework/Azure bot. As ações sugeridas não são suportadas no Microsoft Teams: se você deseja que os botões apareçam em uma mensagem do bot do Teams, use um cartão.
>* Se você estiver usando uma ação de cartão como parte de uma extensão de mensagens, as ações não funcionarão até que o cartão seja enviado para o canal (eles não funcionarão enquanto o cartão estiver na caixa de mensagem de composição).

O Microsoft Teams também oferece suporte a [ações de cartões adaptáveis](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions), que são usados apenas por cartões adaptáveis. Essas ações estão listadas em suas próprias seções no final desta referência.

## <a name="openurl"></a>openUrl

Este tipo de ação especifica uma URL a ser iniciada no navegador padrão. Observe que seu bot não recebe qualquer aviso em que botão foi clicado.

O `value` campo deve conter uma URL completa e corretamente formada.

```json
{
    "type": "openUrl",
    "title": "Tabs in Teams",
    "value": "https://msdn.microsoft.com/microsoft-teams/tabs"
}
```

## <a name="messageback"></a>messageBack

Com `messageBack` o, você pode criar uma ação totalmente personalizada com as seguintes propriedades:

| Propriedade | Descrição |
| --- | --- |
| `title` | Aparece como o rótulo do botão. |
| `displayText` | Opcional. Ecoado pelo usuário para o fluxo de chat quando a ação é executada. Este texto *não* é enviado ao bot. |
| `value` | Enviado ao bot quando a ação é executada. Você pode codificar o contexto da ação, como identificadores exclusivos ou um objeto JSON. |
| `text` | Enviado ao bot quando a ação é executada. Use esta propriedade para simplificar o desenvolvimento de bot: seu código pode verificar uma única propriedade de nível superior para a lógica de bot de expedição. |

A flexibilidade do `messageBack` significa que o código pode optar por não deixar uma mensagem de usuário visível no histórico simplesmente não usando `displayText` .

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

### <a name="inbound-message-example"></a>Exemplo de mensagem de entrada

`replyToId` contém a ID da mensagem da qual a ação do cartão veio. Use-o se você quiser atualizar a mensagem.

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

## <a name="imback"></a>Failback

Esta ação dispara uma mensagem de retorno ao bot, como se o usuário a tivesse digitado em uma mensagem de chat normal. O usuário e todos os outros usuários se estiverem em um canal, verá essa resposta de botão.

O `value` campo deve conter a cadeia de caracteres de texto ecoada no chat e, portanto, enviada de volta para o bot. Este é o texto da mensagem que será processado no bot para executar a lógica desejada. Observação: Este campo é uma cadeia de caracteres simples – não há suporte para formatação ou caracteres ocultos.

```json
{
    "type": "imBack",
    "title": "More",
    "value": "Show me more"
}
```

## <a name="invoke"></a>Ative

A `invoke` ação é usada para invocar [módulos de tarefa](~/task-modules-and-cards/task-modules/task-modules-bots.md).

A `invoke` ação contém três propriedades: `type` , `title` e `value` . A `value` propriedade pode conter uma cadeia de caracteres, um objeto JSON em formato ou um objeto JSON.

```json
{
    "type": "invoke",
    "title": "Option 1",
    "value": {
        "option": "opt1"
    }
}
```

Quando um usuário clica no botão, seu bot receberá o `value` objeto com algumas informações adicionais. Observe que o tipo de atividade será `invoke` em vez de `message` ( `activity.Type == "invoke"` ).

### <a name="example-invoke-button-definition-net"></a>Exemplo: chamar definição de botão (.NET)

```csharp
var button = new CardAction()
{
    Title = "Option 1",
    Type = "invoke",
    Value = "{\"option\": \"opt1\"}"
};
```

### <a name="example-incoming-invoke-message"></a>Exemplo: mensagem de invocação de entrada

A propriedade de nível superior `replyToId` contém a ID da mensagem da qual a ação do cartão veio. Use-o se você quiser atualizar a mensagem.

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

## <a name="signin"></a>SignIn

Inicia um fluxo OAuth, permitindo que os bots se conectem com serviços seguros, conforme descrito em mais detalhes aqui: [fluxo de autenticação em bots](~/bots/how-to/authentication/auth-flow-bot.md).

## <a name="adaptive-cards-actions"></a>Ações de cartões adaptáveis

Os cartões adaptáveis dão suporte a três tipos de ação:

* [Ação. OpenUrl](http://adaptivecards.io/explorer/Action.OpenUrl.html)
* [Action.Submit](http://adaptivecards.io/explorer/Action.Submit.html)
* [Cartão Action.](http://adaptivecards.io/explorer/Action.ShowCard.html)

Além das ações mencionadas acima, você pode modificar a carga de cartão adaptável `Action.Submit` para dar suporte a ações da estrutura de bot existentes usando uma `msteams` propriedade no `data` objeto of `Action.Submit` . As seções abaixo detalham como usar ações da estrutura de bot existentes com cartões adaptáveis.

> [!NOTE]
> Adicionar `msteams` a dados, com uma ação de estrutura de bot, não funciona com um módulo de tarefa de cartão adaptável.

### <a name="adaptive-cards-with-messageback-action"></a>Cartões adaptáveis com ação messageBack

Para incluir uma `messageBack` ação com um cartão adaptável, inclua os seguintes detalhes no `msteams` objeto. Observe que você pode incluir propriedades ocultas adicionais no `data` objeto, se necessário.

| Propriedade | Descrição |
| --- | --- |
| `type` | Definido como `messageBack` |
| `displayText` | Opcional. Ecoado pelo usuário para o fluxo de chat quando a ação é executada. Este texto *não* é enviado ao bot. |
| `value` | Enviado ao bot quando a ação é executada. Você pode codificar o contexto da ação, como identificadores exclusivos ou um objeto JSON. |
| `text` | Enviado ao bot quando a ação é executada. Use esta propriedade para simplificar o desenvolvimento de bot: seu código pode verificar uma única propriedade de nível superior para a lógica de bot de expedição. |

#### <a name="example"></a>Exemplo

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

### <a name="adaptive-cards-with-imback-action"></a>Cartões adaptáveis com ação de inversão

Para incluir uma `imBack` ação com um cartão adaptável, inclua os seguintes detalhes no `msteams` objeto. Observe que você pode incluir propriedades ocultas adicionais no `data` objeto, se necessário.

| Propriedade | Descrição |
| --- | --- |
| `type` | Definido como `imBack` |
| `value` | Cadeia de caracteres que precisa ser ecoada de volta no chat |

#### <a name="example"></a>Exemplo

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

### <a name="adaptive-cards-with-signin-action"></a>Cartões adaptáveis com ação de entrada

Para incluir uma `signin` ação com um cartão adaptável, inclua os seguintes detalhes no `msteams` objeto. Observe que você pode incluir propriedades ocultas adicionais no `data` objeto, se necessário.

| Propriedade | Descrição |
| --- | --- |
| `type` | Definido como `signin` |
| `value` | Defina como a URL para a qual você deseja redirecionar  |

#### <a name="example"></a>Exemplo

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

### <a name="adaptive-cards-with-invoke-action"></a>Cartões adaptáveis com ação chamar
 
Para incluir uma `invoke` ação com um cartão adaptável, inclua os seguintes detalhes no `msteams` objeto. Observe que você pode incluir propriedades ocultas adicionais no `data` objeto, se necessário.

| Propriedade | Descrição |
| --- | --- |
| `type` | Definido como `task/fetch` |
| `data` | Definir o valor  |

#### <a name="example"></a>Exemplo

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

#### <a name="example-2-with-additional-payload-data"></a>Exemplo 2 (com dados de conteúdo adicional)

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
