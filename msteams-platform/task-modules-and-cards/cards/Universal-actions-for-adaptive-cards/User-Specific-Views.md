---
title: Exibições Específicas do Usuário
description: Neste módulo, saiba mais sobre exibições específicas do usuário usando ações universais com exemplo de código e cartão de resposta adaptiveCard/action invoke
author: surbhigupta12
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: a3fdc937ba1528a2bf9aa304bf484bbcae68b5c6
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66143918"
---
# <a name="user-specific-views"></a>Exibições Específicas do Usuário

Anteriormente, se os Cartões Adaptáveis fossem enviados em uma Teams, todos os usuários veriam exatamente o mesmo conteúdo do cartão. Com a introdução do modelo de Ações Universais `refresh` e para Cartões Adaptáveis, os desenvolvedores de bot agora podem fornecer exibições específicas do usuário de Cartões Adaptáveis aos usuários. O mesmo Cartão Adaptável agora pode ser atualizado para um Cartão Adaptável Específico do Usuário. O Cartão Adaptável fornece cenários avançados, como aprovações, controles de criador de sondagem, tíquetes, gerenciamento de incidentes e cartões de gerenciamento de projetos.

> [!NOTE]
>
> * A Exibição Específica do Usuário tem suporte para Cartões Adaptáveis enviados por um bot e depende das Ações Universais.
> * No máximo 60 usuários diferentes podem ver uma versão diferente do cartão com informações ou ações adicionais.

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

A lista a seguir fornece diretrizes de design de cartão para exibições específicas do usuário:

* Comportamento de atualização: você pode criar um máximo de 60 Exibições Específicas do Usuário para um cartão específico enviado a `userIds` uma conversa especificando-os na `Refresh` propriedade.

  * Se o `userIds` campo não `Refresh` for especificado na propriedade, Teams cliente poderá disparar automaticamente a atualização para todos os usuários quando houver menos ou igual a 60 membros na conversa.

  * Para que os usuários disparem manualmente a atualização do cartão, eles podem selecionar **Atualizar** no menu de opções de mensagem. Isso acontece com todos os usuários quando há menos de 60 `userIds` membros em uma conversa ou com o conjunto de usuários não especificado na lista quando há todos ou menos de 60 usuários em uma conversa.

* Cartão base: o bot envia a mensagem, que é inserida com a versão base do cartão. Todos os membros da conversa podem exibir o mesmo. Posteriormente, o bot busca o Cartão Específico do Usuário por meio da atualização para os usuários especificados na `userIds` seção.

* Tempo limite de atualização: Teams cliente dispara uma atualização de duas maneiras, seja por meio de **Atualizar** ou selecionando **Executar**. A atualização será disparada somente se o cartão da última invocação tiver mais de um minuto. Você pode controlar o comportamento de atualização adicionando um carimbo de data/hora ao recipiente de dados e verificando-o antes de enviar o cartão atualizado.

* Uma atualização de mensagem pode ser usada para atualizar o cartão base e atualizar simultaneamente o Cartão Específico do Usuário. Abrir o chat ou canal também atualiza o cartão para usuários com **a Atualização** habilitada.

* Para cenários com grupos maiores em que os usuários alternam para um modo de exibição em ação, que precisa de atualizações dinâmicas para respondentes, você pode continuar adicionando até 60 usuários à `userIds` lista. Você pode remover o primeiro respondente da lista quando o 61º usuário responder. Para os usuários removidos da lista `userIds` , você pode fornecer uma **Atualização manual para** obter o resultado mais recente.

* Forneça um prompt aos usuários para obter uma Exibição Específica do Usuário, em que eles veem apenas uma exibição específica do cartão ou algumas ações.

> [!NOTE]
> O Cartão Específico do Usuário retornado pelo bot é enviado somente para o cliente específico que solicitou. Por exemplo, se um usuário alternar para um cliente diferente, como da área de trabalho para o celular, outro evento de invocação será disparado para buscar o cartão atualizado.

## <a name="code-sample"></a>Exemplo de código

|Nome do exemplo | Descrição | .NETCore | Node.js |
|----------------|-----------------|--------------|--------------|
| Cartões Adaptáveis de Fluxos de Trabalho Sequenciais | Demonstre como implementar Fluxos de Trabalho Sequenciais, Exibições Específicas do Usuário e Cartões Adaptáveis atualizados em bots. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-sequential-flow-adaptive-cards/csharp) | [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-sequential-flow-adaptive-cards/nodejs) |

## <a name="see-also"></a>Confira também

* [Trabalhar com Ações Universais para Cartões Adaptáveis](Work-with-universal-actions-for-adaptive-cards.md)
* [Modos de exibição atualizados](Up-To-Date-Views.md)
* [Comentários de preenchimento do formulário](~/bots/how-to/conversations/conversation-messages.md#form-completion-feedback)
