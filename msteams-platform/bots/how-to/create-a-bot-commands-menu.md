---
title: Criar um menu de comando para o bot
author: clearab
description: Como criar um menu de comando para o bot do Microsoft Teams
ms.topic: overview, command menu
ms.author: anclear
ms.openlocfilehash: 81efb94fc882aa4653ab162863d5d973aeae87b9
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672592"
---
# <a name="bot-command-menus"></a><span data-ttu-id="34129-103">Menus de comando do bot</span><span class="sxs-lookup"><span data-stu-id="34129-103">Bot command menus</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

> [!Note]
> <span data-ttu-id="34129-104">Menus de bot não aparecerão em clientes móveis.</span><span class="sxs-lookup"><span data-stu-id="34129-104">Bot menus won't appear on mobile clients.</span></span>

<span data-ttu-id="34129-105">Adicionar menu de comando para seu bot permite que você defina um conjunto de comandos principais que seu bot possa sempre responder.</span><span class="sxs-lookup"><span data-stu-id="34129-105">Add command menu for your bot allows you to define a set of core commands your bot can always respond to.</span></span> <span data-ttu-id="34129-106">A lista de comandos é apresentada ao usuário acima da área de mensagem de redação quando está convertida com o bot.</span><span class="sxs-lookup"><span data-stu-id="34129-106">The list of commands is presented to the user above the compose message area when they are conversing with your bot.</span></span> <span data-ttu-id="34129-107">A seleção de um comando na lista inserirá a cadeia de caracteres de comando na caixa de mensagem de redação, todos os usuários precisarão ser selecionados **Enviar**.</span><span class="sxs-lookup"><span data-stu-id="34129-107">Selecting a command from the list will insert the command string into the compose message box, then all users need to do is select **Send**.</span></span>

![Menu de comando do bot](./conversations/media/bot-menu-sample.png)

## <a name="create-a-command-menu-for-your-bot"></a><span data-ttu-id="34129-109">Criar um menu de comando para o bot</span><span class="sxs-lookup"><span data-stu-id="34129-109">Create a command menu for your bot</span></span>

<span data-ttu-id="34129-110">Menus de comando são definidos no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="34129-110">Command menus are defined in your app manifest.</span></span> <span data-ttu-id="34129-111">Você pode usar o app Studio para ajudá-lo a criá-los ou adicioná-los manualmente.</span><span class="sxs-lookup"><span data-stu-id="34129-111">You can either use App Studio to help you create them, or add them manually.</span></span>

### <a name="creating-a-command-menu-for-your-bot-using-app-studio"></a><span data-ttu-id="34129-112">Criando um menu de comando para o bot usando o app Studio</span><span class="sxs-lookup"><span data-stu-id="34129-112">Creating a command menu for your bot using App Studio</span></span>

<span data-ttu-id="34129-113">As instruções aqui presumem que você esteja editando um manifesto de aplicativo existente.</span><span class="sxs-lookup"><span data-stu-id="34129-113">The instructions here assume that you'll be editing an existing app manifest.</span></span> <span data-ttu-id="34129-114">As etapas para adicionar um menu de comando são as mesmas, se você está criando um novo manifesto ou editando um existente.</span><span class="sxs-lookup"><span data-stu-id="34129-114">The steps for adding a command menu are the same, whether you're creating a new manifest or editing an existing one.</span></span>

1. <span data-ttu-id="34129-115">Abra o app Studio no... menu de estouro no trilho esquerdo de navegação.</span><span class="sxs-lookup"><span data-stu-id="34129-115">Open App Studio from the ... overflow menu on the left navigation rail.</span></span> <span data-ttu-id="34129-116">Se você não tiver o app Studio disponível, você pode baixá-lo.</span><span class="sxs-lookup"><span data-stu-id="34129-116">If you don't have App Studio available you can download it.</span></span> <span data-ttu-id="34129-117">Consulte [Installing app Studio](https://aka.ms/teams-app-studio#installing-app-studio) para obter mais informações sobre como usar o app Studio.</span><span class="sxs-lookup"><span data-stu-id="34129-117">See [Installing App Studio](https://aka.ms/teams-app-studio#installing-app-studio) for more information on using App Studio.</span></span>

    ![App Studio](./conversations/media/AppStudio.png)

2. <span data-ttu-id="34129-119">Uma vez no app Studio, selecione a guia **Editor do manifesto** .</span><span class="sxs-lookup"><span data-stu-id="34129-119">Once in App Studio, select the **Manifest editor** tab.</span></span>

