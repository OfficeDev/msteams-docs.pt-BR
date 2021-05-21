---
title: Exibições Específicas do Usuário
description: Exemplo de exibições específicas do usuário usando ações universais
author: surbhigupta12
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: 696fc5ce25c79d749b301309bfe0c737e39ad294
ms.sourcegitcommit: 9ef3b415cbba484c2201abe9c6927e08d974388e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52555441"
---
# <a name="user-specific-views"></a>Exibições Específicas do Usuário

Anteriormente, se cartões adaptáveis foram enviados em uma conversa Teams, todos os usuários verão exatamente o mesmo conteúdo do cartão. Com a introdução do modelo de Ações Universais e para Cartões Adaptáveis, os desenvolvedores de bot agora podem fornecer exibições específicas do usuário de cartões `refresh` adaptáveis aos usuários. O mesmo Cartão Adaptável agora pode atualizar para um Cartão Adaptável Específico do Usuário.

Por exemplo, Megan, uma inspetora de segurança da Contoso, deseja criar um incidente e atribuí-lo a Alex. Ela também quer que todos na equipe sejam cientes sobre o incidente. Megan usa a extensão de mensagem de relatório de incidentes da Contoso alimentada por Ações Universais para Cartões Adaptáveis.

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-incident-management.png" alt-text="Exibições Específicas do Usuário":::

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

**Para enviar cartões adaptáveis, atualize exibições específicas do usuário e invoque solicitações ao bot**

1. Quando Megan cria um novo incidente, o bot envia o Cartão Adaptável ou o cartão comum com detalhes de incidentes na Teams conversa.
2. Agora, esse cartão é atualizado automaticamente para o User Specific View para Megan e Alex. Os MRIs de usuário de Alex e Megan são adicionados na propriedade da propriedade `userIds` `refresh` JSON do Cartão Adaptável. O cartão permanece o mesmo para outros usuários na conversa.
3. Para Megan, a atualização automática dispara uma `adaptiveCard/action` solicitação de invocação para o bot. O bot pode retornar um cartão de criador de incidentes com `Edit` um botão como resposta a essa solicitação de invocação.
4. Da mesma forma para Alex, a atualização automática dispara outra `adaptiveCard/action` solicitação de invocação para o bot. O bot pode retornar um botão de cartão de proprietário `Resolve` de incidente como resposta a essa solicitação de invocação.

## <a name="invoke-request-sent-from-teams-client-to-the-bot"></a>Invocar solicitação enviada Teams cliente para o bot

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

## <a name="adaptivecardaction-invoke-response-card"></a>adaptiveCard/action invoca o cartão de resposta

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

## <a name="adaptivecardaction-invoke-response-card-for-alex"></a>adaptiveCard/action invocam o cartão de resposta para Alex

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

## <a name="invoke-response-to-return-adaptive-cards"></a>Invocar resposta para retornar cartões adaptáveis

O código a seguir fornece um exemplo de uma resposta de invocação para retornar Cartões Adaptáveis:

```C#
string cardJson = "<adaptive card json>";
var card = JsonConvert.DeserializeObject(cardJson);

var adaptiveCardResponse = JObject.FromObject(new
 {
    statusCode = 200,
    type = "application/vnd.microsoft.adaptive.card",
    value = card
 });
```

Diretrizes de design de cartão para ter em mente ao projetar exibições específicas do usuário:

* Você pode criar no máximo **60** Exibições Específicas do Usuário para um cartão específico que está sendo enviado para um chat ou canal especificando-os `userIds` na `refresh` seção.
* **Cartão Base:** A versão base do cartão que o desenvolvedor de bot envia para o chat. Esta é a versão do Cartão Adaptável para todos os usuários que não são especificados na `userIds` seção.
* Uma atualização ou edição de mensagem pode ser usada para atualizar o cartão base e atualizar simultaneamente o Cartão Específico do Usuário.

## <a name="see-also"></a>Confira também

* [Trabalhar com Ações Universais para Cartões Adaptáveis](Work-with-universal-actions-for-adaptive-cards.md)
* [Exibições atualizadas](Up-To-Date-Views.md)
