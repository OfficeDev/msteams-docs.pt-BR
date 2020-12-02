---
title: Criar um menu de comando para o bot
author: clearab
description: Como criar um menu de comando para o bot do Microsoft Teams
ms.topic: overview, command menu
ms.author: anclear
ms.openlocfilehash: ccbacc6ec6f18a38512d81dc898d0b14357d6ef7
ms.sourcegitcommit: bfdcd122b6b4ffc52d92320d4741f870c07f0542
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2020
ms.locfileid: "49552483"
---
# <a name="bot-command-menus"></a><span data-ttu-id="9795a-103">Menus de comando do bot</span><span class="sxs-lookup"><span data-stu-id="9795a-103">Bot command menus</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

> [!Note]
> <span data-ttu-id="9795a-104">Menus de bot não aparecerão em clientes móveis.</span><span class="sxs-lookup"><span data-stu-id="9795a-104">Bot menus won't appear on mobile clients.</span></span>

<span data-ttu-id="9795a-105">Adicionar menu de comando para seu bot permite que você defina um conjunto de comandos principais que seu bot possa sempre responder.</span><span class="sxs-lookup"><span data-stu-id="9795a-105">Add command menu for your bot allows you to define a set of core commands your bot can always respond to.</span></span> <span data-ttu-id="9795a-106">A lista de comandos é apresentada ao usuário acima da área de mensagem de redação quando está convertida com o bot.</span><span class="sxs-lookup"><span data-stu-id="9795a-106">The list of commands is presented to the user above the compose message area when they are conversing with your bot.</span></span> <span data-ttu-id="9795a-107">A seleção de um comando na lista inserirá a cadeia de caracteres de comando na caixa de mensagem de redação, todos os usuários precisarão ser selecionados **Enviar**.</span><span class="sxs-lookup"><span data-stu-id="9795a-107">Selecting a command from the list will insert the command string into the compose message box, then all users need to do is select **Send**.</span></span>

![Menu de comando do bot](./conversations/media/bot-menu-sample.png)

## <a name="create-a-command-menu-for-your-bot"></a><span data-ttu-id="9795a-109">Criar um menu de comando para o bot</span><span class="sxs-lookup"><span data-stu-id="9795a-109">Create a command menu for your bot</span></span>

<span data-ttu-id="9795a-110">Menus de comando são definidos no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9795a-110">Command menus are defined in your app manifest.</span></span> <span data-ttu-id="9795a-111">Você pode usar o app Studio para ajudá-lo a criá-los ou adicioná-los manualmente.</span><span class="sxs-lookup"><span data-stu-id="9795a-111">You can either use App Studio to help you create them, or add them manually.</span></span>

### <a name="creating-a-command-menu-for-your-bot-using-app-studio"></a><span data-ttu-id="9795a-112">Criando um menu de comando para o bot usando o app Studio</span><span class="sxs-lookup"><span data-stu-id="9795a-112">Creating a command menu for your bot using App Studio</span></span>

<span data-ttu-id="9795a-113">As instruções aqui presumem que você esteja editando um manifesto de aplicativo existente.</span><span class="sxs-lookup"><span data-stu-id="9795a-113">The instructions here assume that you'll be editing an existing app manifest.</span></span> <span data-ttu-id="9795a-114">As etapas para adicionar um menu de comando são as mesmas, se você está criando um novo manifesto ou editando um existente.</span><span class="sxs-lookup"><span data-stu-id="9795a-114">The steps for adding a command menu are the same, whether you're creating a new manifest or editing an existing one.</span></span>

1. <span data-ttu-id="9795a-115">Abra o app Studio no... menu de estouro no trilho esquerdo de navegação.</span><span class="sxs-lookup"><span data-stu-id="9795a-115">Open App Studio from the ... overflow menu on the left navigation rail.</span></span> <span data-ttu-id="9795a-116">Se você não tiver o app Studio disponível, você pode baixá-lo.</span><span class="sxs-lookup"><span data-stu-id="9795a-116">If you don't have App Studio available you can download it.</span></span> <span data-ttu-id="9795a-117">Consulte [Installing app Studio](https://aka.ms/teams-app-studio#installing-app-studio) para obter mais informações sobre como usar o app Studio.</span><span class="sxs-lookup"><span data-stu-id="9795a-117">See [Installing App Studio](https://aka.ms/teams-app-studio#installing-app-studio) for more information on using App Studio.</span></span>

    ![App Studio](./conversations/media/AppStudio.png)

2. <span data-ttu-id="9795a-119">Uma vez no app Studio, selecione a guia **Editor do manifesto** .</span><span class="sxs-lookup"><span data-stu-id="9795a-119">Once in App Studio, select the **Manifest editor** tab.</span></span>

3. <span data-ttu-id="9795a-120">Na coluna à esquerda do modo de exibição editor de manifesto na seção **recursos** , selecione **bots**.</span><span class="sxs-lookup"><span data-stu-id="9795a-120">In the left column of the manifest editor view in the **Capabilities** section, select **Bots**.</span></span>

