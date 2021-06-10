---
title: Adicionar um menu bot
description: Descreve como criar menus para bots no Microsoft Teams
keywords: Criação de menus de bots do teams
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
# <a name="add-a-bot-menu-in-microsoft-teams"></a><span data-ttu-id="1ffaa-104">Adicionar um menu bot no Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="1ffaa-104">Add a bot menu in Microsoft Teams</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="1ffaa-105">Para ajudar a descoberta e ajudar a instruir os usuários sobre a funcionalidade do bot, agora você pode adicionar menus que aparecerão sempre que o usuário interagir com seu bot.</span><span class="sxs-lookup"><span data-stu-id="1ffaa-105">To aid discovery and to help educate users about your bot’s functionality, you can now add menus that surface whenever the user interacts with your bot.</span></span> <span data-ttu-id="1ffaa-106">O menu mostrará o texto do comando e também fornecerá texto de ajuda, como um exemplo de uso ou descrição da finalidade do comando.</span><span class="sxs-lookup"><span data-stu-id="1ffaa-106">The menu will show the command text and also provide help text, such as a usage example or description of the command’s purpose.</span></span>

![Captura de tela do menu bot](~/assets/images/bots/bot-menus-bot-menu-sample.png)

<span data-ttu-id="1ffaa-108">Quando um usuário seleciona um item de menu, a cadeia de caracteres de comando é inserida na caixa de texto para ajudar na conclusão do usuário da mensagem bot.</span><span class="sxs-lookup"><span data-stu-id="1ffaa-108">When a user selects a menu item, the command string is inserted into the text box to aid in user completion of the bot message.</span></span>

## <a name="bot-menu-support-on-teams-mobile-app"></a><span data-ttu-id="1ffaa-109">Suporte ao menu bot no Teams aplicativo móvel</span><span class="sxs-lookup"><span data-stu-id="1ffaa-109">Bot menu support on Teams mobile app</span></span>
> [!NOTE] 
> <span data-ttu-id="1ffaa-110">Os menus bot não são exibidos em dispositivos móveis.</span><span class="sxs-lookup"><span data-stu-id="1ffaa-110">Bot menus are not displayed on mobile devices.</span></span>

## <a name="app-manifest"></a><span data-ttu-id="1ffaa-111">Manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="1ffaa-111">App manifest</span></span>

<span data-ttu-id="1ffaa-112">Para criar um menu bot, adicione um novo objeto ao [`commandLists`](~/resources/schema/manifest-schema.md#botscommandlists) manifesto do aplicativo na seção bot.</span><span class="sxs-lookup"><span data-stu-id="1ffaa-112">To create a bot menu, add a new [`commandLists`](~/resources/schema/manifest-schema.md#botscommandlists) object to your app manifest under the bot section.</span></span> <span data-ttu-id="1ffaa-113">Você pode declarar menus individuais com comandos separados para cada escopo que seu bot oferece suporte ( , , ou ) Cada menu dá suporte a até `personal` `groupChat` `team` 10 comandos.</span><span class="sxs-lookup"><span data-stu-id="1ffaa-113">You can declare individual menus with separate commands for each scope your bot supports (`personal`, `groupChat`, or `team`) Each menu supports up to 10 commands.</span></span>

### <a name="manifest-excerpt---single-menu-for-both-scopes"></a><span data-ttu-id="1ffaa-114">Trecho de manifesto - menu único para ambos os escopos</span><span class="sxs-lookup"><span data-stu-id="1ffaa-114">Manifest excerpt - single menu for both scopes</span></span>

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

### <a name="manifest-excerpt---separate-menu-per-scope"></a><span data-ttu-id="1ffaa-115">Trecho de manifesto - menu separado por escopo</span><span class="sxs-lookup"><span data-stu-id="1ffaa-115">Manifest excerpt - separate menu per scope</span></span>

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

## <a name="best-practices"></a><span data-ttu-id="1ffaa-116">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="1ffaa-116">Best practices</span></span>

* <span data-ttu-id="1ffaa-117">Mantenha-o simples: o menu bot deve apresentar os principais recursos do bot.</span><span class="sxs-lookup"><span data-stu-id="1ffaa-117">Keep it simple: The bot menu is meant to present the key capabilities of your bot.</span></span>
* <span data-ttu-id="1ffaa-118">Resumindo: as opções de menu não devem ser instruções de linguagem natural extremamente longas e complexas - devem ser comandos simples.</span><span class="sxs-lookup"><span data-stu-id="1ffaa-118">Keep it short: Menu options shouldn’t be extremely long and complex natural language statements - they should be simple commands.</span></span>
* <span data-ttu-id="1ffaa-119">Sempre disponível: ações/comandos de menu bot devem ser sempre invocados, independentemente do estado da conversa ou da caixa de diálogo em que o bot está.</span><span class="sxs-lookup"><span data-stu-id="1ffaa-119">Always available: Bot menu actions/commands should be always invokable, regardless of the state of the conversation or the dialog the bot is in.</span></span>
