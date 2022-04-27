---
title: Exibições Específicas do Usuário
description: Saiba mais sobre exibições específicas do usuário usando ações universais com exemplo de código
author: surbhigupta12
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: b2e5b8d6dd00104fab819ba7d05d5913bb891d83
ms.sourcegitcommit: 3bfd0d2c4d83f306023adb45c8a3f829f7150b1d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65073677"
---
# <a name="user-specific-views"></a>Exibições Específicas do Usuário

Anteriormente, se os Cartões Adaptáveis fossem enviados em uma Teams, todos os usuários verão exatamente o mesmo conteúdo do cartão. Com a introdução do modelo de Ações Universais `refresh` e para Cartões Adaptáveis, os desenvolvedores de bot agora podem fornecer exibições específicas do usuário de Cartões Adaptáveis aos usuários. O mesmo Cartão Adaptável agora pode ser atualizado para um Cartão Adaptável Específico do Usuário. No máximo 60 usuários diferentes podem ver uma versão diferente do cartão com informações ou ações adicionais. O Cartão Adaptável fornece cenários avançados, como aprovações, controles de criador de sondagem, tíquetes, gerenciamento de incidentes e cartões de gerenciamento de projetos.

> [!NOTE]
> A Exibição Específica do Usuário tem suporte para Cartões Adaptáveis enviados por um bot e depende das Ações Universais.

Por exemplo, Megan, uma inspetora de segurança da Contoso, deseja criar um incidente e atribuí-lo a Alex. Megan também quer que todos da equipe sejam cientes do incidente. Sara usa a extensão de mensagem de relatório de incidentes da Contoso da plataforma Ações Universais para Cartões Adaptáveis.

# <a name="mobile"></a>[Dispositivo móvel](#tab/mobile)

:::image type="content" source="~/assets/images/adaptive-cards/mobile-universal-bots-incident-management.jpg" alt-text="Exibições específicas do usuário móvel" lightbox="../../../assets/images/adaptive-cards/mobile-universal-bots-incident-management.jpg":::

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-incident-management.png" alt-text="Exibições Específicas do Usuário" lightbox="../../../assets/images/adaptive-cards/universal-bots-incident-management.png":::

* * *

## <a name="user-specific-views-for-adaptive-cards"></a>Exibições específicas do usuário para cartões adaptáveis

O código a seguir fornece um exemplo de Cartões Adaptáveis:

```JSON
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "originator":"c9b4352b-a76b-43b9-88ff-80edddaa243b",
  "version": "1.4",
  "refresh": {
    "action": {
      "type": "Action.Execute",
      "title": "Refresh",
      "verb": "editOrResolveView",
      "data": {
            "refresh info": "<refresh info>"
      }
    },
    "userIds": ["<Megan's user MRI>", "<Alex's user MRI>"]
  },
  "body": [
    {
      "type": "TextBlock",
      "text": "Incident 1234"
    },
    {
      "type": "TextBlock",
      "text": "Incident details: <incident details>"
    }
  ]
}
```

Para enviar Cartões Adaptáveis, atualize exibições específicas do usuário e invoque solicitações para o bot:

1. Quando Sara cria um novo incidente, o bot envia o Cartão Adaptável ou o cartão comum com detalhes do incidente Teams conversa.
2. Agora, esse cartão é atualizado automaticamente para o Modo de Exibição Específico do Usuário para Sara e Alex. Os MRIs de usuário de Alex e Sara são `userIds` `refresh` adicionados na propriedade do JSON do Cartão Adaptável. O cartão permanece o mesmo para outros usuários na conversa.
3. Para Megan, a atualização automática dispara uma solicitação `adaptiveCard/action` de invocação para o bot. O bot pode retornar um cartão do criador de incidentes com `Edit` o botão como uma resposta a essa solicitação de invocação.
4. Da mesma forma para Alex, a atualização automática dispara outra solicitação `adaptiveCard/action` de invocação para o bot. O bot pode retornar um botão de cartão do proprietário do `Resolve` incidente como uma resposta a essa solicitação de invocação.

## <a name="invoke-request-sent-from-teams-client-to-the-bot"></a>Invocar a solicitação enviada Teams cliente para o bot

O código a seguir fornece um exemplo de uma solicitação de invocação enviada do cliente Teams Alex e Megan para o bot:

```JSON
{ 
  "type": "invoke",
  "name": "adaptiveCard/action",

  // ... other properties omitted for brevity

  "value": { 
    "action": { 
      "type": "Action.Execute", 
      "id": "", 
      "verb": "editOrResolveView",
      "data": { 
            "refresh info": "<refresh info>"
      } 
    },
    "trigger": "automatic" 
  }
}
```

## <a name="adaptivecardaction-invoke-response-card"></a>cartão de resposta adaptiveCard/action invoke