3. <span data-ttu-id="34129-120">Na coluna à esquerda do modo de exibição editor de manifesto na seção **recursos** , selecione **bots**.</span><span class="sxs-lookup"><span data-stu-id="34129-120">In the left column of the manifest editor view in the **Capabilities** section, select **Bots**.</span></span>

4. <span data-ttu-id="34129-121">Na coluna à direita do modo de exibição editor de manifesto na seção **comandos** , selecione o botão **Adicionar** .</span><span class="sxs-lookup"><span data-stu-id="34129-121">In the right column of the manifest editor view in the **Commands** section, select the **Add** button.</span></span>

    ![Botão Adicionar menu de comando do App Studio](./conversations/media/AppStudio-CommandMenu-Add.png)

5. <span data-ttu-id="34129-123">A **nova** tela de comando será exibida.</span><span class="sxs-lookup"><span data-stu-id="34129-123">The **New Command** screen appears.</span></span> <span data-ttu-id="34129-124">Insira o **texto do comando** que você deseja que apareça como o comando de menu e o **texto de ajuda** que você deseja que apareçam diretamente sob o texto do comando no menu.</span><span class="sxs-lookup"><span data-stu-id="34129-124">Enter the **Command text** that you want to have appear as the menu command, and the **Help text** that you want to have appear directly under the command text in the menu.</span></span> <span data-ttu-id="34129-125">Isso deve ser uma breve explicação da finalidade do comando.</span><span class="sxs-lookup"><span data-stu-id="34129-125">This should be a brief explanation of the purpose of the command.</span></span>

6. <span data-ttu-id="34129-126">Em seguida, selecione o (s) escopo (s) onde deseja que este menu de comando apareça e, em seguida, selecione o botão **salvar** .</span><span class="sxs-lookup"><span data-stu-id="34129-126">Next, select the scope(s) where you want this command menu to appear, then select the **Save** button.</span></span>

    ![Botão Adicionar menu de comando do App Studio](./conversations/media/AppStudio-NewCommandMenu.png)

### <a name="creating-a-command-menu-for-your-bot-by-editing-manifestjson"></a><span data-ttu-id="34129-128">Criar um menu de comando para o bot editando **manifest. JSON**</span><span class="sxs-lookup"><span data-stu-id="34129-128">Creating a command menu for your bot by editing **Manifest.json**</span></span>

<span data-ttu-id="34129-129">Outra abordagem válida para a criação de um menu de comando é criá-lo diretamente no arquivo de manifesto ao desenvolver o código-fonte do bot.</span><span class="sxs-lookup"><span data-stu-id="34129-129">Another valid approach for creating a command menu is to create it directly in the manifest file while developing your bot source code.</span></span> <span data-ttu-id="34129-130">Aqui estão algumas coisas que você deve ter em mente ao usar essa abordagem:</span><span class="sxs-lookup"><span data-stu-id="34129-130">Here are a few things to keep in mind when using this approach:</span></span>

1. <span data-ttu-id="34129-131">Cada menu oferece suporte a até 10 comandos.</span><span class="sxs-lookup"><span data-stu-id="34129-131">Each menu supports up to 10 commands.</span></span>

2. <span data-ttu-id="34129-132">Você pode criar um único menu de comando que funcionará em todos os escopos.</span><span class="sxs-lookup"><span data-stu-id="34129-132">You can create a single command menu that will work in all scopes.</span></span>

3. <span data-ttu-id="34129-133">Você pode criar um menu de comando diferente para cada escopo</span><span class="sxs-lookup"><span data-stu-id="34129-133">You can create a different command menu for each scope</span></span>

#### <a name="manifest-example---single-menu-for-both-scopes"></a><span data-ttu-id="34129-134">Exemplo de manifesto – menu único para ambos os escopos</span><span class="sxs-lookup"><span data-stu-id="34129-134">Manifest example - single menu for both scopes</span></span>

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

#### <a name="manifest-example---menu-for-each-scope"></a><span data-ttu-id="34129-135">Exemplo de manifesto-menu para cada escopo</span><span class="sxs-lookup"><span data-stu-id="34129-135">Manifest example - menu for each scope</span></span>

