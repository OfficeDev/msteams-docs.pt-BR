---
title: Adicione um menu de bot
description: Descreve como criar menus para bots em Microsoft Teams
keywords: equipes bots criação menus
ms.topic: how-to
localization_priority: Normal
ms.date: 05/20/2019
ms.openlocfilehash: da6f36e1b7071b92f6411ab7d2afdccb795946b7
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566765"
---
# <a name="add-a-bot-menu-in-microsoft-teams"></a>Adicione um menu de bots em Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Para ajudar na descoberta e ajudar a educar os usuários sobre a funcionalidade do seu bot, agora você pode adicionar menus que aparecem sempre que o usuário interagir com seu bot. O menu mostrará o texto de comando e também fornecerá texto de ajuda, como um exemplo de uso ou descrição do propósito do comando.

![Captura de tela do menu do bot](~/assets/images/bots/bot-menus-bot-menu-sample.png)

Quando um usuário seleciona um item do menu, a sequência de comando é inserida na caixa de texto para ajudar na conclusão do usuário da mensagem do bot.

## <a name="bot-menu-support-on-teams-mobile-app"></a>Suporte ao menu de bots em Teams aplicativo móvel
> [!NOTE] 
> Os menus de bot não são exibidos em dispositivos móveis.

## <a name="app-manifest"></a>Manifesto do aplicativo

Para criar um menu de bot, adicione um novo [`commandLists`](~/resources/schema/manifest-schema.md#botscommandlists) objeto ao manifesto do aplicativo na seção bot. Você pode declarar menus individuais com comandos separados para cada escopo que seu bot suporta ( `personal` , ou ) Cada menu suporta até `groupChat` `team` 10 comandos.

### <a name="manifest-excerpt---single-menu-for-both-scopes"></a>Trecho manifesto - menu único para ambos os escopos

```json
{
  ⋮
  "bots":[
    {
      "botId":"[Microsoft App ID for your bot]",
      "scopes": [
        "personal",
        "team"
      ],
      "commandLists":[
        {
          "scopes":[
            "team",
            "personal"
          ],
          "commands":[
            {
              "title":"Help",
              "description":"Displays this help message"
            },
            {
              "title":"Search Flights",
              "description":"Search flights from Seattle to Phoenix May 2-5 departing after 3pm"
            },
            {
              "title":"Search Hotels",
              "description":"Search hotels in Portland tonight"
            },
            {
              "title":"Best Time to Fly",
              "description":"Best time to fly to London for a 5 day trip this summer"
            }
          ]
        }
      ]
    }
  ],
  ...
}
```

### <a name="manifest-excerpt---separate-menu-per-scope"></a>Trecho manifesto - menu separado por escopo

```json
{
  ...
  "bots":[
    {
      "botId":"[Microsoft app ID for your bot]",
      "scopes": [
        "groupChat",
        "team"
      ],
      "commandLists":[
        {
          "scopes":[
            "team"
          ],
          "commands":[
            {
            "title":"help",
            "description":"Displays this help message for channels"
            }
          ]
        },
        {
          "scopes":[
            "groupChat"
          ],
          "commands":[
            {
            "title":"help",
            "description":"Displays this help message for group chat"
            }
          ]
        }
      ]
    }
  ],
  ...
}
```

## <a name="best-practices"></a>Práticas recomendadas

* Seja simples: o menu do bot é feito para apresentar as principais capacidades do seu bot.
* Mantenha-o curto: as opções de menu não devem ser extremamente longas e complexas declarações de linguagem natural - eles devem ser comandos simples.
* Sempre disponível: As ações/comandos do menu bot devem ser sempre invocáveis, independentemente do estado da conversa ou do diálogo em que o bot está.