4. <span data-ttu-id="9795a-121">Na coluna à direita do modo de exibição editor de manifesto na seção **comandos** , selecione o botão **Adicionar** .</span><span class="sxs-lookup"><span data-stu-id="9795a-121">In the right column of the manifest editor view in the **Commands** section, select the **Add** button.</span></span>

    ![Botão Adicionar menu de comando do App Studio](./conversations/media/AppStudio-CommandMenu-Add.png)

5. <span data-ttu-id="9795a-123">A **nova** tela de comando será exibida.</span><span class="sxs-lookup"><span data-stu-id="9795a-123">The **New Command** screen appears.</span></span> <span data-ttu-id="9795a-124">Insira o **texto do comando** que você deseja que apareça como o comando de menu e o **texto de ajuda** que você deseja que apareçam diretamente sob o texto do comando no menu.</span><span class="sxs-lookup"><span data-stu-id="9795a-124">Enter the **Command text** that you want to have appear as the menu command, and the **Help text** that you want to have appear directly under the command text in the menu.</span></span> <span data-ttu-id="9795a-125">Isso deve ser uma breve explicação da finalidade do comando.</span><span class="sxs-lookup"><span data-stu-id="9795a-125">This should be a brief explanation of the purpose of the command.</span></span>

6. <span data-ttu-id="9795a-126">Em seguida, selecione o (s) escopo (s) onde deseja que este menu de comando apareça e, em seguida, selecione o botão **salvar** .</span><span class="sxs-lookup"><span data-stu-id="9795a-126">Next, select the scope(s) where you want this command menu to appear, then select the **Save** button.</span></span>

    ![Botão Adicionar menu de comando do App Studio](./conversations/media/AppStudio-NewCommandMenu.png)

### <a name="creating-a-command-menu-for-your-bot-by-editing-manifestjson"></a><span data-ttu-id="9795a-128">Criar um menu de comando para o bot editando **Manifest.jsem**</span><span class="sxs-lookup"><span data-stu-id="9795a-128">Creating a command menu for your bot by editing **Manifest.json**</span></span>

<span data-ttu-id="9795a-129">Outra abordagem válida para a criação de um menu de comando é criá-lo diretamente no arquivo de manifesto ao desenvolver o código-fonte do bot.</span><span class="sxs-lookup"><span data-stu-id="9795a-129">Another valid approach for creating a command menu is to create it directly in the manifest file while developing your bot source code.</span></span> <span data-ttu-id="9795a-130">Aqui estão algumas coisas que você deve ter em mente ao usar essa abordagem:</span><span class="sxs-lookup"><span data-stu-id="9795a-130">Here are a few things to keep in mind when using this approach:</span></span>

1. <span data-ttu-id="9795a-131">Cada menu oferece suporte a até 10 comandos.</span><span class="sxs-lookup"><span data-stu-id="9795a-131">Each menu supports up to 10 commands.</span></span>

2. <span data-ttu-id="9795a-132">Você pode criar um único menu de comando que funcionará em todos os escopos.</span><span class="sxs-lookup"><span data-stu-id="9795a-132">You can create a single command menu that will work in all scopes.</span></span>

3. <span data-ttu-id="9795a-133">Você pode criar um menu de comando diferente para cada escopo</span><span class="sxs-lookup"><span data-stu-id="9795a-133">You can create a different command menu for each scope</span></span>

#### <a name="manifest-example---single-menu-for-both-scopes"></a><span data-ttu-id="9795a-134">Exemplo de manifesto – menu único para ambos os escopos</span><span class="sxs-lookup"><span data-stu-id="9795a-134">Manifest example - single menu for both scopes</span></span>

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

#### <a name="manifest-example---menu-for-each-scope"></a><span data-ttu-id="9795a-135">Exemplo de manifesto-menu para cada escopo</span><span class="sxs-lookup"><span data-stu-id="9795a-135">Manifest example - menu for each scope</span></span>

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

## <a name="handling-menu-commands-in-your-bot-code"></a><span data-ttu-id="9795a-136">Manipular comandos de menu no seu código de bot</span><span class="sxs-lookup"><span data-stu-id="9795a-136">Handling menu commands in your bot code</span></span>

<span data-ttu-id="9795a-137">Os bots em um grupo ou canal respondem apenas quando são mencionados ("@botname") em uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="9795a-137">Bots in a group or channel respond only when they are mentioned ("@botname") in a message.</span></span> <span data-ttu-id="9795a-138">Como resultado, todas as mensagens recebidas por um bot quando em um escopo de grupo ou canal conterão seu próprio nome no texto da mensagem retornado.</span><span class="sxs-lookup"><span data-stu-id="9795a-138">As a result, every message received by a bot when in a group or channel scope will contain its own name in the message text returned.</span></span> <span data-ttu-id="9795a-139">Você precisa garantir que as alças de análise da mensagem antes de manipular o comando retornado.</span><span class="sxs-lookup"><span data-stu-id="9795a-139">You need to ensure your message parsing handles that before handling the command being returned.</span></span>

