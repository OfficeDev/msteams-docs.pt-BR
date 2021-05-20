---
title: Adicionar ações de cartão em um bot
description: Descreve ações de cartão em Microsoft Teams e como usá-las em seus bots
localization_priority: Normal
ms.topic: conceptual
keywords: equipes bots ações cartões
ms.openlocfilehash: b9276c7197070df43ba447707e6fa4d3d4098591
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566849"
---
# <a name="card-actions"></a>Ações de cartão

Cartões usados por bots e extensões de mensagens em Teams suportam os [`CardAction`](/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments#process-events-within-rich-cards) seguintes tipos de atividade () . Observe que essas ações diferem de `potentialActions` Office 365 cartões Connector quando usadas a partir de Conectores.

| Tipo | Action |
| --- | --- |
| `openUrl` | Abre uma URL no navegador padrão. |
| `messageBack` | Envia uma mensagem e carga para o bot do usuário que clicou no botão ou tocou no cartão e envia uma mensagem separada para o fluxo de bate-papo. |
| `imBack`| Envia uma mensagem para o bot do usuário que clicou no botão ou tocou no cartão. Esta mensagem (de usuário para bot) é visível para todos os participantes da conversa. |
| `invoke` | Envia uma mensagem e carga para o bot do usuário que clicou no botão ou tocou no cartão. Esta mensagem não é visível. |
| `signin` | Inicia o fluxo OAuth, permitindo que os bots se conectem com serviços seguros. |

> [!NOTE]
>* Teams não suporta `CardAction` tipos não listados na tabela anterior.
>* Teams não suporta a `potentialActions` propriedade.
>* As ações do cartão são diferentes das [ações sugeridas](/azure/bot-service/bot-builder-howto-add-suggested-actions?view=azure-bot-service-4.0&tabs=javascript#suggest-action-using-button&preserve-view=true) no Bot Framework/Azure Bot Service. As ações sugeridas não são suportadas em Microsoft Teams: se você quiser que os botões apareçam em uma mensagem de bot Teams, use um cartão.
>* Se você estiver usando uma ação de cartão como parte de uma extensão de mensagens, as ações não funcionam até que a carteira seja enviada ao canal. Eles não funcionam enquanto o cartão está na caixa de mensagens de composição.

Teams também suporta [ações de Cartões Adaptativos,](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions)que são usadas apenas por Cartões Adaptativos. Essas ações estão listadas em sua própria seção no final desta referência.

## <a name="openurl"></a>openUrl

Esse tipo de ação especifica uma URL para ser lançada no navegador padrão. Observe que seu bot não recebe nenhum aviso sobre qual botão foi clicado.

O `value` campo deve conter uma URL completa e devidamente formada.

```json
{
    "type": "openUrl",
    "title": "Tabs in Teams",
    "value": "https://msdn.microsoft.com/microsoft-teams/tabs"
}
```

## <a name="messageback"></a>mensagemBack

Com `messageBack` , você pode criar uma ação totalmente personalizada com as seguintes propriedades:

| Propriedade | Descrição |
| --- | --- |
| `title` | Aparece como a etiqueta do botão. |
| `displayText` | Opcional. Ecoado pelo usuário no fluxo de bate-papo quando a ação é realizada. Este texto *não* é enviado para o seu bot. |
| `value` | Enviado para o seu bot quando a ação é realizada. Você pode codificar o contexto da ação, como identificadores exclusivos ou um objeto JSON. |
| `text` | Enviado para o seu bot quando a ação é realizada. Use esta propriedade para simplificar o desenvolvimento de bots: seu código pode verificar uma única propriedade de alto nível para despachar a lógica do bot. |

A flexibilidade de `messageBack` meios que seu código pode optar por não deixar uma mensagem de usuário visível no histórico simplesmente não usando `displayText` .

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

A `value` propriedade pode ser uma sequência JSON serializada ou um objeto JSON.

### <a name="inbound-message-example"></a>Exemplo de mensagem de entrada

`replyToId` contém a identificação da mensagem de onde veio a ação do cartão. Use-o se quiser atualizar a mensagem.

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

## <a name="imback"></a>imBack

Essa ação aciona uma mensagem de retorno ao seu bot, como se o usuário digitasse em uma mensagem de chat normal. Seu usuário, e todos os outros usuários se em um canal, verão essa resposta ao botão.

O `value` campo deve conter a sequência de texto ecoada no chat e, portanto, enviada de volta para o bot. Este é o texto de mensagem que você processará em seu bot para executar a lógica desejada. Nota: este campo é uma sequência simples - não há suporte para formatação ou caracteres ocultos.

```json
{
    "type": "imBack",
    "title": "More",
    "value": "Show me more"
}
```

## <a name="invoke"></a>invocar

A `invoke` ação é usada para invocar [módulos de tarefas.](~/task-modules-and-cards/task-modules/task-modules-bots.md)

A `invoke` ação contém três propriedades: `type` , , e `title` `value` . A `value` propriedade pode conter uma sequência, um objeto JSON stringified ou um objeto JSON.

```json
{
    "type": "invoke",
    "title": "Option 1",
    "value": {
        "option": "opt1"
    }
}
```

Quando um usuário clica no botão, o bot receberá o `value` objeto com algumas informações adicionais. Por favor, note que o tipo de atividade será `invoke` em vez de ( `message` `activity.Type == "invoke"` .

### <a name="example-invoke-button-definition-net"></a>Exemplo: Invocar definição de botão (.NET)

```csharp
var button = new CardAction()
{
    Title = "Option 1",
    Type = "invoke",
    Value = "{\"option\": \"opt1\"}"
};
```

### <a name="example-incoming-invoke-message"></a>Exemplo: Mensagem de invocação recebida

A propriedade de alto nível `replyToId` contém a identificação da mensagem de onde a ação do cartão veio. Use-o se quiser atualizar a mensagem.

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

## <a name="signin"></a>signin

Inicia um fluxo OAuth, permitindo que os bots se conectem com serviços seguros, conforme descrito em mais detalhes aqui: [Fluxo de autenticação em bots](~/bots/how-to/authentication/auth-flow-bot.md).

## <a name="adaptive-cards-actions"></a>Ações de Cartões Adaptativos

Cartões adaptativos suportam quatro tipos de ação:

* [Action.OpenUrl](http://adaptivecards.io/explorer/Action.OpenUrl.html)
* [Action.Submit](http://adaptivecards.io/explorer/Action.Submit.html)
* [Action.ShowCard](http://adaptivecards.io/explorer/Action.ShowCard.html)
* [Action.Exefofo](/adaptive-cards/authoring-cards/universal-action-model#actionexecute)

Além das ações mencionadas acima, você pode modificar a carga de cartão adaptável `Action.Submit` para apoiar as ações existentes do Bot Framework usando uma propriedade no objeto de `msteams` `data` `Action.Submit` . As seções abaixo detalham como usar as ações existentes do Bot Framework com cartões adaptativos.

> [!NOTE]
> Adicionar `msteams` dados, com uma ação do Bot Framework, não funciona com um módulo de tarefa de cartão adaptável.

### <a name="adaptive-cards-with-messageback-action"></a>Cartões adaptativos com ação messageBack

Para incluir uma `messageBack` ação com uma placa adaptativa inclua os seguintes detalhes no `msteams` objeto. Observe que você pode incluir propriedades ocultas adicionais no `data` objeto, se necessário.

| Propriedade | Descrição |
| --- | --- |
| `type` | Definido para `messageBack` |
| `displayText` | Opcional. Ecoado pelo usuário no fluxo de bate-papo quando a ação é realizada. Este texto *não* é enviado para o seu bot. |
| `value` | Enviado para o seu bot quando a ação é realizada. Você pode codificar o contexto da ação, como identificadores exclusivos ou um objeto JSON. |
| `text` | Enviado para o seu bot quando a ação é realizada. Use esta propriedade para simplificar o desenvolvimento de bots: seu código pode verificar uma única propriedade de alto nível para despachar a lógica do bot. |

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

### <a name="adaptive-cards-with-imback-action"></a>Cartões adaptativos com ação imBack

Para incluir uma `imBack` ação com uma placa adaptativa inclua os seguintes detalhes no `msteams` objeto. Observe que você pode incluir propriedades ocultas adicionais no `data` objeto, se necessário.

| Propriedade | Descrição |
| --- | --- |
| `type` | Definido para `imBack` |
| `value` | String que precisa ser ecoado de volta no bate-papo |

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

### <a name="adaptive-cards-with-signin-action"></a>Cartões Adaptativos com ação signin

Para incluir uma `signin` ação com uma placa adaptativa inclua os seguintes detalhes no `msteams` objeto. Observe que você pode incluir propriedades ocultas adicionais no `data` objeto, se necessário.

| Propriedade | Descrição |
| --- | --- |
| `type` | Pronto para `signin` . |
| `value` | Defina para a URL para a que você deseja redirecionar.  |

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

### <a name="adaptive-cards-with-invoke-action"></a>Cartões Adaptativos com ação de invocação
 
Para incluir uma `invoke` ação com uma placa adaptativa inclua os seguintes detalhes no `msteams` objeto. Observe que você pode incluir propriedades ocultas adicionais no `data` objeto, se necessário.

| Propriedade | Descrição |
| --- | --- |
| `type` | Definido para `task/fetch` |
| `data` | Defina o valor  |

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

#### <a name="example-2-with-additional-payload-data"></a>Exemplo 2 (com dados adicionais de carga)

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
