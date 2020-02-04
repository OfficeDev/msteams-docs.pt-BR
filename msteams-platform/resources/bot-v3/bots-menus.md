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
# <a name="add-a-bot-menu-in-microsoft-teams"></a><span data-ttu-id="88d08-104">Adicionar um menu de bot no Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="88d08-104">Add a bot menu in Microsoft Teams</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="88d08-105">Para ajudar a descoberta e a treinar os usuários sobre a funcionalidade de seu bot, agora você pode adicionar menus que surgem sempre que o usuário interage com seu bot.</span><span class="sxs-lookup"><span data-stu-id="88d08-105">To aid discovery and to help educate users about your bot’s functionality, you can now add menus that surface whenever the user interacts with your bot.</span></span> <span data-ttu-id="88d08-106">O menu mostrará o texto do comando e também fornecerá texto de ajuda, como um exemplo de uso ou uma descrição do objetivo do comando.</span><span class="sxs-lookup"><span data-stu-id="88d08-106">The menu will show the command text and also provide help text, such as a usage example or description of the command’s purpose.</span></span>

![Captura de tela do menu bot](~/assets/images/bots/bot-menus-bot-menu-sample.png)

<span data-ttu-id="88d08-108">Quando um usuário seleciona um item de menu, a sequência de comandos é inserida na caixa de texto para auxiliar na conclusão do usuário da mensagem do bot.</span><span class="sxs-lookup"><span data-stu-id="88d08-108">When a user selects a menu item, the command string is inserted into the text box to aid in user completion of the bot message.</span></span>

## <a name="bot-menu-support-on-teams-mobile-app"></a><span data-ttu-id="88d08-109">Suporte ao menu do bot no aplicativo móvel do teams</span><span class="sxs-lookup"><span data-stu-id="88d08-109">Bot menu support on Teams mobile app</span></span>
> [!NOTE] 
> <span data-ttu-id="88d08-110">Menus de bot não são exibidos em dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="88d08-110">Bot menus are not displayed on mobile devices</span></span>

## <a name="app-manifest"></a><span data-ttu-id="88d08-111">Manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="88d08-111">App manifest</span></span>

<span data-ttu-id="88d08-112">Para criar um menu de bot, adicione um [`commandLists`](~/resources/schema/manifest-schema.md#botscommandlists) novo objeto ao manifesto do seu aplicativo na seção bot.</span><span class="sxs-lookup"><span data-stu-id="88d08-112">To create a bot menu, add a new [`commandLists`](~/resources/schema/manifest-schema.md#botscommandlists) object to your app manifest under the bot section.</span></span> <span data-ttu-id="88d08-113">Você pode declarar menus individuais com comandos separados para cada escopo que seu bot suporta`personal`( `groupChat` ou `team`) cada menu oferece suporte para até 10 comandos.</span><span class="sxs-lookup"><span data-stu-id="88d08-113">You can declare individual menus with separate commands for each scope your bot supports (`personal`, `groupChat` or `team`) Each menu supports up to 10 commands.</span></span>

### <a name="manifest-excerpt---single-menu-for-both-scopes"></a><span data-ttu-id="88d08-114">Trecho de manifesto-menu único para ambos os escopos</span><span class="sxs-lookup"><span data-stu-id="88d08-114">Manifest excerpt - single menu for both scopes</span></span>

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

### <a name="manifest-excerpt---separate-menu-per-scope"></a><span data-ttu-id="88d08-115">Trecho de manifesto-menu separado por escopo</span><span class="sxs-lookup"><span data-stu-id="88d08-115">Manifest excerpt - separate menu per scope</span></span>

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

## <a name="best-practices"></a><span data-ttu-id="88d08-116">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="88d08-116">Best practices</span></span>

* <span data-ttu-id="88d08-117">Mantenha-o simples: o menu bot é destinado a apresentar os principais recursos do bot.</span><span class="sxs-lookup"><span data-stu-id="88d08-117">Keep it simple: The bot menu is meant to present the key capabilities of your bot.</span></span>
* <span data-ttu-id="88d08-118">Mantenha-o em breve: as opções de menu não devem ser extremamente longas e instruções de linguagem natural complexas-elas devem ser comandos simples.</span><span class="sxs-lookup"><span data-stu-id="88d08-118">Keep it short: Menu options shouldn’t be extremely long and complex natural language statements - they should be simple commands.</span></span>
* <span data-ttu-id="88d08-119">Sempre disponível: as ações/comandos do menu do bot devem ser sempre invocados, independentemente do estado da conversa ou da caixa de diálogo em que o bot está.</span><span class="sxs-lookup"><span data-stu-id="88d08-119">Always available: Bot menu actions/commands should be always invokable, regardless of the state of the conversation or the dialog the bot is in.</span></span>