> <span data-ttu-id="9795a-140">**Observação** Para manipular os comandos no código, eles são enviados ao bot como uma mensagem regular.</span><span class="sxs-lookup"><span data-stu-id="9795a-140">**Note** For handling the commands in code, they are sent to your bot as a regular message.</span></span> <span data-ttu-id="9795a-141">Portanto, você precisa tratá-los como faria para qualquer outra mensagem de seus usuários.</span><span class="sxs-lookup"><span data-stu-id="9795a-141">So you need to handle them as you would do for any other message from your users.</span></span> <span data-ttu-id="9795a-142">Eles são puramente um tratamento de interface do usuário que insere texto pré-configurado na caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="9795a-142">They are purely a UI treatment that inserts pre-configured text into the text box.</span></span> <span data-ttu-id="9795a-143">O usuário deve então enviar esse texto como faria para qualquer outra mensagem.</span><span class="sxs-lookup"><span data-stu-id="9795a-143">The user must then send that text as they would do for any other message.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="9795a-144">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="9795a-144">C#/.NET</span></span>](#tab/dotnet)

<span data-ttu-id="9795a-145">Você pode analisar a parte de **\@ menção** do texto da mensagem usando um método estático fornecido com o Microsoft bot Framework — um método da `Activity` classe chamado `RemoveRecipientMention` .</span><span class="sxs-lookup"><span data-stu-id="9795a-145">You can parse out the **\@Mention** portion of the message text using a static method provided with the Microsoft Bot Framework — a method of the `Activity` class named `RemoveRecipientMention`.</span></span>

```csharp
var modifiedText = turnContext.Activity.RemoveRecipientMention();
```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="9795a-146">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="9795a-146">JavaScript/Node.js</span></span>](#tab/javascript)

<span data-ttu-id="9795a-147">Você pode analisar a parte de **\@ menção** do texto da mensagem usando um método estático fornecido com o Microsoft bot Framework — um método da `TurnContext` classe chamado `removeMentionText` .</span><span class="sxs-lookup"><span data-stu-id="9795a-147">You can parse out the **\@Mention** portion of the message text using a static method provided with the Microsoft Bot Framework — a method of the `TurnContext` class named `removeMentionText`.</span></span>

```javascript
const modifiedText = TurnContext.removeMentionText(turnContext.activity, turnContext.activity.recipient.id);
```

# <a name="python"></a>[<span data-ttu-id="9795a-148">Python</span><span class="sxs-lookup"><span data-stu-id="9795a-148">Python</span></span>](#tab/python)


<span data-ttu-id="9795a-149">Você pode analisar a parte **@Mention** do texto da mensagem usando um método estático fornecido com o Microsoft bot Framework — um método da `TurnContext` classe chamado `remove_recipient_mention` .</span><span class="sxs-lookup"><span data-stu-id="9795a-149">You can parse out the **@Mention** portion of the message text using a static method provided with the Microsoft Bot Framework — a method of the `TurnContext` class named `remove_recipient_mention`.</span></span>

```python
modified_text = TurnContext.remove_recipient_mention(turn_context.activity)
```

* * *

## <a name="command-menu-best-practices"></a><span data-ttu-id="9795a-150">Práticas recomendadas do menu de comandos</span><span class="sxs-lookup"><span data-stu-id="9795a-150">Command menu best practices</span></span>

* <span data-ttu-id="9795a-151">**Mantenha-o simples**: o menu bot é destinado a apresentar os principais recursos do bot.</span><span class="sxs-lookup"><span data-stu-id="9795a-151">**Keep it simple**: The bot menu is meant to present the key capabilities of your bot.</span></span>
* <span data-ttu-id="9795a-152">**Mantenha-** o em breve: as opções de menu não devem ser extremamente longas e instruções de linguagem natural complexas, que devem ser comandos simples.</span><span class="sxs-lookup"><span data-stu-id="9795a-152">**Keep it short**: Menu options shouldn’t be extremely long and complex natural language statements — they should be simple commands.</span></span>
* <span data-ttu-id="9795a-153">**Mantenha-o em invocação**: as ações/comandos do menu do bot devem estar sempre disponíveis, independentemente do estado da conversa ou da caixa de diálogo em que o bot está.</span><span class="sxs-lookup"><span data-stu-id="9795a-153">**Keep it invokable**: Bot menu actions/commands should always be available, regardless of the state of the conversation or the dialog the bot is in.</span></span>

> <span data-ttu-id="9795a-154">**Observação** Se você remover qualquer comando do manifesto, será necessário reimplantar seu aplicativo para que as alterações entrem em vigor.</span><span class="sxs-lookup"><span data-stu-id="9795a-154">**Note** If you remove any commands from your manifest, you will need to redeploy your app for the changes to take effect.</span></span> <span data-ttu-id="9795a-155">Em geral, qualquer alteração no manifesto exige isso.</span><span class="sxs-lookup"><span data-stu-id="9795a-155">In general, any changes to the manifest require this.</span></span>
