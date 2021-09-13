---
title: Adicionar um menu bot
description: Descreve como criar menus para bots no Microsoft Teams
keywords: Criação de menus de bots do teams
ms.topic: how-to
ms.localizationpriority: medium
ms.date: 05/20/2019
ms.openlocfilehash: 14100c9032f0adf964975abbe436c84194475a99
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59155512"
---
# <a name="add-a-bot-menu-in-microsoft-teams"></a>Adicionar um menu bot no Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Para ajudar a descoberta e ajudar a instruir os usuários sobre a funcionalidade do bot, agora você pode adicionar menus que aparecerão sempre que o usuário interagir com seu bot. O menu mostrará o texto do comando e também fornecerá texto de ajuda, como um exemplo de uso ou descrição da finalidade do comando.

![Captura de tela do menu bot](~/assets/images/bots/bot-menus-bot-menu-sample.png)

Quando um usuário seleciona um item de menu, a cadeia de caracteres de comando é inserida na caixa de texto para ajudar na conclusão do usuário da mensagem bot.

## <a name="bot-menu-support-on-teams-mobile-app"></a>Suporte ao menu bot no Teams aplicativo móvel
> [!NOTE] 
> Os menus bot não são exibidos em dispositivos móveis.

## <a name="app-manifest"></a>Manifesto do aplicativo

Para criar um menu bot, adicione um novo objeto ao [`commandLists`](~/resources/schema/manifest-schema.md#botscommandlists) manifesto do aplicativo na seção bot. Você pode declarar menus individuais com comandos separados para cada escopo que seu bot oferece suporte ( , , ou ) Cada menu dá suporte a até `personal` `groupChat` `team` 10 comandos.

### <a name="manifest-excerpt---single-menu-for-both-scopes"></a>Trecho de manifesto - menu único para ambos os escopos

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

### <a name="manifest-excerpt---separate-menu-per-scope"></a>Trecho de manifesto - menu separado por escopo

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

* Mantenha-o simples: o menu bot deve apresentar os principais recursos do bot.
* Resumindo: as opções de menu não devem ser instruções de linguagem natural extremamente longas e complexas - devem ser comandos simples.
* Sempre disponível: ações/comandos de menu bot devem ser sempre invocados, independentemente do estado da conversa ou da caixa de diálogo em que o bot está.
