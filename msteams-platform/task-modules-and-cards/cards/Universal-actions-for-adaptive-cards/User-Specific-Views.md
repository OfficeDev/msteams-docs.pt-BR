---
title: Exibições Específicas do Usuário
description: Amostra para visualizações específicas do usuário usando ações universais
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

Mais cedo, se o Adaptive Cards foi enviado em uma conversa Teams, todos os usuários vêem exatamente o mesmo conteúdo do cartão. Com a introdução do modelo Universal Actions e `refresh` para Cartões Adaptativos, os desenvolvedores de bots agora podem fornecer visualizações específicas do usuário de cartões adaptativos aos usuários. O mesmo Cartão Adaptável agora pode atualizar para um cartão adaptativo específico do usuário.

Por exemplo, Megan, uma inspetora de segurança em Contoso, quer criar um incidente e atribuí-lo a Alex. Ela também quer que todos da equipe estejam cientes sobre o incidente. Megan usa a extensão de mensagens de relatórios de incidentes contoso alimentada pela Universal Actions for Adaptive Cards.

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-incident-management.png" alt-text="Exibições Específicas do Usuário":::

## <a name="user-specific-views-for-adaptive-cards"></a>Visualizações específicas do usuário para cartões adaptativos

O código a seguir fornece um exemplo de Cartões Adaptativos:

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

**Para enviar cartões adaptativos, atualize visualizações específicas do usuário e invoque solicitações ao bot**

1. Quando Megan cria um novo incidente, o bot envia o Cartão Adaptável ou cartão comum com detalhes de incidentes na Teams conversa.
2. Agora, este cartão atualiza automaticamente para a visualização específica do usuário para Megan e Alex. As Ressonâncias Magnéticas usuárias de Alex e Megan são adicionadas em `userIds` propriedade de propriedade do Cartão `refresh` Adaptativo JSON. O cartão permanece o mesmo para outros usuários na conversa.
3. Para Megan, a atualização automática aciona um `adaptiveCard/action` pedido de invocação para o bot. O bot pode devolver um cartão criador de incidentes com `Edit` botão como resposta a este pedido de invocação.
4. Da mesma forma para Alex, a atualização automática aciona outro `adaptiveCard/action` pedido de invocação para o bot. O bot pode retornar um botão de cartão do proprietário do incidente `Resolve` como resposta a este pedido de invocação.

## <a name="invoke-request-sent-from-teams-client-to-the-bot"></a>Solicitar solicitação enviada de Teams cliente para o bot

O código a seguir fornece um exemplo de uma solicitação de invocação enviada do cliente Teams de Alex e Megan para o bot:

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

## <a name="adaptivecardaction-invoke-response-card"></a>cartão de resposta adaptiveCard/action invocar

O código a seguir fornece um exemplo de um cartão de resposta adaptávelcard/action invoke para Megan:

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

## <a name="adaptivecardaction-invoke-response-card-for-alex"></a>cartão de resposta adaptiveCard/action invocar para Alex

O código a seguir fornece um exemplo de um cartão de resposta adaptávelcard/action invoke para Alex:

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

## <a name="invoke-response-to-return-adaptive-cards"></a>Invoque a resposta para retornar cartões adaptativos

O código a seguir fornece um exemplo de uma resposta de invocação para retornar cartões adaptativos:

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

Diretrizes de design de cartão para ter em mente ao projetar visualizações específicas do usuário:

* Você pode criar um máximo de **60 visualizações específicas** do usuário para um determinado cartão sendo enviado para um chat ou canal especificando o seu `userIds` na `refresh` seção.
* **Cartão base:** A versão base do cartão que o desenvolvedor de bot envia para o chat. Esta é a versão do Cartão Adaptável para todos os usuários que não estão especificados na `userIds` seção.
* Uma atualização ou edição de mensagens pode ser usada para atualizar o cartão base e atualizar simultaneamente o Cartão Específico do Usuário.

## <a name="see-also"></a>Confira também

* [Trabalhar com Ações Universais para Cartões Adaptáveis](Work-with-universal-actions-for-adaptive-cards.md)
* [Vistas atualizadas](Up-To-Date-Views.md)