```json
{
  ...
  "bots":[
    {
      "botId":"<Microsoft app ID for your bot>",
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

## <a name="handling-menu-commands-in-your-bot-code"></a><span data-ttu-id="34129-136">Manipular comandos de menu no seu código de bot</span><span class="sxs-lookup"><span data-stu-id="34129-136">Handling menu commands in your bot code</span></span>

<span data-ttu-id="34129-137">Os bots em um grupo ou canal respondem apenas quando são mencionados ("@botname") em uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="34129-137">Bots in a group or channel respond only when they are mentioned ("@botname") in a message.</span></span> <span data-ttu-id="34129-138">Como resultado, todas as mensagens recebidas por um bot quando em um escopo de grupo ou canal conterão seu próprio nome no texto da mensagem retornado.</span><span class="sxs-lookup"><span data-stu-id="34129-138">As a result, every message received by a bot when in a group or channel scope will contain its own name in the message text returned.</span></span> <span data-ttu-id="34129-139">Você precisa garantir que as alças de análise da mensagem antes de manipular o comando retornado.</span><span class="sxs-lookup"><span data-stu-id="34129-139">You need to ensure your message parsing handles that before handling the command being returned.</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="34129-140">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="34129-140">C#/.NET</span></span>](#tab/dotnet)

<span data-ttu-id="34129-141">Você pode analisar a `Activity` `RemoveRecipientMention` \*\* \@\*\* parte de menção do texto da mensagem usando um método estático fornecido com o Microsoft bot Framework — um método da classe chamado.</span><span class="sxs-lookup"><span data-stu-id="34129-141">You can parse out the **\@Mention** portion of the message text using a static method provided with the Microsoft Bot Framework — a method of the `Activity` class named `RemoveRecipientMention`.</span></span>

```csharp
var modifiedText = turnContext.Activity.RemoveRecipientMention();
```

# <a name="javascriptnodejstabjavascript"></a>[<span data-ttu-id="34129-142">JavaScript/node. js</span><span class="sxs-lookup"><span data-stu-id="34129-142">JavaScript/Node.js</span></span>](#tab/javascript)

<span data-ttu-id="34129-143">Você pode analisar a `TurnContext` `removeMentionText` \*\* \@\*\* parte de menção do texto da mensagem usando um método estático fornecido com o Microsoft bot Framework — um método da classe chamado.</span><span class="sxs-lookup"><span data-stu-id="34129-143">You can parse out the **\@Mention** portion of the message text using a static method provided with the Microsoft Bot Framework — a method of the `TurnContext` class named `removeMentionText`.</span></span>

```javascript
const modifiedText = TurnContext.removeMentionText(turnContext.activity, turnContext.activity.recipient.id);
```

# <a name="pythontabpython"></a>[<span data-ttu-id="34129-144">Python</span><span class="sxs-lookup"><span data-stu-id="34129-144">Python</span></span>](#tab/python)


<span data-ttu-id="34129-145">Você pode analisar a parte **@Mention** do texto da mensagem usando um método estático fornecido com o Microsoft bot Framework — um método da `TurnContext` classe chamado. `remove_recipient_mention`</span><span class="sxs-lookup"><span data-stu-id="34129-145">You can parse out the **@Mention** portion of the message text using a static method provided with the Microsoft Bot Framework — a method of the `TurnContext` class named `remove_recipient_mention`.</span></span>

```python
modified_text = TurnContext.remove_recipient_mention(turn_context.activity)
```

* * *

## <a name="command-menu-best-practices"></a><span data-ttu-id="34129-146">Práticas recomendadas do menu de comandos</span><span class="sxs-lookup"><span data-stu-id="34129-146">Command menu best practices</span></span>

* <span data-ttu-id="34129-147">**Mantenha-o simples**: o menu bot é destinado a apresentar os principais recursos do bot.</span><span class="sxs-lookup"><span data-stu-id="34129-147">**Keep it simple**: The bot menu is meant to present the key capabilities of your bot.</span></span>
* <span data-ttu-id="34129-148">**Mantenha-** o em breve: as opções de menu não devem ser extremamente longas e instruções de linguagem natural complexas, que devem ser comandos simples.</span><span class="sxs-lookup"><span data-stu-id="34129-148">**Keep it short**: Menu options shouldn’t be extremely long and complex natural language statements — they should be simple commands.</span></span>
* <span data-ttu-id="34129-149">**Mantenha-o em invocação**: as ações/comandos do menu do bot devem estar sempre disponíveis, independentemente do estado da conversa ou da caixa de diálogo em que o bot está.</span><span class="sxs-lookup"><span data-stu-id="34129-149">**Keep it invokable**: Bot menu actions/commands should always be available, regardless of the state of the conversation or the dialog the bot is in.</span></span>