O código a seguir fornece um exemplo de um cartão de resposta de invocação adaptiveCard/action para Megan:

```JSON
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "originator":"c9b4352b-a76b-43b9-88ff-80edddaa243b",
  "version": "1.4",
  "refresh": {
    "action": {
      "type": "Action.Execute",
      "title": "Refresh",
      "verb": "editOrResolveView"
    },
    "userIds": ["<Megan's user MRI>", "<Alex's user MRI>"]
  },
  "body": [
    {
      "type": "TextBlock",
      "text": "Incident 1234"
    },
    {
      "type": "TextBlock",
      "text": "Incident details: <incident details>"
    }
  ],
  "actions": [
    {
      "type": "Action.Execute",
      "title": "Edit",
      "verb": "edit",
      "data": {
            "additional info": "<additional info>",
            ...
      }
    }
  ]
}
```

## <a name="adaptivecardaction-invoke-response-card-for-alex"></a>adaptiveCard/action invoke response card for Alex

O código a seguir fornece um exemplo de um cartão de resposta de invocação adaptiveCard/action para Alex:

```JSON
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "originator":"c9b4352b-a76b-43b9-88ff-80edddaa243b",
  "version": "1.4",
  "refresh": {
    "action": {
      "type": "Action.Execute",
      "title": "Refresh",
      "verb": "editOrResolveView"
    },
    "userIds": ["<Megan's user MRI>", "<Alex's user MRI>"]
  },
  "body": [
    {
      "type": "TextBlock",
      "text": "Incident 1234"
    },
    {
      "type": "TextBlock",
      "text": "Incident details: <incident details>"
    }
  ],
  "actions": [
    {
      "type": "Action.Execute",
      "title": "Resolve",
      "verb": "resolve",
      "data": {
            "additional info": "<additional info>",
            ...
      }
    }
  ]
}
```

## <a name="invoke-response-to-return-adaptive-cards"></a>Invocar resposta para retornar Cartões Adaptáveis

O código a seguir fornece um exemplo de uma resposta de invocação para retornar Cartões Adaptáveis:

### <a name="c"></a>[C#](#tab/C)

```csharp
string cardJson = "<adaptive card json>";
var card = JsonConvert.DeserializeObject(cardJson);

var adaptiveCardResponse = JObject.FromObject(new
 {
    statusCode = 200,
    type = "application/vnd.microsoft.adaptive.card",
    value = card
 });
```

### <a name="nodejs"></a>[Node.js](#tab/nodejs)

```javascript
var card = "<adaptive card json>";
 
const cardRes = {
        statusCode: 200,
        type: 'application/vnd.microsoft.card.adaptive',
        value: card
    };
    const res = {
        status: 200,
        body: cardRes
    };
    return res;

```

***

Diretrizes de design de cartão para ter em mente durante a criação de exibições específicas do usuário:

* Você pode criar no máximo **60** Exibições Específicas do Usuário para um cartão específico enviado para um chat `userIds` ou canal especificando-os na `refresh` seção.
* **Cartão Base:** A versão base do cartão que o desenvolvedor do bot envia para o chat. A versão base é a versão do Cartão Adaptável para todos os usuários que não estão especificados na `userIds` seção.
* Uma atualização de mensagem pode ser usada para atualizar o cartão base e atualizar simultaneamente o Cartão Específico do Usuário. Abrir o chat ou canal também atualiza o cartão para usuários com a atualização habilitada.
* Para cenários com grupos maiores em que os usuários alternam para um modo de exibição em ação, que precisa de atualizações dinâmicas para respondentes, você pode continuar adicionando até 60 usuários à `userIds` lista. Você pode remover o primeiro respondente da lista quando o 61º usuário responder. Para os usuários removidos `userIds` da lista, você pode fornecer um botão de atualização manual ou usar o botão atualizar no menu de opções de mensagem para obter o resultado mais recente.
* Forneça um prompt aos usuários para obter uma Exibição Específica do Usuário, em que eles veem apenas uma exibição específica do cartão ou algumas ações.

## <a name="code-sample"></a>Exemplo de código

|Nome do exemplo | Descrição | .NETCore | Node.js |
|----------------|-----------------|--------------|--------------|
| Cartões adaptáveis de fluxos de trabalho sequenciais | Demonstrar como implementar fluxos de trabalho sequenciais, exibições específicas do usuário e cartões adaptáveis atualizados em bots. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-sequential-flow-adaptive-cards/csharp) | [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-sequential-flow-adaptive-cards/nodejs) |

## <a name="see-also"></a>Confira também

* [Trabalhar com Ações Universais para Cartões Adaptáveis](Work-with-universal-actions-for-adaptive-cards.md)
* [Modos de exibição atualizados](Up-To-Date-Views.md)
* [Comentários de preenchimento do formulário](~/bots/how-to/conversations/conversation-messages.md#form-completion-feedback)
