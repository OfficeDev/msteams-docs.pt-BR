---
title: Adicionar um menu de bot
description: Neste módulo, saiba como adicionar um menu de bot no Microsoft Teams e criar menus para bots no Microsoft Teams
ms.topic: how-to
ms.localizationpriority: medium
ms.date: 05/20/2019
ms.openlocfilehash: ed65699b930d3e5334dd7fbb03da18a1482d6e5d
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66143379"
---
# <a name="add-a-bot-menu-in-microsoft-teams"></a>Adicionar um menu de bot no Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Para ajudar a descobrir e ajudar a instruir os usuários sobre a funcionalidade do bot, agora você pode adicionar menus que são exibidos sempre que o usuário interage com o bot. O menu mostrará o texto do comando e também fornecerá texto de ajuda, como um exemplo de uso ou uma descrição da finalidade do comando.

![Captura de tela do menu do bot](~/assets/images/bots/bot-menus-bot-menu-sample.png)

Quando um usuário seleciona um item de menu, a cadeia de caracteres de comando é inserida na caixa de texto para auxiliar na conclusão do usuário da mensagem do bot.

## <a name="bot-menu-support-on-teams-mobile-app"></a>Suporte ao menu de bot Teams aplicativo móvel

> [!NOTE]
> Os menus de bot não são exibidos em dispositivos móveis.

## <a name="app-manifest"></a>Manifesto do aplicativo

Para criar um menu de bot, adicione um novo [`commandLists`](~/resources/schema/manifest-schema.md#botscommandlists) objeto ao manifesto do aplicativo na seção do bot. Você pode declarar menus individuais com comandos separados para cada escopo ao qual o bot dá suporte (`personal`ou`groupChat``team`) cada menu dá suporte a até 10 comandos.

### <a name="manifest-excerpt---single-menu-for-both-scopes"></a>Trecho de manifesto – menu único para ambos os escopos

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

### <a name="manifest-excerpt---separate-menu-per-scope"></a>Trecho de manifesto – menu separado por escopo

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

* Mantenha-o simples: o menu do bot destina-se a apresentar os principais recursos do bot.
* Resumindo: as opções de menu não devem ser instruções de linguagem natural extremamente longas e complexas– elas devem ser comandos simples.
* Sempre disponível: ações/comandos de menu do bot devem ser sempre invocados, independentemente do estado da conversa ou da caixa de diálogo em que o bot está.
