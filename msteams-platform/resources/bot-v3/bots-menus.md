---
title: Adicionar um menu de bot
description: Descreve como criar menus para bots no Microsoft Teams
keywords: criação de menus de bots do teams
ms.date: 05/20/2019
ms.openlocfilehash: 36a224dc21cccc5fcd1047e45e3d749e7ca19ea7
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672490"
---
# <a name="add-a-bot-menu-in-microsoft-teams"></a>Adicionar um menu de bot no Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Para ajudar a descoberta e a treinar os usuários sobre a funcionalidade de seu bot, agora você pode adicionar menus que surgem sempre que o usuário interage com seu bot. O menu mostrará o texto do comando e também fornecerá texto de ajuda, como um exemplo de uso ou uma descrição do objetivo do comando.

![Captura de tela do menu bot](~/assets/images/bots/bot-menus-bot-menu-sample.png)

Quando um usuário seleciona um item de menu, a sequência de comandos é inserida na caixa de texto para auxiliar na conclusão do usuário da mensagem do bot.

## <a name="bot-menu-support-on-teams-mobile-app"></a>Suporte ao menu do bot no aplicativo móvel do teams
> [!NOTE] 
> Menus de bot não são exibidos em dispositivos móveis

## <a name="app-manifest"></a>Manifesto do aplicativo

Para criar um menu de bot, adicione um [`commandLists`](~/resources/schema/manifest-schema.md#botscommandlists) novo objeto ao manifesto do seu aplicativo na seção bot. Você pode declarar menus individuais com comandos separados para cada escopo que seu bot suporta`personal`( `groupChat` ou `team`) cada menu oferece suporte para até 10 comandos.

### <a name="manifest-excerpt---single-menu-for-both-scopes"></a>Trecho de manifesto-menu único para ambos os escopos

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

### <a name="manifest-excerpt---separate-menu-per-scope"></a>Trecho de manifesto-menu separado por escopo

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

* Mantenha-o simples: o menu bot é destinado a apresentar os principais recursos do bot.
* Mantenha-o em breve: as opções de menu não devem ser extremamente longas e instruções de linguagem natural complexas-elas devem ser comandos simples.
* Sempre disponível: as ações/comandos do menu do bot devem ser sempre invocados, independentemente do estado da conversa ou da caixa de diálogo em que o bot está.
