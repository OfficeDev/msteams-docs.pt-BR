---
title: Adicionar um menu bot
description: Descreve como criar menus para bots no Microsoft Teams
keywords: Criação de menus de bots do teams
ms.topic: how-to
localization_priority: Normal
ms.date: 05/20/2019
ms.openlocfilehash: f4190d0b21abbe00994e082000202b7bc65b917c
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019766"
---
# <a name="add-a-bot-menu-in-microsoft-teams"></a><span data-ttu-id="b4ef5-104">Adicionar um menu de bot no Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="b4ef5-104">Add a bot menu in Microsoft Teams</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="b4ef5-105">Para ajudar a descoberta e ajudar a instruir os usuários sobre a funcionalidade do bot, agora você pode adicionar menus que aparecerão sempre que o usuário interagir com seu bot.</span><span class="sxs-lookup"><span data-stu-id="b4ef5-105">To aid discovery and to help educate users about your bot’s functionality, you can now add menus that surface whenever the user interacts with your bot.</span></span> <span data-ttu-id="b4ef5-106">O menu mostrará o texto do comando e também fornecerá texto de ajuda, como um exemplo de uso ou descrição da finalidade do comando.</span><span class="sxs-lookup"><span data-stu-id="b4ef5-106">The menu will show the command text and also provide help text, such as a usage example or description of the command’s purpose.</span></span>

![Captura de tela do menu bot](~/assets/images/bots/bot-menus-bot-menu-sample.png)

<span data-ttu-id="b4ef5-108">Quando um usuário seleciona um item de menu, a cadeia de caracteres de comando é inserida na caixa de texto para ajudar na conclusão do usuário da mensagem bot.</span><span class="sxs-lookup"><span data-stu-id="b4ef5-108">When a user selects a menu item, the command string is inserted into the text box to aid in user completion of the bot message.</span></span>

## <a name="bot-menu-support-on-teams-mobile-app"></a><span data-ttu-id="b4ef5-109">Suporte ao menu bot no aplicativo móvel do Teams</span><span class="sxs-lookup"><span data-stu-id="b4ef5-109">Bot menu support on Teams mobile app</span></span>
> [!NOTE] 
> <span data-ttu-id="b4ef5-110">Os menus bot não são exibidos em dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="b4ef5-110">Bot menus are not displayed on mobile devices</span></span>

## <a name="app-manifest"></a><span data-ttu-id="b4ef5-111">Manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="b4ef5-111">App manifest</span></span>

<span data-ttu-id="b4ef5-112">Para criar um menu bot, adicione um novo objeto ao [`commandLists`](~/resources/schema/manifest-schema.md#botscommandlists) manifesto do aplicativo na seção bot.</span><span class="sxs-lookup"><span data-stu-id="b4ef5-112">To create a bot menu, add a new [`commandLists`](~/resources/schema/manifest-schema.md#botscommandlists) object to your app manifest under the bot section.</span></span> <span data-ttu-id="b4ef5-113">Você pode declarar menus individuais com comandos separados para cada escopo que seu bot oferece suporte ( , ou ) Cada menu dá suporte `personal` `groupChat` a até `team` 10 comandos.</span><span class="sxs-lookup"><span data-stu-id="b4ef5-113">You can declare individual menus with separate commands for each scope your bot supports (`personal`, `groupChat` or `team`) Each menu supports up to 10 commands.</span></span>

### <a name="manifest-excerpt---single-menu-for-both-scopes"></a><span data-ttu-id="b4ef5-114">Trecho de manifesto - menu único para ambos os escopos</span><span class="sxs-lookup"><span data-stu-id="b4ef5-114">Manifest excerpt - single menu for both scopes</span></span>

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

### <a name="manifest-excerpt---separate-menu-per-scope"></a><span data-ttu-id="b4ef5-115">Trecho de manifesto - menu separado por escopo</span><span class="sxs-lookup"><span data-stu-id="b4ef5-115">Manifest excerpt - separate menu per scope</span></span>

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

## <a name="best-practices"></a><span data-ttu-id="b4ef5-116">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="b4ef5-116">Best practices</span></span>

* <span data-ttu-id="b4ef5-117">Mantenha-o simples: o menu bot deve apresentar os principais recursos do bot.</span><span class="sxs-lookup"><span data-stu-id="b4ef5-117">Keep it simple: The bot menu is meant to present the key capabilities of your bot.</span></span>
* <span data-ttu-id="b4ef5-118">Resumindo: as opções de menu não devem ser instruções de linguagem natural extremamente longas e complexas - devem ser comandos simples.</span><span class="sxs-lookup"><span data-stu-id="b4ef5-118">Keep it short: Menu options shouldn’t be extremely long and complex natural language statements - they should be simple commands.</span></span>
* <span data-ttu-id="b4ef5-119">Sempre disponível: ações/comandos de menu bot devem ser sempre invocados, independentemente do estado da conversa ou da caixa de diálogo em que o bot está.</span><span class="sxs-lookup"><span data-stu-id="b4ef5-119">Always available: Bot menu actions/commands should be always invokable, regardless of the state of the conversation or the dialog the bot is in.</span></span>
